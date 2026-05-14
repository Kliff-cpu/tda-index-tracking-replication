# TDA-Based Sparse Index Tracking  
### Replication and Beta–Volatility Extension

## Overview

This repository contains the full replication and extension of the paper:

> Goel, A., Pasricha, P. and Kanniainen, J. (2025).  
> *Risk Reduced Sparse Index Tracking Portfolio: A Topological Data Analysis Approach.*

The project reproduces the Topological Data Analysis (TDA) sparse index tracking framework proposed by the original authors and introduces a novel economically interpretable extension based on CAPM beta and asset volatility. The empirical analysis is conducted using S\&P 500 data and follows a rolling-window out-of-sample backtesting framework across multiple market regimes. :contentReference[oaicite:0]{index=0}

The objective is to investigate whether traditional financial risk measures can provide competitive sparse index tracking performance when incorporated into the same weighted Elastic-Net optimisation structure as the TDA framework.

---

## Project Motivation

Sparse index tracking remains an important problem in portfolio optimisation because fully replicating large indices such as the S\&P 500 is often impractical due to transaction costs, liquidity constraints, and portfolio management complexity. :contentReference[oaicite:1]{index=1}

Goel et al. (2025) addressed this problem using Topological Data Analysis, where persistence landscape norms derived from persistent homology are used as adaptive regularisation penalties within a weighted Elastic-Net framework. While the method achieved strong empirical tracking performance, the economic interpretation of the TDA penalties remained unclear. :contentReference[oaicite:2]{index=2}

This project therefore investigates whether economically interpretable measures such as:

- CAPM beta (systematic index exposure)
- Asset volatility (idiosyncratic risk)

can serve as alternative adaptive penalty structures while maintaining competitive tracking performance and portfolio sparsity.

---

## Research Question

Can CAPM beta and volatility serve as economically interpretable alternatives to TDA-based penalties while achieving comparable or improved:

- Tracking accuracy
- Risk control
- Portfolio sparsity
- Portfolio stability
- Risk-adjusted performance

---

## Replication Framework

The original TDA framework uses:

- Topological Data Analysis (TDA)
- Persistent homology
- Persistence landscapes
- \(L^1\) persistence landscape norms
- Weighted Elastic-Net optimisation

The implementation follows the original rolling-window setup:

- 504-day in-sample window
- 21-day out-of-sample window
- Takens embedding: \(d = 3,\ \tau = 1\)
- 42-day overlapping subseries
- Persistent homology via Vietoris–Rips filtrations

Persistence landscape norms are computed from both \(H_0\) and \(H_1\) homology dimensions and used as adaptive portfolio penalties. :contentReference[oaicite:3]{index=3}

---

## Proposed Economic Extension

This study introduces an alternative penalty structure based on:

- CAPM index beta
- Asset volatility

The extension preserves the same optimisation framework used in the original paper but replaces the topological penalties with economically interpretable financial risk measures.

The economic penalties are defined as:

\[
\alpha_i = \frac{1}{|\beta_i| + \varepsilon},
\qquad
b_i = \sigma_i
\]

where:

- \(\beta_i\) measures each asset’s exposure to the benchmark index,
- \(\sigma_i\) measures asset volatility,
- \(\varepsilon\) is a small stabilisation constant.

This creates a hybrid framework linking sparse index tracking with classical financial risk theory. :contentReference[oaicite:4]{index=4}

---

## Models Implemented

| Category | Models |
|---|---|
| Benchmark Model | TE |
| TDA Models | TDA-Lasso, TDA-EN11, TDA-EN12 |
| Economic Extension Models | Vol-EN11, Beta-EN11, BetaVol, BetaVol-Long |

---

## Empirical Findings

The empirical results show that:

- TDA-based models remain the strongest specifications for strict index replication,
- TDA models achieve the lowest tracking errors and strongest benchmark correlations,
- The proposed BetaVol framework generates stronger annualised returns,
- BetaVol achieves substantially lower turnover,
- The economic models improve interpretability but accept higher downside risk and tracking deviation. :contentReference[oaicite:5]{index=5}

The findings suggest that TDA captures structural information in financial return series that is not fully explained by beta or volatility alone.

---

## Repository Structure

```text
tda-index-tracking-replication/
│
├── Notebook/
│   └── Portfolio Final.ipynb
│
├── Data/
│   ├── SP500_Constituents.xlsx
│   └── SP500_Index_Data.xlsx
│
├── Appendix/
│   ├── Raw_Data_Source.pdf
│   ├── Panel_I_Cleaning.pdf
│   └── Panel_II_Cleaning.pdf
│
├── TDA_Final_Report.pdf
├── requirements.txt
└── README.md
```

---

## Data Description

The empirical analysis uses:

- S\&P 500 constituent stock data
- S\&P 500 index data
- Daily adjusted close prices obtained from Yahoo Finance

The dataset is divided into two sub-periods:

| Period | Sample |
|---|---|
| Panel I | 11 October 1999 – 10 October 2018 |
| Panel II | 1 January 2018 – 8 March 2023 |

Only stocks with complete observations throughout each sub-period are retained. :contentReference[oaicite:6]{index=6}

---

## Reproducing the Results

### 1. Clone the repository

```bash
git clone https://github.com/Kliff-cpu/tda-index-tracking-replication.git
cd tda-index-tracking-replication
```

### 2. Install required libraries

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
Notebook/Portfolio Final.ipynb
```

Run all cells sequentially from top to bottom.

---

## Outputs Reproduced

The notebook reproduces:

- Out-of-sample performance tables
- Growth-of-\$1 plots
- Penalty correlation analysis
- Window-by-window penalty comparison
- Epsilon sensitivity analysis
- Kupiec VaR backtesting
- Risk-adjusted performance measures
- Portfolio turnover analysis

---

## Main Libraries

- numpy
- pandas
- matplotlib
- scipy
- cvxpy
- ripser
- persim
- gudhi
- yfinance
- scikit-learn

---

## Full Report

The complete project report is available in:

```text
TDA_Final_Report.pdf
```

Additional supplementary material and data-cleaning documentation are included in the `Appendix/` folder.

---

## Authors

- G Addai (225180738)
- G.K Pule (222047683)
- O.C Seitsang (221011692)
- I.M Chirambwe (221005439)

---

## Reference

Goel, A., Pasricha, P. and Kanniainen, J. (2025).  
*Risk Reduced Sparse Index Tracking Portfolio: A Topological Data Analysis Approach.*  
Omega, 103432.
