# Permanent exclusions from school

Release `2dda583978fb-19eda0e60019` · indicator `dfe_permanent_exclusions` · concept `exclusions`


Pupils permanently excluded from school during the year, per 10,000 pupils.

## Definition

Permanent exclusions in the academic year / pupil headcount x 10,000.

## Why it is included

The most serious school sanction; strong risk marker.

## At a glance

| | |
|---|---|
| Theme | education |
| Role | need |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Academic year 2024/25 (check) |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_pupils_all |
| Numerator | Permanent exclusions |
| Denominator | [Pupils (exclusions publication)](dfe-exclusions-headcount.md): Pupil headcount (same file) |
| Rate | per 10,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

## Sources

- **E4: Suspensions and permanent exclusions in England** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

## Quality and known biases

Small numbers; per 10,000 (DfE publishes per 100) so values are readable. Use CIs.

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
