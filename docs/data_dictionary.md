# Data dictionary

`init_` and `final_` prefixes mean the initial and final measurements of an execution. The definitions below apply to the unprefixed quantity; the original CSV column names are preserved. Counts and IDs are integers, fractions are dimensionless, and entropy uses nats.

| Column | Meaning |
| --- | --- |
| `model_version` | Recorded simulation implementation identifier. |
| `combo_id` | Parameter combination identifier, including the partner selection rule. |
| `run_id` | Repetition index within the parameter combination. |
| `master_seed` | Master seed; preserve as text. |
| `combo_seed` | Seed used for the parameter combination; preserve as text. |
| `combo_seed_for_runs` | Recorded combination seed used for run generation; preserve as text. |
| `seed` | Execution random seed; preserve as text. |
| `N` | Number of agents. |
| `m_attach` | Initial preferential-attachment parameter m. |
| `num_features` | Number F of cultural features per agent. |
| `num_traits` | Number q of categorical trait labels per feature. |
| `rewiring_distance` | Maximum network search radius R for eligible replacement partners. |
| `alpha` | Selection intensity for circle similarity and harmonic selection; retained but not used by mean profile. |
| `rewiring_rule` | circle_similarity, mean_profile or harmonic. |
| `harmonic_update_every` | Refresh interval for the harmonic-centrality cache, in attempts. |
| `profile_update_every` | Refresh interval used by the mean-profile cache, in attempts. |
| `profile_target_mode` | Recorded mean-profile mode; match in this campaign. |
| `max_steps_budget` | Main observation horizon in elementary update attempts. |
| `simulation_seconds` | Recorded execution wall-clock time in seconds. |
| `steps` | Actual number of elementary attempts at termination or observation. |
| `sweeps` | steps / N. |
| `status` | absorbed if no discordant edge remains; otherwise max_steps. |
| `active_edges_final` | Number of edges whose endpoints share some but not all traits. |
| `discordant_edges_final` | Number of edges with nonidentical endpoint cultural vectors. |
| `zero_overlap_edges_final` | Number of edges whose endpoints share no traits. |
| `M` | Number of undirected network edges. |
| `avg_degree` | Arithmetic mean degree. |
| `std_degree` | Population standard deviation of degree (ddof=0). |
| `num_components` | Number of connected network components, including isolated agents. |
| `giant_component_size` | Number of agents in the largest network component. |
| `avg_path_length_giant` | Mean shortest-path length within the largest component. |
| `diameter_giant` | Diameter of the largest component. |
| `clustering` | Global transitivity 3T/W. |
| `assortativity_degree` | Degree assortativity of the undirected graph. |
| `num_cultures` | Number of distinct complete cultural vectors. |
| `culture_entropy` | Cultural entropy in nats as computed by the simulation; includes a 1e-12 logarithm offset. |
| `largest_culture_size` | Number of agents sharing the most frequent complete cultural vector. |
| `largest_culture_frac` | largest_culture_size / N. |
| `mean_edge_similarity` | Mean fraction of shared cultural features over edges; the implementation returns 1 when there are no edges. |
| `active_edge_fraction` | Active edges divided by M; 0 when M is 0. |
| `sample_group` | Classification of the whole selected triplet at the main horizon: absorbed, zero_only or active. |
| `triplet` | Identifier of the matched set containing one execution of each rule. |
| `horizon` | Requested observation time in elementary update attempts. |
| `actual_steps` | Actual simulation clock; can precede horizon after absorption. |
| `baseline_verified` | Whether the temporal execution reproduced its stored main-campaign baseline. |
| `source_batch` | initial_90 or additional_111; the two disjoint parts of the 201-trajectory sample. |
| `baseline_regime` | Individual execution classification at 5 million attempts: absorbed, zero_only or active. |
| `largest_domain_frac` | Largest connected cultural domain size divided by N. |
| `num_domains` | Number of connected cultural domains, including isolated agents. |
| `polarization` | 4 times variance of normalized Hamming distance over all unordered distinct agent pairs. |
| `mean_pair_distance` | Mean normalized Hamming distance across those pairs. |
| `entropy` | Entropy without the logarithm offset, in nats. |
| `effective_cultures` | Exponential of entropy. |
| `batch` | English source-batch label: initial_90 or additional_111. |
| `distance` | Normalized Hamming distance; number of differing features divided by F. |
| `pair_count` | Count of unordered distinct agent pairs at this distance. |
| `pair_fraction` | pair_count / 499500. |
| `agent_id` | Zero-based agent identifier within an execution. |
| `source` | First endpoint of an undirected edge, zero-based. |
| `target` | Second endpoint of an undirected edge, zero-based; greater than source. |
| `edge_count` | Number of exported undirected edges in a final configuration. |
| `source_checkpoint_sha256` | SHA-256 of the original local checkpoint from which this state was exported. |
| `metric` | Name of the measured quantity. |
| `initial` | Mean initial value across the full main campaign. |
| `final` | Mean final value across the full main campaign. |
| `change_pct` | 100 * (final / initial - 1). |
| `changed` | Number of temporal trajectories changing between 5 and 20 million attempts, using the original analysis tolerance. |
| `max_abs` | Largest absolute temporal change. |
| `mean_abs` | Mean absolute temporal change over all 201 trajectories. |
| `absorbed` | Number of trajectories without discordant edges at this horizon. |
| `active` | Number of trajectories with at least one active edge at this horizon. |
| `zero_only` | Number of trajectories with discordance but no active edges at this horizon. |
| `parameter` | Varied input parameter in a marginal curve. |
| `parameter_value` | Value of that input parameter. |
| `mean` | Mean plotted value after averaging the relevant parameter-cell means. |
| `mc_se` | Conditional Monte Carlo standard error; see the data guide. |
| `lower_95` | mean - 1.96 * mc_se. |
| `upper_95` | mean + 1.96 * mc_se. |
| `parameter_cells` | Number B of averaged parameter cells. |
| `runs_per_cell` | Number of executions per parameter cell, 10. |
| `trait_1` | Categorical value of feature 1; empty if this feature exceeds F for this execution. |
| `trait_2` | Categorical value of feature 2; empty if this feature exceeds F for this execution. |
| `trait_3` | Categorical value of feature 3; empty if this feature exceeds F for this execution. |
| `trait_4` | Categorical value of feature 4; empty if this feature exceeds F for this execution. |
| `trait_5` | Categorical value of feature 5; empty if this feature exceeds F for this execution. |
| `trait_6` | Categorical value of feature 6; empty if this feature exceeds F for this execution. |
| `trait_7` | Categorical value of feature 7; empty if this feature exceeds F for this execution. |
| `trait_8` | Categorical value of feature 8; empty if this feature exceeds F for this execution. |

## Columns by file

### derived/cultural_distance_metrics.csv

`rewiring_rule`, `sample_group`, `triplet`, `m_attach`, `num_features`, `num_traits`, `rewiring_distance`, `alpha`, `status`, `actual_steps`, `combo_id`, `run_id`, `horizon`, `baseline_regime`, `polarization`, `mean_pair_distance`, `entropy`, `effective_cultures`, `num_cultures`, `largest_culture_frac`, `batch`

### derived/entropy_by_alpha.csv

`rewiring_rule`, `num_features`, `num_traits`, `alpha`, `mean`, `mc_se`, `lower_95`, `upper_95`, `parameter_cells`, `runs_per_cell`

### derived/final_state_metrics.csv

`combo_id`, `run_id`, `seed`, `rewiring_rule`, `sample_group`, `triplet`, `N`, `m_attach`, `num_features`, `num_traits`, `rewiring_distance`, `alpha`, `horizon`, `actual_steps`, `baseline_verified`, `status`, `active_edges_final`, `discordant_edges_final`, `zero_overlap_edges_final`, `M`, `avg_degree`, `std_degree`, `num_components`, `giant_component_size`, `avg_path_length_giant`, `diameter_giant`, `clustering`, `assortativity_degree`, `num_cultures`, `culture_entropy`, `largest_culture_size`, `largest_culture_frac`, `mean_edge_similarity`, `active_edge_fraction`, `largest_domain_frac`, `num_domains`, `polarization`, `baseline_regime`

### derived/overall_metrics.csv

`metric`, `initial`, `final`, `change_pct`

### derived/pair_distance_distributions.csv

`combo_id`, `run_id`, `distance`, `pair_count`, `pair_fraction`

### derived/parameter_effects.csv

`rewiring_rule`, `parameter`, `parameter_value`, `metric`, `mean`, `mc_se`, `lower_95`, `upper_95`, `parameter_cells`, `runs_per_cell`

### derived/strategy_means.csv

`rewiring_rule`, `final_N`, `final_M`, `final_avg_degree`, `final_std_degree`, `final_num_components`, `final_giant_component_size`, `final_clustering`, `final_avg_path_length_giant`, `final_diameter_giant`, `final_num_cultures`, `final_culture_entropy`, `final_largest_culture_frac`, `final_mean_edge_similarity`, `final_active_edge_fraction`

### derived/temporal_changes.csv

`metric`, `changed`, `max_abs`, `mean_abs`

### derived/temporal_status.csv

`horizon`, `absorbed`, `active`, `zero_only`

### final_states/index.csv

`combo_id`, `run_id`, `N`, `num_features`, `num_traits`, `horizon`, `actual_steps`, `status`, `edge_count`, `source_checkpoint_sha256`

### temporal_extension/observations.csv

`combo_id`, `run_id`, `seed`, `rewiring_rule`, `sample_group`, `triplet`, `N`, `m_attach`, `num_features`, `num_traits`, `rewiring_distance`, `alpha`, `horizon`, `actual_steps`, `baseline_verified`, `status`, `active_edges_final`, `discordant_edges_final`, `zero_overlap_edges_final`, `M`, `avg_degree`, `std_degree`, `num_components`, `giant_component_size`, `avg_path_length_giant`, `diameter_giant`, `clustering`, `assortativity_degree`, `num_cultures`, `culture_entropy`, `largest_culture_size`, `largest_culture_frac`, `mean_edge_similarity`, `active_edge_fraction`

### temporal_extension/selection.csv

`combo_id`, `run_id`, `rewiring_rule`, `sample_group`, `triplet`, `N`, `m_attach`, `num_features`, `num_traits`, `rewiring_distance`, `alpha`, `seed`, `source_batch`, `baseline_regime`

### final_states/agents.csv.gz

`combo_id`, `run_id`, `agent_id`, `trait_1`, `trait_2`, `trait_3`, `trait_4`, `trait_5`, `trait_6`, `trait_7`, `trait_8`

### final_states/edges.csv.gz

`combo_id`, `run_id`, `source`, `target`

### main_campaign/results.csv.gz

`model_version`, `combo_id`, `run_id`, `master_seed`, `combo_seed`, `combo_seed_for_runs`, `seed`, `N`, `m_attach`, `num_features`, `num_traits`, `rewiring_distance`, `alpha`, `rewiring_rule`, `harmonic_update_every`, `profile_update_every`, `profile_target_mode`, `max_steps_budget`, `simulation_seconds`, `steps`, `sweeps`, `status`, `active_edges_final`, `discordant_edges_final`, `zero_overlap_edges_final`, `init_N`, `init_M`, `init_avg_degree`, `init_std_degree`, `init_num_components`, `init_giant_component_size`, `init_avg_path_length_giant`, `init_diameter_giant`, `init_clustering`, `init_assortativity_degree`, `init_num_cultures`, `init_culture_entropy`, `init_largest_culture_size`, `init_largest_culture_frac`, `init_mean_edge_similarity`, `init_active_edge_fraction`, `final_N`, `final_M`, `final_avg_degree`, `final_std_degree`, `final_num_components`, `final_giant_component_size`, `final_avg_path_length_giant`, `final_diameter_giant`, `final_clustering`, `final_assortativity_degree`, `final_num_cultures`, `final_culture_entropy`, `final_largest_culture_size`, `final_largest_culture_frac`, `final_mean_edge_similarity`, `final_active_edge_fraction`
