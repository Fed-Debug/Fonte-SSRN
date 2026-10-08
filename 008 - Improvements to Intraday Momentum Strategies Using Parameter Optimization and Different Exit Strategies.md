# Improvements to Intraday Momentum Strategies

# Using Parameter Optimization and Different Exit Strategies

Ákos Maróy akos@maroy.hu 

January 12, 2025 

## Abstract

Building on the results of Zarattini, C., Aziz, A., & Barbon, A. (2024). Beat the market: An efective intraday momentum strategy for S&P500 ETF (SPY), we explore improvements to noise boundary based intraday momentum strategies by investigating diferent exit strategies and applying parameter optimization to all parameters of the strategies. We show that the returns of the momentum strategy can be significantly improved by such an approach. The best results are achieved with exits based on VWAP, VWAP & Ladder and Ladder exit strategies, with Sharpe ratios over 3.0 and annualized returns of over 50%, which are significant improvements against the baseline strategy. 

Keywords Day Trading, Day Trading Systems, Algo Trading, Momentum, Trend-Following, Intraday Momentum, Delta-Hedging 

## 1 Introduction

This paper builds on the work of Zarattini et al. <sup>1</sup>, which introduced an intraday momentum strategy using a ’noise area’ concept to determine if the intraday movement of an asset is beyond the normal daily movements. One can interpret this concept so that if the intra-day movement is within the ’noise area’, then it is ’just noise’ and not a significant movement, and the strategy should not take a position, while if the movement is outside the ’noise area’, then it is a significant movement, and the strategy should take a position. The strategy outlined in Zarattini et al. <sup>1</sup> explores multiple entry parameters and exit strategies as well as position sizing parameters. 

This paper aims to improve on the results of Zarattini et al. <sup>1</sup> by exploring additional position exit strategies as well as fine-tuning strategy parameters by the use of a hyperparameter optimization approach. 

## 2 Data & Framework

To establish a baseline, results from Zarattini et al. <sup>1</sup> based on the Python code provided in the paper are reproduced using a somewhat diferent data set and framework, also in Python. The most notable diferences are: 

• VectorBT Pro<sup>[2]</sup> is used as the backtesting framework 

• 10 years of data is used instead of 17 years of data, between 1st October 2014 and 1st October 2024 

• 1 second trade bar data resolution is used instead of 1 minute trade bar data resolution 

• To generate entry or exit exit, instead of the close value of each trade bar, the most relevant part of the trade bars is used, e.g. high if the trade is a long entry or short exit, low if the trade is a short entry or long exit 

• Trade sizing is done using the then-current price instead of the day open price • A more detailed cost structure is used instead of a $0.0035 cost per share to reflect the nuances of Interactive Brokers <sup>3</sup> stock commissions 

• To reflect realistic margin requirements by popular trading platforms, instead of a 4x leverage for both long and short positions, a margin requirement of 25% for long and 30% for short positions is used with efective leverages of 4x and 3.33x, respectively. 

• Trades are exited 15 minutes before market close, not at market close. This is to reflect policies by popular trading platforms that start to apply overnight margin requirements 10 minutes before market close, which are lower than intra-day margin requirements. 

• Dividend adjustments are not applied 

In addition to the above, the Target Volatility $\sigma _ { \mathrm { t a r g e t } }$ parameter is treated diferently. In Zarattini et al. <sup>1</sup> this parameter is used assuming a 4x max leverage value and is used together with the max leverage multiplier, in efect bounding the leverage to be used. In this paper, the Target Volatility $\sigma _ { \mathrm { t a r g e t } }$ parameter is used to calculate the position size as a percentage of maximum leverage value. The reason for this change is that we’re using diferent margin requirements for long and short positions, in efect having diferent leverages in the two directions. 

The formula to calculate the number of shares with dynamic position sizing in Zarattini et al. <sup>1</sup> is as follows: 

$$
\operatorname{Shares} _ {t} = \left\lfloor \frac {\mathrm{AUM} _ {t - 1} \times \min \left(4 , \sigma_ {\text {target,aum}} / \sigma_ {\text {Symbol} , t}\right)}{\operatorname{Open} _ {t , 9 : 3 0}} \right\rfloor ,\tag{1}
$$

$\mathrm { A U M } _ { t - 1 } \ .$ - Asset Under Management at the end of the previous day 

• 4 - max leverage 

$\sigma _ { \mathrm { t a r g e t , a u m } }$ - Target Volatility 

• σ - 14-day historical volatility of the traded symbol 

$\mathrm { O p e n } _ { t , 9 : 3 0 }$ - opening price of the asset at 9:30. 

With the historical volatility over 14 days of the traded symbol being calculated as follows: 

$$
\sigma_ {\text {Symbol}, t} = \sqrt {\frac {1}{1 4} \sum_ {i = 1} ^ {1 4} \left(\operatorname{ret} _ {t - i} - \mu_ {\text {SPY} , t}\right) ^ {2}} \quad \text {and} \quad \mu_ {\text {SPY}, t} = \frac {1}{1 4} \sum_ {i = 1} ^ {1 4} \operatorname{ret} _ {t - i}.\tag{2}
$$

Whereas for our purposes we’ll be using the following formula: 

$$
\mathrm{Shares} _ {t} = \left\lfloor \frac {\mathrm{MA} _ {t} \times \min \left(1 , \sigma_ {\mathrm{target}} / \sigma_ {\mathrm{Symbol} , t}\right)}{\mathrm{Price} _ {t}} \right\rfloor ,\tag{3}
$$

• MA - Margin Available at the time of entering the trade 

$\sigma _ { \mathrm { t a r g e t } }$ - Target Volatility 

• σ - historical volatility of the traded symbol for the lookback period used to calculate the noise area 

$\mathrm { P r i c e } _ { t } \mathrm { ~ - ~ } \mathrm { T }$ he price of the asset at the time of entering the trade 

With ldays denoting the historical volatility being over the number of days used for the lookback period of the noise area calculation: 

$$
\sigma_ {\text {Symbol}, t} = \sqrt {\frac {1}{l d a y s} \sum_ {i = 1} ^ {l d a y s} \left(\operatorname{ret} _ {t - i} - \mu_ {\text {SPY} , t}\right) ^ {2}} \quad \text {and} \quad \mu_ {\text {SPY} , t} = \frac {1}{l d a y s} \sum_ {i = 1} ^ {l d a y s} \operatorname{ret} _ {t - i}.\tag{4}
$$

The relationship between Asset Under Management and Margin Available being: 

$$
\mathrm{MA} _ {l o n g, t} = \mathrm{AUM} _ {t} / 25 \% \quad \text {and} \quad \mathrm{MA} _ {s h o r t, t} = \mathrm{AUM} _ {t} / 30 \%\tag{5}
$$

## 3 Baseline


The most promising strategy in Zarattini et al. <sup>1</sup> was to use the ’Current Band’ and the VWAP as a stop loss, and dynamic sizing with a target volatility σ<sub>target,aum</sub> of 2%, which is roughly equivalent of a $\sigma _ { \mathrm { t a r g e t } }$ value of 0.5% in our reproduction. We’re calculating statistics on a per day basis, not on a per trade basis.


<table><tr><td rowspan="2">Symbol</td><td rowspan="2">Look-back days</td><td rowspan="2">Target Vol <eq>σ_{target}</eq></td><td rowspan="2">Vol Mult<eq>^a</eq></td><td colspan="5">Replicated results</td><td colspan="5">Reference results</td></tr><tr><td>Sharpe</td><td>Alpha</td><td>Beta</td><td>Ann Ret<eq>^b</eq></td><td>Ann Vol<eq>^c</eq></td><td>Sharpe</td><td>Alpha</td><td>Beta</td><td>Ann Ret<eq>^b</eq></td><td>Ann Vol<eq>^c</eq></td></tr><tr><td>SPY</td><td>14</td><td><eq>0.5\%^d</eq></td><td>1.0</td><td>0.98</td><td>6%</td><td>-2%</td><td>8%</td><td>8%</td><td>1.33</td><td>20%</td><td>-7%</td><td>20%</td><td><eq>14\%^e</eq></td></tr><tr><td>SPY</td><td>14</td><td><eq>0.5\%^d</eq></td><td>1.3</td><td>0.81</td><td>4%</td><td>1%</td><td>6%</td><td>7%</td><td>1.50</td><td></td><td></td><td>20%</td><td><eq>f</eq></td></tr><tr><td>SPY</td><td>90</td><td><eq>0.5\%^d</eq></td><td>1.0</td><td>0.68</td><td>4%</td><td>-1%</td><td>6%</td><td>8%</td><td>1.50</td><td></td><td></td><td>22%</td><td><eq>14\%^g</eq></td></tr><tr><td>SPY</td><td>90</td><td><eq>0.5\%^d</eq></td><td>1.3</td><td>0.60</td><td>0%</td><td>0%</td><td>4%</td><td>7%</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>QQQ</td><td>14</td><td><eq>0.5\%^d</eq></td><td>1.0</td><td>1.11</td><td>7%</td><td>-1%</td><td>10%</td><td>9%</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>QQQ</td><td>14</td><td><eq>0.5\%^d</eq></td><td>1.3</td><td>0.99</td><td>6%</td><td>-2%</td><td>8%</td><td>8%</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>QQQ</td><td>90</td><td><eq>0.5\%^d</eq></td><td>1.0</td><td>1.28</td><td>8%</td><td>-1%</td><td>11%</td><td>8%</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>QQQ</td><td>90</td><td><eq>0.5\%^d</eq></td><td>1.3</td><td>1.22</td><td>7%</td><td>-1%</td><td>9%</td><td>7%</td><td></td><td></td><td></td><td></td><td></td></tr></table>


<sup>a</sup> Volatility Multiplier 



<sup>b</sup> Annualized Return 



<sup>c</sup> Annualized Volatility 



d $\sigma _ { \mathrm { t a r g e t } }$ of 0.5% is roughly equivalent to $\sigma _ { \mathrm { t a r g e t , a u m } } = 2 \%$ in Zarattini et al. <sup>1</sup> 



<sup>e</sup> See ’Curr.Band + VWAP’ stop loss and dynamic sizing in Zarattini et al. <sup>1</sup>, Table 3 



<sup>f</sup> See Zarattini et al. <sup>1</sup>, Figure 9 



<sup>g</sup> See Zarattini et al. <sup>1</sup>, Q6 



Table 1: Replicating the results of Zarattini et al. <sup>1</sup>. All strategies have a ’Curr.Band + VWAP’ stop loss and dynamic sizing with a target volatility $\sigma _ { \mathrm { t a r g e t } }$ of 0.5% 


The diferences between our reproduction and the results of Zarattini et al. <sup>1</sup> are attributed to the diferent approach and data set noted above. 

As QQQ seems to provide better results, our further investigation will focus on this symbol. 

## 4 Exit strategies

The ideal stock movement pattern for a momentum strategy is a quick and strong movement in the direction of the trade throughout the day, as shown in the example in Figure 1. In this case, the strategy should hold the position until the end of the day to maximize the profit. 

Unfortunately, not all movement is ideal. Figure 2 shows a daily movement with multiple reversals. Using the noise boundary and VWAP as stop loss points, the position is stopped out twice during the day, resulting in losses. If the algorithm kept the position until the end of the day, the profit would have been higher. 

We’ll explore diferent exit strategies to improve the performance of the momentum strategy. In call cases, entering the position is done in the same manner, when the asset price moves outside the noise boundary and only at specified intervals, e.g. every 30 minutes. The exit strategies will aim to allow the price movement to move somewhat lower without stopping out. This approach can work better if the price only dips a bit lower before continuing the upward movement, at the cost of a bigger loss if the downtrend continues. 

## 4.1 Time based exit only

A time based exit strategy would exit the position at a fixed time, e.g. 15 minutes before market close. This strategy is proposed in Zarattini et al. <sup>1</sup> as a baseline strategy and was found to be not performing well. We’re showing this as a reference. See Figure 3a. All our strategies will include a time based exit. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/4380e4a9b090f21ae806b46bc53c52038bafe0b2fc557ea49f0ada6de0bf98e0.jpg)



Figure 1: Ideal daily momentum asset movement pattern



QQQ on $8 ^ { \mathrm { t h } }$ January 2024, lookback period of 14 days, volatility multiplier 1.0. The noise boundary is depicted in grey and as a darker area, VWAP drawn is blue.


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/409f4cac3a96ffd29e2c22536e09bb1a27398a70492f58e07c973d210fad03e2.jpg)



Figure 2: Daily momentum movement with reversals



QQQ on $2 ^ { \mathrm { n d } }$ July 2024, lookback period of 14 days, volatility multiplier 1.0, stops at the noise boundary and WVAP. The position is stopped out twice during the day, resulting in losses.


## 4.2 Exit on hitting VWAP + time

The position is exited when the asset price hits the VWAP or at a fixed time, whichever comes first, see Figure 3b. 

## 4.3 Diferent entry & exit boundaries + VWAP + time

The position is exited when the asset price hits the VWAP, an exit noise boundary or at a fixed time, whichever comes first. This difers from the ’Curr.Band + WVAP’ stop loss strategy in Zarattini et al. <sup>1</sup> in that the exit noise boundary can be narrower compared to the entry noise boundary. This strategy is shown in Figure 3c. 

## 4.4 Diferent entry & exit boundaries + time

The position is exited when the asset price hits an exit noise boundary or at a fixed time, whichever comes first. It’s the same as the previous strategy, but without the VWAP exit. This strategy is shown in Figure 3d. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/19e33b5ed58a71868740b82fd5d3c65f15b8e8a0f9c4f65cffb1043a34f5da63.jpg)



(a) Time based exit only


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/0d1979b836d8fd8d931edea83f46639956cfa9a6ef8530c5c7699021307fcd9e.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/8c7e8efb2dff4f08126722f2b2236ee2a59b937c6cdf1669ce17a361dd7dbe45.jpg)



(c) Diferent entry & exit boundaries + VWAP + time



(b) Exit on hitting VWAP + time


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/bdc43214ec9853257155f0ae895d3a59696e139b71d1e7ab8c5513f791108e11.jpg)



(d) Diferent entry & exit boundaries + time



Figure 3: Comparison of diferent exit strategies


Diferent exit strategies shown for QQQ on 2<sup>nd</sup> July 2024. VWAP is drawn in blue, the entry noise boundary is depicted in grey and as a darker area, while the exit noise boundary is drawn in red. 

## 4.5 Ladder stop loss & take profit

A ladder stop loss & take profit strategy is based on defining a series of stop loss and take profit levels, of which only one pair of stop loss and take profit is active at any given time. When the stop loss is hit, the position is exited. When a take profit is hit, a partial exit is made, and the stop loss and take profit levels are moved to the next levels for the next ’step’. 


In this paper, we’ll be looking at simple, 2-level ladder stop loss & take profit strategies, with a 50% partial exit on hitting the take profit at each level. Each stop is defined as a multiple of some risk parameter r, and is interpreted relative to the entry price.


<table><tr><td></td><td>Stop Loss</td><td>Take Profit</td></tr><tr><td>Step 0</td><td>-1 × r</td><td>2 × r</td></tr><tr><td>Step 1</td><td>0 × r</td><td>5 × r</td></tr></table>


Table 2: An example 2-step ladder


<table><tr><td></td><td>Stop Loss</td><td>Take Profit</td></tr><tr><td>Step 0</td><td>$100 - 1 × $10 = $90</td><td>$100 + 2 × $10 = $120</td></tr><tr><td>Step 1</td><td>$100 + 0 × $10 = $100</td><td>$100 + 5 × $10 = $150</td></tr></table>


Table 3: Sample ladder with entry price $100 and $r = \mathfrak { F } 1 0 \ /$ share


The strategy is always combined with the time-based exit some minutes before the trading day ends and can be combined with other exit strategies listed above. Various scenarios for this strategy are shown in Figure 4. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/66f58eac759281ac3b1b5c93f0d8cbc402def2b6391ccf3c4c295b24c73e5a61.jpg)



(a) Ladder stop loss and take profit not hit - exit triggered by time


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/b2bddd108a6fce7781451d7796bc115d5d793b1d1f53457d8cdf6462d1fa73f8.jpg)



(b) Ladder stop loss hit on the first position, exiting the trade. The the trade is re-entered later


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/00ab64f0499999125faa7cb200ae215531d2776ff303c36ffa20080a49df132e.jpg)



(c) Ladder take profit hit triggering a partial exit, stop loss & take profit moved for the next ladder step



Figure 4: Comparison of diferent scenarios for a ladder stop loss & take profit strategy


Diferent scenarios shown for a ladder stop loss & take profit strategy for QQQ on 2<sup>nd</sup> July 2024. VWAP is drawn in blue, the entry noise boundary is depicted in grey and as a darker area, stop loss is depicted as dashed lines in red, take profit is depicted in green. 

## 5 Parameter optimization


The results of the entry and exit strategies are highly dependent on the parameters used. To find the best parameters for the strategies, a Parameter optimization approach is used using the Optuna library <sup>[4]</sup>. The parameters optimized are:


<table><tr><td></td><td>Boundary &amp; VWAP</td><td>Boundary with different exit</td><td>Boundary with different exit &amp; VWAP</td><td>VWAP</td></tr><tr><td>lookback_days</td><td>√</td><td>√</td><td>√</td><td>√</td></tr><tr><td>volatility_multiplier-enter</td><td>√</td><td>√</td><td>√</td><td>√</td></tr><tr><td>volatility_multiplier_exit</td><td></td><td>√</td><td>√</td><td></td></tr><tr><td>target_daily_volatilitya</td><td>√</td><td>√</td><td>√</td><td>√</td></tr><tr><td>start_trade_after_open_minutes</td><td>√</td><td>√</td><td>√</td><td>√</td></tr><tr><td>trade_frequency_minutes</td><td>√</td><td>√</td><td>√</td><td>√</td></tr><tr><td>exit_trades_before_close_minutes</td><td>√</td><td>√</td><td>√</td><td>√</td></tr></table>


σ , see Section 2 


Table 4: Summary of what parameters are optimized for each strategy without a ladder. See Figure 3 for the strategies. 

<table><tr><td></td><td>Boundary &amp; Ladder</td><td>VWAP &amp; Ladder</td><td>Ladder</td></tr><tr><td>lookback_days</td><td>√</td><td>√</td><td>√</td></tr><tr><td>volatility_multiplier_enter</td><td>√</td><td>√</td><td>√</td></tr><tr><td>volatility_multiplier_exit</td><td></td><td></td><td></td></tr><tr><td>target_daily_volatilitya</td><td>√</td><td>√</td><td>√</td></tr><tr><td>start_trade_after_open_minutes</td><td>√</td><td>√</td><td>√</td></tr><tr><td>trade_frequency_minutes</td><td>√</td><td>√</td><td>√</td></tr><tr><td>exit_trades_before_close_minutes</td><td>√</td><td>√</td><td>√</td></tr><tr><td>stop_loss_ladder_step_0</td><td>√</td><td>√</td><td>√</td></tr><tr><td>stop_loss_ladder_step_1</td><td>√</td><td>√</td><td>√</td></tr><tr><td>take_profit_ladder_step_0</td><td>√</td><td>√</td><td>√</td></tr><tr><td>take_profit_ladder_step_1</td><td>√</td><td>√</td><td>√</td></tr></table>


a σ , see Section 2 



Table 5: Summary of what parameters are optimized for each strategy with a ladder. See Figures 3 and 4 for the strategies. 


The following parameters have interdependencies between them: 

$$
\begin{array}{l} \text {volatility\_multiplier\_exit <   volatility\_multiplier\_enter} \\ \text {stop\_loss\_ladder\_step\_1 > stop\_loss\_ladder\_step\_0} \\ \text {take\_profit\_ladder\_step\_0 > stop\_loss\_ladder\_step\_1} \\ \text {take\_profit\_ladder\_step\_1 > take\_profit\_ladder\_step\_0} \end{array}\tag{6}
$$

To ensure these constraints are met, the parameter optimization framework is used to calculate a diferential value for the dependent parameters and the actual values are calculated based on these: 

volatility_multiplier_exit = volatility_multiplier_enter + volatility_multiplier_exit_dif stop_loss_ladder_step_1 = stop_loss_ladder_step_0 + stop_loss_ladder_step_1_dif take_profit_ladder_step_0 = stop_loss_ladder_step_1 + take_profit_ladder_step_0_dif_stop_loss_1 take_profit_ladder_step_1 = take_profit_ladder_step_0 + take_profit_ladder_step_1_dif 

(7) 


See Table 6 for the parameter ranges used in the optimization.


<table><tr><td></td><td>type</td><td>min</td><td>max</td><td>step</td></tr><tr><td>lookback_days</td><td>int</td><td>1</td><td>60</td><td>1</td></tr><tr><td>volatility_multiplier_enter</td><td>float</td><td>0.1</td><td>10.0</td><td>0.01</td></tr><tr><td>volatility_multiplier_exit_diff</td><td>float</td><td>-1.0</td><td>0.0</td><td>0.01</td></tr><tr><td>target_daily_volatility</td><td>float</td><td>0.001</td><td>0.1</td><td>0.001</td></tr><tr><td>start_trade_after_open_minutes</td><td>int</td><td>1</td><td>90</td><td>1</td></tr><tr><td>trade_frequency_minutes</td><td>int</td><td>1</td><td>60</td><td>1</td></tr><tr><td>exit_trades_before_close_minutes</td><td>int</td><td><eq>11^a</eq></td><td>90</td><td>1</td></tr><tr><td>stop_loss_ladder_step_0</td><td>float</td><td>-2.0</td><td>0.0</td><td>0.01</td></tr><tr><td>stop_loss_ladder_step_1_diff</td><td>float</td><td>0.0</td><td>5.0</td><td>0.01</td></tr><tr><td>take_profit_ladder_step_0_diff_stop_loss_1</td><td>float</td><td>0.0</td><td>10.0</td><td>0.01</td></tr><tr><td>take_profit_ladder_step_1_diff</td><td>float</td><td>0.0</td><td>100.0</td><td>0.01</td></tr></table>


<sup>a</sup> We’re exiting trades at least 11 minutes before market close as most trading platforms start to apply overnight margin requirements 10 minutes before market close. 


Table 6: Parameter optimization details: minimum and maximum values and step sizes for each parameter 

When a stop loss & take profit ladder is used, a risk parameter r of 2% of the Asset Under Management (AUM) is used. 

The optimization framework is asked to simultaneously maximize the Sharpe Ratio and Alpha of each strategy over a 10 year period for QQQ, between 1<sup>st</sup> October 2014 and 1<sup>st</sup> October 2024 on 1 second trade bars. As the maximum value for lookback days is 60 trading days, the first 60 trading days are skipped to ensure the lookback period is always valid and that the trading simulation is always run on the same timeframe. 

SPY is used as a benchmark to calculate Alpha and Beta, which is a good representation of the S&P 500 index. 

## 6 Results


See Table 7 for the best parameter optimization results for each strategy. For most strategies, two diferent parameter sets are considered, providing a balance between the Sharpe Ratio and Alpha. The parameters for each strategy are shown in Tables 9, 10 and 11 in Appendix. A plot showing the cumulative returns can be found in Figure 5 and Figure 6 plotted on a logarithmic scale.


<table><tr><td>Strategy</td><td>Sharpe Ratio</td><td>Alpha</td><td>Beta</td><td>Ann <eq>\text{Ret}^{\text{a}}</eq></td><td>Ann <eq>\text{Vol}^{\text{b}}</eq></td><td><eq>\text{MDD}^{\text{c}}</eq></td><td><eq>\text{MDD Period}^{\text{d}}</eq></td></tr><tr><td>Boundary &amp; VWAP #1</td><td>2.11</td><td>26%</td><td>-4%</td><td>37%</td><td>17%</td><td>18%</td><td>54</td></tr><tr><td>Boundary &amp; VWAP #2</td><td>2.13</td><td>24%</td><td>-5%</td><td>34%</td><td>16%</td><td>16%</td><td>254</td></tr><tr><td>Boundary with different exit #1</td><td>2.76</td><td>36%</td><td>-6%</td><td>51%</td><td>19%</td><td>22%</td><td>23</td></tr><tr><td>Boundary with different exit #2</td><td>2.71</td><td>38%</td><td>-7%</td><td>53%</td><td>20%</td><td>21%</td><td>23</td></tr><tr><td>Boundary with different exit &amp; VWAP</td><td>2.32</td><td>31%</td><td>-3%</td><td>44%</td><td>19%</td><td>22%</td><td>93</td></tr><tr><td>VWAP #1</td><td>3.16</td><td>39%</td><td>1%</td><td>58%</td><td>18%</td><td>15%</td><td>107</td></tr><tr><td>VWAP #2</td><td>2.98</td><td>40%</td><td>2%</td><td>59%</td><td>20%</td><td>15%</td><td>107</td></tr><tr><td>Boundary &amp; Ladder #1</td><td>2.24</td><td>34%</td><td>-6%</td><td>47%</td><td>21%</td><td>20%</td><td>174</td></tr><tr><td>Boundary &amp; Ladder #2</td><td>2.57</td><td>34%</td><td>-7%</td><td>47%</td><td>18%</td><td>14%</td><td>38</td></tr><tr><td>VWAP &amp; Ladder #1</td><td>3.08</td><td>31%</td><td>-1%</td><td>45%</td><td>15%</td><td>11%</td><td>29</td></tr><tr><td>VWAP &amp; Ladder #2</td><td>2.64</td><td>35%</td><td>-3%</td><td>50%</td><td>19%</td><td>21%</td><td>38</td></tr><tr><td>Ladder #1</td><td>3.34</td><td>41%</td><td>-5%</td><td>60%</td><td>19%</td><td>13%</td><td>166</td></tr><tr><td>Ladder #2</td><td>3.35</td><td>39%</td><td>-5%</td><td>57%</td><td>17%</td><td>12%</td><td>61</td></tr></table>


<sup>a</sup> Annualized Return 



<sup>b</sup> Annualized Volatility 



<sup>c</sup> Maximum Drawdown 



<sup>d</sup> Maximum Drawdown Period in days 



Table 7: Best parameter optimization results for each strategy


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/34ee184e7ee3921b3e13e3b9d70679b91f50f784f18b40e12dcb2c70a8439fd9.jpg)



Figure 5: Cumulative returns



Cumulative returns for the best strategies found, two baseline strategies and SPY as the benchmark.


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/730418e584378ba4dfd89721482a02db2b04cee83ea7a54673061217300b1a04.jpg)



Figure 6: Cumulative returns on a logarithmic scale



Cumulative returns for the best strategies found, two baseline strategies and SPY as the benchmark.


## 7 Discussion

We have shown that the momentum strategy can be improved by using diferent exit strategies. The best results were achieved with the VWAP, VWAP & Ladder and Ladder strategies, with Sharpe ratios over 3 in some cases and annualized returns of over 50%, which are significant improvements against the baseline strategy presented in 1. 

The low beta values are a good indication that the strategies are not correlated with the market, which is a good sign for a momentum strategy. This is also visible in Figure 6, where we can clearly see the significant dips in the benchmark at the end of 2018 and in Q2 2020 or 2022, with our strategies not being afected by these or even showing significant gains. 

To conintue the example of 2<sup>nd</sup> July 2024 detailed in Figures 3 and 4, the behaviour of the most successful strategies detailed in Table 7 are shown in Figure 7, broken up between two figures. The strategy returns are against $100 000 of Asset Under Management. The diferences in return stem from the diferent exit strategies as well as the diferent strategy parameters, like trade entry time after the market open, trade frequency time, and the time before market close when the trades are exited, or the stop loss and take profit levels in the ladder strategy. For the Ladder strategies shown in Figures 7l and 7m, it may seem that the first trade is exited at VWAP, but in fact the stop loss is being hit, similarly to Figure 4b. The reference strategies with a 90 day lookback period and volatility multipliers of 1.0 and 1.3 are shown in Figures 7n and 7o. 

All of the successful strategies found through parameter optimization have a lower lookback period than the baseline strategy, some as low as 2 days. This suggests that the momentum strategy is more efective when it reacts to recent price movement patterns when predicting a breakout of the noise area and entering significant daily movement. 

The successful VWAP exit strategies use a volatility multiplier close to or even below 1.0. This can be interpreted that the prediction of the algorithm is that the daily movement will be strong even if it hasn’t yet reached the average daily volatility for the past few days. The successful VWAP & Ladder and Ladder strategies employ a volatility multiplier of 1.33 or 1.28, showing that these strategies only enter a trade when the daily movement is 28% or 33% stronger than the average daily movement for the past few days. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/4168805d3c0f5ecafcd23066d24282c6102230547943312d3c64aa26ec85f303.jpg)



(a) Bondary & VWAP #1: 4 trades, return -$20


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/6b82a5cb92570214494b2fb716f4bc695493770f59aecfcdbf5107c489bccdde.jpg)



(b) Bondary & VWAP #2: 4 trades, return -$177


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/95e4dbf8621f07baf72e5de6a6d99bbf07eafdeeb172bd1cb457abee39be9b42.jpg)



(c) Boundary & diferent exit #1: 2 trades, return $1594


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/eb8f47ba62e2682bb3bda390662f7a4ba6e510ecf3044ccc46aa35f2371ece12.jpg)



(d) Boundary & diferent exit #2: 2 trades, return $1714


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/2c69c090ab363d4c23a68634bfac1066cbd7b76c79c1266bd10fdb482a9879cf.jpg)



(e) Boundary with diferent exit & VWAP:



2 trades, return $1393



Figure 7: Behaviour of the performing strategies on the $2 ^ { \mathrm { n d } }$ July 2024.


Behaviour of the performing strategies listed in Table 7 for the $2 ^ { \mathrm { n d } }$ July 2024. The results are against $100 000 of Asset Under Management. Continued on next page. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/43e1c2f8d979095e7fe9a245b3ec0dea26e12751db517cf9a0e631ce8d7546e0.jpg)



(f) VWAP #1: 2 trades, return $1245


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/01e02662f888e841049f56c4073940f1b0eeed83c700704e89aaabf82c62cfec.jpg)



(g) VWAP #1: 2 trades, return $1245


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/032d062e4c55d0896b2af389cd02215ba83ee1183429572dbac7aa64dc397308.jpg)



(h) VWAP & Ladder #1: 2 trades, return $1434


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/00632f67ca2ce7661819031369d48877eb5c64ee24b2554b73a555d651da447c.jpg)



(i) VWAP & Ladder #2: 2 trades, return $1308


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/b5df987ef3d816ae66f75b8ecc088157520d5ce0342bac4108d4fb729358d9c4.jpg)



(j) Boundary & Ladder #1: 2 trades, return $1378


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/5fec09b82c29a5c267634d22da94f6a51115c1e51f057186f791ff5e26add5de.jpg)



(k) Boundary & Ladder #2: 4 trades, return $288



Figure 7: Behaviour of the performing strategies on the 2<sup>nd</sup> July 2024, continued.


Behaviour of the performing strategies listed in Table 7 for the 2<sup>nd</sup> July 2024. The results are against $100 000 of Asset Under Management. Continued from the previous page. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/a73451222e896c87825f9771e29beb8834af38e66a4f443921615ff7e40ae8f9.jpg)



(l) Ladder #1: 2 trades, return $1698


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/a466947a3f84e0c901610bba283db5b6ff6a5e0d18b7f82cc5a0ea53f496de5b.jpg)



(m) Ladder #2: 2 trades, return $1698


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/7ade55090b3821a2145f920ca4432b9d7d29bee67fb0475cf42635bdf3bbb36e.jpg)



(n) Reference lookback 90 days volatility 1.0x: 2 trades, return $393


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/d6329f7d88ac776022c7d5a47e59c2fff2c52a6a3291e2eee3a46c9e412dca6c.jpg)



(o) Reference lookback 90 days, volatility 1.3x: 2 trades, return $87



Figure 7: Behaviour of the performing strategies on the $2 ^ { \mathrm { n d } }$ July 2024, continued.


Behaviour of the performing strategies listed in Table 7 for the 2<sup>nd</sup> July 2024. The results are against $100 000 of Asset Under Management. Continued from the previous page. 

For the ladder step exit strategies, the steps are defined as multipliers of 2% of the Assent Under Management (AUM). Table 8 shows the steps in relation to the AUM based on the raw parameters in Table 11. We can see that most successful strategies have a trade entry stop loss risking less than 1% of the AUM and 2 out of 4 have a stop loss at step 1 that is still below the entry price per trade. The algorithm may enter multiple trades per day risking more each day. The take profit step of the first ladder is not realistically reachable for 3 out of 4 of the strategies, implying a time based exit. 

<table><tr><td></td><td>Boundary &amp; Ladder #1</td><td>Boundary &amp; Ladder #2</td><td>VWAP &amp; Ladder #1</td><td>VWAP &amp; Ladder #2</td><td>Ladder #1</td><td>Ladder #2</td></tr><tr><td>stop_loss_ladder_step_0</td><td>-1.08%</td><td>-1.08%</td><td>-0.81%</td><td>-1.30%</td><td>-0.80%</td><td>-0.80%</td></tr><tr><td>stop_loss_ladder_step_1</td><td>3.46%</td><td>4.96%</td><td>-0.56%</td><td>5.68%</td><td>0.32%</td><td>-0.54%</td></tr><tr><td>take_profit_ladder_step_0</td><td>6.44%</td><td>7.92%</td><td>4.40%</td><td>23.44%</td><td>5.10%</td><td>4.24%</td></tr><tr><td>take_profit_ladder_step_1</td><td>8.70%</td><td>10.18%</td><td><eq>74.16\%^a</eq></td><td><eq>43.28\%^a</eq></td><td>7.36%</td><td><eq>40.64\%^a</eq></td></tr></table>


<sup>a</sup> Take profit level not realistically reached, the strategy will exit based on time before market close



Table 8: Stop loss and take profit levels for each ladder step in relation to Asset Under Management


Dynamic sizing is introduced in Zarattini et al. <sup>1</sup> using a target_daily_volatility or $\sigma _ { \mathrm { t a r g e t } }$ parameter to calculate the entry size in relation to the Available Margin (AM). The impact of this parameter is that in some cases it will enter a trade with a smaller position size than the maximum available margin. This would allow a smaller trade entry when the result is uncertain, reudcing losses. For the most successful algorithms found through parameter optimization the impact of this parameter is shown in Figure 8, where we can see that the most common entry size is 100% of the Available Margin for all strategies, although for some strategies it gets as low as 75%. It also seems that losing trades do have not use lower entry sizes somewhat more frequently, compared to winning trades, but the diference is not significant. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/94bc09d6-e616-4031-9561-bfb25f4401af/9499f360fa90225b29c21b014fcbc4d03fbc54db48917edc87c52cbf81283bcd.jpg)



Figure 8: Usage frequency of entry size percentage



Usage frequency of various entry sizes in percentage of Available Margin based on σ<sub>target</sub> or target_daily_volatility.


## 8 Conclusion

We have shown that the momentum strategy can be improved by using diferent exit strategies and by applying a parameter optimization approach. The best results were achieved with the VWAP, VWAP & Ladder and Ladder strategies, with Sharpe ratios over 3.0 and annualized returns of over 50%, which are significant improvements against the baseline strategy presented in Zarattini et al. <sup>1</sup> and listed in Table 1. 

## Appendix


A selection of parameter sets for the best strategies found through parameter optimization.


<table><tr><td></td><td>Boundary &amp; VWAP #1</td><td>Boundary &amp; VWAP #2</td><td>Boundary with different exit #1</td><td>Boundary with different exit #2</td></tr><tr><td>lookback_days</td><td>5</td><td>8</td><td>5</td><td>5</td></tr><tr><td>volatility_multiplier_penter</td><td>1.05</td><td>1.05</td><td>1.29</td><td>1.29</td></tr><tr><td>volatility_multiplier_exit</td><td></td><td></td><td>0.78</td><td>0.78</td></tr><tr><td>target_daily_volatility<eq>^{a}</eq></td><td>0.030</td><td>0.018</td><td>0.016</td><td>0.029</td></tr><tr><td>start_trade_after_open_minutes</td><td>20</td><td>58</td><td>7</td><td>7</td></tr><tr><td>trade_frequency_minutes</td><td>42</td><td>45</td><td>35</td><td>35</td></tr><tr><td>exit_trades_before_close_minutes</td><td>12</td><td>12</td><td>16</td><td>22</td></tr></table>


a σ<sub>target</sub>, see Section 2 



Table 9: Parameters for various strategies, see Table 7


<table><tr><td></td><td>Boundary with different exit &amp; VWAP</td><td>VWAP #1</td><td>VWAP #2</td></tr><tr><td>lookback_days</td><td>4</td><td>2</td><td>2</td></tr><tr><td>volatility_multiplier-enter</td><td>1.14</td><td>1.03</td><td>0.85</td></tr><tr><td>volatility_multiplier_exit</td><td>0.35</td><td></td><td></td></tr><tr><td>target_daily_volatility<eq>^{a}</eq></td><td>0.030</td><td>0.013</td><td>0.014</td></tr><tr><td>start_trade_after_open_minutes</td><td>10</td><td>12</td><td>12</td></tr><tr><td>trade_frequency_minutes</td><td>50</td><td>45</td><td>45</td></tr><tr><td>exit_trades_before_close_minutes</td><td>31</td><td>13</td><td>13</td></tr></table>


<sup>a</sup> σ , see Section 2 



Table 10: Parameters for various strategies, see Table 7


<table><tr><td></td><td>Boundary &amp; Ladder #1</td><td>Boundary &amp; Ladder #2</td><td>VWAP &amp; Ladder #1</td><td>VWAP &amp; Ladder #2</td><td>Ladder #1</td><td>Ladder #2</td></tr><tr><td>lookback_days</td><td>4</td><td>4</td><td>4</td><td>4</td><td>4</td><td>4</td></tr><tr><td>volatility_multiplier-enter</td><td>0.85</td><td>1.08</td><td>1.33</td><td>1.33</td><td>1.28</td><td>1.28</td></tr><tr><td>volatility_multiplier_exit target_daily_volatilitya</td><td>0.024</td><td>0.020</td><td>0.025</td><td>0.020</td><td>0.064</td><td>0.052</td></tr><tr><td>start_trade_after_open_minutes</td><td>23</td><td>4</td><td>42</td><td>13</td><td>42</td><td>42</td></tr><tr><td>trade_frequency_minutes</td><td>18</td><td>18</td><td>46</td><td>15</td><td>23</td><td>23</td></tr><tr><td>exit_trades_before_close_minutes</td><td>30</td><td>30</td><td>30</td><td>30</td><td>30</td><td>30</td></tr><tr><td>stop_loss_ladder_step_0</td><td>-0.54</td><td>-0.54</td><td>-0.41</td><td>-0.65</td><td>-0.40</td><td>-0.40</td></tr><tr><td>stop_loss_ladder_step_1</td><td>1.73</td><td>2.47</td><td>-0.28</td><td>2.87</td><td>0.16</td><td>-0.27</td></tr><tr><td>take_profit_ladder_step_0</td><td>3.22</td><td>3.96</td><td>2.2</td><td>11.72</td><td>2.55</td><td>2.12</td></tr><tr><td>take_profit_ladder_step_1</td><td>4.35</td><td>5.09</td><td>37.08</td><td>21.64</td><td>3.68</td><td>20.32</td></tr></table>


a σ , see Section 2 



Table 11: Parameters for each strategy with a stop loss & take profit ladder, see Table 7 


## References



[1] Carlo Zarattini, Andrew Aziz, and Andrea Barbon. Beat the market an efective intraday momentum strategy for S&P500 ETF (SPY). Swiss Finance Institute Research Paper, No. 24-97, May 2024. doi:10.2139/ssrn.4824172. URL https://ssrn.com/abstract=4824172. 





[2] Oleg Polakow. VectorBT Pro, 2024. URL https://vectorbt.pro/. 





[3] Interactive Brokers. Interactive Brokers Stock Commissions, 2024. URL https://www. interactivebrokers.com/en/pricing/commissions-stocks.php. 





[4] Takuya Akiba, Shotaro Sano, Toshihiko Yanase, Takeru Ohta, and Masanori Koyama. Optuna: A next-generation hyperparameter optimization framework. In Proceedings of the 25th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, 2019. 

