# Viz data (cluster nodes & transitions)

The eight files here are the aggregated inputs behind the interactive cluster
explorer (`../docs/`). They cover the full 2×2 of **population × clustering**:

| file stem | population (individuals) | clustering applied |
|---|---|---|
| `*_DK_pop_DK_clusters` | Danish | Danish |
| `*_DK_pop_AT_clusters` | Danish | Austrian |
| `*_AT_pop_DK_clusters` | Austrian | Danish |
| `*_AT_pop_AT_clusters` | Austrian | Austrian |

**`nodes_*.csv`** — one row per cluster (paper numbering, 0–131).
Austrian-population files: `cluster, mean_age, female_ratio, size`.
Danish-population files: `cluster, mean_age, age_q25, age_median, age_q75,
female_ratio, size, size_alive, mortality_rate`.
`size` = number of person-year observations; `mean_age` is the
observation-weighted mean age in the observation year; `size_alive` = alive
person-years (`year <= year of death`); `mortality_rate` = in-hospital deaths
/ `size_alive` (alive person-years). Mortality is available for the Danish
cohort only.

**`links_*.csv`** — cluster-to-cluster yearly transitions as an edge list:
`source, target, value`, where `value` is the transition probability per
source cluster (self-loops included), computed over transitions between
clusters (transitions into death or out of the cohort are excluded before
normalisation).

### Disclosure control
All figures are cluster-level aggregates. Transitions based on fewer than **5**
observed transitions are removed, and mortality is blanked for clusters with
fewer than **5** deaths (rows therefore need not sum exactly to 1), matching the small-count suppression
required by the underlying Danish and Austrian register data agreements.
