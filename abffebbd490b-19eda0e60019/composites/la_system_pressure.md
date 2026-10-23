# La system pressure (experimental)

Release `abffebbd490b-19eda0e60019` · composites version `0.1-experimental` · family **pressure**
· levels service_area

> **Experimental.** Not endorsed by any official publisher. See the
> [composite methodology](methodology_composite.md).

> **Published as domain scores only.** The combined index is computed to document how robust it
> is, but it is not published: its deciles are not stable enough to use (see Results).

## Domains and indicators

### Demand

- [Children in need](../indicators/dfe-cin-at-31mar.md) (At 31 March 2025)
- [Children on child protection plans](../indicators/dfe-cpp-at-31mar.md) (At 31 March 2025)
- [Children in care](../indicators/dfe-cla-at-31mar.md) (At 31 March 2025)
- [Re-referrals within 12 months](../indicators/dfe-cin-rereferrals-12m.md) (1 April 2024 to 31 March 2025)
- [Child referrals for suspected exploitation (NRM)](../indicators/ho-nrm-referrals-under18.md) (1 April 2024 to 31 March 2025)
### Capacity

- [Social worker vacancy rate](../indicators/dfe-sw-vacancy-rate.md) (At 30 September 2024)
- [Agency social worker rate](../indicators/dfe-sw-agency-rate.md) (At 30 September 2024)
- [Social worker turnover rate](../indicators/dfe-sw-turnover-rate.md) (Year to 30 September 2024)
- [Average social worker caseload](../indicators/dfe-sw-average-caseload.md) (At 30 September 2024)
### Send

- [EHC plans issued on time](../indicators/dfe-ehcp-20wk-timeliness.md) (Calendar year 2024)

## Notes

Published as three domain scores (demand, capacity, SEND); the combined index is withheld (D-0090). Pressure indicators are never in la_need.

## Results

### La system pressure: service area

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

[Methodology index](../index.md)
