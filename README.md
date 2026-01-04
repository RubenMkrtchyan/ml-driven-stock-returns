# ML‑Based Stock Return Prediction with Confidence‑Filtered Backtesting

## Project Overview
This project investigates whether machine learning models can improve short‑term stock return prediction and portfolio performance compared to a traditional linear model.

Specifically, we compare:
- Linear Regression (baseline, interpretable model)
- Random Forest Regression (non‑linear ML model)

Rather than trading every prediction, we apply a confidence‑based filtering approach, executing trades only when the model’s predicted signal is strong. This mimics realistic investment decision‑making and reduces overtrading.


## Objective
The goal of this project is to answer: Does a non‑linear ML model (Random Forest) produce better risk‑adjusted returns than Linear Regression when combined with selective, confidence‑based trading?

Performance is evaluated both at the prediction level and the portfolio level using realistic backtesting assumptions.


## Data
- Daily OHLCV stock price data
- 15–20 liquid U.S. equities
- Market index data for relative performance features
- Data sourced via `yfinance`

A fixed stock universe is used to reduce survivorship bias.


## Feature Engineering
Features are designed using financial intuition rather than excessive technical indicators:

- Short- and medium-term returns
- Distance from moving averages
- Rolling volatility
- Relative performance vs market index
- Cross-sectional momentum ranking within the stock universe


## Target Variable
- 5-day forward log return

This target is commonly used in financial modeling due to its stability and interpretability.


## Models
Two models are evaluated:

### Linear Regression
- Interpretable baseline model
- Assumes linear relationships between features and returns

### Random Forest Regression
- Captures non-linear relationships
- Robust to noise and feature interactions

Models are trained using walk-forward validation to avoid look-ahead bias.


## Trading Strategy
Instead of trading every prediction, a confidence-based filtering approach is applied:

- Signals are ranked by absolute predicted return
- Only the top 30% strongest signals are traded
- Weak predictions are ignored
- Portfolio may remain partially in cash


## Portfolio Construction & Backtesting
- Long-only strategy
- Equal-weighted positions
- Maximum of 5–8 active stocks
- Fixed 5-day holding period
- Transaction costs included
- Weekly rebalancing


## Evaluation Metrics

### Model-Level
- Mean Squared Error (MSE)
- Directional accuracy

### Portfolio-Level
- Cumulative return
- Sharpe ratio
- Maximum drawdown
- Turnover


## Limitations
- No short selling
- Fixed stock universe
- Limited macroeconomic features
- Simplified transaction cost assumptions


## Future Improvements
- Add market regime detection
- Test additional ML models (e.g., Gradient Boosting)
- Dynamic confidence thresholds
- Risk-based position sizing
