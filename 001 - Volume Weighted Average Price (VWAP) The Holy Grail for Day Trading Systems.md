# Volume Weighted Average Price (VWAP) The Holy Grail for Day Trading Systems

Carlo Zarattini<sup>1</sup>, Andrew Aziz<sup>2,3</sup> 

<sup>1</sup>Concretum Research, Viale Carlo Cattaneo 1, 6900 Lugano, Switzerland <sup>2</sup>Peak Capital Trading, 744 West Hastings Street, Vancouver, BC, Canada V6C 1A5 <sup>3</sup>Bear Bull Traders, 744 West Hastings Street, Vancouver, BC, Canada V6C 1A5 

Email: <sup>1</sup>carlo@concretumgroup.com, <sup>2</sup>andrew@peakcapitaltrading.com 

November 13, 2023 

## Abstract

This paper explores the application of the Volume Weighted Average Price (VWAP) in detecting market imbalances and enhancing trading decisions across diverse market conditions. We introduce a straightforward VWAP-based day trading strategy, which initiates long positions when price is above the VWAP and short positions when it falls below the VWAP. Our analysis employs QQQ and TQQQ as primary trading instruments, covering the period from January 2, 2018, to September 28, 2023. This timeframe includes two bear markets and multiple high-volatility events, providing a comprehensive test of market variations. Our findings reveal that an initial investment of $25,000 in the VWAP Trend Trading strategy with QQQ would have grown to $192,656, net of commissions, yielding a 671% return. This performance is marked by a maximum drawdown of just 9.4% and a Sharpe Ratio of 2.1. In contrast, a passive buy-and-hold strategy in QQQ during the same period would have returned 126%, with a significantly higher maximum drawdown of 37% and a lower Sharpe Ratio of 0.7. Further enhancing our strategy with TQQQ (3x leveraged ETFs of QQQ), we observed extraordinary outcomes: a $25,000 investment surged to $2,085,417, net of commissions. This equates to an 8,242% total return, or an average annual return of 116%, maintaining a maximum drawdown comparable to the passive QQQ strategy. Although we do not regard it as a fully developed trading system, our findings highlight VWAP’s potential as a powerful tool for active traders and investors, emphasizing its superiority over standard buyand-hold approaches in terms of profitability, risk-adjusted returns, and resilience during market fluctuations. 

Keywords: Day Trading, Volume Weighted Average Price, VWAP, Day Trading Systems, QQQ, TQQQ 

## 1 Introduction

The world of day trading is rife with debates and discussions, often revolving around the most efective strategies and if day trading can be a long term, consistent and uncorrelated source of income. In the recent years especially after COVID-19 pandemic lockdowns, day trading has captivated the imagination of many retail traders seeking to profit from market volatility, but its long-term viability remains a subject of ongoing discussion within the financial community [1, 2, 3, 4]. We previously investigated the validity of day trading with a well-known 5-minute Opening Range Breakout (ORB) strategy during the period of 2016 to 2023 [5]. That period encompassed two bear markets and a few events with abnormal volatility. Our results suggested that with the proper use of leverage or leveraged products (such as 3x leveraged ETFs), day trading can significantly outperform a standard buy and hold portfolio on benchmark indexes in the US public equity markets (Nasdaq or NYSE). For example, between 2016 and 2023, a portfolio of $25,000 actively trading ORB on TQQQ would have earned an outstanding return of 1,484% while an investment in the QQQ ETF would have earned only 169%. 

In recent years, the realm of algorithmic trading has witnessed significant advancements in the development of trading strategies that seek to harness the power of data analytics and market insights [6]. One such strategy that has gained prominence is the use of the Volume Weighted Average Price (VWAP) as a benchmark and basis for intraday trading decisions [7]. The Volume Weighted Average Price (VWAP) is a financial metric used to determine the average price of a security, such as stocks, over a given period (usually intraday), taking into account both the price and the volume of trades during that period. This indicator provides a comprehensive reflection of the market’s price action, as it integrates volume data to emphasize periods with higher trading activity. By doing so, VWAP ofers a more precise measure of a security’s average price compared to simple average price calculations, which do not account for variations in trading volume. 

The formula for VWAP is expressed as follows: 

$$
\mathrm{VWAP} = \frac {\sum (\mathrm{HLC} _ {t} \times \mathrm{Volume} _ {t})}{\sum \mathrm{Volume} _ {t}},\tag{1}
$$

where: 

$\mathrm { H L C } _ { t }$ is the average between High, Low and Close of the security in minute $t ,$ 

• Volume<sub>t</sub> is the trading volume of the security in minute $t ,$ 

• The summation $\displaystyle \sum$ runs over all observations within the specified period. 

VWAP is often used by traders and investors to assess the average price at which a stock has been traded throughout the day, taking into account the varying levels of trading ac tivity. The VWAP is considered one of the most important indicators for active trading due to its ability to provide valuable insights into market trends and price action. 

Institutions and traders often pay close attention to VWAP for several reasons: 

1. Reflects Market Liquidity: VWAP takes into account both the price and volume of trades over a specific time period, usually the trading day. This means it provides a weighted average price that reflects not only the price levels but also the liquidity or trading activity at those levels. High-volume trades have more influence on VWAP than low-volume trades, making it a useful metric for gauging market sentiment. [8, 9] 

2. Execution Benchmark: Institutional traders use VWAP as a benchmark for their trade executions. By comparing the execution price of their trades to the VWAP, they can assess whether they achieved better or worse prices relative to the overall market conditions. This helps them evaluate their trading strategies and performance. VWAP execution orders represent around 50% of all the institutional investors’ trading. [7] 

3. Intraday Trend Analysis: VWAP can be used to identify intraday trends. If the current market price is consistently above the VWAP, it suggests a bullish sentiment, while prices below VWAP indicate a bearish sentiment. Traders often look for opportunities to go long when the price is above VWAP and short when it’s below. [10] 

4. Support and Resistance Levels: VWAP can act as dynamic support or resistance levels during the trading day. Traders may use VWAP to identify potential entry or exit points based on whether the price is moving above or below it. [11] 

In this study, we embark on an exploration of the reliability of VWAP as a tool to identify market imbalances and subsequent market trends. The primary goal of this re search paper is to assess whether the distance of current price versus VWAP ofers a valuable indicator for future price moves. The subsequent obvious step (in case VWAP passed the test) would be to create an intraday VWAP-based trading system that aims to yield meaningful results in terms of profitability and risk-adjusted return. We aim to investigate the efectiveness of this strategy across various market conditions, seeking to understand its potential strengths and limitations. By conducting a comprehensive analysis of historical data and employing statistical methods, we endeavor to contribute valuable insights to the field of algorithmic trading and provide practical guidance for traders and investors. To be consistent with previous published papers, we conducted our analysis using QQQ and TQQQ, two very liquid ETFs tracking the famous Nasdaq100 index. 

It is important to mention that this study remains exploratory in nature. Past successes with a strategy do not serve as a guarantee of future profitability. Our aim is not to ofer definitive prescriptions for trading success but to encourage further investigation and innovation within the trading and quantitative analysis community. We hope to inspire traders and quant analysts to delve deeper into this subject and insights derived from this study serve as a springboard for more extensive research endeavors, ultimately contributing to the collective knowledge of intraday trading strategies and enhancing the toolkit available to traders and investors. It is our hope that this exploration into a simple VWAP-based day trading system sparks interest, fosters collaborative inquiry, and inspires a new wave of research aimed at uncovering innovative and efective trading strategies. 

All the backtests and statistics are produced using MATLAB. The database uses 1-minute open, high, low, close, and volume data for QQQ and TQQQ, from January 2018 until September 2023<sup>1</sup>. Data is provided by IQFeed and Interactive Brokers. 

## 2 Market Imbalances and VWAP

It is often said that when the price of a stock is above VWAP, market participants were net buyers of the stock, while when the price is below VWAP, market participants were net sellers of the stock. But does the fact that market participants have been net buyers in the early part of the regular trading session<sup>2</sup> imply that they would continue to be net buyers in the subsequent part of the regular trading session, and vice versa too? Essentially, does the price traded above or below VWAP intraday have any meaningful trend identification capacity or not? 

In order to investigate this, we study how the market behaves based on where it has traded versus VWAP. The simplest way to run this test is to create two groups of 1-minute candles based on the sign of the diference between the previous candle’s closure and VWAP. The first group, named Above VWAP, would be constituted by all the 1-minute candles whose previous 1-minute candle closure was Above VWAP. The second group, named Below VWAP, would be constituted by all the 1-minute candles whose previous 1-minute candle closure was Below VWAP. To make this clear, we created Figure 1 where group Above VWAP is colored blue while group Below VWAP is colored yellow. 

On January 2, 2018, the first day of our database, QQQ opened at $156.50. On September 28, 2023, the last day of our database, QQQ closed at $358.01. During the 5-year period, QQQ repriced higher by approximately $202 ($358.01 minus $156.50) per share<sup>3</sup>. The increase in price occurred for approximately $98 during regular trading hours (RTH, i.e., 9:30 AM–4:00 PM ET) and for approximately $104 outside regular trading hours (i.e., in pre-market 4:00 AM–9:30 AM ET and in post-market 4:00 PM–8:00 PM ET). 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/cd34683d-f8d3-44c8-a44c-634a07a00181/1e5825032970b0f9563443348983354c4a2faa32337cea58e961e4e459533222.jpg)



Figure 1: Example of an intraday chart of QQQ illustrating the concepts of what “Above VWAP” and “Below VWAP” mean. The only line in the chart is the VWAP, excluding pre- and post-market data. The 1-minute candlesticks above VWAP are colored blue (appearing dark in black and white printed editions), and the 1-minute candlesticks below VWAP are colored yellow (appearing brighter in black and white editions).


The overall upward trend of QQQ is confirmed by the percentage of 1-minute candles that closed above VWAP; approximately 56% of 1-minute candles closed above VWAP while approximately 44% of 1-minute candles closed below VWAP. 

If we sum all the 1-minute changes<sup>4</sup> for candles that belong to the group Above VWAP, we obtain the dollar repricing of QQQ when it was trading above VWAP during regular trading hours. If we sum all the 1-minute changes for candles that belong to the group Below VWAP, we obtain the dollar repricing of QQQ when it was trading below VWAP during regular trading hours. 

Figure 2 shows that when QQQ was trading Above VWAP, it repriced higher by approximately $320, while it repriced lower by approximately $280 when it was trading Below VWAP<sup>5</sup>. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/cd34683d-f8d3-44c8-a44c-634a07a00181/8e6869d41ec0299695463879da75e2cba379f28eac395b520b805b1eb342bb63.jpg)



Figure 2: Comparative repricing of a single share of QQQ from January 2, 2018, to September 28, 2023, delineated by trading periods and VWAP benchmarks. QQQ represents the overall repricing, QQQ (RTH) denotes repricing during regular trading hours (9:30 AM - 4:00 PM ET), while QQQ (Outside RTH) indicates repricing in pre-market or after-market sessions. Above VWAP and Below VWAP denote periods when QQQ was trading above or below the Volume Weighted Average Price, respectively.


This empirical analysis, based on historical data, indicates that when QQQ was subject to buying pressure, evidenced by its price trading above the VWAP, it tended to maintain that buying pressure in the minutes that followed. Conversely, when QQQ was subject to selling pressure, with its price trading below the VWAP, it tended to continue experiencing selling pressure in the subsequent minutes. 

Given our recognition of the importance of price location relative to intraday VWAP in indicating imbalances in price movements, two critical questions emerge. First, how can traders or an algorithmic trading system leverage these insights to develop an active day trading strategy that utilizes VWAP to exploit intraday market imbalances? Second, can this system significantly outperform the traditional buy-and-hold approach, especially when factoring in the commissions and fees associated with active trading? These questions guided us in formulating a novel trend trading strategy based on VWAP, which is detailed in the next section. 

## 3 Strategy Definition: VWAP Trend Trading

The goal of the strategy is to position the portfolio according to the prevailing market imbalance, as measured by the diference between the current price and the last available VWAP. The portfolio maintains a long exposure when QQQ is trading above the VWAP and reverses its exposure when the price of QQQ moves below the VWAP. No positions are held overnight. 

## 3.1 Entry Conditions, Stop Loss and Profit Target

The system waits for the first 1-minute candle to close after the U.S. market opens at 9:30am ET. At exactly 9:31:00am ET if the price of the asset is above the VWAP (not including pre- or post-market trading hours) a long (buy) position is initiated. The strategy includes setting a stop loss at the price level where a 1-minute candle closes below VWAP. The position is held throughout the trading day, with the aim of closing it at the market’s close price at 4pm ET. 

Similarly, if the first 1-minute candle opens below VWAP, the system enters a short (sell) position at the start of the following 1-minute candle. In this case, the strategy sets a stop loss at the price level where a 1-minute candle closes above VWAP, as conceptually illustrated in Figure 1. The position is maintained throughout the trading day, either until it gets stopped out or until it closes at the market’s close price at 4pm ET. 

## 3.2 Multiple Trade Occurrences

Apart from the first minute of the trading session and outside regular trading hours, the strategy always implied an open position, either long or short. This would likely result in multiple trades in each trading session. 

## 3.3 Position sizing

In this method, position size for each trade is determined by utilizing all available equity without the use of any leverage. Whenever we enter into a position, the Risk-to-Reward (R:R) ratio for the trade is unknown; in fact the stop is not fixed and depends on the time-varying VWAP. As a consequence, we cannot employ a position sizing approach typically used by traders based on a fixed risk percentage such as 0.5% or 1% per trade [3, 4, 12]. Consequently, our approach is centered around using 100% of available funds for position sizing. This ensures that the entire available capital is allocated to each trade, addressing the uncertainty surrounding the Risk to Reward ratio. 

## 3.4 Slippage and Commissions

Since we initiated our system with a small account of only $25,000, we assumed no slippage in our order fills. As our accounts in this paper grew significantly, reaching around $2 million, we recognize the potential for slippage to occur. However, based on our study of instruments such as QQQ and TQQQ, we believe that there is reasonably enough liquidity and trading volume in the market at any given time during trading day, making this assumption reasonably valid for smaller accounts. 

Nonetheless, it’s crucial to acknowledge that as account sizes increase, slippage can become a more significant concern. It’s essential to emphasize that we do not consider this system suitable for managing multi-million-dollar funds, especially within the U.S. equity markets, which inherently possess lower liquidity compared to other markets such as currencies or futures. 

For all the backtest, we factored in a commission rate of $0.0005 per share, a standard rate consistent with the majority of brokerage services in the industry, such as Interactive Brokers<sup>6</sup>. 

## 3.5 Visual Examples

The conceptual representation of some examples of this strategy and how it works in various scenarios is depicted in Figures 3 and 4. These figures provide real examples of QQQ price actions and demonstrate how they can trigger our system. They serve as illustrative scenarios only to help readers visualize the system’s operation. It is worth mentioning that a trader could implement the same strategy using a diferent timeframe, for example using 5-minutes candles. 

Figure 3 shows a scenario of how our strategy would have worked on November 10, 2023. The system waits for 1 minute, and then, since the 1-minute candle at 9:31am is below VWAP, it triggers a short trade, but it is stopped out soon. Trade 2 is long and gets stopped out when a 1-minute candlestick closes below VWAP. Trades 3 to 7 are quickly stopped-out, with each trade exiting as a candlestick closes below or above VWAP. Trade 8 happens when QQQ’s price squeezes above VWAP and continues during the day until the Close. In this example, the number of candlesticks on the 1-minute chart doesn’t exactly illustrate the full trading hours, but on November 10, 2023, QQQ never crossed VWAP after 11am, which shows Trade 8 held all the way to the close. 

Another example is illustrated in Figure 4 where the system wait 1 minute after the market Open at 9:30am. At 9:31am, since we have a candlestick above VWAP, even though that candlestick is a red candle, we initiate a long trade until it gets stopped out later when the price crosses below VWAP. Then, Trade 2 is initiated, which is a quick trade that results in stopping out because the price closes below VWAP and then suddenly squeezes back above VWAP. Trades 3, 4 and 5 are also short-lived trades until Trade 6 triggers a short position and it stays below VWAP for the remainder of the day until the close at 4pm ET. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/cd34683d-f8d3-44c8-a44c-634a07a00181/b0902c77c488d5db5c96282f714fd4f1b2bb007ca2072fe23adf2d8af238567c.jpg)



Figure 3: Scenario Illustration of QQQ Price Action on 1-Minute Chart (November 10, 2023) This figure displays the QQQ price action on a 1-minute chart on 10 November, 2023, illustrating how the VWAP strategy outlined in this paper operates. Please note that final point, representing the close, may not align precisely with the count of 1-minute candlesticks but is used for clarity and readability.


It’s essential to emphasize that if the price crosses VWAP but the candlestick does not close below or above VWAP, we do not exit the position. We only exit the position if the candlestick closes above or below VWAP, ensuring a more robust risk management approach. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/cd34683d-f8d3-44c8-a44c-634a07a00181/e22d8cd3b259678a3e466d06a2d38f498760b60449c02a2630f427ef4e13d75d.jpg)



Figure 4: Scenario Illustration of QQQ Price Action on 1-Minute Chart (November 8, 2023) In this figure, we present a scenario on a 1-minute chart to illustrate how the VWAP strategy works in a specific context. Similar to Figure 2, last point, assumed to be the market Close at 4pm, may not align precisely with the count of 1-minute candlesticks but is used for clarity and ease of comprehension.


## 3.6 Results and Discussion

Figure 5 presents a comparative analysis of the equity curve for the VWAP Trend Trading strategy alongside that of a passive investment in the benchmark, namely QQQ. The financial superiority of the active strategy is remarkable: a day trading account starting with $25,000 on January 1st, 2018, would have appreciated to $192,656 (net of commissions) by September 28th, 2023. As exhibited in Table 1, this represents a cumulative return of 671%—an average annual return of 43%. In contrast, a passive investment would have grown to $56,500, yielding a total return of 126% or an average annual return of 15%. The superiority of the VWAP Trend Trading strategy is further evidenced by its lower annualized volatility (18% compared to 25%) and a Sharpe Ratio<sup>7</sup> that is threefold higher than that of the passive investment (2.1 versus 0.7). 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/cd34683d-f8d3-44c8-a44c-634a07a00181/d3a2becf740b6022f7134aa5c387f6ea6108db1fbacec6f9a60d223d98e1501f.jpg)



Figure 5: Performance comparison between a QQQ buy-and-hold portfolio and a portfolio engaged in day trading, both long and short positions on QQQ, using the VWAP-based system described in this paper. The analysis covers the period from January 2, 2018, to September 28, 2023, with an initial net asset value of $25,000 and a commission rate of $0.0005 per share.


To further gauge the outperformance of the active strategy in excess of market risk (or benchmark risk), we ran the following regression<sup>8</sup> on daily returns: 

$$
R e t _ {V W A P \_ T T} = \alpha + \beta \times R e t _ {Q Q Q}\tag{2}
$$


Table 1: Performance comparison between a QQQ buy-and-hold portfolio and a portfolio engaged in day trading, both long and short positions on QQQ, using the VWAP-based system described in this paper. The analysis covers the period from January 2, 2018, to September 28, 2023, with an initial net asset value of $25,000 and a commission rate of $0.0005 per share.


<table><tr><td></td><td>Total Return</td><td>Average Yearly Return</td><td>Volatility</td><td>Sharpe Ratio</td><td>MDD</td></tr><tr><td>VWAP TT (QQQ)</td><td>671%</td><td>43%</td><td>18%</td><td>2.1</td><td>9.4%</td></tr><tr><td>Buy &amp; Hold (QQQ)</td><td>126%</td><td>15%</td><td>25%</td><td>0.7</td><td>35.6%</td></tr></table>

The annualized alpha is 38% (net of commissions) and is highly significant (tstat > 5). The beta coeficient is not statistically diferent from zero, which implies that our active approach was not correlated with the benchmark. This allows the active strategy to exploit two significant bear markets (the COVID-19 bear market and the 2022 bear market triggered by inflation concerns and rising interest rates) and the bullish environments that came after the economic stimulus during COVID-19. 

We believe that the trading rules underpinning the active VWAP Trend Trading portfolio render the strategy exceptionally efective during periods of extreme fear or exuberance. It is precisely during these times that significant demand or supply imbalances can spark pronounced intraday trends. 

An additional established metric for evaluating the risk of two strategies is the Maximum Drawdown (MDD). The MDD quantifies the largest percentage drop a portfolio has encountered over a specified period. In our analysis, the VWAP Trend Trading strategy underwent a MDD of around 10% in early 2019, whereas the passive portfolio tracking QQQ endured a MDD exceeding 35% in 2022. This indicates that, during its most chal lenging phase, the VWAP Trend Trading strategy’s drawdown was three times less severe than that of the passive QQQ investment. 

If a passive investor is comfortable with a 35% Maximum Drawdown (MDD), would it not be wiser to engage in a VWAP Trend Trading strategy with threefold leverage? Such a strategy is likely to exhibit similar drawdown profiles while ofering the possibil ity of substantially higher returns. In the next section we investigate how the VWAP 


Table 2: Performance comparison between a QQQ buy-and-hold portfolio, a TQQQ buy-and-hold portfolio and a portfolio engaged in day trading, both long and short positions on QQQ and TQQQ, using the VWAP-based system described in this paper. The analysis covers the period from January 2, 2018, to September 28, 2023, with an initial net asset value of $25,000 and a commission rate of $0.0005 per share.


<table><tr><td></td><td>Total Return</td><td>Average Yearly Return</td><td>Volatility</td><td>Sharpe Ratio</td><td>MDD</td></tr><tr><td>VWAP TT (TQQQ)</td><td>8,242%</td><td>116%</td><td>54%</td><td>1.7</td><td>36.1%</td></tr><tr><td>VWAP TT (QQQ)</td><td>671%</td><td>43%</td><td>18%</td><td>2.1</td><td>9.4%</td></tr><tr><td>Buy &amp; Hold (QQQ)</td><td>126%</td><td>15%</td><td>25%</td><td>0.7</td><td>35.6%</td></tr><tr><td>Buy &amp; Hold (TQQQ)</td><td>192%</td><td>21%</td><td>45%</td><td>0.6</td><td>81.7%</td></tr></table>

Trend Trading portfolio would have performed if applied on ProShares UltraPro QQQ (TQQQ<sup>9</sup>), a leveraged and liquid ETF that gives traders a 3x exposure to the daily fluctuation of QQQ. 

Using the VWAP Trend Trading rules described before, we run a backtest using 1-minute data for TQQQ. 

The results are even more astounding. With the use of TQQQ the resulting portfolio can achieve a remarkable level of returns, as depicted in Figure 6 and summarized in Table 2. The total return for active TQQQ now stands at an impressive 8,242%, with an average yearly return of 116%. A portfolio starting with $25,000 on January 2, 2018, would have appreciated to $2,085,417 (net of commissions) by September 28, 2023. 

As per our intentions, the VWAP Trend Trading strategy applied to TQQQ is now three times as volatile as the active QQQ version; its annualized volatility is 54% compared with an annualized volatility of 18% for the QQQ strategy. In line with our intentions, the Maximum Drawdown increased to 36.1%, which is one percentage point higher than those experienced by a passive buy and hold investor. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/cd34683d-f8d3-44c8-a44c-634a07a00181/ee9fae46ed5883d09211b227189afd7a097ade39449196d8cdb4b0ef5d9882af.jpg)



Figure 6: Performance comparison between a QQQ buy-and-hold portfolio, a portfolio engaged in day trading, both long and short positions on QQQ based on 1-min candlestick using the VWAP-based system described in this paper and a portfolio of day trading TQQQ based on this approach. The analysis covers the period from January 1, 2018, to September 28, 2023, with an initial net asset value of $25,000 and a commission rate of $0.0005 per share.


Furthermore, the Sharpe Ratio remains strong at 1.7, nearly 2.5 times higher than the simple Buy & Hold on QQQ. This signifies that for the same amount of risk, the active TQQQ strategy produces a return that is 2.5 higher than what can be achieved with a passive QQQ position. 

The annualized alpha is 93% (net of commissions) and is highly significant (tstat > 4). The beta coeficient remained not statistically diferent from zero, implying no market dependency 

## 3.7 Commissions, Volume and Other Key Performance Metrics

We have seen from visual example that the VWAP Trend Trading strategy could incur in multiple trades per day, with the goal of riding as much as possible the trends once established. In this section, we investigate more in details the impact of commissions incurred during the backtested period that span from January 2, 2018 until September 28, 2023. 

As shown in Table 3, the VWAP day trading system on TQQQ starting with a capital of $25,000, concludes with a substantial profit exceeding $2 million, while incurring commissions totaling $400,616. In contrast, the VWAP day trading system for QQQ, with a total commission of only $6,547, achieves an ending capital of $192,656. During the backtested period, the VWAP Trend Trading strategy on QQQ traded approximately 13 million shares, while the TQQQ version accounted for roughly 800 million shares traded. The active VWAP strategies incurred about 22,000 trades. It is important to note that the total number of trades is similar, though not exactly the same. This diference is due to the inherent variations in TQQQ’s price movements. Although TQQQ generally follows QQQ’s intraday trends, it is not perfectly identical, primarily because of the leverage involved and temporary deviations from theoretical prices. As expected, the number of shares traded in the Buy & Hold version is significantly lower, at 160 shares, since only one trade occurred at the start of the backtested period. 

In our next segment, we delve into the summary statistics for trades executed under the VWAP Trend Trading strategy, applied to both QQQ and TQQQ. As illustrated in Table 4, the Hit Ratio, or Accuracy Ratio, stands at approximately 17%. This implies that out of every 100 trades, we made money in only 17 trades. Such a ratio is typical for trend trading strategies that capitalize on intraday price movements. Despite the seemingly low accuracy, the strategy is balanced by a favorable positive asymmetry between gains and losses. On average, gains per trade are 5.5 times greater than the losses. 


Table 3: Volume, Trades, and Commission Analysis for VWAP Trend Trading on QQQ and TQQQ from January 2, 2018, to September 28, 2023. Initial NAV: $25,000; Commission: $0.0005/share.


<table><tr><td></td><td>Start Capital</td><td>End Capital</td><td>Shares Traded</td><td>Commission Paid</td><td># Trades</td></tr><tr><td>VWAP TT (TQQQ)</td><td>$25,000</td><td>$2,085,417</td><td>801,237,880</td><td>400,619</td><td>22,399</td></tr><tr><td>VWAP TT (QQQ)</td><td>$25,000</td><td>$192,656</td><td>13,094,444</td><td>6,547</td><td>21,967</td></tr><tr><td>Buy &amp; Hold (QQQ)</td><td>$25,000</td><td>$56,472</td><td>160</td><td>0.080</td><td>1</td></tr><tr><td>Buy &amp; Hold (TQQQ)</td><td>$25,000</td><td>$73,108</td><td>2,129</td><td>1.1</td><td>1</td></tr></table>


Table 4: Trades Performance Metrics for the VWAP Trend Trading strategy on QQQ and TQQQ from January 2, 2018, to September 28, 2023. Initial NAV: $25,000. Commission: $0.0005 per share.


<table><tr><td rowspan="2"></td><td colspan="4">Trade</td><td colspan="2">Daily</td></tr><tr><td>Hit Ratio</td><td>Gain : Loss</td><td>Max Gain</td><td>Max Loss</td><td>Max Gain</td><td>Max Loss</td></tr><tr><td>VWAP TT (TQQQ)</td><td>17.2%</td><td>5.48</td><td>20.9%</td><td>-4.1%</td><td>20.9%</td><td>-22.7%</td></tr><tr><td>VWAP TT (QQQ)</td><td>17.0%</td><td>5.67</td><td>6.5%</td><td>-1.4%</td><td>6.5%</td><td>-5.1%</td></tr><tr><td>Buy &amp; Hold (QQQ)</td><td></td><td></td><td></td><td></td><td>8.5%</td><td>-12.3%</td></tr><tr><td>Buy &amp; Hold (TQQQ)</td><td></td><td></td><td></td><td></td><td>27.0%</td><td>-34.5%</td></tr></table>

During the backtested period, the most successful trade in the QQQ version yielded a return of 6.5% on the invested capital. In comparison, the TQQQ version, leveraging the same strategy, saw its highest single trade return surge to about 21%, nearly thrice that of QQQ. The worst trade recorded returns -1.4% for QQQ and -4.1% for TQQQ. 

Notably, the maximum daily gain for the VWAP trend trading portfolio in QQQ was 6.5%, while the most challenging day ended with a 5.1% loss, likely attributed to a meanreverting day with numerous false VWAP breaks. For TQQQ, the extremes were even more pronounced: the best day saw a 20.9% gain, while the worst plummeted to a -22.7% loss, paralleling the QQQ experience on a mean-reverting day. 

Interestingly, despite deploying the same level of leverage as the active QQQ strategy, the Buy & Hold portfolio exhibited a maximum daily loss of -12.3% (the Nasdaq index dropped 12.3%, its largest percentage loss ever on 16 March 2020 because of Covid-19 pandemic), which is more than double the most substantial daily loss (-5.1%) in the QQQ VWAP Trend Trading portfolio. This observation underscores the potential risks and rewards inherent in these difering approaches to trading. 

## 4 VWAP, the Holy Grail Indicator for Intraday Trend Trading?

When it comes to intraday trading, active traders often rely on a variety of technical indicators to guide their decisions. Among the plethora of tools available, the Simple Moving Average (SMA), Exponential Moving Average (EMA), Donchian Channels, Keltner Bands, and the Volume Weighted Average Price (VWAP) stand out as popular choices. 

The SMAs is particularly similar to the VWAP in that they all track price movements over time, which helps traders identify trends within specific timeframes. The SMA is calculated by taking the arithmetic mean of a stock’s price over a certain period. 

The critical distinction between SMA and the VWAP lies in the use of volume data. While the SMA solely consider price data, the VWAP also incorporates volume information, providing a more comprehensive view of the market. This volume data allows the VWAP to give a weighted average price that reflects both the price and the quantity of securities traded, which can be particularly valuable for assessing the market’s direction within the trading day. 

Therefore, while the SMA can provide insights into market trends, the VWAP’s inclusion of volume data ofers a unique perspective that can be crucial for intraday traders looking to capture trends as they develop. 

Similar to pharmaceutical experiments where a study group is administered a drug and another group receives a placebo as a control group, we found it intriguing to determine whether the outperformance of our VWAP Day Trading System is primarily attributed to VWAP itself or if a system based on any moving average used for trend detection can significantly outperform a Buy and Hold strategy. Therefore, we conducted a comparison by considering four important and commonly used intraday moving averages: 9, 20, 100, and 200 simple moving averages (SMA). 


Table 5: Summary Statistics for diferent Intraday Trend trading Strategies on QQQ from January 1, 2018, to September 28, 2023. Initial NAV: $25,000. Commission: $0.0005 per share.


<table><tr><td></td><td>Total Return</td><td>Avg. Yearly Return</td><td>Vol.</td><td>Sharpe Ratio</td><td>MDD</td><td># Trades</td><td>Trade Hit Ratio</td><td>Trade Gain: Loss</td></tr><tr><td>VWAP TT (QQQ)</td><td>671%</td><td>43%</td><td>18%</td><td>2.1</td><td>9%</td><td>21,967</td><td>17%</td><td>5.7</td></tr><tr><td>SMA9</td><td>202%</td><td>21%</td><td>16%</td><td>1.3</td><td>41%</td><td>107,067</td><td>30%</td><td>2.4</td></tr><tr><td>SMA20</td><td>49%</td><td>8%</td><td>16%</td><td>0.5</td><td>42%</td><td>69,847</td><td>25%</td><td>3.0</td></tr><tr><td>SMA100</td><td>83%</td><td>12%</td><td>18%</td><td>0.7</td><td>17%</td><td>30,924</td><td>18%</td><td>4.8</td></tr><tr><td>SMA200</td><td>135%</td><td>17%</td><td>19%</td><td>0.9</td><td>21%</td><td>22,005</td><td>16%</td><td>5.8</td></tr><tr><td>Buy &amp; Hold (QQQ)</td><td>126%</td><td>17%</td><td>25%</td><td>0.7</td><td>36%</td><td></td><td></td><td></td></tr></table>

As exhibited in Table 5, the results remain fascinating. The VWAP day trading system consistently demonstrates significant outperformance over any day trading system that relies on moving averages as its trend trading signal. Notably, the strategy with the highest execution frequency is the SMA9, registering over 100,000 diferent trades. In contrast, the SMA100 and SMA200 strategies show a significant reduction in trade frequency, with approximately 31,000 and 22,000 trades, respectively. While faster moving averages exhibit better Hit Ratios, they also show a lower asymmetry between gains and losses. 

The exceptional performance of the VWAP Trend Trading portfolio is further underscored if we consider that it has the highest average annualized return (43%) with the best Maximum Drawdown (9%). This implies that the VWAP Trend Trading portfolio was not only the most lucrative strategy but also the one that managed risk most efectively. 

These superior results achieved with our VWAP Trend Trading strategy can be attributed to several key factors: 

1. Short-term moving averages (e.g., SMA9, SMA20) tend to generate numerous trading signals that, over time, result in a significant amount of commission expenses. 

2. Long-term moving averages (e.g., SMA100, SMA200) can be less efective during the early part of the trading session, as they are often influenced by premarket prices with low-volume confirmation. 

3. After a large intraday move, a sudden reversal sustained by volume will quickly trigger a reverse signal for the VWAP. This allows to protect unrealized gains. Trend portfolio built on SMA100 and SMA200 would be slower to react, and the reversal would erase a big portion of unrealized gains. 

## 5 Time of Day and The Urgency to Act

In previous sections, we have seen that VWAP is an efective trend trading indicator that can help active traders to eficiently ride intraday trends. Here we investigate if there are times of day when VWAP is more or less efective. To run this test, we grouped all the 1-minute PnLs occurred in the QQQ VWAP Trend Trading strategy<sup>10</sup> based on the time of day; for example, Group 1 is constituted by all the PnL occurred between 9:31am and 9:32am, Group 2 is constituted by all the PnL occurred between 9:32am and 9:33am, and so on. Then we sum all the 1-minute PnLs within each group. This would represent the overall strategy performance (per share) occurred from 2018 until 2023 in each minute of the day. As a final step, we take the cumulative sum of all these 1-minute overall repricing. 

The cumulative sum of the 1-minute PnL is exhibited in Figure 7. The overall profitabil ity of a VWAP Trend Trading strategy that traded only 1 share of QQQ would have been approximately $600<sup>11</sup>. As can be easily grasped from the chart, most of the profits came from the early part of the day (9:30am-12pm ET) and on the last hour of the trading session (3pm-4pm). This implies that a more cost-eficient implementation of the VWAP Trend trading strategy may avoid trading between 12pm and 3pm. 

Although delving into the economic reasons behind the time-of-day seasonality of the VWAP indicator falls outside the scope of this paper, we can outline some potential explanations for this phenomenon. As highlighted in the introduction of this paper, the 


Time of Day Profitability VWAP Trend Trading (QQQ)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/cd34683d-f8d3-44c8-a44c-634a07a00181/b0f252ab6ee33732eadd3e05df0afb02cf3b90ca4828df607695e71ac4319b62.jpg)



Figure 7: Cumulative PnL analysis by Time-of-Day using the VWAP Trend Trading Strategy on a Single Share of QQQ, from January 2, 2018, to September 28, 2023. This analysis groups intraday PnL by each minute of the trading day. For each minute, we calculate the total PnL occurrences, followed by a cumulative sum. The chart’s aim is to investigate potential intraday VWAP seasonality. Notably, during the morning session and the final trading hour, the price often trends in accordance with the VWAP direction (upward if above VWAP, downward if below). Conversely, the mid-session shows no significant trend characteristics.


VWAP (Volume Weighted Average Price) is utilized by institutional investors to assess the eficiency of executing large orders throughout the day. When a trader is tasked with executing a large order, whether buying or selling, they are confronted with two primary risks: the possibility of executing at a suboptimal price relative to the end-of-day VWAP, or the challenge of incomplete execution due to waiting for a more favorable price that ultimately does not materialize. Building on this premise, the following behaviors could explain the pattern observed in Figure 7: 

1. During the initial phase of the trading session, a trader who anticipates the VWAP to exhibit a trending behavior throughout the day might be inclined to quickly execute his entire order as soon as the market begins to move with the VWAP’s direction. This could result in a positive feedback loop, intensifying the early session’s movement, whether upwards or downwards. 

2. Alternatively, a trader might choose to wait for a more advantageous price following a significant early session move. If, however, the price does not revert to the VWAP during the midday period, the trader may be compelled to act in the final trading hour to complete his order. This urgency could exert additional pressure on the stock, leading to a pronounced trend in alignment with the VWAP’s direction. 

## 6 Conclusion

Our research, covering the period from January 2, 2018, to September 28, 2023, compellingly demonstrates the superiority of the VWAP-based trading strategy over conventional buy-and-hold methods. The VWAP Trend Trading strategy applied to QQQ achieved a remarkable 671% return (net of commissions), with a maximum drawdown of 9.4% and an impressive Sharpe ratio of 2.1. This period, which includes two bear markets and several instances of abnormal volatility, provides a robust test of the strategy’s resilience. 

In comparison, during the same period, a buy-and-hold strategy on QQQ yielded a total return of 126%, along with a maximum drawdown of 37%, a maximum daily loss of 12%, and a Sharpe ratio of 0.7. 

Extending the strategy to TQQQ resulted in an extraordinary 8,242% return, amounting to an average yearly return of 116%. Notably, this approach achieved a similar maximum drawdown as a passive QQQ investment, highlighting its efectiveness in risk management while amplifying returns. 

While the study highlights the potential challenges, such as the impact of commissions and the frequency of trades, the overall performance and risk-adjusted returns of the VWAP-based strategy remain notably superior. 

This research reafirms the significance of VWAP in intraday trading over the specified period and encourages further exploration into algorithmic strategies. As a result, this paper serves as a critical resource for traders and quantitative analysts, providing a statistically robust and empirically validated approach to enhance trading methodologies. 

# Author Biography

Andrew Aziz 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/cd34683d-f8d3-44c8-a44c-634a07a00181/ee7e2f705df344af503e230ac70606826f1e6974c9182cbfe8bf7dc005648b23.jpg)


## Carlo Zarattini

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/cd34683d-f8d3-44c8-a44c-634a07a00181/fc37b8f7d6daba697b222d4852c1636cd342ed90322bea3ecdc307fd871f08c5.jpg)


Andrew Aziz is a Canadian trader, investor, and oficial Forbes Council member. He has ranked as one of the top 100 bestselling authors in ”Business and Finance” for 7 consecutive years from 2016 to 2023. Aziz’s book on finance has been published in 13 different languages. Originally from Iran, Andrew moved to Canada in 2008 to pursue a PhD in chemical engineering, initiating a distinguished career in academia and industry. As a research scientist, Andrew made signif icant contributions to the field, authoring 13 papers and securing 3 US patents. Following a successful stint in research in chemical engineering and clean technology, he transitioned to the world of trading. Currently Andrew is a trader and proprietary fund manager at Peak Capital Trading in Vancouver, BC Canada. 

Carlo Zarattini, originally from Italy, currently resides in Lugano, Switzerland. After completing his mathematics degree in Padova, he pursued a dual master’s in quantitative finance at Imperial College London and USI Lugano. He formerly served as a quantitative analyst at BlackRock, where he developed volatility and trendfollowing trading strategies. Carlo later established Concretum Research, assisting institutional clients with both high and medium-frequency quantitative strategies in stocks, futures, and options. Additionally, he founded R-Candles.com, the first backtester for discretionary technical traders. 

## References



[1] A. H˚akansson, F. Fern´andez-Aranda, and S. Jim´enez-Murcia. Gambling-like day trading during the covid-19 pandemic – need for research on a pandemic-related risk of indebtedness and mental health impact. Front Psychiatry, 12:1276, Jul 2021. 





[2] R. Caferra and D. Vidal-Tom´as. Who raised from the abyss? a comparison between cryptocurrency and stock market dynamics during the covid-19 pandemic. Financ Res Lett, 43, 2021. 





[3] Andrew Aziz. Advanced Techniques in Day Trading: A Practical Guide to High Probability Strategies and Methods. AMS Publishing Group, 2018. 





[4] Andrew Aziz. How to Day Trade for a Living: A Beginner’s Guide to Trading Tools and Tactics, Money Management, Discipline and Trading Psychology. AMS Publishing Group, 4 edition, 2015. 





[5] C. Zarattini and A. Aziz. Can day trading really be profitable? evidence of sustainable long-term profits from opening range breakout (ORB) day trading strategy vs. benchmark in the us stock market. SSRN Electronic Journal, Apr 2023. 





[6] D. Arumugam. Algorithmic trading: Intraday profitability and trading behavior. Econ Model, 128:106521, Nov 2023. 





[7] J. Bia lkowski, S. Darolles, and G. Le Fol. Improving vwap strategies: A dynamic volume approach. J Bank Financ, 32(9):1709–1722, Sep 2008. 





[8] J. H. Choi, K. Larsen, and D. J. Seppi. Equilibrium efects of intraday order-splitting benchmarks. Mathematics and Financial Economics, 15(2):315–352, Mar 2021. 





[9] A. F. Darrat, S. Rahman, and M. Zhong. Intraday trading volume and return volatility of the djia stocks: A note. J Bank Financ, 27(10):2035–2043, Oct 2003. 





[10] C. Der Fuh, H. W. Teng, and R. H. Wang. On-line vwap trading strategies. Seq Anal, 29(3):292–310, 2010. 





[11] B. Shannon. Maximum Trading Gains With Anchored VWAP: The Perfect Combination of Price, Time and Volume. 2023. 





[12] Alexander Elder. Trading for a Living: Psychology, Trading Tactics, Money Management. Wiley, 1 edition, 2014. 

