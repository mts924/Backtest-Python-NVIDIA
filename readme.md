# Quantitative Backtesting Engine: Moving Average Crossover & Risk Management

An open-source Python framework designed to simulate, optimize, and stress-test algorithmic trading strategies on historical equity data. 

This project explores quantitative modeling fundamentals, parameter optimization, risk mitigation via stop-losses, and empirical validation using strict **In-Sample vs. Out-of-Sample (Train/Test)** methodology.

---

##  Table of Contents
- [Overview](#overview)
- [Architecture & Tech Stack](#architecture--tech-stack)
- [Trading Strategy](#trading-strategy)
- [Risk Management Engine](#risk-management-engine)
- [Optimization & Initial Findings](#optimization--initial-findings)
- [The Reality Check: Out-of-Sample Testing](#the-reality-check-out-of-sample-testing)
- [Installation & Usage](#installation--usage)
- [Next Steps & Roadmap](#next-steps--roadmap)

---

##  Overview
Backtesting is an essential diagnostic tool in quantitative finance to evaluate how a systematic strategy would have performed historically. 

Rather than chasing unrealistic returns, this project focuses on **robustness, parameter stability, and execution discipline**, highlighting the danger of curve-fitting (overfitting) when optimizing trading parameters.

---

##  Architecture & Tech Stack
- **Language:** Python 3.x
- **Environment:** Google Colab / Jupyter Notebooks
- **Data Ingestion:** `yfinance` API (automated retrieval of historical OHLCV data)
- **Data Manipulation:** `pandas`, `numpy`
- **Backtesting Core:** `backtesting.py` (event-driven simulation engine)
- **Version Control:** Git & GitHub

---

##  Trading Strategy
The initial model implements a dual **Simple Moving Average (SMA) crossover** trend-following strategy:
* **Fast Window ($n_1$):** Tracks short-term price momentum.
* **Slow Window ($n_2$):** Tracks broad market direction.
* **Buy Signal:** Triggered when the Fast SMA crosses above the Slow SMA (`crossover(SMA_fast, SMA_slow)`).
* **Exit Signal:** Triggered when the Fast SMA crosses below the Slow SMA (`crossover(SMA_slow, SMA_fast)`).

---

##  Risk Management Engine
A trading edge cannot survive without capital preservation. The engine enforces an automated risk control mechanism:
* **Dynamic Stop-Loss:** Each long position automatically sets a stop-loss at **5% below the entry price** (`sl = Close * 0.95`).
* **Asymmetric Risk/Reward:** Demonstrates the core trading principle of **cutting losers early and letting winners run**.

---

##  Optimization & Initial Findings (In-Sample)
Using grid search optimization on 5-year historical data for **NVIDIA (NVDA)** maximizing for the **Sharpe Ratio**, the optimizer identified:
* **Optimal Windows:** SMA(5) and SMA(35)
* **Total Return:** ~659% (In-Sample)
* **Maximum Drawdown:** Capped at -36%
* **Win Rate:** **36.3%**

### Key Takeaway
Despite losing on nearly two-thirds of the trades (~64% loss rate), the strategy remained highly profitable in-sample because the stop-loss strictly limited downside risk (worst single loss: -14%), while the trend captured outlier upside moves (best single trade: +146%).
---

## 👥 Contributors & Authors

This project is a collaborative effort developed by:

* **Mathis A Motevally**  
  * GitHub: [@mts924](https://github.com/mts.924)  
  * LinkedIn: [Mathis A Motevally](https://www.linkedin.com)

* **[Nom du collaborateur]**  
  * GitHub: [@pseudo-github]---

## 👥 Contributors & Authors

This project is a collaborative effort developed by:

* **Mathis A Motevally**  
  * GitHub: [@mts924](https://github.com/mts.924)  

* **Braylen Morris**  
  * GitHub: [@bray-bit](https://github.com/bray-bit)  
