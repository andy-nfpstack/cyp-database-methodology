# Children in relative low income families

Release `abffebbd490b-19eda0e60019` · indicator `dwp_cilif_relative_bhc` · concept `child_poverty`


The number of children living in families whose income is below 60% of the current UK average, before housing costs.

## Definition

DWP CiLIF: children (under 16, or 16-19 in non-advanced education) in families with equivalised household income below 60% of contemporary median, BHC, calibrated to the national survey (HBAI).

## Why it is included

The main official LA-level child poverty statistic. The dashboard uses it at LA level, with IDACI below LA level (shared concept_id child_poverty).

## At a glance

| | |
|---|---|
| Theme | child poverty |
| Role | need |
| Measure type | count |
| Estimate type | survey calibrated |
| Timing | flow |
| Reference period | Financial year ending March 2025 |
| Native geography | lad |
| Published at | lad, WD25 |
| Age bands | 0_4, 5_10, 11_15, src_16_19, src_0_19 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum the counts |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

## Sources

- **F1: Children in Low Income Families: local area statistics (FYE 2025)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.

## Quality and known biases

Survey-calibrated, BHC only, so it understates poverty where housing costs are high (e.g. London). Perturbed counts. Children are dependent children (to age 19), which does not match any population age band exactly.

## Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |

## Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 5 | 5 | 43 | 0.01% |

---

[Methodology index](../index.md) · [Technical methodology](../methodology_technical.md)
