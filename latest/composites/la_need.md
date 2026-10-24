# LA need (experimental)

Release `2dda583978fb-19eda0e60019` · composites version `0.1-experimental` · family **need**
· levels service_area

> **Experimental.** Not endorsed by any official publisher. See the
> [composite methodology](methodology_composite.md).

## Domains and indicators

### Economic hardship

- [Children in relative low income families (%)](../indicators/dwp-cilif-relative-bhc-pct.md) (Financial year ending March 2025)
- [Pupils eligible for free school meals](../indicators/dfe-fsm-eligible-pupils.md) (January 2025)
- [Income deprivation affecting children: average score](../indicators/mhclg-iod25-idaci-la-avg-score.md) (IoD 2025)
### Family risk

- [Lone-parent households](../indicators/census21-lone-parent-households-dep-children.md) (Census Day, 21 March 2021)
- [Domestic abuse identified at assessment](../indicators/dfe-cin-factor-domestic-abuse.md) (1 April 2024 to 31 March 2025): *practice-sensitive*
- [Parental mental health identified at assessment](../indicators/dfe-cin-factor-parental-mental-health.md) (1 April 2024 to 31 March 2025): *practice-sensitive*
- [Parental alcohol misuse identified at assessment](../indicators/dfe-cin-factor-parental-alcohol-misuse.md) (1 April 2024 to 31 March 2025): *practice-sensitive*
- [Parental drug misuse identified at assessment](../indicators/dfe-cin-factor-parental-drug-misuse.md) (1 April 2024 to 31 March 2025): *practice-sensitive*
### Health

- [Hospital admissions for self-harm (10-24)](../indicators/ohid-self-harm-admissions-10-24.md) (Latest year ending on or before 31 March 2025)
- [Hospital admissions for injuries (0-14)](../indicators/ohid-injury-admissions-0-14.md) (Latest year ending on or before 31 March 2025)
- [Disabled children and young people](../indicators/census21-disabled-0-24.md) (Census Day, 21 March 2021)
### Education

- [Persistent absence from school](../indicators/dfe-persistent-absence.md) (Academic year 2024/25)
- [Suspensions from school](../indicators/dfe-suspensions.md) (Academic year 2024/25 (check))
- [16-17 year olds NEET or activity not known](../indicators/dfe-neet-or-not-known-16-17.md) (End 2024 (Dec 2024 - Feb 2025 average))
### Housing

- [Children in temporary accommodation](../indicators/mhclg-hclic-children-in-ta-by-age.md) (At 31 March 2025)
- [Overcrowded households with children](../indicators/census21-overcrowded-households-dep-children.md) (Census Day, 21 March 2021)
### Safety

- [First-time entrants to youth justice](../indicators/yjb-first-time-entrants-10-17.md) (Year ending 31 December 2024)
- [Violence and sexual offences](../indicators/police-crime-violence-sexual.md) (1 April 2024 to 31 March 2025)

## Notes

Census and police inputs enter at service_area as aggregated L2 counts (exact nesting), never apportioned.

## Results

### LA need: service area

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

[Methodology index](../index.md)
