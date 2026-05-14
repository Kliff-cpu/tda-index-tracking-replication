# TDA-Based Sparse Index Tracking (Replication & Extension)

## Overview

This project replicates and extends the methodology proposed in:

> Goel, A., Pasricha, P. and Kanniainen, J. (2025).  
> *Risk Reduced Sparse Index Tracking Portfolio: A Topological Data Analysis Approach.*

The objective is to construct sparse portfolios that replicate the S&P 500 using data-driven regularisation techniques within a weighted Elastic-Net framework.

---

## Replication Framework

The original framework uses:

- Topological Data Analysis (TDA)
- Persistent homology
- Persistence landscapes
- L1 persistence landscape norms as adaptive penalties
- Weighted Elastic-Net optimisation

The implementation follows the original rolling-window setup:

- 504-day in-sample window
- 21-day out-of-sample window
- Takens embedding: \( d = 3, \tau = 1 \)
- 42-day overlapping subseries

---

## Proposed Extension

Instead of TDA-based penalties, this study introduces economically interpretable penalties based on:

- CAPM beta (systematic risk)
- Asset volatility (idiosyncratic risk)

These measures are incorporated into the same weighted Elastic-Net optimisation framework used in the original paper.

---

## Research Question

Can CAPM beta and volatility serve as economically interpretable alternative penalty measures to TDA-based penalties while achieving comparable or improved:
- Tracking accuracy
- Risk control
- Portfolio sparsity
- Portfolio stability

---

## Models Implemented

### TDA Models
- TE
- TDA-Lasso
- TDA-EN11
- TDA-EN12

### Economic Extension Models
- Vol-EN11
- Beta-EN11
- BetaVol
- BetaVol-Long

---

## Results Summary

The TDA-based models generally:

- Produce lower tracking error
- Achieve stronger benchmark correlation
- Reduce turnover
- Maintain stable sparse portfolios

The Beta–Volatility extension improves interpretability and produces stronger return exposure, although with higher downside risk and tracking deviation.

---

## Repository Structure

```text
tda-index-tracking-replication/
│
├── data/
├── notebooks/
│   └── Portfolio Final.ipynb
│
├── results/
│   ├── tables/
│   └── figures/
│
├── requirements.txt
├── README.md
└── LICENSE

## Reproducing the Results
1. Clone the repository
git clone https://github.com/Kliff-cpu/tda-index-tracking-replication.git
cd tda-index-tracking-replication
2. Install required libraries
pip install -r requirements.txt
3. Run the notebook:
Portfolio Final.ipynb

## The notebook reproduces:

Tables 1–14
Growth-of-$1 plots
Penalty correlation analysis
Kupiec VaR backtesting
Sensitivity analysis

#### Main Libraries
numpy
pandas
matplotlib
cvxpy
ripser
persim
gudhi
yfinance
scipy

## Authors
G Addai (225180738)
G.K Pule (222047683)
O.C Seitsang (221011692)
I.M Chirambwe (221005439)

