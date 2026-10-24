# LA system pressure: capacity domain

Release `2dda583978fb-19eda0e60019` · indicator `l5_la_system_pressure_capacity` · concept `la_system_pressure_capacity`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

The capacity part of the la system pressure index; higher means more pressure.

## Definition

Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3).

## Why it is included

Shows which domain drives an area's composite score.

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
- **C2: Children looked after in England including adoptions, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.
- **C3: Children's social work workforce, at 30 September 2024** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 1 absolute / 0.005 relative.
- **E2: Education, health and care plans (SEN2), January 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **S4: National Referral Mechanism and Duty to Notify statistics** (Home Office). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.01 relative.

## Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

## Coverage

_Coverage is generated at release._

## Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](../index.md) · [Technical methodology](../methodology_technical.md)
