# Children in absolute low income families

Release `abffebbd490b-19eda0e60019` · indicator `dwp_cilif_absolute_bhc` · concept `child_poverty`


The number of children living in families whose income is below a fixed poverty line (60% of the 2024/25 UK average, adjusted for inflation), before housing costs.

## Definition

DWP CiLIF absolute low income, BHC: equivalised household income below 60% of the FYE 2025 median held constant in real terms, calibrated to HBAI. DWP moved the reference year from FYE 2011 to FYE 2025 in this release and revised the back series.

## Why it is included

A complement to relative poverty that does not move with average incomes.

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

As for relative CiLIF. Because FYE 2025 is now the reference year, absolute and relative figures for FYE 2025 are identical in every area (checked: all LA, country and age-band cells match); later years will differ as the absolute line is held fixed in real terms.

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
