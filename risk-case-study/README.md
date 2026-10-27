# Portfolio Risk Case Study: Protecting Gains in a Leveraged Equity Account

**Harminder Singh** · CMT · EPAT

📄 **[Full case study (PDF)](Portfolio_Risk_Case_Study_Harminder_Singh.pdf)**

## The problem
A private client's US equity account (long/short, on margin) was up ~60% by mid-June, then gave most of it back by October.
A 15% drawdown rule existed but was never enforced.

## What I did
- **Rebuilt daily positions** from the trade journal (reconciled missing exits and splits, excluded 7 disputed trades).
- **Measured portfolio risk every evening with historical VaR(95)**, computed bottom-up from actual positions:
  today's holdings × each stock's real daily returns over the last 500 and 250 days, taking the worse of the two.
- **Diagnosed the two largest losses:**
  - **Early June, leverage:** gross exposure 1.52× equity across 17 correlated AI/semiconductor names; VaR 5.9% → next day −10%.
  - **Late June, concentration:** one stock at 53% of equity and half the portfolio's risk; VaR 6.7% → next day −11.5%.
  - VaR first crossed 4% in mid-April, **seven weeks before the first big loss**.
- **Ran a Monte Carlo stress test:** 10,000 simulated 20-day paths, built from 5-day blocks of the portfolio's real daily P&L.
- **Replayed 15 rule combinations** (VaR limits Off/2/3/4/5% × no floor / hard floor / stepped floor) using only data available each day.

## The change I recommended
1. **VaR-based position sizing:** each evening, scale the book to *VaR limit ÷ current VaR* (capped at 100%), with a **5% limit**.
2. **Hard 15% loss floor:** stop trading once the account is 15% below its peak.

## Results (replay, 2 Feb – 5 Oct)

| | Before (no rules) | After (VaR 5% + 15% floor) |
|---|---|---|
| Return | −2.2% | **+18.4%** |
| Maximum drawdown | −30.8% | **−15.1%** |
| Worst single day | −11.5% | **−8.6%** |
| Sharpe ratio | 0.06 | **1.01** |

**Monte Carlo:** with the early-June book, the chance of hitting the 15% floor within 20 days was **50%**; cutting size to the VaR limit lowered it to **28%**. Adding the floor cut the chance of a fall over 20% from **31% to 3%**.

**Also found:** the July–October losses came from overtrading (same-day round trips rose to 53%), which VaR cannot see. The loss floor is what contains it.

Client details are withheld. Results are a replay on the account's own history, not live trading.
