# Income deprivation affecting children (IDACI)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_idaci_score` · concept `child_poverty`


The share of children aged 0 to 15 in the neighbourhood who live in income-deprived families.

## Definition

IDACI 2025 score: proportion of children aged 0-15 living in income-deprived families (MHCLG definition, benefit and tax credit based).

## Why it is included

The official small-area measure of child poverty. The dashboard uses it for child poverty below LA level; CiLIF is used at LA level (shared concept_id child_poverty).

## At a glance

| | |
|---|---|
| Theme | child poverty |
| Role | need |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | src_0_15 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Population-weighted average of scores (MHCLG method) (weights: [Population used in the IoD 2025](mhclg-iod25-population.md)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

## Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

## Quality and known biases

Built from benefits data (2022/23 inputs), so it misses families who are eligible but not claiming, and it overlaps with the UC indicator by construction. Excludes ages 16-24.

## Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

## Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](../index.md) · [Technical methodology](../methodology_technical.md)
