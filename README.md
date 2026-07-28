# public-utility-regression-model
# AFM 244 — Target Revenue Regression Quiz (July 24)

A Jupyter/Colab notebook that models **Target Corporation (TGT)** quarterly revenue using an OLS regression with a linear time trend and two dummy variables, then interprets the results in a client-style memo.

## What it does

1. **Loads data** — reads `qSales_2024.csv`, a panel of quarterly sales (`saleq`) for several tickers.
2. **Filters to Target** — subsets rows where `tic == 'TGT'`.
3. **Explores seasonality** — plots the revenue series and checks average revenue by fiscal quarter to confirm a Q4 (holiday) spike.
4. **Builds features:**
   - `time` — sequential index (1…N) for the linear trend.
   - `holiday_dv` — dummy = 1 in fiscal Q4, else 0 (holiday season).
   - `covid_dv` — dummy = 1 from the quarter ending 2020-05-01 onward, else 0 (post-2020 level shift).
5. **Fits the model** — `sm.OLS(y, x)` on `revenue = const + time + holiday_dv + covid_dv`.
6. **Evaluates** — reports coefficients, R², and p-values via `.summary()`.
7. **Predicts** — generates fitted values and 90% prediction intervals, and plots actual vs. predicted.
8. **Memo** — a markdown cell interpreting the two dummies and the investment implications.

## Fitted model
