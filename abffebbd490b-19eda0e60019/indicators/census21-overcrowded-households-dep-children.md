# Overcrowded households with children

Release `abffebbd490b-19eda0e60019` · indicator `census21_overcrowded_households_dep_children` · concept `overcrowding`


The share of households with children that have fewer bedrooms than they need.

## Definition

Households with dependent children with occupancy rating (bedrooms) of -1 or less / households with dependent children.

## Why it is included

Overcrowding is linked to poorer child health, sleep and educational outcomes.

## At a glance

| | |
|---|---|
| Theme | housing |
| Role | need |
| Measure type | proportion |
| Estimate type | census |
| Timing | stock |
| Reference period | Census Day, 21 March 2021 |
| Native geography | small_area |
| Published at | small_area |
| Age bands | na |
| Numerator | Households with dependent children, occupancy rating (bedrooms) <= -1 |
| Denominator | [Households with dependent children](census21-households-dependent-children.md): Households with dependent children (same table) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

## Sources

- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.

## Quality and known biases

The bedroom standard is applied to Census answers. Perturbed counts; 2021.

## Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 100.0% |

## Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| intermediate_area | 6,856 | 6,855 | 12 | 66.67% |
| lad | 296 | 293 | 34 | 3.31% |
| nation | 1 | 1 | 8 | 0.00% |
| service_area | 153 | 153 | 54 | 1.83% |

---

[Methodology index](../index.md) · [Technical methodology](../methodology_technical.md)
