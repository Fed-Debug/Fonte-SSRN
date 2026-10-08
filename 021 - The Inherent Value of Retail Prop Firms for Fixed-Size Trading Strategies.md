Zachary Youngblood Student at the Gabelli School of Business, Fordham University P.O. Box 1356, 441 East Fordham Road, Bronx, NY 10458, United States zwy@fordham.edu 21 August 2026 

The Inherent Value of Retail Prop Firms for Fixed-Size Trading Strategies 

# The Inherent Value of Retail Prop Firms for Fixed-Size Trading Strategies

21 August 2026 

## ABSTRACT

This article examines whether a retail proprietary or “prop” trading framework can create positive expected economic value for a trading strategy with little or no directional edge. Using 10,000 randomized long/short paths applied to approximately 10 years of 1-minute Nasdaq futures data, the study tests a fixed-size strategy that enters once daily at 10:00 a.m. ET, trades eight Micro E-mini Nasdaq-100 contracts, and uses symmetric 100-tick take-profit and stop-loss barriers. The strategy produced a 49.98% TP/SL win rate and approximately break-even gross performance before transaction costs. Its fixed position size also limits daily profit and loss to $400, rendering several prop firm rules inconsequential. When the same trading paths were evaluated under the modeled Topstep $50,000 account framework, mean trader payouts were $9,368.50 against mean account costs of $7,878.30, producing mean net economic P&L of $1,490.19 per account. However, 39.70% of full-sample simulations lost money, and results varied materially between the two five-year subperiods. The findings establish that retail prop firm premiums can be underpriced for certain strategies: a fixed-size strategy with no directional edge achieved positive expected economic value when the same strategy was simulated through a prop firm’s framework. 

## KEY TAKEAWAYS

• Fixed position sizing made several retail prop firm rules irrelevant, showing that these rules can screen position-sizing behavior without necessarily screening for trading skill. 

• Fixed-size trading, natural market variance, and asymmetric payout structure are the prop firm properties which transformed a strategy with no edge into one with substantial economic value, suggesting each account is underpriced by around $16. 

• The effect was not uniform over time: payouts averaged approximately $1.06 per $1.00 of costs in the first five years and $1.22 in the second, showing that value fluctuates between different market regimes. 

Keywords: retail proprietary trading, expected value, fixed position sizing, trading constraints, futures 

JEL Codes: G13, G17, G23 

## 1. INTRODUCTION

Proprietary or “prop” trading firms fall into two broad groups. Institutional firms such as Jane Street and Susquehanna International Group trade their own capital. Retail prop firms, the focus here, let individual traders trade simulated accounts under rules that can lead to real payouts. By complying with consistency standards and achieving profit targets traders can withdraw most of the simulated funds they earned on the account. 

Research on traditional prop firms has looked at position sizing, risk limits, and the difficulty of separating skill from chance (Jackson 2014). Newer work studies retail evaluations directly. Lim (2026a) models a funded-trader challenge as a contingent claim and shows that value can depend heavily on risk sizing. Lim (2026b) finds wide value differences across 31 retail prop firm contracts and little connection between those values and headline fees. This article asks a narrower question: can a fixed-size strategy with no edge still have positive value inside a retail prop firm framework? 

## 1.1 Hypothesis

This study tests whether retail prop firm accounts can create positive value for a fixedsize strategy with no directional edge due to three key mechanisms: 

1. Fixed-Size Trading: Rules meant to stop oversized or concentrated trades have a negligible impact on strategies whose size and daily gain or loss are already capped by self-imposed rules. 

2. Natural Market Variance: Strategies deviate from their historical average return. For example, the S&P 500 has a nominal average annual return of around 10% but has only returned 10% in 6 calendar years. 

3. Asymmetric Payout Structure: Through prop firms, the downside risk to traders is capped by the account cost, while the potential upside is substantially higher. 

Points two and three are related because theoretically through prop firm framework a trader will generate substantially more during periods when their strategy is higher performing, and their downside is bounded during periods when it is not. These mechanisms should transform even a marginally profitable fixed-size trading strategy into one with significantly higher positive expected value, therefore implying that premiums paid for prop firm accounts are underpriced. 

## 2. METHODOLOGY

## 2.1 Prop Firm Selection

This study uses Topstep as a representative retail prop firm because its account rules, fees, drawdown mechanics, and payout requirements are clearly defined and can be modeled. The research is independent and unsponsored. The final specification uses Topstep’s $50,000 simulated account. Topstep accounts utilize a 2-phase structure. Phase 1 is an evaluation (“Combine”) and if traders pass, they move on to Phase 2 (“Express Funded Account” or “XFA”). This simulation uses Topstep’s “Consistency” path to payout (Option 2) due to its decreased trading day requirement and higher maximum payout quantity which is better suited for the arbitrary strategy outlined below. 

The model separates simulated account balances from the trader’s real cash flows. Combine and XFA balances, targets, drawdowns, gains, and losses are simulated and determine progression, failure, and payout eligibility. The trader’s real downside is account costs; the real upside is cash payouts. Net economic P&L is therefore payouts minus account costs, not changes in the simulated balance. 

## 2.2 Strategy Design

The strategy was deliberately designed to be arbitrary and produce no-edge. The same trades are first measured on their own and then run through the prop firm framework, allowing the change in economic outcome to be traced to the prop firm contribution rather than a different trading strategy. 

## Strategy Rules:

1. Instrument: Micro E-mini Nasdaq-100 (MNQ) futures 

2. Position size: 8 MNQ contracts 

3. Trading frequency: One trade per eligible trading day 

4. Entry: 10:00 a.m. EST 

5. Direction: Randomly assigned long or short with equal probability 

6. Stop-loss: 100 ticks (25 index points) 

7. Take-profit: 100 ticks (25 index points), producing a 1:1 risk-reward ratio 

8. TP/SL value: +/-$400 gross for 8 MNQ contracts 

9. Transaction cost: $1.22 round-turn per MNQ contract, or $9.76 per 8-contract trade 

10. Time exit: Trades that hit neither TP or SL are closed at 4:00 p.m. EST 

11. Session filter: Holidays, early closures, and days with no 10 a.m. candle are excluded 

12. Ambiguous observations: TP and SL hit in same 1-minute bar are excluded 

## 2.3 Backtesting Protocol

The strategy was coded in Python and backtested on ten years of 1-minute Nasdaq-100 futures data from August 8, 2016 through August 5, 2026. The program required a valid 10:00 a.m. EST bar and a full session. It excluded 87 early closures due to holidays, one full session missing the 10:00 bar, and four days where both the take-profit and stop-loss were hit in the same one-minute candle, making the order unknowable. Those four ambiguous days were about 0.16% of the 2,485 recorded trades and therefore deemed negligible. 

For each eligible day, the program calculated both the hypothetical long and short outcome from the 10:00 a.m. entry. A trade exited when its 100-tick take-profit or stop-loss was hit; otherwise it closed at 4:00 p.m. and resulting P&L was recorded. The program generated 10,000 randomized long/short paths over the same dates using a fixed seed of 42 for reproducibility. The same paths were used to backtest the strategy without prop firm framework (the “raw strategy”) and with prop firm implementation, so differences in results came from the account framework rather than different trade decisions. 

These are not 10,000 independent ten-year market histories. Every simulation uses the same 2,485 historical days and randomizes only the direction taken on each date. The exercise therefore measures how different trade sequences affect outcomes within the observed sample. It does not claim to represent every market path that could occur in the future. This distinction matters because the purpose of the randomization is to remove trading skill while keeping the market environment fixed. 

## 2.4. Raw Strategy Performance

## EXHIBIT 1


Distribution of Full-Sample Raw Strategy P&L Across 10,000 Randomized Paths


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-27/064c1244-cf48-4b3a-a818-ee7f1b99a894/0da0dd4cedc53f97e86b258ab82d8b744325fc3f4805d76012bd192354777b09.jpg)


As intended, the strategy was approximately no-edge. Across 10,000 paths, the mean counts were 1,143.98 TP wins, 1,145.02 TP/SL losses, and 196 time exits per 2,485-trade path. Among barrier-resolved trades, the win rate was 49.98%, essentially the 50% break-even rate before costs. Exhibit 1 shows an approximately normal distribution across the randomized paths. 

Mean gross raw P&L was -$0.1678 per trade, -$416.86 per full path, with a median of - $568. Together with the 49.98% win rate, this shows little meaningful directional edge. At $9.76 per round turn, 2,485 trades cost $24,253.60, taking mean net standalone P&L to about - $24,670.46. These results demonstrate a truly neutral benchmark. 

## 2.5 Raw Strategy Simulation Five-Year Split

Before applying the proprietary trading framework, the raw strategy was examined across two consecutive five-year intervals to determine whether the no-edge baseline depended on one portion of the sample. The first period runs from August 8, 2016, through August 6, 2021, and contains 1,246 eligible trading days. The second runs from August 9, 2021, through August 5, 2026, and contains 1,239 eligible trading days. 

The raw strategy remained approximately no-edge in both subperiods. During the first period, the TP/SL win rate was 49.99%, mean gross raw P&L was -$0.0408 per trade, mean total gross raw P&L was -$50.78 per randomized path, and median total gross raw P&L was -$96. During the second period, the TP/SL win rate was 49.96%, mean gross raw P&L was -$0.2955 per trade, mean total gross raw P&L was -$366.08, and median total gross raw P&L was -$400. Neither period deviates from the results originally observed, which reaffirms the legitimacy of this raw strategy as a 0-edge benchmark. 

## 3.0 PROP FIRM SIMULATION

It is essential to distinguish simulated account values from actual profit and loss incurred by the trader: simulated trading gains and losses determine whether an account passes, fails, or qualifies for a payout, while the study's economic P&L consists only of real account costs and trader cash payouts. This is illustrated by the table below: 

<table><tr><td>Simulated P&amp;L</td><td>Real Economic P&amp;L</td></tr><tr><td>Combine Profit Target: $3,000</td><td>Account Cost: $85 per month paid by trader</td></tr><tr><td>Combine and XFA Maximum Loss Limit: $2,000; trails the highest balance until locking at $50,000 in the Combine and $0 in the XFA</td><td>Payout Cap: $6,000 per eligible payout request</td></tr><tr><td>Combine Consistency Requirement: no single best day may represent more than 50% of the profit required to pass</td><td>Maximum Payout Request: 50% of the XFA profit balance</td></tr><tr><td>Daily Loss Limit: $1,000</td><td>Minimum Payout Request: $125</td></tr><tr><td>Reset Credit: one reset credit is earned when the Trading Combine subscription rebills; if a Combine fails, a reset credit can be used rather than repurchasing the Combine, this extends the next billing date by 30 days</td><td>Payout Split: 90% trader / 10% Topstep</td></tr><tr><td>XFA Payout Requirement: at least three trading days with at least one trade per day</td><td></td></tr><tr><td>XFA Consistency Requirement: no single trading day may account for more than 40% of total profit for the payout cycle</td><td></td></tr></table>

The Topstep Trading Combine, XFA, and payout process were modeled by programming the rules outlined above and applying them to the same 10,000 randomized trading paths on the fixed seed 42. The same 10:00 a.m., 100-tick, eight-MNQ raw strategy was used without modification. 

Breaching any of the above rules, such as the Maximum Loss Limit (“MLL”), result in termination of the account. In the simulation, whenever an account is breached a new one is purchased. Therefore, one account is active at all times. The other two rules that can trigger account closure are the Daily Loss Limit and Consistency Requirements for both Combine and XFA. The Daily Loss Limits for Combine and XFA and Consistency Requirement for Combine only do not apply to the tested strategy because with a TP/SL that does not exceed $400, and maximum of one trade per day, it is impossible for a daily loss of $1,000 to be incurred. Furthermore, due to the Combine profit target of $3,000, it is impossible for one trading day to account for more than 50% of the total profit, or $1,500. 

That is not to say this strategy has been completely optimized for prop firm usage. It is the same ambiguous system that generated a winrate of 49.98% using the raw strategy. However, the parameters of the system were created with Topstep’s account rules in mind. A $400 TP/SL is not a proven value expected to generate the best result, rather, it was a value that conveniently lay below Topstep’s daily loss limit and resulted in several rules becoming irrelevant. 

The model also records monthly rebills, reset credits earned and used, Combine passes, XFA failures, payouts, transaction costs, and account costs. A complete audit program was used to check for account cost accuracy, duplicate rebills, reset-credit conservation, payout caps, consistency ratios, and validate the net-P&L. 

The primary economic result is defined on a single $50,000 account sequence. Topstep permits up to five Express Funded Accounts, but five synchronized copies mechanically scale dollar outcomes by five without changing the probability of profitability; the five-account case is therefore not treated as an independent economic result. 

## 3.1 Prop Firm Simulation Results

As anticipated, the simulation revealed substantial differences in economic outcomes when the same 10,000 randomized trading paths were evaluated under Topstep's proprietary trading framework. The distribution of full-sample net economic outcomes across the 10,000 randomized paths is presented in Exhibit 2. 


EXHIBIT 2 Distribution of Prop Firm Net P&L Across 10,000 Randomized Paths


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-27/064c1244-cf48-4b3a-a818-ee7f1b99a894/00eacb96834a1b830407f53e83acf1f025ffb0751f7c8782e9fd1a18b1b1bc3d.jpg)


While the Net P&L is still concentrated at $0, the distribution is now skewed to the right. On a single-account basis, the full-sample simulation generated mean trader payouts of $9,368.50 and mean account costs of $7,878.30. Mean actual net P&L was therefore +$1,490.19 per randomized simulation, while median net P&L was +$1,036.83. Mean payouts relative to mean account costs correspond to approximately $1.19 of payouts for every $1.00 of account costs. The standard deviation of net P&L was $3,926.12, with 5th- and 95th-percentile outcomes of -$3,995.42 and +$8,612.82. Overall, 60.30% of simulations were profitable. 

Applying the full payout-to-cost ratio of approximately 1.19 to the modeled $85 monthly fee implies a fair premium fee near $101 per month ($85 × 1.19), suggesting each account is $16 cheaper than its efficient market valuation. 

The account lifecycle was active rather than being driven by a small number of isolated payouts. Per simulation, the model generated an average of 31.01 Combine subscriptions purchased, 61.68 monthly rebills, 56.31 reset credits used, 17.62 Combine passes/XFAs earned, 17.47 XFA failures, and 14.95 payouts. 

The randomized raw strategy trading process produced mean gross P&L of only -$0.17 per trade and -$416.86 over the complete 2,485-trade path, confirming the absence of meaningful gross directional edge. After applying $9.76 of transaction costs to each standalone trade, mean net raw P&L was approximately -$24,670.46 per path. By comparison, the modeled proprietary framework generated +$1,490.19 of mean net economic P&L per account after account-related costs and trading costs were incorporated. This net-to-net comparison shows that the positive result must be attributed to the incorporation of the prop firm framework. 

Across five accounts, mean net P&L increased to approximately $7,450.95, with a median of $5,184.15. As previously mentioned, all five accounts followed the same 

synchronized trading path, and therefore the results multiply P&L without altering the probability of profitability. 

## 3.2 Prop Firm Simulation Five-Year Split

As with the raw strategy, the proprietary trading simulation was rerun separately over the two five-year blocks. The raw strategy remained approximately zero-edge in both periods, allowing differences in prop firm outcomes to be examined independently of other factors. 

## EXHIBIT 3


Distribution of Net Prop Firm P&L by Five-Year Subperiod


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-27/064c1244-cf48-4b3a-a818-ee7f1b99a894/a62211dc2865afd75d1297dd7d8a2d9f95182216dba53d9d0d4e938fedb0d57c.jpg)


As shown in Exhibit 3, the two five-year periods produced very different economic outcomes. From August 2016 through August 2021, a single account generated mean actual net P&L of +$253.08 and median net P&L of -$214.23. Only 46.45% of simulations were profitable, while 53.55% lost money. Mean trader payouts were $4,155.81 and mean account costs were $3,902.73, corresponding to approximately $1.06 of payouts for every $1.00 of account costs. The 5th- and 95th-percentile net outcomes were approximately -$3,046.92 and +$5,181.51. The positive mean alongside a negative median reflects the right skewness displayed above, but the negative median and minority of profitable paths also show that the economic value in the first period was weak. 

From August 2021 through August 2026, the single-account result strengthened significantly. Mean actual net P&L increased to +$913.49, median net P&L to +$403.34, and 56.05% of simulations were profitable. Mean trader payouts were $5,108.40 and mean account costs were $4,194.91, corresponding to approximately $1.22 of payouts for every $1.00 of account costs. 

A major contributor to the difference between the periods was the distribution of time exits, or trades that did not hit TP or SL and instead were closed at 4 p.m. with their P&L 

accounted for. The first block averaged 196 time exits per randomized path, whereas the second block had zero. This makes sense – more time exits means more trades with a lower P&L absolute value. And if it takes longer for an account to pass or fail, that just means that account will pay more in monthly subscription costs without any greater chance of achieving a payout. 

Across five accounts, mean net P&L was +$1,265.40 in 2016–2021, with a median of −$1,071.15. In 2021–2026, the five-account results strengthened to mean net P&L of +$4,567.45 and median net P&L of +$2,016.70. 

The subperiod results show that positive prop firm value did not require positive trading edge, but the size and reliability of that value varied across the sample. While both subperiods still achieved positive net returns, the payout-to-cost ratio increased from approximately 1.06 in the first five-year period to 1.22 in the second. Combined with the first period's negative median and 46.45% profitability rate, this indicates that the stronger full-sample result was driven by the second five-year period rather than by consistently strong outcomes across both subperiods. 

## 3.3 Time Cost

Time spent trading is a practical consideration of any tested system. Because the strategy uses predetermined take-profit and stop-loss levels, a trader could place a bracket order with the 10:00 a.m. entry rather than continuously monitoring the position. A time-exit procedure is still required on days when neither barrier is reached, but a trader could simply check their trade at 4 p.m. without spending significantly more time on the charts. In the first five-year block this occurred an average of 196 times per randomized path, while no eligible trades required a time exit in the second block. The results of this tested system indicate that a trader could substantially increase their expected value through prop firms without sacrificing any additional time out of their day. 

## 4. DISCUSSION

## 4.1 Implications

The main result is that positive prop firm value did not require directional edge. Both strategies yielded a 49.98% TP/SL win rate and mean gross P&L of -$0.17 per trade. After trading costs, mean standalone P&L was about -$24,670.46 per path, yet the same paths produced positive mean net P&L under Topstep’s framework. 

Again, three mechanisms appear particularly important: 

1. Fixed-Size Trading: By maintaining a position size of 8 $MNQ contracts and set TP/SL of 100 ticks (risking $400 to make $400), the trading system will never breach the Daily Loss Limit or Combine’s Consistency Requirement. 

2. Natural Market Variance: The raw strategy yielded a winrate of approximately 50% in the long-term across all simulations but varied between individual simulations sometimes fluctuating above that benchmark and sometimes below. 

3. Asymmetric Payout Structure: The right skewness displayed by the returns of the prop firm simulation suggests that better performing simulations achieved significantly higher returns than were lost by underperforming simulations. 

For traders, standalone expected return is not enough to judge whether a strategy fits a prop firm account. Strategies with similar expected returns can have very different value under the same rules. What matters is “prop firm compatibility”: how position size, trade frequency, payoff size, dispersion, barrier hits, and sequencing interact with rules that can actually bind. Lim (2026a) reaches a related result in a stylized model, where funded-account value is concentrated around certain levels of risk sizing. 

The account fee can also be viewed as an option-like premium. Jacobs (2000) uses similar option-pricing intuition for strategies that seek upside while limiting downside. A retail prop account creates a related asymmetry: the trader pays a fixed fee for conditional upside while real losses are limited to the costs of obtaining and maintaining the account. The results show that prop firm premiums can be underpriced for some strategies, not that they are always underpriced. Lim (2026b) likewise finds large value differences across 31 contracts and shows that funded-stage terms can matter more than the headline fee. This study extends that idea by showing that value can also change within the same contract: the stronger second-period results occurred even though the account rules and price remained unchanged. 

## 4.2 Limitations

The results of this research would be incomplete without considering the various limitations present. First, the simulations assume exact adherence to the strategy and account rules. Real trading can include slippage, missed trades, execution errors, and discretionary changes. Paths can also include long stretches without payouts and mounting account costs. The prop firm simulation from the first five years shows this risk: the median result was negative and only 46.45% of paths were profitable. Traders may quit or change the strategy before a favorable long-run result appears. 

Second, the model uses the Topstep rules, fees, and payout structure programmed for this study and assumes those terms remain available and payouts are honored. Firms can change fees, drawdowns, consistency rules, payout limits, or account structures, so the estimates should be read as results for the modeled contract rather than a permanent valuation of Topstep. Transaction costs are included in both raw and prop firm backtests, but live trading may also involve slippage, latency, missed fills, or other execution differences that are not captured here. 

Third, results varied sharply across the sample. The payout-to-cost ratio was about 1.06 in the first five years and 1.22 in the second even though directional edge stayed near zero. Results could also change with trade frequency, payoff size, position size, barrier-hit frequency, or other strategy choices. 

Fourth, the study covers one firm, one account size and payout option, one instrument, one fixed-size strategy, and one historical sample. One-minute data also cannot show which barrier was hit first when both the take-profit and stop-loss occur inside the same candle, so four ambiguous days were excluded rather than guessed. The findings show that prop firm premiums can be underpriced under the tested conditions, not that every firm or strategy offers positive expected value. Taxes, legal treatment, trader psychology, and other operating issues are outside the model and could matter in practice. 

## 5. CONCLUSION

## 5.1 Summary

This study asks whether retail proprietary firm accounts can create positive expected value from an underlying strategy with no edge. Across 10,000 randomized paths and 2,485 eligible Nasdaq futures trading days, the ambiguous strategy designed for this test had a 49.98% TP/SL win rate and roughly zero gross P&L per trade. After trading costs, mean standalone P&L was about -$24,670.46 per path. 

Under Topstep’s rules, however, the same paths produced positive mean and median net P&L after account costs, and 60.30% were profitable. The mean payout amounts totaled $9,368.50 and mean account costs were $7,878.30 per account, which corresponds to approximately $1.19 in payouts for every $1.00 in account costs. The $1.19 payout-to-cost ratio implies a break-even monthly fee of approximately $101, suggesting each account is underpriced by around $16. Importantly, the result was not consistent across time. The payout-to-cost ratio was $1.06 in the first five years and $1.22 in the second, with the stronger second period driving much of the full-sample result. 

The prop firm fee can be viewed as a premium for access to a payoff dependent on a trader’s performance. Here, a strategy with roughly zero gross directional edge gained positive expected value from the prop firm structure itself. Fixed-size trading, natural market variance, and asymmetric payout structure are the three mechanisms which provide value for traders within the prop firm framework. Due to these properties, a strategy with no edge produced positive expected value within the prop firm framework, demonstrating that proprietary firm accounts are underpriced for this specific system. 

## 5.2 Future Research

Future work could test other market regimes, entry times, position sizes, trade frequencies, TP/SL distances, and prop firms. Cross-firm comparisons could focus on fees, drawdowns, consistency rules, and payout terms. 

Another useful extension would be to estimate a fair account premium from a strategy’s return distribution and examine independent versus synchronized multi-account portfolios and larger account sizes. Long-run firm sustainability and changing policies also deserve study. 

## 5.3 Endnotes

All historical 1-minute Micro Nasdaq Futures data were purchased from BacktestMarket. 

## 5.4 References

Jackson, Antony. “A Simple Scheme for Allocating Capital in a Foreign Exchange Proprietary Trading Firm.” Journal of Asset Management 16, no. 1 (December 18, 2014): 2–13. https://doi.org/10.1057/jam.2014.40. 

Jacobs, Bruce I. “Momentum Trading.” The Journal of Investing 9, no. 4 (November 30, 2000): 6–8. https://doi.org/10.3905/joi.2000.319434. 

Lim, Boon Chuan. Phantom generosity: Contract Design and value in the market for proprietary-trading evaluations, 2026. https://doi.org/10.2139/ssrn.7184138. 

Lim, Boon Chuan. The price of a funded account: An actuarial analysis of proprietary trading firm challenges, 2026. https://doi.org/10.2139/ssrn.7178078. 

“TOPSTEP Express Funded Account Rules.” Topstep. Accessed August 19, 2026. https://www.topstep.com/express-funded-account-rules. 

zyoungblood6. “Zyoungblood6/the-Inherent-Edge-of-Retail-Proprietary-Trading-Firms.” GitHub. Accessed August 19, 2026. https://github.com/zyoungblood6/The-Inherent-Edgeof-Retail-Proprietary-Trading-Firms. 

## 5.5 Acknowledgements

The author expresses sincere gratitude to Professor Thanh Ngo of East Carolina University for her invaluable guidance and support on this project. After a long break from this work, Professor Ngo’s feedback provided renewed motivation to rework and complete the article. The author also thanks Nathanial Cefalu-Schwartz for recognizing the value of this research from the beginning and for assisting with the original research. 

AI Use: During the preparation of this work, the author used ChatGPT (OpenAI) to assist with language editing and improving readability. The author reviewed and edited all AI-assisted text and takes full responsibility for the content of the publication. 