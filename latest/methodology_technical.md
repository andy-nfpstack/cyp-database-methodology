# Technical methodology

Release `2dda583978fb-19eda0e60019`. Every parameter below is generated from the build
configuration.

## 1. Principles

Source data is never altered. Values flow one way through layers L0 (raw) → L1 (staged)
→ L2 (harmonised, observed only) → L3 (derived) → L4 (release). L5 composites read the snapshot's L2–L3 values read-only and never change L0–L4 (D-0086).
Observed and modelled values never share a table. Counts move between geographies,
never rates. A value is never distributed from an area to the areas it contains. Published figures take precedence
over aggregated ones. Suppression is preserved and nothing is imputed.

## 2. Geography

The hierarchy is LSOA21 → MSOA21 → LAD (April 2025) → UTLA (April 2025) → England.
Nesting is proven in two ways. First, every Output Area in an LSOA or MSOA must map to the same
LAD. Second, each LSOA and MSOA polygon must lie at least 99.9% by area inside its LAD,
using full-resolution (BFC) boundaries. Generalised boundaries are used for display only.

Other geographies (Sub-ICB, ICB, youth justice services, police force areas, wards) are
related to the hierarchy as `coterminous` (relabelled), `nests_within` (summed),
`contains` (no conversion; shown as a labelled fallback) or `overlaps` (apportioned in L3
on the matching age-band population, using GP-registered population for health data, and
flagged unsuitable for spatial analysis).

## 3. Sources and disclosure control

Each source's statistical disclosure control (SDC) determines how closely sums of its cells
can be expected to match its published totals. The profile below is taken from each publisher's own
data guidance, read when the file was inspected, and confirmed against the published totals where
these exist. A sum is "within tolerance" when |sum − published| ≤ absolute tolerance + relative
tolerance × published. Tolerances were fixed before the comparison and not tuned to it (except DWP
Stat-Xplore, F2–F4, set from observed differences in Phase 2). A difference outside tolerance is
reported, never corrected: the published figure is always the value used.

| Source | Publisher | SDC methods | Additivity | Tolerance (abs / rel) | Confirmed | Publisher's disclosure control and checks | Checked in this release |
|---|---|---|---|---|---|---|---|
| G1 | Office for National Statistics | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| G2 | Office for National Statistics | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| G3 | Office for National Statistics | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| G3b | NHS England | none | approximate | 0 / 0.005 | yes | NHS England GP registrations: counts by practice x LSOA21 and sex, no suppression or rounding symbols (inspection, Phase 4); female + male sum exactly to every published total. Patients of unknown sex are excluded by the publisher. Used only as weights and Sub-ICB denominators. | no published total compared |
| G4 | Office for National Statistics | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| G5 | Office for National Statistics | none | none | 0 / 0 | yes | Geometry; no statistical values. | no published total compared |
| G6 | Office for National Statistics | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| G7 | Youth Justice Board (list of services); composition constructed by this project | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| G8 | Office for National Statistics | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| G9 | Office for National Statistics | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| G10 | House of Commons Library | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| P1 | Office for National Statistics | none | exact | 0 / 0 | yes | ONS small area population estimates are constrained to MSOA and local authority mid-year estimates (ONS SAPE quality and methodology information, https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/smallareapopulationestimatesqmi). Checked: LSOA single-year sums equal the published MSOA estimates exactly. | 1,254,648 published totals compared; 1,254,648 within tolerance; largest difference 0 |
| P1b | Office for National Statistics | none | exact | 0 / 0 | yes | Published LA mid-year estimates. Checked: LAD sums equal the published UTLA and England figures exactly in every age and sex cell. | 82,350 published totals compared; 82,350 within tolerance; largest difference 0 |
| P4 | Office for National Statistics | record_swapping, cell_key | approximate | 10 / 0.01 | yes | Census 2021: targeted record swapping and cell key perturbation (ONS, 'Protecting personal data in Census 2021 results', https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/protectingpersonaldataincensus2021results). Small cells are perturbed, so sums of cells differ slightly from published totals; differences are reported in reconciliation.csv. | 313,110 published totals compared; 313,092 within tolerance; largest difference 55 |
| P7 | Department for Education | none | approximate | 0 / 0.001 | yes | School census (SPC) data guidance: no suppression or rounding applied; 'x' not applicable, 'z' unknown. Checked: LA sums equal the published England figures exactly. | 20 published totals compared; 20 within tolerance; largest difference 0 |
| D1 | Ministry of Housing, Communities and Local Government | none | none | 0 / 0 | yes | Index values (scores, ranks, deciles): not additive; no disclosure control. | no published total compared |
| D1b | Ministry of Housing, Communities and Local Government | none | none | 0 / 0 | yes | MHCLG published LA summaries: not additive. Checked: recomputed LAD averages match the published values within published rounding (gate 13). | no published total compared |
| F1 | Department for Work and Pensions | cell_key | approximate | 10 / 0.01 | yes | CiLIF data guidance: DWP applies disclosure control, and totals may not sum because of rounding and disclosure control; percentages rounded to 1 decimal place; no symbols. Checked: LA sums within tolerance of the published England totals. | 10 published totals compared; 10 within tolerance; largest difference 43 |
| F2 | Department for Work and Pensions | cell_key, suppression | approximate | 15 / 0.03 | yes | Stat-Xplore adds small random adjustments to every cell and publishes counts below 5 as 0 (D-0053). DWP: no reliance on small cells; use published data for larger areas (Stat-Xplore Data Confidentiality note). Observed: complete LSOA sums differ from published figures by about 5 x sqrt(areas summed) at the 99th percentile; 15 + 3% covers this. | 7,144 published totals compared; 7,144 within tolerance; largest difference 88 |
| F3 | Department for Work and Pensions | cell_key, suppression | approximate | 15 / 0.03 | yes | Stat-Xplore adds small random adjustments to every cell and publishes counts below 5 as 0 (D-0053). DWP: no reliance on small cells; use published data for larger areas (Stat-Xplore Data Confidentiality note). Observed: complete LSOA sums differ from published figures by about 5 x sqrt(areas summed) at the 99th percentile; 15 + 3% covers this. | 14,623 published totals compared; 14,617 within tolerance; largest difference 58 |
| F4 | Department for Work and Pensions | cell_key, suppression | approximate | 15 / 0.03 | yes | Stat-Xplore adds small random adjustments to every cell and publishes counts below 5 as 0 (D-0053). DWP: no reliance on small cells; use published data for larger areas (Stat-Xplore Data Confidentiality note). Observed: complete LSOA sums differ from published figures by about 5 x sqrt(areas summed) at the 99th percentile; 15 + 3% covers this. | 8,752 published totals compared; 8,750 within tolerance; largest difference 40 |
| F6 | Office for National Statistics | record_swapping, cell_key | approximate | 10 / 0.01 | yes | Census 2021: targeted record swapping and cell key perturbation (ONS, 'Protecting personal data in Census 2021 results', https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/protectingpersonaldataincensus2021results). Small cells are perturbed, so sums of cells differ slightly from published totals; differences are reported in reconciliation.csv. | 21,918 published totals compared; 21,907 within tolerance; largest difference 129 |
| F7 | Office for National Statistics | record_swapping, cell_key | approximate | 10 / 0.01 | yes | Census 2021: targeted record swapping and cell key perturbation (ONS, 'Protecting personal data in Census 2021 results', https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/protectingpersonaldataincensus2021results). Small cells are perturbed, so sums of cells differ slightly from published totals; differences are reported in reconciliation.csv. | 27,550 published totals compared; 27,529 within tolerance; largest difference 135 |
| C1 | Department for Education | suppression, rounding | approximate | 0 / 0.005 | yes | CIN data guidance: 'c' suppression (secondary suppression may apply); England and regional totals rounded to the nearest 10, LA figures unrounded. Checked: LA sums within 5 of the rounded England totals. | 6 published totals compared; 6 within tolerance; largest difference 5 |
| C2 | Department for Education | suppression, rounding | approximate | 0 / 0.005 | yes | CLA data guidance: 'c' suppression; national and regional figures rounded to the nearest 10, LA figures unrounded. Checked: LA sums within tolerance of the rounded England totals. | 1 published totals compared; 1 within tolerance; largest difference 4 |
| C3 | Department for Education | suppression, rounding | approximate | 1 / 0.005 | yes | Children's social work workforce data guidance: 'c' suppression, 'low' rounds to 0; FTEs, rates and caseloads rounded to one decimal place. | no published total compared |
| C4 | Department for Education | suppression | approximate | 1000 / 0.001 | yes | Section 251 outturn: unrounded GBP; 'c' (confidential) and 'x' (not available) take the GSS meanings. No published total is reconciled. | no published total compared |
| C5 | Ofsted | none | exact | 0 / 0 | yes | Ofsted provider list: every registered provider at 31 March 2025, no symbols. Checked: LA sums equal Ofsted's published national homes and places exactly. | no published total compared |
| E1 | Department for Education | none | approximate | 0 / 0.001 | yes | SEN data guidance: no suppression or rounding applied; release convention 'x' not applicable, 'z' not available. Checked: LA sums equal the published England figures exactly. | 5 published totals compared; 5 within tolerance; largest difference 0 |
| E2 | Department for Education | none | approximate | 0 / 0.001 | yes | SEN2 data guidance: no suppression; 'z' not applicable, 'x' unavailable (Lewisham 2024 timeliness withheld by DfE). Checked: LA sums equal the published England figures exactly. | 8 published totals compared; 8 within tolerance; largest difference 0 |
| E3 | Department for Education | none | approximate | 0 / 0.001 | yes | Absence data guidance: no suppression or rounding applied (except PLAA tables, not used). Checked: LA sums equal the published England figures exactly. | 3 published totals compared; 3 within tolerance; largest difference 0 |
| E4 | Department for Education | none | approximate | 0 / 0.001 | yes | Exclusions data guidance: no suppression or rounding applied (except PLAA tables, not used). Checked: LA sums equal the published England figures exactly. | 3 published totals compared; 3 within tolerance; largest difference 0 |
| E5 | Department for Education | suppression, rounding | approximate | 10 / 0.005 | yes | NEET data guidance: indicators on a cohort of 5 or fewer suppressed ('c'); national and regional numbers rounded to the nearest 10. | no published total compared |
| E6 | Department for Education | none | approximate | 0 / 0.001 | yes | School census (SPC) data guidance: no suppression or rounding applied; 'x' not applicable, 'z' unknown. Checked: LA sums equal the published England figures exactly. | 2 published totals compared; 2 within tolerance; largest difference 0 |
| H1 | NHS England | rounding, suppression (base 5) | approximate | 5 / 0.01 | yes | MHSDS: '*' marks a suppressed small value; Sub-ICB and provider figures rounded to the nearest 5, England unrounded. | no published total compared |
| H2 | Office for Health Improvement and Disparities | suppression | approximate | 0 / 0.001 | yes | Fingertips: no symbols; a missing value carries a 'Value note' (suppressed small count, combined area, not presented), mapped to null_reason. | no published total compared |
| H3 | Office for Health Improvement and Disparities | suppression, rounding | approximate | 5 / 0.01 | no | Not loaded (D-0091): disclosure control not assessed. | no published total compared |
| Ho1 | Ministry of Housing, Communities and Local Government | suppression, imputation | approximate | 0 / 0.05 | yes | H-CLIC table footnotes: '..' authority did not submit; '-' breakdown suppressed (fewer than 5); England and regional totals include MHCLG estimates for non-responding authorities, so LA sums fall short of them. | no published total compared |
| S1 | Home Office / police forces (data.police.uk) | location_anonymisation | exact | 0 / 0 | yes | data.police.uk: record-level counts with no suppression; points are snapped to anonymous map points, which affects location, not counts. Checked: published LSOA code agrees with point-in-polygon for 96.5% of England records (T4). | no published total compared |
| S3 | Youth Justice Board / Ministry of Justice | suppression | approximate | 0 / 0.005 | yes | YJB/MoJ supplementary tables: '..' fewer than ten first-time entrants (suppressed); '*' LA boundary change. Open data tables have no symbols. | no published total compared |
| S4 | Home Office | none | approximate | 0 / 0.01 | yes | NRM quarterly tables: whole numbers, no symbols. Checked: police force rows sum to the published UK total in every quarter. | no published total compared |
| S5 | Home Office | none | approximate | 0 / 0.01 | yes | Asy_D11: counts of people, no symbols. Checked: England LA rows sum to the published English regional totals exactly (D-0084). | no published total compared |

## 4. Suppression and missing values

Suppressed cells are stored as NULL with the publisher's symbol kept in `source_code`.
An aggregate with any suppressed or missing component is NULL, with lower and upper
bounds from the maximum value each symbol can hide, and with counts of components and
suppressed components.

| Symbol | Meaning | null_reason |
|---|---|---|
| `c` | Confidential / suppressed to protect individuals | suppressed |
| `[c]` | Confidential / suppressed to protect individuals | suppressed |
| `x` | Not available | not_published |
| `[x]` | Not available | not_published |
| `z` | Not applicable | not_applicable |
| `[z]` | Not applicable | not_applicable |
| `u` | Low reliability (value withheld) | suppressed |
| `[u]` | Low reliability (value withheld) | suppressed |
| `k` | Rounds to zero but is not zero | suppressed |
| `low` | Rounds to zero but is not zero | suppressed |
| `[low]` | Rounds to zero but is not zero | suppressed |
| `*` | Suppressed (small number) | suppressed |
| `..` | Not available / suppressed (confirm per source) | suppressed |
| `-` | Nil or not applicable (confirm per source; NEVER read as zero without confirmation) | not_applicable |
| `<5` | Fewer than 5 | suppressed |

## 5. Age bands

Population is held by single year of age, so a denominator can be built exactly for any
source band. Source bands are never split or trimmed.

| Code | Label | Min | Max | Standard | Total |
|---|---|---|---|---|---|
| `0_4` | Ages 0–4 | 0 | 4 | yes | no |
| `5_10` | Ages 5–10 | 5 | 10 | yes | no |
| `11_15` | Ages 11–15 | 11 | 15 | yes | no |
| `16_17` | Ages 16–17 | 16 | 17 | yes | no |
| `18_20` | Ages 18–20 | 18 | 20 | yes | no |
| `21_24` | Ages 21–24 | 21 | 24 | yes | no |
| `0_17` | Ages 0–17 (children) | 0 | 17 | yes | yes |
| `0_24` | Ages 0–24 | 0 | 24 | yes | yes |
| `0_25` | Ages 0–25 | 0 | 25 | yes | yes |
| `all_ages` | All ages | — | — | yes | yes |
| `na` | Not age-specific | — | — | yes | no |
| `src_infant` | Under 1 (infants) | 0 | 0 | no | no |
| `src_0_14` | Ages 0–14 | 0 | 14 | no | no |
| `src_0_15` | Ages 0–15 | 0 | 15 | no | no |
| `src_0_19` | Ages 0–19 (dependent children) | 0 | 19 | no | no |
| `src_5_24` | Ages 5–24 | 5 | 24 | no | no |
| `src_10_17` | Ages 10–17 | 10 | 17 | no | no |
| `src_10_24` | Ages 10–24 | 10 | 24 | no | no |
| `src_13_19` | Ages 13–19 | 13 | 19 | no | no |
| `src_15_17` | Ages 15–17 | 15 | 17 | no | no |
| `src_16_19` | Ages 16–19 (dependent children) | 16 | 19 | no | no |
| `src_16_24` | Ages 16–24 | 16 | 24 | no | no |
| `src_17_21` | Ages 17–21 | 17 | 21 | no | no |
| `src_19_21` | Ages 19–21 | 19 | 21 | no | no |
| `src_5_15` | Ages 5–15 | 5 | 15 | no | no |
| `src_20_24` | Ages 20–24 | 20 | 24 | no | no |
| `src_25_29` | Ages 25–29 | 25 | 29 | no | no |
| `src_25_49` | Ages 25–49 | 25 | 49 | no | no |
| `src_30_plus` | Ages 30 and over | 30 | — | no | no |
| `src_50_plus` | Ages 50 and over | 50 | — | no | no |
| `src_1_4` | Ages 1–4 | 1 | 4 | no | no |
| `src_5_9` | Ages 5–9 | 5 | 9 | no | no |
| `src_10_15` | Ages 10–15 | 10 | 15 | no | no |
| `src_pupils_all` | All pupils (school census) | — | — | no | no |

## 6. Rates, denominators and confidence intervals

A rate is the numerator divided by the denominator, multiplied by the indicator's
multiplier. The denominator must match the numerator's area, age band, sex and ethnicity
classification. Stock measures use the population estimate closest to the reference date,
and flow measures use the mid-period population. The denominator date must be within
`max_denominator_gap_days` of the numerator period (default 366 days).

Confidence intervals:

- **Wilson score**: person-based proportions and prevalences.
- **Byar's approximation to the exact Poisson**: event counts that can repeat (OHID/PHE
  methods).
- **Published**: the publisher's own interval.
- **None**: model-based, survey-calibrated and index values, and published rates without intervals.

For full administrative counts, an interval reflects random variation in the underlying
process, not sampling error.

A rate is flagged `low_reliability` when its numerator is below the indicator's threshold
(default 10) or its denominator is below its
threshold (default 50).

## 7. Small-area smoothing

Rates for small areas are also given as empirical Bayes estimates (Marshall's global
method, shrinking toward the England rate). Smoothed rates never replace the crude rate.
Where the resident population is known to misrepresent exposure (for example crime in town
centres), the rate is flagged `low_validity_denominator`.

## 8. Comparability

Each indicator is given an England percentile (0–100, ties averaged, missing values excluded) and a
z-score, calculated separately at each level from native and L2 values only. Fallback rows are
excluded. Polarity is recorded as metadata, and signs are never flipped.

## 9. Indices of Deprivation

Published IoD 2025 LSOA values and the published LA summary measures are loaded as observed values.
For MSOAs and custom regions, MHCLG's method is used: the population-weighted average score and
the share of population in the most deprived national decile. The method is validated by
recomputing the published LAD averages. Ranks and deciles are never averaged.

## 10. Limitations

- **Period mismatches:** sources range from Census 2021 to 2025. Each value carries its own period.
- **Ecological fallacy:** area values describe areas, not individuals.
- **Modifiable areal unit problem:** patterns can change with the choice of boundaries.
- **Practice effects:** service measures reflect local thresholds and recording practice.
- **Interval coverage:** confidence intervals describe random variation only; they do not cover bias from
  recording practice, coverage gaps, survey calibration or the period mismatch between numerator and
  denominator.
- **Point in time:** this is one snapshot (reference date 31 March 2025), not a time series; differences
  between areas are not trends.
- **Small numbers:** use the intervals and smoothed rates.

Full references for every method are in [References](references.md).

## 11. Indicator catalogue

154 indicators are catalogued. Each has its own page, listed in the [index](index.md).
