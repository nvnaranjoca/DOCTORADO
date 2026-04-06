# PINN-based spatiotemporal estimation of chlorophyll-a in the Pacific coast of Nariño

This repository contains the computational materials associated with the doctoral thesis *Modelo de pronóstico basado en teledetección y propiedades ópticas para la gestión del riesgo por floraciones algales nocivas (FAN) en la costa pacífica nariñense*.

## Scientific scope

The repository supports a Physics-Informed Neural Network (PINN) designed to estimate chlorophyll-a (Chl-a) as a continuous bio-optical variable in space and time using 8-day MODIS-derived products for the Pacific coast of Nariño, Colombia (2002–2024).

Chl-a is treated as a bio-optical proxy for surface phytoplankton biomass. Therefore, the outputs should be interpreted as support for bio-optical surveillance and environmental follow-up, not as direct detection of harmful algal blooms (HABs), species identification, or toxicity assessment.

## Main repository structure

- `01_scripts/`: training, inference, and model loading scripts.
- `02_config/`: hyperparameter search outputs, metadata, variable statistics, and effective parameters.
- `03_model/`: trained weights.
- `04_outputs_global/`: global metrics, training curves, parity plots, observed/predicted/residual maps.
- `05_validation_by_scene/`: additional validation outputs for specific dates/scenes.
- `06_data/`: consolidated tabular input data or a sample subset.
- `07_docs/`: documentation files for reproducibility.

## Core files expected in this repository

- `chlor_a_all_data.ipynb`: main notebook for PINN training and evaluation.
- `lectura_modelos.py`: script for reading trained models and associated metadata.
- `model_chlor_a_metadata.json`: metadata required for inference and reproducibility.
- `model_chlor_a_weights.npz`: trained model weights.
- `optuna_best_chlor_a.json`: best hyperparameter configuration.
- `optuna_bestvals_chlor_a.csv`: tabular summary of selected hyperparameters.
- `parametros_fisicos`: final effective parameters of the differential formulation.
- `variable_stats.json`: variable statistics used in preprocessing.
- `predictions_val_chlor_a`: tabular predictions on the retained validation block.
- `final_metrics_chlor_a`: global regression metrics.
- `unidas_fecha.csv`: consolidated spatiotemporal dataset.

## Minimal reproducibility workflow

1. Install the computational environment with `requirements.txt` or `environment.yml`.
2. Place the consolidated data file in `06_data/`.
3. Run the training or inference workflow from `01_scripts/`.
4. Use the metadata files in `02_config/` and trained weights in `03_model/`.
5. Compare the generated outputs against the reference files in `04_outputs_global/` and `05_validation_by_scene/`.

## Notes for interpretation

- Temporal resolution corresponds to 8-day composites.
- The model target is `chlor_a`.
- Auxiliary variables used in the forcing term include `nflh`, `Kd_490`, `par`, `poc`, and `sst`.
- The reaction–diffusion-type equation acts as a structural regularizer, not as an exhaustive mechanistic reconstruction of the oceanographic system.

## Citation note

If this repository is cited in academic products, it should be cited together with the corresponding doctoral thesis.
