# Market Beat
### A Practical Quantitative Portfolio Construction Engine

**Market Beat** is a Python-based quantitative investing project that builds a **diversified, rules-based equity portfolio** using real market data, statistical signals, and realistic portfolio constraints.

Unlike purely academic optimizers, Market Beat is designed to reflect **how portfolio decisions are made in practice**: noisy data, liquidity limits, sector exposure rules, and position sizing constraints.

This project was built to demonstrate **end-to-end quantitative thinking** — from raw ticker ingestion to an investable portfolio with weights, capital allocations, and risk controls.

---

## High-Level Overview

Market Beat takes a universe of equity tickers and:

1. Cleans and validates the input universe  
2. Filters for tradability and liquidity  
3. Computes risk, return, and momentum metrics  
4. Scores and ranks securities using multiple signals  
5. Constructs a diversified portfolio under strict constraints  
6. Outputs final weights, allocations, and diagnostics  

---

## What Market Beat Builds

- **Portfolio size:** 10–25 equities  
- **Capital:** CAD $1,000,000  
- **Universe:** U.S. & Canadian listed equities  
- **Strategy type:** Long-only, rules-based  
- **Objective:** Risk-adjusted return with diversification  

### Enforced Constraints
- Maximum **15% per security**
- Maximum **40% per sector**
- Minimum sector diversity
- Liquidity and data-quality requirements

All constraints are enforced programmatically.

---

## How the Model Works (Conceptual)

At a high level, Market Beat follows this pipeline:

```
Tickers → Cleaning → Liquidity Filter → Metric Computation
       → Scoring → Ranking → Portfolio Construction → Output
```

Each stage is deliberately modular and transparent.

---

## How Returns & Scores Are Calculated

### 1. Market Data
- Daily OHLCV data via `yfinance`
- Benchmarks:
  - S&P 500 (U.S. market proxy)
  - TSX Composite (Canadian market proxy)

---

### 2. Core Metrics
For each stock, the model computes:

- Mean daily return  
- Volatility (standard deviation of returns)  
- Sharpe ratio (risk-adjusted performance)  
- Beta vs blended market benchmark  
- Residual alpha and residual momentum  
- Liquidity stability (volume & consistency)  
- Market capitalization (converted to CAD)  
- Sector classification  

📸 **Screenshot Placeholder**
- Metrics dataframe preview

---

### 3. Initial Scoring Logic
Each stock receives an **Initial Score** based on:

- Residual momentum (primary signal)
- Sharpe ratio (quality filter)
- Liquidity score
- Volatility penalty

Scores are normalized to ensure comparability across securities.

📸 **Screenshot Placeholder**
- Top securities by Initial Score

---

### 4. Advanced Estimates
To avoid relying on a single signal, Market Beat incorporates:

- **CAPM expected return**
- **Monte Carlo simulation**
  - 1-year geometric Brownian motion projection
- **Diversification score**
  - Based on average absolute covariance with other assets

📸 **Screenshot Placeholder**
- Monte Carlo expected returns
- Covariance / diversification metrics

---

### 5. Final Ranking
All normalized components are combined into a **Total Score**, producing a ranked universe used for portfolio construction.

📸 **Screenshot Placeholder**
- Final ranking table

---

## Portfolio Construction Logic

1. Selects a 10-stock core portfolio  
2. Converts Total Scores into portfolio weights  
3. Applies position and sector caps  
4. Redistributes excess weight automatically  
5. Expands the portfolio (up to 25 stocks) if needed to preserve diversification  

The final portfolio is **fully invested, constraint-compliant, and interpretable**.

📸 **Screenshot Placeholder**
- Final portfolio table
- Sector allocation summary

---

## Results Summary

> _(Example — replace with your actual run)_

- **Backtest period:** Oct 2024 – Sep 2025  
- **Portfolio return:** +XX.X%  
- **Benchmark return:** +XX.X%  
- **Outperformance:** +X.X%  
- **Annualized volatility:** XX.X%  
- **Sharpe ratio:** X.XX  

📸 **Screenshot Placeholder**
- Portfolio performance summary

---

## Visualizations & Graphs

The project produces clear visual diagnostics, including:

- Equity curve vs benchmark  
- Sector weight breakdown  
- Distribution of portfolio weights  
- Monte Carlo return distribution  

📸 **Screenshot Placeholder**
- Performance graph
- Sector allocation chart
- Monte Carlo distribution

---

## How to Run the Project

### Requirements
Python 3.x with:
- pandas
- numpy
- numpy-financial
- yfinance
- matplotlib

```bash
pip install pandas numpy numpy-financial yfinance matplotlib
```

### Launch Steps
1. Place `Tickers_Example.csv` in the project directory  
2. Run the notebook or script from top to bottom  
3. Review console outputs, tables, and graphs  

---

## Exported Outputs

- Ranked universe with all metrics  
- Final portfolio table:
  - Ticker
  - Sector
  - Weight
  - CAD allocation
  - Share count
- Constraint verification summaries  
- Visual performance diagnostics  

All outputs are designed to be recruiter- and reviewer-friendly.

---

## Why This Project Matters

Market Beat demonstrates:
- Practical quantitative finance intuition  
- Data cleaning and validation discipline  
- Risk-aware portfolio construction  
- Clear, explainable modeling decisions  
- End-to-end ownership of a technical system  

This project prioritizes **clarity and realism over buzzwords**.

---

## Credits

**Author:** Saren Sabeskaran  
**Tools:** Python, pandas, NumPy, yfinance  
**Data Source:** Yahoo Finance  

---

## Disclaimer

This project is for educational and demonstration purposes only.  
It does not constitute investment advice.
