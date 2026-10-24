# EHC plans (ages 0-25)

Release `2dda583978fb-19eda0e60019` · indicator `dfe_ehcps_0_25` · concept `send`


The number of young people aged 0 to 25 with an EHC plan the council is responsible for, per 10,000 young people.

## Definition

EHCPs maintained by the LA at January 2025 (SEN2) / population aged 0-25 (mid-2024 MYE) x 10,000.

## Why it is included

Total SEND statutory demand; runs to age 25, hence the 0_25 total.

## At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | January 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | source_bands, 0_25 |
| Numerator | EHCPs maintained, January 2025 |
| Denominator | [Population](ons-mye-population.md): Population aged 0-25, mid-2024 MYE |
| Rate | per 10,000 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

## Sources

- **E2: Education, health and care plans (SEN2), January 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

## Quality and known biases

practice_sensitive. LA responsibility, not residence, in some edge cases.

## Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

## Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 7 | 7 | 0 | 0.00% |

---

[Methodology index](../index.md) · [Technical methodology](../methodology_technical.md)
