# 📈 Stock Momentum Prediction & Intraday Backtesting System

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active-success?style=for-the-badge)

A comprehensive Machine Learning-based trading system that identifies high-momentum stocks using **XGBoost** and technical analysis, specifically designed for **15-minute intraday intervals**.

---

## 🚀 System Overview

This project operates in a strict two-stage pipeline to separate signal generation from strategy testing.

```mermaid
graph TD
    A["Fetch Data (yfinance)"] -->|History| B("generate_csvs.ipynb")
    B -->|"Feature Eng + XGBoost"| C{"Signal Generation"}
    C -->|"Output Rankings"| D["backtest_data_15min/"]
    E["combined_stock_data/"] -->|"15-min Intraday Data"| F("finalv5.ipynb")
    D -->|"Daily Rankings"| F
    F -->|"Backtest Engine"| G["Metrics & Plotly Viz"]
````

### 1\. Signal Generation (`generate_csvs.ipynb`)

  * **Data Ingestion:** Fetches historical market data using `yfinance`.
  * **Feature Engineering:** Calculates 15+ technical indicators (RSI, MACD, etc.).
  * **ML Prediction:** Uses an **XGBoost** model to score and rank stocks based on momentum probability.
  * **Output:** Generates daily ranking CSV files automatically saved to `backtest_data_15min/`.

### 2\. Backtesting Engine (`finalv5.ipynb`)

  * **Simulation:** Reads the ranking files generated in Step 1.
  * **Intraday Logic:** Loads 15-minute interval data from `combined_stock_data/` to simulate realistic trade entries/exits.
  * **Performance Metrics:** Calculates Sharpe Ratio, Max Drawdown, and Annualized Returns.
  * **Visualization:** Generates interactive equity curves and trade logs using **Plotly**.

-----

## 📂 Project Structure

Ensure your directory is organized exactly as follows for the scripts to link correctly:

```text
├── generate_csvs.ipynb       # [Step 1] Generates momentum rankings
├── finalv5.ipynb             # [Step 2] Runs the backtest simulation
├── backtest_data_15min/      # Output folder for Step 1 (Created automatically)
│   ├── momentum_ranking_2023-01-01.csv
│   └── ...
├── combined_stock_data/      # Input folder: MUST contain 15-min stock CSVs
│   ├── ADANIGREEN_NS.csv
│   ├── BANKBARODA_NS.csv
│   └── ...
└── README.md
```

-----

## 🛠️ Tech Stack

| Category | Technologies |
| :--- | :--- |
| **Language** | Python 3.8+ |
| **Data Analysis** | Pandas, NumPy |
| **ML & Stats** | XGBoost, Scikit-learn |
| **Data Source** | yfinance |
| **Visualization** | Plotly (Interactive), Matplotlib |

-----

## ⚙️ Installation

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/harshit-3024/Inter_BootCamp.git
    cd Inter_Bootcamp
    ```

2.  **Install dependencies:**

    ```bash
    pip install pandas numpy xgboost yfinance plotly matplotlib
    ```

-----

## 🏃‍♂️ Usage Guide

### Step 1: Generate Signals

Open and run `generate_csvs.ipynb`.

> **Note:** This script will analyze historical data and populate the `backtest_data_15min/` folder with ranking files. Ensure you have an active internet connection for `yfinance`.

### Step 2: Run Backtest

Open and run `finalv5.ipynb`.

1.  **Verify Data Path:** Ensure your local 15-minute intraday data is located in `combined_stock_data/`.
2.  **Configure Parameters:** Adjust simulation settings in the "Configuration" cell.
3.  **Analyze Results:** Run all cells to view the interactive dashboard.

-----

## 📊 Key Features

  * **Ensemble Learning:** Combines fundamental technical analysis with gradient boosting for robust predictions.
  * **Realistic Backtesting:** Accounts for intraday volatility by using 15-minute granularity rather than just daily closing prices.
  * **Custom Indicators:** Dedicated Indicators class for consistent calculation of RSI, Moving Averages, and Volatility across both notebooks.

-----

## 📝 License

Distributed under the MIT License. See `LICENSE` for more information.

```
```
