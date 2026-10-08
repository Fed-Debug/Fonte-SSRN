# Structural Limits of OHLCV-Based Intraday Signals in MNQ Futures: A Systematic Falsification Study

Mathias Mesfin 

Independent Researcher 

mathiasmesfin.research@gmail.com 

Research Period: 2024–2026 

Manuscript Date: May 2026 

## Abstract

This paper investigates whether intraday momentum signals derived from open-high-low-close-volume (OHLCV) data generate statistically significant trading edge in Micro E-Mini Nasdaq 100 futures (ticker: MNQ) under realistic execution constraints. Using 947 regular trading hours (RTH) trading days of five-minute bar data spanning 2021 through 2025, we construct and systematically test fourteen distinct signal families. These include opening range breakouts at multiple horizons, gap-based continuation and fade strategies, volume signature signals, cross-session momentum from the Asia session, liquidity grab reversals, volatility-regime-conditioned classifiers, and news-event-driven directional strategies. 

Every signal is evaluated against a consistent institutional standard: a minimum T-statistic of 2.0 on out-of-sample walk-forward results, a minimum of 30 out-of-sample trades, positive net return after a fixed two-point round-trip friction cost, and multi-year stability across all available years. No tested signal survives these combined criteria simultaneously. The gross edge available to next-bar-open systematic execution is structurally constrained to approximately 0.07 to 1.50 points across all signal families—a ceiling that is insufficient to clear two-point round-trip transaction costs. 

One signal family—gap continuation short—produces a T-statistic of 3.23 and a mean net return of 14.52 points but on only 22 trades across three years, falling below the minimum sample threshold and therefore failing deployment criteria. Two separately validated signals—the RTH Confluence Signal (T = 5.83, mean net +15.77 pts, N = 538) and London Session Signal B (T = 5.15, mean net +5.77 pts, N = 289)—are presented as positive controls confirming the methodology is capable of detecting genuine edge when it exists. 

The primary contribution of this paper is methodological: a reproducible, documented falsification framework applied consistently across a broad signal universe on a liquid modern futures instrument. This contributes to a systematic null result that is underrepresented in both retail and academic trading literature, where survivorship bias tends to publish only strategies that appear to work. All results are based on strictly out-of-sample walk-forward validation. 

Keywords: intraday momentum, futures markets, OHLCV, systematic falsification, walk-forward validation, market microstructure, E-mini Nasdaq, transaction costs, signal development 

## 1. Introduction

The hypothesis that short-term price patterns in equity index futures contain exploitable directional information is widely held in retail trading communities and appears frequently in early academic literature on intraday momentum (Gao, Han, Li, & Zhou, 2018; Heston, Korajczyk, & Sadka, 2010). The practical question—whether such patterns survive realistic execution costs on modern, highly liquid instruments—receives considerably less rigorous treatment. Most published retail strategy research suffers from survivorship bias: strategies that appear to work are shared; the far larger population of strategies that do not work is never documented. 

This paper addresses that gap. Rather than searching for a strategy to deploy, we designed a systematic falsification program: define a signal family, apply the cleanest possible test with strict no-lookahead execution assumptions, and report what the data shows—including, especially, when the answer is negative. The research was conducted on Micro E-Mini Nasdaq 100 futures (MNQ), a retail-accessible instrument on one of the world’s most liquid equity index futures markets. MNQ was selected because its liquidity and narrow bid-ask spread minimize execution confounds, and because its tick-by-tick data is widely available, making results reproducible. 

The central finding of this paper is a documented gross edge ceiling: across fourteen signal families and multiple parameter configurations, the maximum achievable gross return from next-bar-open systematic execution on five-minute MNQ bars is approximately 0.07 to 1.50 points per trade. A two-point round-trip transaction cost—which we argue is a conservative estimate for realistic prop firm or retail futures execution—eliminates this gross edge entirely in every case. This result is not a failure of methodology; it is informative about the competitive structure of the market itself. 

The paper proceeds as follows. Section 2 describes the data and execution framework. Section 3 presents the validation standards. Section 4 documents each signal family systematically. Section 5 presents the two positive control signals. Section 6 discusses the structural interpretation of the gross edge ceiling. Section 7 covers limitations and extensions. Section 8 concludes. 

## 2. Data and Execution Framework

## 2.1 Data

The primary dataset consists of 72,604 five-minute OHLCV bars for MNQ continuous front-month futures, covering regular trading hours (09:30–16:00 ET) from December 2021 through August 2025. After removing partial days and session boundary artifacts, 947 complete trading days remain. Data was sourced from NinjaTrader and aggregated from one-minute source bars. 

A secondary dataset of MGC (Micro Gold Futures) five-minute RTH bars covering 1,091 trading days over the same period was used for instrument comparison tests. Asia session analysis used 20:00–02:00 ET bars from the same continuous front-month contract. 

<table><tr><td>Parameter</td><td>Value</td></tr><tr><td>Primary instrument</td><td>MNQ (Micro E-Mini Nasdaq 100)</td></tr><tr><td>Bar resolution</td><td>5-minute OHLCV (RTH)</td></tr><tr><td>Session definition</td><td>09:30–16:00 ET</td></tr><tr><td>Total bars (RTH)</td><td>72,604</td></tr><tr><td>Complete trading days</td><td>947</td></tr><tr><td>Date range</td><td>December 2021 – August 2025</td></tr><tr><td>Secondary instrument</td><td>MGC (Micro Gold Futures)</td></tr><tr><td>MGC trading days</td><td>1,091</td></tr><tr><td>Source platform</td><td>NinjaTrader (aggregated from 1-minute)</td></tr></table>


Table 1. Dataset summary.


## 2.2 Execution Assumptions

All signals are computed at bar close. All entries are executed at the open of the next bar. This bar-close / next-bar-open structure is the minimum realistic assumption for systematic execution and eliminates any possibility of same-bar fill bias. No signal is permitted to use any data from the bar in which it fires for the entry price calculation. 

A fixed two-point round-trip friction cost is applied to every MNQ trade. This represents approximately $4.00 per micro contract and encompasses bid-ask spread, exchange fees, and conservative slippage. For high-volatility environments where the bid-ask spread on MNQ can widen to two ticks or more, this assumption may understate actual costs. All net return figures reported in this paper are after this friction deduction unless explicitly noted as gross. 

## 2.3 Walk-Forward Validation Structure

All signal testing uses expanding-window walk-forward validation. The training window grows progressively: train on 2022, test on 2023; train on 2022–2023, test on 2024; train on 2022–2024, test on 2025. Parameters are selected only on the training window. The test window is never touched until the final evaluation step. This structure prevents the most common form of backtest overfitting—using future data to select parameters—and produces out-of-sample performance estimates that are structurally more reliable than in-sample optimization. 

For signals where no parameter selection is required (pure characterization tests), the full dataset is used and year-by-year stability is assessed by splitting results by calendar year. A result is considered year-stable only if it shows consistent direction and statistical significance across all three primary years (2022, 2023, 2024). 

## 3. Validation Standards

A signal is considered to pass validation only if it satisfies all five of the following criteria simultaneously. Satisfying a subset is not sufficient for deployment consideration. 

<table><tr><td>Criterion</td><td>Threshold</td><td>Rationale</td></tr><tr><td>T-statistic</td><td>≥2.0 (OOS only)</td><td>Minimum statistical significance; in-sample T-stats are not reported as evidence</td></tr><tr><td>Trade count</td><td>≥30 (OOS)</td><td>Below 30 trades, variance is too large for reliable inference</td></tr><tr><td>Net return</td><td>Positive after 2-pt friction</td><td>Economic significance requirement; gross edge alone is insufficient</td></tr><tr><td>Year stability</td><td>Consistent across all years</td><td>Single-year results are treated as potentially spurious</td></tr><tr><td>Permutation test</td><td>p&lt;0.05 where applicable</td><td>Confirms result is not explained by random sequence effects</td></tr></table>


Table 2. Validation criteria. Allfive must be satisfied simultaneously.


These standards are deliberately conservative. In a liquid, highly competitive market such as MNQ, the prior probability of finding genuine exploitable edge in publicly available OHLCV data is low. Applying a lower bar would increase false positive rates substantially. The two positive control signals documented in Section 5 both clear these criteria comfortably, confirming the standards are achievable when genuine edge exists. 

All negative results are archived and treated as permanent findings. A signal that fails these criteria is logged as rejected and is not revisited without documented new evidence or a materially different hypothesis. This prevents the common research failure mode of repeatedly adjusting parameters until a signal appears to pass. 

## 4. Signal Families Tested

## 4.1 Opening Range Breakout (ORB)

The opening range breakout is among the most widely discussed intraday signals in retail futures trading literature. The hypothesis is that a price breakout beyond the high or low of the first N bars of the session signals directional continuation. We test the 09:30–09:55 ET opening range (first six five-minute bars) with immediate entry on breakout, pullback entry, and delayed entry variants. 

<table><tr><td>Variant</td><td>N</td><td>Mean Net (pts)</td><td>T-Stat</td><td>Win Rate</td><td>Verdict</td></tr><tr><td>ORB Long – bar+1</td><td>447</td><td>-0.82</td><td>1.17</td><td>51.9%</td><td>FAIL</td></tr><tr><td>ORB Long – bar+15</td><td>447</td><td>+2.82</td><td>1.50</td><td>55.5%</td><td>FAIL</td></tr><tr><td>ORB Short – bar+1</td><td>428</td><td>-3.45</td><td>-1.33</td><td>47.2%</td><td>FAIL</td></tr><tr><td>ORB Short – bar+15</td><td>428</td><td>-2.16</td><td>-0.04</td><td>47.7%</td><td>FAIL</td></tr><tr><td>ORB Pullback Entry</td><td>83</td><td>-4.44</td><td>-1.27</td><td>19.3%</td><td>FAIL</td></tr></table>


Table 3. Opening range breakout results across variants. All after 2-point friction.


The long breakout at a 15-bar horizon shows the highest T-statistic of 1.50 but remains well below the 2.0 threshold. Year-by-year analysis reveals the reason: 2022 produces −1.42 net, 2023 produces +2.43 net, and 2024 produces +7.04 net at this horizon. The 2024 figure is materially strong but is not reflected in the combined T-statistic because 2022 and 2023 are near-zero or negative. This pattern—one strong year masking weak or negative other years—is the most common failure mode across all tested signals in this study. 

The pullback entry variant (wait for price to retrace to within 5 points of the breakout level before entering) produces a catastrophic 80.7% stop-out rate at a 20-point stop, yielding −4.44 net and T = −1.27. The pullback entry hypothesis assumes that retracements after breakouts are temporary. In MNQ, a high proportion of apparent breakouts simply fail and reverse, making pullback entries systematically wrong. 

## 4.2 Asia Session Opening Range Expansion

This signal tests whether expansion bars during the Asia session (20:00–02:00 ET)—bars whose range exceeds a multiple of the rolling 20-bar mean range—produce directional continuation in the expansion direction. Three expansion thresholds are tested: 1.5x, 2.0x, and 2.5x the rolling mean range. 

<table><tr><td>Threshold</td><td>Horizon</td><td>Gross (pts)</td><td>Net (pts)</td><td>T-Stat</td><td>Win Rate</td></tr><tr><td>1.5x</td><td>b+1</td><td>-0.27</td><td>-2.27</td><td>-10.96</td><td>35.5%</td></tr><tr><td>1.5x</td><td>b+6</td><td>-0.08</td><td>-2.08</td><td>-4.75</td><td>44.4%</td></tr><tr><td>2.0x</td><td>b+1</td><td>-0.35</td><td>-2.35</td><td>-7.42</td><td>36.0%</td></tr><tr><td>2.5x</td><td>b+6</td><td>+1.06</td><td>-0.94</td><td>-0.90</td><td>48.5%</td></tr></table>


Table 4. Asia session expansion bar results. Continuation direction tested.


Figure 3. Average post-breakout price pathfor Asia session expansion bars. Empirical result (red) declines immediately after breakout, opposite to the continuation hypothesis. T = -10.96 at bar+1 confirms the reversal is statistically significant. 


Figure 3 — Asia ORB Post-Breakout Path


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/00c018d5-a1e8-4cfa-b150-c83fcc25eac1/a10e7aee1b5906107052d024ef0b980789f236a8145344fa8987a80a79c5a191.jpg)


The T-statistics here are large and negative, indicating that the continuation direction is actively wrong—not merely unprofitable, but the opposite of the signal's prediction. The T = −10.96 at the 1.5x threshold and one-bar horizon is among the strongest directional results in the entire study, but in the wrong direction. The expansion burst is real but fully contained within the expansion bar itself. By the time a bar-close signal fires and entry executes at the next bar open, the directional move is exhausted. This execution timing finding has broad implications: it suggests that any OHLCV-based strategy targeting expansion moves at bar resolution is structurally disadvantaged on this instrument. 

## 4.3 Asia Session Liquidity Grab Reversal

The liquidity grab signal identifies bars where price temporarily pierces a recent session extreme (high or low) before closing back inside the range, hypothesizing that this sweep of stop orders creates a reversal opportunity. A total of 6,442 such events were identified across the dataset (3,419 long grabs, 3,023 short grabs). 

Fading the grab direction produced mean net −2.20 points with T = −14.12. Trading in the continuation direction (with the grab) produced mean net −1.80 points with T = −13.24. Both directions are significantly negative. The gross directional content of the signal is 0.20–0.80 points in either direction, which is structurally insufficient to clear friction regardless of which direction is traded. This is a pure friction ceiling result: the signal has real directional content but the magnitude is too small to be economically exploitable at this resolution. 

## 4.4 Gap Fill Fade and Gap Continuation

Gap analysis tests two competing hypotheses about overnight gaps in MNQ. The gap fill hypothesis predicts that overnight gaps close (price returns toward the prior close) during the RTH session. The gap continuation hypothesis predicts that gap direction persists. 

<table><tr><td>Strategy</td><td>Entry Time</td><td>N</td><td>Mean Net (pts)</td><td>T-Stat</td><td>Win Rate</td><td>Verdict</td></tr><tr><td>Gap Fill Fade</td><td>09:30</td><td>238–245/yr</td><td>-1.92</td><td>-0.44</td><td>48.1%</td><td>FAIL</td></tr><tr><td>Gap Fill Fade</td><td>09:45</td><td>238–245/yr</td><td>-1.31</td><td>-0.32</td><td>47.2%</td><td>FAIL</td></tr><tr><td>Gap Fill Fade</td><td>10:00</td><td>238–245/yr</td><td>-2.24</td><td>-0.59</td><td>47.9%</td><td>FAIL</td></tr><tr><td>Gap Continuation Short</td><td>09:30 (Kalman v&gt;2.5)</td><td>22</td><td>+14.52</td><td>+3.23</td><td>68.2%</td><td>FAIL – N&lt;30</td></tr></table>


Table 5. Gap strategy results across entry times.


The gap fill fade fails at every tested entry time. MNQ gaps do not consistently fill within the RTH session; the market is as likely to continue in the gap direction as to reverse. The T-statistics of −0.44 to −0.59 are indistinguishable from noise. 

The gap continuation short signal with a Kalman velocity filter above 2.5 is the most interesting result in the study from a purely statistical standpoint: T = 3.23, mean net +14.52 points, win rate 68.2%. However, this signal produced only 22 trades across three years (approximately 0.6 signals per month), falling below the minimum 30-trade threshold required for valid inference. Year-by-year breakdown shows 12 trades in 2022, 6 in 2023, and 4 in 2024, with the frequency declining over time. This signal cannot be validated as a deployable edge under current sample constraints, though the directional finding—that MNQ gap-down days with high Kalman velocity tend to continue downward—is a preserved research asset for future investigation with additional data. 

## 4.5 Volume Signature Signals

Two volume-based hypotheses were tested. The volume spike momentum hypothesis predicts that bars with unusually high volume (top decile relative to rolling 20-bar mean) signal directional continuation in the bar's direction. The volume dry-up exhaustion hypothesis predicts that bars with unusually low volume signal exhaustion of the prior move and an imminent reversal. 

<table><tr><td>Signal</td><td>Direction</td><td>N</td><td>Mean Net (pts)</td><td>T-Stat</td><td>Win Rate</td></tr><tr><td>Volume Spike Momentum</td><td>Up spike</td><td>2,119</td><td>-1.94</td><td>+0.07</td><td>51.6%</td></tr><tr><td>Volume Spike Momentum</td><td>Down spike</td><td>2,409</td><td>-2.50</td><td>-0.64</td><td>50.1%</td></tr><tr><td>Volume Dry-Up Exhaustion</td><td>Up exhaustion</td><td>1,060</td><td>-2.42</td><td>-0.92</td><td>47.4%</td></tr><tr><td>Volume Dry-Up Exhaustion</td><td>Down exhaustion</td><td>723</td><td>-1.99</td><td>+0.03</td><td>49.7%</td></tr></table>


Table 6. Volume signature signal results. All after 2-pointfriction.


Both volume hypotheses fail cleanly. The T-statistics for all four variants are near zero, confirming that volume magnitude at the bar level does not reliably predict next-bar direction. The sample sizes here are large (over 2,000 trades in some variants), which means the near-zero T-statistics are genuine estimates of the population effect rather than artifacts of small samples. These are precise null results. 

## 4.6 Volatility Regime Classifier

A composite day-classification system identifies days simultaneously in the top tercile of three pre-market observable conditions: absolute first-30-minute return, absolute overnight gap, and first-bar volume deviation from a 20-day rolling baseline. This three-condition intersection—termed the volatility-volume-gap (VVG) classifier—activates on approximately 4.4% of trading days (40 days across the 2021–2025 dataset). 

Classifier-positive days show statistically distinct behavioral characteristics: mean next-day return spread of 25.6 basis points above non-classifier days, and a 77.6% peak-reversal rate before the session close. These descriptive findings are genuine. However, all tested directional trading strategies on classifier-positive days fail the validation criteria. 

<table><tr><td>Strategy on Classifier Days</td><td>N</td><td>Mean Net (pts)</td><td>T-Stat</td><td>Win Rate</td><td>Verdict</td></tr><tr><td>Reversal entry</td><td>289</td><td>+1.37</td><td>+0.86</td><td>51.9%</td><td>FAIL</td></tr><tr><td>Continuation entry</td><td>1,175</td><td>-3.22</td><td>-0.44</td><td>48.8%</td><td>FAIL</td></tr><tr><td>Close fade (3:30 PM)</td><td>&lt;30</td><td>insuff.</td><td>1.08</td><td>50.0%</td><td>FAIL – N&lt;30</td></tr></table>


Table 7. VVG classifier directional strategy results.


Year-by-year analysis of the continuation strategy reveals the reason for the overall failure: 2024 shows T = 2.07 with mean net +9.14 points on 312 trades, which would pass validation in isolation. However, 2022 shows T = −1.27 with mean net −9.51, and 2023 shows T = −0.70. The signal is not stable across years; it reflects different behavioral regimes in different years rather than a consistent structural effect. A result driven by a single year is by design treated as insufficient evidence under our validation framework. 

## 4.7 Event Day Trend (News-Driven Signals)

Following high-impact USD economic releases (FOMC, CPI, NFP, PCE), the hypothesis is that forced institutional repositioning creates sustained directional order flow in the 10–60 minutes following the release. A ForexFactory calendar providing 993 qualifying high-impact events from 2022–2025 was used to identify event days. 

The post-release directional signal fails for a structural reason: the measured drift (mean net positive) was entirely contained within bars 1–5 following the release—the news spike itself. When correctly measured from bar +6 onward, all tested horizons produce T-statistics between 0.14 and 0.69. Additionally, the two largest release types by market impact (NFP at 08:30 ET and CPI at 08:30 ET) are entirely excluded under Apex Trader Funding prop firm rules that restrict trading to RTH hours. The event day signal produced T = 0.38 on the filtered RTH-compatible sample. 

An important secondary finding: comparing signal performance on news days versus non-news days for the two validated signals (RTH Confluence and London Signal B) shows no significant difference. London Signal B actually performs modestly better on news days (T = 0.38, mean difference +0.72 points), while RTH Confluence shows no year-stable directional effect from news proximity. This means news calendar filters add no value to the validated signal portfolio. 

## 4.8 MGC Mean Reversion (Cross-Instrument Test)

As a cross-instrument falsification check, Ornstein-Uhlenbeck mean reversion was tested on MGC (Micro Gold Futures) at multiple timeframes. Gold was selected as the comparison instrument due to its structurally different behavioral character—MGC has a Hurst exponent closer to 0.5 compared to MNQ’s 0.59, suggesting less momentum persistence and potentially more mean-reverting behavior. 

<table><tr><td>Configuration</td><td>N</td><td>Mean Net (pts)</td><td>T-Stat</td><td>Win Rate</td><td>Verdict</td></tr><tr><td>OU signal, 5-min, threshold 1.5</td><td>380</td><td>-2.76</td><td>-4.49</td><td>32.1%</td><td>FAIL</td></tr><tr><td>OU signal, 5-min, threshold 2.0</td><td>154</td><td>-2.19</td><td>-2.19</td><td>36.4%</td><td>FAIL</td></tr><tr><td>OU signal, 5-min, threshold 2.5</td><td>49</td><td>-1.72</td><td>-1.12</td><td>34.7%</td><td>FAIL</td></tr><tr><td>OU signal, 60-min</td><td>varies</td><td>-2.00 approx.</td><td>-1.46</td><td>&lt;40%</td><td>FAIL</td></tr></table>


Table 8. MGC mean reversion results across configurations. All after 2-point friction.


All MGC OU configurations fail, with most showing strongly negative T-statistics. The 60-minute OU signal on MGC shows a half-life of approximately 7.85 bars (roughly 8 hours), which structurally exceeds a single RTH session and makes it incompatible with intraday execution constraints. The raw edge of 0.28 points before friction at the 60-minute resolution confirms the friction ceiling finding extends across instruments. 

Figure 1. T-statistics across all fourteen signal families. The red dashed line at T = 2.0 indicates institutional threshold. All bars fall below threshold except gap continuation short which fails on sample size (N = 22). 


Figure 1 — T-Statistic Across Signal Families


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/00c018d5-a1e8-4cfa-b150-c83fcc25eac1/e795cf7d7b963946425a6a85fef7c9f5081e98a33e4688fd6963892467c5ea25.jpg)


## 5. Positive Control Signals

Two signals from a separate research program are presented here as positive controls. Their purpose is to confirm that the methodology used in this paper is capable of detecting genuine edge when it exists—that the consistent null results in Section 4 reflect a true absence of edge rather than a flaw in the testing framework. These signals were developed independently and are not the subject of this paper. 

## 5.1 RTH Confluence Signal (ATR-Adaptive)

The RTH Confluence Signal fires when three conditions are simultaneously true on a completed five-minute bar: the current bar’s GMM regime label equals Regime 1 (Active Flow), the rolling 200-bar Markov transition probability to Regime 2 exceeds 0.15, and the rolling 50-bar volume z-score exceeds 0.5. Entry is on a 25-point (ATR-scaled) pullback from the signal bar close. Exit is at bar 13 from the signal bar. These signals are intentionally not optimized or expanded in this paper to avoid contaminating the falsification framework. 

<table><tr><td>Metric</td><td>Value</td></tr><tr><td>Signal count (IS, 2022–2024)</td><td>538</td></tr><tr><td>Mean net return (horizon 13)</td><td>+15.77 pts</td></tr><tr><td>T-statistic (horizon 13)</td><td>5.83</td></tr><tr><td>Win rate (horizon 13)</td><td>61.0%</td></tr><tr><td>Walk-forward OOS T-stat</td><td>3.11</td></tr><tr><td>Walk-forward OOS mean net</td><td>+11.82 pts</td></tr><tr><td>Walk-forward OOS trades</td><td>196</td></tr><tr><td>2025 OOS mean net (ATR-adaptive)</td><td>+13.14 pts</td></tr><tr><td>Permutation test result</td><td>p &lt; 0.001</td></tr></table>


Table 9. RTH Confluence Signal performance summary.


## 5.2 London Session Signal B (R0→R2 Transition)

London Signal B fires when the GMM regime classifier on 15-minute London session bars (03:00–08:30 ET) detects a clean transition from Regime 0 (Bearish Chop) to Regime 2 (Bullish Drift) with no Regime 1 contamination in the prior two bars. Entry is long at the next 15-minute bar open. Exit is 60 minutes later or at 08:30 ET, whichever comes first. 

<table><tr><td>Metric</td><td>Value</td></tr><tr><td>Total trades</td><td>289</td></tr><tr><td>Mean net return</td><td>+5.77 pts</td></tr><tr><td>T-statistic</td><td>5.15</td></tr><tr><td>Win rate</td><td>64.7%</td></tr><tr><td>Profit factor</td><td>2.42</td></tr><tr><td>Sharpe ratio</td><td>5.09</td></tr><tr><td>Permutation p-value</td><td>&lt; 0.001</td></tr><tr><td>Parameter sensitivity range</td><td>T = 3.87–4.83 across all variations</td></tr><tr><td>1-bar delay reversal</td><td>T = -3.56 (edge destroyed)</td></tr></table>


Table 10. London Session Signal B performance summary.


Both signals clear all five validation criteria with substantial margin. Their T-statistics (5.83 and 5.15) are roughly three times the minimum threshold. This confirms that the validation framework used in Section 4 is not so restrictive as to reject all edges—it accepts edges that are real and rejects edges that are not. 

## 6. The Gross Edge Ceiling: A Structural Interpretation

## 6.1 Quantifying the Ceiling

Across all fourteen signal families in Section 4, the maximum gross return observed before friction deduction is approximately 1.05 to 1.50 points at the most favorable tested horizons. The minimum friction assumption of 2.0 points round-trip consistently exceeds this gross edge. This is not a coincidence or a methodological artifact—it reflects a structural property of the market. Sensitivity analysis suggests that even at sub-1-point friction, the majority of signal families remain below economic viability thresholds. 

<table><tr><td>Signal Family</td><td>Best Gross Return</td><td>T-Stat (Gross)</td><td>Net After 2pt Friction</td><td>T-Stat (Net)</td></tr><tr><td>ORB Long</td><td>+4.82 pts(bar+15)</td><td>1.50</td><td>+2.82 pts</td><td>1.50*</td></tr><tr><td>Asia ORB Expansion 2.5x</td><td>+1.06 pts (b+6)</td><td>-0.90</td><td>-0.94 pts</td><td>-0.90</td></tr><tr><td>Gap Fill Fade</td><td>-1.31 pts (best)</td><td>-0.32</td><td>-1.31 pts</td><td>-0.32</td></tr><tr><td>Gap Continuation Short</td><td>+16.52 pts</td><td>+3.23</td><td>+14.52 pts</td><td>+3.23*</td></tr><tr><td>Volume Spike Momentum</td><td>-1.94 pts</td><td>+0.07</td><td>-1.94 pts</td><td>+0.07</td></tr><tr><td>VVG Classifier Reversal</td><td>+3.37 pts gross</td><td>+0.86</td><td>+1.37 pts</td><td>+0.86</td></tr><tr><td>MGC OU (5-min, 2.0x)</td><td>-0.19 pts gross</td><td>-2.19</td><td>-2.19 pts</td><td>-2.19</td></tr></table>


Table 11. Gross vs. net return comparison across signalfamilies. * indicates T≥2.0 in at least one metric butfailing on other criteria.



Figure 2. Year-by-year net return heatmap across signalfamilies. Red indicates negative net return, blue positive. Single-year outliers are visible in severalfamilies, confirming year instability as the primaryfailure mode.



Figure 2 — Year-by-Year Net Return Heatmap


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/00c018d5-a1e8-4cfa-b150-c83fcc25eac1/4f15f8abb62fd669b7627ef26396d1572cd9f46d0e49384c4de3b1bbf1a289ed.jpg)


## 6.2 Why the Ceiling Exists

The gross edge ceiling has a straightforward market microstructure interpretation. MNQ is among the most actively traded futures contracts in the world. Any OHLCV-observable pattern that reliably predicts next-bar direction creates an arbitrage opportunity that institutional participants with lower transaction costs and faster execution can exploit. The rational equilibrium is that such patterns are traded away until their gross edge approximately equals the friction cost of the marginal participant. For retail-accessible instruments, this equilibrium is at roughly 1–2 points gross per trade on five-minute bars. 

This is distinct from saying the market is perfectly efficient in a strong-form sense. The two positive control signals in Section 5 demonstrate that edge above this ceiling exists—but both signals use regime classification and multi-bar hold periods that capture structural market state transitions rather than single-bar price patterns. The ceiling appears to apply specifically to single-bar directional predictions from price and volume features observable by all market participants. 

## 6.3 Implications for OHLCV-Based Research

The finding has a practical implication for anyone designing intraday systematic strategies on liquid equity index futures. Strategies that rely on next-bar-open execution following a bar-close signal face a structural handicap: the gross edge available from OHLCV features at this resolution is too small to survive realistic friction. Strategies that have appeared to work in retail literature may have benefited from the following confounds: (1) use of bid-mid or unrealistic fill prices, (2) failure to account for full round-trip costs, (3) optimization on in-sample data that does not generalize, or (4) reporting only positive results from a larger set of tests (multiple comparisons bias). 

The two categories of strategy that avoid this ceiling, based on the positive controls in Section 5, share a common feature: they hold positions for 12–15 bars (60–75 minutes) rather than 1–6 bars. This longer hold period allows the signal’s regime-level information to generate sufficient net points to overcome friction. 

Figure 4. Gross return per trade vs. T-statistic across all signal variants. The vertical line at 2.0 points marks the friction threshold. All OHLCV signalfamilies cluster below this line. RTH Confluence and London Signal B (positive controls) plotted as distinct markers above threshold. 


Figure 4 — Gross vs. Net Edge Scatter


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/00c018d5-a1e8-4cfa-b150-c83fcc25eac1/a102e5215e57f1c15a5c01785b9aa66b2fff02f4989b4135def87be0686a8688.jpg)


## 7. Limitations and Extensions

## 7.1 Limitations

The friction assumption of two points round-trip is fixed throughout this study. Actual friction varies with session time, volatility, and order size. In high-volatility regimes, MNQ bid-ask spreads can widen significantly, making the two-point assumption conservative and potentially understating actual costs. Conversely, institutional participants with direct market access can execute at substantially lower costs, and signals that are unprofitable at two-point friction may be profitable at sub-half-point friction. 

The dataset covers 2021–2025 and does not include the 2018–2020 period or earlier. Market microstructure and participant composition in MNQ have changed over time, particularly with the growth of retail options and the proliferation of systematic strategies. Results may not generalize to earlier or later periods. 

Tick data was not available for this study. All signals are constructed from five-minute OHLCV bars. True order flow classification (bid-initiated versus ask-initiated volume) requires tick-level data. It is possible—and the positive controls suggest it is likely—that tick data would reveal directional information that five-minute aggregation destroys. 

The study tests one instrument (MNQ) as the primary subject. While cross-instrument comparison using MGC is included, the generalizability of the gross edge ceiling finding to other futures instruments (crude oil, treasury bonds, currency futures) is an open question. 

## 7.2 Extensions

The most direct extension of this work is to apply the same falsification framework to tick-level data. The positive control signals suggest that regime-level structure at multi-bar resolution contains exploitable information. It is plausible that order flow imbalance at tick resolution contains bar-level directional information that OHLCV aggregation destroys. Databento provides MNQ tick data at approximately $42 per quarter, making this extension feasible at modest cost. 

The gap continuation short signal (T = 3.23, N = 22) is a specific candidate for further investigation. If the underlying mechanism—gap-down days with high Kalman velocity tend to continue downward within the RTH session—is structural rather than a small-sample artifact, a larger dataset (including pre-2021 data) would provide sufficient trade count to validate or reject it definitively. 

The VVG classifier identifies days with distinct behavioral characteristics but fails to produce a tradable directional edge at entry resolutions tested. A natural extension is to investigate whether the classifier has value as a volatility predictor rather than a directional predictor: if classifier-positive days reliably show higher realized variance, a volatility strategy (long straddle or equivalent) might be more appropriate than a directional entry. 

## 8. Conclusion

This paper has documented a systematic falsification study of fourteen OHLCV-based intraday momentum signal families on MNQ futures. No signal survived the combined criteria of $\mathrm { T } \geq 2 . 0$ out-of-sample, ≥ 30 trades, positive net return after friction, and multi-year consistency. The consistent finding across all signal families is a gross edge ceiling of approximately 0.07 to 1.50 points at five-minute bar resolution—insufficient to clear a two-point round-trip friction cost. 

This result is not presented as a proof that no intraday edge exists in MNQ. The two positive control signals demonstrate that edge above the ceiling is achievable through regime classification and multi-bar hold structures. Rather, this result establishes a specific, empirically documented claim: single-bar directional signals derived from publicly observable OHLCV features do not generate economically significant edge at five-minute resolution on this instrument under realistic execution assumptions. 

The contribution of this work is methodological as much as empirical. The falsification framework—pre-specified criteria, walk-forward validation, systematic negative result documentation, and positive control inclusion—is reproducible and applicable to any intraday signal research program. The consistent finding that retail OHLCV patterns fail under these standards supports the hypothesis that liquid equity index futures markets efficiently arbitrage publicly observable price and volume patterns, and that genuine intraday edge in these markets requires either proprietary data, structural regime detection, or execution advantages unavailable to retail participants. 

## References



Gao, L., Han, Y., Li, S. Z., & Zhou, G. (2018). Market intraday momentum. Journal of Financial Economics, 129(2), 394–414. 





Heston, S. L., Korajczyk, R. A., & Sadka, R. (2010). Intraday patterns in the cross-section of stock returns. Journal of Finance, 65(4), 1369–1407. 





Easley, D., Lopez de Prado, M. M., & O’Hara, M. (2012). Flow toxicity and liquidity in a high-frequency world. Review of Financial Studies, 25(5), 1457–1493. 





Wen, F., Gong, X., Ma, C., & Xu, Y. (2019). Intraday momentum and return predictability: Evidence from the crude oil market. Economic Modelling, 78, 128–136. 





Lopez de Prado, M. (2018). Advances in Financial Machine Learning. Wiley. 



Bailey, D. H., Borwein, J., Lopez de Prado, M., & Zhu, Q. J. (2014). The deflated Sharpe ratio: Correcting for selection bias, backtest overfitting, and non-normality. Journal of Portfolio Management, 40(5), 94–107. 

Shi, Y., et al. (2025). Kronos: A Foundation Model for Candlestick Financial Data. AAAI 2026. arXiv preprint. 

Martins, A. (2025). Volume-driven time-of-day effects in intraday volatility models. Working paper. 

## AI disclosure statement.

AI tools were used for editorial assistance, formatting support, and code/debugging workflow support. The author is responsible for the research design, interpretation, conclusions, and final manuscript. 

## Appendix A: Decision Log Summary

All research decisions in this project were assigned D-numbers and logged before results were interpreted. The following table summarizes key locked decisions relevant to this paper. 

<table><tr><td>Decision ID</td><td>Decision</td><td>Status</td></tr><tr><td>D001</td><td>MNQ 5-min bar resolution selected as primary research unit</td><td>LOCKED</td></tr><tr><td>D023</td><td>Short confluence signal permanently rejected</td><td>LOCKED</td></tr><tr><td>D026</td><td>25-point pullback entry as execution layer for Confluence Signal</td><td>LOCKED</td></tr><tr><td>D041</td><td>Bar 13 time-based exit confirmed as primary exit</td><td>LOCKED</td></tr><tr><td>D100</td><td>MNQ OU mean reversion permanently rejected (Hurst 0.59, trending)</td><td>LOCKED</td></tr><tr><td>D101</td><td>MNQ is momentum-dominant at 5-minute resolution</td><td>LOCKED</td></tr><tr><td>D105</td><td>MGC intraday research closed – all approaches exhausted</td><td>LOCKED</td></tr><tr><td>D127</td><td>MNQ post-news drift permanently rejected</td><td>LOCKED</td></tr><tr><td>D130</td><td>London ORB continuation rejected (T = 0.176)</td><td>LOCKED</td></tr><tr><td>D179</td><td>Structural gross edge ceiling confirmed at 5-min OHLCV resolution</td><td>LOCKED</td></tr><tr><td>D213</td><td>Direction prediction from OHLCV at 5-min resolution largely exhausted</td><td>LOCKED</td></tr></table>


Table A1. Selected locked decisions from the project decision ledger. 
