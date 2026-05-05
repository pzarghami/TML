# TML Assignment 1 — Membership Inference Attack

This repository contains our solution for the Membership Inference Attack task.

## Repository structure

- `assignment1/MIA_attack.ipynb` — the notebook that produces our best leaderboard submission
- `assignment1/tml26_task1/` — submodule pointing to the official task data and model

## How to reproduce the result

We ran the notebook on a Kaggle environment with a single NVIDIA T4 GPU.

### 1. Clone the repository with submodules

```bash
git clone --recurse-submodules https://github.com/pzarghami/TML.git
cd TML/assignment1/tml26_task1/
```

This pulls the `tml26_task1` submodule which contains `pub.pt`, `priv.pt`, and `model.pt`.

### 2. Run the notebook

Open `assignment1/MIA_attack.ipynb` in Kaggle, Colab or other similars, run all cells in order, and it will do the clonning and resyncing process itself.

The first cell clones the repo and changes into the task directory. The second cell loads the dataset and target model. The third cell trains 8 shadow models, computes RMIA scores across a grid of `gamma` values and reference-pool choices, evaluates all variants on the public set, and writes the best one to `submission.csv`.

### 3. Submit `submission.csv`

The file is written to `assignment1/tml26_task1/submission.csv`.

## Configuration used for the best result

The shadow-model and RMIA hyperparameters are set at the top of the third cell:

| Parameter      | Value |
|----------------|-------|
| `N_SHADOW`     | 8     |
| `EPOCHS`       | 65    |
| `LR`           | 0.1   |
| `WD`           | 1e-3  |
| `LS`           | 0.03  |
| `BATCH`        | 128   |
| `SUBSET`       | 0.5   |
| `SEED`         | 2032  |


The notebook automatically picks the variant with the highest TPR@5%FPR on the public set and saves it as `submission.csv`.

## Runtime

With a single T4 GPU, training the 8 shadow models takes about 1 hour.