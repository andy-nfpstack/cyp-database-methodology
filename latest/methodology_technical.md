# Technical methodology

Release `abffebbd490b-19eda0e60019`. Every parameter below is generated from the build
configuration.

## 1. Principles

Source data is never altered. Values flow one way through layers L0 (raw) → L1 (staged)
→ L2 (harmonised, observed only) → L3 (derived) → L4 (release), and L5 composites read L4 only.
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
can be expected to match its published totals.

| Source | Publisher | SDC methods | Rounding base | Additivity | Tolerance (abs) | Tolerance (rel) | Confirmed | Basis |
|---|---|---|---|---|---|---|---|---|
| G1 | Office for National Statistics | none | — | none | 0 | 0 | yes | Lookup; no statistical values. |
| G2 | Office for National Statistics | none | — | none | 0 | 0 | yes | Lookup; no statistical values. |
| G3 | Office for National Statistics | none | — | none | 0 | 0 | yes | Lookup; no statistical values. |
| G3b | NHS England | none | — | approximate | 0 | 0.005 | no (draft) | DRAFT: check whether small LSOA counts are rounded or suppressed in this file. |
| G4 | Office for National Statistics | none | — | none | 0 | 0 | yes | Lookup; no statistical values. |
| G5 | Office for National Statistics | none | — | none | 0 | 0 | yes | Geometry; no statistical values. |
| G6 | Office for National Statistics | none | — | none | 0 | 0 | yes | Lookup; no statistical values. |
| G7 | Youth Justice Board (list of services); composition constructed by this project | none | — | none | 0 | 0 | yes | Lookup; no statistical values. |
| G8 | Office for National Statistics | none | — | none | 0 | 0 | yes | Lookup; no statistical values. |
| G9 | Office for National Statistics | none | — | none | 0 | 0 | yes | Lookup; no statistical values. |
| G10 | House of Commons Library | none | — | none | 0 | 0 | yes | Lookup; no statistical values. |
| P1 | Office for National Statistics | none | — | exact | 0 | 0 | no (draft) | SPEC section 8: LSOA estimates are constrained to LA mid-year totals. Confirm in the SAPE methodology. |
| P1b | Office for National Statistics | none | — | exact | 0 | 0 | no (draft) | Published LA estimates sum exactly to UTLA and England. Confirm on load. |
| P4 | Office for National Statistics | record_swapping, cell_key | — | approximate | 10 | 0.01 | no (draft) | DRAFT: Census 2021 cell key perturbation means cells do not sum exactly to published totals. Set from ONS Census 2021 SDC guidance. |
| P7 | Department for Education | suppression | — | approximate | 0 | 0.001 | no (draft) | DRAFT: confirm DfE suppression and rounding rules for this table. |
| D1 | Ministry of Housing, Communities and Local Government | none | — | none | 0 | 0 | no (draft) | Index values; not additive. |
| D1b | Ministry of Housing, Communities and Local Government | none | — | none | 0 | 0 | no (draft) | Summary measures; validation tolerance = published rounding (gate 13). |
| F1 | Department for Work and Pensions | cell_key | — | approximate | 10 | 0.01 | no (draft) | DRAFT: Stat-Xplore perturbation; confirm the DWP method and any rounding. |
| F2 | Department for Work and Pensions | cell_key, suppression | — | approximate | 15 | 0.03 | yes | Stat-Xplore adds small random adjustments to every cell and publishes counts below 5 as 0 (D-0053). DWP: no reliance on small cells; use published data for larger areas (Stat-Xplore Data Confidentiality note). Observed: complete LSOA sums differ from published figures by about 5 x sqrt(areas summed) at the 99th percentile; 15 + 3% covers this. |
| F3 | Department for Work and Pensions | cell_key, suppression | — | approximate | 15 | 0.03 | yes | Stat-Xplore adds small random adjustments to every cell and publishes counts below 5 as 0 (D-0053). DWP: no reliance on small cells; use published data for larger areas (Stat-Xplore Data Confidentiality note). Observed: complete LSOA sums differ from published figures by about 5 x sqrt(areas summed) at the 99th percentile; 15 + 3% covers this. |
| F4 | Department for Work and Pensions | cell_key, suppression | — | approximate | 15 | 0.03 | yes | Stat-Xplore adds small random adjustments to every cell and publishes counts below 5 as 0 (D-0053). DWP: no reliance on small cells; use published data for larger areas (Stat-Xplore Data Confidentiality note). Observed: complete LSOA sums differ from published figures by about 5 x sqrt(areas summed) at the 99th percentile; 15 + 3% covers this. |
| F6 | Office for National Statistics | record_swapping, cell_key | — | approximate | 10 | 0.01 | no (draft) | DRAFT: Census 2021 cell key perturbation. |
| F7 | Office for National Statistics | record_swapping, cell_key | — | approximate | 10 | 0.01 | no (draft) | DRAFT: Census 2021 cell key perturbation. |
| C1 | Department for Education | suppression, rounding | — | approximate | 0 | 0.005 | no (draft) | DRAFT: confirm DfE suppression, secondary suppression and any national rounding. |
| C2 | Department for Education | suppression, rounding | — | approximate | 0 | 0.005 | no (draft) | DRAFT: confirm DfE rounding (national figures may be rounded) and suppression. |
| C3 | Department for Education | suppression, rounding | — | approximate | 1 | 0.005 | no (draft) | DRAFT: FTEs published rounded; confirm. |
| C4 | Department for Education | rounding | — | approximate | 1000 | 0.001 | no (draft) | DRAFT: financial lines are rounded; confirm the units and the rounding. |
| C5 | Ofsted | none | — | exact | 0 | 0 | no (draft) | DRAFT: provider counts expected exact; confirm. |
| E1 | Department for Education | suppression | — | approximate | 0 | 0.001 | no (draft) | DRAFT: confirm DfE suppression rules. |
| E2 | Department for Education | suppression | — | approximate | 0 | 0.001 | no (draft) | DRAFT: confirm DfE suppression rules. |
| E3 | Department for Education | suppression | — | approximate | 0 | 0.001 | no (draft) | DRAFT: confirm DfE suppression rules. |
| E4 | Department for Education | suppression | — | approximate | 0 | 0.001 | no (draft) | DRAFT: confirm DfE suppression rules. |
| E5 | Department for Education | suppression, rounding | — | approximate | 10 | 0.005 | no (draft) | DRAFT: counts may be rounded; confirm. |
| E6 | Department for Education | suppression | — | approximate | 0 | 0.001 | no (draft) | DRAFT: confirm DfE suppression rules. |
| H1 | NHS England | rounding, suppression | 5 | approximate | 5 | 0.01 | no (draft) | SPEC section 8: rounded to 5 with suppression. Confirm in the MHSDS methodology. |
| H2 | Office for Health Improvement and Disparities | suppression | — | approximate | 0 | 0.001 | no (draft) | DRAFT: small counts suppressed by OHID; confirm. |
| H3 | Office for Health Improvement and Disparities | suppression, rounding | — | approximate | 5 | 0.01 | no (draft) | DRAFT: confirm the NDTMS disclosure rules. |
| Ho1 | Ministry of Housing, Communities and Local Government | suppression, imputation | — | approximate | 0 | 0.05 | no (draft) | DRAFT: SPEC section 8 says national totals include imputation for non-responders. Confirm in the technical note. |
| S1 | Home Office / police forces (data.police.uk) | location_anonymisation | — | exact | 0 | 0 | no (draft) | Record-level counts; points are snapped to anonymous map points, which affects location not counts. |
| S3 | Youth Justice Board / Ministry of Justice | suppression | — | approximate | 0 | 0.005 | no (draft) | DRAFT: confirm. |
| S4 | Home Office | suppression | — | approximate | 0 | 0.01 | no (draft) | DRAFT: confirm. |
| S5 | Home Office | suppression | — | approximate | 0 | 0.01 | no (draft) | DRAFT: confirm. |

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
- **Small numbers:** use the intervals and smoothed rates.

## 11. Indicator catalogue

154 indicators are catalogued. Each has its own page, listed in the [index](index.md).
