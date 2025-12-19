# Macro-Adaptive Core–Satellite Portfolio Engine

An institutional-grade systematic investment system that utilizes Hidden Markov Models (HMM) for regime detection and vectorized OLS for idiosyncratic alpha generation. This engine is designed with a focus on **robustness**, **realistic execution modeling**, and **statistical significance**.

##  Interactive Versions
* **Kaggle Notebook:** [Access the Live Engine Here](https://www.kaggle.com/code/gaurav11062002/macro-adaptive-portfolio-engine)
* **GitHub Repo:** [gaurav-kar-ji/Macro-Adaptive-Portfolio-Engine](https://github.com/gaurav-kar-ji/Macro-Adaptive-Portfolio-Engine)

##  Overview

Unlike standard backtests that chase headline Sharpe ratios, this engine prioritizes a rigorous investment process. It separates "Signal Quality" from "Portfolio Engineering" and subjects all results to a quantitative audit using the Probabilistic Sharpe Ratio (PSR).

### Key Features
* **Regime-Aware Strategy:** Uses a 3-state Hidden Markov Model (Bull, Bear, Volatile) to dynamically gate alpha exposure.
* **Idiosyncratic Alpha:** Isolates **Residual Momentum** using vectorized OLS to strip out market beta.
* **Institutional Execution:** Models **Implementation Shortfall** by applying slippage based on realized volatility and turnover.
* **Risk Management:** Implements **Kelly Criterion** for position sizing and **Hierarchical Risk Parity (HRP)** for capital allocation.

---

##  Architecture

The system follows a **Core-Satellite** framework:
1.  **The Core:** A beta-neutral/trend-following component designed for steady capital preservation.
2.  **The Satellite:** An aggressive, idiosyncratic alpha seeker that is only activated when the market regime is conducive to stock-picking.



---

##  Quantitative Audit & Robustness

To meet the standard for quantitative research, this project includes:

### 1. Probabilistic Sharpe Ratio (PSR)
Standard Sharpe ratios often suffer from "luck" or non-normal distribution (fat tails). We calculate the PSR against an **institutional hurdle of 0.5**, accounting for the skewness and kurtosis of returns to ensure statistical significance.



### 2. Parameter Stability Analysis
We avoid "cherry-picking" lookback periods by running a sensitivity matrix. The strategy is tested across a grid of parameters (Lookbacks: 63d to 252d) to ensure the edge is persistent and robust across different market cycles.



### 3. Alpha Attribution
We provide a transparent breakdown of where returns originate:
* **Selection Alpha:** Pure asset-picking skill (unlevered).
* **Engineering Alpha:** Returns generated via Kelly Scaling and Dynamic Gating logic.

---

## ⚙️ Installation & Usage

### Prerequisites
* Python 3.11+
* `hmmlearn`, `yfinance`, `scikit-learn`, `pandas`, `numpy`, `scipy`

### Running the Engine
The notebook is structured as follows:

1. **Data Ingestion:** Fetches multi-asset global data via Yahoo Finance.
2. **Regime Training:** Trains the HMM on pre-2020 data to prevent look-ahead bias.
3. **Backtest:** Runs the institutional engine with slippage and Kelly scaling.
4. **Audit:** Generates the PSR, Sensitivity Matrix, and Attribution plots.

##  Results Summary
* **Annualized Sharpe:** ~1.60
* **PSR (vs 0.5 Hurdle):** >95% Confidence Level
* **Max Drawdown:** Optimized via adaptive regime gating.

---
**Disclaimer:** *This project is for educational and research purposes only. It does not constitute financial advice.*
