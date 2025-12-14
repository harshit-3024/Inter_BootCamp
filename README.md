📈 Stock Momentum Prediction & Intraday Backtesting System

A comprehensive Machine Learning-based trading system that identifies high-momentum stocks using XGBoost and technical analysis, specifically designed for 15-minute intraday intervals.

🚀 System Overview

This project operates in a strict two-stage pipeline to separate signal generation from strategy testing:

1. Signal Generation (generate_csvs.ipynb)

Data Ingestion: Fetches historical market data using yfinance.

Feature Engineering: Calculates 15+ technical indicators (RSI, MACD, etc.).

ML Prediction: Uses an XGBoost model to score and rank stocks based on momentum probability.

Output: Generates daily ranking CSV files containing top picks, saved automatically to the backtest_data_15min/ directory.

2. Backtesting Engine (finalv5.ipynb)

Simulation: Reads the ranking files generated in Step 1.

Intraday Logic: Loads 15-minute interval data from combined_stock_data/ to simulate realistic trade entries and exits.

Performance Metrics: Calculates Sharpe Ratio, Max Drawdown, and Annualized Returns.

Visualization: Generates interactive equity curves and trade logs using Plotly.

📂 Project Structure

Ensure your directory is organized exactly as follows for the scripts to link correctly:

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


🛠️ Tech Stack

Language: Python 3.8+

Data Analysis: Pandas, NumPy

Machine Learning: XGBoost, Scikit-learn

Data Source: yfinance

Visualization: Plotly (Interactive dashboards), Matplotlib

Environment: Jupyter Notebook / Lab

⚙️ Installation

Clone the repository:

git clone https://github.com/harshit-3024/Inter_BootCamp.git
cd Inter_Bootcamp


Install the required dependencies:

pip install pandas numpy xgboost yfinance plotly matplotlib


🏃‍♂️ Usage Guide

Step 1: Generate Signals

Open and run generate_csvs.ipynb.

This script will analyze historical data and populate the backtest_data_15min/ folder with ranking files (e.g., momentum_ranking_2024-01-01.csv).

Note: Ensure you have an active internet connection for yfinance to fetch data.

Step 2: Run Backtest

Open and run finalv5.ipynb.

Verify Data Path: Ensure your 15-minute intraday data is located in combined_stock_data/.

Configure Parameters: You can adjust the simulation settings in the "Configuration" cell

Analyze Results: Run all cells to view the interactive dashboard and performance logs.

📊 Key Features

Ensemble Learning: Combines fundamental technical analysis with gradient boosting for robust predictions.

Realistic Backtesting: Accounts for intraday volatility by using 15-minute granularity rather than just daily closing prices.

Custom Indicators: Dedicated Indicators class for consistent calculation of RSI, Moving Averages, and Volatility across both notebooks.


📝 License

Distributed under the MIT License. See LICENSE for more information.
