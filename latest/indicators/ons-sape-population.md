# Population

Release `abffebbd490b-19eda0e60019` · indicator `ons_sape_population` · concept `population`


The estimated number of people living in each neighbourhood, by single year of age and sex.

## Definition

ONS mid-year Small Area Population Estimates for LSOA21, single year of age (0 to 90+) by sex.

## Why it is included

Denominator for every small-area rate. Stored by single year of age so that a denominator can be built exactly for any source age band (SPEC section 3).

## At a glance

| | |
|---|---|
| Theme | population |
| Role | denominator |
| Measure type | count |
| Estimate type | model based |
| Timing | stock |
| Reference period | 30 June 2024 (mid-2024) |
| Native geography | small_area |
| Published at | small_area, intermediate_area |
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

- **P1: Lower layer Super Output Area population estimates (Small Area Population Estimates), single year of age and sex** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity exact;
  tolerance 0 absolute / 0 relative.

## Quality and known biases

Model-based estimates constrained to LA mid-year totals. Small areas carry more uncertainty than LAs (no published CIs). Areas with large student or armed-forces populations are less reliable at ages 18-24.

## Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

## Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| intermediate_area | 1,254,648 | 1,254,648 | 0 | 0.00% |

---

[Methodology index](../index.md) · [Technical methodology](../methodology_technical.md)
