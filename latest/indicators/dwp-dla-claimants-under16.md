# Children receiving Disability Living Allowance

Release `2dda583978fb-19eda0e60019` · indicator `dwp_dla_claimants_under16` · concept `disability_benefit`


The share of children under 16 receiving Disability Living Allowance, a benefit for children with extra care or mobility needs.

## Definition

DLA cases in payment aged under 16 (Feb 2025) / mid-2024 SAPE population aged 0-15.

## Why it is included

Timely small-area marker of childhood disability and complex needs.

## At a glance

| | |
|---|---|
| Theme | health |
| Role | need |
| Measure type | proportion |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | February 2025 |
| Native geography | small_area |
| Published at | small_area |
| Age bands | 0_4, 5_10, 11_15, src_0_15 |
| Numerator | DLA cases in payment, age 0-15 |
| Denominator | [Population](ons-sape-population.md): Population aged 0-15, mid-2024 SAPE (sum of single years) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

## Sources

- **F3: Disability Living Allowance claimants under 16 (Stat-Xplore)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key, suppression; additivity approximate;
  tolerance 15 absolute / 0.03 relative.

## Quality and known biases

Reflects claiming behaviour and awareness as well as need. Perturbed counts.

## Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 97.7% |

## Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| intermediate_area | 14,472 | 14,466 | 23 | 78.57% |
| lad | 120 | 120 | 58 | 4.81% |
| service_area | 31 | 31 | 47 | 3.52% |

---

[Methodology index](../index.md) · [Technical methodology](../methodology_technical.md)
