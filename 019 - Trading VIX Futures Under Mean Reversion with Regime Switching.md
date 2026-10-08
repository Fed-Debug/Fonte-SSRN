# Trading VIX Futures under Mean Reversion with Regime Switching<sup>∗</sup>

Jiao Li<sup>†</sup> 

June 11, 2016 

## Abstract

This paper studies the optimal VIX futures trading problems under a regime-switching model. We consider the VIX as mean reversion dynamics with dependence on the regime that switches among a finite number of states. For the trading strategies, we analyze the timings and sequences of the investor’s market participation, which leads to several corresponding coupled system of variational inequalities. The numerical approach is developed to solve these optimal double stopping problems by using projected-successive-over-relaxation (PSOR) method with Crank-Nicolson scheme. We illustrate the optimal boundaries via numerical examples of twostate Markov chain model. In particular, we examine the impacts of transaction costs and regime-switching timings on the VIX futures trading strategies. 

Keywords: optimal stopping, mean reversion, futures trading, regime switching, variational inequality 

JEL Classification: C41, G11, G13 

Mathematics Subject Classification (2010): 60G40, 62L15, 91G20, 91G80 

## 1 Introduction

The Chicago Board Options Exchange (CBOE) Volatility Index, commonly known as the VIX, is widely used measure of the market volatility. It was introduced by the CBOE back in 1993, and its calcualtion is based on the implied volatility of S&P 500 index options. Empirically, the VIX is shown to be negatively correlated to the market index. One broadly accepted explanation is that investors buy put options on S&P500 for protection against market turmoil. This increases the option prices and implied volatilities, and thus, the value of the VIX. As a result, the VIX is also called the investor fear gauge (see Whaley (2000)). 

While VIX itself is not traded, investors can gain exposure to the index by trading VIX futures. VIX futures, which are cash settled on the VIX index level, were first traded on the CBOE Futures Exchange in 2004, and since then the market has been growing constantly. Recent market data illustrate the liquidity and popularity of the VIX futures market. During 2015, the average daily volume (ADV) in the VIX futures was over 200,000 contracts, with 51.6 million VIX futures contracts traded in total. 

Each VIX futures comes with a fixed term, ranging from 1 to 9 months, but futures holders do not need to keep the position through the expiration date, and can choose when to close out the position. Furthermore, before entering the market, the investor can opt to start a long or short position, followed by closing it at later time before expiration. 

In this paper, we investigate the VIX futures trading under Cox-Ingersoll-Ross (CIR) model with regime switching. The CIR dynamics is well studied in many empirical studies (see, e.g. Gr¨ubichler and Longstaf (1996), Wang and Daigler (2011)). Zhang and Zhu (2006) analyze the empirical validity of the CIR model by first estimating its parameters from VIX historical data and provide a futures pricing formula. Later Dotsis et al. (2007) add jumps to a CIR difusion. However, studies of Menc´ıa and Sentana (2013) and Sircar and Papanicolaou (2014) show that VIX implied volatility data can be better reproduced by incorporating regime switching. Leung et al. (2016) display two characteristically diferent term structures observed in the VIX futures market. These markedly diferent regimes ofer a very interesting testing ground for analyzing the performance of diferent models for volatility derivatives. It is necessary to allow the key parameters of the VIX to respond to the general market movements. The regime-switching model is one of such formulations, where the model parameters depend on the market regime that switches among a finite number of states. The market regime could reflect the state of the market, the general mood of investors, and other economic factors. Elliott et al. (2008) evaluate the risk measures for derivatives via a partial diferential equation (PDE) approach when the underlying asset dynamics are associated with regime switching. The applications on regime switching for derivatives pricing and optimal stopping problems have been well studied in the literature (see, e.g. Guo (2001), Bufington and Elliott (2002) and Le and Wang (2010)). 

Moreover, we introduce the investor’s optimal strategies to participate the trading. In the first strategy, an investor is expected to establish the long position when the price is suficiently low, and then exits when the price is high. The opposite is expected for the second strategy. In both cases, the presence of transaction costs expands the waiting region, indicating the investor’s desire for better prices. In addition, the waiting region expands drastically near expiry since transaction costs discourage entry when futures is very close to maturity. Finally, the main feature of our trading problem approach is to combine these two related problems and analyze the optimal strategy when an investor has the freedom to choose between either a long-short or a short-long position. Among our results, we find that when the investor has the right to choose, she delays market entry to wait for better prices compared to the individual standalone problems. 

In an earlier study, Brennan and Schwartz (1990) propose the optimal strategies for stock index futures with position limits, where the Brownian bridge process is applied for the the basis dynamics. Dai et al. (2011) extend the optimal strategies with the additional flexibility by allowing the investor to switch between long position and short position directly. In this paper, we extend the model introduced in Leung et al. (2016) by incorporating regime switching into the CIR model for the VIX. We provide a link between the futures pricing problem under the risk-neutral measure and the trading problem conducted under the historical measure. In contrast to Brennan and Schwartz (1990) and Dai et al. (2011), we do not a priori assume the existence of a stochastic basis that may or may not be consistent with the futures prices, but consider the long and short strategies that take advantage of the temporal price diference of futures. Similar trading strategies have been studied by Leung and Li (2015), Leung et al. (2015), Leung et al. (2014), Leung and Li (2016), Leung and Shirai (2015) and Stepanek (2015), among others. Moreover, the strategy studied herein can be automated. For a comprehensive study on algorithmic trading, we refer the reader to Cartea et al. (2015). The ideas can be applied to other derivatives, such as swaps (see Leung and Yamazaki (2013) and Leung and Liu (2012)). 

With regime switching, the optimal trading strategies are determined from a system of m variational inequalities, where $m$ is the number of possible regimes of the market. We apply an implicit-explicit finite diference method with projected-successive-over-relaxation (PSOR) to solve for the optimal trading boundaries under all regimes. While there are a number of studies on optimal stopping problems with regime switching as mentioned above, there are very few that discuss the numerical methods and solutions. In a related study, Khaliq and Liu (2009) develop a penalty method method for pricing the regime-switching American option. 

The rest of the paper is organized as follows. In section 2, we formulate the optimal stopping and trading strategies with regime switching. In section 3, we develop an implicit scheme based on PSOR method. In Section 4, we present the numerical results for optimal trading problems and provide financial interpretations. 

## 2 Optimal Timing to Trade Futures with Regime Switching

We fix a probability space $( \Omega , \mathcal { F } , \mathbb { P } )$ , where P is the historical measure. Let $\xi$ be a continuous-time irreducible finite-state Markov chain with state space $E = \{ 1 , 2 , \dots , m \}$ . The generator matrix of $\xi$ is denoted by $Q ,$ , which has constant entries $q _ { i j }$ for $i , j \in E$ , such that $q _ { i j } \geq 0$ for $i \neq j$ and $\textstyle \sum _ { j \in E } q _ { i j } = 0$ for each $i \in E$ . This Markov chain represents the changing regime of the financial market, and it influences the dynamics of the index. 

Let B be a standard Brownian motion defined on $( \Omega , \mathcal { F } , \mathbb { P } )$ and assume it is independent of $\xi .$ The VIX, denoted by $S ,$ is assumed to follow the CIR process regime switching: 

$$
d S _ {t} = \mu (\xi_ {t}) (\theta (\xi_ {t}) - S _ {t}) d t + \sigma (\xi_ {t}) \sqrt {S _ {t}} d B _ {t},\tag{2.1}
$$

where, for each $i \in E$ , the coeficients $\mu ( i ) , \theta ( i )$ and $\sigma ( i )$ are known constants, with $\mu ( i ) , \theta ( i )$ 2 $\sigma ( i ) > 0$ . Note that $\mu ( i ) , \theta ( i )$ and $\sigma ( i )$ depend on the Markov chain, representing the mean reversion rate, the long-run mean and the volatility of the VIX at regime i. 

To price futures, we assume a re-parametrized CIR model for the risk-neutral VIX dynamics. Due to the additional uncertainty described by regime switching, we note that introducing a Markov chain results in an incomplete market. Hence the equivalent martingale measure is not unique. Elliott et al. (2008) employ the regime-switching Esscher transform to determine an equivalent martingale pricing measure. We do not include the argument in our paper and instead assume that the risk-neutral probability space $( \Omega , \mathcal { F } , \mathbb { Q } )$ is given. Thus, under the risk-neutral measure $\mathbb { Q } ,$ the VIX follows 

$$
d S _ {t} = \tilde {\mu} (\xi_ {t}) (\tilde {\theta} (\xi_ {t}) - S _ {t}) d t + \sigma (\xi_ {t}) \sqrt {S _ {t}} d B _ {t} ^ {\mathbb {Q}},\tag{2.2}
$$

where $\tilde { \mu } ( i ) , \tilde { \theta } ( i ) , \sigma ( i ) > 0$ and $B ^ { \mathbb { Q } }$ is a Q-standard Brownian motion which is also independent of Markov chain. For convenience, we may use the subscript notation for these constants, e.g. $\mu _ { i } \equiv \mu ( i ) , \theta _ { i } \equiv \theta ( i )$ , and $\sigma _ { i } \equiv \sigma ( i )$ . In both SDEs, (2.1) and (2.2), we require $2 \mu _ { i } \theta _ { i } \geq \sigma _ { i } ^ { 2 }$ and $2 \tilde { \mu } _ { i } \tilde { \theta } _ { i } \geq \sigma _ { i } ^ { 2 }$ (Feller condition) so that the CIR process stays strictly positive at all times. The two Brownian motions are related by 

$$
d B _ {t} ^ {\mathbb {Q}} = d B _ {t} + \frac {\mu (\xi_ {t}) (\theta (\xi_ {t}) - S _ {t}) - \tilde {\mu} (\xi_ {t}) (\tilde {\theta} (\xi_ {t}) - S _ {t})}{\sigma (\xi_ {t}) \sqrt {S _ {t}}} d t,\tag{2.3}
$$

such as change of measure preserves the CIR model, up to diferent parameter values across two measures. 

We consider a futures contract written on the S with maturity $T < \infty$ and futures price at time $0 \leq t \leq T$ when $S _ { t } = s$ and regime $\xi _ { t } = i$ . The price of a futures contract is given by 

$$
f (t, s, i) = \mathbb {E} ^ {\mathbb {Q}} \{S _ {T} | S _ {t} = s, \xi_ {t} = i \}, t \leq T,\tag{2.4}
$$

where $\mathbb { E } ^ { \mathbb { Q } }$ is the expectation operator with respect to the risk-neutral measure $\mathbb { Q } .$ We can show that $f _ { i } ( t , s ) \equiv f ( t , s , i ) , i = 1 , \ldots , m ,$ satisfy the following partial diferential equation (see, e.g. Yao et al. (2006)), 

$$
\left\{ \begin{array}{r l} \frac {\partial f _ {i}}{\partial t} + \tilde {\mu} _ {i} (\tilde {\theta} _ {i} - s) \frac {\partial f _ {i}}{\partial s} + \frac {\sigma_ {i} ^ {2} s}{2} \frac {\partial^ {2} f _ {i}}{\partial s ^ {2}} + \sum_ {j \neq i} \tilde {q} _ {i j} (f _ {j} - f _ {i}) = 0, & (t, s) \in [ 0, T) \times \mathbb {R} _ {+}, \\ f _ {i} (T, s) = s, & s \in \mathbb {R} _ {+}, \end{array} \right.\tag{2.5}
$$

where $\tilde { q } _ { i j }$ is the transition probability under measure $\mathbb { Q } .$ . We note that (2.5) involves m interconnected PDEs due to the regime switching introduced in the VIX dynamics. One can eficiently compute the futures prices in all regimes by finite diference methods; see section 3 below. 

## 2.1 Optimal Double Stopping Approach

Let us consider the scenario in which an investor has a long position in a futures contract with expiration date T. With a long position in the futures, the investor can hold it till maturity, but can also close the position early by taking an opposite position at the prevailing market price. At maturity, the two opposite positions cancel each other. This motivates us to investigate the best time to close. 

If the investor selects to close the long position at time $\tau \leq { \hat { T } } .$ , then she will receive the market value of the futures on the expiry date, denoted by $f ( \tau , S _ { \tau } , \xi _ { \tau } )$ , minus the transaction cost $c \geq 0$ To maximize the expected discounted value, evaluated under the investor’s historical probability measure $\mathbb { P }$ with a constant subjective discount rate $r \geq 0$ , the investor solves the optimal stopping problem 

$$
\mathcal {V} (t, s, i) = \sup _ {\tau \in \mathcal {T} _ {t, \hat {T}}} \mathbb {E} \Bigl \{e ^ {- r (\tau - t)} (f (\tau , S _ {\tau}, \xi_ {\tau}) - c) | S _ {t} = s, \xi_ {t} = i \Bigr \},\tag{2.6}
$$

where $\mathcal { T } _ { t , \hat { T } }$ is the set of all stopping times, with taking values between t and $\hat { T }$ , where ${ \hat { T } } \in ( 0 , T ]$ is the trading deadline, which can equal but not exceed the futures’ maturity. Throughout this chapter, we continue to use the notation $\mathbb { E } \{ \cdot \}$ to indicate the expectation taken under the historical probability measure P. 

The value function $\mathcal { V } ( t , s , i )$ represents the expected liquidation value associated with the long futures position in i−state. Prior to taking the long position in $f _ { i } ,$ , the investor, with zero position, can select the optimal timing to start the trade, or not to enter at all. This leads us to analyze the timing option inherent in the trading problem. Precisely, at time $t \leq \hat { T }$ , the investor faces the optimal entry timing problem 

$$
\mathcal {J} (t, s, i) = \sup _ {\nu \in \mathcal {T} _ {t, \hat {T}}} \mathbb {E} \Bigl \{e ^ {- r (\nu - t)} (\mathcal {V} (\nu , S _ {\nu}, \xi_ {\nu}) - (f (\nu , S _ {\nu}, \xi_ {\nu}) + \hat {c})) ^ {+} | S _ {t} = s, \xi_ {t} = i \Bigr \},\tag{2.7}
$$

where $\hat { c } \geq 0$ is the transaction cost, which may difer from c. In other words, the investor seeks to maximize the expected diference between the value function $\mathcal { V } ( \nu , S _ { \nu } , \xi _ { \nu } )$ associated with the long position and the prevailing futures price $f ( \nu , S _ { \nu } , \xi _ { \nu } )$ . The value function $\mathcal { I } ( \nu , S _ { \nu } , \xi _ { \nu } )$ represents the maximum expected value of the trading opportunity embedded in the futures. We refer this “long to open, short to close” strategy as the long-short strategy. 

Alternatively, an investor may well choose to short a futures contract with the speculation that the futures price will fall. By taking a short futures position, the investor can either close it out later by establishing a long position, or hold it until the expiry which will result in a cash settlement. Given an investor who has a unit short position in the futures contract, the objective is to minimize the expected discounted cost to close out this position at/before maturity. The optimal timing strategy is determined from 

$$
\mathcal {U} (t, s, i) = \inf _ {\tau \in \mathcal {T} _ {t, \hat {T}}} \mathbb {E} \Bigl \{e ^ {- r (\tau - t)} (f (\tau , S _ {\tau}, \xi_ {\tau}) + \hat {c}) | S _ {t} = s, \xi_ {t} = i \Bigr \}.\tag{2.8}
$$

If the investor begins with a zero position, then she can decide when to enter the market by solving 

$$
\mathcal {K} (t, s, i) = \sup _ {\nu \in \mathcal {T} _ {t, \hat {T}}} \mathbb {E} \Bigl \{e ^ {- r (\nu - t)} ((f (\nu , S _ {\nu}, \xi_ {\nu}) - c) - \mathcal {U} (\nu , S _ {\nu}, \xi_ {\nu})) ^ {+} | S _ {t} = s, \xi_ {t} = i \Bigr \}.\tag{2.9}
$$

We call this “short to open, long to close” strategy as the short-long strategy. 

When an investor contemplates entering the market, she can either long or short first. Therefore, on top of the timing option, the investor has an additional choice between the long-short and shortlong strategies. Hence, the investor solves the market entry timing problem: 

$$
\mathcal {P} (t, s, i) = \sup _ {\varsigma \in \mathcal {T} _ {t, \hat {T}}} \mathbb {E} \Bigl \{e ^ {- r (\varsigma - t)} \max \{\mathcal {A} (\varsigma , S _ {\varsigma}, \xi_ {\varsigma}), \mathcal {B} (\varsigma , S _ {\varsigma}, \xi_ {\varsigma}) \} | S _ {t} = s, \xi_ {t} = i \Bigr \},\tag{2.10}
$$

with two alternative rewards upon entry defined by 

$$
\begin{array}{l l} \mathcal {A} (\varsigma , S _ {\varsigma}, \xi_ {\varsigma}) := (\mathcal {V} (\varsigma , S _ {\varsigma}, \xi_ {\varsigma}) - (f (\varsigma , S _ {\varsigma}, \xi_ {\varsigma}) + \hat {c})) ^ {+} & \text {(long - short)}, \\ \mathcal {B} (\varsigma , S _ {\varsigma}, \xi_ {\varsigma}) := ((f (\varsigma , S _ {\varsigma}, \xi_ {\varsigma}) - c) - \mathcal {U} (\varsigma , S _ {\varsigma}, \xi_ {\varsigma})) ^ {+} & \text {(short - long)}. \end{array}
$$

Accordingly, the corresponding inputs associated with the optimal stopping problem in (2.10) is given by taking the maximum between the above two rewards. 

## 2.2 Variational Inequalities & Optimal Trading Strategies

Given the CIR dynamics of the VIX, the value functions defined in (2.6) – (2.10) all satisfy the same governing diferential equation in their respective continuation regions and their values equal to the corresponding rewards in their exercise regions. In order to solve for the optimal trading strategies, we need to study the coupled systems of variational inequalities respectively. To this end, we first define the operators: 

$$
\mathcal {L} _ {i} \{\cdot \} := - r \cdot + \frac {\partial \cdot}{\partial t} + \mu_ {i} (\theta_ {i} - s) \frac {\partial \cdot}{\partial s} + \frac {\sigma_ {i} ^ {2} s}{2} \frac {\partial^ {2} \cdot}{\partial s ^ {2}} + \sum_ {j \neq i} q _ {i j} (\cdot_ {j} - \cdot_ {i}),\tag{2.11}
$$

corresponding to CIR model. For convenience, we adopt the subscript notation for these value functions, $\mathrm { e . g . } \ \mathcal { V } _ { i } ( t , s ) \equiv \mathcal { V } ( t , s , i ) , \ \mathcal { I } _ { i } ( t , s ) \equiv \mathcal { I } ( t , s , i ) , \ \mathcal { U } _ { i } ( t , s ) \equiv \mathcal { U } ( t , s , i ) , \ \mathcal { K } _ { i } ( t , s ) \equiv K ( t , s , i )$ and $\mathcal { P } _ { i } ( t , s ) \equiv \mathcal { P } ( t , s , i )$ 

The optimal exit and entry problems $\mathcal { I } _ { i }$ and $\nu _ { i }$ associated with the long-short strategy are solved from the following pair of variational inequalities: 

$$
\max \left\{\mathcal {L} _ {i} \mathcal {V} _ {i} (t, s), (f _ {i} (t, s) - c) - \mathcal {V} _ {i} (t, s) \right\} = 0,\tag{2.12}
$$

$$
\max \left\{\mathcal {L} _ {i} \mathcal {J} _ {i} (t, s), (\mathcal {V} _ {i} (t, s) - (f _ {i} (t, s) + \hat {c})) ^ {+} - \mathcal {J} _ {i} (t, s) \right\} = 0,\tag{2.13}
$$

for $( t , s ) \in [ 0 , \hat { T } ] \times \mathbb { R } _ { + }$ . Similarly, the reverse short-long strategy can be determined by numerically solving the variational inequalities satisfied by $\mathcal { U } _ { i }$ and $\kappa _ { i }$ : 

$$
\min \left\{\mathcal {L} _ {i} \mathcal {U} _ {i} (t, s), \left(f _ {i} (t, s) + \hat {c}\right) - \mathcal {U} _ {i} (t, s) \right\} = 0,\tag{2.14}
$$

$$
\max \left\{\mathcal {L} _ {i} \mathcal {K} _ {i} (t, s), ((f _ {i} (t, s) - c) - \mathcal {U} _ {i} (t, s)) ^ {+} - \mathcal {K} _ {i} (t, s) \right\} = 0.\tag{2.15}
$$

To determine the optimal timing to enter the futures market, we solve the variational inequality 

$$
\max \left\{\mathcal {L} _ {i} \mathcal {P} _ {i} (t, s), \max \{\mathcal {A} _ {i} (t, s), \mathcal {B} _ {i} (t, s) \} - \mathcal {P} _ {i} (t, s) \right\} = 0.\tag{2.16}
$$

In other words, we have to solve the variational inequality (2.12) – (2.15), and then use the solution as inputs to the variational inequality (2.16). 

## 3 Numerical Implementation with Regime Switching

The numerical solution of the system of variational inequalities can be obtained by applying a finitediference scheme in all regimes with the use of the projected-successive-over-relaxation (PSOR) method.<sup>1</sup> The solution of the resulting equations for value functions are solved by the successive over relaxation (SOR) method. In each SOR iterative step in finding the numerical approximation of the value functions, we simply take the maximum value between the approximated function value and compensated futures price. The futures price can be pre-computed by (2.5) conveniently. Similar numerical schemes with regime switching can be found in Leung (2010). More details of our numerical scheme are described in the following. 

First, we define the generic diferential operator 

$$
\mathcal {L} _ {i} \{\cdot \} := - r \cdot + \frac {\partial \cdot}{\partial t} + \varphi_ {i} (s) \frac {\partial \cdot}{\partial s} + \frac {\sigma_ {i} ^ {2} (s)}{2} \frac {\partial^ {2} \cdot}{\partial s ^ {2}} + \sum_ {j \neq i} q _ {i j} (\cdot_ {j} - \cdot_ {i}),\tag{3.1}
$$

then the variational inequalities (2.12) – (2.16) admit the same form as the following variational inequality problem: 

$$
\left\{ \begin{array}{c} \mathcal {L} _ {i} g _ {i} (t, s) \leq 0, g _ {i} (t, s) \geq h _ {i} (t, s), (t, s) \in [ 0, \hat {T}) \times \mathbb {R} _ {+}, \\ (\mathcal {L} _ {i} g _ {i} (t, s)) (h _ {i} (t, s) - g _ {i} (t, s)) = 0, (t, s) \in [ 0, \hat {T}) \times \mathbb {R} _ {+}, \\ g _ {i} (\hat {T}, s) = h _ {i} (\hat {T}, s), s \in \mathbb {R} _ {+}. \end{array} \right.\tag{3.2}
$$

Here, $g _ { i } ( t , s )$ represents the value functions $\mathcal { V } _ { i } ( t , s ) , \ \mathcal { I } _ { i } ( t , s ) , \ - \mathcal { U } _ { i } ( t , s ) , \ \mathcal { K } _ { i } ( t , s )$ , or $\mathcal { P } _ { i } ( t , s )$ . The function $h _ { i } ( t , s )$ represents $f _ { i } ( t , s ) - c , ( \mathcal { V } _ { i } ( t , s ) - ( f _ { i } ( t , s ) + \hat { c } ) ) ^ { + } , - ( f _ { i } ( t , s ) + \hat { c } ) , ( f _ { i } ( t , s ) - c ) - \mathcal { U } _ { i } ( t , s ) ) ^ { + }$ or max $\{ \mathcal { A } _ { i } ( t , s ) , B _ { i } ( t , s ) \}$ . The futures price $f _ { i } ( t , s )$ , with $\hat { T } \le T$ , is given by (2.4). 

We now consider the discretization of the partial diferential equation $\mathcal { L } _ { i } g _ { i } ( t , s ) = 0$ , over an uniform grid with discretizations in time $\begin{array} { r } { ( \delta t = \frac { \hat { T } } { N } ) } \end{array}$ , and space $\begin{array} { r } { ( \delta s = \frac { S \mathrm { m a x } } { M } ) } \end{array}$ . Applying the Crank-Nicolson method for s-derivatives and backward diference for t-derivatives on the resulting equation leads the finite diference equation: 

$$
\begin{array}{c} - \frac {r}{2} (g _ {i} ^ {m, n} + g _ {i} ^ {m, n - 1}) + \frac {g _ {i} ^ {m , n} - g _ {i} ^ {m , n - 1}}{\delta t} + \frac {\varphi_ {i} ^ {m}}{2} (\frac {g _ {i} ^ {m + 1 , n} - g _ {i} ^ {m - 1 , n}}{2 \delta s} + \frac {g _ {i} ^ {m + 1 , n - 1} - g _ {i} ^ {m - 1 , n - 1}}{2 \delta s}) \\ + \frac {(\sigma_ {i} ^ {m}) ^ {2}}{2} (\frac {g _ {i} ^ {m + 1 , n} - 2 g _ {i} ^ {m , n}}{2 (\delta s) ^ {2}} + \frac {g _ {i} ^ {m - 1 , n}}{2 (\delta s) ^ {2}} + \frac {g _ {i} ^ {m + 1 , n - 1} - 2 g _ {i} ^ {m , n - 1} + g _ {i} ^ {m - 1 , n - 1}}{2 (\delta s) ^ {2}}) \\ + \frac {q _ {i i}}{2} (g _ {i} ^ {m, n} + g _ {i} ^ {m, n - 1}) + \sum_ {j \neq i} \frac {q _ {i j}}{2} (g _ {j} ^ {m, n} + g _ {j} ^ {m, n - 1}) = 0, \end{array}\tag{3.3}
$$

where $q _ { i i } = - \textstyle \sum _ { j \neq i } q _ { i j }$ is used. For convenience, we may use the subscript notation for these constants, e.g. $g _ { i } ^ { m ^ { \prime } , \bar { n } ^ { * } } \equiv g _ { i } ( n \delta t , m \delta s ) , h _ { i } ^ { m , n } \equiv h _ { i } ( n \delta t , m \delta s ) , \varphi _ { i } ^ { m } = \varphi _ { i } ( m \delta s )$ and $\sigma _ { i } ^ { m } = \sigma _ { i } ( m \delta s )$ . We implement by explicitly treating the regime coupling terms. Replace $g _ { j } ^ { m , n - 1 }$ with $g _ { j } ^ { m , n }$ for $j \neq i$ and obtain 

$$
\begin{array}{r l r} & & {- \alpha_ {i} ^ {m} g _ {i} ^ {m - 1, n - 1} + (1 - \beta_ {i} ^ {m}) g _ {i} ^ {m, n - 1} - \gamma_ {i} ^ {m} g _ {i} ^ {m + 1, n - 1}} \\ & & {\quad = \alpha_ {i} ^ {m} g _ {i} ^ {m - 1, n} + (1 + \beta_ {i} ^ {m}) g _ {i} ^ {m, n} + \gamma_ {i} ^ {m} g _ {m + 1, n} + \delta t \sum_ {j \neq i} q _ {i j} g _ {j} ^ {m, n},} \end{array}\tag{3.4}
$$

where 

$$
\left\{ \begin{array}{l l} & \alpha_ {i} ^ {m} = \frac {\delta t}{4 \delta s} \big (\frac {(\sigma_ {i} ^ {m}) ^ {2}}{\delta s} - \varphi_ {i} ^ {m} \big), \\ & \beta_ {i} ^ {m} = - \frac {\delta t}{2} \big ((r - q _ {i i}) + \frac {(\sigma_ {i} ^ {m}) ^ {2}}{(\delta s) ^ {2}} \big), \\ & \gamma_ {i} ^ {m} = \frac {\delta t}{4 \delta s} \big (\frac {(\sigma_ {i} ^ {m}) ^ {2}}{\delta s} + \varphi_ {i} ^ {m} \big), \end{array} \right.\tag{3.5}
$$

for $i , j \in E , m = 1 , 2 , . . . , M - 1$ and $n = 1 , 2 , . . . , N - 1$ . The system to be solved backward in time is 

$$
\mathbf {M} _ {\mathrm{i}} ^ {1} \mathbf {g} _ {\mathrm{i}} ^ {\mathrm{n-1}} = \mathbf {r} _ {\mathrm{i}} ^ {\mathrm{n}},\tag{3.6}
$$

where the right-hand side is 

$$
\mathbf {r _ {i} ^ {n}} = \mathbf {M _ {i} ^ {2}} \mathbf {g _ {i} ^ {n}} + \delta t \sum_ {j \neq i} q _ {i j} \mathbf {g _ {j} ^ {n}} + \alpha_ {i} ^ {1} \left[ \begin{array}{c} g _ {i} ^ {0, n - 1} + g _ {i} ^ {0, n} \\ 0 \\ \vdots \\ 0 \end{array} \right] + \gamma_ {i} ^ {M - 1} \left[ \begin{array}{c} 0 \\ \vdots \\ 0 \\ g _ {i} ^ {M, n - 1} + g _ {i} ^ {M, n} \end{array} \right],\tag{3.7}
$$

and 

$$
\begin{array}{r l} & {\mathbf {M _ {i} ^ {1}} = \left[ \begin{array}{c c c c c c} 1 - \beta_ {i} ^ {1} & - \gamma_ {i} ^ {1} & & & & \\ - \alpha_ {i} ^ {2} & 1 - \beta_ {i} ^ {2} & - \gamma_ {i} ^ {2} & & & \\ & - \alpha_ {i} ^ {3} & 1 - \beta_ {i} ^ {3} & - \gamma_ {i} ^ {3} & & \\ & & \ddots & \ddots & \ddots & \\ & & & - \alpha_ {i} ^ {M - 2} & 1 - \beta_ {i} ^ {M - 2} & - \gamma_ {i} ^ {M - 2} \\ & & & & - \alpha_ {i} ^ {M - 1} & 1 - \beta_ {i} ^ {M - 1} \end{array} \right],} \\ & {\mathbf {M _ {i} ^ {2}} = \left[ \begin{array}{c c c c c c} 1 + \beta_ {i} ^ {1} & \gamma_ {i} ^ {1} & & & & \\ \alpha_ {i} ^ {2} & 1 + \beta_ {i} ^ {2} & \gamma_ {i} ^ {2} & & & \\ & \alpha_ {i} ^ {3} & 1 + \beta_ {i} ^ {3} & \gamma_ {i} ^ {3} & & \\ & & \ddots & \ddots & \ddots & \\ & & & \alpha_ {i} ^ {M - 2} & 1 + \beta_ {i} ^ {M - 2} & \gamma_ {i} ^ {M - 2} \\ & & & & \alpha_ {i} ^ {M - 1} & 1 + \beta_ {i} ^ {M - 1} \end{array} \right],} \\ & {\mathbf {g _ {i} ^ {n}} = \left[ g _ {i} ^ {1, n}, g _ {i} ^ {2, n}, \ldots , g _ {i} ^ {M - 1, n} \right] ^ {T}.} \end{array}\tag{3.8}
$$

(3.9) 

(3.10) 

We note that the dimension of ${ \bf { M } _ { i } ^ { 1 } }$ is independent of $m .$ , which is the number of regimes. Thus the scheme (3.6) can be computed in parallel. 

Remark 1 The futures price function (2.5) can be computed via solving the linear system (3.6) by replacing $g _ { i } ^ { m , n }$ with $f _ { i } ^ { m , n }$ , where $f _ { i } ^ { m , n } \equiv f ( t , s , i )$ , and setting $r = 0$ 

Since the investor can establish her position at anytime before the expiry, the value functions $g _ { i } ( t , s )$ must satisfy the constraint 

$$
g _ {i} (t, s) \geq h _ {i} (t, s), \quad s \geq 0, \quad 0 \leq t \leq \hat {T}, \quad i \in E,\tag{3.11}
$$

where the discrete scheme can be written as 

$$
g _ {i} ^ {m, n} \geq h _ {i} ^ {m, n}, \quad 0 \leq m \leq M, \quad 0 \leq n \leq M, \quad i \in E.\tag{3.12}
$$

Hence, at each time step $n \in \{ 1 , 2 , \ldots , N - 1 \}$ , we need to solve 

$$
\left\{ \begin{array}{c} \mathrm {M_ {i} ^ {1} g_ {i} ^ {n - 1}} \geq \mathrm {r_ {i} ^ {n}}, \\ \mathrm {g_ {i} ^ {n - 1}} \geq h _ {i} ^ {n - 1}, \\ (\mathrm {M_ {i} ^ {1} g_ {i} ^ {n - 1}} - \mathrm {r_ {i} ^ {n}}) ^ {T} (h _ {i} ^ {n - 1} - \mathrm {g_ {i} ^ {n - 1}}) = 0. \end{array} \right.\tag{3.13}
$$

To guarantee the constraint, our algorithm enforces the constraint explicitly as follows 

$$
g _ {i, n e w} ^ {m, n - 1} = \max \left\{g _ {i, o l d} ^ {m, n - 1}, h _ {i} ^ {m, n - 1} \right\}.\tag{3.14}
$$

The projected SOR method is used to solve the linear system. Notice that the constraint is enforced at the same time as the iterate $g _ { i , ( k + 1 ) } ^ { m , n - 1 }$ is calculated; the efect of the constraint is immediately felt in the calculation of $g _ { i , ( k + 1 ) } ^ { m + 1 , n - 1 } , g _ { i , ( k + 1 ) } ^ { \tilde { m + 2 } , n - 1 }$ , etc. Thus, at each time step $n ,$ the PSOR algorithm is to iterate (on k) the equations 

$$
\begin{array}{c} g _ {i, (k + 1)} ^ {1, n - 1} = \max \big \{h _ {i} ^ {1, n - 1}, g _ {i, (k)} ^ {1, n - 1} + \frac {\omega}{1 - \beta_ {i} ^ {1}} [ r _ {i} ^ {1, n} - (1 - \beta_ {i} ^ {1}) g _ {i, (k)} ^ {1, n - 1} + \gamma_ {i} ^ {1} g _ {i, (k)} ^ {2, n - 1} ] \big \}, \\ g _ {i, (k + 1)} ^ {2, n - 1} = \max \big \{h _ {i} ^ {2, n - 1}, g _ {i, (k)} ^ {2, n - 1} + \frac {\omega}{1 - \beta_ {i} ^ {2}} [ r _ {i} ^ {2, n} + \alpha_ {i} ^ {2} g _ {i, (k + 1)} ^ {1, n - 1} - (1 - \beta_ {i} ^ {2}) g _ {i, (k)} ^ {2, n - 1} + \gamma_ {i} ^ {2} g _ {i, (k)} ^ {3, n - 1} ] \big \}, \\ \vdots \\ g _ {i, (k + 1)} ^ {M - 1, n - 1} = \max \big \{h _ {i} ^ {M - 1, n - 1}, g _ {i, (k)} ^ {M - 1, n - 1} \\ + \frac {\omega}{1 - \beta_ {i} ^ {M - 1}} [ r _ {i} ^ {M - 1, n} + \alpha_ {i} ^ {M - 1} g _ {i, (k + 1)} ^ {M - 2, n - 1} - (1 - \beta_ {i} ^ {M - 1}) g _ {i, (k)} ^ {M - 1, n - 1} ] \big \}, \end{array}\tag{3.15}
$$

where k is the iteration counter and $\omega$ is the overrelaxation parameter. The iterative scheme starts from an initial point $\mathbf { g } _ { i , ( 0 ) } ^ { n }$ and proceeds until a convergence criterion is met, such as $| | \mathbf { g _ { i , ( k + 1 ) } ^ { n - 1 } } -$ $\mathbf { g _ { i , ( k ) } ^ { n - 1 } } | | < \epsilon$ , where  is a tolerance parameter. The optimal boundary $S _ { f } ( t )$ can be identified by locating the boundary that separates the regions where $g _ { i } ( t , s ) = h _ { i } ( t , s ) , { \mathrm { ~ o r ~ } } g _ { i } ( t , s ) > h _ { i } ( t , s )$ 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8fc43dfe-3031-4e95-9c13-960ce048f5af/0be53ef3e28753bc66f94090931f1b9a41ef9949e9f2c1f62625629dbea60831.jpg)



Figure 1: The futures prices in 2 regimes. Parameters: $S _ { 0 } ~ = ~ 3 0 , \sigma _ { 1 } ~ = ~ 5 . 3 3 , \sigma _ { 2 } ~ = ~ 6 . 4 2 , \tilde { \theta } _ { 1 } ~ = ~$ $1 8 . 1 6 , \tilde { \theta } _ { 2 } = 4 0 . 3 6 , \tilde { \mu } _ { 1 } = 4 . 5 5 , \tilde { \mu } _ { 2 } = 4 . 5 9 , q _ { 1 2 } = - q _ { 1 1 } = 0 . 1 , q _ { 2 1 } = - q _ { 2 2 } = 0 . 5$


## 4 Optimal Trading Strategies

In this section we provide numerical examples to further interpret the optimal trading strategies. The regime-switching CIR model is capable of generating futures curves of diferent term structures. Figure 1 displays the futures prices in two diferent regimes. The CIR model with regime swicthing generates a convex curve in regime 1 (blue), and a concave curve in regime 2 (red). In Figure 2, we illustrate the cases of optimal boundaries for futures trading under the CIR model in a two-regime market. As Figure 2a shows, optimal boundaries divide the space into three disjoint regions in each regime, which can be specified as the long region (region below $^ { 6 6 } { \mathcal { T } } ^ { 3 } )$ , short region (region above $^ { 6 6 } \mathcal { V } ^ { 3 } )$ and the waiting region (region between $^ { 6 } { \mathcal { I } } ^ { 5 }$ and $^ { 6 6 } \mathcal { V } ^ { 9 } )$ ). The subscripts of value functions index to the regimes. Assuming the investor pre-commits to “long-short” strategy, it is optimal to take a long position first if the VIX is in the long region, and then exit the market when the VIX goes up to hit optimal boundary $\ " { \mathcal { I } } ^ { \ast }$ . While if the investor adopts the “short-long” strategy, she will first short a futures and subsequently close out with a long position by the $^ { 6 6 } K ^ { 5 9 }$ and $\ " { \mathcal { U } } ^ { \prime \prime }$ boundaries in Figure 2b . In either case, our strategies confirm the intuition: “buy low and sell high”. 

Figure 2 also displays the optimal boundaries with diferent transaction costs. Without transaction costs (see left panel of Figure 2), the waiting region shrinks since the investor tends to enter and exit the market eariler, resulting in more rapid trades. In the presence of transaction costs (see right panel of Figure 2), the waiting region is widen in order to save on transaction costs. It should also be noted that as the transaction cost increases, the long boundary decreases and the short boundary increases, making the investor trade less frequently. In particular, the fast divergence near expiry indicates that the investor should not enter the market after a critical time. The intuition is that a rational investor will never initiate a position if she does not have enough time to recover at least the transaction costs. 

The $^ { 6 6 } \mathcal { P } ^ { 5 }$ boundaries in Figure 2 indicates the optimal value of VIX at which the investor should open a position. The boundary labeled as ${ } ^ {  } \mathcal { P } = \mathcal { A } ^ {  } \ ( \mathrm { r e s p . } \ { } ^ {  } \mathcal { P } = \mathcal { B } ^ {  } )$ indicates the critical value at which the investor enters the market by taking a long (resp. short) futures position. The investor should choose the “short-first” strategy if the VIX lies in the area above the ${ } ^ { 6 6 } { \mathcal { P } } = B ^ { \prime }$ boundary, whereas choose the “long-first” strategy if the VIX is lower than the ${ } ^ { 6 6 } { \mathcal { P } } = { \mathcal { A } } ^ { \prime }$ boundary. The area between the two boundaries is the region where the investor should wait for an better enter opportunity. This confirms our intuition – take a long position when the VIX is low while take a short position when the VIX is high. Similarly, the waiting region expands significantly near expiry to cover transaction costs. In other words, the investor will not enter the market unless the VIX is either very low or very high. 

Once the investor finished choosing entry strategy, she could resort the exit strategy to corresponding optimal boundaries. For example, if the investor starts by longing a futures, then the optimal exit timing to close her position is represented by the optimal boundary $^ { 6 6 } \mathcal { V } ^ { 5 }$ in Figure 2. However, if the investor’s initial position is short, then she will hold the short position until the VIX hits $\ " { \mathcal { U } } ^ { \prime \prime }$ boundary. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8fc43dfe-3031-4e95-9c13-960ce048f5af/fddf0f7cc02e453036d3427d2b474c18563c430f03c685315d91b1fa9805b694.jpg)



(a)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8fc43dfe-3031-4e95-9c13-960ce048f5af/8e55d95fcaed462a911230747b743fcb0d60673a2883985ccb8714d06e615c05.jpg)



(d)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8fc43dfe-3031-4e95-9c13-960ce048f5af/68dc8eee164a45767f2f44aff179971940e864565173d2591beceafcf97a6d43.jpg)



(b)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8fc43dfe-3031-4e95-9c13-960ce048f5af/777c5a49b6d69f01e751f693de807f40e7040be84f2c088e409f02a3c073e122.jpg)



(e)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8fc43dfe-3031-4e95-9c13-960ce048f5af/88da64ca75856dd00552b1b1bc3ff91baadc85e3bc9734b1461b25fe1197371c.jpg)



(c)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8fc43dfe-3031-4e95-9c13-960ce048f5af/c1e36c9b8d57c114a52c8a281ec31c52bfda7b456a5d97c7b1f06ba5519fb855.jpg)



(f)



Figure 2: Optimal long-short boundaries for futures trading with 2-state regime-switching model. Left panel: $c = { \hat { c } } = 0$ . Right panel: $c = \hat { c } = 0 . 0 1$ . Common parameters: ${ \hat { T } } = { \textstyle \frac { 2 2 } { 2 5 2 } } , { \bar { T } } = { \textstyle \frac { 6 6 } { 2 5 2 } }$ 2 $r = 0 . 0 5 , \sigma _ { 1 } = 5 . 3 3 , \sigma _ { 2 } = 6 . 4 2 , \theta _ { 1 } = 1 7 . 5 8 , \theta _ { 2 } = 3 9 . 5 , { \tilde { \theta } } _ { 1 } = 1 8 . 1 6 , { \tilde { \theta } } _ { 2 } = 4 0 . 3 6 , \mu _ { 1 } = 8 . 5 7 , \mu _ { 2 } = 9 , { \tilde { \mu } } _ { 1 } = 8 . 7 8 , \theta _ { 2 } = 9 . 3 6 , \mu _ { 1 } = 1 . 4 , \tilde { \mu } _ { 2 } = 9 . 3 6 , \tilde { \mu } _ { 3 } = 9 . 3 6 , \tilde { \mu } _ { 2 } = 9 . 3 6 , \tilde { \mu } _ { 3 } = 9 . 3 6 , \tilde { \mu } _ { 2 } = 9 . 3 6 , \tilde { \mu } _ { 3 } = 9 . 3 6 , \tilde { \mu } _ { 2 } = 9 . 3 6 , \tilde { \mu } _ { 3 } = 9 . 3 6 , \tilde { \mu } _ { 2 } = 9 . 3 6 , \tilde { \mu } _ { 2 } = 9 . 3 6 , \tilde { \mu } _ { 3 } = 9 . 3 6 , 0 3 , \tilde { \mu } _ { 2 } = 9 . 3 6 , 0 3 , \tilde { \mu } _ { 3 } = 9 . 3 6 , 0 3 , \tilde { \mu } _ { 2 } = 9 . 3 6 , 0 3 , \tilde { \mu } _ { 3 } = 9 . 3 6 , 0 3 , \tilde { \mu } _ { 2 } = 9 . 3 6 , 0 3 , \tilde { \mu } _ { 3 } = 9 . 3 6 , 0 3 , \tilde { \mu } _ { 2 } = 9 . 3 6 , 0 3 , \tilde { \mu } _ { 3 } = 9 . 3 6 , 0 3 , \tilde { \mu } _ { 2 } = 9 . 3 6 , 0 3 , \tilde { \mu } _ { 3 } = 9 . 3 6 , 0 3 , \tilde { \mu } _ { 2 } = 9 . 3 6 , 0 3 , \tilde { \mu } _ { 3 } = 9 . 3 6 , 0 3 , \tilde { \mu } _ { 3 } = 9 . 3 6 , 0 3 , \tilde { \mu } _ { 2 } = 9 . 3 6 , 0 3 \tilde { \mu } _  3$ $4 . 5 5 , \tilde { \mu } _ { 2 } = 4 . 5 9 , q _ { 1 2 } = - q _ { 1 1 } = 0 . 1 , q _ { 2 1 } = - q _ { 2 2 } = 0 . 5$


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8fc43dfe-3031-4e95-9c13-960ce048f5af/d349e626d9f59d6d85eb4c99dfbd813af6f881f59a582569a89c9c2918fc6eb5.jpg)



(a)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8fc43dfe-3031-4e95-9c13-960ce048f5af/1aa987ec31f38b4991c59bf779dc2faaea515ef8d4ade21f702b8bb8dc7e5007.jpg)



(b)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8fc43dfe-3031-4e95-9c13-960ce048f5af/2075f3f02ecff0beac150543d48878e5157e442fe04c1b42d201543721f2a6e3.jpg)



(c)



Figure 3: Simulated CIR paths and exercise times under 2-state regime-switching model. (a) The investor enters at $\nu _ { 1 }$ and exits at $\tau _ { 1 }$ in regime 1; enters again at $\nu _ { 2 }$ and exits at $\tau _ { 2 }$ in regime 2. (b) The investor enters at $\nu _ { 2 }$ and exits at $\tau _ { 2 }$ in regime 2 without any adjustments in regime 1. (c) The investor takes a short position at $\nu _ { 1 }$ in regime 1 but switches to a long position at $t _ { 1 2 } ( \tau _ { 1 } , \nu _ { 2 } )$ , and then liquilate her position at $\tau _ { 2 }$ in regime 2. The parameters are the same as those in Figure 2.


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8fc43dfe-3031-4e95-9c13-960ce048f5af/19ec26c5aa6fc231c75868cbf2176066641363cf2ca69ccd3bb200ee5b901603.jpg)



Table 1


<table><tr><td></td><td>In regime 1</td><td>In regime 2</td></tr><tr><td><eq>S_1^1</eq></td><td>Long</td><td>Long</td></tr><tr><td><eq>S_2^1</eq></td><td>Wait</td><td>Long</td></tr><tr><td><eq>S_3^1</eq></td><td>Short</td><td>Long</td></tr><tr><td><eq>S_4^1</eq></td><td>Short</td><td>Wait</td></tr><tr><td><eq>S_5^1</eq></td><td>Short</td><td>Short</td></tr></table>


Figure 4: Optimal boundaries for futures trading under the CIR model with 2-state regime switching. Parameters: $\begin{array} { r } { \hat { T } = \frac { 2 2 } { 2 5 2 } , T = \frac { 6 6 } { 2 5 2 } , r = 0 . 0 5 , \sigma _ { 1 } = 5 . 3 3 , \sigma _ { 2 } = 6 . 4 2 , \theta _ { 1 } = 1 7 . 5 8 , \theta _ { 2 } = 3 9 . 5 , \tilde { \theta } _ { 1 } = 3 9 8 , \theta _ { 2 } = 6 . 4 2 , \theta _ { 3 } = 5 . 7 8 , \theta _ { 4 } = 3 9 . 2 5 . \theta _ { 5 } = 5 . 5 0 8 , \theta _ { 5 } = 3 0 . 5 3 , \theta _ { 6 } = 3 0 . 5 3 \theta _ { 7 } = 3 0 8 . 5 3 \theta _ { 8 } = 3 0 . 5 3 8 , \theta _ { 8 } = 3 0 . 5 3 8 , \theta _ { 8 } = 3 0 . 5 3 8 , \theta _ { 8 } = 3 0 . 5 3 8 , \theta _ { 8 } = 3 0 . 5 3 8 8 , \theta _ { 8 } = 3 0 . 5 3 8 8 , \theta _ { 8 } = 3 0 . 5 3 8 8 \cdot \theta _ { 7 } = 3 0 . 5 3 8 8 . \theta _ { 8 } = 3 0 . 5 3 8 8 8 . \theta _ { 8 } = 3 0 . 5 3 8 8 8 8 . } \end{array}$ $1 8 . 1 6 , \tilde { \theta } _ { 2 } = 4 0 . 3 6 , \mu _ { 1 } = 8 . 5 7 , \mu _ { 2 } = 9 , \tilde { \mu } _ { 1 } = 4 . 5 5 , \tilde { \mu } _ { 2 } = 4 . 5 9 , c = \hat { c } = 0 . 0 1 , q _ { 1 2 } = - q _ { 1 1 } = 0 . 1 , q _ { 2 1 } = 0 . 1 , c = 0 . 1 ,$ $- q _ { 2 2 } = 0 . 5$


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8fc43dfe-3031-4e95-9c13-960ce048f5af/74c4124f1262db1f2eab05330caeabfd537afcd2b289b1577388ca0c0a46a830.jpg)



Table 2


<table><tr><td></td><td>In regime 1</td><td>In regime 2</td></tr><tr><td><eq>S_1^1</eq></td><td>Long</td><td>Long</td></tr><tr><td><eq>S_2^1</eq></td><td>Wait</td><td>Long</td></tr><tr><td><eq>S_3^1</eq></td><td>Wait</td><td>Wait</td></tr><tr><td><eq>S_4^1</eq></td><td>Short</td><td>Wait</td></tr><tr><td><eq>S_5^1</eq></td><td>Short</td><td>Short</td></tr></table>


Figure 5: Optimal boundaries for futures trading under the CIR model with 2-state regime switching. Parameters: $\begin{array} { r } { \hat { T } = \frac { 2 2 } { 2 5 2 } , T = \frac { 6 6 } { 2 5 2 } , r = 0 . 0 5 , \sigma _ { 1 } = 5 . 3 3 , \sigma _ { 2 } = 6 . 4 2 , \theta _ { 1 } = 3 5 . 6 , \theta _ { 2 } = 3 9 . 5 , \tilde { \theta } _ { 1 } = } \end{array}$ 35.96, $\tilde { \theta } _ { 2 } = 4 0 . 3 6 , \mu _ { 1 } = 8 . 5 7 , \mu _ { 2 } = 9 , \tilde { \mu } _ { 1 } = 4 . 5 5 , \tilde { \mu } _ { 2 } = 4 . 5 9 , c = \hat { c } = 0 . 0 1 , q _ { 1 2 } = - q _ { 1 1 } = 0 . 1 , q _ { 2 1 } = 0 . 1 , c = \hat { \mu } _ { 1 } = 0 . 0 3 , c = \hat { \mu } _ { 2 } = 0 . 0 3 , c = \hat { \mu } _ { 1 } = 0 . 0 3 , c = \hat { \mu } _ { 2 } = 0 . 0 3 , c = \hat { \mu } _ { 1 } = 0 . 0 3 , c = \hat { \mu } _ { 2 }$ $g _ { 2 2 } = 0 . 5$


To better explain our strategies, here we assume a two-state process and interpret the two regimes as a low-mean regime (regime 1) and a high-mean regime (regime 2). The regime-switching timing $t _ { 1 2 }$ indicates the shift from the low-mean regime to the high-mean regime. As shown in Figure 3a, the investor finishes the long-low-short-high tradings in both regimes. In the low-mean regime, the investor chooses to long a futures position at time $\nu _ { 1 }$ and then closes the position at $\tau _ { 1 }$ . When the regime switches at $t _ { 1 2 }$ , the VIX locates in the long region in high-mean regime. The investor should long one position immediately at $t _ { 1 2 } \left( \nu _ { 2 } \right)$ , and liquidate the position later at $\tau _ { 2 }$ according to the optimal boundaries in regime 2. Figure 3b shows another scenario. It is optimal for the investor to wait before the switch happens, since the VIX stays in the waiting region in regime 1. Then the investor would better to long a futures at $\nu _ { 2 }$ and short at $\tau _ { 2 }$ as the previous case. Another example is shown in Figure 3c. The VIX goes up to hit the short boundary $^ { 6 6 } K _ { 1 } { } ^ { , ; }$ at $\nu _ { 1 }$ in regime 1. The investor chooses to short a position and she speculates that the price will decrease. However, the regime switches at time $t _ { 1 2 } \ ( \tau _ { 1 } , \nu _ { 2 } )$ . The investor should immediately close her position and start to long one position according to the optimal boundaries $^ { 6 6 } { \mathcal { I } } _ { 2 } ^ { , 9 }$ and $^ { 6 6 } \nu _ { 2 } ^ { , 9 }$ . The investor might need to face the loss in the position switching process. In other words, there is a positive probability of losses in a finite time period. We see that the regime-switching timing $t _ { 1 2 }$ plays a key role for investor’s trading decision. 

The introduction of regime switching adds considerable complexity to the optimal trading strategies. The last three examples in Figure 3 are the simplest cases since we assume that the regime switching only happens once at $t _ { 1 2 }$ . Figure 4 and 5 show another approach to understand our models without specifying the regime-switching times. The process used here still has two states. Optimal boundaries separate the space into 5 regions. Table 1 and 2 indicate the exercises in diferent regimes by given VIX. Figure 4 shows the case of “low-mean regime vs high-mean regime”. This regime-switching case captures some sudden changes of market (such as financial crisis in 2008), which might cause extremely high volatility. Once the regime switches, the investor is expected to take the long position aggressively. We can see the long region is as large as ${ } ^ { 4 \natural } S _ { 1 } ^ { 1 } + S _ { 2 } ^ { 1 } + S _ { 3 } ^ { 1 }  \}$ in high-mean regime. It shows that the investor has to adjust her strategies based on the diferent regimes, even though the VIX still stays in the same region. Figure 5 shows two regimes with relatively closer switching means. The optimal boundaries are higher in regime 2 than in regime 1, which means that the investor intends to enter and exit the market earlier in regime 1. Moreover, in regime 1, the waiting region is $^ { 6 6 } S _ { 2 } ^ { 1 } + S _ { 3 } ^ { 1 } \mathrm { w }$ , while in regime 2, the waiting region is $^ { 6 6 } S _ { 3 } ^ { 1 } + S _ { 4 } ^ { 1 } \mathrm { w }$ $^ { 6 6 } S _ { 3 } ^ { 1 5 }$ is the common waiting region in both regimes. It implies that the investor might participate in tradings more frequently by adopting 2-regime model than single regime model. In other words, the presence of regime switching will impact investor’s trading strategies. 

From the perspective of an investor with no position, she is interested in determining the best time to enter the market. We study the optimal timing premium (see Leung and Ludkovski (2011), Leung and Liu (2012), Leung and Ludkovski (2012)), which plays a vital role in the optimal strategies. This premium expresses the benefit of waiting to enter as compared to initialize the position immediately. Precisely, the premium is defined as 

$$
L (t, s, i) := \mathcal {P} (t, s, i) - \max \{\mathcal {A} (t, s, i), \mathcal {B} (t, s, i) \}.\tag{4.1}
$$

As we can see in (4.1), the optimal stopping time for $L ( t , s , i )$ maximizes the expected discounted value from establishing the VIX futures position. Figure 6 shows that $\mathcal { P }$ dominates A and B. We also note that $\mathcal { P } = \mathcal { A }$ when the VIX is low and $\mathcal { P } = B$ when the VIX is high in each regime. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8fc43dfe-3031-4e95-9c13-960ce048f5af/4933047e49ecfb3e46a596f9565c474e8dc9fb523ca2ac59096140ed6f90391f.jpg)



(a)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8fc43dfe-3031-4e95-9c13-960ce048f5af/0c1ddf188bf92523a2707980a6dfc72c3d63ee508655ac1ca7c2c0773c49b6d6.jpg)



(b)



Figure 6: The value functions P, A, and B in 2 regimes are plotted against the VIX at time 0. The parameters are the same as those in Figure 2 .


## 5 Conclusion

We extend the optimal VIX futures trading problems under a regime-switching model. This model allows the investor to capture the structural changes on the market. Numerical method is developed to solve these coupled system of variational inequalities that govern the value functions. Accounting for the timing options as well as the option to choose between a long or short position, we find that it is optimal to delay market entry, as compared to the case of committing to either go long or short a priori. By introduce of regime-switching mechanism, it is noted that investor should modify her trading strategies correspondingly to regime-switching timings. The strategies and numerical method introduced in this paper can also be applied to other derivatives. 

## References



Brennan, M. J. and Schwartz, E. S. (1990). Arbitrage in stock index futures. Journal of Business, 63(1):S7–S31. 





Bufington, J. and Elliott, R. J. (2002). American options with regime switching. International Journal of Theoretical and Applied Finance, 5:497–514. 





Cartea, A., Jaimungal, S., and Penalva, J. (2015). Algorithmic and High-Frequency Trading. Cambridge University Press, Cambridge, England. 





Dai, M., Zhong, Y., and Kwok, Y. K. (2011). Optimal arbitrage strategies on stock index futures under position limits. Journal of Futures Markets, 31(4):394–406. 





Dotsis, G., Psychoyios, D., and Skiadopoulos, G. (2007). An empirical comparison of continuoustime models of implied volatility indices. Journal of Banking & Finance, 31(12):3584–3603. 





Elliott, R. J., Siu, T. K., and Chan, L. (2008). A pde approach for risk measures for derivatives with regime switching. Annals of Finance, 4(1):55–74. 





Gr¨ubichler, A. and Longstaf, F. (1996). Valuing futures and options on volatility. Journal of Banking and Finance, 20(6):985–1001. 





Guo, X. (2001). An explicit solution to an optimal stopping problem with regime switching. Journal of Applied Probability, pages 464–481. 





Khaliq, A. Q. and Liu, R. (2009). New numerical scheme for pricing american option with regimeswitching. International Journal of Theoretical and Applied Finance, 12(03):319–340. 





Le, H. and Wang, C. (2010). A finite time horizon optimal stopping problem with regime switching. SIAM Journal on Control and Optimization, 48(8):5193–5213. 





Leung, T. (2010). A Markov-modulated stochastic control problem with optimal multiple stopping with application to finance. In 49th IEEE Conference on Decision and Control (CDC), pages 559–566. 





Leung, T., Li, J., Li, X., and Wang, Z. (2016). Speculative futures trading under mean reversion. Asia-Pacific Financial Markets, pages 1–24. Published online. 





Leung, T. and Li, X. (2015). Optimal mean reversion trading with transaction costs and stop-loss exit. International Journal of Theoretical & Applied Finance, 18(3):15500. 





Leung, T. and Li, X. (2016). Optimal Mean Reversion Trading: Mathematical Analysis and Practical Applications. Modern Trends in Financial Engineering. World Scientific, Singapore. 





Leung, T., Li, X., and Wang, Z. (2014). Optimal starting–stopping and switching of a CIR process with fixed costs. Risk and Decision Analysis, 5(2):149–161. 





Leung, T., Li, X., and Wang, Z. (2015). Optimal multiple trading times under the exponential OU model with transaction costs. Stochastic Models, 31(4):554–587. 





Leung, T. and Liu, P. (2012). Risk premia and optimal liquidation of credit derivatives. International Journal of Theoretical & Applied Finance, 15(8):1250059. 





Leung, T. and Ludkovski, M. (2011). Optimal timing to purchase options. SIAM Journal on Financial Mathematics, 2(1):768–793. 





Leung, T. and Ludkovski, M. (2012). Accounting for risk aversion in derivatives purchase timing. Mathematics & Financial Economics, 6(4):363–386. 





Leung, T. and Shirai, Y. (2015). Optimal derivative liquidation timing under path-dependent risk penalties. Journal of Financial Engineering, 2(1):1550004. 





Leung, T. and Yamazaki, K. (2013). American step-up and step-down credit default swaps under L´evy models. Quantitative Finance, 13(1):137–157. 





Menc´ıa, J. and Sentana, E. (2013). Valuation of VIX derivatives. Journal of Financial Economics, 108(2):367–391. 





Sircar, R. and Papanicolaou, A. (2014). A regime-switching Heston model for VIX and S&P 500 implied volatilities. Quantitative Finance, 14(10):1811–1827. 





Stepanek, C. (2015). Comparison of commodity future pricing approaches with cointegration techniques. Journal of Financial Engineering, 2(01):1550002. 





Wang, Z. and Daigler, R. T. (2011). The performance of VIX option pricing models: Empirical evidence beyond simulation. Journal of Futures Markets, 31(3):251–281. 





Whaley, R. E. (2000). The investor fear gauge. The Journal of Portfolio Management, 26(3):12–17. 





Wilmott, P., Howison, S., and Dewynne, J. (1995). The Mathematics of Financial Derivatives: A Student Introduction. Cambridge University Press, 1st edition. 





Yao, D. D., Zhang, Q., and Zhou, X. Y. (2006). A regime-switching model for European options. In Stochastic processes, optimization, and control theory: applications in financial engineering, queueing networks, and manufacturing systems, pages 281–300. Springer. 





Zhang, J. E. and Zhu, Y. (2006). VIX futures. Journal of Futures Markets, 26(6):521–531. 

