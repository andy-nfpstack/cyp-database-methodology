# Children in relative low income families (%)

Release `2dda583978fb-19eda0e60019` · indicator `dwp_cilif_relative_bhc_pct` · concept `child_poverty`


The share of children living in families below 60% of the current UK average income, before housing costs.

## Definition

Percentage as published by DWP: children aged 0-15 in relative low income families / ONS mid-2024 population aged 0-15 x 100 (DWP CiLIF note 3). DWP publishes it for lower-tier and unitary councils; for the 21 county councils it is computed by DWP's method from the summed district counts (D-0085).

## Why it is included

A rate is needed for comparison. The DWP denominator is used because no population age band matches 'dependent children aged 0-19' exactly (SPEC 3: never trim a band).

## At a glance

| | |
|---|---|
| Theme | child poverty |
| Role | need |
| Measure type | percent published |
| Estimate type | survey calibrated |
| Timing | flow |
| Reference period | Financial year ending March 2025 |
| Native geography | lad |
| Published at | lad |
| Age bands | src_0_15, src_0_19 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

## Sources

- **F1: Children in Low Income Families: local area statistics (FYE 2025)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.

## Quality and known biases

Survey-calibrated; BHC understates high-housing-cost areas. County council values are our calculation by DWP's stated method, which reproduces all 428 published LA percentages exactly; they are flagged 'derived by the publisher's method'. For custom regions sum the counts and the 0-15 population, then divide.

## Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 86.3% |

## Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](../index.md) · [Technical methodology](../methodology_technical.md)
