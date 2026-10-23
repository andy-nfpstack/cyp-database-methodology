# Anti-social behaviour

Release `abffebbd490b-19eda0e60019` · indicator `police_asb_incidents` · concept `recorded_asb`


Anti-social behaviour incidents reported to the police in the neighbourhood per 1,000 residents over the year. Area context.

## Definition

Street-level records with category 'Anti-social behaviour', Apr 2024 - Mar 2025, per 1,000 usual residents.

## Why it is included

Indicates perceived local disorder.

## At a glance

| | |
|---|---|
| Theme | safety |
| Role | context |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 1 April 2024 to 31 March 2025 |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | Street-level ASB records |
| Denominator | [Population](ons-sape-population.md): Usual resident population, all ages, mid-2024 (SAPE) |
| Rate | per 1,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

## Sources

- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.

## Quality and known biases

Incidents, not crimes. Recording varies a great deal by force.

## Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 100.0% |

## Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](../index.md) · [Technical methodology](../methodology_technical.md)
