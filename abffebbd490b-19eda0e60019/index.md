# England Children and Young People (0–24) Need and System Pressure Database: methodology

Release `abffebbd490b-19eda0e60019` · composites version `0.1-experimental`

## What this is

A point-in-time database of indicators of need and of pressure on services for children
and young people aged 0 to 24 in England. It covers England, children's services
authorities, lower-tier local authorities, and neighbourhoods (MSOAs and LSOAs). Every
value comes from an official published statistic, or is calculated from one by a documented method.

## What it can and cannot tell you

- It **can** show how areas compare on each measure, how sure we can be of each figure,
  and why a figure is missing.
- It **cannot** tell you about individual children, prove that one thing causes another, or show
  trends (it is one snapshot). Area figures describe areas, not the people in them
  (the ecological fallacy).
- Need and system pressure are kept separate on purpose. Service activity partly reflects
  local practice and thresholds, so it is not treated as a measure of need.

## How to read a value

- **Value**: a count, a rate (with its denominator) or a published score.
- **Uncertainty interval**: for administrative counts, this reflects the random variation
  you would expect in the underlying process, not sampling error.
- **Missing-data reason**: every blank has a reason: `suppressed`, `not_published`,
  `incomplete` or `not_applicable`.
- **Fallback (hatched)**: a value shown for a larger containing area (for example a police force
  area), clearly labelled. It is never used in calculations.

## Contents

- [Plain-English guide](guide_plain_english.md)
- [Technical methodology](methodology_technical.md)
- [Composite indices (experimental)](composites/methodology_composite.md)
- [Decision log](decision_log.md)
- [QA summary](qa_summary.md)
- [Changelog](changelog.md)

### Indicators

**Population**

- [Population](indicators/ons-sape-population.md) (denominator)
- [Population](indicators/ons-mye-population.md) (denominator)
- [Population by ethnic group (Census 2021)](indicators/census21-population-by-ethnicity.md) (denominator)
- [Population (Census 2021)](indicators/census21-usual-residents-by-age.md) (denominator)
- [GP-registered population](indicators/nhse-gp-registered-patients.md) (denominator)
- [Pupils by ethnic group](indicators/dfe-pupils-by-ethnicity.md) (denominator)
- [Pupils](indicators/dfe-pupils-on-roll.md) (denominator)
- [Population used in the IoD 2025](indicators/mhclg-iod25-population.md) (denominator)
- [Households with dependent children](indicators/census21-households-dependent-children.md) (denominator)
- [Assessments with factors recorded](indicators/dfe-cin-episodes-with-assessment-factors.md) (denominator)
- [Children in care (distance known)](indicators/dfe-cla-distance-known-at-31mar.md) (denominator)
- [Children in care (stability base)](indicators/dfe-cla-stability-base-at-31mar.md) (denominator)
- [Pupils (SEN publication)](indicators/dfe-pupils-total-sen-publication.md) (denominator)
- [Pupil enrolments](indicators/dfe-absence-enrolments.md) (denominator)
- [Pupils (exclusions publication)](indicators/dfe-exclusions-headcount.md) (denominator)
- [16-17 year olds known to the council](indicators/dfe-neet-cohort-16-17.md) (denominator)
- [People receiving asylum support](indicators/ho-asylum-support-recipients.md)

**Deprivation**

- [Index of Multiple Deprivation (score)](indicators/mhclg-iod25-imd-score.md)
- [Index of Multiple Deprivation (rank)](indicators/mhclg-iod25-imd-rank.md)
- [Index of Multiple Deprivation (decile)](indicators/mhclg-iod25-imd-decile.md)
- [Income deprivation (score)](indicators/mhclg-iod25-income-score.md)
- [Income deprivation (decile)](indicators/mhclg-iod25-income-decile.md)
- [Employment deprivation (score)](indicators/mhclg-iod25-employment-score.md)
- [Employment deprivation (decile)](indicators/mhclg-iod25-employment-decile.md)
- [Education, skills and training deprivation (score)](indicators/mhclg-iod25-education-score.md)
- [Education, skills and training deprivation (decile)](indicators/mhclg-iod25-education-decile.md)
- [Health deprivation and disability (score)](indicators/mhclg-iod25-health-score.md)
- [Health deprivation and disability (decile)](indicators/mhclg-iod25-health-decile.md)
- [Crime deprivation (score)](indicators/mhclg-iod25-crime-score.md)
- [Crime deprivation (decile)](indicators/mhclg-iod25-crime-decile.md)
- [Barriers to housing and services (score)](indicators/mhclg-iod25-barriers-score.md)
- [Barriers to housing and services (decile)](indicators/mhclg-iod25-barriers-decile.md)
- [Living environment deprivation (score)](indicators/mhclg-iod25-living-env-score.md)
- [Living environment deprivation (decile)](indicators/mhclg-iod25-living-env-decile.md)
- [Index of Multiple Deprivation: average score](indicators/mhclg-iod25-imd-la-avg-score.md)
- [Index of Multiple Deprivation: average rank](indicators/mhclg-iod25-imd-la-avg-rank.md)
- [Index of Multiple Deprivation: extent](indicators/mhclg-iod25-imd-la-extent.md)
- [Index of Multiple Deprivation: local concentration](indicators/mhclg-iod25-imd-la-local-concentration.md)
- [Neighbourhoods in England's most deprived 10%](indicators/mhclg-iod25-imd-la-prop-most-deprived-10pct.md)
- [Income deprivation: average score](indicators/mhclg-iod25-income-la-avg-score.md)
- [Income deprivation: neighbourhoods in England's most deprived 10%](indicators/mhclg-iod25-income-la-prop-most-deprived-10pct.md)
- [Employment deprivation: average score](indicators/mhclg-iod25-employment-la-avg-score.md)
- [Employment deprivation: neighbourhoods in England's most deprived 10%](indicators/mhclg-iod25-employment-la-prop-most-deprived-10pct.md)
- [Education, skills and training deprivation: average score](indicators/mhclg-iod25-education-la-avg-score.md)
- [Education, skills and training deprivation: neighbourhoods in England's most deprived 10%](indicators/mhclg-iod25-education-la-prop-most-deprived-10pct.md)
- [Health deprivation and disability: average score](indicators/mhclg-iod25-health-la-avg-score.md)
- [Health deprivation and disability: neighbourhoods in England's most deprived 10%](indicators/mhclg-iod25-health-la-prop-most-deprived-10pct.md)
- [Crime (IoD domain): average score](indicators/mhclg-iod25-crime-la-avg-score.md)
- [Crime (IoD domain): neighbourhoods in England's most deprived 10%](indicators/mhclg-iod25-crime-la-prop-most-deprived-10pct.md)
- [Barriers to housing and services: average score](indicators/mhclg-iod25-barriers-la-avg-score.md)
- [Barriers to housing and services: neighbourhoods in England's most deprived 10%](indicators/mhclg-iod25-barriers-la-prop-most-deprived-10pct.md)
- [Living environment deprivation: average score](indicators/mhclg-iod25-living-env-la-avg-score.md)
- [Living environment deprivation: neighbourhoods in England's most deprived 10%](indicators/mhclg-iod25-living-env-la-prop-most-deprived-10pct.md)

**Child poverty**

- [Income deprivation affecting children (IDACI)](indicators/mhclg-iod25-idaci-score.md)
- [Income deprivation affecting children (rank)](indicators/mhclg-iod25-idaci-rank.md)
- [Income deprivation affecting children (decile)](indicators/mhclg-iod25-idaci-decile.md)
- [Income deprivation affecting children: average score](indicators/mhclg-iod25-idaci-la-avg-score.md)
- [Income deprivation affecting children: average rank](indicators/mhclg-iod25-idaci-la-avg-rank.md)
- [Neighbourhoods in England's most deprived 10% for child income](indicators/mhclg-iod25-idaci-la-prop-most-deprived-10pct.md)
- [Children in relative low income families](indicators/dwp-cilif-relative-bhc.md)
- [Children in relative low income families (%)](indicators/dwp-cilif-relative-bhc-pct.md)
- [Children in absolute low income families](indicators/dwp-cilif-absolute-bhc.md)
- [Children in absolute low income families (%)](indicators/dwp-cilif-absolute-bhc-pct.md)
- [Households with children on Universal Credit](indicators/dwp-uc-households-with-children.md)
- [Pupils eligible for free school meals](indicators/dfe-fsm-eligible-pupils.md)

**Education**

- [Children's education deprivation (score)](indicators/mhclg-iod25-education-cyp-subdomain-score.md)
- [Care leavers not in education, employment or training](indicators/dfe-care-leavers-19-21-neet.md)
- [Pupils with an EHC plan](indicators/dfe-pupils-with-ehcp.md)
- [Pupils receiving SEN support](indicators/dfe-pupils-sen-support.md)
- [Pupils with autism as their main need](indicators/dfe-sen-primary-need-asd.md)
- [Persistent absence from school](indicators/dfe-persistent-absence.md)
- [Severe absence from school](indicators/dfe-severe-absence.md)
- [Suspensions from school](indicators/dfe-suspensions.md)
- [Permanent exclusions from school](indicators/dfe-permanent-exclusions.md)
- [16-17 year olds not in education, employment or training](indicators/dfe-neet-16-17.md)
- [16-17 year olds NEET or activity not known](indicators/dfe-neet-or-not-known-16-17.md)

**Family risk**

- [Lone-parent households](indicators/census21-lone-parent-households-dep-children.md)
- [Young carers](indicators/census21-unpaid-carers-5-24.md)
- [Domestic abuse identified at assessment](indicators/dfe-cin-factor-domestic-abuse.md)
- [Parental mental health identified at assessment](indicators/dfe-cin-factor-parental-mental-health.md)
- [Parental alcohol misuse identified at assessment](indicators/dfe-cin-factor-parental-alcohol-misuse.md)
- [Parental drug misuse identified at assessment](indicators/dfe-cin-factor-parental-drug-misuse.md)
- [Adults in drug/alcohol treatment living with children](indicators/ohid-ndtms-adults-in-treatment-living-with-children.md)
- [Parents in drug/alcohol treatment not living with their children](indicators/ohid-ndtms-parents-not-living-with-children.md)

**Housing**

- [Overcrowded households with children](indicators/census21-overcrowded-households-dep-children.md)
- [Households with children in temporary accommodation](indicators/mhclg-hclic-households-with-children-in-ta.md)
- [Children in temporary accommodation](indicators/mhclg-hclic-children-in-ta.md)
- [Children in temporary accommodation](indicators/mhclg-hclic-children-in-ta-by-age.md)
- [Families assessed as homeless or at risk](indicators/mhclg-hclic-owed-duty-households-with-children.md)
- [Young people assessed as homeless or at risk (16-24)](indicators/mhclg-hclic-owed-duty-applicants-16-24.md)

**Health**

- [Disabled children and young people](indicators/census21-disabled-0-24.md)
- [Children receiving Disability Living Allowance](indicators/dwp-dla-claimants-under16.md)
- [Young people receiving PIP](indicators/dwp-pip-claimants-16-24.md)
- [Pupils with social, emotional and mental health needs](indicators/dfe-sen-primary-need-semh.md)
- [Hospital admissions for self-harm (10-24)](indicators/ohid-self-harm-admissions-10-24.md)
- [A&E attendances (under 5s)](indicators/ohid-ae-attendances-0-4.md)
- [Infant mortality](indicators/ohid-infant-mortality.md)
- [Under-18 conceptions](indicators/ohid-under18-conceptions.md)
- [Low birth weight (full-term babies)](indicators/ohid-low-birthweight-term.md)
- [Hospital admissions for injuries (0-14)](indicators/ohid-injury-admissions-0-14.md)

**Safety**

- [Recorded crime](indicators/police-crime-all-excl-asb.md)
- [Violence and sexual offences](indicators/police-crime-violence-sexual.md)
- [Anti-social behaviour](indicators/police-asb-incidents.md)
- [Possession of weapons](indicators/police-crime-weapons-possession.md)
- [Drug offences](indicators/police-crime-drugs.md)
- [First-time entrants to youth justice](indicators/yjb-first-time-entrants-10-17.md)
- [Custodial sentences (10-17)](indicators/yjb-custodial-sentences-10-17.md)
- [Proven offences by children (10-17)](indicators/yjb-proven-offences-10-17.md)

**Service demand**

- [Children in need](indicators/dfe-cin-at-31mar.md)
- [Referrals to children's social care](indicators/dfe-cin-referrals.md)
- [Re-referrals within 12 months](indicators/dfe-cin-rereferrals-12m.md)
- [Social care assessments](indicators/dfe-cin-assessments-completed.md)
- [Children on child protection plans](indicators/dfe-cpp-at-31mar.md)
- [New child protection plans](indicators/dfe-cpp-starts.md)
- [Children in care](indicators/dfe-cla-at-31mar.md)
- [Children entering care](indicators/dfe-cla-starts.md)
- [Unaccompanied asylum-seeking children in care](indicators/dfe-cla-uasc-at-31mar.md)
- [Care leavers aged 17 to 21](indicators/dfe-care-leavers-17-21.md)
- [Care leavers aged 19 to 21](indicators/dfe-care-leavers-19-21.md) (denominator)
- [Adoptions from care](indicators/dfe-cla-ceased-adoption.md)
- [EHC plans (ages 0-25)](indicators/dfe-ehcps-0-25.md)
- [New EHC plans](indicators/dfe-ehcp-new-plans.md)
- [Child referrals for suspected exploitation (NRM)](indicators/ho-nrm-referrals-under18.md)
- [Children supported by NHS mental health services](indicators/nhse-mhsds-cyp-one-plus-contact-12m.md)
- [Children with open mental health referrals](indicators/nhse-mhsds-cyp-open-referrals.md)

**Service pressure**

- [Children in care placed over 20 miles from home](indicators/dfe-cla-placed-20mi-plus.md)
- [Children in care with 3+ placements in the year](indicators/dfe-cla-3plus-placements.md)
- [Social worker vacancy rate](indicators/dfe-sw-vacancy-rate.md)
- [Agency social worker rate](indicators/dfe-sw-agency-rate.md)
- [Social worker turnover rate](indicators/dfe-sw-turnover-rate.md)
- [Average social worker caseload](indicators/dfe-sw-average-caseload.md)
- [Spending on children's services per child](indicators/dfe-s251-cyp-services-net.md)
- [Spending on children in care per child](indicators/dfe-s251-cla-net.md)
- [Spending on family support per child](indicators/dfe-s251-family-support-net.md)
- [Spending on youth services per young person](indicators/dfe-s251-young-people-services-net.md)
- [Ofsted judgement: children's services](indicators/ofsted-ilacs-overall-effectiveness.md)
- [Children's homes](indicators/ofsted-childrens-homes.md)
- [Children's home places](indicators/ofsted-childrens-homes-places.md)
- [EHC plans issued on time](indicators/dfe-ehcp-20wk-timeliness.md)

**Composite**

- [Neighbourhood need index](indicators/l5-neighbourhood-need.md)
- [Neighbourhood need: economic hardship domain](indicators/l5-neighbourhood-need-economic-hardship.md)
- [Neighbourhood need: health disability domain](indicators/l5-neighbourhood-need-health-disability.md)
- [Neighbourhood need: family housing domain](indicators/l5-neighbourhood-need-family-housing.md)
- [Neighbourhood need: safety domain](indicators/l5-neighbourhood-need-safety.md)
- [La need index](indicators/l5-la-need.md)
- [La need: economic hardship domain](indicators/l5-la-need-economic-hardship.md)
- [La need: family risk domain](indicators/l5-la-need-family-risk.md)
- [La need: health domain](indicators/l5-la-need-health.md)
- [La need: education domain](indicators/l5-la-need-education.md)
- [La need: housing domain](indicators/l5-la-need-housing.md)
- [La need: safety domain](indicators/l5-la-need-safety.md)
- [La system pressure: demand domain](indicators/l5-la-system-pressure-demand.md)
- [La system pressure: capacity domain](indicators/l5-la-system-pressure-capacity.md)
- [La system pressure: send domain](indicators/l5-la-system-pressure-send.md)

## How to cite

> England Children and Young People Need and System Pressure Database, release
> `abffebbd490b-19eda0e60019`. Contains public sector information licensed under the Open
> Government Licence v3.0. Source attributions are listed in `sources.csv`.

## Applying the Code of Practice for Statistics (voluntarily)

- **Trustworthiness:** all code, configuration and decisions are versioned. Every release
  can be rebuilt from its raw inputs, and every judgement is in the decision log.
- **Quality:** source data is never altered. Suppression is preserved. Uncertainty and
  missing-data reasons are published with every value, and QA gates must pass before release.
- **Value:** measures are chosen for their relevance to children and young people, and are
  documented in plain English as well as technically.

## Feedback

We welcome methodological feedback, especially on the experimental composites. Contact
details for the publishing charity are added at release.
