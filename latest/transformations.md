# Transformation specification

Release `2dda583978fb-19eda0e60019`. This page specifies every transformation from the published files to
the released tables, with the rule, the reason and the code that implements it. It is written for
engineers moving the proof of concept to scheduled pipelines on live data. Every source, file,
mapping and parameter below is generated from the configuration the build used, so it cannot
drift from the code. Decision numbers (D-nnnn) refer to the [decision log](decision_log.md), which
gives the full reasoning.

## 1. Layers and invariants

| Layer | Holds | Written by | Rule |
|---|---|---|---|
| L0 raw | Published files exactly as downloaded, with SHA-256 | `cypneed ingest` | Write-once; a new version goes in a new dated folder. API queries are saved beside responses. Rebuilds never call APIs. |
| L1 staged | One long Parquet table per published table | `cypneed stage` | Values kept as published text; labels kept; non-England rows kept; file totals checked. |
| L2 harmonised | `fact_<level>`, `fact_other_geography`, dimensions | `cypneed harmonise` | Observed values only: England only, current codes, standard age bands; nothing imputed. |
| L3 derived | `derived_<level>` | `cypneed derive` | Rates, intervals, smoothing, percentiles, conversions. Never overwrites L2. |
| L4 serving | `serve_*`, `profile_*` views, release files | `cypneed serve`, `cypneed release` | Display layer; fallbacks are display only. |
| L5 composites | `l5_*` tables | `cypneed composite` | Experimental; reads L2–L4 read-only. |

Invariants that every pipeline must keep:

1. **Published figures win.** A value published at a level is used as is; a sum of smaller areas is only used where nothing is published, and any difference is written to `reconciliation`.
2. **Counts move between geographies, rates never do.** Rates are recomputed from summed numerators and denominators.
3. **Nothing is imputed.** A sum with any suppressed or missing part is NULL with a `null_reason` and bounds.
4. **No value is pushed down** from an area to the areas inside it.
5. **Every row carries lineage** (`source_file_id`, `lineage_key`) and the `snapshot_id` (code commit + data hash).
6. **Determinism.** Rows are sorted before floating-point sums, and Monte Carlo runs are seeded, so a rebuild gives identical content (gate 17).

## 2. Pipeline stages

| Step | Command | Code | Input → output | Rules | QA |
|---|---|---|---|---|---|
| T1 Ingest | `ingest` | `ingest/` | publisher URL or API → `data/raw/<source>/<date>/` | Hash; register in `dim_source_file`; never overwrite. | Gate 1 |
| T2 Stage | `stage` | `stage/<module>.py` (per source, below) | raw file → `data/staged/<source>/<table>.parquet` | Find header rows and columns by label; keep text; check totals and expected rows. | Gate 2 |
| T3 Recode | — | not needed (D-0041) | LSOA11 → LSOA21 | Only if a source publishes LSOA11; none does. | — |
| T4 Assign points | `harmonise` | `harmonise/phase2.py` (`police`) | police records → LSOA21 counts | Published LSOA21 code; checked against full-resolution boundary point-in-polygon; rejects kept with a reason. | Gate 11 |
| T5 Apportion | `derive` | `derive/overlap.py` | Sub-ICB values → overlapping councils | Overlaps only; GP-registered population weights; flagged `converted_overlap`, not spatially suitable. | Gate 12 |
| T6 Aggregate | `harmonise` | `harmonise/facts.py` (`aggregate`, `fill_levels`) | LSOA → MSOA → LAD → UTLA → England | Sum counts only, where nesting is proven and nothing is published; NULL if any part is missing. | Gates 4, 7, 8 |
| T6b Other geographies | `harmonise` | `harmonise/phase4.py` (`t6b`) | Sub-ICB / police force / youth justice areas | coterminous → relabel; nests within → sum; contains → fallback only; overlaps → T5. | Gate 12 |
| T6c IoD summaries | `derive` | `derive/iod.py` | IoD LSOA scores → MSOA summaries | Population-weighted average score; share in most deprived decile; validated against published LAD summaries. | Gate 13 |
| T7 Rates and intervals | `derive` | `derive/rates.py`, `derive/stats.py` | counts + populations → rates | Formulas below. | Gate 9 |
| T8 Small numbers | `derive` | `derive/rates.py` (`eb_rows`) | rates → reliability flags, EB-smoothed rates | Marshall global EB; never replaces the crude rate. | Gate 10 |
| T9 Comparability | `derive` | `derive/rates.py` (`comparability_rows`) | rates / values → percentiles, z-scores | Per level, native values only, fallbacks excluded. | Gate 10 |
| Publisher's method | `derive` | `derive/publisher_method.py` | counts + populations → published-style percentages where unpublished | Only after the method reproduces every published value (D-0085). | — |
| T10 Metadata | `harmonise` | `config.py`, `db.py` | config → `dim_*` | Catalogue validated (`validate-config`). | Gate 3 |
| T11 Serve | `serve` | `sql/serving.sql`, `serve/build.py`, `sql/fallback.sql` | L2/L3 → `serve_*`, `profile_*` | One row per area × column, value or reason; fallbacks labelled. | Gates 15, 16 |
| L5 Composites | `composite` | `composite/` | L2/L3 → `l5_*` | SPEC 12; see the [composite methodology](composites/methodology_composite.md). | Gate 19 |
| T12 Release | `release`, `package-release` | `release/` | DB → release files, Fabric bundle | Clean commit only; reproducibility report must match. | Gates 17, 18 |

## 3. Rules used by many sources

### 3.1 Geography

- Hierarchy: LSOA21 → MSOA21 → LAD (April 2025) → UTLA (April 2025) → England. Each LSOA's and MSOA's parent is proven from Output Area membership and checked against full-resolution boundaries (99.9% of area inside the assigned parent).
- **Code successors** (`config/geography.yaml`): an old code is relabelled to its successor only where the new code is absent from that series and boundaries are identical (D-0036, D-0060).
- **Other geographies** are classified against the hierarchy by membership units (D-0054 onwards): `coterminous` (relabel), `nests_within` (sum when the parent is fully covered), `contains` (no conversion; the containing value is a labelled fallback), `overlaps` (T5).

### 3.2 Symbols, suppression and missing values

Each source's symbols are listed in its section below with the `null_reason` they map to and the most
they can hide. A cell with a symbol is stored as NULL with the symbol in `source_code`. A sum is
NULL if any part is NULL: `suppressed` (with `count_lower`, `count_upper`, `n_suppressed`) or
`incomplete`. Absent rows are read as 0 only where the source is proven to list every non-zero
case (D-0066 EHC plans, D-0084 asylum support, D-0048 police, children's homes).

### 3.3 Age bands

Populations are held by single year of age; a denominator band is the exact sum of the single years
covering the numerator band. Source bands are kept as published (`src_*`) and never split.

### 3.4 Rates and confidence intervals (T7)

For count *x* and denominator *n*: rate = *x* / *n* × multiplier (100, 1,000 or 10,000 per indicator).
The denominator must match area, age band, sex and ethnicity classification; stock measures use the
population nearest the reference date, flow measures the mid-period population, and the gap must not
exceed `max_denominator_gap_days`.

- **Wilson score** (proportions), z = 1.959964, p = x/n:
  centre = (p + z²/2n) / (1 + z²/n); half-width = z·√(p(1−p)/n + z²/4n²) / (1 + z²/n).
  Limits are clipped to [0, 1]; x = 0 gives lower 0, x = n gives upper 1.
- **Byar** (event rates): lower count = x(1 − 1/9x − z/3√x)³ (0 when x = 0); upper count =
  (x+1)(1 − 1/9(x+1) + z/3√(x+1))³; each divided by *n* and multiplied.
- **Reliability:** `low_reliability` when x < `min_reliable_numerator` or n < `min_reliable_denominator`.
- Undefined rates are NULL with a reason: `zero_denominator`, `numerator_exceeds_denominator`,
  `denominator_suppressed`, `no_matching_denominator`, `denominator_period_gap`.

### 3.5 Smoothing and comparability (T8, T9)

- **Marshall global empirical Bayes** per indicator and level: m = Σx/Σn; s² = Σn(r−m)²/Σn;
  φ = max(s² − m/n̄, 0); Cᵢ = φ/(φ + m/nᵢ); EBᵢ = m + Cᵢ(rᵢ − m).
- **Percentile** = (average rank − 1)/(N − 1) × 100, ties averaged, NULLs excluded; **z-score** uses
  the population standard deviation. Areas are sorted by code before any sum (determinism).

### 3.6 IoD summaries (T6c)

MSOA score = Σ(LSOA score × population)/Σ population (children 0–15 for IDACI, total population
otherwise); share in decile 1 = population in decile-1 LSOAs / population. Ranks and deciles are never
averaged. Validated against MHCLG's published LAD and UTLA summaries (gate 13).

### 3.7 Fallbacks and the publisher's method

- **Fallback** (`sql/fallback.sql`): where a measure exists only for an area that wholly contains a council, that value is shown for the council with `is_fallback = true`. Never used in derived values, profiles or composites.
- **Publisher's method** (`publisher_method_fill`): a published percentage is computed for areas the publisher leaves out, only after the stated method reproduces every published value to 1e-9 (D-0085).

## 4. Sources

### G1: Output Area (2021) to LSOA (2021) to MSOA (2021) to LAD (April 2025) lookup in England and Wales

- **Publisher:** Office for National Statistics · <https://geoportal.statistics.gov.uk/datasets/b9ca90c10aaa4b8d9791e9859a38ca67/about>
- **Native geography:** OA21 · **period:** April 2025 LAD boundaries · **target:** `dim_geography`
- **Staging code:** `stage/lookups.py` · **harmonise code:** `harmonise/geography.py (nesting proof)`
- **Files:**
  - `oa21_lsoa21_msoa21_lad22_exact`: Output Area (2021) to LSOA to MSOA to LAD (December 2021) Exact Fit Lookup in EW (V3)
  - `oa21_wd25_lad25`: Output Area (2021) to Ward (2025) to LAD (May 2025) Best Fit Lookup in EW (V3)
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0027, D-0095

### G2: Lower Tier Local Authority to Upper Tier Local Authority (April 2025) lookup in England and Wales

- **Publisher:** Office for National Statistics · <https://geoportal.statistics.gov.uk/datasets/53ec53c55c8949b19970ce8c571b3c08/about>
- **Native geography:** LAD25 · **period:** April 2025 · **target:** `dim_geography`
- **Staging code:** `stage/lookups.py` · **harmonise code:** `harmonise/geography.py (nesting proof)`
- **Files:**
  - `lad25_ctyua25`: Local Authority District to County and Unitary Authority (April 2025) Lookup in EW (V2)
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0028, D-0095

### G3: LSOA (2021) to Sub ICB Location to ICB lookup (2024)

- **Publisher:** Office for National Statistics · <https://geoportal.statistics.gov.uk/datasets/27d32e68e05a4c848276330903bb18fc/about>
- **Native geography:** LSOA21 · **period:** 2024 configuration · **target:** `lkp_other_to_hierarchy`
- **Staging code:** `stage/lookups.py` · **harmonise code:** `harmonise/phase4.py (build_geographies, t6b)`
- **Files:**
  - `lsoa21_sicbl24_icb24`: LSOA (2021) to SICBL to ICB to Cancer Alliances to LAD (April 2024) Lookup in EN
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0069, D-0075, D-0078, D-0095

### G3b: Patients Registered at a GP Practice (LSOA by age and sex)

- **Publisher:** NHS England · <https://digital.nhs.uk/data-and-information/publications/statistical/patients-registered-at-a-gp-practice/april-2025>
- **Native geography:** LSOA21 · **period:** Quarter nearest 1 April 2025 · **target:** `lkp_apportion_weights`
- **Staging code:** `stage/phase4.py` · **harmonise code:** `harmonise/phase4.py (gp_registered)`
- **Files:**
  - `gp_reg_sing_age_regions_202504`: Patients Registered at a GP Practice, April 2025: single year of age (Commissioning Regions, ICBs, SICBLs, PCNs) · <https://files.digital.nhs.uk/99/38AC11/gp-reg-pat-prac-sing-age-regions.zip>
  - `gp_reg_lsoa21_202504`: Patients Registered at a GP Practice, April 2025: LSOA 2021 (all persons, females, males) · <https://files.digital.nhs.uk/7E/26EB57/gp-reg-pat-prac-lsoa-2021-male-female-Apr-25.zip>
- **Disclosure control:** none; tolerance 0 / 0.005. NHS England GP registrations: counts by practice x LSOA21 and sex, no suppression or rounding symbols (inspection, Phase 4); female + male sum exactly to every published total. Patients of unknown sex are excluded by the publisher. Used only as weights and Sub-ICB denominators.
- **Decisions:** D-0069, D-0095

### G4: National Statistics Postcode Lookup (NSPL)

- **Publisher:** Office for National Statistics · <https://geoportal.statistics.gov.uk/datasets/9d8364ebae8b4439aa66cda440e54fc8/about>
- **Native geography:** postcode · **period:** Latest · **target:** `point assignment (T4)`
- **Staging code:** `—` · **harmonise code:** `harmonise/geography.py (nesting proof)`
- **Files:**
  - `nspl_aug_2026`: National Statistics Postcode Lookup (August 2026)
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0031, D-0095

### G5: Boundaries: LSOA (Dec 2021), MSOA (Dec 2021), LAD (Apr 2025), Counties and Unitary Authorities (Apr 2025), Sub ICB Locations (Apr 2024), PFA, Wards

- **Publisher:** Office for National Statistics · <https://geoportal.statistics.gov.uk/datasets/2bbaef5230694f3abae4f9145a3a9800/about>
- **Native geography:** various · **period:** As listed in title · **target:** `nesting proof, neighbours, point-in-polygon (BFC); release boundaries/tiles (BGC/BSC)`
- **Staging code:** `stage/boundaries.py` · **harmonise code:** `harmonise/geography.py (nesting proof)`
- **Files:**
  - `lsoa21_bfc`: Lower layer Super Output Areas (December 2021) Boundaries EW BFC (V10)
  - `lsoa21_bgc`: Lower layer Super Output Areas (December 2021) Boundaries EW BGC (V5)
  - `msoa21_bfc`: Middle layer Super Output Areas (December 2021) Boundaries EW BFC (V7)
  - `msoa21_bgc`: Middle layer Super Output Areas (December 2021) Boundaries EW BGC (V3)
  - `lad25_bfc`: Local Authority Districts (May 2025) Boundaries UK BFC (V2)
  - `lad25_bgc`: Local Authority Districts (May 2025) Boundaries UK BGC (V2)
  - `ctyua25_bfc`: Counties and Unitary Authorities (December 2025) Boundaries UK BFC
  - `ctyua25_bgc`: Counties and Unitary Authorities (December 2025) Boundaries UK BGC
- **Disclosure control:** none; tolerance 0 / 0. Geometry; no statistical values.
- **Decisions:** D-0076, D-0095

### G6: LSOA (2021) to Electoral Ward to LAD lookup

- **Publisher:** Office for National Statistics · <https://geoportal.statistics.gov.uk/datasets/f29a49574cc84f6d8e6e59ce2d8efb18/about>
- **Native geography:** WD25 · **period:** May 2025 (verify) · **target:** `dim_other_geography, lkp_other_to_hierarchy`
- **Staging code:** `stage/lookups.py` · **harmonise code:** `harmonise/geography.py (nesting proof)`
- **Files:**
  - `lsoa21_wd25_lad25`: LSOA (2021) to Electoral Ward (2025) to LAD (2025) Best Fit Lookup in EW (V2)
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0095

### G7: Youth justice service to local authority composition (constructed)

- **Publisher:** Youth Justice Board (list of services); composition constructed by this project · <https://www.gov.uk/government/collections/youth-offending-team-contact-details>
- **Native geography:** YJS · **period:** 2024/25 · **target:** `dim_other_geography, lkp_other_to_hierarchy`
- **Staging code:** `—` · **harmonise code:** `harmonise/phase4.py (build_geographies, t6b)`
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0069, D-0071, D-0075, D-0078

### G8: LAD to Police Force Area lookup

- **Publisher:** Office for National Statistics · <https://geoportal.statistics.gov.uk/datasets/8f77bda25c124e43aca5f3b90494e405/about>
- **Native geography:** LAD25 · **period:** 2024/25 · **target:** `lkp_other_to_hierarchy`
- **Staging code:** `stage/lookups.py` · **harmonise code:** `harmonise/phase4.py (build_geographies, t6b)`
- **Files:**
  - `lad25_csp25_pfa25`: Local Authority District to Community Safety Partnership to PFA (April 2025) Lookup in EW
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0069, D-0071, D-0075, D-0078, D-0095

### G9: LSOA (2011) to LSOA (2021) to LAD lookup with change indicator

- **Publisher:** Office for National Statistics
- **Native geography:** LSOA11 · **period:** static · **target:** `lkp_apportion_weights ('X' cases only)`
- **Staging code:** `—` · **harmonise code:** `harmonise/phase4.py (build_geographies, t6b)`
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0069

### G10: MSOA Names (2021 MSOAs)

- **Publisher:** House of Commons Library · <https://houseofcommonslibrary.github.io/msoanames/>
- **Native geography:** MSOA21 · **period:** 2021 vintage · **target:** `dim_geography display names`
- **Staging code:** `stage/lookups.py` · **harmonise code:** `harmonise/geography.py (nesting proof)`
- **Files:**
  - `msoa_names_2_3`: House of Commons Library MSOA Names (2021 MSOAs) v2.3, 13 February 2026 · <https://houseofcommonslibrary.github.io/msoanames/MSOA-Names-2.3.csv>
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0033, D-0095

### P1: Lower layer Super Output Area population estimates (Small Area Population Estimates), single year of age and sex

- **Publisher:** Office for National Statistics · <https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/bulletins/annualsmallareapopulationestimates/latest>
- **Native geography:** LSOA21 · **period:** mid-2024 (30 June 2024) · **target:** `fact_small_area`
- **Staging code:** `stage/population.py` · **harmonise code:** `harmonise/population.py`
- **Files:**
  - `sape_lsoa_sya_2022_2024`: LSOA mid-year population estimates, single year of age, mid-2022 (revised Nov 2025) to mid-2024 · <https://www.ons.gov.uk/file?uri=/peoplepopulationandcommunity/populationandmigration/populationestimates/datasets/lowersuperoutputareamidyearpopulationestimates/mid2022revisednov2025tomid2024/sapelsoasyoa20222024.xlsx>
  - `sape_msoa_sya_2022_2024`: MSOA mid-year population estimates, single year of age, mid-2022 (revised Nov 2025) to mid-2024 · <https://www.ons.gov.uk/file?uri=/peoplepopulationandcommunity/populationandmigration/populationestimates/datasets/middlesuperoutputareamidyearpopulationestimates/mid2022revisednov2025tomid2024/sapemsoasyoa20222024.xlsx>
- **Disclosure control:** none; tolerance 0 / 0. ONS small area population estimates are constrained to MSOA and local authority mid-year estimates (ONS SAPE quality and methodology information, https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/smallareapopulationestimatesqmi). Checked: LSOA single-year sums equal the published MSOA estimates exactly.
- **Decisions:** D-0014, D-0094, D-0095

### P1b: Mid-year population estimates, single year of age and sex (LAD, UTLA, England)

- **Publisher:** Office for National Statistics · <https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/datasets/populationestimatesforukenglandandwalesscotlandandnorthernireland>
- **Native geography:** LAD25 · **period:** mid-2024 · **target:** `fact_lad, fact_service_area, fact_nation`
- **Staging code:** `stage/population.py` · **harmonise code:** `harmonise/population.py`
- **Files:**
  - `mye24_tables_uk`: Population estimates for the UK, England, Wales, Scotland and Northern Ireland: mid-2024 · <https://www.ons.gov.uk/file?uri=/peoplepopulationandcommunity/populationandmigration/populationestimates/datasets/populationestimatesforukenglandandwalesscotlandandnorthernireland/mid2024/mye24tablesuk.xlsx>
- **Disclosure control:** none; tolerance 0 / 0. Published LA mid-year estimates. Checked: LAD sums equal the published UTLA and England figures exactly in every age and sex cell.
- **Decisions:** D-0014, D-0029, D-0031, D-0036, D-0095

### P4: Census 2021: ethnic group by age (custom dataset, LSOA21)

- **Publisher:** Office for National Statistics · <https://www.ons.gov.uk/datasets/create>
- **Native geography:** LSOA21 · **period:** Census Day 21 March 2021 · **target:** `fact_small_area`
- **Staging code:** `stage/apis.py` · **harmonise code:** `harmonise/phase2.py (census)`
- **Files:**
  - `p4_eth6a_age7a_lsoa`: Census 2021 usual residents by ethnic group (6) and age (7), LSOA
  - `p4_eth6a_age7a_msoa`: Census 2021 usual residents by ethnic group (6) and age (7), MSOA
  - `p4_eth6a_age7a_ltla23`: Census 2021 usual residents by ethnic group (6) and age (7), LTLA 2023
  - `p4_eth6a_age7a_utla23`: Census 2021 usual residents by ethnic group (6) and age (7), UTLA 2023
  - `p4_eth6a_age7a_ctry`: Census 2021 usual residents by ethnic group (6) and age (7), country
- **Disclosure control:** record_swapping, cell_key; tolerance 10 / 0.01. Census 2021: targeted record swapping and cell key perturbation (ONS, 'Protecting personal data in Census 2021 results', https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/protectingpersonaldataincensus2021results). Small cells are perturbed, so sums of cells differ slightly from published totals; differences are reported in reconciliation.csv.
- **Decisions:** D-0011, D-0038, D-0045, D-0094

### P7: Schools, pupils and their characteristics: pupils by ethnicity and local authority

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/school-pupils-and-their-characteristics/2024-25>
- **Native geography:** UTLA25 · **period:** January 2025 school census · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_spc_2024_25_p7`: Schools, pupils and their characteristics, 2024/25: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/63491b17-2037-4533-b719-d3656aaf6ed5/files?fromPage=ReleaseDownloads>
- **Disclosure control:** none; tolerance 0 / 0.001. School census (SPC) data guidance: no suppression or rounding applied; 'x' not applicable, 'z' unknown. Checked: LA sums equal the published England figures exactly.
- **Symbols:** `x` = Not applicable (SPC convention) → `not_applicable`; `z` = Unknown (SPC convention) → `not_published`
- **Decisions:** D-0011, D-0054, D-0094, D-0095

### D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores

- **Publisher:** Ministry of Housing, Communities and Local Government · <https://www.gov.uk/government/statistics/english-indices-of-deprivation-2025>
- **Native geography:** LSOA21 · **period:** IoD 2025 (input data mostly 2022/23) · **target:** `fact_small_area`
- **Staging code:** `stage/iod.py` · **harmonise code:** `harmonise/phase2.py (iod)`
- **Files:**
  - `iod25_file7_all`: English Indices of Deprivation 2025, File 7: all ranks, scores, deciles and population denominators (LSOA) · <https://assets.publishing.service.gov.uk/media/691ded56d140bbbaa59a2a7d/File_7_IoD2025_All_Ranks_Scores_Deciles_Population_Denominators.csv>
- **Disclosure control:** none; tolerance 0 / 0. Index values (scores, ranks, deciles): not additive; no disclosure control.

### D1b: English Indices of Deprivation 2025: local authority summary measures

- **Publisher:** Ministry of Housing, Communities and Local Government · <https://www.gov.uk/government/statistics/english-indices-of-deprivation-2025>
- **Native geography:** LAD25 · **period:** IoD 2025 · **target:** `fact_lad, fact_service_area`
- **Staging code:** `stage/iod.py` · **harmonise code:** `harmonise/phase2.py (iod)`
- **Files:**
  - `iod25_file10_lad`: English Indices of Deprivation 2025, File 10: Local Authority District summaries (lower-tier) v2 · <https://assets.publishing.service.gov.uk/media/6917412ebc34c86ce4e6e7fc/File_10_-_IoD2025_Local_Authority_District_Summaries__lower-tier__v2.xlsx>
  - `iod25_file11_utla`: English Indices of Deprivation 2025, File 11: Local Authority District summaries (upper-tier) v2 · <https://assets.publishing.service.gov.uk/media/6917414ab49cc44345161802/File_11_-_IoD2025_Local_Authority_District_Summaries__upper-tier__v2.xlsx>
- **Disclosure control:** none; tolerance 0 / 0. MHCLG published LA summaries: not additive. Checked: recomputed LAD averages match the published values within published rounding (gate 13).
- **Decisions:** D-0013, D-0083

### F1: Children in Low Income Families: local area statistics (FYE 2025)

- **Publisher:** Department for Work and Pensions · <https://www.gov.uk/government/statistics/children-in-low-income-families-local-area-statistics-2022-to-2025>
- **Native geography:** LAD25 · **period:** FYE 2025 · **target:** `fact_service_area, fact_lad, fact_other_geography`
- **Staging code:** `stage/run.py` · **harmonise code:** `harmonise/phase3.py (tables: CiLIF ODS) and harmonise/phase2.py (statxplore: age bands)`
- **Files:**
  - `cilif_local_2022_2025`: Children in low income families: local area statistics, FYE 2022 to FYE 2025 (ODS tables) · <https://assets.publishing.service.gov.uk/media/69b809619d8b52961a62b49a/children-in-low-income-families-local-area-statistics-2022-2025.ods>
  - `f1_cilif_rel_la`: Children in relative low income families (BHC) by age band, local authority, FYE 2025 (Stat-Xplore)
  - `f1_cilif_rel_ctry`: Children in relative low income families (BHC) by age band, country, FYE 2025 (Stat-Xplore)
  - `f1_cilif_abs_la`: Children in absolute low income families (BHC) by age band, local authority, FYE 2025 (Stat-Xplore)
  - `f1_cilif_abs_ctry`: Children in absolute low income families (BHC) by age band, country, FYE 2025 (Stat-Xplore)
- **Disclosure control:** cell_key; tolerance 10 / 0.01. CiLIF data guidance: DWP applies disclosure control, and totals may not sum because of rounding and disclosure control; percentages rounded to 1 decimal place; no symbols. Checked: LA sums within tolerance of the published England totals.
- **Decisions:** D-0054, D-0077, D-0095

### F2: Universal Credit households with children (Stat-Xplore)

- **Publisher:** Department for Work and Pensions · <https://stat-xplore.dwp.gov.uk>
- **Native geography:** LSOA21 · **period:** March 2025 · **target:** `fact_small_area`
- **Staging code:** `stage/apis.py` · **harmonise code:** `harmonise/phase2.py (statxplore)`
- **Files:**
  - `f2_uc_hh_children_lsoa`: Households on Universal Credit with children, LSOA21, March 2025 (Stat-Xplore)
  - `f2_uc_hh_children_msoa`: Households on Universal Credit with children, MSOA21, March 2025 (Stat-Xplore)
  - `f2_uc_hh_children_la`: Households on Universal Credit with children, local authority, March 2025 (Stat-Xplore)
  - `f2_uc_hh_children_ctry`: Households on Universal Credit with children, country, March 2025 (Stat-Xplore)
- **Disclosure control:** cell_key, suppression; tolerance 15 / 0.03. Stat-Xplore adds small random adjustments to every cell and publishes counts below 5 as 0 (D-0053). DWP: no reliance on small cells; use published data for larger areas (Stat-Xplore Data Confidentiality note). Observed: complete LSOA sums differ from published figures by about 5 x sqrt(areas summed) at the 99th percentile; 15 + 3% covers this.
- **Symbols:** `0` = Count below 5 shown as 0 by Stat-Xplore disclosure control → `suppressed` (hides ≤ 4)
- **Decisions:** D-0009, D-0043, D-0053, D-0094

### F3: Disability Living Allowance claimants under 16 (Stat-Xplore)

- **Publisher:** Department for Work and Pensions · <https://stat-xplore.dwp.gov.uk>
- **Native geography:** LSOA21 · **period:** February 2025 · **target:** `fact_small_area`
- **Staging code:** `stage/apis.py` · **harmonise code:** `harmonise/phase2.py (statxplore)`
- **Files:**
  - `f3_dla_u16_lsoa`: DLA cases in payment aged under 16, LSOA21, February 2025 (Stat-Xplore)
  - `f3_dla_u16_msoa`: DLA cases in payment aged under 16, MSOA21, February 2025 (Stat-Xplore)
  - `f3_dla_u16_la`: DLA cases in payment aged under 16, local authority, February 2025 (Stat-Xplore)
  - `f3_dla_u16_ctry`: DLA cases in payment aged under 16, country, February 2025 (Stat-Xplore)
- **Disclosure control:** cell_key, suppression; tolerance 15 / 0.03. Stat-Xplore adds small random adjustments to every cell and publishes counts below 5 as 0 (D-0053). DWP: no reliance on small cells; use published data for larger areas (Stat-Xplore Data Confidentiality note). Observed: complete LSOA sums differ from published figures by about 5 x sqrt(areas summed) at the 99th percentile; 15 + 3% covers this.
- **Symbols:** `0` = Count below 5 shown as 0 by Stat-Xplore disclosure control → `suppressed` (hides ≤ 4)

### F4: Personal Independence Payment claimants aged 16-24 (Stat-Xplore)

- **Publisher:** Department for Work and Pensions · <https://stat-xplore.dwp.gov.uk>
- **Native geography:** LSOA21 · **period:** January 2025 · **target:** `fact_small_area`
- **Staging code:** `stage/apis.py` · **harmonise code:** `harmonise/phase2.py (statxplore)`
- **Files:**
  - `f4_pip_16_24_lsoa`: PIP cases with entitlement aged 16-24, LSOA21, March 2025 (Stat-Xplore)
  - `f4_pip_16_24_msoa`: PIP cases with entitlement aged 16-24, MSOA21, March 2025 (Stat-Xplore)
  - `f4_pip_16_24_la`: PIP cases with entitlement aged 16-24, local authority, March 2025 (Stat-Xplore)
  - `f4_pip_16_24_ctry`: PIP cases with entitlement aged 16-24, country, March 2025 (Stat-Xplore)
- **Disclosure control:** cell_key, suppression; tolerance 15 / 0.03. Stat-Xplore adds small random adjustments to every cell and publishes counts below 5 as 0 (D-0053). DWP: no reliance on small cells; use published data for larger areas (Stat-Xplore Data Confidentiality note). Observed: complete LSOA sums differ from published figures by about 5 x sqrt(areas summed) at the 99th percentile; 15 + 3% covers this.
- **Symbols:** `0` = Count below 5 shown as 0 by Stat-Xplore disclosure control → `suppressed` (hides ≤ 4)
- **Decisions:** D-0009, D-0040, D-0043, D-0053, D-0094

### F6: Census 2021: households with dependent children by type; occupancy rating of such households

- **Publisher:** Office for National Statistics · <https://www.ons.gov.uk/datasets/create>
- **Native geography:** LSOA21 · **period:** Census Day 21 March 2021 · **target:** `fact_small_area`
- **Staging code:** `stage/apis.py` · **harmonise code:** `harmonise/phase2.py (census)`
- **Files:**
  - `f6_hhcomp15a_occ5a_lsoa`: Census 2021 households by composition (15) and bedroom occupancy rating (5), LSOA
  - `f6_hhcomp15a_occ5a_msoa`: Census 2021 households by composition (15) and bedroom occupancy rating (5), MSOA
  - `f6_hhcomp15a_occ5a_ltla23`: Census 2021 households by composition (15) and bedroom occupancy rating (5), LTLA 2023
  - `f6_hhcomp15a_occ5a_utla23`: Census 2021 households by composition (15) and bedroom occupancy rating (5), UTLA 2023
  - `f6_hhcomp15a_occ5a_ctry`: Census 2021 households by composition (15) and bedroom occupancy rating (5), country
- **Disclosure control:** record_swapping, cell_key; tolerance 10 / 0.01. Census 2021: targeted record swapping and cell key perturbation (ONS, 'Protecting personal data in Census 2021 results', https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/protectingpersonaldataincensus2021results). Small cells are perturbed, so sums of cells differ slightly from published totals; differences are reported in reconciliation.csv.
- **Decisions:** D-0039, D-0045, D-0094

### F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)

- **Publisher:** Office for National Statistics · <https://www.ons.gov.uk/datasets/create>
- **Native geography:** LSOA21 · **period:** Census Day 21 March 2021 · **target:** `fact_small_area`
- **Staging code:** `stage/apis.py` · **harmonise code:** `harmonise/phase2.py (census)`
- **Files:**
  - `f7a_disability_age7a_lsoa`: Census 2021 disability (5) by age (7), LSOA
  - `f7a_disability_age7a_msoa`: Census 2021 disability (5) by age (7), MSOA
  - `f7a_disability_age7a_ltla23`: Census 2021 disability (5) by age (7), LTLA 2023
  - `f7a_disability_age7a_utla23`: Census 2021 disability (5) by age (7), UTLA 2023
  - `f7a_disability_age7a_ctry`: Census 2021 disability (5) by age (7), country
  - `f7b_carer_age3c_lsoa`: Census 2021 unpaid care (7) by age (3c), LSOA
  - `f7b_carer_age3c_msoa`: Census 2021 unpaid care (7) by age (3c), MSOA
  - `f7b_carer_age3c_ltla23`: Census 2021 unpaid care (7) by age (3c), LTLA 2023
  - `f7b_carer_age3c_utla23`: Census 2021 unpaid care (7) by age (3c), UTLA 2023
  - `f7b_carer_age3c_ctry`: Census 2021 unpaid care (7) by age (3c), country
- **Disclosure control:** record_swapping, cell_key; tolerance 10 / 0.01. Census 2021: targeted record swapping and cell key perturbation (ONS, 'Protecting personal data in Census 2021 results', https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/protectingpersonaldataincensus2021results). Small cells are perturbed, so sums of cells differ slightly from published totals; differences are reported in reconciliation.csv.
- **Decisions:** D-0039, D-0094

### C1: Children in need, reporting year 2025

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/children-in-need/2025>
- **Native geography:** UTLA25 · **period:** Year ending 31 March 2025 · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_cin_2025`: Children in need, reporting year 2025: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/9e627de0-ba01-442f-b6cf-f77d026a2ed3/files?fromPage=ReleaseDownloads>
- **Disclosure control:** suppression, rounding; tolerance 0 / 0.005. CIN data guidance: 'c' suppression (secondary suppression may apply); England and regional totals rounded to the nearest 10, LA figures unrounded. Checked: LA sums within 5 of the rounded England totals.
- **Symbols:** `c` = Suppressed to protect confidentiality (secondary suppression may apply) → `suppressed`; `z` = Not applicable → `not_applicable`; `x` = Not available → `not_published`; `u` = Low reliability → `suppressed`; `k` = Rounds to zero but is not zero → `suppressed`
- **Decisions:** D-0054, D-0095

### C2: Children looked after in England including adoptions, reporting year 2025

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/children-looked-after-in-england-including-adoptions/2025>
- **Native geography:** UTLA25 · **period:** Year ending 31 March 2025 · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_cla_2025`: Children looked after in England including adoptions, reporting year 2025: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/8c28aca0-6ab9-400b-b7de-c5fc7a148c2e/files?fromPage=ReleaseDownloads>
- **Disclosure control:** suppression, rounding; tolerance 0 / 0.005. CLA data guidance: 'c' suppression; national and regional figures rounded to the nearest 10, LA figures unrounded. Checked: LA sums within tolerance of the rounded England totals.
- **Symbols:** `c` = Suppressed to protect confidentiality (secondary suppression may apply) → `suppressed`; `z` = Not applicable → `not_applicable`; `x` = Not available → `not_published`; `k` = Rounds to zero but is not zero (percentage < 0.5%) → `suppressed`
- **Decisions:** D-0095

### C3: Children's social work workforce, at 30 September 2024

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/children-s-social-work-workforce/2024>
- **Native geography:** UTLA25 · **period:** At 30 September 2024 (off-period; kept as-is) · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_csww_2024`: Children's social work workforce, reporting year 2024: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/3362b622-8a39-4d69-ae14-52e156ad9953/files?fromPage=ReleaseDownloads>
- **Disclosure control:** suppression, rounding; tolerance 1 / 0.005. Children's social work workforce data guidance: 'c' suppression, 'low' rounds to 0; FTEs, rates and caseloads rounded to one decimal place.
- **Symbols:** `z` = Not applicable → `not_applicable`; `x` = Unavailable for unknown or other reasons → `not_published`; `c` = Suppressed to protect confidential information → `suppressed`; `low` = Rounds to 0 but is not 0 → `suppressed`; `u` = Low reliability → `suppressed`
- **Decisions:** D-0056, D-0095

### C4: LA and school expenditure (Section 251 outturn) 2024-25

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/la-and-school-expenditure/2024-25>
- **Native geography:** UTLA25 · **period:** Financial year 2024-25 · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_s251_2024_25`: LA and school expenditure, financial year 2024-25: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/d826124d-95f3-4b2f-a8ab-3425f84145fe/files?fromPage=ReleaseDownloads>
- **Disclosure control:** suppression; tolerance 1000 / 0.001. Section 251 outturn: unrounded GBP; 'c' (confidential) and 'x' (not available) take the GSS meanings. No published total is reconciled.
- **Symbols:** `c` = Confidential (GSS standard) → `suppressed`; `x` = Not available (GSS standard) → `not_published`
- **Decisions:** D-0054, D-0094, D-0095

### C5: Ofsted ILACS judgements and children's social care provider counts

- **Publisher:** Ofsted · <https://www.gov.uk/government/statistics/childrens-social-care-in-england-2025>
- **Native geography:** UTLA25 · **period:** At 31 March 2025 · **target:** `fact_service_area`
- **Staging code:** `stage/sheets.py` · **harmonise code:** `harmonise/phase3.py (ofsted)`
- **Files:**
  - `ofsted_csc_providers_2025`: Ofsted: Children's social care in England 2025, underlying data (providers and places at 31 March 2025) · <https://assets.publishing.service.gov.uk/media/688a3bd4a11f8599944092ab/Childrens_social_care_in_England_2025_underlying_data.ods>
  - `ofsted_la_outcomes_2025_03`: Ofsted: local authority (ILACS) inspection outcomes as at 31 March 2025, underlying data · <https://assets.publishing.service.gov.uk/media/68c2d38e838e7712ea2bfed3/Underlying_data_local_authority_inspection_outcomes_as_at_31_March_2025.ods>
- **Disclosure control:** none; tolerance 0 / 0. Ofsted provider list: every registered provider at 31 March 2025, no symbols. Checked: LA sums equal Ofsted's published national homes and places exactly.
- **Decisions:** D-0054, D-0095

### E1: Special educational needs in England, January 2025

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/special-educational-needs-in-england/2024-25>
- **Native geography:** UTLA25 · **period:** January 2025 school census · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_sen_2024_25`: Special educational needs in England, 2024/25: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/0ca90382-e848-4074-8406-b0db7a03a7f7/files?fromPage=ReleaseDownloads>
- **Disclosure control:** none; tolerance 0 / 0.001. SEN data guidance: no suppression or rounding applied; release convention 'x' not applicable, 'z' not available. Checked: LA sums equal the published England figures exactly.
- **Symbols:** `x` = Not applicable (E1 convention) → `not_applicable`; `z` = Not available (E1 convention) → `not_published`
- **Decisions:** D-0054, D-0058, D-0094, D-0095

### E2: Education, health and care plans (SEN2), January 2025

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/education-health-and-care-plans/2025>
- **Native geography:** UTLA25 · **period:** January 2025 (stock); calendar year 2024 (timeliness) · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_ehcp_2025`: Education, health and care plans, reporting year 2025: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/4c3eb898-bfd5-4081-9a96-4aa9abe32090/files?fromPage=ReleaseDownloads>
- **Disclosure control:** none; tolerance 0 / 0.001. SEN2 data guidance: no suppression; 'z' not applicable, 'x' unavailable (Lewisham 2024 timeliness withheld by DfE). Checked: LA sums equal the published England figures exactly.
- **Symbols:** `z` = Not applicable → `not_applicable`; `x` = Unavailable → `not_published`
- **Decisions:** D-0095

### E3: Pupil absence in schools in England, 2024/25

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/pupil-absence-in-schools-in-england/2024-25>
- **Native geography:** UTLA25 · **period:** Academic year 2024/25 · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_absence_2024_25`: Pupil absence in schools in England, 2024/25: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/3fabdc00-2c0b-4b4d-bfee-1b476b2323bc/files?fromPage=ReleaseDownloads>
- **Disclosure control:** none; tolerance 0 / 0.001. Absence data guidance: no suppression or rounding applied (except PLAA tables, not used). Checked: LA sums equal the published England figures exactly.
- **Symbols:** `x` = Not available → `not_published`; `z` = Not applicable (GSS standard) → `not_applicable`
- **Decisions:** D-0058, D-0095

### E4: Suspensions and permanent exclusions in England

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/suspensions-and-permanent-exclusions-in-england/2024-25>
- **Native geography:** UTLA25 · **period:** Academic year 2024/25 (check) · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_exclusions_2024_25`: Suspensions and permanent exclusions in England, 2024/25: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/0e388e4d-3748-49a4-984c-08dece27c222/files?fromPage=ReleaseDownloads>
- **Disclosure control:** none; tolerance 0 / 0.001. Exclusions data guidance: no suppression or rounding applied (except PLAA tables, not used). Checked: LA sums equal the published England figures exactly.
- **Symbols:** `x` = Not available → `not_published`; `z` = Not applicable → `not_applicable`
- **Decisions:** D-0058, D-0094, D-0095

### E5: Participation in education, training and NEET age 16 to 17 by local authority

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/participation-in-education-training-and-neet-age-16-to-17-by-local-authority/2024-25>
- **Native geography:** UTLA25 · **period:** End of 2024 (December 2024 to February 2025 average) · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_neet_16_17_2024_25`: Participation in education, training and NEET age 16 to 17 by local authority, 2024/25: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/f4ab16e8-ded3-4af3-4130-08dd91389bd2/files?fromPage=ReleaseDownloads>
- **Disclosure control:** suppression, rounding; tolerance 10 / 0.005. NEET data guidance: indicators on a cohort of 5 or fewer suppressed ('c'); national and regional numbers rounded to the nearest 10.
- **Symbols:** `c` = Suppressed to avoid disclosure (cohort of 5 or less) → `suppressed`; `z` = Not applicable → `not_applicable`
- **Decisions:** D-0095

### E6: Schools, pupils and their characteristics, January 2025 (FSM by pupil residence)

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/school-pupils-and-their-characteristics/2024-25>
- **Native geography:** UTLA25 · **period:** January 2025 school census · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_spc_2024_25`: Schools, pupils and their characteristics, 2024/25: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/63491b17-2037-4533-b719-d3656aaf6ed5/files?fromPage=ReleaseDownloads>
- **Disclosure control:** none; tolerance 0 / 0.001. School census (SPC) data guidance: no suppression or rounding applied; 'x' not applicable, 'z' unknown. Checked: LA sums equal the published England figures exactly.
- **Symbols:** `x` = Not applicable (SPC convention) → `not_applicable`; `z` = Unknown (SPC convention) → `not_published`
- **Decisions:** D-0054, D-0094, D-0095

### H1: Mental Health Services Monthly Statistics (MHSDS), March 2025 performance

- **Publisher:** NHS England · <https://digital.nhs.uk/data-and-information/publications/statistical/mental-health-services-monthly-statistics>
- **Native geography:** SICBL24 · **period:** March 2025 performance (rolling 12 months where applicable) · **target:** `fact_other_geography`
- **Staging code:** `stage/phase4.py` · **harmonise code:** `harmonise/phase4.py (mhsds)`
- **Files:**
  - `mhsds_final_202503`: MHSDS Monthly: End of Year Final March 2025 data file · <https://files.digital.nhs.uk/00/FE4D2C/MHSDS%20Data_MarFinal__2025.zip>
- **Disclosure control:** rounding, suppression; tolerance 5 / 0.01. MHSDS: '*' marks a suppressed small value; Sub-ICB and provider figures rounded to the nearest 5, England unrounded.
- **Symbols:** `*` = Suppressed (small number) → `suppressed`
- **Decisions:** D-0069, D-0070, D-0095

### H2: Fingertips: Child and Maternal Health profile (API)

- **Publisher:** Office for Health Improvement and Disparities · <https://fingertips.phe.org.uk/api>
- **Native geography:** UTLA25 · **period:** Latest period ending on or before 31 March 2025 · **target:** `fact_service_area`
- **Staging code:** `stage/fingertips.py` · **harmonise code:** `harmonise/phase3.py (fingertips)`
- **Files:**
  - `fingertips_h2_utla502`: Fingertips all-data CSV for the six H2 indicators, upper-tier LAs (area type 502) and England · <https://fingertips.phe.org.uk/api/all_data/csv/by_indicator_id?indicator_ids=90813,93930,92196,20401,20101,90284&child_area_type_id=502&parent_area_type_id=15>
- **Disclosure control:** suppression; tolerance 0 / 0.001. Fingertips: no symbols; a missing value carries a 'Value note' (suppressed small count, combined area, not presented), mapped to null_reason.
- **Decisions:** D-0054, D-0063, D-0095

### H3: NDTMS: adults in treatment who live with or are parents of children

- **Publisher:** Office for Health Improvement and Disparities · <https://www.ndtms.net/ParentsAndCarers>
- **Native geography:** UTLA25 · **period:** 2024-25 · **target:** `fact_service_area`
- **Staging code:** `—` · **harmonise code:** `not loaded (D-0091)`
- **Disclosure control:** suppression, rounding; tolerance 5 / 0.01. Not loaded (D-0091): disclosure control not assessed.
- **Decisions:** D-0054, D-0055, D-0090, D-0091, D-0094, D-0095

### Ho1: Statutory homelessness in England: detailed local authority tables (H-CLIC)

- **Publisher:** Ministry of Housing, Communities and Local Government · <https://www.gov.uk/government/statistics/statutory-homelessness-in-england-october-to-december-2025/statutory-homelessness-in-england-quarterly-technical-note>
- **Native geography:** LAD25 · **period:** Snapshot 31 March 2025 (TA); financial year 2024-25 (duties) · **target:** `fact_lad`
- **Staging code:** `stage/sheets.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `hclic_detailed_la_202503`: Statutory homelessness: detailed local authority tables, January to March 2025 · <https://assets.publishing.service.gov.uk/media/687e2060791bb4d8c309a01a/Detailed_LA_202503.ods>
  - `hclic_additional_ta_202503`: Statutory homelessness: additional temporary accommodation tables, January to March 2025 · <https://assets.publishing.service.gov.uk/media/688b288b1affbf4bedb7b125/Additional_TA_202503.ods>
  - `hclic_annual_la_2024_25`: Statutory homelessness: detailed local authority data, financial year 2024-25 (corrected) · <https://assets.publishing.service.gov.uk/media/6a2ff87cd95ffddb05d4b063/Statutory_Homelessness_Detailed_Local_Authority_Data_2024-2025_corrected.ods>
- **Disclosure control:** suppression, imputation; tolerance 0 / 0.05. H-CLIC table footnotes: '..' authority did not submit; '-' breakdown suppressed (fewer than 5); England and regional totals include MHCLG estimates for non-responding authorities, so LA sums fall short of them.
- **Symbols:** `..` = Authority with missing data (not submitted) → `not_published`; `-` = Breakdown suppressed: fewer than 5 → `suppressed` (hides ≤ 4)
- **Decisions:** D-0054, D-0095

### S1: data.police.uk street-level crime, April 2024 to March 2025

- **Publisher:** Home Office / police forces (data.police.uk) · <https://data.police.uk/data/>
- **Native geography:** point · **period:** FY 2024/25 · **target:** `fact_small_area`
- **Staging code:** `stage/police.py` · **harmonise code:** `harmonise/phase2.py (police, T4) in a child process (harmonise/isolated.py)`
- **Files:**
  - `police_archive_2026_08`: data.police.uk bulk archive 2026-08 (36 months to August 2026, all forces) · <https://data.police.uk/data/archive/2026-08.zip>
- **Disclosure control:** location_anonymisation; tolerance 0 / 0. data.police.uk: record-level counts with no suppression; points are snapped to anonymous map points, which affects location, not counts. Checked: published LSOA code agrees with point-in-polygon for 96.5% of England records (T4).
- **Decisions:** D-0015, D-0076

### S3: Youth justice statistics 2024 to 2025

- **Publisher:** Youth Justice Board / Ministry of Justice · <https://www.gov.uk/government/statistics/youth-justice-statistics-2024-to-2025>
- **Native geography:** YJS · **period:** Year ending March 2025 · **target:** `fact_other_geography`
- **Staging code:** `stage/phase4.py` · **harmonise code:** `harmonise/phase4.py (youth_justice, fte)`
- **Files:**
  - `yj_local_open_data_2024_25`: Youth justice statistics 2024 to 2025: local level open data tables · <https://assets.publishing.service.gov.uk/media/6984756b7da3dc19896c7dc4/Local_level_open_data_tables.zip>
  - `yj_supplementary_2024_25`: Youth justice statistics 2024 to 2025: supplementary tables · <https://assets.publishing.service.gov.uk/media/6981c8d2e8900d4c455f3730/Youth_Justice_Statistics_2024_to_2025_supplementary_tables.zip>
- **Disclosure control:** suppression; tolerance 0 / 0.005. YJB/MoJ supplementary tables: '..' fewer than ten first-time entrants (suppressed); '*' LA boundary change. Open data tables have no symbols.
- **Symbols:** `..` = Fewer than ten first-time entrants (suppressed) → `suppressed` (hides ≤ 9); `*` = Local authority boundary change; no figure on current boundaries → `not_published`
- **Decisions:** D-0069, D-0095

### S4: National Referral Mechanism and Duty to Notify statistics

- **Publisher:** Home Office · <https://www.gov.uk/government/collections/national-referral-mechanism-statistics>
- **Native geography:** UTLA25 · **period:** April 2024 - March 2025 · **target:** `fact_service_area or fact_other_geography (per verified geography)`
- **Staging code:** `stage/phase4.py` · **harmonise code:** `harmonise/phase4.py (nrm)`
- **Files:**
  - `nrm_tables_2024q2`: Modern slavery: NRM and DtN statistics, April to June 2024: data tables · <https://assets.publishing.service.gov.uk/media/66b37f6da3c2a28abb50de5e/national-referral-mechanism-statistics-uk-quarter-2-2024-apr-to-jun-tables.ods>
  - `nrm_tables_2024q3`: Modern slavery: NRM and DtN statistics, July to September 2024: data tables · <https://assets.publishing.service.gov.uk/media/672b9c4b094e4e60c466d257/national-referral-mechanism-statistics-uk-quarter-3-2024-jul-to-sep-tables.ods>
  - `nrm_tables_2024q4`: Modern slavery: NRM and DtN statistics, October to December 2024: data tables · <https://assets.publishing.service.gov.uk/media/67c5901cb0bb6528ee866ce1/national-referral-mechanism-statistics-uk-quarter-4-2024-oct-to-dec-tables.ods>
  - `nrm_tables_2025q1`: Modern slavery: NRM and DtN statistics, January to March 2025: data tables · <https://assets.publishing.service.gov.uk/media/681b6ba53f1c73824ee3e523/national-referral-mechanism-statistics-uk-quarter-1-2025-jan-to-mar-tables.ods>
- **Disclosure control:** none; tolerance 0 / 0.01. NRM quarterly tables: whole numbers, no symbols. Checked: police force rows sum to the published UK total in every quarter.
- **Decisions:** D-0069, D-0094, D-0095

### S5: Asylum support by local authority (Home Office immigration statistics)

- **Publisher:** Home Office · <https://www.gov.uk/government/statistical-data-sets/immigration-system-statistics-data-tables>
- **Native geography:** LAD25 · **period:** At 31 March 2025 · **target:** `fact_lad / fact_service_area (per published level)`
- **Staging code:** `stage/sheets.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `asy_d11_la_jun_2026`: Home Office immigration system statistics: asylum support local authority datasets, year ending June 2026 edition · <https://assets.publishing.service.gov.uk/media/6a85c5e654bcee010d514574/support-local-authority-datasets-jun-2026.xlsx>
- **Disclosure control:** none; tolerance 0 / 0.01. Asy_D11: counts of people, no symbols. Checked: England LA rows sum to the published English regional totals exactly (D-0084).
- **Decisions:** D-0054, D-0094, D-0095

## 5. Indicators

Each indicator's definition, formula, transformation configuration (the exact entry in
`config/category_maps.yaml`, or the code that builds it) and the decisions that shaped it.

### Theme: population

#### `ons_sape_population`: Population

- **Sources:** P1 · **measure:** count · **native level:** small_area · **polarity:** neutral
- **Value:** ONS mid-year Small Area Population Estimates for LSOA21, single year of age (0 to 90+) by sex. · CI: none · aggregation: sum
- **Built in code:** harmonise/population.py: ONS SAPE single years of age by sex, LSOA (P1); MSOA by exact sum

#### `ons_mye_population`: Population

- **Sources:** P1b · **measure:** count · **native level:** lad · **polarity:** neutral
- **Value:** ONS mid-year population estimates, single year of age (0 to 90+) by sex, as published for LAD, UTLA and England. · CI: none · aggregation: sum
- **Built in code:** harmonise/population.py: ONS mid-year estimates by single year and sex, LAD/UTLA/England (P1b)

#### `census21_population_by_ethnicity`: Population by ethnic group (Census 2021)

- **Sources:** P4 · **measure:** count · **native level:** small_area · **polarity:** neutral
- **Value:** Census 2021 usual residents by ethnic group (most detailed classification ONS releases for LSOA x age) and age. · CI: none · aggregation: sum
- **Map entry** `census.P4`:

```yaml
file_prefix: p4_eth6a_age7a
table: ethnic_group_tb_6a x resident_age_7a
ethnicity_dim: dim1
age_dim: dim2
age_map: CENSUS_AGE_7A
indicator: census21_population_by_ethnicity
```

#### `census21_usual_residents_by_age`: Population (Census 2021)

- **Sources:** F7 · **measure:** count · **native level:** small_area · **polarity:** neutral
- **Value:** Total usual residents by age, taken from the same Census custom tables as the disability and unpaid care counts. · CI: none · aggregation: sum
- **Map entry** `census.F7a.indicators.census21_usual_residents_by_age`:

```yaml
- age_band: '0_24'
  dim1:
  - '1'
  - '2'
  - '3'
  - '4'
  dim2:
  - '1'
  - '2'
  - '3'
  - '4'
  - '5'
```
- **Map entry** `census.F7b.indicators.census21_usual_residents_by_age`:

```yaml
- age_band: src_5_24
  dim1:
  - '1'
  - '2'
  - '3'
  - '4'
  - '5'
  - '6'
  dim2:
  - '1'
```

#### `nhse_gp_registered_patients`: GP-registered population

- **Sources:** G3b · **measure:** count · **native level:** SICBL24 · **polarity:** neutral
- **Value:** Patients registered at GP practices in England on 1 April 2025, by Sub-ICB location (April 2024 configuration), single year of age (0 to 95+, stored to 90+) and sex, as published by NHS England. · CI: none · aggregation: sum
- **Built in code:** harmonise/phase4.py (gp_registered): G3b single years by Sub-ICB; England as the sum
- **Decisions:** D-0070

#### `dfe_pupils_by_ethnicity`: Pupils by ethnic group

- **Sources:** P7 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Headcount of pupils in state-funded schools by ethnicity (DfE classification), January 2025. · CI: none · aggregation: sum
- **Map entry** `tables.P7.measures[0]`:

```yaml
indicator: dfe_pupils_by_ethnicity
table: spc_pupils_ethnicity_and_language
column: headcount
where:
  phase_type_grouping: Total
  language: Total
age_band: src_pupils_all
period:
- 2025-01-16
- 2025-01-16
ethnicity:
  column: ethnicity_minor
  classification: dfe_ethnicity
```

#### `dfe_pupils_on_roll`: Pupils

- **Sources:** E6 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Number of pupils used for FSM in performance tables, by LA of school, January 2025 school census (SPC table spc_pupils_fsm). · CI: none · aggregation: sum
- **Map entry** `tables.E6.measures[0]`:

```yaml
indicator: dfe_pupils_on_roll
table: spc_pupils_fsm
column: headcount
where:
  phase_type_grouping: Total
  fsm: number of pupils (used for FSM in Performance Tables)
age_band: src_pupils_all
period:
- 2025-01-16
- 2025-01-16
```
- **Decisions:** D-0058

#### `mhclg_iod25_population`: Population used in the IoD 2025

- **Sources:** D1 · **measure:** count · **native level:** small_area · **polarity:** neutral
- **Value:** Population denominators published with IoD 2025, by LSOA (total, and the child and older-people bases where published). · CI: none · aggregation: sum
- **Map entry** `iod_lsoa[21]`:

```yaml
indicator: mhclg_iod25_population
kind: count
column: 'Total population: mid 2022'
age_band: all_ages
period: population
```
- **Map entry** `iod_lsoa[22]`:

```yaml
indicator: mhclg_iod25_population
kind: count
column: 'Dependent Children aged 0-15: mid 2022'
age_band: src_0_15
period: population
```

#### `census21_households_dependent_children`: Households with dependent children

- **Sources:** F6 · **measure:** count · **native level:** small_area · **polarity:** neutral
- **Value:** Census 2021 households containing at least one dependent child (aged 0-15, or 16-18 in full-time education and living with parent(s)). · CI: none · aggregation: sum
- **Map entry** `census.F6.indicators.census21_households_dependent_children`:

```yaml
- age_band: na
  dim1:
  - '5'
  - '8'
  - '10'
  - '13'
  dim2:
  - '1'
  - '2'
  - '3'
  - '4'
```

#### `dfe_cin_episodes_with_assessment_factors`: Assessments with factors recorded

- **Sources:** C1 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Episodes with an assessment completed in the year that have assessment factor information (Episodes_with_assessment_factor), DfE CIN table C3. · CI: none · aggregation: sum
- **Map entry** `tables.C1.measures[6]`:

```yaml
indicator: dfe_cin_episodes_with_assessment_factors
table: c3_factors_identified
column: Episodes_with_assessment_factor
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```
- **Decisions:** D-0056

#### `dfe_cla_distance_known_at_31mar`: Children in care (distance known)

- **Sources:** C2 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** CLA at 31 March 2025 placed 20 miles or less from home + placed more than 20 miles from home (two published cells of one DfE table). · CI: none · aggregation: sum
- **Map entry** `tables.C2.measures[5]`:

```yaml
indicator: dfe_cla_distance_known_at_31mar
table: la_cla_on_31_march_by_characteristics
column: children_count
sum_rows: true
where:
  characteristic: Distance between home and placement
  breakdown:
  - Placed 20 miles or less from home
  - Placed more than 20 miles from home
age_band: '0_17'
period:
- 2025-03-31
- 2025-03-31
```
- **Decisions:** D-0057

#### `dfe_cla_stability_base_at_31mar`: Children in care (stability base)

- **Sources:** C2 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** 'Total children' for 'CLA on 31 March' in DfE table LA_CLA_placement_stability, 2025. · CI: none · aggregation: sum
- **Map entry** `tables.C2.measures[7]`:

```yaml
indicator: dfe_cla_stability_base_at_31mar
table: LA_CLA_placement_stability
column: children_count
where:
  cla_group: CLA on 31 March
  placement_stability: Total children
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```
- **Decisions:** D-0057

#### `dfe_pupils_total_sen_publication`: Pupils (SEN publication)

- **Sources:** E1 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Total pupils (phase Total, SEN status Total, primary need Total) in SEN in England table sen_ncyear_, January 2025: the same table as every SEN numerator. · CI: none · aggregation: sum
- **Map entry** `tables.E1.measures[0]`:

```yaml
indicator: dfe_pupils_total_sen_publication
table: sen_ncyear_
column: number_of_pupils
where:
  phase_type_grouping: Total
  sen_status: Total
  sen_primary_need: Total
age_band: src_pupils_all
period:
- 2025-01-16
- 2025-01-16
```

#### `dfe_absence_enrolments`: Pupil enrolments

- **Sources:** E3 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Pupil enrolments, academic year 2024/25, as published in the absence statistics. · CI: none · aggregation: sum
- **Map entry** `tables.E3.measures[0]`:

```yaml
indicator: dfe_absence_enrolments
table: 1_Absence_3term_nat_reg_la
column: enrolments
where:
  education_phase: Total
age_band: src_pupils_all
period:
- 2024-09-01
- 2025-07-31
```

#### `dfe_exclusions_headcount`: Pupils (exclusions publication)

- **Sources:** E4 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Pupil headcount as published in the suspensions and exclusions statistics. · CI: none · aggregation: sum
- **Map entry** `tables.E4.measures[0]`:

```yaml
indicator: dfe_exclusions_headcount
table: exc_nat_region_la
column: headcount
where:
  education_phase: Total
age_band: src_pupils_all
period:
- 2024-09-01
- 2025-07-31
```

#### `dfe_neet_cohort_16_17`: 16-17 year olds known to the council

- **Sources:** E5 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** 16-17 year olds known to the LA (resident), average of December 2024 to February 2025, as published (avgcohort). · CI: none · aggregation: none
- **Map entry** `tables.E5.measures[0]`:

```yaml
indicator: dfe_neet_cohort_16_17
table: ud_neet_characteristics
column: avgcohort
kind: value
where:
  Age: 16-17
  Characteristic_grouping: Total
  Characteristic: Total
age_band: '16_17'
period:
- 2024-12-01
- 2025-02-28
```
- **Decisions:** D-0067

#### `ho_asylum_support_recipients`: People receiving asylum support

- **Sources:** S5 · **measure:** count · **native level:** lad · **polarity:** neutral
- **Value:** People in receipt of asylum support (by support type) at 31 March 2025, by LA. · CI: none · aggregation: sum
- **Map entry** `tables.S5.measures[0]`:

```yaml
indicator: ho_asylum_support_recipients
table: asy_d11_20250331
column: People
sum_rows: true
age_band: all_ages
period:
- 2025-03-31
- 2025-03-31
absent_areas_zero:
  table: asy_d11_regions
  label: Row Labels
  column: 31 Mar 2025
  england:
  - East Midlands
  - East of England
  - London
  - North East
  - North West
  - South East
  - South West
  - West Midlands
  - Yorkshire and The Humber
  zero:
  - N/A - Subsistence Only (Dec 2023 - Dec 2024)
```
- **Decisions:** D-0084

### Theme: deprivation

#### `mhclg_iod25_imd_score`: Index of Multiple Deprivation (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IMD 2025 score for LSOA21: weighted combination of seven exponentially transformed domain scores (MHCLG method). · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[0]`:

```yaml
indicator: mhclg_iod25_imd_score
kind: value
column: Index of Multiple Deprivation (IMD) Score
```

#### `mhclg_iod25_imd_rank`: Index of Multiple Deprivation (rank)

- **Sources:** D1 · **measure:** rank · **native level:** small_area · **polarity:** higher_better
- **Value:** IMD 2025 rank of LSOA21 among all English LSOAs (1 = most deprived). · CI: none · aggregation: none
- **Map entry** `iod_lsoa[1]`:

```yaml
indicator: mhclg_iod25_imd_rank
kind: value
column: Index of Multiple Deprivation (IMD) Rank (where 1 is most deprived)
```

#### `mhclg_iod25_imd_decile`: Index of Multiple Deprivation (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IMD 2025 decile of LSOA21 (1 = most deprived 10% of LSOAs nationally). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[2]`:

```yaml
indicator: mhclg_iod25_imd_decile
kind: value
column: Index of Multiple Deprivation (IMD) Decile (where 1 is most deprived 10% of LSOAs)
```

#### `mhclg_iod25_income_score`: Income deprivation (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD 2025 Income Deprivation domain score: proportion of the population experiencing income deprivation. · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[3]`:

```yaml
indicator: mhclg_iod25_income_score
kind: value
column: Income Score (rate)
```

#### `mhclg_iod25_income_decile`: Income deprivation (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IoD 2025 Income domain decile (1 = most deprived 10%). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[4]`:

```yaml
indicator: mhclg_iod25_income_decile
kind: value
column: Income Decile (where 1 is most deprived 10% of LSOAs)
```

#### `mhclg_iod25_employment_score`: Employment deprivation (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD 2025 Employment Deprivation domain score: proportion of the working-age population involuntarily excluded from the labour market. · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[5]`:

```yaml
indicator: mhclg_iod25_employment_score
kind: value
column: Employment Score (rate)
```

#### `mhclg_iod25_employment_decile`: Employment deprivation (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IoD 2025 Employment domain decile (1 = most deprived 10%). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[6]`:

```yaml
indicator: mhclg_iod25_employment_decile
kind: value
column: Employment Decile (where 1 is most deprived 10% of LSOAs)
```

#### `mhclg_iod25_education_score`: Education, skills and training deprivation (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD 2025 Education, Skills and Training Deprivation domain score (children and young people sub-domain plus adult skills sub-domain). · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[7]`:

```yaml
indicator: mhclg_iod25_education_score
kind: value
column: Education, Skills and Training Score
```

#### `mhclg_iod25_education_decile`: Education, skills and training deprivation (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IoD 2025 Education, Skills and Training domain decile (1 = most deprived 10%). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[8]`:

```yaml
indicator: mhclg_iod25_education_decile
kind: value
column: Education, Skills and Training Decile (where 1 is most deprived 10% of LSOAs)
```

#### `mhclg_iod25_health_score`: Health deprivation and disability (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD 2025 Health Deprivation and Disability domain score. · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[9]`:

```yaml
indicator: mhclg_iod25_health_score
kind: value
column: Health Deprivation and Disability Score
```

#### `mhclg_iod25_health_decile`: Health deprivation and disability (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IoD 2025 Health Deprivation and Disability domain decile (1 = most deprived 10%). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[10]`:

```yaml
indicator: mhclg_iod25_health_decile
kind: value
column: Health Deprivation and Disability Decile (where 1 is most deprived 10% of LSOAs)
```

#### `mhclg_iod25_crime_score`: Crime deprivation (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD 2025 Crime domain score (recorded violence, burglary, theft and criminal damage, modelled). · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[11]`:

```yaml
indicator: mhclg_iod25_crime_score
kind: value
column: Crime Score
```

#### `mhclg_iod25_crime_decile`: Crime deprivation (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IoD 2025 Crime domain decile (1 = most deprived 10%). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[12]`:

```yaml
indicator: mhclg_iod25_crime_decile
kind: value
column: Crime Decile (where 1 is most deprived 10% of LSOAs)
```

#### `mhclg_iod25_barriers_score`: Barriers to housing and services (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD 2025 Barriers to Housing and Services domain score (geographical barriers and wider barriers sub-domains). · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[13]`:

```yaml
indicator: mhclg_iod25_barriers_score
kind: value
column: Barriers to Housing and Services Score
```

#### `mhclg_iod25_barriers_decile`: Barriers to housing and services (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IoD 2025 Barriers domain decile (1 = most deprived 10%). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[14]`:

```yaml
indicator: mhclg_iod25_barriers_decile
kind: value
column: Barriers to Housing and Services Decile (where 1 is most deprived 10% of LSOAs)
```

#### `mhclg_iod25_living_env_score`: Living environment deprivation (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD 2025 Living Environment Deprivation domain score (indoors and outdoors sub-domains). · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[15]`:

```yaml
indicator: mhclg_iod25_living_env_score
kind: value
column: Living Environment Score
```

#### `mhclg_iod25_living_env_decile`: Living environment deprivation (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IoD 2025 Living Environment domain decile (1 = most deprived 10%). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[16]`:

```yaml
indicator: mhclg_iod25_living_env_decile
kind: value
column: Living Environment Decile (where 1 is most deprived 10% of LSOAs)
```

#### `mhclg_iod25_imd_la_avg_score`: Index of Multiple Deprivation: average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IMD 2025 LSOA scores, as published by MHCLG for LAD and UTLA. · CI: none · aggregation: none
- **Map entry** `iod_la[0]`:

```yaml
indicator: mhclg_iod25_imd_la_avg_score
sheet: IMD
measure: IMD - Average score
```

#### `mhclg_iod25_imd_la_avg_rank`: Index of Multiple Deprivation: average rank

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IMD 2025 LSOA ranks, as published by MHCLG (IoD 2025 File 10/11; higher = more deprived, verified on inspection, D-0044). · CI: none · aggregation: none
- **Map entry** `iod_la[1]`:

```yaml
indicator: mhclg_iod25_imd_la_avg_rank
sheet: IMD
measure: IMD - Average rank
```

#### `mhclg_iod25_imd_la_extent`: Index of Multiple Deprivation: extent

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** MHCLG extent measure: proportion of the LA population living in the most deprived LSOAs nationally (weighted, top 30%). · CI: none · aggregation: none
- **Map entry** `iod_la[2]`:

```yaml
indicator: mhclg_iod25_imd_la_extent
sheet: IMD
measure: IMD25 - Extent
```

#### `mhclg_iod25_imd_la_local_concentration`: Index of Multiple Deprivation: local concentration

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average rank of the LA's most deprived LSOAs containing 10% of its population (MHCLG; higher = more deprived in IoD 2025, D-0044). · CI: none · aggregation: none
- **Map entry** `iod_la[3]`:

```yaml
indicator: mhclg_iod25_imd_la_local_concentration
sheet: IMD
measure: IMD25 - Local concentration
```

#### `mhclg_iod25_imd_la_prop_most_deprived_10pct`: Neighbourhoods in England's most deprived 10%

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in IMD 2025 decile 1, as published by MHCLG. · CI: none · aggregation: none
- **Map entry** `iod_la[4]`:

```yaml
indicator: mhclg_iod25_imd_la_prop_most_deprived_10pct
sheet: IMD
measure: IMD - Proportion of LSOAs in most deprived 10% nationally
```

#### `mhclg_iod25_income_la_avg_score`: Income deprivation: average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IoD 2025 Income domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[8]`:

```yaml
indicator: mhclg_iod25_income_la_avg_score
sheet: Income
measure: Income - Average score
```

#### `mhclg_iod25_income_la_prop_most_deprived_10pct`: Income deprivation: neighbourhoods in England's most deprived 10%

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Income domain, as published by MHCLG (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[9]`:

```yaml
indicator: mhclg_iod25_income_la_prop_most_deprived_10pct
sheet: Income
measure: Income - Proportion of LSOAs in most deprived 10% nationally
```

#### `mhclg_iod25_employment_la_avg_score`: Employment deprivation: average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IoD 2025 Employment domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[10]`:

```yaml
indicator: mhclg_iod25_employment_la_avg_score
sheet: Employment
measure: Employment - Average score
```

#### `mhclg_iod25_employment_la_prop_most_deprived_10pct`: Employment deprivation: neighbourhoods in England's most deprived 10%

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Employment domain, as published by MHCLG (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[11]`:

```yaml
indicator: mhclg_iod25_employment_la_prop_most_deprived_10pct
sheet: Employment
measure: Employment - Proportion of LSOAs in most deprived 10% nationally
```

#### `mhclg_iod25_education_la_avg_score`: Education, skills and training deprivation: average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IoD 2025 Education, Skills and Training domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[12]`:

```yaml
indicator: mhclg_iod25_education_la_avg_score
sheet: Education
measure: Education, Skills and Training - Average score
```

#### `mhclg_iod25_education_la_prop_most_deprived_10pct`: Education, skills and training deprivation: neighbourhoods in England's most deprived 10%

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Education, Skills and Training domain, as published by MHCLG (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[13]`:

```yaml
indicator: mhclg_iod25_education_la_prop_most_deprived_10pct
sheet: Education
measure: Education, Skills and Training - Proportion of LSOAs in most deprived 10% nationally
```

#### `mhclg_iod25_health_la_avg_score`: Health deprivation and disability: average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IoD 2025 Health Deprivation and Disability domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[14]`:

```yaml
indicator: mhclg_iod25_health_la_avg_score
sheet: Health
measure: Health Deprivation and Disability - Average score
```

#### `mhclg_iod25_health_la_prop_most_deprived_10pct`: Health deprivation and disability: neighbourhoods in England's most deprived 10%

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Health Deprivation and Disability domain, as published by MHCLG (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[15]`:

```yaml
indicator: mhclg_iod25_health_la_prop_most_deprived_10pct
sheet: Health
measure: Health Deprivation and Disability - Proportion of LSOAs in most deprived 10% nationally
```

#### `mhclg_iod25_crime_la_avg_score`: Crime (IoD domain): average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IoD 2025 Crime domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[16]`:

```yaml
indicator: mhclg_iod25_crime_la_avg_score
sheet: Crime
measure: Crime - Average score
```

#### `mhclg_iod25_crime_la_prop_most_deprived_10pct`: Crime (IoD domain): neighbourhoods in England's most deprived 10%

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Crime domain, as published by MHCLG (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[17]`:

```yaml
indicator: mhclg_iod25_crime_la_prop_most_deprived_10pct
sheet: Crime
measure: Crime - Proportion of LSOAs in most deprived 10% nationally
```

#### `mhclg_iod25_barriers_la_avg_score`: Barriers to housing and services: average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IoD 2025 Barriers to Housing and Services domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[18]`:

```yaml
indicator: mhclg_iod25_barriers_la_avg_score
sheet: Barriers
measure: Barriers to Housing and Services - Average score
```

#### `mhclg_iod25_barriers_la_prop_most_deprived_10pct`: Barriers to housing and services: neighbourhoods in England's most deprived 10%

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Barriers to Housing and Services domain, as published by MHCLG (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[19]`:

```yaml
indicator: mhclg_iod25_barriers_la_prop_most_deprived_10pct
sheet: Barriers
measure: Barriers to Housing and Services - Proportion of LSOAs in most deprived 10% nationally
```

#### `mhclg_iod25_living_env_la_avg_score`: Living environment deprivation: average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IoD 2025 Living Environment domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[20]`:

```yaml
indicator: mhclg_iod25_living_env_la_avg_score
sheet: Living
measure: Living Environment - Average score
```

#### `mhclg_iod25_living_env_la_prop_most_deprived_10pct`: Living environment deprivation: neighbourhoods in England's most deprived 10%

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Living Environment domain, as published by MHCLG (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[21]`:

```yaml
indicator: mhclg_iod25_living_env_la_prop_most_deprived_10pct
sheet: Living
measure: Living Environment - Proportion of LSOAs in most deprived 10% nationally
```

### Theme: child poverty

#### `mhclg_iod25_idaci_score`: Income deprivation affecting children (IDACI)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IDACI 2025 score: proportion of children aged 0-15 living in income-deprived families (MHCLG definition, benefit and tax credit based). · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[17]`:

```yaml
indicator: mhclg_iod25_idaci_score
kind: value
column: Income Deprivation Affecting Children Index (IDACI) Score (rate)
age_band: src_0_15
```

#### `mhclg_iod25_idaci_rank`: Income deprivation affecting children (rank)

- **Sources:** D1 · **measure:** rank · **native level:** small_area · **polarity:** higher_better
- **Value:** IDACI 2025 rank of LSOA21 (1 = most deprived). · CI: none · aggregation: none
- **Map entry** `iod_lsoa[18]`:

```yaml
indicator: mhclg_iod25_idaci_rank
kind: value
column: Income Deprivation Affecting Children Index (IDACI) Rank (where 1 is most deprived)
age_band: src_0_15
```

#### `mhclg_iod25_idaci_decile`: Income deprivation affecting children (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IDACI 2025 decile of LSOA21 (1 = most deprived 10%). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[19]`:

```yaml
indicator: mhclg_iod25_idaci_decile
kind: value
column: Income Deprivation Affecting Children Index (IDACI) Decile (where 1 is most deprived 10% of LSOAs)
age_band: src_0_15
```

#### `mhclg_iod25_idaci_la_avg_score`: Income deprivation affecting children: average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IDACI 2025 LSOA scores, as published by MHCLG. · CI: none · aggregation: none
- **Map entry** `iod_la[5]`:

```yaml
indicator: mhclg_iod25_idaci_la_avg_score
sheet: IDACI
measure: IDACI - Average score
age_band: src_0_15
```

#### `mhclg_iod25_idaci_la_avg_rank`: Income deprivation affecting children: average rank

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IDACI 2025 LSOA ranks, as published by MHCLG (higher = more deprived in IoD 2025, D-0044). · CI: none · aggregation: none
- **Map entry** `iod_la[6]`:

```yaml
indicator: mhclg_iod25_idaci_la_avg_rank
sheet: IDACI
measure: IDACI - Average rank
age_band: src_0_15
```

#### `mhclg_iod25_idaci_la_prop_most_deprived_10pct`: Neighbourhoods in England's most deprived 10% for child income

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in IDACI 2025 decile 1, as published by MHCLG. · CI: none · aggregation: none
- **Map entry** `iod_la[7]`:

```yaml
indicator: mhclg_iod25_idaci_la_prop_most_deprived_10pct
sheet: IDACI
measure: IDACI - Proportion of LSOAs in most deprived 10% nationally
age_band: src_0_15
```

#### `dwp_cilif_relative_bhc`: Children in relative low income families

- **Sources:** F1 · **measure:** count · **native level:** lad · **polarity:** higher_worse
- **Value:** DWP CiLIF: children (under 16, or 16-19 in non-advanced education) in families with equivalised household income below 60% of contemporary median, BHC, calibrated to the national survey (HBAI). · CI: none · aggregation: sum
- **Map entry** `statxplore.F1[0]`:

```yaml
file_prefix: f1_cilif_rel
indicator: dwp_cilif_relative_bhc
age_field: Age of Child (years and bands)
age_map: F1
```
- **Map entry** `tables.F1.measures[0]`:

```yaml
indicator: dwp_cilif_relative_bhc
table: cilif_bhc_la
column: relative_count
age_band: src_0_15
period:
- 2024-04-01
- 2025-03-31
```

#### `dwp_cilif_relative_bhc_pct`: Children in relative low income families (%)

- **Sources:** F1 · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Percentage as published by DWP: children aged 0-15 in relative low income families / ONS mid-2024 population aged 0-15 x 100 (DWP CiLIF note 3). DWP publishes it for lower-tier and unitary councils; for the 21 county councils it is computed by DWP's method from the summed district counts (D-0085). · CI: none · aggregation: none
- **Publisher's method (L3):** where no value is published, `dwp_cilif_relative_bhc` (src_0_15) ÷ `ons_mye_population` × 100, only after this reproduces every published value (D-0085)
- **Map entry** `tables.F1.measures[1]`:

```yaml
indicator: dwp_cilif_relative_bhc_pct
table: cilif_bhc_la
column: relative_pct
kind: value
scale: 100
age_band: src_0_15
period:
- 2024-04-01
- 2025-03-31
```

#### `dwp_cilif_absolute_bhc`: Children in absolute low income families

- **Sources:** F1 · **measure:** count · **native level:** lad · **polarity:** higher_worse
- **Value:** DWP CiLIF absolute low income, BHC: equivalised household income below 60% of the FYE 2025 median held constant in real terms, calibrated to HBAI. DWP moved the reference year from FYE 2011 to FYE 2025 in this release and revised the back series. · CI: none · aggregation: sum
- **Map entry** `statxplore.F1[1]`:

```yaml
file_prefix: f1_cilif_abs
indicator: dwp_cilif_absolute_bhc
age_field: Age of Child (years and bands)
age_map: F1
```
- **Map entry** `tables.F1.measures[2]`:

```yaml
indicator: dwp_cilif_absolute_bhc
table: cilif_bhc_la
column: absolute_count
age_band: src_0_15
period:
- 2024-04-01
- 2025-03-31
```

#### `dwp_cilif_absolute_bhc_pct`: Children in absolute low income families (%)

- **Sources:** F1 · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Percentage as published by DWP alongside CiLIF counts. · CI: none · aggregation: none
- **Publisher's method (L3):** where no value is published, `dwp_cilif_absolute_bhc` (src_0_15) ÷ `ons_mye_population` × 100, only after this reproduces every published value (D-0085)
- **Map entry** `tables.F1.measures[3]`:

```yaml
indicator: dwp_cilif_absolute_bhc_pct
table: cilif_bhc_la
column: absolute_pct
kind: value
scale: 100
age_band: src_0_15
period:
- 2024-04-01
- 2025-03-31
```

#### `dwp_uc_households_with_children`: Households with children on Universal Credit

- **Sources:** F2 · **measure:** count · **native level:** small_area · **polarity:** higher_worse
- **Value:** Count of households on UC (payment) with at least one dependent child, by LSOA21, March 2025. · CI: none · aggregation: sum
- **Map entry** `statxplore.F2`:

```yaml
indicator: dwp_uc_households_with_children
age_band: na
```
- **Decisions:** D-0087

#### `dfe_fsm_eligible_pupils`: Pupils eligible for free school meals

- **Sources:** E6 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Pupils known to be eligible for free school meals ÷ `dfe_pupils_on_roll` (Pupils on roll used for FSM in performance tables (same table, same school-location basis)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.E6.measures[1]`:

```yaml
indicator: dfe_fsm_eligible_pupils
table: spc_pupils_fsm
column: headcount
where:
  phase_type_grouping: Total
  fsm: known to be eligible for free school meals (used for FSM in Performance Tables)
age_band: src_pupils_all
period:
- 2025-01-16
- 2025-01-16
```
- **Decisions:** D-0058

### Theme: education

#### `mhclg_iod25_education_cyp_subdomain_score`: Children's education deprivation (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD 2025 Education domain, Children and Young People sub-domain score (attainment, absence, staying on, entry to higher education). · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[20]`:

```yaml
indicator: mhclg_iod25_education_cyp_subdomain_score
kind: value
column: Children and Young People Sub-domain Score
```

#### `dfe_care_leavers_19_21_neet`: Care leavers not in education, employment or training

- **Sources:** C2 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Care leavers 19-21 NEET ÷ `dfe_care_leavers_19_21` (Care leavers aged 19-21) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C2.measures[10]`:

```yaml
indicator: dfe_care_leavers_19_21_neet
table: la_care_leavers_activity
column: care_leaver_count
where:
  care_leaver_age: 19 to 21 years
  breakdown: Total not in education, employment or training
age_band: src_19_21
period:
- 2024-04-01
- 2025-03-31
```

#### `dfe_pupils_with_ehcp`: Pupils with an EHC plan

- **Sources:** E1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Pupils with EHC plan ÷ `dfe_pupils_total_sen_publication` (Total pupils (same file)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.E1.measures[1]`:

```yaml
indicator: dfe_pupils_with_ehcp
table: sen_ncyear_
column: number_of_pupils
where:
  phase_type_grouping: Total
  sen_status: Education, Health and Care plans
  sen_primary_need: Total
age_band: src_pupils_all
period:
- 2025-01-16
- 2025-01-16
```

#### `dfe_pupils_sen_support`: Pupils receiving SEN support

- **Sources:** E1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Pupils with SEN support ÷ `dfe_pupils_total_sen_publication` (Total pupils (same file)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.E1.measures[2]`:

```yaml
indicator: dfe_pupils_sen_support
table: sen_ncyear_
column: number_of_pupils
where:
  phase_type_grouping: Total
  sen_status: SEN support / SEN without an EHC plan
  sen_primary_need: Total
age_band: src_pupils_all
period:
- 2025-01-16
- 2025-01-16
```

#### `dfe_sen_primary_need_asd`: Pupils with autism as their main need

- **Sources:** E1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Pupils with SEN, primary need ASD ÷ `dfe_pupils_total_sen_publication` (Total pupils) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.E1.measures[4]`:

```yaml
indicator: dfe_sen_primary_need_asd
table: sen_ncyear_
column: number_of_pupils
where:
  phase_type_grouping: Total
  sen_status: Total
  sen_primary_need: Autistic Spectrum Disorder
age_band: src_pupils_all
period:
- 2025-01-16
- 2025-01-16
```

#### `dfe_persistent_absence`: Persistent absence from school

- **Sources:** E3 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Persistently absent enrolments ÷ `dfe_absence_enrolments` (Enrolments (same file)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.E3.measures[1]`:

```yaml
indicator: dfe_persistent_absence
table: 1_Absence_3term_nat_reg_la
column: enrolments_pa_10_exact
where:
  education_phase: Total
age_band: src_pupils_all
period:
- 2024-09-01
- 2025-07-31
```

#### `dfe_severe_absence`: Severe absence from school

- **Sources:** E3 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Severely absent enrolments ÷ `dfe_absence_enrolments` (Enrolments (same file)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.E3.measures[2]`:

```yaml
indicator: dfe_severe_absence
table: 1_Absence_3term_nat_reg_la
column: enrolments_pa_50_exact
where:
  education_phase: Total
age_band: src_pupils_all
period:
- 2024-09-01
- 2025-07-31
```

#### `dfe_suspensions`: Suspensions from school

- **Sources:** E4 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Suspensions ÷ `dfe_exclusions_headcount` (Pupil headcount (same file)) × 100; CI: byar; aggregation: sum_then_divide
- **Map entry** `tables.E4.measures[1]`:

```yaml
indicator: dfe_suspensions
table: exc_nat_region_la
column: suspension
where:
  education_phase: Total
age_band: src_pupils_all
period:
- 2024-09-01
- 2025-07-31
```

#### `dfe_permanent_exclusions`: Permanent exclusions from school

- **Sources:** E4 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Permanent exclusions ÷ `dfe_exclusions_headcount` (Pupil headcount (same file)) × 10000; CI: byar; aggregation: sum_then_divide
- **Map entry** `tables.E4.measures[2]`:

```yaml
indicator: dfe_permanent_exclusions
table: exc_nat_region_la
column: perm_excl
where:
  education_phase: Total
age_band: src_pupils_all
period:
- 2024-09-01
- 2025-07-31
```

#### `dfe_neet_16_17`: 16-17 year olds not in education, employment or training

- **Sources:** E5 · **measure:** percent_published · **native level:** service_area · **polarity:** higher_worse
- **Formula:** 16-17 NEET; CI: none; aggregation: none
- **Map entry** `tables.E5.measures[1]`:

```yaml
indicator: dfe_neet_16_17
table: ud_neet_characteristics
column: NEETprop
kind: value
where:
  Age: 16-17
  Characteristic_grouping: Total
  Characteristic: Total
age_band: '16_17'
period:
- 2024-12-01
- 2025-02-28
```
- **Decisions:** D-0067

#### `dfe_neet_or_not_known_16_17`: 16-17 year olds NEET or activity not known

- **Sources:** E5 · **measure:** percent_published · **native level:** service_area · **polarity:** higher_worse
- **Formula:** 16-17 NEET + not known; CI: none; aggregation: none
- **Map entry** `tables.E5.measures[2]`:

```yaml
indicator: dfe_neet_or_not_known_16_17
table: ud_neet_characteristics
column: NEETNKprop
kind: value
where:
  Age: 16-17
  Characteristic_grouping: Total
  Characteristic: Total
age_band: '16_17'
period:
- 2024-12-01
- 2025-02-28
```
- **Decisions:** D-0067

### Theme: family risk

#### `census21_lone_parent_households_dep_children`: Lone-parent households

- **Sources:** F6 · **measure:** proportion · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Lone-parent households with dependent children ÷ `census21_households_dependent_children` (Households with dependent children (same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `census.F6.indicators.census21_lone_parent_households_dep_children`:

```yaml
- age_band: na
  dim1:
  - '10'
  dim2:
  - '1'
  - '2'
  - '3'
  - '4'
```

#### `census21_unpaid_carers_5_24`: Young carers

- **Sources:** F7 · **measure:** proportion · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Providing 1+ hours unpaid care per week, aged 5-24 ÷ `census21_usual_residents_by_age` (Usual residents aged 5-24 (same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `census.F7b.indicators.census21_unpaid_carers_5_24`:

```yaml
- age_band: src_5_24
  dim1:
  - '2'
  - '3'
  - '4'
  - '5'
  - '6'
  dim2:
  - '1'
```

#### `dfe_cin_factor_domestic_abuse`: Domestic abuse identified at assessment

- **Sources:** C1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Episodes with the 'Domestic abuse: concerns parent is victim' factor at end of assessment (Domestic_Abuse_parent) ÷ `dfe_cin_episodes_with_assessment_factors` (Episodes with assessment factor information (Episodes_with_assessment_factor, same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[7]`:

```yaml
indicator: dfe_cin_factor_domestic_abuse
table: c3_factors_identified
column: Domestic_Abuse_parent
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

#### `dfe_cin_factor_parental_mental_health`: Parental mental health identified at assessment

- **Sources:** C1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Episodes with the 'Mental health: concerns about parent' factor at end of assessment (Mental_Health_parent) ÷ `dfe_cin_episodes_with_assessment_factors` (Episodes with assessment factor information (Episodes_with_assessment_factor, same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[8]`:

```yaml
indicator: dfe_cin_factor_parental_mental_health
table: c3_factors_identified
column: Mental_Health_parent
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

#### `dfe_cin_factor_parental_alcohol_misuse`: Parental alcohol misuse identified at assessment

- **Sources:** C1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Episodes with the 'Alcohol misuse: concerns about parent' factor at end of assessment (Alcohol_Misuse_parent) ÷ `dfe_cin_episodes_with_assessment_factors` (Episodes with assessment factor information (Episodes_with_assessment_factor, same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[9]`:

```yaml
indicator: dfe_cin_factor_parental_alcohol_misuse
table: c3_factors_identified
column: Alcohol_Misuse_parent
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```
- **Decisions:** D-0056

#### `dfe_cin_factor_parental_drug_misuse`: Parental drug misuse identified at assessment

- **Sources:** C1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Episodes with the 'Drug misuse: concerns about parent' factor at end of assessment (Drug_Misuse_parent) ÷ `dfe_cin_episodes_with_assessment_factors` (Episodes with assessment factor information (Episodes_with_assessment_factor, same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[10]`:

```yaml
indicator: dfe_cin_factor_parental_drug_misuse
table: c3_factors_identified
column: Drug_Misuse_parent
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```
- **Decisions:** D-0056

#### `ohid_ndtms_adults_in_treatment_living_with_children`: Adults in drug/alcohol treatment living with children

- **Sources:** H3 · **measure:** count · **native level:** service_area · **polarity:** higher_worse
- **Value:** Adults in structured drug/alcohol treatment in 2024-25 who live with children (own or others'), NDTMS. · CI: none · aggregation: sum
- **Built in code:** not loaded (D-0091)
- **Decisions:** D-0055, D-0091

#### `ohid_ndtms_parents_not_living_with_children`: Parents in drug/alcohol treatment not living with their children

- **Sources:** H3 · **measure:** count · **native level:** service_area · **polarity:** higher_worse
- **Value:** Adults in structured treatment in 2024-25 who are parents not living with their children, NDTMS. · CI: none · aggregation: sum
- **Built in code:** not loaded (D-0091)
- **Decisions:** D-0055

### Theme: housing

#### `census21_overcrowded_households_dep_children`: Overcrowded households with children

- **Sources:** F6 · **measure:** proportion · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Households with dependent children, occupancy rating (bedrooms) <= -1 ÷ `census21_households_dependent_children` (Households with dependent children (same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `census.F6.indicators.census21_overcrowded_households_dep_children`:

```yaml
- age_band: na
  dim1:
  - '5'
  - '8'
  - '10'
  - '13'
  dim2:
  - '4'
```

#### `mhclg_hclic_households_with_children_in_ta`: Households with children in temporary accommodation

- **Sources:** Ho1 · **measure:** count · **native level:** lad · **polarity:** higher_worse
- **Value:** Households with dependent children in TA at 31 March 2025 (H-CLIC TA1). · CI: none · aggregation: sum
- **Map entry** `tables.Ho1.measures[0]`:

```yaml
indicator: mhclg_hclic_households_with_children_in_ta
table: hclic_ta1
column: Total number of households in TA with children
age_band: na
period:
- 2025-03-31
- 2025-03-31
```

#### `mhclg_hclic_children_in_ta`: Children in temporary accommodation

- **Sources:** Ho1 · **measure:** count · **native level:** lad · **polarity:** higher_worse
- **Value:** Dependent children in households in TA at 31 March 2025 (H-CLIC TA1 total). · CI: none · aggregation: sum
- **Map entry** `tables.Ho1.measures[1]`:

```yaml
indicator: mhclg_hclic_children_in_ta
table: hclic_ta1
column: Total number of children in TA
age_band: '0_17'
period:
- 2025-03-31
- 2025-03-31
```

#### `mhclg_hclic_children_in_ta_by_age`: Children in temporary accommodation

- **Sources:** Ho1 · **measure:** rate · **native level:** lad · **polarity:** higher_worse
- **Formula:** Children under 18 in TA (TA8) ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 10000; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.Ho1.measures[2]`:

```yaml
indicator: mhclg_hclic_children_in_ta_by_age
table: hclic_ta8
column: Total Under 18's in TA
age_band: '0_17'
period:
- 2025-03-31
- 2025-03-31
```
- **Map entry** `tables.Ho1.measures[3]`:

```yaml
indicator: mhclg_hclic_children_in_ta_by_age
table: hclic_ta8
period:
- 2025-03-31
- 2025-03-31
band_columns:
  '0_4':
  - '0'
  - '1'
  - '2'
  - '3'
  - '4'
  '5_10':
  - '5'
  - '6'
  - '7'
  - '8'
  - '9'
  - '10'
  '11_15':
  - '11'
  - '12'
  - '13'
  - '14'
  - '15'
  '16_17':
  - '16'
  - '17'
```

#### `mhclg_hclic_owed_duty_households_with_children`: Families assessed as homeless or at risk

- **Sources:** Ho1 · **measure:** count · **native level:** lad · **polarity:** higher_worse
- **Value:** Households with dependent children assessed as owed a prevention or relief duty, 2024-25 (annual H-CLIC). · CI: none · aggregation: sum
- **Map entry** `tables.Ho1.measures[4]`:

```yaml
indicator: mhclg_hclic_owed_duty_households_with_children
table:
- hclic_a5p
- hclic_a5r
age_band: na
period:
- 2024-04-01
- 2025-03-31
columns:
- Single parent with dependent children - Male
- Single parent with dependent children - Female
- Single parent with dependent children - Other/gender not known
- Couple with dependent children
- Three or more adults with dependent children
```

#### `mhclg_hclic_owed_duty_applicants_16_24`: Young people assessed as homeless or at risk (16-24)

- **Sources:** Ho1 · **measure:** rate · **native level:** lad · **polarity:** higher_worse
- **Formula:** Households with lead applicant 16-24 owed a duty ÷ `ons_mye_population` (Population aged 16-24, mid-2024 MYE) × 10000; CI: byar; aggregation: sum_then_divide
- **Map entry** `tables.Ho1.measures[5]`:

```yaml
indicator: mhclg_hclic_owed_duty_applicants_16_24
table: hclic_a6
columns:
- 16-17
- 18-24
age_band: src_16_24
period:
- 2024-04-01
- 2025-03-31
```

### Theme: health

#### `census21_disabled_0_24`: Disabled children and young people

- **Sources:** F7 · **measure:** proportion · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Disabled under the Equality Act, aged 0-24 ÷ `census21_usual_residents_by_age` (Usual residents aged 0-24 (same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `census.F7a.indicators.census21_disabled_0_24`:

```yaml
- age_band: '0_24'
  dim1:
  - '1'
  - '2'
  dim2:
  - '1'
  - '2'
  - '3'
  - '4'
  - '5'
```

#### `dwp_dla_claimants_under16`: Children receiving Disability Living Allowance

- **Sources:** F3 · **measure:** proportion · **native level:** small_area · **polarity:** higher_worse
- **Formula:** DLA cases in payment, age 0-15 ÷ `ons_sape_population` (Population aged 0-15, mid-2024 SAPE (sum of single years)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `statxplore.F3`:

```yaml
indicator: dwp_dla_claimants_under16
age_field: Age (bands and single year)
age_map: F3
```

#### `dwp_pip_claimants_16_24`: Young people receiving PIP

- **Sources:** F4 · **measure:** proportion · **native level:** small_area · **polarity:** higher_worse
- **Formula:** PIP cases with entitlement, age 16-24 ÷ `ons_sape_population` (Population aged 16-24, mid-2024 SAPE) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `statxplore.F4`:

```yaml
indicator: dwp_pip_claimants_16_24
age_field: Age (bands and single year)
age_map: F4
```

#### `dfe_sen_primary_need_semh`: Pupils with social, emotional and mental health needs

- **Sources:** E1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Pupils with SEN, primary need SEMH ÷ `dfe_pupils_total_sen_publication` (Total pupils) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.E1.measures[3]`:

```yaml
indicator: dfe_sen_primary_need_semh
table: sen_ncyear_
column: number_of_pupils
where:
  phase_type_grouping: Total
  sen_status: Total
  sen_primary_need: Social, Emotional and Mental Health
age_band: src_pupils_all
period:
- 2025-01-16
- 2025-01-16
```

#### `ohid_self_harm_admissions_10_24`: Hospital admissions for self-harm (10-24)

- **Sources:** H2 · **measure:** rate_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** Emergency hospital admissions for intentional self-harm, ages 10-24, rate per 100,000 as published by OHID (count and published CI also stored). · CI: published · aggregation: none
- **Map entry** `fingertips.90813`:

```yaml
indicator: ohid_self_harm_admissions_10_24
sex: Persons
age: 10-24 yrs
time_period: 2023/24
period:
- 2023-04-01
- 2024-03-31
age_band: src_10_24
```

#### `ohid_ae_attendances_0_4`: A&E attendances (under 5s)

- **Sources:** H2 · **measure:** rate_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** A&E attendances, ages 0-4, crude rate per 1,000 as published by OHID. · CI: published · aggregation: none
- **Map entry** `fingertips.93930`:

```yaml
indicator: ohid_ae_attendances_0_4
sex: Persons
age: 0-4 yrs
time_period: 2024/25
period:
- 2024-04-01
- 2025-03-31
age_band: '0_4'
```

#### `ohid_infant_mortality`: Infant mortality

- **Sources:** H2 · **measure:** rate_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** Infant deaths under 1 year per 1,000 live births, 3-year pooled, as published by OHID. · CI: published · aggregation: none
- **Map entry** `fingertips.92196`:

```yaml
indicator: ohid_infant_mortality
sex: Persons
age: <1 yr
time_period: 2022 - 24
period:
- 2022-01-01
- 2024-12-31
age_band: src_infant
```

#### `ohid_under18_conceptions`: Under-18 conceptions

- **Sources:** H2 · **measure:** rate_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** Conceptions to women aged under 18 per 1,000 females aged 15-17, as published by OHID (ONS source). · CI: published · aggregation: none
- **Map entry** `fingertips.20401`:

```yaml
indicator: ohid_under18_conceptions
sex: Female
age: <18 yrs
time_period: '2023'
period:
- 2023-01-01
- 2023-12-31
age_band: src_15_17
sex_code: female
```

#### `ohid_low_birthweight_term`: Low birth weight (full-term babies)

- **Sources:** H2 · **measure:** percent_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** Live births at >= 37 weeks gestation with birth weight < 2,500 g / all live term births with recorded weight, % as published. · CI: published · aggregation: none
- **Map entry** `fingertips.20101`:

```yaml
indicator: ohid_low_birthweight_term
sex: Persons
age: '>=37 weeks gestational age at birth'
time_period: '2024'
period:
- 2024-01-01
- 2024-12-31
age_band: na
```
- **Decisions:** D-0087

#### `ohid_injury_admissions_0_14`: Hospital admissions for injuries (0-14)

- **Sources:** H2 · **measure:** rate_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** Emergency admissions for unintentional and deliberate injuries, ages 0-14, crude rate per 10,000 as published. · CI: published · aggregation: none
- **Map entry** `fingertips.90284`:

```yaml
indicator: ohid_injury_admissions_0_14
sex: Persons
age: <15 yrs
time_period: 2024/25
period:
- 2024-04-01
- 2025-03-31
age_band: src_0_14
```

### Theme: safety

#### `police_crime_all_excl_asb`: Recorded crime

- **Sources:** S1 · **measure:** rate · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Street-level crime records excluding ASB ÷ `ons_sape_population` (Usual resident population, all ages, mid-2024 (SAPE)) × 1000; CI: byar; aggregation: sum_then_divide
- **Map entry** `police.police_crime_all_excl_asb`:

```yaml
exclude:
- Anti-social behaviour
```

#### `police_crime_violence_sexual`: Violence and sexual offences

- **Sources:** S1 · **measure:** rate · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Street-level 'Violence and sexual offences' records ÷ `ons_sape_population` (Usual resident population, all ages, mid-2024 (SAPE)) × 1000; CI: byar; aggregation: sum_then_divide
- **Map entry** `police.police_crime_violence_sexual`:

```yaml
include:
- Violence and sexual offences
```

#### `police_asb_incidents`: Anti-social behaviour

- **Sources:** S1 · **measure:** rate · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Street-level ASB records ÷ `ons_sape_population` (Usual resident population, all ages, mid-2024 (SAPE)) × 1000; CI: byar; aggregation: sum_then_divide
- **Map entry** `police.police_asb_incidents`:

```yaml
include:
- Anti-social behaviour
```

#### `police_crime_weapons_possession`: Possession of weapons

- **Sources:** S1 · **measure:** rate · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Street-level 'Possession of weapons' records ÷ `ons_sape_population` (Usual resident population, all ages, mid-2024 (SAPE)) × 1000; CI: byar; aggregation: sum_then_divide
- **Map entry** `police.police_crime_weapons_possession`:

```yaml
include:
- Possession of weapons
```

#### `police_crime_drugs`: Drug offences

- **Sources:** S1 · **measure:** rate · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Street-level 'Drugs' records ÷ `ons_sape_population` (Usual resident population, all ages, mid-2024 (SAPE)) × 1000; CI: byar; aggregation: sum_then_divide
- **Map entry** `police.police_crime_drugs`:

```yaml
include:
- Drugs
```

#### `yjb_first_time_entrants_10_17`: First-time entrants to youth justice

- **Sources:** S3 · **measure:** rate_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** Child first-time entrants (aged 10-17) to the youth justice system per 100,000 population aged 10-17, by local authority of residence, year ending December 2024, as published by YJB/MoJ (supplementary table 2.11). · CI: none · aggregation: none
- **Built in code:** harmonise/phase4.py (fte): YJB/MoJ supplementary tables 2.10/2.11 by LA name (aliases in category_maps fte_la_aliases)
- **Decisions:** D-0073

#### `yjb_custodial_sentences_10_17`: Custodial sentences (10-17)

- **Sources:** S3 · **measure:** count · **native level:** YJS · **polarity:** higher_worse
- **Value:** Custodial sentences to children aged 10-17, year ending March 2025, by YJS. · CI: none · aggregation: sum
- **Map entry** `youth_justice[1]`:

```yaml
indicator: yjb_custodial_sentences_10_17
table: yj_outcomes
column: Number_Cautioned_Sentenced
where:
  Caution_or_sentence_tier: Custody
age_band: src_10_17
period:
- 2024-04-01
- 2025-03-31
```

#### `yjb_proven_offences_10_17`: Proven offences by children (10-17)

- **Sources:** S3 · **measure:** rate · **native level:** YJS · **polarity:** higher_worse
- **Formula:** Proven offences, ages 10-17 ÷ `ons_mye_population` (Population aged 10-17, mid-2024 MYE, summed over the YJS's member UTLAs (G7)) × 10000; CI: byar; aggregation: sum_then_divide
- **Map entry** `youth_justice[0]`:

```yaml
indicator: yjb_proven_offences_10_17
table: yj_offences
column: Number_Offences
age_band: src_10_17
period:
- 2024-04-01
- 2025-03-31
```

### Theme: service demand

#### `dfe_cin_at_31mar`: Children in need

- **Sources:** C1 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Children in need at 31 March 2025 ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 10000; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[0]`:

```yaml
indicator: dfe_cin_at_31mar
table: b1_children_in_need
column: At31_episodes
age_band: '0_17'
period:
- 2025-03-31
- 2025-03-31
```

#### `dfe_cin_referrals`: Referrals to children's social care

- **Sources:** C1 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Referrals in year ending 31 March 2025 ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE (mid-period)) × 10000; CI: byar; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[1]`:

```yaml
indicator: dfe_cin_referrals
table: c1_children_in_need_referrals
column: referral_count
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

#### `dfe_cin_rereferrals_12m`: Re-referrals within 12 months

- **Sources:** C1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Re-referrals within 12 months ÷ `dfe_cin_referrals` (Referrals in year (same file)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[2]`:

```yaml
indicator: dfe_cin_rereferrals_12m
table: c1_children_in_need_referrals
column: rereferral_count
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

#### `dfe_cin_assessments_completed`: Social care assessments

- **Sources:** C1 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Assessments completed in year ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 10000; CI: byar; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[3]`:

```yaml
indicator: dfe_cin_assessments_completed
table: c2_children_in_need_assessments
column: Assessments_completed
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

#### `dfe_cpp_at_31mar`: Children on child protection plans

- **Sources:** C1 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Children on CP plans at 31 March 2025 ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 10000; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[4]`:

```yaml
indicator: dfe_cpp_at_31mar
table: d1_child_protection_plans
column: CPP_At31
age_band: '0_17'
period:
- 2025-03-31
- 2025-03-31
```

#### `dfe_cpp_starts`: New child protection plans

- **Sources:** C1 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** CP plans started in year ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 10000; CI: byar; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[5]`:

```yaml
indicator: dfe_cpp_starts
table: d1_child_protection_plans
column: CPP_start
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

#### `dfe_cla_at_31mar`: Children in care

- **Sources:** C2 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Children looked after at 31 March 2025 ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 10000; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C2.measures[0]`:

```yaml
indicator: dfe_cla_at_31mar
table: cla_number_and_rate_per_10k_children
column: children_count
where:
  population_type: Children looked after on 31 March each year
age_band: '0_17'
period:
- 2025-03-31
- 2025-03-31
```
- **Map entry** `tables.C2.measures[1]`:

```yaml
indicator: dfe_cla_at_31mar
table: la_cla_on_31_march_by_characteristics
column: children_count
where:
  characteristic: Age group
period:
- 2025-03-31
- 2025-03-31
bands:
  column: breakdown
  map:
    src_infant:
    - Under 1 year
    src_1_4:
    - 1 to 4 years
    src_5_9:
    - 5 to 9 years
    src_10_15:
    - 10 to 15 years
    '16_17':
    - 16 years and over
```

#### `dfe_cla_starts`: Children entering care

- **Sources:** C2 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Starts in year ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 10000; CI: byar; aggregation: sum_then_divide
- **Map entry** `tables.C2.measures[2]`:

```yaml
indicator: dfe_cla_starts
table: cla_number_and_rate_per_10k_children
column: children_count
where:
  population_type: Children starting to be looked after each year
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

#### `dfe_cla_uasc_at_31mar`: Unaccompanied asylum-seeking children in care

- **Sources:** C2 · **measure:** rate · **native level:** service_area · **polarity:** neutral
- **Formula:** UASC looked after at 31 March 2025 ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 10000; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C2.measures[3]`:

```yaml
indicator: dfe_cla_uasc_at_31mar
table: la_cla_on_31_march_by_characteristics
column: children_count
where:
  characteristic: Unaccompanied asylum-seeking children
  breakdown: Unaccompanied asylum-seeking children
age_band: '0_17'
period:
- 2025-03-31
- 2025-03-31
```

#### `dfe_care_leavers_17_21`: Care leavers aged 17 to 21

- **Sources:** C2 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Care leavers aged 17-21 on their birthday in the year, as published by DfE. · CI: none · aggregation: sum
- **Map entry** `tables.C2.measures[9]`:

```yaml
indicator: dfe_care_leavers_17_21
table: la_care_leavers_activity
column: care_leaver_count
sum_rows: true
where:
  care_leaver_age:
  - 17 to 18 years
  - 19 to 21 years
  breakdown: Total
age_band: src_17_21
period:
- 2024-04-01
- 2025-03-31
```

#### `dfe_care_leavers_19_21`: Care leavers aged 19 to 21

- **Sources:** C2 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Care leavers aged 19-21, as published by DfE. · CI: none · aggregation: sum
- **Map entry** `tables.C2.measures[8]`:

```yaml
indicator: dfe_care_leavers_19_21
table: la_care_leavers_activity
column: care_leaver_count
where:
  care_leaver_age: 19 to 21 years
  breakdown: Total
age_band: src_19_21
period:
- 2024-04-01
- 2025-03-31
```

#### `dfe_cla_ceased_adoption`: Adoptions from care

- **Sources:** C2 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** CLA who ceased to be looked after in year ending 31 March 2025 with reason 'adopted'. · CI: none · aggregation: sum
- **Map entry** `tables.C2.measures[11]`:

```yaml
indicator: dfe_cla_ceased_adoption
table: la_children_who_ceased_during_the_year
column: children_count
where:
  characteristic: Reason episode ceased
  breakdown: Adopted
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

#### `dfe_ehcps_0_25`: EHC plans (ages 0-25)

- **Sources:** E2 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** EHCPs maintained, January 2025 ÷ `ons_mye_population` (Population aged 0-25, mid-2024 MYE) × 10000; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.E2.measures[0]`:

```yaml
indicator: dfe_ehcps_0_25
table: caseload
column: ehcplans
time_period: '202425'
where:
  breakdown_topic: All EHC plans
  breakdown: All EHC plans
age_band: '0_25'
period:
- 2025-01-16
- 2025-01-16
```
- **Map entry** `tables.E2.measures[1]`:

```yaml
indicator: dfe_ehcps_0_25
table: caseload
column: ehcplans
time_period: '202425'
where:
  breakdown_topic: Child or young persons age
period:
- 2025-01-16
- 2025-01-16
absent_rows_zero:
  total_where:
    breakdown_topic: All EHC plans
    breakdown: All EHC plans
bands:
  column: breakdown
  map:
    '0_4':
    - under 3
    - age 3
    - age 4
    '5_10':
    - age 5
    - age 6
    - age 7
    - age 8
    - age 9
    - age 10
    '11_15':
    - age 11
    - age 12
    - age 13
    - age 14
    - age 15
    '16_17':
    - age 16
    - age 17
    '18_20':
    - age 18
    - age 19
    - age 20
    '21_24':
    - age 21
    - age 22
    - age 23
    - age 24
```

#### `dfe_ehcp_new_plans`: New EHC plans

- **Sources:** E2 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** New EHCPs issued, calendar year 2024 ÷ `ons_mye_population` (Population aged 0-25, mid-2024 MYE) × 10000; CI: byar; aggregation: sum_then_divide
- **Map entry** `tables.E2.measures[2]`:

```yaml
indicator: dfe_ehcp_new_plans
table: newplans
column: new_ehc_plans
time_period: '2024'
where:
  breakdown_topic: New EHC plans
  breakdown: New EHC plans
age_band: '0_25'
period:
- 2024-01-01
- 2024-12-31
```

#### `ho_nrm_referrals_under18`: Child referrals for suspected exploitation (NRM)

- **Sources:** S4 · **measure:** rate · **native level:** PFA · **polarity:** higher_worse
- **Formula:** Under-18 NRM referrals ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE, summed over the force area's LADs (G8)) × 10000; CI: byar; aggregation: sum_then_divide
- **Built in code:** harmonise/phase4.py (nrm): NRM Table 10 child referrals by police force, four quarters (category_maps nrm_forces, nrm_period)
- **Decisions:** D-0074

#### `nhse_mhsds_cyp_one_plus_contact_12m`: Children supported by NHS mental health services

- **Sources:** H1 · **measure:** rate · **native level:** SICBL24 · **polarity:** neutral
- **Formula:** CYP 0-17 with 1+ contact, rolling 12 months ÷ `nhse_gp_registered_patients` (GP-registered population aged 0-17, 1 April 2025, as published by Sub-ICB (G3b)) × 10000; CI: wilson; aggregation: none
- **Map entry** `mhsds[0]`:

```yaml
measure: MHS95
breakdown: Sub ICB of GP Practice or Residence
indicator: nhse_mhsds_cyp_one_plus_contact_12m
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

#### `nhse_mhsds_cyp_open_referrals`: Children with open mental health referrals

- **Sources:** H1 · **measure:** count · **native level:** SICBL24 · **polarity:** neutral
- **Value:** MHSDS measure CYP23: open referrals to children and young people's mental health services at the end of March 2025, by Sub-ICB of GP practice or residence. · CI: none · aggregation: sum
- **Map entry** `mhsds[1]`:

```yaml
measure: CYP23
breakdown: Sub ICB - GP Practice or Residence
indicator: nhse_mhsds_cyp_open_referrals
age_band: na
period:
- 2025-03-31
- 2025-03-31
```

### Theme: service pressure

#### `dfe_cla_placed_20mi_plus`: Children in care placed over 20 miles from home

- **Sources:** C2 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** CLA placed >20 miles from home ÷ `dfe_cla_distance_known_at_31mar` (CLA at 31 March with a known placement distance (sum of the two published distance cells, same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C2.measures[4]`:

```yaml
indicator: dfe_cla_placed_20mi_plus
table: la_cla_on_31_march_by_characteristics
column: children_count
where:
  characteristic: Distance between home and placement
  breakdown: Placed more than 20 miles from home
age_band: '0_17'
period:
- 2025-03-31
- 2025-03-31
```

#### `dfe_cla_3plus_placements`: Children in care with 3+ placements in the year

- **Sources:** C2 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** CLA with 3+ placements during the year ÷ `dfe_cla_stability_base_at_31mar` (Total CLA at 31 March in the placement stability table (same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C2.measures[6]`:

```yaml
indicator: dfe_cla_3plus_placements
table: LA_CLA_placement_stability
column: children_count
where:
  cla_group: CLA on 31 March
  placement_stability: With 3 or more placements during the year
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

#### `dfe_sw_vacancy_rate`: Social worker vacancy rate

- **Sources:** C3 · **measure:** percent_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** FTE vacancies / (FTE vacancies + FTE social workers) at 30 September 2024, as published by DfE. · CI: none · aggregation: none
- **Map entry** `tables.C3.measures[0]`:

```yaml
indicator: dfe_sw_vacancy_rate
table: csww_indicators
column: vacancy_rate_fte
kind: value
age_band: na
period:
- 2024-09-30
- 2024-09-30
```

#### `dfe_sw_agency_rate`: Agency social worker rate

- **Sources:** C3 · **measure:** percent_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** FTE agency workers / (FTE agency + FTE social workers) at 30 September 2024, as published. · CI: none · aggregation: none
- **Map entry** `tables.C3.measures[1]`:

```yaml
indicator: dfe_sw_agency_rate
table: csww_indicators
column: agency_rate_fte
kind: value
age_band: na
period:
- 2024-09-30
- 2024-09-30
```

#### `dfe_sw_turnover_rate`: Social worker turnover rate

- **Sources:** C3 · **measure:** percent_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** FTE leavers in the year to 30 September 2024 / FTE social workers at 30 September 2024, as published. · CI: none · aggregation: none
- **Map entry** `tables.C3.measures[2]`:

```yaml
indicator: dfe_sw_turnover_rate
table: csww_indicators
column: turnover_rate_fte
kind: value
age_band: na
period:
- 2023-10-01
- 2024-09-30
```

#### `dfe_sw_average_caseload`: Average social worker caseload

- **Sources:** C3 · **measure:** rate_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** Cases held by case-holding social workers / FTE case-holding social workers at 30 September 2024, as published. · CI: none · aggregation: none
- **Map entry** `tables.C3.measures[3]`:

```yaml
indicator: dfe_sw_average_caseload
table: csww_indicators
column: caseload_fte
kind: value
age_band: na
period:
- 2024-09-30
- 2024-09-30
```

#### `dfe_s251_cyp_services_net`: Spending on children's services per child

- **Sources:** C4 · **measure:** currency_gbp · **native level:** service_area · **polarity:** neutral
- **Formula:** Net expenditure, children's and young people's services, GBP ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 1; CI: none; aggregation: sum_then_divide
- **Map entry** `tables.C4.measures[0]`:

```yaml
indicator: dfe_s251_cyp_services_net
table: s251_childrens_young_peoples_services
column: net_current_expenditure
kind: value
where:
  description_of_expenditure: 5.0.2 Total Children and Young Peoples Services Expenditure (excluding CERA)
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```
- **Decisions:** D-0087

#### `dfe_s251_cla_net`: Spending on children in care per child

- **Sources:** C4 · **measure:** currency_gbp · **native level:** service_area · **polarity:** neutral
- **Formula:** Net expenditure, children looked after, GBP ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 1; CI: none; aggregation: sum_then_divide
- **Map entry** `tables.C4.measures[1]`:

```yaml
indicator: dfe_s251_cla_net
table: s251_childrens_young_peoples_services
column: net_current_expenditure
kind: value
where:
  description_of_expenditure: 3.1.11 Total Children Looked After
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

#### `dfe_s251_family_support_net`: Spending on family support per child

- **Sources:** C4 · **measure:** currency_gbp · **native level:** service_area · **polarity:** neutral
- **Formula:** Net expenditure, family support services, GBP ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 1; CI: none; aggregation: sum_then_divide
- **Map entry** `tables.C4.measures[2]`:

```yaml
indicator: dfe_s251_family_support_net
table: s251_childrens_young_peoples_services
column: net_current_expenditure
kind: value
where:
  description_of_expenditure: 3.4.6 Total Family Support Services
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

#### `dfe_s251_young_people_services_net`: Spending on youth services per young person

- **Sources:** C4 · **measure:** currency_gbp · **native level:** service_area · **polarity:** neutral
- **Formula:** Net expenditure, services for young people, GBP ÷ `ons_mye_population` (Population aged 13-19, mid-2024 MYE (to confirm)) × 1; CI: none; aggregation: sum_then_divide
- **Map entry** `tables.C4.measures[3]`:

```yaml
indicator: dfe_s251_young_people_services_net
table: s251_childrens_young_peoples_services
column: net_current_expenditure
kind: value
where:
  description_of_expenditure: 3.5.3 Total Services for young people
age_band: src_13_19
period:
- 2024-04-01
- 2025-03-31
```

#### `ofsted_ilacs_overall_effectiveness`: Ofsted judgement: children's services

- **Sources:** C5 · **measure:** ordinal · **native level:** service_area · **polarity:** higher_worse
- **Value:** Overall effectiveness grade from the most recent ILACS inspection published on or before 31 March 2025; category codes in config/categories.yaml; inspection date recorded as period_end. · CI: none · aggregation: none
- **Built in code:** harmonise/phase3.py (ofsted): latest ILACS judgement at 31 March 2025, ordinal codes from config/categories.yaml

#### `ofsted_childrens_homes`: Children's homes

- **Sources:** C5 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Count of Ofsted-registered children's homes located in the LA at 31 March 2025 (LA-level aggregate only; principle 13). · CI: none · aggregation: sum
- **Built in code:** harmonise/phase3.py (ofsted): count of registered children's homes per LA from the provider list (C5); absent LA = 0

#### `ofsted_childrens_homes_places`: Children's home places

- **Sources:** C5 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Registered places in children's homes located in the LA at 31 March 2025 (LA aggregate only). · CI: none · aggregation: sum
- **Built in code:** harmonise/phase3.py (ofsted): sum of registered places per LA from the provider list (C5); absent LA = 0

#### `dfe_ehcp_20wk_timeliness`: EHC plans issued on time

- **Sources:** E2 · **measure:** percent_published · **native level:** service_area · **polarity:** higher_better
- **Value:** New EHCPs issued within 20 weeks, excluding exception cases, as published (%). · CI: none · aggregation: none
- **Map entry** `tables.E2.measures[3]`:

```yaml
indicator: dfe_ehcp_20wk_timeliness
table: timeliness_20_week
column: PC_plans_issued_20_weeks_ex
kind: value
time_period: '2024'
where:
  breakdown_topic: All EHC plans issued
  breakdown: All EHC plans issued
age_band: '0_25'
period:
- 2024-01-01
- 2024-12-31
```

### Theme: composite

#### `l5_neighbourhood_need`: Neighbourhood need index

- **Sources:** D1, F3, F4, F6, F7, S1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD-style composite (SPEC 12.3): rank-based normal scores within domains, exponentially transformed domain scores, equal domain weights. · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

#### `l5_neighbourhood_need_economic_hardship`: Neighbourhood need: economic hardship domain

- **Sources:** D1, F3, F4, F6, F7, S1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

#### `l5_neighbourhood_need_health_disability`: Neighbourhood need: health disability domain

- **Sources:** D1, F3, F4, F6, F7, S1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

#### `l5_neighbourhood_need_family_housing`: Neighbourhood need: family housing domain

- **Sources:** D1, F3, F4, F6, F7, S1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

#### `l5_neighbourhood_need_safety`: Neighbourhood need: safety domain

- **Sources:** D1, F3, F4, F6, F7, S1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

#### `l5_la_need`: LA need index

- **Sources:** C1, D1b, E3, E4, E5, E6, F1, F6, F7, H2, Ho1, S1, S3 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** IoD-style composite (SPEC 12.3): rank-based normal scores within domains, exponentially transformed domain scores, equal domain weights. · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

#### `l5_la_need_economic_hardship`: LA need: economic hardship domain

- **Sources:** C1, D1b, E3, E4, E5, E6, F1, F6, F7, H2, Ho1, S1, S3 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

#### `l5_la_need_family_risk`: LA need: family risk domain

- **Sources:** C1, D1b, E3, E4, E5, E6, F1, F6, F7, H2, Ho1, S1, S3 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

#### `l5_la_need_health`: LA need: health domain

- **Sources:** C1, D1b, E3, E4, E5, E6, F1, F6, F7, H2, Ho1, S1, S3 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

#### `l5_la_need_education`: LA need: education domain

- **Sources:** C1, D1b, E3, E4, E5, E6, F1, F6, F7, H2, Ho1, S1, S3 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

#### `l5_la_need_housing`: LA need: housing domain

- **Sources:** C1, D1b, E3, E4, E5, E6, F1, F6, F7, H2, Ho1, S1, S3 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

#### `l5_la_need_safety`: LA need: safety domain

- **Sources:** C1, D1b, E3, E4, E5, E6, F1, F6, F7, H2, Ho1, S1, S3 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

#### `l5_la_system_pressure_demand`: LA system pressure: demand domain

- **Sources:** C1, C2, C3, E2, S4 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

#### `l5_la_system_pressure_capacity`: LA system pressure: capacity domain

- **Sources:** C1, C2, C3, E2, S4 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

#### `l5_la_system_pressure_send`: LA system pressure: send domain

- **Sources:** C1, C2, C3, E2, S4 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

## 6. Moving to live pipelines

- **One run, one snapshot.** Keep the snapshot model: a run is defined by the code commit and the
  hashes of its input files, and writes a complete new set of tables. Do not update tables in place.
- **Parameters, not code.** Periods (`period_to_take`, `period` in the maps), file URLs and file keys
  live in `config/sources.yaml` and `config/category_maps.yaml`. A new publication should mean new
  config entries, not new code, unless the file layout changes.
- **Fail fast on layout change.** Staging finds columns by their published labels and checks totals
  and row counts (T2). Keep these checks: a renamed column or a missing row must stop the run, not
  produce wrong values.
- **Port the QA gates as data tests.** Gates 1–19 are pytest checks over the output tables; each maps
  to a data-quality rule (keys, England only, conservation, suppression integrity, denominator match,
  ranges, reconciliation, serving completeness, reproducibility).
- **Things that are manual today:** finding each new file (principle 11: verified URLs only); reading
  a new release's data guidance for symbols and rounding (`config/suppression_codes.yaml`); the NDTMS
  gap (D-0091); deciding whether a changed published figure is a revision.
- **Mapping to Microsoft Fabric:** L0 as files in a lakehouse (pipelines or Dataflows to fetch);
  T2–T9 as notebooks writing one Delta table per layer table; L4 views as views or Delta tables; the
  composite step as a notebook with the same seed; the QA gates as a notebook that blocks publication
  when a rule fails.

---

[Methodology index](index.md)
