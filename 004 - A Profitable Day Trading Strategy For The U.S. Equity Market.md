# Swiss Finance Institute Research Paper Series N°24-98

A Profitable Day Trading Strategy for The U.S. Equity Market 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/6c7a3163-41e3-4a71-8be4-7d39021cc21c/e42137811bb2260b641684f74f18f4b9754fc4b6f0521c1a9f1ea83151fd1ed8.jpg)


Carlo Zarattini Concretum Research Lugano 

Andrea Barbon University of St.Gallen and Swiss Finance Institute 

Andrew Aziz Peak Capital Trading and Bear Bull Traders, Canada 

# A Profitable Day Trading Strategy For The U.S. Equity Market

Carlo Zarattini<sup>1</sup>, Andrea Barbon<sup>2</sup>, Andrew Aziz<sup>3,4</sup> 

<sup>1</sup>Concretum Research, Viale Carlo Cattaneo 1, 6900 Lugano, Switzerland <sup>2</sup>University of St.Gallen, Dufourstrasse 50, 9000 St. Gallen, Switzerland <sup>3</sup>Peak Capital Trading, 744 West Hastings Street, Vancouver, BC, Canada V6C 1A5 <sup>4</sup>Bear Bull Traders, 744 West Hastings Street, Vancouver, BC, Canada V6C 1A5 

Q <sup>1</sup>carlo@concretumgroup.com, <sup>2</sup>andrea.barbon@unisg.ch, <sup>4</sup>andrew@peakcapitaltrading.com X: <sup>1</sup>@ConcretumR,<sup>2</sup>@Andrea Barbon,<sup>3</sup>@BearBullTraders , 

First Version: February 16, 2024 

## Abstract

The validity of day trading as a long-term consistent and uncorrelated source of income for traders and investors is a matter of debate. In this paper, we endeavored to answer this question by conducting a thorough analysis of the profitability of Opening Range Breakout (ORB) strategies, with a particular focus on the 5- minute ORB. Using a large dataset that covered more than 7,000 US stocks traded from 2016 to 2023, the research aimed to assess how efective this strategy was in producing consistent and uncorrelated returns. A new aspect of our study was the focus on Stocks in Play, which are stocks that show higher than normal trading activity on a specific day, mostly because of fundamental news about the company. Our results showed a significant benefit in limiting day trading only to those Stocks in Play (even after considering transaction costs). A portfolio that consisted of the top 20 Stocks in Play achieved a total net performance of over 1,600%, with a Sharpe ratio of 2.81, and an annualized alpha of 36%. Passive exposure in the S&P 500 would have achieved a total return of 198% during the same period. Furthermore, this paper expanded the analysis to compare the return profile of the ORB strategy applied to diferent time frames, such as 15, 30, and 60 minutes. In the last part of the paper, we presented detailed stock-specific statistics for the 25 best and worst performers of an ORB strategy over all the time frames. To the best of our knowledge, this is the first public paper with such intraday granularity and comprehensive stock-level database. 

Keywords: Day Trading, Day Trading Systems, Opening Range Breakout, Algo Trading, Stock in Play, News Trading 

## 1 Introduction

Until the mid-2000s, the financial markets were largely the playground of Wall Street professionals. With the advent of advanced trading technologies, a flood of information on trading strategies, and the rise of afordable, even free, brokerage services, the landscape shifted dramatically. Now, the majority of Main Street are actively engaging with financial markets. In 2023, 61% of adults in the United States invested in the stock market directly [1]. The 2020 pandemic served as a catalyst in this transformation. Lockdowns and market volatility sparked a surge in retail trading, especially in the stock market [17, 9, 14]. A landmark event was the 2021 GameStop (GME) short squeeze, an extraordinary David vs. Goliath tale where retail traders triumphed over Wall Street giants, leading to the dissolution of some professional trading firms [3]. This event symbolized the unleashed power of retail trading, a genie that is definitely not going back in the bottle. 

Most retail traders gravitate toward day trading or short-term swing trades. But there is a daunting challenge for retail traders who are competing with high-frequency trading (HFT) algorithms. They need access to proven strategies that can give them an edge and consistent advantage in the markets, often with technical analysis. Our previous research had been focused on informing retail traders [22] and developing, testing, and refining day trading strategies that are useful for retail traders without access to the lowest commission tiers or HFT capabilities [24, 23]. 

Over the years, technical traders have developed and documented hundreds of trading systems. Among them, one of the most important and well-studied strategy that has gained considerable attention is the n-minute ORB, with popular variants including 5- minute, 15-minute, 30-minute and 60-minute time frames. As shown conceptually in Figure 1, the ORB strategy typically focuses on identifying the highest and lowest prices during the first n-minutes of trading, and then buying or selling when the stock breaks out of this range only in the direction of the opening range. For instance, a positive open suggests a long position upon breaking the high, while a negative open indicates a short position upon breaking the low. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/6c7a3163-41e3-4a71-8be4-7d39021cc21c/1379f5bbb415ec9f9c1ab5003759edb9a31368d17c897a30e86c582ce02c3cc7.jpg)



Figure 1: Conceptual illustrations of where a trader would enter into a trade using the ORB strategy for going long (as shown on the left-hand side) and for going short (as shown on the right-hand side).


Toby Crabel is often credited with first introducing the ORB (back in 1990)[11]. In his book, Day Trading with Short Term Price Patterns and Opening Range Breakout, which was one of the earliest and most detailed descriptions of how to trade short-term price patterns across markets, he extensively analyzed the profitability of volatility breakout strategies across various futures markets. In his model, the range was calibrated combining previous days’ volatility with current opening prices. The strategy did not use any intraday data information to define the opening range. In the book, Crabel detailed his core trading philosophy, that any robust trading strategy should capture explainable market participant behavior. Traders must understand the mass psychology of the traders behind the price action. Essentially, traders are social psychologists behind a computer program [12]. 

Over the years, the ORB strategy has been studied and documented significantly both by market participants [23, 4, 2, 10, 15] and academia [8, 18, 13, 21, 19, 16]. In 1995, Raschke and Connors [10] introduced the Momentum Pinball strategy, a model that improves the ORB strategy by combining a 60-minute ORB with a 3-day Relative Strength Index (RSI) of a 1-day rate of change. Their study was tested on diferent futures markets, but the authors suggested that the same methodology could have been applied to common equity markets. 

In his seminal work in 1992, Brock et al. [8] demonstrated the efectiveness of simple technical trading rules, specifically the moving average and ORBs, applied on almost 100 years of Dow Jones Index data. His findings were pivotal in challenging the random walk hypothesis, a financial theory stating that stock market prices evolve according to a random walk and thus cannot be predicted, and emphasized the potential of technical analysis strategies in market prediction. In 2009, Schulmeister [18] focused on the frequency of data in technical trading. By analyzing S&P 500 data from 1960 to 2000, and the futures market from 1983 to 2000, Schulmeister demonstrated that models using 30-minute interval data were more profitable than those relying on daily data, suggesting a shift toward higher frequency trading in technical analysis. 

In 2012, Holmberg et al. [13] studied the profitability of volatility ORBs on US crude oil futures prices from 1983 until 2011. Their results showed that a volatility ORB was significantly profitable, but the profitability was mostly generated in the last decade (2000-2011). In 2018, Tsai et al. [19] further expanded the research on ORB strategies by assessing their performance across multiple indices (Dow Jones Industrial Average, S&P 500, and Nasdaq) and for diferent opening range time frames. The results showed that the most significant profits occur when the opening range length is within 5 minutes from the open. Their research did not consider any profit target or stop loss mechanisms. 

In 2017, Lundstr¨om [16] examined ORB returns in diferent volatility states based on long-term crude oil data and S&P 500 futures contracts, and he found that the profitability of ORB grows with the volatility of the underlyng asset. 

To improve the system and generate larger returns compared to the overall market, Wu et al. in 2020 introduced an evolutionary approach by utilizing a genetic algorithm in their ORB-based model [21]. Their method optimized thresholds and protective closing strategies, significantly enhancing profitability and reducing risks. This study was conducted on Taiwan Index Futures between 2007 and 2018 and showed that the introduction of a profit target is detrimental for overall profitability. The study showed enhanced profitability once a stop loss mechanism was introduced. 

Recently, we provided significant evidence of profitability for a 5-minute ORB applied on QQQ and TQQQ ETFs [23]. We introduced the use of stop losses and large profit targets and found that a 5-minute ORB on TQQQ would have earned an outstanding return of 1,484% between 2016 and 2023, while a passive investment in the QQQ ETF would have earned only 169%. 

In this paper, our goal was to apply the 5-minute ORB framework developed in our previous work [23], but instead of utilizing only QQQ or TQQQ, we expanded the study to all US stocks traded between 2016 and 2023, and assessed if trading volume and other parameters have any statistically meaningful forecasting power on day trading profitability. 

## 2 Strategy Definition

As previously referenced, a 5-minute ORB strategy is a trading strategy that focuses on catching a breakout from the initial range in the first 5 minutes of the trading day [23, 4, 5]. In this current work, we introduced a crucial parameter to this ORB strategy. If the first 5-minute candlestick was bearish (meaning it closed below its opening price), our system would only take a short position. We would not go for a long position even if the price broke above the 5-minute opening range candlestick. Similarly, if the first 5-minute candlestick was bullish (meaning it closed above the opening price), we would stick to taking only a long position. We would avoid taking a short position, even if the price dropped below the 5-minute opening range candlestick [23]. 

The opening range is often thought to provide some useful insight about the institutional supply and demand imbalance that will prevail throughout the day. Day traders typically employ tight stop losses to maximize exposure to intraday trends, letting profits run as long as the trend persists. Setting the right stop loss is crucial and can really make or break a trading strategy. If you set your stop loss too close to your entry point, you might get stopped out too soon or too often. This can lead to missing out on big moves, rack ing up small losses, and paying higher commissions and fees. On the other hand, a stop loss that is too wide could lead to bigger losses and unsatisfactory levels of reward to risk. 

Traders have diferent ways of setting stop losses. Some use technical tools like moving averages, VWAP (Volume Weighted Average Price) or other mathematical indicators [24]. Others prefer to set them based on judgment calls, using key levels like the low or high of the day. A common approach [24, 4] is to set the stop loss at a percentage of the 14-day average true range (ATR)<sup>1</sup>. 

For example, as shown in Figure 2, the daily ATR of a company called BLDR on January 22, 2024 was $5. The following day the stock dipped in the first 5 minutes, prompting a sell stop order at the opening range’s low ($174.44). Half an hour later, the stock breached this level, executing the order. The stop loss was set at 10% of the daily ATR (10% x $5 = $0.50) from the entry point. We have previously looked into how using a stop loss based on ATR afects the ORB strategy and found a link between the expected value of the return and the stop loss [23]. 

To analyze the result, Profit & Loss (PnL) is often quantified in units of risk (R) rather than in dollar value. Figure 2 shows an example of howR unit is utilized in trade management and analysis. In this case, a short trade was triggered, and the R was the potential maximum loss per share, which was $0.50. The profit target was set at the end of the day (EoD). The trade’s per share movement was $6.81 ($174.44 - $167.63), translating to a PnL of 13.62 times the R, or 13.62R ($6.81/0.50). 

The US stocks analyzed in this study encompassed all equities listed on US exchanges (both NYSE and Nasdaq) from January 1, 2016 to December 31, 2023 (we called them the universe. This universe comprised approximately 7,000 stocks and was free from 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/6c7a3163-41e3-4a71-8be4-7d39021cc21c/fa30a054604df69ec9862d255fa9ae278f0c0e5bb2cf627abc815254693fab00.jpg)



Figure 2: A hypothetical example of the 5-minute ORB strategy discussed in this paper on Builders FirstSource, Inc. (BLDR) on 23 Jan 2024, detailing entry, exit, and stop loss points. The first 5 min candlestick is red therefore no long position is allowed to be triggered. Only a short position is allowed to trigger. The entry is triggered at 10am and a stop is added at 10%ATR from the entry. A profit target is set at the EOD. Gray areas are pre- and post-market hours trading.


survivorship bias<sup>2</sup>. The data for these stocks were sourced from the Center for Research in Security Prices (CRSP). Intraday data for all stocks were obtained from IQFeed. Notably, this intraday data remained unadjusted for stock splits or dividends, ensuring that the database was not influenced by any retrospective price adjustments. All backtests and statistical analyses were performed using MATLAB R2023a. 

## 2.1 Base Strategy

We implemented some rules for choosing the stocks we studied. Not all stocks in the US markets are suitable for day trading due to varying levels of liquidity or trading volume. Our best approach was to exclude penny stocks and other low-liquidity stocks. To avoid making decisions based on hindsight, we used set criteria to narrow down our list of stocks on any given day. The stocks we considered had to meet the following requirements: 

1. The opening price had to be above $5. 

2. The average trading volume over the previous 14 days had to be at least 1,000,000 shares per day. 

3. The ATR over the previous 14 days had to be more than $0.50. 

These criteria ensured that the stocks we analyzed had suficient liquidity and volatility as well as favorable conditions for day trading [4, 2]. 

## Entry Conditions

With each eligible stock, we placed a stop order (not to be confused with a stop loss order) at a level equal to the high/low of the 5-minute range, in the direction of the opening range. For example, if a stock had a bullish move within the first 5 minutes of trading (from 9:30 am until 9:35 am ET), we placed a stop order at the highest value of the 5-minute opening range (known as the 5-minute high). Conversely, if a stock had a bearish move within the first 5 minutes of trading, we placed a stop order at the lowest value of the 5-minute opening range (known as the 5-minute low). In the case of a doji (open = close) forming in the first 5 minutes, no order was placed. 

## Stop Loss and Profit Target

In case the order was triggered, we placed a stop loss order at a 10% ATR distance from the executed entry price. If the stop loss was not reached intraday, we closed the position at the end of the trading session (i.e., 4:00 pm ET). 

## Position Sizing

Each stock was traded such that in case of the stop loss being hit, the resulting loss incurred on the capital deployed for that position would be 1%. We also set a maximum leverage constraint at 4x, in accordance with the majority of US FINRA-regulated brokers<sup>3</sup>. 

The resulting long-short portfolio to be traded on any given day was thus composed of all the stocks that satisfied the filters (as defined above) and whose opening range was either positive or negative. 

The backtest was conducted from January 1, 2016 to December 31, 2023. We assumed a starting capital of $25,000 and incorporated a commission cost of $0.0035 per share (this figure represented the entry-level commission fee charged by Interactive Brokers Pro – Tiered as of December 31, 2023). 

Figure 3 displays the equity curve for the portfolio generated by the diversified 5-minute ORB strategy across all US stocks. With an initial investment of $25,000, the portfolio appreciated by 30%, resulting in a net profit of only $7,500 after accounting for commission fees. In contrast, during the same period, a passive long position in the S&P 500 would have seen an increase of nearly 200%, equating to a profit of about $50,000. 

As detailed in Table 1, the active 5-minute ORB strategy underperformed, yielding a modest annual return of only 3.2% and experiencing an annual volatility of approximately 6.6%. This resulted in a Sharpe Ratio of 0.48, which was significantly lower than the 0.78 Sharpe ratio for the S&P 500. 

Despite this overall underperformance when compared to the benchmark, the 5-minute ORB strategy showed some encouraging results. Specifically, its maximum drawdown (MDD) was only 13%, compared to the S&P 500’s MDD of 34% within the same time frame. Moreover, in terms of the worst single day returns, the 5-minute ORB strategy’s performance was notably better, with a maximum loss of only -0.8% in a single day, com pared to the S&P 500’s maximum loss (on March 16, 2020, during the COVID pandemic) of -10.9%. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/6c7a3163-41e3-4a71-8be4-7d39021cc21c/d774fe14c01fa864ddb7b8eb51b6ac57411d00863c6ae6989ab3de6ecda3b71e.jpg)



Figure 3: Equity curve comparison of a S&P500 buy-and-hold portfolio (red line) and a portfolio engaged in day trading both long and short positions on all stocks using the 5-minute ORB strategy described in Section 2.1 (black line). The analysis covers the period from January 1, 2016 to December 31, 2023, with an initial net asset value of $25,000 and a commission rate of $0.0035 per share.


Since the validity of day trading as a long-term consistent and uncorrelated source of income for traders and investors is a matter of debate, we decided to run a simple linear regression analysis to see if the 5-minute ORB returns were correlated with S&P 500 returns and to see if there was any abnormal return in excess of what can be extracted by a passive market exposure. Further insights were also gained from this simple linear regression analysis, where the daily returns of the 5-minute ORB strategy were regressed against the daily returns of the S&P 500. This method, commonly employed by academia and institutional investors, assesses the dependency between two strategies or assets. The regression equation utilized was<sup>4</sup>: 


Table 1: Performance comparison of a S&P500 buy-and-hold portfolio and a portfolio engaged in day trading both long and short positions on all stocks using the 5-minute ORB strategy described in Section 2.1. The analysis covers the period from January 1, 2016 to December 31, 2023, with an initial net asset value of $25,000 and a commission rate of $0.0035 per share.


<table><tr><td>Strategy</td><td>Total Return</td><td>IRR</td><td>Volatility</td><td>Sharpe Ratio</td><td>Hit Ratio</td><td>MDD</td><td>Worst Day</td><td>Alpha</td><td>Beta</td></tr><tr><td>ORB Base</td><td>29%</td><td>3.2%</td><td>6.6%</td><td>0.48</td><td>41.4%</td><td>13%</td><td>-0.8%</td><td>3.3%</td><td>0.01</td></tr><tr><td>S&amp;P500</td><td>198%</td><td>14.2%</td><td>18.3%</td><td>0.78</td><td>54.9%</td><td>34%</td><td>-10.9%</td><td>0.00%</td><td>1.00</td></tr></table>

$$
R e t _ {\mathrm{ORBBase}} = \alpha + \beta \times R e t _ {\mathrm {S\ & P500}}.
$$

The beta coeficient of the ORB strategy, being close to 0, indicated a negligible correlation with the S&P 500. Additionally, an alpha of 3.26% per annum represented the profit generated by the ORB strategy that was not attributable to simple market exposure. 

What factors, therefore, contributed to the basic 5-minute ORB strategy’s lackluster performance? To understand the underlying causes, we must revisit the core concept of the ORB strategy. This strategy aims to identify assets that exhibit an abnormal imbalance between demand and supply in the first few minutes of the trading session. The hypothesis is that this imbalance will persist throughout the session, creating exploitable intraday trends. While the direction of the demand-supply imbalance can be inferred from the opening range, its abnormality can be assessed by comparing its current opening range volume to its recent average. 

In the following section, we introduce a straightforward metric to measure the abnormality of the opening range volume. We will also examine whether this metric efectively predicts the subsequent realized PnL of the ORB strategy. 

# 3 Not All Opening Range Are Created Equally

You are only as good as the stocks that you trade 

– Mike Bellafiore<sup>[6]</sup> 

A prevalent strategy among experienced day traders is to focus their intraday trading activities on Stocks in Play [6, 7]. A stock is considered in play when it shows unusual trading activity throughout the day, which often results in an expansion of its daily price range and a distinct trend in its intraday price movements. A stock is typically expected to be in play in response to a major fundamental catalyst that prompts institutional investors to re-evaluate their financial positions in it. Common catalysts include: 

• Earnings reports 

• Earnings warnings or pre-announcements 

• Earnings surprises 

• FDA approvals or disapprovals 

• Mergers/acquisitions 

• Alliances, partnerships, or major product releases 

• Major contract wins/losses 

• Restructuring, layofs, or management changes 

• Stock splits, buybacks, or debt oferings 

• Break of key technical levels. 

While a fundamental catalyst is often necessary to trigger abnormal trading activity in a stock, it is not always suficient to classify it as a Stock in Play. If the market has already priced in the catalyst, institutional investors may not react significantly, resulting in minimal trading activity. An efective method for traders to determine if a catalyst is indeed causing unusually high trading activity is through the use of Relative Volume. This metric is a statistical comparison of the day’s trading volume against the average volume from previous days. For real-time analysis, traders can calculate the Relative Volume continuosly throughout the day. In our study, we focused on the Relative Volume during the opening range. Specifically, we calculated the Relative Volume for each stock $j$ after the first 5 minutes of each trading day t using this formula: 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/6c7a3163-41e3-4a71-8be4-7d39021cc21c/f0961184deab59fcf6afe3a1fb103739ab5d62b473f7e17e6f48a234bebea949.jpg)



Figure 4: Average PnL (in R) of 5-minute ORB grouped by the Relative Volume in the first 5 minutes of the trading session.


$$
R e l a t i v e V o l u m e _ {t, j} = \frac {O R V o l u m e _ {t , j}}{\frac {1}{1 4} \sum_ {i = 1} ^ {1 4} O R V o l u m e _ {t - 1 , j}},
$$

where $O R V o l u m e _ { t , j }$ represents the volume traded in stock j during the first 5-minutes of trading in day t. 

Building upon the basic filters used in the Base Strategy $( { \mathrm { P r i c e } } > { \mathfrak { H } }$ , Average Volume 14 Days > 1,000,000 shares, ATR 14 Days $> \$ 90.50)$ , we further analyzed the relationship between Relative Volume and average PnL in R. Figure 4 distinctly demonstrates a strong positive correlation between Relative Volume and subsequent realized PnL (net of commissions). 

As shown in Figure 4, when the Relative Volume was below 100%, the average PnL of 5-minute ORB trades was notably low at -0.02R. However, this figure improved signifi cantly to 0.08R per trade when the Relative Volume exceeded 100%. Remarkably, at a 

Relative Volume of over 30x (or more than 3,000%), the average profitability per trade soared to 0.38R. 

While focusing exclusively on stocks with a 30x trading activity may seem attractive in terms of PnL per trade, this approach might limit the total number of trades available per year, potentially impacting the ability to meet a predefined annual target. There is only a limited number of Stocks in Play every week that can reach such high trading volume. In the upcoming section, we will explain how we leveraged these insights to enhance the eficiency of trading the 5-minute ORB strategy in the US market. 

## 4 Opening Range Breakout on Stocks in Play

To enhance the efectiveness of the Base Strategy, we proposed an additional constraint: the strategy should not trade stocks that exhibit below-average trading activity during the opening range (9:30 am to 9:35 am ET). This means we would exclusively focus on those stocks whose Relative Volume was at least 100%. Furthermore, to ensure we were trading the most in play stocks of the day, our strategy would only take positions in the top 20 stocks experiencing the highest Relative Volume. The revised strategy incorporated the following filters: 

1. The opening price had to be above $5. 

2. The average trading volume over the previous 14 days had to be at least 1,000,000 shares per day. 

3. The ATR over the previous 14 days had to be more than $0.50. 

4. The Relative Volume had to be at least 100%. 

5. Trade the stocks with the top 20 Relative Volume. 

As for the base strategy, the direction of each trade (long or short) was determined by the initial movement of the opening range. A positive opening range prompted a stop buy order, whereas a negative one led to a stop sell order. For every position we opened, we set a stop loss at 10% of the ATR. If a position was not stopped during the day, it was unwound at the end of the trading day. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/6c7a3163-41e3-4a71-8be4-7d39021cc21c/e83cfcb53c1c663b9709acf43ad0555bba6e8bd0c50552a8f417d554f61fbbef.jpg)



Figure 5: Equity curve comparison of a S&P500 buy-and-hold portfolio (red line), a portfolio engaged in day trading both long and short positions on all stocks using the 5-minute ORB strategy described in Section 2.1 (black line) and the 5-minute ORB strategy with Relative Volume described in Section 4 (blue line). The analysis covers the period from January 1, 2016 to December 31, 2023, with an initial net asset value of $25,000 and a commission rate of $0.0035 per share.


Consistent with the Base Strategy, each stock was traded in such a way that should the stop loss be triggered, the loss on the capital allocated to that position would not exceed 1%. Additionally, we imposed a maximum leverage constraint of 4x, in line with the regulations of most US FINRA-regulated brokers. The starting assets under management (AUM) and the commission per share remained the same as in the base case. 

Figure 5 displays in blue the equity trajectory for this new version of the 5-minute ORB strategy. The improvement compared to the base strategy is substantial, with a remarkable outperformance against the passive buy-and-hold approach. From January 1, 2016 to December 31, 2023, an initial investment of $25,000 in this strategy would have grown to approximately $435,000, equating to an extraordinary total net return of 1,637%. In contrast, a passive investment in the S&P 500 during the same period would have seen growth from $25,000 to about $75,000, which is roughly a 200% increase. 


Table 2: Performance comparison of a S&P500 buy-and-hold portfolio, a portfolio engaged in day trading both long and short positions on all stocks using the 5-minute ORB strategy described in Section 2.1 and the 5-minute ORB strategy with Relative Volume described in Section 4. The analysis covers the period from January 1, 2016 to December 31, 2023, with an initial net asset value of $25,000 and a commission rate of $0.0035 per share.


<table><tr><td>Strategy</td><td>Total Return</td><td>IRR</td><td>Volatility</td><td>Sharpe Ratio</td><td>Hit Ratio</td><td>MDD</td><td>Worst Day</td><td>Alpha</td><td>Beta</td></tr><tr><td>ORB Base</td><td>29%</td><td>3.2%</td><td>6.6%</td><td>0.48</td><td>41.4%</td><td>13%</td><td>-0.8%</td><td>3.3%</td><td>0.01</td></tr><tr><td>ORB + Rel Vol</td><td>1,637%</td><td>41.6%</td><td>14.8%</td><td>2.81</td><td>48.4%</td><td>12%</td><td>-1.61%</td><td>35.8%</td><td>0.00</td></tr><tr><td>S&amp;P500</td><td>198%</td><td>14.2%</td><td>18.3%</td><td>0.78</td><td>54.9%</td><td>34%</td><td>-10.9%</td><td>0.00%</td><td>1.00</td></tr></table>

Table 2 presents the performance statistics for this newly refined 5-minute ORB strategy, highlighting significant improvements over the Base Strategy. The annual rate of return soared from 3.2% in the ORB Base to an impressive 41.6%. Equally noteworthy was the increase in the Sharpe Ratio, which rose more than 5-fold, from 0.48 to an extraordinary 2.81. 

While the MDD showed a modest improvement, the worst day loss slightly deteriorated, likely due to the more concentrated nature of the portfolio (in fact, in the ORB + Rel Vol portfolio we traded only the top 20 stocks). The potential for a greater worst day loss in a more concentrated portfolio arises from the increased exposure to specific stock movements, which can lead to more pronounced losses on days when those stocks perform poorly. In line with the previous analysis, we conducted a regression of the strategy’s daily returns against those of the S&P 500, with remarkable findings. The beta coeficient remained close to zero, indicating minimal dependency on overall market movements. Most strikingly, the alpha surged to an impressive 36% per annum. 

Considering that these returns were net of commission and the strategy’s parameters were minimal and based on economic rationale rather than retrospective optimization, we are confident that these results could maintain their robustness and significance in future applications. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/6c7a3163-41e3-4a71-8be4-7d39021cc21c/15f274c5abb5e53ddb0f13247dc6530d84d08f4ac5a23a1b3803c968b921b647.jpg)



Figure 6: Equity curve comparison of a S&P500 buy-and-hold portfolio (red line) and a portfolio engaged in day trading both long and short positions using the 5-minute, 15-minute, 30-minute, and 60-minute ORB system described in Section 4. The COMBO (black line) represents an equally weighted portfolio of ORB portfolios across various time frames (5-minute, 15-minute, 30-minute, and 60-minute). The analysis covers the period from January 1, 2016 to December 31, 2023, with an initial net asset value of $25,000 and a commission rate of $0.0035 per share.


## 5 Opening Range Breakout on Other-Time Frames

The ORB strategy can be applied across various time frames during the first trading hour from the open (9:30am to around 10:30am ET), where market volatility and liq uidity are at their peak. Although the 5-minute frame is standard, we thought it would be worthwhile to also explore other popular time frames such as 15, 30, or 60 minutes. For this purpose, we investigated our ORB strategy across various time frames, limiting our study to Stocks in Play with at least 100% Relative Volume in their respective first n-minute time frame. 


Table 3: Performance comparison of a S&P500 buy-and-hold portfolio and a portfolio engaged in day trading both long and short positions using the 5-minute, 15-minute, 30-minute, and 60-minute ORB system described in Section 4. The COMBO represents an equally weighted portfolio of ORB portfolios across various time frames (5-minute, 15-minute, 30-minute, and 60-minute). The analysis covers the period from January 1, 2016 to December 31, 2023, with an initial net asset value of $25,000 and a commission rate of $0.0035 per share.


<table><tr><td>Strategy</td><td>Total Return</td><td>IRR</td><td>Volatility</td><td>Sharpe Ratio</td><td>Hit Ratio</td><td>MDD</td><td>Alpha</td><td>Beta</td></tr><tr><td>5m-ORB + Rel Vol</td><td>1,637%</td><td>41.6%</td><td>14.8%</td><td>2.81</td><td>48.4%</td><td>12%</td><td>35.8%</td><td>0.00</td></tr><tr><td>15m-ORB + Rel Vol</td><td>272%</td><td>17.4%</td><td>12.2%</td><td>1.43</td><td>44.7%</td><td>11%</td><td>16.9%</td><td>-0.01</td></tr><tr><td>30m-ORB + Rel Vol</td><td>21%</td><td>2.3%</td><td>11.1%</td><td>0.21</td><td>42.4%</td><td>35%</td><td>2.8%</td><td>0.01</td></tr><tr><td>60m-ORB + Rel Vol</td><td>39%</td><td>4.1%</td><td>10.2%</td><td>0.40</td><td>42.3%</td><td>21%</td><td>4.4%</td><td>0.01</td></tr><tr><td>COMBO</td><td>234%</td><td>15.8%</td><td>7.9%</td><td>1.99</td><td>47.3%</td><td>7%</td><td>15.0%</td><td>0.00</td></tr><tr><td>S&amp;P500</td><td>198%</td><td>14.2%</td><td>18.3%</td><td>0.78</td><td>54.9%</td><td>34%</td><td>0.00%</td><td>1.00</td></tr></table>

For example, the Relative Volume for a 15-minute ORB is measured in the first 15 minutes, and for a 30-minute ORB, it is compared with the first 30-minute average over the previous 14 days. The results are presented in Figure 6 and Table 3, comparing them to a simple S&P 500 buy-and-hold portfolio. As can be seen, the 5-minute ORB significantly outperformed the other time frames as well as a passive exposure in the S&P 500. The reason for the 5-minute ORB’s superior performance is unclear and warrants further investigation. A plausible explanation might be that the shorter the time-frame that define the opening range, the greater the portion of the move captured by the ORB on trend days. 

## 6 Best/Worst Performers on 5-minute ORB

In this section, we will delve into the specifics of the 25 best and 25 worst performing stocks in the US stock market based on the results from the n-minute ORB strategies with Relative Volume above 1. It is fascinating to observe which stocks emerged as the top performers and which fell behind. As illustrated in Table 4, familiar names such as Tesla (TSLA), NVIDIA (NVDA), and Advanced Micro Devices (AMD) were among the top performing stocks. These tickers are popular among retail traders and typically exhibit significant trading volume, surpassing many other stocks. In contrast, Table 5 lists the worst performing stocks based on the 5-minute ORB strategy. 


Table 4: Best performing stocks for the n-minute ORB strategies with Relative Volume of at least 100% based on cumulative R.


<table><tr><td colspan="3">5m-ORB</td><td colspan="3">15m-ORB</td><td colspan="3">30m-ORB</td><td colspan="3">60m-ORB</td></tr><tr><td>Ticker</td><td>PnL (R)</td><td>Win Ratio (%)</td><td>Ticker</td><td>PnL (R)</td><td>Win Ratio (%)</td><td>Ticker</td><td>PnL (R)</td><td>Win Ratio (%)</td><td>Ticker</td><td>PnL (R)</td><td>Win Ratio (%)</td></tr><tr><td>DDD</td><td>385</td><td>21%</td><td>CAR</td><td>233</td><td>21%</td><td>MXIM</td><td>214</td><td>26%</td><td>DDD</td><td>185</td><td>24%</td></tr><tr><td>FSLR</td><td>370</td><td>20%</td><td>NVDA</td><td>200</td><td>20%</td><td>SAVE</td><td>213</td><td>23%</td><td>THC</td><td>183</td><td>26%</td></tr><tr><td>NVDA</td><td>309</td><td>19%</td><td>AMD</td><td>189</td><td>19%</td><td>ACAD</td><td>201</td><td>21%</td><td>TKAT</td><td>177</td><td>40%</td></tr><tr><td>SWBI</td><td>272</td><td>24%</td><td>LITE</td><td>187</td><td>22%</td><td>CDNS</td><td>196</td><td>24%</td><td>DISH</td><td>169</td><td>25%</td></tr><tr><td>RCL</td><td>271</td><td>20%</td><td>FOSL</td><td>187</td><td>20%</td><td>WOLF</td><td>185</td><td>25%</td><td>EXEL</td><td>162</td><td>25%</td></tr><tr><td>W</td><td>252</td><td>21%</td><td>WW</td><td>180</td><td>22%</td><td>FLR</td><td>171</td><td>23%</td><td>CDNS</td><td>161</td><td>26%</td></tr><tr><td>VIR</td><td>244</td><td>20%</td><td>WOLF</td><td>170</td><td>21%</td><td>TKAT</td><td>171</td><td>30%</td><td>FLR</td><td>154</td><td>22%</td></tr><tr><td>EXAS</td><td>229</td><td>19%</td><td>MTCH</td><td>167</td><td>20%</td><td>CSGP</td><td>163</td><td>28%</td><td>BA</td><td>151</td><td>25%</td></tr><tr><td>ALK</td><td>207</td><td>18%</td><td>ASML</td><td>161</td><td>24%</td><td>FOSL</td><td>161</td><td>21%</td><td>IONS</td><td>145</td><td>28%</td></tr><tr><td>FOSL</td><td>205</td><td>23%</td><td>OMF</td><td>159</td><td>27%</td><td>HRB</td><td>156</td><td>25%</td><td>VLO</td><td>144</td><td>25%</td></tr><tr><td>WW</td><td>190</td><td>19%</td><td>SWBI</td><td>152</td><td>23%</td><td>NET</td><td>149</td><td>23%</td><td>AMD</td><td>140</td><td>25%</td></tr><tr><td>OKTA</td><td>188</td><td>19%</td><td>BWA</td><td>150</td><td>22%</td><td>DDD</td><td>142</td><td>21%</td><td>INTU</td><td>137</td><td>26%</td></tr><tr><td>PBF</td><td>186</td><td>19%</td><td>NFLX</td><td>147</td><td>20%</td><td>DISH</td><td>139</td><td>20%</td><td>FOSL</td><td>136</td><td>23%</td></tr><tr><td>AMD</td><td>184</td><td>17%</td><td>FSLR</td><td>146</td><td>18%</td><td>GDDY</td><td>135</td><td>21%</td><td>FIS</td><td>133</td><td>24%</td></tr><tr><td>TSLA</td><td>183</td><td>18%</td><td>NKTR</td><td>141</td><td>21%</td><td>MTCH</td><td>134</td><td>22%</td><td>KA</td><td>131</td><td>26%</td></tr><tr><td>ADBE</td><td>182</td><td>17%</td><td>CDNS</td><td>141</td><td>20%</td><td>NTNX</td><td>130</td><td>18%</td><td>SAVE</td><td>128</td><td>25%</td></tr><tr><td>ACAD</td><td>176</td><td>17%</td><td>LRCX</td><td>140</td><td>19%</td><td>MA</td><td>129</td><td>20%</td><td>W</td><td>126</td><td>24%</td></tr><tr><td>ELV</td><td>174</td><td>20%</td><td>TER</td><td>138</td><td>22%</td><td>ALK</td><td>128</td><td>18%</td><td>TRU</td><td>126</td><td>25%</td></tr><tr><td>TWLO</td><td>172</td><td>19%</td><td>FLR</td><td>137</td><td>19%</td><td>OMF</td><td>128</td><td>25%</td><td>STZ</td><td>126</td><td>26%</td></tr><tr><td>TDOC</td><td>170</td><td>17%</td><td>CSGP</td><td>136</td><td>23%</td><td>TMX</td><td>126</td><td>27%</td><td>AXDX</td><td>125</td><td>22%</td></tr><tr><td>SPLK</td><td>165</td><td>19%</td><td>LIN</td><td>134</td><td>20%</td><td>LIN</td><td>122</td><td>20%</td><td>CSGP</td><td>125</td><td>26%</td></tr><tr><td>PARA</td><td>164</td><td>17%</td><td>QQQ</td><td>134</td><td>18%</td><td>OLN</td><td>122</td><td>23%</td><td>BAX</td><td>125</td><td>22%</td></tr><tr><td>WDC</td><td>163</td><td>17%</td><td>BCRX</td><td>134</td><td>24%</td><td>AAOI</td><td>122</td><td>21%</td><td>VRTX</td><td>124</td><td>23%</td></tr><tr><td>NWL</td><td>159</td><td>18%</td><td>YELP</td><td>133</td><td>18%</td><td>TT</td><td>121</td><td>19%</td><td>MAR</td><td>122</td><td>25%</td></tr><tr><td>SQ</td><td>158</td><td>18%</td><td>AZTA</td><td>132</td><td>27%</td><td>NFLX</td><td>119</td><td>21%</td><td>NFLX</td><td>119</td><td>21%</td></tr></table>

These findings highlight the importance of selecting stocks with high Relative Volume for day trading strategies like the n-minute ORB. The higher trading volume in these stocks may contribute to their pronounced intraday price movements, ofering traders greater opportunities for profit. Additionally, the popularity of these stocks among retail traders might also increase the likelihood of price movements that are conducive to the ORB strategy, as these stocks are more susceptible to rapid shifts in sentiment and momentum. 

The success of stocks like TSLA, NVDA, and AMD within the 5-minute ORB framework underscores the strategy’s potential when applied to high volume, volatile stocks. These results ofer valuable insights for traders looking to optimize their day trading approaches, suggesting that focusing on stocks with substantial trading activity and widespread in terest among the trading community can enhance the performance of the ORB strategy. 


Table 5: Worst performing stocks for the n-minute ORB strategies with Relative Volume of at least 100% based on cumulative R.


<table><tr><td colspan="3">5m-ORB</td><td colspan="3">15m-ORB</td><td colspan="3">30m-ORB</td><td colspan="3">60m-ORB</td></tr><tr><td>Ticker</td><td>PnL (R)</td><td>Win Ratio (%)</td><td>Ticker</td><td>PnL (R)</td><td>Win Ratio (%)</td><td>Ticker</td><td>PnL (R)</td><td>Win Ratio (%)</td><td>Ticker</td><td>PnL (R)</td><td>Win Ratio (%)</td></tr><tr><td>CMC</td><td>-154</td><td>12%</td><td>CLR</td><td>-155</td><td>13%</td><td>BIIB</td><td>-266</td><td>16%</td><td>BIIB</td><td>-216</td><td>21%</td></tr><tr><td>TRGP</td><td>-132</td><td>14%</td><td>TRGP</td><td>-131</td><td>15%</td><td>AEO</td><td>-165</td><td>14%</td><td>DINO</td><td>-124</td><td>17%</td></tr><tr><td>CSX</td><td>-128</td><td>12%</td><td>TSCO</td><td>-130</td><td>13%</td><td>KMX</td><td>-161</td><td>14%</td><td>DBI</td><td>-113</td><td>20%</td></tr><tr><td>CNP</td><td>-127</td><td>13%</td><td>IVZ</td><td>-119</td><td>16%</td><td>CLR</td><td>-145</td><td>14%</td><td>GM</td><td>-104</td><td>19%</td></tr><tr><td>BJ</td><td>-120</td><td>10%</td><td>HOG</td><td>-119</td><td>13%</td><td>VST</td><td>-141</td><td>12%</td><td>ADI</td><td>-102</td><td>19%</td></tr><tr><td>PSTG</td><td>-120</td><td>13%</td><td>TPR</td><td>-105</td><td>15%</td><td>CNK</td><td>-136</td><td>15%</td><td>BKR</td><td>-99</td><td>15%</td></tr><tr><td>WMB</td><td>-113</td><td>13%</td><td>RES</td><td>-105</td><td>11%</td><td>HAL</td><td>-136</td><td>16%</td><td>GILD</td><td>-96</td><td>15%</td></tr><tr><td>TT</td><td>-112</td><td>12%</td><td>INCY</td><td>-104</td><td>13%</td><td>EA</td><td>-125</td><td>16%</td><td>KDNY</td><td>-96</td><td>10%</td></tr><tr><td>HP</td><td>-112</td><td>13%</td><td>YUMC</td><td>-101</td><td>16%</td><td>GM</td><td>-115</td><td>17%</td><td>AEO</td><td>-94</td><td>16%</td></tr><tr><td>ALLY</td><td>-110</td><td>13%</td><td>TFFP</td><td>-98</td><td>8%</td><td>BG</td><td>-114</td><td>15%</td><td>DBX</td><td>-91</td><td>16%</td></tr><tr><td>FL</td><td>-109</td><td>11%</td><td>GM</td><td>-98</td><td>16%</td><td>REG</td><td>-110</td><td>12%</td><td>FCX</td><td>-89</td><td>19%</td></tr><tr><td>PSX</td><td>-107</td><td>13%</td><td>REG</td><td>-96</td><td>13%</td><td>XYL</td><td>-110</td><td>13%</td><td>UBX</td><td>-89</td><td>9%</td></tr><tr><td>WYNN</td><td>-105</td><td>14%</td><td>FCX</td><td>-93</td><td>14%</td><td>ANF</td><td>-108</td><td>14%</td><td>CMCSA</td><td>-89</td><td>17%</td></tr><tr><td>DOW</td><td>-103</td><td>11%</td><td>MET</td><td>-92</td><td>15%</td><td>SEDG</td><td>-105</td><td>13%</td><td>TDOC</td><td>-89</td><td>15%</td></tr><tr><td>URBN</td><td>-101</td><td>14%</td><td>EQT</td><td>-92</td><td>16%</td><td>MCK</td><td>-105</td><td>15%</td><td>EBAY</td><td>-88</td><td>16%</td></tr><tr><td>APC</td><td>-100</td><td>11%</td><td>KNX</td><td>-91</td><td>13%</td><td>GPS</td><td>-105</td><td>15%</td><td>LBRT</td><td>-88</td><td>13%</td></tr><tr><td>ROST</td><td>-99</td><td>12%</td><td>EXPE</td><td>-89</td><td>13%</td><td>NKE</td><td>-99</td><td>17%</td><td>EVLO</td><td>-85</td><td>10%</td></tr><tr><td>JBL</td><td>-95</td><td>12%</td><td>URBN</td><td>-88</td><td>16%</td><td>DAL</td><td>-96</td><td>16%</td><td>OGE</td><td>-84</td><td>16%</td></tr><tr><td>DD</td><td>-92</td><td>10%</td><td>BG</td><td>-88</td><td>12%</td><td>INTC</td><td>-93</td><td>15%</td><td>CSX</td><td>-84</td><td>17%</td></tr><tr><td>MARA</td><td>-91</td><td>13%</td><td>ROK</td><td>-88</td><td>12%</td><td>XEC</td><td>-92</td><td>16%</td><td>NTRS</td><td>-83</td><td>16%</td></tr><tr><td>VOYA</td><td>-89</td><td>14%</td><td>MU</td><td>-87</td><td>16%</td><td>SM</td><td>-91</td><td>17%</td><td>WMB</td><td>-82</td><td>17%</td></tr><tr><td>BLMN</td><td>-87</td><td>13%</td><td>IOVA</td><td>-87</td><td>12%</td><td>FCX</td><td>-90</td><td>15%</td><td>EWBC</td><td>-82</td><td>17%</td></tr><tr><td>BRO</td><td>-84</td><td>11%</td><td>MGY</td><td>-84</td><td>13%</td><td>PHM</td><td>-87</td><td>15%</td><td>MRO</td><td>-80</td><td>17%</td></tr><tr><td>HOG</td><td>-84</td><td>15%</td><td>SEDG</td><td>-82</td><td>12%</td><td>SGEN</td><td>-87</td><td>13%</td><td>CTSH</td><td>-78</td><td>18%</td></tr><tr><td>SKX</td><td>-83</td><td>15%</td><td>TSN</td><td>-81</td><td>15%</td><td>PSTG</td><td>-85</td><td>15%</td><td>TMUS</td><td>-78</td><td>17%</td></tr></table>

## 7 Conclusion

In conclusion, our comprehensive analysis of the ORB strategy within the US equity market ofers significant insights into its profitability and viability as a day trading approach. By examining a vast dataset covering over 7,000 US stocks traded from 2016 to 2023, we have highlighted the substantial potential of the ORB strategy, especially when applied to Stocks in Play exhibiting high Relative Volume of at least 100%. Our findings underscore the strategy’s efectiveness in generating consistent and uncorrelated returns, thereby addressing the long-standing debate about the feasibility of day trading 

as a sustainable income source. 

The remarkable performance of the 5-minute ORB strategy, in particular, stands out, demonstrating a notable advantage over both longer time frames within the ORB strategy and a passive buy-and-hold approach. This strategy achieved a net performance of over 1,600%, with a Sharpe ratio of 2.81, and an annualized alpha of 36%, significantly outperforming the passive S&P 500 return of 198% over the same period. Such results not only provide empirical support for the ORB strategy’s eficacy but also emphasize the critical role of selecting stocks with substantial trading activity, driven by underlying fundamental news, to capitalize on intraday volatility and liquidity. 

Furthermore, our exploration into varying time frames for the ORB strategy enriches the discourse on day trading methodologies, ofering traders nuanced perspectives on optimizing their strategies to enhance profitability and manage risk. The superior performance of the 5-minute ORB suggests a unique dynamic at play in the earliest phases of the trading day, highlighting an area ripe for further exploration. 

This paper contributes to the body of financial literature by providing a detailed, stockspecific analysis of ORB performance across diferent time frames, a first of its kind with such intraday granularity. Our rigorous statistical analysis, grounded in economic rationale rather than retrospective optimization, suggests that the findings presented herein could maintain their robustness and significance in future applications. 

As the landscape of retail trading continues to evolve, our study reafirms the importance of informed strategy selection, emphasizing the potential of technical analysis and specif ically the ORB strategy, to level the playing field for individual traders against more sophisticated market participants. However, while the ORB strategy presents a promising avenue for day traders, it is crucial to approach it with thorough research, disciplined risk management, and a clear understanding of market dynamics. 

In future research, further investigation into the reasons behind the 5-minute ORB’s exceptional performance, as well as the exploration of additional variables that may influence the strategy’s success, will be invaluable. This could include the impact of market conditions, the role of news and earnings announcements, and the integration of other technical indicators to refine entry and exit points. Through ongoing analysis and adaptation, traders can continue to hone their strategies to navigate the complexities of the financial markets efectively. 

## Author Biography

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/6c7a3163-41e3-4a71-8be4-7d39021cc21c/78fb328e73a76c7f5f4dafe5ef5d019689ac1f94bdd57ba965a595a6d65c29b2.jpg)


Andrew Aziz is a Canadian trader, investor, and oficial Forbes Council member. He has ranked as one of the top 100 best-selling authors in ”Business and Finance” for 7 consecutive years from 2016 to 2023. Aziz’s book on finance has been published in 13 diferent languages. Originally from Iran, Andrew moved to Canada in 2008 to pursue a PhD in chemical engineering, initiating a distinguished career in academia and industry. As a research scientist, Andrew made significant contributions to the field, authoring 13 papers and securing 3 US patents. Following a successful stint in research in chemical engineering and clean technology, he transitioned to the world of trading. Currently Andrew is a trader and proprietary fund manager at Peak Capital Trading in Vancouver, BC Canada. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/6c7a3163-41e3-4a71-8be4-7d39021cc21c/f6e86d65e22c6e99d3b333e1f15f15b1cfeb42da7d1c91bad2ba8dbe26b9c861.jpg)


Carlo Zarattini, originally from Italy, currently resides in Lugano, Switzerland. After completing his mathematics degree in Padova, he pursued a dual master’s in quantitative finance at Imperial College London and USI Lugano. He formerly served as a quantitative analyst at BlackRock, where he developed volatility and trend-following trading strategies. Carlo later established Concretum Research, assisting institutional clients with both high and medium-frequency quantitative strategies in stocks, futures, and options. Additionally, he founded R-Candles.com, the first backtester for discretionary technical traders. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/6c7a3163-41e3-4a71-8be4-7d39021cc21c/fee4847702467ff9c5d9f73e3efe0fccbbd77d57c85e6b0c9fbc42e1d9e4d5ea.jpg)


Andrea Barbon, born in Venice, currently resides in Zurich, Switzerland. He holds a Master degree in pure mathematics from the University of Amsterdam and a PhD in finance from the University of Lugano. He is Assistant Professor of Financial Technology at the FSI Center of the University of St.Gallen, Switzerland and at the Swiss Finance Institute. His research interests include asset pricing, monetary policy, fintech, blockchain, and machine learning. He is also head of AI at Concretum Research, and lead developer for the R-Candles web application. 

## References



[1] U.s. stock ownership highest since 2008, https://news.gallup.com/poll/506303/stockownership-highest-2008.aspx, 2021. 





[2] A. Aaziznia and A. Aziz. A Beginner’s Guide to Investing and Trading in the Modern Stock Market. 2020. 





[3] A. Anand and J. Pathak. The role of reddit in the gamestop short squeeze. Econ Lett, 211:110249, 2022. 





[4] A. Aziz. How to Day Trade for a Living: A Beginner’s Guide to Trading Tools and Tactics, Money Management, Discipline and Trading Psychology. AMS Publishing Group, 2015. 





[5] A. Aziz. Advanced Techniques in Day Trading: A Practical Guide to High Probability Strategies and Methods. AMS Publishing Group, 2018. 





[6] M. Bellafiore. One good trade: inside the highly competitive world of proprietary trading. 2010. 





[7] M. Bellafiore. The playbook: an inside look at how to think like a professional trader. 2013. 





[8] W. Brock, J. Lakonishok, and B. LeBaron. Simple technical trading rules and the stochastic properties of stock returns. J Finance, 47:1731–1764, 1992. 





[9] R. Caferra and D. Vidal-Tom´as. Who raised from the abyss? a comparison between cryptocurrency and stock market dynamics during the covid-19 pandemic. Financ Res Lett, 43, 2021. 





[10] L. A. Connors and L. B. Raschke. Street Smarts: High Probability Short-Term Trading Strategies. M. Gordon Publishing Group, 1995. 





[11] T. Crabel. Day trading with short term price patterns and opening range breakout. 1990. 





[12] A. Elder. Trading for a Living: Psychology, Trading Tactics, Money Management. Wiley, 2014. 





[13] U. Holmberg, C. L¨onnbark, and C. Lundstr¨om. Assessing the profitability of intraday opening range breakout strategies. Financ Res Lett, 10:27–33, 2013. 





[14] A. H˚akansson, F. Fern´andez-Aranda, and S. Jim´enez-Murcia. Gambling-like day trading during the covid-19 pandemic – need for research on a pandemic-related risk of indebtedness and mental health impact. Front Psychiatry, 12:1276, 2021. 





[15] P. J. Kaufman. Trading Systems and Methods. Wiley, 5 edition, 2020. 





[16] C. Lundstr¨om. Day trading returns across volatility states. Ume˚a Economic Studies 861, Ume˚a University, Department of Economics, 2013. Revised March 3, 2017. 





[17] J. M. Maheu, T. H. McCurdy, and Y. Song. Bull and bear markets during the covid-19 pandemic. Financ Res Lett, 42, 2021. 





[18] S. Schulmeister. The profitability of technical stock trading has moved from daily to intraday data. SSRN Electronic Journal, 2007. 





[19] Yi-Cheng Tsai, Mu-En Wu, Jia-Hao Syu, Chin-Laung Lei, Chung-Shu Wu, Jan-Ming Ho, and Chuan-Ju Wang. Assessing the profitability of timely opening range breakout on index futures markets. IEEE Access, 7:32061–32071, 2019. 





[20] J. Welles Wilder. New Concepts in Technical Trading Systems. Trend Research, 1978. 





[21] M. E. Wu, J. H. Syu, J. C. W. Lin, and J. M. Ho. Evolutionary orb-based model with protective closing strategies, 2021. 





[22] C. Zarattini and A. Aziz. The art of financial illusion: How to use martingale betting systems to fool people. SSRN Electronic Journal, 2023. 





[23] C. Zarattini and A. Aziz. Can day trading really be profitable? evidence of sustainable long-term profits from opening range breakout (orb) day trading strategy vs. benchmark in the us stock market. SSRN Electronic Journal, 2023. 





[24] C. Zarattini and A. Aziz. Volume weighted average price (vwap) the holy grail for day trading systems. SSRN Electronic Journal, 2023. 

