# ML4HEP-HGCAL

A tutorial-oriented collection of notebooks for HGCAL regression studies. The notebooks walk through the full workflow: reading the raw HDF5 event sample, flattening it into tabular features, training baseline regressors, and experimenting with graph neural networks and dense neural networks. This will setup the baseline for your own experiments with the HGCAL dataset, demonstrating what a naive implementation of each of these model architectures can achieve. The goal of the exercise would be to improve upon the baseline models.

## Notebook guide

| Notebook | Purpose |
| --- | --- |
| `01_hgcal_flatten_to_csv.ipynb` | Convert the raw HDF5 event sample into a flat CSV with one row per event. |
| `02_hgcal_event_summary_and_baseline.ipynb` | Inspect the raw event arrays, build a tabular summary, and train a gradient-boosting baseline. |
| `03_hgcal_gradient_boosting_regression.ipynb` | Train and evaluate a gradient-boosting regressor on the layer-summed features. |
| `04_hgcal_dense_nn_regression.ipynb` | Train a dense neural network on the tabular features and evaluate it on held-out and additional data. |
| `05_hgcal_gnn_experiments.ipynb` | Compare several graph-construction strategies for a GCN regressor. |

## Suggested reading order

1. Start with `01_hgcal_flatten_to_csv.ipynb` to understand how the raw HDF5 file is flattened.
2. Move to `02_hgcal_event_summary_and_baseline.ipynb` or `03_hgcal_gradient_boosting_regression.ipynb` to see baseline tabular models.
3. Open `04_hgcal_dense_nn_regression.ipynb` to compare a small dense network against the baseline.
4. Finish with `05_hgcal_gnn_experiments.ipynb` for the graph-based experiments.
5. Now, that the baseline experiments are complete, try modifying the models, hyper-parameters (maybe Hyper-parameter tuning), and other new architectures you learnt in the school to see if you can improve the performance of the models. You can also try to implement your own architecture and compare it with the existing ones.

## Data

The notebooks expect HGCAL samples derived from the Zenodo release linked below. The current version of the notebooks uses relative file names such as:

- `hgcal_electron_data_0001.h5`
- `hgcal_electron_data_50000.csv`
- `hgcal_electron_data_10000.csv`
- `BDT_energy_50K.csv`
- `true_test_DNN_15K.csv`

Place the required files in the repository root, or update the `Path(...)` variables at the top of the notebooks if you keep the data elsewhere.

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

- The notebooks use markdown sections to separate the major steps.
- File paths are relative so the examples are easier to run on a new machine.
- Some notebooks intentionally keep multiple model variants side by side so you can compare architecture choices quickly.

## Reference and further reading

### Data and project background

- HGCAL electron sample on Zenodo: https://zenodo.org/records/7864471
- HGCAL project documentation and motivation: use the links in the dataset page and the notebook comments as the starting point for the tutorial flow.

### Package installation
Something like the following should work in a conda environment:

```bash
micromamba create -n myenv \
    -c conda-forge \
    -c pytorch \
    python=3.12 \
    numpy pandas matplotlib seaborn scikit-learn \
    h5py awkward statsmodels tensorflow \
    pytorch pytorch-cuda=12.4 \
    torch-geometric
```
Make sure to check the [PyTorch Geometric installation guide](https://pytorch-geometric.readthedocs.io/en/latest/notes/installation.html) for the correct version of `torch-scatter`, `torch-sparse`, and `torch-geometric` for your PyTorch version, also and your CUDA version if you are using a GPU and any more packages you may need for your experiments (later).

### Notebook workflow tips

- Use the notebook titles and section headers as a quick map of each workflow.
- Run the notebooks top-to-bottom the first time to build the intermediate files.
- Revisit the markdown sections when you want to understand the purpose of a code block before editing it.

## Acknowledgements

This repository is a collaborative HGCAL tutorial project. Original credits from the repository are preserved below.

> Input files source: https://zenodo.org/records/7864471
>
> Work done collaboratively by Avik Das, Chetan Agrawal, Divyajyoti Pandey, Kuldeep Kumar Pal, Kumar Tanay, Manas Ranjan Sahoo, Rahul Kumar Agrawal, Rohit Kumar Singh, Samarendra Nayak, Sandeep Pradhan, Sneh Shuchi, Subhalaxmi Rout, Vatsal Sinha in the guidance of Dr. Rajdeep Mohan Chatterjee.
