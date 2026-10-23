# Children supported by NHS mental health services

Release `abffebbd490b-19eda0e60019` · indicator `nhse_mhsds_cyp_one_plus_contact_12m` · concept `cyp_mental_health_access`


Children and young people who had at least one contact with NHS mental health services in the past year, per 10,000 registered with a GP.

## Definition

MHSDS measure MHS95: children and young people aged under 18 supported through NHS-funded mental health services with at least one contact in the 12 months to 31 March 2025, by Sub-ICB of GP practice or residence / GP-registered population aged 0-17 on 1 April 2025 x 10,000.

## Why it is included

The NHS access measure for CYP mental health; indicates service activity, not prevalence.

## At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 12 months to 31 March 2025 |
| Native geography | SICBL24 |
| Published at | SICBL24 |
| Age bands | 0_17 |
| Numerator | CYP 0-17 with 1+ contact, rolling 12 months |
| Denominator | [GP-registered population](nhse-gp-registered-patients.md): GP-registered population aged 0-17, 1 April 2025, as published by Sub-ICB (G3b) |
| Rate | per 10,000 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | neither better nor worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

## Sources

- **H1: Mental Health Services Monthly Statistics (MHSDS), March 2025 performance** (NHS England). Licence: Open Government Licence v3.0.
  Disclosure control: rounding, suppression; additivity approximate;
  tolerance 5 absolute / 0.01 relative.

## Quality and known biases

A deduplicated person count: Sub-ICB figures sum to more than England (a child can be seen in two Sub-ICBs), so it is never summed across areas (D-0072). Rounded to 5, with suppression. Attributed by GP registration. Data quality varies between providers. Sub-ICB geography: LA values are relabelled, aggregated or shown as fallback per relationship type.

## Coverage

| Level | Areas with a value |
|---|---|
| SICBL24 | 100.0% |
| lad | 14.2% |
| nation | 100.0% |
| service_area | 28.8% |

## Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](../index.md) · [Technical methodology](../methodology_technical.md)
