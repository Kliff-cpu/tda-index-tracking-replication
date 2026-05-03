# TDA-Based Sparse Index Tracking (Replication & Extension)


## Overview

This project replicates and extends the methodology proposed in:

Goel et al. (2025) — *Risk reduced sparse index tracking portfolio: A topological data analysis approach*

The objective is to construct sparse portfolios that replicate the S&P 500 using data-driven regularisation techniques.

## Replication

The original framework uses:

- Topological Data Analysis (TDA)
- Persistence landscapes
- L1 norms as adaptive penalties (αᵢ, βᵢ)
- Elastic Net optimisation

The implementation follows:

- Rolling window: 504 in-sample / 21 out-of-sample
- Takens embedding (d = 3, τ = 1)
- 42-day subseries with overlap

## Proposed Extension

Instead of TDA-based penalties, this study introduces:

- CAPM Beta (systematic risk)
- Volatility (idiosyncratic risk)

These are used as adaptive penalties in the same Elastic Net framework.

## Research Question

Can CAPM beta and volatility replace TDA-based penalties while achieving similar or better:

- Tracking accuracy
- Risk control
- Portfolio sparsity

## Results Summary

The TDA-based models:

- Reduce tracking error
- Improve turnover (lower transaction costs)
- Maintain strong correlation with the index

The extension aims to improve interpretability while preserving performance.

## Repository Structure
