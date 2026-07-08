# ML4HEP-HGCAL

A tutorial-oriented collection of notebooks for HGCAL regression studies. The notebooks walk through the full workflow: reading the raw HDF5 event sample, flattening it into tabular features, training baseline regressors, and experimenting with graph neural networks and dense neural networks.

## What is in this repository?

| Notebook | Purpose |
| --- | --- |
| `hgcal-feature-csv.ipynb` | Convert the raw HDF5 event sample into a flat CSV with one row per event. |
| `HGCAL-PROJECT-MLIOPB(1).ipynb` | Inspect the raw event arrays, build a tabular summary, and train a gradient-boosting baseline. |
| `HGCAL_regression_XGBoost.ipynb` | Train and evaluate a gradient-boosting regressor on the layer-summed features. |
| `DNN_50K_train_full_data_test.ipynb` | Train a dense neural network on the tabular features and evaluate it on held-out and additional data. |
| `gnn_final(1).ipynb` | Compare several graph-construction strategies for a GCN regressor. |

## Data

The notebooks expect HGCAL samples derived from the Zenodo release linked below. The current version of the notebooks uses relative file names such as:

- `hgcal_electron_data_0001.h5`
- `hgcal_electron_data_50000.csv`
- `hgcal_electron_data_10000.csv`
- `BDT_energy_50K.csv`
- `true_test_DNN_15K.csv`

Place the required files in the repository root, or update the `Path(...)` variables at the top of the notebooks if you keep the data elsewhere.

Input files source: https://zenodo.org/records/7864471

## Suggested reading order

1. Start with `hgcal-feature-csv.ipynb` to understand how the raw HDF5 file is flattened.
2. Move to `HGCAL-PROJECT-MLIOPB(1).ipynb` or `HGCAL_regression_XGBoost.ipynb` to see baseline tabular models.
3. Open `DNN_50K_train_full_data_test.ipynb` to compare a small dense network against the baseline.
4. Finish with `gnn_final(1).ipynb` for the graph-based experiments.

## Environment

The notebooks rely on the usual scientific Python stack plus the ML libraries used in each experiment. A typical environment includes:

- numpy
- pandas
- matplotlib
- seaborn
- scikit-learn
- h5py
- awkward
- statsmodels
- tensorflow
- torch
- torch-geometric

## Notes for tutorial readers

- The notebooks now use markdown sections to separate the major steps.
- File paths are relative so the examples are easier to run on a new machine.
- Some notebooks intentionally keep multiple model variants side by side so you can compare architecture choices quickly.

## Acknowledgements

This repository is a collaborative HGCAL tutorial project. Original credits from the repository are preserved below.

