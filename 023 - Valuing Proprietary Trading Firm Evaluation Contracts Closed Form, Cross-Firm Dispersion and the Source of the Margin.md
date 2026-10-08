# Valuing proprietary trading firm evaluation contracts: closed form, cross-firm dispersion and the source of the margin

Martí Tomàs Fernández
marti.tomas.fernandez@gmail.com 

August 2026 

## Abstract

The evaluations sold by proprietary trading firms are contracts with a bounded premium, a contingent payoff and termination by an absorbing event defined on the drawdown of the P&L. This paper derives their success probability in closed form as a chain of first-passage problems, with six contractual parameters: profit target, drawdown buffer, the level at which the barrier stops trailing, the frequency at which it is updated, the frequency at which breach is checked, and the daily loss limit. The expression reproduces simulation with an error below 1% within its range of validity, which is stated. 

Applied to thirteen products of the same account size collected from official sources, the success probability varies by 62% across products that advertise identical profit target and drawdown buffer. The variation comes entirely from parameters that the firms publish but not alongside the price, and that no industry comparison records. 

Two criteria assessable from published terms follow from the valuation: the minimum productivity that makes an evaluation worth its price, and a sufficient condition under which it is not worth it to any buyer. Carried into the unit P&L, both converge on a single figure—the break-even conversion rate—which is simultaneously the buyer's viability threshold and the point at which the seller's contribution vanishes. The pass rates the industry publishes lie below it; the one the model predicts, above. The difference implies a drift for the average buyer three to thirty times larger than any plausible execution cost, and places the origin of the margin not in the price of the contract but in the selection the evaluation performs. 

Keywords: drawdown barriers; first passage; discrete monitoring; unit economics; price transparency. 

## 1 Introduction

A proprietary trading firm sells the following contract: the buyer pays a fee, receives a simulated account and must reach a profit target before incurring a given loss measured from the running maximum. If they succeed they gain a funded account from which they receive a fraction of the profits they generate; if they fail, they lose the fee and can retry by paying again. 

The product is discussed almost exclusively in operational terms—which strategy to use, how much to risk—and very rarely in valuation terms. The search carried out for this paper found no peer-reviewed literature on the economic structure of these evaluations, despite this being a market whose only documentary record of size—a complaint against a single firm—lists more than 135,000 customers (CFTC, 2023). The probabilistic treatment of the underlying object, by contrast, is well established: the termination condition is defined on the drawdown of the process, a variable studied by Taylor (1975) and Lehoczky (1977) and characterised in Magdon-Ismail et al. (2004). The closest antecedent is Carr et al. (2011), which prices a digital contract on the event “the drawdown precedes the drawup”, the formal twin of the condition studied here although framed as a hedging instrument. 

This paper takes the view opposite to the industry's: it treats the evaluation as an asset, derives its expected value and determines the thresholds beyond which buying it no longer pays. 

Contributions. First, a parameterised closed form ( $\S2$ ) that covers the three barrier regimes the industry uses as values of a single parameter, incorporates the two monitoring frequencies the contracts distinguish, admits drift and treats the two types of daily limit separately. Its validity conditions are established by simulation and stated, together with the direction of the error outside them. 

Second, the measurement of the dispersion those parameters produce ( $\S4$ ) across thirteen products collected from official sources. 

Third, two decision criteria assessable from published terms ( $\S3$ ): the minimum productivity that makes an evaluation viable, and a sufficient condition of unviability for any buyer. 

Fourth, the decomposition of the seller's unit contribution (§5), which identifies the break-even conversion rate, ranks the margin levers by elasticity and locates the origin of the surplus in selection and not in price. 

Fifth, a methodological invariant ( $\S7$ ) that detects a class of error common to procedures that reweight historical scenarios, with the case that motivated it and its correction. 

## 2 The model

## 2.1 Notation

The split between firm, trader and market parameters is what separates what the model says about any contract from what only describes one particular buyer. Every firm parameter is verifiable in its published terms; none of the trader's is. 

## 2.2 The contract as a chain of phases

An evaluation contract is not a single right but a sequence of rights. The buyer passes an evaluation, trades a simulated funded account, and in some products then gains access to a live account. Each segment imposes its own profit target, its own drawdown buffer and its own rules, and payment occurs only if all of them are passed. Writing $F_{k}$ for the parameter vector of phase k, 

$$
P _ {\text { total }} = \prod_ {k = 1} ^ {K} P (\mathcal {F} _ {k}).\tag{1}
$$

The decomposition is exact by the Markov property: each phase starts at its own origin and its outcome does not depend on the path that led there. 

Its usefulness is organisational, not formal. Differences between firms—a one-step or two-step evaluation, a payout threshold that applies in the simulated account or only in the live account, a drawdown that trails in one phase and not in the other—stop being special cases and become different entries of the same vector. What follows characterises a single phase; (1) composes them. 

<table><tr><td colspan="3">Firm parameters, published, by phase</td></tr><tr><td>T</td><td>profit target</td><td>profit that must be reached to pass the phase</td></tr><tr><td>D</td><td>drawdown buffer</td><td>maximum loss allowed from the running maximum</td></tr><tr><td>δ</td><td>freeze level</td><td>level, relative to the starting balance, at which the floor stops trailing</td></tr><tr><td>mM</td><td></td><td>floor updates per session</td></tr><tr><td>mB</td><td></td><td>breach checks per session</td></tr><tr><td>Λ</td><td>daily loss limit</td><td>in soft or hard mode</td></tr><tr><td>c</td><td>consistency</td><td>maximum fraction a single session may contribute</td></tr><tr><td>ce, cr, cm</td><td></td><td>entry, reset and monthly fee</td></tr><tr><td>φ, τ, κ, u</td><td></td><td>profit split, withholding rate, payout cap, payout threshold</td></tr><tr><td>nmax</td><td></td><td>maximum position size</td></tr><tr><td>A</td><td></td><td>maximum number of simultaneous accounts</td></tr><tr><td colspan="3">Trader parameters, chosen</td></tr><tr><td>n(x)</td><td></td><td>position size profile as a function of cumulative profit</td></tr><tr><td>σd</td><td></td><td>standard deviation of their per-session P&amp;L</td></tr><tr><td>G</td><td>productivity</td><td>gross profit generated per funded-account cycle</td></tr><tr><td colspan="3">Market parameters, measured</td></tr><tr><td>μ, σ</td><td></td><td>drift and volatility of the P&amp;L, net of costs</td></tr><tr><td colspan="3">Derived quantities</td></tr><tr><td>P</td><td></td><td>probability of passing a phase; q = 1 - P</td></tr><tr><td>sM, sB</td><td></td><td>standard deviation of the balance between two consecutive evaluations</td></tr><tr><td>ν</td><td></td><td>normalised drift, ν = 2μ/σ2</td></tr><tr><td>N</td><td></td><td>sessions until an attempt resolves</td></tr></table>

## 2.3 A single phase

Let $S_{t}$ be the cumulative profit within the phase, with $S_{0} = 0$ , and let $M_{t} = \max_{v\leq t}S_{v}$ be its running maximum. The floor is 

$$
F _ {t} = \min (M _ {t} - D, \delta),\tag{2}
$$

the phase is passed if $S_{t}$ reaches T and ends if $S_{t}$ reaches $F_{t}$ . The parameter $\delta$ captures on its own the three regimes the industry sells: with $\delta = -D$ the floor never moves and the barrier is fixed; with $\delta = 0$ it trails up to the starting balance and freezes there; with $\delta \geq T - D$ the freeze falls outside the range and the barrier trails throughout the phase. 

Equation (2) splits the phase into two segments, separated by the instant the maximum reaches $D + \delta$ . 

Trailing segment. While $M_{t} < D + \delta$ the floor follows the maximum at distance D. With the process at a maximum m, the probability of reaching $m + dm$ before m - D is, by gambler's ruin between absorbing barriers, $D/(D + dm)$ . Chaining over the path of the maximum, 

$$
P _ {1} = \lim _ {n \to \infty} \prod_ {i = 1} ^ {n} \left(1 - \frac {L / n}{D}\right) = e ^ {- L / D}, \qquad L \equiv \min (D + \delta , T).
$$

Frozen segment. When the maximum reaches $D + \delta$ the process sits at that same level, because the maximum only grows when the process is at it. The floor is then fixed at $\delta$ and the problem reduces to a single gambler's ruin between $\delta$ and $T$ , at distances $D$ and $R \equiv T - D - \delta$ : $P_{2} = D / (D + R)$ . 

With drift, the scale function $h(x) = e^{-\nu x}$ with $\nu = 2\mu/\sigma^{2}$ replaces the linear one and the two segments become 

$$
P = \underbrace {\exp \left(- \frac {\nu L}{e ^ {\nu D} - 1}\right)} _ {\text {trailing}} \cdot \underbrace {\frac {e ^ {\nu D} - 1}{e ^ {\nu D} - e ^ {- \nu R}}} _ {\text {frozen}}, \qquad \begin{array}{l l} & L = \min (D + \delta , T) \\ & R = T - D - \delta \end{array}\tag{3}
$$

with $P = P_{1}$ if $R \leq 0$ . The limit $\nu \to 0$ recovers $e^{-L / D}$ and $D / (D + R)$ . 

<table><tr><td>Regime</td><td><eq>\delta</eq></td><td>P without drift</td><td>Value with T = $3,000, D = $2,000</td></tr><tr><td>Fixed</td><td>-D</td><td>D/(D+T)</td><td>0.400</td></tr><tr><td>Frozen at the starting balance</td><td>0</td><td><eq>e^{-1}</eq> D/T</td><td>0.245</td></tr><tr><td>Frozen, shifted</td><td>+$100</td><td><eq>e^{-(D+\delta)/D}</eq> D/(T-δ)</td><td>0.241</td></tr><tr><td>Trailing</td><td><eq>\geq</eq>T-D</td><td><eq>e^{-T/D}</eq></td><td>0.223</td></tr></table>

All four are the same contract with a different parameter, and the first is 79% more likely to be passed than the last (0.400 against 0.223). No firm publishes $\delta$ in the same table where it publishes T and D. 

## 2.4 Discrete monitoring

Equation (3) assumes that the floor is updated and the breach is checked continuously. No contract does this: the floor is usually recomputed at the session close and the breach is usually applied in real time, and both frequencies are contractual and independent of each other. 

Let $s$ be the standard deviation of the balance between two consecutive evaluations, 

$$
s = \frac {\sigma_ {d} n}{\sqrt {m}},\tag{4}
$$

with m the evaluations per session and n the position size. Equation (4) has a consequence worth pointing out before using it: monitoring frequency and position size enter through the same parameter. A contract monitored at the session close and traded in one lot, and another monitored forty-nine times a session and traded in seven lots, are the same instrument to the model. 

Discretisation shifts the effective barrier. Applying the continuity correction of Broadie et al. (1997) separately to each segment, 

$$
D _ {1} = D + \beta \max (s _ {M}, s _ {B}), \qquad D _ {2} = D + \beta s _ {B}, \qquad \beta = - \frac {\zeta (1 / 2)}{\sqrt {2 \pi}} = 0. 5 8 2 6,\tag{5}
$$

and D is replaced by $D_{1}$ in the trailing segment and by $D_{2}$ in the frozen one. The asymmetry has a direct reading. While the floor follows the maximum, a coarse clock of either kind favours the buyer—a floor that lags, or a breach that goes unwatched. Once frozen, the floor no longer follows anything and only the breach frequency counts. 

Verification. The correction is not imported: it is tested. Simulating the barrier of (2) at different step sizes and solving for the effective buffer that reproduces each probability, the measured ratio $D_{eff}/D$ matches $1 + \beta s/D$ with error below 3% in $D_{eff}$ across the whole range $s/D \in [0.02, 0.75]$ ; the induced error in P is stated below. And across the five combinations of $(m_{M}, m_{B})$ the industry uses, (3) corrected by (5) reproduces the simulation with error of at most 0.5%. 

<table><tr><td>Floor</td><td>Breach</td><td><eq>s_M</eq></td><td><eq>s_B</eq></td><td>Closed form</td><td>Simulation</td></tr><tr><td>intraday</td><td>intraday</td><td>96</td><td>96</td><td>0.2543</td><td>0.2543</td></tr><tr><td>at the close</td><td>intraday</td><td>850</td><td>96</td><td>0.3018</td><td>0.3002</td></tr><tr><td>at the close</td><td>at the close</td><td>850</td><td>850</td><td>0.3203</td><td>0.3193</td></tr><tr><td>intraday</td><td>at the close</td><td>96</td><td>850</td><td>0.3203</td><td>0.3189</td></tr><tr><td>hourly</td><td>intraday</td><td>321</td><td>96</td><td>0.2696</td><td>0.2692</td></tr></table>

Validity condition. The error of (5) is a function of s/D alone: below 1% for $s/D \leq 0.5$ , 3.4% at s/D = 0.7 and 10.7% at s/D = 1.4. Outside $s/D \lesssim 0.5$ the first-order correction stops holding and simulation is required. The direction of the error is worth noting: it overestimates P, so outside its validity range the expression errs in favour of the buyer. 

A corollary on position size. Under continuous monitoring the profile $n(x)$ is irrelevant for P: the driftless process is a martingale and the ruin probability does not depend on its local variance. The entire effect of size therefore operates through discretisation. In a product monitored at the close, quadrupling position size raises P by roughly a third—a figure obtained at s/D = 1.7, outside the validity range of (5) and therefore an upper bound—; in one monitored intraday the same change raises P by about a tenth. It is the only lever the model grants a trader with no edge, and it is largest where the contract watches infrequently. 

## 2.5 Daily loss limit

The daily limit comes in two types that do not admit the same treatment. The soft limit stops trading for the session without terminating the account: by optional stopping it does not change P under continuous monitoring, and under discrete monitoring it reduces it by between 1 and 10% through truncation of the left tail, which is exactly where the benefit of discretisation came from. It admits no closed form and is reported as a measured effect. 

The hard limit does admit one. Let $y = S_{t} - F_{t}$ be the distance to the floor and $\rho = 2\Phi(-\Lambda/\sigma_{d})$ the probability that the adverse excursion of a session reaches $\Lambda$ . A multiplicative killing-rate correction, $P(1-\rho)^{N}$ , is off by as much as 46% because it omits two effects that work in opposite directions. The first is that killing by the daily limit only acts where it is not redundant: if $y \leq \Lambda$ the drawdown floor kills first, and applying the rate there counts it twice. The second is that the increment conditional on survival is not the original increment: it acquires positive drift $\mu_{c}$ and reduced volatility $\sigma_{c}$ . 

With the three ingredients, the harmonic function is piecewise. With $\lambda = -\ln(1 - \rho)$ , $r_{\pm} = (-\mu_{c} \pm \sqrt{\mu_{c}^{2} + 2\sigma_{c}^{2}\lambda})/\sigma_{c}^{2}$ and $\nu_{c} = 2\mu_{c}/\sigma_{c}^{2}$ , 

$$
w (y) = \left\{ \begin{array}{l l} \frac {1 - e ^ {- \nu_ {c} y}}{\nu_ {c}}, & 0 \leq y \leq \Lambda , \\ A   e ^ {r _ {+} (y - \Lambda)} + B   e ^ {r _ {-} (y - \Lambda)}, & y > \Lambda , \end{array} \right.\tag{6}
$$

with A and B determined by continuity of w and $w'$ at $y = \Lambda$ . The probability of passing the phase is then $P_{1} = \exp(-L w'(D_{\mathrm{eff}})/w(D_{\mathrm{eff}}))$ in the trailing segment and $P_{2} = w(D_{\mathrm{eff}})/w(D_{\mathrm{eff}} + R)$ in the frozen one, and $\rho \to 0$ recovers (3). 

Validity condition. The error is below 3% for $\Lambda/\sigma_{d} \geq 2.75$ and grows monotonically as the limit tightens, because at high rates the killing is no longer approximable by a continuous process: it happens once per session, in a single block. The boundary has an economic reading. Below $\Lambda/\sigma_{d} \approx 2$ survival per cycle falls below 0.4 and the daily limit kills more than the drawdown; beyond that point the instrument stops being an option on drawdown and becomes an option on the daily limit, which is a different contract. The expression is therefore valid across most of the region in which the product remains an option on drawdown; between $\Lambda/\sigma_{d} \approx 2$ and 2.75 the error exceeds 3% and simulation is required. 

## 2.6 Consistency rule

The consistency rule caps what a single session can contribute to the total. The industry implements it in three different ways, and all three are modelled by raising the threshold the rule watches: 

raises the profit target: $T_{\mathrm{eff}} = \max \left(T, \frac{\mathrm{daily} \max}{c}\right)$ ; conditions the payout: $u_{\mathrm{eff}} = \max \left(u, \frac{\mathrm{daily} \max}{c}\right)$ . 

The third form, the one that restricts trading by capping the daily gain, works differently: together with the daily limit it confines the increment to $[-\Lambda, +cT]$ . For a zero-mean variable on $[-a, b]$ the maximum variance is ab, attained by the two-point distribution, so that 

$$
s \leq \sqrt {\Lambda c T}
$$

is an exact bound, not an approximation. It is worth noting that the daily limit on its own rarely binds the variance; it is the consistency rule that binds it. 

## 2.7 Duration

The number of sessions to resolution is not a parameter but an output, and it obeys a scaling law. With $\kappa_{N}$ depending only on the geometry, 

$$
\mathbb {E} [ N ] = \kappa_ {N} \left(\frac {D}{\sigma_ {d}}\right) ^ {2}, \quad \kappa_ {N} = \left(1 - e ^ {- \ell}\right) + e ^ {- \ell} \frac {R}{D}, \quad \ell = \frac {\min (D + \delta , T)}{D}.\tag{8}
$$

Expressed in terms of the success probability, $\kappa_{N} = (1 - P)/P$ under a fixed barrier, $\kappa_{N} = 1 - 2/e + 1/(e^{2}P)$ under a barrier frozen at the starting balance and $\kappa_{N} = 1 - P$ under a trailing barrier. Checked against simulation, $\kappa_{N}$ does not depend on $\sigma_{d}$ , as the scaling law requires; the measured value sits between 5 and 8% above the theoretical one, a difference attributable to the duration of the excursion that resolves the phase, which the derivation omits. 

Equation (8) separates what volatility does from what it does not. Under continuous monitoring P does not depend on $\sigma_{d}$ and E[N] depends on its square: volatility does not change the outcome, only the clock. It is also why the pair $(P,\mathbb{E}[N])$ identifies $\sigma_{d}$ without observing it directly. 

## 2.8 Scope

Everything that cannot be represented as a barrier on the cumulative P&L, or as a threshold on it, falls outside the model. In particular, minimum activity rules, restrictions on instruments and trading hours, prohibitions on automated trading and limits on offsetting positions. None of them admits the treatment above and all are declared as a limitation. 

## 3 Valuation

## 3.1 What is computed, and under which measure

The exercise is worth delimiting before carrying it out, because the vocabulary of derivatives valuation does not apply in full to this contract, and using it without qualification is misleading. 

The analogy with a barrier option is exact in one half and false in the other. It is exact for the probability calculation: the extinction condition in (2) is a barrier on the drawdown, the problem is a first-passage problem, and the results of Taylor (1975), Lehoczky (1977), Magdon-Ismail et al. (2004) and Broadie et al. (1997) apply in full. It is false for the value comparison. The underlying is not tradable, the payoff is not replicable—§6.4 documents this—and there is therefore no equivalent martingale measure with which to construct a no-arbitrage price. The probability P in (3) is physical, not risk-neutral. 

What follows is therefore an actuarial comparison: the expected value of the right under the physical measure against the premium paid. Discounting is omitted and the omission is justified: over horizons of some twenty sessions and at a rate of 5% a year, the factor is 0.996, an effect of 0.44% far below the error in any input. The criterion is expected value, that is, risk-indifferent preferences—not a risk-neutral measure—which is defensible when the stake is a three-figure fee and ceases to be so once cycles are chained; that is why §9 uses a different criterion. 

One objection deserves an explicit answer because it is the first one raised: the payoff of this contract requires the holder to trade, and a derivative requires nothing of its owner. Under the hypothesis that supports the model—no exploitable edge—the objection does not hold: any zero-expectation strategy generates the same process, so the trader's directional decisions are irrelevant for P and the contract behaves like a derivative on an exogenous process. What the trader does control, and what the model captures, are two nuisance parameters: scale, which enters through the discretisation ( $\S2.4$ ), and trading frequency, which enters through the cost drift. The trader does not control the drift of the process, which is what would be needed to invalidate the valuation. 

## 3.2 The cost

Obtaining a funded account takes, in expectation, 1/P attempts. The fee structure is not uniform across the industry and the two existing models give different expressions: 

$$
\Phi = \left\{ \begin{array}{l l} c _ {e} + \left(\frac {1}{P} - 1\right) c _ {r} + c _ {a}, & \text {   fee   per   evaluation, } \\ c _ {m} \cdot \max \biggl (1, \frac {\mathbb {E} [ N ]}{2 1 P} \biggr) + c _ {a}, & \text {   monthly   subscription, } \end{array} \right.\tag{9}
$$

with $c_{a}$ the activation fee, paid once and only on passing the evaluation. The second branch has a consequence the first does not: since E[N] decreases with the square of $\sigma_{d}$ by (8), at firms that charge by subscription, trading larger makes the product cheaper, because it resolves sooner and fewer monthly payments are made. At firms that charge per evaluation, it does not. 

The discount is a parameter, not a promotion. The firms examined advertise permanent or near-permanent discounts on a list price that is never actually charged. When the discount does not expire, the list price is not a price but a presentational device, and using it as a model input produces a valuation of a contract nobody buys. Writing d for the effective price factor, Equation (9) is homogeneous of degree one in d, so $\Phi(d) = d\Phi(1)$ and every derived quantity scales linearly. Every quantity is therefore reported at the effective price prevailing on the access date, with the list price recorded alongside it so that any other discount can be applied by scaling. 

## 3.3 The asset delivered

The funded account is not a payment but another phase of the chain (1). Its value decomposes into contractual parameters and a single trader parameter: 

$$
F = (1 - \tau) \varphi \cdot \mathbb {E} \biggl [ \min \biggl (G, \frac {\kappa}{(1 - \tau) \varphi} \biggr) \biggr ],\tag{10}
$$

where G is the expected amount withdrawn per funded account. It already incorporates the probability of reaching the payout threshold, so that probability does not enter a second time as a factor of its own. F thereby ceases to be a measured constant and becomes an output of the model. 

One free parameter remains, G, and under the no-edge hypothesis it is not free either: a zero-drift trader withdraws u on reaching the threshold and nothing otherwise, and that probability is (3) applied to the funded phase, with the payout threshold u in the role of the profit target, so $G_{0} = u P(u, D_{f}; \cdot)$ . Trader productivity turns out, in the neutral case, to be a consequence of the geometry of the funded phase. Any deviation from that value is, by definition, the trader's edge, and it is the quantity the case study measures. 

## 3.4 The value of the right

The state of an ongoing phase is not accumulated profit but the pair $(x,M)$ , balance and running maximum, because the floor in (2) depends on the second. Writing $y = x - F_{t}$ for the distance to the floor, 

$$
P (x, M) = \left\{ \begin{array}{l l} \frac {y}{D} \cdot e ^ {- (D + \delta - M) / D _ {1}} \cdot \frac {D _ {2}}{D _ {2} + R}, & M <   D + \delta , \\ \frac {x - \delta}{T - \delta}, & M \geq D + \delta . \end{array} \right.\tag{11}
$$

In the frozen segment the maximum drops out; in the trailing segment it enters through the exponential factor. The usual expression, $e^{-(T-x)/D}$ , is the special case x = M. 

The value must also capture that failing does not destroy the whole right, because the option to retry remains. Writing W for the value of starting an attempt already paid for, 

$$
W = F P + (1 - P) \left(W - c _ {r}\right) \Longrightarrow W = F - \left(\frac {1}{P} - 1\right) c _ {r}, \quad V (x, M) = P (x, M) \left(F - W + c _ {r}\right) + \left(W - c _ {r}\right).\tag{12}
$$

The value before paying the fee is $W - c_{e}$ , which coincides with $F - \Phi$ by construction: two calculation routes that reconcile, and a check worth reporting. 

## 3.5 Sensitivities

The derivatives of (12) are sensitivities of an expected value, not hedge coefficients. The distinction is not terminological: §6.4 shows that the position cannot be hedged, so none of these quantities admits the hedge-ratio reading it would have for a listed option. 

With respect to the balance. From (11), with the maximum held fixed, 

$$
\frac {\partial V}{\partial x} = \frac {F - W + c _ {r}}{D _ {1}} e ^ {- (D + \delta - M) / D _ {1}} \frac {D _ {2}}{D _ {2} + R}, \qquad \frac {\partial^ {2} V}{\partial x ^ {2}} = 0.\tag{13}
$$

The factor $F-W+c_{r}$ is smaller than F because it nets out the continuation value: the marginal dollar inside an evaluation buys less than it would if failure extinguished the right entirely. 

With respect to the maximum. Within the drawdown band the value is linear in the balance, so the convexity does not lie there. It lies in the maximum: along x = M, 

$$
\frac {\partial P}{\partial M} = \frac {P}{D _ {1}}, \quad \frac {\partial^ {2} P}{\partial M ^ {2}} = \frac {P}{D _ {1} ^ {2}} > 0.
$$

The convexity of the instrument comes from the ratchet of the barrier, not from the accumulation of profit, and that is what distinguishes it from an ordinary option on a level. 

With respect to volatility. Equation (3) does not contain $\sigma$ , so under continuous monitoring and with no drift the sensitivity is zero. It is not zero in any real contract: since $s \propto \sigma$ by (4) and $D_{1}$ and $D_{2}$ grow with $s$ by (5), the sensitivity is positive in every discretely monitored product. The result still runs against the industry's usual belief, but through a different mechanism from the one normally invoked: volatility does not favour the buyer because it speeds up resolution, but because it fattens the step between two looks at the barrier. 

With respect to the terms of the contract. From (3), $\partial P/\partial D > 0$ and $\partial P/\partial T < 0$ , and both are large: in the product examined, cutting the buffer by 10% costs around 15% of the probability of success. Since the terms are set by the seller, who contractually reserves the right to modify them on accounts already sold, this sensitivity has no analogue in a listed contract and admits no hedging. §6 treats it separately. 

## 3.6 The viability condition

The evaluation is worth its price when the expected value of the asset delivered exceeds the expected cost of obtaining it, $F > \Phi$ . Substituting (10) and solving for the trader's only unknown, 

$$
\boxed {G > G ^ {*} \equiv \frac {\Phi}{(1 - \tau) \varphi}}\tag{14}
$$

or, in dimensionless form, $g^{*} = G^{*}/G_{0}$ with $G_{0} = u P(u, D_{f}; \cdot)$ the productivity of a zero-drift trader. A value $g^{*} < 1$ indicates that the evaluation is worth its price even with no edge at all; $g^{*} = 1.4$ , that it requires generating 40% more than the neutral trader. The quantity is dimensionless, comparable across firms and computable entirely from published terms plus the buyer's $\sigma_{d}$ . The condition assumes that the payout cap does not bind; where it binds, $F \leq \kappa$ and no productivity satisfies the condition, which is the case treated in §3.7. 

By the homogeneity of (9) in the price factor, $g^{*}$ is linear in it, and the minimum discount that makes a product viable is $d^{*} = 1/g^{*}(1)$ . This is the operational reading in an industry whose discounts are permanent: a product with $g^{*} = 1.5$ at list price is not unviable; it becomes viable at a discount of 33% or more. 


Equation (14) replaces the geometric condition obtained by specialising to each regime, which is how the industry literature compares products:


<table><tr><td>Regime</td><td>Equivalent condition in T/D</td><td>Threshold with the parameters examined</td></tr><tr><td>Fixed</td><td>T/D &lt; (1 - PA)/PA</td><td>5.04</td></tr><tr><td>Frozen at the starting balance</td><td>T/D &lt; 1/(ePA)</td><td>2.22</td></tr><tr><td>Trailing</td><td>T/D &lt; ln(1 + (F - ce)/cr)</td><td>1.80</td></tr></table>

with $P_{A} = c_{r}/(c_{r} + F - c_{e})$ , which has a reading of its own: it is the break-even conversion rate, that is, the probability of success below which the evaluation ceases to be worth its price, and it is directly comparable with the rate each firm publishes. The three thresholds differ from one another by a factor of three, so applying the one for one regime to a product of another—or the one for one firm to a different firm—produces incorrect verdicts. 

## 3.7 When no skill is enough

From (10) it follows that $F \leq \kappa$ , a bound that does not depend on G: whatever the trader generates, the funded account cannot deliver more than the payout cap. If the payout cap is low enough relative to the cost, the evaluation is not worth its price for any buyer, regardless of skill: 

$$
\boxed {\kappa \leq \Phi^ {\mathrm{min}}}\tag{15}
$$

The condition is sufficient, not necessary, and it is built by bounding the payoff from above and the cost from below—both in the buyer's favour—, so an affirmative verdict admits no false positive. The bounds are computable from published terms: $\sigma_{d}$ is not free but is bounded by the firm's own clauses, $s \leq \sqrt{\Lambda cu}$ by §2.6, and with it $P^{max}$ is determined. The error of the closed form outside its range of validity overstates P (§2.4), which strengthens the bound rather than weakening it. 

Equation (15) does not claim that no firm violates it; it establishes how to check it, and that the check requires no simulation, no knowledge of the buyer, and no datum the firm does not publish. 

## 4 Industry application

## 4.1 Method and traceability

The parameters in this section come exclusively from each firm's own domain: its help centre, its contract terms and its pricing page. Review sites, aggregators and comparison sites are not used. Every value is recorded with the exact address and the verbatim quotation that supports it, collected in Appendix A, and the access date is the same for all of them: 10 August 2026. Dating the collection is not a formality in this industry: terms change, and §6 argues precisely that this variability is the dominant exposure of the contract. 

When a parameter does not appear in an official source it is left blank and declared as such. It is not filled in from third parties. The consequence is that the table below has gaps; they are informative, and filling them would have produced a table that was complete and less reliable. 

Two calculation conventions, both conservative. Where the checking frequency of the breach is not stated, intraday is assumed, which is the one that produces the lowest success probability and the one explicitly documented by the firms that do publish it. And where the freeze level of the floor is not stated, $\delta = 0$ is taken. Both assumptions are flagged in the table. 

All calculations use the same $\sigma_{d}$ , so that the differences between rows are attributable entirely to the contract terms and not to the trader. 

## 4.2 Dispersion of the success probability

* freeze level not located in an official source; $\delta = 0$ is taken. ${}^{\dagger}$ two official pages of the same firm publish different parameters for the same product; see §4.6. 

Eleven of the thirteen products advertise the same profit target and the same drawdown buffer, $3,000 and $2,000. Their success probability ranges from 0.250 to 0.407: a dispersion of 62%, attributable entirely to parameters that no industry comparison records and that in several cases do not appear alongside T and D on the firm's own page. 

The two parameters responsible are the barrier regime, $\delta$ , and the frequency with which the floor is updated. The second separates two sharp groups: the products that recompute the floor at the session close cluster around 0.30, those that do so intraday around 0.25. The difference is $19\%$ and comes exclusively from (5). A third group, that of the two firms whose $T / D$ ratio is 1.20 instead of 1.50, reaches 0.363; and the only fixed-barrier product located, 0.407. 

<table><tr><td>Firm</td><td>Product (50K)</td><td>T/D</td><td>δ</td><td>Floor</td><td>Breach</td><td>P</td></tr><tr><td>Elite Trader Funding</td><td>Static</td><td>1.50</td><td>-D</td><td>fixed</td><td>—</td><td>0.407</td></tr><tr><td>Bulenox</td><td>Qualification</td><td>1.20</td><td>0*</td><td>at close</td><td>intraday</td><td>0.363</td></tr><tr><td>Legends Trading</td><td><eq>Apprentice^†</eq></td><td>1.20</td><td>0*</td><td>at close</td><td>intraday</td><td>0.363</td></tr><tr><td>Apex</td><td>Evaluation EOD</td><td>1.50</td><td>0*</td><td>at close</td><td>intraday</td><td>0.302</td></tr><tr><td>TradeDay</td><td>Quick Pay EOD</td><td>1.50</td><td>0</td><td>at close</td><td>intraday</td><td>0.302</td></tr><tr><td>Topstep</td><td>Trading Combine</td><td>1.50</td><td>0</td><td>at close</td><td>intraday</td><td>0.302</td></tr><tr><td>Earn2Trade</td><td>Gauntlet Mini</td><td>1.50</td><td>0</td><td>at close</td><td>intraday</td><td>0.302</td></tr><tr><td>Take Profit Trader</td><td>Test</td><td>1.50</td><td>0</td><td>at close</td><td>intraday</td><td>0.302</td></tr><tr><td>Legends Trading</td><td><eq>Apprentice^†</eq></td><td>1.50</td><td>0*</td><td>at close</td><td>intraday</td><td>0.302</td></tr><tr><td>Tradeify</td><td>Growth</td><td>1.50</td><td>+$100</td><td>at close</td><td>intraday</td><td>0.300</td></tr><tr><td>Apex</td><td>Evaluation Intraday</td><td>1.50</td><td>0*</td><td>intraday</td><td>intraday</td><td>0.254</td></tr><tr><td>Elite Trader Funding</td><td>1-Step</td><td>1.50</td><td>0*</td><td>intraday</td><td>intraday</td><td>0.254</td></tr><tr><td>MyFundedFutures</td><td>Rapid</td><td>1.50</td><td>+$100</td><td>intraday</td><td>intraday</td><td>0.250</td></tr></table>

Eight of the ten firms update the floor at the close and apply the breach in real time. It is therefore the majority convention of the industry, not a special case. 

## 4.3 The consistency rule operates in three ways


The consistency rule is presented at every firm with the same wording—no session may contribute more than a fraction of the total—and produces three distinct effects depending on which threshold it applies to:


<table><tr><td>Mechanism</td><td>Effect</td><td>Firms and fraction</td></tr><tr><td>Raises the profit target</td><td><eq>T_{\text{eff}} = \max(T, \text{daily max.}/c)</eq></td><td>Topstep 50%, Take Profit Trader 50%, TradeDay 30%, MyFundedFutures 50%</td></tr><tr><td>Conditions the payout</td><td><eq>u_{\text{eff}} = \max(u, \text{daily max.}/c)</eq></td><td>Tradeify 35%</td></tr><tr><td>Caps the daily gain</td><td><eq>s \leq \sqrt{\Lambda cT}</eq></td><td>Earn2Trade 30%</td></tr></table>

The first two do not prevent trading: they delay it or make it more expensive by raising a threshold. The third does restrict it, and it is the only one that admits the variance bound of §2.6. The distinction matters because the first mechanism raises the threshold of the phase currently under way and the second that of a later phase, so that they enter (1) in different factors. 

The effect is not minor. On the payout mechanism, with a daily standard deviation of $400 and some twenty sessions to reach the threshold, a fraction of 35% raises the effective threshold 42% above the nominal one. 

## 4.4 The two billing models

Eight of the ten firms charge by monthly subscription and not by evaluation, so that the first branch of (9) does not apply to most of the industry. The difference is not merely one of form: under a subscription the cost depends on $\mathbb{E}[N]$ and, through (8), on the trader's position size. 

Two firms also bill a monthly fee during the funded phase, which reduces F directly and which (10) does not capture unless it is incorporated as drift under (4). And seven charge an activation fee on passing the evaluation, which is paid once but does not appear in the advertised price. 

## 4.5 Choosing between purchase alternatives

An immediate use of (9) is to rank the variants that a single firm offers of the same product, something no comparison does because it requires knowing how many attempts are needed. One firm alone publishes six combinations of the same account size at different prices, which allows the full comparison: 

<table><tr><td>Variant</td><td>P</td><td>Attempts</td><td>Cost per attempt</td><td>Φ</td></tr><tr><td>Intraday, five-pack</td><td>0.254</td><td>3.93</td><td>$19.00</td><td>$215</td></tr><tr><td>Intraday, single</td><td>0.254</td><td>3.93</td><td>$24.90</td><td>$238</td></tr><tr><td>At close, five-pack</td><td>0.302</td><td>3.31</td><td>$45.00</td><td>$289</td></tr><tr><td>At close, single</td><td>0.302</td><td>3.31</td><td>$49.00</td><td>$302</td></tr><tr><td>At close without activation, five-pack</td><td>0.302</td><td>3.31</td><td>$109.00</td><td>$361</td></tr><tr><td>At close without activation, single</td><td>0.302</td><td>3.31</td><td>$119.00</td><td>$394</td></tr></table>

The expected cost of obtaining a funded account varies by 83% between the best and the worst variant of the same product. And the ranking is not the one that probability suggests: the intraday-barrier variant turns out to be preferable despite having a success probability 16% lower, because the price difference more than offsets it. 

The choice between paying activation or not also admits a general rule. With prices $p_{1}$ and $p_{2}$ for the two variants and an activation fee $c_{a}$ , indifference is reached at 

$$
c _ {a} = \frac {p _ {2} - p _ {1}}{P},
$$

so that below that amount the variant with activation is preferable. In the tabulated case the threshold is $212 against a published fee of $140. 

## 4.6 Discrepancies between sources of the same firm

During the collection, parameters were located that two official pages of the same firm publish with different values. They are recorded because they are a fact about the information available to the buyer, and because in one case the disagreement moves the success probability enough to change the product's position in the table above. 

<table><tr><td>Firm</td><td>Parameter</td><td>Page A</td><td>Page B</td></tr><tr><td rowspan="3">Legends Trading</td><td>drawdown buffer consistency</td><td>$2,000none</td><td>$2,50030%</td></tr><tr><td>minimum days</td><td>1</td><td>4</td></tr><tr><td>maximum position</td><td>2 minis / 20 micros</td><td>4 minis / 40 micros</td></tr><tr><td rowspan="2">Elite Trader Funding</td><td>activation fee</td><td>$150</td><td>$157</td></tr><tr><td>profit split</td><td>100% up to $12,500, 90% thereafter</td><td>80%</td></tr><tr><td>Earn2Trade</td><td>minimum days</td><td>none</td><td>10</td></tr></table>

In the first case, the drawdown buffer determines T/D and with it the success probability: $2,000 place the product at 0.302 and $2,500 at 0.363, a difference of 20%. The exact addresses of each page appear in Appendix A. No inference about the firm is drawn from this; what is recorded is the fact that the two pages coexisted on the access date. 

## 5 Where the margin comes from

## 5.1 Two pass rates that do not agree

The success probability that (3) yields for the industry's products lies between 0.25 and 0.41. The pass rates that circulate within the industry itself lie between $5\%$ and $14\%$ . They are the same quantity, and they differ by a factor of between 1.8 and 8. 

Before explaining that, the second figure is worth qualifying, because its provenance is uneven. The 5–14% figures circulate among aggregators and review sites with no primary source, and those attributed to specific firms are unverified self-reports. Only two observations can be cited: 

1. One firm publishes on its own site a rate of 7.35% since inception, with no sample size. It is a self-report and is treated as such. 

2. A Commodity Futures Trading Commission complaint records more than 135,000 customers and more than $310 million in fees collected over a twenty-two month period by one firm in the industry (CFTC, 2023). Taken at those lower bounds, that is average spending of at least $2,296 per customer; at an average fee of $250, some 9.2 evaluations per customer, and therefore $P \leq 10.9\%$ . It is an upper bound, because a buyer who quits before passing buys fewer than $1/P$ evaluations. The estimate is sensitive to the assumed average fee: $150 puts it at 6.5% and $400 at 17.4%. 

The second is the only industry-level estimate anchored in a court filing, and it corroborates the range from outside the ecosystem that publishes it. The caveats are that the firm traded foreign exchange rather than futures, and that the case was never resolved on the merits. 

## 5.2 Gross contribution per funded account

The discrepancy stops being a curiosity once it is carried into the unit P&L. For every funded account a seller delivers, it takes in the fees the buyer paid until passing—that is, $\Phi$ from (9)—and hands over the value F from (10). Gross contribution is the difference, and it depends only on the conversion rate: 

<table><tr><td>Conversion rate</td><td>P</td><td>Revenue</td><td>Cost</td><td>Contribution</td><td>Margin</td></tr><tr><td>Model, floor at close</td><td>0.300</td><td>$338</td><td>$606</td><td>-$268</td><td>-79.2%</td></tr><tr><td>Model, intraday floor</td><td>0.254</td><td>$398</td><td>$606</td><td>-$208</td><td>-52.4%</td></tr><tr><td>Break-even</td><td>0.166</td><td>$606</td><td>$606</td><td>$0</td><td>0%</td></tr><tr><td>Published, high end</td><td>0.140</td><td>$715</td><td>$606</td><td>+$109</td><td>15.3%</td></tr><tr><td>Published, midpoint</td><td>0.100</td><td>$998</td><td>$606</td><td>+$392</td><td>39.3%</td></tr><tr><td>Self-reported by one firm</td><td>0.073</td><td>$1,355</td><td>$606</td><td>+$749</td><td>55.3%</td></tr><tr><td>Published, low end</td><td>0.050</td><td>$1,988</td><td>$606</td><td>+$1,382</td><td>69.5%</td></tr></table>

The quantity is gross contribution per unit, not profit: it excludes platform, market data, customer acquisition and overhead. And it uses the terms of a single product, so its level does not extrapolate to the industry; what does extrapolate is the shape of the dependence. 

That shape is the result. At the conversion rate the model predicts, the product has negative unit contribution. A seller delivering funded accounts at the rate a zero-drift buyer would achieve would be paying out more than it takes in on each one. The business is not viable at that rate. At the rates the industry publishes, contribution is positive and grows as the rate falls. 

## 5.3 One number, two readings

The point at which contribution vanishes is exactly $P_{A} = c_{r}/(c_{r} + F - c_{e}) = 0.166$ , the same expression §3 obtained as the buyer's viability threshold. This is not coincidence but identity: the evaluation stops being worth its price to the buyer precisely where it stops producing margin for the seller, because the two are opposite sides of the same transaction and no third party takes anything. 

$P_{A}$ therefore admits two simultaneous readings. For the buyer it is the success probability below which they pay more than they receive. For the seller it is the break-even conversion rate: the rate above which the product stops generating contribution. And because it is computed entirely from published terms, anyone can compare it with the pass rate the firm itself advertises. 

## 5.4 Which lever moves the margin

Differentiating contribution with respect to each input, evaluated at a conversion rate of 10%: 

<table><tr><td>Lever</td><td>Elasticity</td><td>Note</td></tr><tr><td>Reset price <eq>c_{r}</eq></td><td>+2.27</td><td>appears in no comparison table</td></tr><tr><td>Conversion rate <eq>P</eq></td><td>-2.30</td><td>set by unadvertised parameters</td></tr><tr><td>Value delivered <eq>F</eq></td><td>-1.55</td><td>profit split, payout cap and payout threshold</td></tr><tr><td>Entry fee <eq>c_{e}</eq></td><td>+0.27</td><td>the only price the market compares</td></tr></table>

The reading is direct, and it has consequences for any transparency rule. The entry price, which is the only one buyers compare, is the least effective lever: it moves contribution eight times less than the reset price. A seller can wipe out the buyer's margin entirely without changing the advertised price, by making the reset more expensive or tightening any of the parameters in §4.2 that determine $P$ and that are not published alongside $T$ and $D$ . 

That explains an observable regularity in the industry: competition is fought on the entry price—with permanent discounts that reach 90%—while the parameters that determine value stay scattered across help centres. Under this decomposition, competing on the entry price costs little margin; the discounts are consistent with that structure of elasticities. 

## 5.5 The gap concentrates in one phase

The model does not fail uniformly along the chain (1). Applied to the funded phase, it predicts a payout probability of 0.50 to 0.61 depending on the threshold; the pair of published figures—around 10% passing and 7% of buyers reaching a payout—implies a conditional payout probability of 0.70. The order of magnitude agrees. Applied to the evaluation, by contrast, the model predicts 0.30 against an observed 0.10: a factor of three. 

The asymmetry admits a single, testable explanation. The funded-phase population has passed a filter; the evaluation population has not. The model describes a zero-drift trader, and it turns out that those who reach the funded phase resemble that trader while the general population does not. The gap is not a failure of the model: it is the size of the selection the evaluation performs. 

## 5.6 The gap has units


Equation (3) allows drift, so the discrepancy can be expressed as the daily drift that would produce it:


<table><tr><td>Pass rate</td><td>Implied μ</td><td>μ/σd</td><td>Per cycle</td></tr><tr><td>14%</td><td>-$127/session</td><td>-0.150</td><td>-$2,814</td></tr><tr><td>10%</td><td>-$189/session</td><td>-0.222</td><td>-$4,177</td></tr><tr><td>7%</td><td>-$249/session</td><td>-0.293</td><td>-$5,512</td></tr><tr><td>5%</td><td>-$303/session</td><td>-0.356</td><td>-$6,694</td></tr></table>

Plausible execution costs—commission and half the spread, at two to eight round turns per session—run between $10 and $40 per session. The implied drift is three to thirty times larger. Commissions and the bid-ask spread do not explain the gap. 

## 5.7 Reading

The three observations above compose a description of the business different from the one implied by the advertised price. 

The evaluation is cheap for a zero-drift trader: on the terms examined, such a trader would receive in expectation close to twice what they pay. That trader is, however, rare. The seller's margin does not come from overpricing—at the conversion rate of a neutral trader, unit contribution would be negative—but from the distance between that hypothetical buyer and the average buyer, a distance the evaluation measures and charges for. 

Two things follow. The first is that the product is not mispriced in the usual sense of the word: it is priced for a buyer who barely exists. The second is that the parameters that determine what it is worth—barrier regime, monitoring frequency, daily limit, consistency rule, reset price and payout threshold—are all verifiable from published terms, and none of them appears in the industry's comparison tables. A transparency rule requiring them to be published alongside the profit target and the drawdown buffer would demand no data the firms do not already have. 

## 6 Stability of the terms

## 6.1 The sensitivity with no analogue

In a listed contract, the strike, the barrier and the expiry are fixed once the contract is entered. Here they are set by the seller, who contractually reserves the right to modify them on accounts already sold. The corresponding sensitivity has no equivalent in a derivative and is, in magnitude, the largest in the instrument. 

From (3), $\partial P / \partial D > 0$ and $\partial P / \partial T < 0$ , with elasticities of order 1.5. On the terms examined, cutting the buffer by $10\%$ costs around $15\%$ of the probability of success; raising the payout threshold from $750 to $1,500 lifts funded-phase mortality from $31.8\%$ to $49.5\%$ . Neither change alters the advertised price, and neither takes more than editing a help page. 

The exposure cannot be hedged, by construction. No instrument has a payoff correlated with a private company's decision to change the rules of its own product, and no market prices that decision. Nor is it bounded: nothing in the contract limits the size of the change. 

## 6.2 A documented case

While this paper was being written, the payout threshold of the product studied went from $750 to $1,500. The effect on the quantity that supports the funded-phase analysis is direct: 

<table><tr><td>Payout threshold</td><td>Funded-phase mortality</td><td>Sessions to payout</td></tr><tr><td>$750</td><td>31.8%</td><td>27.2</td></tr><tr><td>$1,000</td><td>36.8%</td><td>31.5</td></tr><tr><td>$1,250</td><td>44.8%</td><td>38.3</td></tr><tr><td>$1,500</td><td>49.5%</td><td>42.3</td></tr><tr><td>$2,000</td><td>59.4%</td><td>50.9</td></tr></table>

Funded-phase mortality is therefore not a constant of the contract but a function of two parameters: the payout threshold, which the firm sets, and the trader's daily rule, which sets $\sigma_{d}$ . Reporting it as a number would have left it obsolete once the change was made; reporting it as a function leaves it intact. 

## 6.3 No set of terms is stable

Suppose there were a set of parameters under which the buyer captured a sure surplus. Such a set would imply that the seller loses against every buyer who detects it. Since the seller observes its own results and can modify the terms on accounts already sold, such a configuration does not survive being detected. 

Formally, capturing a sure surplus requires three conditions: that the product be cheap, $F > \Phi$ ; that the residual risk can be eliminated at a cost below that margin; and that the parameters stay stable over the life of the contract. The first two are conditions on price. The third is a condition on the counterparty, it admits no hedging, and none of the firms examined offers it. 

## 6.4 The second condition: hedging

The first condition holds for the product examined. The second does not, and by a margin worth quantifying, because the opposite conclusion was tenable for much of the earlier version of this work. 

The accounting. A cycle contains $n_{\mathrm{fail}} = q/(1 - q)$ failed attempts and one that passes, with $n_{\mathrm{att}} = 1/(1 - q)$ attempts in total. Each failure leaves a net residual b from the protection; the unrecoverable costs are the entry fee, paid once, and the carry $C_{a}$ , paid on every attempt. From the single relevant inequality, 

$$
n _ {\mathrm{fail}} b - c _ {e} - n _ {\mathrm{att}} C _ {a} \geq 0 \iff C _ {a} \leq q b - (1 - q) c _ {e} \iff q \geq q ^ {*} = \frac {C _ {a} + c _ {e}}{b + c _ {e}}.\tag{16}
$$

The two conditions that the project literature treated separately—a threshold on the carry and one on the failure rate—are the same inequality solved for different variables, and treating them independently produced opposite verdicts on the same data. 

With the measured values, $C_a^* = \$129$ against a carry of \$899, and $q^* = 3.30$ . That last value is not a demanding threshold: it is impossible. There is no failure rate, not even 100%, that makes hedging profitable at the measured carry. 

Why the result is not accidental. Hedging this contract means being short the underlying or long protection on it, and both positions have negative expectation under the physical measure for an equity index: the first because of the equity risk premium, the second because of the variance risk premium. The hedged buyer is structurally on the unfavourable side of two documented premia. It is an empirical regularity and not a theorem, but it is informative: it says why hedging loses instead of decreeing that it cannot win. 

The size of the effect is not negligible against the threshold. With a notional equivalent to four micro contracts and a risk premium of 5% a year, the short exposure costs some $155 per attempt, above the $129 that (16) allows. Hedging does not fail through execution friction: the instrument that has to be bought has negative expectation before the first spread is paid. The caveat is that with a symmetric hedge—long or short according to the direction of the evaluation—the equity premium cancels on average and only the variance premium remains. 

Liquidity of the instrument. To this is added an observed constraint. On the underlying's option chain at one and two days to expiry, $15\%$ of the observations show a two-sided book with non-zero size, and all of them concentrate at $|\Delta| \leq 0.72$ . In the band the hedge requires, $|\Delta| \in [0.85, 0.95]$ , no observation showed a two-sided book. This is a control internal to the capture itself: the same request, on the same instrument and at the same instant, returns a quote at some strikes and not at others, which rules out the possibility that the absence reflects a limitation of the data feed. The detail and its limits appear in Appendix B. 

## 7 Measure coherence in calibrated simulators

This section documents a methodological error that appeared during the work, the condition that detects it, and its correction. It is set out separately from the case study because the failure is not specific to this contract or to this industry: it appears in any procedure that reweights historical scenarios while holding fixed the prices of the instruments that pay out in them. 

## 7.1 The setup

A simulator has a history of scenarios and an instrument whose payoff depends on the scenario. The observed rate of an event does not match the one the history produces, and the simulator applies a calibration factor that reweights the scenarios until it reproduces that rate. That done, it evaluates the expected result of holding the instrument. 

The failure is that the reweighting alters the distribution of scenarios while the price of the instrument remains the one calibrated under the original distribution. The probability mass of the states in which the asset pays out is increased without repricing the asset. 

## 7.2 The invariant

Measure coherence. If the procedure alters the measure under which it generates the states, from P to $\tilde{P}$ , every quantity priced under P must be repriced under $\tilde{P}$ , or else weighted by the Radon–Nikodym derivative $dP/d\tilde{P}$ . Omitting both steps manufactures expected value in proportion to the shift of the measure. 

Stated this way, the failure has a name: it is importance sampling without the likelihood ratio. It does not require invoking complete markets or absence of arbitrage, which in any case would not apply here because the contract being valued is not traded ( $\S3$ ). It is a condition on the internal coherence of the procedure, and for that reason it is verifiable without assumptions about the market. 

## 7.3 The signature of the artefact

The manufactured value is proportional to the shift of the measure and vanishes as that shift tends to the identity. That dependence is an executable diagnostic: it is enough to sweep the calibration factor and observe whether the result scales with it. A real economic effect does not depend on how much calibration is needed. 

In the case that motivated this section, the engine returned a surplus of \$59 per attempt in favour of the hedged position, and that surplus grew monotonically with the calibration factor and vanished in the regime where the factor tended to one. 

## 7.4 The two corrections and their equivalence

The reweighting admits two correct and equivalent treatments. The first is to reprice the instrument under the shifted measure: if the probability of the state in which it pays out rises, its fair price rises with it. The second is to keep the observed price and weight each scenario by $dP/d\tilde{P}$ . With the first applied to the case cited, the surplus returns to zero for every calibration factor. 

## 7.5 Scope

The setup described is not uncommon. It appears in every backtest that resamples scenarios to fit a target rate, in stress tests that shift probabilities without revising valuations, and in any calibration that forces onto a history a frequency different from the one that history contains. In all of them, the manufactured quantity is proportional to the shift, so that a small shift produces a small effect, hard to distinguish from the result being sought. 

## 7.6 On the procedure

The condition was written before there were any results to defend, and it was what detected the error. That order is what gives it value: an invariant formulated after observing an uncomfortable result is not a test, it is a rationalisation. Appendix C documents the full trajectory of the project's estimates, including the shifts attributable to detected errors and those attributable to procedural defects. 

## 8 Calibration and testing

The preceding sections use no data that is not a published term. This one introduces the only block of information original to this work: one buyer's actual trading on one specific product. It serves two purposes: to calibrate the two trader parameters the model requires, and to test the model's predictions against independently measured quantities. 

## 8.1 Data and procedure

The base is 1,833 sessions of the underlying index at five-minute resolution. Complete attempts are generated on them, with exact accounting of the barrier in (2) and of the product's published rules. Each session's outcome is taken from the historical series with randomised direction, which faithfully implements the no-edge hypothesis: under it, directional decisions do not alter the distribution of the outcome. 

That implementation carries an auxiliary assumption worth declaring, because it is not innocuous: it takes the trader's per-session outcome to be the underlying's session with a random sign, that is, that of a position opened at the open and held to the close. A trader with exit orders, or one who trades intraday, has a different distribution. The model indicates which moments of that distribution matter: $\sigma_d$ through (4) and the shape of the left tail through §2.5. Sensitivity to the first is smaller than sampling error under intraday monitoring; sensitivity to the second is not, wherever a hard daily loss limit applies. 

## 8.2 Precision of the estimates

The quantities derived from the simulation are not as precise as the number of paths generated suggests. The information resides in the sessions available, not in the paths built from them: with S sessions and $E[N]$ sessions per attempt, the number of independent attempts is of order $S/E[N]$ , and the design effect relative to the naive calculation is $n_{\mathrm{sim}}E[N]/S$ . 

<table><tr><td>Quantity</td><td>Value</td><td>Independent n</td><td>Standard error</td><td>95% interval</td></tr><tr><td>Success probability</td><td>0.257</td><td>366</td><td>0.023</td><td>[0.212 — 0.302]</td></tr><tr><td>Funded-phase mortality ($750 threshold)</td><td>0.310</td><td>94</td><td>0.048</td><td>[0.217 — 0.403]</td></tr><tr><td>Sessions per attempt</td><td>5.01</td><td>366</td><td>0.26</td><td>[4.50 — 5.52]</td></tr><tr><td>Value of the funded account</td><td>$606</td><td>—</td><td>$3</td><td>[$600 — $612]</td></tr></table>

The intervals come from a block bootstrap over blocks of five consecutive sessions, which preserves the intraday autocorrelation that independent sampling destroys. 

## 8.3 Testing


The comparison between model and measurement must state how many parameters were fitted in each case.


<table><tr><td>Test</td><td>Parameters fitted</td><td>Model</td><td>Measured</td></tr><tr><td>Evaluation, closed form</td><td>none</td><td>0.300</td><td><eq>0.257 \pm 0.023</eq></td></tr><tr><td>Funded phase, closed form ($1,500 threshold)</td><td>none</td><td>0.50</td><td><eq>0.50 \pm 0.05</eq></td></tr><tr><td>Duration per attempt</td><td><eq>\sigma_d</eq>, identified from (8)</td><td>4.5</td><td><eq>5.01 \pm 0.26</eq></td></tr></table>

The first two rows fit nothing: the geometry of the contract determines the prediction entirely. The third identifies $\sigma_{d}$ , the only trader parameter the model needs, and it does so on an observable different from the one subsequently tested. 

Power. The interval in the first row does not discriminate between regimes: with the sample available, the trailing barrier, the frozen barrier and the frozen barrier corrected for discretisation are all compatible with the measurement. It does exclude the convention of checking at the close. Separating the trailing barrier from the frozen one—a difference of 0.022, which is what distinguishes two different contracts—would require on the order of 3,000 independent attempts, that is, some 15,000 sessions, against the 1,833 available. 

## 8.4 The trader's edge

With no edge, the productivity of the funded account is determined by its geometry: $G_0 = u \cdot P(u, D_f; \cdot) = \$745$ . Measured productivity is \$673, -9.6\% relative to the neutral benchmark. The deviation is, by construction, the trader's edge, and in this case it is negative and of the order of magnitude of execution costs accumulated over the length of the cycle. 

It is the only original figure this work contributes to the model, and its sign is consistent with the reconciliation in §5.5: the trader examined sits close to the neutral benchmark and well above the population that the published rates describe. 

## 8.5 Verdict on the product examined

On published terms and at the effective price in force on the access date—the single one-off purchase at $107, against a list price of $145, plus $99 for each reset—the expected cost of obtaining a funded account is $338 and the value delivered $606: the buyer pays 44% less than the expected value delivered. The minimum productivity that makes the evaluation worth its price is half that of the neutral trader, $g^{*} = 0.50$ , and the product would still be viable at twice the advertised price, $d^{*} = 1.98$ . 

The verdict is therefore favourable to the buyer, and it is conditional on what §5 establishes: it is the verdict for a zero-drift trader. The pass rate the industry publishes implies a population that is not, and for that population the same calculation produces the opposite result. 

## 9 Operating the contract repeatedly

The preceding sections value the contract. This one takes up a different question, whether chaining them is worthwhile, which requires three elements the valuation does not need: a calendar, a risk criterion and the number of simultaneous accounts. It is kept separate because all three introduce assumptions the valuation does not require, and because the decision criterion is no longer expected value. 

## 9.1 Calendar

The number of cycles that fit into a year is not free. With $S_{year}$ market sessions, E[N] sessions per attempt from (8), 1/P attempts per cycle and A simultaneous accounts, 

$$
\text { cycles   per   year } = \frac {S _ {\text { year }} \cdot A \cdot P}{\mathbb {E} [ N ]}.\tag{17}
$$

The expression has to be written out, because otherwise the annualisation stays implicit and can turn out to be infeasible without anyone noticing: a rule that assumes a fixed number of attempts per year requires, once multiplied by the sessions each attempt consumes, a calendar that can exceed the working year. 

## 9.2 Simultaneous accounts

The parameter A is contractually capped at several firms—one of those examined sets it at five—and its effect on risk is not what the diversification intuition suggests. Several accounts traded with the same strategy on the same underlying fail simultaneously: income is multiplied by A and so is the standard deviation, with no reduction in relative variance at all. A ruin probability computed on one account does not carry over to A accounts. 

## 9.3 Criterion

The expected-value criterion of §3 is defensible when the stake is a three-figure fee. It stops being defensible once cycles are chained with the buyer's own capital committed, where the relevant quantity is the probability of exhaustion and not the mean. The results in this section are therefore reported with their distribution and not only with their expectation. 

## 10 Discussion and limits

On the scope of the model. Left outside are the rules that cannot be represented as barriers or thresholds on the cumulative P&L: minimum activity requirements, restrictions on trading hours and instruments, prohibitions on automated trading and limits on offsetting positions. All of them plausibly reduce P, and none is quantified here. 

On the validity conditions. The closed form of (3) corrected by (5) has an error below 1% for $s/D \leq 0.5$ and degrades outside that range, overestimating P. The treatment of the hard daily loss limit has an error below 3% for $\Lambda/\sigma_{d} \geq 2.75$ and also errs on the high side outside it. The soft daily loss limit admits no closed form and its effect is reported as a measurement. 

On the industry data. It comes from official sources on a single date. Terms change, and this paper argues that they change materially. Any conclusion about a specific product lapses with its rulebook; conclusions about the structure do not. 

On the pass rates. With the exception noted in §5, they circulate with no primary source. The argument of that section does not depend on their exact level but on the fact that they lie below the break-even conversion rate, which is the case across the whole published range and also for the bound derived from the only court document available. 

On the no-edge assumption. It carries the entire valuation. It is not tested here, and the natural test—measuring the drift of the trader's actual P&L—is the same experiment that would estimate their edge. A buyer with genuine edge invalidates the model in their favour. 

On the regulatory framework. Supervision of these firms is not settled. The most significant proceeding brought by a US regulator against a firm in the industry (CFTC, 2023) was never resolved on the merits. The gap this paper documents is not closing. 

## 11 Conclusion

A proprietary trading firm's evaluation contract admits closed-form treatment as a chain of first-passage problems on a drawdown barrier. The resulting expression depends on six contractual parameters—profit target, drawdown buffer, freeze level of the floor, updating frequency, checking frequency and daily limit—of which industry comparisons publish two. 

The consequence is measurable. Among thirteen products of the same account size, eleven advertise identical profit target and drawdown buffer and their success probability varies by 62%. The variation is attributable entirely to parameters the firm publishes but not alongside the price. 

From the valuation follows a quantity comparable across firms and computable from a pricing page: the minimum productivity that makes an evaluation worth its price. And a sufficient condition, built on bounds favourable to the buyer, under which the product is not worth its price to any buyer at any level of skill. 

Applied to the industry, it yields a description of the business different from the one the advertised price suggests. The evaluation is not overpriced—for a zero-drift buyer it is cheap—and the seller's unit contribution would be negative at the conversion rate such a buyer would achieve. The margin comes from the distance between that buyer and the real one, and the break-even conversion rate—which is the same expression as the buyer's viability threshold—separates the two populations. 

On capturing that surplus, three negative results. The position cannot be hedged: the carry threshold that would make it profitable is an order of magnitude below the measured one, and the instrument required has negative expectation before friction is taken into account. The price lever the market compares—the entry fee—is the least effective of them all, eight times less so than the reset price. And no set of terms is stable, because the missing condition is not one of price but of contractual commitment: the seller writes the rules and reserves the right to rewrite them. During the preparation of this paper it did so, and the quantity that underpins the funded-phase analysis moved by eighteen points. 

## A Industry data


All parameters come from each firm's own domain. Access date: 10 August 2026. Gaps indicate that the parameter was not located in an official source; they are not filled in from third parties. The data file published with this paper contains, for each value, the exact address and the verbatim quotation that supports it.


<table><tr><td>Firm</td><td>Product</td><td>T</td><td>D</td><td>δ</td><td>Floor</td><td>Λ</td><td>c</td><td>Billing</td></tr><tr><td>Tradeify</td><td>Growth</td><td>3,000</td><td>2,000</td><td>+100</td><td>at close</td><td>1,250 s.</td><td>35% payout</td><td>one-off</td></tr><tr><td>Topstep</td><td>Combine</td><td>3,000</td><td>2,000</td><td>0</td><td>at close</td><td>1,000 s.</td><td>50% target</td><td>monthly</td></tr><tr><td>Apex</td><td>Eval. Intraday</td><td>3,000</td><td>2,000</td><td>—</td><td>intraday</td><td>—</td><td>—</td><td>one-off</td></tr><tr><td>Apex</td><td>Eval. EOD</td><td>3,000</td><td>2,000</td><td>—</td><td>at close</td><td>1,000</td><td>—</td><td>one-off</td></tr><tr><td>Bulenox</td><td>Qualification</td><td>3,000</td><td>2,500</td><td>—</td><td>at close</td><td>1,100 s.</td><td>—</td><td>monthly</td></tr><tr><td>Elite Trader F.</td><td>1-Step</td><td>3,000</td><td>2,000</td><td>—</td><td>intraday</td><td>none</td><td>yes</td><td>monthly</td></tr><tr><td>Elite Trader F.</td><td>Static</td><td>3,000</td><td>2,000</td><td>-D</td><td>fixed</td><td>none</td><td>yes</td><td>monthly</td></tr><tr><td>Earn2Trade</td><td>Gauntlet Mini</td><td>3,000</td><td>2,000</td><td>0</td><td>at close</td><td>1,100 h.</td><td>30% cap</td><td>monthly</td></tr><tr><td>Earn2Trade</td><td>TCP</td><td>3,000</td><td>2,000</td><td>0</td><td>at close</td><td>1,100</td><td>30%</td><td>monthly</td></tr><tr><td>Take Profit T.</td><td>Test</td><td>3,000</td><td>2,000</td><td>0</td><td>at close</td><td>none</td><td>50% target</td><td>monthly</td></tr><tr><td>TradeDay</td><td>Quick Pay EOD</td><td>3,000</td><td>2,000</td><td>0</td><td>at close</td><td>—</td><td>30% target</td><td>monthly</td></tr><tr><td>MyFundedFutures</td><td>Rapid</td><td>3,000</td><td>2,000</td><td>+100</td><td>intraday</td><td>—</td><td>50% target</td><td>monthly</td></tr><tr><td>Legends Trading</td><td><eq>Apprentice^†</eq></td><td>3,000</td><td>2,000/2,500</td><td>—</td><td>at close</td><td>none</td><td>none/30%</td><td>monthly</td></tr></table>


“s.” soft daily loss limit; “h.” hard. $\dagger$ two official pages publish different values. 


## Fees and discounts

Fees in this industry are almost always advertised against a list price to which a permanent or renewed discount is applied. The table therefore distinguishes the advertised price from the one actually applicable on the access date, and records the nature of the discount. All calculations in the body of the paper use the effective price; by the homogeneity of (9), the derived quantities scale linearly with it. 

<table><tr><td>Firm</td><td>Product (50K)</td><td>List</td><td>Effective</td><td>Discount</td><td>Reset</td><td>Activation</td><td>Profit split</td></tr><tr><td>Apex</td><td>Eval. Intraday, single</td><td>249</td><td>24.90</td><td>-90% coupon</td><td>none</td><td>140</td><td>100%</td></tr><tr><td>Apex</td><td>Eval. Intraday, 5-pack</td><td>950</td><td>95 (19 each)</td><td>-90% coupon</td><td>none</td><td>140</td><td>100%</td></tr><tr><td>Apex</td><td>Eval. EOD, single</td><td>490</td><td>49</td><td>-90% coupon</td><td>none</td><td>140</td><td>100%</td></tr><tr><td>Apex</td><td>Eval. EOD, 5-pack</td><td>2,250</td><td>225 (45 each)</td><td>-90% coupon</td><td>none</td><td>140</td><td>100%</td></tr><tr><td>Apex</td><td>Eval. EOD no activ., single</td><td>1,190</td><td>119</td><td>-90% coupon</td><td>none</td><td>0</td><td>100%</td></tr><tr><td>Apex</td><td>Eval. EOD no activ., 5-pack</td><td>5,450</td><td>545 (109 each)</td><td>-90% coupon</td><td>none</td><td>0</td><td>100%</td></tr><tr><td>Tradeify</td><td>Growth, one-off</td><td>145</td><td>107</td><td>permanent</td><td>99</td><td>0</td><td>90%</td></tr><tr><td>Earn2Trade</td><td>TCP, monthly</td><td>190</td><td>114</td><td>-40%</td><td><eq>100^a</eq></td><td><eq>139^b</eq></td><td><eq>50/80\%^c</eq></td></tr><tr><td>Legends Trading</td><td>Apprentice, monthly</td><td>185</td><td>37</td><td>-80% code</td><td>—</td><td>99</td><td>90%</td></tr><tr><td>Take Profit Trader</td><td>Test, monthly</td><td>170</td><td>—</td><td>—</td><td>99</td><td>130</td><td>80%</td></tr><tr><td>Topstep</td><td>Combine, monthly</td><td>49</td><td>—</td><td>—</td><td>49</td><td>149</td><td>90%</td></tr><tr><td>Bulenox</td><td>Qualification, monthly</td><td>175</td><td>—</td><td>—</td><td>78</td><td>148</td><td>90%</td></tr><tr><td>Elite Trader Funding</td><td>1-Step, every 30 days</td><td>167</td><td>—</td><td>—</td><td>47</td><td><eq>150/157^d</eq></td><td><eq>90\%^d</eq></td></tr><tr><td>TradeDay</td><td>Quick Pay EOD, monthly</td><td>175</td><td>—</td><td>—</td><td>79</td><td>0</td><td>80%</td></tr><tr><td>MyFundedFutures</td><td>Rapid, monthly</td><td>157</td><td>—</td><td>—</td><td>157</td><td>0</td><td>90%</td></tr></table>

Amounts in dollars. “—” indicates that no current discount was found or that the parameter does not appear in an official source. $^{a}$ free when the subscription is rebilled. $^{b}$ deducted from the first payout, not paid up front. $^{c}$ in tranches according to the amount of each withdrawal. $^{d}$ two official pages publish different values. 

Three observations on the price structure, all verifiable in the table and none about the conduct of any firm. The first is that the discounts do not expire in the documented cases, so the list price is never actually charged, and using it as a model input values a contract that nobody buys. The second is that most of the industry charges by subscription, so that the cost depends on the duration of the attempt and therefore on the buyer's position size. The third is that seven of the firms examined charge an activation fee on passing the evaluation, which does not appear in the advertised price and which in one case reaches three times the monthly fee. 

## B Testing protocol

Four claims in the earlier version of this work rested on data that were not available. A protocol was built that fixes, for each one, the quantity to be measured, the minimum sample size and the numerical criterion that would refute it, sealed with their cryptographic hash before connecting to the data provider. 

The result of the first collection is that no claim is refuted, none is confirmed, and two of the four criteria were misspecified. One defined the breach variable in units of volatility itself, so that it built into the statistic the very invariance it was meant to test. The other required resolving a difference of one percentage point with twenty binary observations, when the smallest non-zero difference that statistic can take is five. Both are corrected and sealed again. 

The options book collection was run with the market closed and on delayed data, so none of its quantities is incorporated as a measurement. Its content does force one claim in the earlier version of this work to be narrowed: the absence of a two-sided book is not general across the chain, but specific to the delta band that hedging requires. The rest of the chain does quote in the same capture, which turns the observation into an internal control and rules out the possibility that it reflects a limitation of the data feed. 

That two pre-registered criteria were misspecified is a result of the exercise. Sealing prevents the criterion from being moved after the data are observed; it does not prevent it from being set in advance where it does not measure what is intended. 

## C Audit of estimates

The project's central estimate moved seven times. Four moves correspond to errors detected: a risk bound that the distribution violated, an incorrect pairing of adjusted quantities with raw quantities, the artefact of §7 and an accounting that mixed per-cycle quantities with per-attempt quantities. 

The remaining three are procedural deviations, and they are documented for their methodological value: allowing a single-observation sample to move the conclusion in both directions; choosing the summary statistic after observing the data, when the mean and the probability of depletion are the two most pessimistic ones in the face of an absorbing left tail; and a systematic asymmetry in the language, with unfavourable results presented as conclusions and favourable ones as provisional on identical evidence. The correction adopted was to write and run the decision rule for the next datum before accessing it. 

One regularity deserves mention. The four corrections in the first list moved the conclusion in the same direction: against the thesis the project was defending. The errors were not distributed at random. 

## D Reproducibility

The following are published: the implementation of the model of §2, with no external dependencies; the industry data file with the addresses and quotations for each parameter; the reconstruction of funded-phase mortality as a function of its two parameters; and the 1,833 sessions in aggregate form—date, range, adverse excursion and close—, which allow the simulated quantities to be reproduced without disclosing trading activity. 

The original simulation engine is not published. The published reconstruction of the quantity that depended on it reproduces its result with an error of 0.8% and requires no raw data. 

Note. Generative artificial intelligence tools were used in the preparation of this paper, for the writing and for part of the analytical development. The author has verified all results and assumes full responsibility for the content. Conflict of interest. The author traded the product that serves as the case study in §8. 

## References



Broadie, M., Glasserman, P. and Kou, S. (1997). A continuity correction for discrete barrier options. Mathematical Finance, 7(4), 325–349. 





Carr, P., Zhang, H. and Hadjiliadis, O. (2011). Maximum drawdown insurance. International Journal of Theoretical and Applied Finance, 14(8), 1195–1230. 





Commodity Futures Trading Commission (2023). CFTC Charges Traders Global Group Inc. Press release 8771-23. 





Feller, W. (1968). An Introduction to Probability Theory and Its Applications, vol. I, 3rd ed. Wiley. 





Goldberg, L. R. and Mahmoud, O. (2017). Drawdown: from practice to theory and back again. Mathematics and Financial Economics, 11(3), 275–297. 





Lehoczky, J. P. (1977). Formulas for stopped diffusion processes with stopping times based on the maximum. The Annals of Probability, 5(4), 601–607. 





Magdon-Ismail, M., Atiya, A. F., Pratap, A. and Abu-Mostafa, Y. S. (2004). On the maximum drawdown of a Brownian motion. Journal of Applied Probability, 41(1), 147–161. 





Merton, R. C. (1973). Theory of rational option pricing. The Bell Journal of Economics and Management Science, 4(1), 141–183. 





Taylor, H. M. (1975). A stopped Brownian motion formula. The Annals of Probability, 3(2), 234-246. 





Zhang, H., Leung, T. and Hadjiliadis, O. (2013). Stochastic modeling and fair valuation of drawdown insurance. Insurance: Mathematics and Economics, 53(3), 840–850. 

