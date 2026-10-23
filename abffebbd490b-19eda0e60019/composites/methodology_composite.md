# Composite indices: methodology (experimental)

Release `abffebbd490b-19eda0e60019` · composites version `0.1-experimental`

> **Experimental.** These indices are not endorsed by any official publisher. We welcome
> methodological feedback.

## Framework

There are two families of index, and they are **never combined**:

- **Need**: the underlying circumstances of children, young people and families.
- **System pressure**: demand on services and their capacity. Service activity partly
  reflects local thresholds and practice. Keeping it separate from need avoids circularity,
  and lets the two be compared.

The construction follows MHCLG's Indices of Deprivation method and the OECD/JRC
*Handbook on Constructing Composite Indicators* (2008).

## Eligibility

An indicator enters a composite only if it is native to the composite's level (an observed value,
or a rate built from observed counts), it covers at least 95.0% of areas, and its
polarity is higher-is-worse or higher-is-better (neutral indicators cannot be aligned). Apportioned,
converted, recoded and fallback values are never used. At LSOA and MSOA level, rates are
eb smoothed (Marshall global empirical Bayes), so small numbers do not drive the
result. Eligibility is tested at every level for every release, so an indicator can be eligible at MSOA but
not at LSOA. Survey-calibrated inputs (child poverty) are allowed and flagged.

## Primary method

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

## Uncertainty

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
- [EHC plans (ages 0-25)](../indicators/dfe-ehcps-0-25.md)
- [Pupils with an EHC plan](../indicators/dfe-pupils-with-ehcp.md)
- [A&E attendances (under 5s)](../indicators/ohid-ae-attendances-0-4.md)
- [Domestic abuse identified at assessment](../indicators/dfe-cin-factor-domestic-abuse.md)
- [Parental mental health identified at assessment](../indicators/dfe-cin-factor-parental-mental-health.md)
- [Parental alcohol misuse identified at assessment](../indicators/dfe-cin-factor-parental-alcohol-misuse.md)
- [Parental drug misuse identified at assessment](../indicators/dfe-cin-factor-parental-drug-misuse.md)

## Validation

Convergent validity (against IMD and IDACI 2025), criterion validity (LA need against system pressure,
with residuals published), stability (dropping each indicator in turn) and face validity.

- **Neighbourhood need** (small area): 33,723 of 33,755 areas scored; robust decile for 19.9% of areas over all runs and 42.1% over runs with the primary aggregation; within one decile for 91.3%.
- **Neighbourhood need** (intermediate area): 6,856 of 6,856 areas scored; robust decile for 27.1% of areas over all runs and 56.1% over runs with the primary aggregation; within one decile for 92.0%.
- **La need** (service area): 149 of 153 areas scored; robust decile for 10.7% of areas over all runs and 26.2% over runs with the primary aggregation; within one decile for 70.5%.
- **La system pressure** (service area): 144 of 153 areas scored; robust decile for 10.4% of areas over all runs and 13.9% over runs with the primary aggregation; within one decile for 52.8%. **Index not published: domains only (D-0090).**

Spearman ρ between LA need and LA system pressure: 0.297 (142 areas). The two are never combined. The pressure score here is the combined index, computed internally; only its domains are published (D-0090).

Each composite's page has its full results; the whole report is `l5/l5_validation.md` in the release.

## Composites

- [Neighbourhood need](neighbourhood_need.md) (need; small_area, intermediate_area)
- [La need](la_need.md) (need; service_area)
- [La system pressure](la_system_pressure.md) (pressure; service_area)

## Limitations

The inputs come from different periods. The neighbourhood need index overlaps with IMD by design,
because IDACI is built from benefits data, so it is reported alongside IMD rather than instead of it. A
sub-LA composite can only use indicators that exist below LA level.

---

[Methodology index](../index.md)
