# Child referrals for suspected exploitation (NRM)

Release `2dda583978fb-19eda0e60019` · indicator `ho_nrm_referrals_under18` · concept `modern_slavery`


Children referred as potential victims of modern slavery or exploitation, per 10,000 children. This shows how actively agencies identify and refer cases.

## Definition

Potential victims aged 17 or under at referral, referred to the NRM April 2024 - March 2025 (four quarterly releases), by police force area responsible for investigation / population aged 0-17 of the force area x 10,000.

## Why it is included

Proxy for identified child exploitation (incl. county lines). Theme service_demand because it measures referral activity.

## At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 1 April 2024 to 31 March 2025 |
| Native geography | PFA |
| Published at | PFA |
| Age bands | 0_17 |
| Numerator | Under-18 NRM referrals |
| Denominator | [Population](ons-mye-population.md): Population aged 0-17, mid-2024 MYE, summed over the force area's LADs (G8) |
| Rate | per 10,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

## Sources

- **S4: National Referral Mechanism and Duty to Notify statistics** (Home Office). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.01 relative.

## Quality and known biases

Strongly shaped by first-responder awareness. Published by police force responsible for investigation only (no LA of residence), so LAs see the force-area value as a labelled fallback. British Transport Police referrals have no area (D-0074).

## Coverage

| Level | Areas with a value |
|---|---|
| PFA | 100.0% |
| lad | 0.3% |
| service_area | 5.2% |

## Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](../index.md) · [Technical methodology](../methodology_technical.md)
