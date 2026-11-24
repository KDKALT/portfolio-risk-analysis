# Portfolio Risk Analysis

An interactive, single-file web application that applies mean–variance portfolio theory (Markowitz) to real daily price data. It shows how a chosen set of stocks and weights would have behaved over the last 3 or 5 years, quantifies the risk of the combination, and compares it with a benchmark. The interface is in Greek.

https://kdkalt.github.io/portfolio-risk-analysis/

## What it does

- **Data:** load daily closing prices from CSV files (one file per stock), or use built-in simulated data for demonstration. Only daily data is accepted; weekly and monthly files are rejected.
- **Portfolio:** set the weight of each stock with sliders. Amounts and a composition chart update immediately.
- **Back-test:** value of the portfolio over the selected period against a benchmark ETF, with the maximum drawdown highlighted.
- **Plain-language summary:** the key results translated into short statements for readers without a technical background.
- **Risk measures:** annualised return, volatility, maximum drawdown, one-day historical Value at Risk (95%) and the Sharpe ratio.
- **Correlations and covariance matrix:** with a check that the volatility computed from the matrix, sigma_p^2 = w'Σw, equals the volatility of the portfolio's return series.
- **Efficient frontier and Capital Market Line:** minimum-variance portfolio, maximum-Sharpe portfolio, with an option to allow short selling.
- **Optimal combination button:** sets the weights to the maximum-Sharpe long-only portfolio.

## Method

- Daily returns r(t) = P(t) / P(t-1) - 1 on the dates common to all files.
- Annualisation with K, the number of observations per year in the window.
- Portfolio return r(p) = sum of w(i) r(i), with constant weights.
- Sharpe ratio = (mu - Rf) / sigma, where mu is the mean daily return times K and Rf is set by the user.
- With short selling allowed, the efficient frontier is computed analytically (Merton, 1972). Without short selling, the frontier is approximated from random portfolios, and the maximum-Sharpe portfolio is found by numerical search.

## How to use it

1. Download daily CSV files, for example from Stooq (`stooq.com/q/d/l/?s=aapl.us&i=d`), and rename each to its ticker (`AAPL.csv`).
2. Open `index.html` in a browser, choose "Real data (CSV)" and upload all files together.
3. Pick one file as the benchmark; it is used for comparison only and is not part of the weights.

No server and no external libraries are required. Data files are not included in this repository; check the data provider's terms of use before redistributing them.

!NOTE!
Download the four CVS files (APPL,JPM,XOM,NASDAC) that are uploaded in the main files of the project and add them to the app so you can view the results that are being analyzed in the last file "Ερμηνεία των αποτελεσμάτων χαρτοφυλακιου"

## Limitations

- Results are based on historical data and describe the past; they are not predictions.
- Expected returns are estimated from the sample and are highly uncertain, which affects the efficient frontier in particular.
- The optimal weights are computed on the same sample on which they are evaluated (in-sample).
- Constant weights, constant risk and correlations, and no transaction costs or taxes are assumed.
- No currency conversion is performed. Amounts are shown in the currency of the price data.
- Adjustment of prices for dividends depends on the data provider.

This project is for educational purposes and is not investment advice.

## References

- Markowitz, H. (1952). Portfolio selection. The Journal of Finance, 7(1), 77–91.
- Merton, R. C. (1972). An analytic derivation of the efficient portfolio frontier. Journal of Financial and Quantitative Analysis, 7(4), 1851–1872.
- Sharpe, W. F. (1964). Capital asset prices: A theory of market equilibrium under conditions of risk. The Journal of Finance, 19(3), 425–442.
- Sharpe, W. F. (1966). Mutual fund performance. The Journal of Business, 39(1, Part 2), 119–138.
- Sharpe, W. F. (1994). The Sharpe ratio. The Journal of Portfolio Management, 21(1), 49–58.

## Author

Dimitrios Kaltapanidis, Department of Economics, University of Macedonia.
