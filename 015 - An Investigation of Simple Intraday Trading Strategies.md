The proof of the pudding is in the eating. (British Proverb). 

## Abstract:

This working paper investigates the performance of several published simple intraday trading strategies for S&P-500 futures. The general result is: The strategies do not work as advertised under realistic trading assumptions. The paper discusses some possible refinements. It is important to restrict the rules to specific market regimes. An appropriate regime-classifier is the Implied-Volatility-Term-Structure (IVTS) developed in previous working papers. The best strategy under investigation is a set of rules proposed by the Sibyl-Fund trader Siddharth Bhatia. But overall it seems to be difficult to develop a simple and attractive intraday strategy. 

## Open Range Breakout:

In [1] Holmberg et. al. investigate the Open Range Breakout (ORB) strategy. 

This rule is based on the premise that if the market moves a certain percentage from the opening price level, the odds favor a continuation of that move. An ORB filter suggests that, long (short) positions are established at some predetermined price threshold a certain percentage above (below) the opening price. (Holmberg et. al., Introduction). 

The authors test this very simple intraday strategy with daily data. This is an interesting challenge for itself. They derive their promising results by continuity arguments. If we have a daily high/low, the price must pass somewhere to a level in between. This must of course not be true. Additionally one does not know the order of the high and low. The authors claim that their results holds also after taking realistic trading costs into account. But they don't specify them. 

As can be seen in Graphic-1 the results look on the first glance indeed quite promising. One buys ES Emini futures once the price is 0.15% above the opening price at 9:30. This must happen before 15:30. One does not open a position in the last half hour. The Stop-Loss is 1.8%. But there is also a Stop-Win. One closes the position once it has gained 0.8%. Otherwise the position is closed at 16:00. ES futures trade till 16:15, but the result is slightly improved if one sells the position already back at the regular market close. The index is initially at 500.000$. This number is a convention used in previous working papers. One trades 1 E-mini future for each 30.000$ of the index. So initially one goes 16 E-minis long. The results are for the last 4 years from 2010-08-24 till 2014-08-24. The calculation uses 1-minute HFdata at the latest trade price at the end of the 1-minute time interval. The data are provided by IQFeed. The position is only entered long. Trading the short side does not work at all. The S&P-500 has gone up considerable in the last 4 years. The short position has too much headwind. 

There is an additional important refinement: One uses the implied volatility term structure (IVTS) as a filter. The IVTS was developed and applied with good success in several previous working papers (see [2] and the references herein). The IVTS is defined as the quotient of the 1-month VIX to the 3-month VXV implied volatility index. 

$$
\mathrm{IVTS} (t) = \mathrm{VIX} (t) / \mathrm{VXV} (t) \tag {1}
$$

In Graphic-1 the IVTS must be <= 1.0. An IVTS larger than 1.0 indicates a market turmoil. 

<table><tr><td>Symbol</td><td>Threshold</td><td>StL</td><td>StWin</td><td>Open-Time</td><td>Start-Time</td><td>Min-IVTS</td><td>Max-IVTS</td><td>Index-Unit</td><td>Trade-Cost</td><td>From</td></tr><tr><td>@ES</td><td>0.15</td><td>1.8</td><td>0.8</td><td>9:30</td><td>9:30</td><td>0.0</td><td>1.0</td><td>30000.0</td><td>0.0</td><td>2010-8-24</td></tr></table>

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/a941dfce-21ae-4580-9395-efb85bc843db/4332e534eefdee73c71c54bf41b616bba4849e283b15e34a8c01b08964c9dc59.jpg)



Graphic-1: ORB-Strategy (orange) TC 0.0$ and SPY (yellow) 2010-08-24 till 2014-08-24


<table><tr><td>Symbol</td><td>Threshold</td><td>StL</td><td>StWin</td><td>Open-Time</td><td>Start-Time</td><td>Min-IVTS</td><td>Max-IVTS</td><td>Index-Unit</td><td>Trade-Cost</td><td>From</td><td>Draw</td></tr><tr><td>@ES</td><td>0.15</td><td>1.8</td><td>0.8</td><td>9-30</td><td>9-30</td><td>0.0</td><td>1.0</td><td>30000.0</td><td>12.5</td><td>2010-8-24</td><td></td></tr></table>

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/a941dfce-21ae-4580-9395-efb85bc843db/e0a90d5930065eafae3eb03d79a353ee843ad43401b28606003e7bbdb88b06aa.jpg)



Graphic-2: ORB-Strategy (orange) TC 12.5$ and SPY (yellow) 2010-08-24 till 2014-08-24


Assuming no trading costs is of course not realistic. Graphic-2 is the same strategy. But this time there are 12.5$ costs per trade and future. A round-trip is hence 25$. 12.5$ is the money-value of one tick for ES E-mini futures. One assumes that one looses at each trade the bid/ask spread. There are additional broker-fees. But as the first assumption is relative pessimistic, these fees are ignored. The simple ORB strategy looses under realistic assumptions its attractiveness. Without trading costs one makes an overall win of 139.8% to 105.2% of a buy&hold strategy of the SPY. The Sharpe-Ratio is 1.012 for ORB to 1.025 for the SPY. With round-trip costs of 25$ the profit drops to 35.4% and the Sharpe-Ratio to 0.469. One could triple the leverage and buy 1 E-mini for each 10.000$ of the index. This increases the overall profit to 82.8% and reduces the Sharpe-Ratio further to 0.321. 

Note: A 3x leverage does not triple the final profit. One gets a volatility-drag but also a compound effect. The volatility drag is a well know problem of leveraged ETFs. It can be exploited with the Johnny-Walker strategy by going both the leveraged and the inverse leverage ETF short (see [3]). 

According to Holmberg one should hence reduce trading activity to market periods with higher volatility. The best result is shown in Graphic-3. The IVTS must be in the range [0.93,1.0]. This corresponds to a medium excited market like in July 2014. A value above 1.0 indicates a market-crash. One can avoid a lot of trouble if one stays in times of trouble on the sideline. Additionally the bid-ask spread increases. The long position definitely suffers in a crash-scenario. But also the results for the short side were not compelling. 

The overall win is 43.5% with a Sharpe-Ratio of 0.812. The win is low, because because one is most of the time on the sideline. But with 1 E-mini per 10.000$ one gets 171.3% and a Sharpe-Ratio of 0.764. The compound effect is in this case larger than the volatility drag. One avoids the quiet market regime were the trading costs eat up the small gains. It should be noted that Holmberg reports nice profits for 0.5, 1.0, 1.5 and 2.0% ORB thresholds. I got no reasonable results for these values. One waits too long till one enters the trade. There are only very few days where the S&P-500 open to close returns are above 2.0. But even in these rare days one misses the win by waiting for the entry-signal. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/a941dfce-21ae-4580-9395-efb85bc843db/7e70fe93aba10e24a7b0823eb39c21599be379f3376386d226948c5fb24e166d.jpg)



Graphic-3: ORB-Strategy (orange) TC 12.5$ IVTS in [0.93,1.0] and SPY (yellow) 2010-08-24 till 2014-08-24


## Gap-Trading:

The most basic definition of a gap is that the overnight return exceeds – in absolute terms – a given threshold ([4],[5]). Sometimes an additional criterion for a gap is that the opening price is below/above the previous day low/high. But both the trader-oriented book [4] and the academic paper [5] stick to the plain threshold definition. For ES E-mini futures this is the return from 16:15 of the previous day till 9:30. E-minis rock – besides a short break at 16:15 – around the clock. But volume is overnight relative low. Some of the stylized facts can probably be explained by electronic trading. If bad news arrive after market close at 16:00 short E-minis are the easiest way to hedge a market position against the expected drop next morning. There is probably an overshot reaction. Grant et. al. show in [5] that the S&P keeps the overnight direction for about 15 minutes after the opening and turns then around. Their data are from 1987 till 2002. As can be seen in Graphic-4 the pattern is still valid. The graphic shows the distribution at 9:35 (orange), 9:40 (yellow), 9:45 (green) and 9:50 (blue) of the returns since the opening. The overnight return is in the range of -1.0 till -0.2%. The data are from the last 4 years (2010-08-25 till 2014-08-24). The mode, mean and median are negative, but move to the right. The turnaround time has shortened to about 5 minutes. This short term momentum effect works in both directions. One gets a rather save strategy by going on 9:30 long/short if the gap is above/below +/- 0.5% and sells back at 9:35. Unfortunately life is for a plain trader not so easy. The win is more than eaten up by the trading costs. But it should be possible for HFT traders to cash in this effect. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/a941dfce-21ae-4580-9395-efb85bc843db/b95334aa8e083914834855711317232868ab6fe110e38dc9695ef5aaa8e769db.jpg)



Graphic-4: Distributions of Returns for a negative Gap in 5-Minutes Intervals after the Opening


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/a941dfce-21ae-4580-9395-efb85bc843db/81f324e3ce11843dfbdb302ef37c873aa5fe9f355d91c3d380ceb4fcbc00c4c9.jpg)



Graphic-5: Simple-Gap-Strategy (orange) TC 12.5$ and SPY (yellow) 2010-08-24 till 2014-08-24


Graphic-5 shows the result of a simple “Gap-Fade-In” strategy as described in [4]. This is a typical trader book. The strategy is specified by (impressive) examples. It is hence my interpretation what is done. But it is also alongside the more precise description in [5]. One goes a position long, if the overnight gap is below -0.2%. The gap is measured at the end of the overnight momentum effect (9:35). The position is opened at this time. In [4] the position is closed once the value has reached the previous close. This is the “fade-in” aspect of the strategy. This rule works reasonable without trading costs. But with the 12.5$ trading costs I got considerable better results if one closes the position once a profit of 1.0% is reached. The Stop-Loss is 0.8%. There is one refinement to the Stop-Loss. If the price goes up, the Stop-Loss is moved up accordingly. The Stop-Loss is always calculated relative too the highest price of the position. This modification is done for all considered strategies. As an additional filter the IVTS must be <= 0.94. This is a relative quiet market regime. Andrews uses in [4] a classification of gaps. The idea is similar, but there is no precise definition. The overall win of this strategy is 36.9% with a Sharpe-Ratio of 0.861. Without trading costs the Sharpe-Ratio is 1.032 (to 1.025 of the SPY) and the win is 57.1%. If one triples the leverage (1 E-mini per 10.000$) the zero cost performance increases to impressive 266.5% with a Sharpe-Ratio of 1.006. The final win is for 12.5$ trading costs 146.2% with a Sharpe-Ratio of 0.832. The strategy is relative robust to leverage. The strong gap definition that the opening must be below yesterdays low does not improve the strategy. The strategy works within the considered time frame only for long positions (negative gaps). There are minor profits for a short position in very turbulent market regimes (IVTS>=1.0). But it is not worth the risk. 

The Sibyl-Fund trader Siddharth Bhatia has proposed the following refinement. 

Note: Actually Sid's proposal was the starting point of these investigations. The rule is based on traderfolklore. 

One waits after the open for 1 hour and determines the high in this time-period. After this initial time one enters the position once the initial high is confirmed. One gets somewhat better results if one restricts the initial period to half an hour (from 9:35 to 10:05). The gap is set to -0.3. The Stop-Loss is 0.7%. If there is no Stop-Loss one lets the position run till 16:00. The additional filter reduces the number of tradings and hence also the final win. But one gets a very high probability for winning trades. There is no reason to close the position premature. The final win is 30.7% with a nice Sharpe-Ratio of 1.047. Due to the smooth performance (it looks almost like Bernie Madoff's ruler like charts) the Sharpe-Ratio is for the 3x leverage with 1.042 almost the same. The final win of the 3x leverage beats with 121.8% the SPY. But the filters are relative strong. There are periods where one can't trade this strategy at all. One could argue, that the performance is the result of over-fitting. But the principal rules were set up beforehand and the strategy is consistent with trader-intuition. 

<table><tr><td>Symbol</td><td>Gap</td><td>HL-Gap</td><td>StL</td><td>StWin</td><td>Open-Time</td><td>End-Time</td><td>Min-IVTS</td><td>Max-IVTS</td><td>Index-Unit</td><td>Trade-Cost</td><td>From</td><td>Draw</td></tr><tr><td>@ES</td><td>-0.3</td><td>× Off</td><td>0.7</td><td>10.0</td><td>9-35</td><td>10-05</td><td>0.0</td><td>0.94</td><td>30000.0</td><td>12.5</td><td>2010-8-24</td><td></td></tr></table>

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/a941dfce-21ae-4580-9395-efb85bc843db/1a1a0d0c5c1a89d0f316c25b61c45a49610f45b96e007fd440789e7943a6de4f.jpg)



Graphic-6: Sid-Gap-Strategy (orange) TC 12.5$ and SPY (yellow) 2010-08-24 till 2014-08-24


<table><tr><td>Symbol@ES#</td><td>Compare@ES#</td><td>From2014-8-15</td><td>To2014-8-15</td><td>Delta-T5min</td><td>Vola-Len93</td><td>Volatility× Off</td><td>Beta× Off</td><td>Draw</td></tr></table>

## Rebound-Trading:

On 2014-08-15 the S&P-500 suddenly nosedived after a strong opening (Graphic-7). Chrilly mailed to Sid: 

Hi Sid, 

S&P is suddenly nosediving. Something special happened in the world? 

His answer was. 

Ukraine and Russia who else, some stuff about envoys being attacked... 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/a941dfce-21ae-4580-9395-efb85bc843db/9d9e3afa6117a64a227b7f9e7fea16e805fd1fd5fc2affbc5aa310042ff44282.jpg)



Graphic-7: ES-Futures on 2014-08-15


The incident was probably a hoax and the S&P recovered. Such overreactions are a relative general pattern. Zawadowski et. al. are analyzing this effect in [6] for liquid stocks. But it is not easy to exploit the overreaction. As can be seen in Graphic-7 the S&P is not falling straight down. There are 2 larger counter moves in between. When is the bottom reached? Zawadowski proposes a window of 1 hour. If the price has fallen within this hour a certain amount a position is entered. In Graphic-7 it takes 1:20 till the bottom is reached. One would enter the position around the second peak of the counter move. The following steep decline would probably trigger a stop-loss. I got in general for the ES no reasonable results with the Zawadoski-rule. But the authors claim that it works for liquid stocks. I have tested it for Apple and Google. It did not work neither. As the topic of this work was the behavior of the S&P I did not investigate this question further. I believe that the idea is not very promising. 

Instead I tried a variant of the Sid-Strategy. One determines in the first half hour – from 9:35 to 10:05 – a high. The following low must be at least -0.75% down. One enters a position, if the current value is 0.4% above the low. The Stop-Loss is 0.75% and the IVTS is between 0.95 and 1.00. The market-regime is in a transitional state. The strategy makes nice profits in the recovery of the August 2011 crash. But there are otherwise only a few occasions where the conditions are met. The final win is 27.1% with a Sharpe-Ratio of 0.863. With 3x leverage it is 100.8% and a Sharpe-Ratio of 0.856. The leveraged version earns in the short time-period in autumn 2011 the same amount than the SPY over the whole range. The Sharpe-Ratio is somewhat misleading. There is only a minor downside movement. But the ratio is symmetric. The steep increase within a short time is also punished. This strategy is not for everyday trading. But it could be an interesting twist in a transitional market regime. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/a941dfce-21ae-4580-9395-efb85bc843db/315b62f903243bd3db53a52fc0bb4bc2a0b3578586a30e1eb1d0502aefa6dfb4.jpg)



Graphic-8: Rebound Strategy (orange) and SPY (yellow) 2010-08-24 till 2014-08-24


## Up- and Downside Volatility:

Kudryavtsev defines in [7] the Up- and Downside Volatility as: 

$$
\begin{array}{l} \text {Vup} = 2. 0 * (\text {Ph} - \text {Po}) * (\text {Ph - Pc}) \\ \text {Vdown} = 2. 0 * (\text {Po} - \text {Pl}) * (\text {Pc - Pl}) \end{array}\tag{2}
$$

(3) 

Ph is the daily log high-, Pl the log low-, Po the log open-, Pc the log close-price. Becker et. al. use in [8] the same measures. They call (2) Vt,max and (3) Vt,min. 

Note: Kudryavtsev has written a series of papers with the same idea. The Mendeley document database noticed some of them as close copies. The cited one is a random draw. 

Both papers claim that the measure predicts the following overnight return. I have tested this for the S&P and could not find significant results. Both authors apply the idea to the Dow-Jones stocks. I have tested this too. There is weak evidence for some of them. But it does not work for others. Besides the fact that overnight trading was not the topic of this research I don't consider the idea very promising. It is very likely that a simple strategy which enters an overnight E-mini position if the IVTS is at the close below a given threshold (e.g. 0.94) is much more profitable. At least it is claimed in [9] that the ES makes most of its profits overnight. 

I have tested if the Vdown measure can also be applied intraday. One replaces in (3) the close price with the current price. If the downside volatility is above a given threshold one enters the position. The idea is similar to the rebound strategy. Only the measure differs somewhat. Graphic-9 shows the result for a threshold of 0.7 (the measure is scaled by 10000.0 to get the usual percentage unit). The other parameters are the same than for the rebound strategy in Graphic-8. The performance pattern is similar. The final win is 30.1% with a Sharpe-Ratio of 0.786. With 3x leverage it is 133.5% with a Sharpe-Ratio of 0.776. The criterion is weaker. There are hence more trades. But also the risk is slightly higher. The strategy has difficulties at the end of the August-2011 recovery phase. The rebound-strategy does not trade anymore in these days. Trading a short position with the Vup measure is not profitable. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/a941dfce-21ae-4580-9395-efb85bc843db/c27c956bae113da71b786681ab0c8724be859551325307dc0df96ed5b4cce535.jpg)



Graphic-9: Downside Volatility Strategy (orange) and SPY (yellow) 2010-08-24 till 2014-08-24


## Conclusion:

The results claimed in the literature are generally exaggerated and/or assume unrealistic low trading costs. Markets are probably not efficient (whatever this is), but the market participants are definitely not stupid. It would be strange if one could beat the market with rather simple and well known rules. 

The concept of the Implied Volatility Term Structure (IVTS) is also for intraday trading an informative measure to classify market regimes. The IVTS is probably superior to other technical indicators used in the literature (see [10]). It seems to be possible to identify interesting strategies if one restricts trading to specific regimes. But there is also the danger of over-fitting aka datasnooping. The IVTS was smoothed in previous working papers with a median-5 filter to avoid whipsaws. For intraday trading one should use the unfiltered value. The whipsaws are no problem, because one closes the position anyway on the same day. 

The Sid-Gap-Trading rule seems to be a relative safe bet. But it can only be applied in special circumstances. It is nevertheless an interesting addition to the Sibyl-Fund toolbox. The same holds for the rebound rule. 

## Further Work:

There are several extensions of this work possible. One direction is to study liquid stocks or portfolios of them. One could stick to the E-mini futures but could investigate the overnight behavior. Such an investigation could also use global market linkages (see [11]). 

Another interesting topic are short term (not necessarily intraday) movements around earning announcements (see [12]). 

## References:



[1] Holmberg, U., Lönnbark, C., Lundström, Ch.: Assessing the profitability of intraday opening range breakout strategy. 





[2] Donninger, Ch.: How to beat the market with the Implied Volatility Term Structure: The HeroRATs Strategy. Sibyl-Working-Paper, Dec. 2013 





[3] Donninger, Ch.: Leveraged ETF-Trading: The Johnny Walker-Strategy, Sibyl-Working-Paper, Revision-1: 2012.07.29 





[4] Andrews, S.: Understanding Gaps. Traders Press. 





[5] Grant, J., Wolf, A., Yu, S.: Intraday price reversals in the US stock index futures market: A 15-year study. 





[6] Zawadowski, A., Andor, G., Kertesz, J.: Short-term market reaction after extreme price changes of liquid stocks. 





[7] Kudryavtsev, A.: Overnight Stock Price Reversals. 





[8] Becker, M., Friedmann, R., Klößner, St.: On the measurement of intraday overreaction of stock prices. 





[9] Cliff, M., Cooper, M., Gulen, H.: Return Differences between Trading and Non-trading Hours: Like Night and Day. 





[10] Neely, Ch., Rapach, D., Tu, J., Zhou, G.: Forecasting the Equity Risk Premium: The Role of Technical Indicators. 





[11] An, B.: International Stock Market Linkages: Are Overnight Returns on the U.S. Market Informative? 





[12] Berkman, H., McKenzie M.: Earning Announcements: Good News for Institutional Investors and Short Sellers. 

