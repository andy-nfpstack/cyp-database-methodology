# Social care assessments

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cin_assessments_completed` · concept `cin_assessments`


Social care assessments completed during the year, per 10,000 children.

## Definition

Assessments completed in year ending 31 March 2025 / population aged 0-17 x 10,000.

## Why it is included

Workload measure between referral and plan.

## At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 1 April 2024 to 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_17 |
| Numerator | Assessments completed in year |
| Denominator | [Population](ons-mye-population.md): Population aged 0-17, mid-2024 MYE |
| Rate | per 10,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

## Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

## Quality and known biases

Event count; practice-sensitive.

## Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

## Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](../index.md) · [Technical methodology](../methodology_technical.md)
