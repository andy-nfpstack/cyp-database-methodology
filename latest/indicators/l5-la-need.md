# La need index

Release `abffebbd490b-19eda0e60019` · indicator `l5_la_need` · concept `la_need`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

A combined measure of need from 6 domains; higher means more need.

## Definition

IoD-style composite (SPEC 12.3): rank-based normal scores within domains, exponentially transformed domain scores, equal domain weights.

## Why it is included

Summarises many indicators for comparison; need and pressure are kept apart.

## At a glance

| | |
|---|---|
| Theme | composite |
| Role | composite |
| Measure type | score |
| Estimate type | composite experimental |
| Timing | not applicable |
| Reference period | Inputs from several periods, Census 2021 to 2025 (see the composite methodology) |
| Native geography | service_area |
| Published at | service_area |
| Age bands | na |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | no |
| Ethnicity classification | none |

## Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.
- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.
- **E3: Pupil absence in schools in England, 2024/25** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **E4: Suspensions and permanent exclusions in England** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **E5: Participation in education, training and NEET age 16 to 17 by local authority** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 10 absolute / 0.005 relative.
- **E6: Schools, pupils and their characteristics, January 2025 (FSM by pupil residence)** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **F1: Children in Low Income Families: local area statistics (FYE 2025)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **H2: Fingertips: Child and Maternal Health profile (API)** (Office for Health Improvement and Disparities). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **Ho1: Statutory homelessness in England: detailed local authority tables (H-CLIC)** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, imputation; additivity approximate;
  tolerance 0 absolute / 0.05 relative.
- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.
- **S3: Youth justice statistics 2024 to 2025** (Youth Justice Board / Ministry of Justice). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

## Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

## Coverage

_Coverage is generated at release._

## Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](../index.md) · [Technical methodology](../methodology_technical.md)
