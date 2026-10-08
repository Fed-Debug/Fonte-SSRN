# THE MICROSTRUCTURE OF THE ‘FLASH CRASH’ Flow toxicity, liquidity crashes and the Probability of Informed Trading

David Easley dae3@cornell.edu 

Marcos M. López de Prado marcos.lopezdeprado@tudor.com 

Maureen O’Hara mo19@cornell.edu 

November 19<sup>th</sup>, 2010 

## ABSTRACT

The ‘flash crash’ of May $6 ^ { \mathrm { t h } }$ 2010 was the second largest point swing (1,010.14 points) and the biggest one-day point decline (998.5 points) in the history of the Dow Jones Industrial Average. For a few minutes, $1 trillion in market value vanished. In this paper, we argue that the ‘flash crash’ is the result of the new dynamics at play in the current market structure. We highlight the role played by order toxicity in affecting liquidity provision, and we show that a measure of this toxicity, the Volume-Synchronized Probability of Informed Trading (VPIN)*, captures the increasing toxicity of the order flow in the hours and days prior to collapse. Since the ‘flash crash’ might have been avoided had liquidity providers remained in the marketplace, a solution is proposed in the form of a ‘VPIN contract’ which would allow them to dynamically monitor and manage their risks. 

Keywords: Flash crash, liquidity, flow toxicity, market microstructure, probability of informed trading, VPIN. 

JEL codes: C02, D52, D53, G14. 

## 1.Introduction

The events of May $6 ^ { \mathrm { t h } }$ continue to reverberate through the financial markets. The “flash crash” featured the biggest one-day point decline (998.5 points) in the history of the Dow Jones Industrial Average. Futures were also affected, with the price of the E-mini S&P 500 futures collapsing by 5% between 2:30pm<sup>1</sup> and 2:45pm, on top of the 2.97% it had already retreated intraday. This price drop was accompanied by an unusually large volume of transactions (see Figure 1). Between 2:30pm and 3:00pm, in excess of 1.1 million contracts were exchanged in E-mini S&P 500 June 2010 futures alone.<sup>2</sup> Across both futures and equity markets, "there was a complete evaporation of liquidity in the marketplace". 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-30/d8f9b93d-6ed0-4838-90e3-5c33be6072ec/29d262f1bbf38455a756d88e6244843faa6e1b6d182c36ba3af9b841fe00c740.jpg)



Figure 1 – Futures price and volume during the crash.


Observers were quick to offer explanations for the flash crash: 

1. Minutes after the crash, there was speculation that a “fat-finger trade” in ‘Procter & Gamble’ had triggered a cascade of stop loss orders. This explanation was short-lived, as E-mini S&P500 tick data demonstrates that the market was already down by the time ‘Procter & Gamble’ stock plummeted. 

2. Technical reporting difficulties at NYSE and ARCA, as well as delays in the consolidated tape, were alleged to have contributed to the market’s free fall.<sup>5</sup> 

3. Some analysts blamed currency movements, in particular changes in the U.S. Dollar/Japanese Yen exchange rate. 

4. The Wall Street Journal suggested a large purchase of put options by the hedge fund ‘Universa Investments’ may have been the primary cause. 

5. Similar speculation centered on a sale of 75,000 E-Mini contracts by Waddell & Reed as causing the futures market to dislocate.<sup>8</sup> 

6. Nanex argued that a predatory practice called “quote stuffing” forced competitors to slow down their operations in order to catch up with the overwhelming amount of data to be processed by their algorithms. 

The CFTC-SEC Staff Report on the market events of May 6 identifies automated execution of a large sell order in the E-mini contract as precipitating the actual crash. What then followed was “two liquidity crises – one at the broad index level in the Emini, the other with respect to individual stocks.”<sup>9</sup> This generalized severe mismatch in liquidity was exacerbated by the withdrawal of liquidity by some electronic market makers and by uncertainty about, or delays in, market data affecting the actions of market participants. 

This paper presents additional evidence to support this liquidity explanation. Our analysis shows that the liquidity problem was slowly developing in the hours and days before the collapse. Just prior to the inauspicious trade, volume was high and unbalanced, but liquidity was low. We present evidence that during this period order flow was becoming increasingly toxic for market makers. In a high frequency world, order flow toxicity can cause market makers to leave the market, setting the stage for episodic illiquidity. In other research (see Easley, López de Prado and O’Hara (2010)), we develop a technique that allows us to measure this order flow toxicity. In this paper, we use this new measure to address two flash crash-related questions of particular relevance for portfolio managers: Is this anomaly likely to occur in future? And if so, are there any tools to monitor in real-time the likelihood of it occurring again? In the next section, we argue that the answer to the first question is yes. The rest of the paper will be dedicated to answering the second question. 

## 2. New Trends in Market Structure

Since 2009 high-frequency trading firms, which represent approximately 2% of the nearly 20,000 trading firms operating in the U.S. markets, have accounted for over 73% of all U.S. equity trading volume.<sup>10</sup> The CFTC, citing research by Rosenblatt 

Securities, estimates that high-frequency trading constitutes approximately 35% of U.S. futures markets volume, and that its share is expected to grow to 60% by the end of 2010.<sup>11</sup> This increased share of high-frequency traders has not been accompanied by an increase in absolute volume. On the contrary, since 2009 overall equity and futures volumes have fallen, in part due to the lack of participation of retail investors that followed the market downturn in 2008. 

Many of these high frequency firms are in the business of liquidity provision, acting as market makers to position takers.<sup>12</sup> Liquidity provision is a complex process, as position takers may know more about the future direction of prices than do market makers. But position takers also need liquidity, or someone to take the other side of their trade, and market makers can profit by earning the spread provided they can control their position risk. Most liquidity providers do not seek to make a directional bet, but instead participate on both sides of the book in an attempt to maximize the turnover of their inventory. Indeed, the typical high frequency market maker turns over his or her inventory 5 or more times a day, explaining how high frequency firms have come to have such a high share of trading volume. These market makers also seek to hold very small or even zero inventory positions at the end of the session.<sup>13</sup> This short holding period, combined with very small inventories, allows market makers to operate intraday with very low capital, essentially using their speed of trading to control their position risk. 

Providing liquidity in a high frequency environment introduces new risks for market makers. When order flows are essentially balanced, high frequency market makers have the potential to earn razor thin margins on massive numbers of trades. When order flows become unbalanced, however, market makers face the prospect of losses due to adverse selection. The market makers’ estimate of the toxicity (the expected loss from trading with better informed counterparties) of the flow directed to them by position takers now becomes a crucial factor in determining their participation. If they believe that this toxicity is too high, they will liquidate their positions and leave the market. 

In summary, we see three forces at play in the current market structure: 

• Concentration of liquidity provision into a small number of highly specialized firms. 

Reduced participation of retail investors resulting in increased toxicity of the flow received by market makers. 

High sensitivity of liquidity providers to intraday losses, as a result of the liquidity providers’ low capitalization, high turnover, increased competition and small profit target. 

These forces, combined with the ability of high frequency traders to vanish quickly from the market, portend episodes of sudden illiquidity. 

## 3. Liquidity on May ${ \bf 6 ^ { t h } }$ : Market Makers vs. Position Takers

Although May $6 ^ { \mathrm { t h } }$ 2010 was the third-highest-volume-day in the history of E-mini S&P 500 futures, there is consensus in categorizing it as an extremely illiquid day. Indeed, the CFTC-SEC report stresses that “high trading volume is not necessarily a reliable indicator of market liquidity.”<sup>14</sup> That volume and liquidity need not be congruent is a reflection of the delicate symbiosis between market makers and position takers in a high frequency world. 

In the following analysis, we evaluate whether market makers may have withdrawn from the marketplace during the events of May $6 ^ { \mathrm { t h } }$ 2010 as a result of an accumulation of losses and/or extraordinary flow toxicity, inflicted by position takers, in the preceding days and hours. To investigate this hypothesis, we apply a measure of order toxicity (the VPIN metric) developed in Easley, López de Prado and O’Hara (2010) to show how order flow became increasingly toxic over the day. We also show that movements in this VPIN metric measure foreshadowed the actual crash, providing as it were an early-warning of liquidity problems. 

In a high frequency framework, both time and information have different meanings than in more standard microstructure models. Because trades take place in miliseconds, trade time rather than clock time is the relevant metric to use in sampling the information set. Trade time can be measured by volume increments, and the VPIN metric is calibrated using pre-set volume buckets. Similarly, because market makers hold positions for very short periods, information events can reflect asset-related news and/or portfolio-related news. For example, in a futures setting, information that induces traders to all hedge in one direction can portend future movements in futures prices, and thus prove toxic to market makers on the other side of those trades. Easley, López de Prado and O’Hara (2010) develop a microstructure model to capture these high frequency dimensions, and this model produces the VPIN metric we use here to measure toxicity. 

For any time period, the VPIN metric is the ratio of average unbalanced volume to total volume in that period. Heuristically, the VPIN metric measures the fraction of volume-weighted trade that arises from informed traders as the informed tend to trade on one-side of the market and so their activity leads to unbalanced volume (either more buy volume than sells volume or the reverse). In periods in which there is a lot of information-based trade, the VPIN metric will be large. During these periods, market makers are on the wrong side of the trade with the informed (i.e. buying when prices are moving down, and conversely), and so they will accumulate or lose inventory on the wrong side of the market. As market prices move, market makers will make losses on their positions. If these losses accumulate, we would expect market makers to undo their positions, thus adding to the imbalance in trade and potentially leading to a crash. 

## 4. Estimating Order Toxicity: The VPIN metric

The methodology for estimating the VPIN metric is developed in Easley, López de Prado and O’Hara (2010), and we refer the interested reader to that paper. In this paper we focus on the VPIN metrics for the E-mini S&P 500 futures contract for the time period between January $1 ^ { \mathrm { s t } }$ 2008 and October ${ 3 0 } ^ { \mathrm { t h } }$ 2010. We compute the average daily volume for this contract and then estimate a VPIN value for each time period in which one-fiftieth of this volume is traded. This procedure results in an average of fifty VPIN metric values per day, but on very active days the VPIN metric will be updated much more frequently than on less active days. 

The following chart shows the evolution of E-mini S&P 500 (red line, expressed in terms of market value) and the VPIN metric (green line). Two features of the data are striking. First, the VPIN metric is generally a stable process. Second, the VPIN metric reached its highest level for this sample on May $6 ^ { \mathrm { t h } }$ 2010, providing quantitative support to the qualitative assertion that “liquidity evaporated”. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-30/d8f9b93d-6ed0-4838-90e3-5c33be6072ec/5c5e4d734a47b6dc295c531b593728e87d49b54690228533ed1386afac51ef3e.jpg)



Figure 2 - VPIN metric between January 1<sup>st</sup> 2008 and October $\overline { { 3 { \cal O } ^ { t h } } }$ 2010


Before analyzing the VPIN metric in the crash period, it is useful to consider more carefully some statistical properties of the VPIN metric. Figure 3 plots the empirical distribution of the VPIN metric estimates for the entire sample period. This distribution can be closely approximated by a log-normal, and we will use the cumulative distribution function of the fitted log-normal to provide a measure of how unusual a particular level of the VPIN metric is relative to what is normal for the Emini S&P 500 futures contract. For example, 80% of the VPIN metric estimates are below 0.44 (i.e. ), so VPIN metric estimates of more than 0.44 occurCDF( ) = 8.044.0 in only about 20% of the estimates. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-30/d8f9b93d-6ed0-4838-90e3-5c33be6072ec/b5ba5ae197bf0545eb5737417d2b06575198cf37c90c3fca09cdadfe5dc2f9af.jpg)



Figure 3 - The empirical CDF of the VPIN metric



as fitted through a log-normal distribution


## 5. Measuring Order Flow Toxicity before the Crash

We now turn to the behavior of the VPIN metric in the hours and days prior to the crash. The events of May $6 ^ { \mathrm { t h } }$ have been categorized as a liquidity-induced crash, so the VPIN metric should have reflected the increasing toxicity of order flow in the market and its consequent effect on liquidity providers. We focus on the behavior of the E-mini future VPIN metric, but we note that other futures contracts were also affected by events on May $6 ^ { \mathrm { t h } }$ and VPIN results for those contracts are similar.<sup>15</sup> 

Our first observation is that the VPIN metric for the E-mini S&P 500 future was abnormally high at least one week before the flash crash. Figure 4 shows the value of the E-mini S&P 500, the value of the VPIN metric, and, for each estimated value of the VPIN metric, the fraction of the empirical distribution that is less than this value of the VPIN metric, CDF(VPIN). This measure of the likelihood of the VPIN metric being less than or equal to the current value is volatile, but it was generally unusually high during the week before the flash crash. Such behavior must have placed market makers on the alert, as the toxicity of flow directed to them was gradually becoming more unpredictable. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-30/d8f9b93d-6ed0-4838-90e3-5c33be6072ec/42b22d56645e8dee900135956f8598f397dba534c77e1e975a2aab43916df67a.jpg)



Figure 4 – E-mini S&P 500’s VPIN metric one week before and after the flash crash


Our second observation is that this situation worsened (from the point of view of liquidity providers) several hours before the crash. This is illustrated in Figure 5 which shows that by 11:55am on May $6 ^ { \mathrm { t h } }$ , the realized value of the VPIN metric was in the 10% tail of the distribution (it exceeded a 90% CDF(VPIN) critical value). By 1:08pm, the realized value of the VPIN metric was in the 5% tail of the distribution (over a 95% CDF(VPIN)). By 2:30pm the VPIN metric reached its highest level in the history of the E-mini S&P500. At 2:32pm the crash begins according to the CFTC-SEC Report time line. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-30/d8f9b93d-6ed0-4838-90e3-5c33be6072ec/f0b3824fc8c2837379c82da108455e89b6dd874b3a019358ae5505ec14b67712.jpg)



Figure 5 – E-mini S&P 500’s VPIN metric on May $\boldsymbol { \delta } ^ { t h }$


As market makers were being overwhelmed by toxic flow (measured in terms of unusually high levels of the VPIN metric), many high frequency firms decided to withdraw from the market<sup>16</sup>. According to the CFTC-SEC report, “HFTs, therefore, initially provided liquidity to the market. However, between 2:41 and 2:44p.m., HFTs aggressively sold about 2,000 E-Mini contracts in order to reduce their temporary long positions”.<sup>17</sup> The report also notes that the activity of the HF firms from 2:00 through 2:45pm “is consistent with some HFT firms reducing or pausing trading during that time”.<sup>18</sup> 

Large liquidity providers experienced severe losses and some eventually had to stop trading. According to filings with the Securities and Exchange Commission, Goldman Sachs had 10 days of trading losses, including three days of more than $100 million in trading losses. These have been partly attributed to the events surrounding May 6<sup>th</sup>, 2010.<sup>19</sup> Morgan Stanley and Bank of America reported similar trading losses during the same period. This picture contrasts with that of firms taking liquidity from the market, like TD Ameritrade, which saw an unusually high level of activity on May 6<sup>th</sup> 2010. "Like everyone else, that day was a big day for us", CEO Fred Tomczyk said at the Sandler O'Neill Conference. "We had a lot of trades. We don't talk too publicly about the number, but that day was a record day for us."<sup>20</sup> 

## 6. VPIN vs. VIX

The movement in VPIN foreshadowed the price movement in the E-mini contract. One might conjecture that measures of price volatility, such as the VIX, might also have played a similar role on May 6 . But that is simply not the case: VIX and VPIN exhibited very different behavior on the day of the crash. Of particular importance, VIX lagged E-mini S&P 500 future’s VPIN metric before, during and after the event. 

Figure 6 demonstrates the behavior of the VIX, the VPIN, and the E-mini future price on the day of the crash. Following an initial dip at the beginning of the trading day, VIX did experience a run up, from an open of 25.92 at 9:30am to its highest value of the day, 40.69 at 15:28pm. Unlike what we observed with the E-mini VPIN metric, these levels of VIX are far from being their highest in recent history (the VIX reached 89.53 on October 24, 2008). 

While the VPIN metric exhibited a smooth, gradual increase during the day of the flash crash, reaching levels consistent with a 90% CDF(VPIN) by 11:55am, VIX did not hit comparable levels until after the market had collapsed to its lowest level. So rather than anticipating the crash, VIX was impacted by the crash. Indeed, VIX itself became extremely volatile between 2:46pm and 4pm, retreating to 33.32 at around 3:16pm. Such behavior is not surprising: VIX is an investable product, and it was subject to the same price and liquidity imperfections as the rest of the investment universe. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-30/d8f9b93d-6ed0-4838-90e3-5c33be6072ec/94cb6911ea7e4535822f7a66cedb31bb955ed1b2df396965dba676c9013f24bf.jpg)



Figure 6 – VIX and E-mini’s VPIN metric during the crash


## 7. VPIN as a Measure of the Risk of Liquidity-Induced Crashes

High frequency traders generate well over 60% of the volume in equity futures markets. But we have estimated that during the volume burst that triggered the crash, nearly 80% of the flow in the E-mini future was toxic. So although high frequency traders usually provide liquidity, the CFTC-SEC report suggests they turned to consuming liquidity during the crash, in effect producing toxic order flow. This behavior, in turn, exacerbated the developing liquidity crisis. 

To understand why toxicity of order flow can induce such behavior from market makers, let us return to the role that information plays in affecting liquidity in the market. Easley and O’Hara (1992) sets out the mechanism by which informed traders extract wealth from liquidity providers. For example, if a liquidity provider trades against a buy order he loses the difference between the ask price and the expected value of the contract if the buy is from an informed trader. On the other hand, he gains the difference between the ask price and the expected value of the contract if the buy is from an uninformed trader. This loss and gain, weighted by the probabilities of the trade arising from an informed trader or an uninformed trader just balance due to the intense competition between liquidity providers. 

$$
\underbrace {\left(A - E \left[ S _ {T} \mid U , B u y \right]\right) \operatorname* {P r} o b (U \mid B u y)} _ {\text {Gain from an uninformed trader}} = - \underbrace {\left(A - E \left[ S _ {T} \mid I , B u y \right]\right) \operatorname* {P r} o b (I \mid B u y)} _ {\text {Loss to an informed trader}}
$$

If flow toxicity unexpectedly rises (a greater than expected fraction of trades arises from informed traders), market makers face losses. Their inventory may grow beyond their risk limits, in which case they are forced to withdraw from the side of the market that is being adversely selected. Their withdrawal generates further weakness on that side of the market and their inventories keep accumulating additional losses. At some point they capitulate, dumping their inventory and taking the loss. In other words, extreme toxicity has the ability to transform liquidity providers into liquidity consumers. This is likely to be particularly true in the context of equity and equity futures markets, which have been the most impacted by the new trends in market microstructure discussed in Section 2. 

Over the short horizon high frequency liquidity providers deem relevant, the toxicity of orders matters because it can signal potentially adverse future movement of returns. Table 1 shows the distribution of absolute returns between two consecutive volume buckets, conditional on the previous level of VPIN for the E-mini S&P500. That these are probabilities of absolute returns conditional on VPIN can be appreciated from the fact that each row adds up to 100%. VPIN ranges have been chosen to contain each 5% of the total 37163 observations from January 1<sup>st</sup> 2008 to October 30<sup>th</sup> 2010. 

<table><tr><td></td><td>0.25%</td><td>0.50%</td><td>0.75%</td><td>1.00%</td><td>1.25%</td><td>1.50%</td><td>1.75%</td><td>2.00%</td><td>&gt;2.00%</td></tr><tr><td>0.285</td><td>83.53%</td><td>13.19%</td><td>2.37%</td><td>0.59%</td><td>0.27%</td><td>0.00%</td><td>0.00%</td><td>0.05%</td><td>0.00%</td></tr><tr><td>0.301</td><td>82.51%</td><td>14.32%</td><td>2.21%</td><td>0.59%</td><td>0.11%</td><td>0.11%</td><td>0.11%</td><td>0.00%</td><td>0.05%</td></tr><tr><td>0.312</td><td>83.42%</td><td>13.83%</td><td>2.10%</td><td>0.48%</td><td>0.05%</td><td>0.00%</td><td>0.11%</td><td>0.00%</td><td>0.00%</td></tr><tr><td>0.320</td><td>81.32%</td><td>14.64%</td><td>2.74%</td><td>0.81%</td><td>0.32%</td><td>0.05%</td><td>0.11%</td><td>0.00%</td><td>0.00%</td></tr><tr><td>0.327</td><td>81.33%</td><td>15.55%</td><td>2.10%</td><td>0.54%</td><td>0.22%</td><td>0.16%</td><td>0.05%</td><td>0.00%</td><td>0.05%</td></tr><tr><td>0.334</td><td>80.25%</td><td>16.15%</td><td>2.64%</td><td>0.65%</td><td>0.16%</td><td>0.16%</td><td>0.00%</td><td>0.00%</td><td>0.00%</td></tr><tr><td>0.341</td><td>79.87%</td><td>16.31%</td><td>2.69%</td><td>0.86%</td><td>0.16%</td><td>0.11%</td><td>0.00%</td><td>0.00%</td><td>0.00%</td></tr><tr><td>0.348</td><td>78.90%</td><td>16.42%</td><td>2.80%</td><td>0.97%</td><td>0.54%</td><td>0.32%</td><td>0.00%</td><td>0.00%</td><td>0.05%</td></tr><tr><td>0.354</td><td>81.27%</td><td>14.91%</td><td>2.80%</td><td>0.75%</td><td>0.11%</td><td>0.11%</td><td>0.00%</td><td>0.00%</td><td>0.05%</td></tr><tr><td>0.360</td><td>79.40%</td><td>15.76%</td><td>3.50%</td><td>0.65%</td><td>0.38%</td><td>0.16%</td><td>0.05%</td><td>0.05%</td><td>0.05%</td></tr><tr><td>0.367</td><td>80.03%</td><td>15.45%</td><td>3.18%</td><td>0.81%</td><td>0.38%</td><td>0.05%</td><td>0.11%</td><td>0.00%</td><td>0.00%</td></tr><tr><td>0.374</td><td>80.41%</td><td>15.45%</td><td>3.12%</td><td>0.81%</td><td>0.11%</td><td>0.11%</td><td>0.00%</td><td>0.00%</td><td>0.00%</td></tr><tr><td>0.382</td><td>78.63%</td><td>15.82%</td><td>3.50%</td><td>1.02%</td><td>0.43%</td><td>0.38%</td><td>0.11%</td><td>0.05%</td><td>0.05%</td></tr><tr><td>0.390</td><td>78.26%</td><td>16.42%</td><td>3.77%</td><td>0.91%</td><td>0.43%</td><td>0.11%</td><td>0.05%</td><td>0.00%</td><td>0.05%</td></tr><tr><td>0.399</td><td>74.77%</td><td>19.53%</td><td>3.77%</td><td>1.34%</td><td>0.32%</td><td>0.16%</td><td>0.11%</td><td>0.00%</td><td>0.00%</td></tr><tr><td>0.410</td><td>73.36%</td><td>20.13%</td><td>4.47%</td><td>1.02%</td><td>0.59%</td><td>0.16%</td><td>0.16%</td><td>0.05%</td><td>0.05%</td></tr><tr><td>0.423</td><td>74.43%</td><td>19.21%</td><td>4.09%</td><td>1.08%</td><td>0.59%</td><td>0.38%</td><td>0.05%</td><td>0.00%</td><td>0.16%</td></tr><tr><td>0.439</td><td>70.51%</td><td>20.83%</td><td>5.76%</td><td>1.72%</td><td>0.65%</td><td>0.27%</td><td>0.11%</td><td>0.05%</td><td>0.11%</td></tr><tr><td>0.466</td><td>65.39%</td><td>22.07%</td><td>7.37%</td><td>2.58%</td><td>1.56%</td><td>0.43%</td><td>0.27%</td><td>0.22%</td><td>0.11%</td></tr><tr><td>0.685</td><td>59.53%</td><td>22.82%</td><td>9.10%</td><td>4.84%</td><td>1.67%</td><td>1.02%</td><td>0.48%</td><td>0.32%</td><td>0.22%</td></tr></table>


Table 1 –Absolute Returns conditional on prior VPIN for E-mini S&P500


Table 1 shows that below average VPIN levels are followed by absolute returns below or equal to 0.25% in about 80% of the cases. As VPIN levels increase, there is a transfer of probability from lower returns to higher returns. For absolute returns greater than 0.25%, the highest concentration of probability occurs in the 5% top range of prior VPIN readings. 

Table 1 provides information about the distribution of absolute returns following a certain toxicity level. It shows VPIN is useful as a predictive measure of absolute returns. An alternative use of VPIN is as a warning measure. Table 2, which shows the distribution of prior VPIN levels conditional on the following absolute returns, provides information about this aspect of the relationship between VPIN and absolute returns. As these are probabilities of VPIN conditional on absolute returns, each column in Table 2 sums to one. 

<table><tr><td></td><td>0.25%</td><td>0.50%</td><td>0.75%</td><td>1.00%</td><td>1.25%</td><td>1.50%</td><td>1.75%</td><td>2.00%</td><td>&gt;2.00%</td></tr><tr><td>0.285</td><td>5.40%</td><td>3.89%</td><td>3.20%</td><td>2.57%</td><td>2.98%</td><td>0.00%</td><td>0.00%</td><td>6.67%</td><td>0.00%</td></tr><tr><td>0.301</td><td>5.33%</td><td>4.23%</td><td>2.98%</td><td>2.57%</td><td>1.19%</td><td>2.53%</td><td>5.71%</td><td>0.00%</td><td>5.26%</td></tr><tr><td>0.312</td><td>5.39%</td><td>4.08%</td><td>2.83%</td><td>2.10%</td><td>0.60%</td><td>0.00%</td><td>5.71%</td><td>0.00%</td><td>0.00%</td></tr><tr><td>0.320</td><td>5.26%</td><td>4.32%</td><td>3.71%</td><td>3.50%</td><td>3.57%</td><td>1.27%</td><td>5.71%</td><td>0.00%</td><td>0.00%</td></tr><tr><td>0.327</td><td>5.26%</td><td>4.59%</td><td>2.83%</td><td>2.34%</td><td>2.38%</td><td>3.80%</td><td>2.86%</td><td>0.00%</td><td>5.26%</td></tr><tr><td>0.334</td><td>5.19%</td><td>4.77%</td><td>3.56%</td><td>2.80%</td><td>1.79%</td><td>3.80%</td><td>0.00%</td><td>0.00%</td><td>0.00%</td></tr><tr><td>0.341</td><td>5.16%</td><td>4.81%</td><td>3.63%</td><td>3.74%</td><td>1.79%</td><td>2.53%</td><td>0.00%</td><td>0.00%</td><td>0.00%</td></tr><tr><td>0.348</td><td>5.10%</td><td>4.85%</td><td>3.78%</td><td>4.21%</td><td>5.95%</td><td>7.59%</td><td>0.00%</td><td>0.00%</td><td>5.26%</td></tr><tr><td>0.354</td><td>5.25%</td><td>4.40%</td><td>3.78%</td><td>3.27%</td><td>1.19%</td><td>2.53%</td><td>0.00%</td><td>0.00%</td><td>5.26%</td></tr><tr><td>0.360</td><td>5.13%</td><td>4.65%</td><td>4.72%</td><td>2.80%</td><td>4.17%</td><td>3.80%</td><td>2.86%</td><td>6.67%</td><td>5.26%</td></tr><tr><td>0.367</td><td>5.17%</td><td>4.56%</td><td>4.29%</td><td>3.50%</td><td>4.17%</td><td>1.27%</td><td>5.71%</td><td>0.00%</td><td>0.00%</td></tr><tr><td>0.374</td><td>5.20%</td><td>4.56%</td><td>4.22%</td><td>3.50%</td><td>1.19%</td><td>2.53%</td><td>0.00%</td><td>0.00%</td><td>0.00%</td></tr><tr><td>0.382</td><td>5.08%</td><td>4.67%</td><td>4.72%</td><td>4.44%</td><td>4.76%</td><td>8.86%</td><td>5.71%</td><td>6.67%</td><td>5.26%</td></tr><tr><td>0.390</td><td>5.06%</td><td>4.85%</td><td>5.09%</td><td>3.97%</td><td>4.76%</td><td>2.53%</td><td>2.86%</td><td>0.00%</td><td>5.26%</td></tr><tr><td>0.399</td><td>4.84%</td><td>5.77%</td><td>5.09%</td><td>5.84%</td><td>3.57%</td><td>3.80%</td><td>5.71%</td><td>0.00%</td><td>0.00%</td></tr><tr><td>0.410</td><td>4.74%</td><td>5.94%</td><td>6.03%</td><td>4.44%</td><td>6.55%</td><td>3.80%</td><td>8.57%</td><td>6.67%</td><td>5.26%</td></tr><tr><td>0.423</td><td>4.81%</td><td>5.67%</td><td>5.52%</td><td>4.67%</td><td>6.55%</td><td>8.86%</td><td>2.86%</td><td>0.00%</td><td>15.79%</td></tr><tr><td>0.439</td><td>4.56%</td><td>6.15%</td><td>7.78%</td><td>7.48%</td><td>7.14%</td><td>6.33%</td><td>5.71%</td><td>6.67%</td><td>10.53%</td></tr><tr><td>0.466</td><td>4.23%</td><td>6.51%</td><td>9.96%</td><td>11.21%</td><td>17.26%</td><td>10.13%</td><td>14.29%</td><td>26.67%</td><td>10.53%</td></tr><tr><td>0.685</td><td>3.85%</td><td>6.74%</td><td>12.28%</td><td>21.03%</td><td>18.45%</td><td>24.05%</td><td>25.71%</td><td>40.00%</td><td>21.05%</td></tr></table>


Table 2 –Prior VPIN conditional on absolute returns for E-mini S&P500


For example, the VPIN metric was greater than 0.41 prior to 80% of all absolute returns between 1.75% and 2%. So although Table 1 tells us that a VPIN greater than 0.41 does not necessarily imply a crash, Table 2 shows that, if the crash occurs, it is likely that the prior VPIN level was elevated. 

These results lead to a dual interpretation for the VPIN metric: 

• At relatively normal levels, it is a measurement of flow toxicity. 

At abnormally high levels, it can also be understood as indicating the likelihood that market makers turn into liquidity consumers, or that position takers may join and reinforce a brewing market imbalance. In markets dominated by high frequency liquidity providers, such as equity futures, this could lead to them destroying the market they were making. 

This second interpretation makes the VPIN metric an interesting measure to use in monitoring the risk of a liquidity crash. Its accuracy is difficult to evaluate as liquidity-induced crashes are so rare that there is no sample on which we can perform a quantitative study. Nevertheless, both anecdotal evidence and the CFTC-SEC Report confirm that some liquidity providers turned into liquidity consumers during the liquidity crash<sup>21</sup>. 

We can also use our model to provide empirical insight into this phenomenon. During periods of unusually high VPIN metric values, we would expect some increase in stocks’ volatility as a result of liquidity providers withdrawing from the marketplace. To check for this effect, we computed the correlation between the VPIN metric and the absolute value of the subsequent price changes. Note that the VPIN metric is not designed to forecast volatility; it is based on volume information rather than price information. We found a positive and statistically significant correlation (0.1596) between the VPIN metric and future volatility of E-mini S&P500, suggesting that an increase in the VPIN metric does foreshadow an increase in volatility in that instrument. 

## 8. Proposed Solution: The ‘VPIN contract’

The ‘flash crash’ might have been avoided, or at least tempered, had liquidity providers remained in the marketplace. Not only did some withdraw, but arguably they became liquidity consumers by dumping their inventories, thus exacerbating the crash. 

One approach to lessen the likelihood and magnitude of future flash crashes may be to offer market makers the tools they need to measure and manage their risk of being adversely selected: 

Measurement: Our measure of flow toxicity, the VPIN metric, could be used by market makers to anticipate a rise in volatility and estimate the risk of a liquidity-induced crash. 

Management: Creating an exchange future with the VPIN metric as underlying would make available a visible reading of flow toxicity and a venue in which liquidity providers could hedge the risk of being adversely selected. 

A ‘VPIN contract’ could work as a hedging and speculation mechanism. It may make it less likely that liquidity providers would turn into liquidity consumers, because as they perceive an inventory growth they can dynamically and continuously hedge their risks, rather than trying to hold their position and possibly being forced to capitulate in a cascade. 

Other potential uses of the VPIN metric are: 

As a benchmark for execution brokers, who could try to fill their customers’ orders while beating the average flow toxicity of the session. Similarly, clients could use the VPIN metric as a tool to indicate under which conditions brokers should stop filling their orders, and to measure how effectively their brokers avoided adverse selection. 

As a warning sign for market regulators, who may decide to slow down or stop market activity as flow toxicity reaches levels comparable to those witnessed on May 6<sup>th</sup> 2010, thus preventing or mitigating the collapse. 

• An instrument for volatility arbitrage, since the VPIN metric is useful in improving forecasts on volatility. 

## 9. Conclusions

The CFTC-SEC Staff Report identifies conjunctural factors as its explanation of the ‘Flash Crash’. While acknowledging such factors may have played a role, our analysis suggests that the ‘Flash Crash’ is better understood as a liquidity event arising from structural features of the new high frequency world of trading. In this high frequency world, liquidity provision is dominated by computerized market makers programmed to place buy and sell orders while avoiding taking significant inventory positions. When order flow toxicity increases, such market makers face significant losses and curtail their risks by reducing, or even liquidating, their positions. The consequent market illiquidity can then have disastrous repercussions for market participants. 

While some have called for banning high frequency trading, we believe a better solution lies in recognizing and managing the risks of trading in this new market structure. The creation of an exchange-traded ‘VPIN contract’ would serve the dual goal of offering market makers an objective measurement of flow toxicity, plus a risk management tool to hedge the risk of being adversely selected, with implications for execution brokers and market regulators. During periods of market stress, dynamic hedging of their VPIN metric exposure might allow high frequency market makers to remain in the marketplace providing liquidity, thus mitigating or possibly avoiding the next ‘flash crash’. 

## BIBLIOGRAPHY



Ané, T. and H. Geman (2000): “Order flow, transaction clock and normality of asset returns”, The Journal of Finance, 55: 2259–2284. 





CFTC-SEC, Preliminary findings Regarding the Market Events of May 6, 2010, May 18, 2010. 





CFTC-SEC, Findings Regarding the Market Events of May 6, 2010, September 30, 2010. 





CME Group, Statement on the Joint CFTC/SEC Report Regarding the Events of May 6, October 1, 2010. 





Easley, D. and M. O’Hara (1987): "Price, Trade Size, and Information in Securities Markets", Journal of Financial Economics, 19. 





Easley, D. and M. O’Hara (1992): “Time and the process of security price adjustment”, Journal of Finance, 47, 576-605. 





Easley, D., Kiefer, N., O’Hara, M. and J. Paperman (1996): "Liquidity, Information, and Infrequently Traded Stocks", Journal of Finance, September. 





Easley, D., R. F. Engle, M. O’Hara and L. Wu (2008): “Time-Varying Arrival Rates of Informed and Uninformed Traders”, Journal of Financial Econometrics. 





Easley, D., M. López de Prado and M. O’Hara (2010): “Measuring flow toxicity in a high frequency world”, SSRN, Working Paper Series, http://papers.ssrn.com/abstract=1695596. 





Glosten, L. R. and P. Milgrom (1985): “Bid, ask and transaction prices in a specialist market with heterogeneously informed traders”, Journal of Financial Economics, 14, 71-100. 





• Iati, Robert (2009): “High Frequency Trading Technology”, TABB Group. 





Kirilenko, A., A. Kyle, M. Samadi and T. Tuzun (2010): “ The Flash Crash: The Impact of High Frequency Trading on an Electronic Market”, Working paper. 





O’Hara, M. and G. Oldfield (1986): "The Microeconomics of Market Making", Journal of Financial and Quantitative Analysis, December. 



## DISCLAIMER

The views expressed in this paper are those of the authors and not necessarily reflect those of Tudor Investment Corporation. No investment decision or particular course of action is recommended by this paper. 