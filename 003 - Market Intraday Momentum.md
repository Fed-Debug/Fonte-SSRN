# Market Intraday Momentum<sup>∗</sup>

Lei Gao Iowa State University and Yufeng Han University of North Carolina at Charlotte and Sophia Zhengzi Li Rutgers University and Guofu Zhou Washington University in St. Louis<sup>†</sup> 

First Draft: March, 2014 Current Version: June, 2017 

<sup>∗</sup>We are grateful to Vincent Bogousslavsky, Phil Dybvig, Campbell Harvey, Steve Heston, Dashan Huang, Ryan Israelsen, Ohad Kadan, Aditya Kaul, Naveen Khanna, Hong Liu, Zhongjin Lu, Stefan Nagel, Matthew Ringgenberg, Ronnie Sadka, Matthew Spiegel, Robert Stambaugh, Avanidhar Subrahmanyam, Jack Vogel, Daniel Webb, Mao Ye, seminar participants at Michigan State University, Rutgers University, Shanghai Advanced Institute of Finance, Singapore Management University, Southwestern University of Finance and Economics, University of Missouri, Washington University in St. Louis, and Wuhan University, and conference participants at the 2014 Tsinghua University Workshop, 2014 International Symposium on Financial Engineering and Risk Management, 2014 Financial Management Association meeting, 2015 Mid-Atlantic Research Conference in Finance, 2015 ITAM Finance Conference, and 2015 NFA Conference for helpful comments. 

<sup>†</sup>Correspondence: Guofu Zhou, Olin School of Business, Washington University, St. Louis, MO 63130; e-mail: zhou@wustl.edu, phone: (314) 935-6384. 

# Market Intraday Momentum

## Abstract

Based on high frequency data of the S&P 500 ETF from 1993–2013, we document an intraday momentum pattern: the first half-hour return on the market since the previous day’s market close predicts the last half-hour return. The predictability, both statistically and economically significant, is stronger on more volatile days, on higher volume days, on recession days, and on major macroeconomic news release days. This intraday momentum is also present for ten other most actively traded domestic and international ETFs. Theoretically, the intraday momentum is consistent not only with Bogousslavsky’s (2016) model of portfolio infrequent rebalancing, but also with a model of trading on late-informed news near the market close. 

JEL Classification: G11, G14 

Keywords: Predictability, Intraday, Momentum, Economic Value 

## 1 Introduction

Since the seminal work of Jegadeesh and Titman (1993), it has been well-known that winners (losers) over the past six months to a year tend to continue to be winners (losers) over the next six months to a year. Grifin, Ji, and Martin (2003) show that momentum like this is common in global stock markets. In addition to this cross-section momentum, Moskowitz, Ooi, and Pedersen (2012) and Asness, Moskowitz, and Pedersen (2013) recently find evidence that time-series momentum, where previous 12-month returns of an asset positively predict its future returns, is pervasive across asset classes such as equities, bonds, and currencies. To the best of our knowledge, however, almost all momentum studies are confined to return patterns at the monthly or weekly frequency.<sup>1</sup> An open question is whether such return patterns can be observed at the intraday level. This question is critical to understanding intraday market eficiency and the role played by a growing number of high-frequency traders. 

In this paper, we provide the first study on intraday momentum, contributing in a unique way to the large literature on momentum studies. Specifically, we find that the first halfhour return on the market since the previous day’s market close significantly predicts the last half-hour return on the market. 

Why are the first and last half-hours of a trading day so special? Almost all earnings and most major economic news are released before the market opens, and hence the market typically opens at a new level from the previous day that reflects new information. The digestion of the news usually takes about 30 minutes, as evident from the high volume and high volatility in the first half-hour of trading, and then the market cools of until the last half-hour. The volume and volatility display a U-shape during the day, with the high volume and high volatility in the last half-hour signaling the importance of market close. As emphasized by Cushing and Madhavan (2000) and Foucault, Kadan, and Kandel (2005), institutional traders place enormous emphasis on closing stock prices, which are used to calculate portfolio returns, tally the net asset values of mutual funds, and marking-tomarket various financial contracts; and at the same time, the market makers want to unload inventory to avoid exposures to overnight risk. Hence, on a typical trading day, the first and last-half hours are the most important. In this paper, we empirically document an interesting positive correlation between their returns. 

In our empirical analysis, we measure the market return by using the tradable SPY, the most actively traded ETF that tracks the S&P 500.<sup>2</sup> The predictive $R ^ { 2 }$ of the first half-hour return on the last half-hour return is 1.6%, a level matching or exceeding a typical predictive $R ^ { 2 }$ at the monthly frequency (see, e.g., Rapach and Zhou, 2013). If the first half-hour return is combined with the twelfth half-hour return (the half-hour before the last half-hour), the $R ^ { 2 }$ increases further to 2.6%. The predictability is significant not only in sample, but also out of sample (OS). The $R _ { O S } ^ { 2 }$ is 1.4% using the first half-hour return as the only predictor, and 2.0% when this predictor is combined with the twelfth half-hour return predictor. Similar to the in-sample results, the OS predictability is also greater than those typically found at the monthly frequency. 

We document that the predictability rises generally with volatility. For instance, when the first half-hour volatility is high, the $R ^ { 2 }$ increases to 3.3% for the combined predictors. The predictability is also stronger during the recent financial crisis. In addition, the predictability of the first half-hour return stays quite similar across stocks with high or low liquidity and institutional holdings, while that of the twelfth half-hour return varies. Furthermore, the overall predictability is greater on low trade size (in the last half-hour) days, recession days, or days with certain major economic news. 

In terms of economic significance, the predictability based on the first half-hour return can generate an extra risk-adjusted return or “certainty equivalent gains” of 6.02% per annum versus ignoring the predictor for a mean-variance investor with a risk aversion of 5. The gains can further improve to 6.18% per annum if the twelfth half-hour return predictor is used in addition. In terms of market timing, the economic value is also substantial – the average return of the timing strategy using the sign of the first half-hour return is 6.67% per annum with a standard deviation of 6.19%. The Sharpe ratio is thus 1.08, fairly remarkable compared to a level of 0.29 for a daily Buy-and-Hold strategy which delivers an average return of 6.04% per annum with a standard deviation of 20.57%. Moreover, the outperformance remains significant even after accounting for transaction costs, which become increasingly lower due to quote decimalization in 2001 and advances in trading technology. Overall, the intraday momentum is both statistically and economically significant out of sample. 

From the perspective of microfoundations, there are two economic explanations for the intraday momentum. First, Bogousslavsky (2016) shows theoretically that our intraday momentum can be driven by investors’ infrequent rebalancing to their portfolios. Due to the slow-moving of capital and various institutional factors, some institutional investors may rebalance their portfolios in the first half-hour, and others may do so in the last halfhour. Trading in the last half-hour in the same direction as the first can generate the intraday momentum pattern. The second explanation is based on the presence of lateinformed investors who trade the early morning information in the last half-hour. For those who are informed late or are slow in information processing, trading in the last half-hour is desirable to avoid overnight risk and to take advantage of the high liquidity. Thus, informed trading in the last half-hour in the same direction as the first half-hour can also generate the intraday momentum. 

The intraday momentum is quite robust. It persists after accounting for reasonable transaction costs, and is not only limited to the S&P 500 ETF, but also strong and significant for ten other most actively traded ETFs in the US.<sup>3</sup> These ETFs represent alternative stock indices, such as the Dow, the NASDAQ, and the Russell 2000. They also cover financial, real estate, bond and certain international equity indices. Interestingly, perhaps due to their lower liquidity, the out-of-sample predictability and the certainty equivalent gains on these ETFs are often greater than those on the S&P500 ETF.<sup>4</sup> 

Our paper is related to the literature on intraday asset prices. Many of the existing studies have been focused on trading activity and volatility (see, e.g., Chordia, Roll, and Subrahmanyam, 2011; Corwin and Schultz, 2012). Heston, Korajczyk, and Sadka (2010) seem to be the only study that is closely related to ours. They find a striking pattern that returns on certain individual stocks tend to be persistent at the same half-hour intervals across trading days, and that this pattern can last for up to 40 trading days. Bogousslavsky (2016) explains this unique correlation in detail in his theoretical model on infrequent rebalancing. In contrast to these studies, we analyze market intraday momentum, namely the predictability of the market’s first half-hour return for the market’s last half-hour return on the same day. 

The remainder of the paper is organized as follows. Section 2 describes the data we use in the analysis. Section 3 presents the main results of the intraday momentum and ofers two explanations. Section 4 discusses the economic significance of our main finding. Section 5 presents the impact of macro events on the intraday momentum. Section 6 details a series of robustness checks. Section 7 concludes. 

## 2 Data

We use the intraday trading prices of the actively traded S&P 500 ETF, SPY, from the Trade and Quote database (TAQ) to compute half-hour returns. The sample period spans from 

February 1, 1993 through December 31, 2013.<sup>5</sup> We exclude any trading days with fewer than 500 trades.<sup>6</sup> For major news releases, we obtain the historical release dates of the Michigan Consumer Sentiment Index (MCSI) from the University of Michigan; the historical release dates of the GDP estimate from the Bureau of Economic Analysis; the historical release dates of the CPI from the Bureau of Labor Statistics; and the historical release dates of the Federal Open Market Committee (FOMC) minutes from the Federal Reserve Bank.<sup>7</sup> 

Specifically, to examine the intraday return predictability on any trading day t, we calculate the first half-hour return using previous day’s close price and the price at 10:00am Eastern Time, and then every half-hour (30-minute) return from 10:00am to 4:00pm Eastern Time. This gives us a total of 13 half-hour observations per day, 

$$
r _ {j, t} = \frac {p _ {j , t}}{p _ {j - 1 , t}} - 1, \qquad j = 1, \dots , 1 3,\tag{1}
$$

where $p _ { j , t }$ is the price at the j-th half-hour, and $p _ { j - 1 , t }$ is the price at the previous half-hour, for $j = 1 , \dots ,$ 13. Note that $p _ { 0 , t }$ is the previous trading day’s price at the $1 3 ^ { t h }$ half-hour (4:00pm Eastern Time). That is, we use the previous trading day’s closing price as the starting price in calculating the first half-hour return on day t, i.e., $p _ { 0 , t } = p _ { 1 3 , t - 1 }$ , so that the first half-hour return captures the impact of information released after the previous day’s market close. To assess the impact of return volatility on return predictability, we also compute the volatility of the first half-hour return in two steps. First, we calculate the returns minute by minute within the first half-hour. Then, we compute the realized volatility using the estimated one-minute returns to obtain an estimate of the volatility of the first half-hour. 

## 3 Intraday Momentum

## 3.1 Predictive regression analysis

Consider first the simple predictive regression of the last half-hour return on the first halfhour return: 

$$
r _ {1 3, t} = \alpha + \beta r _ {1, t} + \epsilon_ {t}, \qquad t = 1, \dots , T,\tag{2}
$$

where $r _ { 1 3 , t }$ and ${ \boldsymbol { r } } _ { 1 , t }$ are the last half-hour return and the first half-hour return on day t, respectively, and $T$ is the total number of trading days in the sample. 

Panel A of Table 1 reports the results. The first half-hour return, $r _ { 1 }$ , positively predicts the last half-hour return, $r _ { 1 3 }$ , with a scaled (by 100) slope of 6.94, statistically significant at the 1% level, and an $R ^ { 2 }$ of 1.6%. Such a high predictive $R ^ { 2 }$ is impressive, as almost all typical predictors have lower $R ^ { 2 } \mathrm { s }$ (see, e.g., Rapach and Zhou, 2013). Note that the same level of $R ^ { 2 }$ is better at a higher frequency than at a lower one as more trades can be carried out utilizing the predictability. 

The twelfth half-hour $( \mathrm { i . e . }$ , the second-to-last half-hour), $r _ { 1 2 }$ , may also afect the last halfhour return if there is a strong price persistence during the day. The second column in Panel A of Table 1 reports the regression result using this predictor. It is clear that $r _ { 1 2 }$ predicts $r _ { 1 3 }$ at the $1 \%$ significance level with an $R ^ { 2 }$ of 1.1%. We later show that this predictability largely comes from the recent financial crisis period, while that of the first half-hour return is always significant whether there is a crisis or not. 

Since $r _ { 1 }$ or $r _ { 1 2 }$ predicts $r _ { 1 3 }$ individually, how do they predict $r _ { 1 3 }$ jointly? The third column in Panel A of Table 1 reports the predictive regression results using both predictors. Surprisingly, the slopes barely change from their individual regression values. Moreover, the joint $R ^ { 2 }$ , 2.6%, is roughly equal to the sum of the individual $R ^ { 2 } \mathrm { s }$ . The evidence suggests that $r _ { 1 }$ and $r _ { 1 2 }$ are independent and complementary in forecasting the last half-hour return. 

## 3.2 Out-of-sample predictability

Our previous intraday momentum analysis is based on the entire sample (in-sample) estimation. While in-sample estimation is econometrically more eficient if regressions are stable over time, as shown in the next subsection, the financial crisis clearly destabilizes the estimation. At the monthly frequency, Welch and Goyal (2008) find that many macroeconomic predictors sufer from an instability problem, and their predictability largely vanishes once predictive regressions are estimated recursively out-of-sample (OS). Thus, in-sample predictability does not necessarily imply OS predictability. 

To assess whether the intraday momentum persists out of sample, we run recursive regressions similar to other predictability studies at the monthly frequency. That is, to forecast return at any time t, we use data only up to time t − 1. Starting the regression using returns before January 3, 1998, we progressively add one more month of returns each time to form the OS forecasts. Following Campbell and Thompson (2008), Rapach, Strauss, and Zhou (2010), Ferreira and Santa-Clara (2011), Henkel, Martin, and Nardari (2011), and Neely, Rapach, Tu, and Zhou (2014), among others, we measure the OS predictability by using, 

$$
R _ {O S} ^ {2} = 1 - \frac {\sum_ {t = 1} ^ {T} (r _ {1 3 , t} - \hat {r} _ {1 3 , t}) ^ {2}}{\sum_ {t = 1} ^ {T} (r _ {1 3 , t} - \bar {r} _ {1 3 , t}) ^ {2}},\tag{3}
$$

where $\hat { r } _ { 1 3 , t }$ is the forecasted last half-hour return from the predictive regression estimated through period t − 1, and $\bar { r } _ { 1 3 , t }$ is the historical average forecast estimated from the sample mean through period t − 1. A positive $R _ { O S } ^ { 2 }$ indicates that the predictive regression forecast beats the simple historical average. $R _ { O S } ^ { 2 } > 0$ implies predictability. Welch and Goyal (2008) show that it is not an easy matter for a predictor to beat the historical average benchmark. 

Panel B of Table 1 reports the results. When we use the first half-hour return alone, the 

$R _ { O S } ^ { 2 }$ is 1.4%. When we use the twelfth half-hour return alone, the $R _ { O S } ^ { 2 }$ is 0.9%. When we use both of them, the $R _ { O S } ^ { 2 }$ achieves its highest value of 2.0%. The $R _ { O S } ^ { 2 } \mathrm { ^ { * } s }$ match or exceed those at the monthly frequency. As shown by Campbell and Thompson (2008) for monthly returns, and confirmed here later, these levels of $R _ { O S } ^ { 2 }$ ’s are of substantial economic significance. 

## 3.3 Financial crisis

The recent financial crisis is clearly a big outlier in the time series of market returns. The standard monthly momentum strategy is known to have performed poorly during the crisis period. Thus, it is interesting to study how well the intraday momentum performs in this period. 

Panel A of Table 2 reports the predictive regression results from December 2, 2007 through June 30, 2009. The predictive power of $r _ { 1 }$ becomes stronger, with a larger slope of 13.6 and a higher $R ^ { 2 }$ of 4.1%. Moreover, the two predictors combined yield an amazingly high $R ^ { 2 }$ of 6.9%, rarely seen anywhere else. It is noteworthy that the predictive powers of $r _ { 1 }$ and $r _ { 1 2 }$ are still complementary during the crisis period. 

Panel B of the table, for comparison, provides the results excluding those crisis days. The performance clearly becomes much weaker. Although $r _ { 1 2 }$ is less significant, $r _ { 1 }$ remains a powerful predictor of $r _ { 1 3 }$ with a sizable $R ^ { 2 }$ of 0.8%, comparable to many good predictors at the monthly frequency. The combined predictors yield a higher $R ^ { 2 }$ of 1.1%. Therefore, in despite of the financial crisis, there is no doubt for the validity of intraday momentum over the entire sample period. 

To further assess the relation between the intraday momentum and the crisis, Panel C and D of Table 2 report the predictive regression results for the pre- and post-crisis periods. It is interesting that the predictability of $r _ { 1 }$ stays roughly the same in terms of its slope. However, the predictability of $r _ { 1 2 }$ is greater in the post-crisis period, albeit not statistically significant in either period. Note that the insignificant result here is due in part to the sample size of the post-crisis period. In contrast, the earlier periods excluding the crisis have a much larger sample size, and so the $r _ { 1 2 }$ there becomes significant. 

To see whether the intraday momentum has any time trends, which is relevant given the increasing market volume and liquidity over the years, Figure 1 plots the slopes of $r _ { 1 }$ and $r _ { 1 2 }$ . The slopes are estimated recursively over time. That is, on any day t, all data up to this day are used for the estimation, which is what investors may do in practice to form an out-of-sample forecast of the return on day t + 1. It is seen that, after some initial volatility, the slope of $r _ { 1 }$ is fairly stable before the crisis, but increases later due the influence of the crisis. In contrast, the slope of $r _ { 1 2 }$ is more volatile, and it rises much more after the crisis. Overall, the predictability of $r _ { 1 }$ , which is the main predictor that drives intraday momentum, is fairly stable overtime. 

## 3.4 Volatility and Volume

Given that the financial crisis is characterized by high volatility, a question arises as to how volatility impacts the intraday momentum in general. To address this question, we sort all the trading days, according to the first half-hour volatility, into three groups (terciles): low, medium, and high volatility days. For brevity, we only consider the case of joint predictors $r _ { 1 }$ and $r _ { 1 2 }$ 

Panel A of Table 3 reports the results. The predictability appears to be an increasing function of volatility. When the first half-hour volatility is low, the predictability is minimal, with an $R ^ { 2 }$ of 0.6% and an insignificant coeficient for $r _ { 1 }$ . At the intermediate volatility level, the $R ^ { 2 }$ rises to 1.0%, which is economically significant, and the coeficient of $r _ { 1 }$ becomes highly significant. Finally, when the first half-hour volatility is high, the $R ^ { 2 }$ increases more than five times to as high as 3.3% compared to the low volatility case. 

Overall, the intraday momentum seems highly related to volatility. The higher the volatility, the greater the predictability. This appears consistent with the empirical results of Zhang (2006) that the greater the uncertainty, the stronger the persistence of a trend. In our context, the greater the volatility, the greater the likelihood that the first half-hour trend carries over to the last half-hour. 

A related topic of interest is how volume impacts the intraday momentum, since the first half-hour trading is characterized by both high volatility and high volume. Because trading volume increases over the years, we sort the trading days year-by-year, according to the first half-hour trading volume, into three equal groups: low, medium and high volume days. Panel B of Table 3 reports the results. Similar to the case under diferent volatility regimes, the predictability, as judged by the $R ^ { 2 } { \mathrm { s } } ,$ is an increasing function of the first half-hour trading volume. 

## 3.5 Trade size and liquidity

An important question is whether it is individual investors or institutional investors who contribute most to the predictability. Since information about trades of institutions and individuals is not available, we investigate the impact of trade size and liquidity on the intraday momentum to shed some light on the question. 

We estimate the last half-hour trade size of SPY using the last half-hour volume over the number of trades. Because trade size exhibits a downward trend, we first sort all trading days within each year into small and large groups based on the last half-hour trade size, and then combine each trade size group across all years to form the final two trade size days, small and large. 

Panel A of Table 4 reports the predictive regression results on the two types of trading days. It is seen that the predictability of $r _ { 1 }$ is barely afected. However, the predictability of $r _ { 1 2 }$ is stronger in the large trade size days. This seems intuitive. The institutions are likely to trade more actively on large trade size days, and in doing so they are also more likely to trade both in the last half-hour and the half-hour prior to it, causing the greater 

predictability of $r _ { 1 2 }$ 

To assess the impact of liquidity, we group all stocks in the S&P500 into value-weighted low and high Amihud portfolios each day. Following Amihud (2002), the daily illiquidity measure for each stock is computed as the average daily ratio of the absolute stock return to the dollar trading volume over the previous 5-day window. Then we apply the predictive regression to the low and high Amihud portfolio returns separately. 

Panel B of Table 4 reports the results. The predictability of $r _ { 1 }$ , as measured by its slope, t-statistic and $R ^ { 2 }$ , is quite similar between low and high Amihud illiquidity stocks. However, the predictability of $r _ { 1 2 }$ appears stronger for high Amihud (less liquid) stocks, which seems intuitive as predictability is more dificult to exploit away with less liquidity. 

## 3.6 Institutional Trading

To further explore the question of who contributes most to the predictability, we examine how the trading patterns of institutions afect the intraday momentum. 

First, we consider stocks held by institutional investors. Since the holding information is only available quarterly, we group the S&P500 stocks into two value-weighted portfolios each quarter according to their percentage of shares held by institutions in the previous quarter, and run predictive regressions on the low and high holding portfolios separately. 

Panel A of Table 5 reports the results. The predictability of $r _ { 1 }$ is significant for both low and high institutional holding stocks, and is slightly greater for the low. In contrast, the slope of $r _ { 1 2 }$ is greater for high institutional holding stocks. This is consistent with the early results that institutions contribute more to the predictability of $r _ { 1 2 }$ . However, the impact of $r _ { 1 2 }$ on the overall predictability is small, as the $R ^ { 2 }$ is only slightly greater for high institutional holding stocks. 

Second, we consider days with institutional order imbalances. With data from ANcerno, we define a daily institutional order-imbalance measure on SPY as (buy volume - sell volume)/(buy volume + sell volume), where buy volume or sell volume is the total buy or sell volume across all ANcerno institutions on a given day.<sup>8</sup> Note that our measure is only a proxy of all institutional trading activities, since ANcerno tracks about 10% of institutions. Then, we can sort the trading days into low and high order-imbalance days and run predictive regressions on these days separately. 

Panel B of Table 5 reports the results. Again, the predictability of $r _ { 1 }$ is roughly the same, but that of $r _ { 1 2 }$ varies over the two types of order-imbalance days. To understand the latter, it seems likely that the institutional investors have more trades near the market close that make the return correlation stronger. Interestingly, the overall predictability is stronger, with both greater regression slopes and greater $R ^ { 2 } { \mathrm { s } } .$ , on high institutional order-imbalance days. This is consistent with early institutional holding results. 

Finally, we investigate how the predictability is related to institutional trading patterns near month end. Etula, Rinne, Suominen, and Vaittinen (2016) show that, due to their month-end liquidity needs, institutional investors trade less near the end of the month. Strikingly, the market risk premium can be earned predictably in only 7 days around the end of the month, from $T - 3$ to $T + 3$ . To see if there is any impact of these month-end trades, we run the predictive regressions on these 7 month-end days and other days. Though intraday momentum is present on both types of days, it is weaker near the month end. Consistent with early findings, the trading volume over the 7 days is about 5.9% lower than the rest of days. 

## 3.7 Explanations

Statistically, both the in- and out-of-sample analyses provide strong evidence on the intraday momentum. From an economic point of view, it is valuable to consider what economic forces are behind it. We provide two explanations below. 

Before exploring the explanations, it is worthwhile to examine the volume and volatility patterns of the stock market. Figure 2A plots the average trading volume of the S&P 500 ETF every half-hour. Both the first and the last half hours have trading volume close to 15 million shares, while the middle of the day has only about 5 million shares. The plot has a perfect U-shape, consistent with earlier findings about intraday trading activity (see, e.g., Jain and Joh, 1988). Figure 2B also displays a U-shaped volatility pattern. Moreover, the U-shape trading volume pattern is stronger on high volatility days, suggesting a stronger impact of informed trading as volatility rises. This is consistent with our earlier finding that intraday momentum is greater under higher volatility. Economically, as discussed earlier, the U-shaped patterns are due to the digestion of new information in the first half-hour, and the desire to trade in the last half-hour for settlement and for avoiding overnight risk. 

First, Bogousslavsky (2016) provides infrequent rebalancing as one of the economic driving forces. In his presidential address, Dufie (2010) emphasizes the important role of the slow-moving capital and infrequent decisions in our understanding of a number of stylized facts in finance. Along this line, Bogousslavsky (2016) focuses on infrequent rebalancing and its role in return autocorrelation and seasonality. In particular, he shows theoretically that our intraday momentum can be driven by some investors who simply delay their rebalancing trading to near the market close instead of market open. Then, intuitively, trading in the last half-hour in the same direction as the first leads to a positive correlation between the two returns. 

The second explanation is based on the presence of late-informed investors. Consider a day with good news. Some investors may react quickly and buy, pushing the market up in the first half-hour. However, there are others who are late-informed, in that they may learn the news later or simply process the news too slowly to react in the first half-hour. For example, Baker and Wurgler (2006) show that investors still react to month old sentiment measures, and Hong, Torous, and Valkanov (2007) and Cohen and Frazzini (2008) find that information transmission can last up to a month across certain industries. Therefore, information processing can easily take an entire day. As the late-informed investors chase to buy, the last half-hour is clearly the choice since it is the most liquid period after the first half-hour. Buying in the same direction as the first half-hour can yield a positive return for the last half-hour, thereby generating the positive correlation.<sup>9</sup> 

In practice, some funds prefer to trade at a price near the closing price. This is desirable not only for end-of-day settlements, but also for applications of empirical factor models which are, after all, based on closing prices. Mutual fund investors can trade only at the closing prices. Rationally, they will not instruct their fund managers until near the market close to retain the option value of waiting. Technically, these investors can also be regarded as “late-informed” since they trade later in the day rather than earlier. 

Both of the explanations above provide an economic basis for the strong statistical evidence on the intraday momentum. Clearly, there are likely other explanations. Future research is needed to develop a fully dynamic general equilibrium model for understanding intraday trading motives, risk factors, and the equilibrium risk premium associated with the intraday predictability. 

## 4 Economic Significance

## 4.1 Market timing

One way to assess the value of a predictor is to examine how well it performs in market timing. In our case, we use the first and twelfth half-hour returns as timing signal to trade the market in the last half-hour. Specifically, we will take a long position in the market at the beginning of the last half-hour if the timing signal is positive, and take a short position otherwise. It is worth noting that the position (long or short) is closed at the market close on each trading day. 

Consider first the use of the first half-hour return $r _ { 1 }$ as the trading signal. Mathematically, the market timing strategy based on signal $r _ { 1 }$ on day t will have a return in the last half-hour: 

$$
\eta (r _ {1}) = \left\{ \begin{array}{l l} r _ {1 3}, & \text { if } \quad r _ {1} > 0; \\ - r _ {1 3}, & \text { if } \quad r _ {1} \leq 0. \end{array} \right.\tag{4}
$$

When using both $r _ { 1 }$ and $r _ { 1 2 }$ as the trading signal, we $\mathrm { g o }$ long only if both returns are positive, and $\mathrm { g o }$ short when both are negative. Otherwise, we stay out of the market. Mathematically, the return is computed from 

$$
\eta (r _ {1}, r _ {1 2}) = \left\{ \begin{array}{l l} r _ {1 3}, & \text { if } \quad r _ {1} > 0   \&   r _ {1 2} > 0; \\ - r _ {1 3}, & \text { if } \quad r _ {1} \leq 0   \&   r _ {1 2} \leq 0; \\ 0, & \text { otherwise. } \end{array} \right.\tag{5}
$$

Panel A of Table 6 reports summary statistics on returns generated from the three timing strategies. When we use the first half-hour return as the timing signal to trade in the last half hour, the average return is 6.67% on an annual basis.<sup>10</sup> At first glance, this does not seem very high. To gauge the performance, we report the performances of two benchmark strategies. The first is an Always Long strategy, where we always take a long position in the market at the beginning of the last half-hour and close it at the market close. The first row in Panel B of Table 6 shows that the annualized average return of this strategy is very poor, at −1.11% per year and statistically insignificant. Hence, the timing strategy $\eta ( r _ { 1 } )$ outperforms this passive strategy substantially. 

The second benchmark is a Buy-and-Hold strategy, where we simply take a long position in the market from the beginning of the sample, and hold it until the end of the whole sample period. The results are reported in the second row of Panel B. The average return is 6.04% per year, which is much better than Always Long, but is still below the average return delivered by the timing strategy $\eta ( r _ { 1 } )$ and statistically insignificant. Hence, 6.67% is remarkable, considering that we are in the market for only a half-hour each trading day instead of six and half-hours each day. 

Of course, we have to take risk into consideration. The standard deviation is 6.19% per annum for the timing strategy $\eta ( r _ { 1 } )$ , resulting in a Sharpe ratio of 1.08. In contrast, the Always Long strategy has a comparable standard deviation of 6.21%, but a negative Sharpe ratio of −0.18. The long-term Buy-and-Hold strategy has a much higher standard deviation of 20.57%, and a much lower Sharpe ratio of 0.29. Note that the timing strategy $\eta ( r _ { 1 } )$ also enjoys a high positive skewness of 0.90 (versus −0.46 and −0.16 for the Always Long and Buy-and-Hold strategies, respectively) and a kurtosis of 15.65, suggesting that it often delivers high positive returns. 

Finally, we report the success rate, which is defined as the percentage of trading days with zero or positive returns. The success rate of the Always Long strategy is 50.42%, suggesting that the unconditional probability for the last half-hour return being positive is roughly 50%. However, the success rate of the timing strategy $\eta ( r _ { 1 } )$ is higher, at 54.37%. 

Using the twelfth half-hour return as the timing signal yields similar but weaker results. 

The average return is about 1.77% per annum, greater than Always Long, but lower than Buy-and-Hold. However, its Sharpe ratio is 0.29, skewness is 0.38, kurtosis is 15.73, and success rate is 50.93%. Overall, it has a greater Sharpe ratio than the benchmark strategies. 

Combining the two returns, $r _ { 1 }$ and $r _ { 1 2 } .$ , delivers improved performance over using only the twelfth half-hour return, but the performance is slightly weaker than using just the first half-hour return signal. For example, the average daily return is now 4.39% vs. 6.67% per annum, but the success rate is now much higher at an impressive value of 77.05%. This means that combining both $r _ { 1 }$ and $r _ { 1 2 }$ substantially improves the percentage of being correct. Then, why does higher success rate yield lower average returns? The reason is that when we combine the two signals, we take the long or short position only when both of them are positive or negative, which substantially reduces the number of days when we are in the market.<sup>11</sup> 

## 4.2 Utility gains

Instead of using only the signs to form timing strategies, here we use both the signs and magnitudes of the predictors to forecast the expected returns. Then we apply these expected returns to construct the optimal portfolio for a mean-variance investor who allocates funds between the market (SPY) and the risk-free asset (the Treasury T-bill). 

The optimal mean-variance portfolio weight on the market is 

$$
w _ {t} = \frac {1}{\gamma} \frac {\hat {r} _ {1 3 , t + 1}}{\hat {\sigma} _ {1 3 , t + 1} ^ {2}},\tag{6}
$$

where $\hat { r } _ { 1 3 , t + 1 }$ is the forecasted last half-hour return on day t + 1 conditional on information available on or before day t and the predictor(s) on t+1, and $\hat { \sigma } _ { 1 3 , t + 1 }$ is the standard deviation of the last half-hour return, both of which are estimated from the recursive regressions; and the relative risk aversion coeficient, γ, is set at 5. To be more realistic, we impose the portfolio constraint that weight on the market must be between −0.5 and 1.5, meaning that the investor is allowed to borrow or short 50% on margin. This will limit the potential economic gains from the usual unconstrained weights.<sup>12</sup> 

Over the out-of-sample period, the realized utility is 

$$
U = \hat {\mu} _ {p} - \frac {\gamma}{2} \hat {\sigma} _ {p} ^ {2},\tag{7}
$$

where $\hat { \mu } _ { p }$ and $\hat { \sigma } _ { p }$ are computed based on the realized portfolio returns. In the out-of-sample forecasting literature, the historical average is usually the benchmark, and the certainty equivalent return (CER) of predictability is computed from 

$$
C E R = U _ {2} - U _ {1},\tag{8}
$$

where $U _ { 2 }$ is the realized utility of using the forecasted return $\hat { r } _ { 1 3 , t + 1 }$ , and $U _ { 1 }$ is the realized utility of using the historical average mean forecast, $\bar { r } _ { 1 3 , t + 1 }$ . From an economic perspective, CER can be interpreted as the gains of an investor who switches from believing in a random walk model of the intraday prices to believing in intraday momentum. 

The results are reported in Table 7. Using the first half-hour returns to forecast the last half-hour returns yields an average return of 6.51% per annum, a standard deviation of 5.62% per annum (indicating a Sharpe ratio of 1.16), and a large positive skewness. In sharp contrast, using the historical average $\bar { r } _ { 1 3 }$ to predict the last half-hour return only generates an average return of 0.46% per annum, a standard deviation of 3.06% per annum, and hence a Sharpe ratio of merely 0.15. The CER using the first half-hour return is 6.02% per annum (the realized utility of using the historical average is only 0.46%), indicating sizable economic gains when investors switch from following a random walk model to following the intraday momentum. 

When both the first and the twelfth half-hour returns are used to forecast the last halfhour returns, the portfolio delivers the best result, with an average return of 6.68% per annum, a Sharpe ratio of 1.07, and a CER of 6.18% per annum. Note that, unlike the case with market timing, using both predictors is now slightly better than using the first halfhour return alone. This is because we are now always in the market. However, the allocation varies daily. 

## 5 Macroeconomic Events

## 5.1 Business cycles

We use the NBER dates for expansions and recessions to divide all trading days into these two types, and examine how the intraday momentum varies over the business cycles. 

Table 8 reports the predictive regression results. It is seen that the intraday momentum is stronger in recessions than in expansions. During expansions, only the first half-hour return can predict the last half-hour return. Albeit statistically significant, the predictability is relatively weak, with an $R ^ { 2 }$ of 0.9% when using $r _ { 1 }$ alone, and of 1.0% when using both $r _ { 1 }$ and $r _ { 1 2 }$ . During recessions, however, both the first and the twelfth half-hour returns are highly significant, and the $R ^ { 2 }$ increases more than six times to 6.6% when using both of the predictors. The results are consistent with early volatility regime results because the volatility is much greater in recessions than in expansions. This is also consistent early results on liquidity. During recessions, the market is less liquid and hence the a greater momentum impact due to the increasing dificulty of arbitrage. 

## 5.2 News releases

Previously, we have found that the intraday momentum is stronger on days with higher volatility or higher trading volume. One possible source of high volatility or trading volume may be the release of major economic news. It is hence of interest to investigate how news releases afect intraday momentum. 

While there are many regular news releases, we focus on four major ones whose release times span across diferent time frames of the day. The first is the Michigan Consumer Sentiment Index (MCSI), released monthly at 10:00am. The next two are the major macroeconomic variables, the gross domestic product (GDP) and the consumer price index (CPI). Both of these are released monthly on pre-specified dates at 8:30am before the market opens, like most other macroeconomic news. The last is the minutes of the Federal Open Market Committee (FOMC), released regularly at 2:15pm approximately every six weeks. We analyze the impact of the news releases by dividing all the trading days into two groups: days with the news releases, and days without. 

Panel A of Table 9 reports the performance of intraday momentum for the two groups of trading days. On days without MCSI news, the $R ^ { 2 }$ is 2.6%. On days with MCSI releases, the $R ^ { 2 }$ more than doubles to 5.5%. That is, the intraday momentum becomes stronger. The same holds true when we compare the $R ^ { 2 } \mathrm { s }$ on days with and without news announcements for GDP and CPI. These results seem to suggest that there is an information carryover efect of the news on market prices during the whole trading day. 

The most astonishing result is for the releases of the FOMC minutes. While the norelease days have an $R ^ { 2 }$ of only 2.5%, the $R ^ { 2 }$ increases enormously to 11.0% on release days. There are two reasons why this result is astonishing. First, the $R ^ { 2 }$ is high by any standard, exceeding almost all predictors at the usual monthly frequency by far. Second, market participants seem to anticipate correctly in the first half-hour the message the Fed is going to send out to the market. Lucca and Moench (2015) find that pre-announcement excess equity returns account for sizable fractions of total realized stock returns, which is also a global phenomenon. Bernile, Hu, and Tang (2016) investigate market activity minutes prior to the release of the FOMC minutes. Unlike these studies, we focus on the intraday momentum. The high $R ^ { 2 }$ indicates that, even after the FOMC news release, there is a strong tendency of the market to continue the trend in the same direction anticipated in the first half-hour. 

Will the higher $R ^ { 2 } \mathrm { s }$ on the news release days imply greater economic gains? To answer this question, we examine the performance of the earlier market timing strategies on days with and without news release. Panel B of Table 9 only reports the results of using the first half-hour return, $\eta ( r _ { 1 } )$ , for brevity. For the MCSI and CPI news, the gains are around three times the gains on the days without news releases. For the GDP news, the profits on release days are about twice as much. The greatest economic gains are delivered on the release days of the FOMC minutes. The annualized average return reaches a high level of 20.04%. This is close to four times the level on days without FOMC news. Overall, the economic performance of the intraday momentum is much stronger on the days with the four news releases. 

## 6 Robustness

## 6.1 Transaction costs

What are the impacts of transaction costs on our results? With technological advancements and ever increasing competition in the financial industry, we have witnessed a significant decline in transaction costs over the past two decades. This trend becomes even more evident after decimalization of quotations. 

We examine the impact of transaction costs on the profitability of the intraday momentum using the market timing strategy as an example. To this end, we collect from the TAQ database the bid and ask prices at 3:30pm on each trading day and use the ask (bid) price to calculate the last half-hour return if the market timing strategy takes a long (short) position.<sup>13</sup> Since the closing of the SPY is uniquely traded at the market clearing price for all the buys and sells, there will be no bid/ask spread efect for the price at 4:00pm.<sup>14</sup> Due to autoquotes of non-NYSE securities in the TAQ data before decimalization, we examine the efect of transaction costs only after decimalization (after July 1, 2001).<sup>15</sup> 

The results are reported in Table 10. Panel A of the table shows that, using the first half-hour return as the timing signal, the average return reduces to 4.46% per annum, 2.47% lower than the average return before transaction costs, while the standard deviation remains the same at 6.10%. Nevertheless, the profits are still economically significant. In contrast, the Always Long strategy which always invests in the market during the last half-hour yields an average return of −0.74% per annum, and the daily market return (Buy-and-Hold) is 4.90% per annum for the same period. A slightly better result can be obtained when both the first and the twelfth half-hour returns are used to time the market. After adjusting for transaction costs, the average return is reduced by only 1.22% to 4.30% per annum. 

Figure 3 plots the time-series of the proportional spread after decimalization (after July 1, 2001). It shows clearly that the proportional spread narrowed after decimalization, and stabilized at around 1.2 basis point after 2005. To better capture the impact of transaction costs on future performance of the intraday momentum, we consider the performance after January 1, 2005, reported in Panel B of Table 10. The average return of market timing using the first half-hour return is 6.52% after transaction costs compared with 7.96% before transaction costs. Similarly, the average return using both the first and twelfth half-hour returns is 4.74% after transaction costs versus 5.50% before transaction costs. The main result is that the intraday momentum profit survives from transaction costs. 

## 6.2 Other ETFs

Is the intraday momentum a special case for the S&P 500 ETF, or a general phenomenon of the stock market? To address this question, we analyze the intraday returns of ten alternative ETFs. We choose the ten ETFs with the highest average daily trading volume from their inception dates to December 31, 2013.<sup>16</sup> Table 11 describes these ETFs. The asset classes are diverse. They include domestic alternative stock indices such as the Dow, the NASDAQ, and the Russell 2000 (DIA, QQQ, and IWM); international equity indices (EEM, FXI, EFA, VWO); two sector indices (XLF, IYR); and one bond index (TLT). If the intraday momentum found in SPY is also present in this diverse set of ETFs, it should lend more support to our trading behavior explanations. 

Table 12 reports the in-sample and out-of-sample $R ^ { 2 } \mathrm { s }$ and CER performance measures for each ETF. We see a consistent pattern: the first half-hour return significantly predicts the last half-hour return. Moreover, utilizing such predictability generates substantial economic values. When the first half-hour return $r _ { 1 }$ is used alone as a predictor (Panel A), the insample $R ^ { 2 }$ ranges from 1.16% for DIA to 8.54% for EEM, and the out-of-sample $R ^ { 2 }$ is from 0.70% for QQQ to 6.53% for EEM. All the $R ^ { 2 } \mathrm { s }$ strongly suggest that the first half-hour returns predict the last half-hour returns. 

A further examination on the volatility and trading volume of these ETFs reveals that they all have similar U-shaped patterns (unreported here for brevity) as the SPY. Hence, the first half-hour and the last half-hour are also the most important trading periods for these 

ETFs. As a result, the two earlier theoretical explanations, infrequent portfolio rebalancing and late-informed trading, appear to be applicable to them as well. The desire to trade these ETFs in the last half-hour can generate their intraday momentum. 

In terms of economic value, the CER can be as high as 17.71% per annum for FXI, and many are greater than 10.0%. In comparison with the S&P 500 ETF, these ETFs are less liquid, so the price impact of the last half-hour trading is likely greater. This might help explain their higher CERs in general. Adding $r _ { 1 2 }$ to $r _ { 1 }$ as an additional predictor (Panel B), we find a slight improvement over the single predictor $r _ { 1 }$ , but the improvement is not uniform. In short, the results for various ETFs indicate a pervasive intraday momentum pattern in the US stock market. 

## 6.3 Data-snooping

Could our findings be caused by data snooping?<sup>17</sup> We argue that the intraday momentum pattern is strong and persistent, and so it is unlikely to be explained by chance alone. 

First, the intraday momentum shows that $r _ { 1 }$ is a powerful predictor. In Panel A of Table 1, the robust t-statistic of $r _ { 1 }$ is 4.08, substantially exceeding the usual t-statistic between 1 and 3 seen in the return predictive regressions. Moreover, the in-sample $R ^ { 2 }$ of 1.6% is exceedingly high for a short-horizon return prediction problem. Such significant levels not only guard against the false discovery (see, e.g., Harvey, Liu, and Zhu, 2016), but also should bear less discount or “haircut” due to backtesting biases (see, e.g., Harvey and Liu, 2015). Second, the performance of the intraday momentum is persistent throughout our sample, and, as summarized in Tables 1–9, the intraday momentum consistently emerges under vastly diferent market conditions characterized by financial crisis, volatility levels, trading volume, institutional trading, business cycles or macro news releases. Third, the intraday momentum is pervasive. As shown in Sections 6.2, the predicative power of the first half-hour return on the last half-hour return not only exists in SPY, but also in other most actively traded ETFs.<sup>18</sup> In short, due to the plausible economic explanations and strong statistical evidence, the intraday momentum is likely to be a genuine phenomenon. 

## 6.4 Other time frames

So far, we have demonstrated that the first half-hour and last-half hour of a trading day are special and there is an interesting positive correlation between their returns. However, we have not provided any evidence on the relation between other half-hours and the last-half hour return. Table 13 fills in this gap by providing the multivariate regression slopes of the last-half hour return on all the other half-hours. It is clear that, at the 5% significant level, only $r _ { 1 }$ and $r _ { 1 2 }$ matter. This is generally true across other ETFs as well. Again, this is likely due to the preference of trading in the first and last-half hours, as evidenced by the U-shaped patterns of volatility and volume. 

## 7 Conclusion

Our paper documents that the market return in the first half-hour predicts the market return in the last half-hour. This intraday predictability is statistically significant both in- and outof-sample. In terms of market timing and asset allocation, the economic gains of using the predictability are substantial. We also find that the market intraday momentum is stronger on high volatility days, high trading volume days, recession days, and important economic news (MCSI, GDP, CPI, FOMC) release days. Moreover, the intraday momentum is strong not only for the S&P 500 ETF, but also for ten other most actively traded ETFs. Theoretically, the market intraday momentum is consistent with the trading behavior of investors who either infrequently rebalance their portfolios, or trade late from early information. 

There are a few open issues on the intraday momentum. First, the documented empirical facts in this paper call for new theoretical models of intraday trading to identify factors that determine its risk premium. Second, as trading costs become increasingly lower and trading execution becomes more automated, it is important to assess the asset pricing implications of intraday trading strategies and the associated implications for portfolio management. Third, there is a huge literature on the predictability at the monthly frequency, but it is unknown how the intraday predictability is related to the monthly predictability. These are interesting topics for future research. 

## References

Abreu, D., and M. K. Brunnermeier. 2002. Synchronization risk and delayed arbitrage. Journal of Financial Economics 66:341–360. 

Amihud, Y. 2002. Illiquidity and stock returns: Cross-section and time-series efects. Journal of Financial Markets 5:31–56. 

Asness, C. S., T. J. Moskowitz, and L. H. Pedersen. 2013. Value and momentum everywhere. Journal of Finance 68:929–985. 

Baker, M. P., and J. Wurgler. 2006. Investor sentiment and the cross-section of stock returns. Journal of Finance 61:1645–1680. 

Bernile, G., J. Hu, and Y. Tang. 2016. Can information be locked-up? Informed volume and price variability trading ahead of macro-news announcements. Journal of Financial Economics 121:496–520. 

Bogousslavsky, V. 2016. Infrequent rebalancing, return autocorrelation, and seasonality. Journal of Finance 71:2967–3006. 

Campbell, J. Y., and S. B. Thompson. 2008. Predicting excess stock returns out of sample: Can anything beat the historical average? Review of Financial Studies 21:1509–1531. 

Cespa, G., and X. Vives. 2015. The beauty contest and short-term trading. The Journal of Finance 70:2099–2154. 

Chordia, T., R. Roll, and A. Subrahmanyam. 2001. Market liquidity and trading activity. Journal of Finance 56:501–530. 

. 2011. Recent trends in trading activity and market quality. Journal of Financial Economics 101:243–263. 



Cohen, L., and A. Frazzini. 2008. Economic links and predictable returns. Journal ofFinance 63:1977–2011. 





Corwin, S. A., and P. Schultz. 2012. A simple way to estimate bid-ask spreads from daily high and low prices. Journal of Finance 67:719–760. 





Coval, J. D., and T. Shumway. 2005. Do behavioral biases afect prices? Journal of Finance 60:1–34. 





Cushing, D., and A. Madhavan. 2000. Stock returns and trading at the close. Journal of Financial Markets 3:45–67. 





Dufie, D. 2010. Presidential address: Asset price dynamics with slow-moving capital. Journal of Finance 65:1237–1267. 





Etula, E., K. Rinne, M. Suominen, and L. Vaittinen. 2016. Dash for cash: Month-end liquidity needs and the predictability of stock returns. Unpublished working paper, New York University, Luxembourg School of Finance, and Aalto University. 





Ferreira, M. A., and P. Santa-Clara. 2011. Forecasting stock market returns: The sum of the parts is more than the whole. Journal of Financial Economics 100:514–537. 





Foucault, T., O. Kadan, and E. Kandel. 2005. Limit order book as a market for liquidity. Review of Financial Studies 18:1171–1217. 





Grifin, J. M., X. Ji, and J. S. Martin. 2003. Momentum investing and business cycle risk: Evidence from pole to pole. Journal of Finance 58:2515–2547. 





Haigh, M. S., and J. A. List. 2005. Do professional traders exhibit myopic loss aversion? An experimental analysis. Journal of Finance 60:523–534. 





Harvey, C. R., Y. Liu, and H. Zhu. 2016. ...and the cross-section of expected returns. Review of Financial Studies 29:5–68. 





Harvey, C. R., and Y. Liu. 2015. Backtesting. Unpublished working paper, Duke University. 





Henkel, S. J., J. S. Martin, and F. Nardari. 2011. Time-varying short-horizon predictability. Journal of Financial Economics 99:560–580. 





Heston, S. L., R. A. Korajczyk, and R. Sadka. 2010. Intraday patterns in the cross-section of stock returns. Journal of Finance 65:1369–1407. 





Hirshleifer, D., A. Subrahmanyam, and S. Titman. 1994. Security analysis and trading patterns when some investors receive information before others. The Journal of Finance 49:1665–1698. 





Hong, H., W. Torous, and R. Valkanov. 2007. Do industries lead stock markets? Journal of Financial Economics 83:367–396. 





Jain, P. C., and G.-H. Joh. 1988. The dependence between hourly prices and trading volume. Journal of Financial and Quantitative Analysis 23:269–283. 





Jegadeesh, N., and S. Titman. 1993. Returns to buying winners and selling losers: Implications for stock market eficiency. Journal of Finance 48:65–91. 





Locke, P. R., and S. C. Mann. 2000. Do professional traders exhibit loss realization aversion? Unpublished working paper, Texas Christian University. 





Lou, D., C. Polk, and S. Skouras. 2017. A tug of war: Overnight versus intraday expected returns. Unpublished working paper, London School of Economics and Athens University of Economics and Business. 





Lucca, D. O., and E. Moench. 2015. The pre-FOMC announcement drift. Journal of Finance 70:329–371. 





Moskowitz, T. J., Y. H. Ooi, and L. H. Pedersen. 2012. Time series momentum. Journal of Financial Economics 104:228–250. 





Neely, C. J., D. E. Rapach, J. Tu, and G. Zhou. 2014. Forecasting the equity risk premium: The role of technical indicators. Management Science 60:1772–1791. 





Newey, W. K., and K. D. West. 1987. A simple, positive semi-definite, heteroskedasticity and autocorrelation consistent covariance matrix. Econometrica 55:703–708. 





Odean, T. 1998. Are investors reluctant to realize their losses? Journal of Finance 53:1775– 1798. 





Rapach, D., and G. Zhou. 2013. Forecasting stock returns. In G. Elliott and A. Timmermann, eds., Handbook of Economic Forecasting, vol. 2A, chap. 6, 328–383. North-Holland, Amsterdam: Elsevier. 





Rapach, D. E., J. K. Strauss, and G. Zhou. 2010. Out-of-sample equity premium prediction: Combination forecasts and links to the real economy. Review of Financial Studies 23:821– 862. 





Shefrin, H., and M. Statman. 1985. The disposition to sell winners too early and ride losers too long: Theory and evidence. Journal of Finance 40:777–790. 





Welch, I., and A. Goyal. 2008. A comprehensive look at the empirical performance of equity premium prediction. Review of Financial Studies 21:1455–1508. 





Zhang, X. F. 2006. Information uncertainty and stock returns. Journal of Finance 61:105– 137. 




Panel A: Time Series of $r _ { 1 }$ Coeficient


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/69a91ce4-d722-4855-8f66-e2e6e7b8ef8a/f399d756db3d109b71bac114c4f93cbf42cb6947838d6cf77bf21db828d76e6b.jpg)



Panel B: Time Series of $r _ { 1 2 }$ Coeficient


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/69a91ce4-d722-4855-8f66-e2e6e7b8ef8a/bcd94d9931326479c23873f6c0ac2868e1fe4b2dfefb3978cda68ce3c4e230be.jpg)



Figure 1: Time Series of $r _ { 1 }$ and $r _ { 1 2 }$ Coeficients


Panels A and B plot the predictive regression coeficients of $r _ { 1 }$ and $r _ { 1 2 }$ , which are estimated recursively overtime. 


Panel A: Average 30-Minute Trading Volume


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/69a91ce4-d722-4855-8f66-e2e6e7b8ef8a/29d674bbad5fc0c7842c126e3db319d4e5eb04956893af62f6ea408057f0eba8.jpg)



Panel B: Average 30-Minute Trading Volume Under High and Low Volatility


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/69a91ce4-d722-4855-8f66-e2e6e7b8ef8a/161455e21acafdc430ab8ada1017cebcd7775dda97dbbcd0cddc40f046f392c3.jpg)



Figure 2: Average 30-Minute Trading Volume of SPY


For every 30-minute period from 9:30am to 4:00pm Eastern Time, Panel A shows the average trading volume for SPY from February 1, 1993 through December 31, 2013. Each 30-minute period is labeled from 1 to 13 sequentially. Panel B plots the same 30-minute average trading volume on high volatility (top tercile) and low volatility (bottom tercile) days. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/69a91ce4-d722-4855-8f66-e2e6e7b8ef8a/e5abd0ed86b801e828cbc7cae7b2bc771b38fc987e9d735b52ad773c4a133143.jpg)



Figure 3: Time Series of Proportional Spread for SPY


This figure plots the proportional spread at 3:30pm on each trading day for SPY after decimalization (after July 1, 2001). The proportional spread is defined as (Ask − Bid)/Midquote, where the midquote price is the average of the bid and ask prices, $( \mathrm { A s k + B i d } ) / 2$ 

## Table 1: Predictability

This table reports the results of regressing the last half-hour return, $r _ { 1 3 }$ , on the first half-hour return, $r _ { 1 }$ , and the twelfth half-hour return, $r _ { 1 2 } .$ , of the day. The first half-hour return $r _ { 1 }$ is calculated from the closing of the previous trading day at 4:00pm to 10:00am Eastern Time. Panel A shows the in-sample results, while Panel B shows the out-of-sample recursive regression results. The window of the estimation initially uses observations up to December 31, 1997, and progressively includes one more month of returns. The out-of-sample predictability is measured by the out-of-sample R-squared: 

$$
R _ {O S} ^ {2} = 1 - \frac {\sum_ {t = 1} ^ {T} (r _ {1 3 , t} - \hat {r} _ {1 3 , t}) ^ {2}}{\sum_ {t = 1} ^ {T} (r _ {1 3 , t} - \bar {r} _ {1 3 , t}) ^ {2}},
$$

where $\hat { r } _ { 1 3 , t }$ is the forecasted last half-hour return from the predictive regression estimated through period $t - 1$ , and $\bar { r } _ { 1 3 , t }$ is the historical average return of the last half-hour estimated through period t − 1. The returns are annualized and in percentage, and the regression coeficients are scaled by 100. Newey and West (1987) robust t-statistics are in parentheses, and significance at the 1%, 5%, or 10% level is given by an $^ { * * * }$ , an $^ { * * }$ or an *, respectively. The sample period is from February 1, 1993, through December 31, 2013. 

<table><tr><td>Predictor</td><td><eq>r_1</eq></td><td><eq>r_{12}</eq></td><td><eq>r_1</eq> and <eq>r_{12}</eq></td><td><eq>r_1</eq></td><td><eq>r_{12}</eq></td><td><eq>r_1</eq> and <eq>r_{12}</eq></td></tr><tr><td></td><td colspan="3">Panel AIn Sample</td><td colspan="3">Panel BOut of Sample</td></tr><tr><td>Intercept</td><td>-1.63(-1.16)</td><td>-1.33(-0.94)</td><td>-1.82(-1.28)</td><td>-0.40***(-11.4)</td><td>-0.28***(-10.4)</td><td>-0.41***(-10.8)</td></tr><tr><td><eq>\beta_{r_1}</eq></td><td>6.94***(4.08)</td><td></td><td>6.81***(4.14)</td><td>3.43***(8.47)</td><td></td><td>3.34***(8.35)</td></tr><tr><td><eq>\beta_{r_{12}}</eq></td><td></td><td>11.8***(2.62)</td><td>11.4***(2.60)</td><td></td><td>5.92***(9.37)</td><td>5.74***(9.34)</td></tr><tr><td><eq>R^2</eq>(%)</td><td>1.6</td><td>1.1</td><td>2.6</td><td>1.4</td><td>0.9</td><td>2.0</td></tr></table>


Table 2: Predictability and financial crisis



Panels A and B of the table report the predictive regression results during the financial crisis period from December 3, 2007, through June 30, 2009 and the periods excluding the crisis. Panels C and D report the results during the pre- and post-crisis periods. The returns are annualized and in percentage, and the regression coeficients are scaled by 100. Newey and West (1987) robust tstatistics are in parentheses, and significance at the 1%, 5%, or 10% level is given by an ***, an ** or an *, respectively. The sample period is from February 1, 1993, through December 31, 2013.


<table><tr><td>Predictor</td><td><eq>r_1</eq></td><td><eq>r_{12}</eq></td><td><eq>r_1</eq> and <eq>r_{12}</eq></td><td><eq>r_1</eq></td><td><eq>r_{12}</eq></td><td><eq>r_1</eq> and <eq>r_{12}</eq></td></tr><tr><td></td><td colspan="3">Panel AFinancial Crisis</td><td colspan="3">Panel BExcluding Financial Crisis</td></tr><tr><td>Intercept</td><td>2.29(0.29)</td><td>-1.66(-0.20)</td><td>1.36(0.17)</td><td>-1.63(-1.25)</td><td>-1.25(-0.97)</td><td>-1.72(-1.31)</td></tr><tr><td><eq>\beta_{r_1}</eq></td><td>13.6***(2.76)</td><td></td><td>13.2***(2.88)</td><td>4.45***(3.38)</td><td></td><td>4.40***(3.36)</td></tr><tr><td><eq>\beta_{r_{12}}</eq></td><td></td><td>21.1*(1.95)</td><td>20.2**(1.99)</td><td></td><td>6.32*(1.88)</td><td>6.13*(1.83)</td></tr><tr><td><eq>R^2 (\%)</eq></td><td>4.1</td><td>3.1</td><td>6.9</td><td>0.8</td><td>0.3</td><td>1.1</td></tr><tr><td></td><td colspan="3">Panel CBefore Financial Crisis</td><td colspan="3">Panel DAfter Financial Crisis</td></tr><tr><td>Intercept</td><td>-0.91(-1.37)</td><td>-0.80(-1.22)</td><td>-0.96(-1.43)</td><td>0.27(0.31)</td><td>0.40(0.47)</td><td>0.25(0.28)</td></tr><tr><td><eq>r_1</eq></td><td>4.22**(2.69)</td><td></td><td>4.16**(2.65)</td><td>4.41**(2.05)</td><td></td><td>4.39**(2.07)</td></tr><tr><td><eq>r_{12}</eq></td><td></td><td>5.00(1.45)</td><td>4.80(1.38)</td><td></td><td>12.49(1.16)</td><td>12.41(1.18)</td></tr><tr><td><eq>R^2 (\%)</eq></td><td>0.6</td><td>0.2</td><td>0.8</td><td>1.2</td><td>1.0</td><td>2.1</td></tr></table>

## Table 3: Impact of volatility and volume


This table reports the predictive regressions under diferent levels of return volatility (Panel A) or trading volume (Panel B) of the first half-hour. The first half-hour volatility is estimated using one-minute returns, and then all the trading days are ranked into three terciles by their first halfhour volatility: low, medium, and high. We also rank the trading days into low, medium, and high terciles by their first half-hour trading volume year by year to take into account the increasing trading volume over time, and then combine each volume tercile across all years to form three volume groups. The returns are annualized and in percentage, and the regression coeficients are scaled by 100. Newey and West (1987) robust t-statistics are in parentheses, and significance at the 1%, 5%, or 10% level is given by an ***, an ** or an *, respectively. The sample period is from February 1, 1993, through December 31, 2013.


<table><tr><td rowspan="2"></td><td colspan="3">Panel A Volatility</td><td colspan="3">Panel B Volume</td></tr><tr><td>Low</td><td>Medium</td><td>High</td><td>Low</td><td>Medium</td><td>High</td></tr><tr><td rowspan="2">Intercept</td><td>-2.18*</td><td>-3.07</td><td>0.26</td><td>-4.36***</td><td>1.22</td><td>-2.27</td></tr><tr><td>(-1.76)</td><td>(-1.51)</td><td>(0.07)</td><td>(-2.62)</td><td>(0.58)</td><td>(-0.66)</td></tr><tr><td rowspan="2"><eq>\beta_{r_1}</eq></td><td>2.34</td><td>5.40***</td><td>7.20***</td><td>4.32**</td><td>7.22***</td><td>7.08***</td></tr><tr><td>(1.03)</td><td>(2.93)</td><td>(3.76)</td><td>(2.31)</td><td>(3.32)</td><td>(3.01)</td></tr><tr><td rowspan="2"><eq>\beta_{r_{12}}</eq></td><td>8.81**</td><td>8.39**</td><td>12.7**</td><td>10.1**</td><td>6.16</td><td>13.7**</td></tr><tr><td>(2.07)</td><td>(2.29)</td><td>(2.05)</td><td>(2.11)</td><td>(1.39)</td><td>(2.05)</td></tr><tr><td><eq>R^2</eq>(%)</td><td>0.6</td><td>1.0</td><td>3.3</td><td>1.1</td><td>2.3</td><td>3.1</td></tr></table>

## Table 4: Trade size and liquidity

Panel A of the table reports the predictive regression on days with small and large trade sizes, respectively. Panel B shows the regression results on value-weighted portfolios formed from stocks in the S&P 500 sorted by their Amihud illiquidity measure, which is computed as the average daily ratio of the absolute stock return to the dollar trading volume over the previous 5-day window. The returns are annualized and in percentage, and the regression coeficients are scaled by 100. Newey and West (1987) robust t-statistics are in parentheses, and significance at the 1%, 5%, or 10% level is given by an ***, an ** or an *, respectively. The sample period is from February 1, 1993, through December 31, 2013. 

<table><tr><td rowspan="2"></td><td colspan="6">Panel A Trade Size</td></tr><tr><td colspan="3">Small Trade Size Days</td><td colspan="3">Large Trade Size Days</td></tr><tr><td>Intercept</td><td>0.00(-0.62)</td><td>0.00(-0.61)</td><td>-0.01(-0.71)</td><td>0.00(-0.57)</td><td>0.00(-0.24)</td><td>0.00(-0.58)</td></tr><tr><td><eq>r_1</eq></td><td>6.61***(2.75)</td><td></td><td>6.42***(2.72)</td><td>6.09***(4.05)</td><td></td><td>6.05***(4.02)</td></tr><tr><td><eq>r_{12}</eq></td><td></td><td>11.13*(1.69)</td><td>10.66*(1.66)</td><td></td><td>10.48**(2.53)</td><td>10.38**(2.52)</td></tr><tr><td><eq>R^2 (\%)</eq></td><td>1.4</td><td>1.0</td><td>2.2</td><td>1.3</td><td>0.9</td><td>2.2</td></tr></table>


Panel B



Portfolios Sorted on Amihud


<table><tr><td></td><td colspan="3">Low Amihud Stocks</td><td colspan="3">High Amihud stocks</td></tr><tr><td>Intercept</td><td>0.00(-0.46)</td><td>0.00(-0.11)</td><td>0.00(-0.62)</td><td>0.01**(2.23)</td><td>0.01*(1.92)</td><td>0.01*(1.76)</td></tr><tr><td><eq>r_1</eq></td><td>7.29***(4.70)</td><td></td><td>7.15***(4.69)</td><td>7.74***(4.62)</td><td></td><td>7.56***(4.81)</td></tr><tr><td><eq>r_{12}</eq></td><td></td><td>12.32***(2.59)</td><td>11.96***(2.58)</td><td></td><td>27.00***(5.40)</td><td>26.77***(5.58)</td></tr><tr><td><eq>R^2</eq>(%)</td><td>1.8</td><td>1.2</td><td>2.9</td><td>2.3</td><td>5.9</td><td>8.1</td></tr></table>

## Table 5: Institutional trading

This table reports the relation between institutional trading activity and the predictability of the first half-hour return on the last half-hour return. Panel A reports the predictive regression results on low and high institutional holding stocks in the S&P 500. The portfolios are sorted quarterly and value-weighted. Panel B reports the predictive regression results on low and high institutional order imbalance days. The order imbalance, a daily measure on the SPY, is defined as (buy volume − sell volume)/(buy volume + sell volume), where “buy volume” or “sell volume” is the total buy or sell volume across all ANcerno institutions on a given day. We then sort the trading days by this measure and run the predictive regressions separately on the low/high order imbalance days. The returns are annualized and in percentage, and the regression coeficients are scaled by 100. Newey and West (1987) robust t-statistics are in parentheses, and significance at the 1%, 5%, or 10% level is given by an ***, an ** or an *, respectively. The sample period is from February 1, 1993, through December 31, 2013 for Panel A, and from October 1, 1998, through December 31, 2013 for Panel B. 

<table><tr><td colspan="7">Panel APortfolios Sorted on Institutional Holding</td></tr><tr><td></td><td colspan="3">Low Holding Stocks</td><td colspan="3">High Holding Stocks</td></tr><tr><td>Intercept</td><td>-0.01(-1.28)</td><td>0.00(-0.73)</td><td>-0.01(-1.35)</td><td>0.01*(1.84)</td><td>0.01*(1.82)</td><td>0.01*(1.57)</td></tr><tr><td><eq>r_1</eq></td><td>9.68***(4.52)</td><td></td><td>9.59***(4.61)</td><td>6.31***(4.43)</td><td></td><td>6.17***(4.50)</td></tr><tr><td><eq>r_{12}</eq></td><td></td><td>11.62**(2.23)</td><td>11.24**(2.16)</td><td></td><td>19.06***(3.74)</td><td>18.79***(3.78)</td></tr><tr><td><eq>R^2</eq>(%)</td><td>3.3</td><td>1.0</td><td>4.2</td><td>2.0</td><td>3.2</td><td>5.1</td></tr></table>


Panel B



Impact of ANcerno Order Imbalance


<table><tr><td></td><td colspan="3">Low Imbalance Days</td><td colspan="3">High Imbalance Days</td></tr><tr><td>Intercept</td><td>0.31(0.34)</td><td>0.29(0.32)</td><td>0.22(0.24)</td><td>-1.11(-1.29)</td><td>-1.00(-1.17)</td><td>-1.12(-1.33)</td></tr><tr><td><eq>r_1</eq></td><td>6.91***(2.77)</td><td></td><td>6.93***(2.78)</td><td>7.91***(3.41)</td><td></td><td>7.68***(3.42)</td></tr><tr><td><eq>r_{12}</eq></td><td></td><td>10.09(1.31)</td><td>10.15(1.36)</td><td></td><td>15.02***(2.60)</td><td>14.46**(2.45)</td></tr><tr><td><eq>R^2 (\%)</eq></td><td>1.5</td><td>0.8</td><td>2.3</td><td>2.4</td><td>1.9</td><td>4.1</td></tr></table>

## Table 6: Market timing


This table reports the economic value of timing the last half-hour market return using r<sub>1</sub>, r<sub>12</sub> or both. The timing strategy $\eta ( r _ { 1 } ) \ ( \eta ( r _ { 1 2 } ) )$ takes a long position in the market when the first (twelfth) half-hour return is positive, and a short position when the return is negative. The joint strategy $\eta ( r _ { 1 } , r _ { 1 2 } )$ trades only when both returns have the same sign – long when both are positive and short when both are negative. The benchmark Always Long is to invest in the market during the last half-hour on each trading day, and Buy-and-Hold is to buy and hold the market on a daily basis. For each strategy, we report the average return $( A v g R e t )$ , standard deviation (Std Dev), Sharpe ratio (SRatio), skewness, kurtosis, and success rate (Success). The returns are annualized and in percentage. Newey and West (1987) robust t-statistics are in parentheses, and significance at the 1%, 5%, or 10% level is given by an ***, an ** or an *, respectively. The sample period is from February 1, 1993, through December 31, 2013.


<table><tr><td>Timing</td><td>Avg Ret(%)</td><td>Std Dev(%)</td><td>SRatio</td><td>Skewness</td><td>Kurtosis</td><td>Success(%)</td></tr><tr><td></td><td colspan="6">Panel A: Market Timing</td></tr><tr><td><eq>\eta(r_1)</eq></td><td>6.67***(4.36)</td><td>6.19</td><td>1.08</td><td>0.90</td><td>15.65</td><td>54.37</td></tr><tr><td><eq>\eta(r_{12})</eq></td><td>1.77(1.16)</td><td>6.20</td><td>0.29</td><td>0.38</td><td>15.73</td><td>50.93</td></tr><tr><td><eq>\eta(r_1, r_{12})</eq></td><td>4.39***(3.96)</td><td>4.49</td><td>0.98</td><td>1.87</td><td>34.10</td><td>77.05</td></tr><tr><td></td><td colspan="6">Panel B: Benchmarks</td></tr><tr><td>Always Long</td><td>-1.11(-0.73)</td><td>6.21</td><td>-0.18</td><td>-0.46</td><td>15.73</td><td>50.42</td></tr><tr><td>Buy-and-Hold</td><td>6.04(1.19)</td><td>20.57</td><td>0.29</td><td>-0.16</td><td>6.61</td><td></td></tr></table>

## Table 7: Utility gains


This table reports the economic value of recursively predicting the last half-hour market return using the first half-hour return or combining with the twelfth half-hour return. We use the predicted returns to form a constrained mean-variance optimal portfolio for a mean-variance investor with a relative risk aversion of 5. Portfolio weights are restricted to a range between −0.5 and 1.5. For each strategy, we report the average return (Avg Ret), standard deviation (Std Dev), Sharpe ratio (SRatio), skewness, kurtosis, and the certainty equivalent gain of return, CER, calculated as the diference in the certainty equivalent rate of return between the optimal mean-variance strategy and benchmark using the historical average returns instead of the forecasted last half-hour returns. The returns are annualized and in percentage. Newey and West (1987) robust t-statistics are in parentheses, and significance at the 1%, 5%, or 10% level is given by an ***, an ** or an *, respectively. The sample period is from February 1, 1993, through December 31, 2013.


<table><tr><td>Predictor</td><td>Avg Ret(%)</td><td>Std Dev(%)</td><td>SRatio</td><td>Skewness</td><td>Kurtosis</td><td>CER(%)</td></tr><tr><td><eq>\bar{r}_{13}</eq></td><td>0.46(0.57)</td><td>3.06</td><td>0.15</td><td>0.48</td><td>18.05</td><td></td></tr><tr><td><eq>\beta_{1}r_{1}</eq></td><td>6.51***(4.33)</td><td>5.62</td><td>1.16</td><td>1.78</td><td>49.54</td><td>6.02</td></tr><tr><td><eq>\beta_{1}r_{1} + \beta_{2}r_{12}</eq></td><td>6.68***(4.00)</td><td>6.24</td><td>1.07</td><td>0.27</td><td>58.87</td><td>6.18</td></tr></table>


Table 8: Impact of business cycles



This table reports the impact of business cycles on the predictability of the last half-hour return by the first half-hour return and the twelfth half-hour return. The predictive regression results are provided for NBER expansions and recessions, respectively. The returns are annualized and in percentage, and the regression coeficients are scaled by 100. Newey and West (1987) robust t-statistics are in parentheses, and significance at the 1%, 5%, or 10% level is given by an ***, an ** or an *, respectively. The sample period is from February 1, 1993, through December 31, 2013.


<table><tr><td>Predictor</td><td><eq>r_1</eq></td><td><eq>r_{12}</eq></td><td><eq>r_1</eq> and <eq>r_{12}</eq></td><td><eq>r_1</eq></td><td><eq>r_{12}</eq></td><td><eq>r_1</eq> and <eq>r_{12}</eq></td></tr><tr><td></td><td colspan="3">Expansion</td><td colspan="3">Recession</td></tr><tr><td>Intercept</td><td>-2.34*(-1.76)</td><td>-1.81(-1.39)</td><td>-2.41*(-1.80)</td><td>5.42(0.89)</td><td>2.11(0.34)</td><td>4.79(0.78)</td></tr><tr><td><eq>\beta_{r_1}</eq></td><td>4.83***(3.39)</td><td></td><td>4.80***(3.39)</td><td>11.4***(2.76)</td><td></td><td>11.0***(2.87)</td></tr><tr><td><eq>\beta_{r_{12}}</eq></td><td></td><td>4.50(1.31)</td><td>4.32(1.26)</td><td></td><td>22.4**(2.25)</td><td>21.6**(2.30)</td></tr><tr><td><eq>R^2</eq>(%)</td><td>0.9</td><td>0.1</td><td>1.0</td><td>3.2</td><td>3.6</td><td>6.6</td></tr></table>

## Table 9: Impact of macro news release

This table reports the impact of macro news releases on the predictability of the last half-hour market return. Panel A compares the predictive regression results on days with macro news releases and those without. Panel B reports the profitability of the market timing strategies, described in Table 6, on the news days and other days. MCSI is the surveys of consumer confidence by University of Michigan released at 10:00am Eastern Time; GDP is the monthly GDP estimate released at 8:30am Eastern Time; CPI is the monthly CPI released at 8:30am Eastern Time; and FOMC is the Federal Open Market Committee minutes released at 2:15pm Eastern Time. The returns are annualized and in percentage, and the regression coeficients in Panel A are scaled by 100. Newey and West (1987) robust t-statistics are in parentheses, and significance at the 1%, 5%, or 10% level is given by an ***, an ** or an *, respectively. The sample period is from February 1, 1993, through December 31, 2013. 

<table><tr><td colspan="9">Panel A: Predictive Regression</td></tr><tr><td></td><td>No-Release</td><td>Release</td><td>No-Release</td><td>Release</td><td>No-Release</td><td>Release</td><td>No-Release</td><td>Release</td></tr><tr><td></td><td colspan="2">MCSI</td><td colspan="2">GDP</td><td colspan="2">CPI</td><td colspan="2">FOMC</td></tr><tr><td>Intercept</td><td>-1.70(-1.15)</td><td>-7.16(-1.21)</td><td>-1.72(-1.17)</td><td>-6.75(-0.94)</td><td>-1.93(-1.31)</td><td>0.42(0.06)</td><td>-1.49(-1.03)</td><td>-12.6(-1.61)</td></tr><tr><td><eq>\beta_{r_1}</eq></td><td>6.61***(3.90)</td><td>14.4***(3.40)</td><td>6.60***(3.90)</td><td>11.7**(2.37)</td><td>6.63***(3.90)</td><td>10.4*(1.95)</td><td>6.68***(3.98)</td><td>14.4**(2.35)</td></tr><tr><td><eq>\beta_{r_{12}}</eq></td><td>11.9***(2.64)</td><td>-5.51(-0.48)</td><td>12.0***(2.64)</td><td>-3.03(-0.24)</td><td>11.4**(2.56)</td><td>11.7(0.78)</td><td>10.9**(2.51)</td><td>34.1*(1.69)</td></tr><tr><td><eq>R^2</eq>(%)</td><td>2.6</td><td>5.5</td><td>2.7</td><td>3.0</td><td>2.5</td><td>5.0</td><td>2.5</td><td>11.0</td></tr></table>


Panel B: Timing Performance


<table><tr><td></td><td>Macro News</td><td>Avg Ret(%)</td><td>Std Dev(%)</td><td>SRatio</td><td>Skewness</td><td>Kurtosis</td></tr><tr><td>Non-Release</td><td>MCSI</td><td>6.05***(3.83)</td><td>6.24</td><td>0.97</td><td>0.91</td><td>15.83</td></tr><tr><td>Release</td><td>MCSI</td><td>19.09***(3.41)</td><td>4.94</td><td>3.86</td><td>0.91</td><td>2.28</td></tr><tr><td>Non-Release</td><td>GDP</td><td>6.28***(4.01)</td><td>6.19</td><td>1.01</td><td>0.91</td><td>16.26</td></tr><tr><td>Release</td><td>GDP</td><td>14.40**(2.08)</td><td>6.14</td><td>2.35</td><td>0.83</td><td>3.41</td></tr><tr><td>Non-Release</td><td>CPI</td><td>6.10***(3.88)</td><td>6.21</td><td>0.98</td><td>0.91</td><td>16.11</td></tr><tr><td>Release</td><td>CPI</td><td>18.03***(2.75)</td><td>5.80</td><td>3.11</td><td>0.90</td><td>3.84</td></tr><tr><td>Non-Release</td><td>FOMC</td><td>6.24***(4.01)</td><td>6.20</td><td>1.01</td><td>0.90</td><td>15.88</td></tr><tr><td>Release</td><td>FOMC</td><td>20.04**(2.46)</td><td>5.84</td><td>3.43</td><td>1.07</td><td>7.22</td></tr></table>

## Table 10: Transaction costs


This table reports the economic value of timing the last half-hour market return using the first halfhour return or combining with the twelfth half-hour return, incorporating the transaction costs due to the bid–ask spread. The timing strategy is described in Table 6. For each strategy, we report the average return $( A v g R e t )$ , standard deviation (Std Dev), Sharpe ratio (SRatio), skewness, and kurtosis. Panel A is for the period after decimalization (after July 1, 2001), and Panel B is for the period when the spread is stabilized (after January 1, 2005). The returns are annualized and in percentage. Newey and West (1987) robust t-statistics are in parentheses, and significance at the 1%, 5%, or 10% level is given by an ***, an ** or an *, respectively.


<table><tr><td>Timing</td><td>Avg Ret(%)</td><td>Std Dev(%)</td><td>SRatio</td><td>Skewness</td><td>Kurtosis</td></tr><tr><td></td><td colspan="5">Panel A: After July 1, 2001</td></tr><tr><td><eq>\eta(r_1)</eq></td><td>4.46***(2.58)</td><td>6.10</td><td>0.73</td><td>1.21</td><td>19.82</td></tr><tr><td><eq>\eta(r_1, r_{12})</eq></td><td>4.30***(3.44)</td><td>4.40</td><td>0.98</td><td>2.58</td><td>40.65</td></tr><tr><td>Always Long</td><td>-0.74(-0.42)</td><td>6.12</td><td>-0.12</td><td>-0.53</td><td>20.06</td></tr><tr><td>Buy-and-Hold</td><td>4.90(0.85)</td><td>20.34</td><td>0.24</td><td>-0.17</td><td>8.07</td></tr><tr><td></td><td colspan="5">Panel B: After January 1, 2005</td></tr><tr><td><eq>\eta(r_1)</eq></td><td>6.52***(3.00)</td><td>6.51</td><td>1.00</td><td>1.42</td><td>20.48</td></tr><tr><td><eq>\eta(r_1, r_{12})</eq></td><td>4.74***(3.01)</td><td>4.72</td><td>1.00</td><td>2.89</td><td>41.10</td></tr><tr><td>Always Long</td><td>-1.03(-0.47)</td><td>6.54</td><td>-0.16</td><td>-0.54</td><td>20.78</td></tr><tr><td>Buy-and-Hold</td><td>6.75(0.98)</td><td>20.72</td><td>0.33</td><td>-0.26</td><td>9.78</td></tr></table>


Table 11: Summary of other ETFs



This table describes the ten index ETFs to be used for the robustness analysis in Table 12. These ETFs are the most heavily traded ETFs as measured by their average daily trading volume from their inception dates to December 31, 2013.


<table><tr><td>Symbol</td><td>Name</td><td>Inception</td></tr><tr><td>QQQ</td><td>Powershare NASDAQ 100</td><td>03/10/1999</td></tr><tr><td>XLF</td><td>Financial Select Sector SPDR</td><td>12/22/1998</td></tr><tr><td>IWM</td><td>iShares Russell 2000 ETF</td><td>05/26/2000</td></tr><tr><td>DIA</td><td>Dow Jones Industrial Average ETF</td><td>01/20/1998</td></tr><tr><td>EEM</td><td>iShares MSCI Emerging Markets ETF</td><td>04/11/2003</td></tr><tr><td>FXI</td><td>iShares China Large-Cap ETF</td><td>10/8/2004</td></tr><tr><td>EFA</td><td>iShares MSCI EAFE ETF</td><td>08/17/2001</td></tr><tr><td>VWO</td><td>Emerging Markets ETF</td><td>03/10/2005</td></tr><tr><td>IYR</td><td>iShares U.S. Real Estate ETF</td><td>06/19/2000</td></tr><tr><td>TLT</td><td>20+ Year Treasury Bond ETF</td><td>07/26/2002</td></tr></table>


T<sub>a</sub>bl<sub>e</sub> 1 2 <sub>:</sub> Oth<sub>er</sub> ETF<sub>s</sub>



This table rep orts the average return (A vg Ret) standard deviation ( Std Dev) in-sample $R ^ { 2 }$ <sub>ou</sub>t-<sub>o</sub>f-<sub>samp</sub>l<sub>e</sub> $R ^ { 2 } ~ ( R _ { O S } ^ { 2 } )$ <sub>an</sub>d CER <sub>w</sub>ith th<sub>e</sub> <sub>same</sub> <sub>u</sub>tilit<sub>y</sub> <sub>ga</sub>i<sub>ns</sub> <sub>ana</sub>l<sub>ys</sub>i<sub>s</sub> <sub>as</sub> i<sub>n</sub> T<sub>a</sub>bl<sub>e</sub> 7 <sub>,</sub> <sub>excep</sub>t <sub>rep</sub>l<sub>aces</sub> th<sub>e</sub> <sub>mar</sub>k<sub>e</sub>t <sub>re</sub>t<sub>urn</sub> b<sub>y</sub> <sub>one</sub> <sub>o</sub>f th<sub>e</sub> t<sub>en</sub> ETF<sub>s .</sub> All <sub>quan</sub>titi<sub>es</sub> <sub>are</sub> i<sub>n</sub> <sub>p ercen</sub>t<sub>age ,</sub> <sub>an</sub>d <sub>re</sub>t<sub>urns</sub> <sub>an</sub>d <sub>s</sub>t<sub>an</sub>d<sub>ar</sub>d d<sub>ev</sub>i<sub>a</sub>ti<sub>ons</sub> <sub>are</sub> <sub>annua</sub>li<sub>ze</sub>d <sub>.</sub> P<sub>ane</sub>l A <sub>rep or</sub>t<sub>s</sub> th<sub>e</sub> <sub>resu</sub>lt<sub>s</sub> <sub>us</sub>i<sub>ng</sub> th<sub>e</sub> fi<sub>rs</sub>t h<sub>a</sub>lf-h<sub>our</sub> <sub>re</sub>t<sub>urn</sub> $( r _ { 1 } )$ t<sub>o</sub> f<sub>orecas</sub>t <sub>an</sub>d P<sub>ane</sub>l B <sub>rep or</sub>t <sub>s</sub> t h<sub>e</sub> <sub>resu</sub>lt <sub>s</sub> <sub>us</sub>i<sub>ng</sub> b <sub>o</sub>t h $r _ { 1 }$ <sub>an</sub>d $r _ { 1 2 }$ to forecast <sub>.</sub> Newey and West ( 1 98 7) robust t- st at ist ics are in parent heses and significance at th<sub>e</sub> 1 % 5 % <sub>or</sub> 1 0% l<sub>eve</sub>l i<sub>s</sub> <sub>g</sub>i<sub>ven</sub> b<sub>y</sub> <sub>an</sub> <sup>* * *</sup> <sub>an</sub> <sup>* *</sup> <sub>or</sub> <sub>an</sub> <sup>*</sup> <sub>resp ec</sub>ti<sub>ve</sub>l<sub>y.</sub> Th<sub>e</sub> <sub>samp</sub>l<sub>e</sub> <sub>p er</sub>i<sub>o</sub>d f<sub>or</sub> <sub>eac</sub>h ETF i<sub>s</sub> f<sub>rom</sub> it<sub>s</sub> i<sub>ncep</sub>ti<sub>on</sub> d<sub>a</sub>t<sub>e</sub> t<sub>o</sub> D<sub>ecem</sub>b <sub>er</sub> 3 1 20 1 3 <sub>exc</sub>l<sub>u</sub>di<sub>ng</sub> d<sub>ays w</sub>ith f<sub>ewer</sub> th<sub>an</sub> 1 00 t<sub>ra</sub>d<sub>es .</sub>



Fund Avg Ret (% ) Std Dev (% ) $R ^ { 2 } ( \% )$ $R _ { O S } ^ { 2 } ( \% )$ CER ( % ) Avg Ret ( % ) Std Dev ( % ) $R ^ { 2 } ( \% )$ $R _ { O S } ^ { 2 } ( \% )$ CER(%)


<table><tr><td></td><td colspan="5">Panel A: <eq>\beta_1r_1</eq></td><td colspan="5">Panel B: <eq>\beta_1r_1 + \beta_2r_{12}</eq></td></tr><tr><td>QQQ</td><td>7.75***(3.65)</td><td>7.89</td><td>1.43</td><td>0.70</td><td>7.38</td><td>8.34***(3.83)</td><td>8.08</td><td>2.26</td><td>0.50</td><td>7.96</td></tr><tr><td>XLF</td><td>12.04***(4.36)</td><td>9.95</td><td>3.64</td><td>3.55</td><td>12.44</td><td>8.73***(3.24)</td><td>9.70</td><td>4.37</td><td>2.19</td><td>9.13</td></tr><tr><td>IWM</td><td>11.72***(5.18)</td><td>7.70</td><td>2.51</td><td>2.43</td><td>11.72</td><td>12.12***(4.45)</td><td>9.26</td><td>4.53</td><td>3.81</td><td>12.09</td></tr><tr><td>DIA</td><td>3.46**(2.35)</td><td>5.69</td><td>1.16</td><td>1.03</td><td>4.16</td><td>4.63***(2.79)</td><td>6.40</td><td>2.25</td><td>1.81</td><td>5.31</td></tr><tr><td>EEM</td><td>14.76***(4.91)</td><td>9.01</td><td>8.54</td><td>6.53</td><td>14.69</td><td>18.46***(6.01)</td><td>9.20</td><td>13.27</td><td>10.43</td><td>18.38</td></tr><tr><td>FXI</td><td>18.42***(5.20)</td><td>10.17</td><td>7.80</td><td>5.90</td><td>17.71</td><td>15.98***(4.35)</td><td>10.54</td><td>10.42</td><td>7.52</td><td>15.26</td></tr><tr><td>EFA</td><td>7.45***(4.16)</td><td>5.82</td><td>3.53</td><td>1.90</td><td>7.18</td><td>6.53***(3.69)</td><td>5.76</td><td>4.79</td><td>1.43</td><td>6.27</td></tr><tr><td>VWO</td><td>12.18***(3.76)</td><td>8.72</td><td>5.72</td><td>4.39</td><td>12.12</td><td>13.61***(4.15)</td><td>8.83</td><td>8.45</td><td>6.29</td><td>13.55</td></tr><tr><td>IYR</td><td>24.22***(5.86)</td><td>12.29</td><td>5.29</td><td>4.60</td><td>14.98</td><td>29.80***(6.43)</td><td>13.78</td><td>11.77</td><td>9.82</td><td>20.52</td></tr><tr><td>TLT</td><td>4.03***(4.32)</td><td>2.89</td><td>1.77</td><td>1.65</td><td>2.26</td><td>4.50***(5.14)</td><td>2.71</td><td>1.81</td><td>1.51</td><td>2.73</td></tr></table>


T<sub>a</sub>bl<sub>e</sub> 1 3 <sub>:</sub> P<sub>re</sub>di<sub>c</sub>t <sub>a</sub>bilit<sub>y o</sub>f th<sub>e</sub> l<sub>as</sub>t h<sub>a</sub>lf-h<sub>our re</sub>t<sub>urns :</sub> M<sub>u</sub>lti<sub>var</sub>i<sub>a</sub>t<sub>e regress</sub>i<sub>ons</sub>



Thi<sub>s</sub> t <sub>a</sub>bl<sub>e</sub> <sub>rep or</sub>t <sub>s</sub> <sub>mu</sub>lt i<sub>var</sub>i<sub>a</sub>t<sub>e</sub> <sub>regress</sub>i<sub>on</sub> <sub>resu</sub>lt <sub>s</sub> <sub>o</sub>f <sub>regress</sub>i<sub>ng</sub> t h<sub>e</sub> l<sub>as</sub>t h<sub>a</sub>lf- h<sub>our</sub> <sub>re</sub>t <sub>urn</sub> $r _ { 1 3 } ,$ <sub>on</sub> <sub>a</sub>ll <sub>o</sub>f t h<sub>e</sub> fi<sub>rs</sub>t 1 2 h<sub>a</sub>lf- h<sub>our</sub> <sub>re</sub>t <sub>urns</sub> f<sub>or</sub> SPY <sub>an</sub>d 1 0 <sub>o</sub>th<sub>er</sub> <sub>mos</sub>t h<sub>eav</sub>il<sub>y</sub> t<sub>ra</sub>d<sub>e</sub>d ETF<sub>s .</sub> $r _ { k }$ d<sub>eno</sub>t<sub>es</sub> th<sub>e</sub> kth h<sub>a</sub>lf-h<sub>our</sub> <sub>re</sub>t<sub>urn</sub> <sub>o</sub>f th<sub>e</sub> d<sub>ay</sub> <sub>w</sub>h<sub>ere</sub> $k = 1 , 2 , \cdots , 1 2$ <sub>.</sub> Th<sub>e</sub> <sub>re</sub>t <sub>urns</sub> <sub>are</sub> annualized and in p ercentage and the coeficients are scaled by 1 00 Newey and West ( 1 987) robust t-statistics are in parentheses and <sub>s</sub>i<sub>gn</sub>ifi<sub>cance a</sub>t th<sub>e</sub> 1 % 5 % <sub>or</sub> 1 0% l<sub>eve</sub>l i<sub>s g</sub>i<sub>ven</sub> b<sub>y an</sub> <sup>* * *</sup> <sub>an</sub> <sup>* *</sup> <sub>or an</sub> <sup>*</sup> <sub>resp ec</sub>ti<sub>ve</sub>l<sub>y.</sub> Th<sub>e samp</sub>l<sub>e p er</sub>i<sub>o</sub>d f<sub>or eac</sub>h ETF i<sub>s</sub> f<sub>rom</sub> it<sub>s</sub> inception date to Decemb er 3 1 20 1 3 excluding days with fewer than 1 00 trades ( 500 for S PY) <sub>.</sub>


<table><tr><td>ETFs</td><td>Intercept</td><td><eq>r_1</eq></td><td><eq>r_2</eq></td><td><eq>r_3</eq></td><td><eq>r_4</eq></td><td><eq>r_5</eq></td><td><eq>r_6</eq></td><td><eq>r_7</eq></td><td><eq>r_8</eq></td><td><eq>r_9</eq></td><td><eq>r_{10}</eq></td><td><eq>r_{11}</eq></td><td><eq>r_{12}</eq></td><td><eq>R^2(\%)</eq></td></tr><tr><td>SPY</td><td>-1.30(-0.87)</td><td>6.51***(4.35)</td><td>6.58*(1.92)</td><td>6.72(1.51)</td><td>1.22(0.30)</td><td>8.67*(1.88)</td><td>6.61(1.03)</td><td>-10.00(-1.58)</td><td>-5.83(-1.12)</td><td>-2.93(-0.49)</td><td>2.56(0.50)</td><td>1.23(0.27)</td><td>11.06**(2.53)</td><td>4.10</td></tr><tr><td>QQQ</td><td>-2.51(-1.15)</td><td>5.67***(3.79)</td><td>1.69(0.61)</td><td>8.46**(2.30)</td><td>3.60(0.89)</td><td>8.12**(2.10)</td><td>3.79(0.76)</td><td>-1.74(-0.35)</td><td>2.40(0.63)</td><td>-2.14(-0.47)</td><td>3.96(0.98)</td><td>8.52**(2.25)</td><td>9.76***(2.59)</td><td>3.90</td></tr><tr><td>XLF</td><td>2.61(1.07)</td><td>8.48***(4.47)</td><td>4.74(1.13)</td><td>5.36(1.02)</td><td>4.05(0.87)</td><td>10.63**(2.05)</td><td>14.62**(2.02)</td><td>-3.23(-0.49)</td><td>-0.30(-0.06)</td><td>-4.82(-0.69)</td><td>2.19(0.36)</td><td>10.53*(1.83)</td><td>10.61*(1.85)</td><td>6.70</td></tr><tr><td>IWM</td><td>1.41(0.65)</td><td>8.38***(6.06)</td><td>6.41**(2.02)</td><td>10.19**(2.41)</td><td>2.05(0.51)</td><td>12.56***(3.02)</td><td>10.43(1.64)</td><td>-8.17(-1.13)</td><td>-0.26(-0.04)</td><td>-2.71(-0.45)</td><td>6.27(1.06)</td><td>2.87(0.55)</td><td>18.83***(4.03)</td><td>6.80</td></tr><tr><td>DIA</td><td>-0.47(-0.32)</td><td>6.01***(3.81)</td><td>6.37*(1.73)</td><td>5.08(1.07)</td><td>0.61(0.14)</td><td>9.89**(2.03)</td><td>5.83(0.93)</td><td>-13.14*(-1.89)</td><td>-8.88(-1.58)</td><td>-0.74(-0.11)</td><td>3.43(0.60)</td><td>1.74(0.36)</td><td>11.47**(2.18)</td><td>3.90</td></tr><tr><td>EEM</td><td>-1.71(-0.74)</td><td>9.59***(5.71)</td><td>5.23(1.02)</td><td>9.31(1.31)</td><td>-2.56(-0.40)</td><td>4.42(0.67)</td><td>7.09(0.86)</td><td>-19.21*(-1.89)</td><td>0.96(0.09)</td><td>4.35(0.42)</td><td>3.23(0.43)</td><td>9.43(1.40)</td><td>26.73***(4.08)</td><td>15.60</td></tr><tr><td>FXI</td><td>-1.70(-0.61)</td><td>8.55***(5.70)</td><td>6.63(1.15)</td><td>6.52(0.86)</td><td>1.74(0.24)</td><td>5.03(0.62)</td><td>7.21(0.71)</td><td>-17.28(-1.56)</td><td>5.86(0.61)</td><td>10.04(0.93)</td><td>-4.23(-0.43)</td><td>5.54(0.70)</td><td>21.98***(2.95)</td><td>12.20</td></tr><tr><td>EFA</td><td>1.42(0.92)</td><td>5.46***(4.32)</td><td>2.82(0.73)</td><td>5.97(1.04)</td><td>-1.64(-0.39)</td><td>3.82(0.85)</td><td>5.83(0.77)</td><td>-16.08*(-1.79)</td><td>-2.37(-0.34)</td><td>-5.36(-0.55)</td><td>7.72(1.13)</td><td>5.41(0.82)</td><td>12.21*(1.78)</td><td>6.90</td></tr><tr><td>VWO</td><td>0.96(0.37)</td><td>7.29***(4.31)</td><td>4.24(0.78)</td><td>8.49(1.23)</td><td>0.67(0.11)</td><td>7.68(1.23)</td><td>4.89(0.58)</td><td>-16.32*(-1.72)</td><td>3.10(0.34)</td><td>-1.21(-0.11)</td><td>0.07(0.01)</td><td>3.83(0.57)</td><td>18.60***(2.79)</td><td>10.20</td></tr><tr><td>IYR</td><td>12.93***(3.91)</td><td>13.94***(4.17)</td><td>1.99(0.34)</td><td>6.54(0.80)</td><td>-1.02(-0.13)</td><td>5.92(0.66)</td><td>19.84**(2.08)</td><td>-15.86(-1.49)</td><td>-10.19(-1.10)</td><td>-2.18(-0.24)</td><td>16.54*(1.92)</td><td>1.53(0.18)</td><td>35.01***(3.93)</td><td>14.30</td></tr><tr><td>TLT</td><td>1.40**(2.06)</td><td>2.96***(4.60)</td><td>1.94(1.28)</td><td>5.00**(2.16)</td><td>1.56(0.68)</td><td>-1.43(-0.56)</td><td>0.37(0.15)</td><td>-0.32(-0.14)</td><td>0.59(0.31)</td><td>0.20(0.07)</td><td>1.75(0.84)</td><td>-0.62(-0.14)</td><td>-3.72(-1.10)</td><td>2.20</td></tr></table>