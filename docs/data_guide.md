# Reading the data

## Identifiers and joins

The pair `(combo_id, run_id)` identifies an execution. The main table has one row per execution. In the temporal table, add `horizon` to obtain a unique observation key. The `combo_id` includes the rule, so the three executions of a matched parameter triplet have different combination IDs. Use `triplet` in `temporal_extension/selection.csv` to identify matched sets.

`agent_id`, `source` and `target` are zero-based and refer to agents within one execution. Join agents and edges using both execution identifiers. Never join edges from different executions by agent ID alone. Each undirected edge occurs once, with `source < target`. Agents with no edges remain in the agent table.

`trait_1` through `trait_8` store integer categorical labels. Only the first `num_features` columns apply to a given execution. The remaining trait columns are empty, meaning that the feature is not part of that execution, not that its value was lost. Valid traits are 0 through `num_traits - 1`.

## Time and stopping

`horizon` is the requested observation time in elementary update attempts; it is not a count of successful cultural or network changes. `actual_steps` is the actual simulation clock. For an absorbed execution it can be smaller than the horizon, and the same state is carried forward. In the main table these quantities are represented by `max_steps_budget` and `steps`; `sweeps = steps / N`.

`status = absorbed` means there are no discordant edges. `status = max_steps` means the observation horizon was reached without that certificate; it does not imply active cultural copying. Distinguish active edges (some but not all traits shared) from zero-overlap edges (no traits shared).

`sample_group` describes the whole matched triplet at 5 million attempts. `baseline_regime` describes the individual execution. `zero_only` means at least one discordant edge and no active edges. The saved `temporal_status.csv` counts individual execution regimes at each horizon.

## Numerical conventions

Entropy is measured with natural logarithms, in nats. Raw simulation `culture_entropy` uses `-sum(p * log(p + 1e-12))`, so numerical values near consensus can be slightly negative. These values are preserved. The independently calculated `entropy` in `cultural_distance_metrics.csv` uses `-sum(p * log(p))` and is nonnegative. Their small difference is numerical, not a different cultural configuration.

Clustering is global transitivity, `3 * number_of_triangles / number_of_connected_triples`, with triples counted by their central vertex. It is not the unweighted average of individual clustering coefficients. An undefined numeric network measure is represented by an empty CSV field or NaN as stored by the original exporter. Such entries must not be silently changed to zero.

Culture size groups agents by the equality of their entire cultural vectors, irrespective of connectivity. A connected cultural domain also requires paths through agents with that same vector. A network component requires connectivity but need not be culturally homogeneous.

Polarization is the operational index `4 * Var(d)`, where `d` is normalized Hamming distance across every distinct unordered agent pair, including pairs in different connected components. Each histogram sums to 499,500 pairs. It does not measure ideological extremity. `effective_cultures = exp(entropy)`.

## Figure summaries

The numerical series for Figures 2 and 3 first average the 10 executions within each parameter cell. Their plotted means then average those cell means over the other parameters. The Monte Carlo standard error is `sqrt(sum(within_cell_sample_variance) / 10) / B`, where `B` is the number of averaged cells. Bounds are mean plus or minus 1.96 times that standard error. Largest-component sizes and their uncertainties are divided by 1,000 where plotted as population fractions.

These intervals are conditional on the chosen parameter grid and initial topologies. They do not estimate variability across independent network realizations. The original alpha grid is retained for all three rules, although alpha does not enter the mean profile selection rule.

## Provenance

The main CSV and temporal observation CSV preserve their original numerical output. English file paths replace the local project organization. Two batch labels in the cultural-distance table were translated to `initial_90` and `additional_111`; unnamed metric columns were labeled `metric`. Final states were exported from existing checkpoints as integer traits and edge lists. No simulation was run to prepare this repository.

The original manifests retain historical source-code hashes and runtime information. Those hashes identify the recorded generating sources; they do not refer to source code included in this data-only repository. Their lists of runtime versions are ordered Python, NumPy, pandas, igraph and joblib. The final-state index records each original checkpoint hash. Selection metadata describes both the original 90 trajectories and the additional 111, without treating the first set as a separate additional sample.

The validation record describes checks against saved results. It does not assert independent validation of the model implementation or regeneration of the simulation campaign.
