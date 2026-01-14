# Quantitative-Portfolio-Management-Strategy

A Python-based portfolio construction system that builds a **rules-compliant, diversified equity portfolio** using market data, statistical scoring, and risk controls.  
The model is designed to reflect **practical portfolio management constraints**, not purely theoretical optimization.

---

## Project Summary

This project constructs a **long-only equity portfolio (10–25 stocks)** under realistic investment constraints using historical market data.  
It combines **data cleaning, factor-based scoring, risk-adjusted performance metrics, and diversification controls** to produce a final, investable portfolio.

Key objectives:
- Select fundamentally tradable equities (US & Canada)
- Rank securities using multiple performance and risk signals
- Enforce strict position and sector constraints
- Convert model output into real-world allocations (CAD, shares)

---

## Portfolio Constraints

The portfolio strictly enforces the following rules:

- **Total capital:** CAD $1,000,000  
- **Number of holdings:** 10–25 stocks  
- **Maximum weight per stock:** 15%  
- **Maximum weight per sector:** 40%  
- **Long-only** (no leverage, no short selling)

All constraints are programmatically checked and enforced.

---

## Data Inputs

### Required Input File
**`Tickers_Example.csv`**
- Single column of equity tickers
- Mixed sector exposure required
- Invalid, illiquid, or unsupported tickers are automatically removed

### Market Data Source
- Historical price and volume data retrieved via `yfinance`
- Market benchmarks:
  - S&P 500 (US)
  - TSX Composite (Canada)

---

## Methodology Overview

### 1. Ticker Cleaning & Validation
- Removes whitespace, empty rows, duplicates, and malformed tickers
- Filters to equities with valid market data
- Stops execution if:
  - Fewer than 10 valid tickers remain
  - Insufficient sector diversity is detected

📸 **Screenshot Placeholder**
- Cleaned ticker list vs original CSV

---

### 2. Liquidity Filtering
Ensures all securities are realistically tradable:
- Minimum trading frequency per month
- Minimum average daily volume threshold

📸 **Screenshot Placeholder**
- Liquidity filter results

---

### 3. Metric Computation
For each eligible security, the model computes:
- Mean daily returns and volatility
- Sharpe ratio (risk-adjusted return)
- Beta vs blended market benchmark
- Residual alpha and momentum
- Liquidity stability
- Market capitalization (converted to CAD)
- Sector classification

📸 **Screenshot Placeholder**
- Metrics dataframe preview

---

### 4. Factor Scoring
Each stock receives an **Initial Score** based on:
- Residual momentum (primary signal)
- Sharpe ratio
- Liquidity quality
- Volatility penalty

Scores are normalized to ensure comparability across securities.

📸 **Screenshot Placeholder**
- Top-ranked securities by Initial Score

---

### 5. Advanced Risk & Return Estimates
The model enhances ranking using:
- **CAPM expected return**
- **Monte Carlo simulation** (1-year GBM projection)
- **Diversification score** using average absolute covariance

📸 **Screenshot Placeholder**
- Monte Carlo expected returns
- Covariance/diversification metrics

---

### 6. Total Score & Ranking
All normalized components are combined into a **Total Score**, producing a final ranked universe of securities.

📸 **Screenshot Placeholder**
- Final ranking by Total Score

---

### 7. Portfolio Construction
- Selects a 10-stock core portfolio with sector caps
- Converts Total Scores into portfolio weights
- Applies:
  - 15% single-stock cap
  - 40% sector cap
- Automatically redistributes excess weight
- Expands the portfolio (up to 25 stocks) if required to maintain constraints

📸 **Screenshot Placeholder**
- Final portfolio allocation table
- Sector weight summary

---

## Outputs

The program produces:
- Ranked security universe with full metrics
- Final portfolio with:
  - Ticker
  - Sector
  - Total Score
  - Portfolio weight
  - CAD allocation
  - Number of shares
- Constraint verification summaries

All outputs are designed to be directly interpretable and submission-ready.

---

## How to Run

1. Install dependencies:
```bash
pip install pandas numpy numpy-financial yfinance matplotlib
```

2. Place `Tickers_Example.csv` in the project directory  
3. Run the notebook or script from top to bottom  
4. Review final portfolio outputs and constraint checks  

---

## Assumptions & Limitations

- Relies on publicly available historical market data
- Market regime changes are not explicitly modeled
- FX conversion assumes stable CAD/USD rates when data is unavailable
- Results are illustrative and not financial advice

---

## Team Information

**Team XX**  
(Add names and student IDs)

---

## Disclaimer

This project is for academic and educational purposes only.  
It does not constitute investment advice or a recommendation to trade securities.
