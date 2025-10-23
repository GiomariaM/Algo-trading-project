# Algorithmic Trading Strategies

This repository contains the implementation and evaluation of several algorithmic trading strategies developed and tested on the SPY ETF (which tracks the S&P 500 index).  
It’s based on a university project exploring how traditional and machine-learning-based approaches compare when applied to real market data.

## Overview

The repository includes the following strategies:

1. **Buy-and-Hold Strategy** (`buynhold_strategy.ipynb`)  
   - Baseline benchmark: buy SPY at the start and hold throughout the period.  
   - Uses 5x leverage to simulate a margin-based investment.  

2. **Trend-Following Strategy** (`intro_trend_following_strategy.ipynb`)  
   - Uses short-term and long-term moving averages to identify market direction.  
   - Goes long with leverage when short-term momentum exceeds long-term trend.  

3. **Technical Analysis Strategy** (`technical_analysis_strategy.ipynb`)  
   - Combines three classic indicators: MACD, RSI, and Bollinger Bands.  
   - Goes long when at least two of the indicators signal a buy opportunity.  

4. **Neural Network (LSTM) Strategy** (`torch_lstm_strategy.ipynb`)  
   - A machine learning approach using a Long Short-Term Memory (LSTM) model implemented in PyTorch.  
   - Predicts the next day’s price and trades long/short accordingly.  

## Methodology

Each strategy was trained and tested using SPY data (2014–2019) from Yahoo! Finance.  
The Effective Fed Funds Rate (EFFR) was used as the risk-free rate, adjusted to daily values.  
All strategies use **5x leverage** for consistency.

Performance metrics include:
- **Sharpe Ratio**
- **Sortino Ratio**
- **Maximum Drawdown**
- **Calmar Ratio**

The notebook `report.pdf` provides a detailed explanation of the methodology, formulas, and results analysis.

## Results Summary

| Strategy | Sharpe (Test) | Sortino (Test) | Max Drawdown (Test) | Calmar (Test) |
|-----------|---------------|----------------|----------------------|----------------|
| Buy & Hold | 0.66 | 0.83 | -0.71 | 0.68 |
| Trend-Following | 0.81 | 0.59 | -0.39 | 0.88 |
| Technical Analysis | 0.62 | 0.29 | -0.37 | 0.67 |
| LSTM | -0.20 | -0.32 | -0.78 | -0.19 |

Overall, **Buy-and-Hold** proved the most stable and profitable strategy in this market period.  
The **LSTM** strategy showed strong overfitting — excellent training performance but poor generalization on the test set.

## Files

| File | Description |
|------|--------------|
| `buynhold_strategy.ipynb` | Benchmark buy-and-hold implementation |
| `intro_trend_following_strategy.ipynb` | Moving-average trend-following strategy |
| `technical_analysis_strategy.ipynb` | Multi-indicator technical trading strategy |
| `torch_lstm_strategy.ipynb` | LSTM-based predictive model |
| `report.pdf` | Full report and methodology |

