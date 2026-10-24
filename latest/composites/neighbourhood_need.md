# Neighbourhood need (experimental)

Release `2dda583978fb-19eda0e60019` · composites version `0.1-experimental` · family **need**
· levels small_area, intermediate_area

> **Experimental.** Not endorsed by any official publisher. See the
> [composite methodology](methodology_composite.md).

## Domains and indicators

### Economic hardship

- [Income deprivation affecting children (IDACI)](../indicators/mhclg-iod25-idaci-score.md) (IoD 2025 (most inputs 2022/23))
### Health disability

- [Children receiving Disability Living Allowance](../indicators/dwp-dla-claimants-under16.md) (February 2025)
- [Young people receiving PIP](../indicators/dwp-pip-claimants-16-24.md) (March 2025)
- [Disabled children and young people](../indicators/census21-disabled-0-24.md) (Census Day, 21 March 2021)
### Family housing

- [Overcrowded households with children](../indicators/census21-overcrowded-households-dep-children.md) (Census Day, 21 March 2021)
- [Lone-parent households](../indicators/census21-lone-parent-households-dep-children.md) (Census Day, 21 March 2021)
- [Young carers](../indicators/census21-unpaid-carers-5-24.md) (Census Day, 21 March 2021)
### Safety

- [Violence and sexual offences](../indicators/police-crime-violence-sexual.md) (1 April 2024 to 31 March 2025)

## Notes

Overlaps with IMD by design (IDACI is benefit-based). Report alongside IMD, not instead of it (12.7).

## Results

### Neighbourhood need: small area

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

### Neighbourhood need: intermediate area

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

[Methodology index](../index.md)
