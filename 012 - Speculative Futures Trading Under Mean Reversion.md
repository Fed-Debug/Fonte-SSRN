# Speculative Futures Trading under Mean Reversion*

Tim Leung $^{\dagger\ddagger}$ Jiao Li $^{\S}$ Xin Li $^{\P}$ Zheng Wang $^{\|}$ 

November 25, 2015 

## Abstract

This paper studies the problem of trading futures with transaction costs when the underlying spot price is mean-reverting. Specifically, we model the spot dynamics by the Ornstein-Uhlenbeck (OU), Cox-Ingersoll-Ross (CIR), or exponential Ornstein-Uhlenbeck (XOU) model. The futures term structure is derived and its connection to futures price dynamics is examined. For each futures contract, we describe the evolution of the roll yield, and compute explicitly the expected roll yield. For the futures trading problem, we incorporate the investor's timing option to enter or exit the market, as well as a chooser option to long or short a futures upon entry. This leads us to formulate and solve the corresponding optimal double stopping problems to determine the optimal trading strategies. Numerical results are presented to illustrate the optimal entry and exit boundaries under different models. We find that the option to choose between a long or short position induces the investor to delay market entry, as compared to the case where the investor pre-commits to go either long or short. 

Keywords: optimal stopping, mean reversion, futures trading, roll yield, variational inequality  
JEL Classification: C41, G11, G13 

Mathematics Subject Classification (2010): 60G40, 62L15, 91G20, 91G80 

## 1 Introduction

Futures are an integral part of the universe of derivatives. In 2014, the total number of futures and options contracts traded on exchanges worldwide rose 1.5% to 21.87 billion from 21.55 billion in 2013, with futures contracts alone accounting for 12.17 billion of these contracts. The CME group and Intercontinental Exchange are the two largest futures and options exchanges. The 2014 combined trading volume of CME group with its subsidiary exchanges, Chicago Mercantile Exchange, Chicago Board of Trade and New York Mercantile Exchange was 3.44 billion contracts, while Intercontinental Exchange had a volume of 2.28 billion contracts. $^{1}$ 

A futures is a contract that requires the buyer to purchase (seller to sell) a fixed quantity of an asset, such as a commodity, at a fixed price to be paid for on a pre-specified future date. Commonly traded on exchanges, there are futures written on various underlying assets or references, including commodities, interest rates, equity indices, and volatility indices. Many futures stipulate physical delivery of the underlying asset, with notable examples of agricultural, energy, and metal futures. However, some, like the VIX futures, are settled in cash. 

Futures are often used as a hedging instrument, but they are also popular among speculative investors. In fact, they are seldom traded with the intention of holding it to maturity as less than 1% of futures traded ever reach physical delivery. $^{2}$ This motivates the question of optimal timing to trade a futures. 

In this paper, we investigate the speculative trading of futures under mean-reverting spot price dynamics. Mean reversion is commonly observed for the spot price in many futures markets, ranging from commodities and interest rates to currencies and volatility indices, as studied in many empirical studies (see, among others, Bessembinder et al. (1995), Irwin et al. (1996), Schwartz (1997), Casassus and Collin-Dufresne (2005), Geman (2007), Bali and Demirtas (2008), Wang and Daigler (2011)). For volatility futures as an example, Grübichler and Longstaff (1996) and Zhang and Zhu (2006) model the S&P500 volatility index (VIX) by the Cox-Ingersoll-Ross (CIR) process and provide a formula for the futures price. We start by deriving the price functions and dynamics of the futures under the Ornstein-Uhlenbeck (OU), CIR, and exponential OU (XOU) models. Futures prices are computed under the risk-neutral measure, but its evolution over time is described by the historical measure. Thus, the investor's optimal timing to trade depends on both measures. 

Moreover, we incorporate the investor's timing option to enter and subsequently exit the market. Before entering the market, the investor faces two possible strategies: long or short a futures first, then close the position later. In the first strategy, an investor is expected to establish the long position when the price is sufficiently low, and then exits when the price is high. The opposite is expected for the second strategy. In both cases, the presence of transaction costs expands the waiting region, indicating the investor's desire for better prices. In addition, the waiting region expands drastically near expiry since transaction costs discourage entry when futures is very close to maturity. Finally, the main feature of our trading problem approach is to combine these two related problems and analyze the optimal strategy when an investor has the freedom to choose between either a long-short or a short-long position. Among our results, we find that when the investor has the right to choose, she delays market entry to wait for better prices compared to the individual standalone problems. 

Our model is a variation of the theoretical arbitrage model proposed by Dai et al. (2011), who also incorporate the timing options to enter and exit the market, as well as the choice between opposite positions upon entry. Their sole underlying traded process is the stochastic basis representing the difference between the index and futures values, which is modeled by a Brownian bridge. In an earlier study, Brennan and Schwartz (1990) formulate a similar optimal stopping problem for trading futures where the underlying basis is a Brownian bridge. In comparison to these two models, we model directly the spot price process, which allows for calibration of futures prices and provide a no-arbitrage link between the (risk-neutral) pricing and (historical) trading problems, as opposed to a priori assuming the existence of arbitrage opportunities, and modeling the basis that is neither calibrated nor shown to be consistent with the futures curves. A similar timing strategy for pairs trading has been studied by Cartea et al. (2015) as an extension of the buy-low-sell-high strategy used in Leung and Li (2015). 

In addition, we study the distribution and dynamics of roll yield, an important concept in futures trading. Following the literature and industry practice, we define roll yield as the difference between changes in futures price and changes in the underlying price (see e.g. Moskowitz et al. (2012), Gorton et al. (2013)). For traders, roll yield is a useful gauge for deciding to invest in the spot asset or associated futures. In essence, roll yield defined herein represents the net cost and/or benefit of owning futures over the spot asset. Therefore, even for an investor who trades futures only, the corresponding roll yield is a useful reference and can affect her trading decisions. 

The rest of the paper is structured as follows. Section 2 summarizes the futures prices and term structures under mean reversion. We discuss the concept of roll yield in Section 3. In Section 4, we formulate and numerically solve the optimal double stopping problems for futures trading. Our numerical algorithm is described in the Appendix. 

## 2 Futures Prices and Term Structures

Throughout this paper, we consider futures that are written on an asset whose price process is mean-reverting. In this section, we discuss the pricing of futures and their term structures under different spot models. 

## 2.1 OU and CIR Spot Models

We begin with two mean-reverting models for the spot price S, namely, the OU and CIR models. As we will see, they yield the same price function for the futures contract. To start, suppose that the spot price evolves according to the OU model: 

$$
d S _ {t} = \mu (\theta - S _ {t}) d t + \sigma d B _ {t},
$$

where $\mu,\sigma>0$ are the speed of mean reversion and volatility of the process respectively. $\theta\in R$ is the long run mean and B is a standard Brownian motion under the historical measure P. 

To price futures, we assume a re-parametrized OU model for the risk-neutral spot price dynamics. Hence, under the risk-neutral measure Q, the spot price follows 

$$
d S _ {t} = \tilde {\mu} (\tilde {\theta} - S _ {t}) d t + \sigma d B _ {t} ^ {\mathbb {Q}},
$$

with constant parameters $\tilde{\mu}, \sigma > 0$ , and $\tilde{\theta} \in R$ . This is again an OU process, albeit with a different long-run mean $\tilde{\theta}$ and speed of mean reversion $\tilde{\mu}$ under the risk-neutral measure. This involves a change of measure that connects the two Brownian motions, as described by 

$$
d B _ {t} ^ {\mathbb {Q}} = d B _ {t} + \frac {\mu (\theta - S _ {t}) - \tilde {\mu} (\tilde {\theta} - S _ {t})}{\sigma} d t.
$$

Throughout, futures prices are computed the same as forward prices, and we do not distinguish between the two prices (see Cox et al. (1981); Brennan and Schwartz (1990)). As such, the price of a futures contract with maturity T is given by 

$$
f _ {t} ^ {T} \equiv f (t, S _ {t}; T) := \mathbb {E} ^ {\mathbb {Q}} \{S _ {T} | S _ {t} \} = (S _ {t} - \tilde {\theta}) e ^ {- \tilde {\mu} (T - t)} + \tilde {\theta}, \quad t \leq T.\tag{2.1}
$$

Note that the futures price is a deterministic function of time and the current spot price. 

We now consider the CIR model for the spot price: 

$$
d S _ {t} = \mu (\theta - S _ {t}) d t + \sigma \sqrt {S _ {t}} d B _ {t},\tag{2.2}
$$

where $\mu,\theta,\sigma>0$ , and B is a standard Brownian motion under the historical measure P. Under the risk-neutral measure Q, 

$$
d S _ {t} = \tilde {\mu} (\tilde {\theta} - S _ {t}) d t + \sigma \sqrt {S _ {t}} d B _ {t} ^ {\mathbb {Q}},\tag{2.3}
$$

where $\mu,\theta>0$ , and $B^{Q}$ is a Q-standard Brownian motion. In both SDEs, (2.2) and (2.3), we require $2\mu\theta\geq\sigma^{2}$ and $2\tilde{\mu}\tilde{\theta}\geq\sigma^{2}$ (Feller condition) so that the CIR process stays positive. 

The two Brownian motions are related by 

$$
d B _ {t} ^ {\mathbb {Q}} = d B _ {t} + \frac {\mu (\theta - S _ {t}) - \tilde {\mu} (\tilde {\theta} - S _ {t})}{\sigma \sqrt {S _ {t}}} d t,
$$

which preserves the CIR model, up to different parameter values across two measures. 

The CIR terminal spot price $S_{T}$ admits the non-central Chi-squared distribution and is positive, whereas the OU spot price is normally distributed. Nevertheless, the futures price under the CIR model admits the same functional form as in the OU case (see (2.1)): 

$$
f _ {t} ^ {T} = (S _ {t} - \tilde {\theta}) e ^ {- \tilde {\mu} (T - t)} + \tilde {\theta}, \quad t \leq T.
$$

(2.4) 

Proposition 1 Under the OU or CIR spot model, the futures curve is (i) upward-sloping and concave if the current spot price $S_{0} < \tilde{\theta}$ , (ii) downward-sloping and convex if $S_{0} > \tilde{\theta}$ . 

Proof. We differentiate (2.4) with respect to T to get the derivatives: 

$$
\frac {\partial f _ {0} ^ {T}}{\partial T} = - \tilde {\mu} (S _ {0} - \tilde {\theta}) e ^ {- \tilde {\mu} T} \lessgtr 0 \quad \text {and} \quad \frac {\partial^ {2} f _ {0} ^ {T}}{\partial T ^ {2}} = \tilde {\mu} ^ {2} (S _ {0} - \tilde {\theta}) e ^ {- \tilde {\mu} T} \gtrless 0,
$$

for $S_0 \gtrless \tilde{\theta}$ . Hence, we conclude. 

Remark 2 The futures price formula (2.4) holds more generally for other mean-reverting models with risk-neutral spot dynamics of the form: 

$$
d S _ {t} = \tilde {\mu} (\tilde {\theta} - S _ {t}) d t + \sigma (S _ {t}) d B _ {t} ^ {\mathbb {Q}},
$$

where $\sigma (\cdot)$ is a deterministic function such that $\mathbb{E}^{\mathbb{Q}}\{\int_0^T\sigma (S_t)^2 dt\} < \infty$ 

Under the OU model, the futures satisfies the following SDE under the historical measure P: 

$$
d f _ {t} ^ {T} = \left[ (f _ {t} ^ {T} - \tilde {\theta}) (\tilde {\mu} - \mu) + \mu (\theta - \tilde {\theta}) e ^ {- \tilde {\mu} (T - t)} \right] d t + \sigma e ^ {- \tilde {\mu} (T - t)} d B _ {t}.\tag{2.5}
$$

If the spot follows a CIR process, then the futures prices follows 

$$
d f _ {t} ^ {T} = \left[ (f _ {t} ^ {T} - \tilde {\theta}) (\tilde {\mu} - \mu) + \mu (\theta - \tilde {\theta}) e ^ {- \tilde {\mu} (T - t)} \right] d t + \sigma e ^ {- \tilde {\mu} (T - t)} \sqrt {(f _ {t} ^ {T} - \tilde {\theta}) e ^ {\tilde {\mu} (T - t)} + \tilde {\theta}} d B _ {t}.\tag{2.6}
$$

Notice that the same drift appears in both $(2.5)$ and $(2.6)$ . Alternatively, we can express the drift in terms of the spot price as 

$$
e ^ {- \tilde {\mu} (T - t)} (\mu (\theta - S _ {t}) - \tilde {\mu} (\tilde {\theta} - S _ {t})).
$$

This involves the difference between the mean-reverting drifts of the spot price under the historical measure P and the risk-neutral measure Q. Therefore, the drift of the futures price SDE is positive when the drift of the spot price under P is greater than that under Q, i.e. 

$$
\mu (\theta - S _ {t}) > \tilde {\mu} (\tilde {\theta} - S _ {t}),
$$

and vice versa. 

Now, consider an investor with a long position in a single futures contract, she wishes to close out the position and is interested in determining the best time to short. We consider the delayed liquidation premium, which was introduced in Leung and Shirai (2015) for equity options. This premium expresses the benefit of waiting to liquidate as compared to closing the position immediately. Precisely, the delayed liquidation premium is defined as 

$$
L (t, s) := \sup _ {\tau \in \mathcal {T} _ {t, T}} \mathbb {E} _ {t, s} \bigl \{e ^ {- r (\tau - t)} (f (\tau , S _ {\tau}; T) - c) \bigr \} - (f (t, s; T) - c),\tag{2.7}
$$

where $T_{t,T}$ is the set of all stopping times, with respect to the filtration generated by S, and c is the transaction cost. As we can see in (2.7), the optimal stopping time for $L(t,s)$ , denoted by $\tau^{*}$ , maximizes the expected discounted value from liquidating the futures. 

Proposition 3 Let $t \in [0, T]$ be the current time, and define the function 

$$
G (u, s) := e ^ {- \tilde {\mu} (u - t)} (\mu (\theta - s) + (r - \tilde {\mu}) (\tilde {\theta} - s)) + r (c - \tilde {\theta}).
$$

Under the OU spot model, if $G(u,s) \geq 0$ , $\forall(u,s) \in [t,T] \times \mathbb{R}$ , then it is optimal to hold the futures contract till expiry, namely, $\tau^{*} = T$ in (2.7). If $G(u,s) < 0$ , $\forall(u,s) \in [t,T] \times \mathbb{R}$ , then it is optimal to liquidate immediately, namely, $\tau^{*} = t$ . The same holds under the CIR model with $G(u,s)$ defined over $[t,T] \times R_{+}$ . 

Proof. Applying Ito's formula to the process of $e^{-rt}(f_t^T - c)$ and taking expectation, we can express (2.7) as 

$$
L (t, s) = \sup _ {\tau \in \mathcal {T} _ {t, T}} \mathbb {E} _ {t, s} \left\{\int_ {t} ^ {\tau} e ^ {- r (u - t)} \left[ e ^ {- \tilde {\mu} (u - t)} (\mu (\theta - S _ {u}) + (r - \tilde {\mu}) (\tilde {\theta} - S _ {u})) + r (c - \tilde {\theta}) \right] d u \right\}.\tag{2.8}
$$

Therefore, if $G(u,s)$ (the integrand in (2.8)) is positive, $\forall(u,s) \in [t,T] \times \mathbb{R}$ , then the delayed liquidation premium can be maximized by choosing $\tau^{*} = T$ , which is the largest stopping time. Conversely, if $G < 0 \forall(u,s) \in [t,T] \times \mathbb{R}$ , then it is optimal to take $\tau^{*} = t$ in (2.8). Note that if $G = 0 \forall(u,s) \in [t,T] \times \mathbb{R}$ , then the delayed liquidation premium is zero, and the investor is indifferent toward when to liquidate. ■ 

## 2.2 Exponential OU Spot Model

Under the exponential OU (XOU) model, the spot price follows the SDE: 

$$
d S _ {t} = \mu (\theta - \ln (S _ {t})) S _ {t} d t + \sigma S _ {t} d B _ {t},\tag{2.9}
$$

with positive parameters $(\mu,\theta,\sigma)$ , and standard Brownian motion B under the historical measure P. For pricing futures, we assume that the risk-neutral dynamics of S satisfies 

$$
d S _ {t} = \tilde {\mu} (\tilde {\theta} - \ln (S _ {t})) S _ {t} d t + \sigma S _ {t} d B _ {t} ^ {\mathbb {Q}},
$$

where $\tilde{\mu},\tilde{\theta} >0$ , and $B^{\mathbb{Q}}$ is a standard Brownian motion under the risk-neutral measure $\mathbb{Q}$ . For a futures contract written on $S$ with maturity $T$ , its price at time $t$ is given by 

$$
f _ {t} ^ {T} = \exp \left(e ^ {- \tilde {\mu} (T - t)} \ln (S _ {t}) + (1 - e ^ {- \tilde {\mu} (T - t)}) (\tilde {\theta} - \frac {\sigma^ {2}}{2 \tilde {\mu}}) + \frac {\sigma^ {2}}{4 \tilde {\mu}} (1 - e ^ {- 2 \tilde {\mu} (T - t)})\right).\tag{2.10}
$$

Consequently, the dynamics of the futures price under the historical measure P is given as 

$$
\begin{array}{r l} & {d f _ {t} ^ {T} = \bigg [ \bigg (\ln (f _ {t} ^ {T}) + (e ^ {- \tilde {\mu} (T - t)} - 1) (\tilde {\theta} - \frac {\sigma^ {2}}{2 \tilde {\mu}}) + \frac {\sigma^ {2}}{4 \tilde {\mu}} (e ^ {- 2 \tilde {\mu} (T - t)} - 1) \bigg) (\tilde {\mu} - \mu)} \\ & {\qquad + e ^ {- \tilde {\mu} (T - t)} (\mu \theta - \tilde {\mu} \tilde {\theta}) \bigg ] f _ {t} ^ {T} d t + \sigma e ^ {- \tilde {\mu} (T - t)} f _ {t} ^ {T} d B _ {t}.} \end{array}\tag{2.11}
$$

By rearranging the first term in $(2.11)$ , the drift of the futures price SDE is positive iff 

$$
f _ {t} ^ {T} > \exp \left[ \frac {e ^ {- \tilde {\mu} (T - t)} (\tilde {\mu} \tilde {\theta} - \mu \theta)}{\tilde {\mu} - \mu} - (e ^ {- \tilde {\mu} (T - t)} - 1) (\tilde {\theta} - \frac {\sigma^ {2}}{2 \tilde {\mu}}) - \frac {\sigma^ {2}}{4 \tilde {\mu}} (e ^ {- 2 \tilde {\mu} (T - t)} - 1) \right],
$$

or equivalently in terms of the spot price, 

$$
S _ {t} > \exp \left(\frac {\tilde {\mu} \tilde {\theta} - \mu \theta}{\tilde {\mu} - \mu}\right).\tag{2.12}
$$

In particular, if $\tilde{\theta} = \theta$ , condition (2.12) reduces to $\log S_{t} > \theta$ . Intuitively, since the futures price must converge to the spot price at maturity, the futures price tends to rise to approach the spot price when the spot price is high, as observed in this condition. 

We now consider the delayed liquidation premium defined in (2.7) but under the XOU spot model. Applying Ito's formula, we express the optimal liquidation premium as 

$$
L (t, s) = \sup _ {\tau \in \mathcal {T} _ {t, T}} \mathbb {E} _ {t, s} \left\{\int_ {t} ^ {\tau} e ^ {- r (u - t)} \widetilde {G} (u, S _ {u}) d u \right\},\tag{2.13}
$$

where 

$$
\begin{array}{l} \widetilde {G} (u, s) := \Big \{r + \Big [ \mu (\theta - \ln (s)) - \tilde {\mu} (\tilde {\theta} - \ln (s)) \Big ] e ^ {- \tilde {\mu} (u - t)} \Big \} \\ \qquad \times \exp \left(e ^ {- \tilde {\mu} (u - t)} \ln (s) + (1 - e ^ {- \tilde {\mu} (u - t)}) (\tilde {\theta} - \frac {\sigma^ {2}}{2 \tilde {\mu}}) + \frac {\sigma^ {2}}{4 \tilde {\mu}} (1 - e ^ {- 2 \tilde {\mu} (u - t)})\right) - r c. \end{array}\tag{2.14}
$$

By inspecting the premium definition, we obtain the condition under which immediate liquidation or waiting till maturity is optimal. The proof is identical to that of Proposition 3, so we omit it. 

Proposition 4 Let $t \in [0,T]$ be the current time. Under the XOU spot model, if $\widetilde{G}(u,s) \geq 0$ , $\forall (u,s) \in [t,T] \times \mathbb{R}_{+}$ , then holding till maturity ( $\tau^{*} = T$ ) is optimal for (2.13). If $\widetilde{G}(u,s) < 0$ , $\forall (u,s) \in [t,T] \times \mathbb{R}_{+}$ , then immediate liquidation ( $\tau^{*} = t$ ) is optimal for (2.13). 

Next, we summarize the term structure of futures under the XOU spot model. 

Proposition 5 Under the XOU spot model, the futures curve is 

(i) downward-sloping and convex if 

$$
\ln S _ {0} > \tilde {\theta} - \frac {\sigma^ {2}}{2 \tilde {\mu}} (1 - e ^ {- \tilde {\mu} T}) + \left(\frac {e ^ {2 \tilde {\mu} T}}{4} + \frac {\sigma^ {2}}{2 \tilde {\mu}}\right) ^ {\frac {1}{2}} - \frac {e ^ {\tilde {\mu} T}}{2},
$$

(ii) downward-sloping and concave if 

$$
\tilde {\theta} - \frac {\sigma^ {2}}{2 \tilde {\mu}} (1 - e ^ {- \tilde {\mu} T}) <   \ln S _ {0} <   \tilde {\theta} - \frac {\sigma^ {2}}{2 \tilde {\mu}} (1 - e ^ {- \tilde {\mu} T}) + \left(\frac {e ^ {2 \tilde {\mu} T}}{4} + \frac {\sigma^ {2}}{2 \tilde {\mu}}\right) ^ {\frac {1}{2}} - \frac {e ^ {\tilde {\mu} T}}{2},
$$

(iii) upward-sloping and concave if 

$$
\tilde {\theta} - \frac {\sigma^ {2}}{2 \tilde {\mu}} (1 - e ^ {- \tilde {\mu} T}) - \left(\frac {e ^ {2 \tilde {\mu} T}}{4} + \frac {\sigma^ {2}}{2 \tilde {\mu}}\right) ^ {\frac {1}{2}} - \frac {e ^ {\tilde {\mu} T}}{2} <   \ln S _ {0} <   \tilde {\theta} - \frac {\sigma^ {2}}{2 \tilde {\mu}} (1 - e ^ {- \tilde {\mu} T}),
$$

and 

(iv) upward-sloping and convex if 

$$
\ln S _ {0} <   \tilde {\theta} - \frac {\sigma^ {2}}{2 \tilde {\mu}} (1 - e ^ {- \tilde {\mu} T}) - \left(\frac {e ^ {2 \tilde {\mu} T}}{4} + \frac {\sigma^ {2}}{2 \tilde {\mu}}\right) ^ {\frac {1}{2}} - \frac {e ^ {\tilde {\mu} T}}{2}.
$$

Proof. Direct differentiation of $f_{0}^{T}$ yields that 

$$
\frac {\partial f _ {0} ^ {T}}{\partial T} = \left[ \tilde {\mu} (\tilde {\theta} - \frac {\sigma^ {2}}{2 \tilde {\mu}} - \ln S _ {0}) e ^ {- \tilde {\mu} T} + \frac {\sigma^ {2}}{2} e ^ {- 2 \tilde {\mu} T} \right] f _ {0} ^ {T},
$$

and 

$$
\begin{array}{r l} & {\frac {\partial^ {2} f _ {0} ^ {T}}{\partial T ^ {2}} = \bigg [ \tilde {\mu} ^ {2} e ^ {- 2 \tilde {\mu} T} (\tilde {\theta} - \frac {\sigma^ {2}}{2 \tilde {\mu}} - \ln S _ {0}) ^ {2} + (\tilde {\mu} \sigma^ {2} e ^ {- 3 \tilde {\mu} T} - \tilde {\mu} ^ {2} e ^ {- \tilde {\mu} T}) (\tilde {\theta} - \frac {\sigma^ {2}}{2 \tilde {\mu}} - \ln S _ {0})} \\ & {\qquad + \frac {\sigma^ {4}}{4} e ^ {- 4 \tilde {\mu} T} - \sigma^ {2} \tilde {\mu} e ^ {- 2 \tilde {\mu} T} \bigg ] f _ {0} ^ {T}.} \end{array}
$$

The results are obtained by analyzing the signs of the first and second order derivatives. ■ 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/2e2b697a-fbe5-4172-a93e-0557b18d1a50/ad8f686282e047b8ae46c739ce365d71d954b0746d2666ee813a160101919996.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/2e2b697a-fbe5-4172-a93e-0557b18d1a50/eb8e8d70a67d1ca11db8227f56401443edc2bd702362c71b70fdd164c0548f36.jpg)



Figure 1: (Left) VIX futures historical prices on Nov 20, 2008 with the current VIX value at 80.86. The days to expiration range from 26 to 243 days (Dec–Jul contracts). Calibrated parameters: $\tilde{\mu}=4.59,\tilde{\theta}=40.36$ under the CIR/OU model, or $\tilde{\mu}=3.25,\tilde{\theta}=3.65,\sigma=0.15$ under the XOU model. (Right) VIX futures historical prices on Jul 22, 2015 with the current VIX value at 12.12. The days to expiration ranges from 27 days to 237 days (Aug–Mar contracts). Calibrated parameters: $\tilde{\mu}=4.55,\tilde{\theta}=18.16$ under the CIR/OU model, or $\tilde{\mu}=4.08,\tilde{\theta}=3.06,\sigma=1.63$ under the XOU model.


Figure 1 displays two characteristically different term structures observed in the VIX futures market. These futures, written on the CBOE Volatility Index (VIX) are traded on the CBOE Futures Exchange. As the VIX measures the 1-month implied volatility calculated from the prices of S&P 500 options, VIX futures provide exposure to the market's volatility. We plot the VIX futures prices during the recent financial crisis on November 20, 2008 (left), and on a post-crisis date, July 22, 2015 (right), along with the calibrated futures curves under the OU/CIR model and XOU model. In the calibration, the model parameter values are chosen to minimize the sum of squared errors between the model and observed futures prices. 

The OU/CIR/XOU model generates a decreasing convex curve for November 20, 2008 (left), and an increasing concave curve for July 22, 2015 (right), and they all fit the observed futures prices very well. The former term structure starts with a very high spot price of 80.86 with a calibrated risk-neutral long-run mean $\tilde{\theta} = 40.36$ under the OU/CIR model, suggesting that the market's expectation of falling market volatility. In contrast, we infer from the term structure on July 25, 2015 that the market expects the VIX to raise from the current spot value of 12.12 to be closer to $\tilde{\theta} = 18.16$ . 

## 3 Roll Yield

By design, the value of a futures contract converges to the spot price as time approaches maturity. If the futures market is in backwardation, the futures price increases to reach the spot price at expiry. In contrast, when the market is in contango, the futures price tends to decrease to the spot price. For an investor with a long futures position, the return is positive in a backwardation market, and negative in a contango market. An investor can long the front-month contract, then short it at or before expiry, and simultaneously go long the next-month contract. This rolling strategy that involves repeatedly rolling an expiring contract into a new one is commonly adopted during backwardation, while its opposite is often used in a contango market. Backwardation and contango phenomena are widely observed in the energy commodities and volatility futures markets. 

More generally, both the futures and spot prices vary over time. If the spot price increases/decreases, the futures price will also end up higher/lower. This leads us to consider the difference between the futures and spot returns, defined as the change in values without dividing by the initial value. $^{3}$ Let $0 \leq t_{1} < t_{2} \leq T$ . We denote the roll yield over the period $[t_{1}, t_{2}]$ associated with a single futures contract with maturity T by 

$$
\mathcal {R} (t _ {1}, t _ {2}, T) := (f _ {t _ {2}} ^ {T} - f _ {t _ {1}} ^ {T}) - (S _ {t _ {2}} - S _ {t _ {1}}).\tag{3.1}
$$

In other words, roll yield here is the change in the futures price that is not accounted for by the change in spot price. It represents the net benefits and/or costs of owning futures rather than the underlying asset itself. 

This notion of roll yield is the same as that in Moskowitz et al. (2012) where the relationship between roll yield and futures returns is studied. Gorton et al. (2013) treat roll yield as the same as futures basis, which means a negative roll yield signifies a market in contango and a positive roll yield is equivalent to backwardation. In our set-up, if one always holds a futures contract to maturity, then roll yield is the same as futures basis. Therefore, the definition of roll yield in Gorton et al. (2013) is a special case of ours. In particular, if $t_{2} = T$ , then the roll yield reduces to the price difference $(S_{t_{1}} - f_{t_{1}}^{T})$ . Furthermore, observe that if $S_{t_{2}} = S_{t_{1}}$ then roll yield becomes merely the change in futures price. 

A closely related concept is the S&P-GSCI roll yield. S&P-GSCI carries out rolling of the underlying futures contracts once each month, from the fifth to the ninth business day. On each day, 20% of the current portfolio is rolled over, in a process commonly known as the Goldman roll. The S&P-GSCI roll yield for each commodity is defined as the difference between the average purchasing price of the new futures contracts and the average selling price of the old futures contracts. In essence, it is an indicator of the sign of the slope of the futures term structure. In comparison to the S&P-GSCI index, our definition accounts for the changes of spot price over time. 

Next, we examine the cumulative roll yield across maturities. Denote by $T_{1} < T_{2} < T_{3} < \ldots$ the maturities of futures contracts. We roll over at every $T_{i}$ by replacing the contract expiring at $T_{i}$ with a new contract that expires at $T_{i+1}$ . Let $i(t) := \min\{i : T_{i-1} < t \leq T_{i}\}$ , and $i(0) = 1$ . Then the roll yield up to time $t > T_{1}$ is 

$$
\begin{array}{l} \mathcal {R} (0, t) = (f _ {t} ^ {T _ {i (t)}} - f _ {T _ {i (t) - 1}} ^ {T _ {i (t)}}) + \sum_ {j = 2} ^ {i (t) - 1} (S _ {T _ {j}} - f _ {T _ {j - 1}} ^ {T _ {j}}) + (S _ {T _ {1}} - f _ {0} ^ {T _ {1}}) - (S _ {t} - S _ {0}) \\ = \underbrace {(f _ {t} ^ {T _ {i (t)}} - S _ {t}) - (f _ {0} ^ {T _ {1}} - S _ {0})} _ {\text {Basis Return}} + \underbrace {\sum_ {j = 1} ^ {i (t) - 1} (S _ {T _ {j}} - f _ {T _ {j}} ^ {T _ {j + 1}})} _ {\text {Cumulative Roll Adjustment}}. \end{array}\tag{3.2}
$$

The cumulative roll adjustment is related to the term structure of futures contracts. If $T_{i} - T_{i-1}$ is constant, and the term structure only moves parallel, then the cumulative roll adjustment is simply the number of roll-over times a constant (difference between spot and near-month futures contract). 

## 3.1 OU and CIR Spot Models

Suppose the spot price follows the OU or CIR model described in Section 2.1. Inspecting (3.2), we can write down the SDE for the roll yield under the OU model: 

$$
\begin{array}{r l} & {d \mathcal {R} (0, t) = d f _ {t} ^ {T _ {i (t)}} - d S _ {t}} \\ & {\qquad = \left[ e ^ {- \tilde {\mu} (T _ {i (t)} - t)} \left(\mu (\theta - S _ {t}) - \tilde {\mu} (\tilde {\theta} - S _ {t})\right) - \mu (\theta - S _ {t}) \right] d t + \sigma \left(e ^ {- \tilde {\mu} (T _ {i (t)} - t)} - 1\right) d B _ {t}.} \end{array}\tag{3.3}
$$

The roll yield SDE for under the CIR model has the same drift as $(3.3)$ . Furthermore, the drift is positive iff 

$$
S _ {t} > \frac {e ^ {- \tilde {\mu} (T _ {i (t)} - t)} (\tilde {\mu} \tilde {\theta} - \mu \theta) + \mu \theta}{e ^ {- \tilde {\mu} (T _ {i (t)} - t)} (\tilde {\mu} - \mu) + \mu}.
$$

In particular, if $\theta = \tilde{\theta}$ , then the drift is positive iff $S_{t} > \theta$ . When $t = T_{i(t)}$ , the drift is $\tilde{\mu}(S_{t} - \tilde{\theta})$ and is positive iff $S_{t} > \tilde{\theta}$ . Furthermore, the drift term can also be expressed as 

$$
\tilde {\mu} \left(f _ {t} ^ {T _ {i (t)}} - \tilde {\theta}\right) - \left(1 - e ^ {- \tilde {\mu} (T _ {i (t)} - t)}\right) \mu (\theta - S _ {t}).
$$

On the other hand, we observe that 

$$
d \mathcal {R} (0, t) d S _ {t} = \sigma^ {2} \left(e ^ {- \tilde {\mu} (T _ {i (t)} - t)} - 1\right) d t,
$$

under the OU case and 

$$
d \mathcal {R} (0, t) d S _ {t} = \sigma^ {2} \left(e ^ {- \tilde {\mu} (T _ {i (t)} - t)} - 1\right) S _ {t} d t,
$$

under the CIR case. In other words, the instantaneous covariations between roll yield and spot price under both OU and CIR models are negative for $t < T_{i(t)}$ regardless of the spot price level. 

Consider a longer horizon with rolling at multiple maturities, the expected roll yield is 

$$
\begin{array}{l} \mathbb {E} \{\mathcal {R} (0, t) \} = \mathbb {E} \{f _ {t} ^ {T _ {i (t)}} - S _ {t} \} - (f _ {0} ^ {T _ {1}} - S _ {0}) + \sum_ {j = 1} ^ {i (t) - 1} \mathbb {E} \{S _ {T _ {j}} - f _ {T _ {j}} ^ {T _ {j + 1}} \} \\ \qquad = ((S _ {0} - \theta) e ^ {- \mu t} + \theta - \tilde {\theta}) (e ^ {- \tilde {\mu} (T _ {i (t)} - t)} - 1) - (S _ {0} - \tilde {\theta}) (e ^ {- \tilde {\mu} T _ {1}} - 1) \\ \qquad + \sum_ {j = 1} ^ {i (t) - 1} ((S _ {0} - \theta) e ^ {- \mu T _ {j}} + \theta - \tilde {\theta}) (1 - e ^ {- \tilde {\mu} (T _ {j + 1} - T _ {j})}). \end{array}
$$

In summary, the expected roll yield depends not only on the risk-neutral parameters $\tilde{\mu}$ and $\tilde{\theta}$ , but also their historical counterparts. It vanishes when $S_{0} = \theta = \tilde{\theta}$ . This is intuitive because if the current spot price is currently at the long-run mean, and the risk-neutral and historical measures coincide, then the spot and futures prices have little tendency to deviate from the long-run mean. Also, notice that neither the futures price nor the roll yield depends on the volatility parameter $\sigma$ . This is true under the OU/CIR model, but not the exponential OU model, as we discuss next. 

## 3.2 Exponential OU Spot Model

We now turn to the exponential OU spot price model discussed in Section 2.2. Recalling the futures price in (2.10), the expected roll yield is given by 

$$
\mathbb {E} \{\mathcal {R} (0, t) \} = Y _ {1} (t) + Y _ {2} (t) - (f _ {0} ^ {T _ {1}} - S _ {0}),\tag{3.4}
$$

where 

$$
\begin{array}{l} Y _ {1} (t) = \mathbb {E} \{f _ {t} ^ {T _ {i (t)}} - S _ {t} \} \\ \qquad = \exp \bigg (e ^ {- \tilde {\mu} (T _ {i (t)} - t) - \mu t} \ln (S _ {0}) + \bigg (\theta - \frac {\sigma^ {2}}{2 \mu} \bigg) (1 - e ^ {- \mu t}) e ^ {- \tilde {\mu} (T _ {i (t)} - t)} \\ \qquad + \frac {\sigma^ {2}}{4 \mu} e ^ {- 2 \tilde {\mu} (T _ {i (t)} - t)} (1 - e ^ {- 2 \mu t}) + (1 - e ^ {- \tilde {\mu} (T _ {i (t)} - t)}) (\tilde {\theta} - \frac {\sigma^ {2}}{2 \tilde {\mu}}) \\ \qquad + \frac {\sigma^ {2}}{4 \tilde {\mu}} (1 - e ^ {- 2 \tilde {\mu} (T _ {i (t)} - t)}) \bigg) \\ \qquad - \exp \bigg (e ^ {- \mu t} \ln (S _ {0}) + (1 - e ^ {- \mu t}) (\theta - \frac {\sigma^ {2}}{2 \mu}) + \frac {\sigma^ {2}}{4 \mu} (1 - e ^ {- \mu t}) \bigg), \end{array}
$$

and 

$$
\begin{array}{l} Y _ {2} (t) = \sum_ {j = 1} ^ {i (t) - 1} \mathbb {E} \{S _ {T _ {j}} - f _ {T _ {j}} ^ {T _ {j + 1}} \} \\ = \sum_ {j = 1} ^ {i (t) - 1} \bigg (\exp \bigg (e ^ {- \mu T _ {j}} \ln (S _ {0}) + (1 - e ^ {- \mu T _ {j}}) (\theta - \frac {\sigma^ {2}}{2 \mu}) + \frac {\sigma^ {2}}{4 \mu} (1 - e ^ {- \mu T _ {j}}) \bigg) \\ - \exp \bigg (e ^ {- \tilde {\mu} (T _ {j + 1} - T _ {j}) - \mu T _ {j}} \ln (S _ {0}) + \bigg (\theta - \frac {\sigma^ {2}}{2 \mu} \bigg) (1 - e ^ {- \mu T _ {j}}) e ^ {- \tilde {\mu} (T _ {j + 1} - T _ {j})} \\ + \frac {\sigma^ {2}}{4 \mu} e ^ {- 2 \tilde {\mu} (T _ {j + 1} - T _ {j})} (1 - e ^ {- 2 \mu T _ {j}}) \\ + (1 - e ^ {- \tilde {\mu} (T _ {j + 1} - T _ {j})}) (\tilde {\theta} - \frac {\sigma^ {2}}{2 \tilde {\mu}}) + \frac {\sigma^ {2}}{4 \tilde {\mu}} (1 - e ^ {- 2 \tilde {\mu} (T _ {j + 1} - T _ {j})}) \bigg) \bigg). \end{array}
$$

The explicit formula (3.4) for the expected roll yield reveals the non-trivial dependence on the volatility parameter $\sigma$ , as well as the risk-neutral parameters $(\tilde{\mu},\tilde{\theta})$ and historical parameters $(\mu ,\theta)$ . It is useful for instantly predicting the roll yield after calibrating the risk-neutral parameters from the term structure of the futures prices, and estimating the historical parameters from past spot prices. 

Referring to $(2.9)$ and $(2.11)$ , the historical dynamics of the roll yield under an XOU spot model is given by 

$$
d \mathcal {R} (0, t) = h (t, s) d t + \sigma \left(e ^ {- \tilde {\mu} (T _ {i (t)} - t)} f _ {t} ^ {T _ {i (t)}} - S _ {t}\right) d B _ {t},
$$

where 

$$
\begin{array}{r l} & h (t, s) = \Big (\ln s (\tilde {\mu} - \mu) + (\mu \theta - \tilde {\mu} \tilde {\theta}) \Big) \exp \bigg (e ^ {- \tilde {\mu} (T _ {i (t)} - t)} \ln (s) + (1 - e ^ {- \tilde {\mu} (T _ {i (t)} - t)}) (\tilde {\theta} - \frac {\sigma^ {2}}{2 \tilde {\mu}} \\ & \qquad + \frac {\sigma^ {2}}{4 \tilde {\mu}} (1 - e ^ {- 2 \tilde {\mu} (T _ {i (t)} - t)}) \bigg) e ^ {- \tilde {\mu} (T _ {i (t)} - t)} - \mu (\theta - \ln (s)) s, \end{array}
$$

is the drift expressed in terms of the spot price $S_{t}$ . This reduces to 

$$
h (T _ {i (t)}, s) = s \ln (s) (\tilde {\mu} - \mu + \mu \theta) - \tilde {\mu} \tilde {\theta} s, \quad \text { if } t = T _ {i (t)}.
$$

Unlike the OU/CIR case, under an XOU spot model there is no explicit solution for the critical level of the spot price at which the drift changes sign. 

As in the OU/CIR spot model, it is of interest to compute 

$$
d \mathcal {R} (0, t) d S _ {t} = \sigma^ {2} \left(e ^ {- \tilde {\mu} (T _ {i (t)} - t)} f _ {t} ^ {T _ {i (t)}} - S _ {t}\right) S _ {t} d t,
$$

from which we see that the covariation between roll yield and spot price can be either positive or negative. In particular when the futures price is significantly higher than the spot price, i.e. when the market is in contango, the correlation tends to be positive. 

## 4 Optimal Timing to Trade Futures

In Section 2, we have discussed the timing to liquidate a long futures position, and the concept of rolling discussed in Section 3 corresponds to holding the futures up to expiry. In this section, we further explore the timing options embedded in futures, and develop the optimal trading strategies. 

## 4.1 Optimal Double Stopping Approach

Let us consider the scenario in which an investor has a long position in a futures contract with expiration date T. With a long position in the futures, the investor can hold it till maturity, but can also close the position early by taking an opposite position at the prevailing market price. At maturity, the two opposite positions cancel each other. This motivates us to investigate the best time to close. 

If the investor selects to close the long position at time $\tau \leq T$ , then she will receive the market value of the futures on the expiry date, denoted by $f(\tau, S_{\tau}; T)$ , minus the transaction cost $c \geq 0$ . To maximize the expected discounted value, evaluated under the investor's historical probability measure $\mathbb{P}$ with a constant subjective discount rate $r > 0$ , the investor solves the optimal stopping problem 

$$
\mathcal {V} (t, s) = \sup _ {\tau \in \mathcal {T} _ {t, T}} \mathbb {E} _ {t, s} \bigl \{e ^ {- r (\tau - t)} (f (\tau , S _ {\tau}; T) - c) \bigr \},
$$

where $T_{t,T}$ is the set of all stopping times, with respect to the filtration generated by S, taking values between t and $\hat{T}$ , where $\hat{T} \in (0, T]$ is the trading deadline, which can equal but not exceed the futures' maturity. Throughout this chapter, we continue to use the shorthand notation $E_{t,s}\{\cdot\} \equiv E\{\cdot | S_t = s\}$ to indicate the expectation taken under the historical probability measure P. 

The value function $\mathcal{V}(t,s)$ represents the expected liquidation value associated with the long futures position. Prior to taking the long position in f, the investor, with zero position, can select the optimal timing to start the trade, or not to enter at all. This leads us to analyze the timing option inherent in the trading problem. Precisely, at time $t \leq T$ , the investor faces the optimal entry timing problem 

$$
\mathcal {J} (t, s) = \sup _ {\nu \in \mathcal {T} _ {t, T}} \mathbb {E} _ {t, s} \Bigl \{e ^ {- r (\nu - t)} (\mathcal {V} (\nu , S _ {\nu}) - (f (\nu , S _ {\nu}; T) + \hat {c})) ^ {+} \Bigr \},
$$

where $\hat{c} \geq 0$ is the transaction cost, which may differ from c. In other words, the investor seeks to maximize the expected difference between the value function $\mathcal{V}(\nu, S_{\nu})$ associated with the long position and the prevailing futures price $f(\nu, S_{\nu}; T)$ . The value function $\mathcal{J}(t, s)$ represents the maximum expected value of the trading opportunity embedded in the futures. We refer this “long to open, short to close” strategy as the long-short strategy. 

Alternatively, an investor may well choose to short a futures contract with the speculation that the futures price will fall, and then close it out later by establishing a long position. $^{4}$ Given an investor who has a unit short position in the futures contract, the objective is to minimize the expected discounted cost to close out this position at/before maturity. The optimal timing strategy is determined from 

$$
\mathcal {U} (t, s) = \inf _ {\tau \in \mathcal {T} _ {t, T}} \mathbb {E} _ {t, s} \Bigl \{e ^ {- r (\tau - t)} (f (\tau , S _ {\tau}; T) + \hat {c}) \Bigr \}.
$$

If the investor begins with a zero position, then she can decide when to enter the market by solving 

$$
\mathcal {K} (t, s) = \sup _ {\nu \in \mathcal {T} _ {t, T}} \mathbb {E} _ {t, s} \left\{e ^ {- r (\nu - t)} ((f (\nu , S _ {\nu}; T) - c) - \mathcal {U} (\nu , S _ {\nu})) ^ {+} \right\}.
$$

We call this “short to open, long to close” strategy as the short-long strategy. 

When an investor contemplates entering the market, she can either long or short first. Therefore, on top of the timing option, the investor has an additional choice between the long-short and short-long strategies. Hence, the investor solves the market entry timing problem: 

$$
\mathcal {P} (t, s) = \sup _ {\varsigma \in \mathcal {T} _ {t, T}} \mathbb {E} _ {t, s} \Bigl \{e ^ {- r (\varsigma - t)} \max \{\mathcal {A} (\varsigma , S _ {\varsigma}), \mathcal {B} (\varsigma , S _ {\varsigma}) \} \Bigr \},\tag{4.1}
$$

with two alternative rewards upon entry defined by 

$$
\begin{array}{l l} \mathcal {A} (\varsigma , S _ {\varsigma}) := (\mathcal {V} (\varsigma , S _ {\varsigma}) - (f (\varsigma , S _ {\varsigma}; T) + \hat {c})) ^ {+} & \text {(long - short)}, \\ \mathcal {B} (\varsigma , S _ {\varsigma}) := ((f (\varsigma , S _ {\varsigma}; T) - c) - \mathcal {U} (\varsigma , S _ {\varsigma})) ^ {+} & \text {(short - long)}. \end{array}
$$

## 4.2 Variational Inequalities & Optimal Trading Strategies

In order to solve for the optimal trading strategies, we study the variational inequalities corresponding to the value functions J, V, U, K and P. To this end, we first define the operators: 

$$
\mathcal {L} ^ {(1)} \{\cdot \} := - r \cdot + \frac {\partial \cdot}{\partial t} + \tilde {\mu} (\tilde {\theta} - s) \frac {\partial \cdot}{\partial s} + \frac {\sigma^ {2}}{2} \frac {\partial^ {2} \cdot}{\partial s ^ {2}},\tag{4.2}
$$

$$
\mathcal {L} ^ {(2)} \{\cdot \} := - r \cdot + \frac {\partial \cdot}{\partial t} + \tilde {\mu} (\tilde {\theta} - s) \frac {\partial \cdot}{\partial s} + \frac {\sigma^ {2} s}{2} \frac {\partial^ {2} \cdot}{\partial s ^ {2}},\tag{4.3}
$$

$$
\mathcal {L} ^ {(3)} \{\cdot \} := - r \cdot + \frac {\partial \cdot}{\partial t} + \tilde {\mu} (\tilde {\theta} - \ln s) \frac {\partial \cdot}{\partial s} + \frac {\sigma^ {2} s ^ {2}}{2} \frac {\partial^ {2} \cdot}{\partial s ^ {2}},\tag{4.4}
$$

corresponding to, respectively, the OU, CIR, and XOU models. 

The optimal exit and entry problems J and V associated with the long-short strategy are solved from the following pair of variational inequalities: 

$$
\max \left\{\mathcal {L} ^ {(i)} \mathcal {V} (t, s), (f (t, s; T) - c) - \mathcal {V} (t, s) \right\} = 0,\tag{4.5}
$$

$$
\max \left\{\mathcal {L} ^ {(i)} \mathcal {J} (t, s), (\mathcal {V} (t, s) - (f (t, s; T) + \hat {c})) ^ {+} - \mathcal {J} (t, s) \right\} = 0,\tag{4.6}
$$

for $(t,s)\in[0,T]\times\mathbb{R}$ , with $i\in\{1,2,3\}$ representing the OU, CIR, or XOU model respectively. $^{5}$ Similarly, the reverse short-long strategy can be determined by numerically solving the variational inequalities satisfied by U and K: 

$$
\min \left\{\mathcal {L} ^ {(i)} \mathcal {U} (t, s), (f (t, s; T) + \hat {c}) - \mathcal {U} (t, s) \right\} = 0,\tag{4.7}
$$

$$
\max \left\{\mathcal {L} ^ {(i)} \mathcal {K} (t, s), ((f (t, s; T) - c) - \mathcal {U} (t, s)) ^ {+} - \mathcal {K} (t, s) \right\} = 0.\tag{4.8}
$$

As V, J, U, and K are numerically solved, they become the input to the final problem represented by the value function P. To determine the optimal timing to enter the futures market, we solve the variational inequality 

$$
\max \left\{\mathcal {L} ^ {(i)} \mathcal {P} (t, s), \max \{\mathcal {A} (t, s), \mathcal {B} (t, s) \} - \mathcal {P} (t, s) \right\} = 0.\tag{4.9}
$$

The optimal timing strategies are described by a series of boundaries representing the time-varying critical spot price at which the investor should establish a long/short futures position. In the “long to open, short to close” trading problem, where the investor pre-commits to taking a long position first, the market entry timing is described by the “J” boundary in Figure 2(a). The subsequent timing to exit the market is represented by the “V” boundary in Figure 2(a). As we can see, the investor will long the futures when the spot price is low, and short to close the position when the spot price is high, confirming the buy-low-sell-high intuition. 

If the investor adopts the short-long strategy, by which she will first short a futures and subsequently close out with a long position, then the optimal market entry and exit timing strategies are represented, respectively, by the “K” and “U” boundaries in Figure 2(c). The investor will enter the market by shorting a futures when the spot price is sufficiently high (at the “K” boundary), and close it out when the spot price is low. Thus, the boundaries reflect a sell-high-buy-low strategy. 

When there are no transaction costs (see Figure 2(b) and 2(d)), the waiting region shrinks for both strategies. Practically, this means that the investor tends to enter and exit the market earlier, resulting in more rapid trades. This is intuitive as transaction costs discourage trades, especially near expiry. 

In the market entry problem represented by $\mathcal{P}(t,s)$ in (4.1), the investor decides at what spot price to open a position. The corresponding timing strategy is illustrated by two boundaries in Figure 2(e). The boundary labeled as “ $P = A$ ” (resp. “ $P = B$ ”) indicates the critical spot price (as a function of time) at which the investor enters the market by taking a long (resp. short) futures position. The area above the “ $P = B$ ” boundary is the “short-first” region, whereas the area below the “ $P = A$ ” boundary is the “long-first” region. The area between the two boundaries is the region where the investor should wait to enter. The ordering of the regions is intuitive – the investor should long the futures when the spot price is currently low and short it when the spot price is high. As time approaches maturity, the value of entering the market diminishes. The investor will not start a long/short position unless the spot is very low/high close to maturity. Therefore, the waiting region expands significantly near expiry. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/2e2b697a-fbe5-4172-a93e-0557b18d1a50/53ef565a5a9f92edfd9755bf928d1b4109d4c1535ec7de445b487fdeb10d09cb.jpg)



(a)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/2e2b697a-fbe5-4172-a93e-0557b18d1a50/dd6cb14c96cd3e0e265f8fb975d40b3e331c9d968a842db7f68e0c7245df2cdf.jpg)



(b)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/2e2b697a-fbe5-4172-a93e-0557b18d1a50/0fa9fe5084da5ba35030d56a12ec5266065d9970f55448e5bd5d803d3d0f01b3.jpg)



(c)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/2e2b697a-fbe5-4172-a93e-0557b18d1a50/5452342430429a03a30e75f50ab2c0b422ec49db199a428ef8219adc1e0d88e9.jpg)



(d)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/2e2b697a-fbe5-4172-a93e-0557b18d1a50/c7ed1d1ee705e65e70510a33c115cba2d2d966289cbe6f447852c442fa125633.jpg)



(e)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/2e2b697a-fbe5-4172-a93e-0557b18d1a50/35abae5f4e1024de3be51d9621f50d256f8cf06ba9458634f345e15c0cda3f98.jpg)



(f)



Figure 2: Optimal long-short boundaries with/without transaction costs for futures trading under the CIR model in (a) and (b) respectively, optimal short-long boundaries with/without transaction costs in (c) and (d) respectively, and optimal boundaries with/without transaction costs in (e) and (f) respectively. Parameters: $\hat{T} = \frac{22}{252}$ , $T = \frac{66}{252}$ , r = 0.05, $\sigma = 5.33$ , $\theta = 17.58$ , $\tilde{\theta} = 18.16$ , $\mu = 8.57$ , $\tilde{\mu} = 4.55$ , $c = \hat{c} = 0.005$ .


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/2e2b697a-fbe5-4172-a93e-0557b18d1a50/86bb0064af3d459f17158edf8151986e9f39a9c9b7b427c9304055121e822e57.jpg)



(a)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/2e2b697a-fbe5-4172-a93e-0557b18d1a50/29961b6b2bcb79c494ffc457abfe01d2787432932d02d5e71fbf15dfb92e40f0.jpg)



(b)



Figure 3: Optimal boundaries with and without transaction costs for futures trading under the CIR model in (a) and (b) respectively. Parameters: $\hat{T} = \frac{22}{252}$ , $T = \frac{66}{252}$ , r = 0.05, $\sigma = 5.33$ , $\theta = 17.58$ , $\tilde{\theta} = 18.16$ , $\mu = 8.57$ , $\tilde{\mu} = 4.55$ , $c = \hat{c} = 0.005$ .


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/2e2b697a-fbe5-4172-a93e-0557b18d1a50/15906e760cbc460db9a3f481c44e1de18c2d548463c28f47374f0121e0e38824.jpg)



(a)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/2e2b697a-fbe5-4172-a93e-0557b18d1a50/53d3680f949b012c8d8da94fcfb6d0b102b6a8bd2a10458569307b6d43c326d9.jpg)



(b)



Figure 4: Optimal boundaries with transaction costs for futures trading. (a) OU spot model with $\sigma = 18.7$ , $\theta = 17.58$ , $\tilde{\theta} = 18.16$ , $\mu = 8.57$ , $\tilde{\mu} = 4.55$ . (b) XOU spot model with $\sigma = 1.63$ , $\theta = 3.03$ , $\tilde{\theta} = 3.06$ , $\mu = 8.57$ , $\tilde{\mu} = 4.08$ . Common parameters: $\hat{T} = \frac{22}{252}$ , $T = \frac{66}{252}$ , $c = \hat{c} = 0.005$ .


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/2e2b697a-fbe5-4172-a93e-0557b18d1a50/c846c2f4f86fc75daa9d64fd57fdf8116a99ec38be38b3fb81e7ac1eb8216cda.jpg)



Figure 5: The value functions P, A, and B plotted against the spot price at time 0. The parameters are the same as those in Figure 4.


The investor's exit strategy depends on the initial entry position. If the investor enters by taking a long position (at the “ $\mathcal{P} = \mathcal{A}$ ” boundary), then the optimal exit timing to close her position is represented by the upper boundary with label “ $\mathcal{V}$ ” in Figure 2(a). If the investor's initial position is short, then the optimal time to close by going long the futures is described by the lower boundary with label “ $\mathcal{U}$ ” in Figure 2(c). 

Since the value function P dominates both J and K due to the additional flexibility, it is not surprising that the “P = A” boundary is lower than the “J” boundary, and the “P = B” boundary is higher than the “K” boundary, as seen in Figure 3(a). This means that the embedded timing option to choose between the two strategies (“long to open, short to close” or “short to open, long to close”) induces the investor to delay market entry to wait for better prices. This phenomenon is also observed for both OU and XOU spot models in Figure 4. Figure 5 shows that the value function P dominates B and A for all values of spot price. We can also see the regions where the “P = A” (when the spot price is low) and “P = B” (when the spot price is high). 

We see that Figure 4(b) is similar to Figure 3(a), in both CIR and XOU cases, the difference between “U” boundary and the “J” boundary is much larger than the difference between the “V” boundary and the “K” boundary. This means that the decision to choose either long-short or short-long has a larger impact on the optimal price level to long futures compared to the optimal level to short. On the other hand, in Figure 4(a), we observe a more symmetric relationship between the long-short and short-long optimal exercise boundaries. In particular, choosing one strategy or the other does not affect the optimal price levels as much as CIR and XOU cases. 

## 5 Conclusion

We have studied an optimal double stopping approach for trading futures under a number of mean-reverting spot models. Our model yields trading decisions that are consistent with the spot price dynamics and futures term structure. Accounting for the timing options as well as the option to choose between a long or short position, we find that it is optimal to delay market entry, as compared to the case of committing to either go long or short a priori. 

A natural direction for future research is to investigate the trading strategies under a multifactor or time-varying mean-reverting spot price model. To this end, we include here some references that discuss the pricing aspect of futures under such models, for example, Detemple and Osakwe (2000); Lu and Zhu (2009); Zhu and Lian (2012); Mencía and Sentana (2013) for VIX futures, Schwartz (1997); Ribeiro and Hodges (2004) for commodities, and Monoyios and Sarno (2002) for equity index futures. It is also of practical interest to develop similar optimal multiple stopping approaches to trading commodities under mean-reverting spot models (Leung et al. (2015, 2014)), and credit derivatives trading (Leung and Liu (2012)). 

## 6 Appendix

## 6.1 Numerical Implementation

We apply a finite difference method to compute the optimal boundaries in Figures 2, 3 and 4. The operators $\mathcal{L}^{(i)}$ , $i \in \{1, 2, 3\}$ , defined in (4.2)-(4.4) correspond to the OU, CIR, and XOU models, respectively. To capture these models, we define the generic differential operator 

$$
\mathcal {L} \left\{\cdot \right\} := - r \cdot + \frac {\partial \cdot}{\partial t} + \varphi (s) \frac {\partial \cdot}{\partial s} + \frac {\sigma^ {2} (s)}{2} \frac {\partial^ {2} \cdot}{\partial s ^ {2}},
$$

then the variational inequalities (4.5), (4.6), (4.7), (4.8) and (4.9) admit the same form as the following variational inequality problem: 

$$
\left\{ \begin{array}{c} \mathcal {L}   g (t, s) \leq 0,    g (t, s) \geq \xi (t, s), \quad (t, s) \in [ 0, \hat {T}) \times \mathbb {R} _ {+}, \\ (\mathcal {L}   g (t, s)) (\xi (t, s) - g (t, s)) = 0, \quad (t, s) \in [ 0, \hat {T}) \times \mathbb {R} _ {+}, \\ g (\hat {T}, s) = \xi (\hat {T}, s), \quad s \in \mathbb {R} _ {+}. \end{array} \right.\tag{6.1}
$$

Here, $g(t,s)$ represents the value functions $\mathcal{V}(t,s)$ , $\mathcal{J}(t,s)$ , $-\mathcal{U}(t,s)$ , $\mathcal{K}(t,s)$ , or $\mathcal{P}(t,s)$ . The function $\xi(t,s)$ represents $f(t,s;T)-c$ , $(\mathcal{V}(t,s)-(f(t,s;T)+\hat{c}))^{+}$ , $-(f(t,s;T)+\hat{c})$ , $(f(t,s;T)-c)-\mathcal{U}(t,s))^{+}$ , or $\max\{\mathcal{A}(t,s),\mathcal{B}(t,s)\}$ . The futures price $f(t,s;T)$ , with $\hat{T}\leq T$ , is given by (2.1), (2.4), and (2.10) under the OU, CIR, and XOU models, respectively. 

We now consider the discretization of the partial differential equation $\mathcal{L}g(t,s)=0$ , over an uniform grid with discretizations in time $(\delta t=\frac{\hat{T}}{N})$ , and space $(\delta s=\frac{S_{\max}}{M})$ . We apply the Crank-Nicolson method, which involves the finite difference equation: 

$$
- \alpha_ {i} g _ {i - 1, j - 1} + (1 - \beta_ {i}) g _ {i, j - 1} - \gamma_ {i} g _ {i + 1, j - 1} = \alpha_ {i} g _ {i - 1, j} + (1 + \beta_ {i}) g _ {i, j} + \gamma_ {i} g _ {i + 1, j},
$$

where 

$$
g _ {i, j} = g (j \delta t, i \delta s), \quad \xi_ {i, j} = \xi (j \delta t, i \delta s), \quad \varphi_ {i} = \varphi (i \delta s), \quad \sigma_ {i} = \sigma (i \delta s).
$$

$$
\alpha_ {i} = \frac {\delta t}{4 \delta s} \big (\frac {\sigma_ {i} ^ {2}}{\delta s} - \varphi_ {i} \big), \quad \beta_ {i} = - \frac {\delta t}{2} \big (r + \frac {\sigma_ {i} ^ {2}}{(\delta s) ^ {2}} \big), \quad \gamma_ {i} = \frac {\delta t}{4 \delta s} \big (\frac {\sigma_ {i} ^ {2}}{\delta s} + \varphi_ {i} \big),
$$

for $i = 1,2,\dots,M - 1$ and $j = 1,2,\dots,N - 1$ . The system to be solved backward in time is 

$$
\mathbf {M _ {1} g _ {j - 1}} = \mathbf {r _ {j}},
$$

where the right-hand side is 

$$
\mathbf {r _ {j}} = \mathbf {M _ {2} g _ {j}} + \alpha_ {1} \left[ \begin{array}{c} g _ {0, j - 1} + g _ {0, j} \\ 0 \\ \vdots \\ 0 \end{array} \right] + \gamma_ {M - 1} \left[ \begin{array}{c} 0 \\ \vdots \\ 0 \\ g _ {M, j - 1} + g _ {M, j}, \end{array} \right],
$$

and 

$$
\begin{array}{r l} & {\mathbf {M _ {1}} = \left[ \begin{array}{c c c c c c} 1 - \beta_ {1} & - \gamma_ {1} & & & & \\ - \alpha_ {2} & 1 - \beta_ {2} & - \gamma_ {2} & & & \\ & - \alpha_ {3} & 1 - \beta_ {3} & - \gamma_ {3} & & \\ & & \ddots & \ddots & \ddots & \\ & & & - \alpha_ {M - 2} & 1 - \beta_ {M - 2} & - \gamma_ {M - 2} \\ & & & & - \alpha_ {M - 1} & 1 - \beta_ {M - 1} \end{array} \right],} \\ & {\mathbf {M _ {2}} = \left[ \begin{array}{c c c c c c} 1 + \beta_ {1} & \gamma_ {1} & & & & \\ \alpha_ {2} & 1 + \beta_ {2} & \gamma_ {2} & & & \\ & \alpha_ {3} & 1 + \beta_ {3} & \gamma_ {3} & & \\ & & \ddots & \ddots & \ddots & \\ & & & \alpha_ {M - 2} & 1 + \beta_ {M - 2} & \gamma_ {M - 2} \\ & & & & \alpha_ {M - 1} & 1 + \beta_ {M - 1} \end{array} \right],} \\ & {\mathbf {g _ {j}} = [ g _ {1, j}, g _ {2, j}, \ldots , g _ {M - 1, j} ] ^ {T}.} \end{array}
$$

This leads to a sequence of stationary complementarity problems. Hence, at each time step $j \in \{1, 2, \ldots, N - 1\}$ , we need to solve 

$$
\left\{ \begin{array}{c} \mathbf {M _ {1}} \mathbf {g _ {j - 1}} \geq \mathbf {r _ {j}}, \\ \mathbf {g _ {j - 1}} \geq \boldsymbol {\xi_ {j - 1}}, \\ (\mathbf {M _ {1}} \mathbf {g _ {j - 1}} - \mathbf {r _ {j}}) ^ {T} (\boldsymbol {\xi_ {j - 1}} - \mathbf {g _ {j - 1}}) = 0. \end{array} \right.
$$

To solve the optimal problem, our algorithm enforces the constraint explicitly as follows 

$$
g _ {i, j - 1} ^ {n e w} = \max \left\{g _ {i, j - 1} ^ {o l d}, \xi_ {i, j - 1} \right\}.\tag{6.2}
$$

The projected SOR method is used to solve the linear system. $^{6}$ At each time j, we iteratively solve 

$$
\begin{array}{r l} & g _ {1, j - 1} ^ {(k + 1)} = \max \big \{\xi_ {1, j - 1}, g _ {1, j - 1} ^ {(k)} + \frac {\omega}{1 - \beta_ {1}} [ r _ {1, j} - (1 - \beta_ {1}) g _ {1, j - 1} ^ {(k)} + \gamma_ {1} g _ {2, j - 1} ^ {(k)} ] \big \}, \\ & g _ {2, j - 1} ^ {(k + 1)} = \max \big \{\xi_ {2, j - 1}, g _ {2, j - 1} ^ {(k)} + \frac {\omega}{1 - \beta_ {2}} [ r _ {2, j} + \alpha_ {2} g _ {1, j - 1} ^ {(k + 1)} - (1 - \beta_ {2}) g _ {2, j - 1} ^ {(k)} + \gamma_ {2} g _ {3, j - 1} ^ {(k)} ] \big \}, \\ & \vdots \\ & g _ {M - 1, j - 1} ^ {(k + 1)} = \max \big \{\xi_ {M - 1, j - 1}, g _ {M - 1, j - 1} ^ {(k)} + \frac {\omega}{1 - \beta_ {M - 1}} [ r _ {M - 1, j} + \alpha_ {M - 1} g _ {M - 2, j - 1} ^ {(k + 1)} - (1 - \beta_ {M - 1}) g _ {M - 1, j - 1} ^ {(k)} ] \big \}, \end{array}\tag{6.3}
$$

where k is the iteration counter and $\omega$ is the overrelaxation parameter. The iterative scheme starts from an initial point $\mathbf{g}_{j}^{(0)}$ and proceeds until a convergence criterion is met, such as $||\mathbf{g}_{j-1}^{(k+1)}-\mathbf{g}_{j-1}^{(k)}||<\epsilon$ , where $\epsilon$ is a tolerance parameter. The optimal boundary $S_{f}(t)$ can be identified by locating the boundary that separates the regions where $g(t,s)=\xi(t,s)$ , or $g(t,s)\geq\xi(t,s)$ . 

## References



Acworth, W. (2015). 2014 FIA annual global futures and options volume: Gains in North America and Europe offset declines in Asia-Pacific. [Online; posted 09-March-2015]. 





Bali, T. G. and Demirtas, K. O. (2008). Testing mean reversion in financial market volatility: Evidence from S&P 500 index futures. Journal of Futures Markets, 28(1):1–33. 





Bessembinder, H., Coughenour, J. F., Seguin, P. J., and Smoller, M. M. (1995). Mean reversion in equilibrium asset prices: Evidence from the futures term structure. The Journal of Finance, 50(1):361–375. 





Brennan, M. J. and Schwartz, E. S. (1990). Arbitrage in stock index futures. Journal of Business, 63(1):S7–S31. 





Cartea, A., Jaimungal, S., and Penalva, J. (2015). Algorithmic and High-Frequency Trading. Cambridge University Press, Cambridge, England. 





Casassus, J. and Collin-Dufresne, P. (2005). Stochastic convenience yield implied from commodity futures and interest rates. The Journal of Finance, 60(5):2283–2331. 





Cox, J. C., Ingersoll, J., and Ross, S. A. (1981). The relation between forward prices and futures prices. Journal of Financial Economics, 9(4):321–346. 





Dai, M., Zhong, Y., and Kwok, Y. K. (2011). Optimal arbitrage strategies on stock index futures under position limits. Journal of Futures Markets, 31(4):394–406. 





Detemple, J. and Osakwe, C. (2000). The valuation of volatility options. European Finance Review, 4(1):21–50. 





Elton, E. J., Gruber, M. J., Brown, S. J., and Goetzmann, W. N. (2009). Modern Portfolio Theory and Investment Analysis. Wiley, 8th edition. 





Geman, H. (2007). Mean reversion versus random walk in oil and natural gas prices. In Fu, M. C., Jarrow, R. A., Yen, J.-Y. J., and Elliot, R. J., editors, Advances in Mathematical Finance, Applied and Numerical Harmonic Analysis, pages 219–228. Birkhuser Boston. 





Gorton, G. B., Hayashi, F., and Rouwenhorst, K. G. (2013). The fundamentals of commodity futures returns. Review of Finance, 17(1):35–105. 





Grübichler, A. and Longstaff, F. (1996). Valuing futures and options on volatility. Journal of Banking and Finance, 20(6):985–1001. 





Irwin, S. H., Zulauf, C. R., and Jackson, T. E. (1996). Monte Carlo analysis of mean reversion in commodity futures prices. American Journal of Agricultural Economics, 78(2):387–399. 





Leung, T. and Li, X. (2015). Optimal mean reversion trading with transaction costs and stop-loss exit. International Journal of Theoretical & Applied Finance, 18(3):15500. 





Leung, T., Li, X., and Wang, Z. (2014). Optimal starting-stopping and switching of a CIR process with fixed costs. Risk and Decision Analysis, 5(2):149–161. 





Leung, T., Li, X., and Wang, Z. (2015). Optimal multiple trading times under the exponential OU model with transaction costs. Stochastic Models, 31(4). 





Leung, T. and Liu, P. (2012). Risk premia and optimal liquidation of credit derivatives. International Journal of Theoretical & Applied Finance, 15(8):1250059. 





Leung, T. and Shirai, Y. (2015). Optimal derivative liquidation timing under path-dependent risk penalties. Journal of Financial Engineering, 2(1):1550004. 





Lu, Z. and Zhu, Y. (2009). Volatility components: The term structure dynamics of VIX futures. Journal of Futures Markets, 30(3):230–256. 





Mencía, J. and Sentana, E. (2013). Valuation of VIX derivatives. Journal of Financial Economics, 108(2):367–391. 





Monoyios, M. and Sarno, L. (2002). Mean reversion in stock index futures markets: a nonlinear analysis. The Journal of Futures Markets, 22(4):285–314. 





Moskowitz, T. J., Ooi, Y. H., and Pedersen, L. H. (2012). Time series momentum. Journal of Financial Economics, 104(2):228–250. 





Ribeiro, D. R. and Hodges, S. D. (2004). A two-factor model for commodity prices and futures valuation. EFMA 2004 Basel Meetings Paper. 





Schwartz, E. (1997). The stochastic behavior of commodity prices: Implications for valuation and hedging. The Journal of Finance, 52(3):923–973. 





Wang, Z. and Daigler, R. T. (2011). The performance of VIX option pricing models: Empirical evidence beyond simulation. Journal of Futures Markets, 31(3):251–281. 





Wilmott, P., Howison, S., and Dewynne, J. (1995). The Mathematics of Financial Derivatives: A Student Introduction. Cambridge University Press, 1st edition. 





Zhang, J. E. and Zhu, Y. (2006). VIX futures. Journal of Futures Markets, 26(6):521–531. 





Zhu, S.-P. and Lian, G.-H. (2012). An analytical formula for VIX futures and its applications. Journal of Futures Markets, 32(2):166–190. 

