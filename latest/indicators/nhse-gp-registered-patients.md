# GP-registered population

Release `2dda583978fb-19eda0e60019` · indicator `nhse_gp_registered_patients` · concept `population_gp_registered`


The number of people registered with a GP who live in each neighbourhood.

## Definition

Patients registered at GP practices in England on 1 April 2025, by Sub-ICB location (April 2024 configuration), single year of age (0 to 95+, stored to 90+) and sex, as published by NHS England.

## Why it is included

NHS activity data (MHSDS) is attributed by GP registration, so health-geography weights and denominators use the registered population, not the resident population (SPEC 4.4).

## At a glance

| | |
|---|---|
| Theme | population |
| Role | denominator |
| Measure type | count |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | 1 April 2025 |
| Native geography | SICBL24 |
| Published at | SICBL24 |
| Age bands | single_year |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | neither better nor worse |
| Aggregating to other areas | Sum the counts |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

## Sources

- **G3b: Patients Registered at a GP Practice (LSOA by age and sex)** (NHS England). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

## Quality and known biases

Published by Sub-ICB location only: NHS England publishes no LSOA x age file (LSOA files are all ages), so LSOA counts are used only as apportionment weights (D-0070). Registered lists are inflated by people who have moved away or died ('list inflation'), most of all among young adults and in cities. Not the same as the resident population.

## Coverage

| Level | Areas with a value |
|---|---|
| SICBL24 | 100.0% |
| lad | 14.5% |
| nation | 100.0% |
| service_area | 30.1% |

## Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](../index.md) · [Technical methodology](../methodology_technical.md)
