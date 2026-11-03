# Files supporting the manuscript results

| Manuscript item | Data |
| --- | --- |
| Parameter grid and simulation protocol | `metadata/main_campaign_manifest.json`; input columns in `main_campaign/results.csv.gz` |
| Figure 1: mean structural and cultural outcomes | `derived/strategy_means.csv`; full execution data in `main_campaign/results.csv.gz` |
| Figure 2: responses to initial connectivity, search radius and selection intensity | `derived/parameter_effects.csv`; full execution data in `main_campaign/results.csv.gz` |
| Figure 3: entropy versus alpha, separated by F and q | `derived/entropy_by_alpha.csv`; full execution data in `main_campaign/results.csv.gz` |
| Table of states at 5, 10 and 20 million attempts | `derived/temporal_status.csv`; all observations in `temporal_extension/observations.csv` |
| Changes between 5 and 20 million attempts | `derived/temporal_changes.csv`; all observations in `temporal_extension/observations.csv` |
| Figure 4: largest connected cultural domain, largest culture and largest component | `derived/final_state_metrics.csv`; configurations in `final_states/` |
| Figure 5: entropy and operational polarization | `derived/final_state_metrics.csv`; `derived/cultural_distance_metrics.csv`; `derived/pair_distance_distributions.csv`; configurations in `final_states/` |
| Overall initial-to-final changes | `derived/overall_metrics.csv`; full execution data in `main_campaign/results.csv.gz` |
| Selected execution identifiers and triplets | `temporal_extension/selection.csv`; `metadata/selection_design.json` |

All 201 trajectories are included in the temporal and final-state data. The repository contains no 200-trajectory subset. The temporal sample remains exploratory and cannot estimate the frequency of its outcomes in the full campaign.
