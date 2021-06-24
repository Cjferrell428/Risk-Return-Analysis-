# Risk-Return-Analysis-
Challenge 4

Analyzing Portfolio Risk and Return
In this Challenge, you'll assume the role of a quantitative analyst for a FinTech investing platform. This platform aims to offer clients a one-stop online investment solution for their retirement portfolios that’s both inexpensive and high quality. (Think about Wealthfront or Betterment). To keep the costs low, the firm uses algorithms to build each client's portfolio. The algorithms choose from various investment styles and options.

You've been tasked with evaluating four new investment options for inclusion in the client portfolios. Legendary fund and hedge-fund managers run all four selections. (People sometimes refer to these managers as whales, because of the large amount of money that they manage). You’ll need to determine the fund with the most investment potential based on key risk-management metrics: the daily returns, standard deviations, Sharpe ratios, and betas.

Instructions
Import the Data
Use the whale_analysis.ipynb file to complete the following steps:

Import the required libraries and dependencies.

Use the read_csv function and the Path module to read the whale_navs.csv file into a Pandas DataFrame. Be sure to create a DateTimeIndex. Review the first five rows of the DataFrame by using the head function.

Use the Pandas pct_change function together with dropna to create the daily returns DataFrame. Base this DataFrame on the NAV prices of the four portfolios and on the closing price of the S&P 500 Index. Review the first five rows of the daily returns DataFrame.

Analyze the Performance
Analyze the data to determine if any of the portfolios outperform the broader stock market, which the S&P 500 represents. To do so, complete the following steps:

Use the default Pandas plot function to visualize the daily return data of the four fund portfolios and the S&P 500. Be sure to include the title parameter, and adjust the figure size if necessary.

Use the Pandas cumprod function to calculate the cumulative returns for the four fund portfolios and the S&P 500. Review the last five rows of the cumulative returns DataFrame by using the Pandas tail function.

Use the default Pandas plot to visualize the cumulative return values for the four funds and the S&P 500 over time. Be sure to include the title parameter, and adjust the figure size if necessary.

Answer the following question: Based on the cumulative return data and the visualization, do any of the four fund portfolios outperform the S&P 500 Index?

Analyze the Volatility
Analyze the volatility of each of the four fund portfolios and of the S&P 500 Index by using box plots. To do so, complete the following steps:

Use the Pandas plot function and the kind="box" parameter to visualize the daily return data for each of the four portfolios and for the S&P 500 in a box plot. Be sure to include the title parameter, and adjust the figure size if necessary.

Use the Pandas drop function to create a new DataFrame that contains the data for just the four fund portfolios by dropping the S&P 500 column. Visualize the daily return data for just the four fund portfolios by using another box plot. Be sure to include the title parameter, and adjust the figure size if necessary.

Hint Save this new DataFrame—the one that contains the data for just the four fund portfolios. You’ll use it throughout the analysis.

Answer the following question: Based on the box plot visualization of just the four fund portfolios, which fund was the most volatile (with the greatest spread) and which was the least volatile (with the smallest spread)?

Analyze the Risk
Evaluate the risk profile of each portfolio by using the standard deviation and the beta. To do so, complete the following steps:

Use the Pandas std function to calculate the standard deviation for each of the four portfolios and for the S&P 500. Review the standard deviation calculations, sorted from smallest to largest.

Calculate the annualized standard deviation for each of the four portfolios and for the S&P 500. To do that, multiply the standard deviation by the square root of the number of trading days. Use 252 for that number.

Use the daily returns DataFrame and a 21-day rolling window to plot the rolling standard deviations of the four fund portfolios and of the S&P 500 index. Be sure to include the title parameter, and adjust the figure size if necessary.

Use the daily returns DataFrame and a 21-day rolling window to plot the rolling standard deviations of only the four fund portfolios. Be sure to include the title parameter, and adjust the figure size if necessary.

Answer the following three questions:

Based on the annualized standard deviation, which portfolios pose more risk than the S&P 500?

Based on the rolling metrics, does the risk of each portfolio increase at the same time that the risk of the S&P 500 increases?

Based on the rolling standard deviations of only the four fund portfolios, which portfolio poses the most risk? Does this change over time?

Analyze the Risk-Return Profile
To determine the overall risk of an asset or portfolio, quantitative analysts and investment managers consider not only its risk metrics but also its risk-return profile. After all, if you have two portfolios that each offer a 10% return but one has less risk, you’d probably invest in the smaller-risk portfolio. For this reason, you need to consider the Sharpe ratios for each portfolio. To do so, complete the following steps:

Use the daily return DataFrame to calculate the annualized average return data for the four fund portfolios and for the S&P 500. Use 252 for the number of trading days. Review the annualized average returns, sorted from lowest to highest.

Calculate the Sharpe ratios for the four fund portfolios and for the S&P 500. To do that, divide the annualized average return by the annualized standard deviation for each. Review the resulting Sharpe ratios, sorted from lowest to highest.

Visualize the Sharpe ratios for the four funds and for the S&P 500 in a bar chart. Be sure to include the title parameter, and adjust the figure size if necessary.

Answer the following question: Which of the four portfolios offers the best risk-return profile? Which offers the worst?

Diversify the Portfolio
Your analysis is nearing completion. Now, you need to evaluate how the portfolios react relative to the broader market. Based on your analysis so far, choose two portfolios that you’re most likely to recommend as investment options. To start your analysis, complete the following step:

Use the Pandas var function to calculate the variance of the S&P 500 by using a 60-day rolling window. Visualize the last five rows of the variance of the S&P 500.
Next, for each of the two portfolios that you chose, complete the following steps:

Using the 60-day rolling window, the daily return data, and the S&P 500 returns, calculate the covariance. Review the last five rows of the covariance of the portfolio.

Calculate the beta of the portfolio. To do that, divide the covariance of the portfolio by the variance of the S&P 500.

Use the Pandas mean function to calculate the average value of the 60-day rolling beta of the portfolio.

Plot the 60-day rolling beta. Be sure to include the title parameter, and adjust the figure size if necessary.

Finally, answer the following two questions:

Which of the two portfolios seem more sensitive to movements in the S&P 500?

Which of the two portfolios do you recommend for inclusion in your firm’s suite of fund offerings?

Import the Data
Step 1: Import the required libraries and dependencies.
import pandas as pd
from pathlib import Path
import numpy as np
%matplotlib inline
# Import the required libraries and dependencies
import pandas as pd
from pathlib import Path
import numpy as np
%matplotlib inline
​
Step 2: Use the read_csv function and the Path module to read the whale_navs.csv file into a Pandas DataFrame. Be sure to create a DateTimeIndex. Review the first five rows of the DataFrame by using the head function.
csvpath = Path("../Python_Project/whale_navs") 
whale_navs_df = pd.read_csv(
    Path("../Python_Project/whale_navs.csv"),
    index_col='date', 
    parse_dates=True, 
    infer_datetime_format=True)
# Import the data by reading in the CSV file and setting the DatetimeIndex 
# Review the first 5 rows of the DataFrame
csvpath = Path("../Python_Project/whale_navs") 
whale_navs_df = pd.read_csv(
    Path("../Python_Project/whale_navs.csv"),
    index_col='date', 
    parse_dates=True, 
    infer_datetime_format=True)
whale_navs_df.head()
​
SOROS FUND MANAGEMENT LLC	PAULSON & CO.INC.	TIGER GLOBAL MANAGEMENT LLC	BERKSHIRE HATHAWAY INC	S&P 500
date					
2014-10-01	31.950240	14.991826	59.977830	51.948712	194.35
2014-10-02	31.936110	14.994072	59.978626	51.957619	194.38
2014-10-03	31.969707	14.999596	60.002264	52.022484	196.52
2014-10-06	32.048215	14.999471	60.006244	52.036387	196.29
2014-10-07	31.964216	14.994720	59.993735	52.005864	193.26
Step 3: Use the Pandas pct_change function together with dropna to create the daily returns DataFrame. Base this DataFrame on the NAV prices of the four portfolios and on the closing price of the S&P 500 Index. Review the first five rows of the daily returns DataFrame.
# Prepare for the analysis by converting the dataframe of NAVs and prices to daily returns
# Drop any rows with all missing values
# Review the first five rows of the daily returns DataFrame.
daily_returns = whale_navs_df.pct_change()
daily_returns.head(5).dropna() #dropped the na values but still included the first 5 rows
​
SOROS FUND MANAGEMENT LLC	PAULSON & CO.INC.	TIGER GLOBAL MANAGEMENT LLC	BERKSHIRE HATHAWAY INC	S&P 500
date					
2014-10-02	-0.000442	0.000150	0.000013	0.000171	0.000154
2014-10-03	0.001052	0.000368	0.000394	0.001248	0.011009
2014-10-06	0.002456	-0.000008	0.000066	0.000267	-0.001170
2014-10-07	-0.002621	-0.000317	-0.000208	-0.000587	-0.015436
Quantative Analysis
The analysis has several components: performance, volatility, risk, risk-return profile, and portfolio diversification. You’ll analyze each component one at a time.

Analyze the Performance
Analyze the data to determine if any of the portfolios outperform the broader stock market, which the S&P 500 represents.

Step 1: Use the default Pandas plot function to visualize the daily return data of the four fund portfolios and the S&P 500. Be sure to include the title parameter, and adjust the figure size if necessary.
# Plot the daily return data of the 4 funds and the S&P 500 
# Inclue a title parameter and adjust the figure size
daily_returns.plot(figsize = (20, 14), title = "Daily Returns of Four Fund Portfolios")
​
<AxesSubplot:title={'center':'Daily Returns of Four Fund Portfolios'}, xlabel='date'>

Step 2: Use the Pandas cumprod function to calculate the cumulative returns for the four fund portfolios and the S&P 500. Review the last five rows of the cumulative returns DataFrame by using the Pandas tail function.
# Calculate and plot the cumulative returns of the 4 fund portfolios and the S&P 500
# Review the last 5 rows of the cumulative returns DataFrame
cumulative_returns = (1 + daily_returns).cumprod()
cumulative_returns.tail()
​
SOROS FUND MANAGEMENT LLC	PAULSON & CO.INC.	TIGER GLOBAL MANAGEMENT LLC	BERKSHIRE HATHAWAY INC	S&P 500
date					
2020-09-04	0.987355	0.958187	1.055714	1.244856	1.762645
2020-09-08	0.985640	0.956378	1.054373	1.238608	1.714484
2020-09-09	0.986739	0.958409	1.057221	1.240858	1.748341
2020-09-10	0.985498	0.959740	1.055539	1.237883	1.717983
2020-09-11	0.985086	0.957887	1.055081	1.236625	1.718858
Step 3: Use the default Pandas plot to visualize the cumulative return values for the four funds and the S&P 500 over time. Be sure to include the title parameter, and adjust the figure size if necessary.
# Visualize the cumulative returns using the Pandas plot function
# Include a title parameter and adjust the figure size
cumulative_returns.plot(figsize = (20, 10), title = "Cumulative Returns of Four Funds and S&P")
​
<AxesSubplot:title={'center':'Cumulative Returns of Four Funds and S&P'}, xlabel='date'>

Step 4: Answer the following question: Based on the cumulative return data and the visualization, do any of the four fund portfolios outperform the S&P 500 Index?
Question Based on the cumulative return data and the visualization, do any of the four fund portfolios outperform the S&P 500 Index?

Answer Bassed on the cumulative return data none of the fund portfolios outperform the S&P 500 index. The only couple days of the month that the four fund portfolios outperformed the S&P 500 index was early 2015, late 2015, and early 2016. Other than those time periods the S&P 500 has outperformed the four other funds.

Analyze the Volatility
Analyze the volatility of each of the four fund portfolios and of the S&P 500 Index by using box plots.

Step 1: Use the Pandas plot function and the kind="box" parameter to visualize the daily return data for each of the four portfolios and for the S&P 500 in a box plot. Be sure to include the title parameter, and adjust the figure size if necessary.
# Use the daily return data to create box plots to visualize the volatility of the 4 funds and the S&P 500 
# Include a title parameter and adjust the figure size
daily_returns.plot(kind="box", figsize = (20,10), title = "Four Funds Daily Return & S&P 500")
​
<AxesSubplot:title={'center':'Four Funds Daily Return & S&P 500'}>

Step 2: Use the Pandas drop function to create a new DataFrame that contains the data for just the four fund portfolios by dropping the S&P 500 column. Visualize the daily return data for just the four fund portfolios by using another box plot. Be sure to include the title parameter, and adjust the figure size if necessary.
# Create a new DataFrame containing only the 4 fund portfolios by dropping the S&P 500 column from the DataFrame
four_daily_returns = daily_returns.drop(labels="S&P 500", axis=1)
four_daily_returns.head(6).dropna() #Used the drop function to remove S&P column and drop na function to get rid of all na data.
​
# Create box plots to reflect the return data for only the 4 fund portfolios
# Include a title parameter and adjust the figure size
four_daily_returns.plot(kind="box", figsize = (20,10), title = "Four Funds Daily Return")
​
<AxesSubplot:title={'center':'Four Funds Daily Return'}>

Step 3: Answer the following question: Based on the box plot visualization of just the four fund portfolios, which fund was the most volatile (with the greatest spread) and which was the least volatile (with the smallest spread)?
Question Based on the box plot visualization of just the four fund portfolios, which fund was the most volatile (with the greatest spread) and which was the least volatile (with the smallest spread)?

Answer The most volatile fund was the Berkshire Hathaway Inc. fund. It had the widest range of daily returns and the largest box on the plot. The least volatile fund was the Tiger Global Management LLC fund. It had the smallest range of daily returns and the smallest box on the plot.

Analyze the Risk
Evaluate the risk profile of each portfolio by using the standard deviation and the beta.

Step 1: Use the Pandas std function to calculate the standard deviation for each of the four portfolios and for the S&P 500. Review the standard deviation calculations, sorted from smallest to largest.
# Calculate and sort the standard deviation for all 4 portfolios and the S&P 500
# Review the standard deviations sorted smallest to largest
standard_deviation = daily_returns.std()
standard_deviation_sorted = standard_deviation.sort_values()
standard_deviation_sorted
​
TIGER GLOBAL MANAGEMENT LLC    0.000996
SOROS FUND MANAGEMENT LLC      0.001405
PAULSON & CO.INC.              0.002199
BERKSHIRE HATHAWAY INC         0.003256
S&P 500                        0.011550
dtype: float64
Step 2: Calculate the annualized standard deviation for each of the four portfolios and for the S&P 500. To do that, multiply the standard deviation by the square root of the number of trading days. Use 252 for that number.
# Calculate and sort the annualized standard deviation (252 trading days) of the 4 portfolios and the S&P 500
# Review the annual standard deviations smallest to largest
annualized_standard_deviation = standard_deviation * np.sqrt(252)
annualized_standard_deviation.sort_values()
​
TIGER GLOBAL MANAGEMENT LLC    0.015804
SOROS FUND MANAGEMENT LLC      0.022297
PAULSON & CO.INC.              0.034912
BERKSHIRE HATHAWAY INC         0.051692
S&P 500                        0.183345
dtype: float64
Step 3: Use the daily returns DataFrame and a 21-day rolling window to plot the rolling standard deviations of the four fund portfolios and of the S&P 500 index. Be sure to include the title parameter, and adjust the figure size if necessary.
# Using the daily returns DataFrame and a 21-day rolling window, 
# plot the rolling standard deviation of the 4 portfolios and the S&P 500
# Include a title parameter and adjust the figure size
daily_returns.rolling(21).std().plot(figsize=(18,12), title='Rolling Std Dev Four Funds & S&P 500')
​
<AxesSubplot:title={'center':'Rolling Std Dev Four Funds & S&P 500'}, xlabel='date'>

Step 4: Use the daily returns DataFrame and a 21-day rolling window to plot the rolling standard deviations of only the four fund portfolios. Be sure to include the title parameter, and adjust the figure size if necessary.
# Using the daily return data and a 21-day rolling window, plot the rolling standard deviation of just the 4 portfolios. 
# Include a title parameter and adjust the figure size
four_std_rolling = daily_returns.drop(labels="S&P 500", axis=1)
four_std_rolling.rolling(21).std().plot(figsize=(18,12), title='Rolling Std Dev Four Funds')
<AxesSubplot:title={'center':'Rolling Std Dev Four Funds'}, xlabel='date'>

Step 5: Answer the following three questions:
Based on the annualized standard deviation, which portfolios pose more risk than the S&P 500?

Based on the rolling metrics, does the risk of each portfolio increase at the same time that the risk of the S&P 500 increases?

Based on the rolling standard deviations of only the four fund portfolios, which portfolio poses the most risk? Does this change over time?

Question 1 Based on the annualized standard deviation, which portfolios pose more risk than the S&P 500?

Answer 1 None of the portfolios pose more risk than the S&P 500. The S&P has the highest standard deviation which tells us that the data price points tend to be spread out over a wide range of values. Which poses the most risk. While the S&P poses the most risk Berkshire Hathaway has the second largest standard deviation.

Question 2 Based on the rolling metrics, does the risk of each portfolio increase at the same time that the risk of the S&P 500 increases?

Answer 2 The rolling mettrics shows that the risk of each portfolio does not increase at the same time as the S&P 500. The only time it shows that the risk increases at the same rate as the S&P 500 is in the last two years of 2019 and 2020. Other than those two years the risk of each porfolio does not follow the S&P 500s trend.

Question 3 Based on the rolling standard deviations of only the four fund portfolios, which portfolio poses the most risk? Does this change over time?

Answer 3 Berkshire Hathway Inc has the most risk but it changes over time. From mid 2016 to 2019 Berkshire has the most risk. From 2015 to late 2016 other portfolios have more risk than that of Berkshire. Then in 2019 Berkshire and Paulsen and Co. tradeoff for the most risk.

Analyze the Risk-Return Profile
To determine the overall risk of an asset or portfolio, quantitative analysts and investment managers consider not only its risk metrics but also its risk-return profile. After all, if you have two portfolios that each offer a 10% return but one has less risk, you’d probably invest in the smaller-risk portfolio. For this reason, you need to consider the Sharpe ratios for each portfolio.

Step 1: Use the daily return DataFrame to calculate the annualized average return data for the four fund portfolios and for the S&P 500. Use 252 for the number of trading days. Review the annualized average returns, sorted from lowest to highest.
# Calculate the annual average return data for the for fund portfolios and the S&P 500
# Use 252 as the number of trading days in the year
# Review the annual average returns sorted from lowest to highest
year_trading_days = 252
average_annual_return = daily_returns.mean() * year_trading_days
average_annual_return
​
SOROS FUND MANAGEMENT LLC     -0.002281
PAULSON & CO.INC.             -0.006633
TIGER GLOBAL MANAGEMENT LLC    0.009151
BERKSHIRE HATHAWAY INC         0.037090
S&P 500                        0.108102
dtype: float64
Step 2: Calculate the Sharpe ratios for the four fund portfolios and for the S&P 500. To do that, divide the annualized average return by the annualized standard deviation for each. Review the resulting Sharpe ratios, sorted from lowest to highest.
# Calculate the annualized Sharpe Ratios for each of the 4 portfolios and the S&P 500.
# Review the Sharpe ratios sorted lowest to highest
annual_std_dev_portfolios = daily_returns.std() * np.sqrt(year_trading_days)
sharpe_ratios = average_annual_return / annual_std_dev_portfolios
sharpe_ratios.sort_values()
​
PAULSON & CO.INC.             -0.189998
SOROS FUND MANAGEMENT LLC     -0.102290
TIGER GLOBAL MANAGEMENT LLC    0.579002
S&P 500                        0.589612
BERKSHIRE HATHAWAY INC         0.717512
dtype: float64
Step 3: Visualize the Sharpe ratios for the four funds and for the S&P 500 in a bar chart. Be sure to include the title parameter, and adjust the figure size if necessary.
# Visualize the Sharpe ratios as a bar chart
# Include a title parameter and adjust the figure size
sharpe_ratios.plot.bar(title="Sharpe Ratios")
​
<AxesSubplot:title={'center':'Sharpe Ratios'}>

Step 4: Answer the following question: Which of the four portfolios offers the best risk-return profile? Which offers the worst?
Question Which of the four portfolios offers the best risk-return profile? Which offers the worst?

Answer Berkshire Hathaway represents the best risk return profile. Paulson & Co. inc offers the worst risk return profile.

Diversify the Portfolio
Your analysis is nearing completion. Now, you need to evaluate how the portfolios react relative to the broader market. Based on your analysis so far, choose two portfolios that you’re most likely to recommend as investment options.

Use the Pandas var function to calculate the variance of the S&P 500 by using a 60-day rolling window. Visualize the last five rows of the variance of the S&P 500.
# Calculate the variance of the S&P 500 using a rolling 60-day window.
daily_returns.loc[:, "S&P 500"].rolling(60).var().tail()
date
2020-09-04    0.000103
2020-09-08    0.000116
2020-09-09    0.000120
2020-09-10    0.000121
2020-09-11    0.000120
Name: S&P 500, dtype: float64
For each of the two portfolios that you chose, complete the following steps:
Using the 60-day rolling window, the daily return data, and the S&P 500 returns, calculate the covariance. Review the last five rows of the covariance of the portfolio.

Calculate the beta of the portfolio. To do that, divide the covariance of the portfolio by the variance of the S&P 500.

Use the Pandas mean function to calculate the average value of the 60-day rolling beta of the portfolio.

Plot the 60-day rolling beta. Be sure to include the title parameter, and adjust the figure size if necessary.

Portfolio 1 - Step 1: Using the 60-day rolling window, the daily return data, and the S&P 500 returns, calculate the covariance. Review the last five rows of the covariance of the portfolio.
rolling_soros_covariance = daily_returns['SOROS FUND MANAGEMENT LLC'].rolling(window=60).cov(daily_returns['S&P 500'])
rolling_soros_covariance.tail()
# Calculate the covariance using a 60-day rolling window 
# Review the last five rows of the covariance data
rolling_soros_covariance = daily_returns['SOROS FUND MANAGEMENT LLC'].rolling(window=60).cov(daily_returns['S&P 500'])
rolling_soros_covariance.tail()
​
date
2020-09-04    0.000009
2020-09-08    0.000010
2020-09-09    0.000010
2020-09-10    0.000010
2020-09-11    0.000010
dtype: float64
Portfolio 1 - Step 2: Calculate the beta of the portfolio. To do that, divide the covariance of the portfolio by the variance of the S&P 500.
rolling_variance = daily_returns['S&P 500'].rolling(window=60).var()
portfolio_beta_soros = rolling_soros_covariance / rolling_variance
portfolio_beta_soros.dropna()
# Calculate the beta based on the 60-day rolling covariance compared to the market (S&P 500)
# Review the last five rows of the beta information
rolling_variance = daily_returns['S&P 500'].rolling(window=60).var()
portfolio_beta_soros = rolling_soros_covariance / rolling_variance
portfolio_beta_soros.dropna()
date
2014-12-26    0.118895
2014-12-29    0.118847
2014-12-30    0.118225
2014-12-31    0.118379
2015-01-02    0.116288
                ...   
2020-09-04    0.086995
2020-09-08    0.084035
2020-09-09    0.081876
2020-09-10    0.082832
2020-09-11    0.082554
Length: 1438, dtype: float64
Portfolio 1 - Step 3: Use the Pandas mean function to calculate the average value of the 60-day rolling beta of the portfolio.
portfolio_beta_soros.rolling(window=60).mean()
portfolio_beta_soros.dropna()
# Calculate the average of the 60-day rolling beta
portfolio_beta_soros.rolling(window=60).mean()
portfolio_beta_soros.dropna()
​
date
2014-12-26    0.118895
2014-12-29    0.118847
2014-12-30    0.118225
2014-12-31    0.118379
2015-01-02    0.116288
                ...   
2020-09-04    0.086995
2020-09-08    0.084035
2020-09-09    0.081876
2020-09-10    0.082832
2020-09-11    0.082554
Length: 1438, dtype: float64
Portfolio 1 - Step 4: Plot the 60-day rolling beta. Be sure to include the title parameter, and adjust the figure size if necessary.
portfolio_beta_soros.plot(figsize=(40, 20), title='Rolling 60-Day Beta of S&P and SOROS Fund')
# Plot the rolling beta 
portfolio_beta_soros.plot(figsize=(40, 20), title='Rolling 60-Day Beta of S&P and SOROS Fund')
​
​
​
<AxesSubplot:title={'center':'Rolling 60-Day Beta of S&P and SOROS Fund'}, xlabel='date'>

Portfolio 2 - Step 1: Using the 60-day rolling window, the daily return data, and the S&P 500 returns, calculate the covariance. Review the last five rows of the covariance of the portfolio.
# Calculate the covariance using a 60-day rolling window 
rolling_paulson_covariance = daily_returns['PAULSON & CO.INC.'].rolling(window=60).cov(daily_returns['S&P 500'])
rolling_paulson_covariance.tail()
​
​
date
2020-09-04    0.000009
2020-09-08    0.000010
2020-09-09    0.000010
2020-09-10    0.000010
2020-09-11    0.000010
dtype: float64
Portfolio 2 - Step 2: Calculate the beta of the portfolio. To do that, divide the covariance of the portfolio by the variance of the S&P 500.
# Calculate the beta based on the 60-day rolling covariance compared to the market (S&P 500)
# Review the last five rows of the beta information
rolling_variance = daily_returns['S&P 500'].rolling(window=60).var()
portfolio_beta_paulson = rolling_paulson_covariance / rolling_variance
portfolio_beta_paulson.dropna()
​
date
2014-12-26    0.022059
2014-12-29    0.022093
2014-12-30    0.021744
2014-12-31    0.022079
2015-01-02    0.022176
                ...   
2020-09-04    0.085217
2020-09-08    0.087760
2020-09-09    0.084976
2020-09-10    0.084373
2020-09-11    0.083657
Length: 1438, dtype: float64
Portfolio 2 - Step 3: Use the Pandas mean function to calculate the average value of the 60-day rolling beta of the portfolio.
# Calculate the average of the 60-day rolling beta
portfolio_beta_paulson.rolling(window=60).mean()
portfolio_beta_paulson.dropna()
​
date
2014-12-26    0.022059
2014-12-29    0.022093
2014-12-30    0.021744
2014-12-31    0.022079
2015-01-02    0.022176
                ...   
2020-09-04    0.085217
2020-09-08    0.087760
2020-09-09    0.084976
2020-09-10    0.084373
2020-09-11    0.083657
Length: 1438, dtype: float64
Portfolio 2 - Step 4: Plot the 60-day rolling beta. Be sure to include the title parameter, and adjust the figure size if necessary.
# Plot the rolling beta 
# Include a title parameter and adjust the figure size
portfolio_beta_paulson.plot(figsize=(40, 20), title='Rolling 60-Day Beta of S&P and PAULSON Fund')
​
<AxesSubplot:title={'center':'Rolling 60-Day Beta of S&P and PAULSON Fund'}, xlabel='date'>

Answer the following two questions:
Which of the two portfolios seem more sensitive to movements in the S&P 500?

Which of the two portfolios do you recommend for inclusion in your firm’s suite of fund offerings?

Question 1 Which of the two portfolios seem more sensitive to movements in the S&P 500?

Answer 1 The Soros portfolio looks to be more sensitive to movements in the S&P 500. Throughout the six years it tends to drop and rise constantly with the market while the Paulson fund remains somewhat constant until the end of the data set.

Question 2 Which of the two portfolios do you recommend for inclusion in your firm’s suite of fund offerings?

Answer 2 I would recomend the Paulson fund for two reasons. The Beta remained somewhat constant in the data set early on, and the cumulative returns over the data set for Paulson performed better than the soros fund.
