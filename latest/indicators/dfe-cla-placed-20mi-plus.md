# Children in care placed over 20 miles from home

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cla_placed_20mi_plus` · concept `cla_placement_distance`


The share of children in care who live more than 20 miles from their home area.

## Definition

CLA at 31 March 2025 placed more than 20 miles from home / CLA at 31 March 2025 placed 20 miles or less or more than 20 miles from home (distance known) x 100.

## Why it is included

Indicator of placement sufficiency pressure.

## At a glance

| | |
|---|---|
| Theme | service pressure |
| Role | pressure |
| Measure type | proportion |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_17 |
| Numerator | CLA placed >20 miles from home |
| Denominator | [Children in care (distance known)](dfe-cla-distance-known-at-31mar.md): CLA at 31 March with a known placement distance (sum of the two published distance cells, same table) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

## Sources

- **C2: Children looked after in England including adoptions, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

## Quality and known biases

Some distant placements are deliberate (for safety). Unknown distances are excluded per the DfE definition.

## Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

## Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](../index.md) · [Technical methodology](../methodology_technical.md)
