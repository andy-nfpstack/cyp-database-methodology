# A plain-English guide

Release `abffebbd490b-19eda0e60019`

## Areas

England is divided into children's services authorities: the councils responsible for
children's social care and education. Some of these are also responsible for housing;
others (county councils) contain several district councils. Below the councils, the
database uses neighbourhoods defined by the Office for National Statistics: middle-sized
areas (MSOAs, typically 5,000 to 15,000 people) and small areas (LSOAs, typically 1,000 to 3,000 people).

Some measures are only published for whole councils, and some only for areas such as police
forces or NHS areas. We never split a council's figure between its neighbourhoods. Where a
measure only exists for a bigger area, the map shows that bigger area's value, hatched and
labelled.

## Ages and dates

The database covers ages 0 to 24 (and up to 25 where a service runs to 25, such as
education, health and care plans). Each measure keeps the age range its publisher used.
The target date is 31 March 2025, but some sources are older or newer, for example the 2021
Census. Every value shows its own date.

## Why some measures change between levels

Some measures only exist at one level. For example, child poverty in a neighbourhood is
shown using the official Income Deprivation Affecting Children Index, while for a whole
council it is shown using the Children in Low Income Families statistics. They measure
related but different things, and the map tells you which one you are looking at.

## Grey and hatched areas

- **Grey**: no value. The legend says why: hidden to protect privacy, not published,
  incomplete, or not applicable.
- **Hatched**: the value belongs to a bigger area that contains this one.

## Comparing areas fairly

- Compare rates, not counts, unless you want to know about scale.
- Small areas have small numbers, and small numbers jump around. Look at the uncertainty
  range, and use the smoothed rate for small areas.
- Don't rank individual neighbourhoods into "worst area" lists. Look at patterns and at
  deciles (tenths of England).

## The composite indices

The experimental composite indices combine several measures into one score, in the same way as
the official Index of Multiple Deprivation. Need and pressure on services are never
combined. Each score comes with a range showing how much it depends on the choices made
in building it. They are experimental and not endorsed by any official publisher.

## Worked examples

### Reading a rate: children looked after in Barnsley

In Barnsley, 366 children were looked after at 31 Mar 2025,
out of an estimated 51,799 children aged 0 to 17. That is
**70.7 per 10,000 children** (95% interval 63.8 to 78.2),
against 67.1 per 10,000 in England. The interval shows the range a rate like this
could take by chance alone; councils with fewer children have wider intervals.

### A custom area: add up counts and denominators, then divide

South Yorkshire's 4 councils (Barnsley, Rotherham, Doncaster and Sheffield) together had
1,970 children looked after among 295,870 children:
**66.6 per 10,000**. Averaging the four councils' rates instead gives
69.5, which is wrong because it treats a small council the same as a large one.
Always add up the counts and the denominators first, then divide.

### A hatched (fallback) value: child exploitation referrals in Kent

Child referrals to the National Referral Mechanism are only published for police force areas. Kent County
Council's area is inside the Kent police force area, which also covers Medway, so the
map shows the force area's rate, **14.2 per 10,000 children** (during 2024/25), hatched and
labelled. It is not Kent County Council's own figure, and it is never used in rankings or calculations.

### Small numbers: raw and smoothed neighbourhood rates

Neighbourhood E01002882 has about 947 residents and
4 recorded weapons-possession offences in the year, a raw rate of 4.2 per 1,000
(England: 0.84). A count this small can change a lot from one year to the next by chance,
so the database also gives a smoothed rate that leans towards the England figure where the evidence is thin:
3.52 per 1,000.
Use smoothed rates for maps and hotspot analysis, and never rank individual neighbourhoods.

