# Portfolio Selection using Pandas

![Portfolio Analysis](Images/portfolio-analysis.png)

## Background

The aim is to help determine which portfolio is performing the best across multiple areas: volatility, returns, risk, and Sharpe ratios.

I have created a tool that analyzes and visualizes the major metrics of the portfolios across all of these areas, and determine which portfolio outperformed the others. I have the historical daily returns of several portfolios: some from the firm's algorithmic portfolios, some that represent the portfolios of famous "whale" investors like Warren Buffett, and some from the big hedge and mutual funds. I have used this analysis to create a custom portfolio of stocks and compare its performance to that of the other portfolios, as well as the larger market ([S&P 500 Index](https://en.wikipedia.org/wiki/S%26P/TSX_60)).

---
### Prepare the Data

First, read and clean several CSV files for analysis. The CSV files include whale portfolio returns, algorithmic trading portfolio returns, and S&P 500 historical prices. Stepss:

1. Use Pandas to read the following CSV files as a DataFrame. Be sure to convert the dates to a `DateTimeIndex`.

    * `whale_returns.csv`: Contains returns of some famous "whale" investors' portfolios.

    * `algo_returns.csv`: Contains returns from the in-house trading algorithms from Harold's company.

    * `sp500_history.csv`: Contains historical closing prices of the S&P 500 Index.

2. Detect and remove null values.

3. If any columns have dollar signs or characters other than numeric values, remove those characters and convert the data types as needed.

4. The whale portfolios and algorithmic portfolio CSV files contain daily returns, but the S&P 500 CSV file contains closing prices. Convert the S&P 500 closing prices to daily returns.

5. Join `Whale Returns`, `Algorithmic Returns`, and the `S&P 500 Returns` into a single DataFrame with columns for each portfolio's returns.

    ![returns-dataframe.png](Images/returns-dataframe.png)

### Conduct Quantitative Analysis

Analyze the data to see if any of the portfolios outperform the stock market (i.e., the S&P 500).

#### Performance Analysis

1. Calculate and plot daily returns of all portfolios.

2. Calculate and plot cumulative returns for all portfolios. Does any portfolio outperform the S&P 500?

#### Risk Analysis

1. Create a box plot for each of the returns. 

2. Calculate the standard deviation for each portfolio. 

3. Determine which portfolios are riskier than the S&P 500.

4. Calculate the Annualized Standard Deviation.

#### Rolling Statistics

1. Calculate and plot the rolling standard deviation for all portfolios using a 21-day window.

2. Calculate and plot the correlation between each stock to determine which portfolios may mimick the S&P 500.

3. Choose one portfolio, then calculate and plot the 60-day rolling beta between it and the S&P 500.

#### Rolling Statistics Challenge: Exponentially Weighted Average

An alternative method to calculate a rolling window is to take the exponentially weighted moving average. This is like a moving window average, but it assigns greater importance to more recent observations. Tried calculating the [`ewm`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.ewm.html) with a 21-day half-life.

### Sharpe Ratios

Investment managers and their institutional investors look at the return-to-risk ratio, not just the returns. 

1. Using the daily returns, calculate and visualize the Sharpe ratios using a bar plot.

2. Determine whether the algorithmic strategies outperform both the market (S&P 500) and the whales portfolios.

### Create a Custom Portfolio

Whether I can choose my own portfolio that performs just as well as the algorithmic portfolios. Investigated by doing the following:

1. Used Google Sheets' built-in Google Finance function to choose 3-5 stocks for my portfolio.

2. Downloaded the data as CSV files and calculate the portfolio returns.

3. Calculated the weighted returns for your portfolio, assuming equal number of shares per stock.

4. Added my portfolio returns to the DataFrame with the other portfolios.

5. Ran the following analyses:

    * Calculate the Annualized Standard Deviation.
    * Calculate and plot rolling `std` with a 21-day window.
    * Calculate and plot the correlation.
    * Calculate and plot beta for your portfolio compared to the S&P 60 TSX.
    * Calculate the Sharpe ratios and generate a bar plot.

4. Analyzed how does my portfolio do?
