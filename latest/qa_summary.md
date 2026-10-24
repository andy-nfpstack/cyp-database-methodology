# QA summary

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

## Reconciliation

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

## Flagged for manual review

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

[Methodology index](index.md)
