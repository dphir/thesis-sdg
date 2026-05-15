# From Data Silos to Integrated Assurance: A Synthetic Data Approach to the Three Lines Model for Governance, Risk, and Compliance

Master's Thesis — University of Tartu, 2026
Author: Defir Ilmi Faridha
Supervisors: Mahmoud Shoush, PhD & Eduardo Ribas Brito, MSc

## Overview

This repository contains the full simulation pipeline for the thesis, which investigates whether synthetic data can resolve the governance–privacy paradox in GRC environments by enabling privacy-preserving, collaborative data access across the Three Lines Model (3LM).

## Repository Structure

```
thesis-sdg/
├── .gitignore
├── README.md
├── requirements.txt
├── notebooks/
│   ├── 01_as_is_simulation.ipynb
│   ├── 02_synthetic_data_generation.ipynb
│   └── 03_to_be_simulation.ipynb
└── outputs/
    └── figures/
```

## Environment

| Component | Details |
|-----------|---------|
| CPU | AMD Ryzen 5 3550H (2.10 GHz) |
| GPU | NVIDIA GeForce GTX 1050 (CUDA) |
| RAM | 16 GB |
| Python | 3.12.3 |
| Environment | Anaconda |
| Notebook | Jupyter Notebook |

Create a conda environment and install dependencies:

```bash
conda create -n thesis-sdg python=3.12.3
conda activate thesis-sdg
pip install -r requirements.txt
```

> **Note:** A dedicated environment is strongly recommended due to potential dependency conflicts between SynthCity, SynthEval, and other packages. Conflict resolution may vary depending on your system environment.

## Reproducing the Experiments

All experiments use a fixed random seed of 42 throughout sampling, model training, and generation.

1. Run `01_as_is_simulation.ipynb` — segmented (3LoD) governance simulation on real baseline data with IT-mediated access. Includes stratified sampling to produce a representative baseline of 100 customers due to hardware constraints. If sufficient compute is available, stratified sampling can be skipped to run on the full dataset.
2. Run `02_synthetic_data_generation.ipynb` — generates synthetic customer and transaction data using TabDDPM via SynthCity from the baseline produced in step 1, with built-in fidelity, utility, and privacy evaluation. Independent validation is performed using SynthEval.
3. Run `03_to_be_simulation.ipynb` — collaborative (3LM) governance simulation on synthetic data with direct shared access.

Simulation outputs and figures from SynthCity and SynthEval are available in `outputs/figures/` for reference without re-running the full pipeline.

## Data Availability

The original dataset cannot be shared due to privacy constraints. The simulation logic — including threshold parameters, baseline calibration, and escalation rules — was designed based on the characteristics of the available dataset. Researchers applying this pipeline to different datasets or operational contexts should expect to adjust these parameters accordingly.

## Citation

If you use this code, please cite:

Faridha, D. I. (2026). From Data Silos to Integrated Assurance: A Synthetic Data Approach to the Three Lines Model for Governance, Risk, and Compliance. Master's Thesis, University of Tartu.

Full thesis available at: [https://thesis.cs.ut.ee/f12151b2-c92a-41f4-9e55-d621cb954c14]
