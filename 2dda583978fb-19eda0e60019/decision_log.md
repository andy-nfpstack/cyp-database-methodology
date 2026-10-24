# Decision log

Release `2dda583978fb-19eda0e60019`. Generated from `DECISIONS.md`: every assumption and
judgement made in building this release, with its date, its reason and its effect on the outputs.

## D-0001: Repository root is the existing git repository

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** The existing repository (`CYP Database`, already under git with the spec committed) is the project root in place of a new `uk-cyp-need/` directory, so `git init` was not needed. The spec was copied to `SPEC.md`. The original `uk-cyp-need-database-spec.md` is left untouched as the committed v1.2 record. `SPEC.md` is the working copy.
- **Reason:** The folder was already initialised for this project. A nested repository would split history.
- **Effect on outputs:** None. Paths in SPEC section 5 are relative to this root.

## D-0002: Python 3.12 via uv; polars as the dataframe library

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** `.python-version` pins 3.12 (uv-managed CPython 3.12.15). The machine's default Python 3.13 is not used. `requires-python = ">=3.12,<3.13"`. Tabular work uses polars; pandas is present only as a dependency of geopandas.
- **Reason:** SPEC section 5 names Python 3.12. Choosing a single dataframe library keeps parsers consistent.
- **Effect on outputs:** None.

## D-0003: Unverified URLs are left null

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** In `config/sources.yaml`, `landing_url` is filled only for the eight pages verified in SPEC 8.5. All other sources have `landing_url: null`, `verify: true` and a `where_to_look` note naming the publisher page to search. The validator enforces this. `dim_source` (where landing_url is NOT NULL) is loaded per phase, only after verification.
- **Reason:** Principle 11: never guess URLs, file names or layouts.
- **Effect on outputs:** None until each source's phase, when URLs are recorded on verification.

## D-0004: Working database location

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** L2 and L3 tables are built in a working DuckDB at `data/cyp_need.duckdb` (gitignored). The release copy is `release/<snapshot_id>/cyp_need_<snapshot_id>.duckdb`. `make schema` recreates the working DB from `sql/schema.sql` and the config dimensions.
- **Reason:** SPEC section 5 places L2/L3 in DuckDB but does not name the working file.
- **Effect on outputs:** None.

## D-0005: Dirty-tree guard and development runs

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Every pipeline stage refuses to run on a git tree with uncommitted or untracked changes. Stages other than `release` accept `--allow-dirty` for development runs. That flag appends `-dirty` to code_version, so the resulting snapshot_id can never be mistaken for a release. `release` has no such flag.
- **Reason:** Principle 10 requires refusing a dirty tree. Parser development in Phases 1-4 needs to iterate without committing on every run.
- **Effect on outputs:** Only clean-tree builds can produce a release.

## D-0006: Age band code conventions

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Standard bands and totals use the SPEC codes (`0_4` … `0_25`, `all_ages`). A source band that does not map exactly is coded `src_<min>_<max>` (e.g. `src_10_24`), with `src_infant` for under-1 and `src_pupils_all` for school-census populations, which are not age bands. `na` marks rows that are not age-specific (households, births, workforce, spend, judgements). Where a source band equals a standard band exactly (e.g. CiLIF 0-4), the standard code is used. Codes are quoted in YAML because YAML 1.1 reads `0_17` as an octal integer; the validator catches unquoted codes.
- **Reason:** SPEC section 3 (never split or trim a band). Clear, sortable codes.
- **Effect on outputs:** `dim_age_band` codes as listed in `config/age_bands.yaml`.

## D-0007: Single-year-of-age codes

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Population single years are coded `y00` … `y89`, plus `y90plus`, with `is_standard = true` and `rolls_into` computed (e.g. `y17` → `0_17,0_24,0_25`; `y25` → `0_25`).
- **Reason:** SPEC section 3: population stored by single year (0-90+), and denominators are exact sums of single years.
- **Effect on outputs:** 91 single-year rows in `dim_age_band`.

## D-0008: Indicator catalogue conventions

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** `config/indicators.yaml` holds the `dim_indicator` fields plus config-only fields (`framework_role`, `published_levels`, `age_bands`, `period`, `verify`, `needs_decision`). The loader applies documented defaults, `methodology_anchor` defaults to the indicator_id with hyphens, and source_ids are written as a comma list. `framework_role` separates need from pressure: pressure indicators must have theme `service_demand` or `service_pressure`, and need indicators must not. The user approved all 123 indicators on 2026-10-20 (`catalogue_reviewed_date`, applied as each indicator's `reviewed_date`).
- **Reason:** SPEC 13 Phase 0 deliverable. The framework split implements SPEC 12.1 from the start.
- **Effect on outputs:** Feeds `dim_indicator`, the profile and serving metadata, and the methodology pages.

## D-0009: SDC profiles and tolerances are drafts

- **Date:** 2026-10-19
- **Status:** decided; every loaded source's SDC profile confirmed in D-0094 (Census guidance cited). F2–F4 tolerances were set from observed reconciliation (D-0053); all others were set in advance and not changed.
- **Decision:** Each source has an SDC profile following SPEC section 8's expected table. Every profile not yet checked against publisher guidance has `confirmed: false`, and its tolerance_reason starts with `DRAFT`. Draft tolerances: Census 10 abs / 1% rel; Stat-Xplore LSOA 10 / 2%; DfE 0 / 0.1-0.5%; MHSDS 5 / 1% (rounding base 5); H-CLIC 0 / 5% (national imputation); ONS population exact (0 / 0). Each is confirmed, with the guidance cited, before that source's phase QA.
- **Reason:** SPEC 13 Phase 0 asks for SDC profiles. No file or guidance has been read yet, so the numbers are placeholders for review.
- **Effect on outputs:** Gates 2 and 7 use these tolerances once confirmed.

## D-0010: Census "sex" vs DfE "gender"

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Census 2021 records sex, while DfE collections record gender as recorded by the school or LA. Both are mapped to the `dim_sex` codes (`female`, `male`) for display. The concepts are not identical, so a rate never combines a DfE numerator split by gender with a Census or ONS denominator split by sex. Per-source maps are filled at inspection.
- **Reason:** SPEC section 3 asks for this to be recorded.
- **Effect on outputs:** Sex-specific rates are only built where numerator and denominator use the same concept.

## D-0011: Ethnicity categories come only from inspected files

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** `config/ethnicity_classifications.yaml` defines the classifications (`none`, `census21_ew_20cat`, `dfe_ethnicity`) and their totals only. Category lists are copied verbatim from the P4 file (Phase 2) and the P7 file (Phase 3). The Census classification name assumes 20 categories and is renamed if ONS allows a different level at LSOA x age.
- **Reason:** Principles 11 and 15: no guessed labels, no grouping.
- **Effect on outputs:** `dim_ethnicity` has 3 total rows until Phase 2.

## D-0012: Which CI method for which measure

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** Person-based stocks and prevalences use Wilson intervals even when shown per 10,000 (CIN, CLA and CP plans at 31 March, EHCPs, UASC, children in TA, CYP MH access). Event counts that can repeat use Byar (referrals, assessments, CLA starts, CP starts, suspensions, exclusions, crime, FTEs, NRM, homelessness duties). Published rates keep the publisher's CI or none. Model-based, survey-calibrated and index values get no derived CI.
- **Reason:** SPEC T7 names Wilson for proportions and Byar for crude rates. Whether a measure is a proportion depends on whether each person is counted once.
- **Effect on outputs:** `ci_method` per indicator.

## D-0013: IoD 2025 catalogue scope

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** At LSOA level: IMD and IDACI score, rank and decile; the seven domain scores and deciles; the Education Children and Young People sub-domain score; and the IoD population denominators (weights for T6c, assuming IoD 2025 publishes them as IoD 2019 did). At LA level (D1b): the five summary measures for IMD and IDACI. IDAOPI, domain ranks and the other sub-domains are left out. The published LA proportions (extent, share in decile 1) are typed `percent_published`.
- **Reason:** These are the measures relevant to CYP and needed for the dashboard and T6c. The spec asks for "all domains incl. IDACI", so domain scores are included. Domain ranks add nothing for display.
- **Effect on outputs:** 32 IoD indicators (22 LSOA, 10 LA summary). Easy to extend.

## D-0014: ONS population estimates typed as model_based

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** SAPE (P1), MYE (P1b) and the IoD population denominators have `estimate_type = 'model_based'` and `ci_method = 'none'`.
- **Reason:** They are demographic estimates (cohort-component and small-area models), not counts. The schema vocabulary has no separate "demographic estimate" type.
- **Effect on outputs:** Shown as estimates in the serving layer.

## D-0015: Police indicators

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** Five data.police.uk indicators: all crime excluding ASB; violence and sexual offences; ASB; possession of weapons; drugs. Each is a rate per 1,000 usual residents of all ages (multiplier 1000, the usual convention for crime), with Byar intervals. `framework_role = context`, because these are not CYP-specific.
- **Reason:** SPEC 8.4 S1 lists these separately as area context. Excluding ASB keeps "all crime" to crimes.
- **Effect on outputs:** Five indicators at small_area, aggregated upward by exact nesting.

## D-0016: Published rates are stored as published

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Fingertips indicators, the social worker workforce rates, EHCP 20-week timeliness, the CiLIF percentages and the IoD LA proportions are stored as `rate_published` or `percent_published` (in `value`, with published CIs). The count is stored alongside where published. They are not re-derived and cannot be aggregated to custom regions (`custom_aggregation = none`).
- **Reason:** Principle 6 (published first). Several use denominators or standardisation not reproducible from our inputs.
- **Effect on outputs:** These indicators have no derived rate, and no value for custom regions.

## D-0017: Per-head spend uses rate_multiplier 1

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** Section 251 spend lines are `currency_gbp`, with a derived per-child value (multiplier 1; GBP per child aged 0-17, or per 13-19 for youth services). The multiplier vocabulary is extended to {1, 100, 1000, 10000}.
- **Reason:** SPEC 12.1 uses "Section 251 per child". GBP per child is the natural unit.
- **Effect on outputs:** The serving layer shows GBP per child.

## D-0018: Permanent exclusions shown per 10,000 pupils

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** Suspensions are shown per 100 pupils (as DfE publishes). Permanent exclusions are shown per 10,000 pupils (DfE publishes per 100).
- **Reason:** Per 100, permanent exclusion rates are around 0.1, which is hard to read on a map. Per 10,000 gives whole numbers.
- **Effect on outputs:** Display unit only.

## D-0019: Config validation is strict

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** The YAML loader rejects duplicate keys (merge-key overrides are allowed). `validate_config()` checks cross-references and measure/CI/aggregation consistency. Loading the dimensions into DuckDB enforces every CHECK vocabulary in `sql/schema.sql`. All three run in `make qa`.
- **Reason:** Principle 9 (mappings are data) only works if the data is validated.
- **Effect on outputs:** None. Prevents bad config from reaching the build.

## D-0020: Tables loaded in primary-key order; logical hashes defined now

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Loaders sort rows by primary key before inserting (SPEC 7.1). The gate 17 logical content hash is SHA-256 over the column names, then each row as compact JSON (floats as `repr`, dates as ISO 8601), sorted by primary key (all columns if a table has none).
- **Reason:** A fixed serialisation is needed before any data is loaded so that rebuilds can be compared.
- **Effect on outputs:** Gate 17.

## D-0021: UC households with children: choice of denominator

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** Accepted draft position: UC households with children is count-only (no derived rate). Revisit in Phase 6 if the neighbourhood need composite requires a rate. Options considered: (a) count only; (b) rate on Census 2021 households with dependent children, with a `max_denominator_gap_days` override and a flag; (c) a per-child rate (unit mismatch; not recommended). Draft catalogue entry is count only.
- **Reason:** No timely household denominator exists at LSOA. The neighbourhood need index (SPEC 12.1) needs a rate.
- **Effect on outputs:** Decides whether UC can enter the neighbourhood need composite.

## D-0022: CiLIF rate

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** Accepted draft position: use DWP's published LA percentages if published; otherwise no rate (no approximate denominator) until decided again. Use DWP's published percentages (`dwp_cilif_*_bhc_pct`, percent_published) if DWP publishes them at LA level. Otherwise, either have no rate or use a stated approximate denominator, flagged.
- **Reason:** CiLIF counts dependent children aged up to 19. No population band matches, and SPEC 3 forbids trimming bands.
- **Effect on outputs:** The LA-level child poverty rate shown on the dashboard.

## D-0023: NDTMS parents in treatment: rate or count

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** Accepted draft position: count-only. Revisit in Phase 6 if the LA need composite requires a rate. Options considered: Keep it as a count, or express it per 10,000 children aged 0-17 (a ratio across different populations, clearly labelled).
- **Reason:** SPEC 12.1 includes it in the LA need index, which needs a rate.
- **Effect on outputs:** Eligibility for the LA need composite.

## D-0024: Spend polarity and the youth services denominator

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** Accepted draft position: spend polarity stays `neutral` in the catalogue; youth services per-head denominator is ages 13-19. Composite direction is set in Phase 6. Section 251 spend polarity is `neutral` in the catalogue. If spend enters the system pressure index, it is read as "higher = more pressure". The youth services per-head denominator is ages 13-19.
- **Reason:** Spend is not intrinsically better or worse. The composite needs a direction.
- **Effect on outputs:** L5 pressure index direction; display wording.

## D-0025: Composite Monte Carlo settings not given by the spec

- **Date:** 2026-10-19
- **Status:** decided (superseded in detail by D-0088, Phase 6)
- **Decision:** `config/composites.yaml` drafts the values the spec leaves open: seed 20250331; Dirichlet concentration 20 around equal weights; missing-data thresholds {0.5, 0.6667, 0.75}. Domain membership follows SPEC 12.1, mapped to draft indicator_ids. Final values are set in Phase 6.
- **Reason:** SPEC 12.4 fixes 1,000 runs and a fixed seed, but not the concentration or the threshold grid.
- **Effect on outputs:** L5 uncertainty intervals (Phase 6).

## D-0026: Storage safeguards for the USB project drive

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Raw files stream to a `.part` file, are fsynced, renamed, then re-read and re-hashed before acceptance; manifests and staged Parquet are written atomically. The working DuckDB is built in `data/cyp_need.duckdb.building` and only replaces the working database after a complete, successful build. USB selective suspend was turned off on the build machine (user approval, 2026-10-19).
- **Reason:** The project drive (USB, exFAT) dropped off the bus repeatedly on 2026-10-19 (System log: disk event 51). It was stable after a port change (5-minute 256 MB write/hash soak test, no errors).
- **Effect on outputs:** None. Prevents corrupt L0 files or a half-written database.

## D-0027: G1 is built from two ONS OA-level lookups

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** ONS publishes no exact-fit OA21 → LSOA21 → MSOA21 → LAD lookup for 2025 LADs. OA → LSOA → MSOA membership comes from the exact-fit December 2021 lookup (V3). Each OA's 2025 LAD comes from the OA21 → Ward (2025) → LAD (May 2025) lookup (V3). OA unanimity is tested against those 2025 LADs, and the BFC polygon test (≥ 99.9%) provides independent geometric proof. Neither lookup is used as nesting evidence on its own.
- **Reason:** LAD boundaries changed in April 2023 (Cumbria, North Yorkshire, Somerset). SPEC 4.2 forbids best-fit lookups as nesting evidence, so geometry is the proof.
- **Effect on outputs:** `dim_geography.nesting_evidence` records both tests for every LSOA and MSOA.

## D-0028: Upper-tier boundaries use the December 2024 edition

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** ONS has no April or May 2025 Counties and Unitary Authorities boundary set. The December 2025 edition (BFC, BGC) is used: its 153 England codes exactly equal the April 2025 LAD → CTYUA lookup (G2), and every LAD lies ≥ 99.946% inside its service-area polygon. The December 2024 edition was tried first and rejected by the code-set check: it predates the April 2025 recoding of Barnsley (E08000016 → E08000038) and Sheffield (E08000019 → E08000039). It remains in L0 but is not registered or used. LAD boundaries are published as "May 2025" (codes checked equal to G2's April 2025 LADs).
- **Reason:** SPEC 3 boundary vintage is April 2025. The build verifies that the edition used matches it exactly.
- **Effect on outputs:** Service-area polygons for the nesting proof and for display.

## D-0029: LA population is mid-2024, not mid-2025

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** P1b uses the mid-2024 UK estimates (`mye24tablesuk.xlsx`, 26 Sep 2025), although mid-2025 LA estimates now exist.
- **Reason:** SPEC 8.1 fixes mid-2024. LSOA estimates exist only to mid-2024, and gate 6 requires LSOA and LA figures from the same vintage (the SAPE notes state mid-2024 SAPE is coherent with this release). Mid-2024 is also the mid-period point for 2024/25 flow measures.
- **Effect on outputs:** All denominators are mid-2024. For 31 March 2025 stock measures the gap is 274 days (within `max_denominator_gap_days`).

## D-0030: Population is stored exactly as published

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** LSOA and MSOA facts hold what SAPE publishes: female and male by single year (`y00`–`y89`, `y90plus`) plus the persons all-ages total. Persons by single year is not published below LA level, so it is not stored. A persons denominator for any band is built at T7 as the exact sum of the female and male single years (both observed). LA, service area and England facts hold the published MYE2 Persons, Females and Males by single year and all ages. Unitary, metropolitan and London authorities appear once in the source and are loaded at both `lad` and `service_area` (same published figure).
- **Reason:** Principles 3 and 6 (observed values only; published first) and SPEC 4.3 (shared codes).
- **Effect on outputs:** `fact_small_area` and `fact_intermediate_area` have no persons single-year rows; T7 sums the two sexes.

## D-0031: Staging scope in Phase 1

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Only the period taken is staged (the mid-2024 sheets of the SAPE files and the MYE2 sheets of P1b); the other sheets stay in L0. NSPL (G4) is ingested now but staged in Phase 2, where it is first used. Boundaries are staged with every feature, including Wales, Scotland and NI where present (L1 is lossless). BSC boundaries and the ward, Sub-ICB and PFA boundary layers are deferred to the phases that need them.
- **Reason:** L1 is lossless for what is used. Unused periods add size without value.
- **Effect on outputs:** None.

## D-0032: How neighbours are computed

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Queen contiguity is computed from BFC geometry with a GEOS spatial-index `intersects` query (polygons sharing at least one boundary point). k-nearest neighbours (k = 6, 8) use libpysal on polygon centroids in British National Grid. Neighbours are England only, so English areas on the Welsh border have no Welsh neighbours.
- **Reason:** libpysal's vertex-matching contiguity keeps every vertex in memory; full-resolution LSOA boundaries would need several GB on a 15.5 GB machine. The predicate approach gives the same queen definition on exact shared boundaries.
- **Effect on outputs:** The `neighbours` table. Areas with no queen neighbour are listed in D-0034.

## D-0033: MSOA display names are applied at the serving layer

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** `dim_geography.area_name` keeps the official ONS names. House of Commons Library MSOA names (G10 v2.3, Open Parliament Licence) are staged now and joined into the serving views and boundaries in Phase 5, with attribution.
- **Reason:** The schema has one name column. ONS names are the official identifiers, and the HoCL names are a display aid under a different licence.
- **Effect on outputs:** Dashboard labels for MSOAs (Phase 5).

## D-0034: Nesting rule: OA unanimity proves membership; geometry is a 90% sanity check

- **Date:** 2026-10-19
- **Status:** decided (user decision, 2026-10-19; amends SPEC 4.2 step 2)
- **Decision:** Membership is proven by OA unanimity, which is exact. The BFC geometry test is an independent sanity check: each area must have ≥ 90% of its area in its assigned parent and ≤ 10% in any other parent (`config/geography.yaml`). SPEC 4.2's 99.9% is kept as a flag threshold. Flagged areas are written with their shares to `data/harmonised/nesting_flags.csv` and are not failures. `nesting_evidence` records, for every test, the shares in the assigned parent, in another parent and in no parent (e.g. `polygon_lad_99.730(other_0.270,none_0.000)`). The investigation that led to this rule (it halted Phase 1 under SPEC 4.2 step 3) found the following, from exact overlays of full-resolution (BFC) boundaries:
  - **Passes:** OA unanimity for all 33,755 LSOAs and 6,856 MSOAs. LSOA in its MSOA ≥ 99.9991% for all. LAD in its service area ≥ 99.946% for all. Codes match across all lookups and boundaries.
  - **Fails at 99.9%:** 2,360 LSOAs in their LAD (min 90.18%, median failing share 99.73%) and 779 MSOAs (min 95.00%).
  - For 2,234 of the 2,360 LSOAs, the uncovered part lies in a neighbouring LAD; the median sliver is about 1,700 m², concentrated in dense urban boroughs (Newham, Hackney, Kensington and Chelsea, Birmingham, Solihull). The rest lies in no LAD at all: coastline and estuary differences (Sunderland, Durham, Northumberland, Cornwall, Plymouth). No LSOA has more than 6.1% of its area in another LAD.
  - **Cause:** ONS statistical boundaries (OA/LSOA/MSOA) and administrative LAD boundaries trace the same line slightly differently. The failure count is essentially the same against the December 2021 LAD boundaries (99 vs 102 failures among 993 LSOAs in Newham, Birmingham and Hackney), so this is not caused by boundary changes since 2021. Membership is unambiguous.
  - **Listing:** The full list of failing areas, with their shares, is written by every build to `data/harmonised/nesting_failures.csv`. Listing all 3,139 codes here is impractical, so this entry records the counts and the method.
- **Reason:** SPEC 4.2 requires ≥ 99.9% polygon overlap. Official ONS boundaries cannot meet that for about 7% of LSOAs.
- **Effect on outputs:** Phase 1 cannot pass gate 4 until a rule is chosen.

## D-0036: Barnsley and Sheffield MYE relabelled to their April 2025 codes

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** The mid-2024 MYE (April 2024 boundaries) publishes Barnsley as E08000016 and Sheffield as E08000019; from April 2025 they are E08000038 and E08000039. The old → new pairs are recorded as data in `config/geography.yaml` (`code_successors`) and applied to P1b rows (`method_flag = 'relabelled'`), only where the source has no row for the new code.
- **Reason:**   - At the 2021 OA/LSOA resolution the change is a pure recode: no 2021 OA changed LAD, and the LSOA sums under the new codes equal the published MYE under the old codes exactly (251,770 and 582,493).
  - SPEC section 6 allows relabelling at L2.
  - The build re-asserts the exact equality for every relabelled cell, and gate 6 covers it.
- **Effect on outputs:** Barnsley and Sheffield get published LA population figures under their current codes. Any future successor pair must pass the same exact-equality check.

## D-0037: Areas with no queen neighbour

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** Two areas have no queen-contiguous neighbour: LSOA E01019077 (Isles of Scilly 001A) and MSOA E02006781 (Isles of Scilly 001). Each is the only area of its level in the Isles of Scilly (E06000053, flagged `is_small_authority`). Both have knn6 and knn8 rows.
- **Reason:** SPEC section 7 requires islands to be listed and to have knn rows. Hotspot analysis should use knn for these areas.
- **Effect on outputs:** The `neighbours` table.

## D-0038: Census ethnic group at LSOA uses the 6-category classification

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** P4 is Census 2021 `ethnic_group_tb_6a` × `resident_age_7a` (ages 0–4, 5–15, 16–17, 18–20, 21–24, 25–29, 30+), classification `census21_ew_6a`. Published MSOA, LTLA 2023, UTLA 2023 and England tables of the same specification are loaded at those levels.
- **Reason:** ONS disclosure rules block the 20-category ethnic group crossed with any age banding at LSOA (it is released at MSOA and LA). SPEC 8.1 asks for the most detailed classification allowed at LSOA × age; the 6-category version is that. D-0011 anticipated the rename.
- **Effect on outputs:** Ethnicity rows use the 6-category classification at every level, so comparisons stay within one classification (principle 15).

## D-0039: Census tables chosen for F6 and F7

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - F6 is one table, household composition (15) × bedroom occupancy rating (5). It gives all three household indicators, so their numerators and base come from the same perturbed cells.
  - F7a is disability × `resident_age_7a`.
  - F7b is unpaid care × `resident_age_3c`. Unpaid care × `age_7a` or `age_6b` is blocked at LSOA. Under-5s are coded "Does not apply", so carers aged 24 and under are carers aged 5–24, and the 5–24 base is the six non-"Does not apply" categories of the same table.
- **Reason:** These are the most detailed tables ONS releases at LSOA that answer the catalogue definitions exactly.
- **Effect on outputs:** Census proportions are internally consistent: a numerator never exceeds its base.

## D-0040: PIP uses March 2025, not January 2025

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** F4 takes PIP cases with entitlement for March 2025. UC households are also March 2025; DLA is February 2025, the closest quarter.
- **Reason:** SPEC 3 says to take the period closest to 31 March 2025. PIP is published monthly in Stat-Xplore, so March 2025 is available.
- **Effect on outputs:** The PIP reference date is 31 March 2025.

## D-0041: Police data: archive, LSOA vintage and assignment

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - The 2026-08 bulk archive is used: the latest archive covering April 2024 – March 2025, so it includes late resubmissions.
  - Open item 14.4 is resolved: the archive's LSOA codes are LSOA 2021 (all 34,363 distinct codes match).
  - A record's published LSOA code is its primary assignment. It is cross-checked against an independent point-in-polygon assignment on full-resolution boundaries, with the agreement rate reported.
  - Records with no coordinates, or outside England (Welsh forces, PSNI), go to `reject_point_assignment` with a reason.
  - British Transport Police files for February and March 2025 are missing from the archive. This is reported, not imputed.
  - Result: 5,966,690 records; 86,121 without coordinates. All 5,434,030 records with an English LSOA code were assigned (gate 11: 100%). The published code agrees with the full-resolution point-in-polygon for 96.5% of them. The 3.5% that differ are expected: published coordinates are snapped to anonymised map points, so a snapped point can fall in a neighbouring LSOA. That is why the publisher's code is used.
- **Reason:** SPEC T4, principle 6 (published assignment first), and principle 8 (no imputation).
- **Effect on outputs:** Police counts at LSOA (`point_assigned`), aggregated up the hierarchy.

## D-0042: Rate denominators

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - Population denominators are the published estimate for the level: SAPE for LSOA and MSOA, MYE for LAD, service area and England.
  - The denominator band is the exact sum of the single years covering the numerator band; `all_ages` uses the published total. Below LA level, persons = female + male (D-0030).
  - Other denominators (Census households and residents) come from the same table and area.
  - Stock numerators are compared with the denominator date at their period end; flow numerators at their period mid-point. A gap above `max_denominator_gap_days` gives no rate (`denominator_period_gap`).
- **Reason:** SPEC 3 (timing) and T7. Using a published figure at every level avoids building LA denominators from LSOA sums.
- **Effect on outputs:** Every rate's parameters record the denominator indicator, the CI method and the timing rule.

## D-0043: Truncated Stat-Xplore captures replaced (exception to write-once)

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** The first F2–F4 captures held only the first 100 areas of each geography: the Stat-Xplore schema endpoint pages values and my code read only one page. Those 12 files were deleted from L0 before anything was staged or derived from them, and re-captured with paging followed (`Link: rel="next"`). Staging checks that every requested area is present, for both Stat-Xplore and Census sources.
- **Reason:** They were defective captures caused by my code, not source data. Keeping them would have registered incomplete data. This is the only exception to write-once so far, and it is recorded here.
- **Effect on outputs:** None. Nothing was built from the defective files.

## D-0044: IoD 2025 catalogue corrections after inspection

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - Removed `mhclg_iod25_idaci_la_extent` and `mhclg_iod25_idaci_la_local_concentration`: IoD 2025 Files 10 and 11 publish extent and local concentration for the IMD only.
  - Polarity of the IMD and IDACI average rank and the IMD local concentration changed to `higher_worse`. In the 2025 summaries a higher value means more deprived (e.g. Hartlepool's IMD average rank is 23,076, ranked 30th most deprived).
  - Changed indicators carry `reviewed_date` 2026-10-20. The catalogue now has 121 indicators.
- **Reason:** The catalogue must describe what is published (principle 11).
- **Effect on outputs:** Dashboard colour direction for these measures.

## D-0045: ONS-blocked Census areas are suppressed

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** Where the ONS API withholds an area for disclosure (`blocked_areas` in the response), every affected indicator row for that area is NULL with `null_reason = 'suppressed'` and `source_code = 'blocked_by_ons'`. At LSOA: P4 1,015 areas, F7a 40, F7b 570, F6 none. MSOA and higher levels have no blocked areas. Staging checks that returned + blocked = requested, matching ONS's reported count.
- **Reason:** Principle 7: never zero-fill or back-calculate a suppressed cell.
- **Effect on outputs:** Those LSOAs show "suppressed" for the affected Census indicators. Published MSOA/LA values are unaffected.

## D-0046: Census indicator counts are exact sums of cells within one table

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** A Census indicator count, e.g. households with dependent children (four composition categories × all occupancy ratings), is the exact sum of the listed cells of one published table for one area. The cell lists are data in `config/category_maps.yaml`. The count is stored in L2 as `observed` with `n_components` = cells summed and a lineage hash of the component rows. No geography changes.
- **Reason:** The indicator definitions combine published categories. Doing it within one table and area adds no modelling. Using one table keeps numerator ≤ base.
- **Effect on outputs:** Census facts carry `n_components`. Census perturbation means these sums can differ slightly from a separately published total; reconciliation records any such difference.

## D-0047: IoD reference periods

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** IoD 2025 index values (scores, ranks, deciles, LA summaries) are dated 1 April 2022 – 31 March 2023. MHCLG states most inputs are from 2022/23. The IoD population denominators are dated 30 June 2022 ("mid 2022" in File 7).
- **Reason:** SPEC 3 asks for the actual period on every row.
- **Effect on outputs:** Period labels for IoD measures.

## D-0048: Police zero counts are observed zeros

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** An LSOA with no assigned records of a crime type gets count 0 (`point_assigned`), not NULL.
- **Reason:** The archive enumerates every located record for every English force-month in the period except BTP Feb/Mar 2025 (D-0041). No records in an area is an observed zero, not a suppressed cell (principle 7 concerns suppression).
- **Effect on outputs:** Complete LSOA coverage for police indicators.

## D-0049: Low-validity denominators for crime rates

- **Date:** 2026-10-20
- **Status:** decided (user sign-off, 2026-10-20). Evidence: the rule flags 338 LSOAs (cut-off 432 crimes per 1,000 residents against a median of 54). They are city and town centres and transport hubs: Westminster West End (18 LSOAs, up to 6,538 per 1,000), Camden, Birmingham, Liverpool, Brighton, Doncaster town centres, the City of London, and Hillingdon 031A (Heathrow).
- **Decision:** All five police rates are flagged `low_validity_denominator` in LSOAs and MSOAs whose all-crime rate (excluding ASB) is at or above England's 99th percentile at that level. These are mostly town centres and transport hubs, where the resident population understates who is present.
- **Reason:** SPEC T8 asks for a documented method. No daytime or workplace population is in scope for v1, so a transparent rank rule is used.
- **Effect on outputs:** About 1% of areas carry the flag on crime measures. A better exposure measure could replace this rule later.

## D-0050: DWP figures requested as DWP-produced groups

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** Combined categories (UC families with children, DLA under 16, PIP 16–24) are requested from Stat-Xplore as single groups, so DWP's own disclosure perturbation is applied to the combined cell. Component bands are also requested.
- **Reason:** Principle 6: a figure produced by the publisher is preferred to a sum of separately perturbed cells.
- **Effect on outputs:** Published totals at every level, with no sums of perturbed cells.

## D-0051: Census and DWP published levels, and T6 for the rest

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - Census and DWP figures are loaded as published at LSOA, MSOA, LA and England. Census LAs come from `ltla23`/`utla23`, with Barnsley/Sheffield relabelled per D-0036.
  - LSOA sums never replace a published level; they only fill `reconciliation`.
  - T6 aggregation fills only areas the publisher does not cover: police at every level above LSOA, and DWP county councils (summed from published LADs).
- **Reason:** Principle 6 and SPEC 8 ("never sum to a level the Census publishes").
- **Effect on outputs:** `method_flag` shows `observed`, `relabelled` or `aggregated` per row.

## D-0052: Undefined rates are NULL with a specific reason, never capped

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** A derived rate is NULL, with the published counts kept in L2, when:
  - **`zero_denominator`:** the published denominator is 0. Three LSOAs have an SAPE estimate of 0 people aged 16–19.
  - **`numerator_exceeds_denominator`:** a person-based (Wilson) measure has its numerator above its denominator. This happens where two independently produced sources disagree in a tiny cell, e.g. DWP's perturbed claimant count against ONS's modelled population: one LSOA has 6 DLA claimants aged 11–15 against 5 estimated children; another has 34 PIP claimants aged 20–24 against 21.
- **Reason:** A share above 100% is meaningless. Capping it, or replacing either input, would be imputation (principle 8).
- **Effect on outputs:** A handful of LSOA cells show these reasons instead of a rate. Gate 10 (proportions within 0–1) holds.

## D-0053: A Stat-Xplore 0 means "0 to 4" and is treated as suppressed

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** In every DWP Stat-Xplore output (F2–F4), a published 0 is stored as NULL with `null_reason = 'suppressed'`, `source_code = 'statx_0_means_0_to_4'` and bounds `count_lower = 0`, `count_upper = 4`. The rule is configured in `suppression_codes.yaml` (`max_hidden: 4`). T6 aggregates of such cells are NULL with lower and upper bounds. Reconciliation compares only complete sums. The published LSOA, MSOA, LA and England figures remain the values used (principle 6).
- **Reason:**   - **Evidence:** across all twelve DWP files (about 330,000 cells), the values 1, 2, 3 and 4 never occur, while 0 and 5+ are common. For example, the DLA LSOA cells have 34,573 zeros and 11,142 fives. Real counts would have many 1–4s, so Stat-Xplore publishes counts below 5 as 0.
  - **Effect seen in Phase 2 reconciliation:** under-5 DLA summed from LSOAs was 21% below the published England figure, and about 30% of DLA and PIP LA cells fell outside the draft tolerance.
  - **DWP guidance** ([Data Confidentiality](https://stat-xplore.dwp.gov.uk/webapi/metadata/Data%20Confidentiality.html)): cells are randomly adjusted, "no reliance should be placed on small cells", and "published data for the larger area should be used wherever possible". The note does not state the below-5 rule; the data do.
  - Census outputs do not show this pattern (values 1–4 are frequent), so Census zeros remain observed zeros.
- **Effect on outputs:** DWP LSOA cells that were 0 now show "suppressed (0–4)" rather than a false zero: about 73% of LSOAs for DLA under-5, 2.4% for DLA under-16 and 0.2% for UC households with children. Their rates are NULL. Sums of LSOAs for custom areas carry bounds instead of a biased total.

## D-0035: Exact overlay method for nesting tests

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Polygon shares are computed by subdividing each parent polygon into pieces of at most 1,000 vertices (recursive halving with robust box intersection, as PostGIS ST_Subdivide does), then intersecting each child only with the touching pieces. The earlier fast path (`shapely.clip_by_rect`) is not used: GEOS documents that it may not return the exact intersection, and it reported 0% for three LSOAs that lie fully inside their MSOA.
- **Reason:** A proof test must be exact. Unit tests confirm the subdivision partitions area exactly.
- **Effect on outputs:** `nesting_evidence` values. A full run takes about 4–5 minutes.

## D-0054: Phase 3 sources and how they are taken

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** Each DfE source (C1–C4, E1–E6, P7) is ingested as the release's own "download all files" zip from Explore Education Statistics. Only the LA tables the catalogue needs are staged, at the reference period. The other sources:
  - **F1:** two routes.
    - The published ODS gives LA counts and percentages for ages 0–15.
    - Stat-Xplore (CILIF_REL, CILIF_ABS, year 2024/25) gives the age bands 0–4, 5–10, 11–15 and 16–19, plus all ages 0–19 including unknown age, as DWP-produced groups at LA and country level.
  - **H2:** one Fingertips CSV export (`all_data/csv/by_indicator_id`, area type 502, parent England).
  - **Ho1:** the January–March 2025 detailed LA tables (TA1), the additional TA tables (TA8) and the corrected 2024-25 annual tables (A5P, A5R, A6).
  - **C5:** Ofsted's two underlying-data files.
  - **S5:** Asy_D11 from the June 2026 support local authority dataset, at the 31 March 2025 quarter.
- **Reason:** One file per release keeps provenance simple and lets every table be checked against the publisher's own files (principle 11). CiLIF age bands exist only on Stat-Xplore. The ODS is the official table for 0–15 counts and percentages.
- **Effect on outputs:** 21 L0 files. H3 is not loaded (D-0055).

## D-0055: NDTMS parents in treatment (H3) is blocked

- **Date:** 2026-10-20
- **Status:** decided (user, 2026-10-21)
- **Decision:** H3 is not loaded. No machine-readable LA file was found:
  - `ndtms.net` ViewIt/Adult has no download.
  - The ViewIt archive CSV ends in 2023.
  - The parent and child figures are only in the interactive "Prevalence and unmet need toolkit" (`reportId=parental`).
  - Fingertips has no "living with children" indicator.
  - Scraping a web report is excluded (principle 11).
- **Reason:** No verified file exists to ingest.
- **Effect on outputs:** Two indicators are empty. The SPEC 12.1 LA need index loses one input until the user places an NDTMS LA extract (2024-25) in `data/raw/manual/H3/`, or chooses another source.

## D-0056: CIN assessment factors: exact columns, same-table base, alcohol and drugs kept apart

- **Date:** 2026-10-20
- **Status:** decided (user, 2026-10-21)
- **Decision:** The catalogue's factor indicators are built from DfE CIN table C3 as follows:
  - **Factors used:** the parent-related columns, as the "toxic trio" framing intends: `Domestic_Abuse_parent` ("concerns parent is victim"), `Mental_Health_parent`, `Alcohol_Misuse_parent` and `Drug_Misuse_parent`. The `_child` and `_person` variants are not added in, because one episode can carry several factors and adding columns would double-count.
  - **Denominator:** the table's own `Episodes_with_assessment_factor`, as DfE uses, not assessments completed. It is a new catalogue entry, `dfe_cin_episodes_with_assessment_factors`.
  - **Substance misuse split:** `dfe_cin_factor_parental_substance_misuse` is replaced by `dfe_cin_factor_parental_alcohol_misuse` and `dfe_cin_factor_parental_drug_misuse`, because the two cannot be added without double-counting episodes. `config/composites.yaml` lists both.
- **Reason:** Each proportion must count episodes once (Wilson CI). The DfE file publishes no "alcohol or drugs" column.
- **Effect on outputs:** Four factor proportions on DfE's own base, and one more indicator in the catalogue. The composite domain needs sign-off on whether both substance indicators enter it or only one.

## D-0057: Placement distance and stability use same-table denominators

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - **Placed more than 20 miles from home:** divided by children whose distance is known. That base is the exact sum of the two published cells "20 miles or less" and "more than 20 miles" in the same table (new denominator `dfe_cla_distance_known_at_31mar`), as DfE excludes unknown distances.
  - **3+ placements:** divided by the same table's "Total children" for "CLA on 31 March" (new denominator `dfe_cla_stability_base_at_31mar`).
- **Reason:** The catalogue's verify note. A same-table base removes cross-table mismatch.
- **Effect on outputs:** Two new denominator indicators. These proportions match DfE's published percentages, rounding aside.

## D-0058: Free school meals by LA of school; pupils indicator renamed

- **Date:** 2026-10-20
- **Status:** decided (user, 2026-10-21)
- **Decision:** The 2024/25 SPC release publishes LA FSM eligibility by school location only. Its residence-based table (`spc_cbm`) has headcounts and no FSM. So:
  - `dfe_fsm_eligible_pupils` uses the FSM performance-table pair from `spc_pupils_fsm`: the "known to be eligible …" headcount over the "number of pupils (used for FSM in Performance Tables)" headcount, by LA of school.
  - The denominator `dfe_pupils_on_roll_residence` is renamed `dfe_pupils_on_roll`, with its definition corrected.
  - SEN (E1), absence (E3) and exclusions (E4) are also by LA of school (the headline LA tables).
- **Reason:** The residence basis assumed in Phase 0 is not published. Numerator and denominator must share one basis.
- **Effect on outputs:** In LAs with large cross-border pupil flows, FSM and SEN rates describe the LA's schools rather than resident children.

## D-0059: Units and published values in Phase 3

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - **CiLIF percentages** are published as fractions (0.27) and are stored ×100, so that every `percent_published` value is on the 0–100 scale. This is an exact rescale.
  - **Section 251 spend** is DfE's unrounded `net_current_expenditure` in GBP, from the total lines 5.0.2 (all CYP services excluding CERA), 3.1.11 (children looked after), 3.4.6 (family support) and 3.5.3 (services for young people).
  - **Workforce rates** (vacancy, agency, turnover; FTE basis) and the average caseload per case-holding FTE are stored as published (one decimal place).
  - **EHCP 20-week timeliness** uses DfE's headline basis, excluding exceptions.
- **Reason:** Principle 6 (published first) and D-0016.
- **Effect on outputs:** Spend per child is derived with MYE denominators (D-0017).

## D-0060: LA codes: successors, joint reporting and defunct counties

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - **Successor codes:** DfE, Fingertips, H-CLIC, Ofsted and asylum data still use E08000016 (Barnsley) and E08000019 (Sheffield). These are relabelled to E08000038 and E08000039, as in D-0036. Some DfE tables (S251 spend, EHC plans) also still use the pre-unitary county codes for Buckinghamshire (E10000002), North Yorkshire (E10000023) and Somerset (E10000027). Each unitary covers exactly the former county's area, so these are added to `code_successors` and relabelled to E06000060, E06000065 and E06000066. Relabelling is decided per indicator, and only where the new code is absent. `code_successors` no longer forms part of the geography cache key, because the geography build never reads it.
  - **Joint services:** the social work workforce release reports two joint services: North Northamptonshire with West Northamptonshire, and Kingston upon Thames with Richmond upon Thames. Each member LA gets a NULL row with `null_reason = 'not_published'` and `source_code = 'reported_jointly:<codes>'`. The joint figure is not split or copied (principle 8).
  - **Defunct counties:** codes not in the April 2025 hierarchy (CLA rows for the former counties of Cumbria and Northamptonshire) are dropped. The build reports every dropped code (`_harmonise_report.json`, `phase3.tables.dropped_codes`).
- **Reason:** No figure can be invented for one member of a joint service. Former counties no longer exist.
- **Effect on outputs:** Four UTLAs have no workforce figures.

## D-0061: H-CLIC symbols, missing authorities and counties

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - **`..`** (authority with missing data) is `not_published`.
  - **`-`** (breakdown suppressed below 5) is `suppressed` with `count_upper = 4`. In TA8, every `-` row has a total of 0–4.
  - **LAD figures** are loaded as published.
  - **Counties** (service areas) are T6 sums of their districts, NULL where any district is missing or suppressed.
  - **England totals** are MHCLG's published figures. They include estimates for missing authorities and are rounded to 10. TA8 has no England row, so England is the T6 sum and is NULL when any authority is missing.
- **Reason:** SPEC 8.4 (non-submission is `not_published`; national totals include imputation). The table footnotes give the symbol meanings.
- **Effect on outputs:** LA sums do not equal published England totals. The gap is shown in `reconciliation` (D-0065).

## D-0062: Ofsted children's homes and ILACS

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - **Children's homes:** follows Ofsted's own "All Children's Homes" total (Table 6a): children's homes (two spellings occur in the file), secure children's homes, and residential special schools registered as children's homes, at any registration status.
  - **LA matching:** the provider file names LAs but gives no codes. Names are matched to UTLA names, with four aliases (Bristol, Durham, Herefordshire, Kingston upon Hull). Welsh LA names are excluded.
  - **National check:** the build stops unless LA sums equal Ofsted's published national 4,009 homes and 15,742 places.
  - **Zeros:** LAs with no home get an observed 0, because the file lists every registered provider.
  - **ILACS:** the overall effectiveness label is coded 1–4 (`categories.yaml`), with the inspection date as the period.
  - **Level and safeguarding:** everything goes to `fact_service_area` only (gate 14). Provider names, addresses and postcodes are not staged (principle 13).
- **Reason:** Using the publisher's own definition makes the national check exact.
- **Effect on outputs:** Counts of homes and places for all 153 UTLAs.

## D-0063: Fingertips series and notes

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** For each H2 indicator, the latest period ending on or before 31 March 2025 is used:
- **Reason:** The rule in `sources.yaml` ("latest period ending on or before 31 March 2025"). Fingertips publishes combined values for the two smallest LAs.
- **Effect on outputs:** H2 periods differ by indicator. Each is recorded in `period_start` and `period_end`.

## D-0064: NEET 16–17 reference period

- **Date:** 2026-10-20 (confirmed 2026-10-21)
- **Status:** decided
- **Decision:** In the 2024/25 NEET release, `time_period = 2025` is the average of December 2024, January 2025 and February 2025, stored as 1 December 2024 to 28 February 2025. This was inferred in Phase 3 and is now confirmed from two sources:
  - The DfE methodology page: "We therefore take an average estimate from Dec/Jan/Feb for the NEET figures to give an end of year estimate."
  - The release page, which describes its figures as "at the end of 2024/start of 2025" and gives Dudley as 21.5% NEET or not known (2.4% + 19.1%). Our `time_period = 2025` row for Dudley has 2.35% + 19.10% = 21.45%.
- **Reason:** Closest measure to 31 March 2025.
- **Effect on outputs:** NEET period labels. No change to values.

## D-0065: Phase 3 reconciliation: LA sums against England

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** Phase 3 has no LSOA data, so each summable count is reconciled as follows: the sum of service-area figures (published, or T6 sums of published LADs) against the published England figure, written to `reconciliation` with `area_level = 'nation'`. Sums with a suppressed or missing component are not computable and are counted in `phase3.reconciliation_not_computable`.
- **Reason:** Evidence for the draft SDC tolerances. Most publishers round England to 10 and secondary-suppress LA cells. H-CLIC also imputes missing LAs.
- **Effect on outputs:** Reconciliation rows for Phase 3 counts. Gaps are reported, not corrected.

## D-0066: EHCP, CLA and CiLIF age bands

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - **EHC plans** are published by single year (under 3, 3 … 25). Standard bands 0–4 to 21–24 are exact sums of those cells (the D-0046 rule). The 0–25 total is DfE's own.
  - **CLA at 31 March** uses DfE's age groups. Under 1, 1–4, 5–9 and 10–15 are new source bands. "16 years and over" is stored as 16–17, because looked-after children are under 18.
  - **CiLIF:**
    - The DWP bands 0–4, 5–10 and 11–15 are standard.
    - 16–19 stays a source band (dependent children only).
    - 0–19 includes unknown age.
    - The ODS 0–15 count is `src_0_15`.
  - **Ward and small-area CiLIF:** ward counts (May 2024 wards) wait for Phase 4 (other geographies). LSOA and MSOA CiLIF exist on Stat-Xplore (open item 14.2) but are outside the approved catalogue.
  - **Missing single-year EHCP rows:** DfE leaves out single years with no plans. In every one of the 153 LAs (and England), the published single-year rows sum exactly to DfE's "All EHC plans" total, so an absent year is 0. The build re-proves this every run before treating an absent row as 0 (`absent_rows_zero`, `source_code = 'absent_row_zero'` where a whole band is absent).
- **Reason:** SPEC 3: never split or trim a source band.
- **Effect on outputs:** Rates by age band use exact MYE single-year sums.

## D-0067: NEET uses DfE's published proportions

- **Date:** 2026-10-20
- **Status:** decided (user, 2026-10-21)
- **Decision:**   - **Published proportions:** `dfe_neet_16_17` and `dfe_neet_or_not_known_16_17` change from derived Wilson proportions to `percent_published`, using DfE's own NEETprop and NEETNKprop. They have no CI and cannot be aggregated.
  - **Cohort:** `dfe_neet_cohort_16_17` keeps DfE's average cohort, stored in `value` (not `count`) and marked not summable.
- **Reason:** DfE publishes NEET counts as averages of three monthly snapshots (e.g. a cohort of 7,034.33), so they are not whole numbers. Rounding them to build a Wilson interval would alter published data. DfE's own proportion is the published figure (principle 6).
- **Effect on outputs:** No confidence intervals for NEET. Custom regions get no NEET value. Values match DfE's tables exactly.

## D-0068: Section 251 spend per child uses ONS population, not DfE's per-capita figures

- **Date:** 2026-10-21
- **Status:** decided (user, 2026-10-21)
- **Decision:** Per-child spend stays as derived (D-0017): DfE net current expenditure divided by the ONS mid-2024 estimate of 0–17 year olds (13–19 for youth services). DfE's own `per_capita_net_current_spend` column is not loaded.
- **Reason:** The same population basis as every other LA rate keeps measures comparable. The Phase 3 spot-check found the following:
  - Spend matches DfE exactly in all five LAs checked.
  - DfE's implied populations are within about 1% of ONS for Barnsley, Kent and North Northamptonshire, and 4.6% higher for Bristol.
  - For Camden, DfE divides by about 54,900 children, but the ONS mid-2024 estimate of 0–17 year olds is 35,300.
- **Effect on outputs:** Camden's per-child spend is about 56% higher than DfE's published figure. This is noted on the indicators and is to be reported to DfE (statistics.development@education.gov.uk) and recorded in the methodology pack.

## D-0069: Phase 4 sources and access

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:**   - **G3:** LSOA21 to Sub-ICB location to ICB lookup, April 2024 configuration (106 SICBLs, 42 ICBs), the one MHSDS 2024/25 reports on.
  - **G8:** LAD to CSP to PFA lookup, April 2025 (296 LADs, 39 English PFAs).
  - **G3b:** NHS England GP registrations at 1 April 2025, two files: single year of age by SICBL, and practice × LSOA21 (all ages).
  - **H1:** the MHSDS end-of-year final March 2025 file.
  - **S3:** youth justice statistics 2024-25 local open data and supplementary tables.
  - **S4:** the four quarterly NRM table releases for April 2024 to March 2025.
  - **G7:** constructed (D-0071).
  - **G9:** not needed (police and GP data use LSOA21).
  - **Access to digital.nhs.uk:** pages refuse scripted requests (Cloudflare 403), so publication pages were read through the public mirror `nhsd-proxy.openprescribing.net`. Every file is downloaded directly from `files.digital.nhs.uk`; the manifest records that URL and its hash.
- **Reason:** Principle 11: each file is verified from its publisher's page.
- **Effect on outputs:** 11 L0 files.

## D-0070: GP-registered population: Sub-ICB by age; LSOA all ages for weights only

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:** NHS England publishes no LSOA × age file (the LSOA files are practice × LSOA × sex, all ages). Therefore:
  - **Denominator:** `nhse_gp_registered_patients` is loaded as published by SICBL, single year of age by sex (ages 90–94 and 95+ summed to `y90plus`). It is the H1 denominator.
  - **England total:** the exact sum of the 106 SICBLs (aggregated, `fact_nation`), because SICBLs partition England.
  - **T5 weights:** the LSOA21 all-ages file is used only for T5 weights (`lkp_apportion_weights`, basis `gp_registered_all_ages_20250401`).
  - **Denominators are never apportioned:** all-ages weights cannot spread an age-specific population.
- **Reason:** SPEC 4.4 requires a GP-registered basis for health, and this is the finest published form.
- **Effect on outputs:** The H1 rates use the published registered population. Overlap estimates use all-ages weights for a 0–17 measure, which is stated in `parameters`.

## D-0071: Youth justice service composition (G7) is constructed

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:** There is no published YJS-to-LA lookup. `config/yjs_composition.yaml` maps each of the 138 English YJSs in the 2024-25 data to UTLAs, with evidence on every row:
  - By exact name or a short-name alias (Bristol, Durham, Hull, Leicester City).
  - Members named in the YJS name: Bury and Rochdale; Cheshire East, Cheshire West, Halton and Warrington; Kingston and Richmond; Tower Hamlets and City of London; and Cornwall and the Isles of Scilly (GOV.UK South West contact page).
  - By elimination, every UTLA belonging to exactly one YJS: Bedfordshire (Bedford, Central Bedfordshire), Dorset Combined (Dorset, BCP), Northamptonshire (North, West), South Tees (Middlesbrough, Redcar and Cleveland), West Mercia (four UTLAs) and Leicestershire (with Rutland).
- **Reason:** SPEC 8.1 G7: the composition is constructed, with the method recorded.
- **Effect on outputs:** 127 YJSs are coterminous with one UTLA and relabelled. The rest contain several UTLAs, so those UTLAs see a labelled fallback.

## D-0072: MHSDS measures and their handling

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:**   - **Children with 1+ contact:** MHS95 (CYP under 18 with at least one contact, 12 months to 31 March 2025, "Sub ICB of GP Practice or Residence").
  - **Open referrals:** CYP23 (open referrals to CYP mental health services at 31 March 2025). Its age band is `na`, because it counts referrals to CYP services, not people of a stated age.
  - **Rounding and suppression:** Sub-ICB values are rounded to 5; `*` is suppressed. England figures are unrounded and loaded as published.
  - **UNKNOWN rows:** MHS95 4,825, CYP23 5,375. They have no area and are excluded.
  - **MHS95 is not summable:** the Sub-ICB sum (847,920) exceeds England (840,063), because a child can be counted in two Sub-ICBs. It is never aggregated or apportioned.
- **Reason:** These are the catalogue's MHSDS measures, and these are the publisher's rules.
- **Effect on outputs:** MHS95 rates per 10,000 GP-registered 0–17 at SICBL, England (673.5) and coterminous UTLAs and LADs. CYP23 counts at SICBL, with T6b and T5 conversions.

## D-0073: First-time entrants are LA-level published rates, calendar 2024

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:** `yjb_first_time_entrants_10_17` changes from a derived YJS rate to YJB/MoJ's published rate per 100,000 aged 10–17, by LA of residence, for the year ending December 2024 (supplementary table 2.11; FTE are not published by YJS or for years to March).
  - **Model-based:** counts are allocated to LAs by PNC home address, and by a model where there is no address. That is why counts have decimals, and the estimate type is `model_based`.
  - **Symbols:** `..` = fewer than 10 (suppressed, at most 9). `*` = a former area after a boundary change. A `*` row gives way to the current area's published figure where both carry one name (Dorset).
  - **Name aliases:** five aliases match spelling slips in the table ("West Morland and Furness", "... and the Humber").
- **Reason:** Principle 6 (published first), and the published geography is LA, which sits directly on the hierarchy.
- **Effect on outputs:** 149 of 153 UTLAs have a value; 4 are suppressed.

## D-0074: NRM child referrals are at police force area level

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:** Open item 14.7 is resolved. The NRM tables have no LA-of-residence breakdown, so `ho_nrm_referrals_under18` is the "Child (17 or under)" column of Table 10, by police force responsible for investigation.
  - **Period:** the exact sum of the four quarterly releases for April 2024 to March 2025, as first published (later revisions are not captured).
  - **Forces:** force names are mapped to PFA25 (`category_maps.yaml`). British Transport Police has no area and is excluded.
- **Reason:** The police force table is the only one that places a child referral in an area. The first-responder table records who referred, not where the child lives.
- **Effect on outputs:** Rates per 10,000 children for 39 PFAs. The 8 UTLAs coterminous with a PFA get relabelled values. Other UTLAs see a labelled PFA fallback, so the indicator cannot enter the LA system pressure composite as planned (Phase 6 to decide).

## D-0075: Relationship classification, T6b, T5 and fallbacks

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:**   - **Classification:** each other-area / hierarchy-area pair is classified from shared membership units: LSOA21 for SICBL (G3, exact because LSOA nesting is proven), LAD25 for PFA (G8), and UTLA for YJS (G7).
    - **coterminous:** the shared count equals both sizes.
    - **nests_within:** it equals the other area's size.
    - **contains:** it equals the hierarchy area's size.
    - **overlaps:** otherwise.
- **Reason:** SPEC 4.4 and T5/T6b. Open item 14.6 is resolved.
- **Effect on outputs:** Relationship pairs at service-area level:

## D-0076: Police point assignment is cached and runs first

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:** The S1 point-in-polygon step (5.4 million records) runs before the large fact frames are built, and its output is cached in `data/harmonised/police_cache/<key>`. The key hashes the S1, G5 and geography source files, the `phase2.py` code and the crime-type map. The snapshot ID is restamped on reuse.
- **Reason:** As the build grew, the step failed intermittently with memory allocation errors on this 16 GB machine. Its inputs rarely change.
- **Effect on outputs:** None on content. Builds are faster and more reliable.

## D-0077: Ward-level child poverty (F1) is not loaded

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:** DWP's ward tables (children 0–15, May 2024 wards, no percentages) are not loaded. The hierarchy's ward layer is May 2025 (WD25), and there is no published lookup between the two ward vintages here.
- **Reason:** Loading would mean either a code-matching approximation or a new lookup, for counts the LA and LSOA layers already cover.
- **Effect on outputs:** No CiLIF at ward level. LSOA and MSOA CiLIF exist on Stat-Xplore if wanted later (open item 14.2).

## D-0078: Release boundaries

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:** `boundaries.gpkg` holds the ONS generalised (BGC) layers for LSOA21, MSOA21 (with House of Commons Library names), LAD25 and UTLA25, filtered to England and keyed on `dim_geography.area_code`.
  - **Other geographies are dissolved, not downloaded:** each is an exact union of hierarchy areas (Sub-ICB = LSOAs via G3; PFA = LADs via G8; YJS = UTLAs via G7), so the layers are dissolved from those BGC layers. No April 2024 Sub-ICB boundary file exists on the ONS portal; the published PFA boundary vintage (December 2024) differs from the April 2025 lookup.
  - **No PMTiles:** the toolchain (tippecanoe or similar) is not installed, and SPEC 11 makes tiles optional.
- **Reason:** SPEC 11 (BGC for display; one-to-one with `dim_geography`). Dissolving keeps every layer consistent with the relationships used in the data.
- **Effect on outputs:** Seven layers (33,755 / 6,856 / 296 / 153 / 106 / 39 / 138 features). Gate 15 checks the hierarchy layers against `dim_geography`.

## D-0079: Serving layer and profile views

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:**   - **Serving views:** `serve_<level>` is rendered from `sql/serving.sql`, one row per area × profile column used at that level. The display value is:
    - the derived rate for indicators with a rate multiplier;
    - the count for counts;
    - otherwise the published or derived value (IoD MSOA summaries, overlap estimates);
    - for ordinal indicators, a category code with its label.
  - **Rows without a value:** a pair with no value carries the stored reason, or `not_published` (e.g. DfE measures for district councils at `lad` level).
  - **Fallbacks:** fallback rows come only from `fallback_other_geography`.
  - **Profile views:** `profile_<level>` is generated at serve time from `dim_profile_column`, using native values only, so its columns depend on the data. The generated SQL is published in the release.
  - **Population bands:** profile population bands (0–17, 0–24, 0–25) are added to L2 as exact sums of the published single years (the D-0046 rule). Rates still build their own denominators from single years.
  - **Profile columns:** the CiLIF percentage columns use ages 0–15, the band DWP publishes, and a profile column was added for proven offences.
- **Reason:** SPEC 7.2 and 7.3. Gate 15 checks that every row has a value or a reason, that fallbacks stay out of profiles and derived tables, and that boundaries match.
- **Effect on outputs:** Serving rows are about 7,800 at service-area level and 14,800 at LAD level; about 970 are fallback rows.

## D-0080: Reproducibility check (gate 17)

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:**   - **How it runs:** `cypneed verify-rebuild` hashes every table of the working DB (logical content hashes: rows sorted by primary key, fixed serialisation), rebuilds from L0 (stage, then harmonise with the geography and police caches switched off by `CYPNEED_NO_CACHE`, then derive and serve), and hashes again. The report is `data/qa/reproducibility.json`.
  - **How it is published:** `cypneed release` publishes the report only if it is for the same snapshot and every table hash equals the release's `content_hashes.json`. Gate 17 then requires it.
- **Reason:** SPEC gate 17: a clean rebuild at the same commit gives identical logical content. Turning the caches off proves they do not change content.
- **Effect on outputs:** A release needs a verify-rebuild at its commit first (about an hour on this machine).

## D-0081: Release package format

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:**   - **Contents:** the release directory holds a copy of the working DuckDB (all tables and views), Parquet (zstd) and CSV for every table and public view, sorted by primary key, and the serving views as Parquet with `serve_indicator_meta.json`.
  - **Data dictionary:** `data_dictionary.csv` (`dim_indicator`) and `data_dictionary_columns.csv` (every column of every table and view, with descriptions from the schema comments).
  - **Other files:** `sources.csv`, `coverage.csv`, `reconciliation.csv`, `qa_report.md`, `README.md`, `content_hashes.json` and `methodology/`.
  - **Methodology pack:** Markdown, plus a static HTML build rendered with Python-Markdown (no MkDocs), with links rewritten to the HTML pages.
  - **Build safety:** the package is built in `<snapshot>.building` and renamed only after every step has succeeded.
- **Reason:** SPEC 11 and 11.1, with the smallest toolchain that renders the pack.
- **Effect on outputs:** One self-contained directory per snapshot.

## D-0082: Exports for Microsoft Fabric and Power BI

- **Date:** 2026-10-22
- **Status:** decided (user, 2026-10-22: items 1–4)
- **Decision:** The dashboard will be built in Microsoft Fabric / Power BI, so the release adds:
  1. **Delta tables:** `delta/` holds one Delta table per exported table and view, written with delta-rs, for Direct Lake.
  2. **Single-column keys:**
     - `geo_key` (`'<level>|<code>'`, or `'<geography type>|<code>'` for other geographies) on every exported table and view with an area. The lookup also has `other_geo_key`.
     - `serve_dim_area`: one row per area and other area, with parent keys.
     - `serve_dim_measure`: one row per profile column, key `column_prefix`. Power BI relationships cannot join on two columns, and a unitary council is both a `lad` and a `service_area`.
  3. **Numerator and denominator in serving:** `numerator` and `denominator` are added to every serving view (NULL for values, categories and fallbacks), so DAX can aggregate custom selections correctly.
  4. **TopoJSON maps:** `maps/` holds TopoJSON in WGS84, simplified for Power BI map visuals:
     - whole-England files for UTLA, LAD, MSOA, Sub-ICB, PFA and YJS;
     - MSOAs and LSOAs per children's services authority.
- **Reason:** Power BI cannot read DuckDB, GeoPackage or composite keys, and it limits map file sizes. Delta is Fabric's native table format.
- **Effect on outputs:** More files in the release, and three columns added to serving views. There is no change to any value. Methodology links stay relative until a hosting address is chosen.

## D-0083: IoD domain summaries for councils

- **Date:** 2026-10-22
- **Status:** decided
- **Decision:** Fourteen indicators are added from MHCLG's published LAD and UTLA summaries (IoD 2025 Files 10 and 11, the domain sheets of the D1b workbook): for each of the seven domains, the population-weighted average score (`mhclg_iod25_<domain>_la_avg_score`) and the proportion of LSOAs in the most deprived 10% nationally (`..._la_prop_most_deprived_10pct`).
  - **Domains:** income, employment, education, health, crime, barriers, living environment.
  - **Profiles:** each domain's average score becomes a profile column.
- **Reason:** The domain indicators were LSOA-only, so a council-only view had no value for them. MHCLG publishes the LA summaries, so no calculation is needed (the same rule as IDACI and IMD, D1b).
- **Effect on outputs:** 139 indicators. Seven domains now have council values.

## D-0084: Asylum support: councils absent from Asy_D11 are zero

- **Date:** 2026-10-22
- **Status:** decided
- **Decision:** Asy_D11 lists only LAs with at least one person supported: no row has 0, and there are no suppression symbols. At 31 March 2025, 17 England LADs are absent (for example Isles of Scilly, Fenland, Derbyshire Dales, Mid Devon, Torridge, West Devon, Rother, Maldon, Cotswold, Hart). Each absent England LAD is stored as an observed 0 (`source_code = 'absent_area_zero'`), but only after the workbook proves that every person in England is assigned to a listed LA:
  - The workbook's own pivot (`Asy_D11` sheet, filters Support Type and Accommodation Type both "(All)") gives published totals by UK region. The nine English regions sum to 94,754, exactly the sum of the England LA rows.
  - The "N/A - Subsistence Only" row (people with no LA) is 0 at 31 March 2025.
  - Harmonise checks both of these and stops if either fails. Staging checks the pivot filters.
  - Barnsley and Sheffield appear under their pre-2025 codes and are relabelled as before (D-0036).
- **Reason:** Absent here means nobody was supported in that LA on that date. Leaving these LAs NULL made 13 county totals and the England total `incomplete`.
- **Effect on outputs:** `ho_asylum_support_recipients` has a value for all 296 LADs, 153 service areas and England (94,754).

## D-0085: County child poverty percentages by DWP's method

- **Date:** 2026-10-22
- **Status:** decided (replaces the "no rate" position on the CiLIF percentages for areas DWP does not cover)
- **Decision:** DWP publishes CiLIF percentages for lower-tier and unitary councils, but not for the 21 county councils. DWP's note 3 states the method: children aged 0-15 in low income families / mid-2024 ONS population aged 0-15. For a county, the percentage is computed by that method from the summed published district counts and our ONS mid-2024 single years:
  - **Proof first:** before anything is filled, derive recomputes every published percentage by the same method and requires agreement within 1e-9. All 428 published values (296 LAD, 132 service area) agree exactly. Any miss stops the build.
  - **Stored as derived:** rows are derived (`derivation = 'published_method'`), never L2 facts, with numerator and denominator kept. They are filled only where DWP publishes no value.
  - **Serving:** the value is shown in the same column as the published percentages, with `estimate_type` = `survey_calibrated (derived by the publisher's method)` and the profile flag `publisher_method`.
  - **Percentiles:** percentiles rank the published and derived values together.
  - **Generic:** this is the catalogue field `publisher_method_fill`, which other indicators can use only with the same proof.
- **Reason:** The method is DWP's own and is shown to reproduce DWP's figures exactly, so the county value is what DWP would publish. Flagging keeps it distinguishable from published figures.
- **Effect on outputs:** CiLIF percentages at service-area level cover 153 of 153 councils (was 132).

## D-0086: L5 composite build: where it reads, writes and shows

- **Date:** 2026-10-22
- **Status:** decided
- **Decision:**   - **Reads:** `cypneed composite` reads the snapshot's L2 facts and L3 derived values from the working DB, after `serve`. It writes only `l5_*` tables, so L0-L4 never change. SPEC 12 says "reads L4 only"; the serving views don't carry EB-smoothed rates or the indicators without a profile column (the CIN assessment factors), so L5 reads the same frozen L2/L3 values that L4 is built from.
  - **Inputs (12.2):**
    - indicators with a derived rate: the L3 rate built from L2 counts, EB-smoothed at LSOA and MSOA;
    - other indicators: the L2 published value, or, where none is published, an L3 value made by the publisher's own method (IoD MSOA summaries, D-0085 county percentages).
    - Never used: fallback, apportioned, converted or recoded values.
    - Age band: the indicator's profile column band, or its only band.
  - **Tables (12.6):**
    - `l5_composite_<level>` and `l5_domain_<level>` for small_area, intermediate_area and service_area. Columns as SPEC 12.6, plus `rank_median`.
    - `l5_eligibility`, `l5_runs` (Monte Carlo design per run), `l5_sensitivity` (results per choice) and `l5_criterion_residuals`.
    - Per-area, per-run ranks are not stored (34 million rows at LSOA); they are reproducible from the seed.
  - **Catalogue:** every composite and domain score is generated into `dim_indicator` from `composites.yaml` (theme `composite`, estimate type `composite_experimental`, framework role `composite`), so the catalogue cannot drift from the definitions. Each has a profile column and appears in the serving views through the `l5_scores` view.
  - **QA:**
    - Gate 19 reports SPEC 12.8: eligible inputs only; weights sum to 1; a seeded recomputation of the LA composites equals the stored tables exactly; the median rank lies within the interval; NULLs have a reason; the validation report exists.
    - `verify-rebuild` now runs `composite`, so gate 17 also covers the neighbourhood composites.
  - **Release:** the release refuses to run unless the L5 tables and reports are for the same snapshot. It writes `l5/` (tables, `l5_validation.md`, `l5_report.json`), and the methodology pack takes the validation write-up.
- **Reason:** SPEC 12 and 12.8, with one reproducible build path.
- **Effect on outputs:** 16 more `dim_indicator` rows and profile columns, ten `l5_*` tables, gate 19, and a `composite` step between `serve` and `release`.

## D-0087: Composite domain assignment and eligibility (Phase 6)

- **Date:** 2026-10-22
- **Status:** decided (user accepted, 2026-10-23)
- **Decision:** The SPEC 12.1 starting point, with these changes. Eligibility is re-tested at every level for every release, so the indicators that are ineligible today stay listed and enter once they qualify.
  - **Removed:**
    - `dwp_uc_households_with_children` (neighbourhood economic hardship): a count with no same-period denominator. Census 2021 households are four years older than the counts, beyond the 366-day rule. IDACI already measures benefit-based income deprivation.
    - The LA pressure `spend` domain (`dfe_s251_cyp_services_net`): its polarity is neutral, because high spend can mean high demand or high investment, so it cannot be aligned.
  - **Added:** the four CIN assessment factors (domestic abuse, parental mental health, alcohol, drugs) to LA family risk, as signed off in D-0056. Alcohol and drugs have weight 0.5 each.
  - **Reviewed out:** `ohid_low_birthweight_term` from LA health. Its fit with the rest of the domain is negative (rho -0.39), and the domain's alpha was 0.30 with it in. At LA level, term birthweight mainly reflects the population's ethnic composition.
  - **Ineligible today, kept listed:**
    - PIP 16-24 at LSOA (92.0% coverage; it is eligible at MSOA);
    - NDTMS parents in treatment (not loaded);
    - children in temporary accommodation (92.8%);
    - NRM referrals (95% of council values are fallbacks);
    - social worker agency rate (94.8%).
  - **Redundancy (|rho| > 0.9):** only parental alcohol and drug misuse (rho 0.92). The pair is kept on purpose, because the 0.5 weights already make it count once (`redundancy_accepted`). Any other redundant pair stops the build.
  - **Weak fits kept (rho < 0.2 with the rest of the domain, but positive):**
    - lone-parent households in family risk (+0.17): the CIN factors are shares of assessment episodes, not population rates, so they measure something different;
    - average caseload in capacity (+0.07): workload rather than workforce instability.
    - The drop-one stability check shows how much each matters.
  - **Polarity:** EHCP 20-week timeliness is higher-is-better, so it is flipped.
- **Reason:** SPEC 12.2 and 12.3 step 1. The build makes each choice explicit and repeats the checks on every release.
- **Effect on outputs:**   - Neighbourhood need: 4 domains (8 indicators at MSOA, 7 at LSOA).
  - LA need: 6 domains, 17 eligible indicators.
  - LA system pressure: 3 domains, 8 eligible indicators.

## D-0088: Composite method details and Monte Carlo design

- **Date:** 2026-10-22
- **Status:** decided
- **Decision:**   - **Normal scores:** rank-based inverse normal, using Blom's formula (r - 3/8)/(n + 1/4), with average ranks for ties.
  - **Domain score:** the weighted mean of the normal scores of the indicators present (indicator weights 1, except D-0056).
  - **Missing data:**
    - LA: a domain needs at least two-thirds of its indicator weight present.
    - LSOA and MSOA: a domain is scored when any of its indicators is present. SPEC 12.3 gives the two-thirds rule for LA only, and applying it at LSOA left 1,237 LSOAs unscored because of suppressed DLA counts.
    - Every composite needs every domain.
  - **Ranks:** rank 1 and decile 1 are the most need or pressure, as in the IoD. Ties are broken by area code, so every output is deterministic.
  - **Monte Carlo:** 1,000 runs per composite and level. The seed stream is (20250331, composite index, level index). Each run draws uniformly from the options for:
    - normalisation: normal scores, z-scores or min-max;
    - aggregation:
      - IoD exponential;
      - arithmetic mean of the re-normalised domain scores;
      - geometric mean of domain ranks scaled to (0, 1];
    - missing threshold (LA only): 0.5, 0.6667 or 0.75;
    - inclusion: all indicators, drop one, or drop the practice-sensitive indicators.
    - A drop never removes the last indicator of a domain.
  - **Domain weights:** a symmetric Dirichlet with each weight's coefficient of variation at 0.25 (concentration = (D - 1)/0.25^2 - 1). That is about +/-25% of the equal weight (one standard deviation) whatever the number of domains, in line with common composite-audit practice. The skeleton's concentration of 20 gave about +/-50%.
  - **Per area:**
    - median rank;
    - 5th and 95th percentile ranks;
    - P(decile 1);
    - `decile_robust`: in the same decile as the primary method in at least 80% of runs.
  - **Sensitivity:** first-order Sobol' shares of rank variance for each discrete choice (variance of the conditional mean rank, summed over areas). The weights are a vector, so they get a lower bound (the largest single domain weight, binned into deciles) and an upper bound (the sum over domains).
- **Reason:** SPEC 12.3 and 12.4, made exact and reproducible.
- **Effect on outputs:** As described in the methodology pack (`composites/methodology_composite.md`).

## D-0089: Composite results and findings (composites version 0.1-experimental)

- **Date:** 2026-10-22
- **Status:** recorded (results are not adjusted to fit expectations; SPEC 12.5)
- **Decision:** —
- **Reason:** SPEC 12.5: write up every check and say what the results do and do not support.
- **Effect on outputs:** Recorded in the methodology pack (per-composite results) and `l5/l5_validation.md`. For review before the composites are shown publicly.

## D-0090: LA system pressure published as domains only; within-one-decile stability

- **Date:** 2026-10-23
- **Status:** decided (user, 2026-10-23: "proceed with your other recommendations")
- **Decision:**   - **Pressure published as domains only:** `la_system_pressure` is published as its three domain scores (demand, capacity, SEND). The combined index is withheld (`publish_index: false`).
    - It is still computed, so that its robustness and its correlation with LA need are documented in the methodology.
    - It has no `dim_indicator` row, profile column, serving rows or `l5_composite_service_area` rows. Gate 19 checks that none exist.
  - **New stability measure:** every composite and domain row now carries `p_within_one_decile`, the share of Monte Carlo runs in which the area's decile is within one decile of the primary decile. The validation report gives, for each composite and domain, the share of areas within one decile in at least 80% of runs, next to the strict `decile_robust` share.
  - **Dashboard emphasis (release README):** lead with the domain scores, and show the combined need indices in broad bands with their rank interval rather than as exact deciles. The aggregation choice is not narrowed: that would hide real model uncertainty.
- **Reason:**   - The combined pressure index is the least stable output. Only 13.9% of councils keep their decile even under the primary aggregation, and 52.8% stay within one decile.
  - Its capacity domain is weak (alpha 0.39), with the agency rate ineligible at 94.8% coverage.
  - The pressure domains are steadier: within one decile for 97.4% (demand) and 88.4% (capacity) of councils.
  - The need indices stay within one decile for 91.3% (LSOA), 92.0% (MSOA) and 70.5% (LA) of areas. That supports banded display.
- **Effect on outputs:**   - 154 indicators (the pressure index row is removed).
  - A new column `p_within_one_decile` on every `l5_composite_*` and `l5_domain_*` table.
  - Domain stability tables in the validation report.

## D-0091: NDTMS parents in treatment (H3) unavailable

- **Date:** 2026-10-23
- **Status:** decided (user, 2026-10-23)
- **Decision:**   - **Access:** council-level NDTMS figures on parents in treatment exist only in OHID's login-protected "Treatment and recovery unmet need toolkit" (checked 2026-10-23). The user cannot get NDTMS.net access, because registration requires a commissioning or provider purpose. None of the public sources checked has council figures:
    - the GOV.UK adult treatment statistics are England-only;
    - the data.gov.uk listing is a 2012 national bulletin.
  - **Composite:** `ohid_ndtms_adults_in_treatment_living_with_children` is removed from `la_need` family risk, which applies the D-0055 resolution.
  - **Catalogue:** both NDTMS indicators stay in the catalogue with no facts, so the gap stays visible.
- **Reason:** Principle 11 (no scraping or guessed URLs). There is no lawful public route to the data.
- **Effect on outputs:**   - None on values: the indicator was already ineligible.
  - LA family risk remains the least stable domain (D-0090), because it relies on practice-sensitive CIN assessment factors plus lone-parent households.
  - Revisit if OHID publishes council figures, or if a partner commissioner can share an extract under licence.

## D-0092: Methodology hosted on GitHub Pages from its own public repo

- **Date:** 2026-10-23
- **Status:** decided (user, 2026-10-23)
- **Decision:**   - **Hosting:** the rendered methodology pack is published with GitHub Pages from a separate public repo, `andy-nfpstack/cyp-database-methodology`, at https://andy-nfpstack.github.io/cyp-database-methodology/. The code repo stays private; on a free account, Pages serves public repos only.
  - **Settings:** `config/publication.yaml` holds the repo, branch and base URL. It also has placeholders for the contact inbox and DOI, which are still open.
  - **Versioning (SPEC 11.1):** each release is published under `<snapshot_id>/` and kept. `latest/` is a copy of the newest release, and the site root redirects to it and lists every release.
  - **Publishing:** `cypneed publish-methodology [--snapshot S] [--push]` copies a release's `methodology/` into a checkout at `data/pages/` and commits. It pushes only with `--push`.
  - **Links:** `serve_indicator_meta.methodology_url` gives each indicator's page for the release, and the release README links to the online pack.
- **Reason:** SPEC 11.1 ("published ... alongside the dashboard"; versioned) without making the code public or upgrading the account.
- **Effect on outputs:** `methodology_url` in `serve_indicator_meta`, and an online link in the README.

## D-0093: Fabric files shipped as a private GitHub release

- **Date:** 2026-10-24
- **Status:** decided (user, 2026-10-24)
- **Decision:**   - **Why a GitHub release:** the dashboard is built in another organisation's Microsoft Fabric. Its machines cannot reach the build machine's storage or take the D: drive, but the user can sign in to GitHub there.
  - **Command:** `cypneed package-release [--snapshot S] [--upload]` zips only what Fabric needs into `dist/<snapshot>/<snapshot>_fabric.zip`:
    - the Delta tables (every table and view);
    - the TopoJSON maps;
    - `serve_indicator_meta.json`, the data dictionaries, `sources.csv` and the README.
  - **Checksums:** it writes `SHA256SUMS.txt` alongside the zip.
  - **Upload:** with `--upload`, it creates a release `data-<snapshot>` in the private code repo, tagged at the release's own commit.
  - **Left out:** the CSV, Parquet and DuckDB copies, which Fabric does not need.
- **Reason:** GitHub limits release assets to 2 GiB per file with no total limit; the Fabric zip is about 0.26 GB. The private repo keeps the data off the public web until the user decides to publish it, and the checksum lets the receiving organisation verify the download.
- **Effect on outputs:** one zip and one checksum file per release in `dist/` (not committed), and a GitHub release when uploaded.

## D-0094: Final rigour review: disclosure control confirmed, references, open items closed

- **Date:** 2026-10-24
- **Status:** decided (user request, 2026-10-24: "full final review ... academic rigour")
- **Decision:**   - **Disclosure control (closes D-0009):** every loaded source's SDC profile in `config/sources.yaml` is now stated from its publisher's own data guidance, as read at inspection and recorded in `config/suppression_codes.yaml`, and marked confirmed.
    - The Census tables (P4, F6, F7) cite ONS's Census 2021 disclosure control page.
    - The population estimates (P1) cite the ONS small area population estimates quality and methodology information.
    - Method lists are corrected where the guidance says nothing is suppressed: E1–E4, E6, P7, S4 and S5 are `none`; C4 is suppression only.
    - The "DRAFT" wording no longer appears anywhere in the config or the published methodology.
  - **Tolerances unchanged:** tolerances were set in advance and are not changed, so they are not fitted to the results. The F2–F4 exception (set from observed differences, D-0053) is stated in the methodology. The technical methodology now shows, for each source, the publisher's disclosure control and what this release checked (totals compared, within tolerance, largest difference). The results are generated at release from `reconciliation`.
  - **References:** a References page cites every method used:
    - confidence intervals: Wilson; Byar, via Breslow and Day;
    - smoothing and transformation: Marshall's empirical Bayes; Blom's normal scores;
    - consistency checks: Cronbach's alpha;
    - composites: the OECD/JRC handbook; Saisana, Saltelli and Tarantola; Sobol';
    - deprivation: the IoD 2025 technical report;
    - inference: the ecological fallacy (Robinson); the modifiable areal unit problem (Openshaw);
    - the hotspot statistic and false discovery rate in the README guidance;
    - official sources: the ONS disclosure and population pages; the Code of Practice for Statistics, version 3.0.
    - Every URL was verified on 2026-10-24.
  - **Limitations:** the technical methodology adds that confidence intervals cover random variation only, and that the release is a single point in time.
  - **Open items closed:**
    - five `needs_decision` notes resolved by D-0085, D-0087 and D-0091 (youth services spend keeps the 13–19 band it was built with);
    - H3's verified landing page recorded;
    - D-0009 and D-0025 marked decided;
    - D-0087 marked accepted.
  - **Composite titles:** "LA" is capitalised (it had been rendered as "La need").
- **Reason:** SPEC 11.1 and the Code of Practice: every number traceable, every method cited, no draft wording in published outputs, and promised checks (D-0009) actually done.
- **Effect on outputs:** No change to data values. The methodology pack gains `references.md` and the evidence columns in the disclosure-control table.

## D-0095: Fabric-ready release: long serving tables, England level, kit, single-file methodology, transformation specification

- **Date:** 2026-10-24
- **Status:** decided (user request, 2026-10-24)
- **Decision:**   - **England comparator:** `nation` is added as a serving level (`serve_nation`, `profile_nation`).
  - **`serve_all`** stacks every serving level and the other geographies into one fact table, so the Power BI model is a star on two keys (`geo_key`, `column_prefix`).
  - **`l5_area_scores`** holds every composite and domain score with:
    - a fifth band and its label;
    - the number of deciles its 5th–95th rank interval spans;
    - `show_exact_rank` (the interval spans two deciles or fewer, the SPEC 12.6 display rule);
    - the stability measures.
  - **Area labels:** `serve_dim_area` gains `level_label` and `level_order`.
  - **Fabric kit (`release/fabric_kit.py`):** one definition of the model is used to write everything else:
    - the six model tables, five relationships and 18 DAX measures;
    - a load notebook (unzip, save each Delta table, check row counts against `manifest.json`; an optional cell builds the Direct Lake model with semantic-link-labs);
    - `measures.dax`;
    - `FABRIC_GUIDE.md`: setup, the manual modelling steps, six report pages field by field, rules for every visual.
    - The notebook's model cell and the DAX were not run in Fabric or Power BI from the build machine; the guide gives a manual fallback.
  - **Council GeoJSON:** written beside the TopoJSON, for Azure Maps reference layers.
  - **`methodology_complete.md`:** the whole methodology pack in one Markdown file. It has a table of contents, an anchor for each page and internal links rewritten to those anchors. It is published with the pack and attached to the GitHub release.
  - **Transformation specification (`transformations.md`):** generated from config and DECISIONS.md. It covers:
    - layers, invariants and the stage table (T1–T12 with code and QA gates);
    - the shared rules, with the exact formulas used (Wilson, Byar, Marshall's empirical Bayes, percentiles, IoD summaries);
    - every source: files, staging and harmonise code, symbols, disclosure control, decisions;
    - every indicator: formula, the exact category-map entry or the code that builds it, decisions;
    - guidance for moving to live pipelines.
- **Reason:** least work in Fabric (one upload, one notebook), clear modelling and report steps, and documentation complete enough to rebuild the pipelines from (user request).
- **Effect on outputs:**   - England rows in serving.
  - `serve_all`, `l5_area_scores` and the new `serve_dim_area` columns in every export.
  - `transformations.md`, `references.md` and `methodology_complete.md` in the pack.
  - The Fabric bundle carries the kit; the GitHub release carries the guide, notebook and methodology as separate files.

---

[Methodology index](index.md)
