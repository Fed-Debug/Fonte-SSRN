# The Price of a Funded Account: An Actuarial Analysis of Proprietary Trading Firm Challenges

Boon Chuan Lim 

Independent Researcher, Singapore 

ORCID: 0009-0005-8477-9393 

boonchuan@singapore.to 

This version: 25 July 2026 (revised) 

## Abstract

Retail proprietary trading firms sell evaluation contracts ("challenges"): a buyer pays a fee to trade a simulated account and share in future simulated profits, without disclosure of the probabilities that determine the contract's value. I price the standard two-step challenge as a contingent claim. Trader equity follows arithmetic Brownian motion; the challenge is a first-passage problem priced by Monte Carlo simulation, including funded-stage profit sweeps and the customary fee refund. Three findings emerge. The apparently symmetric rules embed a large time-limit edge: a zero-edge trader passes the frictionless benchmark with probability 0.50 but the baseline contract with probability 0.30. Contract value concentrates on a narrow risk-sizing ridge near 2 per cent daily volatility, which the product's marketing never discloses. Under an illustrative baseline population with transaction cost drag, the model-implied average value of a USD 500 challenge is USD 221, implying a 56 per cent gross margin for the firm, with 7.5 per cent of simulated buyers reaching funded status. I propose standardised disclosure, comprising a cohort funnel, a payout ratio and a conditional median payout, modelled on CFD loss-rate and gaming-machine return-to-player regimes. 

Keywords: proprietary trading firms; funded trader programmes; first-passage problems; consumer financial protection; disclosure regulation 

JEL classification: G13, G28, G41, D18 

## 1. Introduction

A retail proprietary trading firm sells a product that did not exist fifteen years ago. The buyer pays a fee, typically between USD 50 and USD 700. In exchange, the buyer trades a demonstration account with simulated capital of USD 10,000 to USD 200,000. If the buyer hits a profit target without breaching loss limits, the firm grants a funded account. In many current programmes the funded account is also simulated, and the firm pays the buyer a share, typically 80 per cent, of the simulated profits in real money; for example, the largest firm publicly confirms that its flagship two-step product uses fictitious capital throughout, imposes no time limit, pays an 80 to 90 per cent split and refunds the fee with the first reward (FTMO, n.d.). Section 2 discusses the heterogeneity in how firms back these payouts. 

The sector has grown quickly and sits in a regulatory gap. The product is not brokerage in the conventional sense, because customer orders need not reach any market. It is not obviously gambling under most statutes, because the outcome depends on skill exercised over weeks. Several European regulators, including Belgium's FSMA and Italy's Consob, have published warnings since 2024 (FSMA, 2024; Consob, 2024), and the classification question remains open in most jurisdictions. 

This paper asks a simple question. What is a challenge actually worth to the person who buys it? The question matters for consumer protection. A buyer can observe the fee, the account size, the profit split and the rules. A buyer cannot observe the probability of passing, the expected life of a funded account or the expected sum of payouts. Firms do not publish these quantities in any standardised form, and the figures that some firms do publish use heterogeneous denominators that prevent comparison across products. The contract is therefore a probability-opaque contingent claim sold at a posted price. 

I price the claim. The structure maps naturally onto a first-passage problem. The profit target is an upper absorbing barrier. The overall loss limit is a lower absorbing barrier. The daily loss rule is a constraint on single-period increments. The time limit is a finite maturity. The funded stage is a sequence of contingent reward claims: positive simulated balances are settled in cash at periodic payout dates, while negative simulated balances reduce or terminate the trader's entitlement. I solve the frictionless benchmark in closed form and price the full contract, including the customary refund of the fee at the first payout, by Monte Carlo simulation across a grid of trader skill and risk sizing. The baseline contract is a stylised fixed-maturity archetype based on the classic two-step design; because several large programmes have since removed time limits, I price the no-time-limit variant throughout. 

Three findings organise the paper. First, the rules that look symmetric are not. A challenge with a +10 per cent target and a -10 per cent overall loss limit gives a zero-edge trader a 50 per cent pass probability in the frictionless benchmark. Adding the classic 30-day time limit and the 5 per cent daily loss rule cuts this to 29.8 per cent, and the time limit accounts for most of the wedge. 

Second, contract value is concentrated on a narrow ridge of risk sizing. Because funded-stage profits are swept at each payout date while accumulated simulated losses terminate the claim, a trader with zero net edge who sizes risk at 2 per cent daily volatility holds a contract with a model fair value of roughly USD 1,500 against a USD 500 fee. The same trader at 0.5 per cent daily volatility holds a contract worth almost nothing, because passing within the time limit is nearly impossible. The value surface is a ridge, and nothing in the product's marketing tells the buyer the ridge exists. 

Third, under the baseline population calibration the posted fee sits well above the model-implied average value. Transaction costs that consume 10 per cent of daily volatility translate into an annualised Sharpe drag of 1.59. Under a gross skill distribution centred at zero with this drag, the model-implied average value of a USD 500 challenge is USD 221 including the fee refund, the implied gross margin is 56 per cent, and 7.5 per cent of simulated buyers ever reach funded status. These are model outputs under stated assumptions, not estimates from challenge-account data; Section 6.4 reports their sensitivity to the population assumptions, and only under the low-cost calibration (k = 0.05) does the average value approach the posted fee. 

The findings support a specific regulatory position. The product need not be banned. But it is sold today with less quantitative disclosure than products regulators already treat as requiring standardised probability disclosure, such as CFDs in the European Union. Standardised disclosure of pass rates, payout ratios and a cohort funnel would let buyers price what they are purchasing. Section 7 develops this argument. 

The paper proceeds as follows. Section 2 describes the institutional setting. Section 3 relates the paper to the literature. Section 4 sets out the model. Section 5 describes calibration and simulation design. 

Section 6 presents results. Section 7 discusses regulatory implications. Section 8 states limitations. Section 9 concludes. 

## 2. Institutional background

The classic product is a two-step challenge on a nominal USD 100,000 account. Step one requires a profit of 10 per cent. Step two requires a further 5 per cent. Both steps impose a maximum daily loss of 5 per cent and a maximum overall loss of 10 per cent, measured from the initial balance. The classic design imposed time limits of roughly 30 days for step one and 60 for step two; large programmes, including the largest firm's current flagship, have since removed time limits, typically at a higher fee, and one-step products with tighter or trailing loss limits also exist (FTMO, n.d.). Loss monitoring also varies: some programmes evaluate equity intraday, including floating profit and loss, commissions and swaps, so that a limit can be breached at any moment rather than only at the daily close. 

On passing both steps, the buyer receives a funded account. The business models behind funded accounts are heterogeneous and imperfectly disclosed. Many modern evaluation firms operate simulated customer-facing accounts throughout. Some firms state that they may copy selected traders' data into live proprietary trading, and some programmes progress a subset of traders to live accounts. The funding mix behind trader payouts is generally not publicly disclosed. What is common across programmes is the contractual structure: the trader keeps a profit share, typically 80 per cent, paid at intervals of roughly two to four weeks; at each payout the profits are withdrawn and the balance resets to the initial level; a breach of either loss limit terminates the account; and many firms refund the challenge fee with the first payout. Many firms also apply consistency rules, which cap the share of profit earned on the best day, and reserve discretion to deny payouts for prohibited strategies. 

Regulators have begun to react. Belgium's FSMA warned on 7 March 2024 that challenge products amount to a "shadow investment game", and stressed that the firms hold no authorisation and are not permitted to provide investment services (FSMA, 2024). Italy's Consob followed on 8 July 2024, likening the products to online trading video games and citing user complaints about tests contrived to induce repurchase and about profit splits that were never paid (Consob, 2024). The most legally developed national position is the Czech National Bank's 2023 regulatory opinion, which distinguishes pure demo trading from reward-linked and trade-mirroring arrangements. It states that simulated trading without actual order execution or settlement generally does not constitute an investment service, while expressly excluding copy-trading models from the opinion's scope; critically, it further observes that where a user becomes entitled to a reward whose amount depends on demo-account trading results, the arrangement may require assessment under the legal framework applicable to financial derivatives (CNB, 2023). The reward-linked arrangement in that carve-out is exactly the contract priced in this paper. The Czech position therefore illustrates, rather than resolves, the regulatory-perimeter uncertainty, and the bank's subsequent public comments confirmed that the classification of funded-trader models remains open (Finance Magnates, 2024). Whatever the eventual perimeter outcome, no jurisdiction has yet imposed a disclosure regime, which is the gap this paper addresses. 

Table 1 summarises the baseline contract priced in this paper. It is a stylised fixed-maturity archetype: the parameters sit within the range offered by the largest firms' classic products, but no named firm's current rules are reproduced exactly, and monitoring is at daily closes rather than intraday. The no-timelimit variant replaces the step maturities with a long horizon. The simulation code allows any variant to be repriced. 


Table 1. Baseline challenge contract (stylised archetype)


<table><tr><td>Parameter</td><td>Value</td></tr><tr><td>Nominal account size</td><td>USD 100,000</td></tr><tr><td>Challenge fee</td><td>USD 500, refunded at first payout</td></tr><tr><td>Step 1 profit target</td><td>+10%</td></tr><tr><td>Step 2 profit target</td><td>+5%</td></tr><tr><td>Maximum daily loss</td><td>5% of initial balance</td></tr><tr><td>Maximum overall loss</td><td>10% of initial balance</td></tr><tr><td>Step 1 time limit</td><td>30 trading days (variant: none)</td></tr><tr><td>Step 2 time limit</td><td>60 trading days (variant: none)</td></tr><tr><td>Profit split (funded)</td><td>80% to trader</td></tr><tr><td>Payout interval (funded)</td><td>20 trading days, balance resets</td></tr><tr><td>Funded horizon modelled</td><td>250 trading days</td></tr><tr><td>Monitoring</td><td>Daily closes</td></tr></table>


Notes: Loss limits are static, measured from the initial balance, and checked on daily closes. The funded balance resets to the initial level after each profit sweep. The no-time-limit variant caps each step at 300 trading days for computational purposes. Source(s): Author's compilation from publicly available programme rules. 


## 3. Related literature

The paper draws on three strands. The first is the literature on retail trading performance. Barber and Odean (2000) show that active retail traders underperform after costs. Barber et al. (2014) find that fewer than 1 per cent of day traders in Taiwan earn reliably positive abnormal returns net of fees, and that the cross-section of skill is wide. These facts motivate, without pinning down, the calibration in Section 5: the population there is an illustrative baseline consistent with poor average net performance, not an estimate for challenge purchasers, whose skill distribution is unobserved. Kumar (2009) and Gao and Lin (2015) document the gambling motive in conventional retail trading, and Grinblatt and Keloharju (2009) link trading activity to sensation seeking; whether challenge purchasers share this behavioural profile is plausible but not established. 

The second strand is tournament theory. Brown, Harlow and Starks (1996) show that interim losers in mutual fund tournaments increase risk because compensation is convex in rank. A challenge is a tournament against a barrier rather than against other players, but the convexity is the same: the buyer's payoff is an option on performance, and option holders want volatility, subject to the knockout barriers that punish it. The tension between these forces produces the interior optimum in risk sizing that Section 6 documents. 

The third strand is the regulation of retail speculative products. Heimer and Simsek (2019) evaluate leverage limits for retail foreign exchange traders and find that the limits reduced losses without large offsetting harms. The European Securities and Markets Authority restricted contracts for difference in 2018 and required each provider to disclose the percentage of retail accounts that lose money (ESMA, 

2018). That regime is the closest existing template for the disclosure standard proposed here. The first-passage mathematics is textbook material; see Karatzas and Shreve (1991). 

## 4. Model

## 4.1 Equity dynamics

I measure trader performance in units of the initial account balance. Daily equity increments are independent normal draws; cumulative performance is their running sum. Arithmetic rather than geometric dynamics match the contracts, whose targets and limits are fixed percentages of the initial balance. Skill is parameterised by the annualised Sharpe ratio s, so that 

$$
r _ {t} \sim \mathrm{N} (\mu , \sigma^ {2}), \quad \mu = \mathrm{s} \sigma / \sqrt {2 5 2}.
$$

Skill and risk sizing are thereby separately interpretable: s is the quality of the signal net of costs, and sigma is how aggressively the trader expresses it. 

## 4.2 The contract as a first-passage problem

Step one ends at the first of four events: cumulative return reaches the target a (pass); cumulative return reaches -b (fail); a single daily increment is less than or equal to -d (fail); or the maturity T expires (fail). Equality with a barrier counts as the event occurring; the daily rule is evaluated before the cumulative barriers within a day, and a path cannot both pass and fail on the same day under this ordering. Step two is identical with its own target and horizon, simulated on independent paths. 

The funded stage applies the same loss rules with no target. Let $X(t)$ denote cumulative simulated profit since the last reset and let $t(1)$ , $t(2)$ , ... be payout dates spaced 20 trading days apart. At each payout date the trader receives 

$$
V _ {k} = \varphi \cdot \max (\mathrm{X} (t _ {k}), 0), \quad \varphi = 0. 8 0,
$$

and X resets to zero if the sweep occurs; between payout dates a breach of either loss limit, still measured from the initial balance, terminates the account. If the contract refunds the fee, the refund is paid with the first sweep. The stage ends at a breach or at the modelled horizon of 250 trading days. 

Without the daily rule and the time limit, the pass probability has a closed form. For drift mu and volatility sigma, define theta = 2 mu / sigma-squared. The probability of reaching +a before -b is 

$$
\mathrm{P} = \left(1 - \mathrm{e} ^ {\theta \mathrm{b}}\right) / \left(\mathrm{e} ^ {- \theta \mathrm{a}} - \mathrm{e} ^ {\theta \mathrm{b}}\right), \quad \theta = 2 \mu / \sigma^ {2},
$$

which reduces to $b / (a + b)$ at mu = 0. For a = b = 0.10, a zero-edge trader passes the frictionless step one with probability exactly one half. This benchmark uses continuously monitored barriers, whereas the simulation monitors daily closes; the two coincide only in the limit of fine monitoring, and the daily-close convention is stated as part of the contract being priced. A programme that monitors equity intraday would count paths that breach and recover within a day as failures, so all pass probabilities and contract values reported here are upper bounds relative to intraday-monitored programmes. 

## 4.3 What the model deliberately omits

The model omits consistency rules, payout caps and discretionary payout denials. Each is a friction that transfers value from trader to firm, so their omission biases the estimated contract value upward and the implied firm margin downward. The model prices the fee refund explicitly, since omitting it would bias the contract value downward. Traders are mechanical: a trader who adjusts volatility dynamically, for instance reducing risk after building a buffer, may hold a more valuable contract than the constant-volatility trader modelled here, although the interaction with costs and minimum activity rules is not modelled. The estimates should be read as the value of the stated contract to a mechanical trader. 

## 5. Calibration and simulation design

I price the contract on a grid of twelve net Sharpe ratios from -5 to +4 and five daily volatilities from 0.5 per cent to 5 per cent. The no-time-limit variant replaces each step maturity with a computational cap of 300 trading days; paths still alive at the cap are counted as failures, so the variant's value is conservatively understated. Barber and colleagues (2014) imply that sustained net Sharpe ratios above 2 are rare even among the most active day traders; the deep negative values cover the left tail of any population with material cost drag. Daily volatility of 2 per cent implies a daily-limit breach, a one-day return at or below -5 per cent, with probability 0.0062 for a zero-drift trader, roughly once per 160 trading days; 5 per cent daily volatility implies a breach roughly every six days. 

Transaction costs, including spread, commission and slippage on simulated fills, enter as a single drag proportional to volatility: if round-trip costs consume a fraction k of daily volatility each day, the annualised Sharpe drag is k sqrt(252). The base case k = 0.10 gives a drag of 1.59; the sensitivity analysis uses k = 0.05 and k = 0.15. 

For population aggregates I assume an illustrative baseline: gross Sharpe standard normal across buyers, net Sharpe equal to gross minus the drag, and risk sizing distributed across the volatility grid with weights of 5/20/30/25/20 per cent from lowest to highest, reflecting the observation that very low sizing cannot reach the target within the classic time limit. These are assumptions, not estimates from challenge-account data. Population values integrate the grid over two million draws of net Sharpe by linear interpolation between grid rows; draws outside the grid take the nearest end row, and the mass below -5 under the base case is 0.03 per cent, so end clipping is immaterial. Section 6.4 reports sensitivity to the weights and the drag. 

Each configuration uses 200,000 simulated paths per stage with independent paths across stages, generated by NumPy's PCG64 generator with fixed seeds recorded in the replication code. Monte Carlo standard errors on pass probabilities are below 0.12 percentage points; standard errors on funded-stage expected payouts are below 1.5 per cent of the reported values at the configurations discussed in the text. The replication package reproduces every number in the paper. In accordance with the publisher's policy on large language models, I document that Claude (Anthropic) was used in developing the simulation code and in drafting the manuscript; all modelling choices, results, citations and text were reviewed, verified and edited by the author, who takes full responsibility for them. 

## 6. Results

## 6.1 Decomposing the edge in the rules

Table 2 starts from the frictionless benchmark and adds the rules one at a time, for a zero-edge trader and for a trader with net Sharpe of 2, both at 2 per cent daily volatility. The frictionless pass probabilities are 0.500 and 0.779. The daily loss rule alone costs the zero-edge trader 4.7 percentage points. The 30-day maturity alone costs 19.0 points. Both together give 0.298. The maturity is responsible for the large majority of the wedge between the advertised symmetry and the actual odds, and a contract that keeps the daily rule but removes the maturity restores the pass probability to 0.453. 


Table 2. Step 1 pass probability as rules are added (2% daily volatility)


<table><tr><td>Rule set</td><td>Net Sharpe 0</td><td>Net Sharpe +2</td></tr><tr><td>Barriers only (closed form)</td><td>0.500</td><td>0.779</td></tr><tr><td>+ daily loss rule only</td><td>0.453</td><td>0.744</td></tr><tr><td>+ 30-day maturity only</td><td>0.310</td><td>0.550</td></tr><tr><td>+ both (baseline contract)</td><td>0.298</td><td>0.532</td></tr><tr><td>+ daily rule, no maturity</td><td>0.453</td><td>0.744</td></tr></table>


Notes: Probability of reaching the +10% target before the -10% overall loss limit under the rule set shown, monitored at daily closes. The closed form is the continuously monitored two-barrier first-passage probability. Simulated rows use 200,000 paths; standard errors are below 0.0012. Source(s): Author's calculations. 


## 6.2 Pass probabilities across skill and risk sizing

Table 3 reports the probability of completing both steps, and Figure 1 plots it. Skill matters, but risk sizing matters at least as much. A trader with net Sharpe of +1 who sizes at 0.5 per cent daily volatility funds with probability below 0.001, because the expected path cannot reach 10 per cent within 30 days. The same trader at 2 per cent volatility funds with probability 0.298, while a trader with net Sharpe of -1 at 2 per cent volatility funds with probability 0.100. The contract cannot distinguish a modestly skilled cautious trader from an unskilled aggressive one; if anything it favours the latter. As a selection device for skill, which is the sector's stated purpose, the classic challenge is weak. 


Table 3. Probability of reaching funded status, by net Sharpe and daily volatility


<table><tr><td>Net Sharpe</td><td>0.5%</td><td>1%</td><td>2%</td><td>3%</td><td>5%</td></tr><tr><td>-3.0</td><td>&lt;0.001</td><td>0.001</td><td>0.022</td><td>0.046</td><td>0.070</td></tr><tr><td>-2.0</td><td>&lt;0.001</td><td>0.002</td><td>0.049</td><td>0.078</td><td>0.096</td></tr><tr><td>-1.0</td><td>&lt;0.001</td><td>0.008</td><td>0.100</td><td>0.128</td><td>0.130</td></tr><tr><td>-0.5</td><td>&lt;0.001</td><td>0.015</td><td>0.137</td><td>0.160</td><td>0.149</td></tr><tr><td>0.0</td><td>&lt;0.001</td><td>0.026</td><td>0.184</td><td>0.195</td><td>0.172</td></tr><tr><td>+0.5</td><td>&lt;0.001</td><td>0.041</td><td>0.237</td><td>0.234</td><td>0.195</td></tr><tr><td>+1.0</td><td>&lt;0.001</td><td>0.066</td><td>0.298</td><td>0.278</td><td>0.220</td></tr><tr><td>+2.0</td><td>0.001</td><td>0.135</td><td>0.434</td><td>0.375</td><td>0.275</td></tr><tr><td>+3.0</td><td>0.004</td><td>0.241</td><td>0.576</td><td>0.471</td><td>0.334</td></tr></table>


Notes: Product of Step 1 and Step 2 pass probabilities under the baseline contract of Table 1; 200,000 paths per step. Entries shown as <0.001 had fewer than 200 passing paths; the 95% upper confidence bound for a cell with zero passes is 1.8e-5. The full grid from net Sharpe -5 to +4 is in the replication package. Source(s): Author's calculations. 


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-27/89929a6c-eaa2-4ba2-8ff6-51f4b085fe09/2c61f419bc8ea79e1cd8e39c30b20e4bf0c0f327b2c520b4f825a0fd4877b3a5.jpg)



Figure 1. Probability of reaching funded status by daily volatility and net annualised Sharpe ratio. The interior maximum near 2-3 per cent reflects the tension between the maturity, which punishes low volatility, and the loss limits, which punish high volatility. Source(s): Author's calculations.


## 6.3 Contract value and the volatility ridge

Table 4 reports the fair fee of the refundable contract, defined as the fee F at which the buyer's expected value is zero: F equals the funding probability times expected funded-stage payouts, divided by one minus the funding probability times the probability of a first payout, the divisor reflecting that the fee itself is returned at the first payout. Figure 2 plots the expected value net of the posted USD 500 fee, refund included. The divisor has a simple intuition: the refund makes the fee partly self-cancelling. Raising the fee raises the refund a successful buyer expects to recover, so a fraction of any fee increase, equal to the probability of funding times the probability of a first payout given funding, flows straight back to the buyer; only the remainder is a true cost, and the fair fee is the fixed point of that recursion. For a zero-edge trader at 2 per cent daily volatility, expected funded-stage payouts conditional on funding are roughly USD 7,300, the probability of at least one payout conditional on funding is 0.56, and the fair fee is USD 1,502. 


Table 4. Fair fee of the refundable contract in USD, by net Sharpe and daily volatility


<table><tr><td>Net Sharpe</td><td>0.5%</td><td>1%</td><td>2%</td><td>3%</td><td>5%</td></tr><tr><td>-3.0</td><td>0</td><td>0</td><td>24</td><td>33</td><td>9</td></tr><tr><td>-2.0</td><td>0</td><td>3</td><td>102</td><td>100</td><td>24</td></tr><tr><td>-1.0</td><td>0</td><td>27</td><td>404</td><td>280</td><td>58</td></tr><tr><td>-0.5</td><td>0</td><td>72</td><td>783</td><td>457</td><td>85</td></tr><tr><td>0.0</td><td>0</td><td>183</td><td>1,502</td><td>728</td><td>127</td></tr><tr><td>+0.5</td><td>1</td><td>432</td><td>2,790</td><td>1,143</td><td>184</td></tr><tr><td>+1.0</td><td>2</td><td>979</td><td>5,058</td><td>1,730</td><td>263</td></tr><tr><td>+2.0</td><td>13</td><td>3,746</td><td>15,826</td><td>3,865</td><td>534</td></tr><tr><td>+3.0</td><td>68</td><td>11,324</td><td>44,874</td><td>7,955</td><td>1,005</td></tr></table>


Notes: Fair fee F solves $F = P(\text{funded}) \times [E(\text{payouts}) + P(\text{first payout} \mid \text{funded}) \times F]$ . USD 100,000 account, 80 per cent split, 250-day funded horizon. The posted fee in the baseline contract is USD 500. Source(s): Author's calculations.


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-27/89929a6c-eaa2-4ba2-8ff6-51f4b085fe09/a7d51b8b929d2758edbf0ec63704e21b63d6c94dd6d05766a4450a74751fe977.jpg)



Figure 2. Expected value of the refundable challenge net of the USD 500 fee. The vertical axis uses a symmetric log scale: values are linear between -1,000 and +1,000 USD and logarithmic beyond, so that large positive values and bounded losses can share one panel. Value concentrates on a narrow ridge around 2 per cent daily volatility. Source(s): Author's calculations.


The striking feature is the narrowness of the ridge. At 2 per cent daily volatility the breakeven net Sharpe at the posted fee is approximately -0.87: even moderately unskilled traders hold positive-value contracts if they size correctly. At 1 per cent volatility the breakeven rises to +0.56, at 5 per cent to +1.94, and at 0.5 per cent no skill level on the grid breaks even. The contract's value is therefore less a reward for forecasting skill than a reward for solving a risk-sizing problem that the firm never states. The implication deserves explicit statement: on the ridge, the contract forgives skill deficits of nearly one Sharpe unit, so the firm's margin derives less from buyers holding negative skill than from two other channels, the transaction cost drag that shifts the whole population leftward and, above all, buyers sizing risk away from the ridge. A population of zero-net-skill buyers who all sized at 2 per cent daily volatility would face a posted fee below fair value; the same buyers at 0.5 or 5 per cent volatility supply most of the margin. Figure 3 shows why the ridge exists: at low volatility the dominant failure mode is timing out, and at high volatility it is breaching the loss rules. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-27/89929a6c-eaa2-4ba2-8ff6-51f4b085fe09/3bfd43567aaf53abb5b655417f260ac28140e23a84eb5b2adb20d67ffec3584f.jpg)



Figure 3. Decomposition of Step 1 outcomes for a zero-edge trader. Bars are distinguished by both colour and fill pattern. Low volatility fails by timeout; high volatility fails by breaching the daily and overall loss limits. Source(s): Author's calculations.


## 6.4 Population aggregates and sensitivity

Table 5 aggregates the grid over the illustrative baseline population of Section 5, integrating over the full net-Sharpe distribution from the extended grid. Under the base case, the model-implied average value of the refundable contract is USD 221 against the posted USD 500, an implied gross margin of USD 279 or 56 per cent before operating costs, and 7.5 per cent of simulated buyers reach funded status. Removing the cost drag raises the average value to USD 1,098 and the funding rate to 15.3 per cent, so the posted fee would be below fair value for a cost-free population; the margin in the base case is generated by the cost drag and by buyers positioned off the volatility ridge, not primarily by the barriers. The no-time-limit variant is worth USD 369 on average with a 10.5 per cent funding rate: removing maturities closes approximately 56 per cent of the gap between the classic contract's model-implied value and the posted fee, both measured without the refund. Both variants are priced against the same USD 500 posted fee for comparability; in practice no-time-limit products are sold at premiums to their fixed-maturity counterparts, and since the implied margin at any posted fee is that fee less the reported average value, the observed premium pricing is qualitatively consistent with the variant's higher model value. The 250-day funded horizon is immaterial at the population level: truncation approaches 8 per cent of contract value only above net Sharpe +2, and the mass there under the baseline calibration is below 0.02 per cent. 


Table 5. Population aggregates (illustrative baseline calibration)


<table><tr><td>Quantity</td><td>Value</td></tr><tr><td>Average value, refundable classic contract</td><td>USD 221</td></tr><tr><td>Average value, non-refundable classic contract</td><td>USD 203</td></tr><tr><td>Average value, refund omitted from a refundable contract</td><td>understated by USD 18</td></tr><tr><td>Average value, no-time-limit variant (non-refundable)</td><td>USD 369</td></tr><tr><td>Average value, no cost drag (classic)</td><td>USD 1,098</td></tr><tr><td>Posted fee</td><td>USD 500</td></tr><tr><td>Implied gross margin (refundable classic)</td><td>USD 279 (56%)</td></tr><tr><td>P(funded), classic / no-time-limit</td><td>7.5% / 10.5%</td></tr><tr><td>Breakeven net Sharpe at 2% / 5% volatility</td><td>-0.87 / +1.94</td></tr></table>


Notes: Gross Sharpe standard normal; cost drag 1.59 (k = 0.10); volatility weights 5/20/30/25/20 per cent. Aggregates integrate two million net-Sharpe draws over the grid from -5 to +4 by linear interpolation; mass outside the grid (0.03 per cent) takes the end rows. Source(s): Author's calculations. 


Table 6 varies the two population assumptions that matter most. The implied average value ranges from USD 60 under a conservative-sizing population with high costs to USD 557 under the base weights with low costs. The posted fee exceeds the model-implied average value in eight of nine scenarios; only when trading costs are at the low end (k = 0.05) does average value approach or exceed USD 500. The qualitative conclusion, that the product's value is opaque, highly sensitive to risk sizing, and below the posted price for populations with realistic cost drag, survives every scenario, but the specific margin figure should be read as calibration-dependent. 


Table 6. Sensitivity of the population average value (refundable contract, USD)


<table><tr><td>Volatility weighting</td><td>k = 0.05</td><td>k = 0.10</td><td>k = 0.15</td></tr><tr><td>Conservative (20/40/25/10/5)</td><td>441</td><td>163</td><td>60</td></tr><tr><td>Base (5/20/30/25/20)</td><td>557</td><td>221</td><td>87</td></tr></table>

Aggressive (0/10/25/30/35) 517 213 87 

Notes: k is the share of daily volatility consumed by round-trip costs; the implied annualised Sharpe drag is 0.79, 1.59 and 2.38 respectively. Weights are over daily volatilities of 0.5/1/2/3/5 per cent. Source(s): Author's calculations. 

## 7. Regulatory implications

The pricing results feed a classification question that this section can frame but not settle. At least four legal characterisations are available for a challenge contract: a financial instrument or derivative; an investment or ancillary service; a consumer-services or digital-content contract; or a gambling, prize-competition or mixed skill-and-chance product. Which characterisation applies in a given jurisdiction turns on identifiable features: whether customer orders reach a market; whether the firm copies customer trades into live positions; whether the reward is contractually calculated from simulated performance; the firm's discretion to deny rewards; whether the customer risks only the fee; whether skill materially influences outcomes; whether the firm is economic counterparty to the customer's simulated positions; and the territorial scope of marketing. The model in this paper speaks to one of these features directly: skill does materially influence outcomes, moving the funding probability by an order of magnitude across the grid, but so does risk sizing, and for populations with realistic costs the modal buyer's prospects resemble those of a lottery participant. Skill-sensitivity therefore does not by itself settle the gambling question, since many regimes regulate mixed skill-and-chance products, and nothing in the actuarial analysis addresses the separate questions of misrepresentation or contractual performance that fraud law asks. 

Whatever the eventual classification, the product is sold today with materially less quantitative disclosure than comparable regulated products. A CFD provider in the European Union must disclose the percentage of its retail accounts that lose money, calculated on a specified basis (ESMA, 2018). Gaming machines in Great Britain must display either the proportion of amounts staked that is returned as prizes or the odds of winning, a requirement under section 240 of the Gambling Act 2005 typically met by a percentage return-to-player statement; notably, Great Britain imposes no statutory minimum return, so the machine regime is one of pure disclosure (Gambling Commission, 2020), which is precisely the form of intervention proposed here. Challenge firms are not required to disclose pass rates or payout ratios on a standardised and comparable basis, even though both are quantities a firm can compute exactly from its own records. The information asymmetry is stark: the firm knows the empirical distribution over every quantity in this paper, and the buyer knows none of them. The figures some firms volunteer are not comparable across firms because the denominators differ: purchased accounts, attempts, unique customers and account phases all appear in published statistics. 

The natural remedy is disclosure rather than prohibition, and the CFD regime shows the machinery exists. I propose that firms be required to publish, per product and rule version, per quarter, with a defined observation window and treatment of right-censored accounts: (i) a cohort funnel from purchased challenges through step-one passes, step-two passes, first payout and repeat payout, with purchased challenges as the fixed denominator and resets counted as new purchases; (ii) the ratio of total payouts to total fee revenue, stating whether refunded fees are counted as payouts or netted from fee revenue, and separating promotional or related-party payouts; and (iii) the median payout conditional on any payout, gross and net of refunds. A fourth, softer measure follows from the ridge result: firms should be required to state that the probability of passing depends strongly on risk sizing, as leverage warnings are required for CFDs. Inaccurate reporting should carry the same consequences as inaccurate financial promotion. Three implementation details deserve specification. Right-censoring: active accounts at the window close should be handled by reporting the funnel on cohorts purchased at least 180 days before the close, alongside an all-cohorts figure, so that a firm cannot flatter its funnel by front-loading sales into the censored tail. Level of disclosure: reporting must be per product and rule version rather than firm-wide, because firm-level aggregates would let a firm blend a harsh legacy product with a generous flagship; firm-level figures may be published in addition but not in substitution. Enforcement: in jurisdictions without a bespoke regime, misstated figures already fall within the reach of misleading financial promotion and unfair commercial practice law, and periodic assurance of the published figures by an independent reviewer could be made a condition of marketing to residents. ESMA's statement of 24 February 2026 on derivatives marketed as perpetual futures establishes that the commercial name of a product is irrelevant to its regulatory treatment, which follows from economic substance (ESMA, 2026); applying that reasoning to evaluation contracts is this paper's analogy rather than any determination by ESMA, but the principle is the right one. The substance of a challenge is a fee paid for a probability-weighted claim on future payments, and disclosure obligations appropriate to such claims should not be avoidable by calling the product an evaluation. 

## 8. Limitations

Six limitations qualify the estimates. First, returns are normal and independent. A robustness run with Student-t innovations with four degrees of freedom, scaled to the same volatility, lowers the step-one pass probability at 2 per cent volatility from 0.298 to 0.273 for a zero-edge trader and from 0.532 to 0.503 at net Sharpe 2, so in this calibration heavier tails reduce contract value modestly; the direction is not general, since heavy tails also raise the probability of large favourable moves, and skewed or jump processes could move values either way. Second, monitoring is at daily closes; intraday equity monitoring, used by some major programmes, can only remove surviving paths, so the reported values are upper bounds in that dimension. Third, traders are mechanical; dynamic risk control may raise contract value, which would widen but not remove the ridge, since the maturity still punishes low average volatility. Fourth, consistency rules, payout caps and discretionary denials are omitted, again making the reported values upper bounds for the trader. Fifth, the funded horizon of 250 trading days is nearly innocuous for unskilled traders, whose expected payouts change by less than 1 per cent between 250 and 500 days, but truncates roughly 8 per cent of value at net Sharpe 2, so the upper tail of Table 4 is understated. Sixth, the population distributions are illustrative assumptions; Tables III and IV allow any alternative population to be repriced by reweighting, and Table 6 shows the range across plausible alternatives. 

## 9. Conclusion

A proprietary trading challenge is a contingent claim with a posted price and hidden probabilities. This paper computes the probabilities for a stylised archetype of the classic two-step contract and its no-time-limit variant. The advertised symmetry of targets and loss limits conceals a maturity edge worth roughly 20 percentage points of pass probability. Contract value is concentrated on a narrow ridge of risk sizing near 2 per cent daily volatility, and nothing in the product's marketing discloses the ridge. Under an illustrative baseline population with transaction cost drag, the model-implied average value of a USD 500 refundable challenge is USD 221, the implied gross margin is 56 per cent, and 7.5 per cent of simulated buyers reach funded status; the qualitative pattern survives wide variation in the population assumptions. None of the corresponding empirical quantities is currently disclosed by firms in any standardised form. The policy proposal is correspondingly narrow: require challenge firms to publish a cohort funnel, a payout ratio with defined refund treatment, and the conditional median payout. Buyers of probability-opaque contracts deserve at least the disclosure standards already applied to CFDs and gaming machines. For consumer policy, the implication is that an effective remedy exists below the threshold of the unresolved classification question: disclosure obligations can attach to the product's economic substance now, whichever perimeter it eventually falls within. For consumer research, the model generates testable predictions, foremost that observed challenge buyers cluster away from the value-maximising risk sizing; cohort data from any firm, or behavioural testing of the proposed disclosures against purchase decisions, would confront the calibration assumed here with evidence. 

## Data availability

The paper uses no proprietary or trader-level dataset. Institutional parameters and regulatory background are drawn from publicly available sources cited in the text. A replication package containing the simulation code and model outputs that generate every table and figure is available from the author. 

## Declaration of interest

The author declares no competing interests. The author has traded retail derivative products and has participated in proprietary trading firm evaluations as a consumer. 

## Disclosure of AI use

During the preparation of this work the author used Claude (Anthropic) to assist with drafting, simulation code development and language editing. The author reviewed and edited all output and takes full responsibility for the content of the publication. 

## References



Barber, B.M. and Odean, T. (2000), "Trading is hazardous to your wealth: the common stock investment performance of individual investors", Journal of Finance, Vol. 55 No. 2, pp. 773-806. doi: 10.1111/0022-1082.00226. 





Barber, B.M., Lee, Y.-T., Liu, Y.-J. and Odean, T. (2014), "The cross-section of speculator skill: evidence from day trading", Journal of Financial Markets, Vol. 18, pp. 1-24. doi: 10.1016/j.finmar.2013.05.006. 





Brown, K.C., Harlow, W.V. and Starks, L.T. (1996), "Of tournaments and temptations: an analysis of managerial incentives in the mutual fund industry", Journal of Finance, Vol. 51 No. 1, pp. 85-110. doi: 10.1111/j.1540-6261.1996.tb05203.x. 





Česká národní banka (2023), "K simulovanému obchodování na demo účtu" [On simulated trading on a demo account], regulatory opinion RS2023-18, 28 September, CNB, Prague, available at: www.cnb.cz/cs/dohled-financni-trh/legislativni-zakladna/stanoviska-k-regulaci-financniho-trhu/RS2023-18 (accessed 25 July 2026). 





Commissione Nazionale per le Società e la Borsa (2024), "Beware of online trading 'video games'", press release, 8 July, Consob, Rome, available at: www.consob.it/documents/1912911/3990887/press_20240708.pdf (accessed 25 July 2026). 





European Securities and Markets Authority (2018), "Decision (EU) 2018/796 of 22 May 2018 to temporarily restrict contracts for differences in the Union in accordance with Article 40 of Regulation (EU) No 600/2014", Official Journal of the European Union, L 136, 1 June, p. 50, available at: eur-lex.europa.eu/eli/dec/2018/796/oj. 





European Securities and Markets Authority (2026), "Statement on identifying derivatives within the scope of the national product intervention measures on CFDs", ESMA35-243228190-8024, 24 February, ESMA, Paris. 





Finance Magnates (2024), "Exclusive: Czech regulator asserts prop trading firms 'may be subject to MiFID'", 10 June, available at: www.financemagnates.com/forex/exclusive-czech-regulator-asserts-prop-trading-firms-may-be-subject-to-mifid/ (accessed 25 July 2026). 





FTMO (n.d.), "How FTMO works", available at: ftmo.com/en/blog/how-ftmo-works/ (accessed 25 July 2026). 





Financial Services and Markets Authority (2024), "The FSMA warns consumers against shadow investment game", warning, 7 March, FSMA, Brussels, available at: www.fsma.be/en/warnings/fsma-warns-consumers-against-shadow-investment-game (accessed 25 July 2026). 





Gambling Commission (2020), "How can gaming machines meet their %RTP if they are random?", Licensing Authority Bulletin, August, Gambling Commission, Birmingham, available at: www.gamblingcommission.gov.uk/authorities/guide/page/la-bulletin-august-2020-feature-article (accessed 25 July 2026). 





Gao, X. and Lin, T.-C. (2015), "Do individual investors treat trading as a fun and exciting gambling activity? Evidence from repeated natural experiments", Review of Financial Studies, Vol. 28 No. 7, pp. 2128-2166. doi: 10.1093/rfs/hhu075. 





Grinblatt, M. and Keloharju, M. (2009), "Sensation seeking, overconfidence, and trading activity", Journal of Finance, Vol. 64 No. 2, pp. 549-578. doi: 10.1111/j.1540-6261.2009.01443.x. 





Heimer, R. and Simsek, A. (2019), "Should retail investors' leverage be limited?", Journal of Financial Economics, Vol. 132 No. 3, pp. 1-21. doi: 10.1016/j.jfineco.2018.10.017. 





Karatzas, I. and Shreve, S.E. (1991), Brownian Motion and Stochastic Calculus, 2nd ed., Springer, New York. doi: 10.1007/978-1-4612-0949-2. 





Kumar, A. (2009), "Who gambles in the stock market?", Journal of Finance, Vol. 64 No. 4, pp. 1889-1933. doi: 10.1111/j.1540-6261.2009.01483.x. 

