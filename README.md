# Drug Toxicity Prediction

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/python-3.9%2B-success.svg)](https://www.python.org/)

## Overview

This repository contains a comprehensive set of tools and Jupyter notebooks for **predicting drug toxicity** using a variety of public bioactivity datasets. The project demonstrates how to preprocess data, train multiple machine learning models, evaluate their performance, and visualise the results.

## Table of Contents

- [Datasets](#datasets)
- [Installation](#installation)
- [Usage](#usage)
- [Notebooks](#notebooks)
- [Results & Visualisations](#results--visualisations)
- [Contributing](#contributing)
- [License](#license)

## Datasets

The project works with several well‑known toxicity‑related datasets:

| Dataset | Description | Source |
|---------|-------------|--------|
| **BBBP** | Blood‑Brain Barrier Penetration | <https://pubchem.ncbi.nlm.nih.gov/> |
| **ClinTox** | Clinical trial outcomes (toxic / non‑toxic) | <https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5943005/> |
| **SIDER** | Side Effect Resource – drug–adverse‑event relationships | <https://sideeffects.embl.de/> |
| **Tox21** | High‑throughput screening data for 12 toxicity assays | <https://tripod.nih.gov/tox21/> |
| **NPASS** | Natural product activity & species source | <https://bidd.group/NPASS/> |

All datasets are automatically downloaded and pre‑processed by the helper scripts located in `data/`.

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your‑username/drug-toxicity-prediction.git
   cd drug-toxicity-prediction
   ```

2. **Create a Python virtual environment** (recommended)
   ```bash
   python -m venv .venv
   .venv\Scripts\activate   # Windows
   # source .venv/bin/activate   # macOS/Linux
   ```

3. **Install required packages**
   ```bash
   pip install -r requirements.txt
   ```

4. **Install additional system dependencies** (optional but recommended for faster training)
   - `rdkit` – for chemical fingerprint generation (see the `README_RDKit.md` for installation instructions on Windows).

## Usage

The core workflow is demonstrated in the Jupyter notebooks under `notebooks/`.

```bash
jupyter notebook
```

Open any notebook – for example, `notebooks/001_data_preprocessing.ipynb` – and run the cells sequentially. The notebooks are ordered to guide you through:

1. **Data loading & cleaning**
2. **Feature engineering** (Morgan fingerprints, physicochemical descriptors)
3. **Model training** (Random Forest, XGBoost, Deep Neural Networks)
4. **Evaluation** (ROC‑AUC, PR‑AUC, confusion matrices)
5. **Visualisation** of results and feature importance

All notebooks are self‑contained and include detailed markdown explanations.

## Notebooks

| Notebook | Purpose |
|----------|---------|
| `001_data_preprocessing.ipynb` | Load raw CSVs, handle missing values, split into train/validation/test. |
| `002_feature_engineering.ipynb` | Generate molecular fingerprints and compute descriptor matrices. |
| `003_model_training.ipynb` | Train multiple classifiers and log hyper‑parameters using `mlflow`. |
| `004_evaluation.ipynb` | Compute performance metrics, generate ROC/PR curves. |
| `005_visualisation.ipynb` | Interactive plots (Plotly) for model comparison and feature importance. |

## Results & Visualisations

The `results/` folder contains pre‑generated figures and CSV files summarising model performance across all datasets. Key highlights:

- **Best average ROC‑AUC** across the five datasets: **0.89** (XGBoost with depth 6).
- **Feature importance** shows that topological fingerprints dominate predictive power, with selected physicochemical descriptors providing complementary information.

You can regenerate these figures by running `004_evaluation.ipynb` followed by `005_visualisation.ipynb`.

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new feature branch (`git checkout -b feature/your‑feature`).
3. Ensure code style compliance (`flake8` and `black`).
4. Add or update tests in the `tests/` directory.
5. Submit a pull request with a clear description of your changes.

## License

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.

---

*Feel free to open an issue if you encounter any bugs or have suggestions for improvements.*
