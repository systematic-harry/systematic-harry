# StockGPT on NSE: Language-Model Return Prediction for Indian Equities

**Harminder Singh** · CMT · EPAT (QuantInsti) capstone project

Can a GPT-style model that reads only past price moves predict which Indian stocks will do well next month?
This project adapts StockGPT (Mai, 2024), originally built on US stocks, to the Indian market (NSE).

📄 **[Read the full paper (PDF)](StockGPT_NSE_Harminder_Singh.pdf)**

## Headline result
Out-of-sample backtest, Jan 2019 – Dec 2025, monthly long-only top 5% (about 69 stocks),
**after 57 bp round-trip costs**:

| | StockGPT (retrained to 2018) | Average filtered stock |
|---|---|---|
| Compounded annual return | **41.4%** | 16.4% |
| Growth of ₹1 lakh | **₹11.0 lakh** | ₹2.9 lakh |
| Sharpe ratio | **1.15** | 0.68 |
| Maximum drawdown | **−34.2%** | −50.8% |
| Winning stock picks | 54.1% | |
| Profit factor | 1.69 | |

## The data
- Survivorship-free NSE dataset built from raw exchange files: **9.9 million daily records, 4,047 stocks
  (including delisted ones), 1995–2025**
- Adjusted for splits, bonuses and dividends; cross-checked against Interactive Brokers prices
  (over 99% match where IBKR data is clean)
- Liquidity filter on 60-day median turnover; pump-and-dump filter for stocks stuck at circuit limits

## How the test was kept honest
- **Separate periods:** trained on 1995–2010, models compared on 2011–2018, then a single test on 2019–2025.
  The retrained version (trained to 2018) was added afterwards as a robustness check.
- **No extra tuning:** used the original paper's published settings.
- **Benchmarks:** LightGBM, Amazon Chronos, short-term reversal and 12-1 momentum.
- **Costs included** in every reported return.

## Limitations
- **Lumpy returns:** 2020 and 2021 contributed most of the gain; 2022 and 2025 were negative versus the average stock.
- **Smaller stocks:** among the ~180 large, liquid F&O stocks the edge disappears.
- **Recent drawdown:** the 34% fall from Dec 2024 to Feb 2025 had not been recovered by Dec 2025.
- **High turnover:** about 57% of the portfolio changes each month.

## What's in this folder
- `StockGPT_NSE_Harminder_Singh.pdf`: full research paper with charts and results

The data, model and trading code are private. A walkthrough is available to interested firms on request.

## Reference
Mai, D. (2024). *StockGPT: A GenAI Model for Stock Prediction and Trading.* arXiv:2404.05101.

## Contact
[LinkedIn](https://linkedin.com/in/harminder-singh-389310147) · [GitHub](https://github.com/systematic-harry)
