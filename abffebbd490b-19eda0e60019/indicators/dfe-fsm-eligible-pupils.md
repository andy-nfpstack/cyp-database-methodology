# Pupils eligible for free school meals

Release `abffebbd490b-19eda0e60019` · indicator `dfe_fsm_eligible_pupils` · concept `fsm_eligibility`


The share of pupils at schools in the authority who are eligible for free school meals.

## Definition

Pupils known to be eligible for FSM / pupils on roll (both as used for FSM in performance tables), all schools in the SPC FSM table, by LA of school, January 2025.

## Why it is included

Timely, administrative indicator of low family income for school-age children.

## At a glance

| | |
|---|---|
| Theme | child poverty |
| Role | need |
| Measure type | proportion |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | January 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_pupils_all |
| Numerator | Pupils known to be eligible for free school meals |
| Denominator | [Pupils](dfe-pupils-on-roll.md): Pupils on roll used for FSM in performance tables (same table, same school-location basis) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

## Sources

- **E6: Schools, pupils and their characteristics, January 2025 (FSM by pupil residence)** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

## Quality and known biases

Eligibility reflects benefit rules and UC transitional protection, so it has risen for policy as well as economic reasons. Excludes independent and home-educated pupils. By LA of school: DfE does not publish LA FSM by pupil residence in this release (D-0058).

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
