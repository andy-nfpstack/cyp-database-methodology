# Population (Census 2021)

Release `abffebbd490b-19eda0e60019` · indicator `census21_usual_residents_by_age` · concept `population`


The number of people in each neighbourhood by age at the 2021 Census.

## Definition

Total usual residents by age, taken from the same Census custom tables as the disability and unpaid care counts.

## Why it is included

Census-period numerators use Census denominators (SPEC 3, Timing). Taking the total from the same table avoids mismatches from cell perturbation between tables.

## At a glance

| | |
|---|---|
| Theme | population |
| Role | denominator |
| Measure type | count |
| Estimate type | census |
| Timing | stock |
| Reference period | Census Day, 21 March 2021 |
| Native geography | small_area |
| Published at | small_area |
| Age bands | 0_24, src_5_24 |
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

- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.

## Quality and known biases

Cell-key perturbed; totals from different Census tables can differ slightly. Use only with numerators from the same table.

## Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 99.9% |

## Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| intermediate_area | 13,197 | 13,197 | 24 | 1.15% |
| lad | 397 | 397 | 68 | 0.58% |
| service_area | 181 | 181 | 135 | 0.58% |

---

[Methodology index](../index.md) · [Technical methodology](../methodology_technical.md)
