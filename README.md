# IVF Prediction with Logistic Regression–ABC Hybrid Model

This repository contains the dataset and code used in the study:  
**“Predicting IVF Outcomes Using a Logistic Regression–ABC Hybrid Model: A Proof-of-Concept Study on Supplement Associations.”**

## 📂 Repository Structure
- `Gebelik_calisma_revision.ipynb` → Jupyter Notebook with analysis
- `IVF_english.xlsx` → Dataset used in the manuscript
- `requirements.txt` → Dependencies for reproducibility
- `README.md` → Documentation

## ⚙️ Requirements
Install dependencies with:
```bash
pip install -r requirements.txt

#Project: LR–ABC Hybrid ML for IVF Outcome Modeling (with LIME)

A clean, reproducible codebase to accompany the manuscript on exploring associations between supplement use and IVF outcomes using a Logistic Regression–Artificial Bee Colony (LR–ABC) hybrid pipeline with SMOTE, Stratified K‑Fold, and LIME explanations.

2) Quick Start

# Option A: conda
conda env create -f environment.yml
conda activate ivf-lrabc


# Option B: pip
python -m venv .venv && source .venv/bin/activate # (Windows: .venv\Scripts\activate)
pip install -r requirements.txt


# Reproduce paper results (one command)
make all # or run the commands listed in Section 6

3) Data

4) Environment

ame: ivf-lrabc
channels: [conda-forge, defaults]
dependencies:
- python=3.10
- pandas
- numpy
- scikit-learn
- imbalanced-learn
- lime
- matplotlib
- seaborn
- joblib
- pip

5) Reproducibility & Seeds

We fix seeds for numpy, Python, and scikit‑learn. Stratified 5‑fold indices are exported to data/processed/folds/ and re‑used for all models. SMOTE is applied within each training fold only to avoid leakage.

# src/utils/seeds.py
import os, random, numpy as np
SEED = 42
os.environ["PYTHONHASHSEED"] = str(SEED)
random.seed(SEED)
np.random.seed(SEED)

6) What to Expect (sanity ranges)

To avoid overclaiming, we report relative improvements (hybrid > baseline) instead of a single high accuracy. Typical ranges observed in the manuscript:

Accuracy: ~0.78–0.90 across models (hybrids generally higher than baselines)

F1‑macro: ~0.75–0.89

Recall (sensitivity): hybrids > baselines

7) LIME Explanations

- Local explanations are generated for a stratified sample of positive/negative predictions.
- We save: per‑instance bar charts of feature contributions + the raw JSON explanation.
- Report in the paper: examples where Omega‑3 and Folic acid appear as influential, framed as hypothesis‑generating, not clinical evidence.

8) Coding Style & Comments

Use PEP8 and Google‑style docstrings.
