# Axelrod Culture 2

Data supporting **Selective rewiring, clustering and cultural diversity in an adaptive Axelrod model**, by Yuri Perez and Pedro Henrique Triguis Schimit.

This repository contains the simulation results and final configurations used in the manuscript. It contains data and documentation only. Simulation and analysis source code are not included in this deposit.

## Contents

| Folder | Contents |
| --- | --- |
| `main_campaign/` | Original consolidated results of 121,500 executions at up to 5 million update attempts, compressed without changing the CSV |
| `temporal_extension/` | 603 observations from 201 selected trajectories at 5, 10 and 20 million attempts, plus the selection table |
| `final_states/` | Agent cultural traits and network edge lists for all 201 final states, with an index identifying each state |
| `derived/` | Numerical results underlying the manuscript figures and temporal comparisons |
| `metadata/` | Simulation manifests, selection design, provenance and validation results |
| `docs/` | Data dictionary, reading instructions and mapping between files and manuscript results |

Start with [the data guide](docs/data_guide.md), [the data dictionary](docs/data_dictionary.md) and [the manuscript mapping](docs/manuscript_mapping.md). [The file inventory](metadata/file_inventory.csv) gives row counts, sizes and SHA-256 hashes.

## Study design

The main campaign has 12,150 parameter cells including the partner selection rule, with 10 executions per cell and 1,000 agents per execution. The three rules are circle similarity, mean profile and harmonic selection. The main observation horizon is 5 million elementary update attempts; executions certified absorbed can terminate earlier.

The temporal extension contains 67 matched parameter triplets, with one execution per rule and the same repetition index in each triplet, giving 201 trajectories. These executions use independent initial networks and stochastic updates across rules. The sample covers 22 triplets classified as absorbed, 22 with zero-overlap discordance but no active edges, and 23 with at least one execution with active edges at the main horizon. The triplet classification and an individual execution's classification are separate fields.

The sample was selected to cover dynamical cases and parameter values. It is not a random representative sample of the full campaign, and its proportions must not be interpreted as population frequencies over the parameter grid.

## Coverage and limitations

The final state files contain the network and cultural vectors at 20 million attempts, or the earlier absorbing configuration carried forward to that horizon. They are snapshots, not complete trajectories of every update. Full intermediate networks at 5 and 10 million attempts are not included because those configurations were not retained in the final checkpoints. Scalar measurements at all three horizons are provided.

The main campaign provides initial and final summary measurements, parameters and seeds. Full networks and cultural vectors for all 121,500 main executions are not available in this repository. This deposit preserves the data supporting the manuscript; it does not claim that the full simulation campaign can be regenerated without its source code.

## Formats

Tables use UTF-8 CSV with a decimal point. `.csv.gz` files are standard gzip-compressed CSV files and can be decompressed by ordinary archive tools. Preserve seed columns as text: some seeds are larger than the exact integer range of spreadsheet and floating-point formats. No Python pickle files are needed to read this deposit.

## Citation

Perez, Yuri, and Schimit, Pedro Henrique Triguis (2026). *Axelrod Culture 2: data for selective rewiring, clustering and cultural diversity in an adaptive Axelrod model*. Version 1.0.0. https://github.com/labdinpop/axelrod-culture-2

The manuscript was being prepared for submission when this dataset was released. This repository does not assign a DOI or imply that the paper has been accepted or published. See `CITATION.cff` for citation metadata and cite a specific commit or tag when identifying a fixed version.
