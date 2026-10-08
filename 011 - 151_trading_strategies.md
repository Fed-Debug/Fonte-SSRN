# 151 Trading Strategies

**Zura Kakushadze** [^1] [^3] and **Juan Andrés Serur** [^2]

Quantigic® Solutions LLC, 1127 High Ridge Road #135, Stamford, CT 06905  
Free University of Tbilisi, Business School & School of Physics, 240, David Agmashenebeli Alley, Tbilisi, 0159, Georgia  
Universidad del CEMA, Av. Córdoba 374, C1054AAP, Ciudad de Buenos Aires, Argentina

*(August 17, 2018)*

> ZK: To my mother Mila and my children Mirabelle and Maximilien  
> JAS: To my parents, Claudio and Andrea, and my brother Emiliano

## Abstract
We provide detailed descriptions, including over 550 mathematical formulas, for over 150 trading strategies across a host of asset classes (and trading styles). This includes stocks, options, fixed income, futures, ETFs, indexes, commodities, foreign exchange, convertibles, structured assets, volatility (as an asset class), real estate, distressed assets, cash, cryptocurrencies, miscellany (such as weather, energy, inflation), global macro, infrastructure, and tax arbitrage. Some strategies are based on machine learning algorithms (such as artificial neural networks, Bayes, k-nearest neighbors). We also give: source code for illustrating out-of-sample backtesting with explanatory notes; around 2,000 bibliographic references; and over 900 glossary, acronym and math definitions. The presentation is intended to be descriptive and pedagogical.

---

## 1. Introduction and Summary

A trading strategy can be defined as a set of instructions to achieve certain asset holdings by some predefined times $t_{1},t_{2},...$ which holdings can (but need not) be null at one or more of these times. In many cases, the main objective of a trading strategy is to make a profit, i.e., to generate a positive return on its investment. However, some viable trading strategies are not always outright profitable as stand-alone strategies. E.g., a hedging strategy can be a part of a bigger plan, which itself can but need not be a trading strategy.

The purpose of these notes is to collect a variety of trading strategies in the context of finance across essentially all (or at least most frequently encountered) asset classes. We consider: derivatives such as options and futures; exchange-traded funds (ETFs); indexes; volatility; structured assets; convertible bonds; distressed assets; cryptocurrencies; miscellaneous assets such as weather and energy; and also trading strategies such as tax arbitrage and global macro. Some strategies are relatively simple and can be described in words, while many (in fact, most) require a much more detailed mathematical description, which we provide formulaically.

## 2. Options

### 2.1 Generalities
A European call option is a right (but not an obligation) to buy a stock at the maturity time $T$ for the strike price $k$ agreed on at time $t=0$. The claim for the call option $f^{call}(S_{T},k)=(S_{T}-k)^{+}$. Here $(x)^{+}=x$ if $x>0$, and $(x)^{+}=0$ if $x\le0$. 

Similarly, a European put option is a right (but not an obligation) to sell a stock at the maturity time $T$ for the strike price $k$ agreed on at time $t=0$. The claim for the put option is given by $f^{put}(S_{T},k)=(k-S_{T})^{+}$.

In the remainder of this section, unless stated otherwise, all options are for the same stock and have the same time-to-maturity (TTM). The moneyness abbreviations are: ATM = at-the-money, ITM = in-the-money, OTM = out-of-the-money.
Also: $f_{T}$ is the payoff at maturity $T$; $S_{0}$ is the stock price at the time $t=0$ of entering the trade; $S_{T}$ is the stock price at maturity; $C$ is the net credit received at $t=0$, and $D$ is the net debit required at $t=0$.

### 2.2 Strategy: Covered call
This strategy (a.k.a. "buy-write" strategy) amounts to buying stock and writing a call option with a strike price $K$ against the stock position. The trader's outlook on the stock price is neutral to bullish.
$$f_{T}=S_{T}-S_{0}-(S_{T}-K)^{+}+C=K-S_{0}-(K-S_{T})^{+}+C \quad (1)$$
$$S_{*}=S_{0}-C \quad (2)$$
$$P_{max}=K-S_{0}+C \quad (3)$$
$$L_{max}=S_{0}-C \quad (4)$$

### 2.3 Strategy: Covered put
This strategy (a.k.a. "sell-write" strategy) amounts to shorting stock and writing a put option with a strike price $K$ against the stock position. The trader's outlook is neutral to bearish.
$$f_{T}=S_{0}-S_{T}-(K-S_{T})^{+}+C=S_{0}-K-(S_{T}-K)^{+}+C \quad (5)$$
$$S_{*}=S_{0}+C \quad (6)$$
$$P_{max}=S_{0}-K+C \quad (7)$$
$$L_{max}=\text{unlimited} \quad (8)$$

### 2.4 Strategy: Protective put
This strategy (a.k.a. "married put" or "synthetic call") amounts to buying stock and an ATM or OTM put option with a strike price $K\le S_{0}$. The trader's outlook is bullish.
$$f_{T}=S_{T}-S_{0}+(K-S_{T})^{+}-D=K-S_{0}+(S_{T}-K)^{+}-D \quad (9)$$
$$S_{*}=S_{0}+D \quad (10)$$
$$P_{max}=\text{unlimited} \quad (11)$$
$$L_{max}=S_{0}-K+D \quad (12)$$

### 2.5 Strategy: Protective call
This strategy amounts to shorting stock and buying an ATM or OTM call option with a strike price $K\ge S_{0}$. The trader's outlook is bearish.
$$f_{T}=S_{0}-S_{T}+(S_{T}-K)^{+}-D=S_{0}-K+(K-S_{T})^{+}-D \quad (13)$$
$$S_{*}=S_{0}-D \quad (14)$$
$$P_{max}=S_{0}-D \quad (15)$$
$$L_{max}=K-S_{0}+D \quad (16)$$

### 2.6 Strategy: Bull call spread
This is a vertical spread consisting of a long position in a close to ATM call option with a strike price $K_{1}$, and a short position in an OTM call option with a higher strike price $K_{2}$.
$$f_{T}=(S_{T}-K_{1})^{+}-(S_{T}-K_{2})^{+}-D \quad (17)$$
$$S_{*}=K_{1}+D \quad (18)$$
$$P_{max}=K_{2}-K_{1}-D \quad (19)$$
$$L_{max}=D \quad (20)$$

### 2.12 Strategy: Long combo
This strategy (a.k.a. "long risk reversal") amounts to buying an OTM call option with a strike price $K_{1}$ and selling an OTM put option with a strike price $K_{2}$. We have $(K_{1}>K_{2})$:
$$f_{T}=(S_{T}-K_{1})^{+}-(K_{2}-S_{T})^{+}-H \quad (41)$$
$$S_{*}=K_{1}+H, \quad H>0 \quad (42)$$
$$S_{*}=K_{2}+H, \quad H<0 \quad (43)$$
$$K_{2}\le S_{*}\le K_{1}, \quad H=0 \quad (44)$$

---

## 3. Stocks

### 3.1 Strategy: Price-momentum
Empirically, there appears to be certain "inertia" in stock returns known as the momentum effect. Let $t$ denote time measured in the units of 1 month. Let $P_{i}(t)$ be the time series of prices for the stock labeled by $i$.

$$R_{i}(t)=\frac{P_{i}(t)}{P_{i}(t+1)}-1 \quad (266)$$
$$R_{i}^{cum}=\frac{P_{i}(S)}{P_{i}(S+T)}-1 \quad (267)$$
$$R_{i}^{mean}=\frac{1}{T}\sum_{t=S}^{S+T-1}R_{i}(t) \quad (268)$$
$$R_{i}^{risk.adj}=\frac{R_{i}^{mean}}{\sigma_{i}} \quad (269)$$
$$\sigma_{i}^{2}=\frac{1}{T-1}\sum_{t=S}^{S+T-1}(R_{i}(t)-R_{i}^{mean})^{2} \quad (270)$$

### 3.8 Strategy: Pairs trading
This dollar-neutral strategy amounts to identifying a pair of historically highly correlated stocks (stock A and stock B) and, when a mispricing occurs, shorting the "rich" stock and buying the "cheap" stock.
$$R_{A}=\ln\left(\frac{P_{A}(t_{2})}{P_{A}(t_{1})}\right) \quad (285)$$
$$R_{B}=\ln\left(\frac{P_{B}(t_{2})}{P_{B}(t_{1})}\right) \quad (286)$$

Next, let $\tilde{R}_{A}$ and $\tilde{R}_{B}$ be the demeaned returns:
$$\overline{R}=\frac{1}{2}(R_{A}+R_{B}) \quad (287)$$
$$\tilde{R}_{A}=R_{A}-\overline{R} \quad (288)$$
$$\tilde{R}_{B}=R_{B}-\overline{R} \quad (289)$$

The numbers of shares $Q_{A}, Q_{B}$ to short/buy are fixed by the total desired dollar investment $I$ and the requirement of dollar-neutrality:
$$P_{A}|Q_{A}|+P_{B}|Q_{B}|=I \quad (290)$$
$$P_{A}Q_{A}+P_{B}Q_{B}=0 \quad (291)$$

### 3.18 Strategy: Statistical arbitrage optimization
Let $C_{ij}$ be the sample or model covariance matrix for the $N$ stock returns in a portfolio. Let $D_{i}$ be the dollar holdings. The expected portfolio P&L $P$, volatility $V$ and Sharpe ratio $S$ are given by:
$$P=\sum_{i=1}^{N}E_{i}D_{i} \quad (342)$$
$$V^{2}=\sum_{i,j=1}^{N}C_{ij}D_{i}D_{j} \quad (343)$$
$$S=P/V \quad (344)$$

---

## Appendix A: R Source Code for Backtesting

In this appendix we give the R source code for backtesting intraday strategies. The sole purpose of this code is to illustrate some simple tricks for doing out-of-sample backtesting.

```r
qrm.backtest <- function (days = 252 * 5, d.r = 21, d.addv = 21,
n.addv = 2000, inv.lvl = 2e+07, bnds = .01, incl.cost = F)
{
    calc.ix <- function(i, d, d.r)
    {
        k1 <- d - i
        k1 <- trunc(k1 / d.r)
        ix <- d - k1 * d.r
        return(ix)
    }

    calc.mv.avg <- function(x, days, d.r)
    {
        y <- matrix(0, nrow(x), days)
        for(i in 1:days)
            y[, i] <- rowMeans(x[, i:(i + d.r - 1)])
        return(y)
    }

    calc.mv.sd <- function(x, days, d.r)
    {
        y <- matrix(0, nrow(x), days)
        for(i in 1:days)
            y[, i] <- apply(x[, i:(i + d.r - 1)], 1, sd)
        return(y)
    }

    read.x <- function(file)
    {
        x <- read.delim(file, as.is = T)
        x <- as.matrix(x)
        mode(x) <- "numeric"
        return(x)
    }

    calc.sharpe <- function (pnl, inv.lvl)
    {
        print(sum(pnl, na.rm = T))
        print(mean(pnl, na.rm = T) * 252 / inv.lvl * 100)
        print(mean(pnl, na.rm = T) / sd(pnl, na.rm = T) * sqrt(252))
    }

    ret <- read.x("nrm.ret.txt")
    open <- read.x("nrm.open.txt")
    close <- read.x("nrm.close.txt")
    vol <- read.x("nrm.vol.txt")
    prc <- read.x("nrm.prc.txt")

    addv <- calc.mv.avg(vol * close, days, d.addv)
    ret.close <- log(prc[, -ncol(prc)]/prc[, -1])
    tr <- calc.mv.sd(ret.close, days, d.r)

    ret <- ret[, 1:days]
    prc <- prc[, 1:days]
    close <- close[, 1:days]
    open <- open[, 1:days]
    close1 <- cbind(close[, 1], close[, -ncol(close)])
    open1 <- cbind(close[, 1], open[, -ncol(open)])

    pnl <- matrix(0, nrow(ret), ncol(ret))
    des.hold <- matrix(0, nrow(ret), ncol(ret))

    for(i in 1:ncol(ret))
    {
        ix <- calc.ix(i, ncol(ret), d.r)
        if(i == 1)
            prev.ix <- 0
        if(ix != prev.ix)
        {
            liq <- addv[, ix]
            x <- sort(liq)
            x <- x[length(x):1]
            take <- liq >= x[n.addv]
            r1 <- ret.close[take, (ix:(ix + d.r - 1))]
            
            rr <- qrm.cov.pc(r1)
            cov.mat <- rr$inv.cov
            prev.ix <- ix
        }
        w.int <- rep(1, sum(take))
        ret.opt <- ret ### DELAY-0 MEAN-REVERSION
        
        if(incl.cost)
        {
            lin.cost <- tr[take, i] / addv[take, i]
            lin.cost <- 1e-3 * lin.cost / mean(lin.cost)
        }
        else
            lin.cost <- 0
            
        ret.lin.cost <- ret.opt[take, i]
        ret.lin.cost <- sign(ret.lin.cost) * pmax(abs(ret.lin.cost) - lin.cost, 0)
        
        des.hold[take, i] <- as.vector(bopt.calc.opt(ret.lin.cost, w.int,
            cov.mat, bnds * liq[take]/inv.lvl, -bnds * liq[take]/inv.lvl))
            
        des.hold[take, i] <- -des.hold[take, i] * inv.lvl / sum(abs(des.hold[take, i]))
        pnl[take, i] <- des.hold[take, i] * (close1[take, i]/open1[take, i] - 1)
        pnl[take, i] <- pnl[take, i] - abs(des.hold[take, i]) * lin.cost
    }

    des.hold <- des.hold[, -1]
    pnl <- pnl[, -1]
    pnl <- colSums(pnl)

    calc.sharpe(pnl, inv.lvl)
    trd.vol <- 2 * sum(abs(des.hold/open1[, -1]))
    cps <- 100 * sum(pnl) / trd.vol
    print(cps)
}
```

[^1]: Zura Kakushadze, Ph.D., is the President and CEO of Quantigic® Solutions LLC, and a Full Professor at Free University of Tbilisi. Email: zura@quantigic.com
[^2]: Juan Andrés Serur, M.Fin., is an Assistant Professor at University of CEMA. Email: jaserur15@ucema.edu.ar
[^3]: DISCLAIMER: This address is used by the corresponding author for no purpose other than to indicate his professional affiliation as is customary in publications.

# Market Microstructure Invariance: Theory and Empirical Tests<sup>∗</sup>

Albert S. Kyle University of Maryland akyle@rhsmith.umd.edu 

Anna A. Obizhaeva New Economic School aobizhaeva@nes.ru 

October 17, 2014<sup>†</sup> 

## Abstract

Using the intuition that financial markets transfer risks in business time, we define “market microstructure invariance” as the hypothesis that the distribution of risk transfers (“bets”), transactions costs, market resiliency, and pricing accuracy are constant across assets when measured per unit of business time. A structural model of risk-neutral informed trading and noise trading with linear price impact shows that invariance relationships arise when the costs of informative signals are constant. The invariance hypotheses imply that microstructure variables like bet size and transactions costs have empirically testable relationships to observable dollar volume and volatility. Since portfolio transitions can be viewed as natural experiments for measuring transactions costs and individual orders can be treated as proxies for bets, we test these empirical predictions using a dataset of 400,000+ portfolio transition orders and find that the predictions closely match the data. 

Keywords: market microstructure, liquidity, bid-ask spread, market impact, transactions costs, market eficiency, resiliency, order size, number of orders, portfolio transitions, eficient markets hypothesis, econophysics, invariance, scaling, structural estimation. 

This paper proposes a modeling principle for financial markets that we call “market microstructure invariance.” When portfolio managers trade financial assets, they can be modeled as playing trading games in which risks are transferred. Market microstructure invariance begins with the intuition that these risk transfers, which we call “bets,” take place in business time. The rate at which business time passes— market “velocity”—is the rate at which new bets arrive into the market. For actively traded assets, business time passes quickly; for inactively traded assets, business time passes slowly. Market microstructure invariance hypothesizes that microstructure characteristics, which vary when measured in units of calendar time, become constants—“microstructure invariants”—when measured in units of business time. 

In section 1, we formulate the three invariance principles as empirical hypotheses, conjectured to apply for all securities and across time: 

• The distribution of the dollar risk transferred by a bet is the same when the dollar risk it transfers is measured in units of business time. 

• The dollar expected transactions cost of executing a bet is the same function of the size of the bet when its size is measured as the dollar risk it transfers in units of business time. 

• Pricing accuracy is the same if its reciprocal is scaled by returns volatility per unit of business time, and market resiliency is the same if it is measured in units of business time. 

When measured in calendar time, invariance implies that the size distribution of risk transfers, the number of bets, illiquidity, bid-ask spreads, market impact, pricing accuracy, and resiliency become proportional to powers of market velocity. Market velocity itself is proportional to the two-thirds power of calendar-time “trading activity,” which we define as the product of empirically observable dollar volume and returns volatility. This gives specific testable empirical content to the invariance hypotheses. For example, the size distribution of bets, as a fraction of trading volume, is inversely proportional to the two-thirds power of trading activity. The transactions cost function is the product of an invariant cost function of bet size and an assetspecific measure of illiquidity, which is proportional to the cube root of the ratio of returns variance to dollar volume. Other market microstructure characteristics are also proportional to powers of observable dollar volume and returns volatility. 

In section 2, we develop a structural model showing that all three microstructure invariance hypotheses are consistent with a dynamic infinite-horizon model of market microstructure with risk-neutral informed trading, noise trading, market making, and endogenous production of information. The invariance relationships are derived under the assumption that the efort required to generate one discrete bet does not vary across stocks and time. Since bets are based on the arrival of discrete chunks of information, the structural model describes how the invariance relationships reflect diferences in the granularity of information flows across markets. The invariance of pricing accuracy and market resiliency requires the additional assumption that private information has the same signal-to-noise ratio across markets. 

In section 3, we show how invariance can be used to derive testable implications from theoretical models of market microstructure. Invariance provides guidance on how to construct good empirical proxies for some dificult-to-observe microstructure concepts such as “order imbalances.” It imposes a discipline on empirical tests by showing how to specify regressions and scale explanatory variables so that estimated regression coeficients can be assumed to be constant across observations. 

In section 4, we describe the portfolio transitions data used to test invariance relationships concerning bet size and transactions costs. The dataset consists of more than 400,000 portfolio transition orders executed over the period 2001 through 2005 by a leading vendor of portfolio transition services. Portfolio transitions are used by institutional sponsors to transfer funds from legacy portfolio managers to new managers in order to replace fund managers, change asset allocations, or accommodate cash inflows and outflows. Portfolio transitions provide a good natural experiment for identifying bets and measuring transactions costs. 

In section 5, we examine whether bet sizes are consistent with the invariance hypothesis under the identifying assumption that portfolio transition orders are proportional to bets. As implied by invariance, the size distribution of the product of the ratio of order size as a fraction of average daily volume and the two-thirds power of trading activity indeed resembles an invariant distribution. Regression analysis also confirms this finding. 

The portfolio transition orders have a log-normal distribution with estimated logvariance of 2.53 (figure 2). The log-normal empirical distribution of order size (a bi-modal “signed” log-normal distribution for buy and sell orders) has much more kurtosis than the normal distribution often assumed for analytical convenience in the theoretical literature. The fat tails of the estimated log-normal distribution suggest that very large bets represent a large fraction of trading volume and generate an even larger fraction of returns variance. Execution of large bets may trigger noticeable market dislocations. 

In section 6, we use implementation shortfall to examine whether transactions costs are consistent with the invariance hypothesis. Even though statistical tests usually reject invariance hypotheses, the results are economically close to those implied by invariance. Consistent with invariance, transactions cost functions can be closely approximated by the product of an asset-specific illiquidity measure (proportional to the cube root of the ratio of returns variance to dollar volume) and an invariant function of bet size (figure 5). Invariance itself does not impose a particular form on the transactions cost function. Empirically, both a linear model and a square root model explain transactions costs well. A square root model explains transactions costs for orders in the 90th to 99th percentiles better than a linear model; a linear model explains transaction costs for the largest 1% of orders slightly better than the square root model. Quoted spreads are also consistent with the predictions of invariance. 

In section 7, we present estimates of the distribution of bet size, the number of bets, and linear and square root transactions cost functions based on calibration of a handful of parameters. 

The potential benefits of invariance principles for empirical market microstructure are enormous. In the area of transactions cost measurement, for example, controlled experiments are costly and natural experiments are rare; even well-specified tests of transactions cost models tend to have low statistical power. Market microstructure invariance defines parsimonious structural relationships leading to precise predictions about how various microstructure characteristics, including transactions costs, vary across stocks with diferent dollar volume and volatility. These predictions can be tested with structural estimates of a handful of parameters using limited data from many diferent stocks. 

The idea of using invariance principles in finance and economics, at least implicitly, is not new. The theory of Modigliani and Miller (1958) is an example of an invariance principle. The idea of measuring trading in financial markets in business time or transaction time is not new either. The “time-change” literature has a long history, beginning with Mandelbrot and Taylor (1967), who link business time to transactions, and Clark (1973), who links business time to volume. Allais (1956) and Allais (1966) are other early examples of models with time deformation. More recent papers include Hasbrouck (1999), An´e and Geman (2000), Dufour and Engle (2000), Plerou et al. (2000), and Derman (2002). Invariance is not based on the idea that returns volatility is constant in transaction time, like some of these papers; instead, invariance is based on the diferent idea that the dollar risk transferred by the average bet is the same in bet time. 

Given values of a tiny number of proportionality constants, the invariance relationships allow microscopic features of the market for a financial asset to be inferred from macroscopic market characteristics such as dollar volume and returns volatility. The units in which these proportionality factors are measured are consistent with their intended economic content. Making empirical predictions on the basis of invariance principles is well established in physics. Our analysis is similar in spirit to inferring the size and number of molecules in a mole of gas from measurable large-scale physical quantities. It is also similar to methods physicists use to model turbulence. 

In both physics and market microstructure, application of invariance principles requires that certain assumptions be met. For example, the laws of physics hold in simplest form for objects traveling in a vacuum but have to be modified when resistance from air generates friction. Similarly, in market microstructure, invariance relationships may hold only under idealized conditions. For example, the predic tions of invariance may hold most closely when tick size is small, market makers are competitive, and transactions fees and taxes are minimal. Invariance principles provide a benchmark from which the importance of frictions such as a large tick size, non-competitive market access, or high fees and taxes can be measured. 

## 1 Market Microstructure Invariance as an Empirical Hypothesis

Market microstructure characteristics such as order size, order arrival rate, price impact, bid-ask spread, pricing accuracy, and market resiliency vary across assets and across time. We define “market microstructure invariance” as the empirical hypothesis that this variation almost disappears when these characteristics are examined at an asset-specific “business-time” scale which measures the rate at which risk transfer takes place. 

Although the discussion below is based on cross-sectional implications of invariance for equity markets for individual stocks, we believe that invariance principles generalize to markets for commodities, bonds, currencies, and aggregate indices such as exchange-traded funds and stock index futures contracts. For simplicity, we assume that a bet transfers only idiosyncratic risk about a single security, not market risk; modeling both idiosyncratic and market risks simultaneously takes us beyond the scope of this paper. 

Notation. In the market for an individual stock, institutional asset managers buy and sell shares to implement “bets.” We think of a bet as a decision to acquire a longterm position of a specific size in a stock, distributed approximately independently from other such decisions. Intermediaries with short-term trading strategies—market makers, high frequency traders, and other arbitragers—clear markets by taking the other side of bets placed by long-term traders. 

Over short periods of time, we assume that the bet arrival rate can be approximated by a compound Poisson process. Let γ denote the expected bet arrival rate of independently distributed bets, measured in bets per calendar day. Let $\tilde { Q }$ denote a random variable whose probability distribution represents the signed size of bets; Q<sup>˜</sup> is measured in shares (positive for buys, negative for sells) with $E \{ \tilde { Q } \} = 0$ . The bet arrival rate γ measures market velocity, the rate at which business time passes for a particular stock.<sup>1</sup> 

Bets can be dificult for researchers to observe. Consider an asset manager who places one bet by purchasing 100,000 shares of IBM stock. The bet might be implemented by placing orders over several days, and each of the orders might be “shredded” into many small trades. Since bets represent independent increments in the intended order flow, the various trades which implement the bet must all be added together to recover the size of the original bet. Thus, individual bets are impossible to reconstruct from publicly disseminated records of time-stamped prices and quantities such as those contained in the Trade and Quote (TAQ) database. 

Similarly, if an analyst issues a buy recommendation to ten diferent customers and each of the customers quickly places executable orders to buy 10,000 shares, it might be appropriate to think of the ten orders as one bet for 100,000 shares. The bet results from a new idea, which can be shared. The ten individual orders lack statistical independence. 

We assume that, on average, each unit of betting volume results in $\zeta$ units of total volume, i.e., one unit of betting volume leads to $\zeta - 1$ units of intermediation volume. On a given calendar day, expected trading volume (in shares) is given by $V : = \zeta / 2 \cdot \gamma \cdot E | \tilde { Q } | ;$ ; dividing by two implies that a buy-bet matched to a sell-bet is counted as one unit of volume, not two. We define expected “betting volume” V<sup>¯</sup> by 

$$
\bar {V} := \gamma \cdot E \{| \tilde {Q} | \} = \frac {2}{\zeta} \cdot V.\tag{1}
$$

We can estimate expected betting volume $\bar { V }$ by combining an estimate of expected market volume V with a value for the “volume multiplier” ζ. If all trades are bets and there are no intermediaries, then $\zeta = 1$ , since each unit of trading volume matches a buy-bet with a sell-bet. If a monopolistic specialist intermediates all bets without involvement of other intermediaries, then $\zeta = 2$ . If each bet is intermediated by diferent market makers, each of whom lays of inventory by trading with other market makers, then $\zeta = 3$ . If positions are passed around among multiple intermediaries, then $\zeta \geq 4$ 

Define “returns volatility” σ as the percentage standard deviation of a stock’s daily returns. Some price fluctuations result from release of information directly without trading, such as overnight news announcements. Let $\psi ^ { 2 }$ denote the fraction of returns variance $\sigma ^ { 2 }$ resulting from order flow imbalances, which are ultimately related to the arrival bets. We define “betting volatility” as the standard deviation of returns resulting from bet-related order flow imbalances: 

$$
\bar {\sigma} := \psi \cdot \sigma .\tag{2}
$$

We can estimate betting volatility $\bar { \sigma }$ by combining an estimate of returns volatility σ with a value for the “volatility multiplier” ψ. Let $P$ denote the price of the stock; then dollar “betting volatility” is $P \cdot { \bar { \sigma } } = \psi \cdot P \cdot \sigma$ 

For simplicity, we assume that ζ and ψ are constant across stocks and time. 

Invariance of Bets. Market microstructure invariance hypothesizes that the distribution of the dollar risk transferred by a bet is the same when the dollar risk it transfers is measured in units of business time. 

A bet of dollar size $P \cdot \tilde { Q }$ generates a standard deviation of dollar mark-to-market gains or losses equal to $P \cdot | \tilde { Q } | \cdot \bar { \sigma } \cdot \gamma ^ { - 1 / 2 }$ in one unit of business time $1 / \gamma$ . The signed standard deviation $P \cdot \tilde { Q } \cdot \bar { \sigma } \cdot \gamma ^ { - 1 / 2 }$ measures both the direction and the size of the risk transfer resulting from the bet. Instead of measuring the size of a bet as a number of shares ${ \tilde { Q } } .$ the size of the bet can alternatively be measured as the amount of risk it transfers per unit of business time, which we denote as $\tilde { I } .$ Therefore, $\tilde { I }$ is defined by 

$$
\tilde {I} := P \cdot \tilde {Q} \cdot \bar {\sigma} \cdot \gamma^ {- 1 / 2}.\tag{3}
$$

Invariance of bets is the hypothesis that the distribution of the random variable $\tilde { I }$ is the same across stocks and time. In this sense, the distribution of risk transfer $\tilde { I }$ is a market microstructure invariant. 

By analogy with bets, we define “trading activity” W as the product of expected dollar trading volume $P \cdot V$ and calendar returns volatility $\sigma ,$ i.e., $W : = \sigma \cdot P \cdot V$ Trading activity measures the aggregate dollar risk transferred by all bets during one calendar day. Similarly, define “betting activity” $\bar { W }$ as the product of dollar betting volume $P \cdot { \bar { V } }$ and betting volatility ¯σ, i.e., $\bar { W } : = \bar { \sigma } \cdot P \cdot \bar { V } . ^ { 2 }$ Given values of the volume multiplier $\zeta$ and the volatility multiplier $\psi _ { ; }$ , we can convert more-easilyobserved trading activity $W$ into less-easily-observed betting activity $\bar { W }$ using the relationship $\bar { W } = W \cdot 2 \psi / \zeta$ 

Equations (1) and (3) imply that betting activity $\bar { W }$ can be expressed as a function of the unobservable speed of business time $\gamma$ as: 

$$
\bar {W} = \bar {\sigma} \cdot P \cdot \bar {V} = \bar {\sigma} \cdot P \cdot \gamma \cdot E \{| \tilde {Q} | \} = \gamma^ {3 / 2} \cdot E \{| \tilde {I} | \}.\tag{4}
$$

Invariance of bets therefore makes it possible to infer the bet arrival rate $\gamma$ and the average bet size $E \{ | \tilde { Q } | \}$ from the level of betting activity $\bar { W }$ , up to some proportionality constant $E \{ | \tilde { I } | \}$ which does not vary across stocks. Define $\iota : = ( \bar { E } \{ | \bar { \tilde { I } } | \} ) ^ { - 1 / 3 }$ ; since $\tilde { I }$ has an invariant probability distribution, $\iota$ is a constant. Solving equation (4) for $\gamma$ in terms of W<sup>¯</sup> and $E \{ | \tilde { Q } | \}$ yields 

$$
\gamma = \bar {W} ^ {2 / 3} \cdot \iota^ {2}, E \{| \tilde {Q} | \} = \bar {W} ^ {1 / 3} \cdot \frac {1}{P \cdot \bar {\sigma}} \cdot \iota^ {- 2}.\tag{5}
$$

The shape of the entire distribution of bet size $\tilde { Q }$ can be obtained by plugging $\gamma$ from equation (5) into equation (3). Expressing bet size $\tilde { Q }$ as a fraction of expected betting volume $\bar { V }$ , we obtain 

$$
\frac {\tilde {Q}}{\bar {V}} = \bar {W} ^ {- 2 / 3} \cdot \tilde {I} \cdot \iota .\tag{6}
$$

Equations (5) and $( 6 )$ summarize the implications of invariance for bet size and arrival rate. We test these implications in section 5. 

The specific exponents $2 / 3$ and $1 / 3$ in equation (5) have simple intuition. Suppose business time $\gamma$ speeds up by a factor of 4, but volatility in calendar time ¯σ does not change. Then volatility per unit of business time $\bar { \boldsymbol { \sigma } } \cdot \boldsymbol { \gamma } ^ { - 1 / 2 }$ decreases by a factor of $2$ . 

The invariance principle (3) therefore requires bet size $\tilde { Q }$ to increase by a factor of 2 to keep the distribution of <sup>˜</sup>I invariant. The resulting increase in betting volume by a factor of $8 = 4 ^ { 3 / 2 }$ can be decomposed into an increase in the number of bets by a factor of $8 ^ { 2 / 3 } = 4$ and the size of bets by a factor of $8 ^ { 1 / 3 } = 2$ 

As betting activity increases, the number of bets increases twice as fast as their size. This specific relationship between the number and size of bets lies at the very heart of invariance. Our hypotheses about transactions costs, price impact, pricing accuracy, and market resiliency are based on the order flow having this specific composition. 

Invariance of Transactions Costs. Market microstructure invariance also makes empirical predictions about transactions costs. Market microstructure invariance hypothesizes that the dollar expected transactions cost of executing a bet is the same function of the size of the bet when its size is measured as the dollar risk it transfers in units of business time. 

Since the risk transferred per unit of business time by a bet of $\tilde { Q }$ shares is measured by $\tilde { I } = P { \cdot } \tilde { Q } { \cdot } \bar { \sigma } { \cdot } \gamma ^ { - 1 / 2 }$ , invariance of trading costs implies that there exists an “invariant expected transactions cost function” $C _ { B } ( { \tilde { I } } )$ which measures in dollars the expected execution cost of transferring the risk represented by $\tilde { Q } = \tilde { I } \cdot ( \bar { \sigma } P \gamma ^ { - 1 / 2 } ) ^ { - 1 }$ shares. The dollar transactions cost function $C _ { B } ( \tilde { I } )$ is a market microstructure invariant. 

Consider the following numerical example. Suppose that a 99th percentile bet in stock A is for $10 million (e.g., 100, 000 shares at $100 per share) while a 99th percentile bet in stock B is for $1 million (e.g., 100, 000 shares at $10 per share). Even though the dollar sizes of these bets are diferent, stock A may be more actively traded than stock $B ,$ and therefore its returns volatility per unit of business time is lower. Since both bets occupy the same percentile in the bet size distribution for their respective stocks, the invariance of the distribution of bet size implies that the value of $\dot { \tilde { I } }$ is the same in both cases. Furthermore, even though the bet in stock A has 10 times the dollar value of the bet in stock $B ,$ invariance of transactions costs implies that the expected cost of executing each bet $C _ { B } ( { \tilde { I } } )$ is the same in dollars, because both bets transfer the same amount of risk per stock-specific unit of business time. Measured in basis points, however, invariance implies that the transactions cost for Stock B is 10 times greater than for stock A. 

Let $C ( \tilde { Q } )$ denote the stock-specific expected cost of executing a bet of $\tilde { Q }$ shares, expressed as a fraction of the notional value of the bet $| P \cdot \tilde { Q } | , \mathrm { i . e . }$ , in units of $1 0 ^ { - 4 }$ basis points. Define the unconditional expected cost $\bar { C } _ { B } : = \dot { E } \{ \dot { C } _ { B } ( \tilde { I } ) \}$ . From equation (3), it follows that the formula for percentage costs is given by 

$$
C (\tilde {Q}) = \frac {C _ {B} (\tilde {I})}{| P \cdot \tilde {Q} |} = \frac {\bar {C} _ {B}}{E \{| P \cdot \tilde {Q} | \}} \cdot \frac {C _ {B} (\tilde {I}) / \bar {C} _ {B}}{| \tilde {I} | / E \{| \tilde {I} | \}}.\tag{7}
$$

Let $f ( \tilde { I } ) : = [ C _ { B } ( \tilde { I } ) / \bar { C } _ { B } ] / [ | \tilde { I } | / E \{ | \tilde { I } | \} ]$ denote the invariant “average cost function” for executing a bet <sup>˜</sup>I. This function is the ratio of $C _ { B } ( { \tilde { I } } )$ to $| \tilde { I } |$ when both $C _ { B } ( { \tilde { I } } )$ and $| \tilde { I } |$ are expressed as multiples of their means. For example, if I denotes a bet that is 5 times greater than than an average unsigned bet of size $E \{ | \tilde { I } | \}$ and such a bet has a dollar transactions cost 10 times greater than the mean cost $\bar { C } _ { B }$ , then $f ( I ) = 2$ 

Let $1 / L : = \bar { C } _ { B } / E \{ | P \cdot \tilde { Q } | \}$ be an asset-specific measure of illiquidity equal to the dollar-volume-weighted expected cost of executing a bet. For an asset manager who places many bets in the same stock, this expresses expected transactions cost as a fraction of the dollar value traded $( 1 0 ^ { - 4 }$ basis points). Equation (5) yields 

$$
\frac {1}{L} := \iota^ {2} \bar {C} _ {B} \cdot \bar {\sigma} \bar {W} ^ {- 1 / 3} = \iota^ {2} \bar {C} _ {B} \cdot \left(\frac {\bar {\sigma} ^ {2}}{P \cdot \bar {V}}\right) ^ {1 / 3}.\tag{8}
$$

Recall that $\iota : = ( E \{ | \tilde { I } | \} ) ^ { - 1 / 3 }$ and $\bar { C } _ { B }$ are constants in this equation. 

Plugging the definitions of $f ( { \tilde { I } } )$ and $1 / L$ into equation (7) makes it possible to write the expected percentage cost function $C ( Q )$ as the product of the asset-specific illiquidity measure $1 / L$ and an invariant transactions cost function $f ( { \tilde { I } } )$ 

$$
C (\tilde {Q}) = \frac {1}{L} \cdot f (\tilde {I}).\tag{9}
$$

This is an important decomposition of transaction cost functions. 

When the bet size is measured as a fraction of betting volume $\tilde { Q } / \bar { V }$ , the cost function $C ( Q )$ can be expressed conveniently in terms of betting activity $\bar { W }$ and invariant constants ι and $\bar { C } _ { B }$ as 

$$
C (\tilde {Q}) = \bar {\sigma} \bar {W} ^ {- 1 / 3} \cdot \iota^ {2} \bar {C} _ {B} \cdot f \left(\frac {\bar {W} ^ {2 / 3}}{\iota} \cdot \frac {\tilde {Q}}{\bar {V}}\right).\tag{10}
$$

We test this specification empirically in section 6. 

To implement L empirically, it is simpler to define L in terms of expected dollar trading volume $P \cdot V$ and expected returns volatility σ rather than in terms of dollar betting volume $P \cdot { \bar { V } }$ and betting volatility ¯σ. Using equations (1) and (2), we have 

$$
\frac {1}{L} = (\frac {\zeta}{2} \psi^ {2}) ^ {1 / 3} \cdot \iota^ {2} \bar {C} _ {B} \cdot \left(\frac {\sigma^ {2}}{P \cdot V}\right) ^ {1 / 3}.\tag{11}
$$

The idea that liquidity is related to dollar volume per unit of returns variance $P \cdot V / \sigma ^ { 2 }$ is intuitive. Traders believe that transactions costs are low in markets with high dollar volume and high in markets with high volatility. If the volume multiplier ζ and the volatility multiplier ψ do not vary across stocks, then $L \propto [ P \cdot V / \sigma ^ { 2 } ] ^ { 1 / 3 }$ becomes a simple index of liquidity. 

The liquidity measure $L = [ \iota ^ { 2 } \bar { C } _ { B } ] ^ { - 1 } \cdot [ P \cdot \bar { V } / \bar { \sigma } ^ { 2 } ] ^ { 1 / 3 }$ is an intuitive and practical alternative to other measures of liquidity, such as Amihud (2002) and Stambough and Pastor (2003). The value of L can easily be calibrated from price and volume data provided by The Center for Research in Security Prices (CRSP).<sup>3</sup> 

Invariance does not imply a specific functional form for function $f ( . )$ . In our analysis, we focus on two specific functional forms: linear price impact costs and square root price impact costs. For both functional forms, we also allow a constant bid-ask spread cost component. The linear price impact function is consistent with price impact models based on adverse selection, such as Kyle (1985). The square root price impact function is consistent with empirical findings in the econophysics literature, such as Gabaix et al. (2006), although these results are based on single trades rather than bets; some papers in this literature, such as Almgren et al. (2005), find an exponent closer to 0.60 than the square root exponent of 0.50. 

For the linear model, we write $f ( { \tilde { I } } )$ as the sum of a bid-ask spread component and a linear price impact cost component, $f ( \tilde { I } ) : = ( \iota ^ { 2 } \bar { C } _ { B } ) ^ { - 1 } \cdot \kappa _ { 0 } + ( \iota \bar { C } _ { B } ) ^ { - 1 } \cdot \kappa _ { I } \cdot | \tilde { I } |$ , where invariance implies that the bid-ask spread cost parameter $\kappa _ { 0 }$ , the market impact cost parameter $\kappa _ { I }$ , and the constants ι and $\bar { C } _ { B }$ do not vary across stocks. Since the specific coeficients $\iota ^ { 2 } \bar { C } _ { B }$ and $\iota \bar { C } _ { B }$ are chosen to cancel out in a nice way, equation (9) implies that the proportional cost function $C ( \tilde { Q } )$ has the simple form 

$$
C (\tilde {Q}) = \bar {\sigma} \left(\kappa_ {0} \cdot \bar {W} ^ {- 1 / 3} + \kappa_ {I} \cdot \bar {W} ^ {1 / 3} \cdot \frac {| \tilde {Q} |}{\bar {V}}\right).\tag{12}
$$

When bet sizes are measured as a fraction of expected betting volume and transactions costs are measured in basis points, bid-ask spread costs are decreasing in betting activity $\bar { W }$ and market impact costs are increasing in betting activity $\bar { W }$ . When transactions costs in basis points are further scaled in units of betting volatility ${ \bar { \sigma } } .$ equation (12) says that bid-ask spread costs are proportional $\bar { W } ^ { - 1 / 3 }$ and market impact costs are proportional to $\bar { W } ^ { 1 / 3 }$ for a given fraction of betting volume. 

For the square root model, we write $f ( { \tilde { I } } )$ as the sum of a bid-ask spread component and a square root function of $| \tilde { I } |$ , obtaining $f ( \tilde { I } ) : = ( \iota ^ { 2 } \bar { C } _ { B } ) ^ { - 1 } \kappa _ { 0 } + ( \iota ^ { 3 / 2 } \bar { C } _ { B } ) ^ { - 1 } \kappa _ { I } \cdot | \tilde { I } | ^ { 1 / 2 }$ 2 where invariance implies that $\kappa _ { 0 } , ~ \kappa _ { I } , ~ \iota$ , and $\bar { C } _ { B }$ do not vary across stocks. The proportional cost function $C ( \tilde { Q } )$ from (9) is given by 

$$
C (\tilde {Q}) = \bar {\sigma} \left(\kappa_ {0} \cdot \bar {W} ^ {- 1 / 3} + \kappa_ {I} \cdot \left| \frac {\tilde {Q}}{\bar {V}} \right| ^ {1 / 2}\right).\tag{13}
$$

When transactions costs are measured in units of betting volatility ${ \bar { \sigma } } ,$ , bid-ask spread costs remain proportional to $\bar { W } ^ { - 1 / 3 }$ , but the square root model implies that the betting activity coeficient $\bar { W } ^ { 1 / 3 }$ cancels out of the price impact term. Indeed, the square root is the only function for which invariance leads to the empirical prediction that impact costs (measured in units of returns volatility) depend only on bet size as a fraction of betting activity $\tilde { Q } / \bar { V }$ and not on any other stock characteristics. If there are no bid-ask spread costs so that $\kappa _ { 0 } = 0$ , then the square root model implies the parsimonious transactions cost function $C ( \tilde { Q } ) = \bar { \sigma } \cdot \kappa _ { I } \cdot \bar { [ | \tilde { Q } | / \bar { V } ] ^ { 1 / 2 } }$ 

Sometimes called by practitioners “the Barra model,” a square root price impact model like specification (13) was proposed by Barra (1997) based on empirical regularities observed by Loeb (1983). Grinold and Kahn (1995) use an inventory risk model to derive a square root price impact formula. Gabaix et al. (2006) formalize this approach under the assumptions that (1) orders are executed as a constant fraction of volume and (2) liquidity providers have mean-variance utility functions linear in expected wealth and its standard deviation (not variance). 

Invariance of Pricing Accuracy and Market Resiliency. We think of “fundamental value” F as the value to which a stock price would converge if traders continuously invested huge resources acquiring information about its value. Let Σ denote the variance of the log-diference between price and fundamental value, $\Sigma : = \operatorname { v a r } \{ \ln ( F / P ) \}$ . Then $\Sigma ^ { 1 / 2 }$ measures the standard deviation of this log-diference as a fraction of the market price, and $\Sigma ^ { - 1 / 2 }$ measures “pricing accuracy.” 

Black (1986) defines eficient markets using a similar concept of pricing accuracy; he conjectures that “almost all markets are eficient” in the sense that “price is within a factor 2 of value” at least 90% of the time. Using our notation, Black’s conjecture is satisfied if $\Sigma ^ { 1 / 2 } < \ln ( 2 ) / 1 . 6 4$ in almost all markets, since the probability that a normal distribution is within 1.64 standard deviations of its mean is approximately 90%. If $\Sigma ^ { 1 / 2 }$ becomes smaller, Black would say that the market has become more “eficient.” 

Fischer Black’s definition of market eficiency based on pricing accuracy contrasts sharply with the conventional definition of Eugene Fama, who considers a market to be “eficient” if all available information is appropriately reflected in price, even if very little information is available and prices are not very accurate, i.e., $\Sigma ^ { 1 / 2 }$ is large. 

The pricing error variance Σ can be converted into time units by scaling it by fundamental volatility $\sigma ^ { 2 }$ . The quantity $\Sigma / \sigma ^ { 2 }$ can be further interpreted as the number of years by which the informational content of prices lags behind fundamental value. For example, if a stock’s annual volatility is about 35% and $\Sigma ^ { 1 / 2 } = \ln ( 2 ) / 1$ .64, then prices are about 1.50 years “behind” fundamental value since $( \ln ( 2 ) / 1 . 6 4 ) ^ { 2 } / 0 . 3 5 ^ { 2 } \approx 1 . 5 0$ 

Define “market resiliency” ρ as the mean-reversion parameter (per calendar day) measuring the speed with which a random shock to prices, resulting from execution of an uninformative bet, dies out over time as informative orders drive prices towards fundamental value. The half-life of an uninformative shock to prices is $\rho ^ { - 1 } \cdot \ln ( 2 )$ 

Market microstructure invariance hypothesizes that pricing accuracy is the same if its reciprocal is scaled by returns volatility per unit of business time, and market resiliency is the same if it is measured in units of business time. More specifically, invariance of pricing accuracy implies that the ratio $\Sigma ^ { 1 / 2 } / [ \bar { \sigma } \cdot \gamma ^ { - 1 / 2 } ]$ is invariant across stocks. Since $1 / L$ ∝ $\bar { \boldsymbol { \sigma } } \cdot \boldsymbol { \gamma } ^ { - 1 / 2 }$ from equation (11), invariance also implies proportionality between pricing accuracy $\Sigma ^ { - 1 / 2 }$ and liquidity L. Invariance suggests that the ratio $\rho / \gamma$ is invariant across stocks, making resiliency proportional to the rate at which business time passes. 

Using equation (5), invariance implies the following invariance relationships: 

$$
\Sigma^ {1 / 2} \propto \bar {\sigma} \cdot \bar {W} ^ {- 1 / 3} \propto \frac {1}{L}, \quad \rho \propto \bar {W} ^ {2 / 3} \propto \gamma .\tag{14}
$$

For example, when trading activity increases by a factor of 8, resiliency increases by a factor of 4 and pricing accuracy increases by a factor of $2 . ^ { 4 }$ Intuitively, the unstated invariant proportionality factors implied by equation (14) should be related to the information content of bets. More informative bets should make markets more eficient and resilient. This intuition is made precise in the structural model examined in the next section. 

We do not examine empirically the predictions of equation (14); they are however interesting topics for future research. 

Numerical Example. The following example illustrates the invariance hypotheses. Suppose a stock has daily volume of $40 million and daily returns volatility of 2%. Suppose there are approximately 100 bets per day and the mean size of a bet is $400, 000. A daily volatility of 2% implies a standard deviation of mark-to-market dollar gains and losses equal to $8, 000 per calendar day for the mean bet. Since business time passes at the rate bets arrive into the market, 100 bets per day implies about 1 bet every 4 minutes; the business clock therefore ticks once every 4 minutes. Over a 4-minute period, the standard deviation of returns is 20 basis points (200/ 100). Thus, the mean bet has a standard deviation of risk transfer of $800 per unit of business time. 

Invariance says that the specific number $800 is constant across stocks and across time. For example, if the arrival rate of bets increases by a factor of 4, the business clock ticks 4 times faster (once every minute), and the standard deviation of returns per tick on that clock is reduced from 20 basis points to 10 basis points (200/ 400). For the standard deviation of mark-to-market dollar gains and losses on the mean bet to remain constant at $800, invariance implies that the dollar size of the mean bet must increase by a factor of 2 from $400, 000 to $800, 000. Thus, holding volatility constant, the bet arrival rate increases by a factor of 4 and the size of bets increases by a factor of 2. This implies that daily volume increases by a factor of 8 from $40 million to $320 million. Holding volatility constant, the bet arrival rate increases by a factor proportional the $2 / 3$ power of the factor by which dollar volume changes, and the size of bets increases by the 1/3 power of the factor by which dollar volume changes. 

Invariance of transaction costs says that the dollar cost of executing a bet of a given size percentile is the same across diferent stocks. The dollar costs of executing the mean bet is therefore the same constant across securities and across time and, for example, equal to $2, 000. Doubling the size of the mean bet from $400, 000 to $800, 000 decreases the cost of $2, 000 measured in basis points from 50 basis points to 25 basis points, i.e., by a factor of 2. The transactions cost of executing a bet, measured in basis points, is therefore inversely proportional to the $1 / 3$ power of the factor by which dollar volume changes, holding volatility constant. 

Similar arguments are valid for bets in diferent percentiles of the bet size distri bution. Suppose, for example, that the standard deviation of mark-to-market gains or losses on a 99th percentile bet is $10, 000 per tick of business time (4 minutes). The size of such a bet is therefore $5 million in the first stock and $10 million in the second stock, diferent by a factor of 2. If the dollar costs of executing 99th percentile bets is equal to $50, 000, then this corresponds to a cost of 100 basis points in the first stock and 50 basis points in the second stock. The percentage cost for the second stock is lower by a factor of 2; this diference is inversely proportional to the $1 / 3$ power of the factor by which dollar volume changes, holding volatility constant. 

Discussion and Other Implications. Invariance is consistent with irrelevance of the units in which time is measured. The values of $\tilde { I } , \ C _ { B } ( \tilde { I } ) , \ f ( \tilde { I } )$ , and $1 / L -$ and therefore the economic content of the predictions of invariance—remain the same regardless of whether researchers measure γ, $\bar { V } , \bar { \sigma }$ , and $\bar { W }$ using daily weekly, monthly, or annual units of time. This is unlike some other models, such as ARCH and GARCH. 

The values of $\tilde { I }$ and $C _ { B } ( { \tilde { I } } )$ are measured in dollars. Invariance relationships can also be applied to an international context in which markets have diferent currencies or diferent real exchange rates; they can also be applied across periods of time when the price level is changing significantly. Invariance is consistent with the idea that these nominal values $\breve { \tilde { I } }$ and $C _ { B } ( { \tilde { I } } )$ should be equal to the nominal cost of financial services calculated from the productivity-adjusted wages of finance professionals in the local currency of the given market during the given time period. Since wages are measured in dollars per day and productivity is measured in bets per day, the ratio of wages to productivity is measured in dollars per bet, exactly the same units as $\tilde { I }$ and $C _ { B } ( \tilde { I } )$ . Like fundamental constants in physics, dividing the invariants $\tilde { I }$ and $C _ { B } ( { \tilde { I } } )$ by the ratio of wages to productivity makes them dimensionless. 

We model market microstructure using invariance in a manner similar to the way modern physicists model turbulence. Kolmogorov (1941a) derived his “two-thirds law” (or “five-thirds law”) for the energy distribution in a turbulent fluid based on dimensional analysis and scaling.<sup>5</sup> 

Invariance is also consistent with the Modigliani-Miller irrelevance of leverage and splits. It can be shown that invariance relationships do not change if a company levers up its equity by paying a debt-financed cash dividend or implements a stock split. 

Invariance has numerous implications. We outline some of them below to indicate interesting directions for future research without pursuing them further in this paper. 

Invariance relationships are based on the implicit assumption that bets are executed at an endogenously determined “natural” speed that trades of the benefits of faster execution against higher transactions costs. It does not rule out the possibility that unusually fast execution of a bet would lead to execution costs higher than the costs implied by the functions $f ( { \tilde { I } } )$ and $C _ { B } ( { \tilde { I } } )$ . For example, it is possible to consider more general invariant cost functions $f ( { \tilde { I } } , T / \gamma )$ and $C _ { B } ( \tilde { I } , T / \gamma )$ that depend not only of the size of bets but also on execution horizons $T$ converted from units of calendar time into units of business time $T / \gamma$ 

Invariance implies that trading liquidity and funding liquidity may be two sides of the same coin. Trading liquidity is measured by L, which is proportional to $\bar { W } ^ { 1 / 3 } / \bar { \sigma }$ and $\gamma ^ { 1 / 2 } / \bar { \sigma }$ . A good measure of funding liquidity is the repo haircut that suficiently protects a creditor from losses if the creditor sells the collateral due to default by the borrower. Such a haircut should be proportional to the volatility of the asset’s return over the horizon during which the collateral would be liquidated. This horizon should be proportional to business time $1 / \gamma$ , making volatility over the liquidation horizon proportional to $\bar { \sigma } \cdot \gamma ^ { - 1 / 2 }$ , which is itself proportional to $1 / L$ . Thus, invariance suggests that both trading liquidity and funding liquidity can be measured by L. 

Asset pricing models often assume that less liquid assets must command a returns premium to compensate investors for illiquidity. Invariance suggests the hypothesis that the returns premium required to compensate an investor for asset illiquidity should be proportional to $1 / L$ . Indeed, suppose that active long only asset managers are the marginal investors in a universe of stocks with similar turnover rates, and the costs of bets are imposed pro rata on the investors. Since market capitalization is proportional to $P \cdot V$ and dollar costs are proportional to the bet arrival rate $\gamma \propto W ^ { 2 / 3 }$ , percentage costs in basis points are proportional to $W ^ { 2 / 3 } / ( P V ) \propto 1 / L$ This argument suggests that the proportionality factor may show up both in returns and management fees. 

Invariance also leads naturally to implications for the time periods over which institutional investors hold their positions. Active speculative positions are expected to be held for a period of time proportional to the bet arrival rate $\gamma \propto W ^ { 2 / 3 }$ 

## 2 Market Microstructure Invariance as an Implication of a Structural Model

In this section, we derive invariance relationships as endogenous implications of a structural model of informed trading, noise trading, and intermediation (market making). 

The model has the following structure. The unobserved “fundamental value” of the stock follows geometric Brownian motion with log-standard-deviation $\sigma _ { F }$ . There are two types of traders: informed traders and noise traders. Informed traders and noise traders arrive in the market randomly and trade only once. Each informed trader trades based on a costly informative signal of precision $\tau ;$ the price impact of the trade incorporates a fraction $\theta$ of this private information into prices. In the spirit of Black (1986), each noise trader trades based on a “fake” signal which has the same unconditional distribution as an informative signal but has no information content. We call the noise traders “Fischer Black noise traders.” When an informed or noise trader arrives in the market, the trader “places a bet” by announcing to competitive market makers the quantity the trader wishes to trade. Conditional on this announced quantity but not knowing whether the trader is informed or not, competitive risk-neutral market makers determine a break-even price at which the trade takes place. Noise traders place bets at a rate which leads to an exogenously given turnover rate η of the exogenous float of N shares. Informed traders place bets at an endogenously determined rate which equates the cost $c _ { I }$ of each private signal to the expected value of trading on that signal, taking into account the price impact of the bet. Our structural model has the flavor of Glosten and Milgrom (1985) and Black (1986). 

Invariance relationships come about through the following intuition: Suppose the number of noise traders increases for some exogenous reason. In the structural model, this happens when the share price and therefore market capitalization increases, keeping the share turnover of noise traders constant. To be specific, assume that the number of noise traders increases by a factor of 4. As a result, market depth increases and, consequently, the number of informed traders increases, since their bets now are more profitable. The structural model shows that the number of informed traders eventually increases by a factor of 4 as well, and each of their bets accounts for a 4 times smaller fraction of returns variance. Returns volatility per unit of business time decreases by a factor of 2 (the square root of 4). The structural model shows that pricing accuracy and liquidity both increase by a factor of $2 ,$ , as a result of which informed traders exactly cover the cost of private signals by submitting bets 2 times as large as before. Overall dollar volume in the market increases by a factor of $8 .$ Thus, the “one-third, two-thirds” intuition comes about: One-third of the increase in dollar volume comes from changes in bet size $\left( 8 ^ { 1 / 3 } = 2 \right)$ and two-thirds comes from changes in the number of bets $\left( 8 ^ { 2 / 3 } = 4 \right)$ 

To make clear the distinction between endogenous variables and exogenous parameters, we use notation that assumes all exogenous parameters are constants while all endogenous variables are time-varying. In equilibrium, the price $P ( t )$ follows an endogenously derived martingale process with returns volatility $\sigma ( t )$ . The model endogenously determines the rate at which informed bets occur $\gamma _ { I } ( t )$ , the rate at which bets by noise traders occur $\gamma _ { U } ( t )$ , the distribution of bet sizes $\tilde { Q } ( t )$ , pricing accuracy $\Sigma ( t ) ^ { - 1 / 2 }$ , market resiliency $\rho ( t )$ , market illiquidity $1 / L ( t )$ , and the price impact parameter $\lambda ( t )$ 

In the remainder of this section, we describe the structural model in more detail, using notation consistent with the previous section. For simplicity, we assume $\zeta = 2$ and $\psi = 1$ so that $V = { \bar { V } }$ and $\sigma = \bar { \sigma }$ . It is straightforward to adjust the model for $\zeta \neq 2$ and $\psi \neq 1$ by applying equations (1) and $( 2 )$ 

Fundamental Value and Private Information. Let the unobserved “fundamental value” of the asset follow a geometric Brownian motion given by 

$$
F (t) := \exp [ \sigma_ {F} \cdot B (t) - \frac {1}{2} \cdot \sigma_ {F} ^ {2} \cdot t ],\tag{15}
$$

where $B ( t )$ follows standardized Brownian motion with var $\{ B ( t + \Delta t ) - B ( t ) \} = \Delta t$ the constant $\sigma _ { F }$ measures the “Black-Scholes volatility” of the fundamental value, and the term $\frac { 1 } { 2 } \cdot \sigma _ { F } ^ { 2 } \cdot t$ makes $F ( t )$ follow a martingale. Assume a zero risk-free rate of interest. Trading takes place over some long finite horizon, ending at a distant date at which all traders receive a payof equal to the fundamental value of the asset. 

The price changes as informed traders and noise traders arrive into into the market and anonymously place bets. Risk-neutral market makers set the market price $P ( t )$ as the conditional expectation of the fundamental value $F ( t )$ given a history of the “bet flow,” which we can assume to be informationally equivalent to the history of prices. 

Rather than focusing on the market’s estimate of the fundamental value $F ( t )$ 2 we focus instead on the market’s estimate of the Brownian motion $B ( t )$ , in terms of which $F ( t )$ is defined. Let $\bar { B } ( t )$ denote the market’s conditional expectation of $B ( t )$ based on observing the history of prices. For now, assume that the error $B ( t ) - \bar { B } ( t )$ has approximately a normal distribution with variance denoted $\Sigma ( t ) / \sigma _ { F } ^ { 2 }$ ; scaling by $\sigma _ { F } ^ { 2 }$ makes the notation $\Sigma ( t )$ consistent with the notation for $\Sigma$ in section 1. 

The price is the best estimate of fundamental value when $P ( t )$ is given by 

$$
P (t) = \exp [ \sigma_ {F} \cdot \bar {B} (t) + \frac {1}{2} \cdot \Sigma (t) - \frac {1}{2} \cdot \sigma_ {F} ^ {2} \cdot t ].\tag{16}
$$

The price has a martingale property and the variance of log $[ F ( t ) / P ( t ) ]$ is equal to $\Sigma ( t )$ , i.e. $\Sigma ( t ) ^ { - 1 / 2 } \Sigma ( t ) ^ { - \top / 2 }$ measures “pricing accuracy.” 

Informed Traders. Informed traders arrive randomly into the market at endogenously determined rate $\gamma _ { I } ( t )$ . If an informed trader arrives at time $t ,$ he observes one private signal $\tilde { i } ( t )$ in addition to the history of prices , then places one and only one bet, which is executed by trading with market makers. Informed signals are assumed to have the form 

$$
\tilde {i} (t) := \tau^ {1 / 2} \cdot \Sigma (t) ^ {- 1 / 2} \cdot \sigma_ {F} \cdot [ B (t) - \bar {B} (t) ] + \tilde {Z} _ {I} (t),\tag{17}
$$

where $\tau$ is an exogenous constant parameter measuring the precision of the signal and the noise term $\tilde { Z } _ { I } ( t ) \sim N ( 0 , 1 )$ is distributed independently from the history of prices prior to the arrival of the signal. Scaling $\tau ^ { 1 / 2 }$ <sup>2</sup> by $\Sigma ( t ) ^ { - 1 / 2 } \cdot \sigma _ { F }$ , the reciprocal of the standard deviation of $B ( t ) - \bar { B } ( t )$ , makes $\tau$ measure the constant signal-to-noise ratio. We assume $\tau$ is small enough so that var $\{ \tilde { i } ( t ) \} = 1 + \tau \approx 1$ . Although the signal associated with the nth bet to arrive is diferent from previous signals, we omit a clarifying subscript n on $\tilde { i } ( t )$ 

An informed trader calculates his prior estimate $\bar { B } ( t )$ of $B ( t )$ from market prices. Upon observing a signal $\tilde { i } ( t )$ , he updates his prior from $\bar { B } ( t )$ to $\bar { B } ( t ) + \Delta \bar { B } _ { I } ( t )$ . Assuming $\tau$ is small, the update is given by 

$$
\Delta \bar {B} _ {I} (t) \approx \tau^ {1 / 2} \cdot \Sigma (t) ^ {1 / 2} \cdot \sigma_ {F} ^ {- 1} \cdot \tilde {i} (t),\tag{18}
$$

where $\tau ^ { 1 / 2 } \cdot \Sigma ( t ) ^ { 1 / 2 } \cdot \sigma _ { F } ^ { - 1 }$ is the regression coeficient of $B ( t ) - \bar { B } ( t )$ on $\tilde { i } ( t )$ . If the signal value were to be fully incorporated into prices, it can be shown that the dollar price change would be equal to 

$$
E \{F (t) - P (t) \mid \Delta \bar {B} _ {I} (t) \} \approx P (t) \cdot \left(\exp [ \sigma_ {F} \cdot (\Delta \bar {B} _ {I} (t) - \Delta \bar {B} _ {I} (t) ^ {2} / 2) ] - 1\right) \approx P (t) \cdot \sigma_ {F} \cdot \Delta \bar {B} _ {I} (t).\tag{19}
$$

We assume that an informed trader arriving at time t executes a bet of size $\tilde { Q } ( t )$ In order to break even in the presence of adverse selection, market makers take the other side of the bet at a price adjusted by $\lambda ( t ) \cdot \tilde { Q } ( t )$ , where $\lambda ( t )$ is a price impact parameter. The price impact is linear in the size of the bet. 

Suppose that a bet of size $\tilde { Q } ( t )$ is a linear multiple of $\Delta \bar { B } _ { I } ( t )$ in such a way that only a fraction $\theta$ of the “fully revealing” impact $P ( t ) \cdot \sigma _ { F } \cdot \Delta \bar { B } _ { I } ( t )$ is incorporated into prices, i.e., 

$$
\tilde {Q} (t) = \theta \cdot \lambda (t) ^ {- 1} \cdot P (t) \cdot \sigma_ {F} \cdot \Delta \bar {B} _ {I} (t).\tag{20}
$$

If the informed trader were to trade $\tilde { Q } ( t )$ shares defined in equation (20) at price $P ( t )$ with no price impact costs, then his unconditional expected “paper trading” profits, denoted ${ \bar { \pi } } _ { I } ( t )$ , would be equal to 

$$
\bar {\pi} _ {I} (t) := E \{[ F (t) - P (t) ] \cdot \tilde {Q} (t) \} = \frac {\theta \cdot P (t) ^ {2} \cdot \sigma_ {F} ^ {2} \cdot E \{\Delta \bar {B} _ {I} (t) ^ {2} \}}{\lambda (t)}.\tag{21}
$$

Conditioning on observing the signal $\tilde { i } ( t )$ , the expected profits of the informed trader, net of transactions costs $\lambda ( t ) \cdot \tilde { Q } ( t ) ^ { 2 }$ , are 

$$
E \left\{\left[ F (t) - P (t) \right] \cdot \tilde {Q} (t) - \lambda (t) \cdot \tilde {Q} (t) ^ {2} \mid \Delta \bar {B} _ {I} (t) \right\} = \frac {\theta \cdot (1 - \theta) \cdot P (t) ^ {2} \cdot \sigma_ {F} ^ {2} \cdot \Delta \bar {B} _ {I} (t) ^ {2}}{\lambda (t)}.\tag{22}
$$

It is clear that $\theta = 1 / 2$ maximizes the expected profits of the informed trader and therefore solves the optimization problem of a a risk-neutral informed trader. Rather than assuming that informed traders are risk neutral and therefore $\theta = 1 / 2$ as the equilibrium choice of $\theta ,$ we will instead allow $\theta$ to have an arbitrary exogenous value such that $0 < \theta < 1$ . This approach accommodates the possibility that informed traders are risk averse, in which case $\theta < 1 / 2$ might be optimal; it also accommodates the possibility of information leakage, in which case $\theta > 1 / 2$ might be optimal. More importantly, it allows us to show that the invariance results derived below depend only on the fact that $\theta$ is some constant, not that θ has the specific value $1 / 2$ 

Noise Traders. Noise traders arrive randomly at an endogenously determined rate $\gamma _ { U } ( t )$ . Each noise trader places one bet which mimics the size distribution of an informed bet, even though it contains no information. In other words, if a noise trader arrives at time $t ,$ he receives a signal $\tilde { i } ( t )$ which is assumed to have the same unconditional distribution as an informed signal, i.e., $\tilde { i } ( t ) = \tilde { Z } _ { U } ( t ) \sim N ( 0 , 1 + \tau ) \approx$ $N ( 0 , 1 )$ , but it is “noise” in the sense that $\tilde { i } ( t )$ is distributed independently from the error $\bar { B } ( t ) - B ( t )$ and the history of prices. Noise traders are assumed to place bets at a rate such that a constant fraction η of the market capitalization of the firm turns over on average per day. 

Let N denote the number of shares outstanding, let $V ( t )$ denote average share volume per day from informed and noise traders combined, and let $\gamma ( t ) : = \gamma _ { I } ( t ) +$ $\gamma _ { U } ( t )$ denote the combined arrival rate of bets by informed traders and noise traders. Let informed trades and noise trades be distributed as the random variable $\tilde { Q } ( t )$ in equation (20). Then, expected share volume from noise traders $\eta \cdot N$ , total volume $V ( t )$ , and the fraction of volume from noise traders $\gamma _ { U } ( t ) / \gamma ( t )$ satisfy 

$$
\gamma_ {U} (t) \cdot E \{| \tilde {Q} (t) | \} = \eta \cdot N, \qquad \gamma (t) \cdot E \{| \tilde {Q} (t) | \} = V (t).\tag{23}
$$

Market Makers (Intermediaries). Zero-profit, risk-neutral, competitive market makers are assumed to set prices such that the price impact of anonymous trades by informed and noise traders make the price $P ( t )$ equal to the conditional expectation of the fundamental value $F ( t )$ given the history of all bets. If market makers could observe whether a bet was placed by an informed trader or noise trader, they would multiply the price impact of informed bets $\lambda ( t ) \cdot \tilde { Q } ( t )$ by $1 / \theta$ (since informed bets have price impact which reveals only fraction θ of their information content) and they would multiply the price impact of noise bets $\lambda ( t ) \cdot \tilde { Q } ( t )$ by zero (since noise bets have no information content). The probability of an informed bet is $\gamma _ { U } ( t ) / \gamma ( t )$ , and the probability of a noise bet is $\gamma _ { U } ( t ) / \gamma ( t )$ . In equilibrium, the average impact of a bet must satisfy 

$$
\lambda (t) \cdot \tilde {Q} (t) = \frac {\gamma_ {I} (t)}{\gamma_ {I} (t) + \gamma_ {U} (t)} \cdot \lambda (t) \cdot \tilde {Q} (t) \cdot \frac {1}{\theta} + \frac {\gamma_ {U} (t)}{\gamma_ {I} (t) + \gamma_ {U} (t)} \cdot \lambda (t) \cdot \tilde {Q} (t) \cdot 0.\tag{24}
$$

This implies that the fraction of informed traders and noise traders satisfies 

$$
\frac {\gamma_ {I} (t)}{\gamma_ {I} (t) + \gamma_ {U} (t)} = \theta .\tag{25}
$$

Thus, the fraction of traders who are informed turns out to be to the exogenous constant θ. In the special case when informed traders are risk neutral, $\theta = 1 / 2$ implies that the number of informed traders is equal to the number of uninformed traders. Note that this ratio is not determined by equations describing the profitability of informed trading but rather by equations describing the adverse selection problem faced by market makers. Moreover, equations (23) and (25) imply that, in terms of exogenous variables, share volume $V ( t )$ is actually a constant given by 

$$
V (t) = \eta \cdot N / (1 - \theta).\tag{26}
$$

Break-Even Conditions. Equation (20) implies that the unconditional expected price impact cost of an informed bet, denoted $\bar { C } _ { B } ( t )$ , is given by 

$$
\bar {C} _ {B} (t) := \lambda (t) \cdot E \{\tilde {Q} (t) ^ {2} \} = \frac {\theta^ {2} \cdot P (t) ^ {2} \cdot \sigma_ {F} ^ {2} \cdot E \{\Delta \bar {B} _ {I} (t) ^ {2} \}}{\lambda (t)}.\tag{27}
$$

Bets by noise traders have the same expected impact cost since they have the same unconditional distribution as informed bets and are indistinguishable from informed bets from the perspective of market makers. The equilibrium level of costs must allow market makers to break even. Thus, the expected dollar price impact costs that market makers expect to collect from all traders must be equal to the expected dollar paper trading profits of informed traders: 

$$
(\gamma_ {I} (t) + \gamma_ {U} (t)) \cdot \bar {C} _ {B} (t) = \gamma_ {I} \cdot \bar {\pi} _ {I} (t).\tag{28}
$$


Figure 1: Intuition for the Model.


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/c5f5b707-866d-494a-8be3-5c8615679388/182c40ad44b95d39af2e973cf3ab929fa0e944245c2ad1315a23050834d68c5a.jpg)



There is price continuation after an informed trade and mean reversion after a noise trade.


Figure 1 illustrates the intuition informally and non-rigorously. Informed traders incorporate only a fraction θ of their information into prices by trading $\tilde { Q } ( t )$ ; they pay transactions costs $\bar { C } _ { B } ( t )$ and expect to make $\bar { \pi } _ { I } ( t ) - \bar { C } _ { B } ( t )$ as the price gradually converges to fundamental value $F ( t )$ due to the subsequent trading of other informed traders. These profits are realized at some distant date when the game ends and positions are liquidated at the fundamental value $F ( t )$ . Noise traders execute orders which incur transactions costs $\bar { C } _ { B } ( t )$ but would earn nothing if there were no transactions costs. As in Treynor (1995), the expected losses market makers incur trading with informed traders $\gamma _ { I } ( t ) \cdot ( \bar { \pi } _ { I } ( t ) - \bar { C } _ { B } ( t ) )$ are equal to their expected gains trading with noise traders $\gamma _ { U } ( t ) \cdot \bar { C } _ { B } ( t )$ 

The break-even condition for informed traders yields the rate at which informed traders place bets $\gamma _ { I } ( t )$ . The expected paper trading profits from trading on a signal ${ \bar { \pi } } _ { I } ( t )$ must equal the sum of expected transaction costs $\bar { C } _ { B } ( t )$ and the exogenously constant cost of acquiring private information denoted $c _ { I }$ : 

$$
\bar {\pi} _ {I} (t) = \bar {C} _ {B} (t) + c _ {I}.\tag{29}
$$

We let $1 / L ( t ) : = \bar { C } _ { B } ( t ) / E \{ | P ( t ) \cdot \tilde { Q } ( t ) | \}$ denote the expected percentage cost of executing a bet in basis points, as in section 1. 

Difusion Approximation and Conditional Steady State. The model theoretically implies that the price follows a jump process which changes when a bet arrives. Conditional expectations of $\bar { B } ( t )$ calculated based on a random number of bet arrivals during a given time interval are not precisely linear. Moreover, since the price is a nonlinear function of $\bar { B } ( t )$ , price impact is theoretically nonlinear as well. 

To deal with these non-linearities, we assume that the arrival rate of bets is so fast—and the resulting price impact of each bet is so small—that a linear approximation based on a difusion is appropriate. In the limit as the bet arrival rate $\gamma ( t )$ goes to infinity, the conditional expectation $\bar { B } ( t )$ becomes an exactly linear function of the history of bets, and the price process becomes a difusion. This is compatible with assuming that market makers and traders use linear filtering, market makers ofer linear supply schedules to traders, traders place bets as linear functions of signals, log-price changes are normally distributed, and price changes are conditionally normally distributed in the sense of an Euler approximation. 

As a result of each bet, market makers update their estimate of $\bar { B } ( t )$ by $\Delta \bar { B } ( t )$ (not to be confused with the update $\Delta \bar { B } _ { I } ( t )$ of informed traders). A trade is informed with probability θ and, if informed, incorporates a fraction θ of its information content into prices, leading to an adjustment in $\bar { B } ( t )$ of 

$$
\Delta \bar {B} (t) = \theta \cdot \tau^ {1 / 2} \cdot \Sigma (t) ^ {1 / 2} \cdot \sigma_ {F} ^ {- 1} \cdot \left(\tau^ {1 / 2} \cdot \Sigma (t) ^ {- 1 / 2} \cdot \sigma_ {F} \cdot [ B (t) - \bar {B} (t) ] + \tilde {Z} _ {I} (t)\right)\tag{30}
$$

from equations (17) and (18). A trade is uninformed with probability $1 - \theta$ and, if uninformed, adds noise to $\bar { B } ( t )$ of 

$$
\Delta \bar {B} (t) = \theta \cdot \tau^ {1 / 2} \cdot \Sigma (t) ^ {1 / 2} \cdot \sigma_ {F} ^ {- 1} \cdot \tilde {Z} _ {U} (t).\tag{31}
$$

When the arrival rate of bets $\gamma ( t )$ per day is suficiently large, the difusion approximation for the dynamics of the estimate $\bar { B } ( t )$ can be written as 

$$
d \bar {B} (t) = \gamma (t) \cdot \theta^ {2} \cdot \tau \cdot [ B (t) - \bar {B} (t) ] \cdot d t + \gamma (t) ^ {1 / 2} \cdot \theta \cdot \tau^ {1 / 2} \cdot \Sigma (t) ^ {1 / 2} \cdot \sigma_ {F} ^ {- 1} \cdot d Z (t).\tag{32}
$$

The first term corresponds to the information contained in informed signals which arrive at rate $\theta \cdot \gamma ( t )$ . The second term corresponds to the noise contained in all bets arriving at rate $\gamma ( t )$ . Here, $\gamma ( t ) ^ { 1 / 2 } \cdot d Z ( t )$ is obtained by converting the mixture of $d Z _ { I } ( t )$ and $d Z _ { U } ( t )$ —with probabilities $\theta$ and $1 - \theta$ , respectively—into a Brownian motion $d Z ( t )$ with the same variance. 

Define $\sigma ( t )$ by 

$$
\sigma (t) := \theta \cdot \tau^ {1 / 2} \cdot \Sigma (t) ^ {1 / 2} \cdot \gamma (t) ^ {1 / 2}.\tag{33}
$$

By applying Ito’s lemma to the definition of price in equation (16) and using equation (32), we obtain 

$$
\frac {d P (t)}{P (t)} = \frac {1}{2} \cdot [ \Sigma^ {\prime} (t) - \sigma_ {F} ^ {2} + \sigma (t) ^ {2} ] \cdot d t + \sigma_ {F} \cdot d \bar {B} (t).\tag{34}
$$

Market eficiency implies that $P ( t )$ must follow a martingale. Its drift therefore must be zero, implying that $\Sigma ( t )$ must satisfy the diferential equation 

$$
\frac {d \Sigma (t)}{d t} = \sigma_ {F} ^ {2} - \sigma (t) ^ {2}.\tag{35}
$$

Now define $d \bar { Z } ( t ) : = \Sigma ( t ) ^ { - 1 } \cdot \sigma ( t ) \cdot \sigma _ { F } \cdot [ B ( t ) - \bar { B } ( t ) ] \cdot d t + d Z ( t )$ . The process $\bar { Z } ( t )$ is a standardized Brownian motion under the market’s filtration, because $\bar { B } ( t )$ is the market’s best estimate of $B ( t )$ . Equation (32) can now be written in the simplified form $d \bar { B } ( t ) = \sigma ( t ) \cdot \sigma _ { F } ^ { - 1 } \cdot d \bar { Z } ( t )$ . Using this fact and substituting $d \bar { Z } ( t )$ for $d \bar { B } ( t )$ , the price process (34) can be written as the martingale process 

$$
\frac {d P (t)}{P (t)} = \sigma (t) \cdot d \bar {Z} (t).\tag{36}
$$

Thus, $\sigma ( t )$ measures returns volatility, consistent with our notation $\sigma$ throughout this paper. 

Returns volatility $\sigma ( t )$ measures the rate at which new information is being incorporated into prices. According to equation (33), returns volatility $\sigma ( t )$ is stochastic, even though fundamental volatility $\sigma _ { F }$ is constant. When returns volatility $\sigma ^ { 2 } ( t )$ is greater than fundamental volatility $\sigma _ { F } ^ { 2 }$ , equation (35) says that the diference represents the rate at which pricing error $\Sigma ( t )$ is falling, since new information is being incorporated into prices faster than new fundamental uncertainty is unfolding. When returns volatility $\sigma ^ { 2 } ( t )$ is smaller than fundamental volatility $\sigma _ { F } ^ { 2 }$ , the diference represents the rate at which pricing error $\Sigma ( t )$ is increasing, since new fundamental uncertainty is unfolding faster than information is being incorporated into prices. 

When $\Sigma ^ { \prime } ( t ) = 0$ , we shall say that $\Sigma ( t )$ has reached a “conditional steady state” in which the unfolding of new fundamental volatility and the incorporation of new private information into prices are in balance, i.e., $\sigma ( t ) = \sigma _ { F }$ . We use this terminology because the right-hand side of equation (35) does not converge to a constant due to the fact that the value of $\gamma ( t )$ , which follows a difusion, is constantly changing and this makes $\sigma ( t )$ change as well. If $\gamma ( t )$ were to remain constant for a long period of time, the value of $\Sigma ( t )$ would converge to the conditional steady state given by 

$$
\Sigma (t) = \frac {\sigma_ {F} ^ {2}}{\gamma (t) \cdot \theta^ {2} \cdot \tau},\tag{37}
$$

obtained from the definition of $\sigma ( t )$ in equation (33) and equation (35) when $\Sigma ^ { \prime } ( t ) = 0$ As changes in prices $P ( t )$ lead to immediate changes in market capitalization and therefore changes in the arrival rate of bets $\gamma ( t )$ , the value of $\Sigma ( t )$ gradually drifts towards a “conditional steady state” value.<sup>6</sup> According to equation (37), more accurate signals and more frequent bets make market prices more accurate. The invariance theorem discussed next applies both in the conditional steady state and outside it. 

Equations (32) and (33) imply that the diference $B ( t ) - \bar { B } ( t )$ follows the meanreverting process 7 

$$
d [ B (t) - \bar {B} (t) ] = - \frac {\sigma (t) ^ {2}}{\Sigma (t)} \cdot [ B (t) - \bar {B} (t) ] \cdot d t + d B (t) - \frac {\sigma (t)}{\sigma_ {F}} \cdot d Z (t).\tag{38}
$$

As in section 1, let market resiliency $\rho ( t )$ denote the mean reversion rate at which pricing errors disappear. We have 

$$
\rho (t) = \frac {\sigma (t) ^ {2}}{\Sigma (t)}.\tag{39}
$$

Holding returns volatility constant, resiliency is greater in markets with higher pricing accuracy. 

The endogenous quantities in the model are all functions of the two “state variables” $P ( t )$ and $\Sigma ( t )$ , which evolve stochastically according to equations (35) and (36), with stochastic returns volatility given by equation (33). These equations have interesting dynamics due to the fact that business time operates at a faster pace relative to calendar time when market capitalization and therefore trading volume are higher. When trading volume is high, bets arrive quickly and $\Sigma ( t )$ moves quickly towards its conditional steady state level; returns volatility remains close to fundamental volatil ity; $\Sigma ( t )$ does not deviate far from its conditional steady state level. When trading volume is low, bets arrive slowly and $\Sigma ( t )$ adjusts slowly towards its conditional steady state level; returns volatility may remain below fundamental volatility for extended periods of time.<sup>8</sup> 

Solution of the Model with Invariance. The following invariance theorem states that all of the invariance hypotheses in section 1 are implied by this structural model and reveals specific connections among the hypotheses. 

Invariance Theorem. Assume the cost $c _ { I }$ of generating a signal is an invariant constant and let $m : = E \{ | \tilde { i } ( t ) | \}$ define an additional invariant constant. $T h e n ,$ the invariance conjectures hold: The dollar risk transferred by a bet per unit of business time $\tilde { I } ( t )$ is a random variable with an invariant distribution and the expected cost of executing a bet $\bar { C } _ { B } ( t )$ is an invariant constant:<sup>9</sup> 

$$
\tilde {I} (t) := \frac {P (t) \cdot \tilde {Q} (t) \cdot \sigma (t)}{\gamma (t) ^ {1 / 2}} = \frac {\tilde {Q} (t)}{V (t)} \cdot W (t) ^ {2 / 3} \cdot (m \cdot \bar {c} _ {B}) ^ {1 / 3} = \bar {c} _ {B} \cdot \tilde {i} (t).\tag{40}
$$

$$
\bar {C} _ {B} (t) = \bar {c} _ {B} := c _ {I} \cdot \theta / (1 - \theta).\tag{41}
$$

The number of bets $\gamma ( t )$ , their size $\tilde { Q } ( t )$ , liquidity $L ( t )$ , pricing accuracy $1 / \Sigma ( t ) ^ { 1 / 2 }$ , and market resiliency $\rho ( t )$ are related to price $P ( t )$ , share volume $V ( t )$ , volatility $\sigma ( t )$ , and trading activity $W ( t ) = P ( t ) { \cdot } V ( t ) { \cdot } \sigma ( t )$ by the following invariance relationships, which are consistent with the invariance relationships in equations $( 5 ) , ( 6 ) , ( 8 )$ , and $( 1 \llcorner )$ 

$$
\gamma (t) = \left(\frac {\lambda (t) \cdot V (t)}{\sigma (t) \cdot P (t) \cdot m}\right) ^ {2} = \left(\frac {E \{| \tilde {Q} (t) | \}}{V (t)}\right) ^ {- 1} = \frac {(\sigma (t) \cdot L (t)) ^ {2}}{m ^ {2}} = \frac {\sigma (t) ^ {2}}{\theta^ {2} \cdot \tau \cdot \Sigma (t)} = \frac {\rho (t)}{\theta^ {2} \cdot \tau} = \left(\frac {W (t)}{m \cdot \bar {c} _ {B}}\right) ^ {2 / 3}.\tag{42}
$$

Here, $\tau$ is the precision of a signal, and θ is the fraction of information $\tilde { i } ( t )$ incorporated by an informed trade. The price follows a martingale with stochastic returns volatility $\overset { \cdot } { \sigma } ( t ) : = \theta \cdot \tau ^ { 1 / 2 } \cdot \Sigma ( t ) ^ { 1 / 2 } \cdot \widehat { \gamma ( t ) } ^ { 1 / 2 }$ 

Proof of Invariance Conjectures and Relationships. Using equations (25), (28), and (29), we obtain equation (41). The value $\bar { c } _ { B } = \theta \cdot c _ { I } / ( 1 - \theta )$ is constant across stocks, since $c _ { I }$ is constant across stocks by assumption and θ is constant across stocks by assumption (or, alternatively, by proof that $\theta = 1 / 2$ for risk-neutral informed traders). 

Dividing the definition $\tilde { I } ( t ) : = P ( t ) \cdot \tilde { Q } ( t ) \cdot \sigma ( t ) \cdot \gamma ( t ) ^ { - 1 / 2 }$ by the equation $\bar { C } _ { B } ( t ) : =$ $\lambda ( t ) \cdot E \{ \tilde { Q } ( t ) ^ { 2 } \}$ , plugging in the definitions of $\tilde { Q } ( t )$ and $\Delta \tilde { B } _ { I } ( t )$ from equations (18) and (20), and using definition (33), we obtain the third equality $\tilde { I } ( t ) = \bar { c } _ { B } \cdot \tilde { i } ( t )$ in equation (40); the first equality in equation (40) is the definition of $\tilde { I } ( t )$ and the second equality (involving $W ^ { 2 / 3 } )$ will follow from equation (42) below. Since $\tilde { i } ( t )$ is invariant by assumption and $\bar { c } _ { B }$ is invariant by proof, $\tilde { I } ( t ) = \dot { \bar { c } } _ { B } \cdot \tilde { i } ( t )$ has an invariant distribution. Note that both $\tilde { I } ( t )$ and $\bar { c } _ { B }$ are measured in dollars while $\tilde { i } ( t )$ represents unit-less information. 

We write equation (23) for daily volume, equation (27) for expected costs, and equation (33) for returns volatility using equations (18) and (20) as a system of three equations: 

$$
\gamma (t) \cdot E \{| \tilde {Q} (t) | \} = V (t),\tag{43}
$$

$$
\bar {c} _ {B} = \lambda (t) \cdot E \{\tilde {Q} ^ {2} (t) \},\tag{44}
$$

$$
\gamma (t) \cdot \lambda (t) ^ {2} \cdot E \{\tilde {Q} (t) ^ {2} \} = P (t) ^ {2} \cdot \sigma (t) ^ {2}.\tag{45}
$$

These three equations reflect the economic assumptions important for deriving invariance. Equation (43) says that observable trading volume results from bets. Equation (44) says that the expected price impact cost of a bet is $\bar { c } _ { B }$ (which is constant from equation (41)) assuming the bet has linear price impact costs. Equation (45) says that the price impact of a bet generates returns volatility, also under the assumption that price impact is linear. Note that the concepts of “price impact cost” and “price impact,” which both depend on the linear price impact parameter λ(t) in the model, actually represent somewhat diferent concepts, which happen to be the same in a dealer market model in which markets are semi-strong eficient and dealers make zero profits based on linear signal processing. In the structural model, it is a derived result that price impact and transaction costs are linear. 

In the three equations (43), (44), and (45), one can think of $\gamma ( t ) , \lambda ( t ) , E \{ \tilde { Q } ( t ) ^ { 2 } \}$ ， and $E \{ | \tilde { Q } ( t ) | \}$ as unknown variables to be solved for in terms of known variables $V ( t ) , \bar { c } _ { B } , P ( t )$ , and $\sigma ( t )$ . Since there are three equations and four unknowns, we need a fourth equation. The fourth equation is the moment ratio 

$$
m = \frac {E \{| \tilde {Q} (t) | \}}{[ E \{\tilde {Q} (t) ^ {2} \} ] ^ {1 / 2}}.\tag{46}
$$

Since m $\begin{array} { r l } { : = E \{ | \tilde { i } | \} } \end{array}$ , this equation follows from the fact that $\tilde { Q } ( t )$ is a linear multiple of $\tilde { i } ( t )$ and $\tilde { i } ( t )$ has a variance of one. Since $\tilde { i } ( t )$ is assumed to have a normal distribution with a variance of one, we have $m = ( 2 / \pi ) ^ { 1 / 2 }$ . For a diferent distributional assumptions, m would have a diferent value. If we think of m as an exogenous parameter, we now have four equations in four unknowns. 

Using the definition of m and the definition of trading activity $W ( t ) = P ( t )$ $V ( t ) \cdot \sigma ( t )$ , we can solve equations (43), (44), and (45) for $\gamma ( t ) , E \{ | \tilde { Q } ( t ) | \}$ , and $\lambda ( t )$ as follows. Multiply the product of (43) and (44) by the square root of (45) and solve for $\gamma ( t )$ to obtain 

$$
\gamma (t) = (m \cdot \bar {c} _ {B}) ^ {- 2 / 3} \cdot W (t) ^ {2 / 3}.\tag{47}
$$

Divide the product of (45) and the square of (44) by (43) and solve for $E \{ | \tilde { Q } ( t ) | \}$ using (46) to obtain 

$$
E \{| \tilde {Q} (t) | \} = (m \cdot \bar {c} _ {B}) ^ {2 / 3} \cdot V (t) \cdot W (t) ^ {- 2 / 3}.\tag{48}
$$

Divide the product of (45) and the square root of (44) by (43) and solve for $\lambda ( t )$ to obtain 

$$
\lambda (t) = \left(\frac {m ^ {2}}{\bar {c} _ {B}}\right) ^ {1 / 3} \cdot \frac {1}{V (t) ^ {2}} \cdot W (t) ^ {4 / 3}.\tag{49}
$$

Equation (48) and the definition of illiquidity $1 / L ( t ) : = \bar { c } _ { B } / [ P ( t ) \cdot V ( t ) ]$ imply that $1 / L$ satisfies 

$$
\frac {1}{L (t)} = \left(\frac {m ^ {2}}{\bar {c} _ {B}}\right) ^ {- 1 / 3} \cdot \sigma (t) \cdot W (t) ^ {- 1 / 3}.\tag{50}
$$

Equations (33), (39), and (47) imply that pricing accuracy $1 / \Sigma ( t ) ^ { 1 / 2 }$ and resiliency $\rho ( t )$ satisfy 

$$
\rho (t) = \frac {\sigma (t) ^ {2}}{\Sigma (t)} = \left(\frac {1}{m \cdot \bar {c} _ {B}}\right) ^ {2 / 3} \cdot \theta^ {2} \cdot \tau \cdot W (t) ^ {2 / 3}.\tag{51}
$$

Equations (47) for $\gamma ( t )$ , (48) for $\tilde { Q } ( t )$ , (50) for $1 / L ( t )$ , and (51) for $1 / \Sigma ( t ) ^ { 1 / 2 }$ and $\rho ( t )$ are summarized in equation (42). They are respectively equivalent to equations (5), (6), (8), and (14) implied by the market microstructure invariance hypotheses in section 1, since $E \{ | \tilde { i } | \} = m$ implies $E \{ | \tilde { I } | \} = m \cdot \bar { c } _ { B }$ from (40). 

Since trading activity $W ( t )$ and its components are observable, we can empirically infer values of $\gamma ( t ) , E \{ | \tilde { Q } ( t ) | \} , 1 / L ( t ) , \lambda ( t ) , 1 / \Sigma ( t ) ^ { 1 / 2 }$ and $\rho ( t )$ from equation (42) if the values of the three constants $m , { \bar { c } } _ { B }$ , and $\theta ^ { 2 } \tau$ are known. 

Discussion. The model adds additional structure that imposes restrictions on the three invariance hypotheses outlined in section 1. These additional assumptions impose a particular structure on the proportionality constants in invariance relationships (5), (6), (9), and (14) and allow us to write these disconnected relationships in a consolidated form of the invariance theorem (42). 

The level of trading activity $W ( t )$ and its components—prices $P ( t )$ , share volume $V ( t )$ , and returns volatility $\sigma ( t ) { \mathrm { - } } \mathrm { a r e }$ “macroscopic” quantities whose value can be estimated from aggregate market data, e.g., from the CRSP dataset. The bet arrival rate $\gamma ( t )$ , the bet size $\mathbf { \tilde { \cal { Q } } } ( t )$ , the average cost of $\mathrm { a }$ bet $1 / L ( t )$ , pricing accuracy $\Sigma ( t ) ^ { 1 / 2 }$ and resiliency $\rho ( t )$ are granular “microscopic” quantities whose values are dificult to observe even with data on individual trades by individual traders. Since knowledge of the constants $\bar { c } _ { B }$ , m, and $\tau \cdot \theta ^ { 2 }$ makes it possible to infer microscopic quantities from macroscopic quantities using equation (42), these constants play roles in our structural model somewhat similar to the role played by Boltzmann’s constant or Avogadro’s number in physics. 

For example, the structural model implies a particular relationship between the invariance of bet sizes and transaction costs. Equation (40) suggests that the bet size invariant $\tilde { I }$ and transaction costs invariant $\bar { c } _ { B }$ satisfy the restriction $E | \tilde { I } | = m \cdot \bar { c } _ { B }$ or, equivalently, that the standard deviation of $\tilde { I }$ is equal to $\bar { c } _ { B }$ . This restriction follows from the assumption that market makers break even. 

The structural model also implies a particular relationship between the invariance of pricing accuracy and the invariance of resiliency. In the model, the result $\rho ( t ) = \sigma ( t ) ^ { 2 } / \Sigma ( t )$ implies a specific restriction on the proportionality constants in equations (14).<sup>10</sup> 

In section 1, invariance relationships for bets and transaction costs were derived based on the assumption that the cost of executing a bet $\bar { c } _ { B }$ is constant across stocks. The structural model shows that $\bar { c } _ { B }$ is not the “deepest” structural parameter in the model. The result $\bar { c } _ { B } = \theta \cdot c _ { I } / ( 1 - \theta )$ implies that $\bar { c } _ { B }$ is constant across stocks if the “deeper” structural parameters $c _ { I }$ and $\theta$ are constant across stocks. It is useful to think of the cost of private information $c _ { I }$ as proportional to the average wages of finance professionals, adjusted for their productivity or efort required to generate one bet. The productivity-adjusted wage of a finance professional is therefore a “deeper” parameter than the endogenous cost of executing a bet $\bar { c } _ { B }$ . The invariance relationships in equation (42) result from finance professionals allocating their skills across diferent markets to maximize the value of trading on the signals they generate. The assumption that distinct bets result from distinct pieces of private information implies a particular level of granularity for both signals and bets. 

It is interesting that invariance relationships relating the granularity of bets to their costs depend on the first absolute moment of the distribution of signals $m$ , but not on the precision of signals $\tau .$ 

The structural model also shows that the invariance of pricing accuracy and resiliency requires stronger assumptions: In addition to $\bar { c } _ { B }$ and m being constant, the informativeness of a bet $\tau \cdot \theta ^ { 2 }$ , measured as the product of signal precision $\tau$ and the squared fraction of informed traders $\theta ^ { 2 }$ , must be constant across time (or across stocks) as well. 

Although the structural model is motivated by the time series properties of a single stock as its market capitalization changes, the model applies cross-sectionally across diferent securities under the assumption that the exogenously assumed cost of a private signal $c _ { I }$ , the shape of the distribution of signals $m .$ , and the informativeness of bets $\tau \cdot \theta ^ { 2 }$ are constant across all markets. 

Robustness of Assumptions. Our structural model makes restrictive assumptions which lead to specific properties of equilibrium. Private signals are normally distributed. Bets are linear functions of private signals and are therefore also normally distributed. Price impact is linear in bet size. Informed traders place one bet in a dealer market setting rather than shredding bets into many pieces and executing them at an equilibrium speed over time. Dealers do not make profits; there are no bidask spread costs; there are no “efective bid-ask spread” costs related to immediate reversal of temporary price impact in executing bets. 

The empirical results we are about to describe are not consistent with the “linearnormal” features of the structural model, but are consistent with the more general invariance hypotheses concerning bet size and transactions costs in section 1. In section 5, we find that the size of unsigned bets closely fits a log-normal distribution, not a normal distribution. In section 6, we find that a linear price impact model predicts transaction costs reasonably well, but a square root model predicts transaction costs better than a linear model. 

We conjecture that it should be possible to modify our structural model to accommodate non-normally distributed bet size, non-linear price impact, and dynamic execution of bets at an equilibrium speed proportional to the rate at which business time unfolds. 

Although the structural model assumes that fundamental volatility $\sigma _ { F } ,$ shares outstanding N, and noise-trader turnover rate η are constants, it is also straightforward to modify the model so that these quantities vary over time or across stocks. 

We provide a discussion of the invariance hypotheses in section 1 separately from the discussion of the structure model in this section because the invariance hypotheses are likely to hold more generally than under the somewhat restrictive assumptions of our structural model. The structural model is to be interpreted as a “proof of concept,” while the invariance hypotheses should apply more generally. 

## 3 Microstructure Invariance in the Context of the Market Microstructure Literature

Market microstructure invariance builds a bridge from theoretical models of market microstructure to empirical tests of those models. Theoretical microstructure models usually suggest measures of liquidity based on the idea that order flow imbalances move prices. By scaling business time to be proportional to the rate at which bets arrive, market microstructure invariance imposes cross-sectional (or time-series) restrictions which make it easier to implement liquidity measures based on order flow imbalances. 

Many theoretical models use game theory to model trading. These models typically make specific assumptions about the risk aversion of traders, the consistency of beliefs across traders, the flow of public and private information which informed traders use to trade, the flow of orders from liquidity traders, and auction mechanisms in the context of which market makers compete to take the other sides of trades. Some models emphasize adverse selection, such as Treynor (1995), Kyle (1985), Glosten and Milgrom (1985), and Back and Baruch (2004); some models emphasize inventory dynamics, such Grossman and Miller (1988) and Campbell and Kyle (1993); some models emphasize both, such as Grossman and Stiglitz (1980) and Wang (1993). 

While these theoretical models are all based on the idea that order flow imbalances move prices (with particular parameters depending on specifics of each model), it has proven dificult to infer from these models precise empirical implications. Theoretical models usually provide neither a unified framework for mapping the theoretical concept of an order flow imbalance into its empirical measurements nor precise predictions concerning how price impact varies across diferent stocks. 

Instead, researchers have taken an approach based on ad hoc empirical intuition. For example, price changes can be regressed on imperfect empirical proxies for order flow imbalances— $\mathrm { e . g . }$ , the diference between uptick and downtick volume, popularized by Lee and Ready (1991)—to obtain market impact coeficients, which can then be related to stock characteristics such as market capitalization, trading volume, and volatility. Breen, Hodrick and Korajczyk (2002) is an example of this approach. A voluminous empirical literature describes how the rate at which orders arrive in calendar time, the dollar size of orders, the market impact costs, and bid-ask spread costs vary across diferent assets. For example, Brennan and Subrahmanyam (1998) estimate order size as a function of various stock characteristics. Hasbrouck (2007) and Holden, Jacobsen and Subrahmanyam (2015) provide surveys of this empirical literature. 

In contrast to this literature, microstructure invariance generates precise empirically testable predictions about how the size of bets, arrival rate of bets, market impact costs, and bid-ask spread costs vary across assets with diferent levels of trading activity. These predictions are consistent with intuition shared by many models. The unidentified parameters in theoretical models show up as invariant constants $( \mathrm { e . g . , } E \{ | \tilde { I } | \}$ and $\bar { C } _ { B } )$ , which can be calibrated from data. 

In this sense, microstructure invariance is a modeling principle applicable to different models, not a model itself. It compliments theoretical models by making it easier to test them empirically. 

Applying Invariance to the Model of Kyle (1985). Consider, for example, the continuous-time theoretical model of Kyle (1985). The market depth formula $\lambda = \sigma _ { V } / \sigma _ { U }$ in that model measures market depth (in units of dollars per share per share) as the ratio of the standard deviation of stock price changes $\sigma _ { V }$ (measured in dollars per share per square root of units of time) to the standard deviation in order flow imbalances $\sigma _ { U }$ (measured in shares per square root of units of time). This formula asserts that price fluctuations result from the linear impact of order flow imbalances. The market depth formula itself does not depend on specific assumptions about interactions among market makers, informed traders, and noise traders. An empirical implementation of the market impact formula $\lambda = \sigma _ { V } / \sigma _ { U }$ should not be considered a test of the specific assumptions of the model of Kyle (1985), such as the existence of a monopolistic informed trader who trades smoothly and patiently in a context where less patient liquidity traders trade more aggressively and market makers set stock prices eficiently. Instead, empirical implementation of the formula $\lambda = \sigma _ { V } / \sigma _ { U }$ attempts the more general task of measuring a market impact coeficient λ based on the assumption that price fluctuations result from the linear impact of order flow innovations, a property shared by many models, including the structural model in section 2. 

Measuring the numerator $\sigma _ { V }$ is much more straightforward than measuring the denominator $\sigma _ { U }$ . The value of $\sigma _ { V }$ is easily inferred from a stock price and returns volatility. In the context of our structural model (where $\sigma = \bar { \sigma } )$ , we have $\sigma _ { V } = \bar { \sigma } \cdot P$ 

Measuring the denominator $\sigma _ { U }$ is dificult because the connection between observed trading volume and order flow imbalances is not straightforward. Intuitively, $\sigma _ { U }$ should be related to trading volume in some way. The continuous-time model provides no help concerning what this relationship is; in the Brownian motion model of Kyle (1985), trading volume is infinite. Without some approach for measuring $\sigma _ { U } ,$ the model is untestable. In the context of our structural model, order flow imbalances result from random discrete decisions by traders to change stock holdings so that the standard deviation of order imbalances is given by $\sigma _ { U } = \gamma ^ { 1 / 2 } \cdot [ E \{ \tilde { Q } ( \bar { t } ) ^ { 2 } \} ] ^ { 1 / 2 }$ This calculation is also consistent with the spirit of other models, such as Glosten and Milgrom (1985) and Back and Baruch (2004). 

The formulas for the numerator and denominator imply that the price impact of a bet of X shares, expressed as a fraction of the value of a share $P ,$ is given by 

$$
\frac {\lambda}{P ^ {2}} \cdot (X \cdot P) = \frac {\sigma_ {V}}{\sigma_ {U}} \cdot \frac {X}{P} = \bar {\sigma} \gamma^ {- 1 / 2} \cdot \frac {X}{[ E \{\tilde {Q} (t) ^ {2} \} ] ^ {1 / 2}}.\tag{52}
$$

Thus, a one-standard deviation bet $X = [ E \{ \tilde { Q } ( t ) ^ { 2 } \} ] ^ { 1 / 2 }$ has a price impact $\bar { \sigma } \gamma ^ { - 1 / 2 }$ equal to one standard deviation of returns volatility ¯σ measured over a time interval of length $1 / \gamma , \ \mathrm { i . e . }$ ., the expected time between bet arrivals. Empirical tests of this formula require assumptions about $\tilde { Q }$ and $\gamma ,$ which decompose the order flow so that the standard deviation of order flow imbalances can be calculated. 

This formula can be tested empirically using restrictions imposed by microstructure invariance. Using equations (5) and (6) to determine how $\gamma$ and moments of $\tilde { Q }$ vary with observable volume and volatility, we find that the price impact cost of an order of dollar size $X \cdot P .$ , as a fraction of the value traded, is 

$$
\frac {\lambda}{P ^ {2}} \cdot (X \cdot P) := \frac {\bar {\sigma}}{P \cdot \gamma^ {1 / 2} \cdot (E \tilde {Q} ^ {2}) ^ {1 / 2}} \cdot (X \cdot P) = \frac {E \{| \tilde {I} | \} ] ^ {2 / 3}}{[ E \{\tilde {I} ^ {2} \} ] ^ {1 / 2}} \cdot \frac {\bar {\sigma}}{P \cdot \bar {V}} \cdot \bar {W} ^ {1 / 3} \cdot (X \cdot P).\tag{53}
$$

The percentage price impact is proportional to ${ \bar { W } } ^ { 1 / 3 } \cdot { \bar { \sigma } } / ( P \cdot { \bar { V } } )$ , which itself is proportional to the illiquidity measure $1 / L ^ { 2 }$ . As a consequence of the hypothesis, which implies that the size and number of bets vary with the $1 / 3$ and $2 / 3$ exponents of trading activity, the distribution of $\tilde { I }$ invariant. Since this makes the proportionality constant $[ \check { E } \{ \tilde { I } ^ { 2 } \} ] ^ { - 1 / 2 } \cdot E \{ | \tilde { I } | \} ] ^ { 2 / 3 }$ invariant as well, implementation of the market impact formula (53) requires calibration of only one proportionality constant for all stocks and all time periods. Note that this constant does not depend on the units of time in which variables are measured, because $\tilde { I }$ itself does not depend on time units. 

As an alternative to invariance, the formula $\lambda = \sigma _ { V } / \sigma _ { U }$ can be implemented empirically by imposing diferent assumptions concerning the connection between $\sigma _ { U }$ and trading volume. For example, we can assume that the expected arrival rate of bets is some unknown constant, the same for all stocks; this will imply that $\sigma _ { U }$ is proportional to volume $V$ and illiquidity measure in formula (52) is proportional to $\sigma / ( P \cdot V )$ . We obtain 

$$
\frac {\lambda}{P ^ {2}} \cdot (X \cdot P) := \frac {\bar {\sigma}}{P \cdot \gamma^ {1 / 2} \cdot (E \tilde {Q} ^ {2}) ^ {1 / 2}} \cdot (X \cdot P) \propto \frac {\bar {\sigma}}{P \cdot \bar {V}} \cdot (X \cdot P).\tag{54}
$$

This empirical implementation of the formula can be thought of as the illiquidity ratio in Amihud (2002). Indeed, Amihud’s illiquidity ratio is the time-series average of the daily ratios of the absolute value of percentage returns to dollar volume. To the extent that dollar volume is relatively stable across time and returns are drawn from the same distribution, illiquidity ratio is efectively proportional to $\sigma / ( P \cdot V )$ . Although this is a logically consistent way to connect theory with empirical implementation, it is unrealistic to assume that the most actively traded and least actively traded stocks have the same number of bets per day; empirical intuition suggests that stocks with high levels of trading activity have more bets per day than stocks with low levels of trading activity. We are aware of no empirical studies which claim that the number of orders or bets in diferent stocks is the same. 

The same issue can be addressed by thinking about time units. Unlike our illiquidity measure $1 / L = \iota ^ { 2 } \bar { C } _ { B } \cdot [ P \cdot \bar { V } / \bar { \sigma } ^ { 2 } ] ^ { - 1 / 3 }$ , the Amihud ratio $\sigma / ( P \cdot V )$ has time units: $\sigma ^ { 2 }$ and P · V have the same time units, but $\sigma$ and P · V do not; Amihud’s ratio thus depends on the time horizon at which volume and volatility are measured. To keep the left-hand side consistent with the right-hand side of equation (54), the proportionality constant in that equation must change when time units are changed. Furthermore, if the invariance-implied market impact formula (53) is correct, then Amihud’s market impact formula (54) theoretically implies a diferent proportionality constant for every stock. This problem can be “fixed”—i.e., the same proportionality coeficient can be obtain for every stock using Amihud’s approach—if data for each stock is sampled at a diferent stock-specific frequency appropriate to the stock’s level of trading activity. Invariance implies that the appropriate sampling frequency should be proportional to $1 / \gamma ,$ which is proportional to $W ^ { - 2 / 3 }$ 

Illiquidity ratios calculated using data sampled at the same calendar time frequencies, as proposed originally and implemented in many empirical studies, implicitly rely on the unrealistic assumption that the standard deviation of order imbalances is proportional to trading volume. In contrast, our illiquidity measure 1/L does not depend on time units, and therefore it does not matter over what time horizons its components are measured; even if diferent horizons are used for diferent stocks, its value will be the same. 

## 4 Data

Portfolio Transitions Data. We test the empirical implications of market microstructure invariance using a proprietary dataset of portfolio transitions from a leading vendor of portfolio transition services. During the evaluation period, this portfolio transition vendor supervised more than 30 percent of outsourced U.S. portfolio transitions. The sample includes 2,552 portfolio transitions executed over the period 2001-2005 for U.S. clients. A portfolio transition may involve orders for hundreds of individual stocks. Each order is a stock-transition pair potentially executed over multiple days using a combination of internal crosses, external crosses, and open market transactions. 

The portfolio transitions dataset contains fields identifying the portfolio transition; its starting and ending dates; the stock traded; the trade date; the number of shares traded; a buy or sell indicator; the average execution price; the pre-transition benchmark price (closing price the day before the transition trades began); commissions; SEC fees; and a trading venue indicator distinguishing among internal crossing networks, external crossing networks, open market transactions, and in-kind transfers. 

When old “legacy” and new “target” portfolios overlap, positions are transferred from the legacy to the new portfolio as “in-kind” transfers. For example, if the legacy portfolio holds 10, 000 shares of IBM stock and the new portfolio holds 4, 000 shares of IBM, then 4, 000 shares are transferred in-kind and the balance of 6, 000 shares is sold. The in-kind transfers do not incur transactions costs and have no efect on our empirical analysis. The 6, 000 shares sold constitute one “portfolio transition order,” even if the 6, 000 shares are sold over multiple days. 

We augment the portfolio transitions data with stock price, returns, and volume data from CRSP. Only common stocks (CRSP share codes of 10 and 11) listed on the New York Stock Exchange (NYSE), the American Stock Exchange (Amex), and NASDAQ in the period from January 2001 through December 2005 are included in the sample. ADRs, REITs, and closed-end funds are excluded. Also excluded are stocks with missing CRSP information necessary to construct variables used for empirical tests, transition orders in high-priced Berkshire Hathaway class A shares, and transition observations which appeared to contain typographical errors and obvious inaccuracies. Since it is unclear from the data whether adjustments for dividends and stock splits are made in a consistent manner across all transitions, all observations with non-zero payouts during the first week following the starting date of portfolio transitions were excluded from statistical tests. 

After exclusions, there are 439,765 observations (“orders”), including 201,401 buy orders and 238,364 sell orders. 

CRSP Data: Prices, Volume, and Volatility. For each of the transition-stock observations (i = 1, . . . , 439765), we collect data on pre-transition benchmark price, expected volume, and expected volatility. The benchmark price, denoted $P _ { 0 , i }$ , is the closing price for the stock the evening before the first trade is made in any of the stocks in the portfolio transition. A proxy for expected daily trading volume, denoted $V _ { i }$ (in shares), is the average daily trading volume for the stock in the previous full pre-transition calendar month. 

The expected volatility of daily returns, denoted $\sigma _ { i }$ for order $i ,$ is calculated using past daily returns in two diferent ways. 

First, for each security $j$ and each calendar month $m ,$ we estimate the monthly standard deviation of returns $\sigma _ { j , m }$ as the square root of the sum of squared daily returns for the full calendar month m (without de-meaning or adjusting for autocorrelation). We define $\sigma _ { i } = \sigma _ { j , m } / N _ { m } ^ { 1 / 2 }$ , where $j$ corresponds to the stock traded in order $i ,$ m is the previous full calendar month preceding order $i ,$ and $N _ { m }$ is the number of CRSP trading days in month m. 

Second, to reduce efects from the positive skewness of the standard deviation estimates, we estimate for each stock j a third-order moving average process for the changes in $\ln ( \sigma _ { j , m } )$ for all months m over the entire period 2001-2005: (1 − $L ) \ln ( \sigma _ { j , m } ) = \Theta _ { j , 0 } + ( 1 - \Theta _ { j , 1 } L - \Theta _ { j , 2 } L ^ { 2 } - \Theta _ { j , 3 } L ^ { 3 } ) u _ { j , m }$ . Letting $y _ { j , m }$ denote the estimate of $\ln ( \sigma _ { j , m } )$ and $\hat { V } _ { j }$ the variance of the prediction error, we alternatively define the conditional forecast for the volatility of daily returns by $\sigma _ { i } = \exp ( y _ { j , m } + \hat { V } _ { j } / 2 ) / N _ { m } ^ { 1 / 2 }$ where m is the current full calendar month for order i. 

These volatility estimates can be thought of as instrumental variables for true expected volatility. While below we report results using the second definition of $\sigma _ { i }$ based on the log-ARIMA model, these results remain quantitatively similar when we use the first definition of $\sigma _ { i }$ based on simple historical volatility during the preceding full calendar month. 

Except to the extent that the ARIMA model uses in-sample data to estimate model parameters, we use the pre-transition variables known to the market before portfolio transition trades are executed in order to avoid any spurious efects from using contemporaneous variables. 

Descriptive Statistics. Table 1 reports descriptive statistics for traded securities in panel A and for individual transition orders in panel B. The first column reports statistics for all securities in aggregate; the remaining ten columns report statistics for stocks in ten dollar volume groups. Instead of dividing the securities into ten deciles with the same number of securities in each decile, volume break points are set at the 30th, 50th, 60th, 70th, 75th, 80th, 85th, 90th, and 95th percentiles of trading volume for the universe of stocks listed on the NYSE with CRSP share codes of 10 and 11. Group 1 contains stocks in the bottom 30th percentile of dollar trading volume. Group 10 approximately corresponds to the universe of S&P 100 stocks. The top five groups approximately cover the universe of S&P 500 stocks. Narrower percentile bands for the more active stocks make it possible to focus on the stocks which are most important economically. For each month, the thresholds are recalculated and the stocks are reshufled across bins. 

Panel A of table 1 reports descriptive statistics for traded securities. For the entire sample, the median daily volume is $18.72 million, ranging from $1.13 million for the lowest volume group to $212.85 million for the highest volume group. The median volatility is 1.93 percent per day, ranging from 1.76 percent in the highest volume decile to 2.16 in the lowest decile. Since there is so much more cross-sectional variation in dollar volume than in volatility across stocks, the variation in trading activity across stocks is related mostly to variation in dollar volume. Trading activity difers by a factor of 150 between stocks in the lowest group and stocks in the highest group, and this variation creates statistical power helpful in determining how transactions costs and order sizes vary with trading activity. 

The median quoted bid-ask spread, obtained from the transition dataset, is 12.04 basis points; its mean is 25.42 basis points. From lowest volume group to highest volume group, the median spread declines monotonically from 40.96 to 4.83 basis points, by a factor of 8.48. A back-of-the-envelope calculation based on invariance suggests that spreads should decrease approximately by a factor of $1 5 0 ^ { 1 / 3 } \approx 5 . 3 1$ from lowest to highest volume group. The diference between 5.31 and 8.48 is partially explained by diferences in returns volatility across the volume groups and warrants further investigation.The monotonic decline of almost one order of magnitude is potentially large enough to generate significant statistical power in estimates of a bid-ask spread component of transactions costs based on implementation shortfall. 

Panel B of table 1 reports properties of portfolio transition order sizes. The average order size is 4.20% of average daily volume, declining monotonically across the ten volume groups from 16.23% in the smallest group to 0.49% in the largest group, by a factor of 33.12. The median order is 0.57% of average daily volume, also declining monotonically from 3.33% in the smallest group to 0.14% in the largest group, by a factor of 23.79. The invariance hypothesis implies that order sizes should decline by a factor of approximately $1 5 0 ^ { 2 / 3 } \approx 2 8 . 2 3$ , a value which matches the data closely. The medians are much smaller than the means, indicating that distributions of order sizes are skewed to the right. We show below that the distribution of order sizes closely fits a log-normal. 

The average trading cost (estimated based on implementation shortfall, as explained below) is 16.79 basis points per order, ranging from 44.95 basis points in the lowest volume group to 6.16 basis points in the highest volume group. Invariance suggests that these costs should fall by a factor of $1 5 0 ^ { 1 / 3 } \approx 5 . 3 1$ , somewhat smaller than the actual decline. The cost estimates exclude commissions and SEC fees.<sup>11</sup> 

One portfolio transition typically contains orders for dozens or hundreds of stocks; it typically takes several days to execute all of the orders. About 60% of orders are executed during the first day of a portfolio transition. Since transition managers often operate under a “cash-in–advance” constraint—using proceeds from selling stocks in a legacy portfolio to acquire stocks in a target portfolio—sell orders tend to be executed slightly faster than buy orders (1.72 days versus 1.85 days). In terms of dollar volume, about 41%, 23%, 15%, 7%, and 5% of dollar volume is executed on the first day through the fifth days respectively. The two longest transitions in the sample were executed over 18 and 19 business days. The time frame for a portfolio transition is usually set before its actual implementation begins. 

## 5 Empirical Tests Based on Order Sizes

Market microstructure invariance predicts that the distribution of $\bar { W } ^ { 2 / 3 } \cdot \tilde { Q } / \bar { V }$ does not vary across stocks or time (see equation (6)). We test these predictions using data on portfolio transition orders, making the identifying assumption that portfolio transition orders are proportional to bets. 

Portfolio Transitions and Bets. Since bets are statistically independent intended orders, bets can be conceptually dificult for researchers to observe. Consider, for example, a trader who makes a decision on Monday to make one bet to buy 100,000 shares of stock, then implements the bet by purchasing 20,000 shares on Monday and 80,000 shares on Thursday. To an econometrician, this one bet for 100,000 shares may be dificult to distinguish from two bets for 20,000 shares and 80,000 shares respectively. In the context of a portfolio transition, identifying a bet is easier because the size of the order for 100,000 shares is known and recorded on Monday, even if the order is executed over several subsequent days. 

Portfolio transition orders may not have a size distribution matching precisely the size distribution of typical bets. Transition orders may be smaller than bets if transitions tend to liquidate a portion of an asset manager’s positions or larger than bets if transitions liquidate the sum of bets made by the asset manager in the past. When both target and legacy portfolios hold long positions in the same stock, the portfolio transition order may represent the diference between two bets. 

Let $X _ { i }$ denote the unsigned number of shares transacted in portfolio transition order i, $i = 1 , \ldots , 4 3 9 7 6 5$ . The quantity $X _ { i }$ sums shares traded over multiple days, 

excluding in-kind transfers. 

We make the identifying assumption that, for some constant $\delta$ which does not vary across stocks with diferent characteristics such as trading activity, the distribution of scaled portfolio transition orders $\delta \cdot X _ { i }$ is the same as the distribution of unsigned bets in the same stock at the same time, denoted $| \tilde { Q } |$ . If $\delta = 1$ , the distribution of portfolio transition orders matches the distribution of bets. 

The Empirical Hypotheses of Invariance and Log-Normality for the Size Distribution of Portfolio Transition Orders. Let $W _ { i } : = V _ { i } \cdot P _ { i } \cdot \sigma _ { i }$ and ${ \bar { W } } _ { i } : =$ $\bar { V } _ { i } \cdot P _ { i } \cdot \bar { \sigma } _ { i }$ denote trading activity and betting activity, respectively, for the stock in transition order $i .$ Under the identifying assumption that portfolio transition orders are proportional to bets, invariance of bets implies invariance of portfolio transition orders. Specifically, replacing $\tilde { Q }$ with $X _ { i }$ in equation (6) implies that the distribution of $\bar { W } _ { i } ^ { 2 / 3 } \cdot X _ { i } / \bar { V } _ { i }$ does not vary with stock characteristics such as volume, volatility, stock price, or market capitalization. 

To facilitate intuitive interpretation of parameter estimates, we scale observations by a hypothetical “benchmark stock” with share price $P ^ { * }$ of $40, daily volume $V ^ { * }$ of one million shares, and volatility $\sigma ^ { * }$ of $2 \%$ per day, implying $W ^ { * } = 4 0 \cdot 1 0 ^ { 6 } \cdot 0 . 0 2$ . This benchmark stock would belong to the bottom tercile of S&P 500 (volume group $7$ in table 1). 

Combining invariance of portfolio transition orders with equations (1) and (2) to convert the betting activity variables $\bar { W } _ { i }$ and $\bar { V } _ { i }$ into trading activity variables $W _ { i }$ and $V _ { i }$ and taking logs, invariance implies the empirically testable relationship 

$$
\ln \left(\left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {2 / 3} \cdot \frac {X _ {i}}{V _ {i}}\right) = \ln (\bar {q}) + \tilde {\epsilon} _ {i}.\tag{55}
$$

Under the identifying assumptions that the volume multiplier $\zeta ,$ the volatility multiplier $\psi .$ , and the deflator $\delta$ do not vary across observations, ln $( \bar { q } )$ is an invariant constant $\ln ( \bar { q } ) = E \{ \ln ( | \tilde { Q } ^ { * } | / V ^ { * } ) \} - \ln ( \delta )$ and $\tilde { \epsilon } _ { i }$ is a zero-mean error with the same invariant distribution as $\ln ( | \tilde { I } | ) - E \{ \ln ( | \tilde { I } | ) \} . ^ { 1 2 }$ Adjustment by $W ^ { * }$ in equation (55) scales each observation on the left side so that it has the same invariant distribution as the log of a hypothetical portfolio transition order in the benchmark stock, expressed as a fraction of its expected daily volume. 

We will also examine the stronger log-normality hypothesis—not implied by microstructure invariance—that the distribution of unsigned order sizes adjusted for trading activity $[ W _ { i } / W ^ { * } ] ^ { 2 / 3 } \cdot X _ { i } / V _ { i }$ has a log-normal distribution, i.e., $\tilde { \epsilon } _ { i }$ in equation (55) has a normal distribution. The log-normality hypothesis implies that the rightside of equation (55) is characterized by two invariant constants, the mean $\ln ( \bar { q } )$ and the variance of $\tilde { \epsilon } _ { i }$ 

Next, we implement several tests to examine this hypothesis. 

The Graphical Relationship Between Order Sizes and Trading Activity. One way to examine the invariance hypothesis is to plot the log of order size as a fraction of average daily volume ln $[ X _ { i } / V _ { i } ]$ against the log of scaled trading activity ln $[ W _ { i } / W ^ { * } ]$ . Figure 4 presents a cloud of points for all $^ { 4 0 0 , 0 0 0 + }$ portfolio transition orders. The line ln $[ X _ { i } / V _ { i } ] = - 5 . 7 1 { - } 2 / 3 { \cdot } \ln [ W _ { i } / W ^ { * } ]$ is also shown for comparison. The slope of this line is fixed at $- 2 / 3$ , as implied by invariance; the intercept, estimated from an OLS regression, is the sample mean. On the horizontal axis, zero represents the log of trading activity in the benchmark stock; on the vertical axis, zero represents orders for 100% of expected daily volume. The shape of the “super-cloud” conforms well with the invariance hypothesis in that the slope of $- 2 / 3$ is close to the shape of the plotted points and there is only little evidence of heteroscedasticity. 

Log-Normal Order Size Distribution for Volume and Volatility Groups. When the portfolio transition orders are sorted into diferent groups based on characteristics such as dollar volume, volatility, stock price, and turnover, the joint hypotheses of invariance and log-normality imply that the means and variances of $\ln [ [ W _ { i } / W ^ { * } ] ^ { 2 / 3 } \cdot X _ { i } / V _ { i } ]$ for each group should match the mean and variance of the pooled sample. The pooled sample mean of $\ln [ [ W _ { i } / W ^ { * } ] ^ { 2 / 3 } \cdot X _ { i } / V _ { i } ]$ is −5.71; the pooled sample variance is 2.53. The pooled sample mean is an estimate of ln(¯q); the pooled sample variance is an estimate of the variance of the error $\tilde { \epsilon } _ { i }$ 13 

To examine this hypothesis visually, we plot the empirical distributions of the lefthand side of equation (55), ln $[ [ W _ { i } / W ^ { * } ] ^ { 2 / 3 } \cdot X _ { i } / V _ { i } ]$ , for selected volume and volatility groups. As before, we define ten dollar volume groups with thresholds corresponding to the 30th, 50th, 60th, 70th, 75th, 80th, 85th, 90th, and 95th percentiles of NYSE dollar volume. We define five volatility groups with thresholds corresponding to the 20th, 40th, 60th, and 80th percentiles of returns standard deviation for NYSE stocks. On each plot, we superimpose the bell-shaped density function $N ( - 5 . 7 1 , 2 . 5 3 )$ matching the mean and variance of the pooled sample. 

Figure 2 shows plots of the empirical distributions of $\ln [ [ W _ { i } / W ^ { * } ] ^ { 2 / 3 } \cdot X _ { i } / V _ { i } ]$ for volume groups 1, 4, 7, 9, and 10 and for volatility groups 1, 3, and 5. Consistent with the invariance hypothesis, these fifteen distributions of W-adjusted order sizes are all visually strikingly similar to the superimposed normal distribution. Results for the remaining 35 subgroups also look very similar and therefore are not presented in this paper. The visual similarity of the distributions is reflected in the similarity of their first four moments. For the 15 volume-volatility groups, the means range from −6.03 to −5.41, close to the mean of −5.71 for the pooled sample. The variances range from 2.23 to 2.90, also close to the variance of 2.53 for the pooled sample. The skewness ranges from −0.21 to 0.10, close to skewness of zero for the normal distribution. The kurtosis ranges from 2.73 to 3.38, also close to the kurtosis of 3 for a normal random variable. These results suggest that it is reasonable to assume that unsigned order sizes have a log-normal distribution. Scaling order sizes by $[ W / W ^ { * } ] ^ { 2 / 3 }$ , as implied by the invariance hypothesis, adjusts the means of the distributions so that they visually appear to be similar. 

Despite the visual similarity, a Kolmogorov-Smirnov test rejects the hypothesis that all fifty empirical distributions are generated from the same normal distribution. The standard deviation of the means across bins is larger than implied by a common normal distribution. Microstructure invariance does not describe the data perfectly, but it makes a good benchmark from which the modest deviations seen in these plots can be investigated in future research. 

Figure 3 further examines log-normality by focusing on the tails of the distributions of portfolio transition orders. For each of the five volume groups 1, 4, 7, 9, and 10, panel A shows quantile-quantile plots of the empirical distribution of ln $[ [ W _ { i } / W ^ { * } ] ^ { 2 / 3 } \cdot X _ { i } / V _ { i } ]$ versus a normal distribution with the same mean and variance. The more similar these empirical distributions are to a normal distribution, the closer the plots should be to the 45-degree line. Panel B shows logs of ranks based on scaled order sizes. Under the hypothesis of log-normality, the right tail should be quadratic. A straight line in the right tail implies a power law. Both panels show that the empirical distributions are similar to a normal distribution, except in the far right and left tails. 

In panel A, the smallest orders in the left tails tend to be smaller than implied by a normal distribution. These observations are economically insignificant. Most of them represent one-share transactions in low-price stocks (perhaps the result of coding errors in the data). There are too few such orders to have a meaningful efect on our statistical results. 

In panel A, the largest orders in the right tails are much more important economically. On each subplot, a handful of positive outliers (out of 400,000+ observations) do not appear to fit a normal distribution. The largest orders in low-volume stocks appear to be smaller than implied by a normal distribution, and the largest orders in high-volume stocks appear to be larger than implied by a normal distribution. 

The finding that the largest orders in low-volume stocks are smaller than implied by a log-normal may be explained by reporting requirements. When an owner acquires more than 5% of the shares of a publicly traded company, the SEC requires information to be reported on Schedule 13D. To avoid reporting requirements, large institutional investors may intentionally acquire fewer shares when intended holdings would otherwise exceed the 5% reporting threshold. Indeed, all 400,000+ portfolio transition orders are for amounts smaller than 4.5% of shares outstanding. A closer examination reveals that the five largest orders for low-volume stocks accounts for about 2%, 3%, 4%, 4%, and 4% of shares outstanding, respectively, just below the 5% threshold. The largest order in high-volume stocks is for about 1% of shares outstanding. 

To summarize, we conclude that the distribution of portfolio transition order sizes appears to conform closely to—but not exactly to— the invariance hypothesis. 

Furthermore, the distribution of order sizes appears to be similar to—but not exactly equal to—a log-normal. 

OLS Estimates of Order Size. The order size predictions from equation (55) can also be tested using a simple log-linear OLS regression 

$$
\ln \left[ \frac {X _ {i}}{V _ {i}} \right] = \ln \left[ \bar {q} \right] + \alpha_ {0} \cdot \ln \left[ \frac {W _ {i}}{W ^ {*}} \right] + \tilde {\epsilon} _ {i}.\tag{56}
$$

Invariance of bets implies $\alpha _ { 0 } = - 2 / 3$ 

To adjust standard errors of OLS estimates of $\alpha _ { 0 }$ for positive contemporaneous correlation in transition order sizes across diferent stocks, the 439, 765 observations are pooled by week over the 2001-2005 period into 4, 389 clusters across 17 industry categories. The double clustering by weeks and industries conservatively adjusts standard errors for large portfolio transitions that may involve hundreds of relatively large orders, executed during the course of a week and potentially concentrated in particular industries.<sup>14</sup> 

Table 2 presents estimates for the OLS coeficients in equation (56). The first column of the table reports the results of a regression pooling all the data. The four other columns in the table report results for four separate OLS regressions in which the parameters are estimated separately for NYSE Buys, NYSE Sells, NASDAQ Buys, and NASDAQ Sells. 

For the entire sample, the estimate for $\alpha _ { 0 }$ is $\hat { \alpha } _ { 0 } = - 0 . 6 2$ with standard error of 0.009. Economically, the point estimate for $\alpha _ { 0 }$ is close to the value $- 2 / 3$ predicted by the invariance hypothesis, but the hypothesis $\alpha _ { 0 } ~ = ~ - 2 / 3$ is strongly rejected $( F = 2 5 . 3 1 , p < 0 . 0 0 0 1 )$ ) because the standard error is very small. 

When the sample is broken down into NYSE Buys, NYSE Sells, NASDAQ Buys, and NASDAQ Sells, it is interesting to note that the estimated coeficients for buy orders, −0.63 for NYSE and −0.71 for NASDAQ, are closer to $- 2 / 3$ than the coeficients for sell orders, −0.59 for both NYSE and NASDAQ. Since portfolio transitions tend to be applied to long-only portfolios, sell orders tend to represent liquidations of past bets. If the size distribution of sell orders depends on past values of volume and volatility—not current values—there is an errors-in-variables problem related to past trading activity being used as a noisy version of current trading activity. This will bias the absolute values of coeficient estimates downwards, consistent with the absolute values of the coeficient estimates for NYSE and NASDAQ sell orders being less than $2 / 3$ 

<sup>14</sup>A potential econometric issue with the log-linear specification in equation (56) is that taking the log of order size as a fraction of average daily volume may create large negative outliers from tiny, economically meaningless orders, with an inordinately large influence on coeficient estimates. Since we have shown above that the shape of the distribution of scaled order sizes closely matches a log-normal, these tiny orders are expected to have only a negligible distorting efect on estimates. 

Quantile Estimates of Order Sizes. Table 7 in the Appendix presents quantile regression results for equation (56) based on the 1st (smallest orders), 5th, 25th, 50th, 75th, 95th, and 99th percentiles (largest orders). The corresponding quantile estimates for $\alpha _ { 0 }$ are $- 0 . 6 5 , \ : - 0 . 6 4 , \ : - 0 . 6 1 , \ : - 0 . 6 2 , \ : - 0 . 6 1 , \ : - 0 . 6 4$ , and −0.63, respectively. Although the hypothesis $\alpha _ { 0 } = - 2 / 3$ is rejected due to small standard errors, all quantile estimates are economically close to the value of $- 2 / 3$ predicted by the invariance hypothesis. 

Model Calibration and Its Economic Interpretation. Under the invariance and log-normality hypotheses, we can calibrate the distribution of bet sizes by imposing the restriction $\alpha _ { 0 } = - 2 / 3$ on equation (56). Thus, only the constant term in the regression needs to be estimated. 

The results of this calibration exercise are presented in table 3. The estimated constant term, −5.71, is the previously reported sample mean of ln(¯q) in equation (55). The mean-square error, 2.53, is the previously reported sample variance of $\tilde { \epsilon } _ { i }$ in equation (55). 

The $R ^ { 2 }$ (with zero degrees of freedom) is 0.3149; the log of trading activity ln $( W / W ^ { * } )$ , with the coeficient $\alpha _ { 0 } = - 2 / 3$ imposed by invariance, explains a significance percentage of the variation of order size as a fraction of volume $X _ { i } / V _ { i }$ 

When the parameter $\alpha _ { 0 }$ is estimated rather than held fixed, changing $\alpha _ { 0 }$ from the predicted value of $\alpha _ { 0 } = - 2 / 3$ to the estimated value of $\hat { \alpha _ { 0 } } = - 0 . 6 2$ increases the $R ^ { 2 }$ from 0.3149 (table 3) to 0.3167 (table 2), a modest increase of 0.0018. Although statistically significant, the addition of one degree of freedom does not add much explanatory power. 

We relax the specification further by allowing the coeficients on the three components of trading activity—volatility $\sigma _ { i } ,$ price $P _ { 0 , i }$ , and volume $V _ { i } \mathrm { - a s }$ well as monthly turnover rate $\nu _ { i }$ to vary freely: 

$$
\ln \left[ \frac {X _ {i}}{V _ {i}} \right] = \ln [ \bar {q} ] + \alpha_ {0} \cdot \ln \left[ \frac {W _ {i}}{W ^ {*}} \right] + b _ {1} \cdot \ln \left[ \frac {\sigma_ {i}}{0 . 0 2} \right] + b _ {2} \cdot \ln \left[ \frac {P _ {0 , i}}{4 0} \right] + b _ {3} \cdot \ln \left[ \frac {V _ {i}}{1 0 ^ {6}} \right] + b _ {4} \cdot \ln \left[ \frac {\nu_ {i}}{1 / 1 2} \right] + \tilde {\epsilon} _ {i}.\tag{57}
$$

This regression imposes on $\mathrm { l n } [ W _ { i } / W _ { * } ]$ the coeficient $\alpha _ { 0 } = - 2 / 3$ predicted by invariance and then allows the coeficients $b _ { 1 } , ~ b _ { 2 } , ~ b _ { 3 } , ~ b _ { 4 }$ on the three components of $W _ { i }$ and turnover rate to vary freely. The invariance hypothesis implies $b _ { 1 } = b _ { 2 } =$ $b _ { 3 } = b _ { 4 } = 0$ . Table 3 reports that increasing the degrees of freedom from one to four increases the $R ^ { 2 }$ of the regression from 0.3167 to 0.3229, an increase of 0.0062. Although again statistically significant, the improvement in $R ^ { 2 }$ is again modest. Invariance explains much—but not quite all—of the variation in portfolio transition order size across stocks that can be explained by all four variables. 

The point estimates for the coeficient on volatility of $\hat { b } _ { 1 } = 0 . 4 2$ , the coeficient on price of $\hat { b } _ { 2 } = 0 . 2 4$ , the coeficient on share volume of $\hat { b } _ { 3 } = 0 . 0 6$ , the coeficient on turnover rate of $\hat { b } _ { 4 } = - 0 . 1 8$ are all statistically significant, with standard errors of 

0.040, 0.019, 0.010, and 0.015, respectively (see table 8 in the Appendix). The coeficients on volatility and price are significantly positive, indicating that order size—as a fraction of average daily volume—does not decrease with increasing volatility and price as fast as predicted by the invariance hypothesis. The statistically significant positive coeficient on volume may be partially ofset by a statistically significant negative coeficient on turnover rate. 

Discussion. The documented log-normality of bet size is strikingly diferent from the typical assumptions of microstructure models, where innovations in order flow from noise traders are distributed as a normal, not a log-normal or power law. Although normal random variables are a convenient modeling device—they allow conditional expectations to be linear functions of underlying jointly normally distributed variables—their implications are qualitatively very diferent. 

The estimated log-mean of −5.71 implies that a median portfolio transition order size is equal to 0.33% of expected daily volume for the benchmark stock, since $\exp ( - 5 . 7 1 ) \approx 0 . 0 0 3 3$ . The estimated log-variance of 2.53 implies that a one standard deviation increase in order size is a factor of 4.90 for all stocks, since $\exp ( 2 . 5 3 ^ { 1 / 2 } ) \approx$ 4.90. 

We next explain why the log-variance of 2.53 also implies that a large fraction of trading volume and an even larger fraction of returns variance come from large bets. 

Let $\eta ( z )$ and $N ( z )$ denote the PDF and CDF, respectively, of a standardized normal distribution. Define $F ( \bar { z } , p )$ by $\begin{array} { r } { F ( \bar { z } , p ) : = \int _ { z = \bar { z } } ^ { \infty } \exp ( p \cdot \sqrt { 2 . 5 3 } \cdot z ) \cdot \eta ( z ) \cdot d z } \end{array}$ . It is easy to show that $F ( \bar { z } , p ) = \exp ( p ^ { 2 } \cdot 2 . 5 3 / 2 ) \cdot ( 1 - N ( \bar { z } - p \cdot \sqrt { 2 . 5 3 } ) )$ . This implies that the fraction of the pth moment of order size arising from bets greater than ¯z standard deviations above the log-mean is given by $F ( \bar { z } , p ) / F ( - \infty , p ) = 1 - N ( \bar { z } - p \cdot \sqrt { 2 . 5 3 } )$ 

Plugging $p = 1$ , we find that bets larger than ¯z standard deviations above the log mean (median) generate a fraction of total trading volume given by $1 - N ( \bar { z } - \sqrt { 2 . 5 3 } )$ Bets larger than the 50th percentile generate 94.41% of trading volume $( \bar { z } = 0 )$ . Bets larger than than $\sqrt { 2 . 5 3 }$ standard deviations above the log-mean (median) bet size— i.e., the largest 5.39% of bets—generate 50% of trading volume $( \bar { z } = \sqrt { 2 . 5 3 } )$ 

Plugging $p = 2$ , we find that bets larger than ¯z standard deviations above the log-mean bet size contribute a fraction of total returns variance given by $1 - N ( \bar { z } -$ $2 \cdot { \sqrt { 2 . 5 3 } } )$ under the assumption that the contribution of bets to price variance is proportional to their squared size (implied by linear price impact). Bets greater than the 50th percentile generate 99.93% of returns variance $( \bar { z } = 0 )$ Bets larger than than $2 \cdot { \sqrt { 2 . 5 3 } } = 3 . 1 8$ standard deviations above the log-mean—i.e., the largest 0.07% of bets—generate 50% of returns variance $( \bar { z } = 2 \cdot \sqrt { 2 . 5 3 } )$ 

Under the assumptions $\zeta / 2 = \psi = \delta = 1$ (stronger than our identifying assump tions), the estimates of mean and variance imply that the benchmark stock has about 85 bets per day for each of the 252 trading days in a calendar year. These estimates then imply that the 1, 155 largest bets out of 21, 420 bets generate approximately half of the trading volume during one year, and the 15 largest bets generate approximately 

half of returns variance during one year. 

Rare large bets may not only account for a significant percentage of returns variance but may also account for some of the stochastic time series variation in volatility. We conjecture that the pattern of short term volatility associated with execution of rare large bets may depend on the speed with which such bets are executed. Large market disturbances such as the stock market crash of 1929 and 1987, the liquidation of Jerome Kerviel’s rogue trades by Soci´et´e G´en´erale, and the flash crash of May 6, 2010, could have been induced by execution of gigantic bets. 

Another implication of log-normality may be greater kurtosis in the empirical distribution of price changes than a normal distribution would suggest. Given the estimated log-variance of 2.53, the excess kurtosis of one bet has the enormous value of exp(10), or about 22,000. Thus, excess kurtosis in daily price changes may be influenced more by the kurtosis of individual bets than by the random number of bets arriving each day. 

Invariance implies a diferent way of thinking about trading data from that in the “time change” literature, which goes back to Mandelbrot and Taylor (1967) and Clark (1973). Mandelbrot and Taylor (1967) begin with the intuition that the distribution of price changes is a stable distribution, i.e., a distribution such that a linear combination of two independent random variables has the same shape, up to location and scale parameters. Since it has fatter tails than a normal distribution, it is confined to be a stable Pareto distribution. Following this line of research, the econophysics literature—such as Gopikrishnan et al. (1998), Plerou et al. (2000), and Gabaix et al. (2006)—estimates diferent power-laws for the probability distributions of diferent variables and searches for price-formation models consistent with those distributions. Whether order size follows a power law or a log-normal distribution is an interesting question for future research. 

Clark (1973) suggests as an alternative hypothesis that the distribution of daily price changes is subordinated to a normal distribution with a time clock linked to a log-normally distributed trading volume. The log-normal distribution is neither stable nor infinitely divisible; the sum of random variables with independent lognormal distributions is not log-normal. Thus, if daily price changes can be described by Clark’s hypothesis, neither half-day price changes nor weekly price changes will be described by the same hypothesis. 

In some sense, our approach seems to be closer to Mandelbrot and Taylor (1967), who imagine orders of diferent sizes arriving in the market, with business time linked to their arrival rates rather than to trading volume. 

Empirical regularities similar to those implied by invariance can be inferred from the previous literature. Bouchaud, Farmer and Lillo (2009) report, for example, that the number of TAQ prints per day is proportional to market capitalization raised to powers between 0.44 to 0.86. Under the assumption that volatility and turnover rates are stable across stocks as shown in table 1, the midpoint 0.65 of that interval is close to the value of 2/3 implied by invariance for the number of bets per day. 

The log-normality of bet size may be related to the log-normality of assets under management for financial firms. Schwarzkopf and Farmer (2010) study the size of U.S. mutual funds and find that its distribution closely conforms to a log-normal with log-variance of about 2.50, similar to our estimates of log-variance for portfolio transition orders. Their annual estimates of log-variance are stable during the twelve years from 1994 to 2005, ranging from 2.43 to 2.59. For years 1991, 1992, and 1993, the log-variance estimates of 1.51, 1.98, and 2.09 are slightly lower, probably because many observations are missing from the CRSP U.S. mutual funds dataset for those years. 

As discussed by Aitchison and Brown (1957), log-normal distributions can be found in many areas of natural science. For example, Kolmogorov (1941b) proves mathematically that the probability distribution of the sizes of particles under fragmentation converges over time to a log-normal. 

## 6 Empirical Tests Based on Transactions Costs

To examine statistically whether transactions costs conform to the predictions of market microstructure invariance in equation (9), we use the concept of implementation shortfall developed by Perold (1988). Specifically, we estimate costs by comparing the average execution prices of portfolio transition orders with closing prices the evening before any portfolio transition orders begin to be executed. Our tests measure implicit transactions costs resulting from bid-ask spreads and market impact; they exclude explicit transactions costs such as commissions and fees. 

Portfolio Transitions and Implementation Shortfall. In portfolio transitions, quantities to be traded are known precisely before trading begins, these quantities are recorded accurately, and all intended quantities are executed. In other trading situations, quantities intended to be traded may not be recorded accurately, and orders may be canceled or quantities may be revised in response to price movements after trading begins. When orders are canceled after prices move in an unfavorable direction or when order size is increased after prices move in a favorable direction, implementation shortfall may dramatically underestimate actual transactions costs. Portfolio transitions data are not subject to these concerns. 

Portfolio transition trades are unlikely to be based on short-lived private information about specific stocks because decisions to undertake portfolio transitions and their timing likely result from regularly scheduled meetings of investment committees and boards of plan sponsors, not from fast-breaking private information in the hands of fund managers. Transactions cost estimates are therefore unlikely to be biased upward as a result of short-lived private information being incorporated into prices while orders are being executed. 

These properties of portfolio transitions are not often shared by other data. Consider a dataset built up from trades by a mutual fund, a hedge fund, or a proprietary trading desk at an investment bank. In such samples, the intentions of traders may not be recorded in the dataset. For example, a dataset might time stamp a record of a trader placing an order to buy 100,000 shares of stock but not time stamp a record of the trader’s actual intention to buy another 200,000 shares after the first 100,000 shares are bought. Furthermore, trading intentions may not coincide with realized trades because the trader changes his mind as market conditions change. Indeed, traders often condition their trading strategies on prices by using limit orders or canceling orders, thus hard-wiring into their strategies a selection bias problem for using such data to estimate transactions costs. The dependence of actually traded quantities on prices usually makes it impossible to use implementation shortfall in a meaningful way to estimate market depth and bid-ask spreads from data on trades only. Portfolio transitions data are particularly well suited for using implementation shortfall to measure transactions costs because portfolio transitions data avoid these sources of statistical bias. 

The Empirical Hypotheses of Invariance and a Power Function Specification for Transaction Costs. For each unsigned transition order $X _ { i } ,$ let $\mathbb { I } _ { B S , i }$ denote a buy-sell indicator variable which is +1 for buy orders and −1 for sell orders. For transition order i, let $C _ { i }$ denote the expected transactions cost as a fraction of the value transacted. Let $S _ { i }$ denote the implementation shortfall, defined by $S _ { i } = \mathbb { I } _ { B S , i } \cdot ( P _ { e x , i } - P _ { 0 , i } ) / P _ { 0 , i }$ , where $P _ { e x , i }$ is the average execution price of order i and $P _ { 0 , i }$ is its benchmark price. Implementation shortfall is positive when orders are unusually costly and negative when orders are unusually cheap. 

Invariance imposes the restriction that the unobserved transactions cost $C _ { i }$ has the form given in equation (10): 

$$
C _ {i} = \bar {\sigma} _ {i} \cdot \bar {W} _ {i} ^ {- 1 / 3} \cdot \Big (\iota^ {2} \cdot \bar {C} _ {B} \cdot f \Big (\frac {\bar {W} _ {i} ^ {2 / 3}}{\iota} \cdot \frac {\mathbb {I} _ {B S , i} \cdot X _ {i}}{\bar {V} _ {i}} \Big) \Big).\tag{58}
$$

Under the stronger hypothesis that the cost function has a power specification for market impact costs, invariance implies the generalization of equations (12) and (13) 

$$
C _ {i} = \bar {\sigma} _ {i} \cdot \bar {W} _ {i} ^ {- 1 / 3} \cdot \left(\kappa_ {0} + \kappa_ {I} \cdot \left(\bar {W} _ {i} ^ {2 / 3} \cdot \frac {X _ {i}}{\bar {V} _ {i}}\right) ^ {z}\right),\tag{59}
$$

where $z = 1$ for the linear specification and $z = 1 / 2$ for the square root specification. Next, we test whether the cost functions can be in fact represented as the product of $\bar { \sigma } _ { i } \cdot \bar { W } _ { i } ^ { - 1 / 3 }$ and an invariant function of $\bar { W } _ { i } ^ { 2 / 3 } \cdot [ X _ { i } / \bar { V } _ { i } ]$ 

The predictions invariance makes about transactions costs can be expressed in terms of a non-linear regression. To justify nonlinear regression estimation, we can think of implementation shortfall as representing the sum of two components: (1) the transactions costs incurred as a result of order execution and (2) the efect of other random price changes between the time the benchmark price is set and the time the trades are executed. If we make the identifying assumption that the implementation shortfall from the portfolio transition dataset is an unbiased estimate of the transactions cost, we can think of modeling the other random price changes as an error in a regression of implementation shortfall on transactions costs. 

For example, suppose that while one portfolio transition order is being executed, there are 99 other bets being executed at the same time. The temporary and permanent price impact of executing the portfolio transition order shows up as a transactions cost, while the temporary and permanent price impact of the other 99 unobserved bets being executed shows up as other random price changes. Since the portfolio transition order is one of 100 bets being simultaneously executed, the $R ^ { 2 }$ of the regression is likely to be about 0.01. 

To further develop a non-linear regression framework for testing invariance, we need to make several adjustments. 

First, using equation (1) and equation (2), we replace the “bar” variables $\bar { \sigma } , \bar { V } ,$ and W<sup>¯</sup> with observable variables σ, V, and W and with potentially unobservable constants. We also incorporate the assumption that portfolio transition orders are proportional to bets. 

Second, since we want the error in our regression of implementation shortfall on transaction costs be positive when the stock price is moving up and negative when the stock price is moving down, we multiply both the implementation shortfall $S _ { i }$ and the transactions cost function $C ( X _ { i } )$ by the buy-sell indicator. The regression specification can be then written $\mathbb { I } _ { B S , i } \cdot S _ { i } = \mathbb { I } _ { B S , i } \cdot C _ { i } + \tilde { \epsilon } _ { i }$ . Note that $\mathbb { I } _ { B S , i } \cdot S _ { i } =$ $( P _ { e x , i } - P _ { 0 , i } ) / P _ { 0 , i }$ since $\mathbb { I } _ { B S , i } ^ { 2 } = 1$ . This gives us a non-linear regression of the form 

$$
\mathbb {I} _ {B S, i} \cdot S _ {i} = \mathbb {I} _ {B S, i} \cdot \left[ \frac {\psi}{\psi^ {*}} \right] ^ {2 / 3} \left[ \frac {\zeta}{\zeta^ {*}} \right] ^ {1 / 3} \left[ \frac {\sigma_ {i}}{\sigma^ {*}} \right] \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {- 1 / 3} \cdot f (I _ {i} \cdot \delta^ {- 1}) / L ^ {*} + \tilde {\epsilon} _ {i},\tag{60}
$$

where $I _ { i } : = \phi ^ { - 1 } \cdot ( W _ { i } / W ^ { * } ) ^ { 2 / 3 } \cdot X _ { i } / V _ { i }$ , with invariant constant $\phi$ obtained from equation (6) and illiquidity measure for the benchmark stock $1 / L ^ { * } : = \iota ^ { 2 } \cdot \bar { C } _ { B } \cdot \bar { \sigma } ^ { * } \cdot [ \bar { W } ^ { * } ] ^ { \bar { - } 1 / 3 }$ obtained from equation $( 8 ) . ^ { 1 5 }$ Note that $f ( I _ { i } \cdot \delta ^ { - 1 } ) / L ^ { * }$ denotes the invariant cost function for the benchmark stock, expressed as a fraction of notional value, similar to equation (9). 

Third, since $W _ { i } , X _ { i }$ , and V<sub>i</sub> are observable, the quantity $\phi \cdot I _ { i }$ is observable. The quantity $I _ { i }$ itself in equation (60), however, is not observable because the constant ϕ is defined in terms of potentially unobservable constants $\iota , \delta , \psi$ , and $\zeta .$ To estimate the nonlinear regression equation (60), we substitute for $f ( . )$ a diferent function $f ^ { * } ( . )$ defined by $\bar { f } ^ { * } ( x ) = ( \bar { \psi } / \psi ^ { * } ) ^ { 2 / 3 } \cdot ( \zeta / \zeta ^ { * } ) ^ { 1 / 3 } \cdot f ( \phi ^ { - 1 } \delta ^ { - 1 } x )$ . Using $x = \phi \cdot I _ { i }$ , the right side of equation (60) becomes a simpler expression in terms of observable data, with various potentially unobserved constants incorporated into the definition of $f ^ { * }$ , whose functional form is to be estimated from the data. Under the identifying assumptions $\psi = \psi ^ { * }$ and $\zeta = \zeta ^ { * }$ , we have $f ^ { * } ( \phi I _ { i } ) = f ( I _ { i } \cdot \delta ^ { - 1 } )$ , where $\phi \cdot I _ { i } : = ( W _ { i } / W ^ { * } ) ^ { 2 / 3 } \cdot X _ { i } / V _ { i }$ is observable. The unobserved constants hidden in ϕ afect the economic interpretation of the scaling of the estimated functional form for $f ^ { * } ( . )$ , but they do not otherwise afect the estimation itself. 

Fourth, the variance of errors in the regression is likely to be proportional in size to the variance of returns and the execution horizon. On average, portfolio transition orders tend to be executed in about one day. To correct for heteroscedasticity resulting from diferences in return volatility, we divide both the right and left sides by return volatility $\sigma _ { i } / { \sigma ^ { * } }$ , where $\sigma ^ { * } = 0 . 0 2$ . Indeed, this adjustment makes the root mean squared error of the resulting regression approximately equal to 0.02. 

Fifth, to control for the economically and statistically significant influence that general market movements have on implementation shortfall, we add the CRSP valueweighted market return $R _ { m k t , i }$ on the first day of the transition to the right side of the regression equation. To the extent that portfolio transition orders are suficiently large to move the entire U.S. stock market, this adjustment will result in understated transactions costs by measuring only the idiosyncratic component of transactions costs. It is an interesting subject for future research to investigate how large trades in multiple stocks afect general market movements. 

Upon making these two changes and using the definition of $f ^ { * } ( . )$ , regression equation (60) becomes 

$$
\mathbb {I} _ {B S, i} \cdot S _ {i} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} = \beta_ {m k t} \cdot R _ {m k t, i} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} + \mathbb {I} _ {B S, i} \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {\alpha} \cdot f ^ {*} (\phi I _ {i}) / L ^ {*} + \tilde {\epsilon} _ {i}.\tag{61}
$$

where invariance implies $\alpha = - 1 / 3$ . One of our tests is designed to examine this prediction. 

Scaling by $W ^ { * }$ makes the function $f ^ { * } ( \phi I _ { i } ) / L ^ { * }$ in equation (61) measure the transactions cost for the benchmark stock in terms of the observable value $\phi I _ { i }$ . Although invariance itself does not specify a function form for $f ^ { * } ( . ) / L ^ { * }$ , the regression places strong cross-sectional restrictions on the shape of the transactions cost function. In addition to the restriction $\alpha = - 1 / 3$ , it requires that the same function $f ^ { * } ( \phi I _ { i } ) / L ^ { * }$ with $\phi I _ { i } = ( W _ { i } / W ^ { * } ) ^ { 2 / 3 } { \cdot } X _ { i } / V _ { i }$ for order i be used for all stocks. We test this prediction as well. 

We do not undertake separate estimates of transactions cost parameters for internal crosses, external crosses, and open market transactions. Such estimates would be dificult to interpret due to selection bias resulting from transition managers optimally choosing trading venues to minimize costs. 

To adjust standard errors for positive contemporaneous correlation in returns, the observations are pooled by week over the 2001-2005 period into 4,389 clusters across 17 industry categories using the pooling option on Stata. 

Dummy Variable Regression. In our first test, we fix $\alpha = - 1 / 3$ in transaction costs regression equation (61), estimate function $f ^ { * } ( . ) / L ^ { * }$ using dummy variables, and examine calibrated functions across ten volume groups. Invariance predicts those functions to be similar. The test does not put restrictions on the specific functional forms of $f ^ { * } ( . )$ 

We sort all 439, 765 orders into 100 order size bins of equal size based on the value of the “invariant” order size $\phi \cdot I _ { i } = [ W _ { i } / W ^ { * } ] ^ { 2 / 3 } \cdot [ X _ { i } / V _ { i } ]$ . As before, we also place each order into one of ten volume groups based on average dollar trading volume in the underlying stock $P _ { i } V _ { i }$ , with thresholds corresponding to the 30th, 50th, 60th, 70th, 75th, 80th, 85th, 90th, and 95th percentiles of NYSE dollar volume. As shown in section $5 { \mathrm { , } }$ , the distribution of $\phi I _ { i }$ is approximately invariant across volume groups; specifically, across all volume groups $k = 1 , \ldots , 1 0$ , each bin h has a similar number of observations and similar magnitudes for $\phi I _ { i }$ 

In the regression equation (61), we replace the function $f ^ { * } ( \phi I _ { i } ) / L ^ { * }$ with 1, 000 dummy variables $D _ { i } ^ { * } ( k , h ) , k = 1 , \ldots , 1 0$ and $h = 1 , \ldots , 1 0 0$ , where $D _ { i } ^ { * } ( k , h ) = 1$ if bet i belongs to volume group k based on dollar volume $P _ { i } V _ { i }$ and to order size bin h based on $\phi I _ { i } ;$ otherwise $D _ { i } ^ { * } ( k , h ) = 0$ . We then estimate 1, 000 coeficients $f ^ { * } ( k , h ) / L ^ { * } , k = 1 , \dots , 1 0 , h = 1 , \dots .$ , 100 for the dummy variables using a separate OLS regression for each of the volume groups, $k = 1 , \ldots , 1 0$ 

$$
\mathbb {I} _ {B S, i} \cdot S _ {i} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} = \beta_ {m k t} \cdot R _ {m k t} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} + \mathbb {I} _ {B S, i} \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {- 1 / 3} \cdot \sum_ {h = 1} ^ {1 0 0} D _ {i} ^ {*} (k, h) \cdot f ^ {*} (k, h) / L ^ {*} + \tilde {\epsilon} _ {i}.\tag{62}
$$

For each volume group $k ,$ the 100 dummy variable coeficients $f ^ { * } ( k , h ) / L ^ { * }$ (where $h = 1 , \ldots , 1 0 0 )$ track the shape of function $f ^ { * } ( . ) / L ^ { * }$ , without imposing any particular restrictions on its functional form. Invariance predicts that the ten values of the coeficients $f ^ { * } ( k , h ) / L ^ { * } , k = 1 , \dots , 1 0$ should be the same for each order size bin $h ,$ $h = 1 , \ldots , 1 0 0$ . In other words, $f ^ { * } ( k , h ) / L ^ { * }$ is predicted not to depend on volumegroup index k. 

Figure 5 shows ten plots, one for each of the ten volume groups, with the 100 estimated coeficients for the dummy variables plotted as solid dots in each plot. On each plot, we also superimpose the 95% confidence intervals for 100 dummy variable coeficients estimated based on the pooled sample (dotted lines). The superimposed confidence bands help to assess the degree of similarity between cost functions estimated separately based on observations in each volume bin. 

On each of the ten plots, the horizontal and vertical axes are scaled in the same way to facilitate comparison. On the horizontal axis, we plot the value for ordersize bin h equal to the log of the average $\phi I _ { i }$ for observations in that size bin and corresponding volume group k. 

On the right vertical axis, we plot the values of the dummy variable coeficients $f ^ { * } ( k , h ) / L ^ { * }$ quantifying for the benchmark stock the cost function as a fraction of notional value, scaled in basis points. To make deviations of cost patterns from invariants visually obvious, we have efectively scaled cost functions as suggested by invariance using regression (62): We multiply orders sizes $X _ { i } / V _ { i }$ by $( W _ { i } / W ^ { * } ) ^ { 2 / 3 }$ and divide implementation shortfalls $S _ { i }$ by $L ^ { * } / L = ( \sigma _ { i } / \sigma ^ { * } ) \cdot ( W _ { i } / W ^ { * } ) ^ { - 1 / 3 }$ . Here $1 / L ^ { * } : = \iota ^ { 2 } \cdot \bar { C } _ { B } \cdot \bar { \sigma } ^ { * } \cdot [ \bar { W } ^ { * } ] ^ { - 1 / 3 }$ is the illiquidity measure for the benchmark stock from equation (60). The invariance hypothesis implies that the 100 points plotted for each of the 10 volume groups will describe the same underlying cost function when the vertical axis is scaled according to invariance. 

On the left vertical axis, we plot actual average transactions cost $f ^ { * } ( k , h ) / L ^ { k }$ as a fraction of notional value, scaled in basis points. For each volume group k, this scaling reverses invariance-based scaling by multiplying estimated coeficients $f ^ { * } ( k , h ) / L ^ { * }$ by $L ^ { * } / L ^ { k }$ , where $1 / L ^ { k }$ is the illiquidity measure for orders in volume group k given by $1 / \dot { L } ^ { k } : = \iota ^ { 2 } \cdot \bar { C } _ { B } \cdot \bar { \sigma } _ { m e d } ^ { k } \cdot ( \bar { W } ^ { k } { } _ { m e d } \bar { ) } ^ { - 1 / 3 }$ , with $\bar { \sigma } _ { m e d } ^ { k }$ denoting median betting volatility and $\hat { W } _ { m e d } ^ { k }$ denoting median betting activity for volume group k. 

Without appropriate scaling, the data do not reveal their invariant properties. The actual costs on the left vertical axes vary significantly across volume groups. In the low volume group, costs range from −220 basis points to 366 basis points; in the high volume group, costs range from −33 basis point to 55 basis points, 7 times less than in the low volume group. 

After applying “invariance” scaling, however, our plots appear to be visually consistent with the invariance hypothesis. For all ten subplots in figure 5, the estimated dummy variable coeficients on the right vertical axes are very similar across volume groups. They also line up along the superimposed confidence band. 

Moving from low-volume groups to high-volume groups, these estimates also become visually more noisy. For low-volume group 1, dummy variable estimates lie within the confidence band, very tightly pining down the estimated shape for the function $f ^ { * } ( . ) / L ^ { * }$ . For high-volume group 10, many dummy variable estimates lie outside of the confidence band, with 11 observations above the band and about 40 observations below the band. These patterns suggest that the statistical power of our tests concerning transactions costs comes mostly from low-volume groups. 

Invariance suggests that orders might be executed over horizons inversely proportional to the speed of business time, implying very slow executions for large orders in stocks with low trading activity. Portfolio transitions are, however, usually implemented within a clearly defined tight calendar time frame, which has the efect of speeding up the “natural” execution horizon for stocks with low trading activity. When transition orders are executed over a fixed number of calendar days, the execution in business time is efectively faster for low-volume stocks and slower for high volume stocks. When a transition order in a low-volume stock is being executed, there are therefore probably fewer other bets being executed at the same time; this makes the $R ^ { 2 }$ of the regression higher. Over the same period of calendar time, more bets are being executed for the high-volume stocks, making the $R ^ { 2 }$ lower than for low-volume stocks. The more patient business-time pace of execution for high-volume stocks may explain why the dummy variable estimates are noisier for high-volume stocks than for low-volume stocks. This may also explain why the execution costs of high volume stocks appear to be slightly less expensive than low-volume stocks. 

Transactions Cost Estimates in Non-Linear Regression. Next, we test the hypothesis $\alpha = - 1 / 3$ in transaction cost regression equation (61) while simultaneously calibrating a specific functional form for the cost function $f ^ { * } ( . ) / L ^ { * }$ . We assume that this function has a particular parametric functional form equal to the sum of a constant bid-ask spread term and a market impact term which is a power of $\phi \cdot I ,$ similar to equation (59). For this particular specification, the non-linear regression (61) can be written as 

$$
\mathbb {I} _ {B S, i} \cdot S _ {i} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} = \beta_ {m k t} \cdot R _ {m k t} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} + \mathbb {I} _ {B S, i} \cdot \kappa_ {0} ^ {*} \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {\alpha_ {1}} + \mathbb {I} _ {B S, i} \cdot \kappa_ {I} ^ {*} \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {\alpha_ {2}} \cdot \left[ \frac {\phi I _ {i}}{0 . 0 1} \right] ^ {z} + \tilde {\epsilon} _ {i},\tag{63}
$$

where $\phi I _ { i } / 0 . 0 1 = [ W _ { i } / W ^ { * } ] ^ { 2 / 3 } \cdot X _ { i } / [ 0 . 0 1 V _ { i } ]$ . The explanatory variables are scaled so that, for the benchmark stock, execution of one percent of daily volume has price impact cost of $\kappa _ { I } ^ { * }$ and fixed bid-ask spread of $\kappa _ { 0 } ^ { * } .$ both measured as a fraction of the value traded (with units of $1 0 ^ { - 4 }$ equivalent to basis points). Equation (63) nests for empirical testing both the linear model of equation (12) $( z = 1 )$ and the square root model of equation (13) $( z = 1 / 2 )$ 

First, we report estimates of the six parameters $( \beta _ { m k t } , \ z , \ \alpha _ { 1 } , \ \kappa _ { 0 } ^ { * } , \ \alpha _ { 2 }$ , and $\kappa _ { I } ^ { * } )$ in equation (63) using non-linear regression. Second, we calibrate the three-parameter linear impact model of equation (12) with parameters $( \beta _ { m k t } , ~ \kappa _ { 0 } ^ { * } , ~ \kappa _ { I } ^ { * } )$ by imposing the additional invariance restrictions $\alpha _ { 1 } = \alpha _ { 2 } = - 1 / 3$ and the linear cost restriction $z = 1$ . Third, we also calibrate the three-parameter square root model of equation (13) with parameters $( \beta _ { m k t } , \kappa _ { 0 } ^ { * } , \kappa _ { I } ^ { * } )$ by imposing the alternate restriction $z = 1 / 2$ . Finally, we examine a twelve-parameter generalization of equation (63) which replaces powers $\alpha _ { 1 }$ and $\alpha _ { 2 }$ of trading activity $W$ with powers of volatility σ, price $P _ { \mathrm { : } }$ volume $V$ , and turnover $\eta .$ . Although statistical tests reject invariance, the results indicate that the predictions of invariance are economically significant, with the square root version of invariance explaining transactions costs better than the linear version. 

The parameter estimates for the six parameters $\beta _ { m k t } , \ \kappa _ { 0 } ^ { * } , \ z , \ \alpha _ { 1 } , \ \kappa _ { I } ^ { * } , \ \alpha _ { 2 }$ in the non-linear regression (63) are reported in table 4. 

For the coeficient $\beta _ { m k t }$ , which multiplies the market return $R _ { m k t }$ , the estimate is $\hat { \beta } _ { m k t } = 0 . 6 5$ with standard error 0.013. The fact that $\hat { \beta } _ { m k t } < 1$ suggests that many transition orders are executed early on the first day.<sup>16</sup> 

The point estimate of the estimated bid-ask spread exponent is $\hat { \alpha } _ { 1 } = - 0 . 4 9$ , with standard error 0.050, three standard errors lower than the predicted value $\alpha _ { 1 } = - 1 / 3$ In comparison with invariance, this result implies higher spread costs for less actively traded stocks and lower spread costs for more actively traded stocks. Note, however, that the factor involving $\alpha _ { 1 }$ is multiplied by $2 \cdot \kappa _ { 0 } ^ { * }$ , and $\kappa _ { 0 } ^ { \ast }$ is only of marginal statistical significance since it difers from zero by about two standard errors; excluding the bidask spread component of prices reduces the $R ^ { 2 }$ from 0.1010 to 0.1006 (not reported in table). This result may have something to do with the minimum tick size of one cent being a binding constraint for some securities. 

The point estimate for $\alpha _ { 2 }$ is $\hat { \alpha } _ { 2 } = - 0 . 3 2$ with standard error 0.015. Since invariance implies $\alpha _ { 2 } = - 1 / 3$ , this result strongly supports invariance. When the four parameters are estimated separately for NYSE Buys, NYSE Sells, NASDAQ Buys, and NASDAQ Sells, the estimated coeficients for $\alpha _ { 2 }$ are $- 0 . 4 0 , \ : - 0 . 3 3 , \ : - 0 . 4 1$ , and −0.29, respectively. 

The estimate for the market impact curvature parameter $z$ is $\hat { z } ~ = ~ 0 . 5 7$ with standard error 0.039. This suggests that a square root specification $( z = 1 / 2 )$ may describe observed transactions costs better than a linear specification $( z = 1 )$ . Note that invariance does not place any restrictions on the parameter z itself. 

The point estimate of the market impact coeficient $\kappa _ { I } ^ { * }$ is $\hat { \kappa } _ { I } ^ { * } = 1 0 . 6 9 \cdot 1 0 ^ { - 4 }$ with standard error $1 . 3 7 6 \cdot 1 0 ^ { - 4 }$ . The estimates of $\kappa _ { I } ^ { * }$ are higher for buy orders than for sell orders $\left( 1 2 . 0 8 \cdot 1 0 ^ { - 4 } \right.$ versus $9 . 5 6 \cdot 1 0 ^ { - 4 }$ for NYSE; $1 2 . 3 3 \cdot 1 0 ^ { - 4 }$ versus $9 . 3 4 \cdot 1 0 ^ { - 4 }$ for NASDAQ). 

Note that the point estimate of the market impact coeficient $\kappa _ { I } ^ { * }$ is diferent from zero with much greater statistical significance than the bid-ask spread coeficient $\kappa _ { 0 } ^ { * } ;$ this is consistent with the interpretation that market impact costs are of considerably greater economic importance than bid-ask spread costs. 

Results for the five-parameter linear specification, regression equation (63) with the parameter restriction $z = 1$ (linear impact), are reported in table 9 in the $\mathrm { A p \mathrm { - } }$ pendix. The estimate of the bid-ask spread cost $\kappa _ { 0 } ^ { \ast }$ is $6 . 2 8 \cdot 1 0 ^ { - 4 }$ with standard error $0 . 8 9 0 \cdot 1 0 ^ { - 4 }$ , and the estimate of the exponent $\alpha _ { 1 }$ is $\hat { \alpha } _ { 1 } = - 0 . 3 9$ with standard error 0.020. The estimate of the market impact cost $\kappa _ { I } ^ { * }$ is $2 . 7 3 \cdot 1 0 ^ { - 4 }$ with standard error 0.252. The estimate of the exponent $\alpha _ { 2 }$ is $\hat { \alpha } _ { 2 } = - 0 . 3 1$ with standard error of 0.028; thus, under the restriction of linear price impact $( z = 1 )$ , the additional restriction imposed by invariance $( \alpha _ { 2 } = 1 / 3 )$ is not statistically rejected. 

Model Calibration. Next, we calibrate transaction cost models, under the assumption of invariance and the assumption of either linear or square root specification for the cost function. 

Table 5 presents estimates for the three parameters $\beta _ { m k t } , ~ \kappa _ { 0 } ^ { * }$ , and $\kappa _ { I } ^ { * }$ in equation (63), imposing the invariance restrictions $\alpha _ { 1 } = \alpha _ { 2 } = - 1 / 3$ and also imposing either a linear transactions cost model $z = 1$ or a square root model $z = 1 / 2$ 

In the linear specification with $z = 1$ , the point estimate for market impact cost $\hat { \kappa } _ { I } ^ { * }$ is equal to $2 . 5 0 \cdot 1 0 ^ { - 4 }$ , and the point estimate for bid-ask spread cost $\hat { \kappa } _ { 0 } ^ { * }$ is equal $8 . 2 1 \cdot 1 0 ^ { - 4 }$ 

In the square root specification with $z = 1 / 2$ , the point estimate for market impact cost $\hat { \kappa } _ { I } ^ { * }$ is equal to $1 2 . 0 8 \cdot 1 0 ^ { - 4 }$ , and the point estimate for half bid-ask spread $\hat { \kappa } _ { 0 } ^ { * }$ is equal to $2 . 0 8 \cdot 1 0 ^ { - 4 }$ 

For the benchmark stock, these estimates imply that the total cost of a hypothetical trade of one percent of daily volume incurs a cost of about 10.71 basis points in the linear model and 14.16 basis points in the square root model. 

The benchmark stock would belong to volume group 7, and the corresponding average quoted spread in table 1 for that group is 12.04 basis points. The implied spread estimate of about 16.42 basis points for the linear model is close to the quoted spread; the implied spread estimate of 4.16 basis points for the square root model may be biased downwards due to collinearity between the constant term and and the square root term in the regression in the region close to zero. 

Economic Interpretation. We examine the economic significance of our results by comparing the $R ^ { 2 }$ of diferent specifications for transaction costs models. 

The $R ^ { 2 }$ is equal to 0.0847 in the transaction cost regressions with market return only (not reported). This implies that a substantial part of realized transaction costs is explained by overall market dynamics. The transaction costs models improve the $R ^ { 2 } \mathrm { s }$ by only one or two percent. 

A comparison of the $R ^ { 2 } \mathrm { s }$ in table 4 and table 5 provides strong support for the invariance hypothesis. When the coeficient on $W / W _ { * }$ is fixed at the invariance-implied value of $- 1 / 3$ and only two transactions cost parameters $\kappa _ { I } ^ { * }$ and $\kappa _ { 0 } ^ { \ast }$ are estimated (table 5), the $R ^ { 2 }$ is 0.0991 for a linear specification and 0.1007 for a square root specification. The square root specification performs better than the linear specification. Compared with the square root specification, adding the three additional parameters $\alpha _ { 1 } , \alpha _ { 2 }$ and z modestly increases the $R ^ { 2 }$ from 0.1007 to 0.1010 (table 5). The modest increase strongly supports the economic importance of invariance. 

We also consider a more general specification with eleven estimated coeficients. The exponents on the three components of trading activity $W _ { i }$ (volatility $\sigma _ { i }$ , price $P _ { 0 , i } .$ , volume $V _ { i } )$ as well as the exponent on the monthly turnover $\nu _ { i }$ are allowed to vary freely. The estimated regression equation is 

$$
\begin{array}{l} \mathbb {I} _ {B S, i} \cdot S _ {i} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} = \beta_ {m k t} \cdot R _ {m k t} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} \mathbb {I} _ {B S, i} \cdot \kappa_ {0} ^ {*} \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {- 1 / 3} \cdot \frac {\sigma_ {i} ^ {\beta_ {1}} \cdot P _ {0 , i} ^ {\beta_ {2}} \cdot V _ {i} ^ {\beta_ {3}} \cdot \nu_ {i} ^ {\beta_ {4}}}{(0 . 0 2) (4 0) (1 0 ^ {6}) (1 / 1 2)} + \\ + \mathbb {I} _ {B S, i} \cdot \kappa_ {I} ^ {*} \cdot \left[ \frac {\phi I _ {i}}{0 . 0 1} \right] ^ {z} \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {- 1 / 3} \cdot \frac {\sigma_ {i} ^ {\beta_ {5}} \cdot P _ {0 , i} ^ {\beta_ {6}} \cdot V _ {i} ^ {\beta_ {7}} \cdot \nu_ {i} ^ {\beta_ {8}}}{(0 . 0 2) (4 0) (1 0 ^ {6}) (1 / 1 2)} + \tilde {\epsilon} _ {i}. \end{array} \tag {64}
$$

Because the exponents on the W-terms are set to be $- 1 / 3$ , the invariance hypothesis predicts $\beta _ { 1 } = \beta _ { 2 } = \beta _ { 3 } = \beta _ { 4 } = \beta _ { 5 } = \beta _ { 6 } = \beta _ { 7 } = \beta _ { 8 } = 0$ 

Table 5 shows that despite increasing the number of estimated parameters from four to eleven, the $R ^ { 2 }$ in the aggregate regression increases from 0.1010 to only 0.1016. The estimates of $\beta _ { 1 } , ~ \beta _ { 2 } , ~ \beta _ { 3 } , ~ \beta _ { 4 } , ~ \beta _ { 5 } , ~ \beta _ { 6 } , ~ \beta _ { 7 }$ , and $\beta _ { 8 }$ are shown in table 11 in the Appendix. The estimates of $\beta _ { 1 } , ~ \beta _ { 2 } , ~ \beta _ { 3 } , ~ \beta _ { 4 }$ are often statistically significant, but these explanatory variables are multiplied by statistically insignificant coeficient $\kappa _ { 0 } ^ { \ast }$ Almost all estimates of $\beta _ { 5 } , \beta _ { 6 } , \beta _ { 7 }$ , and $\beta _ { 8 }$ are statistically insignificant, both for the pooled sample as well as the four sub-samples. 

In all three specifications, separate regressions for NYSE Buys, NYSE Sells, NAS-DAQ Buys, and NASDAQ Sells suggest that price impact costs are higher for buy orders than for sell orders. This is consistent with the hypothesis, discussed Obizhaeva (2009), that the market believes that buy orders—in particular, buy orders in portfolio transitions—contain more information than sell orders. 

OLS Estimates for Quoted Spread. Finally, we present results of statistical tests based on the data on quoted bid-ask spread for portfolio transition orders. 

Since invariance implies that bid-ask spread costs are proportional to $\bar { \boldsymbol { \sigma } } \cdot \bar { \boldsymbol { W } } ^ { - 1 / 3 }$ intuition suggests that quoted spreads may also have this invariant property. As a supplement to our empirical results on transactions costs, we test this prediction using data on quoted spreads, supplied in the portfolio transition data as pre-trade information for each transition order. 

Let $s _ { i }$ denote the dollar quoted spread for order i. Applying equation (12) or (13) to quoted spreads, we obtain 

$$
s _ {i} / P _ {i} \propto \bar {\sigma} _ {i} \cdot \bar {W} _ {i} ^ {- 1 / 3}.\tag{65}
$$

Using equation (1) and equation (2), we can write the log-linear OLS regression 

$$
\ln \left[ \frac {s _ {i}}{P _ {i} \cdot \sigma_ {i}} \right] = \ln \bar {s} + \alpha_ {3} \cdot \ln \left[ \frac {W _ {i}}{W ^ {*}} \right] + \tilde {\epsilon} _ {i},\tag{66}
$$

where invariance implies $\alpha _ { 3 } = - 1 / 3$ . The constant term ln $\bar { s } : = \ln [ s ^ { * } / ( 4 0 \cdot 0 . 0 2 ) ] +$ $2 / 3 \ln ( \psi / \psi ^ { * } ) - 1 / 3 \ln ( \zeta ^ { * } / \zeta )$ quantifies the dollar spread $s ^ { * }$ for the benchmark stock as a fraction of dollar volatility $P ^ { * } \cdot \sigma ^ { * }$ , under the identifying assumptions $\zeta = \zeta ^ { * }$ and $\psi = \psi ^ { * }$ 

Table 6 presents the regression results. The point estimate $\hat { \alpha } _ { 3 } = - 0 . 3 5$ has standard error 0.003. For sub-samples of NYSE Buys, NYSE Sells, NASDAQ Buys, and NASDAQ Sells, the estimates are $- 0 . 3 1 , \ : - 0 . 3 2 , \ : - 0 . 4 0$ , and −0.39, respectively. Although the hypothesis $\alpha _ { 3 } = - 1 / 3$ is usually rejected statistically, the estimates are economically close to the value of $- 1 / 3$ predicted by invariance. The point estimate of ln ¯s is equal to −3.07, implying a quoted spread of $\exp ( - 3 . 0 7 ) \cdot 0 . 0 2 \approx 9 \cdot 1 0 ^ { - 4 }$ for the benchmark stock. This number is similar to the median spread of 8.12 basis points for volume group 7 in table 1. 

It can be shown that an implicit spread proportional to $\bar { \sigma } \cdot \bar { W } ^ { - 1 / 3 }$ , as implied by invariance, provides a better proxy for the actually incurred spread costs than the quoted spread itself. When regression equation (63) is estimated with linear impact $z = 1$ , using only the 436,649 observations for which quoted bid-ask spread data is supplied, we find the $R ^ { 2 }$ is equal to 0.0992. Now replace the invariance-implied spread cost proportional to $\bar { \sigma } \cdot \bar { W } ^ { - 1 / 3 }$ with the quoted half spread $1 / 2 \cdot s _ { i } / P _ { i }$ in equation (12). The estimated equation is 

$$
\mathbb {I} _ {B S, i} \cdot S _ {i} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} = \beta_ {m k t} \cdot R _ {m k t} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} + \mathbb {I} _ {B S, i} \cdot h \cdot \frac {1}{2} \cdot \frac {s _ {i}}{P _ {0 , i}} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} + \mathbb {I} _ {B S, i} \cdot \kappa_ {I} \cdot \left[ \frac {\phi I _ {i}}{0 . 0 1} \right] \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {\alpha_ {2}} + \tilde {\epsilon} _ {i}.\tag{67}
$$

We find that the $R ^ { 2 }$ drops from 0.0992 to 0.0976 (table 10 in the Appendix). The point estimate of the coeficient on the quoted half-spread coeficient is $\ddot { h } = 0 . 7 1$ . The estimates are equal to 0.61, 0.74, 0.61, and 0.75, when estimated for NYSE Buys, NYSE Sells, NASDAQ Buys, and NASDAQ Sells, respectively. 

One interpretation of the estimate of 0.71 is that transition managers incur as a transactions cost only 71% of the quoted half-spread. The values are consistent with the intuition in Goettler, Parlour and Rajan (2005) that endogenously optimizing traders capture a fraction of the bid-ask spread by mixing between market orders and limit orders. Another interpretation is that noise in the quoted spread relative to the “true” spread biases the coeficient towards zero and reduces the explanatory power of the regression. 

Bouchaud, Farmer and Lillo (2009) and Dufour and Engle (2000) report that the quoted bid-ask spread is proportional to the standard deviation of percentage returns between trades; this result is implied by microstructure invariance under the assumption that the rate at which trades occur is proportional to the rate at which bets arrive. Stoll (1978a) proposes a theory that the percentage dealer bid-ask spread in NASDAQ stocks is proportional to variables including the dealer holding period and the returns variance of the stock; this captures the spirit of invariance if the dealer holding period is proportional to the rate at which bets arrive. Stoll (1978b) also tests this theory using data on dealer spreads for NASDAQ stocks, and his estimates are consistent with our findings as well.<sup>17</sup> 

Discussion. Figure 6 plots the estimated coeficients for the 100 dummy variables, along with their 95% confidence intervals, estimated from the dummy variable regression equation (62) by pooling the data across all 10 volume groups. The linear and square root cost functions with parameters calibrated in table 5 are superimposed. The linear specification is $2 . 5 0 \cdot 1 0 ^ { - 4 } \cdot { \phi } I / 0 . 0 1 + 8 . 2 1 \cdot 1 0 ^ { - 4 }$ (solid black line), and the square root specification is $1 2 . 0 7 \cdot 1 0 ^ { - 4 } \cdot \sqrt { \phi I / 0 . 0 1 } + 2 . 0 8 \cdot 1 0 ^ { - 4 }$ (solid grey line). Both specifications result in estimates economically close to each other. 

Consistent with the higher reported $R ^ { 2 }$ for the square root model than the linear model in table 5, the square root specification fits the data slightly better than the linear specification, particularly for large orders in the order size bins from 90th to 99th percentiles. Consistent with our results, most studies find that total price impact is best described by a concave function.<sup>18</sup> For example, Almgren et al. (2005) obtain an estimate $\hat { z } = 0 . 6 0$ for their sample of almost 30, 000 U.S. stock orders executed by Citigroup between 2001 and 2003; this is comparable to our estimate of $\hat { z } = 0 . 5 6$ when the constraint $\alpha _ { 1 } = \alpha _ { 2 } = - 1 / 3$ is imposed in regression equation (63). To diferentiate temporary impact from permanent impact of earlier executed trades, Almgren et al. (2005) assume a particular execution algorithm with a constant rate of trading. We do not quantify these cost components separately but rather focus on total costs. 

Intuition might suggest that for gigantic orders, the square root model would predict dramatically lower transactions costs than the linear model, making it easy to distinguish the predictions of one model from the other. As the superimposed estimated linear and square root cost functions for the ten plots in figure 5 make clear, both specifications estimate similar transactions costs for the bin representing the largest 1% or orders (because the graphs of the linear and square root functions in figure 6 cross near the bin representing the largest $1 \%$ of orders). Furthermore, the transaction cost dummy variable for the largest 1% of orders fits both the linear and square root models well. For the largest 1% of orders in the highest volume group in figure 5, the estimated dummy variable fits the higher cost estimates of the linear model better than the square root model. 

## 7 Implications

The invariance relationships (5), (6), (9), and (14) are like a structural model which describes the implications of market microstructure for bet size, transactions costs, eficiency and resiliency. The model is fully specified by constants describing the moments of $\tilde { I }$ and the shape of the un-modeled function $C _ { B } ( . )$ , which determines the constant $\bar { C } _ { B }$ . These constants can be inferred from the estimates in section 5 and section 6, but their economic interpretation depends on assumptions about the volume multiplier $\zeta ,$ the volatility multiplier $\psi _ { ; }$ , and the deflator δ. 

Our empirical tests provide not only evidence in favor of the invariance hypotheses but also inputs for the calibration process. Our empirical results can be summarized as follows. The distribution of portfolio transition orders $| \tilde { X } |$ |—expressed as a fraction of volume—is approximately a log-normal. It is therefore fully described by two parameters, the log-mean for the benchmark stock estimated to be −5.71 and the log-variance estimated to be 2.53 (table 3). The following formula shows how these estimates can be extrapolated to stocks with other levels of trading activity $W =$ $\sigma \cdot P \cdot V$ and volume $V { : }$ 

$$
\ln \left[ \frac {| \tilde {X} |}{V} \right] \approx - 5. 7 1 - \frac {2}{3} \cdot \ln \left[ \frac {W}{(0 . 0 2) (4 0) (1 0 ^ {6})} \right] + \sqrt {2 . 5 3} \cdot \tilde {Z}, \qquad \tilde {Z} \sim N (0, 1)\tag{68}
$$

both the linear model and the concave square root model show up as exponential functions; the graph of the linear model is more convex than the graph of the square root model. 

$$
\gamma = 8 5 \cdot \left[ \frac {W}{(0 . 0 2) (4 0) (1 0 ^ {6})} \right] ^ {2 / 3}.\tag{69}
$$

The last equation for the number of bets $\gamma$ follows directly from equation (68) under the assumption that the volume multiplier $\zeta = 2$ and the portfolio transition size multiplier $\delta = 1$ . These two equations fully describe the order flow process. 

Our empirical results also suggest that transactions cost functions can be described by either a linear model or a square root model. Since both models also have a constant bid-ask spread term, each model is described by two parameters. For an order of $1 \%$ of average daily volume in the benchmark stock, the estimates imply market impact costs of $\kappa _ { I } = 2 . 5 0 \cdot 1 0 ^ { - 4 }$ and spread costs of $\kappa _ { 0 } = 8 . 2 1 \cdot 1 0 ^ { - 4 }$ for the linear model as well as market impact costs of $\kappa _ { I } = 1 2 . 0 8 \cdot 1 0 ^ { - 4 }$ and spread costs of $\kappa _ { 0 } = 2 . 0 8 \cdot 1 0 ^ { - 4 }$ for the square root model (table 5). The following formulas show how these estimates can be extrapolated to execution costs of an order of X shares for stocks with other levels of trading activity W, volume $V ,$ and volatility σ: 

$$
C (X) = \frac {\sigma}{0 . 0 2} \left(\frac {8 . 2 1}{1 0 ^ {4}} \cdot \left[ \frac {W}{(0 . 0 2) (4 0) (1 0 ^ {6})} \right] ^ {- 1 / 3} + \frac {2 . 5 0}{1 0 ^ {4}} \cdot \left[ \frac {W}{(0 . 0 2) (4 0) (1 0 ^ {6})} \right] ^ {1 / 3} \frac {X}{(0 . 0 1) V}\right).\tag{70}
$$

$$
C (X) = \frac {\sigma}{0 . 0 2} \left(\frac {2 . 0 8}{1 0 ^ {4}} \cdot \left[ \frac {W}{(0 . 0 2) (4 0) (1 0 ^ {6})} \right] ^ {- 1 / 3} + \frac {1 2 . 0 8}{1 0 ^ {4}} \cdot \left[ \frac {X}{(0 . 0 1) V} \right] ^ {1 / 2}\right).\tag{71}
$$

These two equations fully describe the transactions cost models. 

To summarize, formulas (68), (69), (70), and (71) provide a simple way to calculate the number of bets, diferent percentiles of bet sizes, and transactions costs. The only stock-specific inputs required are expected dollar volume and volatility.<sup>19</sup> 

Our results can also be used to calibrate the distribution of $\tilde { I }$ and the invariant cost function $C _ { B } ( \cdot )$ , which further implies specific quantitative relationships concerning various market microstructure variables such as the number of bets per day, bet sizes, spread, liquidity, pricing accuracy, and resiliency as functions of easily observable trading activity and its components. These implications ultimately depend on values assigned to the volatility multiplier ψ, the volume multiplier $\zeta ,$ and the deflator $\delta .$ 

In a more complicated exercise left for future research, this handful of parameters would make it possible to triangulate the value of parameters measuring the fraction of trading volume due to long-term investors rather than intermediaries $1 / \zeta .$ , the fraction of returns volatility generated by bets $\psi .$ , and the ratio of the size of bets to the size of portfolio transition orders δ. In the future, careful thinking about calibration of the invariants and estimation of multipliers will be necessary to sharpen predictions based on invariance principles. 

## 8 Conclusion

We have shown that the predictions based on market microstructure invariance are economically consistent with results estimate from portfolio transitions data for U.S. equities. We conjecture that predictions based on invariance may be found to hold in other data as well, such as spread, quote, and transactions data in the TAQ dataset; levels and changes in holdings recorded in 13-F filings of institutional investment managers; institutional trades reported in the Ancerno dataset; and other datasets. For example, we conjecture that data on news articles can help to show that information flows take place in the same business time as trading. 

We conjecture that predictions of market microstructure invariance may generalize to other markets such as bond markets, currency markets, and futures markets, as well as to other countries. Whether market microstructure invariance applies to other markets poses an interesting set of issues for future research. 

We do not expect invariance to hold perfectly across diferent markets and different times periods. Diferences in trading institutions across markets might make the volume multiplier and the volatility multiplier vary across markets. We expect transactions costs, particularly bid-ask spread costs (but perhaps not market impact costs), to be influenced by numerous institutional features, such as government regulation (e.g., short sale restrictions, customer order handling rules), transactions taxes, competitiveness of market making institutions, eficiency of trading platforms, market fragmentation, technological change, and tick size. For example, if minimum tick size rules afect bid-ask spread costs, we believe that market microstructure invariance can be used as a benchmark against which the efect of tick size on bid-ask spread costs can be evaluated. 

To conclude, market microstructure invariance implies simple scaling laws which lead to sharp statistical hypothesis about bet size and transaction costs; it is consistent with a simple structural model from which specific versions of these scaling laws can be derived in closed form; and its implications explain an economically significant portion of the variation in portfolio transition order size and transaction costs when the scaling laws are imposed on the data. The scaling laws enable us to derive simple operational formulas describing order size distributions and transaction costs; thus, they provide simple benchmarks from which past research can be evaluated and open up new lines of research into market microstructure. 

## References



Aitchison, J., and J. A. C. Brown. 1957. The Lognormal Distribution with Special 





Reference to Its Uses in Economics. Cambridge University Press. 





Allais, Maurice. 1956. “Explication del Cycles Economiques Par Un Modele Non Lin´eaire a R´egulation Retard´ee.” Metroeconomica, 8(1): 4–83. 





Allais, Maurice. 1966. “A Restatement of the Quantity Theory of Money.” American Economic Review, 56(5): 1123–1157. 





Almgren, Robert, Chee Thum, Emmanuel Hauptmann, and Hong Li. 2005. “Direct Estimation of Equity Market Impact.” Risk, 18(7): 58–62. 





Amihud, Yakov. 2002. “Illiquidity and Stock Returns: Cross-Section and Time-Series Efects.” The Journal of Financial Markets, 5: 31–56. 





An´e, Thierry, and Helyette Geman. 2000. “Order Flow, Transaction Clock, and Normality of Asset Returns.” The Journal of Finance, 55(5): 2259–2284. 





Back, Kerry, and Shmuel Baruch. 2004. “Information in Securities Markets: Kyle meets Glosten and Milgrom.” Econometrica, 72: 433–465. 





Barra. 1997. In Market Impact Model Handbook. Berkley, CA: Barra. 





Black, Fischer. 1986. “Noise.” The Journal of Finance, 41: 529–543. 





Bouchaud, Jean-Philippe, Doyne J. Farmer, and Fabrizio Lillo. 2009. “How Markets Slowly Digest Changes in Supply and Demand.” In Handbook of Financial Markets: Dynamics and Evolution. 47–160. North Holland. 





Breen, William, Laurie Simon Hodrick, and Robert A. Korajczyk. 2002. “Predicting Equity Liquidity.” Management Science, 48: 470–83. 





Brennan, Michael, and Avanidhar Subrahmanyam. 1998. “The Determinants of Average Trade Size.” The Journal of Business, 71(1): 1–25. 





Campbell, John Y., and Albert S. Kyle. 1993. “Smart Money, Noise Trading, and Stock Price Behavior.” The Review of Economic Studies, 60: 1–34. 





Clark, Peter. 1973. “A Subordinated Stochastic Process Model with Finite Variance for Speculative Prices.” Econometrica, 41: 135–155. 





Derman, Emanuel. 2002. “The Perception of Time, Risk and Return during Periods of Speculation.” Quantitative Finance, 2: 282–296. 





Dufour, Alfonso, and Robert F. Engle. 2000. “Time and the Price Impact of a Trade.” The Journal of Finance, 55(6): 2467–2598. 





Gabaix, Xavier, Parameswaran Gopikrishnan, Vasiliki Plerou, and Eugene H. Stanley. 2006. “Institutional Investors and Stock Market Volatility.” The Quarterly Journal of Economics, 121: 461–504. 





Glosten, Lawrence R., and Paul R. Milgrom. 1985. “Bid, Ask and Transaction Prices in a Specialist Market with Heterogeneously Informed Traders.” The Journal of Financial Economics, 14: 71–100. 





Goettler, Ronald L., Christine A. Parlour, and Uday Rajan. 2005. “Equilibrium in a Dynamic Limit Order Market.” The Journal ofFinance, 60(5): 2149–2192. 





Gopikrishnan, Parameswaran, Martin Meyer, Luis A. Amaral, and Eugene H. Stanley. 1998. “Inverse Cubic Law for the Distribution of Stock Price Variations.” The European Physical Journal, 3: 139–140. 





Grinold, Richard C., and Ronald N. Kahn. 1995. In Active Portfolio Management. Probus Publishing. 





Grossman, Sanford J., and Joseph E. Stiglitz. 1980. “On the Impossibility of Informationally Eficient Markets.” American Economic Review, 70(3): 393–408. 





Grossman, Sanford J., and Merton H. Miller. 1988. “Liquidity and Market Structure.” The Journal of Finance, 43(3): 617–633. 





Hasbrouck, Joel. 1999. “Trading Fast and Slow: Security Market Events in Real Time.” Working Paper, New York University. 





Hasbrouck, Joel. 2007. Empirical Market Microstructure: The Institutions, Economics, and Econometrics of Securities Trading. Oxford University Press, USA. 





Holden, Craig W, Stacey E Jacobsen, and Avanidhar Subrahmanyam. 2015. “The empirical analysis of liquidity.” Foundations and Trends in Finance, forthcoming. 





Kolmogorov, Andrei N. 1941a. “The Local Structure of Turbulence in Incompressible Viscous Fluids at Very Large Reynolds Numbers.” Doklady Akademii Nauk SSSR, 30: 301–305. Reprinted in Procedings of the Royal Society London A 434, 9-13, 1991. 





Kolmogorov, Andrei N. 1941b. “On The Log-Normal Distribution of Particle Sizes during Break-up Process.” Doklady Akademii Nauk SSSR, 31(2): 99–101. 





Kyle, Albert S. 1985. “Continuous Auctions and Insider Trading.” Econometrica, 53(6): 1315–1335. 





Lee, Charles, and Mark Ready. 1991. “Inferring Trade Direction from Intraday Data.” The Journal of Finance, 46: 733–746. 





Loeb, Thomas. 1983. “Trading Cost: The Critical Link between Investment Information and Results.” Financial Analysts Journal, 39: 39–44. 





Mandelbrot, Benoˆıt, and Howard M. Taylor. 1967. “On the Distribution of Stock Price Diferences.” Operations Research, 15(6): 1057–1062. 





Modigliani, Franco, and Merton H. Miller. 1958. “The Cost of Capital, Corporation Finance and the Theory of Investment.” American Economic Review, 48: 261–297. 





Obizhaeva, Anna. 2009. “Portfolio Transitions and Price Dynamics.” Working Paper, University of Maryland. 





Perold, Andr´e. 1988. “The Implementation Shortfall: Paper vs. Reality.” Journal of Portfolio Management, 14(3): 4–9. 





Plerou, Vasiliki, Parameswaran Gopikrishnan, Luis A. Amaral, Xavier Gabaix, and Eugene H. Stanley. 2000. “Economic Fluctuations and Anomalous Difusion.” Physical Review E, 62: 3023–3026. 





Schwarzkopf, Yonathan, and Doyne J. Farmer. 2010. “Empirical Study of the Tails of Mutual Fund Size.” Physical Review E, 81: 066113. 





Stambough, Robert F., and Lubos Pastor. 2003. “Liquidity Risk and Expected Stock Returns.” Journal of Political Economy, 111: 642–685. 





Stoll, Hans R. 1978a. “The supply of dealer services in securities markets.” The Journal of Finance, 33(4): 1133–1151. 





Stoll, Hans R. 1978b. “The pricing of security dealer services: An empirical study of NASDAQ stocks.” The Journal of Finance, 33(4): 1153–1172. 





Treynor, Jack. 1995. “The Only Game in Town.” The Financial Analysts Journal, 51(1): 81–83 (reprinted from The Financial Analysts Journal 22, 1971, 12–14, 22). 





Wang, Jiang. 1993. “A Model of Intertemporal Asset Prices Under Asymmetric Information.” The Review of Economic Studies, 60(2): 249–282. 




Table1:DescriptiveStatistics.


<table><tr><td colspan="12">panel A: Properties of Securities.</td></tr><tr><td></td><td>All</td><td>1</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td><td>7</td><td>8</td><td>9</td><td>10</td></tr><tr><td><eq>Med(V \cdot P) \times 10^6</eq></td><td>18.72</td><td>1.13</td><td>5.10</td><td>9.92</td><td>15.93</td><td>23.87</td><td>31.41</td><td>42.12</td><td>60.25</td><td>101.60</td><td>212.85</td></tr><tr><td><eq>Med(\sigma) \times 10^2</eq></td><td>1.93</td><td>2.16</td><td>2.04</td><td>1.94</td><td>1.98</td><td>1.90</td><td>1.86</td><td>1.80</td><td>1.78</td><td>1.77</td><td>1.76</td></tr><tr><td><eq>Med(Sprd) \times 10^4</eq></td><td>12.04</td><td>40.96</td><td>18.72</td><td>13.70</td><td>12.02</td><td>10.32</td><td>9.42</td><td>8.12</td><td>7.21</td><td>5.92</td><td>4.83</td></tr><tr><td><eq>Med(Turn) \times 10^2</eq></td><td>12.72</td><td>6.58</td><td>12.36</td><td>14.80</td><td>15.95</td><td>16.80</td><td>16.36</td><td>15.37</td><td>14.41</td><td>14.92</td><td>11.12</td></tr><tr><td colspan="12">panel B: Properties of Portfolio Transitions Orders.</td></tr><tr><td></td><td>All</td><td>1</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td><td>7</td><td>8</td><td>9</td><td>10</td></tr><tr><td><eq>Avg(X/V) \times 10^2</eq></td><td>4.20</td><td>16.23</td><td>4.54</td><td>2.62</td><td>1.83</td><td>1.37</td><td>1.18</td><td>1.08</td><td>0.88</td><td>0.69</td><td>0.49</td></tr><tr><td><eq>Med(X/V) \times 10^2</eq></td><td>0.57</td><td>3.33</td><td>1.36</td><td>0.79</td><td>0.53</td><td>0.40</td><td>0.34</td><td>0.30</td><td>0.25</td><td>0.20</td><td>0.14</td></tr><tr><td><eq>Avg(X/Cap) \times 10^4</eq></td><td>1.72</td><td>3.55</td><td>2.68</td><td>2.04</td><td>1.59</td><td>1.26</td><td>1.06</td><td>0.91</td><td>0.72</td><td>0.56</td><td>0.37</td></tr><tr><td><eq>Med(X/Cap) \times 10^4</eq></td><td>0.35</td><td>0.98</td><td>0.80</td><td>0.58</td><td>0.42</td><td>0.32</td><td>0.27</td><td>0.23</td><td>0.19</td><td>0.15</td><td>0.09</td></tr><tr><td><eq>Avg C(X) \times 10^4</eq></td><td>16.79</td><td>44.95</td><td>21.46</td><td>14.53</td><td>12.62</td><td>11.70</td><td>5.58</td><td>9.27</td><td>3.99</td><td>7.37</td><td>6.16</td></tr><tr><td><eq>Avg Comm \times 10^4</eq></td><td>7.43</td><td>14.90</td><td>9.30</td><td>7.86</td><td>7.00</td><td>6.15</td><td>5.49</td><td>4.93</td><td>4.34</td><td>3.62</td><td>2.68</td></tr><tr><td><eq>Avg SEC fee \times 10^5</eq></td><td>2.90</td><td>3.26</td><td>3.02</td><td>3.00</td><td>2.85</td><td>2.84</td><td>2.76</td><td>2.76</td><td>2.73</td><td>2.68</td><td>2.56</td></tr><tr><td># Obs</td><td>439,765</td><td>71,000</td><td>68,689</td><td>41,238</td><td>49,000</td><td>28,073</td><td>29,330</td><td>29,778</td><td>34,409</td><td>40,640</td><td>47,608</td></tr><tr><td># Stks</td><td>2,583</td><td>1,108</td><td>486</td><td>224</td><td>182</td><td>106</td><td>126</td><td>90</td><td>102</td><td>81</td><td>78</td></tr></table>


Table 2: OLS Estimates of Order Size.


<table><tr><td rowspan="2"></td><td rowspan="2">All</td><td colspan="2">NYSE</td><td colspan="2">NASDAQ</td></tr><tr><td>Buy</td><td>Sell</td><td>Buy</td><td>Sell</td></tr><tr><td><eq>\ln [\bar{q}]</eq></td><td>-5.67(0.017)</td><td>-5.68(0.023)</td><td>-5.63(0.018)</td><td>-5.75(0.035)</td><td>-5.65(0.032)</td></tr><tr><td><eq>\alpha_0</eq></td><td>-0.62(0.009)</td><td>-0.63(0.011)</td><td>-0.59(0.008)</td><td>-0.71(0.019)</td><td>-0.59(0.015)</td></tr><tr><td><eq>R^2</eq></td><td>0.3167</td><td>0.2587</td><td>0.2646</td><td>0.4298</td><td>0.3542</td></tr><tr><td><eq>Q^*/V^*·\delta^{-1}×10^{-4}</eq></td><td>34.62</td><td>34.14</td><td>35.98</td><td>31.80</td><td>34.78</td></tr><tr><td>#Obs</td><td>439,765</td><td>131,530</td><td>150,377</td><td>69,871</td><td>87,987</td></tr></table>


Table presents the estimates ln $\bar { q }$ and $\alpha _ { 0 }$ for the regression: 


$$
\ln \left[ \frac {X _ {i}}{V _ {i}} \right] = \ln \left[ \bar {q} \right] + \alpha_ {0} \cdot \ln \left[ \frac {W _ {i}}{W ^ {*}} \right] + \tilde {\epsilon} _ {i}.
$$

Each observation corresponds to transition order i with order size $X _ { i }$ , benchmark price $P _ { 0 , i } { \mathrm { . } }$ , expected daily volume $V _ { i } ,$ expected daily volatility $\sigma _ { i } ,$ trading activity $W _ { i } . \bar { q }$ is the measure of order size such that $Q ^ { * } / V ^ { * }$ measures the median order size for a benchmark stock. The benchmark stock has daily volatility of 2%, share price of $40, and daily volume of one million shares. The standard errors are clustered at weekly levels for 17 industries and shown in parentheses. The sample ranges from January 2001 to December 2005. 


Table 3: OLS Estimates for Order Size: Model Calibration.


<table><tr><td rowspan="2"></td><td rowspan="2">All</td><td colspan="2">NYSE</td><td colspan="2">NASDAQ</td></tr><tr><td>Buy</td><td>Sell</td><td>Buy</td><td>Sell</td></tr><tr><td colspan="6">Restricted Specification: <eq>\alpha_0 = -2/3, b_1 = b_2 = b_3 = b_4 = 0</eq></td></tr><tr><td><eq>\ln [\bar{q}]</eq></td><td>-5.71(0.019)</td><td>-5.70(0.023)</td><td>-5.68(0.019)</td><td>-5.70(0.042)</td><td>-5.77(0.039)</td></tr><tr><td><eq>Q^*/V^* \cdot \delta^{-1} \times 10^{-4}</eq></td><td>33.13</td><td>33.46</td><td>34.14</td><td>33.46</td><td>31.20</td></tr><tr><td>MSE</td><td>2.53</td><td>2.61</td><td>2.54</td><td>2.32</td><td>2.56</td></tr><tr><td><eq>R^2</eq></td><td>0.3149</td><td>0.2578</td><td>0.2599</td><td>0.4278</td><td>0.3479</td></tr><tr><td colspan="6">Unrestricted Specification With 5 Degrees of Freedom: <eq>\alpha_0 = -2/3.</eq></td></tr><tr><td><eq>R^2</eq></td><td>0.3229</td><td>0.2668</td><td>0.2739</td><td>0.4318</td><td>0.3616</td></tr><tr><td>#Obs</td><td>439,765</td><td>131,530</td><td>150,377</td><td>69,871</td><td>87,987</td></tr></table>

Table presents the estimates ln $\bar { q }$ and the mean squared error (MSE) for the regression: 

$$
\ln \left[ \frac {X _ {i}}{V _ {i}} \right] = \ln [ \bar {q} ] + \alpha_ {0} \cdot \ln \left[ \frac {W _ {i}}{W ^ {*}} \right] + b _ {1} \cdot \ln \left[ \frac {\sigma_ {i}}{0 . 0 2} \right] + b _ {2} \cdot \ln \left[ \frac {P _ {0 , i}}{4 0} \right] + b _ {3} \cdot \ln \left[ \frac {V _ {i}}{1 0 ^ {6}} \right] + b _ {4} \cdot \ln \left[ \frac {\nu_ {i}}{1 / 1 2)} \right] + \tilde {\epsilon} _ {i}.
$$

with $\alpha _ { 0 }$ restricted to be $- 2 / 3$ as predicted by invariance hypothesis and $b _ { 1 } =$ $b _ { 2 } = b _ { 3 } = 0$ . Each observation corresponds to transition order i with order size $X _ { i }$ , benchmark price $P _ { 0 , i }$ , expected daily volume $V _ { i } ,$ expected daily volatility $\sigma _ { i } .$ , trading activity $W _ { i }$ , and monthly turnover rate $\nu _ { i } . ~ \bar { q }$ is the measure of order size such that $Q ^ { * } / V ^ { * }$ measures the corresponding percentile of order size for a benchmark stock. The benchmark stock has daily volatility of $2 \%$ , share price of $\$ 40$ , and daily volume of one million shares. The $R ^ { 2 } \mathrm { s }$ are reported for restricted specification with $\alpha _ { 0 } = - 2 / 3 , b _ { 1 } = b _ { 2 } = b _ { 3 } = b _ { 4 } = 0$ as well as for unrestricted specification with coeficients ln ¯q and $b _ { 1 } , b _ { 2 } , b _ { 3 } , b _ { 4 }$ allowed to vary freely. The standard errors are clustered at weekly levels for 17 industries and shown in parentheses. The sample ranges from January 2001 to December 2005. 


Table 4: Transactions Cost Estimates in Non-Linear Regression.


<table><tr><td rowspan="2"></td><td rowspan="2">All</td><td colspan="2">NYSE</td><td colspan="2">NASDAQ</td></tr><tr><td>Buy</td><td>Sell</td><td>Buy</td><td>Sell</td></tr><tr><td><eq>\beta_{mkt}</eq></td><td>0.66(0.013)</td><td>0.63(0.016)</td><td>0.62(0.016)</td><td>0.76(0.037)</td><td>0.78(0.036)</td></tr><tr><td><eq>\kappa_0^* \times 10^4</eq></td><td>1.77(0.837)</td><td>-0.27(2.422)</td><td>1.14(1.245)</td><td>0.77(4.442)</td><td>3.55(1.415)</td></tr><tr><td><eq>\alpha_1</eq></td><td>-0.49(0.050)</td><td>-0.37(1.471)</td><td>-0.50(0.114)</td><td>0.53(1.926)</td><td>-0.44(0.045)</td></tr><tr><td><eq>\kappa_I^* \times 10^4</eq></td><td>10.69(1.376)</td><td>12.08(2.693)</td><td>9.56(2.254)</td><td>12.33(2.356)</td><td>9.34(2.686)</td></tr><tr><td>z</td><td>0.57(0.039)</td><td>0.54(0.056)</td><td>0.56(0.062)</td><td>0.44(0.051)</td><td>0.63(0.086)</td></tr><tr><td><eq>\alpha_2</eq></td><td>-0.32(0.015)</td><td>-0.40(0.037)</td><td>-0.33(0.029)</td><td>-0.41(0.035)</td><td>-0.29(0.037)</td></tr><tr><td><eq>R^2</eq></td><td>0.1010</td><td>0.1118</td><td>0.1029</td><td>0.0945</td><td>0.0919</td></tr><tr><td>#Obs</td><td>439,765</td><td>131,530</td><td>150,377</td><td>69,871</td><td>87,987</td></tr></table>


Table presents the estimates for $\beta _ { m k t } , z , \alpha _ { 1 } , \kappa _ { 0 } ^ { * } , \alpha _ { 2 }$ , and $\kappa _ { I } ^ { * }$ in the regression: 


$$
\mathbb {I} _ {B S, i} \cdot S _ {i} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} = \beta_ {m k t} \cdot R _ {m k t} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} + \mathbb {I} _ {B S, i} \cdot \kappa_ {0} ^ {*} \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {\alpha_ {1}} + \mathbb {I} _ {B S, i} \cdot \kappa_ {I} ^ {*} \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {\alpha_ {2}} \cdot \left[ \frac {\phi I _ {i}}{0 . 0 1} \right] ^ {z} + \tilde {\epsilon} _ {i}.\tag{72}
$$

where $\phi I _ { i } / 0 . 0 1 = X _ { i } / ( 0 . 0 1 V _ { i } ) \cdot ( W _ { i } / W ^ { * } ) ^ { 2 / 3 } . S _ { i }$ is implementation shortfall. $R _ { m k t }$ is the value-weight market return for the first day of transition. The trading activity $W _ { i }$ is the product of expected volatility $\sigma _ { i } .$ benchmark price $P _ { 0 , i } ,$ and expected volume $V _ { i } .$ . The scaling constant $W ^ { * } = ( 0 . 0 2 ) ( 4 0 ) ( 1 0 ^ { 6 } )$ is the trading activity for the benchmark stock with volatility of 2% per day, price $40 per share, and trading volume of one million shares per day. $X _ { i }$ is the number of shares in the order i. $\kappa _ { I } ^ { * }$ is the market impact costs of executing a trade of one percent of daily volume in a benchmark stock, and $\kappa _ { 0 } ^ { \ast }$ is the efective spread cost. The standard errors are clustered at weekly levels for 17 industries and shown in parentheses. The sample ranges from January 2001 to December 2005. 


Table 5: Transactions Costs: Model Calibration.


<table><tr><td rowspan="2"></td><td rowspan="2">All</td><td colspan="2">NYSE</td><td colspan="2">NASDAQ</td></tr><tr><td>Buy</td><td>Sell</td><td>Buy</td><td>Sell</td></tr><tr><td></td><td colspan="5">Linear Model: <eq>z = 1</eq>, <eq>\beta_1 = \beta_2 = \beta_3 = \beta_4 = \beta_5 = \beta_6 = \beta_7 = \beta_8 = 0</eq>.</td></tr><tr><td><eq>\kappa_0^* \times 10^4</eq></td><td>8.21(0.578)</td><td>7.19(1.122)</td><td>6.77(0.794)</td><td>9.18(1.563)</td><td>9.27(0.781)</td></tr><tr><td><eq>\kappa_I^* \times 10^4</eq></td><td>2.50(0.190)</td><td>3.37(0.370)</td><td>1.92(0.265)</td><td>3.46(0.395)</td><td>2.46(0.327)</td></tr><tr><td><eq>R^2</eq></td><td>0.0991</td><td>0.1102</td><td>0.1012</td><td>0.0926</td><td>0.0897</td></tr><tr><td></td><td colspan="5">Square Root Model: <eq>z = 1/2</eq>, <eq>\beta_1 = \beta_2 = \beta_3 = \beta_4 = \beta_5 = \beta_6 = \beta_7 = \beta_8 = 0</eq>.</td></tr><tr><td><eq>\kappa_0^* \times 10^4</eq></td><td>2.08(0.704)</td><td>-1.31(1.278)</td><td>0.92(0.926)</td><td>2.28(2.055)</td><td>4.65(0.824)</td></tr><tr><td><eq>\kappa_I^* \times 10^4</eq></td><td>12.08(0.742)</td><td>15.65(1.218)</td><td>11.10(1.298)</td><td>13.50(1.456)</td><td>10.41(1.207)</td></tr><tr><td><eq>R^2</eq></td><td>0.1007</td><td>0.1116</td><td>0.1027</td><td>0.0941</td><td>0.0911</td></tr><tr><td></td><td colspan="5">Unrestricted Specification With 12 Degrees of Freedom.</td></tr><tr><td><eq>R^2</eq></td><td>0.1016</td><td>0.1121</td><td>0.1032</td><td>0.0957</td><td>0.0944</td></tr><tr><td>#Obs</td><td>439,765</td><td>131,530</td><td>150,377</td><td>69,871</td><td>87,987</td></tr></table>

Table presents the estimates $\kappa _ { 0 } ^ { \ast }$ and $\kappa _ { I } ^ { * }$ for the regression: 

$$
\begin{array}{r l} & {\mathbb {I} _ {B S, i} \cdot S _ {i} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} = \beta_ {m k t} \cdot R _ {m k t} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} \mathbb {I} _ {B S, i} \cdot \kappa_ {0} ^ {*} \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {- 1 / 3} \cdot \frac {\sigma_ {i} ^ {\beta_ {1}} \cdot P _ {0 , i} ^ {\beta_ {2}} \cdot V _ {i} ^ {\beta_ {3}} \cdot \nu_ {i} ^ {\beta_ {4}}}{(0 . 0 2) (4 0) (1 0 ^ {6}) (1 / 1 2)} +} \\ & {\qquad + \mathbb {I} _ {B S, i} \cdot \kappa_ {I} ^ {*} \cdot \left[ \frac {\phi I _ {i}}{0 . 0 1} \right] ^ {z} \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {- 1 / 3} \cdot \frac {\sigma_ {i} ^ {\beta_ {5}} \cdot P _ {0 , i} ^ {\beta_ {6}} \cdot V _ {i} ^ {\beta_ {7}} \cdot \nu_ {i} ^ {\beta_ {8}}}{(0 . 0 2) (4 0) (1 0 ^ {6}) (1 / 1 2)} + \tilde {\epsilon} _ {i}.} \end{array}
$$

where invariant $\phi I _ { i } / 0 . 0 1 = X _ { i } / ( 0 . 0 1 V _ { i } ) \cdot ( W _ { i } / W ^ { * } ) ^ { 2 / 3 } . S _ { i }$ is implementation shortfall. $R _ { m k t }$ is the value-weight market return for the first day of transition. The trading activity $W _ { i }$ is the product of expected volatility $\sigma _ { i } .$ , benchmark price $P _ { 0 , i }$ , and expected volume $V _ { i } .$ . The scaling constant $W ^ { * } = ( 0 . 0 2 ) ( 4 0 ) ( 1 0 ^ { 6 } )$ is the trading activity for the benchmark stock with volatility of 2% per day, price $40 per share, and trading volume of one million shares per day. $X _ { i }$ is the number of shares in the order i. $\kappa _ { I } ^ { * }$ is the market impact costs of executing a trade of one percent of daily volume in a benchmark stock, and $\kappa _ { 0 } ^ { \ast }$ is the efective spread cost. The $R ^ { 2 } \mathrm { s }$ are reported for restricted specification as well as for unrestricted specification with twelve coeficients $\beta _ { m k t } , ~ z , ~ \kappa _ { I } ^ { * } , \kappa _ { 0 } ^ { * } , \beta _ { 1 } , \beta _ { 2 } , \beta _ { 3 } , \beta _ { 4 } , \beta _ { 5 } , \beta _ { 6 } , \beta _ { 7 } , \beta _ { 8 }$ allowed to vary freely. The standard errors are clustered at weekly levels for 17 industries and shown in parentheses. The sample ranges from January 2001 to December 2005. 62 62 


Table 6: OLS Estimates of Log of Quoted Spread.


<table><tr><td rowspan="2"></td><td rowspan="2">All</td><td colspan="2">NYSE</td><td colspan="2">NASDAQ</td></tr><tr><td>Buy</td><td>Sell</td><td>Buy</td><td>Sell</td></tr><tr><td><eq>\ln \bar{s}</eq></td><td>-3.07(0.008)</td><td>-3.09(0.008)</td><td>-3.08(0.008)</td><td>-3.04(0.013)</td><td>-3.04(0.012)</td></tr><tr><td><eq>\alpha_3</eq></td><td>-0.35(0.003)</td><td>-0.31(0.003)</td><td>-0.32(0.003)</td><td>-0.40(0.004)</td><td>-0.39(0.004)</td></tr><tr><td><eq>R^2</eq></td><td>0.4744</td><td>0.3545</td><td>0.3964</td><td>0.5516</td><td>0.5721</td></tr><tr><td><eq>e^{\ln \bar{s}}\cdot 0.02\times 10^4</eq></td><td>9.28</td><td>9.10</td><td>9.19</td><td>9.57</td><td>9.57</td></tr><tr><td>#Obs</td><td>434,920</td><td>130,700</td><td>149,197</td><td>68,833</td><td>86,190</td></tr></table>


Table presents the estimates ln ¯s and $\alpha _ { 3 }$ for the regression: 


$$
\ln \left[ \frac {s _ {i}}{P _ {i} \cdot \sigma_ {i}} \right] = \ln \bar {s} + \alpha_ {3} \cdot \ln \left[ \frac {W _ {i}}{W ^ {*}} \right] + \tilde {\epsilon} _ {i},
$$

Each observation corresponds to order i. The left-hand side variable is the logarithm of the quoted bid-ask spread $s _ { i } / P _ { 0 , i }$ as a fraction of expected return volatility $\sigma _ { i }$ . The trading activity $W _ { i }$ is the product of expected daily volatility $\sigma _ { i } .$ benchmark price $P _ { 0 , i }$ , and expected daily volume $V _ { i } ,$ , measured as the last month’s average daily volume. The scaling constant $W ^ { * } = ( 0 . 0 2 ) ( 4 0 ) ( 1 0 ^ { 6 } )$ corresponds to the trading activity for the benchmark stock with volatility of 2% per day, price $40 per share, and trading volume of one million shares per day. The median percentage spread for a benchmark stock is exp(ln ¯s) · 0.02. The standard errors are clustered at weekly levels for 17 industries and shown in parentheses. The sample ranges from January 2001 to December 2005. 


<sub>2:</sub> <sub>Invariant</sub> <sub>Order</sub> <sup>Size</sup> <sup>Distri</sup>


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/c5f5b707-866d-494a-8be3-5c8615679388/b57538118e0702d0f16f000ae299406ea825cfca58868d0f95697657cba78a76.jpg)


<sub>ce</sub>m<sup>ber</sup> <sup>20</sup> <sub>variance</sub> <sub>of</sub> <sub>distribution</sub> <sub>over</sub> <sub>the</sub> <sub>entire</sub> <sub>sample.</sub> <sub>The</sub> <sub>sa</sub>m<sup>ple</sup> <sup>ranges</sup> <sup>from</sup> <sub>( ance</sub> <sub>of</sub> <sub>2.54</sub> <sub>is</sub> <sub>imposed</sub> <sub>on</sub> <sub>each</sub> <sub>subplot.</sub> <sub>The</sub> <sub>com</sub><sup>mon</sup> <sup>mean</sup> <sup>and</sup> <sup>varia</sup> <sub>the</sub> <sub>kurtosis</sub> <sub>k)</sub> <sub>for</sub> <sub>depicted</sub> <sub>distribution.</sub> <sub>The</sub> <sub>nor</sub>m<sup>al</sup> <sup>distribution</sup> <sup>with</sup> <sub>ubplot</sub> <sub>also</sub> <sub>shows</sub> <sub>the</sub> <sub>number</sub> <sub>of</sub> <sub>observations</sub> <sub>(N),</sub> <sub>t</sub><sup>he</sup> <sup>mean</sup> <sup>(m),</sup> <sup>the</sup> <sub>mon</sub> <sub>N</sub>Y<sup>SE-listed</sup> <sup>stocks.</sup> <sup>Volatility</sup> <sup>group</sup> <sup>1</sup> <sup>(group</sup> <sup>5)</sup> <sup>has</sup> <sup>stocks</sup> <sup>with</sup> <sup>th</sup> <sub>lu</sub>m<sup>e.</sup> <sup>The</sup> <sup>thresholds</sup> <sup>of</sup> <sup>five</sup> <sup>volatility</sup> <sup>groups</sup> <sup>correspond</sup> <sup>to</sup> <sup>20th,</sup> <sup>40t</sup> <sub>s</sub> <sub>listed</sub> <sub>on</sub> <sub>the</sub> <sub>NYSE.</sub> V<sup>olume</sup> <sup>group</sup> <sup>1</sup> <sup>(group</sup> <sup>10)</sup> <sup>contains</sup> <sup>orders</sup> <sup>in</sup> <sup>s</sup> <sub>to</sub> <sub>30th,</sub> <sub>50th,</sub> <sub>60th,</sub> <sub>70th,</sub> <sub>75th,</sub> <sub>80th,</sub> <sub>85t</sub>h<sup>,</sup> <sup>90th,</sup> <sup>and</sup> <sup>95th</sup> <sup>percentile</sup> <sub>erage</sub> <sub>daily</sub> <sub>volume</sub> <sub>in</sub> <sub>shares,</sub> <sub>and</sub>W<sup>iis</sup> <sup>the</sup> <sup>trading</sup> <sup>activity.</sup> <sup>The</sup> <sup>thresh</sup> <sub>(</sub>  <sub>( me</sub> <sub>groups</sub> <sub>1,</sub> <sub>4,</sub> <sub>7,</sub> <sub>9,</sub> <sub>10</sub> <sub>and</sub> <sub>volati</sub>l<sup>ity</sup> <sup>groups</sup> <sup>1,</sup> <sup>3,</sup> <sup>5</sup> <sup>are</sup> <sup>reported).</sup> <sup>Xi</sup> <sub>ibutions</sub> <sub>of</sub> <sub>ln˜ X/V)+2/3</sub> <sub>lnWi</sub>/<sup>W∗)</sup> <sup>for</sup> <sup>stocks</sup> <sup>sorted</sup> <sup>into</sup> <sup>10</sup> <sup>volume</sup> <sup>grou</sup> 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/c5f5b707-866d-494a-8be3-5c8615679388/77d52da6385a077ebf98beef711d8791ee42ae67c494104d9b0fd9b3872573cd.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/c5f5b707-866d-494a-8be3-5c8615679388/fdd0a8ee5f48947b2b509921d7eeac7f26a9fe629cc3b7ab2417a78d2960a522.jpg)



<sub>ntile-to-Quantile</sub> <sub>Plot</sub> <sub>for</sub> <sub>Empirical</sub> <sub>an</sub><sup>d</sup> <sup>Lognormal</sup>


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/c5f5b707-866d-494a-8be3-5c8615679388/3d96e5af6d72441b2718b056213873fc4b51704141deb213e07b329f4aa8b957.jpg)



<sub>3:</sub> <sub>Invariant</sub> <sub>Order</sub> <sup>Size</sup> <sup>Distri</sup>


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/c5f5b707-866d-494a-8be3-5c8615679388/b6c5d935788a22914315cc669aaad8d56d1cf82c3cd0d383aa6e1b14d3d4260c.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/c5f5b707-866d-494a-8be3-5c8615679388/55e23e775a6c4de39d701f5cfec976fc0ea18161af7c93619b4d773d6c37c410.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/c5f5b707-866d-494a-8be3-5c8615679388/f321b9ca06a64355814ee1ef2bc1cce0f6edb23dc39a74374a2276d0e7366992.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/c5f5b707-866d-494a-8be3-5c8615679388/9610ce0e9a3ea94e2c44a6c927bc024234cab6bcd084183e8d24163de2c8434f.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/c5f5b707-866d-494a-8be3-5c8615679388/e3c539aa3791e0b863f4205026df1791bb30e4e318e313893a837db26d67c338.jpg)



<sub>( e</sub> <sub>sample</sub> <sub>ran</sub><sup>ges</sup> <sup>from</sup> <sup>January</sup> <sup>2001</sup> <sup>to</sup> <sup>Dece</sup> <sub>he</sub> <sub>skewness</sub> <sub>(s),</sub> <sub>and</sub> <sub>the</sub> <sub>kurtosis</sub> <sub>(k</sub>) <sup>of</sup> <sup>a</sup> <sup>depicted</sup> <sup>distribution.</sup> <sup>There</sup> <sub>t)</sub> <sub>trading</sub> <sub>volume.</sub> <sub>Each</sub> <sub>subplot</sub> <sub>shows</sub> <sub>the</sub> <sub>nu</sub>m<sup>ber</sup> <sup>of</sup> <sup>observations</sup> <sup>(N</sup> <sub>ollar</sub> <sub>volume</sub> <sub>for</sub> <sub>common</sub> <sup>NYSE-listed</sup> <sup>stocks.</sup> <sup>Volume</sup> <sup>group</sup> <sup>1</sup> <sup>(group</sup> <sup>1</sup> <sub>th</sub> <sub>thresholds</sub> <sub>correspondi</sub>n<sup>g</sup> <sup>to</sup> <sup>30th,</sup> <sup>50th,</sup> <sup>60th,</sup> <sup>70th,</sup> <sup>75th,</sup> <sup>80th,</sup> <sup>85t</sup> <sub>hm</sub> <sub>of</sub> <sub>ranks</sub> <sub>based</sub> <sub>on</sub> <sub>that</sub> <sub>d</sub><sup>istribution.</sup> <sup>The</sup> <sup>ten</sup> <sup>volume</sup> <sup>groups</sup> <sup>are</sup> <sup>based</sup> <sub>cks</sub> <sub>sorted</sub> <sub>into</sub> <sub>10</sub> <sub>volume</sub> <sub>groups</sub> (<sup>only</sup> <sup>volume</sup> <sup>groups</sup> <sup>1,</sup> <sup>4,</sup> <sup>7,</sup> <sup>9,</sup> <sup>10</sup> <sup>are</sup> <sup>r</sup> <sub>antile-quantile</sub> <sub>plots</sub> <sub>of</sub> <sub>empirical</sub> <sub>distributions</sub> <sub>of</sub> <sub>ln(˜X/V)</sub> <sub>+</sub> <sub>2/3</sub> <sub>ln(</sub>W<sup>i/</sup>


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/c5f5b707-866d-494a-8be3-5c8615679388/8f2f3606c2648e5d2915358028def2b4d84cfad1da2d0bf47d0125516849642d.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/c5f5b707-866d-494a-8be3-5c8615679388/6ac691ff11121f88da9b5f2de8296acc20f1456c4d4d4675219602e2777a8843.jpg)



Figure 4: Order Size and Trading Activity.


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/c5f5b707-866d-494a-8be3-5c8615679388/8afd1ddb118f4d57e0e86cc25153dae9891c9b514a9fbf9a22c582cfd33bc78f.jpg)



The figure plots ln $( X _ { i } / V _ { i } )$ on the vertical axis against ln $( W _ { i } / W ^ { * } )$ on the horizontal axis, where $X _ { i }$ is portfolio transition order size in shares, $V _ { i }$ is average daily volume in shares, and $W _ { i } = P _ { i } \cdot V _ { i } \cdot \sigma _ { i }$ is trading activity. The fitted line is $\ln ( X _ { i } / V _ { i } ) = - 5 . 7 0 5 - 2 / 3 \cdot \ln ( W _ { i } / W ^ { * } )$ , where the intercept is estimated from an OLS regression with the slope fixed at $- 2 / 3$ . There are 400,000+ data points from January 2001 to December 2005.



Figure5:InvariantTransactionsCostFunctions.


Figure shows estimates of transactions cost functions for stock sorted into 10 volume groups. On the horizontal axis, there are 100 equally spaced bins based on re-scaled order sizes, $\phi I = \tilde{X} / V \cdot (W_i / W^*)^{2/3}$ . For each volume group $k = 1,\dots,10$ , the subplot contains 100 estimates of dummy variables $f^*(k,h)/L^*, h = 1,\dots,100$ from regression (62). On the right-hand side vertical axis, there are units of scaled transactions cost $f^*(.)/L^*$ for a benchmark stock. On the left-hand side vertical axis, there are units of actual transactions cost $f^*(.)/L^k$ for a benchmark stock, where $1/L^k$ is the illiquidity measure for orders in volume group $k$ . The 95th percent confidence interval estimates based on the entire sample are imposed on each subplot (blue dotted lines). The common linear and square root functions are imposed on each subplot with the parameter estimated on the entire sample. A linear function is $2.50 \cdot 10^{-4} \cdot \phi I / 0.01 + 8.21 \cdot 10^{-4}$ (black solid line). A square root function is $12.07 \cdot 10^{-4} \cdot \sqrt{\phi I / 0.01} + 2.08 \cdot 10^{-4}$ (grey solid line). The thresholds of ten volume groups correspond to 30th, 50th, 60th, 70th, 75th, 80th, 85th, 90th, and 95th percentiles of dollar volume for common stocks listed on the NYSE. Group 1 (group 10) contains orders in stocks with lowest (highest) dollar volume. Each subplot also shows the number of observations $N$ and the number of stocks $M$ (for the last month). The sample ranges from January 2001 to December 2005. 


Figure 6: Transactions Cost Functions.


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/c5f5b707-866d-494a-8be3-5c8615679388/38bd6a2934d29e26de4c3a31c8ed7d1cb27d3c3a26ce4914a987aa15be885e21.jpg)



Figure shows estimates of transactions cost functions based on entire sample. On the horizonal axis, there are 100 equally spaced bins based on re-scaled order sizes, $\phi I = \tilde { X } / V \cdot \left( W _ { i } / W ^ { * } \right) ^ { - 2 / 3 }$ . The plot contains 100 estimates $f ^ { * } ( k , h ) / L ^ { * } , h = 1 , . . . ,$ , 100 from the regression


$$
\mathbb {I} _ {B S, i} \cdot S _ {i} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} = \beta_ {m k t} \cdot R _ {m k t} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} + \mathbb {I} _ {B S, i} \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {- 1 / 3} \cdot \sum_ {h = 1} ^ {1 0 0} D _ {i} ^ {*} (k, h) \cdot f ^ {*} (k, h) / L ^ {*} + \tilde {\epsilon} _ {i}.
$$

$X _ { i }$ is an order size in shares, $V _ { i }$ is the average daily volume in shares, and $W _ { i }$ is the measure of trading activity. The vertical axis presents estimated transactions cost invariant $f ^ { * } ( . ) / L$ in basis points. The 95th percent confidence interval are superimposed (dotted lines). A linear function is $2 . 5 0 \cdot 1 0 ^ { - 4 } \cdot { \phi } I / 0 . 0 1 + 8 . 2 1 \cdot 1 0 ^ { - 4 }$ (black solid line). A square root function is $1 2 . 0 7 \cdot 1 0 ^ { - 4 } \cdot \sqrt { \phi I / 0 . 0 1 } + 2 . 0 8 \cdot 1 0 ^ { - 4 }$ (grey solid line). The √sample ranges from January 2001 to December 2005. 

Part I Appendix 


Table 7: Quantile Estimates of Order Size.


<table><tr><td></td><td>p1</td><td>p5</td><td>p25</td><td>p50</td><td>p75</td><td>p95</td><td>p99</td></tr><tr><td><eq>\ln\left[\bar{q}\right]</eq></td><td>-9.37(0.008)</td><td>-8.31(0.006)</td><td>-6.73(0.004)</td><td>-5.66(0.003)</td><td>-4.59(0.004)</td><td>-3.05(0.006)</td><td>-2.05(0.009)</td></tr><tr><td><eq>α_0</eq></td><td>-0.65(0.005)</td><td>-0.64(0.003)</td><td>-0.61(0.002)</td><td>-0.62(0.002)</td><td>-0.61(0.002)</td><td>-0.64(0.003)</td><td>-0.63(0.005)</td></tr><tr><td>Pseudo <eq>R^2</eq></td><td>0.1621</td><td>0.1534</td><td>0.1650</td><td>0.1727</td><td>0.1795</td><td>0.1949</td><td>0.2232</td></tr><tr><td><eq>Q^*/V^*·δ×10^{-4}</eq></td><td>0.85</td><td>2.46</td><td>11.95</td><td>34.83</td><td>101.53</td><td>473.59</td><td>1287.35</td></tr><tr><td>#Obs</td><td>439,765</td><td>439,765</td><td>439,765</td><td>439,765</td><td>439,765</td><td>439,765</td><td>439,765</td></tr></table>

Table presents the estimates ln $\bar { q }$ and $\alpha _ { 0 }$ for the quantile regression: 

$$
\ln \left[ \frac {X _ {i}}{V _ {i}} \right] = \ln \left[ \bar {q} \right] + \alpha_ {0} \cdot \ln \left[ \frac {W _ {i}}{W ^ {*}} \right] + \tilde {\epsilon} _ {i}.
$$

Each observation corresponds to transition order i with order size $X _ { i }$ , benchmark price $P _ { 0 , i }$ , expected daily volume $V _ { i } ,$ expected daily volatility $\sigma _ { i } ,$ trading activity $W _ { i } . \bar { q }$ is the measure of order size such that $Q ^ { * } / V ^ { * }$ measures the corresponding percentile of order size for a benchmark stock. The benchmark stock has daily volatility of $2 \%$ , share price of $40, and daily volume of one million shares. The standard errors are shown in parentheses. The sample ranges from January 2001 to December 2005. 


Table 8: OLS Estimates for Order Size: Model Calibration.


<table><tr><td rowspan="2"></td><td rowspan="2">All</td><td colspan="2">NYSE</td><td colspan="2">NASDAQ</td></tr><tr><td>Buy</td><td>Sell</td><td>Buy</td><td>Sell</td></tr><tr><td colspan="6">Restricted Specification: <eq>\alpha_0 = -2/3, b_1 = b_2 = b_3 = b_4 = 0</eq></td></tr><tr><td><eq>\ln [\bar{q}]</eq></td><td>-5.71(0.019)</td><td>-5.70(0.023)</td><td>-5.68(0.019)</td><td>-5.70(0.042)</td><td>-5.77(0.039)</td></tr><tr><td><eq>Q^*/V^* \cdot \delta \times 10^4</eq></td><td>33.13</td><td>33.46</td><td>34.14</td><td>33.46</td><td>31.20</td></tr><tr><td>MSE</td><td>2.53</td><td>2.61</td><td>2.54</td><td>2.32</td><td>2.56</td></tr><tr><td><eq>R^2</eq></td><td>0.3149</td><td>0.2578</td><td>0.2599</td><td>0.4278</td><td>0.3479</td></tr><tr><td colspan="6">Unrestricted Specification With 5 Degrees of Freedom: <eq>\alpha_0 = -2/3</eq>.</td></tr><tr><td><eq>\ln [\bar{q}]</eq></td><td>-5.53(0.019)</td><td>-5.55(0.026)</td><td>-5.48(0.019)</td><td>-5.77(0.051)</td><td>-5.48(0.047)</td></tr><tr><td><eq>b_1</eq></td><td>0.42(0.040)</td><td>0.47(0.050)</td><td>0.53(0.043)</td><td>0.19(0.094)</td><td>0.33(0.087)</td></tr><tr><td><eq>b_2</eq></td><td>0.24(0.019)</td><td>0.17(0.021)</td><td>0.29(0.017)</td><td>0.04(0.049)</td><td>0.33(0.040)</td></tr><tr><td><eq>b_3</eq></td><td>0.06(0.010)</td><td>0.06(0.012)</td><td>0.07(0.009)</td><td>-0.06(0.026)</td><td>0.07(0.021)</td></tr><tr><td><eq>b_4</eq></td><td>-0.18(0.015)</td><td>-0.24(0.020)</td><td>-0.22(0.017)</td><td>-0.02(0.040)</td><td>-0.11(0.032)</td></tr><tr><td><eq>R^2</eq></td><td>0.3229</td><td>0.2668</td><td>0.2739</td><td>0.4318</td><td>0.3616</td></tr><tr><td>#Obs</td><td>439,765</td><td>131,530</td><td>150,377</td><td>69,871</td><td>87,987</td></tr></table>


Table presents the estimates and the mean squared error (MSE) for the regression: 


$$
\ln \left[ \frac {X _ {i}}{V _ {i}} \right] = \ln [ \bar {q} ] + \alpha_ {0} \cdot \ln \left[ \frac {W _ {i}}{W ^ {*}} \right] + b _ {1} \cdot \ln \left[ \frac {\sigma_ {i}}{0 . 0 2} \right] + b _ {2} \cdot \ln \left[ \frac {P _ {0 , i}}{4 0} \right] + b _ {3} \cdot \ln \left[ \frac {V _ {i}}{1 0 ^ {6}} \right] + b _ {4} \cdot \ln \left[ \frac {\nu_ {i}}{1 / 1 2}\right) + \tilde {\epsilon} _ {i}.
$$

with $\alpha _ { 0 }$ restricted to be $- 2 / 3$ as predicted by invariance hypothesis and $b _ { 1 } =$ $b _ { 2 } = b _ { 3 } = 0$ . Each observation corresponds to transition order i with order size $X _ { i }$ , benchmark price $P _ { 0 , i } { \mathrm { . } }$ , expected daily volume $V _ { i } ,$ expected daily volatility $\sigma _ { i } .$ trading activity $W _ { i }$ , and monthly turnover rate $\nu _ { i } . ~ \bar { q }$ is the measure of order size such that $Q ^ { * } / V ^ { * }$ measures the corresponding percentile of order size for a benchmark stock. The benchmark stock has daily volatility of $2 \%$ , share price of $40, and daily volume of one million shares. The $R ^ { 2 } \mathrm { s }$ are reported for restricted specification with $\alpha _ { 0 } = - 2 / 3 , b _ { 1 } = b _ { 2 } = b _ { 3 } = b _ { 4 } = 0$ as well as for unrestricted specification with coeficients ln $\bar { q }$ and $b _ { 1 } , b _ { 2 } , b _ { 3 } , b _ { 4 }$ allowed to vary freely. The standard errors are clustered at weekly levels for 17 industries and shown in parentheses. The sample ranges from January 2001 to December 2005. 


Table 9: Transactions Cost Estimates in Non-Linear Regression with Linear Impact.


<table><tr><td rowspan="2"></td><td rowspan="2">All</td><td colspan="2">NYSE</td><td colspan="2">NASDAQ</td></tr><tr><td>Buy</td><td>Sell</td><td>Buy</td><td>Sell</td></tr><tr><td><eq>\beta_{mkt}</eq></td><td>0.66(0.013)</td><td>0.63(0.016)</td><td>0.62(0.016)</td><td>0.77(0.037)</td><td>0.77(0.036)</td></tr><tr><td><eq>\kappa_0^* \times 10^4</eq></td><td>6.28(0.890)</td><td>6.51(1.600)</td><td>5.43(1.154)</td><td>5.94(2.147)</td><td>6.54(1.501)</td></tr><tr><td><eq>α_1</eq></td><td>-0.40(0.020)</td><td>-0.36(0.048)</td><td>-0.39(0.029)</td><td>-0.44(0.051)</td><td>-0.40(0.031)</td></tr><tr><td><eq>κ_I^* \times 10^4</eq></td><td>2.73(0.252)</td><td>2.63(0.460)</td><td>2.10(0.346)</td><td>3.69(0.663)</td><td>3.13(0.765)</td></tr><tr><td><eq>α_2</eq></td><td>-0.31(0.028)</td><td>-0.45(0.038)</td><td>-0.31(0.041)</td><td>-0.32(0.056)</td><td>-0.28(0.058)</td></tr><tr><td><eq>R^2</eq></td><td>0.0993</td><td>0.1105</td><td>0.1014</td><td>0.0931</td><td>0.0901</td></tr><tr><td>#Obs</td><td>439,765</td><td>131,530</td><td>150,377</td><td>69,871</td><td>87,987</td></tr></table>

Table presents the estimates for $\beta _ { m k t } , \alpha _ { 1 } , \kappa _ { 0 } ^ { * } , \alpha _ { 2 }$ , and $\kappa _ { I } ^ { * }$ in the regression: 

$$
\mathbb {I} _ {B S, i} \cdot S _ {i} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} = \beta_ {m k t} \cdot R _ {m k t} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} + \mathbb {I} _ {B S, i} \cdot \kappa_ {0} ^ {*} \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {\alpha_ {1}} + \mathbb {I} _ {B S, i} \cdot \kappa_ {I} ^ {*} \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {\alpha_ {2}} \cdot \left[ \frac {\phi I _ {i}}{0 . 0 1} \right] ^ {z} + \tilde {\epsilon} _ {i}.\tag{73}
$$

where $z = 1$ and $\phi I _ { i } / 0 . 0 1 = X _ { i } / ( 0 . 0 1 V _ { i } ) \cdot ( W _ { i } / W ^ { * } ) ^ { 2 / 3 } . S _ { i }$ is implementation shortfall. $R _ { m k t }$ is the value-weight market return for the first day of transition. The trading activity $W _ { i }$ is the product of expected volatility $\sigma _ { i } .$ benchmark price $P _ { 0 , i }$ , and expected volume $V _ { i } .$ . The scaling constant $W ^ { * } = ( 0 . 0 2 ) ( 4 0 ) ( 1 0 ^ { 6 } )$ is the trading activity for the benchmark stock with volatility of 2% per day, price $40 per share, and trading volume of one million shares per day. $X _ { i }$ is the number of shares in the order i. $\kappa _ { I } ^ { * }$ is the market impact costs of executing a trade of one percent of daily volume in a benchmark stock, and $\kappa _ { 0 } ^ { \ast }$ is the efective spread cost. The standard errors are clustered at weekly levels for $1 7$ industries and shown in parentheses. The sample ranges from January 2001 to December 2005. 


Table 10: Transactions Cost Estimates in Non-Linear Regression with Quoted Spread.


<table><tr><td rowspan="2"></td><td rowspan="2">All</td><td colspan="2">NYSE</td><td colspan="2">NASDAQ</td></tr><tr><td>Buy</td><td>Sell</td><td>Buy</td><td>Sell</td></tr><tr><td><eq>\beta_{mkt}</eq></td><td>0.65(0.013)</td><td>0.63(0.016)</td><td>0.62(0.015)</td><td>0.76(0.036)</td><td>0.77(0.037)</td></tr><tr><td><eq>\kappa_I \times 10^4</eq></td><td>2.95(0.261)</td><td>2.97(0.504)</td><td>2.24(0.366)</td><td>3.76(0.700)</td><td>2.95(0.749)</td></tr><tr><td><eq>α_2</eq></td><td>-0.32(0.029)</td><td>-0.44(0.036)</td><td>-0.32(0.039)</td><td>-0.37(0.053)</td><td>-0.33(0.060)</td></tr><tr><td>h</td><td>0.71(0.053)</td><td>0.61(0.110)</td><td>0.74(0.094)</td><td>0.61(0.127)</td><td>0.75(0.073)</td></tr><tr><td><eq>R^2</eq></td><td>0.0976</td><td>0.1094</td><td>0.1010</td><td>0.0891</td><td>0.0872</td></tr><tr><td>#Obs</td><td>436,649</td><td>131,100</td><td>149,600</td><td>69,218</td><td>86,731</td></tr></table>

Table presents the estimates for $\beta _ { m k t } , \kappa _ { I } , \alpha _ { 2 }$ , and h in the regression: 

$$
\mathbb {I} _ {B S, i} \cdot S _ {i} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} = \beta_ {m k t} \cdot R _ {m k t} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} + \mathbb {I} _ {B S, i} \cdot h \cdot \frac {1}{2} \cdot \frac {s _ {i}}{P _ {0 , i}} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} + \mathbb {I} _ {B S, i} \cdot \kappa_ {I} \cdot \left[ \frac {\phi I _ {i}}{0 . 0 1} \right] \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {\alpha_ {2}} + \tilde {\epsilon} _ {i}.
$$

where invariant $\begin{array} { r } { I _ { i } = \frac { X _ { i } } { ( 0 . 0 1 ) V _ { i } } \cdot \left[ \frac { W _ { i } } { W ^ { * } } \right] ^ { 2 / 3 } } \end{array}$ . Each observation corresponds to order i. $\mathbb { I } _ { B S , i }$ is a buy/sell indicator, $S _ { i }$ is implementation shortfall, $R _ { m k t }$ is the value-weight market return for the first day of transition. The term $( 0 . 0 2 ) / \sigma _ { i }$ adjusts for heteroscedasticity. The trading activity $W _ { i }$ is the product of expected volatility $\sigma _ { i } ,$ , benchmark price $P _ { 0 , i } { \mathrm { . } }$ , and expected volume $V _ { i } .$ . The scaling constant $W ^ { * } = ( 0 . 0 2 ) ( 4 0 ) ( 1 0 ^ { 6 } )$ is the trading activity for the benchmark stock with volatility of 2% per day, price $40 per share, and trading volume of one million shares per day. $X _ { i }$ is the number of shares in the order i. $\kappa _ { I }$ is the market impact costs of executing a trade of one percent of daily volume in a benchmark stock. $s _ { i } / P _ { 0 , i }$ is the quoted spread. The standard errors are clustered at weekly levels for 17 industries and shown in parentheses. The sample ranges from January 2001 to December 2005. 


Table 11: Transactions Costs: Model Calibration.


<table><tr><td rowspan="2"></td><td rowspan="2">All</td><td colspan="2">NYSE</td><td colspan="2">NASDAQ</td></tr><tr><td>Buy</td><td>Sell</td><td>Buy</td><td>Sell</td></tr><tr><td></td><td colspan="5">Linear Model: z = 1, β1 = β2 = β3 = β4 = β5 = β6 = β7 = β8 = 0.</td></tr><tr><td>βmkt</td><td>0.6571(0.0135)</td><td>0.6308(0.0159)</td><td>0.6195(0.0158)</td><td>0.7693(0.0371)</td><td>0.7771(0.0365)</td></tr><tr><td>κ0 × 104</td><td>8.2134(0.5776)</td><td>7.1934(1.1215)</td><td>6.7698(0.7943)</td><td>9.1832(1.5627)</td><td>9.2658(0.7811)</td></tr><tr><td>κI × 104</td><td>2.5003(0.1903)</td><td>3.3663(0.3700)</td><td>1.9220(0.2650)</td><td>3.4614(0.3953)</td><td>2.4629(0.3267)</td></tr><tr><td>R2</td><td>0.0991</td><td>0.1102</td><td>0.1012</td><td>0.0926</td><td>0.0897</td></tr><tr><td></td><td colspan="5">Square Root Model: z = 1/2, β1 = β2 = β3 = β4 = β5 = β6 = β7 = β8 = 0.</td></tr><tr><td>βmkt</td><td>0.6552(0.0134)</td><td>0.6285(0.0158)</td><td>0.6192(0.0159)</td><td>0.7598(0.0365)</td><td>0.7782(0.0364)</td></tr><tr><td>κ0 × 104</td><td>2.0763(0.7035)</td><td>-1.3091(1.2779)</td><td>0.9167(0.9264)</td><td>2.2844(2.0554)</td><td>4.6530(0.8244)</td></tr><tr><td>κI × 104</td><td>12.0787(0.7416)</td><td>15.6544(1.2177)</td><td>11.0986(1.2979)</td><td>13.5025(1.4564)</td><td>10.4063(1.2069)</td></tr><tr><td>R2</td><td>0.1007</td><td>0.1116</td><td>0.1027</td><td>0.0941</td><td>0.0911</td></tr><tr><td></td><td colspan="5">Unrestricted Specification With 12 Degrees of Freedom.</td></tr><tr><td>βmkt</td><td>0.66(0.013)</td><td>0.63(0.016)</td><td>0.62(0.015)</td><td>0.76(0.036)</td><td>0.78(0.036)</td></tr><tr><td>κ0* × 104</td><td>0.94(0.675)</td><td>-0.05(0.124)</td><td>0.47(0.556)</td><td>1.55(1.698)</td><td>1.61(1.148)</td></tr><tr><td>β1</td><td>-0.43(0.147)</td><td>-2.47(0.890)</td><td>-1.08(0.392)</td><td>-0.44(0.489)</td><td>-0.46(0.131)</td></tr><tr><td>β2</td><td>0.17(0.072)</td><td>2.87(1.230)</td><td>0.23(0.231)</td><td>0.20(0.127)</td><td>0.11(0.109)</td></tr><tr><td>β3</td><td>-0.56(0.159)</td><td>1.85(0.754)</td><td>-0.47(0.296)</td><td>-0.47(0.238)</td><td>-0.49(0.155)</td></tr><tr><td>β4</td><td>0.62(0.173)</td><td>0.13(0.620)</td><td>0.49(0.490)</td><td>0.49(0.313)</td><td>0.58(0.175)</td></tr><tr><td>κI* × 104</td><td>9.36(1.307)</td><td>11.61(2.471)</td><td>10.93(1.804)</td><td>8.88(3.340)</td><td>5.00(2.033)</td></tr><tr><td>z</td><td>0.58(0.041)</td><td>0.54(0.039)</td><td>0.52(0.042)</td><td>0.58(0.094)</td><td>0.63(0.083)</td></tr><tr><td>β5</td><td>0.02(0.135)</td><td>-0.11(0.192)</td><td>0.36(0.229)</td><td>-0.17(0.252)</td><td>-0.23(0.242)</td></tr><tr><td>β6</td><td>-0.14(0.061)</td><td>-0.11(0.113)</td><td>0.03(0.100)</td><td>-0.27*(0.120)</td><td>-0.22(0.113)</td></tr><tr><td>β7</td><td>0.01(0.037)</td><td>-0.07(0.050)</td><td>0.04(0.052)</td><td>0.00(0.099)</td><td>-0.16(0.100)</td></tr><tr><td>β8</td><td>0.08(0.067)</td><td>0.07(0.086)</td><td>-0.11(0.101)</td><td>0.08(0.143)</td><td>0.39(0.153)</td></tr><tr><td>R2</td><td>0.1016</td><td>0.1121</td><td>0.1032</td><td>0.0957</td><td>0.0944</td></tr><tr><td>#Obs</td><td>439,765</td><td>131,530</td><td>150,377</td><td>69,871</td><td>87,987</td></tr></table>

Table presents the estimates for the regression: 

$$
\begin{array}{l} \mathbb {I} _ {B S, i} \cdot S _ {i} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} = \beta_ {m k t} \cdot R _ {m k t} \cdot \frac {(0 . 0 2)}{\sigma_ {i}} \mathbb {I} _ {B S, i} \cdot \kappa_ {0} ^ {*} \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {- 1 / 3} \cdot \frac {\sigma_ {i} ^ {\beta_ {1}} \cdot P _ {0 , i} ^ {\beta_ {2}} \cdot V _ {i} ^ {\beta_ {3}} \cdot \nu_ {i} ^ {\beta_ {4}}}{(0 . 0 2) (4 0) (1 0 ^ {6}) (1 / 1 2)} + \\ \qquad + \mathbb {I} _ {B S, i} \cdot \kappa_ {I} ^ {*} \cdot \left[ \frac {\phi I _ {i}}{0 . 0 1} \right] ^ {z} \cdot \left[ \frac {W _ {i}}{W ^ {*}} \right] ^ {- 1 / 3} \cdot \frac {\sigma_ {i} ^ {\beta_ {5}} \cdot P _ {0 , i} ^ {\beta_ {6}} \cdot V _ {i} ^ {\beta_ {7}} \cdot \nu_ {i} ^ {\beta_ {8}}}{(0 . 0 2) (4 0) (1 0 ^ {6}) (1 / 1 2)} + \tilde {\epsilon} _ {i}. \end{array}
$$

where $\phi I _ { i } / 0 . 0 1 = X _ { i } / ( 0 . 0 1 V _ { i } ) \cdot ( W _ { i } / W ^ { * } ) ^ { 2 / 3 } . S _ { i }$ is implementation shortfall. $R _ { m k t }$ is the value-weight market return for the first day of transition. The trading activity $W _ { i }$ is the product of expected volatility $\sigma _ { i } .$ benchmark price $P _ { 0 , i }$ , and expected volume $V _ { i } .$ . The scaling constant $W ^ { * } = ( 0 . 0 2 ) ( 4 0 ) ( 1 0 ^ { 6 } )$ is the trading activity for the benchmark stock with volatility of 2% per day, price $40 per share, and trading volume of one million shares per day. $X _ { i }$ is the number of shares in the order i. $\kappa _ { I } ^ { * }$ is the market impact costs of executing a trade of one percent of daily volume in a benchmark stock, and $\kappa _ { 0 } ^ { \ast }$ is the efective spread cost. The $R ^ { 2 } \mathrm { s }$ are reported for restricted specification as well as for unrestricted specification with twelve coeficients $\beta _ { m k t } , ~ z , ~ \kappa _ { I } ^ { * } , \kappa _ { 0 } ^ { * } , \beta _ { 1 } , \beta _ { 2 } , \beta _ { 3 } , \beta _ { 4 } , \beta _ { 5 } , \beta _ { 6 } , \beta _ { 7 } , \beta _ { 8 }$ allowed to vary freely. The standard errors are clustered at weekly levels for 17 industries and shown in parentheses. The sample ranges from January 2001 to December 2005. 