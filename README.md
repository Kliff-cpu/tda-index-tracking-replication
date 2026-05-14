# TDA-Based Sparse Index Tracking  
### Replication and Beta–Volatility Extension

## Overview

This project replicates and extends the methodology proposed by Goel, Pasricha and Kanniainen (2025) in *Risk Reduced Sparse Index Tracking Portfolio: A Topological Data Analysis Approach*.

The objective is to construct sparse portfolios that track the S&P 500 using data-driven regularisation techniques within a weighted Elastic-Net framework.

---

## Replication Framework

The original framework uses:

- Topological Data Analysis (TDA)
- Persistent homology
- Persistence landscapes
- \(L^1\) persistence landscape norms as adaptive penalties
- Weighted Elastic-Net optimisation

The implementation follows the original rolling-window setup:

- 504-day in-sample window
- 21-day out-of-sample window
- Takens embedding: \(d = 3,\ \tau = 1\)
- 42-day overlapping subseries

---

## Proposed Extension

This study introduces economically interpretable penalties based on:

- CAPM beta, representing systematic index exposure
- Asset volatility, representing asset-specific risk

These measures are incorporated into the same weighted Elastic-Net optimisation framework used in the original TDA model.

---

## Research Question

Can CAPM beta and volatility serve as economically interpretable alternatives to TDA-based penalties while achieving comparable or improved tracking accuracy, risk control, portfolio sparsity and portfolio stability?

---

## Models Implemented

| Model Type | Models |
|---|---|
| TDA Models | TE, TDA-Lasso, TDA-EN11, TDA-EN12 |
| Economic Extension Models | Vol-EN11, Beta-EN11, BetaVol, BetaVol-Long |

---

## Results Summary

The TDA-based models generally produce lower tracking error, stronger benchmark correlation, lower turnover and stable sparse portfolios.

The Beta–Volatility extension improves interpretability and produces stronger return exposure, although this comes with higher downside risk and larger tracking deviation.

---

## Repository Structure

```text
tda-index-tracking-replication/
│
├── Portfolio Final.ipynb
├── README.md
└── requirements.txt
```

---

## Reproducing the Results

### 1. Clone the repository

```bash
git clone https://github.com/Kliff-cpu/tda-index-tracking-replication.git
cd tda-index-tracking-replication
```

### 2. Install the required libraries

```bash
pip install -r requirements.txt
```

### 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

### 4. Open and run the notebook

Open:

```text
Portfolio Final.ipynb
```

Then run all cells from top to bottom.

---

## Outputs Reproduced

The notebook reproduces:

- Tables 1–14
- Growth-of-$1 plots
- Penalty correlation analysis
- Kupiec VaR backtesting
- Epsilon sensitivity analysis

---

## Main Libraries

- numpy
- pandas
- matplotlib
- cvxpy
- ripser
- persim
- gudhi
- yfinance
- scipy

---

## Authors

- G Addai (225180738)
- G.K Pule (222047683)
- O.C Seitsang (221011692)
- I.M Chirambwe (221005439)
