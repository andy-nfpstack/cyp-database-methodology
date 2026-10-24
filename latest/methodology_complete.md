# England Children and Young People (0–24) Need and System Pressure Database: complete methodology

Release `2dda583978fb-19eda0e60019`. Every page of the published methodology pack in one file: the plain-English guide, the technical methodology, the composite methodology and results, the transformation specification, QA results, references, the full decision log and one section per indicator.

## Contents

- [England Children and Young People (0–24) Need and System Pressure Database: methodology](#page-index)
- [A plain-English guide](#page-guide_plain_english)
- [Technical methodology](#page-methodology_technical)
- [Composite indices: methodology (experimental)](#page-composites-methodology_composite)
- [LA need (experimental)](#page-composites-la_need)
- [LA system pressure (experimental)](#page-composites-la_system_pressure)
- [Neighbourhood need (experimental)](#page-composites-neighbourhood_need)
- [Transformation specification](#page-transformations)
- [QA summary](#page-qa_summary)
- [References](#page-references)
- [Decision log](#page-decision_log)
- [Changelog](#page-changelog)
- [Indicators](#page-indicators-census21-disabled-0-24) (154 pages, alphabetical by identifier)

---

<a id="page-index"></a>

## England Children and Young People (0–24) Need and System Pressure Database: methodology

Release `2dda583978fb-19eda0e60019` · composites version `0.1-experimental`

### What this is

A point-in-time database of indicators of need and of pressure on services for children
and young people aged 0 to 24 in England. It covers England, children's services
authorities, lower-tier local authorities, and neighbourhoods (MSOAs and LSOAs). Every
value comes from an official published statistic, or is calculated from one by a documented method.

### What it can and cannot tell you

- It **can** show how areas compare on each measure, how sure we can be of each figure,
  and why a figure is missing.
- It **cannot** tell you about individual children, prove that one thing causes another, or show
  trends (it is one snapshot). Area figures describe areas, not the people in them
  (the ecological fallacy).
- Need and system pressure are kept separate on purpose. Service activity partly reflects
  local practice and thresholds, so it is not treated as a measure of need.

### How to read a value

- **Value**: a count, a rate (with its denominator) or a published score.
- **Uncertainty interval**: for administrative counts, this reflects the random variation
  you would expect in the underlying process, not sampling error.
- **Missing-data reason**: every blank has a reason: `suppressed`, `not_published`,
  `incomplete` or `not_applicable`.
- **Fallback (hatched)**: a value shown for a larger containing area (for example a police force
  area), clearly labelled. It is never used in calculations.

### Contents

- [Plain-English guide](#page-guide_plain_english)
- [Technical methodology](#page-methodology_technical)
- [Composite indices (experimental)](#page-composites-methodology_composite)
- [Decision log](#page-decision_log)
- [QA summary](#page-qa_summary)
- [Changelog](#page-changelog)

#### Indicators

**Population**

- [Population](#page-indicators-ons-sape-population) (denominator)
- [Population](#page-indicators-ons-mye-population) (denominator)
- [Population by ethnic group (Census 2021)](#page-indicators-census21-population-by-ethnicity) (denominator)
- [Population (Census 2021)](#page-indicators-census21-usual-residents-by-age) (denominator)
- [GP-registered population](#page-indicators-nhse-gp-registered-patients) (denominator)
- [Pupils by ethnic group](#page-indicators-dfe-pupils-by-ethnicity) (denominator)
- [Pupils](#page-indicators-dfe-pupils-on-roll) (denominator)
- [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population) (denominator)
- [Households with dependent children](#page-indicators-census21-households-dependent-children) (denominator)
- [Assessments with factors recorded](#page-indicators-dfe-cin-episodes-with-assessment-factors) (denominator)
- [Children in care (distance known)](#page-indicators-dfe-cla-distance-known-at-31mar) (denominator)
- [Children in care (stability base)](#page-indicators-dfe-cla-stability-base-at-31mar) (denominator)
- [Pupils (SEN publication)](#page-indicators-dfe-pupils-total-sen-publication) (denominator)
- [Pupil enrolments](#page-indicators-dfe-absence-enrolments) (denominator)
- [Pupils (exclusions publication)](#page-indicators-dfe-exclusions-headcount) (denominator)
- [16-17 year olds known to the council](#page-indicators-dfe-neet-cohort-16-17) (denominator)
- [People receiving asylum support](#page-indicators-ho-asylum-support-recipients)

**Deprivation**

- [Index of Multiple Deprivation (score)](#page-indicators-mhclg-iod25-imd-score)
- [Index of Multiple Deprivation (rank)](#page-indicators-mhclg-iod25-imd-rank)
- [Index of Multiple Deprivation (decile)](#page-indicators-mhclg-iod25-imd-decile)
- [Income deprivation (score)](#page-indicators-mhclg-iod25-income-score)
- [Income deprivation (decile)](#page-indicators-mhclg-iod25-income-decile)
- [Employment deprivation (score)](#page-indicators-mhclg-iod25-employment-score)
- [Employment deprivation (decile)](#page-indicators-mhclg-iod25-employment-decile)
- [Education, skills and training deprivation (score)](#page-indicators-mhclg-iod25-education-score)
- [Education, skills and training deprivation (decile)](#page-indicators-mhclg-iod25-education-decile)
- [Health deprivation and disability (score)](#page-indicators-mhclg-iod25-health-score)
- [Health deprivation and disability (decile)](#page-indicators-mhclg-iod25-health-decile)
- [Crime deprivation (score)](#page-indicators-mhclg-iod25-crime-score)
- [Crime deprivation (decile)](#page-indicators-mhclg-iod25-crime-decile)
- [Barriers to housing and services (score)](#page-indicators-mhclg-iod25-barriers-score)
- [Barriers to housing and services (decile)](#page-indicators-mhclg-iod25-barriers-decile)
- [Living environment deprivation (score)](#page-indicators-mhclg-iod25-living-env-score)
- [Living environment deprivation (decile)](#page-indicators-mhclg-iod25-living-env-decile)
- [Index of Multiple Deprivation: average score](#page-indicators-mhclg-iod25-imd-la-avg-score)
- [Index of Multiple Deprivation: average rank](#page-indicators-mhclg-iod25-imd-la-avg-rank)
- [Index of Multiple Deprivation: extent](#page-indicators-mhclg-iod25-imd-la-extent)
- [Index of Multiple Deprivation: local concentration](#page-indicators-mhclg-iod25-imd-la-local-concentration)
- [Neighbourhoods in England's most deprived 10%](#page-indicators-mhclg-iod25-imd-la-prop-most-deprived-10pct)
- [Income deprivation: average score](#page-indicators-mhclg-iod25-income-la-avg-score)
- [Income deprivation: neighbourhoods in England's most deprived 10%](#page-indicators-mhclg-iod25-income-la-prop-most-deprived-10pct)
- [Employment deprivation: average score](#page-indicators-mhclg-iod25-employment-la-avg-score)
- [Employment deprivation: neighbourhoods in England's most deprived 10%](#page-indicators-mhclg-iod25-employment-la-prop-most-deprived-10pct)
- [Education, skills and training deprivation: average score](#page-indicators-mhclg-iod25-education-la-avg-score)
- [Education, skills and training deprivation: neighbourhoods in England's most deprived 10%](#page-indicators-mhclg-iod25-education-la-prop-most-deprived-10pct)
- [Health deprivation and disability: average score](#page-indicators-mhclg-iod25-health-la-avg-score)
- [Health deprivation and disability: neighbourhoods in England's most deprived 10%](#page-indicators-mhclg-iod25-health-la-prop-most-deprived-10pct)
- [Crime (IoD domain): average score](#page-indicators-mhclg-iod25-crime-la-avg-score)
- [Crime (IoD domain): neighbourhoods in England's most deprived 10%](#page-indicators-mhclg-iod25-crime-la-prop-most-deprived-10pct)
- [Barriers to housing and services: average score](#page-indicators-mhclg-iod25-barriers-la-avg-score)
- [Barriers to housing and services: neighbourhoods in England's most deprived 10%](#page-indicators-mhclg-iod25-barriers-la-prop-most-deprived-10pct)
- [Living environment deprivation: average score](#page-indicators-mhclg-iod25-living-env-la-avg-score)
- [Living environment deprivation: neighbourhoods in England's most deprived 10%](#page-indicators-mhclg-iod25-living-env-la-prop-most-deprived-10pct)

**Child poverty**

- [Income deprivation affecting children (IDACI)](#page-indicators-mhclg-iod25-idaci-score)
- [Income deprivation affecting children (rank)](#page-indicators-mhclg-iod25-idaci-rank)
- [Income deprivation affecting children (decile)](#page-indicators-mhclg-iod25-idaci-decile)
- [Income deprivation affecting children: average score](#page-indicators-mhclg-iod25-idaci-la-avg-score)
- [Income deprivation affecting children: average rank](#page-indicators-mhclg-iod25-idaci-la-avg-rank)
- [Neighbourhoods in England's most deprived 10% for child income](#page-indicators-mhclg-iod25-idaci-la-prop-most-deprived-10pct)
- [Children in relative low income families](#page-indicators-dwp-cilif-relative-bhc)
- [Children in relative low income families (%)](#page-indicators-dwp-cilif-relative-bhc-pct)
- [Children in absolute low income families](#page-indicators-dwp-cilif-absolute-bhc)
- [Children in absolute low income families (%)](#page-indicators-dwp-cilif-absolute-bhc-pct)
- [Households with children on Universal Credit](#page-indicators-dwp-uc-households-with-children)
- [Pupils eligible for free school meals](#page-indicators-dfe-fsm-eligible-pupils)

**Education**

- [Children's education deprivation (score)](#page-indicators-mhclg-iod25-education-cyp-subdomain-score)
- [Care leavers not in education, employment or training](#page-indicators-dfe-care-leavers-19-21-neet)
- [Pupils with an EHC plan](#page-indicators-dfe-pupils-with-ehcp)
- [Pupils receiving SEN support](#page-indicators-dfe-pupils-sen-support)
- [Pupils with autism as their main need](#page-indicators-dfe-sen-primary-need-asd)
- [Persistent absence from school](#page-indicators-dfe-persistent-absence)
- [Severe absence from school](#page-indicators-dfe-severe-absence)
- [Suspensions from school](#page-indicators-dfe-suspensions)
- [Permanent exclusions from school](#page-indicators-dfe-permanent-exclusions)
- [16-17 year olds not in education, employment or training](#page-indicators-dfe-neet-16-17)
- [16-17 year olds NEET or activity not known](#page-indicators-dfe-neet-or-not-known-16-17)

**Family risk**

- [Lone-parent households](#page-indicators-census21-lone-parent-households-dep-children)
- [Young carers](#page-indicators-census21-unpaid-carers-5-24)
- [Domestic abuse identified at assessment](#page-indicators-dfe-cin-factor-domestic-abuse)
- [Parental mental health identified at assessment](#page-indicators-dfe-cin-factor-parental-mental-health)
- [Parental alcohol misuse identified at assessment](#page-indicators-dfe-cin-factor-parental-alcohol-misuse)
- [Parental drug misuse identified at assessment](#page-indicators-dfe-cin-factor-parental-drug-misuse)
- [Adults in drug/alcohol treatment living with children](#page-indicators-ohid-ndtms-adults-in-treatment-living-with-children)
- [Parents in drug/alcohol treatment not living with their children](#page-indicators-ohid-ndtms-parents-not-living-with-children)

**Housing**

- [Overcrowded households with children](#page-indicators-census21-overcrowded-households-dep-children)
- [Households with children in temporary accommodation](#page-indicators-mhclg-hclic-households-with-children-in-ta)
- [Children in temporary accommodation](#page-indicators-mhclg-hclic-children-in-ta)
- [Children in temporary accommodation](#page-indicators-mhclg-hclic-children-in-ta-by-age)
- [Families assessed as homeless or at risk](#page-indicators-mhclg-hclic-owed-duty-households-with-children)
- [Young people assessed as homeless or at risk (16-24)](#page-indicators-mhclg-hclic-owed-duty-applicants-16-24)

**Health**

- [Disabled children and young people](#page-indicators-census21-disabled-0-24)
- [Children receiving Disability Living Allowance](#page-indicators-dwp-dla-claimants-under16)
- [Young people receiving PIP](#page-indicators-dwp-pip-claimants-16-24)
- [Pupils with social, emotional and mental health needs](#page-indicators-dfe-sen-primary-need-semh)
- [Hospital admissions for self-harm (10-24)](#page-indicators-ohid-self-harm-admissions-10-24)
- [A&E attendances (under 5s)](#page-indicators-ohid-ae-attendances-0-4)
- [Infant mortality](#page-indicators-ohid-infant-mortality)
- [Under-18 conceptions](#page-indicators-ohid-under18-conceptions)
- [Low birth weight (full-term babies)](#page-indicators-ohid-low-birthweight-term)
- [Hospital admissions for injuries (0-14)](#page-indicators-ohid-injury-admissions-0-14)

**Safety**

- [Recorded crime](#page-indicators-police-crime-all-excl-asb)
- [Violence and sexual offences](#page-indicators-police-crime-violence-sexual)
- [Anti-social behaviour](#page-indicators-police-asb-incidents)
- [Possession of weapons](#page-indicators-police-crime-weapons-possession)
- [Drug offences](#page-indicators-police-crime-drugs)
- [First-time entrants to youth justice](#page-indicators-yjb-first-time-entrants-10-17)
- [Custodial sentences (10-17)](#page-indicators-yjb-custodial-sentences-10-17)
- [Proven offences by children (10-17)](#page-indicators-yjb-proven-offences-10-17)

**Service demand**

- [Children in need](#page-indicators-dfe-cin-at-31mar)
- [Referrals to children's social care](#page-indicators-dfe-cin-referrals)
- [Re-referrals within 12 months](#page-indicators-dfe-cin-rereferrals-12m)
- [Social care assessments](#page-indicators-dfe-cin-assessments-completed)
- [Children on child protection plans](#page-indicators-dfe-cpp-at-31mar)
- [New child protection plans](#page-indicators-dfe-cpp-starts)
- [Children in care](#page-indicators-dfe-cla-at-31mar)
- [Children entering care](#page-indicators-dfe-cla-starts)
- [Unaccompanied asylum-seeking children in care](#page-indicators-dfe-cla-uasc-at-31mar)
- [Care leavers aged 17 to 21](#page-indicators-dfe-care-leavers-17-21)
- [Care leavers aged 19 to 21](#page-indicators-dfe-care-leavers-19-21) (denominator)
- [Adoptions from care](#page-indicators-dfe-cla-ceased-adoption)
- [EHC plans (ages 0-25)](#page-indicators-dfe-ehcps-0-25)
- [New EHC plans](#page-indicators-dfe-ehcp-new-plans)
- [Child referrals for suspected exploitation (NRM)](#page-indicators-ho-nrm-referrals-under18)
- [Children supported by NHS mental health services](#page-indicators-nhse-mhsds-cyp-one-plus-contact-12m)
- [Children with open mental health referrals](#page-indicators-nhse-mhsds-cyp-open-referrals)

**Service pressure**

- [Children in care placed over 20 miles from home](#page-indicators-dfe-cla-placed-20mi-plus)
- [Children in care with 3+ placements in the year](#page-indicators-dfe-cla-3plus-placements)
- [Social worker vacancy rate](#page-indicators-dfe-sw-vacancy-rate)
- [Agency social worker rate](#page-indicators-dfe-sw-agency-rate)
- [Social worker turnover rate](#page-indicators-dfe-sw-turnover-rate)
- [Average social worker caseload](#page-indicators-dfe-sw-average-caseload)
- [Spending on children's services per child](#page-indicators-dfe-s251-cyp-services-net)
- [Spending on children in care per child](#page-indicators-dfe-s251-cla-net)
- [Spending on family support per child](#page-indicators-dfe-s251-family-support-net)
- [Spending on youth services per young person](#page-indicators-dfe-s251-young-people-services-net)
- [Ofsted judgement: children's services](#page-indicators-ofsted-ilacs-overall-effectiveness)
- [Children's homes](#page-indicators-ofsted-childrens-homes)
- [Children's home places](#page-indicators-ofsted-childrens-homes-places)
- [EHC plans issued on time](#page-indicators-dfe-ehcp-20wk-timeliness)

**Composite**

- [Neighbourhood need index](#page-indicators-l5-neighbourhood-need)
- [Neighbourhood need: economic hardship domain](#page-indicators-l5-neighbourhood-need-economic-hardship)
- [Neighbourhood need: health disability domain](#page-indicators-l5-neighbourhood-need-health-disability)
- [Neighbourhood need: family housing domain](#page-indicators-l5-neighbourhood-need-family-housing)
- [Neighbourhood need: safety domain](#page-indicators-l5-neighbourhood-need-safety)
- [LA need index](#page-indicators-l5-la-need)
- [LA need: economic hardship domain](#page-indicators-l5-la-need-economic-hardship)
- [LA need: family risk domain](#page-indicators-l5-la-need-family-risk)
- [LA need: health domain](#page-indicators-l5-la-need-health)
- [LA need: education domain](#page-indicators-l5-la-need-education)
- [LA need: housing domain](#page-indicators-l5-la-need-housing)
- [LA need: safety domain](#page-indicators-l5-la-need-safety)
- [LA system pressure: demand domain](#page-indicators-l5-la-system-pressure-demand)
- [LA system pressure: capacity domain](#page-indicators-l5-la-system-pressure-capacity)
- [LA system pressure: send domain](#page-indicators-l5-la-system-pressure-send)

### How to cite

> England Children and Young People Need and System Pressure Database, release
> `2dda583978fb-19eda0e60019`. Contains public sector information licensed under the Open
> Government Licence v3.0. Source attributions are listed in `sources.csv`.

### Applying the Code of Practice for Statistics (voluntarily)

- **Trustworthiness:** all code, configuration and decisions are versioned. Every release
  can be rebuilt from its raw inputs, and every judgement is in the decision log.
- **Quality:** source data is never altered. Suppression is preserved. Uncertainty and
  missing-data reasons are published with every value, and QA gates must pass before release.
- **Value:** measures are chosen for their relevance to children and young people, and are
  documented in plain English as well as technically.

### Feedback

We welcome methodological feedback, especially on the experimental composites. Contact
details for the publishing charity are added at release.

---

<a id="page-guide_plain_english"></a>

## A plain-English guide

Release `2dda583978fb-19eda0e60019`

### Areas

England is divided into children's services authorities: the councils responsible for
children's social care and education. Some of these are also responsible for housing;
others (county councils) contain several district councils. Below the councils, the
database uses neighbourhoods defined by the Office for National Statistics: middle-sized
areas (MSOAs, typically 5,000 to 15,000 people) and small areas (LSOAs, typically 1,000 to 3,000 people).

Some measures are only published for whole councils, and some only for areas such as police
forces or NHS areas. We never split a council's figure between its neighbourhoods. Where a
measure only exists for a bigger area, the map shows that bigger area's value, hatched and
labelled.

### Ages and dates

The database covers ages 0 to 24 (and up to 25 where a service runs to 25, such as
education, health and care plans). Each measure keeps the age range its publisher used.
The target date is 31 March 2025, but some sources are older or newer, for example the 2021
Census. Every value shows its own date.

### Why some measures change between levels

Some measures only exist at one level. For example, child poverty in a neighbourhood is
shown using the official Income Deprivation Affecting Children Index, while for a whole
council it is shown using the Children in Low Income Families statistics. They measure
related but different things, and the map tells you which one you are looking at.

### Grey and hatched areas

- **Grey**: no value. The legend says why: hidden to protect privacy, not published,
  incomplete, or not applicable.
- **Hatched**: the value belongs to a bigger area that contains this one.

### Comparing areas fairly

- Compare rates, not counts, unless you want to know about scale.
- Small areas have small numbers, and small numbers jump around. Look at the uncertainty
  range, and use the smoothed rate for small areas.
- Don't rank individual neighbourhoods into "worst area" lists. Look at patterns and at
  deciles (tenths of England).

### The composite indices

The experimental composite indices combine several measures into one score, in the same way as
the official Index of Multiple Deprivation. Need and pressure on services are never
combined. Each score comes with a range showing how much it depends on the choices made
in building it. They are experimental and not endorsed by any official publisher.

### Worked examples

#### Reading a rate: children looked after in Barnsley

In Barnsley, 366 children were looked after at 31 Mar 2025,
out of an estimated 51,799 children aged 0 to 17. That is
**70.7 per 10,000 children** (95% interval 63.8 to 78.2),
against 67.1 per 10,000 in England. The interval shows the range a rate like this
could take by chance alone; councils with fewer children have wider intervals.

#### A custom area: add up counts and denominators, then divide

South Yorkshire's 4 councils (Barnsley, Rotherham, Doncaster and Sheffield) together had
1,970 children looked after among 295,870 children:
**66.6 per 10,000**. Averaging the four councils' rates instead gives
69.5, which is wrong because it treats a small council the same as a large one.
Always add up the counts and the denominators first, then divide.

#### A hatched (fallback) value: child exploitation referrals in Kent

Child referrals to the National Referral Mechanism are only published for police force areas. Kent County
Council's area is inside the Kent police force area, which also covers Medway, so the
map shows the force area's rate, **14.2 per 10,000 children** (during 2024/25), hatched and
labelled. It is not Kent County Council's own figure, and it is never used in rankings or calculations.

#### Small numbers: raw and smoothed neighbourhood rates

Neighbourhood E01002882 has about 947 residents and
4 recorded weapons-possession offences in the year, a raw rate of 4.2 per 1,000
(England: 0.84). A count this small can change a lot from one year to the next by chance,
so the database also gives a smoothed rate that leans towards the England figure where the evidence is thin:
3.52 per 1,000.
Use smoothed rates for maps and hotspot analysis, and never rank individual neighbourhoods.

---

<a id="page-methodology_technical"></a>

## Technical methodology

Release `2dda583978fb-19eda0e60019`. Every parameter below is generated from the build
configuration.

### 1. Principles

Source data is never altered. Values flow one way through layers L0 (raw) → L1 (staged)
→ L2 (harmonised, observed only) → L3 (derived) → L4 (release). L5 composites read the snapshot's L2–L3 values read-only and never change L0–L4 (D-0086).
Observed and modelled values never share a table. Counts move between geographies,
never rates. A value is never distributed from an area to the areas it contains. Published figures take precedence
over aggregated ones. Suppression is preserved and nothing is imputed.

### 2. Geography

The hierarchy is LSOA21 → MSOA21 → LAD (April 2025) → UTLA (April 2025) → England.
Nesting is proven in two ways. First, every Output Area in an LSOA or MSOA must map to the same
LAD. Second, each LSOA and MSOA polygon must lie at least 99.9% by area inside its LAD,
using full-resolution (BFC) boundaries. Generalised boundaries are used for display only.

Other geographies (Sub-ICB, ICB, youth justice services, police force areas, wards) are
related to the hierarchy as `coterminous` (relabelled), `nests_within` (summed),
`contains` (no conversion; shown as a labelled fallback) or `overlaps` (apportioned in L3
on the matching age-band population, using GP-registered population for health data, and
flagged unsuitable for spatial analysis).

### 3. Sources and disclosure control

Each source's statistical disclosure control (SDC) determines how closely sums of its cells
can be expected to match its published totals. The profile below is taken from each publisher's own
data guidance, read when the file was inspected, and confirmed against the published totals where
these exist. A sum is "within tolerance" when |sum − published| ≤ absolute tolerance + relative
tolerance × published. Tolerances were fixed before the comparison and not tuned to it (except DWP
Stat-Xplore, F2–F4, set from observed differences in Phase 2). A difference outside tolerance is
reported, never corrected: the published figure is always the value used.

| Source | Publisher | SDC methods | Additivity | Tolerance (abs / rel) | Confirmed | Publisher's disclosure control and checks | Checked in this release |
|---|---|---|---|---|---|---|---|
| G1 | Office for National Statistics | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| G2 | Office for National Statistics | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| G3 | Office for National Statistics | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| G3b | NHS England | none | approximate | 0 / 0.005 | yes | NHS England GP registrations: counts by practice x LSOA21 and sex, no suppression or rounding symbols (inspection, Phase 4); female + male sum exactly to every published total. Patients of unknown sex are excluded by the publisher. Used only as weights and Sub-ICB denominators. | no published total compared |
| G4 | Office for National Statistics | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| G5 | Office for National Statistics | none | none | 0 / 0 | yes | Geometry; no statistical values. | no published total compared |
| G6 | Office for National Statistics | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| G7 | Youth Justice Board (list of services); composition constructed by this project | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| G8 | Office for National Statistics | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| G9 | Office for National Statistics | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| G10 | House of Commons Library | none | none | 0 / 0 | yes | Lookup; no statistical values. | no published total compared |
| P1 | Office for National Statistics | none | exact | 0 / 0 | yes | ONS small area population estimates are constrained to MSOA and local authority mid-year estimates (ONS SAPE quality and methodology information, https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/smallareapopulationestimatesqmi). Checked: LSOA single-year sums equal the published MSOA estimates exactly. | 1,254,648 published totals compared; 1,254,648 within tolerance; largest difference 0 |
| P1b | Office for National Statistics | none | exact | 0 / 0 | yes | Published LA mid-year estimates. Checked: LAD sums equal the published UTLA and England figures exactly in every age and sex cell. | 82,350 published totals compared; 82,350 within tolerance; largest difference 0 |
| P4 | Office for National Statistics | record_swapping, cell_key | approximate | 10 / 0.01 | yes | Census 2021: targeted record swapping and cell key perturbation (ONS, 'Protecting personal data in Census 2021 results', https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/protectingpersonaldataincensus2021results). Small cells are perturbed, so sums of cells differ slightly from published totals; differences are reported in reconciliation.csv. | 313,110 published totals compared; 313,092 within tolerance; largest difference 55 |
| P7 | Department for Education | none | approximate | 0 / 0.001 | yes | School census (SPC) data guidance: no suppression or rounding applied; 'x' not applicable, 'z' unknown. Checked: LA sums equal the published England figures exactly. | 20 published totals compared; 20 within tolerance; largest difference 0 |
| D1 | Ministry of Housing, Communities and Local Government | none | none | 0 / 0 | yes | Index values (scores, ranks, deciles): not additive; no disclosure control. | no published total compared |
| D1b | Ministry of Housing, Communities and Local Government | none | none | 0 / 0 | yes | MHCLG published LA summaries: not additive. Checked: recomputed LAD averages match the published values within published rounding (gate 13). | no published total compared |
| F1 | Department for Work and Pensions | cell_key | approximate | 10 / 0.01 | yes | CiLIF data guidance: DWP applies disclosure control, and totals may not sum because of rounding and disclosure control; percentages rounded to 1 decimal place; no symbols. Checked: LA sums within tolerance of the published England totals. | 10 published totals compared; 10 within tolerance; largest difference 43 |
| F2 | Department for Work and Pensions | cell_key, suppression | approximate | 15 / 0.03 | yes | Stat-Xplore adds small random adjustments to every cell and publishes counts below 5 as 0 (D-0053). DWP: no reliance on small cells; use published data for larger areas (Stat-Xplore Data Confidentiality note). Observed: complete LSOA sums differ from published figures by about 5 x sqrt(areas summed) at the 99th percentile; 15 + 3% covers this. | 7,144 published totals compared; 7,144 within tolerance; largest difference 88 |
| F3 | Department for Work and Pensions | cell_key, suppression | approximate | 15 / 0.03 | yes | Stat-Xplore adds small random adjustments to every cell and publishes counts below 5 as 0 (D-0053). DWP: no reliance on small cells; use published data for larger areas (Stat-Xplore Data Confidentiality note). Observed: complete LSOA sums differ from published figures by about 5 x sqrt(areas summed) at the 99th percentile; 15 + 3% covers this. | 14,623 published totals compared; 14,617 within tolerance; largest difference 58 |
| F4 | Department for Work and Pensions | cell_key, suppression | approximate | 15 / 0.03 | yes | Stat-Xplore adds small random adjustments to every cell and publishes counts below 5 as 0 (D-0053). DWP: no reliance on small cells; use published data for larger areas (Stat-Xplore Data Confidentiality note). Observed: complete LSOA sums differ from published figures by about 5 x sqrt(areas summed) at the 99th percentile; 15 + 3% covers this. | 8,752 published totals compared; 8,750 within tolerance; largest difference 40 |
| F6 | Office for National Statistics | record_swapping, cell_key | approximate | 10 / 0.01 | yes | Census 2021: targeted record swapping and cell key perturbation (ONS, 'Protecting personal data in Census 2021 results', https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/protectingpersonaldataincensus2021results). Small cells are perturbed, so sums of cells differ slightly from published totals; differences are reported in reconciliation.csv. | 21,918 published totals compared; 21,907 within tolerance; largest difference 129 |
| F7 | Office for National Statistics | record_swapping, cell_key | approximate | 10 / 0.01 | yes | Census 2021: targeted record swapping and cell key perturbation (ONS, 'Protecting personal data in Census 2021 results', https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/protectingpersonaldataincensus2021results). Small cells are perturbed, so sums of cells differ slightly from published totals; differences are reported in reconciliation.csv. | 27,550 published totals compared; 27,529 within tolerance; largest difference 135 |
| C1 | Department for Education | suppression, rounding | approximate | 0 / 0.005 | yes | CIN data guidance: 'c' suppression (secondary suppression may apply); England and regional totals rounded to the nearest 10, LA figures unrounded. Checked: LA sums within 5 of the rounded England totals. | 6 published totals compared; 6 within tolerance; largest difference 5 |
| C2 | Department for Education | suppression, rounding | approximate | 0 / 0.005 | yes | CLA data guidance: 'c' suppression; national and regional figures rounded to the nearest 10, LA figures unrounded. Checked: LA sums within tolerance of the rounded England totals. | 1 published totals compared; 1 within tolerance; largest difference 4 |
| C3 | Department for Education | suppression, rounding | approximate | 1 / 0.005 | yes | Children's social work workforce data guidance: 'c' suppression, 'low' rounds to 0; FTEs, rates and caseloads rounded to one decimal place. | no published total compared |
| C4 | Department for Education | suppression | approximate | 1000 / 0.001 | yes | Section 251 outturn: unrounded GBP; 'c' (confidential) and 'x' (not available) take the GSS meanings. No published total is reconciled. | no published total compared |
| C5 | Ofsted | none | exact | 0 / 0 | yes | Ofsted provider list: every registered provider at 31 March 2025, no symbols. Checked: LA sums equal Ofsted's published national homes and places exactly. | no published total compared |
| E1 | Department for Education | none | approximate | 0 / 0.001 | yes | SEN data guidance: no suppression or rounding applied; release convention 'x' not applicable, 'z' not available. Checked: LA sums equal the published England figures exactly. | 5 published totals compared; 5 within tolerance; largest difference 0 |
| E2 | Department for Education | none | approximate | 0 / 0.001 | yes | SEN2 data guidance: no suppression; 'z' not applicable, 'x' unavailable (Lewisham 2024 timeliness withheld by DfE). Checked: LA sums equal the published England figures exactly. | 8 published totals compared; 8 within tolerance; largest difference 0 |
| E3 | Department for Education | none | approximate | 0 / 0.001 | yes | Absence data guidance: no suppression or rounding applied (except PLAA tables, not used). Checked: LA sums equal the published England figures exactly. | 3 published totals compared; 3 within tolerance; largest difference 0 |
| E4 | Department for Education | none | approximate | 0 / 0.001 | yes | Exclusions data guidance: no suppression or rounding applied (except PLAA tables, not used). Checked: LA sums equal the published England figures exactly. | 3 published totals compared; 3 within tolerance; largest difference 0 |
| E5 | Department for Education | suppression, rounding | approximate | 10 / 0.005 | yes | NEET data guidance: indicators on a cohort of 5 or fewer suppressed ('c'); national and regional numbers rounded to the nearest 10. | no published total compared |
| E6 | Department for Education | none | approximate | 0 / 0.001 | yes | School census (SPC) data guidance: no suppression or rounding applied; 'x' not applicable, 'z' unknown. Checked: LA sums equal the published England figures exactly. | 2 published totals compared; 2 within tolerance; largest difference 0 |
| H1 | NHS England | rounding, suppression (base 5) | approximate | 5 / 0.01 | yes | MHSDS: '*' marks a suppressed small value; Sub-ICB and provider figures rounded to the nearest 5, England unrounded. | no published total compared |
| H2 | Office for Health Improvement and Disparities | suppression | approximate | 0 / 0.001 | yes | Fingertips: no symbols; a missing value carries a 'Value note' (suppressed small count, combined area, not presented), mapped to null_reason. | no published total compared |
| H3 | Office for Health Improvement and Disparities | suppression, rounding | approximate | 5 / 0.01 | no | Not loaded (D-0091): disclosure control not assessed. | no published total compared |
| Ho1 | Ministry of Housing, Communities and Local Government | suppression, imputation | approximate | 0 / 0.05 | yes | H-CLIC table footnotes: '..' authority did not submit; '-' breakdown suppressed (fewer than 5); England and regional totals include MHCLG estimates for non-responding authorities, so LA sums fall short of them. | no published total compared |
| S1 | Home Office / police forces (data.police.uk) | location_anonymisation | exact | 0 / 0 | yes | data.police.uk: record-level counts with no suppression; points are snapped to anonymous map points, which affects location, not counts. Checked: published LSOA code agrees with point-in-polygon for 96.5% of England records (T4). | no published total compared |
| S3 | Youth Justice Board / Ministry of Justice | suppression | approximate | 0 / 0.005 | yes | YJB/MoJ supplementary tables: '..' fewer than ten first-time entrants (suppressed); '*' LA boundary change. Open data tables have no symbols. | no published total compared |
| S4 | Home Office | none | approximate | 0 / 0.01 | yes | NRM quarterly tables: whole numbers, no symbols. Checked: police force rows sum to the published UK total in every quarter. | no published total compared |
| S5 | Home Office | none | approximate | 0 / 0.01 | yes | Asy_D11: counts of people, no symbols. Checked: England LA rows sum to the published English regional totals exactly (D-0084). | no published total compared |

### 4. Suppression and missing values

Suppressed cells are stored as NULL with the publisher's symbol kept in `source_code`.
An aggregate with any suppressed or missing component is NULL, with lower and upper
bounds from the maximum value each symbol can hide, and with counts of components and
suppressed components.

| Symbol | Meaning | null_reason |
|---|---|---|
| `c` | Confidential / suppressed to protect individuals | suppressed |
| `[c]` | Confidential / suppressed to protect individuals | suppressed |
| `x` | Not available | not_published |
| `[x]` | Not available | not_published |
| `z` | Not applicable | not_applicable |
| `[z]` | Not applicable | not_applicable |
| `u` | Low reliability (value withheld) | suppressed |
| `[u]` | Low reliability (value withheld) | suppressed |
| `k` | Rounds to zero but is not zero | suppressed |
| `low` | Rounds to zero but is not zero | suppressed |
| `[low]` | Rounds to zero but is not zero | suppressed |
| `*` | Suppressed (small number) | suppressed |
| `..` | Not available / suppressed (confirm per source) | suppressed |
| `-` | Nil or not applicable (confirm per source; NEVER read as zero without confirmation) | not_applicable |
| `<5` | Fewer than 5 | suppressed |

### 5. Age bands

Population is held by single year of age, so a denominator can be built exactly for any
source band. Source bands are never split or trimmed.

| Code | Label | Min | Max | Standard | Total |
|---|---|---|---|---|---|
| `0_4` | Ages 0–4 | 0 | 4 | yes | no |
| `5_10` | Ages 5–10 | 5 | 10 | yes | no |
| `11_15` | Ages 11–15 | 11 | 15 | yes | no |
| `16_17` | Ages 16–17 | 16 | 17 | yes | no |
| `18_20` | Ages 18–20 | 18 | 20 | yes | no |
| `21_24` | Ages 21–24 | 21 | 24 | yes | no |
| `0_17` | Ages 0–17 (children) | 0 | 17 | yes | yes |
| `0_24` | Ages 0–24 | 0 | 24 | yes | yes |
| `0_25` | Ages 0–25 | 0 | 25 | yes | yes |
| `all_ages` | All ages | — | — | yes | yes |
| `na` | Not age-specific | — | — | yes | no |
| `src_infant` | Under 1 (infants) | 0 | 0 | no | no |
| `src_0_14` | Ages 0–14 | 0 | 14 | no | no |
| `src_0_15` | Ages 0–15 | 0 | 15 | no | no |
| `src_0_19` | Ages 0–19 (dependent children) | 0 | 19 | no | no |
| `src_5_24` | Ages 5–24 | 5 | 24 | no | no |
| `src_10_17` | Ages 10–17 | 10 | 17 | no | no |
| `src_10_24` | Ages 10–24 | 10 | 24 | no | no |
| `src_13_19` | Ages 13–19 | 13 | 19 | no | no |
| `src_15_17` | Ages 15–17 | 15 | 17 | no | no |
| `src_16_19` | Ages 16–19 (dependent children) | 16 | 19 | no | no |
| `src_16_24` | Ages 16–24 | 16 | 24 | no | no |
| `src_17_21` | Ages 17–21 | 17 | 21 | no | no |
| `src_19_21` | Ages 19–21 | 19 | 21 | no | no |
| `src_5_15` | Ages 5–15 | 5 | 15 | no | no |
| `src_20_24` | Ages 20–24 | 20 | 24 | no | no |
| `src_25_29` | Ages 25–29 | 25 | 29 | no | no |
| `src_25_49` | Ages 25–49 | 25 | 49 | no | no |
| `src_30_plus` | Ages 30 and over | 30 | — | no | no |
| `src_50_plus` | Ages 50 and over | 50 | — | no | no |
| `src_1_4` | Ages 1–4 | 1 | 4 | no | no |
| `src_5_9` | Ages 5–9 | 5 | 9 | no | no |
| `src_10_15` | Ages 10–15 | 10 | 15 | no | no |
| `src_pupils_all` | All pupils (school census) | — | — | no | no |

### 6. Rates, denominators and confidence intervals

A rate is the numerator divided by the denominator, multiplied by the indicator's
multiplier. The denominator must match the numerator's area, age band, sex and ethnicity
classification. Stock measures use the population estimate closest to the reference date,
and flow measures use the mid-period population. The denominator date must be within
`max_denominator_gap_days` of the numerator period (default 366 days).

Confidence intervals:

- **Wilson score**: person-based proportions and prevalences.
- **Byar's approximation to the exact Poisson**: event counts that can repeat (OHID/PHE
  methods).
- **Published**: the publisher's own interval.
- **None**: model-based, survey-calibrated and index values, and published rates without intervals.

For full administrative counts, an interval reflects random variation in the underlying
process, not sampling error.

A rate is flagged `low_reliability` when its numerator is below the indicator's threshold
(default 10) or its denominator is below its
threshold (default 50).

### 7. Small-area smoothing

Rates for small areas are also given as empirical Bayes estimates (Marshall's global
method, shrinking toward the England rate). Smoothed rates never replace the crude rate.
Where the resident population is known to misrepresent exposure (for example crime in town
centres), the rate is flagged `low_validity_denominator`.

### 8. Comparability

Each indicator is given an England percentile (0–100, ties averaged, missing values excluded) and a
z-score, calculated separately at each level from native and L2 values only. Fallback rows are
excluded. Polarity is recorded as metadata, and signs are never flipped.

### 9. Indices of Deprivation

Published IoD 2025 LSOA values and the published LA summary measures are loaded as observed values.
For MSOAs and custom regions, MHCLG's method is used: the population-weighted average score and
the share of population in the most deprived national decile. The method is validated by
recomputing the published LAD averages. Ranks and deciles are never averaged.

### 10. Limitations

- **Period mismatches:** sources range from Census 2021 to 2025. Each value carries its own period.
- **Ecological fallacy:** area values describe areas, not individuals.
- **Modifiable areal unit problem:** patterns can change with the choice of boundaries.
- **Practice effects:** service measures reflect local thresholds and recording practice.
- **Interval coverage:** confidence intervals describe random variation only; they do not cover bias from
  recording practice, coverage gaps, survey calibration or the period mismatch between numerator and
  denominator.
- **Point in time:** this is one snapshot (reference date 31 March 2025), not a time series; differences
  between areas are not trends.
- **Small numbers:** use the intervals and smoothed rates.

Full references for every method are in [References](#page-references).

### 11. Indicator catalogue

154 indicators are catalogued. Each has its own page, listed in the [index](#page-index).

---

<a id="page-composites-methodology_composite"></a>

## Composite indices: methodology (experimental)

Release `2dda583978fb-19eda0e60019` · composites version `0.1-experimental`

> **Experimental.** These indices are not endorsed by any official publisher. We welcome
> methodological feedback.

### Framework

There are two families of index, and they are **never combined**:

- **Need**: the underlying circumstances of children, young people and families.
- **System pressure**: demand on services and their capacity. Service activity partly
  reflects local thresholds and practice. Keeping it separate from need avoids circularity,
  and lets the two be compared.

The construction follows MHCLG's Indices of Deprivation method (McLennan, Noble et al., 2025) and the
OECD/JRC *Handbook on Constructing Composite Indicators* (2008); the uncertainty and sensitivity analysis
follows Saisana, Saltelli and Tarantola (2005). Full citations are in [References](#page-references).

### Eligibility

An indicator enters a composite only if it is native to the composite's level (an observed value,
or a rate built from observed counts), it covers at least 95.0% of areas, and its
polarity is higher-is-worse or higher-is-better (neutral indicators cannot be aligned). Apportioned,
converted, recoded and fallback values are never used. At LSOA and MSOA level, rates are
eb smoothed (Marshall global empirical Bayes), so small numbers do not drive the
result. Eligibility is tested at every level for every release, so an indicator can be eligible at MSOA but
not at LSOA. Survey-calibrated inputs (child poverty) are allowed and flagged.

### Primary method

1. **Checks within each domain.** Spearman correlations. A pair with |ρ| > 0.9 is
   redundant (one is kept, with the reason recorded; pairs kept on purpose are listed below). An indicator with ρ < 0.2 against its
   domain is reviewed. Cronbach's alpha and the first principal component's variance share are reported.
2. **Normalisation.** Polarity is aligned so that higher means more need or pressure. Values are ranked within
   England and converted to normal scores (rank inverse normal).
3. **Within a domain.** equal weight mean of the normal scores. Exceptions:
   `dfe_cin_factor_parental_alcohol_misuse` has weight 0.5,    `dfe_cin_factor_parental_drug_misuse` has weight 0.5.4. **Domain transformation.** IoD exponential transformation:
   `X = −23 × ln(1 − R × (1 − exp(−100/23)))`, where R is the
   rank scaled to (0, 1] and 1 is the highest need. This limits how far low need in one domain can offset high need in another.
5. **Combining domains.** Equal domain weights. No stakeholder weighting exercise
   was available, and equal weights are the most transparent default. Correlated domains
   carry extra weight implicitly.
6. **Missing data.** Nothing is imputed. At LSOA and MSOA level a domain is scored when any of its indicators is
   present. At LA level a domain needs at least 66.7% of its indicators
   (by weight). Every composite needs every domain; otherwise it is NULL with `null_reason = 'incomplete'`.
7. **Ranks and deciles.** As in the IoD, rank 1 is the area with the most need (or pressure) in England,
   and decile 1 is the 10% of areas with the most.

Redundant pairs kept on purpose:
- `dfe_cin_factor_parental_alcohol_misuse` and `dfe_cin_factor_parental_drug_misuse`: One factor (parental substance misuse) published as two series; each has weight 0.5, so together they count once (D-0056, D-0087).

### Uncertainty

A seeded Monte Carlo with 1000 runs (seed 20250331). Each run varies:

- domain weights: dirichlet draws centred on equal weights, each weight with a
  coefficient of variation of 0.25,
- normalisation: rank_inverse_normal, z_score, min_max,
- domain aggregation: iod_exponential, arithmetic_mean, geometric_mean,
- missing-data threshold (LA composites): 0.5, 0.6667, 0.75,
- inclusion: all indicators, drop one indicator, drop practice sensitive.

For each area we report the median rank, the 5th–95th percentile rank interval, the probability
of being in the highest-need decile, and whether its decile is robust (the same decile in at
least 80% of runs). The share of rank variance explained by each
choice is estimated with first-order Sobol' indices; for the weights, which are a vector, a lower and an
upper bound are given. Per-run settings are in `l5_runs`, and results per choice in `l5_sensitivity`.

**Reading the uncertainty.** Where an area's 5th–95th percentile rank interval spans more than two deciles,
show its decile with the interval, not an exact rank.

Practice-sensitive indicators tested by exclusion:
- [EHC plans (ages 0-25)](#page-indicators-dfe-ehcps-0-25)
- [Pupils with an EHC plan](#page-indicators-dfe-pupils-with-ehcp)
- [A&E attendances (under 5s)](#page-indicators-ohid-ae-attendances-0-4)
- [Domestic abuse identified at assessment](#page-indicators-dfe-cin-factor-domestic-abuse)
- [Parental mental health identified at assessment](#page-indicators-dfe-cin-factor-parental-mental-health)
- [Parental alcohol misuse identified at assessment](#page-indicators-dfe-cin-factor-parental-alcohol-misuse)
- [Parental drug misuse identified at assessment](#page-indicators-dfe-cin-factor-parental-drug-misuse)

### Validation

Convergent validity (against IMD and IDACI 2025), criterion validity (LA need against system pressure,
with residuals published), stability (dropping each indicator in turn) and face validity.

- **Neighbourhood need** (small area): 33,723 of 33,755 areas scored; robust decile for 19.9% of areas over all runs and 42.1% over runs with the primary aggregation; within one decile for 91.3%.
- **Neighbourhood need** (intermediate area): 6,856 of 6,856 areas scored; robust decile for 27.1% of areas over all runs and 56.1% over runs with the primary aggregation; within one decile for 92.0%.
- **LA need** (service area): 149 of 153 areas scored; robust decile for 10.7% of areas over all runs and 26.2% over runs with the primary aggregation; within one decile for 70.5%.
- **LA system pressure** (service area): 144 of 153 areas scored; robust decile for 10.4% of areas over all runs and 13.9% over runs with the primary aggregation; within one decile for 52.8%. **Index not published: domains only (D-0090).**

Spearman ρ between LA need and LA system pressure: 0.297 (142 areas). The two are never combined. The pressure score here is the combined index, computed internally; only its domains are published (D-0090).

Each composite's page has its full results; the whole report is `l5/l5_validation.md` in the release.

### Composites

- [Neighbourhood need](#page-composites-neighbourhood_need) (need; small_area, intermediate_area)
- [LA need](#page-composites-la_need) (need; service_area)
- [LA system pressure](#page-composites-la_system_pressure) (pressure; service_area)

### Limitations

The inputs come from different periods. The neighbourhood need index overlaps with IMD by design,
because IDACI is built from benefits data, so it is reported alongside IMD rather than instead of it. A
sub-LA composite can only use indicators that exist below LA level.

---

[Methodology index](#page-index)

---

<a id="page-composites-la_need"></a>

## LA need (experimental)

Release `2dda583978fb-19eda0e60019` · composites version `0.1-experimental` · family **need**
· levels service_area

> **Experimental.** Not endorsed by any official publisher. See the
> [composite methodology](#page-composites-methodology_composite).

### Domains and indicators

#### Economic hardship

- [Children in relative low income families (%)](#page-indicators-dwp-cilif-relative-bhc-pct) (Financial year ending March 2025)
- [Pupils eligible for free school meals](#page-indicators-dfe-fsm-eligible-pupils) (January 2025)
- [Income deprivation affecting children: average score](#page-indicators-mhclg-iod25-idaci-la-avg-score) (IoD 2025)
#### Family risk

- [Lone-parent households](#page-indicators-census21-lone-parent-households-dep-children) (Census Day, 21 March 2021)
- [Domestic abuse identified at assessment](#page-indicators-dfe-cin-factor-domestic-abuse) (1 April 2024 to 31 March 2025): *practice-sensitive*
- [Parental mental health identified at assessment](#page-indicators-dfe-cin-factor-parental-mental-health) (1 April 2024 to 31 March 2025): *practice-sensitive*
- [Parental alcohol misuse identified at assessment](#page-indicators-dfe-cin-factor-parental-alcohol-misuse) (1 April 2024 to 31 March 2025): *practice-sensitive*
- [Parental drug misuse identified at assessment](#page-indicators-dfe-cin-factor-parental-drug-misuse) (1 April 2024 to 31 March 2025): *practice-sensitive*
#### Health

- [Hospital admissions for self-harm (10-24)](#page-indicators-ohid-self-harm-admissions-10-24) (Latest year ending on or before 31 March 2025)
- [Hospital admissions for injuries (0-14)](#page-indicators-ohid-injury-admissions-0-14) (Latest year ending on or before 31 March 2025)
- [Disabled children and young people](#page-indicators-census21-disabled-0-24) (Census Day, 21 March 2021)
#### Education

- [Persistent absence from school](#page-indicators-dfe-persistent-absence) (Academic year 2024/25)
- [Suspensions from school](#page-indicators-dfe-suspensions) (Academic year 2024/25 (check))
- [16-17 year olds NEET or activity not known](#page-indicators-dfe-neet-or-not-known-16-17) (End 2024 (Dec 2024 - Feb 2025 average))
#### Housing

- [Children in temporary accommodation](#page-indicators-mhclg-hclic-children-in-ta-by-age) (At 31 March 2025)
- [Overcrowded households with children](#page-indicators-census21-overcrowded-households-dep-children) (Census Day, 21 March 2021)
#### Safety

- [First-time entrants to youth justice](#page-indicators-yjb-first-time-entrants-10-17) (Year ending 31 December 2024)
- [Violence and sexual offences](#page-indicators-police-crime-violence-sexual) (1 April 2024 to 31 March 2025)

### Notes

Census and police inputs enter at service_area as aggregated L2 counts (exact nesting), never apportioned.

### Results

#### LA need: service area

149 of 153 areas have a score.

Areas without a score are `incomplete` because a domain could not be scored:

- family_risk: City of London
- health: Rutland, Isles of Scilly, City of London
- safety: Rutland, Telford and Wrekin, Isles of Scilly, City of London

**Indicators not eligible at this level:**

- `mhclg_hclic_children_in_ta_by_age`: coverage 92.8% < 95%

**Domain checks** (Spearman ρ between indicators; Cronbach's α; first component):

| Domain | Indicators | α | PC1 share | Weakest fit with rest |
|---|---|---|---|---|
| economic_hardship | 3 | 0.92 | 0.86 | dwp_cilif_relative_bhc_pct (+0.79) |
| family_risk | 5 | 0.85 | 0.69 | census21_lone_parent_households_dep_children (+0.17) |
| health | 3 | 0.79 | 0.70 | ohid_injury_admissions_0_14 (+0.57) |
| education | 3 | 0.70 | 0.62 | dfe_persistent_absence (+0.49) |
| housing | 1 | – | – | – |
| safety | 2 | 0.44 | 0.64 | yjb_first_time_entrants_10_17 (+0.31) |

Redundant pairs kept on purpose: dfe_cin_factor_parental_alcohol_misuse ~ dfe_cin_factor_parental_drug_misuse (ρ 0.92): kept on purpose

**Convergent validity:**

| Measure | Spearman ρ | Areas |
|---|---|---|
| Index of Multiple Deprivation: average score | 0.846 | 149 |
| Income deprivation affecting children: average score | 0.775 | 149 |

**Stability** (primary method, each indicator dropped in turn):

| Indicator dropped | Median |rank change| | Largest |rank change| | Areas changing decile |
|---|---|---|---|
| dwp_cilif_relative_bhc_pct | 2 | 17 | 15 of 149 |
| dfe_fsm_eligible_pupils | 1 | 11 | 22 of 149 |
| mhclg_iod25_idaci_la_avg_score | 1 | 13 | 18 of 149 |
| census21_lone_parent_households_dep_children | 2 | 25 | 35 of 149 |
| dfe_cin_factor_domestic_abuse | 2 | 15 | 22 of 149 |
| dfe_cin_factor_parental_mental_health | 1 | 14 | 24 of 149 |
| dfe_cin_factor_parental_alcohol_misuse | 1 | 6 | 12 of 149 |
| dfe_cin_factor_parental_drug_misuse | 1 | 6 | 10 of 149 |
| ohid_self_harm_admissions_10_24 | 2 | 23 | 26 of 149 |
| ohid_injury_admissions_0_14 | 2 | 14 | 34 of 149 |
| census21_disabled_0_24 | 2 | 22 | 29 of 149 |
| dfe_persistent_absence | 2 | 21 | 34 of 149 |
| dfe_suspensions | 2 | 22 | 36 of 149 |
| dfe_neet_or_not_known_16_17 | 2 | 26 | 32 of 149 |
| census21_overcrowded_households_dep_children | – | – | not droppable (only indicator in its domain) |
| yjb_first_time_entrants_10_17 | 4 | 22 | 51 of 149 |
| police_crime_violence_sexual | 4 | 30 | 45 of 149 |

**Face validity:** highest and lowest ranked areas:

| Rank | Area | Score |
|---|---|---|
| 1 | Blackpool | 67.06 |
| 2 | Middlesbrough | 54.48 |
| 3 | Newcastle upon Tyne | 49.41 |
| 4 | Knowsley | 46.80 |
| 5 | Birmingham | 45.50 |
| 6 | Torbay | 44.01 |
| 7 | Hartlepool | 43.16 |
| 8 | Northumberland | 42.62 |
| 9 | Kingston upon Hull, City of | 42.45 |
| 10 | Liverpool | 41.99 |
| 140 | Kingston upon Thames | 6.58 |
| 141 | Leicestershire | 6.55 |
| 142 | Central Bedfordshire | 6.32 |
| 143 | Bracknell Forest | 6.19 |
| 144 | Bromley | 6.04 |
| 145 | West Berkshire | 5.38 |
| 146 | Windsor and Maidenhead | 5.27 |
| 147 | Richmond upon Thames | 4.89 |
| 148 | Trafford | 4.08 |
| 149 | Wokingham | 1.64 |

**Criterion validity** (LA need against children's services rates):

| Pressure measure | Spearman ρ with need | Slope (per need score point) | Areas |
|---|---|---|---|
| Children in need | 0.625 | 5.005 | 149 |
| Children in care | 0.688 | 1.762 | 149 |
| Children on child protection plans | 0.496 | 0.751 | 149 |

Largest differences between children in need and what need predicts (standardised residuals):

| Area | Observed rate | Predicted | Standardised residual |
|---|---|---|---|
| Leicester | 232.4 | 411.0 | -2.64 |
| Hartlepool | 635.8 | 463.6 | +2.55 |
| Tameside | 553.1 | 385.8 | +2.48 |
| Croydon | 493.6 | 330.9 | +2.41 |
| Birmingham | 317.6 | 475.3 | -2.33 |
| Herefordshire, County of | 457.0 | 301.8 | +2.30 |
| Essex | 178.1 | 309.4 | -1.94 |
| Redcar and Cleveland | 582.2 | 452.4 | +1.92 |
| Reading | 444.5 | 317.7 | +1.88 |
| Lewisham | 479.1 | 357.4 | +1.80 |

**Uncertainty:** share of rank variance explained by each choice (first-order):

| Choice | First-order share |
|---|---|
| normalisation | 0.028 |
| aggregation | 0.440 |
| missing_threshold | 0.002 |
| inclusion | 0.179 |
| weights | 0.082 to 0.276 |

Areas with a robust decile (same decile in at least 80% of runs): 10.7% over all runs; 26.2% over the 366 runs that use the primary aggregation (IoD exponential transformation). Areas whose decile stays within one decile in at least 80% of runs: 70.5%.

**Domain stability** (share of areas):

| Domain | Same decile (robust) | Within one decile |
|---|---|---|
| economic_hardship | 90.2% | 100.0% |
| family_risk | 15.8% | 43.4% |
| health | 80.0% | 100.0% |
| education | 68.0% | 98.7% |
| housing (one indicator: stable by construction) | 100.0% | 100.0% |
| safety | 43.6% | 94.6% |


---

[Methodology index](#page-index)

---

<a id="page-composites-la_system_pressure"></a>

## LA system pressure (experimental)

Release `2dda583978fb-19eda0e60019` · composites version `0.1-experimental` · family **pressure**
· levels service_area

> **Experimental.** Not endorsed by any official publisher. See the
> [composite methodology](#page-composites-methodology_composite).

> **Published as domain scores only.** The combined index is computed to document how robust it
> is, but it is not published: its deciles are not stable enough to use (see Results).

### Domains and indicators

#### Demand

- [Children in need](#page-indicators-dfe-cin-at-31mar) (At 31 March 2025)
- [Children on child protection plans](#page-indicators-dfe-cpp-at-31mar) (At 31 March 2025)
- [Children in care](#page-indicators-dfe-cla-at-31mar) (At 31 March 2025)
- [Re-referrals within 12 months](#page-indicators-dfe-cin-rereferrals-12m) (1 April 2024 to 31 March 2025)
- [Child referrals for suspected exploitation (NRM)](#page-indicators-ho-nrm-referrals-under18) (1 April 2024 to 31 March 2025)
#### Capacity

- [Social worker vacancy rate](#page-indicators-dfe-sw-vacancy-rate) (At 30 September 2024)
- [Agency social worker rate](#page-indicators-dfe-sw-agency-rate) (At 30 September 2024)
- [Social worker turnover rate](#page-indicators-dfe-sw-turnover-rate) (Year to 30 September 2024)
- [Average social worker caseload](#page-indicators-dfe-sw-average-caseload) (At 30 September 2024)
#### Send

- [EHC plans issued on time](#page-indicators-dfe-ehcp-20wk-timeliness) (Calendar year 2024)

### Notes

Published as three domain scores (demand, capacity, SEND); the combined index is withheld (D-0090). Pressure indicators are never in la_need.

### Results

#### LA system pressure: service area

> **Domains only.** The combined index below is computed to document its robustness, and is not published (D-0090). The published outputs are the domain scores.

144 of 153 areas have a score.

Areas without a score are `incomplete` because a domain could not be scored:

- demand: Isles of Scilly, City of London
- capacity: Isles of Scilly, North Northamptonshire, West Northamptonshire, Birmingham, Kingston upon Thames, Richmond upon Thames
- send: Dorset, City of London, Lewisham

**Indicators not eligible at this level:**

- `ho_nrm_referrals_under18`: coverage 5.2% < 95%
- `dfe_sw_agency_rate`: coverage 94.8% < 95%

**Domain checks** (Spearman ρ between indicators; Cronbach's α; first component):

| Domain | Indicators | α | PC1 share | Weakest fit with rest |
|---|---|---|---|---|
| demand | 4 | 0.77 | 0.62 | dfe_cin_rereferrals_12m (+0.22) |
| capacity | 3 | 0.39 | 0.48 | dfe_sw_average_caseload (+0.07) |
| send | 1 | – | – | – |

**Convergent validity:**

| Measure | Spearman ρ | Areas |
|---|---|---|
| Index of Multiple Deprivation: average score | 0.240 | 144 |
| Income deprivation affecting children: average score | 0.151 | 144 |

**Stability** (primary method, each indicator dropped in turn):

| Indicator dropped | Median |rank change| | Largest |rank change| | Areas changing decile |
|---|---|---|---|
| dfe_cin_at_31mar | 3 | 20 | 40 of 144 |
| dfe_cpp_at_31mar | 3 | 26 | 45 of 144 |
| dfe_cla_at_31mar | 3 | 31 | 43 of 144 |
| dfe_cin_rereferrals_12m | 4 | 37 | 51 of 144 |
| dfe_sw_vacancy_rate | 5 | 38 | 70 of 144 |
| dfe_sw_turnover_rate | 6 | 67 | 65 of 144 |
| dfe_sw_average_caseload | 6 | 66 | 69 of 144 |
| dfe_ehcp_20wk_timeliness | – | – | not droppable (only indicator in its domain) |

**Face validity:** highest and lowest ranked areas:

| Rank | Area | Score |
|---|---|---|
| 1 | Tameside | 68.24 |
| 2 | Plymouth | 52.75 |
| 3 | North East Lincolnshire | 51.29 |
| 4 | Liverpool | 50.33 |
| 5 | Isle of Wight | 49.11 |
| 6 | Kingston upon Hull, City of | 48.26 |
| 7 | Middlesbrough | 46.75 |
| 8 | Oldham | 44.70 |
| 9 | Portsmouth | 44.49 |
| 10 | Havering | 44.27 |
| 135 | Norfolk | 6.76 |
| 136 | Enfield | 6.36 |
| 137 | Hammersmith and Fulham | 6.03 |
| 138 | Westminster | 5.83 |
| 139 | Wandsworth | 5.34 |
| 140 | Hertfordshire | 5.18 |
| 141 | Hounslow | 4.60 |
| 142 | Lincolnshire | 4.25 |
| 143 | Kensington and Chelsea | 2.34 |
| 144 | Barnet | 1.59 |

**Uncertainty:** share of rank variance explained by each choice (first-order):

| Choice | First-order share |
|---|---|
| normalisation | 0.062 |
| aggregation | 0.444 |
| missing_threshold | 0.004 |
| inclusion | 0.005 |
| weights | 0.168 to 0.438 |

Areas with a robust decile (same decile in at least 80% of runs): 10.4% over all runs; 13.9% over the 333 runs that use the primary aggregation (IoD exponential transformation). Areas whose decile stays within one decile in at least 80% of runs: 52.8%.

**Domain stability** (share of areas):

| Domain | Same decile (robust) | Within one decile |
|---|---|---|
| demand | 60.3% | 97.4% |
| capacity | 49.0% | 88.4% |
| send (one indicator: stable by construction) | 100.0% | 100.0% |


---

[Methodology index](#page-index)

---

<a id="page-composites-neighbourhood_need"></a>

## Neighbourhood need (experimental)

Release `2dda583978fb-19eda0e60019` · composites version `0.1-experimental` · family **need**
· levels small_area, intermediate_area

> **Experimental.** Not endorsed by any official publisher. See the
> [composite methodology](#page-composites-methodology_composite).

### Domains and indicators

#### Economic hardship

- [Income deprivation affecting children (IDACI)](#page-indicators-mhclg-iod25-idaci-score) (IoD 2025 (most inputs 2022/23))
#### Health disability

- [Children receiving Disability Living Allowance](#page-indicators-dwp-dla-claimants-under16) (February 2025)
- [Young people receiving PIP](#page-indicators-dwp-pip-claimants-16-24) (March 2025)
- [Disabled children and young people](#page-indicators-census21-disabled-0-24) (Census Day, 21 March 2021)
#### Family housing

- [Overcrowded households with children](#page-indicators-census21-overcrowded-households-dep-children) (Census Day, 21 March 2021)
- [Lone-parent households](#page-indicators-census21-lone-parent-households-dep-children) (Census Day, 21 March 2021)
- [Young carers](#page-indicators-census21-unpaid-carers-5-24) (Census Day, 21 March 2021)
#### Safety

- [Violence and sexual offences](#page-indicators-police-crime-violence-sexual) (1 April 2024 to 31 March 2025)

### Notes

Overlaps with IMD by design (IDACI is benefit-based). Report alongside IMD, not instead of it (12.7).

### Results

#### Neighbourhood need: small area

33,723 of 33,755 areas have a score.

Areas without a score are `incomplete` because a domain could not be scored:

- health_disability: 32 areas

**Indicators not eligible at this level:**

- `dwp_pip_claimants_16_24`: coverage 92.0% < 95%

**Domain checks** (Spearman ρ between indicators; Cronbach's α; first component):

| Domain | Indicators | α | PC1 share | Weakest fit with rest |
|---|---|---|---|---|
| economic_hardship | 1 | – | – | – |
| health_disability | 2 | 0.76 | 0.81 | dwp_dla_claimants_under16 (+0.61) |
| family_housing | 3 | 0.61 | 0.57 | census21_unpaid_carers_5_24 (+0.32) |
| safety | 1 | – | – | – |

**Convergent validity:**

| Measure | Spearman ρ | Areas |
|---|---|---|
| Index of Multiple Deprivation (score) | 0.886 | 33,723 |
| Income deprivation affecting children (IDACI) | 0.899 | 33,723 |

**Stability** (primary method, each indicator dropped in turn):

| Indicator dropped | Median |rank change| | Largest |rank change| | Areas changing decile |
|---|---|---|---|
| mhclg_iod25_idaci_score | – | – | not droppable (only indicator in its domain) |
| dwp_dla_claimants_under16 | 639 | 16212 | 9,205 of 33,715 |
| census21_disabled_0_24 | 707 | 13300 | 8,752 of 32,945 |
| census21_overcrowded_households_dep_children | 617 | 8818 | 8,597 of 33,723 |
| census21_lone_parent_households_dep_children | 598 | 13341 | 7,799 of 33,723 |
| census21_unpaid_carers_5_24 | 656 | 10198 | 8,980 of 33,723 |
| police_crime_violence_sexual | – | – | not droppable (only indicator in its domain) |

**Face validity:** highest and lowest ranked areas:

| Rank | Area | Score |
|---|---|---|
| 1 | Tendring 018A | 95.71 |
| 2 | Wirral 016G | 90.32 |
| 3 | Wirral 016C | 89.17 |
| 4 | Liverpool 024B | 88.74 |
| 5 | Birmingham 125E | 88.19 |
| 6 | Tendring 016B | 88.05 |
| 7 | Halton 013F | 86.69 |
| 8 | Middlesbrough 011B | 86.53 |
| 9 | Tendring 015D | 86.36 |
| 10 | Great Yarmouth 006A | 86.13 |
| 33,714 | Trafford 026A | 0.41 |
| 33,715 | Trafford 021A | 0.39 |
| 33,716 | Wandsworth 017B | 0.37 |
| 33,717 | Bromley 027C | 0.36 |
| 33,718 | Richmond upon Thames 012A | 0.33 |
| 33,719 | Trafford 028A | 0.33 |
| 33,720 | Trafford 023B | 0.29 |
| 33,721 | Trafford 021C | 0.24 |
| 33,722 | Trafford 021B | 0.23 |
| 33,723 | Trafford 026B | 0.20 |

**Uncertainty:** share of rank variance explained by each choice (first-order):

| Choice | First-order share |
|---|---|
| normalisation | 0.075 |
| aggregation | 0.528 |
| missing_threshold | 0.000 |
| inclusion | 0.003 |
| weights | 0.084 to 0.242 |

Areas with a robust decile (same decile in at least 80% of runs): 19.9% over all runs; 42.1% over the 319 runs that use the primary aggregation (IoD exponential transformation). Areas whose decile stays within one decile in at least 80% of runs: 91.3%.

**Domain stability** (share of areas):

| Domain | Same decile (robust) | Within one decile |
|---|---|---|
| economic_hardship (one indicator: stable by construction) | 100.0% | 100.0% |
| health_disability | 80.7% | 99.6% |
| family_housing | 37.9% | 92.9% |
| safety (one indicator: stable by construction) | 100.0% | 100.0% |

#### Neighbourhood need: intermediate area

6,856 of 6,856 areas have a score.

**Domain checks** (Spearman ρ between indicators; Cronbach's α; first component):

| Domain | Indicators | α | PC1 share | Weakest fit with rest |
|---|---|---|---|---|
| economic_hardship | 1 | – | – | – |
| health_disability | 3 | 0.87 | 0.79 | census21_disabled_0_24 (+0.72) |
| family_housing | 3 | 0.69 | 0.62 | census21_overcrowded_households_dep_children (+0.44) |
| safety | 1 | – | – | – |

**Convergent validity:**

| Measure | Spearman ρ | Areas |
|---|---|---|
| Index of Multiple Deprivation (score) | 0.909 | 6,856 |
| Income deprivation affecting children (IDACI) | 0.921 | 6,856 |

**Stability** (primary method, each indicator dropped in turn):

| Indicator dropped | Median |rank change| | Largest |rank change| | Areas changing decile |
|---|---|---|---|
| mhclg_iod25_idaci_score | – | – | not droppable (only indicator in its domain) |
| dwp_dla_claimants_under16 | 61 | 1237 | 865 of 6,856 |
| dwp_pip_claimants_16_24 | 64 | 1664 | 1,013 of 6,856 |
| census21_disabled_0_24 | 62 | 1060 | 836 of 6,856 |
| census21_overcrowded_households_dep_children | 125 | 1171 | 1,677 of 6,856 |
| census21_lone_parent_households_dep_children | 101 | 2002 | 1,360 of 6,856 |
| census21_unpaid_carers_5_24 | 121 | 1371 | 1,690 of 6,856 |
| police_crime_violence_sexual | – | – | not droppable (only indicator in its domain) |

**Face validity:** highest and lowest ranked areas:

| Rank | Area | Score |
|---|---|---|
| 1 | Wirral 016 | 92.52 |
| 2 | Tendring 016 | 90.96 |
| 3 | Great Yarmouth 006 | 90.74 |
| 4 | Blackpool 010 | 87.25 |
| 5 | North East Lincolnshire 002 | 85.76 |
| 6 | Bradford 052 | 85.30 |
| 7 | Sefton 037 | 84.92 |
| 8 | Blackpool 013 | 84.40 |
| 9 | Sheffield 048 | 83.51 |
| 10 | Swale 002 | 82.58 |
| 6,847 | Wandsworth 017 | 0.57 |
| 6,848 | Bromley 025 | 0.56 |
| 6,849 | North Tyneside 001 | 0.53 |
| 6,850 | Elmbridge 018 | 0.53 |
| 6,851 | Bristol 009 | 0.47 |
| 6,852 | Wandsworth 009 | 0.44 |
| 6,853 | Trafford 020 | 0.40 |
| 6,854 | Trafford 023 | 0.27 |
| 6,855 | Trafford 021 | 0.26 |
| 6,856 | Trafford 026 | 0.13 |

**Uncertainty:** share of rank variance explained by each choice (first-order):

| Choice | First-order share |
|---|---|
| normalisation | 0.064 |
| aggregation | 0.613 |
| missing_threshold | 0.000 |
| inclusion | 0.003 |
| weights | 0.095 to 0.258 |

Areas with a robust decile (same decile in at least 80% of runs): 27.1% over all runs; 56.1% over the 324 runs that use the primary aggregation (IoD exponential transformation). Areas whose decile stays within one decile in at least 80% of runs: 92.0%.

**Domain stability** (share of areas):

| Domain | Same decile (robust) | Within one decile |
|---|---|---|
| economic_hardship (one indicator: stable by construction) | 100.0% | 100.0% |
| health_disability | 91.4% | 99.7% |
| family_housing | 59.5% | 96.9% |
| safety (one indicator: stable by construction) | 100.0% | 100.0% |


---

[Methodology index](#page-index)

---

<a id="page-transformations"></a>

## Transformation specification

Release `2dda583978fb-19eda0e60019`. This page specifies every transformation from the published files to
the released tables, with the rule, the reason and the code that implements it. It is written for
engineers moving the proof of concept to scheduled pipelines on live data. Every source, file,
mapping and parameter below is generated from the configuration the build used, so it cannot
drift from the code. Decision numbers (D-nnnn) refer to the [decision log](#page-decision_log), which
gives the full reasoning.

### 1. Layers and invariants

| Layer | Holds | Written by | Rule |
|---|---|---|---|
| L0 raw | Published files exactly as downloaded, with SHA-256 | `cypneed ingest` | Write-once; a new version goes in a new dated folder. API queries are saved beside responses. Rebuilds never call APIs. |
| L1 staged | One long Parquet table per published table | `cypneed stage` | Values kept as published text; labels kept; non-England rows kept; file totals checked. |
| L2 harmonised | `fact_<level>`, `fact_other_geography`, dimensions | `cypneed harmonise` | Observed values only: England only, current codes, standard age bands; nothing imputed. |
| L3 derived | `derived_<level>` | `cypneed derive` | Rates, intervals, smoothing, percentiles, conversions. Never overwrites L2. |
| L4 serving | `serve_*`, `profile_*` views, release files | `cypneed serve`, `cypneed release` | Display layer; fallbacks are display only. |
| L5 composites | `l5_*` tables | `cypneed composite` | Experimental; reads L2–L4 read-only. |

Invariants that every pipeline must keep:

1. **Published figures win.** A value published at a level is used as is; a sum of smaller areas is only used where nothing is published, and any difference is written to `reconciliation`.
2. **Counts move between geographies, rates never do.** Rates are recomputed from summed numerators and denominators.
3. **Nothing is imputed.** A sum with any suppressed or missing part is NULL with a `null_reason` and bounds.
4. **No value is pushed down** from an area to the areas inside it.
5. **Every row carries lineage** (`source_file_id`, `lineage_key`) and the `snapshot_id` (code commit + data hash).
6. **Determinism.** Rows are sorted before floating-point sums, and Monte Carlo runs are seeded, so a rebuild gives identical content (gate 17).

### 2. Pipeline stages

| Step | Command | Code | Input → output | Rules | QA |
|---|---|---|---|---|---|
| T1 Ingest | `ingest` | `ingest/` | publisher URL or API → `data/raw/<source>/<date>/` | Hash; register in `dim_source_file`; never overwrite. | Gate 1 |
| T2 Stage | `stage` | `stage/<module>.py` (per source, below) | raw file → `data/staged/<source>/<table>.parquet` | Find header rows and columns by label; keep text; check totals and expected rows. | Gate 2 |
| T3 Recode | — | not needed (D-0041) | LSOA11 → LSOA21 | Only if a source publishes LSOA11; none does. | — |
| T4 Assign points | `harmonise` | `harmonise/phase2.py` (`police`) | police records → LSOA21 counts | Published LSOA21 code; checked against full-resolution boundary point-in-polygon; rejects kept with a reason. | Gate 11 |
| T5 Apportion | `derive` | `derive/overlap.py` | Sub-ICB values → overlapping councils | Overlaps only; GP-registered population weights; flagged `converted_overlap`, not spatially suitable. | Gate 12 |
| T6 Aggregate | `harmonise` | `harmonise/facts.py` (`aggregate`, `fill_levels`) | LSOA → MSOA → LAD → UTLA → England | Sum counts only, where nesting is proven and nothing is published; NULL if any part is missing. | Gates 4, 7, 8 |
| T6b Other geographies | `harmonise` | `harmonise/phase4.py` (`t6b`) | Sub-ICB / police force / youth justice areas | coterminous → relabel; nests within → sum; contains → fallback only; overlaps → T5. | Gate 12 |
| T6c IoD summaries | `derive` | `derive/iod.py` | IoD LSOA scores → MSOA summaries | Population-weighted average score; share in most deprived decile; validated against published LAD summaries. | Gate 13 |
| T7 Rates and intervals | `derive` | `derive/rates.py`, `derive/stats.py` | counts + populations → rates | Formulas below. | Gate 9 |
| T8 Small numbers | `derive` | `derive/rates.py` (`eb_rows`) | rates → reliability flags, EB-smoothed rates | Marshall global EB; never replaces the crude rate. | Gate 10 |
| T9 Comparability | `derive` | `derive/rates.py` (`comparability_rows`) | rates / values → percentiles, z-scores | Per level, native values only, fallbacks excluded. | Gate 10 |
| Publisher's method | `derive` | `derive/publisher_method.py` | counts + populations → published-style percentages where unpublished | Only after the method reproduces every published value (D-0085). | — |
| T10 Metadata | `harmonise` | `config.py`, `db.py` | config → `dim_*` | Catalogue validated (`validate-config`). | Gate 3 |
| T11 Serve | `serve` | `sql/serving.sql`, `serve/build.py`, `sql/fallback.sql` | L2/L3 → `serve_*`, `profile_*` | One row per area × column, value or reason; fallbacks labelled. | Gates 15, 16 |
| L5 Composites | `composite` | `composite/` | L2/L3 → `l5_*` | SPEC 12; see the [composite methodology](#page-composites-methodology_composite). | Gate 19 |
| T12 Release | `release`, `package-release` | `release/` | DB → release files, Fabric bundle | Clean commit only; reproducibility report must match. | Gates 17, 18 |

### 3. Rules used by many sources

#### 3.1 Geography

- Hierarchy: LSOA21 → MSOA21 → LAD (April 2025) → UTLA (April 2025) → England. Each LSOA's and MSOA's parent is proven from Output Area membership and checked against full-resolution boundaries (99.9% of area inside the assigned parent).
- **Code successors** (`config/geography.yaml`): an old code is relabelled to its successor only where the new code is absent from that series and boundaries are identical (D-0036, D-0060).
- **Other geographies** are classified against the hierarchy by membership units (D-0054 onwards): `coterminous` (relabel), `nests_within` (sum when the parent is fully covered), `contains` (no conversion; the containing value is a labelled fallback), `overlaps` (T5).

#### 3.2 Symbols, suppression and missing values

Each source's symbols are listed in its section below with the `null_reason` they map to and the most
they can hide. A cell with a symbol is stored as NULL with the symbol in `source_code`. A sum is
NULL if any part is NULL: `suppressed` (with `count_lower`, `count_upper`, `n_suppressed`) or
`incomplete`. Absent rows are read as 0 only where the source is proven to list every non-zero
case (D-0066 EHC plans, D-0084 asylum support, D-0048 police, children's homes).

#### 3.3 Age bands

Populations are held by single year of age; a denominator band is the exact sum of the single years
covering the numerator band. Source bands are kept as published (`src_*`) and never split.

#### 3.4 Rates and confidence intervals (T7)

For count *x* and denominator *n*: rate = *x* / *n* × multiplier (100, 1,000 or 10,000 per indicator).
The denominator must match area, age band, sex and ethnicity classification; stock measures use the
population nearest the reference date, flow measures the mid-period population, and the gap must not
exceed `max_denominator_gap_days`.

- **Wilson score** (proportions), z = 1.959964, p = x/n:
  centre = (p + z²/2n) / (1 + z²/n); half-width = z·√(p(1−p)/n + z²/4n²) / (1 + z²/n).
  Limits are clipped to [0, 1]; x = 0 gives lower 0, x = n gives upper 1.
- **Byar** (event rates): lower count = x(1 − 1/9x − z/3√x)³ (0 when x = 0); upper count =
  (x+1)(1 − 1/9(x+1) + z/3√(x+1))³; each divided by *n* and multiplied.
- **Reliability:** `low_reliability` when x < `min_reliable_numerator` or n < `min_reliable_denominator`.
- Undefined rates are NULL with a reason: `zero_denominator`, `numerator_exceeds_denominator`,
  `denominator_suppressed`, `no_matching_denominator`, `denominator_period_gap`.

#### 3.5 Smoothing and comparability (T8, T9)

- **Marshall global empirical Bayes** per indicator and level: m = Σx/Σn; s² = Σn(r−m)²/Σn;
  φ = max(s² − m/n̄, 0); Cᵢ = φ/(φ + m/nᵢ); EBᵢ = m + Cᵢ(rᵢ − m).
- **Percentile** = (average rank − 1)/(N − 1) × 100, ties averaged, NULLs excluded; **z-score** uses
  the population standard deviation. Areas are sorted by code before any sum (determinism).

#### 3.6 IoD summaries (T6c)

MSOA score = Σ(LSOA score × population)/Σ population (children 0–15 for IDACI, total population
otherwise); share in decile 1 = population in decile-1 LSOAs / population. Ranks and deciles are never
averaged. Validated against MHCLG's published LAD and UTLA summaries (gate 13).

#### 3.7 Fallbacks and the publisher's method

- **Fallback** (`sql/fallback.sql`): where a measure exists only for an area that wholly contains a council, that value is shown for the council with `is_fallback = true`. Never used in derived values, profiles or composites.
- **Publisher's method** (`publisher_method_fill`): a published percentage is computed for areas the publisher leaves out, only after the stated method reproduces every published value to 1e-9 (D-0085).

### 4. Sources

#### G1: Output Area (2021) to LSOA (2021) to MSOA (2021) to LAD (April 2025) lookup in England and Wales

- **Publisher:** Office for National Statistics · <https://geoportal.statistics.gov.uk/datasets/b9ca90c10aaa4b8d9791e9859a38ca67/about>
- **Native geography:** OA21 · **period:** April 2025 LAD boundaries · **target:** `dim_geography`
- **Staging code:** `stage/lookups.py` · **harmonise code:** `harmonise/geography.py (nesting proof)`
- **Files:**
  - `oa21_lsoa21_msoa21_lad22_exact`: Output Area (2021) to LSOA to MSOA to LAD (December 2021) Exact Fit Lookup in EW (V3)
  - `oa21_wd25_lad25`: Output Area (2021) to Ward (2025) to LAD (May 2025) Best Fit Lookup in EW (V3)
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0027, D-0095

#### G2: Lower Tier Local Authority to Upper Tier Local Authority (April 2025) lookup in England and Wales

- **Publisher:** Office for National Statistics · <https://geoportal.statistics.gov.uk/datasets/53ec53c55c8949b19970ce8c571b3c08/about>
- **Native geography:** LAD25 · **period:** April 2025 · **target:** `dim_geography`
- **Staging code:** `stage/lookups.py` · **harmonise code:** `harmonise/geography.py (nesting proof)`
- **Files:**
  - `lad25_ctyua25`: Local Authority District to County and Unitary Authority (April 2025) Lookup in EW (V2)
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0028, D-0095

#### G3: LSOA (2021) to Sub ICB Location to ICB lookup (2024)

- **Publisher:** Office for National Statistics · <https://geoportal.statistics.gov.uk/datasets/27d32e68e05a4c848276330903bb18fc/about>
- **Native geography:** LSOA21 · **period:** 2024 configuration · **target:** `lkp_other_to_hierarchy`
- **Staging code:** `stage/lookups.py` · **harmonise code:** `harmonise/phase4.py (build_geographies, t6b)`
- **Files:**
  - `lsoa21_sicbl24_icb24`: LSOA (2021) to SICBL to ICB to Cancer Alliances to LAD (April 2024) Lookup in EN
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0069, D-0075, D-0078, D-0095

#### G3b: Patients Registered at a GP Practice (LSOA by age and sex)

- **Publisher:** NHS England · <https://digital.nhs.uk/data-and-information/publications/statistical/patients-registered-at-a-gp-practice/april-2025>
- **Native geography:** LSOA21 · **period:** Quarter nearest 1 April 2025 · **target:** `lkp_apportion_weights`
- **Staging code:** `stage/phase4.py` · **harmonise code:** `harmonise/phase4.py (gp_registered)`
- **Files:**
  - `gp_reg_sing_age_regions_202504`: Patients Registered at a GP Practice, April 2025: single year of age (Commissioning Regions, ICBs, SICBLs, PCNs) · <https://files.digital.nhs.uk/99/38AC11/gp-reg-pat-prac-sing-age-regions.zip>
  - `gp_reg_lsoa21_202504`: Patients Registered at a GP Practice, April 2025: LSOA 2021 (all persons, females, males) · <https://files.digital.nhs.uk/7E/26EB57/gp-reg-pat-prac-lsoa-2021-male-female-Apr-25.zip>
- **Disclosure control:** none; tolerance 0 / 0.005. NHS England GP registrations: counts by practice x LSOA21 and sex, no suppression or rounding symbols (inspection, Phase 4); female + male sum exactly to every published total. Patients of unknown sex are excluded by the publisher. Used only as weights and Sub-ICB denominators.
- **Decisions:** D-0069, D-0095

#### G4: National Statistics Postcode Lookup (NSPL)

- **Publisher:** Office for National Statistics · <https://geoportal.statistics.gov.uk/datasets/9d8364ebae8b4439aa66cda440e54fc8/about>
- **Native geography:** postcode · **period:** Latest · **target:** `point assignment (T4)`
- **Staging code:** `—` · **harmonise code:** `harmonise/geography.py (nesting proof)`
- **Files:**
  - `nspl_aug_2026`: National Statistics Postcode Lookup (August 2026)
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0031, D-0095

#### G5: Boundaries: LSOA (Dec 2021), MSOA (Dec 2021), LAD (Apr 2025), Counties and Unitary Authorities (Apr 2025), Sub ICB Locations (Apr 2024), PFA, Wards

- **Publisher:** Office for National Statistics · <https://geoportal.statistics.gov.uk/datasets/2bbaef5230694f3abae4f9145a3a9800/about>
- **Native geography:** various · **period:** As listed in title · **target:** `nesting proof, neighbours, point-in-polygon (BFC); release boundaries/tiles (BGC/BSC)`
- **Staging code:** `stage/boundaries.py` · **harmonise code:** `harmonise/geography.py (nesting proof)`
- **Files:**
  - `lsoa21_bfc`: Lower layer Super Output Areas (December 2021) Boundaries EW BFC (V10)
  - `lsoa21_bgc`: Lower layer Super Output Areas (December 2021) Boundaries EW BGC (V5)
  - `msoa21_bfc`: Middle layer Super Output Areas (December 2021) Boundaries EW BFC (V7)
  - `msoa21_bgc`: Middle layer Super Output Areas (December 2021) Boundaries EW BGC (V3)
  - `lad25_bfc`: Local Authority Districts (May 2025) Boundaries UK BFC (V2)
  - `lad25_bgc`: Local Authority Districts (May 2025) Boundaries UK BGC (V2)
  - `ctyua25_bfc`: Counties and Unitary Authorities (December 2025) Boundaries UK BFC
  - `ctyua25_bgc`: Counties and Unitary Authorities (December 2025) Boundaries UK BGC
- **Disclosure control:** none; tolerance 0 / 0. Geometry; no statistical values.
- **Decisions:** D-0076, D-0095

#### G6: LSOA (2021) to Electoral Ward to LAD lookup

- **Publisher:** Office for National Statistics · <https://geoportal.statistics.gov.uk/datasets/f29a49574cc84f6d8e6e59ce2d8efb18/about>
- **Native geography:** WD25 · **period:** May 2025 (verify) · **target:** `dim_other_geography, lkp_other_to_hierarchy`
- **Staging code:** `stage/lookups.py` · **harmonise code:** `harmonise/geography.py (nesting proof)`
- **Files:**
  - `lsoa21_wd25_lad25`: LSOA (2021) to Electoral Ward (2025) to LAD (2025) Best Fit Lookup in EW (V2)
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0095

#### G7: Youth justice service to local authority composition (constructed)

- **Publisher:** Youth Justice Board (list of services); composition constructed by this project · <https://www.gov.uk/government/collections/youth-offending-team-contact-details>
- **Native geography:** YJS · **period:** 2024/25 · **target:** `dim_other_geography, lkp_other_to_hierarchy`
- **Staging code:** `—` · **harmonise code:** `harmonise/phase4.py (build_geographies, t6b)`
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0069, D-0071, D-0075, D-0078

#### G8: LAD to Police Force Area lookup

- **Publisher:** Office for National Statistics · <https://geoportal.statistics.gov.uk/datasets/8f77bda25c124e43aca5f3b90494e405/about>
- **Native geography:** LAD25 · **period:** 2024/25 · **target:** `lkp_other_to_hierarchy`
- **Staging code:** `stage/lookups.py` · **harmonise code:** `harmonise/phase4.py (build_geographies, t6b)`
- **Files:**
  - `lad25_csp25_pfa25`: Local Authority District to Community Safety Partnership to PFA (April 2025) Lookup in EW
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0069, D-0071, D-0075, D-0078, D-0095

#### G9: LSOA (2011) to LSOA (2021) to LAD lookup with change indicator

- **Publisher:** Office for National Statistics
- **Native geography:** LSOA11 · **period:** static · **target:** `lkp_apportion_weights ('X' cases only)`
- **Staging code:** `—` · **harmonise code:** `harmonise/phase4.py (build_geographies, t6b)`
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0069

#### G10: MSOA Names (2021 MSOAs)

- **Publisher:** House of Commons Library · <https://houseofcommonslibrary.github.io/msoanames/>
- **Native geography:** MSOA21 · **period:** 2021 vintage · **target:** `dim_geography display names`
- **Staging code:** `stage/lookups.py` · **harmonise code:** `harmonise/geography.py (nesting proof)`
- **Files:**
  - `msoa_names_2_3`: House of Commons Library MSOA Names (2021 MSOAs) v2.3, 13 February 2026 · <https://houseofcommonslibrary.github.io/msoanames/MSOA-Names-2.3.csv>
- **Disclosure control:** none; tolerance 0 / 0. Lookup; no statistical values.
- **Decisions:** D-0033, D-0095

#### P1: Lower layer Super Output Area population estimates (Small Area Population Estimates), single year of age and sex

- **Publisher:** Office for National Statistics · <https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/bulletins/annualsmallareapopulationestimates/latest>
- **Native geography:** LSOA21 · **period:** mid-2024 (30 June 2024) · **target:** `fact_small_area`
- **Staging code:** `stage/population.py` · **harmonise code:** `harmonise/population.py`
- **Files:**
  - `sape_lsoa_sya_2022_2024`: LSOA mid-year population estimates, single year of age, mid-2022 (revised Nov 2025) to mid-2024 · <https://www.ons.gov.uk/file?uri=/peoplepopulationandcommunity/populationandmigration/populationestimates/datasets/lowersuperoutputareamidyearpopulationestimates/mid2022revisednov2025tomid2024/sapelsoasyoa20222024.xlsx>
  - `sape_msoa_sya_2022_2024`: MSOA mid-year population estimates, single year of age, mid-2022 (revised Nov 2025) to mid-2024 · <https://www.ons.gov.uk/file?uri=/peoplepopulationandcommunity/populationandmigration/populationestimates/datasets/middlesuperoutputareamidyearpopulationestimates/mid2022revisednov2025tomid2024/sapemsoasyoa20222024.xlsx>
- **Disclosure control:** none; tolerance 0 / 0. ONS small area population estimates are constrained to MSOA and local authority mid-year estimates (ONS SAPE quality and methodology information, https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/smallareapopulationestimatesqmi). Checked: LSOA single-year sums equal the published MSOA estimates exactly.
- **Decisions:** D-0014, D-0094, D-0095

#### P1b: Mid-year population estimates, single year of age and sex (LAD, UTLA, England)

- **Publisher:** Office for National Statistics · <https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/datasets/populationestimatesforukenglandandwalesscotlandandnorthernireland>
- **Native geography:** LAD25 · **period:** mid-2024 · **target:** `fact_lad, fact_service_area, fact_nation`
- **Staging code:** `stage/population.py` · **harmonise code:** `harmonise/population.py`
- **Files:**
  - `mye24_tables_uk`: Population estimates for the UK, England, Wales, Scotland and Northern Ireland: mid-2024 · <https://www.ons.gov.uk/file?uri=/peoplepopulationandcommunity/populationandmigration/populationestimates/datasets/populationestimatesforukenglandandwalesscotlandandnorthernireland/mid2024/mye24tablesuk.xlsx>
- **Disclosure control:** none; tolerance 0 / 0. Published LA mid-year estimates. Checked: LAD sums equal the published UTLA and England figures exactly in every age and sex cell.
- **Decisions:** D-0014, D-0029, D-0031, D-0036, D-0095

#### P4: Census 2021: ethnic group by age (custom dataset, LSOA21)

- **Publisher:** Office for National Statistics · <https://www.ons.gov.uk/datasets/create>
- **Native geography:** LSOA21 · **period:** Census Day 21 March 2021 · **target:** `fact_small_area`
- **Staging code:** `stage/apis.py` · **harmonise code:** `harmonise/phase2.py (census)`
- **Files:**
  - `p4_eth6a_age7a_lsoa`: Census 2021 usual residents by ethnic group (6) and age (7), LSOA
  - `p4_eth6a_age7a_msoa`: Census 2021 usual residents by ethnic group (6) and age (7), MSOA
  - `p4_eth6a_age7a_ltla23`: Census 2021 usual residents by ethnic group (6) and age (7), LTLA 2023
  - `p4_eth6a_age7a_utla23`: Census 2021 usual residents by ethnic group (6) and age (7), UTLA 2023
  - `p4_eth6a_age7a_ctry`: Census 2021 usual residents by ethnic group (6) and age (7), country
- **Disclosure control:** record_swapping, cell_key; tolerance 10 / 0.01. Census 2021: targeted record swapping and cell key perturbation (ONS, 'Protecting personal data in Census 2021 results', https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/protectingpersonaldataincensus2021results). Small cells are perturbed, so sums of cells differ slightly from published totals; differences are reported in reconciliation.csv.
- **Decisions:** D-0011, D-0038, D-0045, D-0094

#### P7: Schools, pupils and their characteristics: pupils by ethnicity and local authority

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/school-pupils-and-their-characteristics/2024-25>
- **Native geography:** UTLA25 · **period:** January 2025 school census · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_spc_2024_25_p7`: Schools, pupils and their characteristics, 2024/25: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/63491b17-2037-4533-b719-d3656aaf6ed5/files?fromPage=ReleaseDownloads>
- **Disclosure control:** none; tolerance 0 / 0.001. School census (SPC) data guidance: no suppression or rounding applied; 'x' not applicable, 'z' unknown. Checked: LA sums equal the published England figures exactly.
- **Symbols:** `x` = Not applicable (SPC convention) → `not_applicable`; `z` = Unknown (SPC convention) → `not_published`
- **Decisions:** D-0011, D-0054, D-0094, D-0095

#### D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores

- **Publisher:** Ministry of Housing, Communities and Local Government · <https://www.gov.uk/government/statistics/english-indices-of-deprivation-2025>
- **Native geography:** LSOA21 · **period:** IoD 2025 (input data mostly 2022/23) · **target:** `fact_small_area`
- **Staging code:** `stage/iod.py` · **harmonise code:** `harmonise/phase2.py (iod)`
- **Files:**
  - `iod25_file7_all`: English Indices of Deprivation 2025, File 7: all ranks, scores, deciles and population denominators (LSOA) · <https://assets.publishing.service.gov.uk/media/691ded56d140bbbaa59a2a7d/File_7_IoD2025_All_Ranks_Scores_Deciles_Population_Denominators.csv>
- **Disclosure control:** none; tolerance 0 / 0. Index values (scores, ranks, deciles): not additive; no disclosure control.

#### D1b: English Indices of Deprivation 2025: local authority summary measures

- **Publisher:** Ministry of Housing, Communities and Local Government · <https://www.gov.uk/government/statistics/english-indices-of-deprivation-2025>
- **Native geography:** LAD25 · **period:** IoD 2025 · **target:** `fact_lad, fact_service_area`
- **Staging code:** `stage/iod.py` · **harmonise code:** `harmonise/phase2.py (iod)`
- **Files:**
  - `iod25_file10_lad`: English Indices of Deprivation 2025, File 10: Local Authority District summaries (lower-tier) v2 · <https://assets.publishing.service.gov.uk/media/6917412ebc34c86ce4e6e7fc/File_10_-_IoD2025_Local_Authority_District_Summaries__lower-tier__v2.xlsx>
  - `iod25_file11_utla`: English Indices of Deprivation 2025, File 11: Local Authority District summaries (upper-tier) v2 · <https://assets.publishing.service.gov.uk/media/6917414ab49cc44345161802/File_11_-_IoD2025_Local_Authority_District_Summaries__upper-tier__v2.xlsx>
- **Disclosure control:** none; tolerance 0 / 0. MHCLG published LA summaries: not additive. Checked: recomputed LAD averages match the published values within published rounding (gate 13).
- **Decisions:** D-0013, D-0083

#### F1: Children in Low Income Families: local area statistics (FYE 2025)

- **Publisher:** Department for Work and Pensions · <https://www.gov.uk/government/statistics/children-in-low-income-families-local-area-statistics-2022-to-2025>
- **Native geography:** LAD25 · **period:** FYE 2025 · **target:** `fact_service_area, fact_lad, fact_other_geography`
- **Staging code:** `stage/run.py` · **harmonise code:** `harmonise/phase3.py (tables: CiLIF ODS) and harmonise/phase2.py (statxplore: age bands)`
- **Files:**
  - `cilif_local_2022_2025`: Children in low income families: local area statistics, FYE 2022 to FYE 2025 (ODS tables) · <https://assets.publishing.service.gov.uk/media/69b809619d8b52961a62b49a/children-in-low-income-families-local-area-statistics-2022-2025.ods>
  - `f1_cilif_rel_la`: Children in relative low income families (BHC) by age band, local authority, FYE 2025 (Stat-Xplore)
  - `f1_cilif_rel_ctry`: Children in relative low income families (BHC) by age band, country, FYE 2025 (Stat-Xplore)
  - `f1_cilif_abs_la`: Children in absolute low income families (BHC) by age band, local authority, FYE 2025 (Stat-Xplore)
  - `f1_cilif_abs_ctry`: Children in absolute low income families (BHC) by age band, country, FYE 2025 (Stat-Xplore)
- **Disclosure control:** cell_key; tolerance 10 / 0.01. CiLIF data guidance: DWP applies disclosure control, and totals may not sum because of rounding and disclosure control; percentages rounded to 1 decimal place; no symbols. Checked: LA sums within tolerance of the published England totals.
- **Decisions:** D-0054, D-0077, D-0095

#### F2: Universal Credit households with children (Stat-Xplore)

- **Publisher:** Department for Work and Pensions · <https://stat-xplore.dwp.gov.uk>
- **Native geography:** LSOA21 · **period:** March 2025 · **target:** `fact_small_area`
- **Staging code:** `stage/apis.py` · **harmonise code:** `harmonise/phase2.py (statxplore)`
- **Files:**
  - `f2_uc_hh_children_lsoa`: Households on Universal Credit with children, LSOA21, March 2025 (Stat-Xplore)
  - `f2_uc_hh_children_msoa`: Households on Universal Credit with children, MSOA21, March 2025 (Stat-Xplore)
  - `f2_uc_hh_children_la`: Households on Universal Credit with children, local authority, March 2025 (Stat-Xplore)
  - `f2_uc_hh_children_ctry`: Households on Universal Credit with children, country, March 2025 (Stat-Xplore)
- **Disclosure control:** cell_key, suppression; tolerance 15 / 0.03. Stat-Xplore adds small random adjustments to every cell and publishes counts below 5 as 0 (D-0053). DWP: no reliance on small cells; use published data for larger areas (Stat-Xplore Data Confidentiality note). Observed: complete LSOA sums differ from published figures by about 5 x sqrt(areas summed) at the 99th percentile; 15 + 3% covers this.
- **Symbols:** `0` = Count below 5 shown as 0 by Stat-Xplore disclosure control → `suppressed` (hides ≤ 4)
- **Decisions:** D-0009, D-0043, D-0053, D-0094

#### F3: Disability Living Allowance claimants under 16 (Stat-Xplore)

- **Publisher:** Department for Work and Pensions · <https://stat-xplore.dwp.gov.uk>
- **Native geography:** LSOA21 · **period:** February 2025 · **target:** `fact_small_area`
- **Staging code:** `stage/apis.py` · **harmonise code:** `harmonise/phase2.py (statxplore)`
- **Files:**
  - `f3_dla_u16_lsoa`: DLA cases in payment aged under 16, LSOA21, February 2025 (Stat-Xplore)
  - `f3_dla_u16_msoa`: DLA cases in payment aged under 16, MSOA21, February 2025 (Stat-Xplore)
  - `f3_dla_u16_la`: DLA cases in payment aged under 16, local authority, February 2025 (Stat-Xplore)
  - `f3_dla_u16_ctry`: DLA cases in payment aged under 16, country, February 2025 (Stat-Xplore)
- **Disclosure control:** cell_key, suppression; tolerance 15 / 0.03. Stat-Xplore adds small random adjustments to every cell and publishes counts below 5 as 0 (D-0053). DWP: no reliance on small cells; use published data for larger areas (Stat-Xplore Data Confidentiality note). Observed: complete LSOA sums differ from published figures by about 5 x sqrt(areas summed) at the 99th percentile; 15 + 3% covers this.
- **Symbols:** `0` = Count below 5 shown as 0 by Stat-Xplore disclosure control → `suppressed` (hides ≤ 4)

#### F4: Personal Independence Payment claimants aged 16-24 (Stat-Xplore)

- **Publisher:** Department for Work and Pensions · <https://stat-xplore.dwp.gov.uk>
- **Native geography:** LSOA21 · **period:** January 2025 · **target:** `fact_small_area`
- **Staging code:** `stage/apis.py` · **harmonise code:** `harmonise/phase2.py (statxplore)`
- **Files:**
  - `f4_pip_16_24_lsoa`: PIP cases with entitlement aged 16-24, LSOA21, March 2025 (Stat-Xplore)
  - `f4_pip_16_24_msoa`: PIP cases with entitlement aged 16-24, MSOA21, March 2025 (Stat-Xplore)
  - `f4_pip_16_24_la`: PIP cases with entitlement aged 16-24, local authority, March 2025 (Stat-Xplore)
  - `f4_pip_16_24_ctry`: PIP cases with entitlement aged 16-24, country, March 2025 (Stat-Xplore)
- **Disclosure control:** cell_key, suppression; tolerance 15 / 0.03. Stat-Xplore adds small random adjustments to every cell and publishes counts below 5 as 0 (D-0053). DWP: no reliance on small cells; use published data for larger areas (Stat-Xplore Data Confidentiality note). Observed: complete LSOA sums differ from published figures by about 5 x sqrt(areas summed) at the 99th percentile; 15 + 3% covers this.
- **Symbols:** `0` = Count below 5 shown as 0 by Stat-Xplore disclosure control → `suppressed` (hides ≤ 4)
- **Decisions:** D-0009, D-0040, D-0043, D-0053, D-0094

#### F6: Census 2021: households with dependent children by type; occupancy rating of such households

- **Publisher:** Office for National Statistics · <https://www.ons.gov.uk/datasets/create>
- **Native geography:** LSOA21 · **period:** Census Day 21 March 2021 · **target:** `fact_small_area`
- **Staging code:** `stage/apis.py` · **harmonise code:** `harmonise/phase2.py (census)`
- **Files:**
  - `f6_hhcomp15a_occ5a_lsoa`: Census 2021 households by composition (15) and bedroom occupancy rating (5), LSOA
  - `f6_hhcomp15a_occ5a_msoa`: Census 2021 households by composition (15) and bedroom occupancy rating (5), MSOA
  - `f6_hhcomp15a_occ5a_ltla23`: Census 2021 households by composition (15) and bedroom occupancy rating (5), LTLA 2023
  - `f6_hhcomp15a_occ5a_utla23`: Census 2021 households by composition (15) and bedroom occupancy rating (5), UTLA 2023
  - `f6_hhcomp15a_occ5a_ctry`: Census 2021 households by composition (15) and bedroom occupancy rating (5), country
- **Disclosure control:** record_swapping, cell_key; tolerance 10 / 0.01. Census 2021: targeted record swapping and cell key perturbation (ONS, 'Protecting personal data in Census 2021 results', https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/protectingpersonaldataincensus2021results). Small cells are perturbed, so sums of cells differ slightly from published totals; differences are reported in reconciliation.csv.
- **Decisions:** D-0039, D-0045, D-0094

#### F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)

- **Publisher:** Office for National Statistics · <https://www.ons.gov.uk/datasets/create>
- **Native geography:** LSOA21 · **period:** Census Day 21 March 2021 · **target:** `fact_small_area`
- **Staging code:** `stage/apis.py` · **harmonise code:** `harmonise/phase2.py (census)`
- **Files:**
  - `f7a_disability_age7a_lsoa`: Census 2021 disability (5) by age (7), LSOA
  - `f7a_disability_age7a_msoa`: Census 2021 disability (5) by age (7), MSOA
  - `f7a_disability_age7a_ltla23`: Census 2021 disability (5) by age (7), LTLA 2023
  - `f7a_disability_age7a_utla23`: Census 2021 disability (5) by age (7), UTLA 2023
  - `f7a_disability_age7a_ctry`: Census 2021 disability (5) by age (7), country
  - `f7b_carer_age3c_lsoa`: Census 2021 unpaid care (7) by age (3c), LSOA
  - `f7b_carer_age3c_msoa`: Census 2021 unpaid care (7) by age (3c), MSOA
  - `f7b_carer_age3c_ltla23`: Census 2021 unpaid care (7) by age (3c), LTLA 2023
  - `f7b_carer_age3c_utla23`: Census 2021 unpaid care (7) by age (3c), UTLA 2023
  - `f7b_carer_age3c_ctry`: Census 2021 unpaid care (7) by age (3c), country
- **Disclosure control:** record_swapping, cell_key; tolerance 10 / 0.01. Census 2021: targeted record swapping and cell key perturbation (ONS, 'Protecting personal data in Census 2021 results', https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/protectingpersonaldataincensus2021results). Small cells are perturbed, so sums of cells differ slightly from published totals; differences are reported in reconciliation.csv.
- **Decisions:** D-0039, D-0094

#### C1: Children in need, reporting year 2025

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/children-in-need/2025>
- **Native geography:** UTLA25 · **period:** Year ending 31 March 2025 · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_cin_2025`: Children in need, reporting year 2025: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/9e627de0-ba01-442f-b6cf-f77d026a2ed3/files?fromPage=ReleaseDownloads>
- **Disclosure control:** suppression, rounding; tolerance 0 / 0.005. CIN data guidance: 'c' suppression (secondary suppression may apply); England and regional totals rounded to the nearest 10, LA figures unrounded. Checked: LA sums within 5 of the rounded England totals.
- **Symbols:** `c` = Suppressed to protect confidentiality (secondary suppression may apply) → `suppressed`; `z` = Not applicable → `not_applicable`; `x` = Not available → `not_published`; `u` = Low reliability → `suppressed`; `k` = Rounds to zero but is not zero → `suppressed`
- **Decisions:** D-0054, D-0095

#### C2: Children looked after in England including adoptions, reporting year 2025

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/children-looked-after-in-england-including-adoptions/2025>
- **Native geography:** UTLA25 · **period:** Year ending 31 March 2025 · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_cla_2025`: Children looked after in England including adoptions, reporting year 2025: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/8c28aca0-6ab9-400b-b7de-c5fc7a148c2e/files?fromPage=ReleaseDownloads>
- **Disclosure control:** suppression, rounding; tolerance 0 / 0.005. CLA data guidance: 'c' suppression; national and regional figures rounded to the nearest 10, LA figures unrounded. Checked: LA sums within tolerance of the rounded England totals.
- **Symbols:** `c` = Suppressed to protect confidentiality (secondary suppression may apply) → `suppressed`; `z` = Not applicable → `not_applicable`; `x` = Not available → `not_published`; `k` = Rounds to zero but is not zero (percentage < 0.5%) → `suppressed`
- **Decisions:** D-0095

#### C3: Children's social work workforce, at 30 September 2024

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/children-s-social-work-workforce/2024>
- **Native geography:** UTLA25 · **period:** At 30 September 2024 (off-period; kept as-is) · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_csww_2024`: Children's social work workforce, reporting year 2024: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/3362b622-8a39-4d69-ae14-52e156ad9953/files?fromPage=ReleaseDownloads>
- **Disclosure control:** suppression, rounding; tolerance 1 / 0.005. Children's social work workforce data guidance: 'c' suppression, 'low' rounds to 0; FTEs, rates and caseloads rounded to one decimal place.
- **Symbols:** `z` = Not applicable → `not_applicable`; `x` = Unavailable for unknown or other reasons → `not_published`; `c` = Suppressed to protect confidential information → `suppressed`; `low` = Rounds to 0 but is not 0 → `suppressed`; `u` = Low reliability → `suppressed`
- **Decisions:** D-0056, D-0095

#### C4: LA and school expenditure (Section 251 outturn) 2024-25

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/la-and-school-expenditure/2024-25>
- **Native geography:** UTLA25 · **period:** Financial year 2024-25 · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_s251_2024_25`: LA and school expenditure, financial year 2024-25: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/d826124d-95f3-4b2f-a8ab-3425f84145fe/files?fromPage=ReleaseDownloads>
- **Disclosure control:** suppression; tolerance 1000 / 0.001. Section 251 outturn: unrounded GBP; 'c' (confidential) and 'x' (not available) take the GSS meanings. No published total is reconciled.
- **Symbols:** `c` = Confidential (GSS standard) → `suppressed`; `x` = Not available (GSS standard) → `not_published`
- **Decisions:** D-0054, D-0094, D-0095

#### C5: Ofsted ILACS judgements and children's social care provider counts

- **Publisher:** Ofsted · <https://www.gov.uk/government/statistics/childrens-social-care-in-england-2025>
- **Native geography:** UTLA25 · **period:** At 31 March 2025 · **target:** `fact_service_area`
- **Staging code:** `stage/sheets.py` · **harmonise code:** `harmonise/phase3.py (ofsted)`
- **Files:**
  - `ofsted_csc_providers_2025`: Ofsted: Children's social care in England 2025, underlying data (providers and places at 31 March 2025) · <https://assets.publishing.service.gov.uk/media/688a3bd4a11f8599944092ab/Childrens_social_care_in_England_2025_underlying_data.ods>
  - `ofsted_la_outcomes_2025_03`: Ofsted: local authority (ILACS) inspection outcomes as at 31 March 2025, underlying data · <https://assets.publishing.service.gov.uk/media/68c2d38e838e7712ea2bfed3/Underlying_data_local_authority_inspection_outcomes_as_at_31_March_2025.ods>
- **Disclosure control:** none; tolerance 0 / 0. Ofsted provider list: every registered provider at 31 March 2025, no symbols. Checked: LA sums equal Ofsted's published national homes and places exactly.
- **Decisions:** D-0054, D-0095

#### E1: Special educational needs in England, January 2025

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/special-educational-needs-in-england/2024-25>
- **Native geography:** UTLA25 · **period:** January 2025 school census · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_sen_2024_25`: Special educational needs in England, 2024/25: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/0ca90382-e848-4074-8406-b0db7a03a7f7/files?fromPage=ReleaseDownloads>
- **Disclosure control:** none; tolerance 0 / 0.001. SEN data guidance: no suppression or rounding applied; release convention 'x' not applicable, 'z' not available. Checked: LA sums equal the published England figures exactly.
- **Symbols:** `x` = Not applicable (E1 convention) → `not_applicable`; `z` = Not available (E1 convention) → `not_published`
- **Decisions:** D-0054, D-0058, D-0094, D-0095

#### E2: Education, health and care plans (SEN2), January 2025

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/education-health-and-care-plans/2025>
- **Native geography:** UTLA25 · **period:** January 2025 (stock); calendar year 2024 (timeliness) · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_ehcp_2025`: Education, health and care plans, reporting year 2025: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/4c3eb898-bfd5-4081-9a96-4aa9abe32090/files?fromPage=ReleaseDownloads>
- **Disclosure control:** none; tolerance 0 / 0.001. SEN2 data guidance: no suppression; 'z' not applicable, 'x' unavailable (Lewisham 2024 timeliness withheld by DfE). Checked: LA sums equal the published England figures exactly.
- **Symbols:** `z` = Not applicable → `not_applicable`; `x` = Unavailable → `not_published`
- **Decisions:** D-0095

#### E3: Pupil absence in schools in England, 2024/25

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/pupil-absence-in-schools-in-england/2024-25>
- **Native geography:** UTLA25 · **period:** Academic year 2024/25 · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_absence_2024_25`: Pupil absence in schools in England, 2024/25: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/3fabdc00-2c0b-4b4d-bfee-1b476b2323bc/files?fromPage=ReleaseDownloads>
- **Disclosure control:** none; tolerance 0 / 0.001. Absence data guidance: no suppression or rounding applied (except PLAA tables, not used). Checked: LA sums equal the published England figures exactly.
- **Symbols:** `x` = Not available → `not_published`; `z` = Not applicable (GSS standard) → `not_applicable`
- **Decisions:** D-0058, D-0095

#### E4: Suspensions and permanent exclusions in England

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/suspensions-and-permanent-exclusions-in-england/2024-25>
- **Native geography:** UTLA25 · **period:** Academic year 2024/25 (check) · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_exclusions_2024_25`: Suspensions and permanent exclusions in England, 2024/25: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/0e388e4d-3748-49a4-984c-08dece27c222/files?fromPage=ReleaseDownloads>
- **Disclosure control:** none; tolerance 0 / 0.001. Exclusions data guidance: no suppression or rounding applied (except PLAA tables, not used). Checked: LA sums equal the published England figures exactly.
- **Symbols:** `x` = Not available → `not_published`; `z` = Not applicable → `not_applicable`
- **Decisions:** D-0058, D-0094, D-0095

#### E5: Participation in education, training and NEET age 16 to 17 by local authority

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/participation-in-education-training-and-neet-age-16-to-17-by-local-authority/2024-25>
- **Native geography:** UTLA25 · **period:** End of 2024 (December 2024 to February 2025 average) · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_neet_16_17_2024_25`: Participation in education, training and NEET age 16 to 17 by local authority, 2024/25: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/f4ab16e8-ded3-4af3-4130-08dd91389bd2/files?fromPage=ReleaseDownloads>
- **Disclosure control:** suppression, rounding; tolerance 10 / 0.005. NEET data guidance: indicators on a cohort of 5 or fewer suppressed ('c'); national and regional numbers rounded to the nearest 10.
- **Symbols:** `c` = Suppressed to avoid disclosure (cohort of 5 or less) → `suppressed`; `z` = Not applicable → `not_applicable`
- **Decisions:** D-0095

#### E6: Schools, pupils and their characteristics, January 2025 (FSM by pupil residence)

- **Publisher:** Department for Education · <https://explore-education-statistics.service.gov.uk/find-statistics/school-pupils-and-their-characteristics/2024-25>
- **Native geography:** UTLA25 · **period:** January 2025 school census · **target:** `fact_service_area`
- **Staging code:** `stage/ees.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `ees_spc_2024_25`: Schools, pupils and their characteristics, 2024/25: all release files (EES zip) · <https://content.explore-education-statistics.service.gov.uk/api/releases/63491b17-2037-4533-b719-d3656aaf6ed5/files?fromPage=ReleaseDownloads>
- **Disclosure control:** none; tolerance 0 / 0.001. School census (SPC) data guidance: no suppression or rounding applied; 'x' not applicable, 'z' unknown. Checked: LA sums equal the published England figures exactly.
- **Symbols:** `x` = Not applicable (SPC convention) → `not_applicable`; `z` = Unknown (SPC convention) → `not_published`
- **Decisions:** D-0054, D-0094, D-0095

#### H1: Mental Health Services Monthly Statistics (MHSDS), March 2025 performance

- **Publisher:** NHS England · <https://digital.nhs.uk/data-and-information/publications/statistical/mental-health-services-monthly-statistics>
- **Native geography:** SICBL24 · **period:** March 2025 performance (rolling 12 months where applicable) · **target:** `fact_other_geography`
- **Staging code:** `stage/phase4.py` · **harmonise code:** `harmonise/phase4.py (mhsds)`
- **Files:**
  - `mhsds_final_202503`: MHSDS Monthly: End of Year Final March 2025 data file · <https://files.digital.nhs.uk/00/FE4D2C/MHSDS%20Data_MarFinal__2025.zip>
- **Disclosure control:** rounding, suppression; tolerance 5 / 0.01. MHSDS: '*' marks a suppressed small value; Sub-ICB and provider figures rounded to the nearest 5, England unrounded.
- **Symbols:** `*` = Suppressed (small number) → `suppressed`
- **Decisions:** D-0069, D-0070, D-0095

#### H2: Fingertips: Child and Maternal Health profile (API)

- **Publisher:** Office for Health Improvement and Disparities · <https://fingertips.phe.org.uk/api>
- **Native geography:** UTLA25 · **period:** Latest period ending on or before 31 March 2025 · **target:** `fact_service_area`
- **Staging code:** `stage/fingertips.py` · **harmonise code:** `harmonise/phase3.py (fingertips)`
- **Files:**
  - `fingertips_h2_utla502`: Fingertips all-data CSV for the six H2 indicators, upper-tier LAs (area type 502) and England · <https://fingertips.phe.org.uk/api/all_data/csv/by_indicator_id?indicator_ids=90813,93930,92196,20401,20101,90284&child_area_type_id=502&parent_area_type_id=15>
- **Disclosure control:** suppression; tolerance 0 / 0.001. Fingertips: no symbols; a missing value carries a 'Value note' (suppressed small count, combined area, not presented), mapped to null_reason.
- **Decisions:** D-0054, D-0063, D-0095

#### H3: NDTMS: adults in treatment who live with or are parents of children

- **Publisher:** Office for Health Improvement and Disparities · <https://www.ndtms.net/ParentsAndCarers>
- **Native geography:** UTLA25 · **period:** 2024-25 · **target:** `fact_service_area`
- **Staging code:** `—` · **harmonise code:** `not loaded (D-0091)`
- **Disclosure control:** suppression, rounding; tolerance 5 / 0.01. Not loaded (D-0091): disclosure control not assessed.
- **Decisions:** D-0054, D-0055, D-0090, D-0091, D-0094, D-0095

#### Ho1: Statutory homelessness in England: detailed local authority tables (H-CLIC)

- **Publisher:** Ministry of Housing, Communities and Local Government · <https://www.gov.uk/government/statistics/statutory-homelessness-in-england-october-to-december-2025/statutory-homelessness-in-england-quarterly-technical-note>
- **Native geography:** LAD25 · **period:** Snapshot 31 March 2025 (TA); financial year 2024-25 (duties) · **target:** `fact_lad`
- **Staging code:** `stage/sheets.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `hclic_detailed_la_202503`: Statutory homelessness: detailed local authority tables, January to March 2025 · <https://assets.publishing.service.gov.uk/media/687e2060791bb4d8c309a01a/Detailed_LA_202503.ods>
  - `hclic_additional_ta_202503`: Statutory homelessness: additional temporary accommodation tables, January to March 2025 · <https://assets.publishing.service.gov.uk/media/688b288b1affbf4bedb7b125/Additional_TA_202503.ods>
  - `hclic_annual_la_2024_25`: Statutory homelessness: detailed local authority data, financial year 2024-25 (corrected) · <https://assets.publishing.service.gov.uk/media/6a2ff87cd95ffddb05d4b063/Statutory_Homelessness_Detailed_Local_Authority_Data_2024-2025_corrected.ods>
- **Disclosure control:** suppression, imputation; tolerance 0 / 0.05. H-CLIC table footnotes: '..' authority did not submit; '-' breakdown suppressed (fewer than 5); England and regional totals include MHCLG estimates for non-responding authorities, so LA sums fall short of them.
- **Symbols:** `..` = Authority with missing data (not submitted) → `not_published`; `-` = Breakdown suppressed: fewer than 5 → `suppressed` (hides ≤ 4)
- **Decisions:** D-0054, D-0095

#### S1: data.police.uk street-level crime, April 2024 to March 2025

- **Publisher:** Home Office / police forces (data.police.uk) · <https://data.police.uk/data/>
- **Native geography:** point · **period:** FY 2024/25 · **target:** `fact_small_area`
- **Staging code:** `stage/police.py` · **harmonise code:** `harmonise/phase2.py (police, T4) in a child process (harmonise/isolated.py)`
- **Files:**
  - `police_archive_2026_08`: data.police.uk bulk archive 2026-08 (36 months to August 2026, all forces) · <https://data.police.uk/data/archive/2026-08.zip>
- **Disclosure control:** location_anonymisation; tolerance 0 / 0. data.police.uk: record-level counts with no suppression; points are snapped to anonymous map points, which affects location, not counts. Checked: published LSOA code agrees with point-in-polygon for 96.5% of England records (T4).
- **Decisions:** D-0015, D-0076

#### S3: Youth justice statistics 2024 to 2025

- **Publisher:** Youth Justice Board / Ministry of Justice · <https://www.gov.uk/government/statistics/youth-justice-statistics-2024-to-2025>
- **Native geography:** YJS · **period:** Year ending March 2025 · **target:** `fact_other_geography`
- **Staging code:** `stage/phase4.py` · **harmonise code:** `harmonise/phase4.py (youth_justice, fte)`
- **Files:**
  - `yj_local_open_data_2024_25`: Youth justice statistics 2024 to 2025: local level open data tables · <https://assets.publishing.service.gov.uk/media/6984756b7da3dc19896c7dc4/Local_level_open_data_tables.zip>
  - `yj_supplementary_2024_25`: Youth justice statistics 2024 to 2025: supplementary tables · <https://assets.publishing.service.gov.uk/media/6981c8d2e8900d4c455f3730/Youth_Justice_Statistics_2024_to_2025_supplementary_tables.zip>
- **Disclosure control:** suppression; tolerance 0 / 0.005. YJB/MoJ supplementary tables: '..' fewer than ten first-time entrants (suppressed); '*' LA boundary change. Open data tables have no symbols.
- **Symbols:** `..` = Fewer than ten first-time entrants (suppressed) → `suppressed` (hides ≤ 9); `*` = Local authority boundary change; no figure on current boundaries → `not_published`
- **Decisions:** D-0069, D-0095

#### S4: National Referral Mechanism and Duty to Notify statistics

- **Publisher:** Home Office · <https://www.gov.uk/government/collections/national-referral-mechanism-statistics>
- **Native geography:** UTLA25 · **period:** April 2024 - March 2025 · **target:** `fact_service_area or fact_other_geography (per verified geography)`
- **Staging code:** `stage/phase4.py` · **harmonise code:** `harmonise/phase4.py (nrm)`
- **Files:**
  - `nrm_tables_2024q2`: Modern slavery: NRM and DtN statistics, April to June 2024: data tables · <https://assets.publishing.service.gov.uk/media/66b37f6da3c2a28abb50de5e/national-referral-mechanism-statistics-uk-quarter-2-2024-apr-to-jun-tables.ods>
  - `nrm_tables_2024q3`: Modern slavery: NRM and DtN statistics, July to September 2024: data tables · <https://assets.publishing.service.gov.uk/media/672b9c4b094e4e60c466d257/national-referral-mechanism-statistics-uk-quarter-3-2024-jul-to-sep-tables.ods>
  - `nrm_tables_2024q4`: Modern slavery: NRM and DtN statistics, October to December 2024: data tables · <https://assets.publishing.service.gov.uk/media/67c5901cb0bb6528ee866ce1/national-referral-mechanism-statistics-uk-quarter-4-2024-oct-to-dec-tables.ods>
  - `nrm_tables_2025q1`: Modern slavery: NRM and DtN statistics, January to March 2025: data tables · <https://assets.publishing.service.gov.uk/media/681b6ba53f1c73824ee3e523/national-referral-mechanism-statistics-uk-quarter-1-2025-jan-to-mar-tables.ods>
- **Disclosure control:** none; tolerance 0 / 0.01. NRM quarterly tables: whole numbers, no symbols. Checked: police force rows sum to the published UK total in every quarter.
- **Decisions:** D-0069, D-0094, D-0095

#### S5: Asylum support by local authority (Home Office immigration statistics)

- **Publisher:** Home Office · <https://www.gov.uk/government/statistical-data-sets/immigration-system-statistics-data-tables>
- **Native geography:** LAD25 · **period:** At 31 March 2025 · **target:** `fact_lad / fact_service_area (per published level)`
- **Staging code:** `stage/sheets.py` · **harmonise code:** `harmonise/phase3.py (tables)`
- **Files:**
  - `asy_d11_la_jun_2026`: Home Office immigration system statistics: asylum support local authority datasets, year ending June 2026 edition · <https://assets.publishing.service.gov.uk/media/6a85c5e654bcee010d514574/support-local-authority-datasets-jun-2026.xlsx>
- **Disclosure control:** none; tolerance 0 / 0.01. Asy_D11: counts of people, no symbols. Checked: England LA rows sum to the published English regional totals exactly (D-0084).
- **Decisions:** D-0054, D-0094, D-0095

### 5. Indicators

Each indicator's definition, formula, transformation configuration (the exact entry in
`config/category_maps.yaml`, or the code that builds it) and the decisions that shaped it.

#### Theme: population

##### `ons_sape_population`: Population

- **Sources:** P1 · **measure:** count · **native level:** small_area · **polarity:** neutral
- **Value:** ONS mid-year Small Area Population Estimates for LSOA21, single year of age (0 to 90+) by sex. · CI: none · aggregation: sum
- **Built in code:** harmonise/population.py: ONS SAPE single years of age by sex, LSOA (P1); MSOA by exact sum

##### `ons_mye_population`: Population

- **Sources:** P1b · **measure:** count · **native level:** lad · **polarity:** neutral
- **Value:** ONS mid-year population estimates, single year of age (0 to 90+) by sex, as published for LAD, UTLA and England. · CI: none · aggregation: sum
- **Built in code:** harmonise/population.py: ONS mid-year estimates by single year and sex, LAD/UTLA/England (P1b)

##### `census21_population_by_ethnicity`: Population by ethnic group (Census 2021)

- **Sources:** P4 · **measure:** count · **native level:** small_area · **polarity:** neutral
- **Value:** Census 2021 usual residents by ethnic group (most detailed classification ONS releases for LSOA x age) and age. · CI: none · aggregation: sum
- **Map entry** `census.P4`:

```yaml
file_prefix: p4_eth6a_age7a
table: ethnic_group_tb_6a x resident_age_7a
ethnicity_dim: dim1
age_dim: dim2
age_map: CENSUS_AGE_7A
indicator: census21_population_by_ethnicity
```

##### `census21_usual_residents_by_age`: Population (Census 2021)

- **Sources:** F7 · **measure:** count · **native level:** small_area · **polarity:** neutral
- **Value:** Total usual residents by age, taken from the same Census custom tables as the disability and unpaid care counts. · CI: none · aggregation: sum
- **Map entry** `census.F7a.indicators.census21_usual_residents_by_age`:

```yaml
- age_band: '0_24'
  dim1:
  - '1'
  - '2'
  - '3'
  - '4'
  dim2:
  - '1'
  - '2'
  - '3'
  - '4'
  - '5'
```
- **Map entry** `census.F7b.indicators.census21_usual_residents_by_age`:

```yaml
- age_band: src_5_24
  dim1:
  - '1'
  - '2'
  - '3'
  - '4'
  - '5'
  - '6'
  dim2:
  - '1'
```

##### `nhse_gp_registered_patients`: GP-registered population

- **Sources:** G3b · **measure:** count · **native level:** SICBL24 · **polarity:** neutral
- **Value:** Patients registered at GP practices in England on 1 April 2025, by Sub-ICB location (April 2024 configuration), single year of age (0 to 95+, stored to 90+) and sex, as published by NHS England. · CI: none · aggregation: sum
- **Built in code:** harmonise/phase4.py (gp_registered): G3b single years by Sub-ICB; England as the sum
- **Decisions:** D-0070

##### `dfe_pupils_by_ethnicity`: Pupils by ethnic group

- **Sources:** P7 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Headcount of pupils in state-funded schools by ethnicity (DfE classification), January 2025. · CI: none · aggregation: sum
- **Map entry** `tables.P7.measures[0]`:

```yaml
indicator: dfe_pupils_by_ethnicity
table: spc_pupils_ethnicity_and_language
column: headcount
where:
  phase_type_grouping: Total
  language: Total
age_band: src_pupils_all
period:
- 2025-01-16
- 2025-01-16
ethnicity:
  column: ethnicity_minor
  classification: dfe_ethnicity
```

##### `dfe_pupils_on_roll`: Pupils

- **Sources:** E6 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Number of pupils used for FSM in performance tables, by LA of school, January 2025 school census (SPC table spc_pupils_fsm). · CI: none · aggregation: sum
- **Map entry** `tables.E6.measures[0]`:

```yaml
indicator: dfe_pupils_on_roll
table: spc_pupils_fsm
column: headcount
where:
  phase_type_grouping: Total
  fsm: number of pupils (used for FSM in Performance Tables)
age_band: src_pupils_all
period:
- 2025-01-16
- 2025-01-16
```
- **Decisions:** D-0058

##### `mhclg_iod25_population`: Population used in the IoD 2025

- **Sources:** D1 · **measure:** count · **native level:** small_area · **polarity:** neutral
- **Value:** Population denominators published with IoD 2025, by LSOA (total, and the child and older-people bases where published). · CI: none · aggregation: sum
- **Map entry** `iod_lsoa[21]`:

```yaml
indicator: mhclg_iod25_population
kind: count
column: 'Total population: mid 2022'
age_band: all_ages
period: population
```
- **Map entry** `iod_lsoa[22]`:

```yaml
indicator: mhclg_iod25_population
kind: count
column: 'Dependent Children aged 0-15: mid 2022'
age_band: src_0_15
period: population
```

##### `census21_households_dependent_children`: Households with dependent children

- **Sources:** F6 · **measure:** count · **native level:** small_area · **polarity:** neutral
- **Value:** Census 2021 households containing at least one dependent child (aged 0-15, or 16-18 in full-time education and living with parent(s)). · CI: none · aggregation: sum
- **Map entry** `census.F6.indicators.census21_households_dependent_children`:

```yaml
- age_band: na
  dim1:
  - '5'
  - '8'
  - '10'
  - '13'
  dim2:
  - '1'
  - '2'
  - '3'
  - '4'
```

##### `dfe_cin_episodes_with_assessment_factors`: Assessments with factors recorded

- **Sources:** C1 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Episodes with an assessment completed in the year that have assessment factor information (Episodes_with_assessment_factor), DfE CIN table C3. · CI: none · aggregation: sum
- **Map entry** `tables.C1.measures[6]`:

```yaml
indicator: dfe_cin_episodes_with_assessment_factors
table: c3_factors_identified
column: Episodes_with_assessment_factor
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```
- **Decisions:** D-0056

##### `dfe_cla_distance_known_at_31mar`: Children in care (distance known)

- **Sources:** C2 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** CLA at 31 March 2025 placed 20 miles or less from home + placed more than 20 miles from home (two published cells of one DfE table). · CI: none · aggregation: sum
- **Map entry** `tables.C2.measures[5]`:

```yaml
indicator: dfe_cla_distance_known_at_31mar
table: la_cla_on_31_march_by_characteristics
column: children_count
sum_rows: true
where:
  characteristic: Distance between home and placement
  breakdown:
  - Placed 20 miles or less from home
  - Placed more than 20 miles from home
age_band: '0_17'
period:
- 2025-03-31
- 2025-03-31
```
- **Decisions:** D-0057

##### `dfe_cla_stability_base_at_31mar`: Children in care (stability base)

- **Sources:** C2 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** 'Total children' for 'CLA on 31 March' in DfE table LA_CLA_placement_stability, 2025. · CI: none · aggregation: sum
- **Map entry** `tables.C2.measures[7]`:

```yaml
indicator: dfe_cla_stability_base_at_31mar
table: LA_CLA_placement_stability
column: children_count
where:
  cla_group: CLA on 31 March
  placement_stability: Total children
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```
- **Decisions:** D-0057

##### `dfe_pupils_total_sen_publication`: Pupils (SEN publication)

- **Sources:** E1 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Total pupils (phase Total, SEN status Total, primary need Total) in SEN in England table sen_ncyear_, January 2025: the same table as every SEN numerator. · CI: none · aggregation: sum
- **Map entry** `tables.E1.measures[0]`:

```yaml
indicator: dfe_pupils_total_sen_publication
table: sen_ncyear_
column: number_of_pupils
where:
  phase_type_grouping: Total
  sen_status: Total
  sen_primary_need: Total
age_band: src_pupils_all
period:
- 2025-01-16
- 2025-01-16
```

##### `dfe_absence_enrolments`: Pupil enrolments

- **Sources:** E3 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Pupil enrolments, academic year 2024/25, as published in the absence statistics. · CI: none · aggregation: sum
- **Map entry** `tables.E3.measures[0]`:

```yaml
indicator: dfe_absence_enrolments
table: 1_Absence_3term_nat_reg_la
column: enrolments
where:
  education_phase: Total
age_band: src_pupils_all
period:
- 2024-09-01
- 2025-07-31
```

##### `dfe_exclusions_headcount`: Pupils (exclusions publication)

- **Sources:** E4 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Pupil headcount as published in the suspensions and exclusions statistics. · CI: none · aggregation: sum
- **Map entry** `tables.E4.measures[0]`:

```yaml
indicator: dfe_exclusions_headcount
table: exc_nat_region_la
column: headcount
where:
  education_phase: Total
age_band: src_pupils_all
period:
- 2024-09-01
- 2025-07-31
```

##### `dfe_neet_cohort_16_17`: 16-17 year olds known to the council

- **Sources:** E5 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** 16-17 year olds known to the LA (resident), average of December 2024 to February 2025, as published (avgcohort). · CI: none · aggregation: none
- **Map entry** `tables.E5.measures[0]`:

```yaml
indicator: dfe_neet_cohort_16_17
table: ud_neet_characteristics
column: avgcohort
kind: value
where:
  Age: 16-17
  Characteristic_grouping: Total
  Characteristic: Total
age_band: '16_17'
period:
- 2024-12-01
- 2025-02-28
```
- **Decisions:** D-0067

##### `ho_asylum_support_recipients`: People receiving asylum support

- **Sources:** S5 · **measure:** count · **native level:** lad · **polarity:** neutral
- **Value:** People in receipt of asylum support (by support type) at 31 March 2025, by LA. · CI: none · aggregation: sum
- **Map entry** `tables.S5.measures[0]`:

```yaml
indicator: ho_asylum_support_recipients
table: asy_d11_20250331
column: People
sum_rows: true
age_band: all_ages
period:
- 2025-03-31
- 2025-03-31
absent_areas_zero:
  table: asy_d11_regions
  label: Row Labels
  column: 31 Mar 2025
  england:
  - East Midlands
  - East of England
  - London
  - North East
  - North West
  - South East
  - South West
  - West Midlands
  - Yorkshire and The Humber
  zero:
  - N/A - Subsistence Only (Dec 2023 - Dec 2024)
```
- **Decisions:** D-0084

#### Theme: deprivation

##### `mhclg_iod25_imd_score`: Index of Multiple Deprivation (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IMD 2025 score for LSOA21: weighted combination of seven exponentially transformed domain scores (MHCLG method). · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[0]`:

```yaml
indicator: mhclg_iod25_imd_score
kind: value
column: Index of Multiple Deprivation (IMD) Score
```

##### `mhclg_iod25_imd_rank`: Index of Multiple Deprivation (rank)

- **Sources:** D1 · **measure:** rank · **native level:** small_area · **polarity:** higher_better
- **Value:** IMD 2025 rank of LSOA21 among all English LSOAs (1 = most deprived). · CI: none · aggregation: none
- **Map entry** `iod_lsoa[1]`:

```yaml
indicator: mhclg_iod25_imd_rank
kind: value
column: Index of Multiple Deprivation (IMD) Rank (where 1 is most deprived)
```

##### `mhclg_iod25_imd_decile`: Index of Multiple Deprivation (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IMD 2025 decile of LSOA21 (1 = most deprived 10% of LSOAs nationally). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[2]`:

```yaml
indicator: mhclg_iod25_imd_decile
kind: value
column: Index of Multiple Deprivation (IMD) Decile (where 1 is most deprived 10% of LSOAs)
```

##### `mhclg_iod25_income_score`: Income deprivation (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD 2025 Income Deprivation domain score: proportion of the population experiencing income deprivation. · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[3]`:

```yaml
indicator: mhclg_iod25_income_score
kind: value
column: Income Score (rate)
```

##### `mhclg_iod25_income_decile`: Income deprivation (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IoD 2025 Income domain decile (1 = most deprived 10%). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[4]`:

```yaml
indicator: mhclg_iod25_income_decile
kind: value
column: Income Decile (where 1 is most deprived 10% of LSOAs)
```

##### `mhclg_iod25_employment_score`: Employment deprivation (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD 2025 Employment Deprivation domain score: proportion of the working-age population involuntarily excluded from the labour market. · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[5]`:

```yaml
indicator: mhclg_iod25_employment_score
kind: value
column: Employment Score (rate)
```

##### `mhclg_iod25_employment_decile`: Employment deprivation (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IoD 2025 Employment domain decile (1 = most deprived 10%). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[6]`:

```yaml
indicator: mhclg_iod25_employment_decile
kind: value
column: Employment Decile (where 1 is most deprived 10% of LSOAs)
```

##### `mhclg_iod25_education_score`: Education, skills and training deprivation (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD 2025 Education, Skills and Training Deprivation domain score (children and young people sub-domain plus adult skills sub-domain). · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[7]`:

```yaml
indicator: mhclg_iod25_education_score
kind: value
column: Education, Skills and Training Score
```

##### `mhclg_iod25_education_decile`: Education, skills and training deprivation (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IoD 2025 Education, Skills and Training domain decile (1 = most deprived 10%). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[8]`:

```yaml
indicator: mhclg_iod25_education_decile
kind: value
column: Education, Skills and Training Decile (where 1 is most deprived 10% of LSOAs)
```

##### `mhclg_iod25_health_score`: Health deprivation and disability (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD 2025 Health Deprivation and Disability domain score. · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[9]`:

```yaml
indicator: mhclg_iod25_health_score
kind: value
column: Health Deprivation and Disability Score
```

##### `mhclg_iod25_health_decile`: Health deprivation and disability (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IoD 2025 Health Deprivation and Disability domain decile (1 = most deprived 10%). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[10]`:

```yaml
indicator: mhclg_iod25_health_decile
kind: value
column: Health Deprivation and Disability Decile (where 1 is most deprived 10% of LSOAs)
```

##### `mhclg_iod25_crime_score`: Crime deprivation (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD 2025 Crime domain score (recorded violence, burglary, theft and criminal damage, modelled). · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[11]`:

```yaml
indicator: mhclg_iod25_crime_score
kind: value
column: Crime Score
```

##### `mhclg_iod25_crime_decile`: Crime deprivation (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IoD 2025 Crime domain decile (1 = most deprived 10%). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[12]`:

```yaml
indicator: mhclg_iod25_crime_decile
kind: value
column: Crime Decile (where 1 is most deprived 10% of LSOAs)
```

##### `mhclg_iod25_barriers_score`: Barriers to housing and services (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD 2025 Barriers to Housing and Services domain score (geographical barriers and wider barriers sub-domains). · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[13]`:

```yaml
indicator: mhclg_iod25_barriers_score
kind: value
column: Barriers to Housing and Services Score
```

##### `mhclg_iod25_barriers_decile`: Barriers to housing and services (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IoD 2025 Barriers domain decile (1 = most deprived 10%). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[14]`:

```yaml
indicator: mhclg_iod25_barriers_decile
kind: value
column: Barriers to Housing and Services Decile (where 1 is most deprived 10% of LSOAs)
```

##### `mhclg_iod25_living_env_score`: Living environment deprivation (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD 2025 Living Environment Deprivation domain score (indoors and outdoors sub-domains). · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[15]`:

```yaml
indicator: mhclg_iod25_living_env_score
kind: value
column: Living Environment Score
```

##### `mhclg_iod25_living_env_decile`: Living environment deprivation (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IoD 2025 Living Environment domain decile (1 = most deprived 10%). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[16]`:

```yaml
indicator: mhclg_iod25_living_env_decile
kind: value
column: Living Environment Decile (where 1 is most deprived 10% of LSOAs)
```

##### `mhclg_iod25_imd_la_avg_score`: Index of Multiple Deprivation: average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IMD 2025 LSOA scores, as published by MHCLG for LAD and UTLA. · CI: none · aggregation: none
- **Map entry** `iod_la[0]`:

```yaml
indicator: mhclg_iod25_imd_la_avg_score
sheet: IMD
measure: IMD - Average score
```

##### `mhclg_iod25_imd_la_avg_rank`: Index of Multiple Deprivation: average rank

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IMD 2025 LSOA ranks, as published by MHCLG (IoD 2025 File 10/11; higher = more deprived, verified on inspection, D-0044). · CI: none · aggregation: none
- **Map entry** `iod_la[1]`:

```yaml
indicator: mhclg_iod25_imd_la_avg_rank
sheet: IMD
measure: IMD - Average rank
```

##### `mhclg_iod25_imd_la_extent`: Index of Multiple Deprivation: extent

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** MHCLG extent measure: proportion of the LA population living in the most deprived LSOAs nationally (weighted, top 30%). · CI: none · aggregation: none
- **Map entry** `iod_la[2]`:

```yaml
indicator: mhclg_iod25_imd_la_extent
sheet: IMD
measure: IMD25 - Extent
```

##### `mhclg_iod25_imd_la_local_concentration`: Index of Multiple Deprivation: local concentration

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average rank of the LA's most deprived LSOAs containing 10% of its population (MHCLG; higher = more deprived in IoD 2025, D-0044). · CI: none · aggregation: none
- **Map entry** `iod_la[3]`:

```yaml
indicator: mhclg_iod25_imd_la_local_concentration
sheet: IMD
measure: IMD25 - Local concentration
```

##### `mhclg_iod25_imd_la_prop_most_deprived_10pct`: Neighbourhoods in England's most deprived 10%

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in IMD 2025 decile 1, as published by MHCLG. · CI: none · aggregation: none
- **Map entry** `iod_la[4]`:

```yaml
indicator: mhclg_iod25_imd_la_prop_most_deprived_10pct
sheet: IMD
measure: IMD - Proportion of LSOAs in most deprived 10% nationally
```

##### `mhclg_iod25_income_la_avg_score`: Income deprivation: average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IoD 2025 Income domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[8]`:

```yaml
indicator: mhclg_iod25_income_la_avg_score
sheet: Income
measure: Income - Average score
```

##### `mhclg_iod25_income_la_prop_most_deprived_10pct`: Income deprivation: neighbourhoods in England's most deprived 10%

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Income domain, as published by MHCLG (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[9]`:

```yaml
indicator: mhclg_iod25_income_la_prop_most_deprived_10pct
sheet: Income
measure: Income - Proportion of LSOAs in most deprived 10% nationally
```

##### `mhclg_iod25_employment_la_avg_score`: Employment deprivation: average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IoD 2025 Employment domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[10]`:

```yaml
indicator: mhclg_iod25_employment_la_avg_score
sheet: Employment
measure: Employment - Average score
```

##### `mhclg_iod25_employment_la_prop_most_deprived_10pct`: Employment deprivation: neighbourhoods in England's most deprived 10%

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Employment domain, as published by MHCLG (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[11]`:

```yaml
indicator: mhclg_iod25_employment_la_prop_most_deprived_10pct
sheet: Employment
measure: Employment - Proportion of LSOAs in most deprived 10% nationally
```

##### `mhclg_iod25_education_la_avg_score`: Education, skills and training deprivation: average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IoD 2025 Education, Skills and Training domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[12]`:

```yaml
indicator: mhclg_iod25_education_la_avg_score
sheet: Education
measure: Education, Skills and Training - Average score
```

##### `mhclg_iod25_education_la_prop_most_deprived_10pct`: Education, skills and training deprivation: neighbourhoods in England's most deprived 10%

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Education, Skills and Training domain, as published by MHCLG (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[13]`:

```yaml
indicator: mhclg_iod25_education_la_prop_most_deprived_10pct
sheet: Education
measure: Education, Skills and Training - Proportion of LSOAs in most deprived 10% nationally
```

##### `mhclg_iod25_health_la_avg_score`: Health deprivation and disability: average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IoD 2025 Health Deprivation and Disability domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[14]`:

```yaml
indicator: mhclg_iod25_health_la_avg_score
sheet: Health
measure: Health Deprivation and Disability - Average score
```

##### `mhclg_iod25_health_la_prop_most_deprived_10pct`: Health deprivation and disability: neighbourhoods in England's most deprived 10%

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Health Deprivation and Disability domain, as published by MHCLG (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[15]`:

```yaml
indicator: mhclg_iod25_health_la_prop_most_deprived_10pct
sheet: Health
measure: Health Deprivation and Disability - Proportion of LSOAs in most deprived 10% nationally
```

##### `mhclg_iod25_crime_la_avg_score`: Crime (IoD domain): average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IoD 2025 Crime domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[16]`:

```yaml
indicator: mhclg_iod25_crime_la_avg_score
sheet: Crime
measure: Crime - Average score
```

##### `mhclg_iod25_crime_la_prop_most_deprived_10pct`: Crime (IoD domain): neighbourhoods in England's most deprived 10%

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Crime domain, as published by MHCLG (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[17]`:

```yaml
indicator: mhclg_iod25_crime_la_prop_most_deprived_10pct
sheet: Crime
measure: Crime - Proportion of LSOAs in most deprived 10% nationally
```

##### `mhclg_iod25_barriers_la_avg_score`: Barriers to housing and services: average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IoD 2025 Barriers to Housing and Services domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[18]`:

```yaml
indicator: mhclg_iod25_barriers_la_avg_score
sheet: Barriers
measure: Barriers to Housing and Services - Average score
```

##### `mhclg_iod25_barriers_la_prop_most_deprived_10pct`: Barriers to housing and services: neighbourhoods in England's most deprived 10%

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Barriers to Housing and Services domain, as published by MHCLG (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[19]`:

```yaml
indicator: mhclg_iod25_barriers_la_prop_most_deprived_10pct
sheet: Barriers
measure: Barriers to Housing and Services - Proportion of LSOAs in most deprived 10% nationally
```

##### `mhclg_iod25_living_env_la_avg_score`: Living environment deprivation: average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IoD 2025 Living Environment domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[20]`:

```yaml
indicator: mhclg_iod25_living_env_la_avg_score
sheet: Living
measure: Living Environment - Average score
```

##### `mhclg_iod25_living_env_la_prop_most_deprived_10pct`: Living environment deprivation: neighbourhoods in England's most deprived 10%

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Living Environment domain, as published by MHCLG (Files 10 and 11). · CI: none · aggregation: none
- **Map entry** `iod_la[21]`:

```yaml
indicator: mhclg_iod25_living_env_la_prop_most_deprived_10pct
sheet: Living
measure: Living Environment - Proportion of LSOAs in most deprived 10% nationally
```

#### Theme: child poverty

##### `mhclg_iod25_idaci_score`: Income deprivation affecting children (IDACI)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IDACI 2025 score: proportion of children aged 0-15 living in income-deprived families (MHCLG definition, benefit and tax credit based). · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[17]`:

```yaml
indicator: mhclg_iod25_idaci_score
kind: value
column: Income Deprivation Affecting Children Index (IDACI) Score (rate)
age_band: src_0_15
```

##### `mhclg_iod25_idaci_rank`: Income deprivation affecting children (rank)

- **Sources:** D1 · **measure:** rank · **native level:** small_area · **polarity:** higher_better
- **Value:** IDACI 2025 rank of LSOA21 (1 = most deprived). · CI: none · aggregation: none
- **Map entry** `iod_lsoa[18]`:

```yaml
indicator: mhclg_iod25_idaci_rank
kind: value
column: Income Deprivation Affecting Children Index (IDACI) Rank (where 1 is most deprived)
age_band: src_0_15
```

##### `mhclg_iod25_idaci_decile`: Income deprivation affecting children (decile)

- **Sources:** D1 · **measure:** decile · **native level:** small_area · **polarity:** higher_better
- **Value:** IDACI 2025 decile of LSOA21 (1 = most deprived 10%). · CI: none · aggregation: share_in_decile
- **Map entry** `iod_lsoa[19]`:

```yaml
indicator: mhclg_iod25_idaci_decile
kind: value
column: Income Deprivation Affecting Children Index (IDACI) Decile (where 1 is most deprived 10% of LSOAs)
age_band: src_0_15
```

##### `mhclg_iod25_idaci_la_avg_score`: Income deprivation affecting children: average score

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IDACI 2025 LSOA scores, as published by MHCLG. · CI: none · aggregation: none
- **Map entry** `iod_la[5]`:

```yaml
indicator: mhclg_iod25_idaci_la_avg_score
sheet: IDACI
measure: IDACI - Average score
age_band: src_0_15
```

##### `mhclg_iod25_idaci_la_avg_rank`: Income deprivation affecting children: average rank

- **Sources:** D1b · **measure:** score · **native level:** lad · **polarity:** higher_worse
- **Value:** Population-weighted average of IDACI 2025 LSOA ranks, as published by MHCLG (higher = more deprived in IoD 2025, D-0044). · CI: none · aggregation: none
- **Map entry** `iod_la[6]`:

```yaml
indicator: mhclg_iod25_idaci_la_avg_rank
sheet: IDACI
measure: IDACI - Average rank
age_band: src_0_15
```

##### `mhclg_iod25_idaci_la_prop_most_deprived_10pct`: Neighbourhoods in England's most deprived 10% for child income

- **Sources:** D1b · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Proportion of the LA's LSOAs in IDACI 2025 decile 1, as published by MHCLG. · CI: none · aggregation: none
- **Map entry** `iod_la[7]`:

```yaml
indicator: mhclg_iod25_idaci_la_prop_most_deprived_10pct
sheet: IDACI
measure: IDACI - Proportion of LSOAs in most deprived 10% nationally
age_band: src_0_15
```

##### `dwp_cilif_relative_bhc`: Children in relative low income families

- **Sources:** F1 · **measure:** count · **native level:** lad · **polarity:** higher_worse
- **Value:** DWP CiLIF: children (under 16, or 16-19 in non-advanced education) in families with equivalised household income below 60% of contemporary median, BHC, calibrated to the national survey (HBAI). · CI: none · aggregation: sum
- **Map entry** `statxplore.F1[0]`:

```yaml
file_prefix: f1_cilif_rel
indicator: dwp_cilif_relative_bhc
age_field: Age of Child (years and bands)
age_map: F1
```
- **Map entry** `tables.F1.measures[0]`:

```yaml
indicator: dwp_cilif_relative_bhc
table: cilif_bhc_la
column: relative_count
age_band: src_0_15
period:
- 2024-04-01
- 2025-03-31
```

##### `dwp_cilif_relative_bhc_pct`: Children in relative low income families (%)

- **Sources:** F1 · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Percentage as published by DWP: children aged 0-15 in relative low income families / ONS mid-2024 population aged 0-15 x 100 (DWP CiLIF note 3). DWP publishes it for lower-tier and unitary councils; for the 21 county councils it is computed by DWP's method from the summed district counts (D-0085). · CI: none · aggregation: none
- **Publisher's method (L3):** where no value is published, `dwp_cilif_relative_bhc` (src_0_15) ÷ `ons_mye_population` × 100, only after this reproduces every published value (D-0085)
- **Map entry** `tables.F1.measures[1]`:

```yaml
indicator: dwp_cilif_relative_bhc_pct
table: cilif_bhc_la
column: relative_pct
kind: value
scale: 100
age_band: src_0_15
period:
- 2024-04-01
- 2025-03-31
```

##### `dwp_cilif_absolute_bhc`: Children in absolute low income families

- **Sources:** F1 · **measure:** count · **native level:** lad · **polarity:** higher_worse
- **Value:** DWP CiLIF absolute low income, BHC: equivalised household income below 60% of the FYE 2025 median held constant in real terms, calibrated to HBAI. DWP moved the reference year from FYE 2011 to FYE 2025 in this release and revised the back series. · CI: none · aggregation: sum
- **Map entry** `statxplore.F1[1]`:

```yaml
file_prefix: f1_cilif_abs
indicator: dwp_cilif_absolute_bhc
age_field: Age of Child (years and bands)
age_map: F1
```
- **Map entry** `tables.F1.measures[2]`:

```yaml
indicator: dwp_cilif_absolute_bhc
table: cilif_bhc_la
column: absolute_count
age_band: src_0_15
period:
- 2024-04-01
- 2025-03-31
```

##### `dwp_cilif_absolute_bhc_pct`: Children in absolute low income families (%)

- **Sources:** F1 · **measure:** percent_published · **native level:** lad · **polarity:** higher_worse
- **Value:** Percentage as published by DWP alongside CiLIF counts. · CI: none · aggregation: none
- **Publisher's method (L3):** where no value is published, `dwp_cilif_absolute_bhc` (src_0_15) ÷ `ons_mye_population` × 100, only after this reproduces every published value (D-0085)
- **Map entry** `tables.F1.measures[3]`:

```yaml
indicator: dwp_cilif_absolute_bhc_pct
table: cilif_bhc_la
column: absolute_pct
kind: value
scale: 100
age_band: src_0_15
period:
- 2024-04-01
- 2025-03-31
```

##### `dwp_uc_households_with_children`: Households with children on Universal Credit

- **Sources:** F2 · **measure:** count · **native level:** small_area · **polarity:** higher_worse
- **Value:** Count of households on UC (payment) with at least one dependent child, by LSOA21, March 2025. · CI: none · aggregation: sum
- **Map entry** `statxplore.F2`:

```yaml
indicator: dwp_uc_households_with_children
age_band: na
```
- **Decisions:** D-0087

##### `dfe_fsm_eligible_pupils`: Pupils eligible for free school meals

- **Sources:** E6 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Pupils known to be eligible for free school meals ÷ `dfe_pupils_on_roll` (Pupils on roll used for FSM in performance tables (same table, same school-location basis)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.E6.measures[1]`:

```yaml
indicator: dfe_fsm_eligible_pupils
table: spc_pupils_fsm
column: headcount
where:
  phase_type_grouping: Total
  fsm: known to be eligible for free school meals (used for FSM in Performance Tables)
age_band: src_pupils_all
period:
- 2025-01-16
- 2025-01-16
```
- **Decisions:** D-0058

#### Theme: education

##### `mhclg_iod25_education_cyp_subdomain_score`: Children's education deprivation (score)

- **Sources:** D1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD 2025 Education domain, Children and Young People sub-domain score (attainment, absence, staying on, entry to higher education). · CI: none · aggregation: pop_weighted_mean
- **Map entry** `iod_lsoa[20]`:

```yaml
indicator: mhclg_iod25_education_cyp_subdomain_score
kind: value
column: Children and Young People Sub-domain Score
```

##### `dfe_care_leavers_19_21_neet`: Care leavers not in education, employment or training

- **Sources:** C2 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Care leavers 19-21 NEET ÷ `dfe_care_leavers_19_21` (Care leavers aged 19-21) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C2.measures[10]`:

```yaml
indicator: dfe_care_leavers_19_21_neet
table: la_care_leavers_activity
column: care_leaver_count
where:
  care_leaver_age: 19 to 21 years
  breakdown: Total not in education, employment or training
age_band: src_19_21
period:
- 2024-04-01
- 2025-03-31
```

##### `dfe_pupils_with_ehcp`: Pupils with an EHC plan

- **Sources:** E1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Pupils with EHC plan ÷ `dfe_pupils_total_sen_publication` (Total pupils (same file)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.E1.measures[1]`:

```yaml
indicator: dfe_pupils_with_ehcp
table: sen_ncyear_
column: number_of_pupils
where:
  phase_type_grouping: Total
  sen_status: Education, Health and Care plans
  sen_primary_need: Total
age_band: src_pupils_all
period:
- 2025-01-16
- 2025-01-16
```

##### `dfe_pupils_sen_support`: Pupils receiving SEN support

- **Sources:** E1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Pupils with SEN support ÷ `dfe_pupils_total_sen_publication` (Total pupils (same file)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.E1.measures[2]`:

```yaml
indicator: dfe_pupils_sen_support
table: sen_ncyear_
column: number_of_pupils
where:
  phase_type_grouping: Total
  sen_status: SEN support / SEN without an EHC plan
  sen_primary_need: Total
age_band: src_pupils_all
period:
- 2025-01-16
- 2025-01-16
```

##### `dfe_sen_primary_need_asd`: Pupils with autism as their main need

- **Sources:** E1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Pupils with SEN, primary need ASD ÷ `dfe_pupils_total_sen_publication` (Total pupils) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.E1.measures[4]`:

```yaml
indicator: dfe_sen_primary_need_asd
table: sen_ncyear_
column: number_of_pupils
where:
  phase_type_grouping: Total
  sen_status: Total
  sen_primary_need: Autistic Spectrum Disorder
age_band: src_pupils_all
period:
- 2025-01-16
- 2025-01-16
```

##### `dfe_persistent_absence`: Persistent absence from school

- **Sources:** E3 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Persistently absent enrolments ÷ `dfe_absence_enrolments` (Enrolments (same file)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.E3.measures[1]`:

```yaml
indicator: dfe_persistent_absence
table: 1_Absence_3term_nat_reg_la
column: enrolments_pa_10_exact
where:
  education_phase: Total
age_band: src_pupils_all
period:
- 2024-09-01
- 2025-07-31
```

##### `dfe_severe_absence`: Severe absence from school

- **Sources:** E3 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Severely absent enrolments ÷ `dfe_absence_enrolments` (Enrolments (same file)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.E3.measures[2]`:

```yaml
indicator: dfe_severe_absence
table: 1_Absence_3term_nat_reg_la
column: enrolments_pa_50_exact
where:
  education_phase: Total
age_band: src_pupils_all
period:
- 2024-09-01
- 2025-07-31
```

##### `dfe_suspensions`: Suspensions from school

- **Sources:** E4 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Suspensions ÷ `dfe_exclusions_headcount` (Pupil headcount (same file)) × 100; CI: byar; aggregation: sum_then_divide
- **Map entry** `tables.E4.measures[1]`:

```yaml
indicator: dfe_suspensions
table: exc_nat_region_la
column: suspension
where:
  education_phase: Total
age_band: src_pupils_all
period:
- 2024-09-01
- 2025-07-31
```

##### `dfe_permanent_exclusions`: Permanent exclusions from school

- **Sources:** E4 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Permanent exclusions ÷ `dfe_exclusions_headcount` (Pupil headcount (same file)) × 10000; CI: byar; aggregation: sum_then_divide
- **Map entry** `tables.E4.measures[2]`:

```yaml
indicator: dfe_permanent_exclusions
table: exc_nat_region_la
column: perm_excl
where:
  education_phase: Total
age_band: src_pupils_all
period:
- 2024-09-01
- 2025-07-31
```

##### `dfe_neet_16_17`: 16-17 year olds not in education, employment or training

- **Sources:** E5 · **measure:** percent_published · **native level:** service_area · **polarity:** higher_worse
- **Formula:** 16-17 NEET; CI: none; aggregation: none
- **Map entry** `tables.E5.measures[1]`:

```yaml
indicator: dfe_neet_16_17
table: ud_neet_characteristics
column: NEETprop
kind: value
where:
  Age: 16-17
  Characteristic_grouping: Total
  Characteristic: Total
age_band: '16_17'
period:
- 2024-12-01
- 2025-02-28
```
- **Decisions:** D-0067

##### `dfe_neet_or_not_known_16_17`: 16-17 year olds NEET or activity not known

- **Sources:** E5 · **measure:** percent_published · **native level:** service_area · **polarity:** higher_worse
- **Formula:** 16-17 NEET + not known; CI: none; aggregation: none
- **Map entry** `tables.E5.measures[2]`:

```yaml
indicator: dfe_neet_or_not_known_16_17
table: ud_neet_characteristics
column: NEETNKprop
kind: value
where:
  Age: 16-17
  Characteristic_grouping: Total
  Characteristic: Total
age_band: '16_17'
period:
- 2024-12-01
- 2025-02-28
```
- **Decisions:** D-0067

#### Theme: family risk

##### `census21_lone_parent_households_dep_children`: Lone-parent households

- **Sources:** F6 · **measure:** proportion · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Lone-parent households with dependent children ÷ `census21_households_dependent_children` (Households with dependent children (same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `census.F6.indicators.census21_lone_parent_households_dep_children`:

```yaml
- age_band: na
  dim1:
  - '10'
  dim2:
  - '1'
  - '2'
  - '3'
  - '4'
```

##### `census21_unpaid_carers_5_24`: Young carers

- **Sources:** F7 · **measure:** proportion · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Providing 1+ hours unpaid care per week, aged 5-24 ÷ `census21_usual_residents_by_age` (Usual residents aged 5-24 (same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `census.F7b.indicators.census21_unpaid_carers_5_24`:

```yaml
- age_band: src_5_24
  dim1:
  - '2'
  - '3'
  - '4'
  - '5'
  - '6'
  dim2:
  - '1'
```

##### `dfe_cin_factor_domestic_abuse`: Domestic abuse identified at assessment

- **Sources:** C1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Episodes with the 'Domestic abuse: concerns parent is victim' factor at end of assessment (Domestic_Abuse_parent) ÷ `dfe_cin_episodes_with_assessment_factors` (Episodes with assessment factor information (Episodes_with_assessment_factor, same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[7]`:

```yaml
indicator: dfe_cin_factor_domestic_abuse
table: c3_factors_identified
column: Domestic_Abuse_parent
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

##### `dfe_cin_factor_parental_mental_health`: Parental mental health identified at assessment

- **Sources:** C1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Episodes with the 'Mental health: concerns about parent' factor at end of assessment (Mental_Health_parent) ÷ `dfe_cin_episodes_with_assessment_factors` (Episodes with assessment factor information (Episodes_with_assessment_factor, same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[8]`:

```yaml
indicator: dfe_cin_factor_parental_mental_health
table: c3_factors_identified
column: Mental_Health_parent
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

##### `dfe_cin_factor_parental_alcohol_misuse`: Parental alcohol misuse identified at assessment

- **Sources:** C1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Episodes with the 'Alcohol misuse: concerns about parent' factor at end of assessment (Alcohol_Misuse_parent) ÷ `dfe_cin_episodes_with_assessment_factors` (Episodes with assessment factor information (Episodes_with_assessment_factor, same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[9]`:

```yaml
indicator: dfe_cin_factor_parental_alcohol_misuse
table: c3_factors_identified
column: Alcohol_Misuse_parent
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```
- **Decisions:** D-0056

##### `dfe_cin_factor_parental_drug_misuse`: Parental drug misuse identified at assessment

- **Sources:** C1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Episodes with the 'Drug misuse: concerns about parent' factor at end of assessment (Drug_Misuse_parent) ÷ `dfe_cin_episodes_with_assessment_factors` (Episodes with assessment factor information (Episodes_with_assessment_factor, same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[10]`:

```yaml
indicator: dfe_cin_factor_parental_drug_misuse
table: c3_factors_identified
column: Drug_Misuse_parent
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```
- **Decisions:** D-0056

##### `ohid_ndtms_adults_in_treatment_living_with_children`: Adults in drug/alcohol treatment living with children

- **Sources:** H3 · **measure:** count · **native level:** service_area · **polarity:** higher_worse
- **Value:** Adults in structured drug/alcohol treatment in 2024-25 who live with children (own or others'), NDTMS. · CI: none · aggregation: sum
- **Built in code:** not loaded (D-0091)
- **Decisions:** D-0055, D-0091

##### `ohid_ndtms_parents_not_living_with_children`: Parents in drug/alcohol treatment not living with their children

- **Sources:** H3 · **measure:** count · **native level:** service_area · **polarity:** higher_worse
- **Value:** Adults in structured treatment in 2024-25 who are parents not living with their children, NDTMS. · CI: none · aggregation: sum
- **Built in code:** not loaded (D-0091)
- **Decisions:** D-0055

#### Theme: housing

##### `census21_overcrowded_households_dep_children`: Overcrowded households with children

- **Sources:** F6 · **measure:** proportion · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Households with dependent children, occupancy rating (bedrooms) <= -1 ÷ `census21_households_dependent_children` (Households with dependent children (same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `census.F6.indicators.census21_overcrowded_households_dep_children`:

```yaml
- age_band: na
  dim1:
  - '5'
  - '8'
  - '10'
  - '13'
  dim2:
  - '4'
```

##### `mhclg_hclic_households_with_children_in_ta`: Households with children in temporary accommodation

- **Sources:** Ho1 · **measure:** count · **native level:** lad · **polarity:** higher_worse
- **Value:** Households with dependent children in TA at 31 March 2025 (H-CLIC TA1). · CI: none · aggregation: sum
- **Map entry** `tables.Ho1.measures[0]`:

```yaml
indicator: mhclg_hclic_households_with_children_in_ta
table: hclic_ta1
column: Total number of households in TA with children
age_band: na
period:
- 2025-03-31
- 2025-03-31
```

##### `mhclg_hclic_children_in_ta`: Children in temporary accommodation

- **Sources:** Ho1 · **measure:** count · **native level:** lad · **polarity:** higher_worse
- **Value:** Dependent children in households in TA at 31 March 2025 (H-CLIC TA1 total). · CI: none · aggregation: sum
- **Map entry** `tables.Ho1.measures[1]`:

```yaml
indicator: mhclg_hclic_children_in_ta
table: hclic_ta1
column: Total number of children in TA
age_band: '0_17'
period:
- 2025-03-31
- 2025-03-31
```

##### `mhclg_hclic_children_in_ta_by_age`: Children in temporary accommodation

- **Sources:** Ho1 · **measure:** rate · **native level:** lad · **polarity:** higher_worse
- **Formula:** Children under 18 in TA (TA8) ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 10000; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.Ho1.measures[2]`:

```yaml
indicator: mhclg_hclic_children_in_ta_by_age
table: hclic_ta8
column: Total Under 18's in TA
age_band: '0_17'
period:
- 2025-03-31
- 2025-03-31
```
- **Map entry** `tables.Ho1.measures[3]`:

```yaml
indicator: mhclg_hclic_children_in_ta_by_age
table: hclic_ta8
period:
- 2025-03-31
- 2025-03-31
band_columns:
  '0_4':
  - '0'
  - '1'
  - '2'
  - '3'
  - '4'
  '5_10':
  - '5'
  - '6'
  - '7'
  - '8'
  - '9'
  - '10'
  '11_15':
  - '11'
  - '12'
  - '13'
  - '14'
  - '15'
  '16_17':
  - '16'
  - '17'
```

##### `mhclg_hclic_owed_duty_households_with_children`: Families assessed as homeless or at risk

- **Sources:** Ho1 · **measure:** count · **native level:** lad · **polarity:** higher_worse
- **Value:** Households with dependent children assessed as owed a prevention or relief duty, 2024-25 (annual H-CLIC). · CI: none · aggregation: sum
- **Map entry** `tables.Ho1.measures[4]`:

```yaml
indicator: mhclg_hclic_owed_duty_households_with_children
table:
- hclic_a5p
- hclic_a5r
age_band: na
period:
- 2024-04-01
- 2025-03-31
columns:
- Single parent with dependent children - Male
- Single parent with dependent children - Female
- Single parent with dependent children - Other/gender not known
- Couple with dependent children
- Three or more adults with dependent children
```

##### `mhclg_hclic_owed_duty_applicants_16_24`: Young people assessed as homeless or at risk (16-24)

- **Sources:** Ho1 · **measure:** rate · **native level:** lad · **polarity:** higher_worse
- **Formula:** Households with lead applicant 16-24 owed a duty ÷ `ons_mye_population` (Population aged 16-24, mid-2024 MYE) × 10000; CI: byar; aggregation: sum_then_divide
- **Map entry** `tables.Ho1.measures[5]`:

```yaml
indicator: mhclg_hclic_owed_duty_applicants_16_24
table: hclic_a6
columns:
- 16-17
- 18-24
age_band: src_16_24
period:
- 2024-04-01
- 2025-03-31
```

#### Theme: health

##### `census21_disabled_0_24`: Disabled children and young people

- **Sources:** F7 · **measure:** proportion · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Disabled under the Equality Act, aged 0-24 ÷ `census21_usual_residents_by_age` (Usual residents aged 0-24 (same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `census.F7a.indicators.census21_disabled_0_24`:

```yaml
- age_band: '0_24'
  dim1:
  - '1'
  - '2'
  dim2:
  - '1'
  - '2'
  - '3'
  - '4'
  - '5'
```

##### `dwp_dla_claimants_under16`: Children receiving Disability Living Allowance

- **Sources:** F3 · **measure:** proportion · **native level:** small_area · **polarity:** higher_worse
- **Formula:** DLA cases in payment, age 0-15 ÷ `ons_sape_population` (Population aged 0-15, mid-2024 SAPE (sum of single years)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `statxplore.F3`:

```yaml
indicator: dwp_dla_claimants_under16
age_field: Age (bands and single year)
age_map: F3
```

##### `dwp_pip_claimants_16_24`: Young people receiving PIP

- **Sources:** F4 · **measure:** proportion · **native level:** small_area · **polarity:** higher_worse
- **Formula:** PIP cases with entitlement, age 16-24 ÷ `ons_sape_population` (Population aged 16-24, mid-2024 SAPE) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `statxplore.F4`:

```yaml
indicator: dwp_pip_claimants_16_24
age_field: Age (bands and single year)
age_map: F4
```

##### `dfe_sen_primary_need_semh`: Pupils with social, emotional and mental health needs

- **Sources:** E1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Pupils with SEN, primary need SEMH ÷ `dfe_pupils_total_sen_publication` (Total pupils) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.E1.measures[3]`:

```yaml
indicator: dfe_sen_primary_need_semh
table: sen_ncyear_
column: number_of_pupils
where:
  phase_type_grouping: Total
  sen_status: Total
  sen_primary_need: Social, Emotional and Mental Health
age_band: src_pupils_all
period:
- 2025-01-16
- 2025-01-16
```

##### `ohid_self_harm_admissions_10_24`: Hospital admissions for self-harm (10-24)

- **Sources:** H2 · **measure:** rate_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** Emergency hospital admissions for intentional self-harm, ages 10-24, rate per 100,000 as published by OHID (count and published CI also stored). · CI: published · aggregation: none
- **Map entry** `fingertips.90813`:

```yaml
indicator: ohid_self_harm_admissions_10_24
sex: Persons
age: 10-24 yrs
time_period: 2023/24
period:
- 2023-04-01
- 2024-03-31
age_band: src_10_24
```

##### `ohid_ae_attendances_0_4`: A&E attendances (under 5s)

- **Sources:** H2 · **measure:** rate_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** A&E attendances, ages 0-4, crude rate per 1,000 as published by OHID. · CI: published · aggregation: none
- **Map entry** `fingertips.93930`:

```yaml
indicator: ohid_ae_attendances_0_4
sex: Persons
age: 0-4 yrs
time_period: 2024/25
period:
- 2024-04-01
- 2025-03-31
age_band: '0_4'
```

##### `ohid_infant_mortality`: Infant mortality

- **Sources:** H2 · **measure:** rate_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** Infant deaths under 1 year per 1,000 live births, 3-year pooled, as published by OHID. · CI: published · aggregation: none
- **Map entry** `fingertips.92196`:

```yaml
indicator: ohid_infant_mortality
sex: Persons
age: <1 yr
time_period: 2022 - 24
period:
- 2022-01-01
- 2024-12-31
age_band: src_infant
```

##### `ohid_under18_conceptions`: Under-18 conceptions

- **Sources:** H2 · **measure:** rate_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** Conceptions to women aged under 18 per 1,000 females aged 15-17, as published by OHID (ONS source). · CI: published · aggregation: none
- **Map entry** `fingertips.20401`:

```yaml
indicator: ohid_under18_conceptions
sex: Female
age: <18 yrs
time_period: '2023'
period:
- 2023-01-01
- 2023-12-31
age_band: src_15_17
sex_code: female
```

##### `ohid_low_birthweight_term`: Low birth weight (full-term babies)

- **Sources:** H2 · **measure:** percent_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** Live births at >= 37 weeks gestation with birth weight < 2,500 g / all live term births with recorded weight, % as published. · CI: published · aggregation: none
- **Map entry** `fingertips.20101`:

```yaml
indicator: ohid_low_birthweight_term
sex: Persons
age: '>=37 weeks gestational age at birth'
time_period: '2024'
period:
- 2024-01-01
- 2024-12-31
age_band: na
```
- **Decisions:** D-0087

##### `ohid_injury_admissions_0_14`: Hospital admissions for injuries (0-14)

- **Sources:** H2 · **measure:** rate_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** Emergency admissions for unintentional and deliberate injuries, ages 0-14, crude rate per 10,000 as published. · CI: published · aggregation: none
- **Map entry** `fingertips.90284`:

```yaml
indicator: ohid_injury_admissions_0_14
sex: Persons
age: <15 yrs
time_period: 2024/25
period:
- 2024-04-01
- 2025-03-31
age_band: src_0_14
```

#### Theme: safety

##### `police_crime_all_excl_asb`: Recorded crime

- **Sources:** S1 · **measure:** rate · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Street-level crime records excluding ASB ÷ `ons_sape_population` (Usual resident population, all ages, mid-2024 (SAPE)) × 1000; CI: byar; aggregation: sum_then_divide
- **Map entry** `police.police_crime_all_excl_asb`:

```yaml
exclude:
- Anti-social behaviour
```

##### `police_crime_violence_sexual`: Violence and sexual offences

- **Sources:** S1 · **measure:** rate · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Street-level 'Violence and sexual offences' records ÷ `ons_sape_population` (Usual resident population, all ages, mid-2024 (SAPE)) × 1000; CI: byar; aggregation: sum_then_divide
- **Map entry** `police.police_crime_violence_sexual`:

```yaml
include:
- Violence and sexual offences
```

##### `police_asb_incidents`: Anti-social behaviour

- **Sources:** S1 · **measure:** rate · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Street-level ASB records ÷ `ons_sape_population` (Usual resident population, all ages, mid-2024 (SAPE)) × 1000; CI: byar; aggregation: sum_then_divide
- **Map entry** `police.police_asb_incidents`:

```yaml
include:
- Anti-social behaviour
```

##### `police_crime_weapons_possession`: Possession of weapons

- **Sources:** S1 · **measure:** rate · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Street-level 'Possession of weapons' records ÷ `ons_sape_population` (Usual resident population, all ages, mid-2024 (SAPE)) × 1000; CI: byar; aggregation: sum_then_divide
- **Map entry** `police.police_crime_weapons_possession`:

```yaml
include:
- Possession of weapons
```

##### `police_crime_drugs`: Drug offences

- **Sources:** S1 · **measure:** rate · **native level:** small_area · **polarity:** higher_worse
- **Formula:** Street-level 'Drugs' records ÷ `ons_sape_population` (Usual resident population, all ages, mid-2024 (SAPE)) × 1000; CI: byar; aggregation: sum_then_divide
- **Map entry** `police.police_crime_drugs`:

```yaml
include:
- Drugs
```

##### `yjb_first_time_entrants_10_17`: First-time entrants to youth justice

- **Sources:** S3 · **measure:** rate_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** Child first-time entrants (aged 10-17) to the youth justice system per 100,000 population aged 10-17, by local authority of residence, year ending December 2024, as published by YJB/MoJ (supplementary table 2.11). · CI: none · aggregation: none
- **Built in code:** harmonise/phase4.py (fte): YJB/MoJ supplementary tables 2.10/2.11 by LA name (aliases in category_maps fte_la_aliases)
- **Decisions:** D-0073

##### `yjb_custodial_sentences_10_17`: Custodial sentences (10-17)

- **Sources:** S3 · **measure:** count · **native level:** YJS · **polarity:** higher_worse
- **Value:** Custodial sentences to children aged 10-17, year ending March 2025, by YJS. · CI: none · aggregation: sum
- **Map entry** `youth_justice[1]`:

```yaml
indicator: yjb_custodial_sentences_10_17
table: yj_outcomes
column: Number_Cautioned_Sentenced
where:
  Caution_or_sentence_tier: Custody
age_band: src_10_17
period:
- 2024-04-01
- 2025-03-31
```

##### `yjb_proven_offences_10_17`: Proven offences by children (10-17)

- **Sources:** S3 · **measure:** rate · **native level:** YJS · **polarity:** higher_worse
- **Formula:** Proven offences, ages 10-17 ÷ `ons_mye_population` (Population aged 10-17, mid-2024 MYE, summed over the YJS's member UTLAs (G7)) × 10000; CI: byar; aggregation: sum_then_divide
- **Map entry** `youth_justice[0]`:

```yaml
indicator: yjb_proven_offences_10_17
table: yj_offences
column: Number_Offences
age_band: src_10_17
period:
- 2024-04-01
- 2025-03-31
```

#### Theme: service demand

##### `dfe_cin_at_31mar`: Children in need

- **Sources:** C1 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Children in need at 31 March 2025 ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 10000; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[0]`:

```yaml
indicator: dfe_cin_at_31mar
table: b1_children_in_need
column: At31_episodes
age_band: '0_17'
period:
- 2025-03-31
- 2025-03-31
```

##### `dfe_cin_referrals`: Referrals to children's social care

- **Sources:** C1 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Referrals in year ending 31 March 2025 ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE (mid-period)) × 10000; CI: byar; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[1]`:

```yaml
indicator: dfe_cin_referrals
table: c1_children_in_need_referrals
column: referral_count
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

##### `dfe_cin_rereferrals_12m`: Re-referrals within 12 months

- **Sources:** C1 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Re-referrals within 12 months ÷ `dfe_cin_referrals` (Referrals in year (same file)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[2]`:

```yaml
indicator: dfe_cin_rereferrals_12m
table: c1_children_in_need_referrals
column: rereferral_count
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

##### `dfe_cin_assessments_completed`: Social care assessments

- **Sources:** C1 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Assessments completed in year ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 10000; CI: byar; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[3]`:

```yaml
indicator: dfe_cin_assessments_completed
table: c2_children_in_need_assessments
column: Assessments_completed
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

##### `dfe_cpp_at_31mar`: Children on child protection plans

- **Sources:** C1 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Children on CP plans at 31 March 2025 ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 10000; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[4]`:

```yaml
indicator: dfe_cpp_at_31mar
table: d1_child_protection_plans
column: CPP_At31
age_band: '0_17'
period:
- 2025-03-31
- 2025-03-31
```

##### `dfe_cpp_starts`: New child protection plans

- **Sources:** C1 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** CP plans started in year ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 10000; CI: byar; aggregation: sum_then_divide
- **Map entry** `tables.C1.measures[5]`:

```yaml
indicator: dfe_cpp_starts
table: d1_child_protection_plans
column: CPP_start
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

##### `dfe_cla_at_31mar`: Children in care

- **Sources:** C2 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Children looked after at 31 March 2025 ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 10000; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C2.measures[0]`:

```yaml
indicator: dfe_cla_at_31mar
table: cla_number_and_rate_per_10k_children
column: children_count
where:
  population_type: Children looked after on 31 March each year
age_band: '0_17'
period:
- 2025-03-31
- 2025-03-31
```
- **Map entry** `tables.C2.measures[1]`:

```yaml
indicator: dfe_cla_at_31mar
table: la_cla_on_31_march_by_characteristics
column: children_count
where:
  characteristic: Age group
period:
- 2025-03-31
- 2025-03-31
bands:
  column: breakdown
  map:
    src_infant:
    - Under 1 year
    src_1_4:
    - 1 to 4 years
    src_5_9:
    - 5 to 9 years
    src_10_15:
    - 10 to 15 years
    '16_17':
    - 16 years and over
```

##### `dfe_cla_starts`: Children entering care

- **Sources:** C2 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** Starts in year ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 10000; CI: byar; aggregation: sum_then_divide
- **Map entry** `tables.C2.measures[2]`:

```yaml
indicator: dfe_cla_starts
table: cla_number_and_rate_per_10k_children
column: children_count
where:
  population_type: Children starting to be looked after each year
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

##### `dfe_cla_uasc_at_31mar`: Unaccompanied asylum-seeking children in care

- **Sources:** C2 · **measure:** rate · **native level:** service_area · **polarity:** neutral
- **Formula:** UASC looked after at 31 March 2025 ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 10000; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C2.measures[3]`:

```yaml
indicator: dfe_cla_uasc_at_31mar
table: la_cla_on_31_march_by_characteristics
column: children_count
where:
  characteristic: Unaccompanied asylum-seeking children
  breakdown: Unaccompanied asylum-seeking children
age_band: '0_17'
period:
- 2025-03-31
- 2025-03-31
```

##### `dfe_care_leavers_17_21`: Care leavers aged 17 to 21

- **Sources:** C2 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Care leavers aged 17-21 on their birthday in the year, as published by DfE. · CI: none · aggregation: sum
- **Map entry** `tables.C2.measures[9]`:

```yaml
indicator: dfe_care_leavers_17_21
table: la_care_leavers_activity
column: care_leaver_count
sum_rows: true
where:
  care_leaver_age:
  - 17 to 18 years
  - 19 to 21 years
  breakdown: Total
age_band: src_17_21
period:
- 2024-04-01
- 2025-03-31
```

##### `dfe_care_leavers_19_21`: Care leavers aged 19 to 21

- **Sources:** C2 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Care leavers aged 19-21, as published by DfE. · CI: none · aggregation: sum
- **Map entry** `tables.C2.measures[8]`:

```yaml
indicator: dfe_care_leavers_19_21
table: la_care_leavers_activity
column: care_leaver_count
where:
  care_leaver_age: 19 to 21 years
  breakdown: Total
age_band: src_19_21
period:
- 2024-04-01
- 2025-03-31
```

##### `dfe_cla_ceased_adoption`: Adoptions from care

- **Sources:** C2 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** CLA who ceased to be looked after in year ending 31 March 2025 with reason 'adopted'. · CI: none · aggregation: sum
- **Map entry** `tables.C2.measures[11]`:

```yaml
indicator: dfe_cla_ceased_adoption
table: la_children_who_ceased_during_the_year
column: children_count
where:
  characteristic: Reason episode ceased
  breakdown: Adopted
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

##### `dfe_ehcps_0_25`: EHC plans (ages 0-25)

- **Sources:** E2 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** EHCPs maintained, January 2025 ÷ `ons_mye_population` (Population aged 0-25, mid-2024 MYE) × 10000; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.E2.measures[0]`:

```yaml
indicator: dfe_ehcps_0_25
table: caseload
column: ehcplans
time_period: '202425'
where:
  breakdown_topic: All EHC plans
  breakdown: All EHC plans
age_band: '0_25'
period:
- 2025-01-16
- 2025-01-16
```
- **Map entry** `tables.E2.measures[1]`:

```yaml
indicator: dfe_ehcps_0_25
table: caseload
column: ehcplans
time_period: '202425'
where:
  breakdown_topic: Child or young persons age
period:
- 2025-01-16
- 2025-01-16
absent_rows_zero:
  total_where:
    breakdown_topic: All EHC plans
    breakdown: All EHC plans
bands:
  column: breakdown
  map:
    '0_4':
    - under 3
    - age 3
    - age 4
    '5_10':
    - age 5
    - age 6
    - age 7
    - age 8
    - age 9
    - age 10
    '11_15':
    - age 11
    - age 12
    - age 13
    - age 14
    - age 15
    '16_17':
    - age 16
    - age 17
    '18_20':
    - age 18
    - age 19
    - age 20
    '21_24':
    - age 21
    - age 22
    - age 23
    - age 24
```

##### `dfe_ehcp_new_plans`: New EHC plans

- **Sources:** E2 · **measure:** rate · **native level:** service_area · **polarity:** higher_worse
- **Formula:** New EHCPs issued, calendar year 2024 ÷ `ons_mye_population` (Population aged 0-25, mid-2024 MYE) × 10000; CI: byar; aggregation: sum_then_divide
- **Map entry** `tables.E2.measures[2]`:

```yaml
indicator: dfe_ehcp_new_plans
table: newplans
column: new_ehc_plans
time_period: '2024'
where:
  breakdown_topic: New EHC plans
  breakdown: New EHC plans
age_band: '0_25'
period:
- 2024-01-01
- 2024-12-31
```

##### `ho_nrm_referrals_under18`: Child referrals for suspected exploitation (NRM)

- **Sources:** S4 · **measure:** rate · **native level:** PFA · **polarity:** higher_worse
- **Formula:** Under-18 NRM referrals ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE, summed over the force area's LADs (G8)) × 10000; CI: byar; aggregation: sum_then_divide
- **Built in code:** harmonise/phase4.py (nrm): NRM Table 10 child referrals by police force, four quarters (category_maps nrm_forces, nrm_period)
- **Decisions:** D-0074

##### `nhse_mhsds_cyp_one_plus_contact_12m`: Children supported by NHS mental health services

- **Sources:** H1 · **measure:** rate · **native level:** SICBL24 · **polarity:** neutral
- **Formula:** CYP 0-17 with 1+ contact, rolling 12 months ÷ `nhse_gp_registered_patients` (GP-registered population aged 0-17, 1 April 2025, as published by Sub-ICB (G3b)) × 10000; CI: wilson; aggregation: none
- **Map entry** `mhsds[0]`:

```yaml
measure: MHS95
breakdown: Sub ICB of GP Practice or Residence
indicator: nhse_mhsds_cyp_one_plus_contact_12m
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

##### `nhse_mhsds_cyp_open_referrals`: Children with open mental health referrals

- **Sources:** H1 · **measure:** count · **native level:** SICBL24 · **polarity:** neutral
- **Value:** MHSDS measure CYP23: open referrals to children and young people's mental health services at the end of March 2025, by Sub-ICB of GP practice or residence. · CI: none · aggregation: sum
- **Map entry** `mhsds[1]`:

```yaml
measure: CYP23
breakdown: Sub ICB - GP Practice or Residence
indicator: nhse_mhsds_cyp_open_referrals
age_band: na
period:
- 2025-03-31
- 2025-03-31
```

#### Theme: service pressure

##### `dfe_cla_placed_20mi_plus`: Children in care placed over 20 miles from home

- **Sources:** C2 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** CLA placed >20 miles from home ÷ `dfe_cla_distance_known_at_31mar` (CLA at 31 March with a known placement distance (sum of the two published distance cells, same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C2.measures[4]`:

```yaml
indicator: dfe_cla_placed_20mi_plus
table: la_cla_on_31_march_by_characteristics
column: children_count
where:
  characteristic: Distance between home and placement
  breakdown: Placed more than 20 miles from home
age_band: '0_17'
period:
- 2025-03-31
- 2025-03-31
```

##### `dfe_cla_3plus_placements`: Children in care with 3+ placements in the year

- **Sources:** C2 · **measure:** proportion · **native level:** service_area · **polarity:** higher_worse
- **Formula:** CLA with 3+ placements during the year ÷ `dfe_cla_stability_base_at_31mar` (Total CLA at 31 March in the placement stability table (same table)) × 100; CI: wilson; aggregation: sum_then_divide
- **Map entry** `tables.C2.measures[6]`:

```yaml
indicator: dfe_cla_3plus_placements
table: LA_CLA_placement_stability
column: children_count
where:
  cla_group: CLA on 31 March
  placement_stability: With 3 or more placements during the year
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

##### `dfe_sw_vacancy_rate`: Social worker vacancy rate

- **Sources:** C3 · **measure:** percent_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** FTE vacancies / (FTE vacancies + FTE social workers) at 30 September 2024, as published by DfE. · CI: none · aggregation: none
- **Map entry** `tables.C3.measures[0]`:

```yaml
indicator: dfe_sw_vacancy_rate
table: csww_indicators
column: vacancy_rate_fte
kind: value
age_band: na
period:
- 2024-09-30
- 2024-09-30
```

##### `dfe_sw_agency_rate`: Agency social worker rate

- **Sources:** C3 · **measure:** percent_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** FTE agency workers / (FTE agency + FTE social workers) at 30 September 2024, as published. · CI: none · aggregation: none
- **Map entry** `tables.C3.measures[1]`:

```yaml
indicator: dfe_sw_agency_rate
table: csww_indicators
column: agency_rate_fte
kind: value
age_band: na
period:
- 2024-09-30
- 2024-09-30
```

##### `dfe_sw_turnover_rate`: Social worker turnover rate

- **Sources:** C3 · **measure:** percent_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** FTE leavers in the year to 30 September 2024 / FTE social workers at 30 September 2024, as published. · CI: none · aggregation: none
- **Map entry** `tables.C3.measures[2]`:

```yaml
indicator: dfe_sw_turnover_rate
table: csww_indicators
column: turnover_rate_fte
kind: value
age_band: na
period:
- 2023-10-01
- 2024-09-30
```

##### `dfe_sw_average_caseload`: Average social worker caseload

- **Sources:** C3 · **measure:** rate_published · **native level:** service_area · **polarity:** higher_worse
- **Value:** Cases held by case-holding social workers / FTE case-holding social workers at 30 September 2024, as published. · CI: none · aggregation: none
- **Map entry** `tables.C3.measures[3]`:

```yaml
indicator: dfe_sw_average_caseload
table: csww_indicators
column: caseload_fte
kind: value
age_band: na
period:
- 2024-09-30
- 2024-09-30
```

##### `dfe_s251_cyp_services_net`: Spending on children's services per child

- **Sources:** C4 · **measure:** currency_gbp · **native level:** service_area · **polarity:** neutral
- **Formula:** Net expenditure, children's and young people's services, GBP ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 1; CI: none; aggregation: sum_then_divide
- **Map entry** `tables.C4.measures[0]`:

```yaml
indicator: dfe_s251_cyp_services_net
table: s251_childrens_young_peoples_services
column: net_current_expenditure
kind: value
where:
  description_of_expenditure: 5.0.2 Total Children and Young Peoples Services Expenditure (excluding CERA)
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```
- **Decisions:** D-0087

##### `dfe_s251_cla_net`: Spending on children in care per child

- **Sources:** C4 · **measure:** currency_gbp · **native level:** service_area · **polarity:** neutral
- **Formula:** Net expenditure, children looked after, GBP ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 1; CI: none; aggregation: sum_then_divide
- **Map entry** `tables.C4.measures[1]`:

```yaml
indicator: dfe_s251_cla_net
table: s251_childrens_young_peoples_services
column: net_current_expenditure
kind: value
where:
  description_of_expenditure: 3.1.11 Total Children Looked After
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

##### `dfe_s251_family_support_net`: Spending on family support per child

- **Sources:** C4 · **measure:** currency_gbp · **native level:** service_area · **polarity:** neutral
- **Formula:** Net expenditure, family support services, GBP ÷ `ons_mye_population` (Population aged 0-17, mid-2024 MYE) × 1; CI: none; aggregation: sum_then_divide
- **Map entry** `tables.C4.measures[2]`:

```yaml
indicator: dfe_s251_family_support_net
table: s251_childrens_young_peoples_services
column: net_current_expenditure
kind: value
where:
  description_of_expenditure: 3.4.6 Total Family Support Services
age_band: '0_17'
period:
- 2024-04-01
- 2025-03-31
```

##### `dfe_s251_young_people_services_net`: Spending on youth services per young person

- **Sources:** C4 · **measure:** currency_gbp · **native level:** service_area · **polarity:** neutral
- **Formula:** Net expenditure, services for young people, GBP ÷ `ons_mye_population` (Population aged 13-19, mid-2024 MYE (to confirm)) × 1; CI: none; aggregation: sum_then_divide
- **Map entry** `tables.C4.measures[3]`:

```yaml
indicator: dfe_s251_young_people_services_net
table: s251_childrens_young_peoples_services
column: net_current_expenditure
kind: value
where:
  description_of_expenditure: 3.5.3 Total Services for young people
age_band: src_13_19
period:
- 2024-04-01
- 2025-03-31
```

##### `ofsted_ilacs_overall_effectiveness`: Ofsted judgement: children's services

- **Sources:** C5 · **measure:** ordinal · **native level:** service_area · **polarity:** higher_worse
- **Value:** Overall effectiveness grade from the most recent ILACS inspection published on or before 31 March 2025; category codes in config/categories.yaml; inspection date recorded as period_end. · CI: none · aggregation: none
- **Built in code:** harmonise/phase3.py (ofsted): latest ILACS judgement at 31 March 2025, ordinal codes from config/categories.yaml

##### `ofsted_childrens_homes`: Children's homes

- **Sources:** C5 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Count of Ofsted-registered children's homes located in the LA at 31 March 2025 (LA-level aggregate only; principle 13). · CI: none · aggregation: sum
- **Built in code:** harmonise/phase3.py (ofsted): count of registered children's homes per LA from the provider list (C5); absent LA = 0

##### `ofsted_childrens_homes_places`: Children's home places

- **Sources:** C5 · **measure:** count · **native level:** service_area · **polarity:** neutral
- **Value:** Registered places in children's homes located in the LA at 31 March 2025 (LA aggregate only). · CI: none · aggregation: sum
- **Built in code:** harmonise/phase3.py (ofsted): sum of registered places per LA from the provider list (C5); absent LA = 0

##### `dfe_ehcp_20wk_timeliness`: EHC plans issued on time

- **Sources:** E2 · **measure:** percent_published · **native level:** service_area · **polarity:** higher_better
- **Value:** New EHCPs issued within 20 weeks, excluding exception cases, as published (%). · CI: none · aggregation: none
- **Map entry** `tables.E2.measures[3]`:

```yaml
indicator: dfe_ehcp_20wk_timeliness
table: timeliness_20_week
column: PC_plans_issued_20_weeks_ex
kind: value
time_period: '2024'
where:
  breakdown_topic: All EHC plans issued
  breakdown: All EHC plans issued
age_band: '0_25'
period:
- 2024-01-01
- 2024-12-31
```

#### Theme: composite

##### `l5_neighbourhood_need`: Neighbourhood need index

- **Sources:** D1, F3, F4, F6, F7, S1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** IoD-style composite (SPEC 12.3): rank-based normal scores within domains, exponentially transformed domain scores, equal domain weights. · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

##### `l5_neighbourhood_need_economic_hardship`: Neighbourhood need: economic hardship domain

- **Sources:** D1, F3, F4, F6, F7, S1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

##### `l5_neighbourhood_need_health_disability`: Neighbourhood need: health disability domain

- **Sources:** D1, F3, F4, F6, F7, S1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

##### `l5_neighbourhood_need_family_housing`: Neighbourhood need: family housing domain

- **Sources:** D1, F3, F4, F6, F7, S1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

##### `l5_neighbourhood_need_safety`: Neighbourhood need: safety domain

- **Sources:** D1, F3, F4, F6, F7, S1 · **measure:** score · **native level:** small_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

##### `l5_la_need`: LA need index

- **Sources:** C1, D1b, E3, E4, E5, E6, F1, F6, F7, H2, Ho1, S1, S3 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** IoD-style composite (SPEC 12.3): rank-based normal scores within domains, exponentially transformed domain scores, equal domain weights. · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

##### `l5_la_need_economic_hardship`: LA need: economic hardship domain

- **Sources:** C1, D1b, E3, E4, E5, E6, F1, F6, F7, H2, Ho1, S1, S3 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

##### `l5_la_need_family_risk`: LA need: family risk domain

- **Sources:** C1, D1b, E3, E4, E5, E6, F1, F6, F7, H2, Ho1, S1, S3 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

##### `l5_la_need_health`: LA need: health domain

- **Sources:** C1, D1b, E3, E4, E5, E6, F1, F6, F7, H2, Ho1, S1, S3 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

##### `l5_la_need_education`: LA need: education domain

- **Sources:** C1, D1b, E3, E4, E5, E6, F1, F6, F7, H2, Ho1, S1, S3 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

##### `l5_la_need_housing`: LA need: housing domain

- **Sources:** C1, D1b, E3, E4, E5, E6, F1, F6, F7, H2, Ho1, S1, S3 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

##### `l5_la_need_safety`: LA need: safety domain

- **Sources:** C1, D1b, E3, E4, E5, E6, F1, F6, F7, H2, Ho1, S1, S3 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

##### `l5_la_system_pressure_demand`: LA system pressure: demand domain

- **Sources:** C1, C2, C3, E2, S4 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

##### `l5_la_system_pressure_capacity`: LA system pressure: capacity domain

- **Sources:** C1, C2, C3, E2, S4 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

##### `l5_la_system_pressure_send`: LA system pressure: send domain

- **Sources:** C1, C2, C3, E2, S4 · **measure:** score · **native level:** service_area · **polarity:** higher_worse
- **Value:** Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3). · CI: none · aggregation: none
- **Built in code:** composite/ (config/composites.yaml; composite methodology)

### 6. Moving to live pipelines

- **One run, one snapshot.** Keep the snapshot model: a run is defined by the code commit and the
  hashes of its input files, and writes a complete new set of tables. Do not update tables in place.
- **Parameters, not code.** Periods (`period_to_take`, `period` in the maps), file URLs and file keys
  live in `config/sources.yaml` and `config/category_maps.yaml`. A new publication should mean new
  config entries, not new code, unless the file layout changes.
- **Fail fast on layout change.** Staging finds columns by their published labels and checks totals
  and row counts (T2). Keep these checks: a renamed column or a missing row must stop the run, not
  produce wrong values.
- **Port the QA gates as data tests.** Gates 1–19 are pytest checks over the output tables; each maps
  to a data-quality rule (keys, England only, conservation, suppression integrity, denominator match,
  ranges, reconciliation, serving completeness, reproducibility).
- **Things that are manual today:** finding each new file (principle 11: verified URLs only); reading
  a new release's data guidance for symbols and rounding (`config/suppression_codes.yaml`); the NDTMS
  gap (D-0091); deciding whether a changed published figure is a revision.
- **Mapping to Microsoft Fabric:** L0 as files in a lakehouse (pipelines or Dataflows to fetch);
  T2–T9 as notebooks writing one Delta table per layer table; L4 views as views or Delta tables; the
  composite step as a notebook with the same seed; the QA gates as a notebook that blocks publication
  when a rule fails.

---

[Methodology index](#page-index)

---

<a id="page-qa_summary"></a>

## QA summary

Release `2dda583978fb-19eda0e60019`

| Gate | Check | Result |
|---|---|---|
| 1 | Hashes: every L0 file matches dim_source_file.sha256 | passed |
| 2 | L1 reconciliation: row counts and published totals within tolerance | passed |
| 3 | Keys: PKs unique, FKs resolve, indicator metadata complete, ethnicity classes | passed |
| 4 | Hierarchy: single parents, nesting proven, counts, same_as_parent | passed |
| 5 | England only in L2/L3/L4 | passed |
| 6 | Population conservation (P1 vs P1b, exact) | passed |
| 7 | Count conservation and reconciliation table | passed |
| 8 | Suppression integrity | passed |
| 9 | Denominator match | passed |
| 10 | Ranges and outlier flags | passed |
| 11 | Point assignment match rate >= 99% | passed |
| 12 | Relationships have evidence; nothing derived from 'contains' | passed |
| 13 | IoD validation: recomputed LAD averages match D1b | passed |
| 14 | Safeguarding and disclosure | passed |
| 15 | Serving layer completeness and fallback isolation | passed |
| 16 | Coverage report written | passed |
| 17 | Reproducibility: logical content hashes identical on rebuild | passed |
| 18 | Methodology completeness | passed |
| 19 | L5 composites (12.8): inputs, weights, seeded rerun, rank intervals, reasons, report | passed |

### Reconciliation

| Indicator | Level | Pairs | Within tolerance | Largest difference |
|---|---|---|---|---|
| census21_disabled_0_24 | intermediate_area | 6,824 | 6,809 | 16 |
| census21_disabled_0_24 | lad | 279 | 278 | 59 |
| census21_disabled_0_24 | service_area | 136 | 136 | 103 |
| census21_households_dependent_children | intermediate_area | 6,856 | 6,850 | 23 |
| census21_households_dependent_children | lad | 296 | 296 | 129 |
| census21_households_dependent_children | nation | 1 | 1 | 61 |
| census21_households_dependent_children | service_area | 153 | 153 | 129 |
| census21_lone_parent_households_dep_children | intermediate_area | 6,856 | 6,855 | 12 |
| census21_lone_parent_households_dep_children | lad | 296 | 296 | 49 |
| census21_lone_parent_households_dep_children | nation | 1 | 1 | 96 |
| census21_lone_parent_households_dep_children | service_area | 153 | 153 | 49 |
| census21_overcrowded_households_dep_children | intermediate_area | 6,856 | 6,855 | 12 |
| census21_overcrowded_households_dep_children | lad | 296 | 293 | 34 |
| census21_overcrowded_households_dep_children | nation | 1 | 1 | 8 |
| census21_overcrowded_households_dep_children | service_area | 153 | 153 | 54 |
| census21_population_by_ethnicity | intermediate_area | 302,085 | 302,084 | 15 |
| census21_population_by_ethnicity | lad | 7,644 | 7,635 | 41 |
| census21_population_by_ethnicity | service_area | 3,381 | 3,373 | 55 |
| census21_unpaid_carers_5_24 | intermediate_area | 6,373 | 6,371 | 11 |
| census21_unpaid_carers_5_24 | lad | 118 | 116 | 27 |
| census21_unpaid_carers_5_24 | service_area | 45 | 44 | 27 |
| census21_usual_residents_by_age | intermediate_area | 13,197 | 13,197 | 24 |
| census21_usual_residents_by_age | lad | 397 | 397 | 68 |
| census21_usual_residents_by_age | service_area | 181 | 181 | 135 |
| dfe_absence_enrolments | nation | 1 | 1 | 0 |
| dfe_care_leavers_19_21 | nation | 1 | 1 | 4 |
| dfe_cin_assessments_completed | nation | 1 | 1 | 0 |
| dfe_cin_at_31mar | nation | 1 | 1 | 2 |
| dfe_cin_episodes_with_assessment_factors | nation | 1 | 1 | 0 |
| dfe_cin_factor_parental_alcohol_misuse | nation | 1 | 1 | 5 |
| dfe_cin_referrals | nation | 1 | 1 | 2 |
| dfe_cin_rereferrals_12m | nation | 1 | 1 | 3 |
| dfe_ehcp_new_plans | nation | 1 | 1 | 0 |
| dfe_ehcps_0_25 | nation | 7 | 7 | 0 |
| dfe_exclusions_headcount | nation | 1 | 1 | 0 |
| dfe_fsm_eligible_pupils | nation | 1 | 1 | 0 |
| dfe_permanent_exclusions | nation | 1 | 1 | 0 |
| dfe_persistent_absence | nation | 1 | 1 | 0 |
| dfe_pupils_by_ethnicity | nation | 20 | 20 | 0 |
| dfe_pupils_on_roll | nation | 1 | 1 | 0 |
| dfe_pupils_sen_support | nation | 1 | 1 | 0 |
| dfe_pupils_total_sen_publication | nation | 1 | 1 | 0 |
| dfe_pupils_with_ehcp | nation | 1 | 1 | 0 |
| dfe_sen_primary_need_asd | nation | 1 | 1 | 0 |
| dfe_sen_primary_need_semh | nation | 1 | 1 | 0 |
| dfe_severe_absence | nation | 1 | 1 | 0 |
| dfe_suspensions | nation | 1 | 1 | 0 |
| dwp_cilif_absolute_bhc | nation | 5 | 5 | 43 |
| dwp_cilif_relative_bhc | nation | 5 | 5 | 43 |
| dwp_dla_claimants_under16 | intermediate_area | 14,472 | 14,466 | 23 |
| dwp_dla_claimants_under16 | lad | 120 | 120 | 58 |
| dwp_dla_claimants_under16 | service_area | 31 | 31 | 47 |
| dwp_pip_claimants_16_24 | intermediate_area | 8,737 | 8,736 | 19 |
| dwp_pip_claimants_16_24 | lad | 13 | 12 | 40 |
| dwp_pip_claimants_16_24 | service_area | 2 | 2 | 40 |
| dwp_uc_households_with_children | intermediate_area | 6,787 | 6,787 | 17 |
| dwp_uc_households_with_children | lad | 254 | 254 | 88 |
| dwp_uc_households_with_children | service_area | 103 | 103 | 88 |
| ons_mye_population | lad | 54,168 | 54,168 | 0 |
| ons_mye_population | nation | 183 | 183 | 0 |
| ons_mye_population | service_area | 27,999 | 27,999 | 0 |
| ons_sape_population | intermediate_area | 1,254,648 | 1,254,648 | 0 |

### Flagged for manual review

Values beyond 4 standard deviations from the England mean (kept, for manual review):

| Indicator | Level | Areas |
|---|---|---|
| census21_disabled_0_24 | intermediate_area | 7 |
| census21_disabled_0_24 | small_area | 38 |
| census21_lone_parent_households_dep_children | small_area | 5 |
| census21_overcrowded_households_dep_children | intermediate_area | 17 |
| census21_overcrowded_households_dep_children | lad | 2 |
| census21_overcrowded_households_dep_children | small_area | 127 |
| census21_unpaid_carers_5_24 | intermediate_area | 7 |
| census21_unpaid_carers_5_24 | small_area | 71 |
| dfe_cin_assessments_completed | lad | 1 |
| dfe_cin_assessments_completed | service_area | 1 |
| dfe_cin_at_31mar | lad | 1 |
| dfe_cin_at_31mar | service_area | 1 |
| dfe_cin_factor_domestic_abuse | lad | 1 |
| dfe_cin_factor_domestic_abuse | service_area | 1 |
| dfe_cin_referrals | lad | 1 |
| dfe_cin_referrals | service_area | 2 |
| dfe_cin_rereferrals_12m | lad | 2 |
| dfe_cin_rereferrals_12m | service_area | 3 |
| dfe_cla_at_31mar | lad | 2 |
| dfe_cla_at_31mar | service_area | 2 |
| dfe_cla_starts | lad | 1 |
| dfe_cla_starts | service_area | 1 |
| dfe_ehcps_0_25 | lad | 2 |
| dfe_ehcps_0_25 | service_area | 4 |
| dfe_neet_or_not_known_16_17 | lad | 1 |
| dfe_neet_or_not_known_16_17 | service_area | 1 |
| dfe_persistent_absence | lad | 1 |
| dfe_persistent_absence | service_area | 1 |
| dfe_s251_cla_net | lad | 1 |
| dfe_s251_cla_net | service_area | 1 |
| dfe_s251_cyp_services_net | lad | 1 |
| dfe_s251_cyp_services_net | service_area | 1 |
| dfe_s251_young_people_services_net | lad | 1 |
| dfe_s251_young_people_services_net | service_area | 1 |
| dfe_sen_primary_need_asd | service_area | 1 |
| dfe_suspensions | service_area | 1 |
| dfe_sw_agency_rate | lad | 1 |
| dfe_sw_agency_rate | service_area | 1 |
| dfe_sw_turnover_rate | lad | 1 |
| dfe_sw_turnover_rate | service_area | 2 |
| dfe_sw_vacancy_rate | lad | 1 |
| dfe_sw_vacancy_rate | service_area | 1 |
| dwp_dla_claimants_under16 | intermediate_area | 69 |
| dwp_dla_claimants_under16 | lad | 1 |
| dwp_dla_claimants_under16 | small_area | 281 |
| dwp_pip_claimants_16_24 | intermediate_area | 34 |
| dwp_pip_claimants_16_24 | small_area | 223 |
| mhclg_hclic_children_in_ta_by_age | lad | 20 |
| mhclg_hclic_children_in_ta_by_age | service_area | 12 |
| mhclg_hclic_owed_duty_applicants_16_24 | lad | 2 |
| mhclg_iod25_barriers_la_prop_most_deprived_10pct | lad | 3 |
| mhclg_iod25_barriers_la_prop_most_deprived_10pct | service_area | 2 |
| mhclg_iod25_barriers_score | small_area | 1 |
| mhclg_iod25_crime_decile | intermediate_area | 85 |
| mhclg_iod25_crime_la_prop_most_deprived_10pct | lad | 1 |
| mhclg_iod25_crime_la_prop_most_deprived_10pct | service_area | 1 |
| mhclg_iod25_crime_score | small_area | 1 |
| mhclg_iod25_education_decile | intermediate_area | 124 |
| mhclg_iod25_education_score | intermediate_area | 4 |
| mhclg_iod25_education_score | small_area | 12 |
| mhclg_iod25_employment_decile | intermediate_area | 115 |
| mhclg_iod25_employment_score | intermediate_area | 7 |
| mhclg_iod25_employment_score | small_area | 53 |
| mhclg_iod25_health_decile | intermediate_area | 116 |
| mhclg_iod25_health_la_avg_score | lad | 1 |
| mhclg_iod25_health_la_avg_score | service_area | 1 |
| mhclg_iod25_health_la_prop_most_deprived_10pct | lad | 2 |
| mhclg_iod25_idaci_la_prop_most_deprived_10pct | lad | 1 |
| mhclg_iod25_idaci_la_prop_most_deprived_10pct | service_area | 1 |
| mhclg_iod25_imd_la_local_concentration | service_area | 1 |
| mhclg_iod25_imd_la_prop_most_deprived_10pct | lad | 1 |
| mhclg_iod25_imd_score | intermediate_area | 4 |
| mhclg_iod25_imd_score | small_area | 13 |
| mhclg_iod25_income_decile | intermediate_area | 149 |
| mhclg_iod25_income_score | intermediate_area | 3 |
| mhclg_iod25_income_score | small_area | 9 |
| mhclg_iod25_living_env_decile | intermediate_area | 110 |
| mhclg_iod25_living_env_la_avg_score | lad | 1 |
| mhclg_iod25_living_env_la_avg_score | service_area | 1 |
| mhclg_iod25_living_env_la_prop_most_deprived_10pct | lad | 3 |
| mhclg_iod25_living_env_la_prop_most_deprived_10pct | service_area | 2 |
| mhclg_iod25_living_env_score | intermediate_area | 4 |
| ohid_ae_attendances_0_4 | lad | 1 |
| ohid_ae_attendances_0_4 | service_area | 1 |
| police_asb_incidents | intermediate_area | 52 |
| police_asb_incidents | lad | 2 |
| police_asb_incidents | service_area | 2 |
| police_asb_incidents | small_area | 313 |
| police_crime_all_excl_asb | intermediate_area | 33 |
| police_crime_all_excl_asb | lad | 2 |
| police_crime_all_excl_asb | service_area | 2 |
| police_crime_all_excl_asb | small_area | 230 |
| police_crime_drugs | intermediate_area | 65 |
| police_crime_drugs | lad | 2 |
| police_crime_drugs | service_area | 1 |
| police_crime_drugs | small_area | 263 |
| police_crime_violence_sexual | intermediate_area | 54 |
| police_crime_violence_sexual | lad | 1 |
| police_crime_violence_sexual | service_area | 1 |
| police_crime_violence_sexual | small_area | 270 |
| police_crime_weapons_possession | intermediate_area | 43 |
| police_crime_weapons_possession | lad | 2 |
| police_crime_weapons_possession | service_area | 1 |
| police_crime_weapons_possession | small_area | 159 |

---

[Methodology index](#page-index)

---

<a id="page-references"></a>

## References

Release `2dda583978fb-19eda0e60019`. Methods and standards cited in this methodology. Data sources and
their licences are listed in `sources.csv` and on each indicator's page.

### Statistical methods

- **Wilson score interval:** Wilson, E. B. (1927). Probable inference, the law of succession, and
  statistical inference. *Journal of the American Statistical Association*, 22(158), 209–212.
- **Byar's approximation to the exact Poisson interval:** Breslow, N. E. and Day, N. E. (1987).
  *Statistical Methods in Cancer Research, Volume II: The Design and Analysis of Cohort Studies*. IARC
  Scientific Publications No. 82. Lyon: International Agency for Research on Cancer.
- **Empirical Bayes smoothing (global):** Marshall, R. J. (1991). Mapping disease and mortality rates
  using empirical Bayes estimators. *Journal of the Royal Statistical Society, Series C (Applied
  Statistics)*, 40(2), 283–294.
- **Rank-based normal scores:** Blom, G. (1958). *Statistical Estimates and Transformed Beta-Variables*.
  New York: Wiley.
- **Internal consistency:** Cronbach, L. J. (1951). Coefficient alpha and the internal structure of
  tests. *Psychometrika*, 16(3), 297–334.
- **Hotspot statistic (README guidance):** Ord, J. K. and Getis, A. (1995). Local spatial
  autocorrelation statistics: distributional issues and an application. *Geographical Analysis*, 27(4),
  286–306.
- **False discovery rate:** Benjamini, Y. and Hochberg, Y. (1995). Controlling the false discovery
  rate: a practical and powerful approach to multiple testing. *Journal of the Royal Statistical
  Society, Series B*, 57(1), 289–300.

### Composite indicators

- **Construction:** OECD and European Commission Joint Research Centre (2008). *Handbook on
  Constructing Composite Indicators: Methodology and User Guide*. Paris: OECD Publishing.
- **Uncertainty and sensitivity analysis:** Saisana, M., Saltelli, A. and Tarantola, S. (2005).
  Uncertainty and sensitivity analysis techniques as tools for the quality assessment of composite
  indicators. *Journal of the Royal Statistical Society, Series A*, 168(2), 307–323.
- **Variance-based sensitivity (Sobol' indices):** Sobol', I. M. (1993). Sensitivity estimates for
  nonlinear mathematical models. *Mathematical Modelling and Computational Experiments*, 1(4), 407–414.
- **Indices of Deprivation (domain construction, exponential transformation, LA summaries):**
  McLennan, D., Noble, S. et al. (2025). *The English Indices of Deprivation 2025: Technical Report*.
  London: Ministry of Housing, Communities and Local Government.
  https://assets.publishing.service.gov.uk/media/68ff59c80f801e57b5bef907/ID_2025_Technical_Report.pdf

### Geography and inference

- **Ecological fallacy:** Robinson, W. S. (1950). Ecological correlations and the behavior of
  individuals. *American Sociological Review*, 15(3), 351–357.
- **Modifiable areal unit problem:** Openshaw, S. (1984). *The Modifiable Areal Unit Problem*. Concepts
  and Techniques in Modern Geography 38. Norwich: Geo Books.

### Official statistics and disclosure control

- **Census 2021 disclosure control:** Office for National Statistics. Protecting personal data in
  Census 2021 results.
  https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/protectingpersonaldataincensus2021results
- **Small area population estimates:** Office for National Statistics. Small area population estimates:
  quality and methodology information.
  https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/smallareapopulationestimatesqmi
- **Statistical standards:** UK Statistics Authority. *Code of Practice for Statistics*, version 3.0.
  Office for Statistics Regulation. https://osr.statisticsauthority.gov.uk/the-code-of-practice-for-statistics/
- Each publisher's disclosure control is summarised, with the data guidance it comes from, in the
  [technical methodology](#page-methodology_technical) (section 3).

---

[Methodology index](#page-index)

---

<a id="page-decision_log"></a>

## Decision log

Release `2dda583978fb-19eda0e60019`. Generated from `DECISIONS.md`: every assumption and
judgement made in building this release, with its date, its reason and its effect on the outputs.

### D-0001: Repository root is the existing git repository

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** The existing repository (`CYP Database`, already under git with the spec committed) is the project root in place of a new `uk-cyp-need/` directory, so `git init` was not needed. The spec was copied to `SPEC.md`. The original `uk-cyp-need-database-spec.md` is left untouched as the committed v1.2 record. `SPEC.md` is the working copy.
- **Reason:** The folder was already initialised for this project. A nested repository would split history.
- **Effect on outputs:** None. Paths in SPEC section 5 are relative to this root.

### D-0002: Python 3.12 via uv; polars as the dataframe library

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** `.python-version` pins 3.12 (uv-managed CPython 3.12.15). The machine's default Python 3.13 is not used. `requires-python = ">=3.12,<3.13"`. Tabular work uses polars; pandas is present only as a dependency of geopandas.
- **Reason:** SPEC section 5 names Python 3.12. Choosing a single dataframe library keeps parsers consistent.
- **Effect on outputs:** None.

### D-0003: Unverified URLs are left null

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** In `config/sources.yaml`, `landing_url` is filled only for the eight pages verified in SPEC 8.5. All other sources have `landing_url: null`, `verify: true` and a `where_to_look` note naming the publisher page to search. The validator enforces this. `dim_source` (where landing_url is NOT NULL) is loaded per phase, only after verification.
- **Reason:** Principle 11: never guess URLs, file names or layouts.
- **Effect on outputs:** None until each source's phase, when URLs are recorded on verification.

### D-0004: Working database location

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** L2 and L3 tables are built in a working DuckDB at `data/cyp_need.duckdb` (gitignored). The release copy is `release/<snapshot_id>/cyp_need_<snapshot_id>.duckdb`. `make schema` recreates the working DB from `sql/schema.sql` and the config dimensions.
- **Reason:** SPEC section 5 places L2/L3 in DuckDB but does not name the working file.
- **Effect on outputs:** None.

### D-0005: Dirty-tree guard and development runs

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Every pipeline stage refuses to run on a git tree with uncommitted or untracked changes. Stages other than `release` accept `--allow-dirty` for development runs. That flag appends `-dirty` to code_version, so the resulting snapshot_id can never be mistaken for a release. `release` has no such flag.
- **Reason:** Principle 10 requires refusing a dirty tree. Parser development in Phases 1-4 needs to iterate without committing on every run.
- **Effect on outputs:** Only clean-tree builds can produce a release.

### D-0006: Age band code conventions

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Standard bands and totals use the SPEC codes (`0_4` … `0_25`, `all_ages`). A source band that does not map exactly is coded `src_<min>_<max>` (e.g. `src_10_24`), with `src_infant` for under-1 and `src_pupils_all` for school-census populations, which are not age bands. `na` marks rows that are not age-specific (households, births, workforce, spend, judgements). Where a source band equals a standard band exactly (e.g. CiLIF 0-4), the standard code is used. Codes are quoted in YAML because YAML 1.1 reads `0_17` as an octal integer; the validator catches unquoted codes.
- **Reason:** SPEC section 3 (never split or trim a band). Clear, sortable codes.
- **Effect on outputs:** `dim_age_band` codes as listed in `config/age_bands.yaml`.

### D-0007: Single-year-of-age codes

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Population single years are coded `y00` … `y89`, plus `y90plus`, with `is_standard = true` and `rolls_into` computed (e.g. `y17` → `0_17,0_24,0_25`; `y25` → `0_25`).
- **Reason:** SPEC section 3: population stored by single year (0-90+), and denominators are exact sums of single years.
- **Effect on outputs:** 91 single-year rows in `dim_age_band`.

### D-0008: Indicator catalogue conventions

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** `config/indicators.yaml` holds the `dim_indicator` fields plus config-only fields (`framework_role`, `published_levels`, `age_bands`, `period`, `verify`, `needs_decision`). The loader applies documented defaults, `methodology_anchor` defaults to the indicator_id with hyphens, and source_ids are written as a comma list. `framework_role` separates need from pressure: pressure indicators must have theme `service_demand` or `service_pressure`, and need indicators must not. The user approved all 123 indicators on 2026-10-20 (`catalogue_reviewed_date`, applied as each indicator's `reviewed_date`).
- **Reason:** SPEC 13 Phase 0 deliverable. The framework split implements SPEC 12.1 from the start.
- **Effect on outputs:** Feeds `dim_indicator`, the profile and serving metadata, and the methodology pages.

### D-0009: SDC profiles and tolerances are drafts

- **Date:** 2026-10-19
- **Status:** decided; every loaded source's SDC profile confirmed in D-0094 (Census guidance cited). F2–F4 tolerances were set from observed reconciliation (D-0053); all others were set in advance and not changed.
- **Decision:** Each source has an SDC profile following SPEC section 8's expected table. Every profile not yet checked against publisher guidance has `confirmed: false`, and its tolerance_reason starts with `DRAFT`. Draft tolerances: Census 10 abs / 1% rel; Stat-Xplore LSOA 10 / 2%; DfE 0 / 0.1-0.5%; MHSDS 5 / 1% (rounding base 5); H-CLIC 0 / 5% (national imputation); ONS population exact (0 / 0). Each is confirmed, with the guidance cited, before that source's phase QA.
- **Reason:** SPEC 13 Phase 0 asks for SDC profiles. No file or guidance has been read yet, so the numbers are placeholders for review.
- **Effect on outputs:** Gates 2 and 7 use these tolerances once confirmed.

### D-0010: Census "sex" vs DfE "gender"

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Census 2021 records sex, while DfE collections record gender as recorded by the school or LA. Both are mapped to the `dim_sex` codes (`female`, `male`) for display. The concepts are not identical, so a rate never combines a DfE numerator split by gender with a Census or ONS denominator split by sex. Per-source maps are filled at inspection.
- **Reason:** SPEC section 3 asks for this to be recorded.
- **Effect on outputs:** Sex-specific rates are only built where numerator and denominator use the same concept.

### D-0011: Ethnicity categories come only from inspected files

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** `config/ethnicity_classifications.yaml` defines the classifications (`none`, `census21_ew_20cat`, `dfe_ethnicity`) and their totals only. Category lists are copied verbatim from the P4 file (Phase 2) and the P7 file (Phase 3). The Census classification name assumes 20 categories and is renamed if ONS allows a different level at LSOA x age.
- **Reason:** Principles 11 and 15: no guessed labels, no grouping.
- **Effect on outputs:** `dim_ethnicity` has 3 total rows until Phase 2.

### D-0012: Which CI method for which measure

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** Person-based stocks and prevalences use Wilson intervals even when shown per 10,000 (CIN, CLA and CP plans at 31 March, EHCPs, UASC, children in TA, CYP MH access). Event counts that can repeat use Byar (referrals, assessments, CLA starts, CP starts, suspensions, exclusions, crime, FTEs, NRM, homelessness duties). Published rates keep the publisher's CI or none. Model-based, survey-calibrated and index values get no derived CI.
- **Reason:** SPEC T7 names Wilson for proportions and Byar for crude rates. Whether a measure is a proportion depends on whether each person is counted once.
- **Effect on outputs:** `ci_method` per indicator.

### D-0013: IoD 2025 catalogue scope

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** At LSOA level: IMD and IDACI score, rank and decile; the seven domain scores and deciles; the Education Children and Young People sub-domain score; and the IoD population denominators (weights for T6c, assuming IoD 2025 publishes them as IoD 2019 did). At LA level (D1b): the five summary measures for IMD and IDACI. IDAOPI, domain ranks and the other sub-domains are left out. The published LA proportions (extent, share in decile 1) are typed `percent_published`.
- **Reason:** These are the measures relevant to CYP and needed for the dashboard and T6c. The spec asks for "all domains incl. IDACI", so domain scores are included. Domain ranks add nothing for display.
- **Effect on outputs:** 32 IoD indicators (22 LSOA, 10 LA summary). Easy to extend.

### D-0014: ONS population estimates typed as model_based

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** SAPE (P1), MYE (P1b) and the IoD population denominators have `estimate_type = 'model_based'` and `ci_method = 'none'`.
- **Reason:** They are demographic estimates (cohort-component and small-area models), not counts. The schema vocabulary has no separate "demographic estimate" type.
- **Effect on outputs:** Shown as estimates in the serving layer.

### D-0015: Police indicators

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** Five data.police.uk indicators: all crime excluding ASB; violence and sexual offences; ASB; possession of weapons; drugs. Each is a rate per 1,000 usual residents of all ages (multiplier 1000, the usual convention for crime), with Byar intervals. `framework_role = context`, because these are not CYP-specific.
- **Reason:** SPEC 8.4 S1 lists these separately as area context. Excluding ASB keeps "all crime" to crimes.
- **Effect on outputs:** Five indicators at small_area, aggregated upward by exact nesting.

### D-0016: Published rates are stored as published

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Fingertips indicators, the social worker workforce rates, EHCP 20-week timeliness, the CiLIF percentages and the IoD LA proportions are stored as `rate_published` or `percent_published` (in `value`, with published CIs). The count is stored alongside where published. They are not re-derived and cannot be aggregated to custom regions (`custom_aggregation = none`).
- **Reason:** Principle 6 (published first). Several use denominators or standardisation not reproducible from our inputs.
- **Effect on outputs:** These indicators have no derived rate, and no value for custom regions.

### D-0017: Per-head spend uses rate_multiplier 1

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** Section 251 spend lines are `currency_gbp`, with a derived per-child value (multiplier 1; GBP per child aged 0-17, or per 13-19 for youth services). The multiplier vocabulary is extended to {1, 100, 1000, 10000}.
- **Reason:** SPEC 12.1 uses "Section 251 per child". GBP per child is the natural unit.
- **Effect on outputs:** The serving layer shows GBP per child.

### D-0018: Permanent exclusions shown per 10,000 pupils

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** Suspensions are shown per 100 pupils (as DfE publishes). Permanent exclusions are shown per 10,000 pupils (DfE publishes per 100).
- **Reason:** Per 100, permanent exclusion rates are around 0.1, which is hard to read on a map. Per 10,000 gives whole numbers.
- **Effect on outputs:** Display unit only.

### D-0019: Config validation is strict

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** The YAML loader rejects duplicate keys (merge-key overrides are allowed). `validate_config()` checks cross-references and measure/CI/aggregation consistency. Loading the dimensions into DuckDB enforces every CHECK vocabulary in `sql/schema.sql`. All three run in `make qa`.
- **Reason:** Principle 9 (mappings are data) only works if the data is validated.
- **Effect on outputs:** None. Prevents bad config from reaching the build.

### D-0020: Tables loaded in primary-key order; logical hashes defined now

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Loaders sort rows by primary key before inserting (SPEC 7.1). The gate 17 logical content hash is SHA-256 over the column names, then each row as compact JSON (floats as `repr`, dates as ISO 8601), sorted by primary key (all columns if a table has none).
- **Reason:** A fixed serialisation is needed before any data is loaded so that rebuilds can be compared.
- **Effect on outputs:** Gate 17.

### D-0021: UC households with children: choice of denominator

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** Accepted draft position: UC households with children is count-only (no derived rate). Revisit in Phase 6 if the neighbourhood need composite requires a rate. Options considered: (a) count only; (b) rate on Census 2021 households with dependent children, with a `max_denominator_gap_days` override and a flag; (c) a per-child rate (unit mismatch; not recommended). Draft catalogue entry is count only.
- **Reason:** No timely household denominator exists at LSOA. The neighbourhood need index (SPEC 12.1) needs a rate.
- **Effect on outputs:** Decides whether UC can enter the neighbourhood need composite.

### D-0022: CiLIF rate

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** Accepted draft position: use DWP's published LA percentages if published; otherwise no rate (no approximate denominator) until decided again. Use DWP's published percentages (`dwp_cilif_*_bhc_pct`, percent_published) if DWP publishes them at LA level. Otherwise, either have no rate or use a stated approximate denominator, flagged.
- **Reason:** CiLIF counts dependent children aged up to 19. No population band matches, and SPEC 3 forbids trimming bands.
- **Effect on outputs:** The LA-level child poverty rate shown on the dashboard.

### D-0023: NDTMS parents in treatment: rate or count

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** Accepted draft position: count-only. Revisit in Phase 6 if the LA need composite requires a rate. Options considered: Keep it as a count, or express it per 10,000 children aged 0-17 (a ratio across different populations, clearly labelled).
- **Reason:** SPEC 12.1 includes it in the LA need index, which needs a rate.
- **Effect on outputs:** Eligibility for the LA need composite.

### D-0024: Spend polarity and the youth services denominator

- **Date:** 2026-10-19
- **Status:** decided (user sign-off of the indicator catalogue, 2026-10-20)
- **Decision:** Accepted draft position: spend polarity stays `neutral` in the catalogue; youth services per-head denominator is ages 13-19. Composite direction is set in Phase 6. Section 251 spend polarity is `neutral` in the catalogue. If spend enters the system pressure index, it is read as "higher = more pressure". The youth services per-head denominator is ages 13-19.
- **Reason:** Spend is not intrinsically better or worse. The composite needs a direction.
- **Effect on outputs:** L5 pressure index direction; display wording.

### D-0025: Composite Monte Carlo settings not given by the spec

- **Date:** 2026-10-19
- **Status:** decided (superseded in detail by D-0088, Phase 6)
- **Decision:** `config/composites.yaml` drafts the values the spec leaves open: seed 20250331; Dirichlet concentration 20 around equal weights; missing-data thresholds {0.5, 0.6667, 0.75}. Domain membership follows SPEC 12.1, mapped to draft indicator_ids. Final values are set in Phase 6.
- **Reason:** SPEC 12.4 fixes 1,000 runs and a fixed seed, but not the concentration or the threshold grid.
- **Effect on outputs:** L5 uncertainty intervals (Phase 6).

### D-0026: Storage safeguards for the USB project drive

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Raw files stream to a `.part` file, are fsynced, renamed, then re-read and re-hashed before acceptance; manifests and staged Parquet are written atomically. The working DuckDB is built in `data/cyp_need.duckdb.building` and only replaces the working database after a complete, successful build. USB selective suspend was turned off on the build machine (user approval, 2026-10-19).
- **Reason:** The project drive (USB, exFAT) dropped off the bus repeatedly on 2026-10-19 (System log: disk event 51). It was stable after a port change (5-minute 256 MB write/hash soak test, no errors).
- **Effect on outputs:** None. Prevents corrupt L0 files or a half-written database.

### D-0027: G1 is built from two ONS OA-level lookups

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** ONS publishes no exact-fit OA21 → LSOA21 → MSOA21 → LAD lookup for 2025 LADs. OA → LSOA → MSOA membership comes from the exact-fit December 2021 lookup (V3). Each OA's 2025 LAD comes from the OA21 → Ward (2025) → LAD (May 2025) lookup (V3). OA unanimity is tested against those 2025 LADs, and the BFC polygon test (≥ 99.9%) provides independent geometric proof. Neither lookup is used as nesting evidence on its own.
- **Reason:** LAD boundaries changed in April 2023 (Cumbria, North Yorkshire, Somerset). SPEC 4.2 forbids best-fit lookups as nesting evidence, so geometry is the proof.
- **Effect on outputs:** `dim_geography.nesting_evidence` records both tests for every LSOA and MSOA.

### D-0028: Upper-tier boundaries use the December 2024 edition

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** ONS has no April or May 2025 Counties and Unitary Authorities boundary set. The December 2025 edition (BFC, BGC) is used: its 153 England codes exactly equal the April 2025 LAD → CTYUA lookup (G2), and every LAD lies ≥ 99.946% inside its service-area polygon. The December 2024 edition was tried first and rejected by the code-set check: it predates the April 2025 recoding of Barnsley (E08000016 → E08000038) and Sheffield (E08000019 → E08000039). It remains in L0 but is not registered or used. LAD boundaries are published as "May 2025" (codes checked equal to G2's April 2025 LADs).
- **Reason:** SPEC 3 boundary vintage is April 2025. The build verifies that the edition used matches it exactly.
- **Effect on outputs:** Service-area polygons for the nesting proof and for display.

### D-0029: LA population is mid-2024, not mid-2025

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** P1b uses the mid-2024 UK estimates (`mye24tablesuk.xlsx`, 26 Sep 2025), although mid-2025 LA estimates now exist.
- **Reason:** SPEC 8.1 fixes mid-2024. LSOA estimates exist only to mid-2024, and gate 6 requires LSOA and LA figures from the same vintage (the SAPE notes state mid-2024 SAPE is coherent with this release). Mid-2024 is also the mid-period point for 2024/25 flow measures.
- **Effect on outputs:** All denominators are mid-2024. For 31 March 2025 stock measures the gap is 274 days (within `max_denominator_gap_days`).

### D-0030: Population is stored exactly as published

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** LSOA and MSOA facts hold what SAPE publishes: female and male by single year (`y00`–`y89`, `y90plus`) plus the persons all-ages total. Persons by single year is not published below LA level, so it is not stored. A persons denominator for any band is built at T7 as the exact sum of the female and male single years (both observed). LA, service area and England facts hold the published MYE2 Persons, Females and Males by single year and all ages. Unitary, metropolitan and London authorities appear once in the source and are loaded at both `lad` and `service_area` (same published figure).
- **Reason:** Principles 3 and 6 (observed values only; published first) and SPEC 4.3 (shared codes).
- **Effect on outputs:** `fact_small_area` and `fact_intermediate_area` have no persons single-year rows; T7 sums the two sexes.

### D-0031: Staging scope in Phase 1

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Only the period taken is staged (the mid-2024 sheets of the SAPE files and the MYE2 sheets of P1b); the other sheets stay in L0. NSPL (G4) is ingested now but staged in Phase 2, where it is first used. Boundaries are staged with every feature, including Wales, Scotland and NI where present (L1 is lossless). BSC boundaries and the ward, Sub-ICB and PFA boundary layers are deferred to the phases that need them.
- **Reason:** L1 is lossless for what is used. Unused periods add size without value.
- **Effect on outputs:** None.

### D-0032: How neighbours are computed

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Queen contiguity is computed from BFC geometry with a GEOS spatial-index `intersects` query (polygons sharing at least one boundary point). k-nearest neighbours (k = 6, 8) use libpysal on polygon centroids in British National Grid. Neighbours are England only, so English areas on the Welsh border have no Welsh neighbours.
- **Reason:** libpysal's vertex-matching contiguity keeps every vertex in memory; full-resolution LSOA boundaries would need several GB on a 15.5 GB machine. The predicate approach gives the same queen definition on exact shared boundaries.
- **Effect on outputs:** The `neighbours` table. Areas with no queen neighbour are listed in D-0034.

### D-0033: MSOA display names are applied at the serving layer

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** `dim_geography.area_name` keeps the official ONS names. House of Commons Library MSOA names (G10 v2.3, Open Parliament Licence) are staged now and joined into the serving views and boundaries in Phase 5, with attribution.
- **Reason:** The schema has one name column. ONS names are the official identifiers, and the HoCL names are a display aid under a different licence.
- **Effect on outputs:** Dashboard labels for MSOAs (Phase 5).

### D-0034: Nesting rule: OA unanimity proves membership; geometry is a 90% sanity check

- **Date:** 2026-10-19
- **Status:** decided (user decision, 2026-10-19; amends SPEC 4.2 step 2)
- **Decision:** Membership is proven by OA unanimity, which is exact. The BFC geometry test is an independent sanity check: each area must have ≥ 90% of its area in its assigned parent and ≤ 10% in any other parent (`config/geography.yaml`). SPEC 4.2's 99.9% is kept as a flag threshold. Flagged areas are written with their shares to `data/harmonised/nesting_flags.csv` and are not failures. `nesting_evidence` records, for every test, the shares in the assigned parent, in another parent and in no parent (e.g. `polygon_lad_99.730(other_0.270,none_0.000)`). The investigation that led to this rule (it halted Phase 1 under SPEC 4.2 step 3) found the following, from exact overlays of full-resolution (BFC) boundaries:
  - **Passes:** OA unanimity for all 33,755 LSOAs and 6,856 MSOAs. LSOA in its MSOA ≥ 99.9991% for all. LAD in its service area ≥ 99.946% for all. Codes match across all lookups and boundaries.
  - **Fails at 99.9%:** 2,360 LSOAs in their LAD (min 90.18%, median failing share 99.73%) and 779 MSOAs (min 95.00%).
  - For 2,234 of the 2,360 LSOAs, the uncovered part lies in a neighbouring LAD; the median sliver is about 1,700 m², concentrated in dense urban boroughs (Newham, Hackney, Kensington and Chelsea, Birmingham, Solihull). The rest lies in no LAD at all: coastline and estuary differences (Sunderland, Durham, Northumberland, Cornwall, Plymouth). No LSOA has more than 6.1% of its area in another LAD.
  - **Cause:** ONS statistical boundaries (OA/LSOA/MSOA) and administrative LAD boundaries trace the same line slightly differently. The failure count is essentially the same against the December 2021 LAD boundaries (99 vs 102 failures among 993 LSOAs in Newham, Birmingham and Hackney), so this is not caused by boundary changes since 2021. Membership is unambiguous.
  - **Listing:** The full list of failing areas, with their shares, is written by every build to `data/harmonised/nesting_failures.csv`. Listing all 3,139 codes here is impractical, so this entry records the counts and the method.
- **Reason:** SPEC 4.2 requires ≥ 99.9% polygon overlap. Official ONS boundaries cannot meet that for about 7% of LSOAs.
- **Effect on outputs:** Phase 1 cannot pass gate 4 until a rule is chosen.

### D-0036: Barnsley and Sheffield MYE relabelled to their April 2025 codes

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** The mid-2024 MYE (April 2024 boundaries) publishes Barnsley as E08000016 and Sheffield as E08000019; from April 2025 they are E08000038 and E08000039. The old → new pairs are recorded as data in `config/geography.yaml` (`code_successors`) and applied to P1b rows (`method_flag = 'relabelled'`), only where the source has no row for the new code.
- **Reason:**   - At the 2021 OA/LSOA resolution the change is a pure recode: no 2021 OA changed LAD, and the LSOA sums under the new codes equal the published MYE under the old codes exactly (251,770 and 582,493).
  - SPEC section 6 allows relabelling at L2.
  - The build re-asserts the exact equality for every relabelled cell, and gate 6 covers it.
- **Effect on outputs:** Barnsley and Sheffield get published LA population figures under their current codes. Any future successor pair must pass the same exact-equality check.

### D-0037: Areas with no queen neighbour

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** Two areas have no queen-contiguous neighbour: LSOA E01019077 (Isles of Scilly 001A) and MSOA E02006781 (Isles of Scilly 001). Each is the only area of its level in the Isles of Scilly (E06000053, flagged `is_small_authority`). Both have knn6 and knn8 rows.
- **Reason:** SPEC section 7 requires islands to be listed and to have knn rows. Hotspot analysis should use knn for these areas.
- **Effect on outputs:** The `neighbours` table.

### D-0038: Census ethnic group at LSOA uses the 6-category classification

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** P4 is Census 2021 `ethnic_group_tb_6a` × `resident_age_7a` (ages 0–4, 5–15, 16–17, 18–20, 21–24, 25–29, 30+), classification `census21_ew_6a`. Published MSOA, LTLA 2023, UTLA 2023 and England tables of the same specification are loaded at those levels.
- **Reason:** ONS disclosure rules block the 20-category ethnic group crossed with any age banding at LSOA (it is released at MSOA and LA). SPEC 8.1 asks for the most detailed classification allowed at LSOA × age; the 6-category version is that. D-0011 anticipated the rename.
- **Effect on outputs:** Ethnicity rows use the 6-category classification at every level, so comparisons stay within one classification (principle 15).

### D-0039: Census tables chosen for F6 and F7

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - F6 is one table, household composition (15) × bedroom occupancy rating (5). It gives all three household indicators, so their numerators and base come from the same perturbed cells.
  - F7a is disability × `resident_age_7a`.
  - F7b is unpaid care × `resident_age_3c`. Unpaid care × `age_7a` or `age_6b` is blocked at LSOA. Under-5s are coded "Does not apply", so carers aged 24 and under are carers aged 5–24, and the 5–24 base is the six non-"Does not apply" categories of the same table.
- **Reason:** These are the most detailed tables ONS releases at LSOA that answer the catalogue definitions exactly.
- **Effect on outputs:** Census proportions are internally consistent: a numerator never exceeds its base.

### D-0040: PIP uses March 2025, not January 2025

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** F4 takes PIP cases with entitlement for March 2025. UC households are also March 2025; DLA is February 2025, the closest quarter.
- **Reason:** SPEC 3 says to take the period closest to 31 March 2025. PIP is published monthly in Stat-Xplore, so March 2025 is available.
- **Effect on outputs:** The PIP reference date is 31 March 2025.

### D-0041: Police data: archive, LSOA vintage and assignment

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - The 2026-08 bulk archive is used: the latest archive covering April 2024 – March 2025, so it includes late resubmissions.
  - Open item 14.4 is resolved: the archive's LSOA codes are LSOA 2021 (all 34,363 distinct codes match).
  - A record's published LSOA code is its primary assignment. It is cross-checked against an independent point-in-polygon assignment on full-resolution boundaries, with the agreement rate reported.
  - Records with no coordinates, or outside England (Welsh forces, PSNI), go to `reject_point_assignment` with a reason.
  - British Transport Police files for February and March 2025 are missing from the archive. This is reported, not imputed.
  - Result: 5,966,690 records; 86,121 without coordinates. All 5,434,030 records with an English LSOA code were assigned (gate 11: 100%). The published code agrees with the full-resolution point-in-polygon for 96.5% of them. The 3.5% that differ are expected: published coordinates are snapped to anonymised map points, so a snapped point can fall in a neighbouring LSOA. That is why the publisher's code is used.
- **Reason:** SPEC T4, principle 6 (published assignment first), and principle 8 (no imputation).
- **Effect on outputs:** Police counts at LSOA (`point_assigned`), aggregated up the hierarchy.

### D-0042: Rate denominators

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - Population denominators are the published estimate for the level: SAPE for LSOA and MSOA, MYE for LAD, service area and England.
  - The denominator band is the exact sum of the single years covering the numerator band; `all_ages` uses the published total. Below LA level, persons = female + male (D-0030).
  - Other denominators (Census households and residents) come from the same table and area.
  - Stock numerators are compared with the denominator date at their period end; flow numerators at their period mid-point. A gap above `max_denominator_gap_days` gives no rate (`denominator_period_gap`).
- **Reason:** SPEC 3 (timing) and T7. Using a published figure at every level avoids building LA denominators from LSOA sums.
- **Effect on outputs:** Every rate's parameters record the denominator indicator, the CI method and the timing rule.

### D-0043: Truncated Stat-Xplore captures replaced (exception to write-once)

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** The first F2–F4 captures held only the first 100 areas of each geography: the Stat-Xplore schema endpoint pages values and my code read only one page. Those 12 files were deleted from L0 before anything was staged or derived from them, and re-captured with paging followed (`Link: rel="next"`). Staging checks that every requested area is present, for both Stat-Xplore and Census sources.
- **Reason:** They were defective captures caused by my code, not source data. Keeping them would have registered incomplete data. This is the only exception to write-once so far, and it is recorded here.
- **Effect on outputs:** None. Nothing was built from the defective files.

### D-0044: IoD 2025 catalogue corrections after inspection

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - Removed `mhclg_iod25_idaci_la_extent` and `mhclg_iod25_idaci_la_local_concentration`: IoD 2025 Files 10 and 11 publish extent and local concentration for the IMD only.
  - Polarity of the IMD and IDACI average rank and the IMD local concentration changed to `higher_worse`. In the 2025 summaries a higher value means more deprived (e.g. Hartlepool's IMD average rank is 23,076, ranked 30th most deprived).
  - Changed indicators carry `reviewed_date` 2026-10-20. The catalogue now has 121 indicators.
- **Reason:** The catalogue must describe what is published (principle 11).
- **Effect on outputs:** Dashboard colour direction for these measures.

### D-0045: ONS-blocked Census areas are suppressed

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** Where the ONS API withholds an area for disclosure (`blocked_areas` in the response), every affected indicator row for that area is NULL with `null_reason = 'suppressed'` and `source_code = 'blocked_by_ons'`. At LSOA: P4 1,015 areas, F7a 40, F7b 570, F6 none. MSOA and higher levels have no blocked areas. Staging checks that returned + blocked = requested, matching ONS's reported count.
- **Reason:** Principle 7: never zero-fill or back-calculate a suppressed cell.
- **Effect on outputs:** Those LSOAs show "suppressed" for the affected Census indicators. Published MSOA/LA values are unaffected.

### D-0046: Census indicator counts are exact sums of cells within one table

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** A Census indicator count, e.g. households with dependent children (four composition categories × all occupancy ratings), is the exact sum of the listed cells of one published table for one area. The cell lists are data in `config/category_maps.yaml`. The count is stored in L2 as `observed` with `n_components` = cells summed and a lineage hash of the component rows. No geography changes.
- **Reason:** The indicator definitions combine published categories. Doing it within one table and area adds no modelling. Using one table keeps numerator ≤ base.
- **Effect on outputs:** Census facts carry `n_components`. Census perturbation means these sums can differ slightly from a separately published total; reconciliation records any such difference.

### D-0047: IoD reference periods

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** IoD 2025 index values (scores, ranks, deciles, LA summaries) are dated 1 April 2022 – 31 March 2023. MHCLG states most inputs are from 2022/23. The IoD population denominators are dated 30 June 2022 ("mid 2022" in File 7).
- **Reason:** SPEC 3 asks for the actual period on every row.
- **Effect on outputs:** Period labels for IoD measures.

### D-0048: Police zero counts are observed zeros

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** An LSOA with no assigned records of a crime type gets count 0 (`point_assigned`), not NULL.
- **Reason:** The archive enumerates every located record for every English force-month in the period except BTP Feb/Mar 2025 (D-0041). No records in an area is an observed zero, not a suppressed cell (principle 7 concerns suppression).
- **Effect on outputs:** Complete LSOA coverage for police indicators.

### D-0049: Low-validity denominators for crime rates

- **Date:** 2026-10-20
- **Status:** decided (user sign-off, 2026-10-20). Evidence: the rule flags 338 LSOAs (cut-off 432 crimes per 1,000 residents against a median of 54). They are city and town centres and transport hubs: Westminster West End (18 LSOAs, up to 6,538 per 1,000), Camden, Birmingham, Liverpool, Brighton, Doncaster town centres, the City of London, and Hillingdon 031A (Heathrow).
- **Decision:** All five police rates are flagged `low_validity_denominator` in LSOAs and MSOAs whose all-crime rate (excluding ASB) is at or above England's 99th percentile at that level. These are mostly town centres and transport hubs, where the resident population understates who is present.
- **Reason:** SPEC T8 asks for a documented method. No daytime or workplace population is in scope for v1, so a transparent rank rule is used.
- **Effect on outputs:** About 1% of areas carry the flag on crime measures. A better exposure measure could replace this rule later.

### D-0050: DWP figures requested as DWP-produced groups

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** Combined categories (UC families with children, DLA under 16, PIP 16–24) are requested from Stat-Xplore as single groups, so DWP's own disclosure perturbation is applied to the combined cell. Component bands are also requested.
- **Reason:** Principle 6: a figure produced by the publisher is preferred to a sum of separately perturbed cells.
- **Effect on outputs:** Published totals at every level, with no sums of perturbed cells.

### D-0051: Census and DWP published levels, and T6 for the rest

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - Census and DWP figures are loaded as published at LSOA, MSOA, LA and England. Census LAs come from `ltla23`/`utla23`, with Barnsley/Sheffield relabelled per D-0036.
  - LSOA sums never replace a published level; they only fill `reconciliation`.
  - T6 aggregation fills only areas the publisher does not cover: police at every level above LSOA, and DWP county councils (summed from published LADs).
- **Reason:** Principle 6 and SPEC 8 ("never sum to a level the Census publishes").
- **Effect on outputs:** `method_flag` shows `observed`, `relabelled` or `aggregated` per row.

### D-0052: Undefined rates are NULL with a specific reason, never capped

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** A derived rate is NULL, with the published counts kept in L2, when:
  - **`zero_denominator`:** the published denominator is 0. Three LSOAs have an SAPE estimate of 0 people aged 16–19.
  - **`numerator_exceeds_denominator`:** a person-based (Wilson) measure has its numerator above its denominator. This happens where two independently produced sources disagree in a tiny cell, e.g. DWP's perturbed claimant count against ONS's modelled population: one LSOA has 6 DLA claimants aged 11–15 against 5 estimated children; another has 34 PIP claimants aged 20–24 against 21.
- **Reason:** A share above 100% is meaningless. Capping it, or replacing either input, would be imputation (principle 8).
- **Effect on outputs:** A handful of LSOA cells show these reasons instead of a rate. Gate 10 (proportions within 0–1) holds.

### D-0053: A Stat-Xplore 0 means "0 to 4" and is treated as suppressed

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** In every DWP Stat-Xplore output (F2–F4), a published 0 is stored as NULL with `null_reason = 'suppressed'`, `source_code = 'statx_0_means_0_to_4'` and bounds `count_lower = 0`, `count_upper = 4`. The rule is configured in `suppression_codes.yaml` (`max_hidden: 4`). T6 aggregates of such cells are NULL with lower and upper bounds. Reconciliation compares only complete sums. The published LSOA, MSOA, LA and England figures remain the values used (principle 6).
- **Reason:**   - **Evidence:** across all twelve DWP files (about 330,000 cells), the values 1, 2, 3 and 4 never occur, while 0 and 5+ are common. For example, the DLA LSOA cells have 34,573 zeros and 11,142 fives. Real counts would have many 1–4s, so Stat-Xplore publishes counts below 5 as 0.
  - **Effect seen in Phase 2 reconciliation:** under-5 DLA summed from LSOAs was 21% below the published England figure, and about 30% of DLA and PIP LA cells fell outside the draft tolerance.
  - **DWP guidance** ([Data Confidentiality](https://stat-xplore.dwp.gov.uk/webapi/metadata/Data%20Confidentiality.html)): cells are randomly adjusted, "no reliance should be placed on small cells", and "published data for the larger area should be used wherever possible". The note does not state the below-5 rule; the data do.
  - Census outputs do not show this pattern (values 1–4 are frequent), so Census zeros remain observed zeros.
- **Effect on outputs:** DWP LSOA cells that were 0 now show "suppressed (0–4)" rather than a false zero: about 73% of LSOAs for DLA under-5, 2.4% for DLA under-16 and 0.2% for UC households with children. Their rates are NULL. Sums of LSOAs for custom areas carry bounds instead of a biased total.

### D-0035: Exact overlay method for nesting tests

- **Date:** 2026-10-19
- **Status:** decided
- **Decision:** Polygon shares are computed by subdividing each parent polygon into pieces of at most 1,000 vertices (recursive halving with robust box intersection, as PostGIS ST_Subdivide does), then intersecting each child only with the touching pieces. The earlier fast path (`shapely.clip_by_rect`) is not used: GEOS documents that it may not return the exact intersection, and it reported 0% for three LSOAs that lie fully inside their MSOA.
- **Reason:** A proof test must be exact. Unit tests confirm the subdivision partitions area exactly.
- **Effect on outputs:** `nesting_evidence` values. A full run takes about 4–5 minutes.

### D-0054: Phase 3 sources and how they are taken

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** Each DfE source (C1–C4, E1–E6, P7) is ingested as the release's own "download all files" zip from Explore Education Statistics. Only the LA tables the catalogue needs are staged, at the reference period. The other sources:
  - **F1:** two routes.
    - The published ODS gives LA counts and percentages for ages 0–15.
    - Stat-Xplore (CILIF_REL, CILIF_ABS, year 2024/25) gives the age bands 0–4, 5–10, 11–15 and 16–19, plus all ages 0–19 including unknown age, as DWP-produced groups at LA and country level.
  - **H2:** one Fingertips CSV export (`all_data/csv/by_indicator_id`, area type 502, parent England).
  - **Ho1:** the January–March 2025 detailed LA tables (TA1), the additional TA tables (TA8) and the corrected 2024-25 annual tables (A5P, A5R, A6).
  - **C5:** Ofsted's two underlying-data files.
  - **S5:** Asy_D11 from the June 2026 support local authority dataset, at the 31 March 2025 quarter.
- **Reason:** One file per release keeps provenance simple and lets every table be checked against the publisher's own files (principle 11). CiLIF age bands exist only on Stat-Xplore. The ODS is the official table for 0–15 counts and percentages.
- **Effect on outputs:** 21 L0 files. H3 is not loaded (D-0055).

### D-0055: NDTMS parents in treatment (H3) is blocked

- **Date:** 2026-10-20
- **Status:** decided (user, 2026-10-21)
- **Decision:** H3 is not loaded. No machine-readable LA file was found:
  - `ndtms.net` ViewIt/Adult has no download.
  - The ViewIt archive CSV ends in 2023.
  - The parent and child figures are only in the interactive "Prevalence and unmet need toolkit" (`reportId=parental`).
  - Fingertips has no "living with children" indicator.
  - Scraping a web report is excluded (principle 11).
- **Reason:** No verified file exists to ingest.
- **Effect on outputs:** Two indicators are empty. The SPEC 12.1 LA need index loses one input until the user places an NDTMS LA extract (2024-25) in `data/raw/manual/H3/`, or chooses another source.

### D-0056: CIN assessment factors: exact columns, same-table base, alcohol and drugs kept apart

- **Date:** 2026-10-20
- **Status:** decided (user, 2026-10-21)
- **Decision:** The catalogue's factor indicators are built from DfE CIN table C3 as follows:
  - **Factors used:** the parent-related columns, as the "toxic trio" framing intends: `Domestic_Abuse_parent` ("concerns parent is victim"), `Mental_Health_parent`, `Alcohol_Misuse_parent` and `Drug_Misuse_parent`. The `_child` and `_person` variants are not added in, because one episode can carry several factors and adding columns would double-count.
  - **Denominator:** the table's own `Episodes_with_assessment_factor`, as DfE uses, not assessments completed. It is a new catalogue entry, `dfe_cin_episodes_with_assessment_factors`.
  - **Substance misuse split:** `dfe_cin_factor_parental_substance_misuse` is replaced by `dfe_cin_factor_parental_alcohol_misuse` and `dfe_cin_factor_parental_drug_misuse`, because the two cannot be added without double-counting episodes. `config/composites.yaml` lists both.
- **Reason:** Each proportion must count episodes once (Wilson CI). The DfE file publishes no "alcohol or drugs" column.
- **Effect on outputs:** Four factor proportions on DfE's own base, and one more indicator in the catalogue. The composite domain needs sign-off on whether both substance indicators enter it or only one.

### D-0057: Placement distance and stability use same-table denominators

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - **Placed more than 20 miles from home:** divided by children whose distance is known. That base is the exact sum of the two published cells "20 miles or less" and "more than 20 miles" in the same table (new denominator `dfe_cla_distance_known_at_31mar`), as DfE excludes unknown distances.
  - **3+ placements:** divided by the same table's "Total children" for "CLA on 31 March" (new denominator `dfe_cla_stability_base_at_31mar`).
- **Reason:** The catalogue's verify note. A same-table base removes cross-table mismatch.
- **Effect on outputs:** Two new denominator indicators. These proportions match DfE's published percentages, rounding aside.

### D-0058: Free school meals by LA of school; pupils indicator renamed

- **Date:** 2026-10-20
- **Status:** decided (user, 2026-10-21)
- **Decision:** The 2024/25 SPC release publishes LA FSM eligibility by school location only. Its residence-based table (`spc_cbm`) has headcounts and no FSM. So:
  - `dfe_fsm_eligible_pupils` uses the FSM performance-table pair from `spc_pupils_fsm`: the "known to be eligible …" headcount over the "number of pupils (used for FSM in Performance Tables)" headcount, by LA of school.
  - The denominator `dfe_pupils_on_roll_residence` is renamed `dfe_pupils_on_roll`, with its definition corrected.
  - SEN (E1), absence (E3) and exclusions (E4) are also by LA of school (the headline LA tables).
- **Reason:** The residence basis assumed in Phase 0 is not published. Numerator and denominator must share one basis.
- **Effect on outputs:** In LAs with large cross-border pupil flows, FSM and SEN rates describe the LA's schools rather than resident children.

### D-0059: Units and published values in Phase 3

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - **CiLIF percentages** are published as fractions (0.27) and are stored ×100, so that every `percent_published` value is on the 0–100 scale. This is an exact rescale.
  - **Section 251 spend** is DfE's unrounded `net_current_expenditure` in GBP, from the total lines 5.0.2 (all CYP services excluding CERA), 3.1.11 (children looked after), 3.4.6 (family support) and 3.5.3 (services for young people).
  - **Workforce rates** (vacancy, agency, turnover; FTE basis) and the average caseload per case-holding FTE are stored as published (one decimal place).
  - **EHCP 20-week timeliness** uses DfE's headline basis, excluding exceptions.
- **Reason:** Principle 6 (published first) and D-0016.
- **Effect on outputs:** Spend per child is derived with MYE denominators (D-0017).

### D-0060: LA codes: successors, joint reporting and defunct counties

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - **Successor codes:** DfE, Fingertips, H-CLIC, Ofsted and asylum data still use E08000016 (Barnsley) and E08000019 (Sheffield). These are relabelled to E08000038 and E08000039, as in D-0036. Some DfE tables (S251 spend, EHC plans) also still use the pre-unitary county codes for Buckinghamshire (E10000002), North Yorkshire (E10000023) and Somerset (E10000027). Each unitary covers exactly the former county's area, so these are added to `code_successors` and relabelled to E06000060, E06000065 and E06000066. Relabelling is decided per indicator, and only where the new code is absent. `code_successors` no longer forms part of the geography cache key, because the geography build never reads it.
  - **Joint services:** the social work workforce release reports two joint services: North Northamptonshire with West Northamptonshire, and Kingston upon Thames with Richmond upon Thames. Each member LA gets a NULL row with `null_reason = 'not_published'` and `source_code = 'reported_jointly:<codes>'`. The joint figure is not split or copied (principle 8).
  - **Defunct counties:** codes not in the April 2025 hierarchy (CLA rows for the former counties of Cumbria and Northamptonshire) are dropped. The build reports every dropped code (`_harmonise_report.json`, `phase3.tables.dropped_codes`).
- **Reason:** No figure can be invented for one member of a joint service. Former counties no longer exist.
- **Effect on outputs:** Four UTLAs have no workforce figures.

### D-0061: H-CLIC symbols, missing authorities and counties

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - **`..`** (authority with missing data) is `not_published`.
  - **`-`** (breakdown suppressed below 5) is `suppressed` with `count_upper = 4`. In TA8, every `-` row has a total of 0–4.
  - **LAD figures** are loaded as published.
  - **Counties** (service areas) are T6 sums of their districts, NULL where any district is missing or suppressed.
  - **England totals** are MHCLG's published figures. They include estimates for missing authorities and are rounded to 10. TA8 has no England row, so England is the T6 sum and is NULL when any authority is missing.
- **Reason:** SPEC 8.4 (non-submission is `not_published`; national totals include imputation). The table footnotes give the symbol meanings.
- **Effect on outputs:** LA sums do not equal published England totals. The gap is shown in `reconciliation` (D-0065).

### D-0062: Ofsted children's homes and ILACS

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - **Children's homes:** follows Ofsted's own "All Children's Homes" total (Table 6a): children's homes (two spellings occur in the file), secure children's homes, and residential special schools registered as children's homes, at any registration status.
  - **LA matching:** the provider file names LAs but gives no codes. Names are matched to UTLA names, with four aliases (Bristol, Durham, Herefordshire, Kingston upon Hull). Welsh LA names are excluded.
  - **National check:** the build stops unless LA sums equal Ofsted's published national 4,009 homes and 15,742 places.
  - **Zeros:** LAs with no home get an observed 0, because the file lists every registered provider.
  - **ILACS:** the overall effectiveness label is coded 1–4 (`categories.yaml`), with the inspection date as the period.
  - **Level and safeguarding:** everything goes to `fact_service_area` only (gate 14). Provider names, addresses and postcodes are not staged (principle 13).
- **Reason:** Using the publisher's own definition makes the national check exact.
- **Effect on outputs:** Counts of homes and places for all 153 UTLAs.

### D-0063: Fingertips series and notes

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** For each H2 indicator, the latest period ending on or before 31 March 2025 is used:
- **Reason:** The rule in `sources.yaml` ("latest period ending on or before 31 March 2025"). Fingertips publishes combined values for the two smallest LAs.
- **Effect on outputs:** H2 periods differ by indicator. Each is recorded in `period_start` and `period_end`.

### D-0064: NEET 16–17 reference period

- **Date:** 2026-10-20 (confirmed 2026-10-21)
- **Status:** decided
- **Decision:** In the 2024/25 NEET release, `time_period = 2025` is the average of December 2024, January 2025 and February 2025, stored as 1 December 2024 to 28 February 2025. This was inferred in Phase 3 and is now confirmed from two sources:
  - The DfE methodology page: "We therefore take an average estimate from Dec/Jan/Feb for the NEET figures to give an end of year estimate."
  - The release page, which describes its figures as "at the end of 2024/start of 2025" and gives Dudley as 21.5% NEET or not known (2.4% + 19.1%). Our `time_period = 2025` row for Dudley has 2.35% + 19.10% = 21.45%.
- **Reason:** Closest measure to 31 March 2025.
- **Effect on outputs:** NEET period labels. No change to values.

### D-0065: Phase 3 reconciliation: LA sums against England

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:** Phase 3 has no LSOA data, so each summable count is reconciled as follows: the sum of service-area figures (published, or T6 sums of published LADs) against the published England figure, written to `reconciliation` with `area_level = 'nation'`. Sums with a suppressed or missing component are not computable and are counted in `phase3.reconciliation_not_computable`.
- **Reason:** Evidence for the draft SDC tolerances. Most publishers round England to 10 and secondary-suppress LA cells. H-CLIC also imputes missing LAs.
- **Effect on outputs:** Reconciliation rows for Phase 3 counts. Gaps are reported, not corrected.

### D-0066: EHCP, CLA and CiLIF age bands

- **Date:** 2026-10-20
- **Status:** decided
- **Decision:**   - **EHC plans** are published by single year (under 3, 3 … 25). Standard bands 0–4 to 21–24 are exact sums of those cells (the D-0046 rule). The 0–25 total is DfE's own.
  - **CLA at 31 March** uses DfE's age groups. Under 1, 1–4, 5–9 and 10–15 are new source bands. "16 years and over" is stored as 16–17, because looked-after children are under 18.
  - **CiLIF:**
    - The DWP bands 0–4, 5–10 and 11–15 are standard.
    - 16–19 stays a source band (dependent children only).
    - 0–19 includes unknown age.
    - The ODS 0–15 count is `src_0_15`.
  - **Ward and small-area CiLIF:** ward counts (May 2024 wards) wait for Phase 4 (other geographies). LSOA and MSOA CiLIF exist on Stat-Xplore (open item 14.2) but are outside the approved catalogue.
  - **Missing single-year EHCP rows:** DfE leaves out single years with no plans. In every one of the 153 LAs (and England), the published single-year rows sum exactly to DfE's "All EHC plans" total, so an absent year is 0. The build re-proves this every run before treating an absent row as 0 (`absent_rows_zero`, `source_code = 'absent_row_zero'` where a whole band is absent).
- **Reason:** SPEC 3: never split or trim a source band.
- **Effect on outputs:** Rates by age band use exact MYE single-year sums.

### D-0067: NEET uses DfE's published proportions

- **Date:** 2026-10-20
- **Status:** decided (user, 2026-10-21)
- **Decision:**   - **Published proportions:** `dfe_neet_16_17` and `dfe_neet_or_not_known_16_17` change from derived Wilson proportions to `percent_published`, using DfE's own NEETprop and NEETNKprop. They have no CI and cannot be aggregated.
  - **Cohort:** `dfe_neet_cohort_16_17` keeps DfE's average cohort, stored in `value` (not `count`) and marked not summable.
- **Reason:** DfE publishes NEET counts as averages of three monthly snapshots (e.g. a cohort of 7,034.33), so they are not whole numbers. Rounding them to build a Wilson interval would alter published data. DfE's own proportion is the published figure (principle 6).
- **Effect on outputs:** No confidence intervals for NEET. Custom regions get no NEET value. Values match DfE's tables exactly.

### D-0068: Section 251 spend per child uses ONS population, not DfE's per-capita figures

- **Date:** 2026-10-21
- **Status:** decided (user, 2026-10-21)
- **Decision:** Per-child spend stays as derived (D-0017): DfE net current expenditure divided by the ONS mid-2024 estimate of 0–17 year olds (13–19 for youth services). DfE's own `per_capita_net_current_spend` column is not loaded.
- **Reason:** The same population basis as every other LA rate keeps measures comparable. The Phase 3 spot-check found the following:
  - Spend matches DfE exactly in all five LAs checked.
  - DfE's implied populations are within about 1% of ONS for Barnsley, Kent and North Northamptonshire, and 4.6% higher for Bristol.
  - For Camden, DfE divides by about 54,900 children, but the ONS mid-2024 estimate of 0–17 year olds is 35,300.
- **Effect on outputs:** Camden's per-child spend is about 56% higher than DfE's published figure. This is noted on the indicators and is to be reported to DfE (statistics.development@education.gov.uk) and recorded in the methodology pack.

### D-0069: Phase 4 sources and access

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:**   - **G3:** LSOA21 to Sub-ICB location to ICB lookup, April 2024 configuration (106 SICBLs, 42 ICBs), the one MHSDS 2024/25 reports on.
  - **G8:** LAD to CSP to PFA lookup, April 2025 (296 LADs, 39 English PFAs).
  - **G3b:** NHS England GP registrations at 1 April 2025, two files: single year of age by SICBL, and practice × LSOA21 (all ages).
  - **H1:** the MHSDS end-of-year final March 2025 file.
  - **S3:** youth justice statistics 2024-25 local open data and supplementary tables.
  - **S4:** the four quarterly NRM table releases for April 2024 to March 2025.
  - **G7:** constructed (D-0071).
  - **G9:** not needed (police and GP data use LSOA21).
  - **Access to digital.nhs.uk:** pages refuse scripted requests (Cloudflare 403), so publication pages were read through the public mirror `nhsd-proxy.openprescribing.net`. Every file is downloaded directly from `files.digital.nhs.uk`; the manifest records that URL and its hash.
- **Reason:** Principle 11: each file is verified from its publisher's page.
- **Effect on outputs:** 11 L0 files.

### D-0070: GP-registered population: Sub-ICB by age; LSOA all ages for weights only

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:** NHS England publishes no LSOA × age file (the LSOA files are practice × LSOA × sex, all ages). Therefore:
  - **Denominator:** `nhse_gp_registered_patients` is loaded as published by SICBL, single year of age by sex (ages 90–94 and 95+ summed to `y90plus`). It is the H1 denominator.
  - **England total:** the exact sum of the 106 SICBLs (aggregated, `fact_nation`), because SICBLs partition England.
  - **T5 weights:** the LSOA21 all-ages file is used only for T5 weights (`lkp_apportion_weights`, basis `gp_registered_all_ages_20250401`).
  - **Denominators are never apportioned:** all-ages weights cannot spread an age-specific population.
- **Reason:** SPEC 4.4 requires a GP-registered basis for health, and this is the finest published form.
- **Effect on outputs:** The H1 rates use the published registered population. Overlap estimates use all-ages weights for a 0–17 measure, which is stated in `parameters`.

### D-0071: Youth justice service composition (G7) is constructed

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:** There is no published YJS-to-LA lookup. `config/yjs_composition.yaml` maps each of the 138 English YJSs in the 2024-25 data to UTLAs, with evidence on every row:
  - By exact name or a short-name alias (Bristol, Durham, Hull, Leicester City).
  - Members named in the YJS name: Bury and Rochdale; Cheshire East, Cheshire West, Halton and Warrington; Kingston and Richmond; Tower Hamlets and City of London; and Cornwall and the Isles of Scilly (GOV.UK South West contact page).
  - By elimination, every UTLA belonging to exactly one YJS: Bedfordshire (Bedford, Central Bedfordshire), Dorset Combined (Dorset, BCP), Northamptonshire (North, West), South Tees (Middlesbrough, Redcar and Cleveland), West Mercia (four UTLAs) and Leicestershire (with Rutland).
- **Reason:** SPEC 8.1 G7: the composition is constructed, with the method recorded.
- **Effect on outputs:** 127 YJSs are coterminous with one UTLA and relabelled. The rest contain several UTLAs, so those UTLAs see a labelled fallback.

### D-0072: MHSDS measures and their handling

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:**   - **Children with 1+ contact:** MHS95 (CYP under 18 with at least one contact, 12 months to 31 March 2025, "Sub ICB of GP Practice or Residence").
  - **Open referrals:** CYP23 (open referrals to CYP mental health services at 31 March 2025). Its age band is `na`, because it counts referrals to CYP services, not people of a stated age.
  - **Rounding and suppression:** Sub-ICB values are rounded to 5; `*` is suppressed. England figures are unrounded and loaded as published.
  - **UNKNOWN rows:** MHS95 4,825, CYP23 5,375. They have no area and are excluded.
  - **MHS95 is not summable:** the Sub-ICB sum (847,920) exceeds England (840,063), because a child can be counted in two Sub-ICBs. It is never aggregated or apportioned.
- **Reason:** These are the catalogue's MHSDS measures, and these are the publisher's rules.
- **Effect on outputs:** MHS95 rates per 10,000 GP-registered 0–17 at SICBL, England (673.5) and coterminous UTLAs and LADs. CYP23 counts at SICBL, with T6b and T5 conversions.

### D-0073: First-time entrants are LA-level published rates, calendar 2024

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:** `yjb_first_time_entrants_10_17` changes from a derived YJS rate to YJB/MoJ's published rate per 100,000 aged 10–17, by LA of residence, for the year ending December 2024 (supplementary table 2.11; FTE are not published by YJS or for years to March).
  - **Model-based:** counts are allocated to LAs by PNC home address, and by a model where there is no address. That is why counts have decimals, and the estimate type is `model_based`.
  - **Symbols:** `..` = fewer than 10 (suppressed, at most 9). `*` = a former area after a boundary change. A `*` row gives way to the current area's published figure where both carry one name (Dorset).
  - **Name aliases:** five aliases match spelling slips in the table ("West Morland and Furness", "... and the Humber").
- **Reason:** Principle 6 (published first), and the published geography is LA, which sits directly on the hierarchy.
- **Effect on outputs:** 149 of 153 UTLAs have a value; 4 are suppressed.

### D-0074: NRM child referrals are at police force area level

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:** Open item 14.7 is resolved. The NRM tables have no LA-of-residence breakdown, so `ho_nrm_referrals_under18` is the "Child (17 or under)" column of Table 10, by police force responsible for investigation.
  - **Period:** the exact sum of the four quarterly releases for April 2024 to March 2025, as first published (later revisions are not captured).
  - **Forces:** force names are mapped to PFA25 (`category_maps.yaml`). British Transport Police has no area and is excluded.
- **Reason:** The police force table is the only one that places a child referral in an area. The first-responder table records who referred, not where the child lives.
- **Effect on outputs:** Rates per 10,000 children for 39 PFAs. The 8 UTLAs coterminous with a PFA get relabelled values. Other UTLAs see a labelled PFA fallback, so the indicator cannot enter the LA system pressure composite as planned (Phase 6 to decide).

### D-0075: Relationship classification, T6b, T5 and fallbacks

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:**   - **Classification:** each other-area / hierarchy-area pair is classified from shared membership units: LSOA21 for SICBL (G3, exact because LSOA nesting is proven), LAD25 for PFA (G8), and UTLA for YJS (G7).
    - **coterminous:** the shared count equals both sizes.
    - **nests_within:** it equals the other area's size.
    - **contains:** it equals the hierarchy area's size.
    - **overlaps:** otherwise.
- **Reason:** SPEC 4.4 and T5/T6b. Open item 14.6 is resolved.
- **Effect on outputs:** Relationship pairs at service-area level:

### D-0076: Police point assignment is cached and runs first

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:** The S1 point-in-polygon step (5.4 million records) runs before the large fact frames are built, and its output is cached in `data/harmonised/police_cache/<key>`. The key hashes the S1, G5 and geography source files, the `phase2.py` code and the crime-type map. The snapshot ID is restamped on reuse.
- **Reason:** As the build grew, the step failed intermittently with memory allocation errors on this 16 GB machine. Its inputs rarely change.
- **Effect on outputs:** None on content. Builds are faster and more reliable.

### D-0077: Ward-level child poverty (F1) is not loaded

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:** DWP's ward tables (children 0–15, May 2024 wards, no percentages) are not loaded. The hierarchy's ward layer is May 2025 (WD25), and there is no published lookup between the two ward vintages here.
- **Reason:** Loading would mean either a code-matching approximation or a new lookup, for counts the LA and LSOA layers already cover.
- **Effect on outputs:** No CiLIF at ward level. LSOA and MSOA CiLIF exist on Stat-Xplore if wanted later (open item 14.2).

### D-0078: Release boundaries

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:** `boundaries.gpkg` holds the ONS generalised (BGC) layers for LSOA21, MSOA21 (with House of Commons Library names), LAD25 and UTLA25, filtered to England and keyed on `dim_geography.area_code`.
  - **Other geographies are dissolved, not downloaded:** each is an exact union of hierarchy areas (Sub-ICB = LSOAs via G3; PFA = LADs via G8; YJS = UTLAs via G7), so the layers are dissolved from those BGC layers. No April 2024 Sub-ICB boundary file exists on the ONS portal; the published PFA boundary vintage (December 2024) differs from the April 2025 lookup.
  - **No PMTiles:** the toolchain (tippecanoe or similar) is not installed, and SPEC 11 makes tiles optional.
- **Reason:** SPEC 11 (BGC for display; one-to-one with `dim_geography`). Dissolving keeps every layer consistent with the relationships used in the data.
- **Effect on outputs:** Seven layers (33,755 / 6,856 / 296 / 153 / 106 / 39 / 138 features). Gate 15 checks the hierarchy layers against `dim_geography`.

### D-0079: Serving layer and profile views

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:**   - **Serving views:** `serve_<level>` is rendered from `sql/serving.sql`, one row per area × profile column used at that level. The display value is:
    - the derived rate for indicators with a rate multiplier;
    - the count for counts;
    - otherwise the published or derived value (IoD MSOA summaries, overlap estimates);
    - for ordinal indicators, a category code with its label.
  - **Rows without a value:** a pair with no value carries the stored reason, or `not_published` (e.g. DfE measures for district councils at `lad` level).
  - **Fallbacks:** fallback rows come only from `fallback_other_geography`.
  - **Profile views:** `profile_<level>` is generated at serve time from `dim_profile_column`, using native values only, so its columns depend on the data. The generated SQL is published in the release.
  - **Population bands:** profile population bands (0–17, 0–24, 0–25) are added to L2 as exact sums of the published single years (the D-0046 rule). Rates still build their own denominators from single years.
  - **Profile columns:** the CiLIF percentage columns use ages 0–15, the band DWP publishes, and a profile column was added for proven offences.
- **Reason:** SPEC 7.2 and 7.3. Gate 15 checks that every row has a value or a reason, that fallbacks stay out of profiles and derived tables, and that boundaries match.
- **Effect on outputs:** Serving rows are about 7,800 at service-area level and 14,800 at LAD level; about 970 are fallback rows.

### D-0080: Reproducibility check (gate 17)

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:**   - **How it runs:** `cypneed verify-rebuild` hashes every table of the working DB (logical content hashes: rows sorted by primary key, fixed serialisation), rebuilds from L0 (stage, then harmonise with the geography and police caches switched off by `CYPNEED_NO_CACHE`, then derive and serve), and hashes again. The report is `data/qa/reproducibility.json`.
  - **How it is published:** `cypneed release` publishes the report only if it is for the same snapshot and every table hash equals the release's `content_hashes.json`. Gate 17 then requires it.
- **Reason:** SPEC gate 17: a clean rebuild at the same commit gives identical logical content. Turning the caches off proves they do not change content.
- **Effect on outputs:** A release needs a verify-rebuild at its commit first (about an hour on this machine).

### D-0081: Release package format

- **Date:** 2026-10-21
- **Status:** decided
- **Decision:**   - **Contents:** the release directory holds a copy of the working DuckDB (all tables and views), Parquet (zstd) and CSV for every table and public view, sorted by primary key, and the serving views as Parquet with `serve_indicator_meta.json`.
  - **Data dictionary:** `data_dictionary.csv` (`dim_indicator`) and `data_dictionary_columns.csv` (every column of every table and view, with descriptions from the schema comments).
  - **Other files:** `sources.csv`, `coverage.csv`, `reconciliation.csv`, `qa_report.md`, `README.md`, `content_hashes.json` and `methodology/`.
  - **Methodology pack:** Markdown, plus a static HTML build rendered with Python-Markdown (no MkDocs), with links rewritten to the HTML pages.
  - **Build safety:** the package is built in `<snapshot>.building` and renamed only after every step has succeeded.
- **Reason:** SPEC 11 and 11.1, with the smallest toolchain that renders the pack.
- **Effect on outputs:** One self-contained directory per snapshot.

### D-0082: Exports for Microsoft Fabric and Power BI

- **Date:** 2026-10-22
- **Status:** decided (user, 2026-10-22: items 1–4)
- **Decision:** The dashboard will be built in Microsoft Fabric / Power BI, so the release adds:
  1. **Delta tables:** `delta/` holds one Delta table per exported table and view, written with delta-rs, for Direct Lake.
  2. **Single-column keys:**
     - `geo_key` (`'<level>|<code>'`, or `'<geography type>|<code>'` for other geographies) on every exported table and view with an area. The lookup also has `other_geo_key`.
     - `serve_dim_area`: one row per area and other area, with parent keys.
     - `serve_dim_measure`: one row per profile column, key `column_prefix`. Power BI relationships cannot join on two columns, and a unitary council is both a `lad` and a `service_area`.
  3. **Numerator and denominator in serving:** `numerator` and `denominator` are added to every serving view (NULL for values, categories and fallbacks), so DAX can aggregate custom selections correctly.
  4. **TopoJSON maps:** `maps/` holds TopoJSON in WGS84, simplified for Power BI map visuals:
     - whole-England files for UTLA, LAD, MSOA, Sub-ICB, PFA and YJS;
     - MSOAs and LSOAs per children's services authority.
- **Reason:** Power BI cannot read DuckDB, GeoPackage or composite keys, and it limits map file sizes. Delta is Fabric's native table format.
- **Effect on outputs:** More files in the release, and three columns added to serving views. There is no change to any value. Methodology links stay relative until a hosting address is chosen.

### D-0083: IoD domain summaries for councils

- **Date:** 2026-10-22
- **Status:** decided
- **Decision:** Fourteen indicators are added from MHCLG's published LAD and UTLA summaries (IoD 2025 Files 10 and 11, the domain sheets of the D1b workbook): for each of the seven domains, the population-weighted average score (`mhclg_iod25_<domain>_la_avg_score`) and the proportion of LSOAs in the most deprived 10% nationally (`..._la_prop_most_deprived_10pct`).
  - **Domains:** income, employment, education, health, crime, barriers, living environment.
  - **Profiles:** each domain's average score becomes a profile column.
- **Reason:** The domain indicators were LSOA-only, so a council-only view had no value for them. MHCLG publishes the LA summaries, so no calculation is needed (the same rule as IDACI and IMD, D1b).
- **Effect on outputs:** 139 indicators. Seven domains now have council values.

### D-0084: Asylum support: councils absent from Asy_D11 are zero

- **Date:** 2026-10-22
- **Status:** decided
- **Decision:** Asy_D11 lists only LAs with at least one person supported: no row has 0, and there are no suppression symbols. At 31 March 2025, 17 England LADs are absent (for example Isles of Scilly, Fenland, Derbyshire Dales, Mid Devon, Torridge, West Devon, Rother, Maldon, Cotswold, Hart). Each absent England LAD is stored as an observed 0 (`source_code = 'absent_area_zero'`), but only after the workbook proves that every person in England is assigned to a listed LA:
  - The workbook's own pivot (`Asy_D11` sheet, filters Support Type and Accommodation Type both "(All)") gives published totals by UK region. The nine English regions sum to 94,754, exactly the sum of the England LA rows.
  - The "N/A - Subsistence Only" row (people with no LA) is 0 at 31 March 2025.
  - Harmonise checks both of these and stops if either fails. Staging checks the pivot filters.
  - Barnsley and Sheffield appear under their pre-2025 codes and are relabelled as before (D-0036).
- **Reason:** Absent here means nobody was supported in that LA on that date. Leaving these LAs NULL made 13 county totals and the England total `incomplete`.
- **Effect on outputs:** `ho_asylum_support_recipients` has a value for all 296 LADs, 153 service areas and England (94,754).

### D-0085: County child poverty percentages by DWP's method

- **Date:** 2026-10-22
- **Status:** decided (replaces the "no rate" position on the CiLIF percentages for areas DWP does not cover)
- **Decision:** DWP publishes CiLIF percentages for lower-tier and unitary councils, but not for the 21 county councils. DWP's note 3 states the method: children aged 0-15 in low income families / mid-2024 ONS population aged 0-15. For a county, the percentage is computed by that method from the summed published district counts and our ONS mid-2024 single years:
  - **Proof first:** before anything is filled, derive recomputes every published percentage by the same method and requires agreement within 1e-9. All 428 published values (296 LAD, 132 service area) agree exactly. Any miss stops the build.
  - **Stored as derived:** rows are derived (`derivation = 'published_method'`), never L2 facts, with numerator and denominator kept. They are filled only where DWP publishes no value.
  - **Serving:** the value is shown in the same column as the published percentages, with `estimate_type` = `survey_calibrated (derived by the publisher's method)` and the profile flag `publisher_method`.
  - **Percentiles:** percentiles rank the published and derived values together.
  - **Generic:** this is the catalogue field `publisher_method_fill`, which other indicators can use only with the same proof.
- **Reason:** The method is DWP's own and is shown to reproduce DWP's figures exactly, so the county value is what DWP would publish. Flagging keeps it distinguishable from published figures.
- **Effect on outputs:** CiLIF percentages at service-area level cover 153 of 153 councils (was 132).

### D-0086: L5 composite build: where it reads, writes and shows

- **Date:** 2026-10-22
- **Status:** decided
- **Decision:**   - **Reads:** `cypneed composite` reads the snapshot's L2 facts and L3 derived values from the working DB, after `serve`. It writes only `l5_*` tables, so L0-L4 never change. SPEC 12 says "reads L4 only"; the serving views don't carry EB-smoothed rates or the indicators without a profile column (the CIN assessment factors), so L5 reads the same frozen L2/L3 values that L4 is built from.
  - **Inputs (12.2):**
    - indicators with a derived rate: the L3 rate built from L2 counts, EB-smoothed at LSOA and MSOA;
    - other indicators: the L2 published value, or, where none is published, an L3 value made by the publisher's own method (IoD MSOA summaries, D-0085 county percentages).
    - Never used: fallback, apportioned, converted or recoded values.
    - Age band: the indicator's profile column band, or its only band.
  - **Tables (12.6):**
    - `l5_composite_<level>` and `l5_domain_<level>` for small_area, intermediate_area and service_area. Columns as SPEC 12.6, plus `rank_median`.
    - `l5_eligibility`, `l5_runs` (Monte Carlo design per run), `l5_sensitivity` (results per choice) and `l5_criterion_residuals`.
    - Per-area, per-run ranks are not stored (34 million rows at LSOA); they are reproducible from the seed.
  - **Catalogue:** every composite and domain score is generated into `dim_indicator` from `composites.yaml` (theme `composite`, estimate type `composite_experimental`, framework role `composite`), so the catalogue cannot drift from the definitions. Each has a profile column and appears in the serving views through the `l5_scores` view.
  - **QA:**
    - Gate 19 reports SPEC 12.8: eligible inputs only; weights sum to 1; a seeded recomputation of the LA composites equals the stored tables exactly; the median rank lies within the interval; NULLs have a reason; the validation report exists.
    - `verify-rebuild` now runs `composite`, so gate 17 also covers the neighbourhood composites.
  - **Release:** the release refuses to run unless the L5 tables and reports are for the same snapshot. It writes `l5/` (tables, `l5_validation.md`, `l5_report.json`), and the methodology pack takes the validation write-up.
- **Reason:** SPEC 12 and 12.8, with one reproducible build path.
- **Effect on outputs:** 16 more `dim_indicator` rows and profile columns, ten `l5_*` tables, gate 19, and a `composite` step between `serve` and `release`.

### D-0087: Composite domain assignment and eligibility (Phase 6)

- **Date:** 2026-10-22
- **Status:** decided (user accepted, 2026-10-23)
- **Decision:** The SPEC 12.1 starting point, with these changes. Eligibility is re-tested at every level for every release, so the indicators that are ineligible today stay listed and enter once they qualify.
  - **Removed:**
    - `dwp_uc_households_with_children` (neighbourhood economic hardship): a count with no same-period denominator. Census 2021 households are four years older than the counts, beyond the 366-day rule. IDACI already measures benefit-based income deprivation.
    - The LA pressure `spend` domain (`dfe_s251_cyp_services_net`): its polarity is neutral, because high spend can mean high demand or high investment, so it cannot be aligned.
  - **Added:** the four CIN assessment factors (domestic abuse, parental mental health, alcohol, drugs) to LA family risk, as signed off in D-0056. Alcohol and drugs have weight 0.5 each.
  - **Reviewed out:** `ohid_low_birthweight_term` from LA health. Its fit with the rest of the domain is negative (rho -0.39), and the domain's alpha was 0.30 with it in. At LA level, term birthweight mainly reflects the population's ethnic composition.
  - **Ineligible today, kept listed:**
    - PIP 16-24 at LSOA (92.0% coverage; it is eligible at MSOA);
    - NDTMS parents in treatment (not loaded);
    - children in temporary accommodation (92.8%);
    - NRM referrals (95% of council values are fallbacks);
    - social worker agency rate (94.8%).
  - **Redundancy (|rho| > 0.9):** only parental alcohol and drug misuse (rho 0.92). The pair is kept on purpose, because the 0.5 weights already make it count once (`redundancy_accepted`). Any other redundant pair stops the build.
  - **Weak fits kept (rho < 0.2 with the rest of the domain, but positive):**
    - lone-parent households in family risk (+0.17): the CIN factors are shares of assessment episodes, not population rates, so they measure something different;
    - average caseload in capacity (+0.07): workload rather than workforce instability.
    - The drop-one stability check shows how much each matters.
  - **Polarity:** EHCP 20-week timeliness is higher-is-better, so it is flipped.
- **Reason:** SPEC 12.2 and 12.3 step 1. The build makes each choice explicit and repeats the checks on every release.
- **Effect on outputs:**   - Neighbourhood need: 4 domains (8 indicators at MSOA, 7 at LSOA).
  - LA need: 6 domains, 17 eligible indicators.
  - LA system pressure: 3 domains, 8 eligible indicators.

### D-0088: Composite method details and Monte Carlo design

- **Date:** 2026-10-22
- **Status:** decided
- **Decision:**   - **Normal scores:** rank-based inverse normal, using Blom's formula (r - 3/8)/(n + 1/4), with average ranks for ties.
  - **Domain score:** the weighted mean of the normal scores of the indicators present (indicator weights 1, except D-0056).
  - **Missing data:**
    - LA: a domain needs at least two-thirds of its indicator weight present.
    - LSOA and MSOA: a domain is scored when any of its indicators is present. SPEC 12.3 gives the two-thirds rule for LA only, and applying it at LSOA left 1,237 LSOAs unscored because of suppressed DLA counts.
    - Every composite needs every domain.
  - **Ranks:** rank 1 and decile 1 are the most need or pressure, as in the IoD. Ties are broken by area code, so every output is deterministic.
  - **Monte Carlo:** 1,000 runs per composite and level. The seed stream is (20250331, composite index, level index). Each run draws uniformly from the options for:
    - normalisation: normal scores, z-scores or min-max;
    - aggregation:
      - IoD exponential;
      - arithmetic mean of the re-normalised domain scores;
      - geometric mean of domain ranks scaled to (0, 1];
    - missing threshold (LA only): 0.5, 0.6667 or 0.75;
    - inclusion: all indicators, drop one, or drop the practice-sensitive indicators.
    - A drop never removes the last indicator of a domain.
  - **Domain weights:** a symmetric Dirichlet with each weight's coefficient of variation at 0.25 (concentration = (D - 1)/0.25^2 - 1). That is about +/-25% of the equal weight (one standard deviation) whatever the number of domains, in line with common composite-audit practice. The skeleton's concentration of 20 gave about +/-50%.
  - **Per area:**
    - median rank;
    - 5th and 95th percentile ranks;
    - P(decile 1);
    - `decile_robust`: in the same decile as the primary method in at least 80% of runs.
  - **Sensitivity:** first-order Sobol' shares of rank variance for each discrete choice (variance of the conditional mean rank, summed over areas). The weights are a vector, so they get a lower bound (the largest single domain weight, binned into deciles) and an upper bound (the sum over domains).
- **Reason:** SPEC 12.3 and 12.4, made exact and reproducible.
- **Effect on outputs:** As described in the methodology pack (`composites/methodology_composite.md`).

### D-0089: Composite results and findings (composites version 0.1-experimental)

- **Date:** 2026-10-22
- **Status:** recorded (results are not adjusted to fit expectations; SPEC 12.5)
- **Decision:** —
- **Reason:** SPEC 12.5: write up every check and say what the results do and do not support.
- **Effect on outputs:** Recorded in the methodology pack (per-composite results) and `l5/l5_validation.md`. For review before the composites are shown publicly.

### D-0090: LA system pressure published as domains only; within-one-decile stability

- **Date:** 2026-10-23
- **Status:** decided (user, 2026-10-23: "proceed with your other recommendations")
- **Decision:**   - **Pressure published as domains only:** `la_system_pressure` is published as its three domain scores (demand, capacity, SEND). The combined index is withheld (`publish_index: false`).
    - It is still computed, so that its robustness and its correlation with LA need are documented in the methodology.
    - It has no `dim_indicator` row, profile column, serving rows or `l5_composite_service_area` rows. Gate 19 checks that none exist.
  - **New stability measure:** every composite and domain row now carries `p_within_one_decile`, the share of Monte Carlo runs in which the area's decile is within one decile of the primary decile. The validation report gives, for each composite and domain, the share of areas within one decile in at least 80% of runs, next to the strict `decile_robust` share.
  - **Dashboard emphasis (release README):** lead with the domain scores, and show the combined need indices in broad bands with their rank interval rather than as exact deciles. The aggregation choice is not narrowed: that would hide real model uncertainty.
- **Reason:**   - The combined pressure index is the least stable output. Only 13.9% of councils keep their decile even under the primary aggregation, and 52.8% stay within one decile.
  - Its capacity domain is weak (alpha 0.39), with the agency rate ineligible at 94.8% coverage.
  - The pressure domains are steadier: within one decile for 97.4% (demand) and 88.4% (capacity) of councils.
  - The need indices stay within one decile for 91.3% (LSOA), 92.0% (MSOA) and 70.5% (LA) of areas. That supports banded display.
- **Effect on outputs:**   - 154 indicators (the pressure index row is removed).
  - A new column `p_within_one_decile` on every `l5_composite_*` and `l5_domain_*` table.
  - Domain stability tables in the validation report.

### D-0091: NDTMS parents in treatment (H3) unavailable

- **Date:** 2026-10-23
- **Status:** decided (user, 2026-10-23)
- **Decision:**   - **Access:** council-level NDTMS figures on parents in treatment exist only in OHID's login-protected "Treatment and recovery unmet need toolkit" (checked 2026-10-23). The user cannot get NDTMS.net access, because registration requires a commissioning or provider purpose. None of the public sources checked has council figures:
    - the GOV.UK adult treatment statistics are England-only;
    - the data.gov.uk listing is a 2012 national bulletin.
  - **Composite:** `ohid_ndtms_adults_in_treatment_living_with_children` is removed from `la_need` family risk, which applies the D-0055 resolution.
  - **Catalogue:** both NDTMS indicators stay in the catalogue with no facts, so the gap stays visible.
- **Reason:** Principle 11 (no scraping or guessed URLs). There is no lawful public route to the data.
- **Effect on outputs:**   - None on values: the indicator was already ineligible.
  - LA family risk remains the least stable domain (D-0090), because it relies on practice-sensitive CIN assessment factors plus lone-parent households.
  - Revisit if OHID publishes council figures, or if a partner commissioner can share an extract under licence.

### D-0092: Methodology hosted on GitHub Pages from its own public repo

- **Date:** 2026-10-23
- **Status:** decided (user, 2026-10-23)
- **Decision:**   - **Hosting:** the rendered methodology pack is published with GitHub Pages from a separate public repo, `andy-nfpstack/cyp-database-methodology`, at https://andy-nfpstack.github.io/cyp-database-methodology/. The code repo stays private; on a free account, Pages serves public repos only.
  - **Settings:** `config/publication.yaml` holds the repo, branch and base URL. It also has placeholders for the contact inbox and DOI, which are still open.
  - **Versioning (SPEC 11.1):** each release is published under `<snapshot_id>/` and kept. `latest/` is a copy of the newest release, and the site root redirects to it and lists every release.
  - **Publishing:** `cypneed publish-methodology [--snapshot S] [--push]` copies a release's `methodology/` into a checkout at `data/pages/` and commits. It pushes only with `--push`.
  - **Links:** `serve_indicator_meta.methodology_url` gives each indicator's page for the release, and the release README links to the online pack.
- **Reason:** SPEC 11.1 ("published ... alongside the dashboard"; versioned) without making the code public or upgrading the account.
- **Effect on outputs:** `methodology_url` in `serve_indicator_meta`, and an online link in the README.

### D-0093: Fabric files shipped as a private GitHub release

- **Date:** 2026-10-24
- **Status:** decided (user, 2026-10-24)
- **Decision:**   - **Why a GitHub release:** the dashboard is built in another organisation's Microsoft Fabric. Its machines cannot reach the build machine's storage or take the D: drive, but the user can sign in to GitHub there.
  - **Command:** `cypneed package-release [--snapshot S] [--upload]` zips only what Fabric needs into `dist/<snapshot>/<snapshot>_fabric.zip`:
    - the Delta tables (every table and view);
    - the TopoJSON maps;
    - `serve_indicator_meta.json`, the data dictionaries, `sources.csv` and the README.
  - **Checksums:** it writes `SHA256SUMS.txt` alongside the zip.
  - **Upload:** with `--upload`, it creates a release `data-<snapshot>` in the private code repo, tagged at the release's own commit.
  - **Left out:** the CSV, Parquet and DuckDB copies, which Fabric does not need.
- **Reason:** GitHub limits release assets to 2 GiB per file with no total limit; the Fabric zip is about 0.26 GB. The private repo keeps the data off the public web until the user decides to publish it, and the checksum lets the receiving organisation verify the download.
- **Effect on outputs:** one zip and one checksum file per release in `dist/` (not committed), and a GitHub release when uploaded.

### D-0094: Final rigour review: disclosure control confirmed, references, open items closed

- **Date:** 2026-10-24
- **Status:** decided (user request, 2026-10-24: "full final review ... academic rigour")
- **Decision:**   - **Disclosure control (closes D-0009):** every loaded source's SDC profile in `config/sources.yaml` is now stated from its publisher's own data guidance, as read at inspection and recorded in `config/suppression_codes.yaml`, and marked confirmed.
    - The Census tables (P4, F6, F7) cite ONS's Census 2021 disclosure control page.
    - The population estimates (P1) cite the ONS small area population estimates quality and methodology information.
    - Method lists are corrected where the guidance says nothing is suppressed: E1–E4, E6, P7, S4 and S5 are `none`; C4 is suppression only.
    - The "DRAFT" wording no longer appears anywhere in the config or the published methodology.
  - **Tolerances unchanged:** tolerances were set in advance and are not changed, so they are not fitted to the results. The F2–F4 exception (set from observed differences, D-0053) is stated in the methodology. The technical methodology now shows, for each source, the publisher's disclosure control and what this release checked (totals compared, within tolerance, largest difference). The results are generated at release from `reconciliation`.
  - **References:** a References page cites every method used:
    - confidence intervals: Wilson; Byar, via Breslow and Day;
    - smoothing and transformation: Marshall's empirical Bayes; Blom's normal scores;
    - consistency checks: Cronbach's alpha;
    - composites: the OECD/JRC handbook; Saisana, Saltelli and Tarantola; Sobol';
    - deprivation: the IoD 2025 technical report;
    - inference: the ecological fallacy (Robinson); the modifiable areal unit problem (Openshaw);
    - the hotspot statistic and false discovery rate in the README guidance;
    - official sources: the ONS disclosure and population pages; the Code of Practice for Statistics, version 3.0.
    - Every URL was verified on 2026-10-24.
  - **Limitations:** the technical methodology adds that confidence intervals cover random variation only, and that the release is a single point in time.
  - **Open items closed:**
    - five `needs_decision` notes resolved by D-0085, D-0087 and D-0091 (youth services spend keeps the 13–19 band it was built with);
    - H3's verified landing page recorded;
    - D-0009 and D-0025 marked decided;
    - D-0087 marked accepted.
  - **Composite titles:** "LA" is capitalised (it had been rendered as "La need").
- **Reason:** SPEC 11.1 and the Code of Practice: every number traceable, every method cited, no draft wording in published outputs, and promised checks (D-0009) actually done.
- **Effect on outputs:** No change to data values. The methodology pack gains `references.md` and the evidence columns in the disclosure-control table.

### D-0095: Fabric-ready release: long serving tables, England level, kit, single-file methodology, transformation specification

- **Date:** 2026-10-24
- **Status:** decided (user request, 2026-10-24)
- **Decision:**   - **England comparator:** `nation` is added as a serving level (`serve_nation`, `profile_nation`).
  - **`serve_all`** stacks every serving level and the other geographies into one fact table, so the Power BI model is a star on two keys (`geo_key`, `column_prefix`).
  - **`l5_area_scores`** holds every composite and domain score with:
    - a fifth band and its label;
    - the number of deciles its 5th–95th rank interval spans;
    - `show_exact_rank` (the interval spans two deciles or fewer, the SPEC 12.6 display rule);
    - the stability measures.
  - **Area labels:** `serve_dim_area` gains `level_label` and `level_order`.
  - **Fabric kit (`release/fabric_kit.py`):** one definition of the model is used to write everything else:
    - the six model tables, five relationships and 18 DAX measures;
    - a load notebook (unzip, save each Delta table, check row counts against `manifest.json`; an optional cell builds the Direct Lake model with semantic-link-labs);
    - `measures.dax`;
    - `FABRIC_GUIDE.md`: setup, the manual modelling steps, six report pages field by field, rules for every visual.
    - The notebook's model cell and the DAX were not run in Fabric or Power BI from the build machine; the guide gives a manual fallback.
  - **Council GeoJSON:** written beside the TopoJSON, for Azure Maps reference layers.
  - **`methodology_complete.md`:** the whole methodology pack in one Markdown file. It has a table of contents, an anchor for each page and internal links rewritten to those anchors. It is published with the pack and attached to the GitHub release.
  - **Transformation specification (`transformations.md`):** generated from config and DECISIONS.md. It covers:
    - layers, invariants and the stage table (T1–T12 with code and QA gates);
    - the shared rules, with the exact formulas used (Wilson, Byar, Marshall's empirical Bayes, percentiles, IoD summaries);
    - every source: files, staging and harmonise code, symbols, disclosure control, decisions;
    - every indicator: formula, the exact category-map entry or the code that builds it, decisions;
    - guidance for moving to live pipelines.
- **Reason:** least work in Fabric (one upload, one notebook), clear modelling and report steps, and documentation complete enough to rebuild the pipelines from (user request).
- **Effect on outputs:**   - England rows in serving.
  - `serve_all`, `l5_area_scores` and the new `serve_dim_area` columns in every export.
  - `transformations.md`, `references.md` and `methodology_complete.md` in the pack.
  - The Fabric bundle carries the kit; the GitHub release carries the guide, notebook and methodology as separate files.

---

[Methodology index](#page-index)

---

<a id="page-changelog"></a>

## Changelog

Release `2dda583978fb-19eda0e60019`

- First release. No earlier release to compare with.

---

[Methodology index](#page-index)

---

<a id="page-indicators-census21-disabled-0-24"></a>

## Disabled children and young people

Release `2dda583978fb-19eda0e60019` · indicator `census21_disabled_0_24` · concept `disability`


The share of children and young people whose day-to-day activities are limited by a long-term health problem or disability.

### Definition

Census 2021 usual residents aged 0-24 who are disabled under the Equality Act (activities limited a little or a lot) / usual residents aged 0-24 (same table).

### Why it is included

The only neighbourhood-level measure of disability across the whole 0-24 age range.

### At a glance

| | |
|---|---|
| Theme | health |
| Role | need |
| Measure type | proportion |
| Estimate type | census |
| Timing | stock |
| Reference period | Census Day, 21 March 2021 |
| Native geography | small_area |
| Published at | small_area |
| Age bands | 0_24 |
| Numerator | Disabled under the Equality Act, aged 0-24 |
| Denominator | [Population (Census 2021)](#page-indicators-census21-usual-residents-by-age): Usual residents aged 0-24 (same table) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.

### Quality and known biases

Self- or proxy-reported (by the householder for children). Perturbed; 2021 during the pandemic.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 99.9% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| intermediate_area | 6,824 | 6,809 | 16 | 12.04% |
| lad | 279 | 278 | 59 | 1.92% |
| service_area | 136 | 136 | 103 | 1.92% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-census21-households-dependent-children"></a>

## Households with dependent children

Release `2dda583978fb-19eda0e60019` · indicator `census21_households_dependent_children` · concept `households_with_children`


The number of households in the neighbourhood with at least one dependent child, at the 2021 Census.

### Definition

Census 2021 households containing at least one dependent child (aged 0-15, or 16-18 in full-time education and living with parent(s)).

### Why it is included

Same-source denominator for lone-parent and overcrowding measures.

### At a glance

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
| Age bands | na |
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

### Sources

- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.

### Quality and known biases

Cell-key perturbed; 2021 during the pandemic.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| intermediate_area | 6,856 | 6,850 | 23 | 4.76% |
| lad | 296 | 296 | 129 | 0.70% |
| nation | 1 | 1 | 61 | 0.00% |
| service_area | 153 | 153 | 129 | 0.70% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-census21-lone-parent-households-dep-children"></a>

## Lone-parent households

Release `2dda583978fb-19eda0e60019` · indicator `census21_lone_parent_households_dep_children` · concept `lone_parent_households`


The share of households with dependent children headed by a single parent.

### Definition

Census 2021 lone-parent households with dependent children / households with dependent children.

### Why it is included

Single-parent families face higher poverty risk. Included as a risk factor, not a judgement on family form.

### At a glance

| | |
|---|---|
| Theme | family risk |
| Role | need |
| Measure type | proportion |
| Estimate type | census |
| Timing | stock |
| Reference period | Census Day, 21 March 2021 |
| Native geography | small_area |
| Published at | small_area |
| Age bands | na |
| Numerator | Lone-parent households with dependent children |
| Denominator | [Households with dependent children](#page-indicators-census21-households-dependent-children): Households with dependent children (same table) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.

### Quality and known biases

Perturbed counts. Four years before the snapshot. Family type is a risk marker, not a measure of need in itself; describe it carefully.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| intermediate_area | 6,856 | 6,855 | 12 | 10.53% |
| lad | 296 | 296 | 49 | 2.27% |
| nation | 1 | 1 | 96 | 0.01% |
| service_area | 153 | 153 | 49 | 2.27% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-census21-overcrowded-households-dep-children"></a>

## Overcrowded households with children

Release `2dda583978fb-19eda0e60019` · indicator `census21_overcrowded_households_dep_children` · concept `overcrowding`


The share of households with children that have fewer bedrooms than they need.

### Definition

Households with dependent children with occupancy rating (bedrooms) of -1 or less / households with dependent children.

### Why it is included

Overcrowding is linked to poorer child health, sleep and educational outcomes.

### At a glance

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
| Denominator | [Households with dependent children](#page-indicators-census21-households-dependent-children): Households with dependent children (same table) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.

### Quality and known biases

The bedroom standard is applied to Census answers. Perturbed counts; 2021.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| intermediate_area | 6,856 | 6,855 | 12 | 66.67% |
| lad | 296 | 293 | 34 | 3.31% |
| nation | 1 | 1 | 8 | 0.00% |
| service_area | 153 | 153 | 54 | 1.83% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-census21-population-by-ethnicity"></a>

## Population by ethnic group (Census 2021)

Release `2dda583978fb-19eda0e60019` · indicator `census21_population_by_ethnicity` · concept `population_by_ethnicity`


The number of people in each neighbourhood by ethnic group and age, from the 2021 Census.

### Definition

Census 2021 usual residents by ethnic group (most detailed classification ONS releases for LSOA x age) and age.

### Why it is included

Describes the ethnic make-up of the child and youth population. It is the only same-classification denominator for Census-classified ethnicity measures (principle 15).

### At a glance

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
| Age bands | 0_4, src_5_15, 16_17, 18_20, 21_24, src_25_29, src_30_plus |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | neither better nor worse |
| Aggregating to other areas | Sum the counts |
| Suitable for spatial analysis | yes |
| Ethnicity classification | census21_ew_6a |

### Sources

- **P4: Census 2021: ethnic group by age (custom dataset, LSOA21)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.

### Quality and known biases

Census 2021 is a near-complete count but is cell-key perturbed, so small cells are unreliable and cells do not sum exactly to totals. Taken during the COVID-19 pandemic. Four years before the reference date.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 97.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| intermediate_area | 302,085 | 302,084 | 15 | 500.00% |
| lad | 7,644 | 7,635 | 41 | 100.00% |
| service_area | 3,381 | 3,373 | 55 | 30.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-census21-unpaid-carers-5-24"></a>

## Young carers

Release `2dda583978fb-19eda0e60019` · indicator `census21_unpaid_carers_5_24` · concept `young_carers`


The share of children and young people aged 5 to 24 who look after someone because of illness, disability or old age.

### Definition

Census 2021 usual residents aged 5-24 providing any unpaid care / usual residents aged 5-24 (same table).

### Why it is included

Young carers are a recognised group at risk of poorer education and wellbeing.

### At a glance

| | |
|---|---|
| Theme | family risk |
| Role | need |
| Measure type | proportion |
| Estimate type | census |
| Timing | stock |
| Reference period | Census Day, 21 March 2021 |
| Native geography | small_area |
| Published at | small_area |
| Age bands | src_5_24 |
| Numerator | Providing 1+ hours unpaid care per week, aged 5-24 |
| Denominator | [Population (Census 2021)](#page-indicators-census21-usual-residents-by-age): Usual residents aged 5-24 (same table) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.

### Quality and known biases

Widely thought to undercount young carers (the question is answered by the householder). Perturbed; 2021.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 98.3% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| intermediate_area | 6,373 | 6,371 | 11 | 33.33% |
| lad | 118 | 116 | 27 | 4.62% |
| service_area | 45 | 44 | 27 | 1.87% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-census21-usual-residents-by-age"></a>

## Population (Census 2021)

Release `2dda583978fb-19eda0e60019` · indicator `census21_usual_residents_by_age` · concept `population`


The number of people in each neighbourhood by age at the 2021 Census.

### Definition

Total usual residents by age, taken from the same Census custom tables as the disability and unpaid care counts.

### Why it is included

Census-period numerators use Census denominators (SPEC 3, Timing). Taking the total from the same table avoids mismatches from cell perturbation between tables.

### At a glance

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

### Sources

- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.

### Quality and known biases

Cell-key perturbed; totals from different Census tables can differ slightly. Use only with numerators from the same table.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 99.9% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| intermediate_area | 13,197 | 13,197 | 24 | 1.15% |
| lad | 397 | 397 | 68 | 0.58% |
| service_area | 181 | 181 | 135 | 0.58% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-absence-enrolments"></a>

## Pupil enrolments

Release `2dda583978fb-19eda0e60019` · indicator `dfe_absence_enrolments` · concept `pupils`


The number of pupil enrolments used to calculate absence rates.

### Definition

Pupil enrolments, academic year 2024/25, as published in the absence statistics.

### Why it is included

Same-file denominator for persistent and severe absence.

### At a glance

| | |
|---|---|
| Theme | population |
| Role | denominator |
| Measure type | count |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Academic year 2024/25 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_pupils_all |
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

### Sources

- **E3: Pupil absence in schools in England, 2024/25** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Enrolments, not unique pupils.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-care-leavers-17-21"></a>

## Care leavers aged 17 to 21

Release `2dda583978fb-19eda0e60019` · indicator `dfe_care_leavers_17_21` · concept `care_leavers`


The number of young people aged 17 to 21 who have left care and are supported by the council.

### Definition

Care leavers aged 17-21 on their birthday in the year, as published by DfE.

### Why it is included

Leaving-care support is a statutory duty that extends to age 25.

### At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | count |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Year ending 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_17_21 |
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

### Sources

- **C2: Children looked after in England including adoptions, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Count only. No matching population denominator for 'formerly looked after', so no rate.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.3% |
| nation | 100.0% |
| service_area | 99.3% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-care-leavers-19-21-neet"></a>

## Care leavers not in education, employment or training

Release `2dda583978fb-19eda0e60019` · indicator `dfe_care_leavers_19_21_neet` · concept `care_leavers_neet`


The share of care leavers aged 19 to 21 who are not in education, employment or training.

### Definition

Care leavers aged 19-21 recorded as NEET / care leavers aged 19-21 x 100.

### Why it is included

A key outcome for young people leaving care.

### At a glance

| | |
|---|---|
| Theme | education |
| Role | need |
| Measure type | proportion |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Year ending 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_19_21 |
| Numerator | Care leavers 19-21 NEET |
| Denominator | [Care leavers aged 19 to 21](#page-indicators-dfe-care-leavers-19-21): Care leavers aged 19-21 |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C2: Children looked after in England including adoptions, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Activity unknown for those not in touch; check how DfE treats them.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.3% |
| nation | 100.0% |
| service_area | 99.3% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-care-leavers-19-21"></a>

## Care leavers aged 19 to 21

Release `2dda583978fb-19eda0e60019` · indicator `dfe_care_leavers_19_21` · concept `care_leavers`


The number of care leavers aged 19 to 21, used to calculate the share in education, employment or training.

### Definition

Care leavers aged 19-21, as published by DfE.

### Why it is included

Same-file denominator for care leaver NEET.

### At a glance

| | |
|---|---|
| Theme | service demand |
| Role | denominator |
| Measure type | count |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Year ending 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_19_21 |
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

### Sources

- **C2: Children looked after in England including adoptions, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

As published.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 4 | 0.01% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cin-assessments-completed"></a>

## Social care assessments

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cin_assessments_completed` · concept `cin_assessments`


Social care assessments completed during the year, per 10,000 children.

### Definition

Assessments completed in year ending 31 March 2025 / population aged 0-17 x 10,000.

### Why it is included

Workload measure between referral and plan.

### At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 1 April 2024 to 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_17 |
| Numerator | Assessments completed in year |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 0-17, mid-2024 MYE |
| Rate | per 10,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Event count; practice-sensitive.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cin-at-31mar"></a>

## Children in need

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cin_at_31mar` · concept `children_in_need`


Children the council's social care service was supporting because they need help to be safe or healthy, per 10,000 children.

### Definition

Children in need (episodes open) at 31 March 2025 / population aged 0-17 (mid-2024 MYE) x 10,000.

### Why it is included

The core measure of demand on children's social care.

### At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | source_bands, 0_17 |
| Numerator | Children in need at 31 March 2025 |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 0-17, mid-2024 MYE |
| Rate | per 10,000 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Reflects local thresholds and practice as well as need. Includes unborn children. Ethnicity breakdowns exist, but there is no same-classification population denominator, so no rates by ethnicity.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 2 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cin-episodes-with-assessment-factors"></a>

## Assessments with factors recorded

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cin_episodes_with_assessment_factors` · concept `assessment_factors`


The number of completed assessments in the year where at least one factor was recorded; the base for the assessment factor shares.

### Definition

Episodes with an assessment completed in the year that have assessment factor information (Episodes_with_assessment_factor), DfE CIN table C3.

### Why it is included

Same-table denominator for the assessment factor proportions, as DfE uses.

### At a glance

| | |
|---|---|
| Theme | population |
| Role | denominator |
| Measure type | count |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 1 April 2024 to 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_17 |
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

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Excludes episodes where no factors were identified, so it is smaller than all completed assessments.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cin-factor-domestic-abuse"></a>

## Domestic abuse identified at assessment

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cin_factor_domestic_abuse` · concept `assessment_factors`


Of completed social care assessments, the share where domestic abuse against a parent or carer was identified as a concern.

### Definition

Episodes with an assessment completed in the year where the factor 'Domestic abuse: concerns parent is victim' (Domestic_Abuse_parent) was recorded / episodes with assessment factor information (Episodes_with_assessment_factor), DfE CIN table C3, x 100.

### Why it is included

One of the few LA-level measures of family-level risk factors.

### At a glance

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
| Numerator | Episodes with the 'Domestic abuse: concerns parent is victim' factor at end of assessment (Domestic_Abuse_parent) |
| Denominator | [Assessments with factors recorded](#page-indicators-dfe-cin-episodes-with-assessment-factors): Episodes with assessment factor information (Episodes_with_assessment_factor, same table) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Only covers children who reached assessment, so it reflects practice and thresholds as well as need. Factor recording varies between LAs. An episode can have several factors. Excludes episodes with no factors identified (DfE footnote 2).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.3% |
| nation | 100.0% |
| service_area | 99.3% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cin-factor-parental-alcohol-misuse"></a>

## Parental alcohol misuse identified at assessment

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cin_factor_parental_alcohol_misuse` · concept `assessment_factors`


Of completed social care assessments, the share where a parent's or carer's alcohol misuse was identified as a concern.

### Definition

Episodes with an assessment completed in the year where the factor 'Alcohol misuse: concerns about parent' (Alcohol_Misuse_parent) was recorded / episodes with assessment factor information (Episodes_with_assessment_factor), DfE CIN table C3, x 100.

### Why it is included

Family risk factor; complements NDTMS treatment counts. Published separately from drug misuse; the two cannot be added because one episode can have both (D-0056).

### At a glance

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
| Numerator | Episodes with the 'Alcohol misuse: concerns about parent' factor at end of assessment (Alcohol_Misuse_parent) |
| Denominator | [Assessments with factors recorded](#page-indicators-dfe-cin-episodes-with-assessment-factors): Episodes with assessment factor information (Episodes_with_assessment_factor, same table) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Only covers children who reached assessment, so it reflects practice and thresholds as well as need. Factor recording varies between LAs. An episode can have several factors. Excludes episodes with no factors identified (DfE footnote 2).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 5 | 0.01% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cin-factor-parental-drug-misuse"></a>

## Parental drug misuse identified at assessment

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cin_factor_parental_drug_misuse` · concept `assessment_factors`


Of completed social care assessments, the share where a parent's or carer's drug misuse was identified as a concern.

### Definition

Episodes with an assessment completed in the year where the factor 'Drug misuse: concerns about parent' (Drug_Misuse_parent) was recorded / episodes with assessment factor information (Episodes_with_assessment_factor), DfE CIN table C3, x 100.

### Why it is included

Family risk factor; complements NDTMS treatment counts. Published separately from alcohol misuse; the two cannot be added because one episode can have both (D-0056).

### At a glance

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
| Numerator | Episodes with the 'Drug misuse: concerns about parent' factor at end of assessment (Drug_Misuse_parent) |
| Denominator | [Assessments with factors recorded](#page-indicators-dfe-cin-episodes-with-assessment-factors): Episodes with assessment factor information (Episodes_with_assessment_factor, same table) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Only covers children who reached assessment, so it reflects practice and thresholds as well as need. Factor recording varies between LAs. An episode can have several factors. Excludes episodes with no factors identified (DfE footnote 2).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.3% |
| nation | 100.0% |
| service_area | 99.3% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cin-factor-parental-mental-health"></a>

## Parental mental health identified at assessment

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cin_factor_parental_mental_health` · concept `assessment_factors`


Of completed social care assessments, the share where a parent's or carer's mental health was identified as a concern.

### Definition

Episodes with an assessment completed in the year where the factor 'Mental health: concerns about parent' (Mental_Health_parent) was recorded / episodes with assessment factor information (Episodes_with_assessment_factor), DfE CIN table C3, x 100.

### Why it is included

Family risk factor visible only through social care data.

### At a glance

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
| Denominator | [Assessments with factors recorded](#page-indicators-dfe-cin-episodes-with-assessment-factors): Episodes with assessment factor information (Episodes_with_assessment_factor, same table) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Only covers children who reached assessment, so it reflects practice and thresholds as well as need. Factor recording varies between LAs. An episode can have several factors. Excludes episodes with no factors identified (DfE footnote 2).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cin-referrals"></a>

## Referrals to children's social care

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cin_referrals` · concept `cin_referrals`


The number of times children were referred to the council's children's social care during the year, per 10,000 children.

### Definition

Referrals completed in the year ending 31 March 2025 / population aged 0-17 x 10,000.

### Why it is included

Front-door demand on children's social care.

### At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 1 April 2024 to 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_17 |
| Numerator | Referrals in year ending 31 March 2025 |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 0-17, mid-2024 MYE (mid-period) |
| Rate | per 10,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Event count: a child can be referred more than once. Counting practice at the front door varies between LAs.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 2 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cin-rereferrals-12m"></a>

## Re-referrals within 12 months

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cin_rereferrals_12m` · concept `cin_rereferrals`


The share of referrals for children who had already been referred in the previous 12 months.

### Definition

Referrals in the year that were within 12 months of a previous referral / referrals in the year x 100.

### Why it is included

Indicates repeat demand and whether earlier help resolved concerns.

### At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | proportion |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 1 April 2024 to 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_17 |
| Numerator | Re-referrals within 12 months |
| Denominator | [Referrals to children's social care](#page-indicators-dfe-cin-referrals): Referrals in year (same file) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Practice-sensitive; partly reflects how referrals are closed.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 3 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cla-3plus-placements"></a>

## Children in care with 3+ placements in the year

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cla_3plus_placements` · concept `cla_placement_stability`


The share of children in care who moved home three or more times during the year.

### Definition

CLA at 31 March 2025 with 3+ placements during the year / total CLA at 31 March 2025 in the same DfE placement stability table x 100.

### Why it is included

Placement instability reflects sufficiency pressure and harms children.

### At a glance

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
| Numerator | CLA with 3+ placements during the year |
| Denominator | [Children in care (stability base)](#page-indicators-dfe-cla-stability-base-at-31mar): Total CLA at 31 March in the placement stability table (same table) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C2: Children looked after in England including adoptions, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Small numbers in small LAs.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cla-at-31mar"></a>

## Children in care

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cla_at_31mar` · concept `looked_after_children`


Children in the care of the council, per 10,000 children.

### Definition

Children looked after at 31 March 2025 / population aged 0-17 x 10,000.

### Why it is included

The highest-intensity children's social care demand.

### At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | source_bands, 0_17 |
| Numerator | Children looked after at 31 March 2025 |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 0-17, mid-2024 MYE |
| Rate | per 10,000 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C2: Children looked after in England including adoptions, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Includes unaccompanied asylum-seeking children (UASC), whose numbers are concentrated in some LAs (see dfe_cla_uasc_at_31mar). LA of responsibility, not placement location.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.3% |
| nation | 100.0% |
| service_area | 99.3% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cla-ceased-adoption"></a>

## Adoptions from care

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cla_ceased_adoption` · concept `adoption`


The number of children adopted from the council's care during the year.

### Definition

CLA who ceased to be looked after in year ending 31 March 2025 with reason 'adopted'.

### Why it is included

Part of the care system's activity; included for completeness of the CLA publication.

### At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | count |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 1 April 2024 to 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_17 |
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

### Sources

- **C2: Children looked after in England including adoptions, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Small numbers; neither good nor bad in itself.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 36.8% |
| nation | 100.0% |
| service_area | 85.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cla-distance-known-at-31mar"></a>

## Children in care (distance known)

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cla_distance_known_at_31mar` · concept `cla_placement_distance`


Children in care whose distance from home to placement is recorded; the base for the share placed over 20 miles away.

### Definition

CLA at 31 March 2025 placed 20 miles or less from home + placed more than 20 miles from home (two published cells of one DfE table).

### Why it is included

DfE excludes unknown distances from the distance percentages; this is the same base.

### At a glance

| | |
|---|---|
| Theme | population |
| Role | denominator |
| Measure type | count |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_17 |
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

### Sources

- **C2: Children looked after in England including adoptions, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Exact sum of two published cells (D-0046 rule). NULL where either cell is suppressed.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cla-placed-20mi-plus"></a>

## Children in care placed over 20 miles from home

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cla_placed_20mi_plus` · concept `cla_placement_distance`


The share of children in care who live more than 20 miles from their home area.

### Definition

CLA at 31 March 2025 placed more than 20 miles from home / CLA at 31 March 2025 placed 20 miles or less or more than 20 miles from home (distance known) x 100.

### Why it is included

Indicator of placement sufficiency pressure.

### At a glance

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
| Denominator | [Children in care (distance known)](#page-indicators-dfe-cla-distance-known-at-31mar): CLA at 31 March with a known placement distance (sum of the two published distance cells, same table) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C2: Children looked after in England including adoptions, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Some distant placements are deliberate (for safety). Unknown distances are excluded per the DfE definition.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cla-stability-base-at-31mar"></a>

## Children in care (stability base)

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cla_stability_base_at_31mar` · concept `cla_placement_stability`


Children in care at 31 March, as counted in DfE's placement stability table; the base for the share with 3 or more placements.

### Definition

'Total children' for 'CLA on 31 March' in DfE table LA_CLA_placement_stability, 2025.

### Why it is included

Same-table denominator for the placement stability proportion.

### At a glance

| | |
|---|---|
| Theme | population |
| Role | denominator |
| Measure type | count |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_17 |
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

### Sources

- **C2: Children looked after in England including adoptions, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Should equal children looked after at 31 March; any difference is reported at load.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.3% |
| nation | 100.0% |
| service_area | 99.3% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cla-starts"></a>

## Children entering care

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cla_starts` · concept `looked_after_children`


Children who came into care during the year, per 10,000 children.

### Definition

Children starting to be looked after in year ending 31 March 2025 / population aged 0-17 x 10,000.

### Why it is included

Flow into care.

### At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 1 April 2024 to 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_17 |
| Numerator | Starts in year |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 0-17, mid-2024 MYE |
| Rate | per 10,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C2: Children looked after in England including adoptions, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Event-based; UASC arrivals affect some LAs.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.3% |
| nation | 100.0% |
| service_area | 99.3% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cla-uasc-at-31mar"></a>

## Unaccompanied asylum-seeking children in care

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cla_uasc_at_31mar` · concept `uasc`


Children in care who arrived in the UK alone seeking asylum, per 10,000 children.

### Definition

UASC looked after at 31 March 2025 / population aged 0-17 x 10,000.

### Why it is included

Distinct demand driven by arrivals and the National Transfer Scheme, not local need.

### At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_17 |
| Numerator | UASC looked after at 31 March 2025 |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 0-17, mid-2024 MYE |
| Rate | per 10,000 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | neither better nor worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C2: Children looked after in England including adoptions, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Concentrated in port and receiving LAs. Age-disputed cases are handled per DfE guidance.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cpp-at-31mar"></a>

## Children on child protection plans

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cpp_at_31mar` · concept `child_protection`


Children on a plan because they are at risk of significant harm, per 10,000 children.

### Definition

Children subject of a child protection plan at 31 March 2025 / population aged 0-17 x 10,000.

### Why it is included

Measure of the most serious safeguarding demand.

### At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | source_bands, 0_17 |
| Numerator | Children on CP plans at 31 March 2025 |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 0-17, mid-2024 MYE |
| Rate | per 10,000 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Practice-sensitive; LAs differ in their use of CP plans versus other routes. Small numbers in small LAs.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-cpp-starts"></a>

## New child protection plans

Release `2dda583978fb-19eda0e60019` · indicator `dfe_cpp_starts` · concept `child_protection`


Child protection plans started during the year, per 10,000 children.

### Definition

CP plans starting in year ending 31 March 2025 / population aged 0-17 x 10,000.

### Why it is included

Flow of serious safeguarding cases.

### At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 1 April 2024 to 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_17 |
| Numerator | CP plans started in year |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 0-17, mid-2024 MYE |
| Rate | per 10,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Event count; a child can start more than one plan.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-ehcp-20wk-timeliness"></a>

## EHC plans issued on time

Release `2dda583978fb-19eda0e60019` · indicator `dfe_ehcp_20wk_timeliness` · concept `send_timeliness`


The share of new EHC plans issued within the 20-week legal time limit.

### Definition

New EHCPs issued within 20 weeks, excluding exception cases, as published (%).

### Why it is included

The clearest published measure of SEND system strain.

### At a glance

| | |
|---|---|
| Theme | service pressure |
| Role | pressure |
| Measure type | percent published |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Calendar year 2024 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_25 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | better |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **E2: Education, health and care plans (SEN2), January 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Published percentage; small denominators in small LAs; year-to-year volatility.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.6% |
| nation | 100.0% |
| service_area | 98.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-ehcp-new-plans"></a>

## New EHC plans

Release `2dda583978fb-19eda0e60019` · indicator `dfe_ehcp_new_plans` · concept `send`


New EHC plans the council issued during the year, per 10,000 young people aged 0 to 25.

### Definition

New EHCPs issued in calendar year 2024 / population aged 0-25 x 10,000.

### Why it is included

Flow of SEND statutory demand.

### At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Calendar year 2024 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_25 |
| Numerator | New EHCPs issued, calendar year 2024 |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 0-25, mid-2024 MYE |
| Rate | per 10,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **E2: Education, health and care plans (SEN2), January 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Calendar-year flow; mid-period denominator is mid-2024 (exact).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-ehcps-0-25"></a>

## EHC plans (ages 0-25)

Release `2dda583978fb-19eda0e60019` · indicator `dfe_ehcps_0_25` · concept `send`


The number of young people aged 0 to 25 with an EHC plan the council is responsible for, per 10,000 young people.

### Definition

EHCPs maintained by the LA at January 2025 (SEN2) / population aged 0-25 (mid-2024 MYE) x 10,000.

### Why it is included

Total SEND statutory demand; runs to age 25, hence the 0_25 total.

### At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | January 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | source_bands, 0_25 |
| Numerator | EHCPs maintained, January 2025 |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 0-25, mid-2024 MYE |
| Rate | per 10,000 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **E2: Education, health and care plans (SEN2), January 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

practice_sensitive. LA responsibility, not residence, in some edge cases.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 7 | 7 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-exclusions-headcount"></a>

## Pupils (exclusions publication)

Release `2dda583978fb-19eda0e60019` · indicator `dfe_exclusions_headcount` · concept `pupils`


The number of pupils used to calculate suspension and exclusion rates.

### Definition

Pupil headcount as published in the suspensions and exclusions statistics.

### Why it is included

Same-file denominator.

### At a glance

| | |
|---|---|
| Theme | population |
| Role | denominator |
| Measure type | count |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | Academic year 2024/25 (check) |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_pupils_all |
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

### Sources

- **E4: Suspensions and permanent exclusions in England** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

As published.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-fsm-eligible-pupils"></a>

## Pupils eligible for free school meals

Release `2dda583978fb-19eda0e60019` · indicator `dfe_fsm_eligible_pupils` · concept `fsm_eligibility`


The share of pupils at schools in the authority who are eligible for free school meals.

### Definition

Pupils known to be eligible for FSM / pupils on roll (both as used for FSM in performance tables), all schools in the SPC FSM table, by LA of school, January 2025.

### Why it is included

Timely, administrative indicator of low family income for school-age children.

### At a glance

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
| Denominator | [Pupils](#page-indicators-dfe-pupils-on-roll): Pupils on roll used for FSM in performance tables (same table, same school-location basis) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **E6: Schools, pupils and their characteristics, January 2025 (FSM by pupil residence)** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Eligibility reflects benefit rules and UC transitional protection, so it has risen for policy as well as economic reasons. Excludes independent and home-educated pupils. By LA of school: DfE does not publish LA FSM by pupil residence in this release (D-0058).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-neet-16-17"></a>

## 16-17 year olds not in education, employment or training

Release `2dda583978fb-19eda0e60019` · indicator `dfe_neet_16_17` · concept `neet`


The share of 16 and 17 year olds known to the council who are not in education, employment or training.

### Definition

16-17 year olds NEET / 16-17 year olds known to the LA x 100.

### Why it is included

Key participation outcome at the transition to adulthood.

### At a glance

| | |
|---|---|
| Theme | education |
| Role | need |
| Measure type | percent published |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | End 2024 (Dec 2024 - Feb 2025 average) |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 16_17 |
| Numerator | 16-17 NEET |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **E5: Participation in education, training and NEET age 16 to 17 by local authority** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 10 absolute / 0.005 relative.

### Quality and known biases

DfE's published proportion (NEETprop) of three-month average counts; no CI (D-0067). Depends on tracking quality; read with 'not known'.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-neet-cohort-16-17"></a>

## 16-17 year olds known to the council

Release `2dda583978fb-19eda0e60019` · indicator `dfe_neet_cohort_16_17` · concept `neet`


The number of 16 and 17 year olds the council tracks, used to calculate NEET rates.

### Definition

16-17 year olds known to the LA (resident), average of December 2024 to February 2025, as published (avgcohort).

### Why it is included

Same-file denominator for NEET measures.

### At a glance

| | |
|---|---|
| Theme | population |
| Role | denominator |
| Measure type | count |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | End 2024 (Dec 2024 - Feb 2025 average) |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 16_17 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | neither better nor worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **E5: Participation in education, training and NEET age 16 to 17 by local authority** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 10 absolute / 0.005 relative.

### Quality and known biases

A three-month average, so not a whole number; stored in value, not count (D-0067). National figures rounded to the nearest 10.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-neet-or-not-known-16-17"></a>

## 16-17 year olds NEET or activity not known

Release `2dda583978fb-19eda0e60019` · indicator `dfe_neet_or_not_known_16_17` · concept `neet`


The share of 16 and 17 year olds who are not in education, employment or training, or whose activity the council does not know.

### Definition

(16-17 NEET + activity not known) / 16-17 known to the LA x 100.

### Why it is included

DfE headline measure; less sensitive to tracking quality.

### At a glance

| | |
|---|---|
| Theme | education |
| Role | need |
| Measure type | percent published |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | End 2024 (Dec 2024 - Feb 2025 average) |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 16_17 |
| Numerator | 16-17 NEET + not known |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **E5: Participation in education, training and NEET age 16 to 17 by local authority** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 10 absolute / 0.005 relative.

### Quality and known biases

DfE's published proportion (NEETNKprop) of three-month average counts; no CI (D-0067). Combines need with tracking performance.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-permanent-exclusions"></a>

## Permanent exclusions from school

Release `2dda583978fb-19eda0e60019` · indicator `dfe_permanent_exclusions` · concept `exclusions`


Pupils permanently excluded from school during the year, per 10,000 pupils.

### Definition

Permanent exclusions in the academic year / pupil headcount x 10,000.

### Why it is included

The most serious school sanction; strong risk marker.

### At a glance

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
| Denominator | [Pupils (exclusions publication)](#page-indicators-dfe-exclusions-headcount): Pupil headcount (same file) |
| Rate | per 10,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **E4: Suspensions and permanent exclusions in England** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Small numbers; per 10,000 (DfE publishes per 100) so values are readable. Use CIs.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-persistent-absence"></a>

## Persistent absence from school

Release `2dda583978fb-19eda0e60019` · indicator `dfe_persistent_absence` · concept `school_absence`


The share of pupils who missed at least 1 in 10 school sessions during the year.

### Definition

Enrolments missing 10% or more of possible sessions / enrolments x 100, 2024/25.

### Why it is included

Strong marker of disengagement, unmet need and risk.

### At a glance

| | |
|---|---|
| Theme | education |
| Role | need |
| Measure type | proportion |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Academic year 2024/25 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_pupils_all |
| Numerator | Persistently absent enrolments |
| Denominator | [Pupil enrolments](#page-indicators-dfe-absence-enrolments): Enrolments (same file) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **E3: Pupil absence in schools in England, 2024/25** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Includes authorised absence (e.g. illness). Enrolment-based.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-pupils-by-ethnicity"></a>

## Pupils by ethnic group

Release `2dda583978fb-19eda0e60019` · indicator `dfe_pupils_by_ethnicity` · concept `population_by_ethnicity`


The number of pupils in each local authority by ethnic group, from the January school census.

### Definition

Headcount of pupils in state-funded schools by ethnicity (DfE classification), January 2025.

### Why it is included

Same-classification denominator for DfE ethnicity-disaggregated measures (principle 15).

### At a glance

| | |
|---|---|
| Theme | population |
| Role | denominator |
| Measure type | count |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | January 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_pupils_all |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | neither better nor worse |
| Aggregating to other areas | Sum the counts |
| Suitable for spatial analysis | yes |
| Ethnicity classification | dfe_ethnicity |

### Sources

- **P7: Schools, pupils and their characteristics: pupils by ethnicity and local authority** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Covers only pupils in state-funded schools (not independent schools or home education). Ethnicity is recorded by the school, usually as reported by the parent or pupil.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 20 | 20 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-pupils-on-roll"></a>

## Pupils

Release `2dda583978fb-19eda0e60019` · indicator `dfe_pupils_on_roll` · concept `pupils`


The number of pupils at schools in each local authority.

### Definition

Number of pupils used for FSM in performance tables, by LA of school, January 2025 school census (SPC table spc_pupils_fsm).

### Why it is included

Same-source denominator for free school meal eligibility.

### At a glance

| | |
|---|---|
| Theme | population |
| Role | denominator |
| Measure type | count |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | January 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_pupils_all |
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

### Sources

- **E6: Schools, pupils and their characteristics, January 2025 (FSM by pupil residence)** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Excludes independent schools and home education; the coverage gap varies by area. By LA of school, matching the FSM numerator (D-0058).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-pupils-sen-support"></a>

## Pupils receiving SEN support

Release `2dda583978fb-19eda0e60019` · indicator `dfe_pupils_sen_support` · concept `send`


The share of pupils who receive extra help at school for special educational needs, without a legal plan.

### Definition

Pupils with SEN support / total pupils x 100, January 2025.

### Why it is included

Broader measure of identified SEN.

### At a glance

| | |
|---|---|
| Theme | education |
| Role | need |
| Measure type | proportion |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | January 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_pupils_all |
| Numerator | Pupils with SEN support |
| Denominator | [Pupils (SEN publication)](#page-indicators-dfe-pupils-total-sen-publication): Total pupils (same file) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **E1: Special educational needs in England, January 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Identification practice varies by school and LA.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-pupils-total-sen-publication"></a>

## Pupils (SEN publication)

Release `2dda583978fb-19eda0e60019` · indicator `dfe_pupils_total_sen_publication` · concept `pupils`


The number of pupils, used to calculate the share with special educational needs.

### Definition

Total pupils (phase Total, SEN status Total, primary need Total) in SEN in England table sen_ncyear_, January 2025: the same table as every SEN numerator.

### Why it is included

Same-file denominator for SEN proportions.

### At a glance

| | |
|---|---|
| Theme | population |
| Role | denominator |
| Measure type | count |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | January 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_pupils_all |
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

### Sources

- **E1: Special educational needs in England, January 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

By LA of school, as are the SEN numerators. The table covers state-funded and non-maintained special schools (no independent schools).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-pupils-with-ehcp"></a>

## Pupils with an EHC plan

Release `2dda583978fb-19eda0e60019` · indicator `dfe_pupils_with_ehcp` · concept `send`


The share of pupils with a legal plan setting out the support they need for special educational needs.

### Definition

Pupils with an EHC plan / total pupils x 100, January 2025.

### Why it is included

Prevalence of the highest level of identified SEND in schools.

### At a glance

| | |
|---|---|
| Theme | education |
| Role | need |
| Measure type | proportion |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | January 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_pupils_all |
| Numerator | Pupils with EHC plan |
| Denominator | [Pupils (SEN publication)](#page-indicators-dfe-pupils-total-sen-publication): Total pupils (same file) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **E1: Special educational needs in England, January 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Reflects identification, assessment practice and parental advocacy as well as need (practice_sensitive).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-s251-cla-net"></a>

## Spending on children in care per child

Release `2dda583978fb-19eda0e60019` · indicator `dfe_s251_cla_net` · concept `childrens_services_spend`


How much the council spent on children in care in the year, per child in the population.

### Definition

Net expenditure on children looked after 2024-25 (GBP) / population aged 0-17.

### Why it is included

Placement costs are the main pressure on children's services budgets.

### At a glance

| | |
|---|---|
| Theme | service pressure |
| Role | pressure |
| Measure type | currency gbp |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Financial year 2024-25 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_17 |
| Numerator | Net expenditure, children looked after, GBP |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 0-17, mid-2024 MYE |
| Rate | per 1 |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | neither better nor worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C4: LA and school expenditure (Section 251 outturn) 2024-25** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 1000 absolute / 0.001 relative.

### Quality and known biases

As for total spend. Per child uses ONS mid-2024 population (as every LA rate), not DfE's own per-capita column; the two agree within about 1% except where DfE's population differs (Camden: DfE about 54,900 children vs ONS 35,300; D-0068).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-s251-cyp-services-net"></a>

## Spending on children's services per child

Release `2dda583978fb-19eda0e60019` · indicator `dfe_s251_cyp_services_net` · concept `childrens_services_spend`


How much the council spent, after income, on children's and young people's services in the year, per child.

### Definition

Total net children's and young people's services expenditure 2024-25 (GBP) / population aged 0-17 (mid-2024).

### Why it is included

Spending reflects both need and pressure; used in the system-pressure index (spend per child).

### At a glance

| | |
|---|---|
| Theme | service pressure |
| Role | pressure |
| Measure type | currency gbp |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Financial year 2024-25 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_17 |
| Numerator | Net expenditure, children's and young people's services, GBP |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 0-17, mid-2024 MYE |
| Rate | per 1 |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | neither better nor worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C4: LA and school expenditure (Section 251 outturn) 2024-25** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 1000 absolute / 0.001 relative.

### Quality and known biases

Accounting practice varies between LAs. Polarity is a judgement: higher spend is read as higher pressure, not worse performance. Per child uses ONS mid-2024 population (as every LA rate), not DfE's own per-capita column; the two agree within about 1% except where DfE's population differs (Camden: DfE about 54,900 children vs ONS 35,300; D-0068).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-s251-family-support-net"></a>

## Spending on family support per child

Release `2dda583978fb-19eda0e60019` · indicator `dfe_s251_family_support_net` · concept `childrens_services_spend`


How much the council spent on early help and family support in the year, per child.

### Definition

Net expenditure on family support services 2024-25 (GBP) / population aged 0-17.

### Why it is included

Shows the balance between preventative and statutory spend.

### At a glance

| | |
|---|---|
| Theme | service pressure |
| Role | pressure |
| Measure type | currency gbp |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Financial year 2024-25 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_17 |
| Numerator | Net expenditure, family support services, GBP |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 0-17, mid-2024 MYE |
| Rate | per 1 |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | neither better nor worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C4: LA and school expenditure (Section 251 outturn) 2024-25** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 1000 absolute / 0.001 relative.

### Quality and known biases

Classification of early help spend varies between LAs. Per child uses ONS mid-2024 population (as every LA rate), not DfE's own per-capita column; the two agree within about 1% except where DfE's population differs (Camden: DfE about 54,900 children vs ONS 35,300; D-0068).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-s251-young-people-services-net"></a>

## Spending on youth services per young person

Release `2dda583978fb-19eda0e60019` · indicator `dfe_s251_young_people_services_net` · concept `childrens_services_spend`


How much the council spent on services for young people (such as youth work) in the year, per young person.

### Definition

Net expenditure on services for young people 2024-25 (GBP) / population aged 13-19 (the usual youth-service age range, to confirm).

### Why it is included

Youth provision is a preventative resource for older children.

### At a glance

| | |
|---|---|
| Theme | service pressure |
| Role | pressure |
| Measure type | currency gbp |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Financial year 2024-25 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_13_19 |
| Numerator | Net expenditure, services for young people, GBP |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 13-19, mid-2024 MYE (to confirm) |
| Rate | per 1 |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | neither better nor worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C4: LA and school expenditure (Section 251 outturn) 2024-25** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 1000 absolute / 0.001 relative.

### Quality and known biases

Small budgets; line definitions vary. Per child uses ONS mid-2024 population (as every LA rate), not DfE's own per-capita column; the two agree within about 1% except where DfE's population differs (Camden: DfE about 54,900 children vs ONS 35,300; D-0068).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-sen-primary-need-asd"></a>

## Pupils with autism as their main need

Release `2dda583978fb-19eda0e60019` · indicator `dfe_sen_primary_need_asd` · concept `send_primary_need`


The share of all pupils whose main special educational need is autism.

### Definition

Pupils (EHCP or SEN support) with primary type of need ASD / total pupils x 100.

### Why it is included

Largest and fastest-growing EHCP primary need; drives SEND system demand.

### At a glance

| | |
|---|---|
| Theme | education |
| Role | need |
| Measure type | proportion |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | January 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_pupils_all |
| Numerator | Pupils with SEN, primary need ASD |
| Denominator | [Pupils (SEN publication)](#page-indicators-dfe-pupils-total-sen-publication): Total pupils |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **E1: Special educational needs in England, January 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Diagnosis and identification rates vary by area.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-sen-primary-need-semh"></a>

## Pupils with social, emotional and mental health needs

Release `2dda583978fb-19eda0e60019` · indicator `dfe_sen_primary_need_semh` · concept `send_primary_need`


The share of all pupils whose main special educational need is social, emotional or mental health.

### Definition

Pupils (EHCP or SEN support) with primary type of need SEMH / total pupils x 100.

### Why it is included

School-based signal of children's mental health needs at LA level.

### At a glance

| | |
|---|---|
| Theme | health |
| Role | need |
| Measure type | proportion |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | January 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_pupils_all |
| Numerator | Pupils with SEN, primary need SEMH |
| Denominator | [Pupils (SEN publication)](#page-indicators-dfe-pupils-total-sen-publication): Total pupils |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **E1: Special educational needs in England, January 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Only covers needs identified in school; one primary need per pupil.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-severe-absence"></a>

## Severe absence from school

Release `2dda583978fb-19eda0e60019` · indicator `dfe_severe_absence` · concept `school_absence`


The share of pupils who missed at least half of school sessions during the year.

### Definition

Enrolments missing 50% or more of possible sessions / enrolments x 100, 2024/25.

### Why it is included

Identifies children largely missing from education.

### At a glance

| | |
|---|---|
| Theme | education |
| Role | need |
| Measure type | proportion |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Academic year 2024/25 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_pupils_all |
| Numerator | Severely absent enrolments |
| Denominator | [Pupil enrolments](#page-indicators-dfe-absence-enrolments): Enrolments (same file) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **E3: Pupil absence in schools in England, 2024/25** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Small numbers in small LAs; use CIs.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-suspensions"></a>

## Suspensions from school

Release `2dda583978fb-19eda0e60019` · indicator `dfe_suspensions` · concept `exclusions`


The number of times pupils were suspended from school during the year, per 100 pupils.

### Definition

Suspensions in the academic year / pupil headcount x 100.

### Why it is included

Exclusion is linked to exploitation risk and poorer outcomes.

### At a glance

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
| Numerator | Suspensions |
| Denominator | [Pupils (exclusions publication)](#page-indicators-dfe-exclusions-headcount): Pupil headcount (same file) |
| Rate | per 100 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **E4: Suspensions and permanent exclusions in England** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Event count (a pupil can be suspended more than once). School policy affects rates.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 44.6% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 1 | 1 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-sw-agency-rate"></a>

## Agency social worker rate

Release `2dda583978fb-19eda0e60019` · indicator `dfe_sw_agency_rate` · concept `social_work_workforce`


The share of children's social workers employed through agencies rather than directly.

### Definition

FTE agency workers / (FTE agency + FTE social workers) at 30 September 2024, as published.

### Why it is included

High agency use signals recruitment pressure and affects continuity for children.

### At a glance

| | |
|---|---|
| Theme | service pressure |
| Role | pressure |
| Measure type | percent published |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 30 September 2024 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | na |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C3: Children's social work workforce, at 30 September 2024** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 1 absolute / 0.005 relative.

### Quality and known biases

Off-period snapshot; published rate.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 41.9% |
| nation | 100.0% |
| service_area | 94.8% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-sw-average-caseload"></a>

## Average social worker caseload

Release `2dda583978fb-19eda0e60019` · indicator `dfe_sw_average_caseload` · concept `social_work_workforce`


The average number of children's cases held by each social worker.

### Definition

Cases held by case-holding social workers / FTE case-holding social workers at 30 September 2024, as published.

### Why it is included

Direct measure of workload pressure.

### At a glance

| | |
|---|---|
| Theme | service pressure |
| Role | pressure |
| Measure type | rate published |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 30 September 2024 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | na |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C3: Children's social work workforce, at 30 September 2024** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 1 absolute / 0.005 relative.

### Quality and known biases

Counting practice varies between LAs. Published ratio (stored as rate_published); not re-aggregable.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 42.9% |
| nation | 100.0% |
| service_area | 96.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-sw-turnover-rate"></a>

## Social worker turnover rate

Release `2dda583978fb-19eda0e60019` · indicator `dfe_sw_turnover_rate` · concept `social_work_workforce`


The share of children's social workers who left during the year.

### Definition

FTE leavers in the year to 30 September 2024 / FTE social workers at 30 September 2024, as published.

### Why it is included

Turnover disrupts relationships with children and families.

### At a glance

| | |
|---|---|
| Theme | service pressure |
| Role | pressure |
| Measure type | percent published |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Year to 30 September 2024 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | na |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C3: Children's social work workforce, at 30 September 2024** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 1 absolute / 0.005 relative.

### Quality and known biases

Published rate; off-period.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 42.9% |
| nation | 100.0% |
| service_area | 96.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dfe-sw-vacancy-rate"></a>

## Social worker vacancy rate

Release `2dda583978fb-19eda0e60019` · indicator `dfe_sw_vacancy_rate` · concept `social_work_workforce`


The share of children's social worker posts that are vacant.

### Definition

FTE vacancies / (FTE vacancies + FTE social workers) at 30 September 2024, as published by DfE.

### Why it is included

Workforce capacity is the main constraint on social care response.

### At a glance

| | |
|---|---|
| Theme | service pressure |
| Role | pressure |
| Measure type | percent published |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 30 September 2024 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | na |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C3: Children's social work workforce, at 30 September 2024** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 1 absolute / 0.005 relative.

### Quality and known biases

Snapshot at 30 Sep 2024 (off-period). Published rate; cannot be re-aggregated without FTE counts.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.2% |
| nation | 100.0% |
| service_area | 97.4% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dwp-cilif-absolute-bhc-pct"></a>

## Children in absolute low income families (%)

Release `2dda583978fb-19eda0e60019` · indicator `dwp_cilif_absolute_bhc_pct` · concept `child_poverty`


The share of children living in families below a fixed poverty line, before housing costs.

### Definition

Percentage as published by DWP alongside CiLIF counts.

### Why it is included

Comparable rate for absolute low income.

### At a glance

| | |
|---|---|
| Theme | child poverty |
| Role | need |
| Measure type | percent published |
| Estimate type | survey calibrated |
| Timing | flow |
| Reference period | Financial year ending March 2025 |
| Native geography | lad |
| Published at | lad |
| Age bands | src_0_15, src_0_19 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **F1: Children in Low Income Families: local area statistics (FYE 2025)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.

### Quality and known biases

As for the relative percentage (including county values by DWP's method). Identical to the relative percentage for FYE 2025 (reference year).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 86.3% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dwp-cilif-absolute-bhc"></a>

## Children in absolute low income families

Release `2dda583978fb-19eda0e60019` · indicator `dwp_cilif_absolute_bhc` · concept `child_poverty`


The number of children living in families whose income is below a fixed poverty line (60% of the 2024/25 UK average, adjusted for inflation), before housing costs.

### Definition

DWP CiLIF absolute low income, BHC: equivalised household income below 60% of the FYE 2025 median held constant in real terms, calibrated to HBAI. DWP moved the reference year from FYE 2011 to FYE 2025 in this release and revised the back series.

### Why it is included

A complement to relative poverty that does not move with average incomes.

### At a glance

| | |
|---|---|
| Theme | child poverty |
| Role | need |
| Measure type | count |
| Estimate type | survey calibrated |
| Timing | flow |
| Reference period | Financial year ending March 2025 |
| Native geography | lad |
| Published at | lad, WD25 |
| Age bands | 0_4, 5_10, 11_15, src_16_19, src_0_19 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum the counts |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **F1: Children in Low Income Families: local area statistics (FYE 2025)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.

### Quality and known biases

As for relative CiLIF. Because FYE 2025 is now the reference year, absolute and relative figures for FYE 2025 are identical in every area (checked: all LA, country and age-band cells match); later years will differ as the absolute line is held fixed in real terms.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 5 | 5 | 43 | 0.01% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dwp-cilif-relative-bhc-pct"></a>

## Children in relative low income families (%)

Release `2dda583978fb-19eda0e60019` · indicator `dwp_cilif_relative_bhc_pct` · concept `child_poverty`


The share of children living in families below 60% of the current UK average income, before housing costs.

### Definition

Percentage as published by DWP: children aged 0-15 in relative low income families / ONS mid-2024 population aged 0-15 x 100 (DWP CiLIF note 3). DWP publishes it for lower-tier and unitary councils; for the 21 county councils it is computed by DWP's method from the summed district counts (D-0085).

### Why it is included

A rate is needed for comparison. The DWP denominator is used because no population age band matches 'dependent children aged 0-19' exactly (SPEC 3: never trim a band).

### At a glance

| | |
|---|---|
| Theme | child poverty |
| Role | need |
| Measure type | percent published |
| Estimate type | survey calibrated |
| Timing | flow |
| Reference period | Financial year ending March 2025 |
| Native geography | lad |
| Published at | lad |
| Age bands | src_0_15, src_0_19 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **F1: Children in Low Income Families: local area statistics (FYE 2025)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.

### Quality and known biases

Survey-calibrated; BHC understates high-housing-cost areas. County council values are our calculation by DWP's stated method, which reproduces all 428 published LA percentages exactly; they are flagged 'derived by the publisher's method'. For custom regions sum the counts and the 0-15 population, then divide.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 86.3% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dwp-cilif-relative-bhc"></a>

## Children in relative low income families

Release `2dda583978fb-19eda0e60019` · indicator `dwp_cilif_relative_bhc` · concept `child_poverty`


The number of children living in families whose income is below 60% of the current UK average, before housing costs.

### Definition

DWP CiLIF: children (under 16, or 16-19 in non-advanced education) in families with equivalised household income below 60% of contemporary median, BHC, calibrated to the national survey (HBAI).

### Why it is included

The main official LA-level child poverty statistic. The dashboard uses it at LA level, with IDACI below LA level (shared concept_id child_poverty).

### At a glance

| | |
|---|---|
| Theme | child poverty |
| Role | need |
| Measure type | count |
| Estimate type | survey calibrated |
| Timing | flow |
| Reference period | Financial year ending March 2025 |
| Native geography | lad |
| Published at | lad, WD25 |
| Age bands | 0_4, 5_10, 11_15, src_16_19, src_0_19 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum the counts |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **F1: Children in Low Income Families: local area statistics (FYE 2025)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.

### Quality and known biases

Survey-calibrated, BHC only, so it understates poverty where housing costs are high (e.g. London). Perturbed counts. Children are dependent children (to age 19), which does not match any population age band exactly.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| nation | 5 | 5 | 43 | 0.01% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dwp-dla-claimants-under16"></a>

## Children receiving Disability Living Allowance

Release `2dda583978fb-19eda0e60019` · indicator `dwp_dla_claimants_under16` · concept `disability_benefit`


The share of children under 16 receiving Disability Living Allowance, a benefit for children with extra care or mobility needs.

### Definition

DLA cases in payment aged under 16 (Feb 2025) / mid-2024 SAPE population aged 0-15.

### Why it is included

Timely small-area marker of childhood disability and complex needs.

### At a glance

| | |
|---|---|
| Theme | health |
| Role | need |
| Measure type | proportion |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | February 2025 |
| Native geography | small_area |
| Published at | small_area |
| Age bands | 0_4, 5_10, 11_15, src_0_15 |
| Numerator | DLA cases in payment, age 0-15 |
| Denominator | [Population](#page-indicators-ons-sape-population): Population aged 0-15, mid-2024 SAPE (sum of single years) |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **F3: Disability Living Allowance claimants under 16 (Stat-Xplore)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key, suppression; additivity approximate;
  tolerance 15 absolute / 0.03 relative.

### Quality and known biases

Reflects claiming behaviour and awareness as well as need. Perturbed counts.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 97.7% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| intermediate_area | 14,472 | 14,466 | 23 | 78.57% |
| lad | 120 | 120 | 58 | 4.81% |
| service_area | 31 | 31 | 47 | 3.52% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dwp-pip-claimants-16-24"></a>

## Young people receiving PIP

Release `2dda583978fb-19eda0e60019` · indicator `dwp_pip_claimants_16_24` · concept `disability_benefit`


The share of young people aged 16 to 24 receiving Personal Independence Payment, a disability benefit.

### Definition

PIP cases with entitlement aged 16-24 (Jan 2025) / mid-2024 SAPE population aged 16-24.

### Why it is included

Small-area marker of disability and long-term ill health, including mental health, in young adults.

### At a glance

| | |
|---|---|
| Theme | health |
| Role | need |
| Measure type | proportion |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | March 2025 |
| Native geography | small_area |
| Published at | small_area |
| Age bands | src_16_19, src_20_24, src_16_24 |
| Numerator | PIP cases with entitlement, age 16-24 |
| Denominator | [Population](#page-indicators-ons-sape-population): Population aged 16-24, mid-2024 SAPE |
| Rate | per 100 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **F4: Personal Independence Payment claimants aged 16-24 (Stat-Xplore)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key, suppression; additivity approximate;
  tolerance 15 absolute / 0.03 relative.

### Quality and known biases

Reflects claiming behaviour; mental health conditions are a growing share of awards. Perturbed counts.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 99.7% |
| nation | 100.0% |
| service_area | 99.3% |
| small_area | 92.6% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| intermediate_area | 8,737 | 8,736 | 19 | 100.00% |
| lad | 13 | 12 | 40 | 6.29% |
| service_area | 2 | 2 | 40 | 2.79% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-dwp-uc-households-with-children"></a>

## Households with children on Universal Credit

Release `2dda583978fb-19eda0e60019` · indicator `dwp_uc_households_with_children` · concept `benefit_receipt_families`


The number of households with children in the neighbourhood that receive Universal Credit.

### Definition

Count of households on UC (payment) with at least one dependent child, by LSOA21, March 2025.

### Why it is included

The most recent small-area signal of low family income (IDACI inputs date from 2022/23).

### At a glance

| | |
|---|---|
| Theme | child poverty |
| Role | need |
| Measure type | count |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | March 2025 |
| Native geography | small_area |
| Published at | small_area |
| Age bands | na |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum the counts |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **F2: Universal Credit households with children (Stat-Xplore)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key, suppression; additivity approximate;
  tolerance 15 absolute / 0.03 relative.

### Quality and known biases

Perturbed counts. Reflects take-up as well as need. The legacy-benefit migration to UC was still under way in 2024/25, so UC counts partly reflect migration timing rather than need.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 99.8% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| intermediate_area | 6,787 | 6,787 | 17 | 23.68% |
| lad | 254 | 254 | 88 | 1.63% |
| service_area | 103 | 103 | 88 | 1.63% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-ho-asylum-support-recipients"></a>

## People receiving asylum support

Release `2dda583978fb-19eda0e60019` · indicator `ho_asylum_support_recipients` · concept `asylum_support`


The number of people seeking asylum who receive housing or financial support from the Home Office in the council area. All ages.

### Definition

People in receipt of asylum support (by support type) at 31 March 2025, by LA.

### Why it is included

Context for families seeking asylum, who may need children's services.

### At a glance

| | |
|---|---|
| Theme | population |
| Role | context |
| Measure type | count |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 31 March 2025 |
| Native geography | lad |
| Published at | lad |
| Age bands | all_ages |
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

### Sources

- **S5: Asylum support by local authority (Home Office immigration statistics)** (Home Office). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.01 relative.

### Quality and known biases

All ages, not CYP-specific; dispersal policy drives the distribution. Count only.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-ho-nrm-referrals-under18"></a>

## Child referrals for suspected exploitation (NRM)

Release `2dda583978fb-19eda0e60019` · indicator `ho_nrm_referrals_under18` · concept `modern_slavery`


Children referred as potential victims of modern slavery or exploitation, per 10,000 children. This shows how actively agencies identify and refer cases.

### Definition

Potential victims aged 17 or under at referral, referred to the NRM April 2024 - March 2025 (four quarterly releases), by police force area responsible for investigation / population aged 0-17 of the force area x 10,000.

### Why it is included

Proxy for identified child exploitation (incl. county lines). Theme service_demand because it measures referral activity.

### At a glance

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
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 0-17, mid-2024 MYE, summed over the force area's LADs (G8) |
| Rate | per 10,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **S4: National Referral Mechanism and Duty to Notify statistics** (Home Office). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.01 relative.

### Quality and known biases

Strongly shaped by first-responder awareness. Published by police force responsible for investigation only (no LA of residence), so LAs see the force-area value as a labelled fallback. British Transport Police referrals have no area (D-0074).

### Coverage

| Level | Areas with a value |
|---|---|
| PFA | 100.0% |
| lad | 0.3% |
| service_area | 5.2% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-l5-la-need-economic-hardship"></a>

## LA need: economic hardship domain

Release `2dda583978fb-19eda0e60019` · indicator `l5_la_need_economic_hardship` · concept `la_need_economic_hardship`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

The economic hardship part of the la need index; higher means more need.

### Definition

Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3).

### Why it is included

Shows which domain drives an area's composite score.

### At a glance

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

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.
- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.
- **E3: Pupil absence in schools in England, 2024/25** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **E4: Suspensions and permanent exclusions in England** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **E5: Participation in education, training and NEET age 16 to 17 by local authority** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 10 absolute / 0.005 relative.
- **E6: Schools, pupils and their characteristics, January 2025 (FSM by pupil residence)** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **F1: Children in Low Income Families: local area statistics (FYE 2025)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **H2: Fingertips: Child and Maternal Health profile (API)** (Office for Health Improvement and Disparities). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **Ho1: Statutory homelessness in England: detailed local authority tables (H-CLIC)** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, imputation; additivity approximate;
  tolerance 0 absolute / 0.05 relative.
- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.
- **S3: Youth justice statistics 2024 to 2025** (Youth Justice Board / Ministry of Justice). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-l5-la-need-education"></a>

## LA need: education domain

Release `2dda583978fb-19eda0e60019` · indicator `l5_la_need_education` · concept `la_need_education`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

The education part of the la need index; higher means more need.

### Definition

Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3).

### Why it is included

Shows which domain drives an area's composite score.

### At a glance

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

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.
- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.
- **E3: Pupil absence in schools in England, 2024/25** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **E4: Suspensions and permanent exclusions in England** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **E5: Participation in education, training and NEET age 16 to 17 by local authority** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 10 absolute / 0.005 relative.
- **E6: Schools, pupils and their characteristics, January 2025 (FSM by pupil residence)** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **F1: Children in Low Income Families: local area statistics (FYE 2025)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **H2: Fingertips: Child and Maternal Health profile (API)** (Office for Health Improvement and Disparities). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **Ho1: Statutory homelessness in England: detailed local authority tables (H-CLIC)** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, imputation; additivity approximate;
  tolerance 0 absolute / 0.05 relative.
- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.
- **S3: Youth justice statistics 2024 to 2025** (Youth Justice Board / Ministry of Justice). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-l5-la-need-family-risk"></a>

## LA need: family risk domain

Release `2dda583978fb-19eda0e60019` · indicator `l5_la_need_family_risk` · concept `la_need_family_risk`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

The family risk part of the la need index; higher means more need.

### Definition

Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3).

### Why it is included

Shows which domain drives an area's composite score.

### At a glance

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

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.
- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.
- **E3: Pupil absence in schools in England, 2024/25** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **E4: Suspensions and permanent exclusions in England** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **E5: Participation in education, training and NEET age 16 to 17 by local authority** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 10 absolute / 0.005 relative.
- **E6: Schools, pupils and their characteristics, January 2025 (FSM by pupil residence)** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **F1: Children in Low Income Families: local area statistics (FYE 2025)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **H2: Fingertips: Child and Maternal Health profile (API)** (Office for Health Improvement and Disparities). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **Ho1: Statutory homelessness in England: detailed local authority tables (H-CLIC)** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, imputation; additivity approximate;
  tolerance 0 absolute / 0.05 relative.
- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.
- **S3: Youth justice statistics 2024 to 2025** (Youth Justice Board / Ministry of Justice). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-l5-la-need-health"></a>

## LA need: health domain

Release `2dda583978fb-19eda0e60019` · indicator `l5_la_need_health` · concept `la_need_health`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

The health part of the la need index; higher means more need.

### Definition

Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3).

### Why it is included

Shows which domain drives an area's composite score.

### At a glance

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

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.
- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.
- **E3: Pupil absence in schools in England, 2024/25** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **E4: Suspensions and permanent exclusions in England** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **E5: Participation in education, training and NEET age 16 to 17 by local authority** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 10 absolute / 0.005 relative.
- **E6: Schools, pupils and their characteristics, January 2025 (FSM by pupil residence)** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **F1: Children in Low Income Families: local area statistics (FYE 2025)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **H2: Fingertips: Child and Maternal Health profile (API)** (Office for Health Improvement and Disparities). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **Ho1: Statutory homelessness in England: detailed local authority tables (H-CLIC)** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, imputation; additivity approximate;
  tolerance 0 absolute / 0.05 relative.
- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.
- **S3: Youth justice statistics 2024 to 2025** (Youth Justice Board / Ministry of Justice). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-l5-la-need-housing"></a>

## LA need: housing domain

Release `2dda583978fb-19eda0e60019` · indicator `l5_la_need_housing` · concept `la_need_housing`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

The housing part of the la need index; higher means more need.

### Definition

Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3).

### Why it is included

Shows which domain drives an area's composite score.

### At a glance

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

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.
- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.
- **E3: Pupil absence in schools in England, 2024/25** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **E4: Suspensions and permanent exclusions in England** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **E5: Participation in education, training and NEET age 16 to 17 by local authority** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 10 absolute / 0.005 relative.
- **E6: Schools, pupils and their characteristics, January 2025 (FSM by pupil residence)** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **F1: Children in Low Income Families: local area statistics (FYE 2025)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **H2: Fingertips: Child and Maternal Health profile (API)** (Office for Health Improvement and Disparities). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **Ho1: Statutory homelessness in England: detailed local authority tables (H-CLIC)** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, imputation; additivity approximate;
  tolerance 0 absolute / 0.05 relative.
- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.
- **S3: Youth justice statistics 2024 to 2025** (Youth Justice Board / Ministry of Justice). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-l5-la-need-safety"></a>

## LA need: safety domain

Release `2dda583978fb-19eda0e60019` · indicator `l5_la_need_safety` · concept `la_need_safety`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

The safety part of the la need index; higher means more need.

### Definition

Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3).

### Why it is included

Shows which domain drives an area's composite score.

### At a glance

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

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.
- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.
- **E3: Pupil absence in schools in England, 2024/25** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **E4: Suspensions and permanent exclusions in England** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **E5: Participation in education, training and NEET age 16 to 17 by local authority** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 10 absolute / 0.005 relative.
- **E6: Schools, pupils and their characteristics, January 2025 (FSM by pupil residence)** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **F1: Children in Low Income Families: local area statistics (FYE 2025)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **H2: Fingertips: Child and Maternal Health profile (API)** (Office for Health Improvement and Disparities). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **Ho1: Statutory homelessness in England: detailed local authority tables (H-CLIC)** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, imputation; additivity approximate;
  tolerance 0 absolute / 0.05 relative.
- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.
- **S3: Youth justice statistics 2024 to 2025** (Youth Justice Board / Ministry of Justice). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-l5-la-need"></a>

## LA need index

Release `2dda583978fb-19eda0e60019` · indicator `l5_la_need` · concept `la_need`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

A combined measure of need from 6 domains; higher means more need.

### Definition

IoD-style composite (SPEC 12.3): rank-based normal scores within domains, exponentially transformed domain scores, equal domain weights.

### Why it is included

Summarises many indicators for comparison; need and pressure are kept apart.

### At a glance

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

### Sources

- **C1: Children in need, reporting year 2025** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 0 absolute / 0.005 relative.
- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.
- **E3: Pupil absence in schools in England, 2024/25** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **E4: Suspensions and permanent exclusions in England** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **E5: Participation in education, training and NEET age 16 to 17 by local authority** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 10 absolute / 0.005 relative.
- **E6: Schools, pupils and their characteristics, January 2025 (FSM by pupil residence)** (Department for Education). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **F1: Children in Low Income Families: local area statistics (FYE 2025)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **H2: Fingertips: Child and Maternal Health profile (API)** (Office for Health Improvement and Disparities). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.
- **Ho1: Statutory homelessness in England: detailed local authority tables (H-CLIC)** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, imputation; additivity approximate;
  tolerance 0 absolute / 0.05 relative.
- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.
- **S3: Youth justice statistics 2024 to 2025** (Youth Justice Board / Ministry of Justice). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-l5-la-system-pressure-capacity"></a>

## LA system pressure: capacity domain

Release `2dda583978fb-19eda0e60019` · indicator `l5_la_system_pressure_capacity` · concept `la_system_pressure_capacity`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

The capacity part of the la system pressure index; higher means more pressure.

### Definition

Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3).

### Why it is included

Shows which domain drives an area's composite score.

### At a glance

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

### Sources

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

### Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-l5-la-system-pressure-demand"></a>

## LA system pressure: demand domain

Release `2dda583978fb-19eda0e60019` · indicator `l5_la_system_pressure_demand` · concept `la_system_pressure_demand`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

The demand part of the la system pressure index; higher means more pressure.

### Definition

Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3).

### Why it is included

Shows which domain drives an area's composite score.

### At a glance

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

### Sources

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

### Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-l5-la-system-pressure-send"></a>

## LA system pressure: send domain

Release `2dda583978fb-19eda0e60019` · indicator `l5_la_system_pressure_send` · concept `la_system_pressure_send`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

The send part of the la system pressure index; higher means more pressure.

### Definition

Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3).

### Why it is included

Shows which domain drives an area's composite score.

### At a glance

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

### Sources

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

### Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-l5-neighbourhood-need-economic-hardship"></a>

## Neighbourhood need: economic hardship domain

Release `2dda583978fb-19eda0e60019` · indicator `l5_neighbourhood_need_economic_hardship` · concept `neighbourhood_need_economic_hardship`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

The economic hardship part of the neighbourhood need index; higher means more need.

### Definition

Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3).

### Why it is included

Shows which domain drives an area's composite score.

### At a glance

| | |
|---|---|
| Theme | composite |
| Role | composite |
| Measure type | score |
| Estimate type | composite experimental |
| Timing | not applicable |
| Reference period | Inputs from several periods, Census 2021 to 2025 (see the composite methodology) |
| Native geography | small_area |
| Published at | small_area, intermediate_area |
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

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.
- **F3: Disability Living Allowance claimants under 16 (Stat-Xplore)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key, suppression; additivity approximate;
  tolerance 15 absolute / 0.03 relative.
- **F4: Personal Independence Payment claimants aged 16-24 (Stat-Xplore)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key, suppression; additivity approximate;
  tolerance 15 absolute / 0.03 relative.
- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-l5-neighbourhood-need-family-housing"></a>

## Neighbourhood need: family housing domain

Release `2dda583978fb-19eda0e60019` · indicator `l5_neighbourhood_need_family_housing` · concept `neighbourhood_need_family_housing`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

The family housing part of the neighbourhood need index; higher means more need.

### Definition

Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3).

### Why it is included

Shows which domain drives an area's composite score.

### At a glance

| | |
|---|---|
| Theme | composite |
| Role | composite |
| Measure type | score |
| Estimate type | composite experimental |
| Timing | not applicable |
| Reference period | Inputs from several periods, Census 2021 to 2025 (see the composite methodology) |
| Native geography | small_area |
| Published at | small_area, intermediate_area |
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

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.
- **F3: Disability Living Allowance claimants under 16 (Stat-Xplore)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key, suppression; additivity approximate;
  tolerance 15 absolute / 0.03 relative.
- **F4: Personal Independence Payment claimants aged 16-24 (Stat-Xplore)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key, suppression; additivity approximate;
  tolerance 15 absolute / 0.03 relative.
- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-l5-neighbourhood-need-health-disability"></a>

## Neighbourhood need: health disability domain

Release `2dda583978fb-19eda0e60019` · indicator `l5_neighbourhood_need_health_disability` · concept `neighbourhood_need_health_disability`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

The health disability part of the neighbourhood need index; higher means more need.

### Definition

Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3).

### Why it is included

Shows which domain drives an area's composite score.

### At a glance

| | |
|---|---|
| Theme | composite |
| Role | composite |
| Measure type | score |
| Estimate type | composite experimental |
| Timing | not applicable |
| Reference period | Inputs from several periods, Census 2021 to 2025 (see the composite methodology) |
| Native geography | small_area |
| Published at | small_area, intermediate_area |
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

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.
- **F3: Disability Living Allowance claimants under 16 (Stat-Xplore)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key, suppression; additivity approximate;
  tolerance 15 absolute / 0.03 relative.
- **F4: Personal Independence Payment claimants aged 16-24 (Stat-Xplore)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key, suppression; additivity approximate;
  tolerance 15 absolute / 0.03 relative.
- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-l5-neighbourhood-need-safety"></a>

## Neighbourhood need: safety domain

Release `2dda583978fb-19eda0e60019` · indicator `l5_neighbourhood_need_safety` · concept `neighbourhood_need_safety`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

The safety part of the neighbourhood need index; higher means more need.

### Definition

Equal-weighted mean of rank-based normal scores of the domain's eligible indicators (SPEC 12.3 steps 2-3).

### Why it is included

Shows which domain drives an area's composite score.

### At a glance

| | |
|---|---|
| Theme | composite |
| Role | composite |
| Measure type | score |
| Estimate type | composite experimental |
| Timing | not applicable |
| Reference period | Inputs from several periods, Census 2021 to 2025 (see the composite methodology) |
| Native geography | small_area |
| Published at | small_area, intermediate_area |
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

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.
- **F3: Disability Living Allowance claimants under 16 (Stat-Xplore)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key, suppression; additivity approximate;
  tolerance 15 absolute / 0.03 relative.
- **F4: Personal Independence Payment claimants aged 16-24 (Stat-Xplore)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key, suppression; additivity approximate;
  tolerance 15 absolute / 0.03 relative.
- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-l5-neighbourhood-need"></a>

## Neighbourhood need index

Release `2dda583978fb-19eda0e60019` · indicator `l5_neighbourhood_need` · concept `neighbourhood_need`

> **Experimental.** Not endorsed by any official publisher.
> **Draft:** this indicator definition has not yet been reviewed.

A combined measure of need from 4 domains; higher means more need.

### Definition

IoD-style composite (SPEC 12.3): rank-based normal scores within domains, exponentially transformed domain scores, equal domain weights.

### Why it is included

Summarises many indicators for comparison; need and pressure are kept apart.

### At a glance

| | |
|---|---|
| Theme | composite |
| Role | composite |
| Measure type | score |
| Estimate type | composite experimental |
| Timing | not applicable |
| Reference period | Inputs from several periods, Census 2021 to 2025 (see the composite methodology) |
| Native geography | small_area |
| Published at | small_area, intermediate_area |
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

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.
- **F3: Disability Living Allowance claimants under 16 (Stat-Xplore)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key, suppression; additivity approximate;
  tolerance 15 absolute / 0.03 relative.
- **F4: Personal Independence Payment claimants aged 16-24 (Stat-Xplore)** (Department for Work and Pensions). Licence: Open Government Licence v3.0.
  Disclosure control: cell_key, suppression; additivity approximate;
  tolerance 15 absolute / 0.03 relative.
- **F6: Census 2021: households with dependent children by type; occupancy rating of such households** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **F7: Census 2021: disability by age (0-24); unpaid care by age (5-24)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: record_swapping, cell_key; additivity approximate;
  tolerance 10 absolute / 0.01 relative.
- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Experimental (composites version 0.1-experimental); not endorsed by any official publisher. Show the decile with its uncertainty (rank interval, robust decile).

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-hclic-children-in-ta-by-age"></a>

## Children in temporary accommodation

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_hclic_children_in_ta_by_age` · concept `temporary_accommodation`


Children under 18 living in temporary accommodation, per 10,000 children.

### Definition

Children aged under 18 in TA at 31 March 2025 by age band (H-CLIC TA8) / population aged 0-17 x 10,000.

### Why it is included

Age-matched rate of child homelessness.

### At a glance

| | |
|---|---|
| Theme | housing |
| Role | need |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 31 March 2025 |
| Native geography | lad |
| Published at | lad, nation |
| Age bands | source_bands, 0_17 |
| Numerator | Children under 18 in TA (TA8) |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 0-17, mid-2024 MYE |
| Rate | per 10,000 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **Ho1: Statutory homelessness in England: detailed local authority tables (H-CLIC)** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, imputation; additivity approximate;
  tolerance 0 absolute / 0.05 relative.

### Quality and known biases

Non-submitting LAs NULL. Placement may be outside the responsible LA (the count belongs to the placing LA).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 96.3% |
| service_area | 92.8% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-hclic-children-in-ta"></a>

## Children in temporary accommodation

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_hclic_children_in_ta` · concept `temporary_accommodation`


The number of children living in temporary accommodation arranged by the council.

### Definition

Dependent children in households in TA at 31 March 2025 (H-CLIC TA1 total).

### Why it is included

Headline count of homeless children.

### At a glance

| | |
|---|---|
| Theme | housing |
| Role | need |
| Measure type | count |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 31 March 2025 |
| Native geography | lad |
| Published at | lad, nation |
| Age bands | na |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum the counts |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **Ho1: Statutory homelessness in England: detailed local authority tables (H-CLIC)** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, imputation; additivity approximate;
  tolerance 0 absolute / 0.05 relative.

### Quality and known biases

Dependent children may include 16-18 year olds in education, so the count is not age-matched to 0-17; the rate uses the TA8 age-banded indicator.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 96.3% |
| nation | 100.0% |
| service_area | 92.8% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-hclic-households-with-children-in-ta"></a>

## Households with children in temporary accommodation

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_hclic_households_with_children_in_ta` · concept `temporary_accommodation`


The number of homeless families with children living in temporary accommodation arranged by the council.

### Definition

Households with dependent children in TA at 31 March 2025 (H-CLIC TA1).

### Why it is included

Homelessness is among the most acute forms of child housing need.

### At a glance

| | |
|---|---|
| Theme | housing |
| Role | need |
| Measure type | count |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 31 March 2025 |
| Native geography | lad |
| Published at | lad, nation |
| Age bands | na |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum the counts |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **Ho1: Statutory homelessness in England: detailed local authority tables (H-CLIC)** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, imputation; additivity approximate;
  tolerance 0 absolute / 0.05 relative.

### Quality and known biases

Non-submitting LAs are NULL (not_published). Placement may be outside the responsible LA.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 96.3% |
| nation | 100.0% |
| service_area | 92.8% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-hclic-owed-duty-applicants-16-24"></a>

## Young people assessed as homeless or at risk (16-24)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_hclic_owed_duty_applicants_16_24` · concept `youth_homelessness`


Young people aged 16 to 24 whose household the council assessed as homeless or threatened with homelessness, per 10,000 young people.

### Definition

Households with lead applicant aged 16-24 owed a prevention or relief duty in 2024-25 / population aged 16-24 x 10,000.

### Why it is included

Youth homelessness is a core concern for the 16-24 age range.

### At a glance

| | |
|---|---|
| Theme | housing |
| Role | need |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Financial year 2024-25 |
| Native geography | lad |
| Published at | lad, nation |
| Age bands | src_16_24 |
| Numerator | Households with lead applicant 16-24 owed a duty |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 16-24, mid-2024 MYE |
| Rate | per 10,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **Ho1: Statutory homelessness in England: detailed local authority tables (H-CLIC)** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, imputation; additivity approximate;
  tolerance 0 absolute / 0.05 relative.

### Quality and known biases

Lead applicant only (misses young people in other households). Event count.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 93.9% |
| nation | 100.0% |
| service_area | 89.5% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-hclic-owed-duty-households-with-children"></a>

## Families assessed as homeless or at risk

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_hclic_owed_duty_households_with_children` · concept `homelessness_duties`


The number of households with children the council assessed as homeless or threatened with homelessness during the year.

### Definition

Households with dependent children assessed as owed a prevention or relief duty, 2024-25 (annual H-CLIC).

### Why it is included

Wider flow of family homelessness risk beyond those in TA.

### At a glance

| | |
|---|---|
| Theme | housing |
| Role | need |
| Measure type | count |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Financial year 2024-25 |
| Native geography | lad |
| Published at | lad, nation |
| Age bands | na |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum the counts |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **Ho1: Statutory homelessness in England: detailed local authority tables (H-CLIC)** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, imputation; additivity approximate;
  tolerance 0 absolute / 0.05 relative.

### Quality and known biases

Non-submitting LAs NULL. Count only (no household denominator in scope).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 93.2% |
| nation | 100.0% |
| service_area | 88.2% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-barriers-decile"></a>

## Barriers to housing and services (decile)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_barriers_decile` · concept `iod_barriers`


Which tenth of neighbourhoods this one falls in for barriers to housing and services; 1 is the most deprived.

### Definition

IoD 2025 Barriers domain decile (1 = most deprived 10%).

### Why it is included

Display form of the Barriers domain.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | decile |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | better |
| Aggregating to other areas | Share of population in the most deprived national decile (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Deciles are never averaged.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-barriers-la-avg-score"></a>

## Barriers to housing and services: average score

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_barriers_la_avg_score` · concept `iod_barriers`


The average barriers to housing and services score of the authority's neighbourhoods, weighted by how many people live in each.

### Definition

Population-weighted average of IoD 2025 Barriers to Housing and Services domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11).

### Why it is included

The official LA summary of a neighbourhood-level domain, so the domain can be shown in a council-only view (D-0083).

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Averaging hides variation within the LA; read alongside the share of neighbourhoods in the most deprived 10%. Most domain inputs are from 2022/23.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-barriers-la-prop-most-deprived-10pct"></a>

## Barriers to housing and services: neighbourhoods in England's most deprived 10%

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_barriers_la_prop_most_deprived_10pct` · concept `iod_barriers`


The share of the authority's neighbourhoods that are among England's most deprived 10% on this domain.

### Definition

Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Barriers to Housing and Services domain, as published by MHCLG (Files 10 and 11).

### Why it is included

Official LA summary of a neighbourhood-level domain; easy to explain (D-0083).

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | percent published |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Counts areas, not people.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-barriers-score"></a>

## Barriers to housing and services (score)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_barriers_score` · concept `iod_barriers`


How hard it is to get to local services and to afford a decent home.

### Definition

IoD 2025 Barriers to Housing and Services domain score (geographical barriers and wider barriers sub-domains).

### Why it is included

Housing affordability, overcrowding and access to services shape family circumstances.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Population-weighted average of scores (MHCLG method) (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Combines rural access barriers with urban housing barriers, so similar scores can mean very different things.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-crime-decile"></a>

## Crime deprivation (decile)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_crime_decile` · concept `iod_crime`


Which tenth of neighbourhoods this one falls in for crime; 1 is the most deprived.

### Definition

IoD 2025 Crime domain decile (1 = most deprived 10%).

### Why it is included

Display form of the Crime domain.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | decile |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | better |
| Aggregating to other areas | Share of population in the most deprived national decile (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Deciles are never averaged.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-crime-la-avg-score"></a>

## Crime (IoD domain): average score

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_crime_la_avg_score` · concept `iod_crime`


The average crime (iod domain) score of the authority's neighbourhoods, weighted by how many people live in each.

### Definition

Population-weighted average of IoD 2025 Crime domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11).

### Why it is included

The official LA summary of a neighbourhood-level domain, so the domain can be shown in a council-only view (D-0083).

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Averaging hides variation within the LA; read alongside the share of neighbourhoods in the most deprived 10%. Most domain inputs are from 2022/23.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-crime-la-prop-most-deprived-10pct"></a>

## Crime (IoD domain): neighbourhoods in England's most deprived 10%

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_crime_la_prop_most_deprived_10pct` · concept `iod_crime`


The share of the authority's neighbourhoods that are among England's most deprived 10% on this domain.

### Definition

Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Crime domain, as published by MHCLG (Files 10 and 11).

### Why it is included

Official LA summary of a neighbourhood-level domain; easy to explain (D-0083).

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | percent published |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Counts areas, not people.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-crime-score"></a>

## Crime deprivation (score)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_crime_score` · concept `iod_crime`


The neighbourhood's risk of personal and material victimisation, compared with other areas.

### Definition

IoD 2025 Crime domain score (recorded violence, burglary, theft and criminal damage, modelled).

### Why it is included

Published, modelled crime measure that is less noisy than raw police counts.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Population-weighted average of scores (MHCLG method) (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Inputs predate the snapshot. Resident-population denominators distort city-centre areas.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-education-cyp-subdomain-score"></a>

## Children's education deprivation (score)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_education_cyp_subdomain_score` · concept `iod_education_cyp`


How far children and young people in the neighbourhood fall behind in attainment, staying on in education and going on to higher education.

### Definition

IoD 2025 Education domain, Children and Young People sub-domain score (attainment, absence, staying on, entry to higher education).

### Why it is included

The only official small-area measure of children's educational disadvantage.

### At a glance

| | |
|---|---|
| Theme | education |
| Role | need |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Population-weighted average of scores (MHCLG method) (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Sub-domain scores are published but not ranked into deciles by default (verify). Inputs are multi-year averages.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-education-decile"></a>

## Education, skills and training deprivation (decile)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_education_decile` · concept `iod_education`


Which tenth of neighbourhoods this one falls in for education deprivation; 1 is the most deprived.

### Definition

IoD 2025 Education, Skills and Training domain decile (1 = most deprived 10%).

### Why it is included

Display form of the Education domain.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | decile |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | better |
| Aggregating to other areas | Share of population in the most deprived national decile (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Deciles are never averaged.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-education-la-avg-score"></a>

## Education, skills and training deprivation: average score

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_education_la_avg_score` · concept `iod_education`


The average education, skills and training deprivation score of the authority's neighbourhoods, weighted by how many people live in each.

### Definition

Population-weighted average of IoD 2025 Education, Skills and Training domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11).

### Why it is included

The official LA summary of a neighbourhood-level domain, so the domain can be shown in a council-only view (D-0083).

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Averaging hides variation within the LA; read alongside the share of neighbourhoods in the most deprived 10%. Most domain inputs are from 2022/23.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-education-la-prop-most-deprived-10pct"></a>

## Education, skills and training deprivation: neighbourhoods in England's most deprived 10%

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_education_la_prop_most_deprived_10pct` · concept `iod_education`


The share of the authority's neighbourhoods that are among England's most deprived 10% on this domain.

### Definition

Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Education, Skills and Training domain, as published by MHCLG (Files 10 and 11).

### Why it is included

Official LA summary of a neighbourhood-level domain; easy to explain (D-0083).

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | percent published |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Counts areas, not people.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-education-score"></a>

## Education, skills and training deprivation (score)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_education_score` · concept `iod_education`


How far the neighbourhood lacks attainment and skills, among both children and adults.

### Definition

IoD 2025 Education, Skills and Training Deprivation domain score (children and young people sub-domain plus adult skills sub-domain).

### Why it is included

Educational disadvantage is central to CYP outcomes.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Population-weighted average of scores (MHCLG method) (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Mixes child and adult measures; see the CYP sub-domain for children specifically. Some inputs may be affected by pandemic-era assessment changes (check the IoD 2025 technical report).

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-employment-decile"></a>

## Employment deprivation (decile)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_employment_decile` · concept `iod_employment`


Which tenth of neighbourhoods this one falls in for employment deprivation; 1 is the most deprived.

### Definition

IoD 2025 Employment domain decile (1 = most deprived 10%).

### Why it is included

Display form of the Employment domain.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | decile |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | better |
| Aggregating to other areas | Share of population in the most deprived national decile (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Deciles are never averaged.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-employment-la-avg-score"></a>

## Employment deprivation: average score

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_employment_la_avg_score` · concept `iod_employment`


The average employment deprivation score of the authority's neighbourhoods, weighted by how many people live in each.

### Definition

Population-weighted average of IoD 2025 Employment domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11).

### Why it is included

The official LA summary of a neighbourhood-level domain, so the domain can be shown in a council-only view (D-0083).

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Averaging hides variation within the LA; read alongside the share of neighbourhoods in the most deprived 10%. Most domain inputs are from 2022/23.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-employment-la-prop-most-deprived-10pct"></a>

## Employment deprivation: neighbourhoods in England's most deprived 10%

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_employment_la_prop_most_deprived_10pct` · concept `iod_employment`


The share of the authority's neighbourhoods that are among England's most deprived 10% on this domain.

### Definition

Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Employment domain, as published by MHCLG (Files 10 and 11).

### Why it is included

Official LA summary of a neighbourhood-level domain; easy to explain (D-0083).

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | percent published |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Counts areas, not people.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-employment-score"></a>

## Employment deprivation (score)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_employment_score` · concept `iod_employment`


The share of working-age people in the neighbourhood who are kept out of work by unemployment, sickness, disability or caring.

### Definition

IoD 2025 Employment Deprivation domain score: proportion of the working-age population involuntarily excluded from the labour market.

### Why it is included

Parental worklessness is linked to child poverty and family stress.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Population-weighted average of scores (MHCLG method) (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Working-age adults, not CYP-specific. Benefit-based.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-health-decile"></a>

## Health deprivation and disability (decile)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_health_decile` · concept `iod_health`


Which tenth of neighbourhoods this one falls in for health deprivation; 1 is the most deprived.

### Definition

IoD 2025 Health Deprivation and Disability domain decile (1 = most deprived 10%).

### Why it is included

Display form of the Health domain.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | decile |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | better |
| Aggregating to other areas | Share of population in the most deprived national decile (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Deciles are never averaged.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-health-la-avg-score"></a>

## Health deprivation and disability: average score

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_health_la_avg_score` · concept `iod_health`


The average health deprivation and disability score of the authority's neighbourhoods, weighted by how many people live in each.

### Definition

Population-weighted average of IoD 2025 Health Deprivation and Disability domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11).

### Why it is included

The official LA summary of a neighbourhood-level domain, so the domain can be shown in a council-only view (D-0083).

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Averaging hides variation within the LA; read alongside the share of neighbourhoods in the most deprived 10%. Most domain inputs are from 2022/23.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-health-la-prop-most-deprived-10pct"></a>

## Health deprivation and disability: neighbourhoods in England's most deprived 10%

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_health_la_prop_most_deprived_10pct` · concept `iod_health`


The share of the authority's neighbourhoods that are among England's most deprived 10% on this domain.

### Definition

Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Health Deprivation and Disability domain, as published by MHCLG (Files 10 and 11).

### Why it is included

Official LA summary of a neighbourhood-level domain; easy to explain (D-0083).

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | percent published |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Counts areas, not people.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-health-score"></a>

## Health deprivation and disability (score)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_health_score` · concept `iod_health`


How far people in the neighbourhood are at risk of early death or poor quality of life through poor health or disability.

### Definition

IoD 2025 Health Deprivation and Disability domain score.

### Why it is included

Family health and disability affects children's circumstances.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Population-weighted average of scores (MHCLG method) (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Mostly adult measures; not CYP-specific.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-idaci-decile"></a>

## Income deprivation affecting children (decile)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_idaci_decile` · concept `child_poverty`


Which tenth of neighbourhoods this one falls in for child income deprivation; 1 is the most deprived 10%.

### Definition

IDACI 2025 decile of LSOA21 (1 = most deprived 10%).

### Why it is included

Headline display of child income deprivation at neighbourhood level.

### At a glance

| | |
|---|---|
| Theme | child poverty |
| Role | official measure |
| Measure type | decile |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | src_0_15 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | better |
| Aggregating to other areas | Share of population in the most deprived national decile (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Deciles are never averaged; use share in decile 1 for larger areas.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-idaci-la-avg-rank"></a>

## Income deprivation affecting children: average rank

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_idaci_la_avg_rank` · concept `child_poverty`


The average national ranking of the authority's neighbourhoods on child income deprivation. Higher means more deprived.

### Definition

Population-weighted average of IDACI 2025 LSOA ranks, as published by MHCLG (higher = more deprived in IoD 2025, D-0044).

### Why it is included

Official LA summary measure.

### At a glance

| | |
|---|---|
| Theme | child poverty |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | src_0_15 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Published summary of ranks.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-idaci-la-avg-score"></a>

## Income deprivation affecting children: average score

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_idaci_la_avg_score` · concept `child_poverty`


The average share of children in income-deprived families across the authority.

### Definition

Population-weighted average of IDACI 2025 LSOA scores, as published by MHCLG.

### Why it is included

Official LA summary of child income deprivation. Validates T6c (gate 13).

### At a glance

| | |
|---|---|
| Theme | child poverty |
| Role | need |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | src_0_15 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Benefit-based; read alongside CiLIF at LA level.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-idaci-la-prop-most-deprived-10pct"></a>

## Neighbourhoods in England's most deprived 10% for child income

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_idaci_la_prop_most_deprived_10pct` · concept `child_poverty`


The share of the authority's neighbourhoods among England's most deprived 10% for child income deprivation.

### Definition

Proportion of the LA's LSOAs in IDACI 2025 decile 1, as published by MHCLG.

### Why it is included

Official LA summary measure.

### At a glance

| | |
|---|---|
| Theme | child poverty |
| Role | official measure |
| Measure type | percent published |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | src_0_15 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Counts areas, not children.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-idaci-rank"></a>

## Income deprivation affecting children (rank)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_idaci_rank` · concept `child_poverty`


Where the neighbourhood ranks on child income deprivation; 1 is the most deprived.

### Definition

IDACI 2025 rank of LSOA21 (1 = most deprived).

### Why it is included

Published rank of the official child income deprivation measure.

### At a glance

| | |
|---|---|
| Theme | child poverty |
| Role | official measure |
| Measure type | rank |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | src_0_15 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | better |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Ranks are never averaged or summed.

### Coverage

| Level | Areas with a value |
|---|---|
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-idaci-score"></a>

## Income deprivation affecting children (IDACI)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_idaci_score` · concept `child_poverty`


The share of children aged 0 to 15 in the neighbourhood who live in income-deprived families.

### Definition

IDACI 2025 score: proportion of children aged 0-15 living in income-deprived families (MHCLG definition, benefit and tax credit based).

### Why it is included

The official small-area measure of child poverty. The dashboard uses it for child poverty below LA level; CiLIF is used at LA level (shared concept_id child_poverty).

### At a glance

| | |
|---|---|
| Theme | child poverty |
| Role | need |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | src_0_15 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Population-weighted average of scores (MHCLG method) (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Built from benefits data (2022/23 inputs), so it misses families who are eligible but not claiming, and it overlaps with the UC indicator by construction. Excludes ages 16-24.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-imd-decile"></a>

## Index of Multiple Deprivation (decile)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_imd_decile` · concept `imd`


Which tenth of neighbourhoods in England this one falls in; 1 is the most deprived 10%.

### Definition

IMD 2025 decile of LSOA21 (1 = most deprived 10% of LSOAs nationally).

### Why it is included

The headline way the dashboard shows deprivation at neighbourhood level.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | decile |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | better |
| Aggregating to other areas | Share of population in the most deprived national decile (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Deciles are never averaged. For larger areas use the share of population in decile 1 (T6c).

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-imd-la-avg-rank"></a>

## Index of Multiple Deprivation: average rank

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_imd_la_avg_rank` · concept `imd`


The average national ranking of the authority's neighbourhoods, weighted by population. Higher means more deprived.

### Definition

Population-weighted average of IMD 2025 LSOA ranks, as published by MHCLG (IoD 2025 File 10/11; higher = more deprived, verified on inspection, D-0044).

### Why it is included

Official LA summary measure.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

A published summary of ranks. This project never computes its own average of ranks.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-imd-la-avg-score"></a>

## Index of Multiple Deprivation: average score

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_imd_la_avg_score` · concept `imd`


The average deprivation of the local authority, weighted by how many people live in each neighbourhood.

### Definition

Population-weighted average of IMD 2025 LSOA scores, as published by MHCLG for LAD and UTLA.

### Why it is included

The official LA summary. Recomputed from D1 to validate the T6c method (gate 13).

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Averaging hides variation within the LA; read alongside extent and local concentration.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-imd-la-extent"></a>

## Index of Multiple Deprivation: extent

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_imd_la_extent` · concept `imd`


The share of the authority's population living in the most deprived areas of England.

### Definition

MHCLG extent measure: proportion of the LA population living in the most deprived LSOAs nationally (weighted, top 30%).

### Why it is included

Official LA summary measure of how widespread deprivation is.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | percent published |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Published proportion; no CI.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-imd-la-local-concentration"></a>

## Index of Multiple Deprivation: local concentration

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_imd_la_local_concentration` · concept `imd`


How deprived the authority's most deprived neighbourhoods are. Higher means more deprived.

### Definition

Population-weighted average rank of the LA's most deprived LSOAs containing 10% of its population (MHCLG; higher = more deprived in IoD 2025, D-0044).

### Why it is included

Official LA summary measure of deprivation hotspots.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Published summary of ranks.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-imd-la-prop-most-deprived-10pct"></a>

## Neighbourhoods in England's most deprived 10%

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_imd_la_prop_most_deprived_10pct` · concept `imd`


The share of the authority's neighbourhoods that are among the most deprived 10% in England.

### Definition

Proportion of the LA's LSOAs in IMD 2025 decile 1, as published by MHCLG.

### Why it is included

Official LA summary measure; easy to explain.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | percent published |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Counts areas, not people.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-imd-rank"></a>

## Index of Multiple Deprivation (rank)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_imd_rank` · concept `imd`


Where the neighbourhood ranks among all neighbourhoods in England; 1 is the most deprived.

### Definition

IMD 2025 rank of LSOA21 among all English LSOAs (1 = most deprived).

### Why it is included

Published rank, as used by partners and commissioners.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | rank |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | better |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Ranks are never averaged or summed. Small score differences can produce large rank differences in the middle of the distribution.

### Coverage

| Level | Areas with a value |
|---|---|
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-imd-score"></a>

## Index of Multiple Deprivation (score)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_imd_score` · concept `imd`


The official overall measure of how deprived a neighbourhood is, combining income, jobs, education, health, crime, housing and living environment.

### Definition

IMD 2025 score for LSOA21: weighted combination of seven exponentially transformed domain scores (MHCLG method).

### Why it is included

The official, widely understood benchmark for neighbourhood deprivation. Shown as published, and used to check the L5 composites against (convergent validity).

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Population-weighted average of scores (MHCLG method) (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Relative measure: ranks areas, it does not measure absolute change. Most inputs are 2022/23. Scores should not be averaged across areas except by MHCLG's population-weighted method (T6c).

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-income-decile"></a>

## Income deprivation (decile)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_income_decile` · concept `iod_income`


Which tenth of neighbourhoods this one falls in for income deprivation; 1 is the most deprived.

### Definition

IoD 2025 Income domain decile (1 = most deprived 10%).

### Why it is included

Display form of the Income domain.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | decile |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | better |
| Aggregating to other areas | Share of population in the most deprived national decile (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Deciles are never averaged.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-income-la-avg-score"></a>

## Income deprivation: average score

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_income_la_avg_score` · concept `iod_income`


The average income deprivation score of the authority's neighbourhoods, weighted by how many people live in each.

### Definition

Population-weighted average of IoD 2025 Income domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11).

### Why it is included

The official LA summary of a neighbourhood-level domain, so the domain can be shown in a council-only view (D-0083).

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Averaging hides variation within the LA; read alongside the share of neighbourhoods in the most deprived 10%. Most domain inputs are from 2022/23.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-income-la-prop-most-deprived-10pct"></a>

## Income deprivation: neighbourhoods in England's most deprived 10%

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_income_la_prop_most_deprived_10pct` · concept `iod_income`


The share of the authority's neighbourhoods that are among England's most deprived 10% on this domain.

### Definition

Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Income domain, as published by MHCLG (Files 10 and 11).

### Why it is included

Official LA summary of a neighbourhood-level domain; easy to explain (D-0083).

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | percent published |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Counts areas, not people.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-income-score"></a>

## Income deprivation (score)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_income_score` · concept `iod_income`


The share of people in the neighbourhood on low incomes, measured through benefits.

### Definition

IoD 2025 Income Deprivation domain score: proportion of the population experiencing income deprivation.

### Why it is included

Household income is a core driver of child outcomes. Published domain.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Population-weighted average of scores (MHCLG method) (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Benefit-based; misses non-claimants. Overlaps with IDACI.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-living-env-decile"></a>

## Living environment deprivation (decile)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_living_env_decile` · concept `iod_living_environment`


Which tenth of neighbourhoods this one falls in for living environment; 1 is the most deprived.

### Definition

IoD 2025 Living Environment domain decile (1 = most deprived 10%).

### Why it is included

Display form of the Living Environment domain.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | decile |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | better |
| Aggregating to other areas | Share of population in the most deprived national decile (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Deciles are never averaged.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-living-env-la-avg-score"></a>

## Living environment deprivation: average score

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_living_env_la_avg_score` · concept `iod_living_env`


The average living environment deprivation score of the authority's neighbourhoods, weighted by how many people live in each.

### Definition

Population-weighted average of IoD 2025 Living Environment domain LSOA scores, as published by MHCLG for LAD and UTLA (Files 10 and 11).

### Why it is included

The official LA summary of a neighbourhood-level domain, so the domain can be shown in a council-only view (D-0083).

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Averaging hides variation within the LA; read alongside the share of neighbourhoods in the most deprived 10%. Most domain inputs are from 2022/23.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-living-env-la-prop-most-deprived-10pct"></a>

## Living environment deprivation: neighbourhoods in England's most deprived 10%

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_living_env_la_prop_most_deprived_10pct` · concept `iod_living_env`


The share of the authority's neighbourhoods that are among England's most deprived 10% on this domain.

### Definition

Proportion of the LA's LSOAs in decile 1 of the IoD 2025 Living Environment domain, as published by MHCLG (Files 10 and 11).

### Why it is included

Official LA summary of a neighbourhood-level domain; easy to explain (D-0083).

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | percent published |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 |
| Native geography | lad |
| Published at | lad, service_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1b: English Indices of Deprivation 2025: local authority summary measures** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Counts areas, not people.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-living-env-score"></a>

## Living environment deprivation (score)

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_living_env_score` · concept `iod_living_environment`


The quality of housing and the local environment, such as air quality and road traffic accidents.

### Definition

IoD 2025 Living Environment Deprivation domain score (indoors and outdoors sub-domains).

### Why it is included

Housing quality and the environment affect child health.

### At a glance

| | |
|---|---|
| Theme | deprivation |
| Role | official measure |
| Measure type | score |
| Estimate type | index |
| Timing | not applicable |
| Reference period | IoD 2025 (most inputs 2022/23) |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Population-weighted average of scores (MHCLG method) (weights: [Population used in the IoD 2025](#page-indicators-mhclg-iod25-population)) |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Indicators are partly modelled.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-mhclg-iod25-population"></a>

## Population used in the IoD 2025

Release `2dda583978fb-19eda0e60019` · indicator `mhclg_iod25_population` · concept `iod_population`


The population figures MHCLG used to build the Indices of Deprivation 2025.

### Definition

Population denominators published with IoD 2025, by LSOA (total, and the child and older-people bases where published).

### Why it is included

Weights for the MSOA and custom-region IoD summaries (T6c) must be the ones MHCLG used, so that the LAD summaries can be reproduced and checked against D1b (gate 13).

### At a glance

| | |
|---|---|
| Theme | population |
| Role | denominator |
| Measure type | count |
| Estimate type | model based |
| Timing | stock |
| Reference period | As published with IoD 2025 |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages, src_0_15 |
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

### Sources

- **D1: English Indices of Deprivation 2025: LSOA ranks, deciles and scores** (Ministry of Housing, Communities and Local Government). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity none;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Population base differs from mid-2024 SAPE. Used only as IoD weights, never as a general denominator.

### Coverage

| Level | Areas with a value |
|---|---|
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-nhse-gp-registered-patients"></a>

## GP-registered population

Release `2dda583978fb-19eda0e60019` · indicator `nhse_gp_registered_patients` · concept `population_gp_registered`


The number of people registered with a GP who live in each neighbourhood.

### Definition

Patients registered at GP practices in England on 1 April 2025, by Sub-ICB location (April 2024 configuration), single year of age (0 to 95+, stored to 90+) and sex, as published by NHS England.

### Why it is included

NHS activity data (MHSDS) is attributed by GP registration, so health-geography weights and denominators use the registered population, not the resident population (SPEC 4.4).

### At a glance

| | |
|---|---|
| Theme | population |
| Role | denominator |
| Measure type | count |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | 1 April 2025 |
| Native geography | SICBL24 |
| Published at | SICBL24 |
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

### Sources

- **G3b: Patients Registered at a GP Practice (LSOA by age and sex)** (NHS England). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Published by Sub-ICB location only: NHS England publishes no LSOA x age file (LSOA files are all ages), so LSOA counts are used only as apportionment weights (D-0070). Registered lists are inflated by people who have moved away or died ('list inflation'), most of all among young adults and in cities. Not the same as the resident population.

### Coverage

| Level | Areas with a value |
|---|---|
| SICBL24 | 100.0% |
| lad | 14.5% |
| nation | 100.0% |
| service_area | 30.1% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-nhse-mhsds-cyp-one-plus-contact-12m"></a>

## Children supported by NHS mental health services

Release `2dda583978fb-19eda0e60019` · indicator `nhse_mhsds_cyp_one_plus_contact_12m` · concept `cyp_mental_health_access`


Children and young people who had at least one contact with NHS mental health services in the past year, per 10,000 registered with a GP.

### Definition

MHSDS measure MHS95: children and young people aged under 18 supported through NHS-funded mental health services with at least one contact in the 12 months to 31 March 2025, by Sub-ICB of GP practice or residence / GP-registered population aged 0-17 on 1 April 2025 x 10,000.

### Why it is included

The NHS access measure for CYP mental health; indicates service activity, not prevalence.

### At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 12 months to 31 March 2025 |
| Native geography | SICBL24 |
| Published at | SICBL24 |
| Age bands | 0_17 |
| Numerator | CYP 0-17 with 1+ contact, rolling 12 months |
| Denominator | [GP-registered population](#page-indicators-nhse-gp-registered-patients): GP-registered population aged 0-17, 1 April 2025, as published by Sub-ICB (G3b) |
| Rate | per 10,000 |
| Uncertainty | Wilson score interval (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | neither better nor worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **H1: Mental Health Services Monthly Statistics (MHSDS), March 2025 performance** (NHS England). Licence: Open Government Licence v3.0.
  Disclosure control: rounding, suppression; additivity approximate;
  tolerance 5 absolute / 0.01 relative.

### Quality and known biases

A deduplicated person count: Sub-ICB figures sum to more than England (a child can be seen in two Sub-ICBs), so it is never summed across areas (D-0072). Rounded to 5, with suppression. Attributed by GP registration. Data quality varies between providers. Sub-ICB geography: LA values are relabelled, aggregated or shown as fallback per relationship type.

### Coverage

| Level | Areas with a value |
|---|---|
| SICBL24 | 100.0% |
| lad | 14.2% |
| nation | 100.0% |
| service_area | 28.8% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-nhse-mhsds-cyp-open-referrals"></a>

## Children with open mental health referrals

Release `2dda583978fb-19eda0e60019` · indicator `nhse_mhsds_cyp_open_referrals` · concept `cyp_mental_health_caseload`


Children and young people in contact with NHS mental health services at the end of March 2025.

### Definition

MHSDS measure CYP23: open referrals to children and young people's mental health services at the end of March 2025, by Sub-ICB of GP practice or residence.

### Why it is included

Stock of current CYP mental health caseload.

### At a glance

| | |
|---|---|
| Theme | service demand |
| Role | pressure |
| Measure type | count |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 31 March 2025 |
| Native geography | SICBL24 |
| Published at | SICBL24 |
| Age bands | na |
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

### Sources

- **H1: Mental Health Services Monthly Statistics (MHSDS), March 2025 performance** (NHS England). Licence: Open Government Licence v3.0.
  Disclosure control: rounding, suppression; additivity approximate;
  tolerance 5 absolute / 0.01 relative.

### Quality and known biases

Rounded to 5; provider data quality varies. Counts referrals to CYP services, not people of a stated age, so it is not age-banded (D-0072).

### Coverage

| Level | Areas with a value |
|---|---|
| SICBL24 | 100.0% |
| lad | 23.3% |
| nation | 100.0% |
| service_area | 39.2% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-ofsted-childrens-homes-places"></a>

## Children's home places

Release `2dda583978fb-19eda0e60019` · indicator `ofsted_childrens_homes_places` · concept `childrens_homes_supply`


The number of places in registered children's homes in the council area (totals only).

### Definition

Registered places in children's homes located in the LA at 31 March 2025 (LA aggregate only).

### Why it is included

Capacity measure for placement sufficiency.

### At a glance

| | |
|---|---|
| Theme | service pressure |
| Role | pressure |
| Measure type | count |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 31 March 2025 |
| Native geography | service_area |
| Published at | service_area |
| Age bands | na |
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

### Sources

- **C5: Ofsted ILACS judgements and children's social care provider counts** (Ofsted). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity exact;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

As for homes count.

### Coverage

| Level | Areas with a value |
|---|---|
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-ofsted-childrens-homes"></a>

## Children's homes

Release `2dda583978fb-19eda0e60019` · indicator `ofsted_childrens_homes` · concept `childrens_homes_supply`


The number of registered children's homes located in the council area. Only totals for the whole council area are given, never locations.

### Definition

Count of Ofsted-registered children's homes located in the LA at 31 March 2025 (LA-level aggregate only; principle 13).

### Why it is included

Placement sufficiency: where homes are located compared with where children in care come from.

### At a glance

| | |
|---|---|
| Theme | service pressure |
| Role | pressure |
| Measure type | count |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | At 31 March 2025 |
| Native geography | service_area |
| Published at | service_area |
| Age bands | na |
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

### Sources

- **C5: Ofsted ILACS judgements and children's social care provider counts** (Ofsted). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity exact;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Location of supply, not use by local children; many homes are run by private providers and serve other LAs.

### Coverage

| Level | Areas with a value |
|---|---|
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-ofsted-ilacs-overall-effectiveness"></a>

## Ofsted judgement: children's services

Release `2dda583978fb-19eda0e60019` · indicator `ofsted_ilacs_overall_effectiveness` · concept `ofsted_ilacs`


Ofsted's most recent overall judgement of the council's children's services, from Outstanding to Inadequate.

### Definition

Overall effectiveness grade from the most recent ILACS inspection published on or before 31 March 2025; category codes in config/categories.yaml; inspection date recorded as period_end.

### Why it is included

Independent assessment of system quality; context for pressure measures.

### At a glance

| | |
|---|---|
| Theme | service pressure |
| Role | pressure |
| Measure type | ordinal |
| Estimate type | administrative count |
| Timing | stock |
| Reference period | Most recent inspection at 31 March 2025 |
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
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **C5: Ofsted ILACS judgements and children's social care provider counts** (Ofsted). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity exact;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Inspections are years apart, so a judgement can be several years old. Ordinal (not interval) data; never averaged.

### Coverage

| Level | Areas with a value |
|---|---|
| service_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-ohid-ae-attendances-0-4"></a>

## A&E attendances (under 5s)

Release `2dda583978fb-19eda0e60019` · indicator `ohid_ae_attendances_0_4` · concept `ae_attendances`


Visits to A&E by children under 5, per 1,000 children.

### Definition

A&E attendances, ages 0-4, crude rate per 1,000 as published by OHID.

### Why it is included

Proxy for access to primary care and for child health pressures.

### At a glance

| | |
|---|---|
| Theme | health |
| Role | need |
| Measure type | rate published |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Latest year ending on or before 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | 0_4 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | Publisher's own interval |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **H2: Fingertips: Child and Maternal Health profile (API)** (Office for Health Improvement and Disparities). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Reflects access to primary care and local service models as well as need (practice_sensitive).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-ohid-infant-mortality"></a>

## Infant mortality

Release `2dda583978fb-19eda0e60019` · indicator `ohid_infant_mortality` · concept `infant_mortality`


Deaths of babies under one year old, per 1,000 live births, pooled over three years.

### Definition

Infant deaths under 1 year per 1,000 live births, 3-year pooled, as published by OHID.

### Why it is included

Fundamental marker of maternal and infant health inequality.

### At a glance

| | |
|---|---|
| Theme | health |
| Role | need |
| Measure type | rate published |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Latest 3-year pooled period ending on or before 2024 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_infant |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | Publisher's own interval |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **H2: Fingertips: Child and Maternal Health profile (API)** (Office for Health Improvement and Disparities). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Small numbers; three-year pooled period (recorded on the row). Births denominator, not population.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-ohid-injury-admissions-0-14"></a>

## Hospital admissions for injuries (0-14)

Release `2dda583978fb-19eda0e60019` · indicator `ohid_injury_admissions_0_14` · concept `child_injuries`


Hospital admissions for injuries among children aged 0 to 14, per 10,000 children.

### Definition

Emergency admissions for unintentional and deliberate injuries, ages 0-14, crude rate per 10,000 as published.

### Why it is included

Reflects home safety, supervision and environmental risk.

### At a glance

| | |
|---|---|
| Theme | health |
| Role | need |
| Measure type | rate published |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Latest year ending on or before 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_0_14 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | Publisher's own interval |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **H2: Fingertips: Child and Maternal Health profile (API)** (Office for Health Improvement and Disparities). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Admission thresholds vary by trust.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-ohid-low-birthweight-term"></a>

## Low birth weight (full-term babies)

Release `2dda583978fb-19eda0e60019` · indicator `ohid_low_birthweight_term` · concept `low_birthweight`


The share of babies born at full term who weigh under 2.5 kg.

### Definition

Live births at >= 37 weeks gestation with birth weight < 2,500 g / all live term births with recorded weight, % as published.

### Why it is included

Marker of maternal health and deprivation affecting the start of life.

### At a glance

| | |
|---|---|
| Theme | health |
| Role | need |
| Measure type | percent published |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Latest calendar year published |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | na |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | Publisher's own interval |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **H2: Fingertips: Child and Maternal Health profile (API)** (Office for Health Improvement and Disparities). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Births denominator; small numbers in small LAs.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-ohid-ndtms-adults-in-treatment-living-with-children"></a>

## Adults in drug/alcohol treatment living with children

Release `2dda583978fb-19eda0e60019` · indicator `ohid_ndtms_adults_in_treatment_living_with_children` · concept `parental_substance_misuse`


The number of adults in drug or alcohol treatment who live with children.

### Definition

Adults in structured drug/alcohol treatment in 2024-25 who live with children (own or others'), NDTMS.

### Why it is included

Measures parental substance misuse through treatment contact.

### At a glance

| | |
|---|---|
| Theme | family risk |
| Role | need |
| Measure type | count |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Financial year 2024-25 |
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
| Aggregating to other areas | Sum the counts |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **H3: NDTMS: adults in treatment who live with or are parents of children** (Office for Health Improvement and Disparities). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 5 absolute / 0.01 relative.

### Quality and known biases

Treatment contact only; reflects treatment access as well as prevalence.

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-ohid-ndtms-parents-not-living-with-children"></a>

## Parents in drug/alcohol treatment not living with their children

Release `2dda583978fb-19eda0e60019` · indicator `ohid_ndtms_parents_not_living_with_children` · concept `parental_substance_misuse`


The number of parents in drug or alcohol treatment who do not live with their children.

### Definition

Adults in structured treatment in 2024-25 who are parents not living with their children, NDTMS.

### Why it is included

Complements the 'living with children' measure.

### At a glance

| | |
|---|---|
| Theme | family risk |
| Role | need |
| Measure type | count |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Financial year 2024-25 |
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
| Aggregating to other areas | Sum the counts |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **H3: NDTMS: adults in treatment who live with or are parents of children** (Office for Health Improvement and Disparities). Licence: Open Government Licence v3.0.
  Disclosure control: suppression, rounding; additivity approximate;
  tolerance 5 absolute / 0.01 relative.

### Quality and known biases

As above.

### Coverage

_Coverage is generated at release._

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-ohid-self-harm-admissions-10-24"></a>

## Hospital admissions for self-harm (10-24)

Release `2dda583978fb-19eda0e60019` · indicator `ohid_self_harm_admissions_10_24` · concept `self_harm`


Hospital admissions caused by self-harm among young people aged 10 to 24, per 100,000 young people.

### Definition

Emergency hospital admissions for intentional self-harm, ages 10-24, rate per 100,000 as published by OHID (count and published CI also stored).

### Why it is included

The main LA-level measure of serious mental distress in young people.

### At a glance

| | |
|---|---|
| Theme | health |
| Role | need |
| Measure type | rate published |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Latest year ending on or before 31 March 2025 |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_10_24 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | Publisher's own interval |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **H2: Fingertips: Child and Maternal Health profile (API)** (Office for Health Improvement and Disparities). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Captures only admissions, not all self-harm. Coding and admission practice vary by trust. Check whether the published rate is crude or directly standardised.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.6% |
| nation | 100.0% |
| service_area | 98.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-ohid-under18-conceptions"></a>

## Under-18 conceptions

Release `2dda583978fb-19eda0e60019` · indicator `ohid_under18_conceptions` · concept `teenage_conceptions`


Conceptions among young women under 18, per 1,000 women aged 15 to 17.

### Definition

Conceptions to women aged under 18 per 1,000 females aged 15-17, as published by OHID (ONS source).

### Why it is included

Linked to deprivation and to poorer outcomes for young parents and their children.

### At a glance

| | |
|---|---|
| Theme | health |
| Role | need |
| Measure type | rate published |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Latest calendar year published |
| Native geography | service_area |
| Published at | service_area, nation |
| Age bands | src_15_17 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | Publisher's own interval |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **H2: Fingertips: Child and Maternal Health profile (API)** (Office for Health Improvement and Disparities). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.001 relative.

### Quality and known biases

Published with a lag; calendar-year period. Includes conceptions leading to abortion.

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.9% |
| nation | 100.0% |
| service_area | 98.7% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-ons-mye-population"></a>

## Population

Release `2dda583978fb-19eda0e60019` · indicator `ons_mye_population` · concept `population`


The estimated number of people living in each local authority, by single year of age and sex.

### Definition

ONS mid-year population estimates, single year of age (0 to 90+) by sex, as published for LAD, UTLA and England.

### Why it is included

Denominator for LA-level rates. Published figures are used at each level (principle 6).

### At a glance

| | |
|---|---|
| Theme | population |
| Role | denominator |
| Measure type | count |
| Estimate type | model based |
| Timing | stock |
| Reference period | 30 June 2024 (mid-2024) |
| Native geography | lad |
| Published at | lad, service_area, nation |
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

### Sources

- **P1b: Mid-year population estimates, single year of age and sex (LAD, UTLA, England)** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity exact;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Official estimates; quality is lower for LAs with high migration or large student populations. Mid-2024 sits 9 months before the 31 March 2025 reference date (within max_denominator_gap_days).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| lad | 54,168 | 54,168 | 0 | 0.00% |
| nation | 183 | 183 | 0 | 0.00% |
| service_area | 27,999 | 27,999 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-ons-sape-population"></a>

## Population

Release `2dda583978fb-19eda0e60019` · indicator `ons_sape_population` · concept `population`


The estimated number of people living in each neighbourhood, by single year of age and sex.

### Definition

ONS mid-year Small Area Population Estimates for LSOA21, single year of age (0 to 90+) by sex.

### Why it is included

Denominator for every small-area rate. Stored by single year of age so that a denominator can be built exactly for any source age band (SPEC section 3).

### At a glance

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

### Sources

- **P1: Lower layer Super Output Area population estimates (Small Area Population Estimates), single year of age and sex** (Office for National Statistics). Licence: Open Government Licence v3.0.
  Disclosure control: none; additivity exact;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Model-based estimates constrained to LA mid-year totals. Small areas carry more uncertainty than LAs (no published CIs). Areas with large student or armed-forces populations are less reliable at ages 18-24.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

| Level | Pairs | Within tolerance | Largest difference | Largest relative |
|---|---|---|---|---|
| intermediate_area | 1,254,648 | 1,254,648 | 0 | 0.00% |

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-police-asb-incidents"></a>

## Anti-social behaviour

Release `2dda583978fb-19eda0e60019` · indicator `police_asb_incidents` · concept `recorded_asb`


Anti-social behaviour incidents reported to the police in the neighbourhood per 1,000 residents over the year. Area context.

### Definition

Street-level records with category 'Anti-social behaviour', Apr 2024 - Mar 2025, per 1,000 usual residents.

### Why it is included

Indicates perceived local disorder.

### At a glance

| | |
|---|---|
| Theme | safety |
| Role | context |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 1 April 2024 to 31 March 2025 |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | Street-level ASB records |
| Denominator | [Population](#page-indicators-ons-sape-population): Usual resident population, all ages, mid-2024 (SAPE) |
| Rate | per 1,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Incidents, not crimes. Recording varies a great deal by force.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-police-crime-all-excl-asb"></a>

## Recorded crime

Release `2dda583978fb-19eda0e60019` · indicator `police_crime_all_excl_asb` · concept `recorded_crime`


Crimes recorded by the police in the neighbourhood per 1,000 residents over the year. This describes the area, not crimes against children.

### Definition

Count of street-level crime records (all categories except anti-social behaviour), assigned to LSOA21 by coordinates, Apr 2024 - Mar 2025, per 1,000 usual residents (all ages).

### Why it is included

Area safety is part of children's environment. Shown as area context, not as a CYP outcome.

### At a glance

| | |
|---|---|
| Theme | safety |
| Role | context |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 1 April 2024 to 31 March 2025 |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | Street-level crime records excluding ASB |
| Denominator | [Population](#page-indicators-ons-sape-population): Usual resident population, all ages, mid-2024 (SAPE) |
| Rate | per 1,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Locations are snapped to anonymous points. Recording practice varies by force. Resident denominators overstate rates in town centres and other high-footfall areas (low_validity_denominator). Check for forces with missing months.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-police-crime-drugs"></a>

## Drug offences

Release `2dda583978fb-19eda0e60019` · indicator `police_crime_drugs` · concept `recorded_crime_drugs`


Drug offences recorded in the neighbourhood per 1,000 residents over the year. Area context.

### Definition

Street-level records with category 'Drugs', Apr 2024 - Mar 2025, per 1,000 usual residents.

### Why it is included

Linked to county lines and child criminal exploitation.

### At a glance

| | |
|---|---|
| Theme | safety |
| Role | context |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 1 April 2024 to 31 March 2025 |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | Street-level 'Drugs' records |
| Denominator | [Population](#page-indicators-ons-sape-population): Usual resident population, all ages, mid-2024 (SAPE) |
| Rate | per 1,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Strongly driven by police activity rather than underlying prevalence.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-police-crime-violence-sexual"></a>

## Violence and sexual offences

Release `2dda583978fb-19eda0e60019` · indicator `police_crime_violence_sexual` · concept `recorded_crime_violence`


Violent and sexual crimes recorded in the neighbourhood per 1,000 residents over the year. Area context.

### Definition

Street-level records with category 'Violence and sexual offences', Apr 2024 - Mar 2025, per 1,000 usual residents.

### Why it is included

Violence is the crime type most relevant to children's safety. Area context, used in the neighbourhood need index.

### At a glance

| | |
|---|---|
| Theme | safety |
| Role | context |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 1 April 2024 to 31 March 2025 |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | Street-level 'Violence and sexual offences' records |
| Denominator | [Population](#page-indicators-ons-sape-population): Usual resident population, all ages, mid-2024 (SAPE) |
| Rate | per 1,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Includes domestic incidents recorded at home addresses. Same location and denominator caveats as all crime.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-police-crime-weapons-possession"></a>

## Possession of weapons

Release `2dda583978fb-19eda0e60019` · indicator `police_crime_weapons_possession` · concept `recorded_crime_weapons`


Weapon possession offences recorded in the neighbourhood per 1,000 residents over the year. Area context.

### Definition

Street-level records with category 'Possession of weapons', Apr 2024 - Mar 2025, per 1,000 usual residents.

### Why it is included

Relevant to youth violence and exploitation concerns.

### At a glance

| | |
|---|---|
| Theme | safety |
| Role | context |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | 1 April 2024 to 31 March 2025 |
| Native geography | small_area |
| Published at | small_area |
| Age bands | all_ages |
| Numerator | Street-level 'Possession of weapons' records |
| Denominator | [Population](#page-indicators-ons-sape-population): Usual resident population, all ages, mid-2024 (SAPE) |
| Rate | per 1,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **S1: data.police.uk street-level crime, April 2024 to March 2025** (Home Office / police forces (data.police.uk)). Licence: Open Government Licence v3.0.
  Disclosure control: location_anonymisation; additivity exact;
  tolerance 0 absolute / 0 relative.

### Quality and known biases

Small counts; largely reflects proactive policing such as stop and search. Use the EB-smoothed rate.

### Coverage

| Level | Areas with a value |
|---|---|
| intermediate_area | 100.0% |
| lad | 100.0% |
| nation | 100.0% |
| service_area | 100.0% |
| small_area | 100.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-yjb-custodial-sentences-10-17"></a>

## Custodial sentences (10-17)

Release `2dda583978fb-19eda0e60019` · indicator `yjb_custodial_sentences_10_17` · concept `youth_custody`


The number of custodial sentences given to children aged 10 to 17 in the year.

### Definition

Custodial sentences to children aged 10-17, year ending March 2025, by YJS.

### Why it is included

The most serious justice outcome.

### At a glance

| | |
|---|---|
| Theme | safety |
| Role | need |
| Measure type | count |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Year ending 31 March 2025 |
| Native geography | YJS |
| Published at | YJS |
| Age bands | src_10_17 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum the counts |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **S3: Youth justice statistics 2024 to 2025** (Youth Justice Board / Ministry of Justice). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Very small numbers; suppression likely. Count only.

### Coverage

| Level | Areas with a value |
|---|---|
| YJS | 100.0% |
| lad | 36.5% |
| service_area | 83.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-yjb-first-time-entrants-10-17"></a>

## First-time entrants to youth justice

Release `2dda583978fb-19eda0e60019` · indicator `yjb_first_time_entrants_10_17` · concept `first_time_entrants`


Children aged 10 to 17 receiving their first caution or conviction during the year, per 10,000 children of that age.

### Definition

Child first-time entrants (aged 10-17) to the youth justice system per 100,000 population aged 10-17, by local authority of residence, year ending December 2024, as published by YJB/MoJ (supplementary table 2.11).

### Why it is included

Key measure of children's involvement with the justice system.

### At a glance

| | |
|---|---|
| Theme | safety |
| Role | need |
| Measure type | rate published |
| Estimate type | model based |
| Timing | flow |
| Reference period | Year ending 31 December 2024 |
| Native geography | service_area |
| Published at | service_area |
| Age bands | src_10_17 |
| Numerator | — |
| Denominator | — |
| Rate | — |
| Uncertainty | None |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Cannot be aggregated to other areas |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **S3: Youth justice statistics 2024 to 2025** (Youth Justice Board / Ministry of Justice). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Reflects policing and diversion practice. MoJ allocates children to LAs by home address on the PNC, and by a model for those with no address, so figures are estimates. Areas with fewer than 10 FTEs are suppressed. Year to December 2024 (the latest published), not March 2025 (D-0073).

### Coverage

| Level | Areas with a value |
|---|---|
| lad | 43.2% |
| service_area | 97.4% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)

---

<a id="page-indicators-yjb-proven-offences-10-17"></a>

## Proven offences by children (10-17)

Release `2dda583978fb-19eda0e60019` · indicator `yjb_proven_offences_10_17` · concept `proven_offences`


Offences by children aged 10 to 17 that resulted in a caution or conviction, per 10,000 children.

### Definition

Proven offences by children aged 10-17, year ending March 2025 / population aged 10-17 x 10,000.

### Why it is included

Volume of youth offending dealt with by the justice system.

### At a glance

| | |
|---|---|
| Theme | safety |
| Role | need |
| Measure type | rate |
| Estimate type | administrative count |
| Timing | flow |
| Reference period | Year ending 31 March 2025 |
| Native geography | YJS |
| Published at | YJS |
| Age bands | src_10_17 |
| Numerator | Proven offences, ages 10-17 |
| Denominator | [Population](#page-indicators-ons-mye-population): Population aged 10-17, mid-2024 MYE, summed over the YJS's member UTLAs (G7) |
| Rate | per 10,000 |
| Uncertainty | Byar's approximation to the exact Poisson (95%) |
| Reliability flag | numerator < 10 or denominator < 50 |
| Maximum denominator gap | 366 days |
| Higher values are | worse |
| Aggregating to other areas | Sum numerators and denominators, then divide |
| Suitable for spatial analysis | yes |
| Ethnicity classification | none |

### Sources

- **S3: Youth justice statistics 2024 to 2025** (Youth Justice Board / Ministry of Justice). Licence: Open Government Licence v3.0.
  Disclosure control: suppression; additivity approximate;
  tolerance 0 absolute / 0.005 relative.

### Quality and known biases

Event count; reflects policing practice.

### Coverage

| Level | Areas with a value |
|---|---|
| YJS | 100.0% |
| lad | 36.5% |
| service_area | 83.0% |

### Reconciliation with published totals

_Reconciliation results are generated at release._

---

[Methodology index](#page-index) · [Technical methodology](#page-methodology_technical)
