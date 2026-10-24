# Parental mental health identified at assessment

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cin_factor_parental_mental_health` · concept `assessment_factors`


Of completed social care assessments, the share where a parent's or carer's mental health was identified as a concern.

## Definition

Episodes with an assessment completed in the year where the factor 'Mental health: concerns about parent' (Mental_Health_parent) was recorded / episodes with assessment factor information (Episodes_with_assessment_factor), DfE CIN table C3, x 100.

## Why it is included

Family risk factor visible only through social care data.

## At a glance

| | |
|---|---|
| Theme | family risk |
| Role | need |
| Measure type | proportion |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 1 April 2024 to 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_17 |
| Numerator | Episodes with the 'Mental health: concerns about parent' factor at end of assessment (Mental_Health_parent) |
| Denominator | [Assessments with factors recorded](dfe-cin-episodes-with-assessment-factors.md): Episodes with assessment factor information (Episodes_with_assessment_factor, same table) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

## Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

## Quality and known biases

Only covers children who reached assessment, so it reflects practice and thresholds as well as need. Factor recording varies between LAs. An episode can have several factors. Excludes episodes with no factors identified (DfE footnote 2).

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
