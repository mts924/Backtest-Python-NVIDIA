# Quantitative Backtesting & Risk Management Pipeline

A collaborative Python project focused on algorithmic trading backtesting, risk management enforcement, and out-of-sample robustness testing for financial markets.

---

## Project Overview
Most beginner trading projects focus exclusively on finding "magical" historical returns. This project takes a rigorous, engineering-focused approach: **methodology, parameter optimization, and strict risk management** over curve-fitted profits.

Developed collaboratively using Python and Git version control, this repository simulates moving average strategies, enforces strict stop-losses, and implements chronological train/test splits to evaluate real-world viability.

---

##  Tech Stack & Tools
* **Language:** Python
* **Environment:** Google Colab (Cloud Jupyter Notebooks)
* **Data Source:** Yahoo Finance API (`yfinance`)
* **Backtesting Engine:** `backtesting.py`
* **Data Manipulation:** `pandas`, `numpy`
* **Version Control:** Git & GitHub

---

##  Core Methodology & Strategy

### 1. The Strategy (Moving Average Crossover)
* Computes two Simple Moving Averages: a **fast line** (short-term momentum) and a **slow line** (macro trend).
* **Entry Rule:** Buy when the fast SMA crosses above the slow SMA.
* **Exit Rule:** Close position when the fast SMA crosses below the slow SMA.

### 2. Risk Management First
* Implemented a **strict 5% stop-loss** (`sl = Close * 0.95`) upon trade entry.
* Designed to cut losing trades early and let winning trends run, addressing the asymmetry of market risk.

### 3. Overfitting & Out-of-Sample Testing
* **The In-Sample Trap:** Initial grid searches optimized over a 5-year dataset yielded high returns (e.g., +659% on NVDA with an SMA 5/35 configuration and a 36.3% win rate), proving the value of cutting losses early (-14% max loss vs +146% max win).
* **The Out-of-Sample Reality:** To prevent curve-fitting, we implemented chronological **Train/Test splits** (optimizing rules strictly on past blocks, e.g., 2001–2011, and testing once on unseen future data, e.g., 2012–2026). This mirrors institutional workflows where past parameters rarely guarantee future correlation.

---

##  Repository Structure
```text
├── notebooks/          # Google Colab notebooks for backtesting experiments
├── src/                # Modular Python scripts (data ingestion, strategy logic)
├── data/               # Historical OHLCV datasets and caches
├── README.md           # Project documentation
└── requirements.txt    # Python dependencies
