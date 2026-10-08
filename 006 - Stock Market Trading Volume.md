# Stock Market Trading Volume

Andrew W. Lo and Jiang Wang<sup>∗</sup> 

First Draft: September 5, 2001 

This Draft: May 16, 2009 

To appear in Y. A¨ıt-Sahalia and L. Hansen, eds., 2009, The Handbook of Financial Econometrics. New York: North-Holland. 

## Abstract

If price and quantity are the fundamental building blocks of any theory of market interac tions, the importance of trading volume in understanding the behavior of financial markets is clear. However, while many economic models of financial markets have been developed to explain the behavior of prices—predictability, variability, and information content—far less attention has been devoted to explaining the behavior of trading volume. In this chapter, we hope to expand our understanding of trading volume by developing well-articulated economic models of asset prices and volume and empirically estimating them using recently available daily volume data for individual securities from the University of Chicago’s Center for Research in Securities Prices. Our theoretical contributions include: (1) an economic definition of volume that is most consistent with theoretical models of trading activity; (2) the derivation of volume implications of basic portfolio theory; and (3) the development of an intertemporal equilibrium model of asset market in which the trading process is determined endogenously by liquidity needs and risk-sharing motives. Our empirical contributions include: (1) the construction of a volume/returns database extract of the CRSP volume data; (2) comprehensive exploratory data analysis of both the time-series and cross-sectional properties of trading volume; (3) estimation and inference for price/volume relations implied by asset-pricing models; and (4) a new approach for empirically identifying factors to be included in a linear-factor model of asset returns using volume data. 

## Contents

1 Introduction 1   
2 Measuring Trading Activity 3   
2.1 Notation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 5   
2.2 Motivation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 5   
2.3 Defining Individual and Portfolio Turnover. 7   
2.4 Time Aggregation. 10   
2.5 The Data. 10   
3 Time-Series Properties 11   
3.1 Seasonalities. 14   
3.2 Secular Trends and Detrending. 18   
4 Cross-Sectional Properties 28   
4.1 Specification of Cross-Sectional Regressions. 34   
4.2 Summary Statistics For Regressors. 38   
4.3 Regression Results. 43   
5 Volume Implications of Portfolio Theory 47   
5.1 Two-Fund Separation. 50   
5.2 $(K + 1)$ -Fund Separation. 51   
5.3 Empirical Tests of $(K + 1)$ -Fund Separation. 53   
6 Volume Implications of Intertemporal Asset-Pricing Models 58   
6.1 An Intertemporal Capital Asset-Pricing Model. 60   
6.2 The Behavior of Returns and Volume. 64   
6.3 Empirical Construction of the Hedging Portfolio. 69   
6.4 The Forecast Power of the Hedging Portfolio. 75   
6.5 The Hedging-Portfolio Return as a Risk Factor. 86   
6.6 Updated Empirical Results. 90   
7 Conclusion 96   
References 103 

## 1 Introduction

One of the most fundamental notions of economics is the determination of prices through the interaction of supply and demand. The remarkable amount of information contained in equilibrium prices has been the subject of countless studies, both theoretical and empirical, and with respect to financial securities, several distinct literatures devoted solely to prices have developed.<sup>1</sup> Indeed, one of the most well-developed and most highly cited strands of modern economics is the asset-pricing literature. 

However, the intersection of supply and demand determines not only equilibrium prices but also equilibrium quantities, yet quantities have received far less attention, especially in the asset-pricing literature (is there a parallel asset-quantities literature?). 

In this chapter, we hope to balance the asset-pricing literature by reviewing the quantity implications of a dynamic general equilibrium model of asset markets under uncertainty, and investigating those implications empirically. Through theoretical and empirical analysis, we seek to understand the motives for trade, the process by which trades are consummated, the interaction between prices and volume, and the roles that risk preferences and market frictions play in determining trading activity as well as price dynamics. We begin in Section 2 with the basic definitions and notational conventions of our volume investigation—not a trivial task given the variety of volume measures used in the extant literature, e.g., shares traded, dollars traded, number of transactions, etc. We argue that turnover—shares traded divided by shares outstanding—is a natural measure of trading activity when viewed in the context of standard portfolio theory and equilibrium asset-pricing models. 

Using weekly turnover data for individual securities on the New York and American Stock Exchanges from 1962 to 1996—made available by the Center for Research in Securities Prices—we document in Sections 3 and 4 the time-series and cross-sectional properties of turnover indexes, individual turnover, and portfolio turnover. Turnover indexes exhibit a clear time trend from 1962 to 1996, beginning at less than 0.5% in 1962, reaching a high of 4% in October 1987, and dropping to just over 1% at the end of our sample in 1996. The cross section of turnover also varies through time, fairly concentrated in the early 1960’s, much wider in the late 1960’s, narrow again in the mid 1970’s, and wide again after that. 

There is some persistence in turnover deciles from week to week—the largest- and smallestturnover stocks in one week are often the largest- and smallest-turnover stocks, respectively, the next week—however, there is considerable difusion of stocks across the intermediate turnover-deciles from one week to the next. To investigate the cross-sectional variation of turnover in more detail, we perform cross-sectional regressions of average turnover on several regressors related to expected return, market capitalization, and trading costs. With R<sup>2</sup>’s ranging from 29.6% to 44.7%, these regressions show that stock-specific characteristics do explain a significant portion of the cross-sectional variation in turnover. This suggests the possibility of a parsimonious linear-factor representation of the turnover cross-section. 

In Section 5, we derive the volume implications of basic portfolio theory, showing that two-fund separation implies that turnover is identical across all assets, and that (K + 1)- fund separation implies that turnover has an approximately linear K-factor structure. To investigate these implications empirically, we perform a principal-components decomposition of the covariance matrix of the turnover of ten portfolios, where the portfolios are constructed by sorting on turnover betas. Across five-year subperiods, we find that a one-factor model for turnover is a reasonable approximation, at least in the case of turnover-beta-sorted portfolios, and that a two-factor model captures well over 90% of the time-series variation in turnover. 

Finally, to investigate the dynamics of trading volume, in Section 6 we propose an intertemporal equilibrium asset-pricing model and derive its implications for the joint behavior of volume and asset returns. In this model, assets are exposed to two sources of risks: market risk and the risk of changes in market conditions.<sup>2</sup> As a result, investors wish to hold two distinct portfolios of risky assets: the market portfolio and a hedging portfolio. The market portfolio allows them to adjust their exposure to market risk, and the hedging portfolio allows them to hedge the risk of changes in market conditions. In equilibrium, investors trade in only these two portfolios, and expected asset returns are determined by their exposure to these two risks, i.e., a two-factor linear pricing model holds, where the two factors are the returns on the market portfolio and the hedging portfolio, respectively. We then explore the implications of this model on the joint behavior of volume and returns using the same weekly turnover data as in the earlier sections. From the trading volume of individual stocks, we construct the hedging portfolio and its returns. We find that the hedging-portfolio returns consistently outperforms other factors in predicting future returns to the market portfolio, an implication of the intertemporal equilibrium model. We then use the returns to the hedging and market portfolios as two risk factors in a cross-sectional test along the lines of Fama and MacBeth (1973), and find that the hedging portfolio is comparable to other factors in explaining the cross-sectional variation of expected returns. 

Our extensive analysis was based on data from 1962 to 1996, when it was first available from CRSP. We have later updated our analysis on the tests of volume-return implications of the intertemporal asset pricing model to include the data from 1997 to 2004. These results reported at the end of Section 6. 

We conclude with suggestions for future research in Section 7. 

## 2 Measuring Trading Activity

Any empirical analysis of trading activity in the market must start with a proper measure of volume. The literature on trading activity in financial markets is extensive and a number of measures of volume have been proposed and studied.<sup>3</sup> Some studies of aggregate trading activity use the total number of shares traded as a measure of volume (see Epps and Epps (1976), Gallant, Rossi, and Tauchen (1992), Hiemstra and Jones (1994), and Ying (1966)). Other studies use aggregate turnover—the total number of shares traded divided by the total number of shares outstanding—as a measure of volume (see Campbell, Grossman, Wang (1993), LeBaron (1992), Smidt (1990), and the 1996 NYSE Fact Book). Individual share volume is often used in the analysis of price/volume and volatility/volume relations (see Andersen (1996), Epps and Epps (1976), and Lamoureux and Lastrapes (1990, 1994)). Studies focusing on the impact of information events on trading activity use individual turnover as a measure of volume (see Bamber (1986, 1987), Lakonishok and Smidt (1986), Morse (1980), Richardson, Sefcik, Thompson (1986), Stickel and Verrecchia (1994)). Alternatively, Tkac (1999) considers individual dollar volume normalized by aggregate market dollar-volume. And even the total number of trades (Conrad, Hameed, and Niden (1994)) and the number of trading days per year (James and Edmister (1983)) have been used as measures of trading activity. Table 1 provides a summary of the various measures used in a representative sample of the recent volume literature. These diferences suggest that diferent applications call for diferent volume measures. 

In order to proceed with our analysis, we need to first settle on a measure of volume. 

<table><tr><td>Volume Measure</td><td>Study</td></tr><tr><td>Aggregate Share Volume</td><td>Gallant, Rossi, and Tauchen (1992), Hiemstra and Jones (1994), Ying (1966)</td></tr><tr><td>Individual Share Volume</td><td>Andersen (1996), Epps and Epps (1976), James and Edmister (1983), Lamoureux and Lastrapes (1990, 1994)</td></tr><tr><td>Aggregate Dollar Volume</td><td>—</td></tr><tr><td>Individual Dollar Volume</td><td>James and Edmister (1983), Lakonishok and Vermaelen (1986)</td></tr><tr><td>Relative Individual Dollar Volume</td><td>Tkac (1999)</td></tr><tr><td>Individual Turnover</td><td>Bamber (1986, 1987), Hu (1997), Lakonishok and Smidt (1986), Morse (1980), Richardson, Sefcik, Thompson (1986), Stickel and Verrechia (1994)</td></tr><tr><td>Aggregate Turnover</td><td>Campbell, Grossman, Wang (1993), LeBaron (1992), Smidt (1990), NYSE Fact Book</td></tr><tr><td>Total Number of Trades</td><td>Conrad, Hameed, and Niden (1994)</td></tr><tr><td>Trading Days Per Year</td><td>James and Edmister (1983)</td></tr><tr><td>Contracts Traded</td><td>Tauchen and Pitts (1983)</td></tr></table>


Table 1: Selected volume studies grouped according to the volume measure used.


After developing some basic notation in Section 2.1, we review several volume measures in Section 2.2 and provide some economic motivation for turnover as a canonical measure of trading activity. Formal definitions of turnover—for individual securities, portfolios, and in the presence of time aggregation—are given in Sections 2.3–2.4. Theoretical justifications for turnover as a volume measure are provided in Sections 5 and 6. Based on these considerations, in Section 2.5 we describe our approach to constructing the volume variables used throughout the rest of this chapter. 

## 2.1 Notation

Our analysis begins with I investors indexed by $i = 1 , \dots , I$ and J stocks indexed by $j =$ $1 , \ldots , J .$ . We assume that all the stocks are risky and non-redundant. For each stock $j$ , let $N _ { j t }$ be its total number of shares outstanding, $D _ { j t }$ its dividend, and $P _ { j t }$ its ex-dividend price at date t. For notational convenience and without loss of generality, we assume throughout that the total number of shares outstanding for each stock is constant over time, i.e., $N _ { j t } = N _ { j }$ 2 $j = 1 , \dots , J .$ 

For each investor $i ,$ let $S _ { j t } ^ { i }$ denote the number of shares of stock $j$ he holds at date t. Let $P _ { t } \equiv [ \ P _ { 1 t } \ \cdot \cdot \ P _ { J t } \ ] ^ { \top }$ and $S _ { t } \equiv [ \ : S _ { 1 t } \ : \ : \cdot \ : \ : S _ { J t } ] ^ { \intercal }$ denote the vector of stock prices and shares held in a given portfolio, where $A ^ { \top }$ denotes the transpose of a vector or matrix A. Let the return on stock $j$ at t be $R _ { j t } \equiv ( P _ { j t } - P _ { j t - 1 } + D _ { j t } ) / P _ { j t - 1 }$ <sub>1</sub>. Finally, denote by $V _ { j t }$ the total number of shares of security $j$ traded at time t, i.e., share volume, hence 

$$
V _ {j t} = \frac {1}{2} \sum_ {i = 1} ^ {I} | S _ {j t} ^ {i} - S _ {j t - 1} ^ {i} |\tag{1}
$$

where the coeficient $\begin{array} { l } { { \frac { 1 } { 2 } } } \end{array}$ corrects for the double counting when summing the shares traded over all investors. 

## 2.2 Motivation

To motivate the definition of volume used in this chapter, we begin with a simple numerical example drawn from portfolio theory (a formal discussion is given in Section 5). Consider a stock market comprised of only two securities, A and B. For concreteness, assume that security A has 10 shares outstanding and is priced at $100 per share, yielding a market value of $1000, and security B has 30 shares outstanding and is priced at $50 per share, yielding a market value of $1500, hence $N _ { a t } = 1 0 , N _ { b t } = 3 0 , P _ { a t } = 1 0 0 , P _ { b t } = 5 0$ . Suppose there are only two investors in this market—call them investor 1 and 2—and let two-fund separation hold so that both investors hold a combination of risk-free bonds and a stock portfolio with A and B in the same relative proportion. Specifically, let investor 1 hold 1 share of A and 3 shares of B, and let investor 2 hold 9 shares of A and 27 shares of B. In this way, all shares are held and both investors hold the same market portfolio (40% A and 60% B). 

Now suppose that investor 2 liquidates $750 of his portfolio—3 shares of A and 9 shares of B—and assume that investor 1 is willing to purchase exactly this amount from investor 2 at the prevailing market prices.<sup>4</sup> After completing the transaction, investor 1 owns 4 shares of A and 12 shares of B, and investor 2 owns 6 shares of A and 18 shares of B. What kind of trading activity does this transaction imply? 

For individual stocks, we can construct the following measures of trading activity: 

• Number of trades per period 

• Share volume, $V _ { j t }$ 

• Dollar volume, $P _ { j t } V _ { j t }$ 

• Relative dollar volume, $P _ { j t } V _ { j t } / \sum _ { j } P _ { j t } V _ { j t }$ 

• Share turnover, 

$$
\tau_ {j t} \equiv \frac {V _ {j t}}{N _ {j t}}
$$

• Dollar turnover, 

$$
\nu_ {j t} \equiv \frac {P _ {j t} V _ {j t}}{P _ {j t} N _ {j t}} = \tau_ {j t}
$$

where $j = a , b . ^ { 5 }$ To measure aggregate trading activity, we can define similar measures: 

• Number of trades per period 

• Total number of shares traded, $V _ { a t } + V _ { b t }$ 

• Dollar volume, $P _ { a t } V _ { a t } + P _ { b t } V _ { b t }$ 

• Share-weighted turnover, 

$$
\tau_ {t} ^ {S W} \equiv \frac {V _ {a t} + V _ {b t}}{N _ {a} + N _ {b}} = \frac {N _ {a}}{N _ {a} + N _ {b}} \tau_ {a t} + \frac {N _ {b}}{N _ {a} + N _ {b}} \tau_ {b t}
$$

• Equal-weighted turnover, 

$$
\tau_ {t} ^ {E W} \equiv \frac {1}{2} \left(\frac {V _ {a t}}{N _ {a}} + \frac {V _ {b t}}{N _ {a}}\right) = \frac {1}{2} (\tau_ {a t} + \tau_ {b t})
$$

• Value-weighted turnover, 

$$
\tau_ {t} ^ {V W} \equiv \frac {P _ {a t} N _ {a}}{P _ {a t} N _ {a} + P _ {b t} N _ {b}} \frac {V _ {a t}}{N _ {a}} + \frac {P _ {b t} N _ {b}}{P _ {a t} N _ {a} + P _ {b t} N _ {b}} \frac {V _ {b t}}{N _ {b}} = \omega_ {a t} \tau_ {a t} + \omega_ {b t} \tau_ {b t}.
$$

Table 2 reports the values that these various measures of trading activity take on for the hypothetical transaction between investors 1 and 2. Though these values vary considerably— 2 trades, 12 shares traded, $750 traded—one regularity does emerge: the turnover measures are all identical. This is no coincidence, but is an implication of two-fund separation. If all investors hold the same relative proportions of risky assets at all times, then it can be shown that trading activity—as measured by turnover—must be identical across all risky securities (see Section 5). Although the other measures of volume do capture important aspects of trading activity, if the focus is on the relation between volume and equilibrium models of asset markets (such as the CAPM and ICAPM), turnover yields the sharpest empirical implications and is the most natural measure. For this reason, we will use turnover as the measure of volume throughout this chapter. In Section 5 and $6 ,$ we formally demonstrate this point in the context of classic portfolio theory and intertemporal capital asset pricing models. 

## 2.3 Defining Individual and Portfolio Turnover

For each individual stock $j ,$ let turnover be defined by: 

Definition 1 The turnover $\tau _ { j t }$ of stock $j$ at time t is 

$$
\tau_ {j t} \equiv \frac {V _ {j t}}{N _ {j}}\tag{2}
$$

<table><tr><td>Volume Measure</td><td>A</td><td>B</td><td>Aggregate</td></tr><tr><td>Number of Trades</td><td>1</td><td>1</td><td>2</td></tr><tr><td>Shares Traded</td><td>3</td><td>9</td><td>12</td></tr><tr><td>Dollars Traded</td><td>$300</td><td>$450</td><td>$750</td></tr><tr><td>Share Turnover</td><td>0.3</td><td>0.3</td><td>0.3</td></tr><tr><td>Dollar Turnover</td><td>0.3</td><td>0.3</td><td>0.3</td></tr><tr><td>Share-Weighted Turnover</td><td>—</td><td>—</td><td>0.3</td></tr><tr><td>Equal-Weighted Turnover</td><td>—</td><td>—</td><td>0.3</td></tr><tr><td>Value-Weighted Turnover</td><td>—</td><td>—</td><td>0.3</td></tr></table>


Table 2: Volume measures for a two-stock, two-investor example when investors only trade in the market portfolio.


where $V _ { j t }$ is the share volume of security j at time t and $N _ { j }$ is the total number of shares outstanding of stock $j$ . 

Although we define the turnover ratio using the total number of shares traded, it is obvious that using the total dollar volume normalized by the total market value gives the same result. 

Given that investors, particularly institutional investors, often trade portfolios or baskets of stocks, a measure of portfolio trading activity would be useful. But even after settling on turnover as the preferred measure of an individual stock’s trading activity, there is still some ambiguity in extending this definition to the portfolio case. In the absence of a theory for which portfolios are traded, why they are traded, and how they are traded, there is no natural definition of portfolio turnover.<sup>6</sup> For the specific purpose of investigating the implications of portfolio theory and ICAPM for trading activity (see Section 5 and 6), we propose the following definition: 

Definition 2 For any portfolio p defined by the vector of shares held $S _ { t } ^ { p } = [ \ : S _ { 1 t } ^ { p } \cdot \cdot \cdot S _ { J t } ^ { p } ] ^ { \intercal }$ with non-negative holdings in all stocks, i.e., $S _ { j t } ^ { p } \geq 0$ for all $j$ , and strictly positive market value, i.e., $S _ { t } ^ { p \top } P _ { t } > 0$ , let $\omega _ { j t } ^ { p } \equiv S _ { j t } ^ { p } P _ { j t } / ( S _ { t } ^ { p \top } P _ { t } )$ be the fraction invested in stock j, $j = 1 , \dots , J ,$ Then its turnover is defined to be 

$$
\tau_ {t} ^ {p} \equiv \sum_ {j = 1} ^ {J} \omega_ {j t} ^ {p} \tau_ {j t}.\tag{3}
$$

Under this definition, the turnover of value-weighted and equal-weighted indexes are welldefined 

$$
\tau_ {t} ^ {V W} \equiv \sum_ {j = 1} ^ {J} \omega_ {j t} ^ {V W} \tau_ {j t}, \qquad \tau_ {t} ^ {E W} \equiv \frac {1}{J} \sum_ {j = 1} ^ {J} \tau_ {j t}\tag{4}
$$

respectively, where $\omega _ { j t } ^ { V W } \equiv N _ { j } { P _ { j t } } / \left( { \sum _ { j } { N _ { j } { P _ { j t } } } } \right)$ , for $j = 1 , \dots , J .$ 

Although (3) seems to be a reasonable definition of portfolio turnover, some care must be exercised in interpreting it. While $\tau _ { t } ^ { V W }$ and $\tau _ { t } ^ { E W }$ are relevant to the theoretical implications derived in Section 5 and 6, they should be viewed only as particular weighted averages of individual turnover, not necessarily as the turnover of any specific trading strategy. 

In particular, Definition 2 cannot be applied too broadly. Suppose, for example, shortsales are allowed so that some portfolio weights can be negative. In that case, (3) can be quite misleading since the turnover of short positions will ofset the turnover of long positions. We can modify (3) to account for short positions by using the absolute values of the portfolio weights 

$$
\tau_ {t} ^ {p} \equiv \sum_ {j = 1} ^ {J} \frac {| \omega_ {j t} ^ {p} |}{\sum_ {k} | \omega_ {k t} ^ {p} |} \tau_ {j t}\tag{5}
$$

but this can yield some anomalous results as well. For example, consider a two-asset portfolio with weights $\omega _ { a t } = 3$ and $\omega _ { b t } = - 2$ . If the turnover of both stocks are identical and equal to $\tau ,$ , the portfolio turnover according to (5) is also $\tau ,$ yet there is clearly a great deal more trading activity than this implies. Without specifying why and how this portfolio is traded, a sensible definition of portfolio turnover cannot be proposed. 

Neither (3) or (5) are completely satisfactory measures of trading activities of a portfolio in general. Until we introduce a more specific context in which trading activity is to be measured, we shall have to satisfy ourselves with Definition 2 as a measure of trading activities of a portfolio. 

## 2.4 Time Aggregation

Given our choice of turnover as a measure of volume for individual securities, the most natural method of handling time aggregation is to sum turnover across dates to obtain timeaggregated turnover. Although there are several other alternatives, e.g., summing share volume and then dividing by average shares outstanding, summing turnover ofers several advantages. Unlike a measure based on summed shares divided by average shares outstanding, summed turnover is cumulative and linear, each component of the sum corresponds to the actual measure of trading activity for that day, and it is unafected by “neutral” changes of units such as stock splits and stock dividends.<sup>7</sup> Therefore, we shall adopt this measure of time aggregation in our empirical analysis below. 

Definition 3 If the turnover for stock j at time t is given by $\tau _ { j t }$ , the turnover between $t - 1$ to $t + q$ for any $q \geq 0 _ { ; }$ , is given by: 

$$
\tau_ {j t} (q) \equiv \tau_ {j t} + \tau_ {j t + 1} + \dots + \tau_ {j t + q}.\tag{6}
$$

## 2.5 The Data

Having defined our measure of trading activity as turnover, we use the University of Chicago’s Center for Research in Securities Prices (CRSP) Daily Master File to construct weekly turnover series for individual NYSE and AMEX securities from July 1962 to December 1996 (1,800 weeks) using the time-aggregation method discussed in Section 2.4, which we call the “MiniCRSP” volume data extract.<sup>8</sup> We choose a weekly horizon as the best compromise between maximizing sample size while minimizing the day-to-day volume and return fluctuations that have less direct economic relevance. And since our focus is the implications of portfolio theory for volume behavior, we confine our attention to ordinary common shares on the NYSE and AMEX (CRSP sharecodes 10 and 11 only), omitting ADRs, SBIs, REITs, closed-end funds, and other such exotica whose turnover may be dificult to interpret in the usual sense.<sup>9</sup> We also omit NASDAQ stocks altogether since the diferences between NAS-DAQ and the NYSE/AMEX (market structure, market capitalization, etc.) have important implications for the measurement and behavior of volume (see, for example, Atkins and Dyl (1997)), and this should be investigated separately. 

Throughout our empirical analysis, we report turnover and returns in units of percent per week—they are not annualized. 

Finally, in addition to the exchange and sharecode selection criteria imposed, we also discard 37 securities from our sample because of a particular type of data error in the CRSP volume entries.<sup>10</sup> 

## 3 Time-Series Properties

Although it is dificult to develop simple intuition for the behavior of the entire timeseries/cross-section volume dataset—a dataset containing between 1,700 and 2,200 individual securities per week over a sample period of 1,800 weeks—some gross characteristics of volume can be observed from value-weighted and equal-weighted turnover indexes.<sup>11</sup> These characteristics are presented in Figure 1 and in Tables 3 and 4. 

Figure 1a shows that value-weighted turnover has increased dramatically since the mid-1960’s, growing from less than 0.20% to over 1% per week. The volatility of value-weighted turnover also increases over this period. However, equal-weighted turnover behaves somewhat diferently: Figure 1b shows that it reaches a peak of nearly 2% in 1968, then declines until the 1980’s when it returns to a similar level (and goes well beyond it during October 1987). These diferences between the value- and equal-weighted indexes suggest that smaller-capitalization companies can have high turnover. 

Since turnover is, by definition, an asymmetric measure of trading activity—it cannot be negative—its empirical distribution is naturally skewed. Taking natural logarithms may provide more (visual) information about its behavior and this is done in Figures 1c- 1d. Although a trend is still present, there is more evidence for cyclical behavior in both indexes. 

Table 3 reports various summary statistics for the two indexes over the 1962–1996 sample period, and Table 4 reports similar statistics for five-year subperiods. Over the entire sample the average weekly turnover for the value-weighted and equal-weighted indexes is 0.78% and 0.91%, respectively. The standard deviation of weekly turnover for these two indexes is 0.48% and 0.37%, respectively, yielding a coeficient of variation of 0.62 for the valueweighted turnover index and 0.41 for the equal-weighted turnover index. In contrast, the coeficients of variation for the value-weighted and equal-weighted returns indexes are 8.52 and 6.91, respectively. Turnover is not nearly so variable as returns, relative to their means. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/0446c5e0c63a0a3960c525b7c7a7e25232c020b40017044f06b362c9d47bda60.jpg)



( a )



Log (Val ue-Weig hted Tu rnove r I ndex)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/53a2eaf71e4776405d9a1c5b07062d0cf73bb25f4668447065a3f7963b40c088.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/df6def6ef2881a9ee37112285e2225882b0e75d477998d6e1eb58327d5c719e2.jpg)



( c )



( b )



Log ( E q ual-Weig hted Tu rnove r I ndex)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/d0e65118577b0d8e0cf610be5f330efac813dc10c0c113c15cfff3b654508758.jpg)



( d )



Fi<sub>gure</sub> 1 <sub>:</sub> W<sub>ee</sub>kl<sub>y</sub> V<sub>a</sub>l<sub>ue</sub>-W<sub>e</sub>i<sub>g</sub>ht<sub>e</sub>d <sub>an</sub>d E<sub>qua</sub>l-W<sub>e</sub>i<sub>g</sub>ht<sub>e</sub>d T<sub>urnover</sub> I<sub>n</sub>d<sub>exes ,</sub> 1 962 t<sub>o</sub> 1 996 <sub>.</sub>


Table 4 illustrates the nature of the secular trend in turnover through the five-year subperiod statistics. Average weekly value-weighted and equal-weighted turnover is 0.25% and 0.57%, respectively, in the first subperiod (1962–1966); they grow to 1.25% and 1.31%, respectively, by the last subperiod (1992–1996). At the beginning of the sample, equalweighted turnover is three to four times more volatile than value-weighted turnover (0.21% versus 0.07% in 1962–1966, 0.32% versus 0.08% in 1967–1971), but by the end of the sample their volatilities are comparable (0.22% versus 0.23% in 1992–1996). 

The subperiod containing the October 1987 crash exhibits a few anomalous properties: excess skewness and kurtosis for both returns and turnover, average value-weighted turnover slightly higher than average equal-weighted turnover, and slightly higher volatility for valueweighted turnover. These anomalies are consistent with the extreme outliers associated with the 1987 crash (see Figure 1). 

## 3.1 Seasonalities

In Tables 5–7b, we check for seasonalities in daily and weekly turnover, e.g., day-of-theweek, quarter-of-the-year, turn-of-the-quarter, and turn-of-the-year efects. Table 5 reports regression results for the entire sample period, Table 6 reports day-of-the-week regressions for each subperiod, and Tables 7a and 7b report turn-of-the-quarter and turn-of-the-year regressions for each subperiod. The dependent variable for each regression is either turnover or returns and the independent variables are indicators of the particular seasonality efect. No intercept terms are included in any of these regressions. 

Table 5 shows that, in contrast to returns which exhibit a strong day-of-the-week efect, daily turnover is relatively stable over the week. Mondays and Fridays have slightly lower average turnover than the other days of the week, Wednesdays the highest, but the diferences are generally small for both indexes: the largest diference is 0.023% for value-weighted turnover and 0.018% for equal-weighted turnover, both between Mondays and Wednesdays. 

Table 5 also shows that turnover is relatively stable over quarters—the third quarter has the lowest average turnover, but it difers from the other quarters by less than 0.15% for either turnover index. Turnover tends to be lower at the beginning-of-quarters, beginning-of-years, and end-of-years, but only the end-of-year efect for value-weighted turnover (−0.189%) and the beginning-of-quarter efect for equal-weighted turnover (−0.074) are statistically significant at the 5% level. 

Table 6 reports day-of-the-week regressions for the five-year subperiods and shows that the patterns in Table 6 are robust across subperiods: turnover is slightly lower on Mondays and Fridays. Interestingly, the return regressions indicate that the “weekend” efect—large negative returns on Mondays and large positive returns on Fridays—is not robust across subperiods.<sup>12</sup> In particular, in the 1992–1996 subperiod average Monday-returns for the value-weighted index is positive, statistically significant, and the highest of all the five days’ average returns. 

<table><tr><td>Statistic</td><td><eq>\tau^{VW}</eq></td><td><eq>\tau^{EW}</eq></td><td><eq>R^{VW}</eq></td><td><eq>R^{EW}</eq></td></tr><tr><td>Mean</td><td>0.78</td><td>0.91</td><td>0.23</td><td>0.32</td></tr><tr><td>Std. Dev.</td><td>0.48</td><td>0.37</td><td>1.96</td><td>2.21</td></tr><tr><td>Skewness</td><td>0.66</td><td>0.38</td><td>-0.41</td><td>-0.46</td></tr><tr><td>Kurtosis</td><td>0.21</td><td>-0.09</td><td>3.66</td><td>6.64</td></tr><tr><td colspan="5">Percentiles:</td></tr><tr><td>Min</td><td>0.13</td><td>0.24</td><td>-15.64</td><td>-18.64</td></tr><tr><td>5%</td><td>0.22</td><td>0.37</td><td>-3.03</td><td>-3.44</td></tr><tr><td>10%</td><td>0.26</td><td>0.44</td><td>-2.14</td><td>-2.26</td></tr><tr><td>25%</td><td>0.37</td><td>0.59</td><td>-0.94</td><td>-0.80</td></tr><tr><td>50%</td><td>0.64</td><td>0.91</td><td>0.33</td><td>0.49</td></tr><tr><td>75%</td><td>1.19</td><td>1.20</td><td>1.44</td><td>1.53</td></tr><tr><td>90%</td><td>1.44</td><td>1.41</td><td>2.37</td><td>2.61</td></tr><tr><td>95%</td><td>1.57</td><td>1.55</td><td>3.31</td><td>3.42</td></tr><tr><td>Max</td><td>4.06</td><td>3.16</td><td>8.81</td><td>13.68</td></tr><tr><td colspan="5">Autocorrelations:</td></tr><tr><td><eq>\rho_1</eq></td><td>91.25</td><td>86.73</td><td>5.39</td><td>25.63</td></tr><tr><td><eq>\rho_2</eq></td><td>88.59</td><td>81.89</td><td>-0.21</td><td>10.92</td></tr><tr><td><eq>\rho_3</eq></td><td>87.62</td><td>79.30</td><td>3.27</td><td>9.34</td></tr><tr><td><eq>\rho_4</eq></td><td>87.44</td><td>78.07</td><td>-2.03</td><td>4.94</td></tr><tr><td><eq>\rho_5</eq></td><td>87.03</td><td>76.47</td><td>-2.18</td><td>1.11</td></tr><tr><td><eq>\rho_6</eq></td><td>86.17</td><td>74.14</td><td>1.70</td><td>4.07</td></tr><tr><td><eq>\rho_7</eq></td><td>87.22</td><td>74.16</td><td>5.13</td><td>1.69</td></tr><tr><td><eq>\rho_8</eq></td><td>86.57</td><td>72.95</td><td>-7.15</td><td>-5.78</td></tr><tr><td><eq>\rho_9</eq></td><td>85.92</td><td>71.06</td><td>2.22</td><td>2.54</td></tr><tr><td><eq>\rho_{10}</eq></td><td>84.63</td><td>68.59</td><td>-2.34</td><td>-2.44</td></tr><tr><td>Box-Pierce <eq>Q_{10}</eq></td><td>13,723.0(0.000)</td><td>10,525.0(0.000)</td><td>23.0(0.010)</td><td>175.1(0.000)</td></tr></table>


Table 3: Summary statistics for value-weighted and equal-weighted turnover and return indexes of NYSE and AMEX ordinary common shares (CRSP share codes 10 and 11, excluding 37 stocks containing Z-errors in reported volume) for July 1962 to December 1996 (1,800 weeks) and subperiods. Turnover and returns are measured in percent per week and p-values for Box-Pierce statistics are reported in parentheses.


<table><tr><td>Statistic</td><td><eq>\tau^{VW}</eq></td><td><eq>\tau^{EW}</eq></td><td><eq>R^{VW}</eq></td><td><eq>R^{EW}</eq></td><td><eq>\tau^{VW}</eq></td><td><eq>\tau^{EW}</eq></td><td><eq>R^{VW}</eq></td><td><eq>R^{EW}</eq></td></tr><tr><td></td><td colspan="4">1962 to 1966 (234 weeks)</td><td colspan="4">1982 to 1986 (261 weeks)</td></tr><tr><td>Mean</td><td>0.25</td><td>0.57</td><td>0.23</td><td>0.30</td><td>1.20</td><td>1.11</td><td>0.37</td><td>0.39</td></tr><tr><td>Std. Dev.</td><td>0.07</td><td>0.21</td><td>1.29</td><td>1.54</td><td>0.30</td><td>0.29</td><td>2.01</td><td>1.93</td></tr><tr><td>Skewness</td><td>1.02</td><td>1.47</td><td>-0.35</td><td>-0.76</td><td>0.28</td><td>0.45</td><td>0.42</td><td>0.32</td></tr><tr><td>Kurtosis</td><td>0.80</td><td>2.04</td><td>1.02</td><td>2.50</td><td>0.14</td><td>-0.28</td><td>1.33</td><td>1.19</td></tr><tr><td></td><td colspan="4">1967 to 1971 (261 weeks)</td><td colspan="4">1987 to 1991 (261 weeks)</td></tr><tr><td>Mean</td><td>0.40</td><td>0.93</td><td>0.18</td><td>0.32</td><td>1.29</td><td>1.15</td><td>0.29</td><td>0.24</td></tr><tr><td>Std. Dev.</td><td>0.08</td><td>0.32</td><td>1.89</td><td>2.62</td><td>0.35</td><td>0.27</td><td>2.43</td><td>2.62</td></tr><tr><td>Skewness</td><td>0.17</td><td>0.57</td><td>0.42</td><td>0.40</td><td>2.20</td><td>2.15</td><td>-1.51</td><td>-2.06</td></tr><tr><td>Kurtosis</td><td>-0.42</td><td>-0.26</td><td>1.52</td><td>2.19</td><td>14.88</td><td>12.81</td><td>7.85</td><td>16.44</td></tr><tr><td></td><td colspan="4">1972 to 1976 (261 weeks)</td><td colspan="4">1992 to 1996 (261 weeks)</td></tr><tr><td>Mean</td><td>0.37</td><td>0.52</td><td>0.10</td><td>0.19</td><td>1.25</td><td>1.31</td><td>0.27</td><td>0.37</td></tr><tr><td>Std. Dev.</td><td>0.10</td><td>0.20</td><td>2.39</td><td>2.78</td><td>0.23</td><td>0.22</td><td>1.37</td><td>1.41</td></tr><tr><td>Skewness</td><td>0.93</td><td>1.44</td><td>-0.13</td><td>0.41</td><td>-0.06</td><td>-0.05</td><td>-0.38</td><td>-0.48</td></tr><tr><td>Kurtosis</td><td>1.57</td><td>2.59</td><td>0.35</td><td>1.12</td><td>-0.21</td><td>-0.24</td><td>1.00</td><td>1.30</td></tr><tr><td></td><td colspan="4">1977 to 1981 (261 weeks)</td><td></td><td></td><td></td><td></td></tr><tr><td>Mean</td><td>0.62</td><td>0.77</td><td>0.21</td><td>0.44</td><td></td><td></td><td></td><td></td></tr><tr><td>Std. Dev.</td><td>0.18</td><td>0.22</td><td>1.97</td><td>2.08</td><td></td><td></td><td></td><td></td></tr><tr><td>Skewness</td><td>0.29</td><td>0.62</td><td>-0.33</td><td>-1.01</td><td></td><td></td><td></td><td></td></tr><tr><td>Kurtosis</td><td>-0.58</td><td>-0.05</td><td>0.31</td><td>1.72</td><td></td><td></td><td></td><td></td></tr></table>


Table 4: Summary statistics for weekly value-weighted and equal-weighted turnover and return indexes of NYSE and AMEX ordinary common shares (CRSP share codes 10 and 11, excluding 37 stocks containing Z-errors in reported volume) for July 1962 to December 1996 (1,800 weeks) and subperiods. Turnover and returns are measured in percent per week and p-values for Box-Pierce statistics are reported in parentheses.


<table><tr><td>Regressor</td><td><eq>\tau^{VW}</eq></td><td><eq>\tau^{EW}</eq></td><td><eq>R^{VW}</eq></td><td><eq>R^{EW}</eq></td></tr><tr><td colspan="5">Daily: 1962 to 1996 (8,686 days)</td></tr><tr><td>MON</td><td>0.147(0.002)</td><td>0.178(0.002)</td><td>-0.061(0.019)</td><td>-0.095(0.019)</td></tr><tr><td>TUE</td><td>0.164(0.002)</td><td>0.192(0.002)</td><td>0.044(0.019)</td><td>0.009(0.018)</td></tr><tr><td>WED</td><td>0.170(0.002)</td><td>0.196(0.002)</td><td>0.112(0.019)</td><td>0.141(0.018)</td></tr><tr><td>THU</td><td>0.167(0.002)</td><td>0.196(0.002)</td><td>0.050(0.019)</td><td>0.118(0.018)</td></tr><tr><td>FRI</td><td>0.161(0.002)</td><td>0.188(0.002)</td><td>0.091(0.020)</td><td>0.207(0.018)</td></tr><tr><td colspan="5">Weekly: 1962 to 1996 (1,800 weeks)</td></tr><tr><td>Q1</td><td>0.842(0.025)</td><td>0.997(0.019)</td><td>0.369(0.102)</td><td>0.706(0.112)</td></tr><tr><td>Q2</td><td>0.791(0.024)</td><td>0.939(0.018)</td><td>0.232(0.097)</td><td>0.217(0.107)</td></tr><tr><td>Q3</td><td>0.741(0.023)</td><td>0.850(0.018)</td><td>0.201(0.095)</td><td>0.245(0.105)</td></tr><tr><td>Q4</td><td>0.807(0.024)</td><td>0.928(0.019)</td><td>0.203(0.099)</td><td>-0.019(0.110)</td></tr><tr><td>BOQ</td><td>-0.062(0.042)</td><td>-0.074(0.032)</td><td>-0.153(0.171)</td><td>-0.070(0.189)</td></tr><tr><td>EOQ</td><td>0.008(0.041)</td><td>-0.010(0.032)</td><td>-0.243(0.170)</td><td>-0.373(0.187)</td></tr><tr><td>BOY</td><td>-0.109(0.086)</td><td>-0.053(0.067)</td><td>0.179(0.355)</td><td>1.962(0.392)</td></tr><tr><td>EOY</td><td>-0.189(0.077)</td><td>-0.085(0.060)</td><td>0.755(0.319)</td><td>1.337(0.353)</td></tr></table>


Table 5: Seasonality regressions for daily and weekly value-weighted and equal-weighted turnover and return indexes of NYSE and AMEX ordinary common shares (CRSP share codes 10 and 11, excluding 37 stocks containing Z-errors in reported volume) from July 1962 to December 1996. Q1–Q4 are quarterly indicators, BOQ and EOQ are beginning-of-quarter and end-of-quarter indicators, and BOY and EOY are beginning-of-year and end-of-year indicators.


The subperiod regression results for the quarterly and annual indicators in Tables 7a and 7b are consistent with the findings for the entire sample period in Table 5: on average, turnover is slightly lower in third quarters, during the turn-of-the-quarter, and during the turn-of-the-year. 

## 3.2 Secular Trends and Detrending

It is well known that turnover is highly persistent. Table 3 shows the first 10 autocorrelations of turnover and returns and the corresponding Box-Pierce Q-statistics. Unlike returns, turnover is strongly autocorrelated, with autocorrelations that start at 91.25% and 86.73% for the value-weighted and equal-weighted turnover indexes, respectively, decaying very slowly to 84.63% and 68.59%, respectively, at lag 10. This slow decay suggests some kind of nonstationarity in turnover—perhaps a stochastic trend or unit root (see Hamilton (1994), for example)—and this is confirmed at the usual significance levels by applying the Kwiatkowski et al. (1992) Lagrange Multiplier test of stationarity versus a unit root to the two turnover indexes.<sup>13</sup> 

For these reasons, many empirical studies of volume use some form of detrending to induce stationarity. This usually involves either taking first diferences or estimating the trend and subtracting it from the raw data. To gauge the impact of various methods of detrending on the time-series properties of turnover, we report summary statistics of detrended turnover in Table 8 where we detrend according to the following six methods: 

<table><tr><td>Regressor</td><td><eq>\tau^{VW}</eq></td><td><eq>\tau^{EW}</eq></td><td><eq>R^{VW}</eq></td><td><eq>R^{EW}</eq></td><td><eq>\tau^{VW}</eq></td><td><eq>\tau^{EW}</eq></td><td><eq>R^{VW}</eq></td><td><eq>R^{EW}</eq></td></tr><tr><td></td><td colspan="4">1962 to 1966 (1,134 days)</td><td colspan="4">1980 to 1984 (1,264 days)</td></tr><tr><td>MON</td><td>0.050(0.001)</td><td>0.116(0.003)</td><td>-0.092(0.037)</td><td>-0.073(0.038)</td><td>0.224(0.004)</td><td>0.212(0.004)</td><td>-0.030(0.053)</td><td>-0.107(0.043)</td></tr><tr><td>TUE</td><td>0.053(0.001)</td><td>0.119(0.003)</td><td>0.046(0.037)</td><td>0.012(0.037)</td><td>0.251(0.004)</td><td>0.231(0.004)</td><td>0.070(0.051)</td><td>0.040(0.041)</td></tr><tr><td>WED</td><td>0.054(0.001)</td><td>0.122(0.003)</td><td>0.124(0.036)</td><td>0.142(0.037)</td><td>0.262(0.004)</td><td>0.239(0.004)</td><td>0.093(0.051)</td><td>0.117(0.041)</td></tr><tr><td>THU</td><td>0.054(0.001)</td><td>0.121(0.003)</td><td>0.032(0.037)</td><td>0.092(0.037)</td><td>0.258(0.004)</td><td>0.236(0.004)</td><td>0.111(0.052)</td><td>0.150(0.042)</td></tr><tr><td>FRI</td><td>0.051(0.001)</td><td>0.117(0.003)</td><td>0.121(0.037)</td><td>0.191(0.037)</td><td>0.245(0.004)</td><td>0.226(0.004)</td><td>0.122(0.052)</td><td>0.226(0.042)</td></tr><tr><td></td><td colspan="4">1967 to 1971 (1,234 days)</td><td colspan="4">1987 to 1991 (1,263 days)</td></tr><tr><td>MON</td><td>0.080(0.001)</td><td>0.192(0.005)</td><td>-0.157(0.045)</td><td>-0.135(0.056)</td><td>0.246(0.005)</td><td>0.221(0.004)</td><td>-0.040(0.073)</td><td>-0.132(0.062)</td></tr><tr><td>TUE</td><td>0.086(0.001)</td><td>0.200(0.005)</td><td>0.021(0.044)</td><td>0.001(0.054)</td><td>0.269(0.005)</td><td>0.241(0.004)</td><td>0.119(0.071)</td><td>0.028(0.059)</td></tr><tr><td>WED</td><td>0.087(0.001)</td><td>0.197(0.005)</td><td>0.156(0.046)</td><td>0.204(0.057)</td><td>0.276(0.005)</td><td>0.246(0.004)</td><td>0.150(0.071)</td><td>0.193(0.059)</td></tr><tr><td>THU</td><td>0.090(0.001)</td><td>0.205(0.005)</td><td>0.039(0.044)</td><td>0.072(0.055)</td><td>0.273(0.005)</td><td>0.246(0.004)</td><td>0.015(0.071)</td><td>0.108(0.060)</td></tr><tr><td>FRI</td><td>0.084(0.001)</td><td>0.198(0.005)</td><td>0.127(0.044)</td><td>0.221(0.055)</td><td>0.273(0.005)</td><td>0.237(0.004)</td><td>0.050(0.072)</td><td>0.156(0.060)</td></tr><tr><td></td><td colspan="4">1972 to 1976 (1,262 days)</td><td colspan="4">1992 to 1996 (1,265 days)</td></tr><tr><td>MON</td><td>0.069(0.001)</td><td>0.102(0.003)</td><td>-0.123(0.060)</td><td>-0.122(0.057)</td><td>0.232(0.003)</td><td>0.249(0.003)</td><td>0.117(0.036)</td><td>0.033(0.031)</td></tr><tr><td>TUE</td><td>0.080(0.001)</td><td>0.110(0.003)</td><td>0.010(0.059)</td><td>-0.031(0.056)</td><td>0.261(0.003)</td><td>0.276(0.003)</td><td>0.009(0.035)</td><td>0.003(0.030)</td></tr><tr><td>WED</td><td>0.081(0.001)</td><td>0.111(0.003)</td><td>0.066(0.058)</td><td>0.063(0.055)</td><td>0.272(0.003)</td><td>0.283(0.003)</td><td>0.080(0.035)</td><td>0.105(0.030)</td></tr><tr><td>THU</td><td>0.081(0.001)</td><td>0.111(0.003)</td><td>0.087(0.059)</td><td>0.122(0.056)</td><td>0.266(0.003)</td><td>0.281(0.003)</td><td>0.050(0.035)</td><td>0.138(0.030)</td></tr><tr><td>FRI</td><td>0.076(0.001)</td><td>0.106(0.003)</td><td>0.056(0.059)</td><td>0.215(0.056)</td><td>0.259(0.003)</td><td>0.264(0.003)</td><td>0.026(0.035)</td><td>0.164(0.030)</td></tr><tr><td></td><td colspan="4">1977 to 1981 (1,263 days)</td><td></td><td></td><td></td><td></td></tr><tr><td>MON</td><td>0.118(0.003)</td><td>0.153(0.003)</td><td>-0.104(0.051)</td><td>-0.127(0.050)</td><td></td><td></td><td></td><td></td></tr><tr><td>TUE</td><td>0.131(0.002)</td><td>0.160(0.003)</td><td>0.029(0.050)</td><td>0.007(0.048)</td><td></td><td></td><td></td><td></td></tr><tr><td>WED</td><td>0.135(0.002)</td><td>0.166(0.003)</td><td>0.116(0.049)</td><td>0.166(0.048)</td><td></td><td></td><td></td><td></td></tr><tr><td>THU</td><td>0.134(0.002)</td><td>0.164(0.003)</td><td>0.018(0.050)</td><td>0.143(0.048)</td><td></td><td></td><td></td><td></td></tr><tr><td>FRI</td><td>0.126(0.002)</td><td>0.158(0.003)</td><td>0.136(0.050)</td><td>0.277(0.049)</td><td></td><td></td><td></td><td></td></tr><tr><td></td><td colspan="4">1962 to 1966 (234 weeks)</td><td colspan="4">1972 to 1976 (261 weeks)</td></tr><tr><td>Q1</td><td>0.261(0.011)</td><td>0.649(0.030)</td><td>0.262(0.192)</td><td>0.600(0.224)</td><td>0.441(0.012)</td><td>0.677(0.025)</td><td>0.513(0.325)</td><td>1.079(0.355)</td></tr><tr><td>Q2</td><td>0.265(0.010)</td><td>0.615(0.029)</td><td>0.072(0.184)</td><td>0.023(0.215)</td><td>0.364(0.012)</td><td>0.513(0.024)</td><td>0.019(0.308)</td><td>-0.323(0.337)</td></tr><tr><td>Q3</td><td>0.229(0.009)</td><td>0.478(0.026)</td><td>0.185(0.165)</td><td>0.187(0.193)</td><td>0.334(0.012)</td><td>0.436(0.023)</td><td>-0.267(0.306)</td><td>-0.166(0.335)</td></tr><tr><td>Q4</td><td>0.272(0.010)</td><td>0.595(0.027)</td><td>0.413(0.173)</td><td>0.363(0.202)</td><td>0.385(0.012)</td><td>0.500(0.024)</td><td>0.083(0.319)</td><td>-0.416(0.349)</td></tr><tr><td>BOQ</td><td>-0.026(0.017)</td><td>-0.055(0.049)</td><td>0.388(0.310)</td><td>0.304(0.364)</td><td>-0.034(0.021)</td><td>-0.057(0.042)</td><td>-0.569(0.543)</td><td>-0.097(0.593)</td></tr><tr><td>EOQ</td><td>0.017(0.017)</td><td>0.028(0.048)</td><td>-0.609(0.304)</td><td>-0.579(0.357)</td><td>0.013(0.021)</td><td>-0.013(0.042)</td><td>0.301(0.554)</td><td>0.003(0.606)</td></tr><tr><td>BOY</td><td>-0.008(0.037)</td><td>-0.074(0.107)</td><td>0.635(0.674)</td><td>2.009(0.790)</td><td>-0.047(0.042)</td><td>-0.024(0.084)</td><td>1.440(1.098)</td><td>4.553(1.200)</td></tr><tr><td>EOY</td><td>-0.064(0.030)</td><td>-0.049(0.087)</td><td>0.190(0.548)</td><td>0.304(0.642)</td><td>-0.101(0.040)</td><td>-0.019(0.081)</td><td>0.300(1.055)</td><td>1.312(1.153)</td></tr><tr><td></td><td colspan="4">1967 to 1971 (261 weeks)</td><td colspan="4">1977 to 1981 (261 weeks)</td></tr><tr><td>Q1</td><td>0.421(0.010)</td><td>0.977(0.042)</td><td>0.216(0.258)</td><td>0.463(0.355)</td><td>0.613(0.024)</td><td>0.738(0.030)</td><td>-0.034(0.269)</td><td>0.368(0.280)</td></tr><tr><td>Q2</td><td>0.430(0.010)</td><td>1.022(0.041)</td><td>-0.169(0.247)</td><td>-0.118(0.341)</td><td>0.629(0.023)</td><td>0.787(0.029)</td><td>0.608(0.255)</td><td>0.948(0.266)</td></tr><tr><td>Q3</td><td>0.370(0.010)</td><td>0.840(0.040)</td><td>0.307(0.245)</td><td>0.512(0.338)</td><td>0.637(0.023)</td><td>0.805(0.029)</td><td>0.309(0.253)</td><td>0.535(0.264)</td></tr><tr><td>Q4</td><td>0.415(0.010)</td><td>0.928(0.042)</td><td>0.097(0.255)</td><td>0.000(0.352)</td><td>0.643(0.024)</td><td>0.779(0.030)</td><td>0.117(0.265)</td><td>-0.024(0.276)</td></tr><tr><td>BOQ</td><td>-0.029(0.017)</td><td>-0.097(0.070)</td><td>0.407(0.425)</td><td>0.327(0.586)</td><td>-0.012(0.042)</td><td>-0.023(0.052)</td><td>-0.200(0.458)</td><td>-0.322(0.478)</td></tr><tr><td>EOQ</td><td>-0.011(0.018)</td><td>-0.051(0.073)</td><td>0.076(0.442)</td><td>0.029(0.610)</td><td>-0.011(0.041)</td><td>-0.009(0.051)</td><td>-0.588(0.449)</td><td>-0.716(0.469)</td></tr><tr><td>BOY</td><td>-0.021(0.037)</td><td>0.111(0.151)</td><td>-0.751(0.919)</td><td>0.812(1.269)</td><td>-0.028(0.083)</td><td>0.074(0.103)</td><td>0.412(0.912)</td><td>1.770(0.952)</td></tr><tr><td>EOY</td><td>-0.022(0.033)</td><td>0.063(0.133)</td><td>0.782(0.811)</td><td>1.513(1.119)</td><td>-0.144(0.079)</td><td>-0.123(0.098)</td><td>1.104(0.868)</td><td>1.638(0.906)</td></tr><tr><td></td><td colspan="4">1982 to 1986 (261 weeks)</td><td colspan="4">1992 to 1996 (261 weeks)</td></tr><tr><td>Q1</td><td>1.258(0.039)</td><td>1.177(0.039)</td><td>0.389(0.274)</td><td>0.524(0.262)</td><td>1.362(0.029)</td><td>1.432(0.028)</td><td>0.388(0.182)</td><td>0.687(0.183)</td></tr><tr><td>Q2</td><td>1.173(0.037)</td><td>1.115(0.037)</td><td>0.313(0.262)</td><td>0.356(0.251)</td><td>1.253(0.028)</td><td>1.302(0.027)</td><td>0.328(0.176)</td><td>0.292(0.176)</td></tr><tr><td>Q3</td><td>1.188(0.037)</td><td>1.058(0.037)</td><td>0.268(0.262)</td><td>0.164(0.251)</td><td>1.170(0.028)</td><td>1.223(0.027)</td><td>0.521(0.174)</td><td>0.570(0.175)</td></tr><tr><td>Q4</td><td>1.320(0.039)</td><td>1.190(0.039)</td><td>0.625(0.274)</td><td>0.526(0.262)</td><td>1.298(0.029)</td><td>1.353(0.028)</td><td>0.322(0.182)</td><td>0.219(0.183)</td></tr><tr><td>BOQ</td><td>-0.123(0.065)</td><td>-0.132(0.065)</td><td>-0.329(0.462)</td><td>-0.336(0.442)</td><td>-0.058(0.051)</td><td>-0.078(0.050)</td><td>-0.890(0.321)</td><td>-0.705(0.322)</td></tr><tr><td>EOQ</td><td>-0.042(0.065)</td><td>-0.052(0.065)</td><td>0.222(0.462)</td><td>0.158(0.442)</td><td>0.036(0.047)</td><td>0.006(0.046)</td><td>-0.567(0.297)</td><td>-0.840(0.298)</td></tr><tr><td>BOY</td><td>-0.202(0.139)</td><td>-0.114(0.139)</td><td>-0.395(0.985)</td><td>1.033(0.942)</td><td>-0.149(0.105)</td><td>-0.102(0.103)</td><td>0.012(0.663)</td><td>1.857(0.664)</td></tr><tr><td>EOY</td><td>-0.280(0.121)</td><td>-0.158(0.122)</td><td>-0.477(0.861)</td><td>-0.160(0.823)</td><td>-0.348(0.090)</td><td>-0.220(0.088)</td><td>1.204(0.568)</td><td>1.753(0.570)</td></tr><tr><td></td><td colspan="4">1987 to 1991 (261 weeks)</td><td></td><td></td><td></td><td></td></tr><tr><td>Q1</td><td>1.416(0.046)</td><td>1.254(0.035)</td><td>0.823(0.330)</td><td>1.202(0.343)</td><td></td><td></td><td></td><td></td></tr><tr><td>Q2</td><td>1.317(0.044)</td><td>1.159(0.034)</td><td>0.424(0.313)</td><td>0.305(0.325)</td><td></td><td></td><td></td><td></td></tr><tr><td>Q3</td><td>1.252(0.043)</td><td>1.105(0.034)</td><td>0.099(0.310)</td><td>-0.081(0.323)</td><td></td><td></td><td></td><td></td></tr><tr><td>Q4</td><td>1.317(0.045)</td><td>1.160(0.035)</td><td>-0.228(0.325)</td><td>-0.787(0.338)</td><td></td><td></td><td></td><td></td></tr><tr><td>BOQ</td><td>-0.108(0.078)</td><td>-0.060(0.061)</td><td>0.117(0.562)</td><td>0.316(0.584)</td><td></td><td></td><td></td><td></td></tr><tr><td>EOQ</td><td>-0.003(0.077)</td><td>-0.013(0.060)</td><td>-0.548(0.551)</td><td>-0.655(0.573)</td><td></td><td></td><td></td><td></td></tr><tr><td>BOY</td><td>-0.293(0.156)</td><td>-0.207(0.121)</td><td>-0.118(1.120)</td><td>1.379(1.165)</td><td></td><td></td><td></td><td></td></tr><tr><td>EOY</td><td>-0.326(0.148)</td><td>-0.104(0.115)</td><td>2.259(1.065)</td><td>3.037(1.108)</td><td></td><td></td><td></td><td></td></tr></table>


Table 6: Seasonality regressions over subperiods for daily value-weighted and equal-weighted turnover and return indexes of NYSE or AMEX ordinary common shares (CRSP share codes 10 and 11, excluding 37 stocks containing Z-errors in reported volume) for subperiods of the sample period from July 1962 to December 1996.


Table 7a: Seasonality regressions for weekly value-weighted and equal-weighted turnover and return indexes of NYSE or AMEX ordinary common shares (CRSP share codes 10 and 11, excluding 37 stocks containing Z-errors in reported volume) for subperiods of the sample period from July 1962 to December 1991. Q1–Q4 are quarterly indicators, BOQ and EOQ are beginning-of-quarter and end-of-quarter indicators, and BOY and EOY are beginning-of-year and end-of-year indicators. 

$$
\tau_ {1 t} ^ {d} = \tau_ {t} - \left(\hat {\alpha} _ {1} + \hat {\beta} _ {1} t\right)\tag{7a}
$$

$$
\tau_ {2 t} ^ {d} = \log \tau_ {t} - \left(\hat {\alpha} _ {2} + \hat {\beta} _ {2} t\right)\tag{7b}
$$

$$
\tau_ {3 t} ^ {d} = \tau_ {t} - \tau_ {t - 1}\tag{7c}
$$

$$
\tau_ {4 t} ^ {d} = \frac {\tau_ {t}}{(\tau_ {t - 1} + \tau_ {t - 2} + \tau_ {t - 3} + \tau_ {t - 4}) / 4}\tag{7d}
$$

$$
\tau_ {5 t} ^ {d} = \tau_ {t} - \left(\hat {\alpha} _ {4} + \hat {\beta} _ {3, 1} t + \hat {\beta} _ {3, 2} t ^ {2} + \right.
$$

$$
\hat {\beta} _ {3, 3} \mathrm{DEC1} _ {t} + \hat {\beta} _ {3, 4} \mathrm{DEC2} _ {t} + \hat {\beta} _ {3, 5} \mathrm{DEC3} _ {t} + \hat {\beta} _ {3, 6} \mathrm{DEC4} _ {t} +
$$

$$
\hat {\beta} _ {3, 7} \mathrm{JAN1} _ {t} + \hat {\beta} _ {3, 8} \mathrm{JAN2} _ {t} + \hat {\beta} _ {3, 9} \mathrm{JAN3} _ {t} + \hat {\beta} _ {3, 1 0} \mathrm{JAN4} _ {t} +
$$

$$
\left. \hat {\beta} _ {3, 1 1} \mathrm{MAR} _ {t} + \hat {\beta} _ {3, 1 2} \mathrm{APR} _ {t} + \dots + \hat {\beta} _ {3, 1 9} \mathrm{NOV} _ {t}\right)\tag{7e}
$$

$$
\tau_ {6 t} ^ {d} = \tau_ {t} - \hat {\mathrm{K}} (\tau_ {t})\tag{7f}
$$

where (7) denotes linear detrending, (7) denotes log-linear detrending, (7) denotes firstdiferencing, (7) denotes a four-lag moving-average normalization, (7) denotes linear-quadratic detrending and deseasonalization (in the spirit of Gallant, Rossi, and Tauchen (1994)),<sup>14</sup> and (7) denotes nonparametric detrending via kernel regression (where the bandwidth is chosen optimally via cross validation). 

The summary statistics in Table 8 show that the detrending method can have a substantial impact on the time-series properties of detrended turnover. For example, the skewness of detrended value-weighted turnover varies from 0.09 (log-linear) to 1.77 (kernel), and the kurtosis varies from −0.20 (log-linear) to 29.38 (kernel). Linear, log-linear, and Gallant, Rossi, and Tauchen (GRT) detrending seem to do little to eliminate the persistence in turnover, yielding detrended series with large positive autocorrelation coeficients that decay slowly from lags 1 to 10. However, first-diferenced value-weighted turnover has an autocorrelation coeficient of −34.94% at lag 1, which becomes positive at lag 4, and then alternates sign from lags 6 through 10. In contrast, kernel-detrended value-weighted turnover has an autocorrelation of 23.11% at lag 1, which becomes negative at lag 3 and remains negative through lag 10. Similar disparities are also observed for the various detrended equal-weighted turnover series. 

<table><tr><td>Statistic</td><td>Raw</td><td>Linear</td><td>Log Linear</td><td>First Diff.</td><td>MA(4) Ratio</td><td>GRT</td><td>Kernel</td><td>Raw</td><td>Linear</td><td>Log Linear</td><td>First Diff.</td><td>MA(4) Ratio</td><td>GRT</td><td>Kernel</td></tr><tr><td></td><td colspan="7">Value-Weighted Turnover Index</td><td colspan="7">Equal-Weighted Turnover Index</td></tr><tr><td><eq>R^2</eq>(%)</td><td>—</td><td>70.6</td><td>78.6</td><td>82.6</td><td>81.9</td><td>72.3</td><td>88.6</td><td>—</td><td>36.9</td><td>37.2</td><td>73.6</td><td>71.9</td><td>42.8</td><td>78.3</td></tr><tr><td>Mean</td><td>0.78</td><td>0.00</td><td>0.00</td><td>0.00</td><td>1.01</td><td>0.00</td><td>0.00</td><td>0.91</td><td>0.00</td><td>0.00</td><td>0.00</td><td>1.01</td><td>0.00</td><td>0.00</td></tr><tr><td>Std.Dev.</td><td>0.48</td><td>0.26</td><td>0.31</td><td>0.20</td><td>0.20</td><td>0.25</td><td>0.16</td><td>0.37</td><td>0.30</td><td>0.35</td><td>0.19</td><td>0.20</td><td>0.28</td><td>0.17</td></tr><tr><td>Skewness</td><td>0.66</td><td>1.57</td><td>0.09</td><td>0.79</td><td>0.73</td><td>1.69</td><td>1.77</td><td>0.38</td><td>0.90</td><td>0.00</td><td>0.59</td><td>0.67</td><td>1.06</td><td>0.92</td></tr><tr><td>Kurtosis</td><td>0.21</td><td>10.84</td><td>-0.20</td><td>17.75</td><td>3.02</td><td>11.38</td><td>29.38</td><td>-0.09</td><td>1.80</td><td>0.44</td><td>7.21</td><td>2.51</td><td>2.32</td><td>6.67</td></tr><tr><td colspan="15">Percentiles:</td></tr><tr><td>Min</td><td>0.13</td><td>-0.69</td><td>-0.94</td><td>-1.55</td><td>0.45</td><td>-0.61</td><td>-0.78</td><td>0.24</td><td>-0.62</td><td>-1.09</td><td>-0.78</td><td>0.44</td><td>-0.59</td><td>-0.59</td></tr><tr><td>5%</td><td>0.22</td><td>-0.34</td><td>-0.51</td><td>-0.30</td><td>0.69</td><td>-0.32</td><td>-0.26</td><td>0.37</td><td>-0.44</td><td>-0.63</td><td>-0.32</td><td>0.70</td><td>-0.38</td><td>-0.27</td></tr><tr><td>10%</td><td>0.26</td><td>-0.29</td><td>-0.38</td><td>-0.19</td><td>0.76</td><td>-0.28</td><td>-0.15</td><td>0.44</td><td>-0.36</td><td>-0.43</td><td>-0.21</td><td>0.76</td><td>-0.32</td><td>-0.20</td></tr><tr><td>25%</td><td>0.37</td><td>-0.18</td><td>-0.21</td><td>-0.08</td><td>0.89</td><td>-0.17</td><td>-0.06</td><td>0.59</td><td>-0.19</td><td>-0.20</td><td>-0.09</td><td>0.88</td><td>-0.20</td><td>-0.10</td></tr><tr><td>50%</td><td>0.65</td><td>-0.01</td><td>-0.02</td><td>-0.00</td><td>1.00</td><td>-0.02</td><td>0.00</td><td>0.91</td><td>-0.04</td><td>-0.00</td><td>-0.00</td><td>1.01</td><td>-0.05</td><td>-0.01</td></tr><tr><td>75%</td><td>1.19</td><td>0.13</td><td>0.23</td><td>0.07</td><td>1.12</td><td>0.12</td><td>0.06</td><td>1.20</td><td>0.16</td><td>0.20</td><td>0.09</td><td>1.12</td><td>0.16</td><td>0.09</td></tr><tr><td>90%</td><td>1.44</td><td>0.30</td><td>0.41</td><td>0.20</td><td>1.25</td><td>0.29</td><td>0.16</td><td>1.41</td><td>0.42</td><td>0.46</td><td>0.21</td><td>1.25</td><td>0.38</td><td>0.21</td></tr><tr><td>95%</td><td>1.57</td><td>0.45</td><td>0.50</td><td>0.31</td><td>1.35</td><td>0.46</td><td>0.23</td><td>1.55</td><td>0.55</td><td>0.63</td><td>0.32</td><td>1.35</td><td>0.54</td><td>0.28</td></tr><tr><td>Max</td><td>4.06</td><td>2.95</td><td>1.38</td><td>2.45</td><td>2.48</td><td>2.91</td><td>2.36</td><td>3.16</td><td>2.06</td><td>1.11</td><td>1.93</td><td>2.44</td><td>2.08</td><td>1.73</td></tr><tr><td colspan="15">Autocorrelations:</td></tr><tr><td><eq>\rho_1</eq></td><td>91.25</td><td>70.15</td><td>74.23</td><td>-34.94</td><td>22.97</td><td>70.24</td><td>23.11</td><td>86.73</td><td>79.03</td><td>83.07</td><td>-31.94</td><td>29.41</td><td>77.80</td><td>39.23</td></tr><tr><td><eq>\rho_2</eq></td><td>88.59</td><td>61.21</td><td>66.17</td><td>-9.70</td><td>-6.48</td><td>64.70</td><td>0.54</td><td>81.89</td><td>71.46</td><td>77.27</td><td>-8.69</td><td>0.54</td><td>71.60</td><td>17.95</td></tr><tr><td><eq>\rho_3</eq></td><td>87.62</td><td>58.32</td><td>63.78</td><td>-4.59</td><td>-19.90</td><td>60.78</td><td>-6.21</td><td>79.30</td><td>67.58</td><td>74.25</td><td>-5.07</td><td>-13.79</td><td>66.89</td><td>8.05</td></tr><tr><td><eq>\rho_4</eq></td><td>87.44</td><td>58.10</td><td>63.86</td><td>1.35</td><td>-20.41</td><td>60.96</td><td>-5.78</td><td>78.07</td><td>65.84</td><td>72.60</td><td>1.45</td><td>-16.97</td><td>65.14</td><td>4.80</td></tr><tr><td><eq>\rho_5</eq></td><td>87.03</td><td>56.79</td><td>62.38</td><td>2.58</td><td>-6.12</td><td>60.31</td><td>-7.79</td><td>76.47</td><td>63.41</td><td>70.64</td><td>2.68</td><td>-4.87</td><td>62.90</td><td>-0.11</td></tr><tr><td><eq>\rho_6</eq></td><td>86.17</td><td>54.25</td><td>59.37</td><td>-10.96</td><td>-4.35</td><td>58.78</td><td>-12.93</td><td>74.14</td><td>59.95</td><td>67.29</td><td>-8.79</td><td>-4.23</td><td>60.03</td><td>-7.54</td></tr><tr><td><eq>\rho_7</eq></td><td>87.22</td><td>58.20</td><td>60.97</td><td>9.80</td><td>4.54</td><td>61.46</td><td>-1.09</td><td>74.16</td><td>60.17</td><td>66.27</td><td>4.60</td><td>0.17</td><td>59.28</td><td>-3.95</td></tr><tr><td><eq>\rho_8</eq></td><td>86.57</td><td>56.30</td><td>59.83</td><td>-0.10</td><td>1.78</td><td>59.39</td><td>-4.29</td><td>72.95</td><td>58.45</td><td>64.76</td><td>2.52</td><td>-0.37</td><td>57.62</td><td>-5.71</td></tr><tr><td><eq>\rho_9</eq></td><td>85.92</td><td>54.54</td><td>57.87</td><td>3.73</td><td>-2.43</td><td>59.97</td><td>-7.10</td><td>71.06</td><td>55.67</td><td>62.54</td><td>2.25</td><td>-2.27</td><td>56.48</td><td>-10.30</td></tr><tr><td><eq>\rho_{10}</eq></td><td>84.63</td><td>50.45</td><td>53.57</td><td>-11.95</td><td>-13.46</td><td>55.85</td><td>-15.86</td><td>68.59</td><td>51.93</td><td>58.81</td><td>-10.05</td><td>-10.48</td><td>53.06</td><td>-17.59</td></tr></table>


T<sub>a</sub>bl<sub>e</sub> 8 <sub>:</sub> I<sub>mpac</sub>t <sub>o</sub>f d<sub>e</sub>t<sub>ren</sub>di<sub>ng</sub> <sub>on</sub> th<sub>e</sub> <sub>s</sub>t <sub>a</sub>ti<sub>s</sub>ti<sub>ca</sub>l <sub>proper</sub>ti<sub>es o</sub>f <sub>wee</sub>kl<sub>y</sub> <sub>va</sub>l<sub>ue</sub>-<sub>we</sub>i<sub>g</sub>ht<sub>e</sub>d <sub>an</sub>d <sub>equa</sub>l-<sub>we</sub>i<sub>g</sub>ht<sub>e</sub>d t<sub>urnover</sub> i<sub>n</sub>d<sub>exes</sub> <sub>o</sub>f NYSE and AMEX ordinary common shares ( CRSP share codes 1 0 and 1 1 excluding 37 stocks containing Z-errors in reported volume) for July 1 962 to December 1 996 ( 1 800 weeks) <sub>.</sub> Six detrending metho ds are used : linear log-linear first diferencing <sub>norma</sub>li<sub>za</sub>ti<sub>on</sub> b<sub>y</sub> th<sub>e</sub> t<sub>ra</sub>ili<sub>ng</sub> f<sub>our</sub>-<sub>wee</sub>k <sub>mov</sub>i<sub>ng average</sub> li<sub>near</sub>-<sub>qua</sub>d<sub>ra</sub>ti<sub>c an</sub>d <sub>seasona</sub>l d<sub>e</sub>t<sub>ren</sub>di<sub>ng propose</sub>d b<sub>y</sub> G<sub>a</sub>ll<sub>an</sub>t R<sub>oss</sub>i and Tauchen ( 1 992 ) ( GRT) and kernel regression <sub>.</sub>


Despite the fact that the $R ^ { 2 } \mathrm { ` s }$ of the six detrending methods are comparable for the valueweighted turnover index—ranging from 70.6% to 88.6%—the basic time-series properties vary considerably from one detrending method to the next.<sup>15</sup> To visualize the impact that various detrending methods can have on turnover, compare the various plots of detrended value-weighted turnover in Figure 2, and detrended equal-weighted turnover in Figure 3.<sup>16</sup> Even linear and log-linear detrending yield diferences that are visually easy to detect: linear detrended turnover is smoother at the start of the sample and more variable towards the end, whereas loglinearly detrended turnover is equally variable but with lower-frequency fluctuations. The moving-average series looks like white noise, the log-linear series seems to possess a periodic component, and the remaining series seem heteroskedastic. 

For these reasons, we shall continue to use raw turnover rather than its first diference or any other detrended turnover series in much of our empirical analysis (the sole exception is the eigenvalue decomposition of the first diferences of turnover in Table 14). To address the problem of the apparent time trend and other nonstationarities in raw turnover, the empirical analysis in the rest of the chapter is conducted within five-year subperiods only (the exploratory data analysis of this section contains entire-sample results primarily for completeness).<sup>17</sup> This is no doubt a controversial choice and, therefore, requires some justification. 

From a purely statistical point of view, a nonstationary time series is nonstationary over any finite interval—shortening the sample period cannot induce stationarity. Moreover, a shorter sample period increases the impact of sampling errors and reduces the power of statistical tests against most alternatives. 

However, from an empirical point of view, confining our attention to five-year subperiods is perhaps the best compromise between letting the data “speak for themselves” and imposing 

$$
R _ {j} ^ {2} \equiv 1 - \frac {\sum_ {t} (\tau_ {j t} ^ {d} - \overline {{\tau}} _ {j} ^ {d}) ^ {2}}{\sum_ {t} (\tau_ {t} - \overline {{\tau}}) ^ {2}}.
$$

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/f77f27b530c3e5d3b1e171a891ad1db08609032a315170345eb5ffff700b3224.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/52d09623627e1a46af82370a0477aa7f3bbf27e2945d289502c708bc13d05d31.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/a54f4661dbc5db7671b841e2da615861f97958037dfda24783ea36cf1784d403.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/af64d8762814fe3bdf1087cf6b08bbfba0845d290d80be3b13810e9278c0350a.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/28509579831952d13cabbef12db338a90456e23d42b81d36c9cf0b7e2b7a9242.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/270d6f18e764acaf5dc2ba796ee43c9c7163b80538dcfc80d229072137882ed7.jpg)



Figure 2: Raw and Detrended Weekly Value-Weighted Turnover Indexes, 1962 to 1996. 26


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/692c31a06ef6ca0912f82bbc65edb5838c64fa5a3028b7f7829bf57c042e12ec.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/cadec2fc93e401503aec8d3392053f16c21d0fc9c915d959bf10666beb2498e1.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/d5df3cf32d7b5d9f7b8954112394f5b2ada30e0f75a5c00d0b29a6c15bec6a25.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/17aa32b17dcd3f7d7e47b69a099cc03808ef3490ec0b0f0d068e6f877b8d8086.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/eb1aab8617cf05edac59f0d5d074ebaab9dc51b3ed20d7ae566e0c0b61ed0799.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/8f79ef64bbcbc0534341b946ae9108dd1d275db2c3d23c98f2d2aa6d22c2928d.jpg)



Figure 3: Raw and Detrended Weekly Equal-Weighted Turnover Indexes, 1962 to 1996. 27


suficient structure to perform meaningful statistical inference. We have very little confidence in our current understanding of the trend component of turnover, yet a well-articulated model of the trend is a pre-requisite to detrending the data. Rather than filter our data through a specific trend process that others might not find as convincing, we choose instead to analyze the data with methods that require minimal structure, yielding results that may be of broader interest than those of a more structured analysis.<sup>18</sup> 

Of course, some structure is necessary for conducting any kind of statistical inference. For example, we must assume that the mechanisms governing turnover is relatively stable over five-year subperiods, otherwise even the subperiod inferences may be misleading. Nevertheless, for our current purposes—exploratory data analysis and tests of the implications of portfolio theory and intertemporal capital asset pricing models—the benefits of focusing on subperiods are likely to outweigh the costs of larger sampling errors. 

## 4 Cross-Sectional Properties

To develop a sense for cross-sectional diferences in turnover over the sample period, we turn our attention from turnover indexes to the turnover of individual securities. Figure 4 provides a compact graphical representation of the cross section of turnover: Figure 4a plots the deciles for the turnover cross-section—nine points, representing the 10-th percentile, the 20-th percentile, and so on—for each of the 1,800 weeks in the sample period; Figure 4b simplifies this by plotting the deciles of the cross section of average turnover, averaged within each year; and Figures 4c and 4d plot the same data but on a logarithmic scale. 

Figures 4a–b show that while the median turnover (the horizontal bars with vertical sides in Figure 4b) is relatively stable over time—fluctuating between 0.2% and just over 1% over the 1962–1996 sample period—there is considerable variation in the cross-sectional dispersion over time. The range of turnover is relatively narrow in the early 1960’s, with 90% of the values falling between 0% and 1.5%, but there is a dramatic increase in the late 1960’s, with the 90-th percentile approaching 3% at times. The cross-sectional variation of turnover declines sharply in the mid-1970’s and then begins a steady increase until a peak in 1987, followed by a decline and then a gradual increase until 1996. 

The logarithmic plots in Figures 4c–d seem to suggest that the cross-sectional distribution of log-turnover is similar over time up to a location parameter. This implies a potentially useful statistical or “reduced-form” description of the cross-sectional distribution of turnover: an identically distributed random variable multiplied by a time-varying scale factor. 

To explore the dynamics of the cross section of turnover, we ask the following question: if a stock has high turnover this week, how likely will it continue to be a high-turnover stock next week? Is turnover persistent or are there reversals from one week to the next? 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/2f1bbd2aa1c104efc3cf7f229e1d028cc0fd4c8ce69bc02e7443da88100b241a.jpg)



( a )



Deci les of Log (Weekly Tu rnove r)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/615cd827a2309e9de3656733300a8b1ce4e3ef9a3fa037d119ac2f497e237aed.jpg)


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/1ada979835676d62fc32ed44aaa553b8b5ef83c42b3ad4256c8b0fb4c0d4d27a.jpg)



( c )



( b )



Deci les of Log (Weekly Tu rnove r (Ave raged An n ual ly))


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/8bf80029-4e28-449e-a16e-8c6803631c39/b346322476477452e02a1f9e4dd3bf54535b83c9a75223dc8e450364b9f3cf38.jpg)



( d )



Fi<sub>gure</sub> 4 <sub>:</sub> D<sub>ec</sub>il<sub>es</sub> <sub>o</sub>f <sub>wee</sub>kl<sub>y</sub> t<sub>urnover</sub> <sub>an</sub>d th<sub>e</sub> <sub>na</sub>t<sub>ura</sub>l l<sub>oar</sub>ith<sub>m</sub> <sub>o</sub>f <sub>wee</sub>kl<sub>y</sub> t<sub>urnover ,</sub> 1 962 t<sub>o</sub> 1 996 <sub>.</sub>


To answer these questions, Table 9a reports the estimated transition probabilities for turnover deciles in adjacent weeks. For example, the first entry of the first row—54.74— implies that 54.74% of the stocks that have turnover in the first decile this week will, on average, still be in the first turnover-decile next week. The next entry—21.51—implies that 21.51% of the stocks in the first turnover-decile this week will, on average, be in the second turnover-decile next week. 

<table><tr><td rowspan="2" colspan="2">TURNOVER TRANSITION</td><td colspan="10">Next Week Decile</td></tr><tr><td>0-10</td><td>10-20</td><td>20-30</td><td>30-40</td><td>40-50</td><td>50-60</td><td>60-70</td><td>70-80</td><td>80-90</td><td>90-100</td></tr><tr><td rowspan="10">This Week</td><td>0-10</td><td>54.74(0.12)</td><td>21.51(0.06)</td><td>9.82(0.05)</td><td>5.32(0.04)</td><td>3.17(0.03)</td><td>2.02(0.03)</td><td>1.31(0.02)</td><td>0.93(0.02)</td><td>0.66(0.01)</td><td>0.46(0.01)</td></tr><tr><td>10-20</td><td>22.12(0.06)</td><td>28.77(0.10)</td><td>19.36(0.06)</td><td>11.48(0.05)</td><td>6.93(0.05)</td><td>4.42(0.04)</td><td>2.95(0.03)</td><td>1.91(0.03)</td><td>1.26(0.02)</td><td>0.75(0.02)</td></tr><tr><td>20-30</td><td>10.01(0.05)</td><td>20.09(0.07)</td><td>22.37(0.09)</td><td>17.19(0.06)</td><td>11.43(0.05)</td><td>7.50(0.05)</td><td>4.91(0.04)</td><td>3.22(0.03)</td><td>2.05(0.03)</td><td>1.16(0.02)</td></tr><tr><td>30-40</td><td>5.31(0.04)</td><td>11.92(0.05)</td><td>17.91(0.07)</td><td>19.70(0.08)</td><td>16.21(0.06)</td><td>11.49(0.05)</td><td>7.69(0.05)</td><td>4.97(0.04)</td><td>3.09(0.03)</td><td>1.65(0.02)</td></tr><tr><td>40-50</td><td>3.15(0.04)</td><td>7.15(0.05)</td><td>12.18(0.05)</td><td>16.81(0.06)</td><td>18.47(0.08)</td><td>15.77(0.06)</td><td>11.53(0.05)</td><td>7.74(0.05)</td><td>4.75(0.04)</td><td>2.40(0.03)</td></tr><tr><td>50-60</td><td>1.94(0.03)</td><td>4.42(0.04)</td><td>7.82(0.05)</td><td>12.22(0.05)</td><td>16.59(0.06)</td><td>18.37(0.08)</td><td>16.02(0.06)</td><td>11.64(0.05)</td><td>7.33(0.04)</td><td>3.60(0.03)</td></tr><tr><td>60-70</td><td>1.22(0.02)</td><td>2.79(0.03)</td><td>4.91(0.04)</td><td>8.10(0.05)</td><td>12.41(0.05)</td><td>16.99(0.07)</td><td>19.10(0.07)</td><td>16.84(0.06)</td><td>11.72(0.05)</td><td>5.87(0.04)</td></tr><tr><td>70-80</td><td>0.81(0.02)</td><td>1.72(0.03)</td><td>3.05(0.03)</td><td>5.10(0.04)</td><td>8.27(0.05)</td><td>12.73(0.05)</td><td>18.15(0.07)</td><td>21.30(0.08)</td><td>18.69(0.07)</td><td>10.13(0.05)</td></tr><tr><td>80-90</td><td>0.51(0.01)</td><td>1.04(0.02)</td><td>1.78(0.03)</td><td>2.85(0.03)</td><td>4.58(0.04)</td><td>7.77(0.05)</td><td>13.02(0.05)</td><td>20.78(0.07)</td><td>27.18(0.09)</td><td>20.43(0.06)</td></tr><tr><td>90-100</td><td>0.29(0.01)</td><td>0.53(0.01)</td><td>0.79(0.02)</td><td>1.18(0.02)</td><td>1.83(0.03)</td><td>2.97(0.03)</td><td>5.31(0.04)</td><td>10.62(0.05)</td><td>23.28(0.07)</td><td>53.14(0.12)</td></tr></table>

Table 9a: Transition probabilities for weekly turnover deciles (in percent), estimated with weekly turnover of NYSE or AMEX ordinary common shares (CRSP share codes 10 and 11, excluding 37 stocks containing Z-errors in reported volume) from July 1962 to December 1996 (1,800 weeks). Each week all securities with non-missing returns are sorted into turnover deciles and the frequencies of transitions from decile i in one week to decile j in the next week are tabulated for each consecutive pair of weeks and for all (i, j) combinations, $i , j = 1 , \ldots , 1 0$ , and then normalized by the number of consecutive pairs of weeks. The number of securities with non-missing returns in any given week varies between 1,700 and 2,200. Standard errors, computed under the assumption of independently and identically distributed transitions, are given in parentheses. 

These entries indicate some persistence in the cross section of turnover for the extreme deciles, but considerable movement across the intermediate deciles. For example, there is only a 18.47% probability that stocks in the fifth decile (40–50%) in one week remain in the fifth decile the next week, and a probability of 12.18% and 11.53% of jumping to the third 

and seventh deciles, respectively. 

For purposes of comparison, Tables 9b and 9c report similar transition probabilities estimates for market capitalization deciles and return deciles, respectively. Market capitalization is considerably more persistent: none of the diagonal entries in Table 9b are less than 90%. However, returns are considerably less persistent—indeed, Table 9c provides strong evidence of reversals. For example, stocks in the first return-decile this week have a 19.50% probability of being in the tenth return-decile next week; stocks in the tenth return-decile this week have a 20.49% probability of being in the first return-decile next week. These weekly transition probabilities are consistent with the longer-horizon return reversals documented by Chopra, Lakonishok, and Ritter (1992), DeBondt and Thaler (1985), and Lehmann (1990). 

<table><tr><td rowspan="2" colspan="2">MARKET CAP TRANSITION</td><td colspan="10">Next Week Decile</td></tr><tr><td>0-10</td><td>10-20</td><td>20-30</td><td>30-40</td><td>40-50</td><td>50-60</td><td>60-70</td><td>70-80</td><td>80-90</td><td>90-100</td></tr><tr><td rowspan="10">This Week</td><td>0-10</td><td>96.75(0.06)</td><td>3.18(0.03)</td><td>0.01(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td></tr><tr><td>10-20</td><td>3.31(0.03)</td><td>92.61(0.07)</td><td>4.01(0.03)</td><td>0.01(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td></tr><tr><td>20-30</td><td>0.00(0.00)</td><td>4.09(0.03)</td><td>91.61(0.07)</td><td>4.23(0.03)</td><td>0.01(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td></tr><tr><td>30-40</td><td>0.00(0.00)</td><td>0.01(0.00)</td><td>4.26(0.03)</td><td>91.36(0.08)</td><td>4.31(0.04)</td><td>0.01(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td></tr><tr><td>40-50</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.01(0.00)</td><td>4.29(0.03)</td><td>91.80(0.07)</td><td>3.85(0.03)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td></tr><tr><td>50-60</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.01(0.00)</td><td>3.77(0.03)</td><td>92.77(0.07)</td><td>3.39(0.03)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td></tr><tr><td>60-70</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.01(0.00)</td><td>3.31(0.03)</td><td>93.76(0.07)</td><td>2.86(0.03)</td><td>0.00(0.00)</td><td>0.00(0.00)</td></tr><tr><td>70-80</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>2.78(0.02)</td><td>95.01(0.06)</td><td>2.14(0.02)</td><td>0.00(0.00)</td></tr><tr><td>80-90</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>2.08(0.02)</td><td>96.38(0.06)</td><td>1.48(0.02)</td></tr><tr><td>90-100</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>0.00(0.00)</td><td>1.45(0.02)</td><td>98.49(0.06)</td></tr></table>

Table 9b: Transition probabilities for weekly market-capitalization deciles (in percent), estimated with weekly market capitalization of NYSE or AMEX ordinary common shares (CRSP share codes 10 and 11, excluding 37 stocks containing Z-errors in reported volume) from July 1962 to December 1996 (1,800 weeks). Each week all securities with non-missing returns are sorted into market-capitalization deciles and the frequencies of transitions from decile i in one week to decile j in the next week are tabulated for each consecutive pair of weeks and for all (i, j) combinations, i, j = 1, . . . , 10, and then normalized by the number of consecutive pairs of weeks. The number of securities with non-missing returns in any given week varies between 1,700 and 2,200. Standard errors, computed under the assumption of independently and identically distributed transitions, are given in parentheses. 

<table><tr><td rowspan="2" colspan="2">RETURN TRANSITION</td><td colspan="10">Next Week Decile</td></tr><tr><td>0-10</td><td>10-20</td><td>20-30</td><td>30-40</td><td>40-50</td><td>50-60</td><td>60-70</td><td>70-80</td><td>80-90</td><td>90-100</td></tr><tr><td rowspan="10">This Week</td><td>0-10</td><td>12.70(0.09)</td><td>8.57(0.06)</td><td>7.20(0.06)</td><td>7.23(0.07)</td><td>7.58(0.07)</td><td>7.77(0.07)</td><td>8.00(0.07)</td><td>9.28(0.06)</td><td>12.13(0.07)</td><td>19.50(0.11)</td></tr><tr><td>10-20</td><td>9.51(0.06)</td><td>9.95(0.06)</td><td>9.60(0.05)</td><td>9.42(0.05)</td><td>9.24(0.05)</td><td>9.44(0.05)</td><td>9.84(0.05)</td><td>10.63(0.06)</td><td>11.38(0.06)</td><td>10.93(0.06)</td></tr><tr><td>20-30</td><td>8.03(0.06)</td><td>9.74(0.05)</td><td>10.43(0.05)</td><td>10.40(0.06)</td><td>10.38(0.06)</td><td>10.51(0.06)</td><td>10.77(0.06)</td><td>10.78(0.06)</td><td>10.33(0.06)</td><td>8.56(0.06)</td></tr><tr><td>30-40</td><td>7.60(0.06)</td><td>9.33(0.05)</td><td>10.35(0.06)</td><td>10.85(0.07)</td><td>11.20(0.07)</td><td>11.28(0.07)</td><td>11.22(0.07)</td><td>10.55(0.06)</td><td>9.66(0.05)</td><td>7.90(0.06)</td></tr><tr><td>40-50</td><td>7.62(0.07)</td><td>9.07(0.05)</td><td>10.21(0.06)</td><td>10.99(0.07)</td><td>11.70(0.08)</td><td>11.68(0.07)</td><td>11.22(0.07)</td><td>10.38(0.06)</td><td>9.40(0.05)</td><td>7.69(0.06)</td></tr><tr><td>50-60</td><td>7.43(0.07)</td><td>9.16(0.05)</td><td>10.44(0.06)</td><td>11.11(0.07)</td><td>11.55(0.07)</td><td>11.63(0.07)</td><td>11.29(0.07)</td><td>10.52(0.06)</td><td>9.30(0.06)</td><td>7.52(0.06)</td></tr><tr><td>60-70</td><td>7.44(0.06)</td><td>9.61(0.05)</td><td>10.70(0.06)</td><td>11.15(0.07)</td><td>11.17(0.07)</td><td>11.23(0.07)</td><td>11.10(0.07)</td><td>10.45(0.06)</td><td>9.51(0.06)</td><td>7.59(0.05)</td></tr><tr><td>70-80</td><td>8.30(0.06)</td><td>10.40(0.06)</td><td>10.88(0.06)</td><td>10.84(0.07)</td><td>10.46(0.06)</td><td>10.40(0.06)</td><td>10.44(0.06)</td><td>10.37(0.06)</td><td>9.78(0.06)</td><td>8.07(0.05)</td></tr><tr><td>80-90</td><td>10.92(0.07)</td><td>11.70(0.06)</td><td>10.86(0.06)</td><td>9.93(0.06)</td><td>9.34(0.06)</td><td>9.15(0.06)</td><td>9.30(0.06)</td><td>9.61(0.06)</td><td>9.82(0.06)</td><td>9.32(0.06)</td></tr><tr><td>90-100</td><td>20.49(0.11)</td><td>12.39(0.06)</td><td>9.34(0.06)</td><td>8.03(0.06)</td><td>7.28(0.05)</td><td>6.95(0.05)</td><td>6.82(0.05)</td><td>7.38(0.05)</td><td>8.68(0.05)</td><td>12.59(0.08)</td></tr></table>


Table 9c: Transition probabilities for weekly return deciles (in percent), estimated with weekly returns of NYSE or AMEX ordinary common shares (CRSP share codes 10 and 11, excluding 37 stocks containing Z-errors in reported volume) from July 1962 to December 1996 (1,800 weeks). Each week all securities with non-missing returns are sorted into return deciles and the frequencies of transitions from decile i in one week to decile j in the next week are tabulated for each consecutive pair of weeks and for all (i, j) combinations, $i , j = 1 , \dots , 1 0 .$ and then normalized by the number of consecutive pairs of weeks. The number of securities with non-missing returns in any given week varies between 1,700 and 2,200. Standard errors, computed under the assumption of independently and identically distributed transitions, are given in parentheses.


In summary, the turnover cross-section exhibits considerable variation, some persistence in extreme deciles, and significant movement across intermediate deciles. 

## 4.1 Specification of Cross-Sectional Regressions

It is clear from Figure 4 that turnover varies considerably in the cross section. In Section 5 and 6, we propose formal models for the cross-section of volume. But before doing so, we first consider a less formal, more exploratory analysis of the cross-sectional variation in turnover. The results we report here are from Lo and Wang (2000) (see also Lim, Lo, Wang and Adamek (1998). 

In particular, we wish to examine the explanatory power of several economically motivated variables such as expected return, volatility, and trading costs in explaining the cross section of turnover. To do this, we estimate cross-sectional regressions over five-year subperiods where the dependent variable is the median turnover $\tilde { \tau } _ { j }$ of stock j and the explanatory variables are the following stock-specific characteristics:<sup>19</sup> 

$\hat { \alpha } _ { r , j } \colon$ Intercept coeficient from the time-series regression of stock $j ^ { \prime } \mathrm { s }$ return on the value-weighted market return. 

$\hat { \beta } _ { r , j } \mathrm { : }$ Slope coeficient from the time-series regression of stock $j ^ { \prime }$ s return on the value-weighted market return. 

$\hat { \sigma } _ { \epsilon , r , j } \mathopen { } \mathclose \bgroup \left. \langle \mathclose \bgroup \left. \vert \partial _ { \epsilon , r , j } \aftergroup \egroup \right. \aftergroup \egroup \right.$ Residual standard deviation of the time-series regression of stock $j ^ { \prime } \mathrm { s }$ return on the value-weighted market return. 

$v _ { j } { \mathrm { : } }$ Average of natural logarithm of stock $j ^ { \prime } \mathrm { s }$ market capitalization. 

$p _ { j } \colon$ Average of natural logarithm of stock $j ^ { \prime } \mathrm { s }$ price. 

$d _ { j } \colon$ Average of dividend yield of stock $j ,$ , where dividend yield in week t is defined by 

$$
d _ {j t} = \max \left[ 0, \log \left((1 + R _ {j t}) V _ {j t - 1} / V _ {j t}\right) \right]
$$

and $V _ { j t }$ is $j ^ { \prime } \mathrm { s }$ market capitalization in week $t .$ 

$\mathrm { S P 5 0 0 } _ { j }$ Indicator variable for membership in the S&P 500 Index. 

$\hat { \gamma } _ { r , j } ( 1 )$ First-order autocovariance of returns. 

The inclusion of these regressors in our cross-sectional analysis is loosely motivated by various intuitive “theories” that have appeared in the volume literature. 

The motivation for the first three regressors comes partly from linear asset-pricing models such as the CAPM and $\mathrm { A P T } ;$ they capture excess expected return $\left( \hat { \alpha } _ { r , j } \right)$ , systematic risk $( \hat { \beta } _ { r , j } )$ , and residual risk $( \hat { \sigma } _ { \epsilon , r , j } )$ , respectively. To the extent that expected excess return $\left( \hat { \alpha } _ { r , j } \right)$ may contain a premium associated with liquidity (see, for example, Amihud and Mendelson (1986a,b) and Hu (1997)) and heterogeneous information (see, for example, He and Wang (1995) and Wang (1994)), it should also give rise to cross-sectional diferences in turnover. Although a higher premium from lower liquidity should be inversely related to turnover, a higher premium from heterogeneous information can lead to either higher or lower turnover, depending on the nature of information heterogeneity. The two risk measures of an asset, $\hat { \beta } _ { r , j }$ and $\hat { \sigma } _ { \epsilon , r , j }$ , also measure the volatility in its returns that is associated with systematic risk and residual risk, respectively. Given that realized returns often generate portfolio-rebalancing needs, the volatility of returns should be positively related to turnover. 

The motivation for log-market-capitalization $( v _ { j } )$ and log-price $\left( p _ { t } \right)$ is two-fold. On the theoretical side, the role of market capitalization in explaining volume is related to Merton’s (1987) model of capital market equilibrium in which investors hold only the assets they are familiar with. This implies that larger-capitalization companies tend to have more diverse ownership, which can lead to more active trading. The motivation for log-price is related to trading costs. Given that part of trading costs comes from the bid-ask spread, which takes on discrete values in dollar terms, the actual costs in percentage terms are inversely related to price levels. This suggests that volume should be positively related to prices. 

On the empirical side, there is an extensive literature documenting the significance of logmarket-capitalization and log-price in explaining the cross-sectional variation of expected returns, e.g., Banz (1981), Black (1976), Brown, Van Harlow, and Tinic (1993), Marsh and Merton (1987), and Reinganum (1992). If size and price are genuine factors driving expected returns, they should drive turnover as well (see Lo and Wang (1998) for a more formal derivation and empirical analysis of this intuition). 

Dividend yield $( d _ { j } )$ is motivated by its (empirical) ties to expected returns, but also by dividend-capture trades—the practice of purchasing stock just before its ex-dividend date and then selling it shortly thereafter.<sup>20</sup> Often induced by diferential taxation of dividends versus capital gains, dividend-capture trading has been linked to short-term increases in trading activity, e.g., Karpof and Walking (1988, 1990), Lakonishok and Smidt (1986), Lakonishok and Vermaelen (1986), Lynch-Koski (1996), Michaely (1991), Michaely and Vila (1995, 1996), and Stickel (1991). Stocks with higher dividend yields should induce more dividend-capture trading activity, and this may be reflected in higher median turnover. 

The efects of membership in the S&P 500 have been documented in many studies, e.g., Dhillon and Johnson (1991), Goetzmann and Garry (1986), Harris and Gurel (1986), Jacques (1988), Jain (1987), Lamoureux and Wansley (1987), Pruitt and Wei (1989), Shleifer (1986), Tkac (1999), and Woolridge and Ghosh (1986). In particular, Harris and Gurel (1986) document increases in volume just after inclusion in the S&P 500, and Tkac (1999) uses an S&P 500 indicator variable to explain the cross-sectional dispersion of relative turnover (relative dollar-volume divided by relative market-capitalization). The obvious motivation for this variable is the growth of indexation by institutional investors, and by the related practice of index arbitrage, in which disparities between the index futures price and the spot prices of the component securities are exploited by taking the appropriate positions in the futures and spot markets. For these reasons, stocks in the S&P 500 index should have higher turnover than others. Indexation began its rise in popularity with the advent of the mutual-fund industry in the early 1980’s, and index arbitrage first became feasible in 1982 with the introduction of the Chicago Mercantile Exchange’s S&P 500 futures contracts. Therefore, the efects of S&P 500 membership on turnover should be more dramatic in the later subperiods. Another motivation for S&P 500 membership is its efect on the publicity of member companies, which leads to more diverse ownership and more trading activity in the context of Merton (1987). 

The last variable, the first-order return autocovariance $( \hat { \gamma } _ { r , j } ( 1 ) )$ , serves as a proxy for trading costs, as in Roll’s (1984) model of the “efective” bid/ask spread. In that model, Roll shows that in the absence of information-based trades, prices bouncing between bid and ask prices implies the following approximate relation between the spread and the first-order return autocovariance: 

$$
\frac {s _ {r , j} ^ {2}}{4} \approx - \operatorname{Cov} [ R _ {j t}, R _ {j t - 1} ] \equiv - \gamma_ {r, j} (1)\tag{8}
$$

where $s _ { r , j } \equiv s _ { j } / \sqrt { P _ { a j } P _ { b j } }$ is the percentage efective bid/ask spread of stock $j$ as a percentage of the geometric average of the bid and ask prices $P _ { b j }$ and $P _ { a j }$ , respectively, and $s _ { j }$ is the dollar bid/ask spread. 

Rather than solve for $s _ { r , j }$ , we choose instead to include $\hat { \gamma } _ { r , j } ( 1 )$ as a regressor to sidestep the problem of a positive sample first-order autocovariance, which yields a complex number for the efective bid/ask spread. Of course, using $\hat { \gamma } _ { r , j } ( 1 )$ does not eliminate this problem, which is a symptom of a specification error, but rather is a convenient heuristic that allows us to estimate the regression equation (complex observations for even one regressor can yield complex parameter estimates for all the other regressors as well!). This heuristic is not unlike Roll’s method for dealing with positive autocovariances, however, it is more direct.<sup>21</sup> 

Under the trading-cost interpretation for $\hat { \gamma } _ { r , j } ( 1 )$ , we should expect a positive coeficient in our cross-sectional turnover regression—a large negative value for $\hat { \gamma } _ { r , j } ( 1 )$ implies a large bid/ask spread, which should be associated with lower turnover. Alternatively, Roll (1984) interprets a positive value for $\hat { \gamma } _ { r , j } ( 1 )$ as a negative bid/ask spread, hence turnover should be higher for such stocks. 

These eight regressors yield the following regression equation to be estimated: 

$$
\begin{array}{r c l} \tilde {\tau} _ {j} & = & \gamma_ {0} + \gamma_ {1} \hat {\alpha} _ {r, j} + \gamma_ {2} \hat {\beta} _ {r, j} + \gamma_ {3} \hat {\sigma} _ {\epsilon , r, j} + \gamma_ {4} v _ {j} + \gamma_ {5} p _ {j} + \gamma_ {6} d _ {j} + \\ & & \gamma_ {7} \mathrm{SP} 5 0 0 _ {j} + \gamma_ {8} \hat {\gamma} _ {r, j} (1) + \epsilon_ {j}. \end{array}\tag{9}
$$

## 4.2 Summary Statistics For Regressors

Table 10 reports summary statistics for these regressors, as well as for three other variables relevant to Sections 5 and 6: 

$\hat { \alpha } _ { \tau , j } \colon$ Intercept coeficient from the time-series regression of stock $j ^ { \prime }$ s turnover on the value-weighted market turnover. 

$\hat { \beta } _ { \tau , j } \mathrm { : }$ Slope coeficient from the time-series regression of stock $j ^ { \prime } \mathrm { s }$ turnover on the value-weighted market turnover. 

$\hat { \sigma } _ { \epsilon , \tau , j } \mathopen { } \mathclose \bgroup \left. \vert \partial _ { \epsilon , \tau , j } \aftergroup \egroup \right. \mathclose { } .$ Residual standard deviation of the time-series regression of stock $j ^ { \prime } \mathrm { s }$ turnover on the value-weighted market turnover. 

These three variables are loosely motivated by a one-factor linear model of turnover, i.e., a market model for turnover, which will be discussed in Section 5. 

Table 10 contains means, medians, and standard deviations for these variables over each of the seven subperiods. The entries show that return betas are approximately 1.0 on average, with a cross-sectional standard deviation of about 0.5. Observe that return betas have approximately the same mean and median in all subperiods, indicating an absence of dramatic skewness and outliers in their empirical distributions. 

In contrast, turnover betas have a considerably higher means, starting at 2.2 in the first subperiod (1962–1966) to an all-time high of 3.1 in the second subperiod (1967–1971), and declining steadily thereafter to 0.7 (1987–1991) and 0.8 (1992–1996). Also, the means and medians of turnover betas difer dramatically, particularly in the earlier subperiods, e.g., 2.2 mean versus 0.7 median (1962–1966) and 3.1 mean versus 1.9 median (1967–71), implying a skewed empirical distribution with some outliers in the right tail. Turnover betas are also more variable than return betas, with cross-sectional standard deviations that range from twice to ten times those of return betas. 

<table><tr><td></td><td><eq>\overline{\tau}_{j}</eq></td><td><eq>\tilde{\tau}_{j}</eq></td><td><eq>\hat{\alpha}_{\tau,j}</eq></td><td><eq>\hat{\beta}_{\tau,j}</eq></td><td><eq>\hat{\sigma}_{\epsilon,\tau,j}</eq></td><td><eq>\hat{\alpha}_{r,j}</eq></td><td><eq>\hat{\beta}_{r,j}</eq></td><td><eq>\hat{\sigma}_{\epsilon,r,j}</eq></td><td><eq>v_{j}</eq></td><td><eq>p_{j}</eq></td><td><eq>d_{j}</eq></td><td><eq>SP_{j}^{500}</eq></td><td><eq>\hat{\gamma}_{r,j}(1)</eq></td></tr><tr><td colspan="14">1962 to 1966 (234 weeks)</td></tr><tr><td><eq>\mu</eq></td><td>0.576</td><td>0.374</td><td>0.009</td><td>2.230</td><td>0.646</td><td>0.080</td><td>1.046</td><td>4.562</td><td>17.404</td><td>1.249</td><td>0.059</td><td>0.175</td><td>-2.706</td></tr><tr><td>m</td><td>0.397</td><td>0.272</td><td>0.092</td><td>0.725</td><td>0.391</td><td>0.064</td><td>1.002</td><td>3.893</td><td>17.263</td><td>1.445</td><td>0.058</td><td>0.000</td><td>-0.851</td></tr><tr><td>s</td><td>0.641</td><td>0.372</td><td>1.065</td><td>5.062</td><td>0.889</td><td>0.339</td><td>0.529</td><td>2.406</td><td>1.737</td><td>0.965</td><td>0.081</td><td>0.380</td><td>8.463</td></tr><tr><td colspan="14">1967 to 1971 (261 weeks)</td></tr><tr><td><eq>\mu</eq></td><td>0.900</td><td>0.610</td><td>-0.361</td><td>3.134</td><td>0.910</td><td>0.086</td><td>1.272</td><td>5.367</td><td>17.930</td><td>1.442</td><td>0.049</td><td>0.178</td><td>-1.538</td></tr><tr><td>m</td><td>0.641</td><td>0.446</td><td>-0.128</td><td>1.948</td><td>0.612</td><td>0.081</td><td>1.225</td><td>5.104</td><td>17.791</td><td>1.522</td><td>0.042</td><td>0.000</td><td>-0.623</td></tr><tr><td>s</td><td>0.827</td><td>0.547</td><td>0.954</td><td>3.559</td><td>0.940</td><td>0.383</td><td>0.537</td><td>1.991</td><td>1.566</td><td>0.685</td><td>0.046</td><td>0.382</td><td>4.472</td></tr><tr><td colspan="14">1972 to 1976 (261 weeks)</td></tr><tr><td><eq>\mu</eq></td><td>0.521</td><td>0.359</td><td>-0.025</td><td>1.472</td><td>0.535</td><td>0.085</td><td>0.986</td><td>6.252</td><td>17.574</td><td>0.823</td><td>0.072</td><td>0.162</td><td>-3.084</td></tr><tr><td>m</td><td>0.420</td><td>0.291</td><td>0.005</td><td>1.040</td><td>0.403</td><td>0.086</td><td>0.955</td><td>5.825</td><td>17.346</td><td>0.883</td><td>0.063</td><td>0.000</td><td>-1.007</td></tr><tr><td>s</td><td>0.408</td><td>0.292</td><td>0.432</td><td>1.595</td><td>0.473</td><td>0.319</td><td>0.429</td><td>2.619</td><td>1.784</td><td>0.890</td><td>0.067</td><td>0.369</td><td>8.262</td></tr><tr><td colspan="14">1977 to 1981 (261 weeks)</td></tr><tr><td><eq>\mu</eq></td><td>0.780</td><td>0.553</td><td>0.043</td><td>1.199</td><td>0.749</td><td>0.254</td><td>0.950</td><td>5.081</td><td>18.155</td><td>1.074</td><td>0.099</td><td>0.176</td><td>-1.748</td></tr><tr><td>m</td><td>0.629</td><td>0.449</td><td>0.052</td><td>0.818</td><td>0.566</td><td>0.215</td><td>0.936</td><td>4.737</td><td>18.094</td><td>1.212</td><td>0.086</td><td>0.000</td><td>-0.622</td></tr><tr><td>s</td><td>0.561</td><td>0.405</td><td>0.638</td><td>1.348</td><td>0.643</td><td>0.356</td><td>0.428</td><td>2.097</td><td>1.769</td><td>0.805</td><td>0.097</td><td>0.381</td><td>5.100</td></tr><tr><td colspan="14">1982 to 1986 (261 weeks)</td></tr><tr><td><eq>\mu</eq></td><td>1.160</td><td>0.833</td><td>0.005</td><td>0.957</td><td>1.135</td><td>0.113</td><td>0.873</td><td>5.419</td><td>18.629</td><td>1.143</td><td>0.090</td><td>0.181</td><td>-1.627</td></tr><tr><td>m</td><td>0.998</td><td>0.704</td><td>0.031</td><td>0.713</td><td>0.902</td><td>0.146</td><td>0.863</td><td>4.813</td><td>18.512</td><td>1.293</td><td>0.063</td><td>0.000</td><td>-0.573</td></tr><tr><td>s</td><td>0.788</td><td>0.605</td><td>0.880</td><td>1.018</td><td>0.871</td><td>0.455</td><td>0.437</td><td>2.581</td><td>1.763</td><td>0.873</td><td>0.126</td><td>0.385</td><td>8.405</td></tr><tr><td colspan="14">1987 to 1991 (261 weeks)</td></tr><tr><td><eq>\mu</eq></td><td>1.255</td><td>0.888</td><td>0.333</td><td>0.715</td><td>1.256</td><td>-0.007</td><td>0.977</td><td>6.450</td><td>18.847</td><td>0.908</td><td>0.095</td><td>0.191</td><td>-5.096</td></tr><tr><td>m</td><td>0.995</td><td>0.708</td><td>0.171</td><td>0.505</td><td>0.899</td><td>0.014</td><td>0.998</td><td>5.174</td><td>18.778</td><td>1.108</td><td>0.062</td><td>0.000</td><td>-0.386</td></tr><tr><td>s</td><td>1.039</td><td>0.773</td><td>1.393</td><td>1.229</td><td>1.272</td><td>0.543</td><td>0.414</td><td>5.417</td><td>2.013</td><td>1.097</td><td>0.134</td><td>0.393</td><td>44.246</td></tr><tr><td colspan="14">1992 to 1996 (261 weeks)</td></tr><tr><td><eq>\mu</eq></td><td>1.419</td><td>1.032</td><td>0.379</td><td>0.833</td><td>1.378</td><td>0.147</td><td>0.851</td><td>5.722</td><td>19.407</td><td>1.081</td><td>0.063</td><td>0.182</td><td>-3.600</td></tr><tr><td>m</td><td>1.114</td><td>0.834</td><td>0.239</td><td>0.511</td><td>0.997</td><td>0.113</td><td>0.831</td><td>4.674</td><td>19.450</td><td>1.297</td><td>0.042</td><td>0.000</td><td>-1.136</td></tr><tr><td>s</td><td>1.208</td><td>0.910</td><td>1.637</td><td>1.572</td><td>1.480</td><td>0.482</td><td>0.520</td><td>3.901</td><td>2.007</td><td>1.032</td><td>0.095</td><td>0.386</td><td>21.550</td></tr></table>


Table 10: Summary statistics of variables for cross-sectional analysis of weekly turnover of NYSE or AMEX ordinary common shares (CRSP share codes 10 and 11, excluding 37 stocks containing Z-errors in reported volume) for subperiods of the sample period from July 1962 to December 1996. The variables are: $\overline { { \tau } } _ { j }$ (average turnover); $\tilde { \tau } _ { j }$ (median turnover); $\hat { \alpha } _ { \tau , j } , \hat { \beta } _ { \tau , j } ,$ and $\hat { \sigma } _ { \epsilon , \tau , j }$ (the intercept, slope, and residual, respectively, from the time-series regression of an individual security’s turnover on market turnover); $\hat { \alpha } _ { r , j } , \hat { \beta } _ { r , j }$ , and $\hat { \sigma } _ { \epsilon , r , j }$ (the intercept, slope, and residual, respectively, from the time-series regression of an individual security’s return on the market return); $v _ { j }$ (natural logarithm of market capitalization); $p _ { j }$ (natural logarithm of price); $d _ { j }$ (dividend yield); $\mathrm { S P } _ { j } ^ { 5 0 0 }$ (S&P 500 indicator variable); and $\hat { \gamma } _ { r , j } ( 1 )$ (firstorder return autocovariance). The statistics are: $\mu$ (mean); m (median); and s (standard deviation).


The summary statistics for the first-order return autocovariances show that they are negative on average, which is consistent with the trading-cost interpretation, though there is considerable skewness in their distribution as well given the diferences between means and medians. The means and medians vary from subperiod to subperiod in a manner also consistent with the trading-cost interpretation—the higher the median of median turnover $\tilde { \tau } _ { j }$ , the closer to 0 is the median autocovariance.<sup>22</sup> In particular, between the first and second subperiods, median autocovariance decreases (in absolute value) from −0.851 to −0.623, signaling lower trading costs, while median turnover increases from 0.272 to 0.446. Between the second and third subperiods, median autocovariance increases (in absolute value) from −0.623 to −1.007 while median turnover decreases from 0.446 to 0.291, presumably due to the Oil Shock of 1973–1974 and the subsequent recession. The 1977–1981 subperiod is the first subperiod after the advent of negotiated commissions (May 1, 1975), and median turnover increases to 0.449 while median autocovariance decreases (in absolute value) to −0.622. During the 1982–1986 subperiod when S&P 500 index futures begin trading, median autocovariance declines (in absolute value) to −0.573 while median turnover increases dramatically to 0.704. And during the 1987–1991 subperiod which includes the October 1987 Crash, median turnover is essentially unchanged (0.708 versus 0.704 from the previous subperiod), median autocovariance decreases (in absolute value) from −0.573 in the previous subperiod to −0.386, but mean autocovariance increases (in absolute value) dramatically from −1.627 in the previous subperiod to −5.096, indicating the presence of outliers with very large trading costs. 

We have also estimated correlations among the variables in Table 10, which are reported in Table 11. It shows that median turnover is highly correlated with both turnover beta and return beta, with correlations that exceed 50% in most subperiods, hinting at the prospect of two or more factors driving the cross-sectional variation in turnover. We shall address this issue more formally in Section 5. 

Median turnover is not particularly highly correlated with S&P 500 membership dur-

<table><tr><td></td><td><eq>\overline{\tau}_{j}</eq></td><td><eq>\tilde{\tau}_{j}</eq></td><td><eq>\hat{\alpha}_{\tau,j}</eq></td><td><eq>\hat{\beta}_{\tau,j}</eq></td><td><eq>\hat{\sigma}_{\epsilon,\tau,j}</eq></td><td><eq>\hat{\alpha}_{r,j}</eq></td><td><eq>\hat{\beta}_{r,j}</eq></td><td><eq>\hat{\sigma}_{\epsilon,r,j}</eq></td><td><eq>v_{j}</eq></td><td><eq>p_{j}</eq></td><td><eq>d_{j}</eq></td><td><eq>SP_{j}^{500}</eq></td></tr><tr><td colspan="13">1962 to 1966 (2,073 stocks)</td></tr><tr><td><eq>\tilde{\tau}_{j}</eq></td><td>93.1</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\alpha}_{\tau,j}</eq></td><td>-8.6</td><td>1.9</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\beta}_{\tau,j}</eq></td><td>56.6</td><td>43.9</td><td>-86.9</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\sigma}_{\epsilon,\tau,j}</eq></td><td>88.8</td><td>70.3</td><td>-11.8</td><td>54.1</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\alpha}_{r,j}</eq></td><td>14.9</td><td>10.7</td><td>-12.0</td><td>16.9</td><td>14.8</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\beta}_{r,j}</eq></td><td>56.3</td><td>59.3</td><td>-15.8</td><td>40.8</td><td>43.2</td><td>1.5</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\sigma}_{\epsilon,r,j}</eq></td><td>36.1</td><td>25.4</td><td>-19.5</td><td>34.0</td><td>45.8</td><td>16.3</td><td>29.2</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>v_{j}</eq></td><td>-19.2</td><td>-11.4</td><td>9.6</td><td>-17.5</td><td>-28.9</td><td>-3.0</td><td>1.9</td><td>-62.7</td><td></td><td></td><td></td><td></td></tr><tr><td><eq>p_{j}</eq></td><td>-7.6</td><td>1.7</td><td>14.6</td><td>-16.0</td><td>-20.1</td><td>1.6</td><td>3.2</td><td>-77.1</td><td>78.7</td><td></td><td></td><td></td></tr><tr><td><eq>d_{j}</eq></td><td>-11.4</td><td>-9.3</td><td>9.3</td><td>-13.2</td><td>-12.2</td><td>0.4</td><td>-17.0</td><td>-27.9</td><td>13.1</td><td>20.7</td><td></td><td></td></tr><tr><td><eq>SP_{j}^{500}</eq></td><td>-5.0</td><td>-0.6</td><td>4.8</td><td>-6.4</td><td>-10.2</td><td>-6.6</td><td>2.4</td><td>-24.2</td><td>43.1</td><td>32.0</td><td>4.8</td><td></td></tr><tr><td><eq>\hat{\gamma}_{r,j}(1)</eq></td><td>-0.6</td><td>3.0</td><td>5.7</td><td>-5.1</td><td>-7.6</td><td>-14.4</td><td>1.9</td><td>-63.2</td><td>31.1</td><td>52.7</td><td>12.9</td><td>10.7</td></tr><tr><td colspan="13">1967 to 1971 (2,292 stocks)</td></tr><tr><td><eq>\tilde{\tau}_{j}</eq></td><td>96.8</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\alpha}_{\tau,j}</eq></td><td>-30.9</td><td>-23.0</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\beta}_{\tau,j}</eq></td><td>77.6</td><td>70.6</td><td>-83.8</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\sigma}_{\epsilon,\tau,j}</eq></td><td>92.2</td><td>80.7</td><td>-38.2</td><td>77.9</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\alpha}_{r,j}</eq></td><td>10.3</td><td>8.7</td><td>4.2</td><td>1.9</td><td>12.5</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\beta}_{r,j}</eq></td><td>59.2</td><td>60.4</td><td>-31.2</td><td>55.4</td><td>50.0</td><td>-12.6</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\sigma}_{\epsilon,r,j}</eq></td><td>56.3</td><td>49.5</td><td>-36.7</td><td>57.0</td><td>60.7</td><td>-1.5</td><td>61.3</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>v_{j}</eq></td><td>-32.5</td><td>-25.3</td><td>32.7</td><td>-40.5</td><td>-41.1</td><td>1.1</td><td>-23.7</td><td>-67.6</td><td></td><td></td><td></td><td></td></tr><tr><td><eq>p_{j}</eq></td><td>-19.8</td><td>-11.9</td><td>35.6</td><td>-35.3</td><td>-30.1</td><td>16.7</td><td>-22.1</td><td>-68.9</td><td>77.0</td><td></td><td></td><td></td></tr><tr><td><eq>d_{j}</eq></td><td>-38.2</td><td>-37.2</td><td>19.8</td><td>-35.3</td><td>-35.2</td><td>3.0</td><td>-51.9</td><td>-57.1</td><td>28.0</td><td>28.3</td><td></td><td></td></tr><tr><td><eq>SP_{j}^{500}</eq></td><td>-14.0</td><td>-10.6</td><td>11.9</td><td>-16.1</td><td>-18.2</td><td>2.2</td><td>-11.5</td><td>-30.9</td><td>47.9</td><td>35.2</td><td>13.3</td><td></td></tr><tr><td><eq>\hat{\gamma}_{r,j}(1)</eq></td><td>-8.7</td><td>-6.8</td><td>11.7</td><td>-12.8</td><td>-11.4</td><td>8.8</td><td>-14.9</td><td>-40.7</td><td>30.7</td><td>43.8</td><td>18.2</td><td>12.3</td></tr><tr><td colspan="13">1972 to 1976 (2,084 stocks)</td></tr><tr><td><eq>\tilde{\tau}_{j}</eq></td><td>96.5</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\alpha}_{\tau,j}</eq></td><td>2.5</td><td>8.9</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\beta}_{\tau,j}</eq></td><td>67.4</td><td>60.2</td><td>-72.0</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\sigma}_{\epsilon,\tau,j}</eq></td><td>83.9</td><td>69.4</td><td>-5.9</td><td>62.6</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\alpha}_{r,j}</eq></td><td>8.5</td><td>7.2</td><td>-7.7</td><td>11.1</td><td>7.5</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\beta}_{r,j}</eq></td><td>54.3</td><td>54.3</td><td>-16.4</td><td>49.4</td><td>39.7</td><td>-14.8</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\sigma}_{\epsilon,r,j}</eq></td><td>22.2</td><td>12.7</td><td>-2.9</td><td>17.9</td><td>35.7</td><td>-11.3</td><td>29.9</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>v_{j}</eq></td><td>0.6</td><td>12.0</td><td>3.8</td><td>-2.7</td><td>-21.7</td><td>5.3</td><td>12.6</td><td>-65.2</td><td></td><td></td><td></td><td></td></tr><tr><td><eq>p_{j}</eq></td><td>8.1</td><td>17.4</td><td>8.8</td><td>-1.0</td><td>-11.7</td><td>14.6</td><td>1.8</td><td>-76.1</td><td>83.7</td><td></td><td></td><td></td></tr><tr><td><eq>d_{j}</eq></td><td>-20.9</td><td>-18.3</td><td>7.0</td><td>-19.8</td><td>-20.9</td><td>9.4</td><td>-34.2</td><td>-41.6</td><td>19.4</td><td>25.0</td><td></td><td></td></tr><tr><td><eq>SP_{j}^{500}</eq></td><td>1.2</td><td>8.6</td><td>1.5</td><td>-0.4</td><td>-13.1</td><td>-2.2</td><td>9.1</td><td>-28.2</td><td>50.5</td><td>37.9</td><td>2.6</td><td></td></tr><tr><td><eq>\hat{\gamma}_{r,j}(1)</eq></td><td>0.0</td><td>3.2</td><td>6.4</td><td>-5.2</td><td>-5.6</td><td>5.3</td><td>-8.3</td><td>-57.1</td><td>32.9</td><td>50.6</td><td>23.8</td><td>11.6</td></tr></table>

Table 11a: Correlation matrix of variables for cross-sectional analysis of weekly turnover of NYSE or AMEX ordinary common shares (CRSP share codes 10 and 11, excluding 37 stocks containing Z-errors in reported volume) for subperiods of the sample period from July 1962 to December 1996. The variables are: $\overline { { \tau } } _ { j }$ (average turnover); $\tilde { \tau } _ { j }$ (median turnover); $\hat { \alpha } _ { \tau , j } , \hat { \beta } _ { \tau , j }$ and $\hat { \sigma } _ { \epsilon , \tau , j }$ (the intercept, slope, and residual, respectively, from the time-series regression of an individual security’s turnover on market turnover); $\hat { \alpha } _ { r , j } , \hat { \beta } _ { r , j }$ , and $\hat { \sigma } _ { \epsilon , r , j }$ (the intercept, slope, and residual, respectively, from the time-series regression of an individual security’s return on the market return); $v _ { j }$ (natural logarithm of market capitalization), $p _ { j }$ (natural logarithm of price); $d _ { j }$ (dividend yield); $\mathrm { S P } _ { j } ^ { \Xi 0 0 }$ (S&P 500 indicator variable); and $\hat { \gamma } _ { r , j } ( 1 )$ (first-order return autocovariance). 

<table><tr><td></td><td><eq>\overline{\tau}_{j}</eq></td><td><eq>\tilde{\tau}_{j}</eq></td><td><eq>\hat{\alpha}_{\tau,j}</eq></td><td><eq>\hat{\beta}_{\tau,j}</eq></td><td><eq>\hat{\sigma}_{\epsilon,\tau,j}</eq></td><td><eq>\hat{\alpha}_{r,j}</eq></td><td><eq>\hat{\beta}_{r,j}</eq></td><td><eq>\hat{\sigma}_{\epsilon,r,j}</eq></td><td><eq>v_{j}</eq></td><td><eq>p_{j}</eq></td><td><eq>d_{j}</eq></td><td><eq>SP_{j}^{500}</eq></td></tr><tr><td></td><td colspan="12">1977 to 1981 (2,352 stocks)</td></tr><tr><td><eq>\tilde{\tau}_{j}</eq></td><td>96.4</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\alpha}_{\tau,j}</eq></td><td>6.7</td><td>11.0</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\beta}_{\tau,j}</eq></td><td>61.9</td><td>55.1</td><td>-72.9</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\sigma}_{\epsilon,\tau,j}</eq></td><td>83.0</td><td>67.4</td><td>3.5</td><td>54.9</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\alpha}_{r,j}</eq></td><td>10.6</td><td>2.8</td><td>-8.2</td><td>16.9</td><td>22.7</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\beta}_{r,j}</eq></td><td>59.8</td><td>63.8</td><td>-11.0</td><td>47.1</td><td>35.6</td><td>3.2</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\sigma}_{\epsilon,r,j}</eq></td><td>28.5</td><td>18.3</td><td>-8.2</td><td>25.6</td><td>42.8</td><td>30.8</td><td>24.9</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>v_{j}</eq></td><td>5.3</td><td>15.7</td><td>6.7</td><td>-2.0</td><td>-16.5</td><td>-26.8</td><td>16.4</td><td>-63.4</td><td></td><td></td><td></td><td></td></tr><tr><td><eq>p_{j}</eq></td><td>8.1</td><td>17.1</td><td>11.7</td><td>-3.6</td><td>-10.8</td><td>-9.0</td><td>12.2</td><td>-70.1</td><td>80.8</td><td></td><td></td><td></td></tr><tr><td><eq>d_{j}</eq></td><td>-18.4</td><td>-18.2</td><td>3.8</td><td>-15.2</td><td>-14.7</td><td>1.4</td><td>-27.9</td><td>-27.3</td><td>9.9</td><td>13.0</td><td></td><td></td></tr><tr><td><eq>SP_{j}^{500}</eq></td><td>2.5</td><td>8.4</td><td>-0.4</td><td>2.5</td><td>-8.9</td><td>-19.0</td><td>8.5</td><td>-28.5</td><td>51.6</td><td>35.1</td><td>2.8</td><td></td></tr><tr><td><eq>\hat{\gamma}_{r,j}(1)</eq></td><td>0.2</td><td>3.0</td><td>1.8</td><td>-1.3</td><td>-5.3</td><td>-3.6</td><td>-2.3</td><td>-55.6</td><td>31.5</td><td>52.1</td><td>14.7</td><td>10.5</td></tr><tr><td></td><td colspan="12">1982 to 1986 (2,644 stocks)</td></tr><tr><td><eq>\tilde{\tau}_{j}</eq></td><td>96.2</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\alpha}_{\tau,j}</eq></td><td>-12.0</td><td>-5.6</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\beta}_{\tau,j}</eq></td><td>71.3</td><td>64.3</td><td>-77.8</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\sigma}_{\epsilon,\tau,j}</eq></td><td>80.0</td><td>62.8</td><td>-19.8</td><td>64.7</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\alpha}_{r,j}</eq></td><td>-7.4</td><td>-10.9</td><td>-14.5</td><td>6.2</td><td>2.4</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\beta}_{r,j}</eq></td><td>46.4</td><td>50.6</td><td>-12.6</td><td>38.3</td><td>24.8</td><td>-32.5</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\sigma}_{\epsilon,r,j}</eq></td><td>15.4</td><td>7.3</td><td>12.3</td><td>0.7</td><td>25.2</td><td>-17.7</td><td>15.6</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>v_{j}</eq></td><td>19.0</td><td>29.7</td><td>-8.3</td><td>18.8</td><td>-5.0</td><td>-3.1</td><td>27.6</td><td>-55.7</td><td></td><td></td><td></td><td></td></tr><tr><td><eq>p_{j}</eq></td><td>9.0</td><td>16.5</td><td>-12.4</td><td>15.3</td><td>-5.9</td><td>22.3</td><td>10.3</td><td>-76.1</td><td>75.3</td><td></td><td></td><td></td></tr><tr><td><eq>d_{j}</eq></td><td>-6.7</td><td>-7.6</td><td>-4.1</td><td>-0.5</td><td>-2.5</td><td>15.5</td><td>-12.6</td><td>-21.4</td><td>16.6</td><td>20.5</td><td></td><td></td></tr><tr><td><eq>SP_{j}^{500}</eq></td><td>15.5</td><td>22.7</td><td>-2.0</td><td>12.1</td><td>-1.6</td><td>-3.8</td><td>18.2</td><td>-24.7</td><td>57.3</td><td>37.5</td><td>8.0</td><td></td></tr><tr><td><eq>\hat{\gamma}_{r,j}(1)</eq></td><td>5.2</td><td>5.6</td><td>-8.9</td><td>9.5</td><td>4.1</td><td>18.9</td><td>-0.4</td><td>-39.2</td><td>15.7</td><td>32.6</td><td>7.1</td><td>5.2</td></tr><tr><td></td><td colspan="12">1987 to 1991 (2,471 stocks)</td></tr><tr><td><eq>\tilde{\tau}_{j}</eq></td><td>94.1</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\alpha}_{\tau,j}</eq></td><td>17.1</td><td>25.8</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\beta}_{\tau,j}</eq></td><td>50.8</td><td>39.2</td><td>-76.0</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\sigma}_{\epsilon,\tau,j}</eq></td><td>79.1</td><td>56.6</td><td>-1.0</td><td>53.0</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\alpha}_{r,j}</eq></td><td>7.1</td><td>5.1</td><td>16.8</td><td>-9.7</td><td>9.2</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\beta}_{r,j}</eq></td><td>45.4</td><td>49.4</td><td>5.0</td><td>25.5</td><td>22.3</td><td>-15.0</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\sigma}_{\epsilon,r,j}</eq></td><td>3.1</td><td>-3.6</td><td>-0.7</td><td>2.5</td><td>12.7</td><td>24.4</td><td>-2.6</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>v_{j}</eq></td><td>20.3</td><td>31.7</td><td>3.3</td><td>10.4</td><td>-2.0</td><td>5.6</td><td>22.4</td><td>-48.1</td><td></td><td></td><td></td><td></td></tr><tr><td><eq>p_{j}</eq></td><td>12.3</td><td>22.0</td><td>6.4</td><td>2.5</td><td>-5.7</td><td>10.8</td><td>11.2</td><td>-62.0</td><td>80.4</td><td></td><td></td><td></td></tr><tr><td><eq>d_{j}</eq></td><td>-1.2</td><td>-1.9</td><td>-1.8</td><td>0.8</td><td>1.6</td><td>2.9</td><td>-4.7</td><td>-10.9</td><td>12.9</td><td>15.7</td><td></td><td></td></tr><tr><td><eq>SP_{j}^{500}</eq></td><td>16.1</td><td>25.4</td><td>-1.4</td><td>11.6</td><td>-3.8</td><td>-2.4</td><td>19.1</td><td>-20.7</td><td>58.7</td><td>39.1</td><td>5.9</td><td></td></tr><tr><td><eq>\hat{\gamma}_{r,j}(1)</eq></td><td>4.2</td><td>5.5</td><td>2.7</td><td>0.5</td><td>0.4</td><td>-39.5</td><td>11.7</td><td>-76.1</td><td>14.4</td><td>23.0</td><td>2.9</td><td>4.4</td></tr><tr><td></td><td colspan="12">1992 to 1996 (2,520 stocks)</td></tr><tr><td><eq>\tilde{\tau}_{j}</eq></td><td>94.8</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\alpha}_{\tau,j}</eq></td><td>6.8</td><td>10.8</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\beta}_{\tau,j}</eq></td><td>55.8</td><td>49.1</td><td>-78.9</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\sigma}_{\epsilon,\tau,j}</eq></td><td>79.1</td><td>58.6</td><td>6.0</td><td>43.8</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\alpha}_{r,j}</eq></td><td>-2.8</td><td>-6.4</td><td>-13.5</td><td>9.6</td><td>3.8</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\beta}_{r,j}</eq></td><td>46.6</td><td>49.1</td><td>0.0</td><td>28.7</td><td>27.8</td><td>-14.4</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>\hat{\sigma}_{\epsilon,r,j}</eq></td><td>18.6</td><td>6.4</td><td>5.4</td><td>7.4</td><td>36.3</td><td>24.2</td><td>4.2</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td><eq>v_{j}</eq></td><td>10.1</td><td>23.8</td><td>-7.1</td><td>12.0</td><td>-18.8</td><td>-15.7</td><td>27.8</td><td>-61.5</td><td></td><td></td><td></td><td></td></tr><tr><td><eq>p_{j}</eq></td><td>5.8</td><td>17.2</td><td>-3.3</td><td>6.1</td><td>-17.4</td><td>-8.4</td><td>16.2</td><td>-76.8</td><td>81.5</td><td></td><td></td><td></td></tr><tr><td><eq>d_{j}</eq></td><td>-9.5</td><td>-8.3</td><td>-1.5</td><td>-4.5</td><td>-9.3</td><td>0.4</td><td>-6.4</td><td>-14.6</td><td>13.3</td><td>15.4</td><td></td><td></td></tr><tr><td><eq>SP_{j}^{500}</eq></td><td>6.6</td><td>15.9</td><td>-8.8</td><td>11.5</td><td>-12.3</td><td>-9.1</td><td>17.5</td><td>-24.2</td><td>56.7</td><td>37.7</td><td>11.0</td><td></td></tr><tr><td><eq>\hat{\gamma}_{r,j}(1)</eq></td><td>2.3</td><td>4.9</td><td>-2.3</td><td>3.2</td><td>-3.8</td><td>1.2</td><td>12.1</td><td>-23.2</td><td>19.1</td><td>29.3</td><td>5.0</td><td>4.5</td></tr></table>


Table 11b: (continued).


ing the first four subperiods, with correlations ranging from −10.6% (1967–1971) to 8.6% (1972–1976). However, with the advent of S&P 500 futures and the growing popularity of indexation in the early 1980’s, median turnover becomes more highly correlated with S&P 500 membership, jumping to 22.7% in 1982–1986, 25.4% in 1987–1991, and 15.9% in 1992–1996. 

Turnover betas and return betas are highly positively correlated, with correlations ranging from 25.5% (1987–1991) to 55.4% (1967–1971). Not surprisingly, log-price $p _ { j }$ is highly positively correlated with log-market-capitalization $v _ { j }$ , with correlations exceeding 75% in every subperiod. Dividend yield is positively correlated with both log price and log market capitalization, though the correlation is not particularly large. This may seem counterintuitive at first but recall that these are cross-sectional correlations, not time-series correlations, and the level of dividends per share varies cross-sectionally as well as average log-price. 

## 4.3 Regression Results

Table 12 contains the estimates of the cross-sectional regression model (9). We estimated three regression models for each subperiod: one with all eight variables and a constant term included, one excluding log market-capitalization, and one excluding log price. Since the log price and log market-capitalization regressors are so highly correlated (see Lim et al. (1998)), regressions with only one or the other included were estimated to gauge the efects of multicollinearity. The exclusion of either variable does not afect the qualitative features of the regression—no significant coeficients changed sign other than the constant term—though the quantitative features were afected to a small degree. For example, in the first subperiod $v _ { j }$ has a negative coeficient (−0.064) and $p _ { j }$ has a positive coeficient (0.150), both significant at the 5% level. When $v _ { j }$ is omitted the coeficient of $p _ { j }$ is still positive but smaller (0.070), and when $p _ { j }$ is omitted the coeficient of $v _ { j }$ is still negative and also smaller in absolute magnitude (−0.028), and in both these cases the coeficients retain their significance. 

The fact that size has a negative impact on turnover while price has a positive impact is an artifact of the earlier subperiods. This can be seen heuristically in the time-series plots of Figure 1—compare the value-weighted and equal-weighted turnover indexes during the first two or three subperiods. Smaller-capitalization stocks seem to have higher turnover than larger-capitalization stocks. 

This begins to change in the 1977–1981 subperiod: the size coeficient is negative but not significant, and when price is excluded, the size coeficient changes sign and becomes significant. In the subperiods after 1977–1981, both size and price enter positively. One explanation of this change is the growth of the mutual fund industry and other large institutional investors in the early 1980’s. As portfolio managers manage larger asset bases, it becomes more dificult to invest in smaller-capitalization companies because of liquidity and corporate-control issues. Therefore, the natural economies of scale in investment management coupled with the increasing concentration of investment capital make small stocks less actively traded than large stocks. Of course, this efect should have implications for the equilibrium return of small stocks versus large stocks. 

The first-order return autocovariance has a positive coeficient in all subperiods except the second regression of the last subperiod (in which the coeficient is negative but insignificant), and these coeficients are significant at the 5% level in all subperiods except 1972–1976 and 1992–1996. This is consistent with the trading-cost interpretation of $\hat { \gamma } _ { r , j } ( 1 )$ : a large negative return autocovariance implies a large efective bid/ask spread which, in turn, should imply lower turnover. 

Membership in the S&P 500 also has a positive impact on turnover in all subperiods as expected, and the magnitude of the coeficient increases dramatically in the 1982–1986 subperiod—from 0.013 in the previous period to 0.091—also as expected given the growing importance of indexation and index arbitrage during this period, and the introduction of S&P 500 futures contracts in April 1982. Surprisingly, in the 1992–1996 subperiod, the S&P 500 coeficient declines to 0.029, perhaps because of the interactions between this indicator variable and size and price (all three variables are highly positively correlated with each other; see Lim et al. (1998) for further details). When size is omitted, S&P 500 membership becomes more important, yet when price is omitted, size becomes more important and S&P 500 membership becomes irrelevant. These findings are roughly consistent with those in Tkac (1999).<sup>23</sup> 

Both systematic and idiosyncratic risk— ${ - \hat { \beta } _ { r , j } }$ and $\hat { \sigma } _ { \epsilon , r , j }$ —have positive and significant impact on turnover in all subperiods. However, the impact of excess expected returns $\hat { \alpha } _ { r , j }$ on turnover is erratic: negative and significant in the 1977–1981 and 1992–1996 subperiods, and positive and significant in the others. 

<table><tr><td>c</td><td><eq>\hat{\alpha}_{r,j}</eq></td><td><eq>\hat{\beta}_{r,j}</eq></td><td><eq>\hat{\sigma}_{\epsilon,r,j}</eq></td><td><eq>v_j</eq></td><td><eq>p_j</eq></td><td><eq>d_j</eq></td><td>SP500j</td><td><eq>\hat{\gamma}_{r,j}(1)</eq></td><td>R2(%)</td></tr><tr><td colspan="10">1962 to 1966 (234 weeks, 2,073 stocks)</td></tr><tr><td>0.742(0.108)</td><td>0.059(0.019)</td><td>0.354(0.014)</td><td>0.043(0.006)</td><td>-0.064(0.006)</td><td>0.150(0.014)</td><td>0.071(0.081)</td><td>0.048(0.018)</td><td>0.004(0.001)</td><td>41.8</td></tr><tr><td>-0.306(0.034)</td><td>0.068(0.020)</td><td>0.344(0.015)</td><td>0.053(0.006)</td><td>—</td><td>0.070(0.012)</td><td>0.130(0.083)</td><td>-0.006(0.018)</td><td>0.006(0.001)</td><td>38.8</td></tr><tr><td>0.378(0.105)</td><td>0.111(0.019)</td><td>0.401(0.014)</td><td>0.013(0.005)</td><td>-0.028(0.005)</td><td>—</td><td>0.119(0.083)</td><td>0.048(0.019)</td><td>0.005(0.001)</td><td>38.7</td></tr><tr><td colspan="10">1967 to 1971 (261 weeks, 2,292 stocks)</td></tr><tr><td>0.289(0.181)</td><td>0.134(0.024)</td><td>0.448(0.023)</td><td>0.095(0.009)</td><td>-0.062(0.010)</td><td>0.249(0.023)</td><td>0.027(0.235)</td><td>0.028(0.025)</td><td>0.006(0.002)</td><td>44.7</td></tr><tr><td>-0.797(0.066)</td><td>0.152(0.024)</td><td>0.434(0.023)</td><td>0.112(0.009)</td><td>—</td><td>0.173(0.020)</td><td>0.117(0.237)</td><td>-0.026(0.024)</td><td>0.007(0.002)</td><td>43.7</td></tr><tr><td>-0.172(0.180)</td><td>0.209(0.023)</td><td>0.507(0.023)</td><td>0.057(0.009)</td><td>-0.009(0.009)</td><td>—</td><td>-0.108(0.241)</td><td>0.023(0.026)</td><td>0.011(0.002)</td><td>41.9</td></tr><tr><td colspan="10">1972 to 1976 (261 weeks, 2,084 stocks)</td></tr><tr><td>0.437(0.092)</td><td>0.102(0.015)</td><td>0.345(0.013)</td><td>0.027(0.003)</td><td>-0.041(0.005)</td><td>0.171(0.012)</td><td>-0.031(0.079)</td><td>0.031(0.015)</td><td>0.001(0.001)</td><td>38.0</td></tr><tr><td>-0.249(0.027)</td><td>0.111(0.015)</td><td>0.320(0.013)</td><td>0.032(0.003)</td><td>—</td><td>0.114(0.009)</td><td>-0.058(0.080)</td><td>-0.007(0.014)</td><td>0.002(0.001)</td><td>36.5</td></tr><tr><td>-0.188(0.085)</td><td>0.141(0.015)</td><td>0.367(0.014)</td><td>0.008(0.003)</td><td>0.008(0.004)</td><td>—</td><td>-0.072(0.082)</td><td>0.020(0.015)</td><td>0.003(0.001)</td><td>32.7</td></tr><tr><td colspan="10">1977 to 1981 (261 weeks, 2,352 stocks)</td></tr><tr><td>-0.315(0.127)</td><td>-0.059(0.020)</td><td>0.508(0.018)</td><td>0.057(0.006)</td><td>-0.001(0.007)</td><td>0.139(0.017)</td><td>0.015(0.069)</td><td>0.013(0.019)</td><td>0.005(0.002)</td><td>44.2</td></tr><tr><td>-0.344(0.035)</td><td>-0.058(0.019)</td><td>0.508(0.017)</td><td>0.057(0.005)</td><td>—</td><td>0.137(0.013)</td><td>0.015(0.069)</td><td>0.011(0.018)</td><td>0.005(0.002)</td><td>44.2</td></tr><tr><td>-0.810(0.114)</td><td>-0.008(0.019)</td><td>0.534(0.018)</td><td>0.040(0.005)</td><td>0.037(0.006)</td><td>—</td><td>-0.001(0.070)</td><td>-0.001(0.020)</td><td>0.009(0.002)</td><td>42.6</td></tr><tr><td colspan="10">1982 to 1986 (261 weeks, 2,644 stocks)</td></tr><tr><td>-1.385(0.180)</td><td>0.051(0.025)</td><td>0.543(0.027)</td><td>0.062(0.007)</td><td>0.071(0.010)</td><td>0.085(0.023)</td><td>-0.223(0.081)</td><td>0.091(0.031)</td><td>0.006(0.001)</td><td>31.6</td></tr><tr><td>-0.193(0.051)</td><td>0.018(0.024)</td><td>0.583(0.027)</td><td>0.057(0.007)</td><td>—</td><td>0.170(0.020)</td><td>-0.182(0.081)</td><td>0.187(0.028)</td><td>0.005(0.001)</td><td>30.4</td></tr><tr><td>-1.602(0.170)</td><td>0.080(0.023)</td><td>0.562(0.027)</td><td>0.048(0.005)</td><td>0.091(0.009)</td><td>—</td><td>-0.217(0.081)</td><td>0.085(0.031)</td><td>0.006(0.001)</td><td>31.3</td></tr><tr><td colspan="10">1987 to 1991 (261 weeks, 2,471 stocks)</td></tr><tr><td>-1.662(0.223)</td><td>0.155(0.027)</td><td>0.791(0.034)</td><td>0.038(0.005)</td><td>0.078(0.013)</td><td>0.066(0.024)</td><td>-0.138(0.097)</td><td>0.131(0.041)</td><td>0.003(0.001)</td><td>31.9</td></tr><tr><td>-0.313(0.052)</td><td>0.153(0.027)</td><td>0.831(0.033)</td><td>0.035(0.005)</td><td>—</td><td>0.158(0.019)</td><td>-0.128(0.098)</td><td>0.252(0.036)</td><td>0.003(0.001)</td><td>30.9</td></tr><tr><td>-1.968(0.195)</td><td>0.171(0.026)</td><td>0.795(0.034)</td><td>0.031(0.005)</td><td>0.100(0.010)</td><td>—</td><td>-0.122(0.097)</td><td>0.119(0.041)</td><td>0.003(0.001)</td><td>31.7</td></tr><tr><td colspan="10">1992 to 1996 (261 weeks, 2,520 stocks)</td></tr><tr><td>-1.004(0.278)</td><td>-0.087(0.034)</td><td>0.689(0.033)</td><td>0.077(0.007)</td><td>0.040(0.016)</td><td>0.262(0.033)</td><td>-0.644(0.164)</td><td>0.029(0.049)</td><td>0.000(0.001)</td><td>29.6</td></tr><tr><td>-0.310(0.061)</td><td>-0.095(0.034)</td><td>0.708(0.032)</td><td>0.076(0.007)</td><td>—</td><td>0.314(0.026)</td><td>-0.641(0.164)</td><td>0.087(0.043)</td><td>-0.001(0.001)</td><td>29.4</td></tr><tr><td>-2.025(0.249)</td><td>-0.025(0.034)</td><td>0.711(0.033)</td><td>0.046(0.006)</td><td>0.115(0.012)</td><td>—</td><td>-0.590(0.166)</td><td>-0.005(0.049)</td><td>0.000(0.001)</td><td>27.8</td></tr></table>


Table 12a: Cross-sectional regressions of median weekly turnover of NYSE and AMEX ordinary common shares (CRSP share codes 10 and 11, excluding 37 stocks containing Zerrors in reported volume) for five-year subperiods of the sample period from July 1962 to December 1996. The explanatory variables are: $\hat { \alpha } _ { r , j } , \hat { \beta } _ { r , j } ,$ , and $\hat { \sigma } _ { \epsilon , r , j }$ (the intercept, slope, and residual, respectively, from the time-series regression of an individual security’s return on the market return); $v _ { j }$ (natural logarithm of market capitalization), $p _ { j }$ (natural logarithm of price); $d _ { j }$ (dividend yield); $\mathrm { S P 5 0 0 } _ { j }$ (S&P 500 indicator variable); and $\hat { \gamma } _ { r , j } ( 1 )$ (first-order return autocovariance).


The dividend-yield regressor is insignificant in all subperiods but two: 1982–1986 and 1992–1996. In these two subperiods, the coeficient is negative, which contradicts the notion that dividend-capture trading afects turnover. 

In summary, the cross-sectional variation of turnover does seem related to several stockspecific characteristics such as risk, size, price, trading costs, and S&P 500 membership. The explanatory power of these cross-sectional regressions—as measured by $R ^ { 2 }$ —range from 29.6% (1992–1996) to 44.7% (1967–1971), rivaling the $R ^ { 2 } \mathrm { { ^ { s } } }$ of typical cross-sectional return regressions. With sample sizes ranging from 2,073 (1962–1966) to 2,644 (1982–1986) stocks, these $R ^ { 2 } { \mathfrak { s } }$ provide some measure of confidence that cross-sectional variations in median turnover are not purely random but do bear some relation to economic factors. In order to further analyze the cross-section of turnover, additional economic structure is needed. This is the task for the following two sections. 

## 5 Volume Implications of Portfolio Theory

The diversity in the portfolio holdings of individuals and institutions and in their motives for trade suggests that the time-series and cross-sectional patterns of trading activity can be quite complex. However, standard portfolio theory provides an enormous simplification: under certain conditions, mutual-fund separation holds, i.e., investors are indiferent between choosing among the entire universe of securities and a small number of mutual funds (see, for example, Cass and Stiglitz (1970), Markowitz (1952), Ross (1978), Tobin (1958), and Merton (1973)). In this case, all investors trade only in these separating funds and simpler cross-sectional patterns in trading activity emerge, and in this section we derive such crosssectional implications. 

While several models can deliver mutual-fund separation, e.g., the CAPM and ICAPM, we do not specify any such model here, but simply assert that mutual-fund separation holds. In particular, in this section we focus primarily on the cross-sectional properties of volume, we assume nothing about the behavior of asset prices, e.g., a factor structure for asset returns may or may not exist. As long as mutual-fund separation holds, the results in this section (in particular, Section 5.1 and 5.2) must apply. However, in Section 6, we provide a specific intertemporal capital asset pricing model, in which mutual-fund separation holds and the separating funds are linked with the underlying risk structure of the stocks. 

The strong implications of mutual-fund separation for volume that we derive in this section suggest that the assumptions underlying the theory may be quite restrictive and therefore implausible (see, for example, Cass and Stiglitz (1970), Markowitz (1952), Ross (1978), and Tobin (1958)). For example, mutual-fund separation is often derived in static settings in which the motives for trade are not explicitly modeled. Also, most models of mutual-fund separation use a partial equilibrium framework with exogenously specified return distributions and strong restrictions on preferences. Furthermore, these models tend to focus on a rather narrow set of trading motives—changes in portfolio holdings due to changes in return distributions or preferences—ignoring other factors that may motivate individuals and institutions to adjust their portfolios, e.g., asymmetric information, idiosyncratic risk, transactions costs, taxes and other market imperfections. Finally, it has sometimes been argued that recent levels of trading activity in financial markets are simply too high to be attributable to the portfolio-rebalancing needs of rational economic agents. 

A detailed discussion of these concerns is beyond the scope of this chapter. Moreover, we are not advocating any particular structural model of mutual-fund separation here, but merely investigating the implications for trading volume when mutual-fund separation holds. Nevertheless, before deriving these implications, it is important to consider how some of the limitations of mutual-fund separation may afect the interpretation of our analysis. 

First, many of the limitations of mutual-fund separation theorems can be overcome to some degree. For example, extending mutual-fund separation results to dynamic settings is possible. As in the static case, restrictive assumptions on preferences and/or return processes are often required to obtain mutual-fund separation in a discrete-time setting. However, in a continuous-time setting—which has its own set of restrictive assumptions—Merton (1973) shows that mutual-fund separation holds for quite general preferences and return processes. 

Also, it is possible to embed mutual-fund separation in a general equilibrium framework in which asset returns are determined endogenously. The CAPM is a well-known example of mutual-fund separation in a static equilibrium setting. To obtain mutual-fund separation in a dynamic equilibrium setting, stronger assumptions are required—Section 6 provide such an example.<sup>24</sup> 

Of course, from a theoretical standpoint, no existing model is rich enough to capture the full spectrum of portfolio-rebalancing needs of all market participants, e.g., risk-sharing, hedging, liquidity, and speculation. Therefore, it is dificult to argue that current levels of trading activity are too high to be justified by rational portfolio rebalancing. Indeed, under the standard assumption of a difusion information structure, volume is unbounded in absence of transaction costs. Moreover, from an empirical standpoint, little efort has been devoted to calibrating the level of trading volume within the context of a realistic asset-market model (see Lo, Mamaysky and Wang (2004) for more discussions). 

Despite the simplistic nature of mutual-fund separation, we study its volume implications for several reasons. One compelling reason is the fact that mutual-fund separation has become the workhorse of modern investment management. Although the assumptions of models such as the CAPM and ICAPM are known to be violated in practice, these models are viewed by many as a useful approximation for quantifying the trade-of between risk and expected return in financial markets. Thus, it seems natural to begin with such models in an investigation of trading activity in asset markets. Mutual-fund separation may seem inadequate—indeed, some might say irrelevant—for modeling trading activity, nevertheless it may yield an adequate approximation for quantifying the cross-sectional properties of trading volume. If it does not, then this suggests the possibility of important weaknesses in the theory, weaknesses that may have implications that extend beyond trading activity, e.g., preference restrictions, risk-sharing characteristics, asymmetric information, and liquidity. Of course, the virtue of such an approximation can only be judged by its empirical performance, which we examine in this chapter. 

Another reason for focusing on mutual-fund separation is that it can be an important benchmark in developing a more complete model of trading volume. The trading motives that mutual-fund separation captures (such as portfolio rebalancing) may be simple and incomplete, but they are important, at least in the context of models such as the CAPM and ICAPM. Using mutual-fund separation as a benchmark allows us to gauge how important other trading motives may be in understanding the diferent aspects of trading volume. For example, in studying the market reaction to corporate announcements and dividends, the factor model implied by mutual-fund separation can be used as a “market model” in defining the abnormal trading activity that is associated with these events (Tkac (1999) discusses this in the special case of two-fund separation). 

Factors such as asymmetric information, idiosyncratic risks, transaction costs, and other forms of market imperfections are also likely to be relevant for determining the level and variability of trading activity. Each of these issues has been the focus of recent research, but only in the context of specialized models. To examine their importance in explaining volume, we need a more general and unified framework that can capture these factors. Unfortunately, such a model has not yet been developed. 

For all these reasons, we examine the implications of mutual-fund separation for trading activity in this section. The theoretical implications serve as valuable guides for our data construction and empirical analysis, but it is useful to keep their limitations in mind. We view this as the first step in developing a more complete understanding of trading and pricing in asset markets and we hope to explore these other issues in future research (see also Section 6). 

In Section 5.1 we consider the case of two-fund separation in which one fund is the riskless asset and the second fund is a portfolio of risky assets. In Section 5.2 we investigate the general case of (K +1)-fund separation, one riskless fund and K risky funds. Mutual-fund separation with a riskless asset is often called monetary separation to distinguish it from the case without a riskless asset. We assume the existence of a riskless asset mainly to simplify the exposition, but for our purposes this assumption entails no loss of generality.<sup>25</sup> Thus, in what follows, we consider only cases of monetary separation without further qualification. The analysis is mainly based on Lo and Wang (2000). 

## 5.1 Two-Fund Separation

Without loss of generality, we normalize the total number of shares outstanding for each stock to one in this section, i.e., $N _ { j } = 1 , j = 1 , \dots , J$ , and we begin by assuming two-fund separation, i.e., all investors invest in the same two mutual funds: the riskless asset and a stock fund. Market clearing requires that the stock fund is the “market” portfolio. Given our normalization, the market portfolio $S ^ { M }$ —measured in shares outstanding—is simply a vector of one’s: $S ^ { M } = [ \mathrm { ~ 1 ~ } \cdots \mathrm { ~ 1 ~ } ] ^ { \intercal }$ . Two-fund separation implies that the stock holdings of any investor i at time t is given by: 

$$
S _ {t} ^ {i} = h _ {t} ^ {i} S ^ {M} = h _ {t} ^ {i} \left( \begin{array}{c} 1 \\ \vdots \\ 1 \end{array} \right), \qquad i = 1, \ldots , I\tag{10}
$$

where $h _ { t } ^ { i }$ is the share of the market portfolio held by investor i (and $\textstyle \sum _ { i } h _ { t } ^ { i } = 1$ for all t). His holding in stock $j$ is then $S _ { j t } ^ { i } = h _ { t } ^ { i } , j = 1 , . . . , J$ . Over time, investor i may wish to adjust his portfolio. If he does, he does so by trading only in the two funds (by the assumption of two-fund separation), hence he purchases or sells stocks in very specific proportions, as fractions of the market portfolio. His trading in stock j, normalized by shares outstanding, is: $S _ { j t } ^ { i } - S _ { j t - 1 } ^ { i } = h _ { t } ^ { i } - h _ { t - 1 } ^ { i } , i = 1 , \dots , I$ . But this, in turn, implies $S _ { j t } ^ { i } - S _ { j t - 1 } ^ { i } = S _ { j ^ { \prime } t } ^ { i } - S _ { j ^ { \prime } t - 1 } ^ { i }$ $j , j ^ { \prime } = 1 , \ldots , J ,$ . Thus, if two-fund separation holds, investor i’s trading activity in each stock, normalized by shares outstanding, is identical across all stocks. This has an important implication for the turnover of stock j: 

$$
\tau_ {j t} = \frac {1}{2} \sum_ {i = 1} ^ {I} | S _ {j t} ^ {i} - S _ {j t - 1} ^ {i} | = \frac {1}{2} \sum_ {i = 1} ^ {I} | h _ {t} ^ {i} - h _ {t - 1} ^ {i} |, \qquad j = 1, \ldots , J\tag{11}
$$

which is given by the following proposition: 

Proposition 1 When two-fund separation holds, the turnover of all individual stocks are identical. 

Proposition 1 has strong implications for the turnover of the market portfolio. From the definition of Section 2.3, the turnover of the market portfolio is: 

$$
\tau_ {t} ^ {V W} \equiv \sum_ {j = 1} ^ {J} w _ {j t} ^ {V W} \tau_ {j t} = \tau_ {j t}, \qquad j = 1, \ldots , J.
$$

The turnover of individual stocks is identical to the turnover of the market portfolio. This is not surprising given that individual stocks have identical values for turnover. Indeed, all portfolios of risky assets have the same turnover as individual stocks. For reasons that becomes apparent in Section 5.2, we can express the turnover of individual stocks as an exact linear one-factor model: 

$$
\tau_ {j t} = b _ {j} \tilde {F} _ {t}, \qquad j = 1, \ldots , J\tag{12}
$$

where $\tilde { F } _ { t } = \tau _ { t } ^ { V W }$ and $b _ { j } = 1$ 

Proposition 1 also implies that under two-fund separation the share volume of individual stocks is proportional to the total number of shares outstanding and dollar volume is proportional to market capitalization. Another implication is that each security’s relative dollar-volume is identical to its relative market-capitalization for all t: $\begin{array} { r l } { P _ { j t } V _ { j t } / \left( \sum _ { j } P _ { j t } V _ { j t } \right) = } \end{array}$ $\begin{array} { r l } { P _ { j t } N _ { j } / \left( \sum _ { j } P _ { j t } N _ { j } \right) } \end{array}$ . This relation is tested in Tkac (1999). Tkac (1999) derives this result in the context of a continuous-time dynamic equilibrium model with a special form of heterogeneity in preferences, but it holds more generally for any model that implies two-fund separation.<sup>26</sup> 

## 5.2 (K+1)-Fund Separation

We now consider the more general case where (K + 1)-fund separation holds. Let $S _ { k t } =$ $( S _ { 1 t } ^ { k } , \ldots , S _ { J t } ^ { k } ) ^ { \top } , k = 1 , \ldots , K$ , denote the K separating stock funds, where the separating funds are expressed in terms of the number of shares of their component stocks. The stock holdings of any investor i are given by 

$$
\left( \begin{array}{c} S _ {1 t} ^ {i} \\ \vdots \\ S _ {\mathcal {J} t} ^ {i} \end{array} \right) = \sum_ {k = 1} ^ {K} h _ {k t} ^ {i} S _ {t} ^ {k}, \qquad i = 1, \ldots , I.\tag{13}
$$

In particular, his holding in stock $j$ is $\begin{array} { r } { S _ { j t } ^ { i } = \sum _ { k = 1 } ^ { K } h _ { k t } ^ { i } S _ { j t } ^ { k } } \end{array}$ . Therefore, the turnover of stock j at time t is 

$$
\tau_ {j t} = \frac {1}{2} \sum_ {i = 1} ^ {I} | S _ {j t} ^ {i} - S _ {j t - 1} ^ {i} | = \frac {1}{2} \sum_ {i = 1} ^ {I} \Big | \sum_ {k = 1} ^ {K} \left(h _ {k t} ^ {i} S _ {j t} ^ {k} - h _ {k t - 1} ^ {i} S _ {j t} ^ {k}\right) \Big |, j = 1, \ldots , J.\tag{14}
$$

We now impose the following assumption on the separating stock funds: 

Assumption 1 The separating stock funds, $S _ { t } ^ { k } , k = 1 , \ldots , K$ , are constant over time. 

Given that, in equilibrium, $\textstyle \sum _ { i = 1 } ^ { I } S _ { i , t } = S _ { M }$ for all t, we have 

$$
\sum_ {k = 1} ^ {K} \left(\sum_ {i = 1} ^ {I} h _ {k t} ^ {i}\right) S ^ {k} = S ^ {M}.
$$

Therefore, without loss of generality, we can assume that the market portfolio $S _ { M }$ is one of the separating stock funds, which we label as the first fund. Following Merton (1973), we call the remaining stock funds hedging portfolios.<sup>27</sup> 

To simplify notation, we define $\Delta h _ { k t } ^ { i } \equiv h _ { k t } ^ { i } - h _ { k t - 1 } ^ { i }$ as the change in investor $i \mathrm { \ ' } _ { \mathrm { S } }$ holding of fund k from t−1 to t. In addition, we assume that the amount of trading in the hedging portfolios is small for all investors: 

Assumption 2 For $k = 1 , \ldots , K$ , and $i = 1 , \ldots , I , \Delta h _ { 1 t } ^ { 1 } \equiv \tilde { h } _ { 1 t } ^ { 1 }$ and $\Delta h _ { k t } ^ { i } \equiv \lambda \tilde { h } _ { k t } ^ { i } ~ ( k \neq 1 )$ 2 where $| \tilde { h } _ { k t } ^ { i } | \le H < \infty , 0 < \lambda \ll 1$ and $\tilde { h } _ { 1 t } ^ { i } , \tilde { h } _ { 2 t } ^ { i } , . . . , \tilde { h } _ { J t } ^ { i }$ have a continuous joint probability density. 

We then have the following result (see the Appendix for the proof): 

Lemma 1 Under Assumptions 1–2, the turnover of stock j at time t can be approximated by 

$$
\tau_ {j t} \approx \frac {1}{2} \sum_ {i = 1} ^ {I} | \Delta h _ {1 t} ^ {i} | + \frac {1}{2} \sum_ {k = 2} ^ {K} \left[ \sum_ {i = 1} ^ {I} \mathrm{sgn} \left(\Delta h _ {1 t} ^ {i}\right) \Delta h _ {k t} ^ {i} \right] S _ {j} ^ {k}, \quad j = 1, \ldots , J\tag{15}
$$

and the $n { - } t h$ absolute moment of the approximation error is $o ( \lambda ^ { n } )$ 

Now define the following “factors”: 

$$
\begin{array}{r c l} \tilde {F} _ {1 t} & \equiv & \frac {1}{2} \sum_ {i = 1} ^ {I} \left| \Delta h _ {1 t} ^ {i} \right| \\ \tilde {F} _ {k t} & \equiv & \frac {1}{2} \sum_ {i = 1} ^ {I} \mathrm{sgn} \left(\Delta h _ {1 t} ^ {i}\right) \Delta h _ {k t} ^ {i}, \qquad k = 2, \ldots , K. \end{array}
$$

Then the turnover of each stock j can be represented by an approximate K-factor model 

$$
\tau_ {j t} = \tilde {F} _ {1 t} + \sum_ {k = 2} ^ {K} S _ {j} ^ {k} \tilde {F} _ {k t} + o (\lambda), \qquad j = 1, \ldots , J.\tag{16}
$$

In summary, we have: 

Proposition 2 Suppose that the riskless security, the market portfolio, and K −1 constant hedging portfolios are separating funds, and the amount of trading in the hedging portfolios is small. Then the turnover of each stock has an approximate K-factor structure. Moreover, the loading of each stock on the k-th factor gives its share weight in the k-th separating fund. 

## 5.3 Empirical Tests of (K+1)-Fund Separation

Since two-fund and (K+1)-fund separation imply an approximately linear factor structure for turnover, we can investigate these two possibilities by using principal components analysis to decompose the covariance matrix of turnover (see Muirhead (1982) for an exposition of principal components analysis). If turnover is driven by a linear K-factor model, the first K principal components should explain most of the time-series variation in turnover. More formally, if 

$$
\tau_ {j t} = \alpha_ {j} + \delta_ {1} F _ {1 t} + \dots + \delta_ {K} F _ {K t} + \varepsilon_ {j t}\tag{17}
$$

where $\operatorname { E } [ \varepsilon _ { j t } \varepsilon _ { j ^ { \prime } t } ] ~ = ~ 0$ for any $j \neq j ^ { \prime }$ , then the covariance matrix $\Sigma$ of the vector $\begin{array} { r l } { \tau _ { t } } & { { } \equiv } \end{array}$ $[ \mathbf { \nabla } \tau _ { 1 t } \quad \cdot \cdot \mathbf { \nabla } \tau _ { J t } ] ^ { \intercal }$ can be expressed as 

$$
\mathrm{Var} [ \tau_ {t} ] \equiv \Sigma = \eta \Theta \eta^ {\top}\tag{18}
$$

$$
\Theta = \left( \begin{array}{c c c c} \theta_ {1} & 0 & \dots & 0 \\ 0 & \theta_ {2} & & 0 \\ \vdots & & \ddots & \vdots \\ 0 & \dots & 0 & \theta_ {N} \end{array} \right)\tag{19}
$$

where Θ contains the eigenvalues of Σ along its diagonal and η is the matrix of corresponding eigenvectors. Since Σ is a covariance matrix, it is positive semidefinite hence all the eigenvalues are nonnegative. When normalized to sum to one, each eigenvalue can be interpreted as the fraction of the total variance of turnover attributable to the corresponding principal component. If (17) holds, it can be shown that as the size N of the cross section increases without bound, exactly K normalized eigenvalues of Σ approach positive finite limits, and the remaining N − K eigenvalues approach 0 (see, for example, Chamberlain (1983) and Chamberlain and Rothschild (1983)). Therefore, the plausibility of (17), and the value of K, can be gauged by examining the magnitudes of the eigenvalues of Σ. 

The only obstacle is the fact that the covariance matrix Σ must be estimated, hence we encounter the well-known problem that the standard estimator 

$$
\widehat {\Sigma} \equiv \frac {1}{T} \sum_ {t = 1} ^ {T} (\tau_ {t} - \overline {{\tau}}) (\tau_ {t} - \overline {{\tau}}) ^ {\top}
$$

is singular if the number of securities J in the cross section is larger than the number of time series observations $T . ^ { 2 8 }$ Since J is typically much larger than T—for a five-year subperiod T is generally 261 weeks, and J is typically well over 2,000—we must limit our attention to a smaller subset of stocks. We do this by following the common practice of forming a small number of portfolios (see Campbell, Lo, and MacKinlay (1997, Chapter 5)), sorted by turnover beta to maximize the dispersion of turnover beta among the portfolios.<sup>29</sup> In particular, within each five-year subperiod we form ten turnover-beta-sorted portfolios using betas estimated from the previous five-year subperiod, estimate the covariance matrix $\widehat { \Sigma }$ using 261 time-series observations, and perform a principal-components decomposition on $\widehat { \Sigma } .$ . For purposes of comparison and interpretation, we perfor m a parallel analysis for returns, using ten return-beta-sorted portfolios. The results are reported in Table 13. 

<table><tr><td><eq>\theta_1</eq></td><td><eq>\theta_2</eq></td><td><eq>\theta_3</eq></td><td><eq>\theta_4</eq></td><td><eq>\theta_5</eq></td><td><eq>\theta_6</eq></td><td><eq>\theta_7</eq></td><td><eq>\theta_8</eq></td><td><eq>\theta_9</eq></td><td><eq>\theta_{10}</eq></td><td>Period</td><td><eq>\theta_1</eq></td><td><eq>\theta_2</eq></td><td><eq>\theta_3</eq></td><td><eq>\theta_4</eq></td><td><eq>\theta_5</eq></td><td><eq>\theta_6</eq></td><td><eq>\theta_7</eq></td><td><eq>\theta_8</eq></td><td><eq>\theta_9</eq></td><td><eq>\theta_{10}</eq></td></tr><tr><td colspan="11">Turnover-Beta-Sorted Turnover Portfolios (<eq>\tau^{\text{VW}}</eq>)</td><td colspan="10">Return-Beta-Sorted Return Portfolios (<eq>R^{\text{VW}}</eq>)</td></tr><tr><td>85.1(7.5)</td><td>8.5(0.7)</td><td>3.6(0.3)</td><td>1.4(0.1)</td><td>0.8(0.1)</td><td>0.3(0.0)</td><td>0.2(0.0)</td><td>0.1(0.0)</td><td>0.0(0.0)</td><td>0.0(0.0)</td><td>1967 to 1971</td><td>85.7(7.5)</td><td>5.9(0.5)</td><td>2.0(0.2)</td><td>1.4(0.1)</td><td>1.4(0.1)</td><td>1.1(0.1)</td><td>0.8(0.1)</td><td>0.7(0.1)</td><td>0.5(0.0)</td><td>0.4(0.0)</td></tr><tr><td>82.8(7.3)</td><td>7.3(0.6)</td><td>4.9(0.4)</td><td>2.0(0.2)</td><td>1.4(0.1)</td><td>0.8(0.1)</td><td>0.5(0.0)</td><td>0.2(0.0)</td><td>0.1(0.0)</td><td>0.1(0.0)</td><td>1972 to 1976</td><td>90.0(7.9)</td><td>3.8(0.3)</td><td>1.8(0.2)</td><td>1.0(0.1)</td><td>0.9(0.1)</td><td>0.7(0.1)</td><td>0.6(0.1)</td><td>0.6(0.0)</td><td>0.4(0.0)</td><td>0.3(0.0)</td></tr><tr><td>83.6(7.3)</td><td>8.6(0.8)</td><td>2.3(0.2)</td><td>2.0(0.2)</td><td>1.2(0.1)</td><td>0.8(0.1)</td><td>0.6(0.1)</td><td>0.4(0.0)</td><td>0.4(0.0)</td><td>0.1(0.0)</td><td>1977 to 1981</td><td>85.4(7.5)</td><td>4.8(0.4)</td><td>4.3(0.4)</td><td>1.4(0.1)</td><td>1.3(0.1)</td><td>0.9(0.1)</td><td>0.6(0.1)</td><td>0.5(0.0)</td><td>0.4(0.0)</td><td>0.3(0.0)</td></tr><tr><td>78.9(6.9)</td><td>7.9(0.7)</td><td>3.6(0.3)</td><td>2.9(0.3)</td><td>2.4(0.2)</td><td>1.4(0.1)</td><td>1.3(0.1)</td><td>0.8(0.1)</td><td>0.5(0.0)</td><td>0.4(0.0)</td><td>1982 to 1986</td><td>86.6(7.6)</td><td>6.1(0.5)</td><td>2.4(0.2)</td><td>1.6(0.1)</td><td>1.0(0.1)</td><td>0.6(0.1)</td><td>0.5(0.0)</td><td>0.5(0.0)</td><td>0.4(0.0)</td><td>0.3(0.0)</td></tr><tr><td>80.1(7.0)</td><td>6.2(0.5)</td><td>5.2(0.5)</td><td>2.4(0.2)</td><td>1.6(0.1)</td><td>1.3(0.1)</td><td>1.0(0.1)</td><td>1.0(0.1)</td><td>0.8(0.1)</td><td>0.5(0.0)</td><td>1987 to 1991</td><td>91.6(8.0)</td><td>2.9(0.3)</td><td>1.7(0.1)</td><td>1.1(0.1)</td><td>0.7(0.1)</td><td>0.6(0.1)</td><td>0.6(0.0)</td><td>0.4(0.0)</td><td>0.3(0.0)</td><td>0.2(0.0)</td></tr><tr><td>71.7(6.3)</td><td>15.6(1.4)</td><td>4.5(0.4)</td><td>2.9(0.3)</td><td>1.8(0.2)</td><td>1.2(0.1)</td><td>0.9(0.1)</td><td>0.8(0.1)</td><td>0.5(0.0)</td><td>0.3(0.0)</td><td>1992 to 1996</td><td>72.4(6.3)</td><td>11.6(1.0)</td><td>4.4(0.4)</td><td>3.5(0.3)</td><td>2.2(0.2)</td><td>1.8(0.2)</td><td>1.5(0.1)</td><td>1.1(0.1)</td><td>0.8(0.1)</td><td>0.6(0.1)</td></tr><tr><td colspan="11">Turnover-Beta-Sorted Turnover Portfolios (<eq>\tau^{\text{EW}}</eq>)</td><td colspan="10">Return-Beta-Sorted Return Portfolios (<eq>R^{\text{EW}}</eq>)</td></tr><tr><td>86.8(7.6)</td><td>7.5(0.7)</td><td>3.0(0.3)</td><td>1.3(0.1)</td><td>0.6(0.0)</td><td>0.5(0.0)</td><td>0.2(0.0)</td><td>0.1(0.0)</td><td>0.1(0.0)</td><td>0.0(0.0)</td><td>1967 to 1971</td><td>87.8(7.7)</td><td>4.3(0.4)</td><td>2.2(0.2)</td><td>1.5(0.1)</td><td>1.0(0.1)</td><td>0.9(0.1)</td><td>0.8(0.1)</td><td>0.5(0.0)</td><td>0.5(0.0)</td><td>0.5(0.0)</td></tr><tr><td>82.8(7.3)</td><td>6.0(0.5)</td><td>5.4(0.5)</td><td>2.9(0.3)</td><td>1.2(0.1)</td><td>1.0(0.1)</td><td>0.4(0.0)</td><td>0.2(0.0)</td><td>0.1(0.0)</td><td>0.0(0.0)</td><td>1972 to 1976</td><td>91.6(8.0)</td><td>4.1(0.4)</td><td>0.9(0.1)</td><td>0.8(0.1)</td><td>0.6(0.0)</td><td>0.5(0.0)</td><td>0.4(0.0)</td><td>0.4(0.0)</td><td>0.3(0.0)</td><td>0.3(0.0)</td></tr><tr><td>79.1(6.9)</td><td>8.5(0.7)</td><td>5.4(0.5)</td><td>2.8(0.2)</td><td>1.4(0.1)</td><td>1.0(0.1)</td><td>0.7(0.1)</td><td>0.6(0.0)</td><td>0.3(0.0)</td><td>0.1(0.0)</td><td>1977 to 1981</td><td>91.5(8.0)</td><td>3.9(0.3)</td><td>1.4(0.1)</td><td>0.8(0.1)</td><td>0.6(0.1)</td><td>0.5(0.0)</td><td>0.4(0.0)</td><td>0.3(0.0)</td><td>0.3(0.0)</td><td>0.3(0.0)</td></tr><tr><td>78.0(6.8)</td><td>10.4(0.9)</td><td>3.1(0.3)</td><td>2.3(0.2)</td><td>2.0(0.2)</td><td>1.3(0.1)</td><td>1.3(0.1)</td><td>0.8(0.1)</td><td>0.6(0.1)</td><td>0.4(0.0)</td><td>1982 to 1986</td><td>88.9(7.8)</td><td>4.4(0.4)</td><td>2.3(0.2)</td><td>1.3(0.1)</td><td>0.7(0.1)</td><td>0.7(0.1)</td><td>0.6(0.0)</td><td>0.5(0.0)</td><td>0.4(0.0)</td><td>0.4(0.0)</td></tr><tr><td>82.5(7.2)</td><td>4.8(0.4)</td><td>3.2(0.3)</td><td>2.4(0.2)</td><td>2.0(0.2)</td><td>1.4(0.1)</td><td>1.3(0.1)</td><td>0.9(0.1)</td><td>0.9(0.1)</td><td>0.6(0.1)</td><td>1987 to 1991</td><td>92.7(8.1)</td><td>3.0(0.3)</td><td>1.2(0.1)</td><td>0.7(0.1)</td><td>0.7(0.1)</td><td>0.4(0.0)</td><td>0.4(0.0)</td><td>0.4(0.0)</td><td>0.3(0.0)</td><td>0.2(0.0)</td></tr><tr><td>79.0(6.9)</td><td>8.5(0.7)</td><td>4.9(0.4)</td><td>2.6(0.2)</td><td>1.5(0.1)</td><td>1.1(0.1)</td><td>0.9(0.1)</td><td>0.6(0.1)</td><td>0.5(0.0)</td><td>0.4(0.0)</td><td>1992 to 1996</td><td>76.8(6.7)</td><td>10.4(0.9)</td><td>3.9(0.3)</td><td>2.7(0.2)</td><td>1.9(0.2)</td><td>1.1(0.1)</td><td>1.0(0.1)</td><td>0.9(0.1)</td><td>0.7(0.1)</td><td>0.6(0.1)</td></tr></table>


T<sub>a</sub>bl<sub>e</sub> 1 3 <sub>:</sub> Ei<sub>genva</sub>l<sub>ues</sub> $\hat { \theta } _ { i } , i = 1 , \ldots , 1 0$ <sub>o</sub>f th<sub>e covar</sub>i<sub>ance ma</sub>t<sub>r</sub>i<sub>x o</sub>f t<sub>en ou</sub>t-<sub>o</sub>f-<sub>samp</sub>l<sub>e</sub>-b<sub>e</sub>t <sub>a</sub>-<sub>sor</sub>t<sub>e</sub>d <sub>por</sub>tf<sub>o</sub>li<sub>os o</sub>f <sub>wee</sub>kl<sub>y</sub> t<sub>urnover</sub> and returns of NYSE and AMEX ordinary common shares ( CRSP share codes 1 0 and 1 1 excluding 37 stocks containing Z-errors in reported volume) —in percent ages (where the eigenvalues are normalized to sum to 1 00 % ) —for subperio ds of th<sub>e</sub> <sub>samp</sub>l<sub>e</sub> <sub>per</sub>i<sub>o</sub> d f<sub>rom</sub> J<sub>u</sub>l<sub>y</sub> 1 962 t<sub>o</sub> D<sub>ecem</sub>b<sub>er</sub> 1 996 <sub>.</sub> T<sub>urnover</sub> <sub>por</sub>tf<sub>o</sub>li<sub>os</sub> <sub>are</sub> <sub>sor</sub>t<sub>e</sub>d b<sub>y</sub> <sub>ou</sub>t-<sub>o</sub>f-<sub>samp</sub>l<sub>e</sub> t<sub>urnover</sub> b<sub>e</sub>t <sub>as</sub> <sub>an</sub>d <sub>re</sub>t<sub>urn por</sub>tf<sub>o</sub>li<sub>os are sor</sub>t<sub>e</sub>d b<sub>y ou</sub>t-<sub>o</sub>f-<sub>samp</sub>l<sub>e re</sub>t<sub>urn</sub> b<sub>e</sub>t <sub>as w</sub>h<sub>ere</sub> th<sub>e sym</sub>b<sub>o</sub>l<sub>s</sub> $\mathit { \Omega } ^ { \left. \left. \mathcal { I } _ { \mathcal { T } } \right. \right. }$ <sub>an</sub>d $^ { 6 \mathrm { V W } }$ i<sub>n</sub>di<sub>ca</sub>t<sub>e</sub> th<sub>a</sub>t th<sub>e</sub> b<sub>e</sub>t <sub>as</sub> <sub>are compu</sub>t<sub>e</sub>d <sub>re</sub>l<sub>a</sub>ti<sub>ve</sub> t<sub>o va</sub>l<sub>ue</sub>-<sub>we</sub>i<sub>g</sub>ht<sub>e</sub>d i<sub>n</sub>d<sub>exes an</sub>d <sup>“</sup><sub>τ</sub><sup>EW”</sup> <sub>an</sub>d ${ } ^ { \mathfrak { s } } R ^ { \mathrm { E W } } { } ^ { \mathfrak { s } }$ i<sub>n</sub>di<sub>ca</sub>t<sub>e</sub> th<sub>a</sub>t th<sub>ey are are compu</sub>t<sub>e</sub>d <sub>re</sub>l<sub>a</sub>ti<sub>ve</sub> t<sub>o</sub> <sub>equa</sub>l-<sub>we</sub>i<sub>g</sub>ht<sub>e</sub>d i<sub>n</sub>d<sub>exes</sub> St <sub>an</sub>d<sub>ar</sub>d <sub>errors</sub> f<sub>or</sub> th<sub>e norma</sub>li<sub>ze</sub>d <sub>e</sub>i<sub>genva</sub>l<sub>ues are g</sub>i<sub>ven</sub> i<sub>n paren</sub>th<sub>eses an</sub>d <sub>are ca</sub>l<sub>cu</sub>l<sub>a</sub>t<sub>e</sub>d <sub>un</sub>d<sub>er</sub> th<sub>e</sub> <sub>assump</sub>ti<sub>on o</sub>f IID <sub>norma</sub>lit<sub>y</sub>


Table 13 contains the principal components decomposition for portfolios sorted on outof-sample betas, where the betas are estimated in two ways: relative to value-weighted indexes (τ<sup>V</sup> <sup>W</sup> and R<sup>V</sup> <sup>W</sup> ) and equal-weighted indexes (τ<sup>EW</sup> and R<sup>EW</sup> ).<sup>30</sup> The first principal component typically explains between 70% to 85% of the variation in turnover, and the first two principal components explain almost all of the variation. For example, the upper-left subpanel of Table 13 shows that in the second five-year subperiod (1967–1971), 85.1% of the variation in the turnover of turnover-beta-sorted portfolios (using turnover betas relative to the value-weighted turnover index) is captured by the first principal component, and 93.6% is captured by the first two principal components. Although using betas computed with valueweighted instead of equal-weighted indexes generally yields smaller eigenvalues for the first principal component (and therefore larger values for the remaining principal components) for both turnover and returns, the diferences are typically not large. 

The importance of the second principal component grows steadily through time for the value-weighted case, reaching a peak of 15.6% in the last subperiod, and the first two principal components account for 87.3% of the variation in turnover in the last subperiod. This is roughly comparable with the return portfolios sorted on value-weighted return-betas—the first principal component is by far the most important, and the importance of the second principal component is most pronounced in the last subperiod. However, the lower left subpanel of Table 13 shows that for turnover portfolios sorted by betas computed against equal-weighted indexes, the second principal component explains approximately the same variation in turnover, varying between 6.0% and 10.4% across the six subperiods. 

Of course, one possible explanation for the dominance of the first principal component is the existence of a time trend in turnover. Despite the fact that we have limited our analysis to five-year subperiods, within each subperiod there is a certain drift in turnover; might this account for the first principal component? To investigate this conjecture, we perform eigenvalue decompositions for the covariance matrices of the first diferences of turnover for the 10 turnover portfolios. 

These results are reported in Table 14 and are consistent with those in Table 13: the first principal component is still the most important, explaining between 60% to 88% of the variation in the first diferences of turnover. The second principal component is typically responsible for another 5% to 20%. And in one case—in-sample sorting on betas relative to the equal-weighted index during 1987–1991—the third principal component accounts for an additional 10%. These figures suggest that the trend in turnover is unlikely to be the source of the dominant first principal component. 

In summary, the results of Tables 13 and 14 indicate that a one-factor model for turnover is a reasonable approximation, at least in the case of turnover-beta-sorted portfolios, and that a two-factor model captures well over 90% of the time-series variation in turnover. This lends some support to the practice of estimating “abnormal” volume by using an eventstudy style “market model”, e.g., Bamber (1986), Jain and Joh (1988), Lakonishok and Smidt (1986), Morse (1980), Richardson, Sefcik, Thompson (1986), Stickel and Verrecchia (1994), and Tkac (1999). 

As compelling as these empirical results are, several qualifications should be kept in mind. First, we have provided little statistical inference for our principal components decomposition. In particular, the asymptotic standard errors reported in Tables 13 and 14 were computed under the assumption of IID Gaussian data, hardly appropriate for weekly US stock returns and even less convincing for turnover (see Muirhead (1982, Chapter 9) for further details). Perhaps nonparametric methods such as the moving-block bootstrap can provide better indications of the statistical significance of our estimated eigenvalues. Monte Carlo simulations should also be conducted to check the finite-sample properties of our estimators. 

More importantly, the economic interpretation of the first two principal components or, alternatively, identifying the specific factors is a challenging issue that principal components cannot resolve. More structure must be imposed on the data—in particular, an intertemporal model of trading—to obtain a better understanding for the sources of turnover variation, and we present such structure in the next section. 

## 6 Volume Implications of Intertemporal Asset-Pricing Models

In this section, we analyze the volume implications of intertemporal asset pricing models and how volume is related to returns. We first develop an intertemporal equilibrium model of stock trading and pricing with multiple assets and heterogeneous investors. We derive the behavior of volume and returns. We show that both volume and returns are driven by the underlying risks of the economy. The results presented here are from Lo and Wang (2006). 

<table><tr><td>Period</td><td><eq>\hat{\theta}_{1}</eq></td><td><eq>\hat{\theta}_{2}</eq></td><td><eq>\hat{\theta}_{3}</eq></td><td><eq>\hat{\theta}_{4}</eq></td><td><eq>\hat{\theta}_{5}</eq></td><td><eq>\hat{\theta}_{6}</eq></td><td><eq>\hat{\theta}_{7}</eq></td><td><eq>\hat{\theta}_{8}</eq></td><td><eq>\hat{\theta}_{9}</eq></td><td><eq>\hat{\theta}_{10}</eq></td></tr><tr><td colspan="11">Out-of-Sample Turnover-Beta-Sorted Turnover-Differences Portfolios (<eq>\tau^{VW}</eq>)</td></tr><tr><td>1967 to 1971</td><td>82.6(7.2)</td><td>7.1(0.6)</td><td>5.1(0.5)</td><td>2.0(0.2)</td><td>1.6(0.1)</td><td>0.8(0.1)</td><td>0.5(0.0)</td><td>0.1(0.0)</td><td>0.1(0.0)</td><td>0.1(0.0)</td></tr><tr><td>1972 to 1976</td><td>81.2(7.1)</td><td>6.8(0.6)</td><td>4.7(0.4)</td><td>2.8(0.2)</td><td>2.0(0.2)</td><td>1.0(0.1)</td><td>0.9(0.1)</td><td>0.4(0.0)</td><td>0.2(0.0)</td><td>0.1(0.0)</td></tr><tr><td>1977 to 1981</td><td>85.2(7.5)</td><td>4.5(0.4)</td><td>2.9(0.3)</td><td>2.6(0.2)</td><td>1.6(0.1)</td><td>1.2(0.1)</td><td>0.8(0.1)</td><td>0.5(0.0)</td><td>0.5(0.0)</td><td>0.2(0.0)</td></tr><tr><td>1982 to 1986</td><td>81.3(7.1)</td><td>5.1(0.4)</td><td>3.5(0.3)</td><td>2.7(0.2)</td><td>2.2(0.2)</td><td>1.7(0.2)</td><td>1.3(0.1)</td><td>0.9(0.1)</td><td>0.7(0.1)</td><td>0.6(0.1)</td></tr><tr><td>1987 to 1991</td><td>73.1(6.4)</td><td>10.9(1.0)</td><td>4.1(0.4)</td><td>3.0(0.3)</td><td>2.2(0.2)</td><td>1.7(0.2)</td><td>1.6(0.1)</td><td>1.4(0.1)</td><td>1.1(0.1)</td><td>0.9(0.1)</td></tr><tr><td>1992 to 1996</td><td>78.4(6.9)</td><td>8.6(0.8)</td><td>4.0(0.4)</td><td>2.8(0.2)</td><td>2.1(0.2)</td><td>1.2(0.1)</td><td>1.0(0.1)</td><td>0.9(0.1)</td><td>0.6(0.0)</td><td>0.4(0.0)</td></tr><tr><td colspan="11">Out-of-Sample Turnover-Beta-Sorted Turnover-Differences Portfolios (<eq>\tau^{EW}</eq>)</td></tr><tr><td>1967 to 1971</td><td>82.2(7.2)</td><td>8.0(0.7)</td><td>4.5(0.4)</td><td>2.3(0.2)</td><td>1.4(0.1)</td><td>0.7(0.1)</td><td>0.4(0.0)</td><td>0.3(0.0)</td><td>0.1(0.0)</td><td>0.0(0.0)</td></tr><tr><td>1972 to 1976</td><td>79.3(7.0)</td><td>7.5(0.7)</td><td>4.8(0.4)</td><td>4.0(0.4)</td><td>1.9(0.2)</td><td>1.3(0.1)</td><td>0.6(0.1)</td><td>0.4(0.0)</td><td>0.2(0.0)</td><td>0.1(0.0)</td></tr><tr><td>1977 to 1981</td><td>80.3(7.0)</td><td>5.3(0.5)</td><td>4.8(0.4)</td><td>3.8(0.3)</td><td>2.0(0.2)</td><td>1.4(0.1)</td><td>1.2(0.1)</td><td>0.7(0.1)</td><td>0.5(0.0)</td><td>0.2(0.0)</td></tr><tr><td>1982 to 1986</td><td>82.6(7.3)</td><td>5.0(0.4)</td><td>3.0(0.3)</td><td>2.6(0.2)</td><td>2.0(0.2)</td><td>1.7(0.1)</td><td>1.1(0.1)</td><td>0.9(0.1)</td><td>0.7(0.1)</td><td>0.4(0.0)</td></tr><tr><td>1987 to 1991</td><td>77.2(6.8)</td><td>5.5(0.5)</td><td>4.3(0.4)</td><td>2.7(0.2)</td><td>2.5(0.2)</td><td>2.3(0.2)</td><td>1.8(0.2)</td><td>1.6(0.1)</td><td>1.2(0.1)</td><td>1.0(0.1)</td></tr><tr><td>1992 to 1996</td><td>80.4(7.1)</td><td>6.4(0.6)</td><td>4.6(0.4)</td><td>2.6(0.2)</td><td>1.7(0.1)</td><td>1.4(0.1)</td><td>1.1(0.1)</td><td>0.7(0.1)</td><td>0.5(0.0)</td><td>0.4(0.0)</td></tr></table>


Table 14: Eigenvalues $\hat { \theta } _ { i } , i = 1 , \ldots$ , 10 of the covariance matrix of the first-diferences of the weekly turnover of ten out-of-sample-beta-sorted portfolios of NYSE and AMEX ordinary common shares (CRSP share codes 10 and 11, excluding 37 stocks containing Z-errors in reported volume)—in percentages (where the eigenvalues are normalized to sum to 100%)— for subperiods of the sample period from July 1962 to December 1996. Turnover betas are calculated in two ways: with respect to a value-weighted turnover index $( \tau ^ { \mathrm { V W } } )$ and an equalweighted turnover index $( \tau ^ { \mathrm { E W } } )$ . Standard errors for the normalized eigenvalues are given in parentheses and are calculated under the assumption of IID normality.


## 6.1 An Intertemporal Capital Asset-Pricing Model

Since our purpose is to draw qualitative implications on the joint behavior of return and volume, the model is kept as parsimonious as possible. Several generalizations of the model are discussed in Lo and Wang (2006). 

## The Economy

We consider an economy defined on a set of discrete dates: $t = 0 , 1 , 2 , \ldots$ There are J risky stocks, each pays a stream of dividends over time. As before, $D _ { j t }$ denote the dividend of stock $j$ at date t, $j = 1 , \cdots , J$ , and $D _ { t } \equiv [ D _ { 1 t } \cdot \cdot \cdot D _ { J t } ]$ denote the column vector of dividends. Without loss of generality, in this section we assume that the total number of shares outstanding is one for each stock. 

A stock portfolio can be expressed in terms of its shares of each stock, denoted by $S \equiv [ S _ { 1 } \ldots S _ { J } ]$ , where $S _ { j }$ is the number of stock $j$ shares in the portfolio $( j = 1 , \ldots , J )$ . A portfolio of particular importance is the market portfolio, denoted by $S ^ { M }$ , which is given by 

$$
S ^ {M} = \iota\tag{20}
$$

where ι is a vector of 1’s with rank J. $D _ { M t } \equiv \iota ^ { \top } D _ { t }$ gives the dividend of the market portfolio, which is the aggregate dividend. 

In addition to the stocks, there is also a risk-free bond that yields a constant, positive interest r per time period. 

There are I investors in the economy. Each investor is endowed with equal shares of the stocks and no bond. Every period, investor $i , i = 1 , \dots , I$ , maximizes his expected utility of the following form: 

$$
\mathrm{E} _ {\mathfrak {t}} \left[ - e ^ {- W _ {t + 1} ^ {i} - (\lambda_ {X} X _ {t} + \lambda_ {Y} Y _ {t} ^ {i}) D _ {M t + 1} - \lambda_ {Z} (1 + Z _ {t} ^ {i}) X _ {t + 1}} \right]\tag{21}
$$

where $W _ { t + 1 } ^ { i }$ is investor i’s wealth next period, $X _ { t } , ~ Y _ { t } ^ { i } , ~ Z _ { t } ^ { i }$ are three one-dimensional state variables, and $\lambda _ { X } , \lambda _ { Y } , \lambda _ { Z }$ are non-negative constants. Apparently, the utility function in 

(21) is state-dependent. We further assume 

$$
\sum_ {i = 1} ^ {I} Y _ {t} ^ {i} = \sum_ {i = 1} ^ {I} Z _ {t} ^ {i} = 0\tag{22}
$$

where $t = 0 , 1 , \ldots$ 

For simplicity, we assume that all the exogenous shocks, $D _ { t } , X _ { t } , \{ Y _ { t } ^ { i } , Z _ { t } ^ { i } , i = 1 , . . . , I \}$ 2 are IID over time with zero means. For tractability, we further assume that $D _ { t + 1 }$ and $X _ { t + 1 }$ are jointly normally distributed: 

$$
u _ {t + 1} \equiv \binom{D _ {t + 1}}{X _ {t + 1}} \quad \stackrel {{d}} {{\sim}} \quad N (\cdot , \sigma) \quad \text {where} \quad \sigma = \left( \begin{array}{c c} \sigma_ {D D} & \sigma_ {D X} \\ \sigma_ {X D} & \sigma_ {X X} \end{array} \right).\tag{23}
$$

Without loss of generality, $\sigma _ { D D }$ is assumed to be positive definite. 

Our model has several features that might seem unusual. One feature of the model is that investors are assumed to have a myopic, but state-dependent utility function in (21). The purpose for using this utility function is to capture the dynamic nature of the investment problem without explicitly solving a dynamic optimization problem. The state dependence of the utility function is assumed to have the following properties. The marginal utility of wealth depends on the dividend of the market portfolio (the aggregate dividend), as reflected in the second term in the exponential of the utility function. When the aggregate dividend goes up, the marginal utility of wealth goes down. The marginal utility of wealth also depends on future state variables, in particular $X _ { t + 1 }$ , as reflected in the third term in the exponential of the utility function. This utility function can be interpreted as the equivalent of a value function from an appropriately specified dynamic optimization problem (see, for example, Wang (1994) and Lo and Wang (2003)). More discussion is given in Lo and Wang (2006) on this point. 

Another feature of the model is the IID assumption for the state variables. This might leave the impression that the model is efectively static. This impression, however, is false since the state-dependence of investors’ utility function introduces important dynamics over time. We can allow richer dynamics for the state variables without changing the main properties of the model. 

The particular form of the utility function and the normality of distribution for the state variables are assumed for tractability. These assumptions are restrictive. But we hope with some confidence that the qualitative predictions of the model that we explore in this chapter are not sensitive to these assumptions. 

In the model, we also assumed an exogenous interest rate for the bond without requiring the bond market to clear. This is a modeling choice we have made in order to simplify our analysis and to focus on the stock market. As will become clear later, changes in the interest rate is not important for the issues we examine in this chapter. 

## Equilibrium

Let $P _ { t } \equiv \left[ P _ { 1 t } \ldots P _ { J t } \right]$ and $S _ { t } ^ { i } \equiv [ S _ { 1 t } ^ { i } ; \ldots ; S _ { J t } ^ { i } ]$ be the (column) vectors of (ex-dividend) stock prices and investor i’s stock holdings respectively. We now derive the equilibrium of the economy. 

Definition 4 An equilibrium is given by a price process $\{ P _ { t } : t = 0 , 1 , . . . \}$ and the investors stock positions $\{ S _ { t } ^ { i } : i = 1 , \ldots , I ; t = 0 , 1 , \ldots \}$ such that: 

1. $S _ { t } ^ { i }$ solves investor i’s optimization problem: 

$$
S _ {t} ^ {i} = \arg \max \mathrm{E} \left[ - e ^ {- W _ {t + 1} ^ {i} - (\lambda_ {X} X _ {t} + \lambda_ {Y} Y _ {t} ^ {i}) D _ {M _ {t + 1}} - \lambda_ {Z} (1 + Z _ {t} ^ {i}) X _ {t + 1}} \right]\tag{24}
$$

$$
\mathrm{s.t.} W _ {t + 1} ^ {i} = W _ {t} ^ {i} + S _ {t} ^ {i \prime} \left[ D _ {t + 1} + P _ {t + 1} - (1 + r) P _ {t} \right]
$$

2. stock market clears: 

$$
\sum_ {i = 1} ^ {i} S _ {t} ^ {i} = \iota .\tag{25}
$$

The above definition of equilibrium is standard, except that the bond market does not clear here. As discussed earlier, the interest rate is given exogenously and there is an elastic supply of bonds at that rate. 

For $t = 0 , 1 , . . . ,$ let $Q _ { t + 1 }$ denote the vector of excess dollar returns on the stocks: 

$$
Q _ {t + 1} \equiv D _ {t + 1} + P _ {t + 1} - (1 + r) P _ {t}.\tag{26}
$$

Thus, $Q _ { j t + 1 } = D _ { j t + 1 } + P _ { j t + 1 } - ( 1 + r ) P _ { j t }$ gives the dollar return on one share of stock $j$ in excess of its financing cost for period $t + 1$ . For the remainder of the chapter, we simply refer to $Q _ { j t + 1 }$ as the dollar return of stock $j ,$ omitting the qualifier “excess”. Dollar return $Q _ { j t + 1 }$ difers from the conventional (excess) return measure $R _ { j t + 1 }$ which is the dollar return normalized by the share price: $R _ { j t + 1 } \equiv Q _ { j t + 1 } / P _ { j t }$ . We refer to $R _ { j t + 1 }$ simply as the return on stock $j$ in period t + 1. 

We can now state the solution to the equilibrium in the following theorem: 

Theorem 1 The economy defined above has a unique linear equilibrium in which 

$$
P _ {t} = - a - b X _ {t}\tag{27}
$$

and 

$$
S _ {t} ^ {i} = \left(I ^ {- 1} - \lambda_ {Y} Y _ {t} ^ {i}\right) \iota - \left(\lambda_ {Z} Z _ {t} ^ {i} + \lambda_ {Y} (b ^ {\prime} \iota) Y _ {t} ^ {i}\right) (\sigma_ {Q Q}) ^ {- 1} \sigma_ {Q X}\tag{28}
$$

where 

$$
\sigma_ {Q Q} = \sigma_ {D D} - b \sigma_ {X D} - \sigma_ {D X} b ^ {\prime} + \sigma_ {X} ^ {2} b b ^ {\prime}
$$

$$
\sigma_ {Q X} = \sigma_ {D X} - \sigma_ {X} ^ {2} b
$$

$$
a = \frac {1}{r} (\bar {\alpha} \sigma_ {Q Q} \iota + \lambda_ {Z} \sigma_ {Q X}
$$

$$
{ b } { = } { \lambda _ { X } [ ( 1 + r ) + \lambda _ { Z } \sigma _ { X D } \iota ) ] ^ { - 1 } \sigma _ { D D } \iota }
$$

and $\bar { a } = 1 / I$ 

The nature of the equilibrium is intuitive. In our model, an investor’s utility function depends not only on his wealth, but also on the stock payofs directly. In other words, even he holds no stocks, his utility fluctuates with the payof of the stocks. Such a “market spirit” afects his demand for the stocks, in addition to the usual factors such as the stocks’ expected returns. The market spirit of investor i is measured by $( \lambda _ { X } X _ { t } + \lambda _ { Y } Y _ { t } ^ { i } )$ . When $( \lambda _ { X } X _ { t } + \lambda _ { Z } Y _ { t } ^ { i } )$ is positive, investor i extracts positive utility when the aggregate stock payof is high. Such a positive “attachment” to the market makes holding stocks less attractive to him. When $( \lambda _ { X } X _ { t } + \lambda _ { Y } Y _ { t } ^ { i } )$ is negative, he has a negative attachment to the market, which makes holding stocks more attractive. Such a market spirit at the aggregate level, which is captured by $X _ { t }$ , afects the aggregate stock demand, which in turn afects their equilibrium prices. Given the particular form of the utility function, $X _ { t }$ afects the equilibrium stock prices linearly. The idiosyncratic diferences among investors in their market spirit, which are captured by $Y _ { t } ^ { i }$ , ofset each other at the aggregate level, thus do not afect the equilibrium stock prices. However, they do afect individual investors’ stock holdings. As the first term of (28) shows, investors with positive $Y _ { t } ^ { i } ^ { , }$ s hold less stocks (they are already happy by just “watching” the stocks paying of). 

Since the aggregate utility variable $X _ { t }$ is driving the stock prices, it is also driving the stock returns. In fact, the expected returns on the stocks are changing with $X _ { t }$ (see the discussion in the next section). The form of the utility function further states that the investors utility function directly depends on $X _ { t }$ , which fully characterizes the investment opportunities investors face. Such a dependence endogenously arises when investors optimize dynamically. In our setting, however, we assume that investors optimize myopically but insert such a dependence directly into the utility function. This dependence induces investors to care about future investment opportunities when choose their portfolios. In particular, they prefer those portfolios whose returns can help them to smooth fluctuations in their utility due to changes in investment opportunities. Such a preference gives rise to the hedging component in their asset demand, which is captured by the second term in (28). 

## 6.2 The Behavior of Returns and Volume

Given the intertemporal CAPM defined above, we can derive the its implications on the behavior of return and volume. For the stocks, their dollar return vector can be re-expressed as follows: 

$$
Q _ {t + 1} = r a + (1 + r) b X _ {t} + \tilde {Q} _ {t + 1}\tag{29}
$$

where $\tilde { Q } _ { t + 1 } \equiv D _ { t + 1 } - b Z _ { t + 1 }$ denotes the vector of unexpected dollar returns on the stocks, which are IID over time with zero mean. Equation (29) shows that the expected returns on the stocks change over time. In particular, they are driven by a single state variable $X _ { t }$ 

The investors stock holdings can be expressed in the following form: 

$$
S _ {t} ^ {i} = h _ {M t} ^ {i} \iota + h _ {H t} ^ {i} S ^ {H} \quad \forall i = 1, 2, \ldots , I\tag{30}
$$

where $h _ { M t } ^ { i } \equiv I ^ { - 1 } - \lambda _ { Y } Y _ { t } ^ { i } , h _ { H t } ^ { i } \equiv \lambda _ { Z } ( b ^ { \prime } \iota ) Y _ { t } ^ { i } - \lambda _ { Y } Z _ { t } ^ { i }$ , and 

$$
S ^ {H} \equiv (\sigma_ {Q Q}) ^ {- 1} \sigma_ {Q X}.\tag{31}
$$

Equation (30) simply states that three-fund separation holds for the investors’ stock portfolios. That is, all investors’ portfolios can be viewed as investments in three common funds: the risk-free asset and two stock funds. The two stock funds are the market portfolio ι and the hedging portfolio $S _ { H }$ . Moreover, in our current model, these two portfolios, expressed in terms of stock shares, are constant over time. 

The particular structure of the returns and the investors’ portfolios lead to several interesting predictions about the behavior of volume and returns. We present these predictions through a set of propositions. 

## The Cross Section of Volume

Given that investors only hold and trade in two stock funds, the results obtained in Section 5 apply here. The turnover of stock j is given by 

$$
\tau_ {j t} \equiv \frac {1}{2} \sum_ {i = 1} ^ {I} \left| \left(h _ {M t} ^ {i} - h _ {M t - 1} ^ {i}\right) + \left(h _ {H t} ^ {i} - h _ {H t - 1} ^ {i}\right) S _ {j} ^ {H} \right| \quad \forall j = 1, \dots , J.\tag{32}
$$

Let $\tau _ { t }$ denote the vector of turnover for all stocks. We have the following proposition on the cross-section of volume, which follows from Proposition 2: 

Proposition 3 When investors’ trading in the hedging portfolio is small relative to their trading in the market portfolio, the two-fund separation in their stock holdings leads to an approximate two-factor structure for stock turnover: 

$$
\tau_ {t} \approx \iota F _ {M t} + S ^ {H} F _ {H t}\tag{33}
$$

where 

$$
F _ {M t} = \frac {1}{2} \sum_ {i = 1} ^ {I} | h _ {M t} ^ {i} - h _ {M t - 1} ^ {i} | \quad a n d \quad F _ {H t} = \frac {1}{2} \sum_ {i = 1} ^ {I} \mathrm{sgn} (h _ {M t} ^ {i} - h _ {M t - 1} ^ {i}) (h _ {H t} ^ {i} - h _ {H t - 1} ^ {i}).
$$

In the special case when two-fund separation holds (when $X _ { t } =  { \mathrm { ~ 0 ~ } } \forall t )$ , turnover would have an exact one-factor structure, $\tau _ { t } = \iota F _ { M t }$ 

In the general case when three-fund separation holds, turnover has an approximate twofactor structure as given in (33). It is important to note that the loading of stock $j ^ { \prime } \mathrm { s }$ turnover on the second factor is proportional to its share weight in the hedging portfolio. Thus, empirically if we can identify the two common factors, $F _ { M t }$ and $F _ { H t }$ , the stocks loadings on the second factor allow us to identify the hedging portfolio. In our empirical analysis, we explore this information that the cross-section of volume conveys. As we discuss below, the hedging portfolio has important properties that allow us to better understand the behavior of returns. Merton (1971) has discussed the properties of hedging portfolios in a continuous-time framework as a characterization of equilibrium. Our discussion here follows Merton in spirit, but is in a discrete-time, equilibrium environment. 

## Time Series Implications for the Hedging Portfolio

By the definition of the hedging portfolio in (31), it is easy to show that its current return gives the best forecast of future market return. 

Let $Q _ { M t + 1 }$ denote the dollar return on the market portfolio in period $t + 1$ and $Q _ { H t + 1 }$ 1 denote the dollar return on the hedging portfolio. Then, 

$$
Q _ {M t + 1} = \iota^ {\top} Q _ {t + 1} \quad \text { and } \quad Q _ {H t + 1} = S ^ {H \top} Q _ {t + 1}.\tag{34}
$$

For an arbitrary portfolio $S _ { i }$ , its dollar return in period t, which is $Q _ { t } \equiv S ^ { \prime } Q _ { t }$ , can serve as a predictor for the dollar of the market next period: 

$$
Q _ {M t + 1} = \gamma_ {0} + \gamma_ {1} Q _ {t} + \varepsilon_ {M t + 1}.
$$

The predictive power of $S$ is measured by the $R ^ { 2 }$ of the above regression. We can solve for the portfolio that maximizes the $R ^ { 2 }$ . The solution, up to a scaling constant, is the hedging portfolio. Thus, we have the following result: 

Proposition 4 Among the returns of all portfolios, the dollar return of the hedging portfolio, $S _ { H }$ , provides the best forecast for the future dollar return of the market. 

In other words, if we regress the market dollar return on the lagged dollar return of any portfolios, the hedging portfolio gives the highest $R ^ { 2 }$ 

## Cross-Sectional Implications for the Hedging Portfolio

We now turn to examine the predictions of our model on the cross-section of returns. For expositional simplicity, we introduce some additional notation. Let $Q _ { p t + 1 }$ be the dollar return of a stock or a portfolio (of stocks). $\tilde { Q } _ { p t + 1 } \equiv Q _ { p t + 1 } - \operatorname { E } _ { \mathrm { t } } [ Q _ { p t + 1 } ]$ then denotes its unexpected dollar return and $\bar { Q } _ { p }$ its unconditional mean. Thus, $\tilde { Q } _ { M t + 1 }$ and $\tilde { Q } _ { H t + 1 }$ denote, respectively, the unexpected dollar returns on the market portfolio and the hedging portfolio, and 

$$
\sigma_ {M} ^ {2} \equiv \mathrm{Var} \left[ \tilde {Q} _ {M t + 1} \right], \quad \sigma_ {H} ^ {2} \equiv \mathrm{Var} \left[ \tilde {Q} _ {H t + 1} \right], \quad \sigma_ {M H} \equiv \mathrm{Cov} \left[ \tilde {Q} _ {M t + 1}, \tilde {Q} _ {H t + 1} \right]
$$

denote their conditional variances and covariance. It is easy to show that 

$$
\sigma_ {M} ^ {2} = \iota^ {\prime} \sigma_ {Q Q} \iota , \quad \sigma_ {H} ^ {2} = \sigma_ {X Q} \sigma_ {Q Q} ^ {- 1} \sigma_ {Q X}, \quad \sigma_ {M H} = \iota^ {\prime} \sigma_ {Q X}
$$

where $\sigma _ { Q Q }$ and $\sigma _ { Q Z }$ are given in Theorem 1. From Theorem 1, we have 

$$
\bar {Q} = \bar {\alpha} \sigma_ {Q Q} \iota + \lambda_ {Y} \sigma_ {Q X}\tag{35a}
$$

$$
\bar {Q} _ {M} = \bar {\alpha} \sigma_ {M} ^ {2} + \lambda_ {Y} \sigma_ {M H}\tag{35b}
$$

$$
\bar {Q} _ {H} = \bar {\alpha} \sigma_ {M H} + \lambda_ {Y} \sigma_ {H} ^ {2}.\tag{35c}
$$

Equation (35) characterizes the cross-sectional variation in the stocks’ expected dollar returns. 

In order to develop more intuition about (35), we first consider the special case when $X _ { t } =  { \mathrm { ~ 0 ~ } } \forall t$ . In this case, returns are IID over time. The risk of a stock is measured by its co-variability with the market portfolio. We have the following result: 

Proposition 5 When $X _ { t } =  { \mathrm { ~ 0 ~ } } \ \forall \ t$ , we have 

$$
\operatorname{E} \left[ \tilde {Q} _ {t + 1} | \tilde {Q} _ {M t + 1} \right] = \beta_ {M} \tilde {Q} _ {M t + 1}\tag{36}
$$

where 

$$
\beta_ {M} \equiv \mathrm{Cov} [ \tilde {Q} _ {t + 1}, \tilde {Q} _ {M t + 1} ] / \mathrm{Var} [ \tilde {Q} _ {M t + 1} ] = \sigma_ {D D} \iota / (\iota^ {\prime} \sigma_ {D D} \iota)
$$

is the vector of the stocks’ market betas. Moreover, 

$$
\bar {Q} = \beta_ {M} \bar {Q} _ {M}\tag{37}
$$

where $\bar { Q } _ { M } = \bar { \lambda } \sigma _ { M } ^ { 2 }$ 

Obviously in this case, the CAPM holds for the dollar returns. It can be shown that it also holds for the returns. 

In the general case when $X _ { t }$ changes over time, there is an additional risk due to changing market conditions (dynamic risk). Moreover, this risk is represented by the dollar return of the hedging portfolio $Q _ { H t }$ . In this case, the risk of a stock is measured by its risk with respect to the market portfolio and its risk with respect to the hedging portfolio. In other words, there are two risk factors, the (contemporaneous) market risk and the (dynamic) risk of changing market conditions. The expected returns of the stocks are then determined by their exposures to these two risks and the associated risk premia. The result is summarized in the following proposition: 

Proposition 6 When $Z _ { t }$ changes over time, we have 

$$
\operatorname{E} \left[ \tilde {Q} _ {t + 1} | \tilde {Q} _ {M t + 1}, \tilde {Q} _ {H t + 1} \right] = \beta_ {M} \tilde {Q} _ {M t + 1} + \beta_ {H} \tilde {Q} _ {H t + 1}\tag{38}
$$

where 

$$
\begin{array}{r c l} (\beta_ {M}, \beta_ {H}) & = & \mathrm{Cov} \left[ \tilde {Q} _ {t + 1}, \left(\tilde {Q} _ {M t + 1}, \tilde {Q} _ {H t + 1}\right) \right] \left\{\mathrm{Var} \left[ \left(\tilde {Q} _ {M t + 1}, \tilde {Q} _ {H t + 1}\right) \right] \right\} ^ {- 1} \\ & = & (\sigma_ {Q M}, \sigma_ {Q H}) \left( \begin{array}{c c} \sigma_ {M} ^ {2} & \sigma_ {M H} \\ \sigma_ {M H} & \sigma_ {H} ^ {2} \end{array} \right) ^ {- 1} \end{array}
$$

is the vector of the stocks’ market betas and hedging betas. Moreover, The stocks’ expected dollar returns satisfy 

$$
\bar {Q} = \beta_ {M} \bar {Q} _ {M} + \beta_ {H} \bar {Q} _ {H}\tag{39}
$$

where $\bar { Q } _ { M } = \bar { \alpha } \sigma _ { M } ^ { 2 } + \lambda _ { Y } \sigma _ { M H }$ and $\bar { Q } _ { H } = \bar { \alpha } \sigma _ { M H } + \lambda _ { Y } \sigma _ { H } ^ { 2 }$ 

Thus, a stock’s market risk is measured by its beta with respect to the market portfolio and its risk to a changing environment is measured by its beta with respect to the hedging portfolio. The expected dollar return on the market portfolio gives the premium of the market risk and the expected dollar return on the hedging portfolio gives the premium of the dynamic risk. (39) simply states that the premium on a stock is then given by the sum of the product of its exposure to each risk and the associated premium. 

The pricing relation we obtain in Proposition 6 is in the spirit of Merton’s Intertemporal CAPM in a continuous-time framework (Merton, 1971). However, it is important to note that Merton’s result is a characterization of the pricing relation under a (class of) proposed price processes and no equilibrium is provided to support these price processes. In contrast, our pricing relation is derived from a dynamic equilibrium model. In this sense, we model provides an particular equilibrium model for which Merton’s characterization holds. 

If we can identify the hedging portfolio empirically, its return provides the second risk factor. Diferences in the stocks’ expected returns can then be fully explained by their exposures to the two risks (market risk and dynamic risk), as measured by their market betas and hedging betas. 

## 6.3 Empirical Construction of the Hedging Portfolio

In the rest of this section, we present some empirical evidence on the theoretical predictions. Our first step is to empirically identify the hedging portfolio using the turnover data. From (33), we know that in the two-factor model for turnover in Proposition 3, stock j’s loading on the second factor $F _ { H t }$ yields the number of shares (as a fraction of its total number of shares outstanding) of stock j in the hedging portfolio. In principle, this specifies the hedging portfolio. However, we face two challenges in practice. First, the exact two-factor specification (33) is, at best, an approximation for the true data-generating process of turnover. Second, the two common factors are generally not observable. We address both of these problems in turn. 

A more realistic starting point for modelling turnover is an approximate two-factor model: 

$$
\tau_ {j t} = F _ {M t} + \theta_ {H j} F _ {H t} + \varepsilon_ {j t}, \quad j = 1, \ldots , J\tag{40}
$$

where $F _ { M t }$ and $F _ { H t }$ are the two factors that generate trading in the market portfolio and the hedging portfolio, respectively, $\theta _ { H j }$ is the percentage of shares of stock j in the hedging portfolio (as a percentage of its total number of shares outstanding), and $\varepsilon _ { j t }$ is the error term, which is assumed to be independent across stocks.<sup>31</sup> 

Since we do not have any suficient theoretical foundation to identify the two common factors $F _ { M t }$ and $F _ { H t } ,$ we use two turnover indexes as their proxies: the equally-weighted and share-weighted turnover of the market. Specifically. let $N _ { j }$ denote the total number of shares outstanding for stock $j$ and $N \equiv \Sigma _ { j } N _ { j }$ the total number of shares outstanding of all stocks. The two turnover indexes are 

$$
\tau_ {t} ^ {E W} \equiv \frac {1}{J} \sum_ {j = 1} ^ {J} \tau_ {j t} = F _ {M t} + n ^ {E W} F _ {H t} + \varepsilon_ {t} ^ {E W}\tag{41a}
$$

$$
\tau_ {t} ^ {S W} \equiv \sum_ {j = 1} ^ {J} \frac {N _ {j}}{N} \tau_ {j t} = F _ {M t} + n ^ {S W} F _ {H t} + \varepsilon_ {t} ^ {S W}\tag{41b}
$$

where 

$$
n ^ {E W} = \frac {1}{J} \sum_ {j = 1} ^ {J} \theta_ {H j} \text {and} n ^ {S W} = \sum_ {j = 1} ^ {J} \frac {N _ {j}}{N} \theta_ {H j}
$$

are the average percentage of shares of each stock in the hedging portfolio and the percentage of all shares (of all stocks) in the hedging portfolio, respectively, and $\varepsilon _ { t } ^ { E W }$ and $\varepsilon _ { t } ^ { S W }$ are the error terms for the two indexes.<sup>32</sup> Since the error terms in (40) are assumed to be independent across stocks, the error terms of the two indexes, which are weighted averages of the error terms of individual stocks, become negligible when the number of stocks is large. For the remainder of our analysis, we shall ignore them. 

Simple algebra then yields the following relation between individual turnover and the two indexes (see Lo and Wang (2006) for more details): 

$$
\tau_ {j t} = \beta_ {\tau j} ^ {S W} \tau_ {t} ^ {S W} + \beta_ {\tau j} ^ {E W} \tau_ {t} ^ {E W} + \varepsilon_ {j t}, \qquad j = 1, \ldots , J\tag{42a}
$$

$$
\mathrm{s.t.} \beta_ {\tau j} ^ {E W} + \beta_ {\tau j} ^ {S W} = 1\tag{42b}
$$

$$
\sum_ {j = 1} ^ {J} \beta_ {\tau j} ^ {E W} = J.\tag{42c}
$$

where 

$$
\beta_ {\tau j} ^ {E W} = \frac {n ^ {E W} - \theta_ {H j}}{n ^ {E W} - n ^ {S W}} \mathrm{and} \beta_ {\tau j} ^ {S W} = \frac {\theta_ {H j} - n ^ {S W}}{n ^ {E W} - n ^ {S W}}.
$$

Using the MiniCRSP volume database, we can empirically estimate $\{ \beta _ { \tau j } ^ { E W } \}$ and $\{ \beta _ { \tau j } ^ { S W } \}$ by estimating (42). From the estimates $\{ \widehat { \beta } _ { \tau j } ^ { E W } \}$ , we can construct estimates of the portfolio weights of the hedging portfolio in the following manner 

$$
\widehat {\theta} _ {H j} = (n ^ {E W} - n ^ {S W}) \widehat {\beta} _ {\tau j} ^ {E W} + n ^ {S W}.\tag{43}
$$

However, there are two remaining parameters, $n ^ { E W }$ and $n ^ { S W }$ , that need to be estimated. It should be emphasized that these two remaining degrees of freedom are inherent in the model (40). When the two common factors are not observed, the parameters $\{ \theta _ { H } j \}$ are only identified up to a scaling constant and a rotation. Clearly, (40) is invariant when $F _ { H t }$ is rescaled as long as $\{ \theta _ { H j } \}$ is also rescaled appropriately. In addition, when the two factors are replaced by their linear combinations, (40) remains formally the same as long as $\{ \theta _ { H j } \}$ is also adjusted with an additive constant.<sup>33</sup> Since the hedging portfolio $\{ \theta _ { H j } \}$ is defined only up to a scaling constant, we let 

$$
n ^ {S W} = 1\tag{44a}
$$

$$
n ^ {E W} - n ^ {S W} = \phi\tag{44b}
$$

where $\phi$ is a parameter that we calibrate to the data (see Section 6.4). This yields the final expression for the J components of the hedging portfolio: 

$$
\widehat {\theta} _ {H j} = \phi \widehat {\beta} _ {\tau j} ^ {E W} + 1.\tag{45}
$$

The normalization $n ^ { S W } = 1$ sets the total number of shares in the portfolio to a positive value. If $\phi = 0$ , the portfolio has equal percentage of all the shares of each company, implying that it is the market portfolio. Nonzero values of $\phi$ represent deviations from the market 

$$
\tau_ {j t} = F _ {M t} + \theta_ {H j} F _ {H t} + \varepsilon_ {j t} = (F _ {M t} + a F _ {H t}) + (\theta_ {H j} - a) F _ {H t} + \varepsilon_ {j t} = \tilde {F} _ {M t} + \tilde {\theta} _ {H j} F _ {H t} + \varepsilon_ {j t}
$$

portfolio. 

To estimate $\{ \beta _ { \tau j } ^ { E W } \}$ and $\{ \beta _ { \tau j } ^ { S W } \}$ , we first construct the two turnover indexes. We estimate (42)–(42) for each of the seven five-year subperiods, ignoring the global constraint (42).<sup>34</sup> Therefore, we estimate constrained linear regressions of the weekly turnover for each stock on equal- and share-weighted turnover indexes in each of the seven five-year subperiods of our sample. 

Table 15 contains summary statistics for these constrained regressions. To provide a clearer sense of the dispersion of these regressions, we first sort them into deciles based on $\{ \widehat { \beta } _ { \tau j } ^ { E W } \}$ , and then compute the means and standard deviations of the estimated coeficients $\{ \widehat { \beta } _ { \tau j } ^ { E W } \}$ and $\{ \widehat { \beta } _ { \tau j } ^ { S W } \}$ , their t-statistics, and the $\bar { R } ^ { 2 } \mathrm { s }$ within each decile. The t-statistics indicate that the estimated coeficients are generally significant—even in the fifth and sixth deciles, the average t-statistic for $\{ \widehat { \beta } _ { \tau j } ^ { E W } \}$ is 4.585 and 6.749, respectively (we would, of course, expect significant t-statistics in the extreme deciles even if the true coeficients were zero, purely from sampling variation). The $\bar { R } ^ { 2 } \mathrm { s }$ also look impressive, however, they must be interpreted with some caution because of the imposition of the constraint (42), which can yield $\bar { R } ^ { 2 }$ greater than unity and less than zero.<sup>35</sup> Table 15 shows that negative $\bar { R } ^ { 2 } \mathrm { s }$ appear mainly in the two extreme deciles, except in the last subperiod when they are negative for all the deciles, presumably an indication that the constraint is not consistent with the data in this last subperiod. 

For comparison, we estimate the unconstrained version of (42) and compute the same summary statistics, reported in Table 16, along with the mean and standard deviation within each decile of p-values corresponding to the statistic that (42) holds. Except for the last subperiod, the constraint seems to be reasonably consistent with the data, with average p-values well above 5% for all but the extreme deciles in most subperiod. For example, in the first subperiod, the average p-values range from a minimum of 4.0% in decile 1 to a maximum of 32.4% in decile 6, and with a value of 19.4% in decile 10. However, in the last subperiod, the average p-value is less than 5% deciles 2–6, and close to significance for most of the other deciles, which explains the negative $\bar { R } ^ { 2 } \mathrm { s }$ in Table 15. 

Without the constraint, the $\bar { R } ^ { 2 } \mathrm { s }$ in Table 16 are well behaved, and of similar magnitude 

<table><tr><td rowspan="2">Decile</td><td rowspan="2">Sample Size</td><td colspan="2"><eq>\widehat{\beta}_{\tau}^{EW}</eq></td><td colspan="2"><eq>t(\widehat{\beta}_{\tau}^{EW})</eq></td><td colspan="2"><eq>\widehat{\beta}_{\tau}^{SW}</eq></td><td colspan="2"><eq>t(\widehat{\beta}_{\tau}^{SW})</eq></td><td colspan="2"><eq>\overline{R}^2 (\%)</eq></td></tr><tr><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td></tr><tr><td colspan="12">July 1962 to December 1966 (234 Weeks)</td></tr><tr><td>1</td><td>218</td><td>-0.906</td><td>0.119</td><td>-49.394</td><td>19.023</td><td>1.906</td><td>0.119</td><td>103.944</td><td>38.755-2520.4</td><td>27817.4</td><td></td></tr><tr><td>2</td><td>219</td><td>-0.657</td><td>0.069</td><td>-26.187</td><td>12.805</td><td>1.657</td><td>0.069</td><td>65.488</td><td>30.083</td><td>56.5</td><td>19.5</td></tr><tr><td>3</td><td>219</td><td>-0.432</td><td>0.064</td><td>-10.917</td><td>5.956</td><td>1.432</td><td>0.064</td><td>35.879</td><td>17.907</td><td>55.0</td><td>20.4</td></tr><tr><td>4</td><td>218</td><td>-0.188</td><td>0.082</td><td>-3.812</td><td>2.732</td><td>1.188</td><td>0.082</td><td>22.907</td><td>10.555</td><td>57.1</td><td>17.8</td></tr><tr><td>5</td><td>219</td><td>0.107</td><td>0.097</td><td>1.273</td><td>1.243</td><td>0.893</td><td>0.097</td><td>11.365</td><td>4.570</td><td>51.5</td><td>16.0</td></tr><tr><td>6</td><td>219</td><td>0.494</td><td>0.119</td><td>4.585</td><td>1.943</td><td>0.506</td><td>0.119</td><td>4.847</td><td>2.401</td><td>50.6</td><td>16.5</td></tr><tr><td>7</td><td>218</td><td>0.927</td><td>0.145</td><td>6.749</td><td>2.258</td><td>0.073</td><td>0.145</td><td>0.639</td><td>1.190</td><td>50.7</td><td>15.5</td></tr><tr><td>8</td><td>219</td><td>1.520</td><td>0.229</td><td>8.229</td><td>2.893</td><td>-0.520</td><td>0.229</td><td>-2.714</td><td>1.348</td><td>49.2</td><td>15.4</td></tr><tr><td>9</td><td>219</td><td>2.568</td><td>0.434</td><td>10.410</td><td>3.491</td><td>-1.568</td><td>0.434</td><td>-6.292</td><td>2.401</td><td>49.4</td><td>15.2</td></tr><tr><td>10</td><td>218</td><td>6.563</td><td>4.100</td><td>11.682</td><td>3.880</td><td>-5.563</td><td>4.100</td><td>-9.500</td><td>3.332</td><td>47.1</td><td>15.3</td></tr><tr><td colspan="12">January 1967 to December 1971 (261 Weeks)</td></tr><tr><td>1</td><td>242</td><td>-0.783</td><td>0.134</td><td>-36.725</td><td>17.343</td><td>1.783</td><td>0.134</td><td>84.302</td><td>38.946</td><td>-175.3</td><td>976.2</td></tr><tr><td>2</td><td>243</td><td>-0.529</td><td>0.056</td><td>-18.772</td><td>8.459</td><td>1.529</td><td>0.056</td><td>53.969</td><td>22.871</td><td>58.2</td><td>16.1</td></tr><tr><td>3</td><td>242</td><td>-0.315</td><td>0.068</td><td>-7.905</td><td>4.099</td><td>1.315</td><td>0.068</td><td>32.431</td><td>13.771</td><td>56.4</td><td>16.3</td></tr><tr><td>4</td><td>243</td><td>-0.054</td><td>0.089</td><td>-1.139</td><td>1.845</td><td>1.054</td><td>0.089</td><td>18.479</td><td>7.855</td><td>55.2</td><td>14.3</td></tr><tr><td>5</td><td>242</td><td>0.264</td><td>0.087</td><td>3.269</td><td>1.482</td><td>0.736</td><td>0.087</td><td>9.228</td><td>3.260</td><td>54.1</td><td>13.2</td></tr><tr><td>6</td><td>243</td><td>0.623</td><td>0.126</td><td>6.035</td><td>2.217</td><td>0.377</td><td>0.126</td><td>3.723</td><td>1.871</td><td>53.5</td><td>13.4</td></tr><tr><td>7</td><td>243</td><td>1.110</td><td>0.154</td><td>8.367</td><td>2.719</td><td>-0.110</td><td>0.154</td><td>-0.735</td><td>1.178</td><td>54.4</td><td>13.0</td></tr><tr><td>8</td><td>242</td><td>1.782</td><td>0.205</td><td>10.314</td><td>3.151</td><td>-0.782</td><td>0.205</td><td>-4.477</td><td>1.630</td><td>53.2</td><td>13.2</td></tr><tr><td>9</td><td>243</td><td>2.661</td><td>0.330</td><td>12.249</td><td>3.120</td><td>-1.661</td><td>0.330</td><td>-7.609</td><td>2.149</td><td>54.6</td><td>11.0</td></tr><tr><td>10</td><td>242</td><td>5.410</td><td>2.540</td><td>13.019</td><td>4.172</td><td>-4.410</td><td>2.540</td><td>-10.260</td><td>3.383</td><td>52.6</td><td>14.2</td></tr><tr><td colspan="12">January 1972 to December 1977 (261 Weeks)</td></tr><tr><td>1</td><td>262</td><td>-2.013</td><td>0.845</td><td>-13.276</td><td>4.901</td><td>3.013</td><td>0.845</td><td>20.755</td><td>8.319-1147.6</td><td>5034.9</td><td></td></tr><tr><td>2</td><td>263</td><td>-1.069</td><td>0.129</td><td>-10.986</td><td>3.890</td><td>2.069</td><td>0.129</td><td>21.239</td><td>7.045</td><td>25.4</td><td>44.6</td></tr><tr><td>3</td><td>263</td><td>-0.697</td><td>0.096</td><td>-6.014</td><td>2.466</td><td>1.697</td><td>0.096</td><td>14.600</td><td>5.619</td><td>44.3</td><td>27.1</td></tr><tr><td>4</td><td>263</td><td>-0.359</td><td>0.105</td><td>-2.825</td><td>1.444</td><td>1.359</td><td>0.105</td><td>10.608</td><td>4.044</td><td>50.3</td><td>22.8</td></tr><tr><td>5</td><td>263</td><td>0.015</td><td>0.114</td><td>0.062</td><td>0.765</td><td>0.985</td><td>0.114</td><td>6.620</td><td>2.466</td><td>53.0</td><td>19.2</td></tr><tr><td>6</td><td>263</td><td>0.485</td><td>0.156</td><td>2.577</td><td>1.159</td><td>0.515</td><td>0.156</td><td>2.792</td><td>1.354</td><td>52.8</td><td>15.4</td></tr><tr><td>7</td><td>263</td><td>1.084</td><td>0.187</td><td>4.684</td><td>1.801</td><td>-0.084</td><td>0.187</td><td>-0.322</td><td>0.870</td><td>51.4</td><td>14.5</td></tr><tr><td>8</td><td>263</td><td>1.888</td><td>0.289</td><td>6.827</td><td>2.426</td><td>-0.888</td><td>0.289</td><td>-3.180</td><td>1.421</td><td>52.8</td><td>14.2</td></tr><tr><td>9</td><td>263</td><td>3.161</td><td>0.501</td><td>8.894</td><td>3.311</td><td>-2.161</td><td>0.501</td><td>-6.060</td><td>2.431</td><td>52.5</td><td>14.0</td></tr><tr><td>10</td><td>262</td><td>7.770</td><td>4.940</td><td>11.202</td><td>4.447</td><td>-6.770</td><td>4.940</td><td>-9.480</td><td>3.965</td><td>52.3</td><td>13.8</td></tr><tr><td colspan="12">January 1977 to December 1981 (261 Weeks)</td></tr><tr><td>1</td><td>242</td><td>-3.096</td><td>0.347</td><td>-22.164</td><td>4.591</td><td>4.096</td><td>0.347</td><td>29.341</td><td>5.815</td><td>-872.7</td><td>6958.8</td></tr><tr><td>2</td><td>243</td><td>-2.284</td><td>0.192</td><td>-15.799</td><td>4.883</td><td>3.284</td><td>0.192</td><td>22.701</td><td>6.846</td><td>32.7</td><td>23.6</td></tr><tr><td>3</td><td>243</td><td>-1.654</td><td>0.208</td><td>-10.524</td><td>4.628</td><td>2.654</td><td>0.208</td><td>16.861</td><td>7.167</td><td>48.9</td><td>20.8</td></tr><tr><td>4</td><td>243</td><td>-1.021</td><td>0.156</td><td>-5.505</td><td>2.335</td><td>2.021</td><td>0.156</td><td>10.884</td><td>4.304</td><td>54.1</td><td>18.4</td></tr><tr><td>5</td><td>243</td><td>-0.394</td><td>0.189</td><td>-1.833</td><td>1.180</td><td>1.394</td><td>0.189</td><td>6.387</td><td>2.655</td><td>55.6</td><td>17.1</td></tr><tr><td>6</td><td>243</td><td>0.355</td><td>0.250</td><td>1.277</td><td>1.045</td><td>0.645</td><td>0.250</td><td>2.472</td><td>1.438</td><td>55.5</td><td>16.5</td></tr><tr><td>7</td><td>243</td><td>1.330</td><td>0.308</td><td>3.864</td><td>1.519</td><td>-0.330</td><td>0.308</td><td>-0.894</td><td>0.971</td><td>53.6</td><td>15.7</td></tr><tr><td>8</td><td>243</td><td>2.599</td><td>0.457</td><td>6.198</td><td>2.242</td><td>-1.599</td><td>0.457</td><td>-3.782</td><td>1.560</td><td>54.5</td><td>15.7</td></tr><tr><td>9</td><td>243</td><td>4.913</td><td>0.809</td><td>8.860</td><td>2.983</td><td>-3.913</td><td>0.809</td><td>-7.038</td><td>2.487</td><td>55.3</td><td>14.5</td></tr><tr><td>10</td><td>242</td><td>10.090</td><td>4.231</td><td>11.202</td><td>3.618</td><td>-9.090</td><td>4.231</td><td>-9.980</td><td>3.311</td><td>55.2</td><td>13.4</td></tr><tr><td rowspan="2">Decile</td><td rowspan="2">Sample Size</td><td colspan="2"><eq>\widehat{\beta}_{\tau}^{EW}</eq></td><td colspan="2"><eq>t(\widehat{\beta}_{\tau}^{EW})</eq></td><td colspan="2"><eq>\widehat{\beta}_{\tau}^{SW}</eq></td><td colspan="2"><eq>t(\widehat{\beta}_{\tau}^{SW})</eq></td><td colspan="2"><eq>\overline{R}^2</eq> (%)</td></tr><tr><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td></tr><tr><td colspan="12">January 1982 to December 1986 (261 Weeks)</td></tr><tr><td>1</td><td>227</td><td>-6.968</td><td>3.038</td><td>-5.636</td><td>2.328</td><td>7.968</td><td>3.038</td><td>6.525</td><td>2.577</td><td>46.6</td><td>15.9</td></tr><tr><td>2</td><td>228</td><td>-2.257</td><td>0.624</td><td>-3.249</td><td>1.604</td><td>3.257</td><td>0.624</td><td>4.724</td><td>2.199</td><td>52.7</td><td>20.2</td></tr><tr><td>3</td><td>228</td><td>-0.640</td><td>0.380</td><td>-1.223</td><td>0.967</td><td>1.640</td><td>0.380</td><td>3.180</td><td>1.667</td><td>45.5</td><td>136.9</td></tr><tr><td>4</td><td>227</td><td>0.501</td><td>0.283</td><td>1.166</td><td>0.841</td><td>0.499</td><td>0.283</td><td>1.177</td><td>0.903</td><td>55.4</td><td>22.4</td></tr><tr><td>5</td><td>228</td><td>1.357</td><td>0.231</td><td>3.540</td><td>1.655</td><td>-0.357</td><td>0.231</td><td>-0.954</td><td>0.786</td><td>41.3</td><td>90.7</td></tr><tr><td>6</td><td>228</td><td>2.077</td><td>0.201</td><td>5.319</td><td>2.159</td><td>-1.077</td><td>0.201</td><td>-2.758</td><td>1.216</td><td>-19.5</td><td>686.3</td></tr><tr><td>7</td><td>227</td><td>2.754</td><td>0.196</td><td>7.402</td><td>2.342</td><td>-1.754</td><td>0.196</td><td>-4.710</td><td>1.531</td><td>28.3</td><td>52.8</td></tr><tr><td>8</td><td>228</td><td>3.431</td><td>0.201</td><td>9.244</td><td>2.667</td><td>-2.431</td><td>0.201</td><td>-6.548</td><td>1.922</td><td>3.2</td><td>101.8</td></tr><tr><td>9</td><td>228</td><td>4.168</td><td>0.237</td><td>11.354</td><td>2.905</td><td>-3.168</td><td>0.237</td><td>-8.630</td><td>2.248</td><td>-163.1</td><td>1678.6</td></tr><tr><td>10</td><td>227</td><td>5.399</td><td>1.170</td><td>14.045</td><td>5.229</td><td>-4.399</td><td>1.170</td><td>-11.392</td><td>4.405</td><td>-348.1</td><td>1027.1</td></tr><tr><td colspan="12">January 1987 to December 1991 (261 Weeks)</td></tr><tr><td>1</td><td>216</td><td>-8.487</td><td>7.040</td><td>-7.093</td><td>3.763</td><td>9.487</td><td>7.040</td><td>8.082</td><td>4.137</td><td>50.2</td><td>16.8</td></tr><tr><td>2</td><td>217</td><td>-2.866</td><td>0.725</td><td>-4.616</td><td>2.439</td><td>3.866</td><td>0.725</td><td>6.263</td><td>3.224</td><td>54.8</td><td>18.8</td></tr><tr><td>3</td><td>217</td><td>-0.843</td><td>0.494</td><td>-1.832</td><td>1.512</td><td>1.843</td><td>0.494</td><td>4.097</td><td>2.537</td><td>56.8</td><td>21.0</td></tr><tr><td>4</td><td>217</td><td>0.441</td><td>0.330</td><td>1.196</td><td>1.277</td><td>0.559</td><td>0.330</td><td>1.423</td><td>1.268</td><td>57.0</td><td>19.9</td></tr><tr><td>5</td><td>217</td><td>1.502</td><td>0.317</td><td>4.887</td><td>3.062</td><td>-0.502</td><td>0.317</td><td>-1.693</td><td>1.583</td><td>57.8</td><td>18.8</td></tr><tr><td>6</td><td>217</td><td>2.510</td><td>0.280</td><td>8.434</td><td>4.070</td><td>-1.510</td><td>0.280</td><td>-5.074</td><td>2.582</td><td>51.2</td><td>18.7</td></tr><tr><td>7</td><td>217</td><td>3.389</td><td>0.234</td><td>12.139</td><td>4.615</td><td>-2.389</td><td>0.234</td><td>-8.567</td><td>3.325</td><td>42.2</td><td>15.6</td></tr><tr><td>8</td><td>217</td><td>4.157</td><td>0.196</td><td>15.329</td><td>4.607</td><td>-3.157</td><td>0.196</td><td>-11.637</td><td>3.513</td><td>23.8</td><td>19.8</td></tr><tr><td>9</td><td>217</td><td>4.836</td><td>0.212</td><td>18.370</td><td>4.580</td><td>-3.836</td><td>0.212</td><td>-14.572</td><td>3.673</td><td>-27.0</td><td>66.1</td></tr><tr><td>10</td><td>217</td><td>5.743</td><td>0.402</td><td>21.430</td><td>5.101</td><td>-4.743</td><td>0.402</td><td>-17.682</td><td>4.229</td><td>-921.9</td><td>4682.1</td></tr><tr><td colspan="12">January 1992 to December 1996 (261 Weeks)</td></tr><tr><td>1</td><td>241</td><td>-4.275</td><td>2.858</td><td>-2.409</td><td>1.092</td><td>5.275</td><td>2.858</td><td>3.097</td><td>1.342</td><td>-423.6</td><td>3336.7</td></tr><tr><td>2</td><td>241</td><td>-1.074</td><td>0.384</td><td>-1.277</td><td>0.741</td><td>2.074</td><td>0.384</td><td>2.538</td><td>1.369</td><td>-147.7</td><td>2631.2</td></tr><tr><td>3</td><td>242</td><td>-0.245</td><td>0.155</td><td>-0.371</td><td>0.301</td><td>1.245</td><td>0.155</td><td>1.944</td><td>0.899</td><td>-14.7</td><td>508.2</td></tr><tr><td>4</td><td>241</td><td>0.189</td><td>0.100</td><td>0.298</td><td>0.203</td><td>0.811</td><td>0.100</td><td>1.296</td><td>0.534</td><td>-135.1</td><td>899.3</td></tr><tr><td>5</td><td>241</td><td>0.520</td><td>0.098</td><td>0.779</td><td>0.313</td><td>0.480</td><td>0.098</td><td>0.729</td><td>0.330</td><td>-1353.9</td><td>5755.2</td></tr><tr><td>6</td><td>242</td><td>0.865</td><td>0.106</td><td>1.226</td><td>0.414</td><td>0.135</td><td>0.106</td><td>0.196</td><td>0.177</td><td>-197.6</td><td>669.1</td></tr><tr><td>7</td><td>241</td><td>1.303</td><td>0.159</td><td>1.725</td><td>0.641</td><td>-0.303</td><td>0.159</td><td>-0.400</td><td>0.260</td><td>-130.3</td><td>931.7</td></tr><tr><td>8</td><td>242</td><td>2.022</td><td>0.254</td><td>2.391</td><td>0.824</td><td>-1.022</td><td>0.254</td><td>-1.202</td><td>0.480</td><td>-58.9</td><td>684.5</td></tr><tr><td>9</td><td>241</td><td>3.271</td><td>0.498</td><td>3.061</td><td>1.027</td><td>-2.271</td><td>0.498</td><td>-2.117</td><td>0.769</td><td>-24.9</td><td>225.8</td></tr><tr><td>10</td><td>241</td><td>8.234</td><td>9.836</td><td>3.844</td><td>1.360</td><td>-7.234</td><td>9.836</td><td>-3.237</td><td>1.190</td><td>-219.9</td><td>1145.7</td></tr></table>


Table 15a: Summary statistics for the restricted volume betas using weekly returns and volume data for NYSE and AMEX stocks from 1962 to 1996 in five-year subperiods. Turnover over individual stocks is regressed on the equally-weighted and share- weighted turnover indices, subject to the restriction that the two regression coeficients, $\widehat { \beta } _ { \tau } ^ { E W }$ and $\widehat { \beta } _ { \tau } ^ { S W }$ , must add up to one. The stocks are then sorted into ten deciles by $\widehat { \beta } _ { \tau } ^ { E W }$ b b. The summary statistics are then reported for each decile.



to those in Table 15 that are between 0% and 100%, ranging from 40% to 60%, even in the last subperiod. Clearly the two-factor model of turnover accounts for a significant amount of variation in the weekly turnover of individual stocks.


<table><tr><td rowspan="2">Decile</td><td rowspan="2">Sample Size</td><td colspan="2"><eq>\widehat{\beta}_{\tau}^{EW}</eq></td><td colspan="2"><eq>t(\widehat{\beta}_{\tau}^{EW})</eq></td><td colspan="2"><eq>\widehat{\beta}_{\tau}^{SW}</eq></td><td colspan="2"><eq>t(\widehat{\beta}_{\tau}^{SW})</eq></td><td colspan="2"><eq>\overline{R}^2 (\%)</eq></td><td colspan="2">p-value (%)</td></tr><tr><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td></tr><tr><td colspan="14">July 1962 to December 1966 (234 Weeks)</td></tr><tr><td>1</td><td>218</td><td>-4.749</td><td>6.337</td><td>-4.121</td><td>2.174</td><td>11.761</td><td>14.451</td><td>5.608</td><td>2.556</td><td>51.4</td><td>18.7</td><td>0.7</td><td>4.0</td></tr><tr><td>2</td><td>219</td><td>-1.321</td><td>0.249</td><td>-3.622</td><td>2.152</td><td>3.891</td><td>1.043</td><td>5.351</td><td>2.670</td><td>57.3</td><td>16.7</td><td>2.3</td><td>8.5</td></tr><tr><td>3</td><td>219</td><td>-0.730</td><td>0.110</td><td>-3.500</td><td>2.466</td><td>2.398</td><td>0.786</td><td>5.394</td><td>3.054</td><td>59.5</td><td>17.5</td><td>16.7</td><td>23.8</td></tr><tr><td>4</td><td>218</td><td>-0.406</td><td>0.071</td><td>-2.756</td><td>1.971</td><td>1.548</td><td>0.664</td><td>4.706</td><td>2.593</td><td>61.0</td><td>17.0</td><td>23.3</td><td>29.2</td></tr><tr><td>5</td><td>219</td><td>-0.195</td><td>0.055</td><td>-2.603</td><td>2.262</td><td>0.967</td><td>0.644</td><td>4.810</td><td>3.103</td><td>63.0</td><td>20.2</td><td>13.2</td><td>24.8</td></tr><tr><td>6</td><td>219</td><td>0.034</td><td>0.090</td><td>-0.012</td><td>0.960</td><td>0.790</td><td>0.806</td><td>1.723</td><td>1.250</td><td>54.6</td><td>19.1</td><td>19.0</td><td>28.6</td></tr><tr><td>7</td><td>218</td><td>0.508</td><td>0.206</td><td>1.554</td><td>1.080</td><td>0.337</td><td>1.058</td><td>-0.015</td><td>1.111</td><td>52.0</td><td>16.4</td><td>26.0</td><td>32.4</td></tr><tr><td>8</td><td>219</td><td>1.470</td><td>0.336</td><td>2.675</td><td>1.481</td><td>-0.768</td><td>1.834</td><td>-1.218</td><td>1.375</td><td>51.7</td><td>14.3</td><td>26.9</td><td>31.5</td></tr><tr><td>9</td><td>219</td><td>3.400</td><td>0.875</td><td>3.685</td><td>1.817</td><td>-3.639</td><td>2.059</td><td>-2.392</td><td>1.670</td><td>46.7</td><td>14.2</td><td>22.0</td><td>30.1</td></tr><tr><td>10</td><td>218</td><td>11.334</td><td>8.125</td><td>5.387</td><td>2.376</td><td>-15.963</td><td>12.976</td><td>-4.137</td><td>2.147</td><td>46.3</td><td>14.7</td><td>9.6</td><td>19.4</td></tr><tr><td colspan="14">January 1967 to December 1971 (261 Weeks)</td></tr><tr><td>1</td><td>242</td><td>-5.109</td><td>17.101</td><td>-4.306</td><td>2.689</td><td>12.966</td><td>35.908</td><td>6.280</td><td>3.303</td><td>52.1</td><td>16.3</td><td>1.0</td><td>4.3</td></tr><tr><td>2</td><td>243</td><td>-0.770</td><td>0.141</td><td>-4.458</td><td>3.052</td><td>2.694</td><td>1.188</td><td>7.022</td><td>3.776</td><td>59.3</td><td>14.3</td><td>10.3</td><td>20.3</td></tr><tr><td>3</td><td>242</td><td>-0.409</td><td>0.078</td><td>-4.600</td><td>3.229</td><td>1.534</td><td>0.634</td><td>7.725</td><td>4.170</td><td>64.3</td><td>14.8</td><td>19.8</td><td>27.7</td></tr><tr><td>4</td><td>243</td><td>-0.176</td><td>0.071</td><td>-2.299</td><td>2.609</td><td>1.128</td><td>0.729</td><td>5.222</td><td>3.639</td><td>60.6</td><td>15.5</td><td>16.3</td><td>27.9</td></tr><tr><td>5</td><td>242</td><td>0.086</td><td>0.087</td><td>0.628</td><td>1.123</td><td>0.851</td><td>0.968</td><td>2.003</td><td>1.537</td><td>57.5</td><td>15.6</td><td>15.5</td><td>27.2</td></tr><tr><td>6</td><td>243</td><td>0.492</td><td>0.152</td><td>2.139</td><td>1.441</td><td>0.447</td><td>0.924</td><td>0.260</td><td>1.289</td><td>56.9</td><td>13.0</td><td>20.5</td><td>29.4</td></tr><tr><td>7</td><td>243</td><td>1.096</td><td>0.201</td><td>3.379</td><td>1.886</td><td>-0.383</td><td>0.931</td><td>-1.096</td><td>1.617</td><td>56.0</td><td>12.0</td><td>20.6</td><td>28.1</td></tr><tr><td>8</td><td>242</td><td>1.906</td><td>0.307</td><td>4.567</td><td>2.143</td><td>-1.583</td><td>1.057</td><td>-2.328</td><td>1.825</td><td>56.4</td><td>12.2</td><td>18.3</td><td>28.5</td></tr><tr><td>9</td><td>243</td><td>3.275</td><td>0.556</td><td>5.533</td><td>2.246</td><td>-3.417</td><td>1.223</td><td>-3.202</td><td>1.760</td><td>56.5</td><td>12.3</td><td>16.8</td><td>24.9</td></tr><tr><td>10</td><td>242</td><td>7.499</td><td>3.595</td><td>6.827</td><td>2.626</td><td>-9.674</td><td>5.563</td><td>-4.641</td><td>2.050</td><td>55.6</td><td>11.7</td><td>10.1</td><td>21.8</td></tr><tr><td colspan="14">January 1972 to December 1976 (261 Weeks)</td></tr><tr><td>1</td><td>262</td><td>-1.908</td><td>1.364</td><td>-4.116</td><td>2.584</td><td>4.371</td><td>2.731</td><td>7.313</td><td>3.930</td><td>57.0</td><td>17.7</td><td>3.2</td><td>11.7</td></tr><tr><td>2</td><td>263</td><td>-0.603</td><td>0.131</td><td>-3.849</td><td>3.151</td><td>1.874</td><td>0.665</td><td>8.135</td><td>4.806</td><td>66.3</td><td>17.2</td><td>11.0</td><td>24.0</td></tr><tr><td>3</td><td>263</td><td>-0.237</td><td>0.094</td><td>-1.949</td><td>1.632</td><td>1.120</td><td>0.481</td><td>6.085</td><td>3.129</td><td>64.7</td><td>16.6</td><td>8.4</td><td>20.6</td></tr><tr><td>4</td><td>263</td><td>0.032</td><td>0.071</td><td>0.316</td><td>0.872</td><td>0.714</td><td>0.570</td><td>3.258</td><td>1.805</td><td>58.0</td><td>17.2</td><td>5.3</td><td>16.8</td></tr><tr><td>5</td><td>263</td><td>0.308</td><td>0.091</td><td>2.249</td><td>1.733</td><td>0.480</td><td>0.659</td><td>1.076</td><td>1.942</td><td>56.1</td><td>15.5</td><td>6.1</td><td>16.7</td></tr><tr><td>6</td><td>263</td><td>0.645</td><td>0.114</td><td>3.586</td><td>2.285</td><td>0.120</td><td>0.807</td><td>-0.517</td><td>2.197</td><td>54.3</td><td>14.8</td><td>7.1</td><td>18.9</td></tr><tr><td>7</td><td>263</td><td>1.107</td><td>0.141</td><td>4.929</td><td>2.814</td><td>-0.361</td><td>0.611</td><td>-1.996</td><td>2.475</td><td>55.5</td><td>14.3</td><td>7.7</td><td>20.9</td></tr><tr><td>8</td><td>263</td><td>1.700</td><td>0.218</td><td>6.180</td><td>3.237</td><td>-0.910</td><td>0.736</td><td>-3.229</td><td>2.838</td><td>56.8</td><td>13.7</td><td>9.9</td><td>23.6</td></tr><tr><td>9</td><td>263</td><td>2.846</td><td>0.497</td><td>7.823</td><td>3.678</td><td>-2.054</td><td>0.894</td><td>-4.950</td><td>3.194</td><td>57.0</td><td>13.8</td><td>9.6</td><td>22.2</td></tr><tr><td>10</td><td>262</td><td>6.609</td><td>3.411</td><td>10.196</td><td>4.149</td><td>-5.892</td><td>3.463</td><td>-7.409</td><td>3.566</td><td>59.3</td><td>11.8</td><td>13.1</td><td>25.6</td></tr></table>

Table 16a: Summary statistics for the unrestricted volume betas using weekly returns and volume data for NYSE and AMEX stocks from 1962 to 1996 in five-year subperiods. Turnover over individual stocks are regressed on the equally-weighted and share- weighted turnover indices, giving two regression coeficients, $\beta _ { \tau } ^ { E W }$ and $\beta _ { \tau } ^ { S W }$ . The stocks are then sorted into ten deciles by the estimates of their $\widehat { \beta } _ { \tau } ^ { E W }$ . The summary statistics are reported for each decile. bThe last two columns report the test statistic for the condition that $\bar { \beta } _ { \tau } ^ { E W }$ and $\beta _ { \tau } ^ { S W }$ add up to one. 

## 6.4 The Forecast Power of the Hedging Portfolio

Having constructed the hedging portfolio up to a parameter $\phi$ to be determined, we can examine its time-series properties as predicted by the model. In particular, in this section we focus on the degree to which the hedging portfolio can predict future stock returns, especially the return on the market portfolio. We first construct the returns of the hedging portfolio in Section 6.4 by calibrating $\phi ,$ and then compare its forecast power with other factors in Sections 6.4 and 6.4. 

<table><tr><td rowspan="2">Decile</td><td rowspan="2">Sample Size</td><td colspan="2"><eq>\widehat{\beta}_{\tau}^{EW}</eq></td><td colspan="2"><eq>t(\widehat{\beta}_{\tau}^{EW})</eq></td><td colspan="2"><eq>\widehat{\beta}_{\tau}^{SW}</eq></td><td colspan="2"><eq>t(\widehat{\beta}_{\tau}^{SW})</eq></td><td colspan="2"><eq>\overline{R}^2 (\%)</eq></td><td colspan="2">p-value (%)</td></tr><tr><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td><td>Mean</td><td>S.D.</td></tr><tr><td colspan="14">January 1977 to December 1981 (261 Weeks)</td></tr><tr><td>1</td><td>242</td><td>-2.622</td><td>1.777</td><td>-2.975</td><td>1.647</td><td>4.749</td><td>2.675</td><td>4.516</td><td>2.251</td><td>54.0</td><td>20.0</td><td>6.4</td><td>16.0</td></tr><tr><td>2</td><td>243</td><td>-0.805</td><td>0.175</td><td>-2.356</td><td>1.508</td><td>1.920</td><td>0.662</td><td>4.251</td><td>2.176</td><td>61.6</td><td>17.5</td><td>13.2</td><td>23.9</td></tr><tr><td>3</td><td>243</td><td>-0.364</td><td>0.101</td><td>-1.559</td><td>1.160</td><td>1.186</td><td>0.539</td><td>3.553</td><td>1.876</td><td>62.0</td><td>18.7</td><td>7.7</td><td>19.3</td></tr><tr><td>4</td><td>243</td><td>-0.072</td><td>0.076</td><td>-0.337</td><td>0.564</td><td>0.733</td><td>0.481</td><td>2.061</td><td>0.999</td><td>56.3</td><td>19.0</td><td>8.8</td><td>21.7</td></tr><tr><td>5</td><td>243</td><td>0.218</td><td>0.093</td><td>0.780</td><td>0.585</td><td>0.504</td><td>0.673</td><td>0.781</td><td>0.823</td><td>53.5</td><td>15.9</td><td>7.0</td><td>18.3</td></tr><tr><td>6</td><td>243</td><td>0.575</td><td>0.119</td><td>1.604</td><td>0.998</td><td>0.238</td><td>0.643</td><td>0.002</td><td>1.053</td><td>56.1</td><td>14.5</td><td>11.0</td><td>21.7</td></tr><tr><td>7</td><td>243</td><td>1.081</td><td>0.184</td><td>2.241</td><td>1.194</td><td>-0.209</td><td>0.641</td><td>-0.727</td><td>1.161</td><td>54.5</td><td>13.9</td><td>12.1</td><td>24.8</td></tr><tr><td>8</td><td>243</td><td>1.900</td><td>0.284</td><td>3.108</td><td>1.530</td><td>-0.917</td><td>0.758</td><td>-1.610</td><td>1.446</td><td>54.7</td><td>13.1</td><td>13.3</td><td>24.4</td></tr><tr><td>9</td><td>243</td><td>2.993</td><td>0.398</td><td>3.819</td><td>1.593</td><td>-1.995</td><td>0.784</td><td>-2.326</td><td>1.482</td><td>54.6</td><td>14.8</td><td>15.9</td><td>27.8</td></tr><tr><td>10</td><td>242</td><td>7.240</td><td>4.979</td><td>4.819</td><td>1.899</td><td>-6.163</td><td>5.374</td><td>-3.419</td><td>1.788</td><td>54.5</td><td>13.8</td><td>20.8</td><td>29.3</td></tr><tr><td colspan="14">January 1982 to December 1986 (261 Weeks)</td></tr><tr><td>1</td><td>227</td><td>-3.038</td><td>1.819</td><td>-2.588</td><td>1.102</td><td>4.377</td><td>2.097</td><td>4.014</td><td>1.497</td><td>49.6</td><td>18.2</td><td>14.6</td><td>26.1</td></tr><tr><td>2</td><td>228</td><td>-0.939</td><td>0.245</td><td>-1.940</td><td>1.284</td><td>1.821</td><td>0.593</td><td>3.799</td><td>2.206</td><td>57.6</td><td>19.9</td><td>7.7</td><td>19.0</td></tr><tr><td>3</td><td>228</td><td>-0.342</td><td>0.123</td><td>-1.021</td><td>0.686</td><td>1.045</td><td>0.477</td><td>2.945</td><td>1.427</td><td>58.7</td><td>18.5</td><td>4.9</td><td>17.0</td></tr><tr><td>4</td><td>227</td><td>0.028</td><td>0.087</td><td>0.116</td><td>0.513</td><td>0.631</td><td>0.459</td><td>1.704</td><td>0.933</td><td>57.6</td><td>16.7</td><td>5.0</td><td>15.9</td></tr><tr><td>5</td><td>228</td><td>0.349</td><td>0.101</td><td>1.247</td><td>0.917</td><td>0.340</td><td>0.465</td><td>0.548</td><td>1.118</td><td>55.9</td><td>19.0</td><td>4.0</td><td>14.4</td></tr><tr><td>6</td><td>228</td><td>0.732</td><td>0.117</td><td>2.306</td><td>1.561</td><td>0.073</td><td>0.587</td><td>-0.507</td><td>1.641</td><td>57.9</td><td>16.4</td><td>4.6</td><td>16.0</td></tr><tr><td>7</td><td>227</td><td>1.204</td><td>0.178</td><td>3.278</td><td>1.885</td><td>-0.396</td><td>0.486</td><td>-1.647</td><td>1.842</td><td>55.3</td><td>13.8</td><td>7.7</td><td>19.7</td></tr><tr><td>8</td><td>228</td><td>1.908</td><td>0.249</td><td>3.840</td><td>1.907</td><td>-0.907</td><td>0.525</td><td>-2.252</td><td>1.856</td><td>54.8</td><td>14.6</td><td>11.2</td><td>24.1</td></tr><tr><td>9</td><td>228</td><td>3.020</td><td>0.459</td><td>5.012</td><td>2.350</td><td>-1.754</td><td>0.663</td><td>-3.369</td><td>2.197</td><td>57.8</td><td>12.7</td><td>11.0</td><td>23.4</td></tr><tr><td>10</td><td>227</td><td>6.772</td><td>3.345</td><td>6.400</td><td>2.616</td><td>-4.903</td><td>2.873</td><td>-4.976</td><td>2.415</td><td>54.9</td><td>13.1</td><td>4.9</td><td>15.2</td></tr><tr><td colspan="14">January 1987 to December 1991 (261 Weeks)</td></tr><tr><td>1</td><td>216</td><td>-3.153</td><td>3.353</td><td>-1.997</td><td>1.036</td><td>4.278</td><td>3.325</td><td>3.224</td><td>1.656</td><td>47.5</td><td>23.3</td><td>20.7</td><td>30.0</td></tr><tr><td>2</td><td>217</td><td>-0.620</td><td>0.236</td><td>-1.246</td><td>0.866</td><td>1.367</td><td>0.546</td><td>2.872</td><td>1.734</td><td>57.4</td><td>21.7</td><td>10.2</td><td>22.9</td></tr><tr><td>3</td><td>217</td><td>-0.098</td><td>0.093</td><td>-0.307</td><td>0.417</td><td>0.673</td><td>0.440</td><td>1.899</td><td>1.156</td><td>56.2</td><td>21.5</td><td>5.0</td><td>16.5</td></tr><tr><td>4</td><td>217</td><td>0.194</td><td>0.077</td><td>0.795</td><td>0.781</td><td>0.332</td><td>0.417</td><td>0.739</td><td>1.123</td><td>55.9</td><td>20.3</td><td>4.6</td><td>16.0</td></tr><tr><td>5</td><td>217</td><td>0.479</td><td>0.086</td><td>1.443</td><td>0.873</td><td>0.150</td><td>0.438</td><td>-0.013</td><td>1.000</td><td>55.5</td><td>17.8</td><td>5.1</td><td>18.0</td></tr><tr><td>6</td><td>217</td><td>0.764</td><td>0.084</td><td>2.059</td><td>1.074</td><td>-0.082</td><td>0.433</td><td>-0.623</td><td>1.185</td><td>56.0</td><td>17.9</td><td>6.7</td><td>19.5</td></tr><tr><td>7</td><td>217</td><td>1.177</td><td>0.146</td><td>2.344</td><td>1.068</td><td>-0.338</td><td>0.474</td><td>-1.053</td><td>1.105</td><td>52.9</td><td>16.8</td><td>07.8</td><td>19.8</td></tr><tr><td>8</td><td>217</td><td>1.806</td><td>0.246</td><td>2.756</td><td>1.259</td><td>-0.719</td><td>0.508</td><td>-1.436</td><td>1.170</td><td>53.9</td><td>16.3</td><td>14.0</td><td>26.3</td></tr><tr><td>9</td><td>217</td><td>2.972</td><td>0.452</td><td>3.104</td><td>1.371</td><td>-1.531</td><td>0.610</td><td>-1.921</td><td>1.231</td><td>51.3</td><td>15.3</td><td>11.5</td><td>22.3</td></tr><tr><td>10</td><td>217</td><td>6.485</td><td>3.351</td><td>3.830</td><td>1.656</td><td>-4.209</td><td>2.654</td><td>-2.823</td><td>1.538</td><td>47.5</td><td>15.8</td><td>4.1</td><td>12.6</td></tr><tr><td colspan="14">January 1992 to December 1996 (261 Weeks)</td></tr><tr><td>1</td><td>241</td><td>-2.894</td><td>2.074</td><td>-2.174</td><td>1.107</td><td>4.563</td><td>2.659</td><td>3.498</td><td>1.595</td><td>57.4</td><td>19.6</td><td>5.5</td><td>16.3</td></tr><tr><td>2</td><td>241</td><td>-0.681</td><td>0.206</td><td>-1.335</td><td>0.822</td><td>1.613</td><td>0.622</td><td>2.886</td><td>1.450</td><td>61.3</td><td>21.0</td><td>4.8</td><td>16.3</td></tr><tr><td>3</td><td>242</td><td>-0.197</td><td>0.093</td><td>-0.623</td><td>0.612</td><td>0.924</td><td>0.534</td><td>2.192</td><td>1.396</td><td>59.8</td><td>22.6</td><td>2.3</td><td>9.7</td></tr><tr><td>4</td><td>241</td><td>0.072</td><td>0.072</td><td>0.308</td><td>0.485</td><td>0.526</td><td>0.488</td><td>1.057</td><td>0.905</td><td>56.0</td><td>20.7</td><td>2.8</td><td>13.4</td></tr><tr><td>5</td><td>241</td><td>0.344</td><td>0.085</td><td>1.064</td><td>0.731</td><td>0.261</td><td>0.441</td><td>0.281</td><td>0.951</td><td>55.6</td><td>20.0</td><td>3.5</td><td>12.8</td></tr><tr><td>6</td><td>242</td><td>0.624</td><td>0.093</td><td>1.430</td><td>0.778</td><td>0.124</td><td>0.659</td><td>-0.176</td><td>0.909</td><td>55.1</td><td>18.2</td><td>2.7</td><td>10.3</td></tr><tr><td>7</td><td>241</td><td>1.018</td><td>0.130</td><td>2.028</td><td>1.151</td><td>-0.224</td><td>0.578</td><td>-0.836</td><td>1.176</td><td>53.3</td><td>17.0</td><td>6.4</td><td>18.8</td></tr><tr><td>8</td><td>242</td><td>1.618</td><td>0.230</td><td>2.357</td><td>1.122</td><td>-0.694</td><td>0.647</td><td>-1.248</td><td>1.110</td><td>51.4</td><td>17.2</td><td>6.1</td><td>18.1</td></tr><tr><td>9</td><td>241</td><td>2.720</td><td>0.454</td><td>2.624</td><td>1.170</td><td>-1.477</td><td>0.830</td><td>-1.616</td><td>1.088</td><td>49.4</td><td>15.1</td><td>10.7</td><td>23.7</td></tr><tr><td>10</td><td>241</td><td>7.977</td><td>9.529</td><td>3.706</td><td>1.411</td><td>-6.205</td><td>9.055</td><td>-2.823</td><td>1.339</td><td>45.3</td><td>14.5</td><td>6.2</td><td>17.4</td></tr></table>


Table 16b: (continued).


## Hedging-Portfolio Returns

To construct the return on the hedging portfolio, we begin by calculating its dollar value and dollar returns. Let k denote subperiod k, $k = 2 , \ldots , 7 , V _ { j t } ( k )$ denote the total market capitalization of stock j at time period t (the end of week t) in subperiod k, $Q _ { j t } ( k )$ denote its dividend-adjusted excess dollar return for the same period, and $R _ { j t } ( k )$ denote the dividend-adjusted excess return, and $\theta _ { j } ( k )$ the estimated share (as fraction of its total shares outstanding) in the hedging portfolio in subperiod k. 

For stock j to be included in the hedging portfolio in subperiod k, which we shall refer to as the “testing period”, we require it to have volume data for at least one third of the sample in the previous subperiod (k−1), which we call the “estimation period”. Among the stocks satisfying this criteria, we eliminate those ranked in the top and bottom 0.5% according to their volume betas (or their share weights in the hedging portfolio) to limit the potential impact of outliers.<sup>36</sup> We let $J _ { t } ( k )$ denote the set of stocks that survive these two filters and that have price and return data for week t of subperiod k. The hedging portfolio in week t of sub-period k is then given by: 

$$
\theta_ {H j t} (k) = \left\{ \begin{array}{l l} \widehat {\theta} _ {H j}, & j \in J _ {t} (k) \\ 0, & j \notin J _ {t} (k) \end{array} \right.\tag{46}
$$

The dollar return of the hedging portfolio for week t follows naturally: 

$$
Q _ {H t} (k) \equiv \sum_ {j} \theta_ {H j t} (k) V _ {j t} R _ {j t}.\tag{47}
$$

and the (rate of) return of the hedging portfolio is given by 

$$
R _ {H t} (k) \equiv \frac {Q _ {H j t} (k)}{V _ {H t} (k)}\tag{48}
$$

where 

$$
V _ {H t} (k) \equiv \sum_ {j} \theta_ {H j t} (k) V _ {j t - 1}\tag{49}
$$

is the value of the hedging portfolio at the beginning of the week. 

The procedure outlined above yields the return and the dollar return of the hedging portfolio up to the parameter $\phi ,$ which must be calibrated. To do so, we exploit a key property of the hedging portfolio: its return is the best forecaster of future market returns (see Section 6.2). Therefore, for a given value of $\phi ,$ we can estimate the following regression 

$$
R _ {M t + 1} = \delta_ {0} + \delta_ {1} \left\{R _ {H t} \mathrm{or} Q _ {H t} \right\} + \varepsilon_ {M t + 1}\tag{50}
$$

where the single regressor is either the return of the hedging portfolio $R _ { H t }$ or its dollar return for a given choice of $\phi ,$ and then vary $\phi$ to maximize the $\bar { R } ^ { 2 }$ .<sup>37</sup> 

In all cases, there is a unique global maximum, from which we obtain $\phi .$ . However, for some values of $\phi ,$ the value of the hedging portfolio changes sign, and in these cases, defining the return on the portfolio becomes problematic. Therefore, we eliminate these values from consideration, and for all subperiods except subperiod 4 and $7$ (i.e., subperiods 2, 3, 5, 6), the omitted values of $\phi$ do not seem to afect the choice of $\phi$ for the maximum $R ^ { 2 }$ (see Lo and Wang (2001) for more discussions on the choice of $\phi )$ 

For subperiods 2 to $^ { 7 , }$ the values for $\phi$ that give the maximum $R ^ { 2 }$ are 1.25, 4.75, 1.75, 47, 38, and 0.25, respectively, using $R _ { H t }$ as the predictor. Using $Q _ { H t }$ , the values of $\phi$ are 1.5, 4.25, 2, 20, 27, and 0.75, respectively. With these values of $\phi$ in hand, we have fully specified the hedging portfolio, its return and dollar return. Table 17 reports the summary statistics for the return and dollar return on the hedging portfolio. 

## Optimal Forecasting Portfolios (OFPs)

Having constructed the return of the hedging portfolio in Section 6.4, we wish to compare its forecast power to those of other forecastors. According to Proposition 4, the returns of the hedging portfolio should outperform the returns of any other portfolios in predicting future market returns. Specifically, if we regress $R _ { M t }$ on the lagged return of any arbitrary portfolio 

<table><tr><td rowspan="2">Statistic</td><td colspan="7">Sample Period</td></tr><tr><td>Entire</td><td>67-71</td><td>72-76</td><td>77-81</td><td>82-86</td><td>87-91</td><td>92-96</td></tr><tr><td colspan="8">Hedging Portfolio Return <eq>R_{Ht}</eq></td></tr><tr><td>Mean</td><td>0.013</td><td>0.001</td><td>0.005</td><td>0.007</td><td>0.011</td><td>0.052</td><td>0.003</td></tr><tr><td>S.D.</td><td>0.198</td><td>0.029</td><td>0.039</td><td>0.045</td><td>0.046</td><td>0.477</td><td>0.013</td></tr><tr><td>Skewness</td><td>24.092</td><td>0.557</td><td>0.542</td><td>-0.330</td><td>0.270</td><td>10.200</td><td>-0.214</td></tr><tr><td>Kurtosis</td><td>747.809</td><td>1.479</td><td>7.597</td><td>0.727</td><td>1.347</td><td>130.476</td><td>0.945</td></tr><tr><td><eq>\rho_1</eq></td><td>0.017</td><td>0.199</td><td>0.141</td><td>0.196</td><td>0.125</td><td>0.004</td><td>-0.165</td></tr><tr><td><eq>\rho_2</eq></td><td>-0.058</td><td>0.018</td><td>0.006</td><td>0.071</td><td>0.036</td><td>-0.070</td><td>-0.028</td></tr><tr><td><eq>\rho_3</eq></td><td>0.104</td><td>-0.028</td><td>-0.036</td><td>-0.010</td><td>0.073</td><td>0.099</td><td>-0.003</td></tr><tr><td><eq>\rho_4</eq></td><td>0.184</td><td>0.070</td><td>0.043</td><td>0.045</td><td>-0.113</td><td>0.182</td><td>-0.010</td></tr><tr><td><eq>\rho_5</eq></td><td>-0.086</td><td>0.114</td><td>0.144</td><td>-0.026</td><td>-0.103</td><td>-0.099</td><td>-0.025</td></tr><tr><td><eq>\rho_6</eq></td><td>0.079</td><td>-0.003</td><td>0.258</td><td>-0.089</td><td>-0.093</td><td>0.072</td><td>0.020</td></tr><tr><td><eq>\rho_7</eq></td><td>0.217</td><td>0.037</td><td>0.083</td><td>-0.031</td><td>-0.173</td><td>0.218</td><td>0.098</td></tr><tr><td><eq>\rho_8</eq></td><td>-0.098</td><td>0.002</td><td>-0.124</td><td>-0.008</td><td>0.006</td><td>-0.111</td><td>-0.130</td></tr><tr><td><eq>\rho_9</eq></td><td>0.048</td><td>-0.002</td><td>-0.008</td><td>-0.060</td><td>0.011</td><td>0.041</td><td>0.006</td></tr><tr><td><eq>\rho_{10}</eq></td><td>-0.044</td><td>-0.017</td><td>0.174</td><td>-0.037</td><td>-0.117</td><td>-0.055</td><td>0.035</td></tr><tr><td colspan="8">Hedging Portfolio Dollar Return <eq>Q_{Ht}</eq></td></tr><tr><td>Mean</td><td>2.113</td><td>0.072</td><td>1.236</td><td>2.258</td><td>5.589</td><td>3.244</td><td>0.281</td></tr><tr><td>S.D.</td><td>16.836</td><td>3.639</td><td>11.059</td><td>21.495</td><td>25.423</td><td>20.906</td><td>1.845</td></tr><tr><td>Skewness</td><td>0.717</td><td>0.210</td><td>-0.144</td><td>-0.495</td><td>-0.080</td><td>2.086</td><td>0.215</td></tr><tr><td>Kurtosis</td><td>14.082</td><td>-0.085</td><td>0.500</td><td>2.286</td><td>6.537</td><td>13.286</td><td>2.048</td></tr><tr><td><eq>\rho_1</eq></td><td>0.164</td><td>0.219</td><td>0.251</td><td>0.200</td><td>0.098</td><td>0.157</td><td>-0.122</td></tr><tr><td><eq>\rho_2</eq></td><td>0.082</td><td>0.014</td><td>0.148</td><td>0.052</td><td>0.125</td><td>-0.015</td><td>-0.095</td></tr><tr><td><eq>\rho_3</eq></td><td>0.039</td><td>0.003</td><td>0.077</td><td>0.010</td><td>0.071</td><td>-0.041</td><td>0.037</td></tr><tr><td><eq>\rho_4</eq></td><td>0.021</td><td>0.061</td><td>0.084</td><td>0.127</td><td>-0.037</td><td>-0.066</td><td>0.014</td></tr><tr><td><eq>\rho_5</eq></td><td>0.036</td><td>0.116</td><td>0.102</td><td>-0.002</td><td>0.051</td><td>-0.016</td><td>-0.027</td></tr><tr><td><eq>\rho_6</eq></td><td>-0.010</td><td>-0.044</td><td>0.127</td><td>-0.094</td><td>-0.053</td><td>0.057</td><td>-0.014</td></tr><tr><td><eq>\rho_7</eq></td><td>-0.006</td><td>0.034</td><td>0.013</td><td>-0.060</td><td>-0.014</td><td>0.010</td><td>0.107</td></tr><tr><td><eq>\rho_8</eq></td><td>-0.046</td><td>0.005</td><td>-0.055</td><td>-0.028</td><td>-0.127</td><td>0.016</td><td>-0.075</td></tr><tr><td><eq>\rho_9</eq></td><td>0.027</td><td>-0.016</td><td>0.045</td><td>-0.006</td><td>0.047</td><td>0.005</td><td>-0.006</td></tr><tr><td><eq>\rho_{10}</eq></td><td>-0.001</td><td>-0.030</td><td>0.042</td><td>0.026</td><td>0.014</td><td>-0.082</td><td>0.031</td></tr></table>


Table 17: Summary statistics for the returns and dollar returns of the hedging portfolio constructed from individual stocks’ volume data using weekly returns and volume data for NYSE and AMEX stocks from 1962 to 1996.


$p ,$ the $\bar { R } ^ { 2 }$ should be less than that of (50). 

It is impractical to compare (50) to all possible portfolios, and uninformative to compare it to random portfolios. Instead, we need only make comparisons to “optimal forecast portfolios”, portfolios that are optimal forecasters of $R _ { M t }$ , since by construction, no other portfolios can have higher levels of predictability than these. The following proposition shows how to construct optimal forecasting portfolios (OFPs) (see Lo and Wang, 2001 for details): 

Proposition 7 Let $\Gamma _ { 0 }$ and $\Gamma _ { 1 }$ denote the contemporaneous and first-order autocovariance matrix of the vector of all returns. For any arbitrary target portfolio q with weights $w _ { q } =$ $( w _ { q 1 } ; \dots ; w _ { q N } )$ , define $A \equiv \Gamma _ { 0 } ^ { - 1 } \Gamma _ { 1 } w _ { q } w _ { q } ^ { \prime } \Gamma _ { 1 } ^ { \prime }$ . The optimal forecast portfolio of $w _ { q }$ is given by the normalized eigenvector of A corresponding to its largest eigenvalue. 

Since $\Gamma _ { 0 }$ and $\Gamma _ { 1 }$ are unobservable, they must be estimated using historical data. Given the large number of stocks in our sample (over 2,000 in each subperiod) and the relatively short time series in each subperiod (261 weekly observations), the standard estimators for $\Gamma _ { 0 }$ and $\Gamma _ { 1 }$ are not viable. However, it is possible to construct OFPs from a much smaller number of “basis portfolios”, and then compare the predictive power of these OFPs to the hedging portfolio. As long as the basis portfolios are not too specialized, the $\bar { R } ^ { 2 } \mathrm { s }$ are likely to be similar to those obtained from the entire universe of all stocks. 

We form several sets of basis portfolios by sorting all the J stocks into K groups of equal numbers $( K \leq J )$ according to: market capitalization, market beta, and SIC codes, and then construct value-weighted portfolios within each group.<sup>38</sup> This procedure yields K basis portfolios for which the corresponding $\Gamma _ { 0 }$ and $\Gamma _ { 1 }$ can be estimated using the portfolios’ weekly returns within each subperiod. Based on the estimated autocovariance matrices, the OFP can be computed easily according to Proposition 7. 

In selecting the number of basis portfolios K, we face the following trade-of: fewer portfolios yield better sampling properties for the covariance matrix estimators, but less desirable properties for the OFP since the predictive power of the OFP is obviously maximized when when $K = J$ . As a compromise, for the OFPs based market capitalization and market betas, we choose K to be 10, 15, 20, and 25. For the OFP based on SIC codes, we choose 13 industry groupings, described in more detail below. 

Specifically, for each five-year subperiod in which we wish to evaluate the forecast power of the hedging portfolio (the testing period), we use the previous five-year subperiod (the estimation period) to estimate the OFPs. For the OFP based on 10 market-capitalizationsorted portfolios, which we call “CAP10”, we construct 10 value-weighted portfolios each week, one for each market-capitalization decile. Market-capitalization deciles are recomputed each week, and the time series of decile returns form the 10 basis portfolio returns of CAP10, with which we can estimate $\Gamma _ { 0 }$ and $\Gamma _ { 1 }$ . To compute the OFP, we also require the weights $\omega _ { q }$ of the target portfolio, in this case the market portfolio. Since the testing period follows the estimation period, we use the market capitalization of each group in the last week of the estimation period to map the weights of the market portfolio into a 10×1-vector of weights for the 10 basis portfolios. The weights of the OFP for the basis portfolios CAP10 follow immediately from Proposition 7. The same procedure is used to form OFPs for CAP15, CAP20, and CAP25 basis portfolios. 

The OFPs of market-beta-sorted basis portfolios are constructed in a similar manner. We first estimate the market betas of individual stocks in the estimation period, sort them according to their estimated betas and then form small groups of basis portfolios, calculating value-weighted returns for each group. We consider 10, 15, 20 and 25 groups, denoted by “Beta10”, “Beta15”, and so on. The same procedure is then followed to construct the OFPs for each of these sets of basis portfolios. 

Finally, the industry portfolios are based on SIC-code groupings. The first two digits of the SIC code yield sixty to eighty industry categories, depending on the sample period, and some of categories contain only one or two stocks. On the other, the first digit yields only eight broad industry categories. As a compromise, we use a slightly more disaggregated grouping of 13 industries, given by the following correspondence:<sup>39</sup> 

# SIC Codes Description 1 1–14 Agriculture, forest, fishing, mining 2 15–19, 30, 32–34 Construction, basic materials (steel, glass, concrete, etc.) 3 20–21 Food and tobacco 4 22, 23, 25, 31, 39 Textiles, clothing, consumer products 5 24, 26–27 Logging, paper, printing, publishing 6 28 Chemicals 7 29 Petroleum 8 35–36, 38 Machinery and equipment supply, including computers 9 37, 40–47 Transportation-related 10 48–49 Utilities and telecommunications 11 50–59 Wholesale distributors, retail 12 60–69 Financial 13 70–89, 98–99 Recreation, entertainment, services, conglomerates, etc. 

Each week, stocks are sorted according to their SIC codes into the 13 categories defined above, and value-weighted returns are computed for each group, yielding the 13 basis portfolios which we denote by “SIC13”. The autocovariance matrices are then estimated and the OFP constructed according to Proposition 7. 

## Hedging Portfolio Return as A Predictor of Market Returns

Table 18 reports the results of the regressions of $R _ { M t }$ on various lagged OFP returns and on the hedging portfolios $R _ { H t }$ and $Q _ { H t }$ . For completeness, we have also included four additional regressions, with lagged value- and equal-weighted CRSP index returns, the logarithm of the reciprocal of lagged market-capitalization, and the lagged three-month constant-maturity Treasury bill return as predictors.<sup>40</sup> Table 18 show that the hedging portfolios outperforms all of the other competing portfolios in forecasting future market returns in three of the six subperiods (subperiods 2, 4, and 6). In subperiod 3, only one OFP (Beta20) outperforms the hedging portfolio, and in subperiod 5, Beta20 and SIC13’s OFPs outperform the hedging portfolio, but only marginally. And in subperiod 7, the equal-weighted CRSP index return outperforms the hedging portfolio. 

However, several caveats should be kept in mind with regard to the three subperiods in which the hedging portfolios were surpassed by one or two competing portfolios. First, in these three subperiods, the hedging portfolio still outperforms most of the other competing portfolios. Second, there is no consistent winner in these subperiods. Third, the performance of the hedging portfolios are often close to the best performer. Moreover, the best performers in these subperiods performed poorly in the other subperiods, raising the possibility that their performance might be due to sampling variation. In contrast, the hedging portfolios forecasted $R _ { M t }$ consistently in every subperiod. Indeed, among all of the regressors, the hedging portfolios were the most consistent across all six subperiods, a remarkable confirmation of the properties of the model of Sections 6.1 and 6.2.<sup>41</sup> 

<table><tr><td>Parameter</td><td>Beta10</td><td>Beta15</td><td>Beta20</td><td>Beta25</td><td>Cap10</td><td>Cap15</td><td>Cap20</td><td>Cap25</td><td>SIC13</td><td><eq>R_H</eq></td><td><eq>Q_H</eq></td><td><eq>log(Cap^{-1})</eq></td><td>VW</td><td>EW</td><td>TBill</td></tr><tr><td colspan="16">January 1967 to December 1971 (261 Weeks)</td></tr><tr><td>Intercept</td><td>0.002</td><td>0.002</td><td>0.001</td><td>0.002</td><td>0.001</td><td>0.002</td><td>0.002</td><td>0.002</td><td>0.001</td><td>0.001</td><td>0.172</td><td>0.746</td><td>0.001</td><td>0.001</td><td>—</td></tr><tr><td>t-Stat</td><td>1.330</td><td>1.360</td><td>1.150</td><td>1.430</td><td>1.240</td><td>1.520</td><td>1.400</td><td>1.380</td><td>0.920</td><td>1.270</td><td>1.200</td><td>2.330</td><td>1.240</td><td>1.250</td><td>—</td></tr><tr><td>Slope</td><td>0.103</td><td>-0.034</td><td>-0.153</td><td>0.171</td><td>-0.262</td><td>0.173</td><td>-0.039</td><td>-0.176</td><td>-0.208</td><td>0.138</td><td>0.154</td><td>0.027</td><td>0.191</td><td>0.092</td><td>—</td></tr><tr><td>t-Stat</td><td>1.810</td><td>-0.550</td><td>-1.890</td><td>1.780</td><td>-1.900</td><td>1.079</td><td>-0.240</td><td>-1.070</td><td>-2.860</td><td>3.460</td><td>3.900</td><td>2.330</td><td>3.130</td><td>2.080</td><td>—</td></tr><tr><td><eq>\overline{R}^2</eq></td><td>0.013</td><td>0.001</td><td>0.014</td><td>0.012</td><td>0.014</td><td>0.005</td><td>0.000</td><td>0.005</td><td>0.031</td><td>0.045</td><td>0.056</td><td>0.021</td><td>0.037</td><td>0.016</td><td>—</td></tr><tr><td colspan="16">January 1972 to December 1976 (261 Weeks)</td></tr><tr><td>Intercept</td><td>0.001</td><td>0.001</td><td>0.001</td><td>0.001</td><td>0.001</td><td>0.001</td><td>0.001</td><td>0.001</td><td>0.001</td><td>0.001</td><td>0.103</td><td>0.389</td><td>0.001</td><td>0.001</td><td>—</td></tr><tr><td>t-Stat</td><td>0.650</td><td>0.640</td><td>0.560</td><td>0.670</td><td>0.830</td><td>0.640</td><td>0.730</td><td>0.630</td><td>0.630</td><td>0.820</td><td>0.760</td><td>1.410</td><td>0.700</td><td>0.640</td><td>—</td></tr><tr><td>Slope</td><td>0.023</td><td>0.204</td><td>-0.315</td><td>0.079</td><td>0.235</td><td>0.098</td><td>-0.169</td><td>0.069</td><td>0.040</td><td>-0.054</td><td>-0.023</td><td>0.014</td><td>-0.003</td><td>0.048</td><td>—</td></tr><tr><td>t-Stat</td><td>0.120</td><td>1.150</td><td>-2.630</td><td>0.580</td><td>1.660</td><td>0.660</td><td>-1.180</td><td>0.430</td><td>0.430</td><td>-1.430</td><td>-1.900</td><td>1.410</td><td>-0.060</td><td>0.910</td><td>—</td></tr><tr><td><eq>\overline{R}^2</eq></td><td>0.000</td><td>0.005</td><td>0.026</td><td>0.001</td><td>0.011</td><td>0.002</td><td>0.005</td><td>0.001</td><td>0.001</td><td>0.008</td><td>0.014</td><td>0.008</td><td>0.000</td><td>0.003</td><td>—</td></tr><tr><td colspan="16">January 1977 to December 1981 (261 Weeks)</td></tr><tr><td>Intercept</td><td>0.002</td><td>0.002</td><td>0.002</td><td>0.002</td><td>0.002</td><td>0.002</td><td>0.002</td><td>0.002</td><td>0.002</td><td>0.002</td><td>0.223</td><td>0.151</td><td>0.002</td><td>0.002</td><td>—</td></tr><tr><td>t-Stat</td><td>1.750</td><td>1.600</td><td>1.800</td><td>1.640</td><td>1.770</td><td>1.760</td><td>1.800</td><td>1.530</td><td>1.749</td><td>1.500</td><td>1.370</td><td>0.720</td><td>1.570</td><td>1.380</td><td>—</td></tr><tr><td>Slope</td><td>0.007</td><td>0.071</td><td>0.065</td><td>0.033</td><td>0.075</td><td>0.003</td><td>-0.204</td><td>-0.186</td><td>0.150</td><td>0.049</td><td>0.013</td><td>0.005</td><td>0.069</td><td>0.080</td><td>—</td></tr><tr><td>t-Stat</td><td>0.040</td><td>0.870</td><td>0.460</td><td>0.510</td><td>0.230</td><td>0.010</td><td>-0.850</td><td>-0.990</td><td>1.130</td><td>1.810</td><td>1.760</td><td>0.710</td><td>1.110</td><td>1.370</td><td>—</td></tr><tr><td><eq>\overline{R}^2</eq></td><td>0.000</td><td>0.003</td><td>0.001</td><td>0.001</td><td>0.000</td><td>0.000</td><td>0.003</td><td>0.004</td><td>0.005</td><td>0.013</td><td>0.012</td><td>0.002</td><td>0.005</td><td>0.007</td><td>—</td></tr></table>


T<sub>a</sub>bl<sub>e</sub> 1 8<sub>a :</sub> F<sub>orecas</sub>t <sub>o</sub>f <sub>wee</sub>kl<sub>y mar</sub>k<sub>e</sub>t-<sub>por</sub>tf<sub>o</sub>li<sub>o re</sub>t<sub>urns</sub> b<sub>y</sub> l<sub>agge</sub>d <sub>wee</sub>kl<sub>y re</sub>t<sub>urns o</sub>f th<sub>e</sub> b<sub>e</sub>t <sub>a</sub>-<sub>sor</sub>t<sub>e</sub>d <sub>op</sub>ti<sub>ma</sub>l f<sub>orecas</sub>t <sub>por</sub>tf<sub>o</sub>li<sub>os</sub> ( O FPs) the market- capit alization-sorted O FP <sup>’</sup> s the SIC-sorted O FP the return and dollar return on the hedging p ortfolio <sub>m</sub>i<sub>nus</sub> l<sub>og</sub>-<sub>mar</sub>k<sub>e</sub>t-<sub>cap</sub>it<sub>a</sub>li<sub>za</sub>ti<sub>on</sub> th<sub>e</sub> l<sub>agge</sub>d <sub>re</sub>t<sub>urns on</sub> th<sub>e</sub> CRSP <sub>va</sub>l<sub>ue</sub>- <sub>an</sub>d <sub>equa</sub>l-<sub>we</sub>i<sub>g</sub>ht<sub>e</sub>d <sub>por</sub>tf<sub>o</sub>li<sub>os an</sub>d l<sub>agge</sub>d <sub>cons</sub>t<sub>an</sub>tmaturity (three-month) Treasury bill rates from 1 962 to 1 996 in five-year subperio ds The value of φ is 1 2 5 for the return $R _ { H }$ <sub>an</sub>d 1 5 f<sub>or</sub> th<sub>e</sub> d<sub>o</sub>ll<sub>ar re</sub>t<sub>urn</sub> $Q _ { H }$ <sub>on</sub> th<sub>e</sub> h<sub>e</sub>d<sub>g</sub>i<sub>ng por</sub>tf<sub>o</sub>li<sub>o respec</sub>ti<sub>ve</sub>l<sub>y.</sub>


<table><tr><td>Parameter</td><td>Beta10</td><td>Beta15</td><td>Beta20</td><td>Beta25</td><td>Cap10</td><td>Cap15</td><td>Cap20</td><td>Cap25</td><td>SIC13</td><td><eq>R_H</eq></td><td><eq>Q_H</eq></td><td>-Cap</td><td>VW</td><td>EW</td><td>TBill</td><td></td></tr><tr><td colspan="16">January 1982 to December 1986 (261 Weeks)</td><td></td></tr><tr><td>Intercept</td><td>0.004</td><td>0.004</td><td>0.004</td><td>0.004</td><td>0.004</td><td>0.004</td><td>0.004</td><td>0.004</td><td>0.004</td><td>0.003</td><td>0.004</td><td>0.672</td><td>0.179</td><td>0.003</td><td>0.003</td><td>0.010</td></tr><tr><td>t-Stat</td><td>3.150</td><td>3.150</td><td>3.130</td><td>3.180</td><td>3.150</td><td>3.160</td><td>3.110</td><td>3.150</td><td>2.640</td><td>3.500</td><td>3.190</td><td>1.130</td><td>2.690</td><td>2.710</td><td>1.860</td><td></td></tr><tr><td>Slope</td><td>-0.006</td><td>0.154</td><td>-0.309</td><td>0.154</td><td>-0.105</td><td>-0.054</td><td>0.142</td><td>0.099</td><td>-0.203</td><td>-0.047</td><td>-0.012</td><td>0.006</td><td>0.068</td><td>0.053</td><td>-4.053</td><td></td></tr><tr><td>t-Stat</td><td>-0.030</td><td>0.910</td><td>-1.990</td><td>1.180</td><td>-0.470</td><td>-0.220</td><td>0.740</td><td>0.530</td><td>-1.890</td><td>-1.760</td><td>-1.490</td><td>1.110</td><td>1.100</td><td>0.820</td><td>-1.212</td><td></td></tr><tr><td><eq>\overline{R}^2</eq></td><td>0.000</td><td>0.003</td><td>0.015</td><td>0.005</td><td>0.001</td><td>0.000</td><td>0.002</td><td>0.001</td><td>0.014</td><td>0.012</td><td>0.009</td><td>0.005</td><td>0.005</td><td>0.003</td><td>0.006</td><td></td></tr><tr><td colspan="16">January 1987 to December 1991 (261 Weeks)</td><td></td></tr><tr><td>Intercept</td><td>0.003</td><td>0.002</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.392</td><td>0.559</td><td>0.003</td><td>0.003</td><td>0.10</td><td></td></tr><tr><td>t-Stat</td><td>1.700</td><td>1.650</td><td>1.770</td><td>1.770</td><td>1.680</td><td>1.730</td><td>1.700</td><td>1.720</td><td>1.800</td><td>2.280</td><td>2.050</td><td>1.460</td><td>1.820</td><td>1.880</td><td>1.098</td><td></td></tr><tr><td>Slope</td><td>0.294</td><td>-0.353</td><td>0.120</td><td>0.130</td><td>-0.540</td><td>-0.062</td><td>0.072</td><td>-0.033</td><td>0.210</td><td>-0.014</td><td>-0.023</td><td>0.020</td><td>0.058</td><td>0.032</td><td>-5.598</td><td></td></tr><tr><td>t-Stat</td><td>1.580</td><td>-2.000</td><td>0.680</td><td>0.820</td><td>-2.320</td><td>-0.320</td><td>0.320</td><td>-0.190</td><td>2.320</td><td>-4.500</td><td>-2.490</td><td>1.460</td><td>0.930</td><td>0.550</td><td>-0.810</td><td></td></tr><tr><td><eq>\overline{R}^2</eq></td><td>0.010</td><td>0.015</td><td>0.002</td><td>0.003</td><td>0.021</td><td>0.000</td><td>0.000</td><td>0.000</td><td>0.021</td><td>0.073</td><td>0.024</td><td>0.008</td><td>0.003</td><td>0.001</td><td>0.003</td><td></td></tr><tr><td colspan="16">January 1992 to December 1996 (261 Weeks)</td><td></td></tr><tr><td>Intercept</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.416</td><td>-0.107</td><td>0.003</td><td>0.003</td><td>-0.003</td><td></td></tr><tr><td>t-Stat</td><td>3.170</td><td>3.120</td><td>3.110</td><td>3.060</td><td>3.060</td><td>3.130</td><td>3.120</td><td>3.170</td><td>3.130</td><td>3.700</td><td>3.510</td><td>-0.780</td><td>3.710</td><td>4.000</td><td>-0.881</td><td></td></tr><tr><td>Slope</td><td>0.118</td><td>-0.009</td><td>0.090</td><td>-0.095</td><td>-0.191</td><td>-0.040</td><td>0.033</td><td>-0.074</td><td>-0.047</td><td>-0.194</td><td>-0.153</td><td>-0.004</td><td>-0.163</td><td>-0.192</td><td>7.280</td><td></td></tr><tr><td>t-Stat</td><td>1.060</td><td>-0.080</td><td>0.930</td><td>-0.850</td><td>-1.090</td><td>-0.270</td><td>0.240</td><td>-0.550</td><td>-0.700</td><td>-2.910</td><td>-2.410</td><td>-0.800</td><td>-2.710</td><td>-3.320</td><td>1.661</td><td></td></tr><tr><td><eq>\overline{R}^2</eq></td><td>0.004</td><td>0.000</td><td>0.003</td><td>0.003</td><td>0.005</td><td>0.000</td><td>0.000</td><td>0.001</td><td>0.002</td><td>0.032</td><td>0.022</td><td>0.003</td><td>0.028</td><td>0.041</td><td>0.011</td><td></td></tr></table>


Table 1 8b : (continued) <sub>.</sub>


## 6.5 The Hedging-Portfolio Return as a Risk Factor

To evaluate the success of the hedging-portfolio return as a risk factor in the cross section of expected returns, we implement a slightly modified version of the well-known regression tests outlined in Fama and MacBeth (1973). The basic approach is the same: form portfolios sorted by an estimated parameter such as market beta coeficients in one time period (the “portfolio-formation period”), estimate betas for those same portfolios in a second nonoverlapping time period (the “estimation period”), and perform a cross-sectional regression test for the explanatory power of those betas using the returns of a third non-overlapping time period (the “testing period”). However, in contrast to Fama and MacBeth (1973), we use weekly instead of monthly returns, and our portfolio-formation, estimation, and testing periods are five years each.<sup>42</sup> 

Specifically, we run the following bivariate regression for each security in the portfolioformation period, using only those securities that exist in all three periods:<sup>43</sup> 

$$
R _ {j t} = \alpha_ {j} + \beta_ {j} ^ {M} R _ {M t} + \beta_ {j} ^ {H} R _ {H t} + \varepsilon_ {i t}\tag{51}
$$

where $R _ { M t }$ is the return on the CRSP value-weighted index and $R _ { H t }$ is the return on the hedging portfolio. Using the estimated coeficients $\{ \widehat { \beta } _ { i } ^ { M } \}$ and $\{ \widehat { \beta } _ { i } ^ { H } \}$ , we perform a double sort among the individual securities in the estimation period, creating 100 portfolios corresponding to the deciles of the estimated market and hedging-portfolio betas. We re-estimate the two betas for each of these 100 portfolios in the estimation period, and use these estimated betas as regressors in the testing period, for which we estimate the following cross-sectional regression: 

$$
R _ {p t} = \gamma_ {0 t} + \gamma_ {1 t} \widehat {\beta} _ {p} ^ {M} + \gamma_ {2 t} \widehat {\beta} _ {p} ^ {H} + \eta_ {p t}\tag{52}
$$

where $R _ { p t }$ is the equal-weighted portfolio return for securities in portfolio $p , p = 1 , \ldots , 1 0 0$ 2 constructed from the double-sorted rankings of the portfolio-estimation period, and $\widehat { \beta } _ { p t } ^ { M }$ and $\widehat { \beta } _ { p t } ^ { H }$ are the market and hedging-portfolio returns, respectively, of portfolio p obtained from the estimation period. This cross-sectional regression is estimated for each of the 261 weeks in the five-year testing period, yielding a time series of coeficients {γ<sub>0t</sub>}, $\{ \widehat { \gamma } _ { 1 t } \}$ , and $\{ \widehat { \gamma } _ { 2 t } \}$ Summary statistics for these coeficients and their diagnostics are then reported, and this entire procedure is repeated by incrementing the portfolio-formation, estimation, and testing periods by five years. We then perform the same analysis for the hedge-portfolio dollar-return series $\left\{ Q _ { H t } \right\}$ 

Because we use weekly instead of monthly data, it may be dificult to compare our results to other cross-sectional tests in the extant literature, e.g., Fama and French (1992). Therefore, we apply our procedure to three other benchmark models: the standard CAPM in which $R _ { M t }$ is the only regressor in (51) and 100 market-beta-sorted portfolios constructed, a two-factor model in which the hedging-portfolio return factor is replaced by a “small-minusbig capitalization” or “SMB” portfolio return factor as in Fama and French (1993), and a two-factor model in which the hedging-portfolio return factor is replaced by the OFP return factor described in Section $6 . 4 .$ .<sup>44</sup> Table 19 reports the correlations between the diferent portfolio return factors, returns on CRSP value- and equal-weighted portfolios, return and dollar return on the hedging portfolio, returns on the SMB portfolio and, OFP, Beta20, and the two turnover indices. 

Table 20 summarizes the results of all of these cross-sectional regression tests for each of the five testing periods from 1972 to 1996. In the first subpanel, corresponding to the first testing period from 1972 to 1976, there is little evidence in support of the CAPM or any of the two-factor models estimated.<sup>45</sup> For example, the first three rows show that the timeseries average of the market-beta coeficients, $\{ \widehat { \gamma } _ { 1 t } \}$ , is 0.000, with a t-statistic of 0.348 and an average $\bar { R } ^ { 2 }$ b<sub>of</sub> <sub>10.0%.</sub>46 <sub>When</sub> <sub>the</sub> <sub>hedging-portfolio</sub> <sub>beta</sub> $\widehat { \beta } _ { t } ^ { H }$ is added to the regression, the $\bar { R } ^ { 2 }$ does increase to 14.3% but the average of the coeficients $\left\{ \hat { \gamma } _ { 2 t } \right\}$ is −0.002 with a t-statistic of −0.820. The average market-beta coeficient is still insignificant, but it has now switched sign. The results for the two-factor model with the hedging-portfolio dollar-return factor and the two-factor model with the SMB factor are similar. 

<table><tr><td></td><td><eq>R_{VWt}</eq></td><td><eq>R_{EWt}</eq></td><td><eq>R_{Ht}</eq></td><td><eq>Q_{Ht}</eq></td><td><eq>R_{SMBt}</eq></td><td><eq>R_{OFPt}</eq></td><td><eq>\tau_t^{EW}</eq></td><td><eq>\tau_t^{SW}</eq></td></tr><tr><td colspan="9">July 1962 to December 1996 (1,800 Weeks)</td></tr><tr><td><eq>R_{VWt}</eq></td><td>100.0</td><td>88.7</td><td>-13.2</td><td>15.6</td><td>14.0</td><td>-26.9</td><td>10.6</td><td>8.1</td></tr><tr><td><eq>R_{EWt}</eq></td><td>88.7</td><td>100.0</td><td>-15.8</td><td>4.6</td><td>53.5</td><td>-25.3</td><td>12.6</td><td>5.5</td></tr><tr><td><eq>R_{Ht}</eq></td><td>-13.2</td><td>-15.8</td><td>100.0</td><td>40.3</td><td>-10.7</td><td>-11.0</td><td>14.9</td><td>16.8</td></tr><tr><td><eq>Q_{Ht}</eq></td><td>15.6</td><td>4.6</td><td>40.3</td><td>100.0</td><td>-13.3</td><td>-6.7</td><td>7.5</td><td>9.9</td></tr><tr><td><eq>R_{SMBt}</eq></td><td>14.0</td><td>53.5</td><td>-10.7</td><td>-13.3</td><td>100.0</td><td>-4.8</td><td>4.6</td><td>-5.8</td></tr><tr><td><eq>R_{OFPt}</eq></td><td>-26.9</td><td>-25.3</td><td>-11.0</td><td>-6.7</td><td>-4.8</td><td>100.0</td><td>-4.9</td><td>-2.4</td></tr><tr><td><eq>\tau_t^{EW}</eq></td><td>10.6</td><td>12.6</td><td>14.9</td><td>7.5</td><td>4.6</td><td>-4.9</td><td>100.0</td><td>86.2</td></tr><tr><td><eq>\tau_t^{SW}</eq></td><td>8.1</td><td>5.5</td><td>16.8</td><td>9.9</td><td>-5.8</td><td>-2.4</td><td>86.2</td><td>100.0</td></tr><tr><td colspan="9">January 1967 to December 1971 (261 Weeks)</td></tr><tr><td><eq>R_{VWt}</eq></td><td>100.0</td><td>92.6</td><td>95.6</td><td>91.5</td><td>62.7</td><td>-76.2</td><td>19.1</td><td>26.3</td></tr><tr><td><eq>R_{EWt}</eq></td><td>92.6</td><td>100.0</td><td>92.3</td><td>88.4</td><td>84.5</td><td>-71.9</td><td>32.8</td><td>36.9</td></tr><tr><td><eq>R_{Ht}</eq></td><td>95.6</td><td>92.3</td><td>100.0</td><td>97.4</td><td>70.7</td><td>-65.0</td><td>22.0</td><td>29.6</td></tr><tr><td><eq>Q_{Ht}</eq></td><td>91.5</td><td>88.4</td><td>97.4</td><td>100.0</td><td>69.8</td><td>-60.1</td><td>22.9</td><td>29.8</td></tr><tr><td><eq>R_{SMBt}</eq></td><td>62.7</td><td>84.5</td><td>70.7</td><td>69.8</td><td>100.0</td><td>-46.6</td><td>39.7</td><td>38.2</td></tr><tr><td><eq>R_{OFPt}</eq></td><td>-76.2</td><td>-71.9</td><td>-65.0</td><td>-60.1</td><td>-46.6</td><td>100.0</td><td>-7.5</td><td>-10.4</td></tr><tr><td><eq>\tau_t^{EW}</eq></td><td>19.1</td><td>32.8</td><td>22.0</td><td>22.9</td><td>39.7</td><td>-7.5</td><td>100.0</td><td>93.1</td></tr><tr><td><eq>\tau_t^{SW}</eq></td><td>26.3</td><td>36.9</td><td>29.6</td><td>29.8</td><td>38.2</td><td>-10.4</td><td>93.1</td><td>100.0</td></tr><tr><td colspan="9">January 1972 to December 1977 (261 Weeks)</td></tr><tr><td><eq>R_{VWt}</eq></td><td>100.0</td><td>84.5</td><td>13.3</td><td>14.2</td><td>-6.9</td><td>-59.5</td><td>19.0</td><td>27.6</td></tr><tr><td><eq>R_{EWt}</eq></td><td>84.5</td><td>100.0</td><td>-11.5</td><td>-18.2</td><td>44.1</td><td>-45.4</td><td>24.3</td><td>35.4</td></tr><tr><td><eq>R_{Ht}</eq></td><td>13.3</td><td>-11.5</td><td>100.0</td><td>86.6</td><td>-55.2</td><td>-8.3</td><td>-2.8</td><td>-1.9</td></tr><tr><td><eq>Q_{Ht}</eq></td><td>14.2</td><td>-18.2</td><td>86.6</td><td>100.0</td><td>-70.4</td><td>-11.6</td><td>-4.1</td><td>-4.2</td></tr><tr><td><eq>R_{SMBt}</eq></td><td>-6.9</td><td>44.1</td><td>-55.2</td><td>-70.4</td><td>100.0</td><td>15.0</td><td>11.3</td><td>16.3</td></tr><tr><td><eq>R_{OFPt}</eq></td><td>-59.5</td><td>-45.4</td><td>-8.3</td><td>-11.6</td><td>15.0</td><td>100.0</td><td>-6.7</td><td>-12.4</td></tr><tr><td><eq>\tau_t^{EW}</eq></td><td>19.0</td><td>24.3</td><td>-2.8</td><td>-4.1</td><td>11.3</td><td>-6.7</td><td>100.0</td><td>87.3</td></tr><tr><td><eq>\tau_t^{SW}</eq></td><td>27.6</td><td>35.4</td><td>-1.9</td><td>-4.2</td><td>16.3</td><td>-12.4</td><td>87.3</td><td>100.0</td></tr><tr><td colspan="9">January 1977 to December 1981 (261 Weeks)</td></tr><tr><td><eq>R_{VWt}</eq></td><td>100.0</td><td>90.2</td><td>85.4</td><td>82.3</td><td>23.8</td><td>22.6</td><td>12.6</td><td>15.7</td></tr><tr><td><eq>R_{EWt}</eq></td><td>90.2</td><td>100.0</td><td>88.5</td><td>82.0</td><td>59.3</td><td>12.7</td><td>7.6</td><td>8.1</td></tr><tr><td><eq>R_{Ht}</eq></td><td>85.4</td><td>88.5</td><td>100.0</td><td>87.1</td><td>51.2</td><td>9.3</td><td>7.6</td><td>8.6</td></tr><tr><td><eq>Q_{Ht}</eq></td><td>82.3</td><td>82.0</td><td>87.1</td><td>100.0</td><td>49.0</td><td>10.4</td><td>11.0</td><td>12.3</td></tr><tr><td><eq>R_{SMBt}</eq></td><td>23.8</td><td>59.3</td><td>51.2</td><td>49.0</td><td>100.0</td><td>-16.7</td><td>-8.3</td><td>-12.7</td></tr><tr><td><eq>R_{OFPt}</eq></td><td>22.6</td><td>12.7</td><td>9.3</td><td>10.4</td><td>-16.7</td><td>100.0</td><td>10.7</td><td>10.4</td></tr><tr><td><eq>\tau_t^{EW}</eq></td><td>12.6</td><td>7.6</td><td>7.6</td><td>11.0</td><td>-8.3</td><td>10.7</td><td>100.0</td><td>94.9</td></tr><tr><td><eq>\tau_t^{SW}</eq></td><td>15.7</td><td>8.1</td><td>8.6</td><td>12.3</td><td>-12.7</td><td>10.4</td><td>94.9</td><td>100.0</td></tr><tr><td colspan="9">January 1982 to December 1986 (261 Weeks)</td></tr><tr><td><eq>R_{VWt}</eq></td><td>100.0</td><td>92.1</td><td>-17.0</td><td>6.1</td><td>-2.8</td><td>-23.5</td><td>27.1</td><td>28.6</td></tr><tr><td><eq>R_{EWt}</eq></td><td>92.1</td><td>100.0</td><td>-34.1</td><td>-10.2</td><td>30.6</td><td>-30.6</td><td>36.0</td><td>31.6</td></tr><tr><td><eq>R_{Ht}</eq></td><td>-17.0</td><td>-34.1</td><td>100.0</td><td>73.3</td><td>-54.5</td><td>13.5</td><td>-12.2</td><td>-7.8</td></tr><tr><td><eq>Q_{Ht}</eq></td><td>6.1</td><td>-10.2</td><td>73.3</td><td>100.0</td><td>-41.1</td><td>8.0</td><td>1.3</td><td>4.2</td></tr><tr><td><eq>R_{SMBt}</eq></td><td>-2.8</td><td>30.6</td><td>-54.5</td><td>-41.1</td><td>100.0</td><td>-15.9</td><td>19.9</td><td>6.5</td></tr><tr><td><eq>R_{OFPt}</eq></td><td>-23.5</td><td>-30.6</td><td>13.5</td><td>8.0</td><td>-15.9</td><td>100.0</td><td>-20.7</td><td>-17.9</td></tr><tr><td><eq>\tau_t^{EW}</eq></td><td>27.1</td><td>36.0</td><td>-12.2</td><td>1.3</td><td>19.9</td><td>-20.7</td><td>100.0</td><td>93.2</td></tr><tr><td><eq>\tau_t^{SW}</eq></td><td>28.6</td><td>31.6</td><td>-7.8</td><td>4.2</td><td>6.5</td><td>-17.9</td><td>93.2</td><td>100.0</td></tr><tr><td colspan="9">January 1987 to December 1991 (261 Weeks)</td></tr><tr><td><eq>R_{VWt}</eq></td><td>100.0</td><td>91.2</td><td>-40.4</td><td>-36.0</td><td>8.1</td><td>18.9</td><td>-15.0</td><td>-17.0</td></tr><tr><td><eq>R_{EWt}</eq></td><td>91.2</td><td>100.0</td><td>-44.3</td><td>-46.5</td><td>44.6</td><td>36.3</td><td>-16.7</td><td>-20.9</td></tr><tr><td><eq>R_{Ht}</eq></td><td>-40.4</td><td>-44.3</td><td>100.0</td><td>58.1</td><td>-23.8</td><td>-26.2</td><td>43.2</td><td>43.7</td></tr><tr><td><eq>Q_{Ht}</eq></td><td>-36.0</td><td>-46.5</td><td>58.1</td><td>100.0</td><td>-37.1</td><td>-32.8</td><td>25.3</td><td>24.0</td></tr><tr><td><eq>R_{SMBt}</eq></td><td>8.1</td><td>44.6</td><td>-23.8</td><td>-37.1</td><td>100.0</td><td>45.1</td><td>-11.4</td><td>-16.9</td></tr><tr><td><eq>R_{OFPt}</eq></td><td>18.9</td><td>36.3</td><td>-26.2</td><td>-32.8</td><td>45.1</td><td>100.0</td><td>-18.5</td><td>-19.7</td></tr><tr><td><eq>\tau_t^{EW}</eq></td><td>-15.0</td><td>-16.7</td><td>43.2</td><td>25.3</td><td>-11.4</td><td>-18.5</td><td>100.0</td><td>94.7</td></tr><tr><td><eq>\tau_t^{SW}</eq></td><td>-17.0</td><td>-20.9</td><td>43.7</td><td>24.0</td><td>-16.9</td><td>-19.7</td><td>94.7</td><td>100.0</td></tr><tr><td colspan="9">January 1992 to December 1996 (261 Weeks)</td></tr><tr><td><eq>R_{VWt}</eq></td><td>100.0</td><td>84.3</td><td>95.5</td><td>66.5</td><td>-1.2</td><td>-13.1</td><td>15.5</td><td>10.4</td></tr><tr><td><eq>R_{EWt}</eq></td><td>84.3</td><td>100.0</td><td>73.2</td><td>40.5</td><td>46.1</td><td>-5.2</td><td>18.2</td><td>5.4</td></tr><tr><td><eq>R_{Ht}</eq></td><td>95.5</td><td>73.2</td><td>100.0</td><td>84.8</td><td>-19.7</td><td>-8.7</td><td>15.3</td><td>11.2</td></tr><tr><td><eq>Q_{Ht}</eq></td><td>66.5</td><td>40.5</td><td>84.8</td><td>100.0</td><td>-41.6</td><td>0.2</td><td>12.0</td><td>9.2</td></tr><tr><td><eq>R_{SMBt}</eq></td><td>-1.2</td><td>46.1</td><td>-19.7</td><td>-41.6</td><td>100.0</td><td>11.3</td><td>3.0</td><td>-10.1</td></tr><tr><td><eq>R_{OFPt}</eq></td><td>-13.1</td><td>-5.2</td><td>-8.7</td><td>0.2</td><td>11.3</td><td>100.0</td><td>-3.0</td><td>-3.3</td></tr><tr><td><eq>\tau_t^{EW}</eq></td><td>15.5</td><td>18.2</td><td>15.3</td><td>12.0</td><td>3.0</td><td>-3.0</td><td>100.0</td><td>92.7</td></tr><tr><td><eq>\tau_t^{SW}</eq></td><td>10.4</td><td>5.4</td><td>11.2</td><td>9.2</td><td>-10.1</td><td>-3.3</td><td>92.7</td><td>100.0</td></tr></table>


Table 19a: Correlation matrix for weekly returns on the CRSP value-weighted index $\left( R _ { V W t } \right)$ the CRSP equal-weighted index $( R _ { E W t } )$ , the hedging-portfolio return $( R _ { H t } )$ , the hedgingportfolio dollar-return $\left( Q _ { H t } \right)$ , the return of the small-minus-big capitalization stocks portfolio $\left( R _ { S M B t } \right)$ , the return return $R _ { O F P t }$ of the optimal-forecast portfolio (OFP) for the set of 25 market-beta-sorted basis portfolios, and the equal-weighted and share-weighted turnover indices $( \tau _ { t } ^ { E W }$ and $\tau _ { t } ^ { S W } )$ , using CRSP weekly returns and volume data for NYSE and AMEX stocks from 1962 to 1996 and in five-year subperiods.


In the second testing period, both specifications with the hedging-portfolio factor exhibit statistically significant means for the hedging-portfolio betas, with average coeficients and t-statistics of −0.012 and −3.712 for the hedging-portfolio return factor and −1.564 and −4.140 for the hedging-portfolio dollar-return factor, respectively. In contrast, the marketbeta coeficients are not significant in either of these specifications, and are also of the wrong sign. The only other specification with a significant mean coeficient is the two-factor model with SMB as the second factor, with an average coeficient of 0.299 for the SMB factor and a t-statistic of 4.433. 

For the three remaining test periods, the only specifications with any statistically significant factors are the SMB and MPP two-factor models in the 1992–1996 testing period. However, the $\bar { R } ^ { 2 } \mathrm { s }$ in the last two testing periods are substantially lower than in the earlier periods, perhaps reflecting the greater volatility of equity returns in recent years. 

Overall, the results do not provide overwhelming support for any factor in explaining the cross-sectional variation of expected returns. There is, of course, the ubiquitous problem of lack of power in these cross-sectional regression tests, hence we should not be surprised that no single factor stands out.<sup>47</sup> However, the point estimates of the cross-sectional regressions show that the hedging-portfolio factor is comparable in magnitude and in performance to other commonly proposed factors. 

## 6.6 Updated Empirical Results

Since writing the initial draft of this chapter, we have updated the empirical results of Sections 6.4 and 6.5 with data from 1997 to 2004, yielding true out-of-sample tests of our intertemporal asset-pricing model in Tables 21–23. Table 21 shows that the hedging portfolios continue to outperform the OFPs in the new subperiods, confirming the predictive power of the hedging portfolios as specified by Proposition 4. 

Table 22 is an update of Table 19, containing correlation matrices of the factors used in Table 23’s updated cross-sectional tests of the explanatory power of the hedging portfolios (only three subperiods are included to conserve space). The cross-sectional regressions in Table 23 contain one additional factor beyond those of Table 20: the Fama and French (1992) high-minus-low (HML) book-to-market factor. 

<table><tr><td>Model</td><td>Statistic</td><td><eq>\hat{\gamma}_{0t}</eq></td><td><eq>\hat{\gamma}_{1t}</eq></td><td><eq>\hat{\gamma}_{2t}</eq></td><td><eq>\overline{R}^{2}</eq>(%)</td></tr><tr><td colspan="6">January 1972 to December 1976 (261 Weeks)</td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \epsilon_{pt}</eq></td><td>Mean:</td><td>0.002</td><td>0.000</td><td></td><td>10.0</td></tr><tr><td>S.D.:</td><td>0.015</td><td>0.021</td><td></td><td>10.9</td></tr><tr><td>t-Stat:</td><td>1.639</td><td>0.348</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HR} + \epsilon_{pt}</eq><eq>(\phi = 1.25)</eq></td><td>Mean:</td><td>0.004</td><td>-0.002</td><td>-0.002</td><td>14.3</td></tr><tr><td>S.D.:</td><td>0.035</td><td>0.035</td><td>0.037</td><td>10.9</td></tr><tr><td>t-Stat:</td><td>2.040</td><td>-1.047</td><td>-0.820</td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HQ} + \epsilon_{pt}</eq><eq>(\phi = 1.50)</eq></td><td>Mean:</td><td>0.004</td><td>-0.002</td><td>-0.104</td><td>15.5</td></tr><tr><td>S.D.:</td><td>0.032</td><td>0.034</td><td>3.797</td><td>10.9</td></tr><tr><td>t-Stat:</td><td>2.162</td><td>-1.081</td><td>-0.442</td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \epsilon_{pt}</eq></td><td>Mean:</td><td>0.001</td><td>0.000</td><td>0.063</td><td>12.1</td></tr><tr><td>S.D.:</td><td>0.014</td><td>0.024</td><td>1.142</td><td>10.8</td></tr><tr><td>t-Stat:</td><td>1.424</td><td>0.217</td><td>0.898</td><td></td></tr><tr><td colspan="6">January 1977 to December 1981 (261 Weeks)</td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \epsilon_{pt}</eq></td><td>Mean:</td><td>0.001</td><td>0.003</td><td></td><td>11.7</td></tr><tr><td>S.D.:</td><td>0.011</td><td>0.022</td><td></td><td>12.8</td></tr><tr><td>t-Stat:</td><td>1.166</td><td>2.566</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HR} + \epsilon_{pt}</eq><eq>(\phi = 4.75)</eq></td><td>Mean:</td><td>0.003</td><td>-0.001</td><td>-0.012</td><td>13.1</td></tr><tr><td>S.D.:</td><td>0.014</td><td>0.020</td><td>0.051</td><td>12.4</td></tr><tr><td>t-Stat:</td><td>3.748</td><td>-0.902</td><td>-3.712</td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HQ} + \epsilon_{pt}</eq><eq>(\phi = 4.25)</eq></td><td>Mean:</td><td>0.003</td><td>-0.001</td><td>-1.564</td><td>12.5</td></tr><tr><td>S.D.:</td><td>0.013</td><td>0.020</td><td>6.104</td><td>12.2</td></tr><tr><td>t-Stat:</td><td>3.910</td><td>-0.754</td><td>-4.140</td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \epsilon_{pt}</eq></td><td>Mean:</td><td>0.001</td><td>0.000</td><td>0.299</td><td>14.9</td></tr><tr><td>S.D.:</td><td>0.011</td><td>0.017</td><td>1.088</td><td>13.4</td></tr><tr><td>t-Stat:</td><td>2.251</td><td>-0.164</td><td>4.433</td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{OFP} + \epsilon_{pt}</eq></td><td>Mean:</td><td>0.003</td><td>0.001</td><td>0.001</td><td>14.1</td></tr><tr><td>S.D.:</td><td>0.018</td><td>0.023</td><td>0.036</td><td>11.6</td></tr><tr><td>t-Stat:</td><td>2.735</td><td>0.843</td><td>0.632</td><td></td></tr></table>


Table 20a: Cross-sectional regression tests of various linear factor models along the lines of Fama and MacBeth (1973) using weekly returns for NYSE and AMEX stocks from 1962 to 1996, five-year subperiods for the portfolio-formation, estimation, and testing periods, and 100 portfolios in the cross-sectional regressions each week. The five linear-factor models are: the standard CAPM $( { \widehat { \beta } } _ { p } ^ { M } )$ , and four two-factor models in which the first factor is the market beta and the second factors are, respectively, the hedging portfolio return beta $( \widehat { \beta } _ { p } ^ { H R } )$ , the hedging portfolio dollar-return beta $( \widehat { \beta } _ { p } ^ { H Q } )$ , the beta of a small-minus-big cap portfolio return $( \widehat { \beta } _ { p } ^ { S M B } )$ , and the beta of the optimal forecast portfolio based on a set of 25 market-beta-sorted basis portfolios $( \widehat { \beta } _ { p } ^ { O F P } )$ 


<table><tr><td>Model</td><td>Statistic</td><td><eq>\hat{\gamma}_{0t}</eq></td><td><eq>\hat{\gamma}_{1t}</eq></td><td><eq>\hat{\gamma}_{2t}</eq></td><td><eq>\overline{R}^{2}</eq>(%)</td></tr><tr><td colspan="6">January 1982 to December 1986 (261 Weeks)</td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \epsilon_{pt}</eq></td><td>Mean:</td><td>0.006</td><td>-0.001</td><td></td><td>9.4</td></tr><tr><td>S.D.:</td><td>0.011</td><td>0.019</td><td></td><td>11.1</td></tr><tr><td>t-Stat:</td><td>8.169</td><td>-1.044</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HR} + \epsilon_{pt}</eq><eq>(\phi = 1.75)</eq></td><td>Mean:</td><td>0.006</td><td>-0.001</td><td>-0.006</td><td>9.6</td></tr><tr><td>S.D.:</td><td>0.011</td><td>0.020</td><td>0.055</td><td>9.4</td></tr><tr><td>t-Stat:</td><td>8.390</td><td>-0.780</td><td>-1.732</td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HQ} + \epsilon_{pt}</eq><eq>(\phi = 2.00)</eq></td><td>Mean:</td><td>0.006</td><td>-0.002</td><td>-0.740</td><td>10.4</td></tr><tr><td>S.D.:</td><td>0.011</td><td>0.019</td><td>19.874</td><td>9.5</td></tr><tr><td>t-Stat:</td><td>8.360</td><td>-1.297</td><td>-0.602</td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \epsilon_{pt}</eq></td><td>Mean:</td><td>0.005</td><td>-0.002</td><td>0.038</td><td>10.0</td></tr><tr><td>S.D.:</td><td>0.012</td><td>0.019</td><td>1.154</td><td>8.4</td></tr><tr><td>t-Stat:</td><td>7.451</td><td>-1.264</td><td>0.531</td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{OFP} + \epsilon_{pt}</eq></td><td>Mean:</td><td>0.005</td><td>-0.001</td><td>0.000</td><td>11.7</td></tr><tr><td>S.D.:</td><td>0.011</td><td>0.020</td><td>0.021</td><td>10.8</td></tr><tr><td>t-Stat:</td><td>7.545</td><td>-0.818</td><td>0.199</td><td></td></tr><tr><td colspan="6">January 1987 to December 1991 (261 Weeks)</td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \epsilon_{pt}</eq></td><td>Mean:</td><td>0.002</td><td>0.000</td><td></td><td>5.9</td></tr><tr><td>S.D.:</td><td>0.013</td><td>0.023</td><td></td><td>8.7</td></tr><tr><td>t-Stat:</td><td>2.649</td><td>0.204</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HR} + \epsilon_{pt}</eq><eq>(\phi = 47)</eq></td><td>Mean:</td><td>0.002</td><td>0.000</td><td>0.000</td><td>5.4</td></tr><tr><td>S.D.:</td><td>0.016</td><td>0.019</td><td>0.060</td><td>6.1</td></tr><tr><td>t-Stat:</td><td>2.254</td><td>0.105</td><td>0.132</td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HQ} + \epsilon_{pt}</eq><eq>(\phi = 20)</eq></td><td>Mean:</td><td>0.002</td><td>0.000</td><td>0.189</td><td>6.0</td></tr><tr><td>S.D.:</td><td>0.016</td><td>0.019</td><td>18.194</td><td>6.7</td></tr><tr><td>t-Stat:</td><td>2.434</td><td>-0.147</td><td>0.168</td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \epsilon_{pt}</eq></td><td>Mean:</td><td>0.003</td><td>0.000</td><td>-0.075</td><td>7.8</td></tr><tr><td>S.D.:</td><td>0.014</td><td>0.020</td><td>1.235</td><td>8.2</td></tr><tr><td>t-Stat:</td><td>3.101</td><td>0.158</td><td>-0.979</td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{OFP} + \epsilon_{pt}</eq></td><td>Mean:</td><td>0.003</td><td>-0.001</td><td>0.000</td><td>6.4</td></tr><tr><td>S.D.:</td><td>0.015</td><td>0.021</td><td>0.021</td><td>7.3</td></tr><tr><td>t-Stat:</td><td>2.731</td><td>-0.385</td><td>-0.234</td><td></td></tr></table>

Table 20b: (continued). 

<table><tr><td>Model</td><td>Statistic</td><td><eq>\hat{\gamma}_{0t}</eq></td><td><eq>\hat{\gamma}_{1t}</eq></td><td><eq>\hat{\gamma}_{2t}</eq></td><td><eq>\overline{R}^{2}</eq>(%)</td></tr><tr><td colspan="6">January 1992 to December 1996 (261 Weeks)</td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \epsilon_{pt}</eq></td><td>Mean:</td><td>0.002</td><td>0.001</td><td></td><td>5.7</td></tr><tr><td>S.D.:</td><td>0.013</td><td>0.020</td><td></td><td>7.7</td></tr><tr><td>t-Stat:</td><td>2.679</td><td>1.178</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HR} + \epsilon_{pt}</eq><eq>(\phi = 38)</eq></td><td>Mean:</td><td>0.002</td><td>0.001</td><td>-0.004</td><td>6.9</td></tr><tr><td>S.D.:</td><td>0.013</td><td>0.020</td><td>0.091</td><td>6.8</td></tr><tr><td>t-Stat:</td><td>2.785</td><td>1.164</td><td>-0.650</td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HQ} + \epsilon_{pt}</eq><eq>(\phi = 27)</eq></td><td>Mean:</td><td>0.003</td><td>0.000</td><td>-1.584</td><td>6.2</td></tr><tr><td>S.D.:</td><td>0.015</td><td>0.022</td><td>12.992</td><td>6.6</td></tr><tr><td>t-Stat:</td><td>3.279</td><td>-0.178</td><td>-1.970</td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \epsilon_{pt}</eq></td><td>Mean:</td><td>0.002</td><td>0.001</td><td>0.154</td><td>6.7</td></tr><tr><td>S.D.:</td><td>0.015</td><td>0.019</td><td>1.157</td><td>7.0</td></tr><tr><td>t-Stat:</td><td>1.653</td><td>0.861</td><td>2.147</td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{OFP} + \epsilon_{pt}</eq></td><td>Mean:</td><td>0.001</td><td>0.002</td><td>0.002</td><td>7.9</td></tr><tr><td>S.D.:</td><td>0.016</td><td>0.020</td><td>0.015</td><td>7.4</td></tr><tr><td>t-Stat:</td><td>0.895</td><td>1.236</td><td>2.407</td><td></td></tr></table>

The results in Table 23 for the original subperiods in Table 20 are not much diferent from the results without the HML factor—in the first subpanel, which corresponds to the first testing period from 1972 to 1976, there is little evidence in support of either the CAPM or any of the other linear models estimated. When the hedging portfolio beta $\widehat { \beta } _ { t } ^ { H }$ is added to the regression, the $\bar { R } ^ { 2 }$ increases to 14.3% but the average of the coeficients $\left\{ \hat { \gamma } _ { 2 t } \right\}$ is −0.2% with a t-statistic of −0.82. The average market beta coeficient is still insignificant, but it has now switched sign. The results for the two-factor model with the hedging portfolio dollar return factor and the two-factor model with the SMB factor are similar. The three-factor model is even less successful, with statistically insignificant coeficients close to 0.0% and an average $R ^ { 2 }$ of 8.8%. 

In the second testing period, both specifications with the hedging portfolio factor exhibit statistically significant means for the hedging portfolio betas, with average coeficients and t-statistics of −1.2% and −3.71 for the hedging-portfolio return factor and −1.56 and −4.14 for the hedging portfolio dollar return factor, respectively. The market beta coeficients are not significant in either of these specifications, and are also of the wrong sign. The only other specifications with a significant mean coeficient are the two-factor model with SMB as the second factor (with an average coeficient of 29.9% for the SMB factor and a t-statistic of 4.43), and the three-factor model in which the SMB factor is also significant (an average coeficient of 0.3% and a t-statistic of 4.61). 

For the five remaining test periods, the only specifications with any statistically significant factors are the SMB and OFP two-factor models in the 1992 to 1996 testing period (though the hedging portfolio dollar return factor is close to significant in the 1997 to 2001 subperiod). However, the $\bar { R } ^ { 2 } \mathrm { s }$ in the last four testing periods are substantially lower than in the earlier periods, perhaps reflecting the greater volatility of equity returns in recent years. 

As before, no single factor is particularly compelling in explaining the cross-sectional variation of expected returns, but the point estimates of the cross-sectional regressions show that the hedging-portfolio factor is comparable both in magnitude and in performance to other commonly proposed factors, and we continue to be optimistic regarding its relevance for intertemporal asset-pricing models. 

<table><tr><td>Parameter</td><td>Beta10</td><td>Beta15</td><td>Beta20</td><td>Beta25</td><td>Cap10</td><td>Cap15</td><td>Cap20</td><td>Cap25</td><td>SIC13</td><td><eq>R_H</eq></td><td><eq>Q_H</eq></td><td>-Cap</td><td>VW</td><td>EW</td><td>TBill</td></tr><tr><td colspan="16">January 1997 to December 2001 (261 Weeks)</td></tr><tr><td>Intercept</td><td>0.006</td><td>0.005</td><td>0.005</td><td>0.006</td><td>0.006</td><td>0.005</td><td>0.005</td><td>0.005</td><td>0.006</td><td>0.006</td><td>0.894</td><td>0.648</td><td>0.006</td><td>0.006</td><td>0.008</td></tr><tr><td>t-Stat</td><td>3.844</td><td>3.639</td><td>3.660</td><td>3.844</td><td>3.778</td><td>3.680</td><td>3.703</td><td>3.619</td><td>3.826</td><td>3.941</td><td>2.718</td><td>2.246</td><td>3.873</td><td>3.863</td><td>1.006</td></tr><tr><td>Slope</td><td>0.095</td><td>0.093</td><td>0.034</td><td>0.095</td><td>-0.045</td><td>0.087</td><td>0.018</td><td>-0.152</td><td>-0.039</td><td>-0.057</td><td>-0.029</td><td>0.022</td><td>-0.078</td><td>-0.094</td><td>-2.414</td></tr><tr><td>t-Stat</td><td>1.033</td><td>1.003</td><td>0.360</td><td>1.033</td><td>-0.434</td><td>0.936</td><td>0.205</td><td>-1.772</td><td>-0.721</td><td>-3.199</td><td>-3.204</td><td>2.227</td><td>-1.247</td><td>-1.363</td><td>-0.303</td></tr><tr><td><eq>\overline{R}^2</eq></td><td>0.004</td><td>0.004</td><td>0.001</td><td>0.004</td><td>0.001</td><td>0.003</td><td>0.000</td><td>0.012</td><td>0.002</td><td>0.039</td><td>0.041</td><td>0.019</td><td>0.006</td><td>0.007</td><td>0.000</td></tr><tr><td colspan="16">January 2002 to December 2004 (156 Weeks)</td></tr><tr><td>Intercept</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.002</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.003</td><td>0.342</td><td>0.620</td><td>0.003</td><td>0.004</td><td>0.008</td></tr><tr><td>t-Stat</td><td>1.536</td><td>1.365</td><td>1.516</td><td>1.355</td><td>1.552</td><td>1.196</td><td>1.708</td><td>1.698</td><td>1.670</td><td>1.787</td><td>1.852</td><td>1.203</td><td>1.765</td><td>2.107</td><td>1.116</td></tr><tr><td>Slope</td><td>-0.334</td><td>0.205</td><td>-0.314</td><td>-0.275</td><td>-0.283</td><td>-0.198</td><td>0.404</td><td>-0.295</td><td>-0.202</td><td>-0.056</td><td>0.028</td><td>0.021</td><td>-0.146</td><td>-0.216</td><td>-19.368</td></tr><tr><td>t-Stat</td><td>-1.847</td><td>1.219</td><td>-2.006</td><td>-1.561</td><td>-1.005</td><td>-0.679</td><td>1.949</td><td>-1.185</td><td>-2.301</td><td>-2.853</td><td>1.600</td><td>1.197</td><td>-1.834</td><td>-2.738</td><td>-0.728</td></tr><tr><td><eq>\overline{R}^2</eq></td><td>0.022</td><td>0.010</td><td>0.026</td><td>0.016</td><td>0.007</td><td>0.003</td><td>0.025</td><td>0.009</td><td>0.034</td><td>0.051</td><td>0.017</td><td>0.009</td><td>0.021</td><td>0.046</td><td>0.004</td></tr></table>


T<sub>a</sub>bl<sub>e</sub> 2 1 <sub>:</sub> F<sub>orecas</sub>t <sub>o</sub>f <sub>wee</sub>kl<sub>y mar</sub>k<sub>e</sub>t-<sub>por</sub>tf<sub>o</sub>li<sub>o re</sub>t<sub>urns</sub> b<sub>y</sub> l<sub>agge</sub>d <sub>wee</sub>kl<sub>y re</sub>t<sub>urns o</sub>f th<sub>e</sub> b<sub>e</sub>t <sub>a</sub>-<sub>sor</sub>t<sub>e</sub>d <sub>op</sub>ti<sub>ma</sub>l f<sub>orecas</sub>t <sub>por</sub>tf<sub>o</sub>li<sub>os</sub> ( O FPs) the market- capit alization-sorted O FP <sup>’</sup> s the SIC-sorted O FP the return and dollar return on the hedging p ortfolio <sub>m</sub>i<sub>nus</sub> l<sub>og</sub>-<sub>mar</sub>k<sub>e</sub>t-<sub>cap</sub>it<sub>a</sub>li<sub>za</sub>ti<sub>on</sub> th<sub>e</sub> l<sub>agge</sub>d <sub>re</sub>t<sub>urns on</sub> th<sub>e</sub> CRSP <sub>va</sub>l<sub>ue</sub>- <sub>an</sub>d <sub>equa</sub>l-<sub>we</sub>i<sub>g</sub>ht<sub>e</sub>d <sub>por</sub>tf<sub>o</sub>li<sub>os an</sub>d l<sub>agge</sub>d <sub>cons</sub>t<sub>an</sub>tmaturity (three-month) Treasury bill rates from 1 99 7 to 2004 in two subperio ds <sub>.</sub> The value of φ is 1 <sub>.</sub> 2 5 for the return $R _ { H }$ <sub>an</sub>d 1 5 f<sub>or</sub> th<sub>e</sub> d<sub>o</sub>ll<sub>ar re</sub>t<sub>urn</sub> $Q _ { H }$ <sub>on</sub> th<sub>e</sub> h<sub>e</sub>d<sub>g</sub>i<sub>ng</sub> <sub>por</sub>tf<sub>o</sub>li<sub>o</sub> <sub>respec</sub>ti<sub>ve</sub>l<sub>y</sub>


## 7 Conclusion

Trading volume is an important aspect of the economic interactions in financial market among diferent investors. Both volume and prices are driven by underlying economic forces, and thus convey important information about the workings of the market. Although the literature on financial markets has focused on analyzing the behavior of returns based on simplifying assumptions about the market such as allocational and informational eficiency, we wish to develop a more realistic framework to understand the empirical characteristics of prices and volume. 

In this chapter, we hope to have made a contribution towards this goal. By deriving an explicit link between economic fundamentals and the dynamic properties of asset returns and volume, we have shown that interactions between prices and quantities in equilibrium yield a rich set of implications for any asset-pricing model. Indeed, by exploiting the relation between prices and volume in our dynamic equilibrium model, we are able to identify and construct the hedging portfolio that all investors use to hedge against changes in market conditions. Moreover, our empirical analysis shows that this hedging portfolio has considerable forecast power in predicting future returns of the market portfolio—a property of the true hedging portfolio—and its abilities to explain cross-sectional variation in expected returns is comparable to other popular risk factors such as market betas, the Fama and French (1993) SMB factor, and optimal forecast portfolios. 

Although our model is purposefully parsimonious so as to focus attention on the essential features of risk-sharing and trading activity, it underscores the general point that quantities, together with prices, should be an integral part of any analysis of asset markets, both theoretically and empirically. Our results provide compelling motivation for determining risk factors from economic fundamentals rather than through statistical means. Although this is an old theme that has its origins in Black (1972), Mayers (1973), and Merton (1973), it has become somewhat less fashionable in recent years than the statistical approach of Roll and Ross (1980) and Chamberlain and Rothschild (1983) and the empirical approach of Fama and French (1992). We hope to revive interest in the more ambitious goal of identifying risk factors through the logic of equilibrium analysis, and by exploiting the information contained in trading volume in particular. 

An important direction for future research is to incorporate more specific aspects of the market microstructure in the analysis of trading volume. In particular, the two standard 

<table><tr><td></td><td><eq>R_{VWt}</eq></td><td><eq>R_{EWt}</eq></td><td><eq>R_{Ht}</eq></td><td><eq>Q_{Ht}</eq></td><td><eq>R_{SMBt}</eq></td><td><eq>R_{HMLt}</eq></td><td><eq>R_{OFPt}</eq></td><td><eq>\tau_t^{EW}</eq></td><td><eq>\tau_t^{SW}</eq></td></tr><tr><td colspan="10">January 1967 to December 1971 (261 Weeks)</td></tr><tr><td><eq>R_{VWt}</eq></td><td>100.0</td><td>92.6</td><td>95.6</td><td>91.5</td><td>62.7</td><td>-44.1</td><td>-76.2</td><td>19.1</td><td>26.3</td></tr><tr><td><eq>R_{EWt}</eq></td><td>92.6</td><td>100.0</td><td>92.3</td><td>88.4</td><td>84.5</td><td>-40.8</td><td>-71.9</td><td>32.8</td><td>36.9</td></tr><tr><td><eq>R_{Ht}</eq></td><td>95.6</td><td>92.3</td><td>100.0</td><td>97.4</td><td>70.7</td><td>-52.4</td><td>-65.0</td><td>22.0</td><td>29.6</td></tr><tr><td><eq>Q_{Ht}</eq></td><td>91.5</td><td>88.4</td><td>97.4</td><td>100.0</td><td>69.8</td><td>-49.4</td><td>-60.1</td><td>22.9</td><td>29.8</td></tr><tr><td><eq>R_{SMBt}</eq></td><td>62.7</td><td>84.5</td><td>70.7</td><td>69.8</td><td>100.0</td><td>-40.6</td><td>-46.6</td><td>39.7</td><td>38.2</td></tr><tr><td><eq>R_{HMLt}</eq></td><td>-44.1</td><td>-40.8</td><td>-52.4</td><td>-49.4</td><td>-40.6</td><td>100.0</td><td>14.5</td><td>-9.0</td><td>-15.0</td></tr><tr><td><eq>R_{OFPt}</eq></td><td>-76.2</td><td>-71.9</td><td>-65.0</td><td>-60.1</td><td>-46.6</td><td>14.5</td><td>100.0</td><td>-7.5</td><td>-10.4</td></tr><tr><td><eq>\tau_t^{EW}</eq></td><td>19.1</td><td>32.8</td><td>22.0</td><td>22.9</td><td>39.7</td><td>-9.0</td><td>-7.5</td><td>100.0</td><td>93.1</td></tr><tr><td><eq>\tau_t^{SW}</eq></td><td>26.3</td><td>36.9</td><td>29.6</td><td>29.8</td><td>38.2</td><td>-15.0</td><td>-10.4</td><td>93.1</td><td>100.0</td></tr><tr><td colspan="10">January 1997 to December 2001 (261 Weeks)</td></tr><tr><td><eq>R_{VWt}</eq></td><td>100.0</td><td>80.4</td><td>57.9</td><td>43.4</td><td>-20.7</td><td>-48.7</td><td>-45.7</td><td>3.3</td><td>-0.9</td></tr><tr><td><eq>R_{EWt}</eq></td><td>80.4</td><td>100.0</td><td>54.8</td><td>42.6</td><td>24.9</td><td>-46.7</td><td>-33.1</td><td>7.9</td><td>-1.4</td></tr><tr><td><eq>R_{Ht}</eq></td><td>57.9</td><td>54.8</td><td>100.0</td><td>89.2</td><td>17.0</td><td>-71.0</td><td>-15.5</td><td>0.0</td><td>-2.2</td></tr><tr><td><eq>Q_{Ht}</eq></td><td>43.4</td><td>42.6</td><td>89.2</td><td>100.0</td><td>25.3</td><td>-70.0</td><td>-1.2</td><td>3.8</td><td>0.4</td></tr><tr><td><eq>R_{SMBt}</eq></td><td>-20.7</td><td>24.9</td><td>17.0</td><td>25.3</td><td>100.0</td><td>-41.8</td><td>25.8</td><td>7.0</td><td>0.1</td></tr><tr><td><eq>R_{HMLt}</eq></td><td>-48.7</td><td>-46.7</td><td>-71.0</td><td>-70.0</td><td>-41.8</td><td>100.0</td><td>2.5</td><td>-0.1</td><td>4.4</td></tr><tr><td><eq>R_{OFPt}</eq></td><td>-45.7</td><td>-33.1</td><td>-15.5</td><td>-1.2</td><td>25.8</td><td>2.5</td><td>100.0</td><td>-0.9</td><td>1.8</td></tr><tr><td><eq>\tau_t^{EW}</eq></td><td>3.3</td><td>7.9</td><td>0.0</td><td>3.8</td><td>7.0</td><td>-0.1</td><td>-0.9</td><td>100.0</td><td>92.4</td></tr><tr><td><eq>\tau_t^{SW}</eq></td><td>-0.9</td><td>-1.4</td><td>-2.2</td><td>0.4</td><td>0.1</td><td>4.4</td><td>1.8</td><td>92.4</td><td>100.0</td></tr><tr><td colspan="10">January 2002 to December 2004 (156 Weeks)</td></tr><tr><td><eq>R_{VWt}</eq></td><td>100.0</td><td>91.8</td><td>68.6</td><td>-11.5</td><td>-17.1</td><td>-6.6</td><td>55.0</td><td>9.3</td><td>4.1</td></tr><tr><td><eq>R_{EWt}</eq></td><td>91.8</td><td>100.0</td><td>76.3</td><td>-32.7</td><td>15.8</td><td>10.2</td><td>50.3</td><td>5.5</td><td>-3.1</td></tr><tr><td><eq>R_{Ht}</eq></td><td>68.6</td><td>76.3</td><td>100.0</td><td>-60.4</td><td>14.1</td><td>-2.0</td><td>31.5</td><td>5.4</td><td>-0.4</td></tr><tr><td><eq>Q_{Ht}</eq></td><td>-11.5</td><td>-32.7</td><td>-60.4</td><td>100.0</td><td>-56.5</td><td>-2.4</td><td>-2.5</td><td>-3.9</td><td>3.3</td></tr><tr><td><eq>R_{SMBt}</eq></td><td>-17.1</td><td>15.8</td><td>14.1</td><td>-56.5</td><td>100.0</td><td>9.4</td><td>-7.2</td><td>-5.6</td><td>-9.1</td></tr><tr><td><eq>R_{HMLt}</eq></td><td>-6.6</td><td>10.2</td><td>-2.0</td><td>-2.4</td><td>9.4</td><td>100.0</td><td>-17.2</td><td>-18.3</td><td>-27.9</td></tr><tr><td><eq>R_{OFPt}</eq></td><td>55.0</td><td>50.3</td><td>31.5</td><td>-2.5</td><td>-7.2</td><td>-17.2</td><td>100.0</td><td>12.1</td><td>3.7</td></tr><tr><td><eq>\tau_t^{EW}</eq></td><td>9.3</td><td>5.5</td><td>5.4</td><td>-3.9</td><td>-5.6</td><td>-18.3</td><td>12.1</td><td>100.0</td><td>77.8</td></tr><tr><td><eq>\tau_t^{SW}</eq></td><td>4.1</td><td>-3.1</td><td>-0.4</td><td>3.3</td><td>-9.1</td><td>-27.9</td><td>3.7</td><td>77.8</td><td>100.0</td></tr></table>


Table 22: Correlation matrix for weekly returns on the CRSP value-weighted index $\left( R _ { V W t } \right)$ the CRSP equal-weighted index $( R _ { E W t } )$ , the hedging portfolio return $( R _ { H t } )$ , the hedging portfolio dollar return $\left( Q _ { H t } \right)$ , the return of the small-minus-big capitalization stocks portfolio $\left( R _ { S M B t } \right)$ , the return $R _ { O F P t }$ of the optimal forecast portfolio (OFP) for the set of 20 marketbeta-sorted basis portfolios, and the equal-weighted and share-weighted turnover indices $( \tau _ { t } ^ { E W }$ and $\tau _ { t } ^ { S W } )$ , using CRSP weekly returns and volume data for NYSE and AMEX stocks for three subperiods: January 1967 to December 1971, January 1997 to December 2001, and January 2002 to December 2004.


<table><tr><td>Model</td><td>Statistic</td><td><eq>\hat{\gamma}_{0t}</eq></td><td><eq>\hat{\gamma}_{1t}</eq></td><td><eq>\hat{\gamma}_{2t}</eq></td><td><eq>\hat{\gamma}_{3t}</eq></td><td><eq>\overline{R}^{2}</eq>(%)</td></tr><tr><td colspan="7">January 1972 to December 1976 (261 Weeks)</td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.2</td><td>0.0</td><td></td><td></td><td>10.0</td></tr><tr><td>S.D. (%):</td><td>1.5</td><td>2.1</td><td></td><td></td><td>10.9</td></tr><tr><td>t-stat:</td><td>1.64</td><td>0.35</td><td></td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HR} + \varepsilon_{pt}</eq><eq>(\phi = 1.25)</eq></td><td>Mean (%):</td><td>0.4</td><td>-0.2</td><td>-0.2</td><td></td><td>14.3</td></tr><tr><td>S.D. (%):</td><td>3.5</td><td>3.5</td><td>3.7</td><td></td><td>10.9</td></tr><tr><td>t-stat:</td><td>2.04</td><td>-1.05</td><td>-0.82</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HQ} + \varepsilon_{pt}</eq><eq>(\phi = 1.50)</eq></td><td>Mean (%):</td><td>0.4</td><td>-0.2</td><td>-10.4</td><td></td><td>15.5</td></tr><tr><td>S.D. (%):</td><td>3.2</td><td>3.4</td><td>379.7</td><td></td><td>10.9</td></tr><tr><td>t-stat:</td><td>2.16</td><td>-1.08</td><td>-0.44</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.1</td><td>0.0</td><td>6.3</td><td></td><td>12.1</td></tr><tr><td>S.D. (%):</td><td>1.4</td><td>2.4</td><td>114.2</td><td></td><td>10.8</td></tr><tr><td>t-stat:</td><td>1.42</td><td>0.22</td><td>0.90</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HML} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.0</td><td>0.1</td><td>0.2</td><td></td><td>7.8</td></tr><tr><td>S.D. (%):</td><td>1.8</td><td>1.9</td><td>1.5</td><td></td><td>7.8</td></tr><tr><td>t-stat:</td><td>0.40</td><td>1.08</td><td>1.66</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \gamma_{3t}\widehat{\beta}_{p}^{HML} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.0</td><td>0.1</td><td>0.0</td><td>0.1</td><td>8.8</td></tr><tr><td>S.D. (%):</td><td>1.8</td><td>2.1</td><td>1.2</td><td>1.5</td><td>7.6</td></tr><tr><td>t-stat:</td><td>0.28</td><td>0.80</td><td>0.50</td><td>1.27</td><td></td></tr><tr><td colspan="7">January 1977 to December 1981 (261 Weeks)</td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.1</td><td>0.3</td><td></td><td></td><td>11.7</td></tr><tr><td>S.D. (%):</td><td>1.1</td><td>2.2</td><td></td><td></td><td>12.8</td></tr><tr><td>t-stat:</td><td>1.17</td><td>2.57</td><td></td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HR} + \varepsilon_{pt}</eq><eq>(\phi = 4.75)</eq></td><td>Mean (%):</td><td>0.3</td><td>-0.1</td><td>-1.2</td><td></td><td>13.1</td></tr><tr><td>S.D. (%):</td><td>1.4</td><td>2.0</td><td>5.1</td><td></td><td>12.4</td></tr><tr><td>t-stat:</td><td>3.75</td><td>-0.90</td><td>-3.71</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HQ} + \varepsilon_{pt}</eq><eq>(\phi = 4.25)</eq></td><td>Mean (%):</td><td>0.3</td><td>-0.1</td><td>-156.4</td><td></td><td>12.5</td></tr><tr><td>S.D. (%):</td><td>1.3</td><td>2.0</td><td>610.4</td><td></td><td>12.2</td></tr><tr><td>t-stat:</td><td>3.91</td><td>-0.75</td><td>-4.14</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.1</td><td>0.0</td><td>29.9</td><td></td><td>14.9</td></tr><tr><td>S.D. (%):</td><td>1.1</td><td>1.7</td><td>108.8</td><td></td><td>13.4</td></tr><tr><td>t-stat:</td><td>2.25</td><td>-0.16</td><td>4.43</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HML} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.2</td><td>0.2</td><td>0.1</td><td></td><td>9.3</td></tr><tr><td>S.D. (%):</td><td>1.3</td><td>1.9</td><td>0.9</td><td></td><td>9.2</td></tr><tr><td>t-stat:</td><td>2.15</td><td>1.52</td><td>1.58</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{OFP} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.3</td><td>0.1</td><td>0.1</td><td></td><td>14.1</td></tr><tr><td>S.D. (%):</td><td>1.8</td><td>2.3</td><td>3.6</td><td></td><td>11.6</td></tr><tr><td>t-stat:</td><td>2.74</td><td>0.84</td><td>0.63</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \gamma_{3t}\widehat{\beta}_{p}^{HML} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.2</td><td>-0.0</td><td>0.3</td><td>-0.1</td><td>11.5</td></tr><tr><td>S.D. (%):</td><td>1.2</td><td>1.7</td><td>1.0</td><td>1.0</td><td>10.0</td></tr><tr><td>t-stat:</td><td>2.72</td><td>-0.07</td><td>4.61</td><td>-0.85</td><td></td></tr></table>

Table 23a: Cross-sectional regression tests of six linear factor models along the lines of Fama and MacBeth (1973), using weekly returns for NYSE and AMEX stocks from 1962 to 2004 in five-year subperiods for the portfolio formation, estimation, and testing periods, and 100 portfolios in the cross-sectional regressions each week. The six linear factor models are: the standard CAPM $( { \widehat { \beta } } _ { p } ^ { M } )$ ; four two-factor models in which the first factor is the market beta and the second factors are, respectively, the hedging portfolio return beta $( \widehat { \beta } _ { p } ^ { H R } )$ , the hedging portfolio dollar return beta $( \widehat { \beta } _ { p } ^ { H Q } )$ , the beta of a small-minus-big cap portfolio return $( \widehat { \beta } _ { p } ^ { S M B } )$ , the beta of the Fama and French (1992) high-minus-low book-to-market portfolio return $( \widehat { \beta } _ { p } ^ { H M L } )$ , and the beta of the optimal forecast portfolio based on a set of 25 marketbeta-sorted basis portfolios $( \widehat { \beta } _ { p } ^ { O F P } )$ ; and a three-factor model with $\widehat { \beta } _ { p } ^ { M } , \widehat { \beta } _ { p } ^ { S M B }$ , and $\widehat { \beta } _ { p } ^ { H M L }$ as the three factors. 

<table><tr><td>Model</td><td>Statistic</td><td><eq>\hat{\gamma}_{0t}</eq></td><td><eq>\hat{\gamma}_{1t}</eq></td><td><eq>\hat{\gamma}_{2t}</eq></td><td><eq>\hat{\gamma}_{3t}</eq></td><td><eq>\overline{R}^{2}</eq>(%)</td></tr><tr><td colspan="7">January 1982 to December 1986 (261 Weeks)</td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.6</td><td>-0.1</td><td></td><td></td><td>9.4</td></tr><tr><td>S.D. (%):</td><td>1.1</td><td>1.9</td><td></td><td></td><td>11.1</td></tr><tr><td>t-stat:</td><td>8.17</td><td>-1.04</td><td></td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HR} + \varepsilon_{pt}</eq><eq>(\phi = 1.75)</eq></td><td>Mean (%):</td><td>0.6</td><td>-0.1</td><td>-0.6</td><td></td><td>9.6</td></tr><tr><td>S.D. (%):</td><td>1.1</td><td>2.0</td><td>5.5</td><td></td><td>9.4</td></tr><tr><td>t-stat:</td><td>8.39</td><td>-0.78</td><td>-1.73</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HQ} + \varepsilon_{pt}</eq><eq>(\phi = 2.00)</eq></td><td>Mean (%):</td><td>0.6</td><td>-0.2</td><td>-74.0</td><td></td><td>10.4</td></tr><tr><td>S.D. (%):</td><td>1.1</td><td>1.9</td><td>1987.4</td><td></td><td>9.5</td></tr><tr><td>t-stat:</td><td>8.36</td><td>-1.30</td><td>-0.60</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.5</td><td>-0.2</td><td>3.8</td><td></td><td>10.0</td></tr><tr><td>S.D. (%):</td><td>1.2</td><td>1.9</td><td>115.4</td><td></td><td>8.4</td></tr><tr><td>t-stat:</td><td>7.45</td><td>-1.26</td><td>0.53</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HML} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.5</td><td>-0.1</td><td>0.2</td><td></td><td>9.2</td></tr><tr><td>S.D. (%):</td><td>1.4</td><td>1.9</td><td>1.5</td><td></td><td>8.5</td></tr><tr><td>t-stat:</td><td>5.57</td><td>-0.83</td><td>1.81</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{OFP} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.5</td><td>-0.1</td><td>0.0</td><td></td><td>11.7</td></tr><tr><td>S.D. (%):</td><td>1.1</td><td>2.0</td><td>2.1</td><td></td><td>10.8</td></tr><tr><td>t-stat:</td><td>7.55</td><td>-0.82</td><td>0.20</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \gamma_{3t}\widehat{\beta}_{p}^{HML} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.4</td><td>-0.0</td><td>0.0</td><td>0.1</td><td>10.0</td></tr><tr><td>S.D. (%):</td><td>1.4</td><td>2.2</td><td>1.0</td><td>1.1</td><td>8.5</td></tr><tr><td>t-stat:</td><td>4.49</td><td>-0.24</td><td>0.55</td><td>1.97</td><td></td></tr><tr><td colspan="7">January 1987 to December 1991 (261 Weeks)</td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.2</td><td>0.0</td><td></td><td></td><td>5.9</td></tr><tr><td>S.D. (%):</td><td>1.3</td><td>2.3</td><td></td><td></td><td>8.7</td></tr><tr><td>t-stat:</td><td>2.65</td><td>0.20</td><td></td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HR} + \varepsilon_{pt}</eq><eq>(\phi = 47)</eq></td><td>Mean (%):</td><td>0.2</td><td>0.0</td><td>0.0</td><td></td><td>5.4</td></tr><tr><td>S.D. (%):</td><td>1.6</td><td>1.9</td><td>6.0</td><td></td><td>6.1</td></tr><tr><td>t-stat:</td><td>2.25</td><td>0.11</td><td>0.13</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HQ} + \varepsilon_{pt}</eq><eq>(\phi = 20)</eq></td><td>Mean (%):</td><td>0.2</td><td>0.0</td><td>18.9</td><td></td><td>6.0</td></tr><tr><td>S.D. (%):</td><td>1.6</td><td>1.9</td><td>1819.4</td><td></td><td>6.7</td></tr><tr><td>t-stat:</td><td>2.43</td><td>-0.15</td><td>0.17</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.3</td><td>0.0</td><td>-7.5</td><td></td><td>7.8</td></tr><tr><td>S.D. (%):</td><td>1.4</td><td>2.0</td><td>123.5</td><td></td><td>8.2</td></tr><tr><td>t-stat:</td><td>3.10</td><td>0.16</td><td>-0.98</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HML} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.2</td><td>0.0</td><td>0.0</td><td></td><td>6.3</td></tr><tr><td>S.D. (%):</td><td>1.6</td><td>2.0</td><td>1.8</td><td></td><td>7.6</td></tr><tr><td>t-stat:</td><td>2.11</td><td>0.03</td><td>-0.38</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{OFP} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.3</td><td>-0.1</td><td>0.0</td><td></td><td>6.4</td></tr><tr><td>S.D. (%):</td><td>1.5</td><td>2.1</td><td>2.1</td><td></td><td>7.3</td></tr><tr><td>t-stat:</td><td>2.73</td><td>-0.39</td><td>-0.23</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \gamma_{3t}\widehat{\beta}_{p}^{HML} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.3</td><td>0.0</td><td>-0.1</td><td>-0.1</td><td>7.8</td></tr><tr><td>S.D. (%):</td><td>1.9</td><td>2.1</td><td>1.2</td><td>1.5</td><td>6.8</td></tr><tr><td>t-stat:</td><td>2.21</td><td>0.16</td><td>-0.97</td><td>-1.10</td><td></td></tr><tr><td colspan="7">January 1992 to December 1996 (261 Weeks)</td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.2</td><td>0.1</td><td></td><td></td><td>5.7</td></tr><tr><td>S.D. (%):</td><td>1.3</td><td>2.0</td><td></td><td></td><td>7.7</td></tr><tr><td>t-stat:</td><td>2.68</td><td>1.18</td><td></td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HR} + \varepsilon_{pt}</eq><eq>(\phi = 38)</eq></td><td>Mean (%):</td><td>0.2</td><td>0.1</td><td>-0.4</td><td></td><td>6.9</td></tr><tr><td>S.D. (%):</td><td>1.3</td><td>2.0</td><td>9.1</td><td></td><td>6.8</td></tr><tr><td>t-stat:</td><td>2.79</td><td>1.16</td><td>-0.65</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HQ} + \varepsilon_{pt}</eq><eq>(\phi = 27)</eq></td><td>Mean (%):</td><td>0.3</td><td>0.0</td><td>-158.4</td><td></td><td>6.2</td></tr><tr><td>S.D. (%):</td><td>1.5</td><td>2.2</td><td>1299.2</td><td></td><td>6.6</td></tr><tr><td>t-stat:</td><td>3.28</td><td>-0.18</td><td>-1.97</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.2</td><td>0.1</td><td>15.4</td><td></td><td>6.7</td></tr><tr><td>S.D. (%):</td><td>1.5</td><td>1.9</td><td>115.7</td><td></td><td>7.0</td></tr><tr><td>t-stat:</td><td>1.65</td><td>0.86</td><td>2.15</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HML} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.3</td><td>0.1</td><td>0.0</td><td></td><td>7.7</td></tr><tr><td>S.D. (%):</td><td>1.4</td><td>1.9</td><td>1.0</td><td></td><td>7.9</td></tr><tr><td>t-stat:</td><td>3.19</td><td>0.78</td><td>-0.43</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{OFP} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.1</td><td>0.2</td><td>0.2</td><td></td><td>7.9</td></tr><tr><td>S.D. (%):</td><td>1.6</td><td>2.0</td><td>1.5</td><td></td><td>7.4</td></tr><tr><td>t-stat:</td><td>0.90</td><td>1.24</td><td>2.41</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \gamma_{3t}\widehat{\beta}_{p}^{HML} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.3</td><td>0.0</td><td>0.2</td><td>-0.0</td><td>6.6</td></tr><tr><td>S.D. (%):</td><td>1.5</td><td>2.0</td><td>1.1</td><td>1.1</td><td>5.8</td></tr><tr><td>t-stat:</td><td>2.76</td><td>0.08</td><td>2.21</td><td>-0.27</td><td></td></tr><tr><td colspan="7">January 1997 to December 2001 (261 Weeks)</td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.3</td><td>0.0</td><td></td><td></td><td>8.1</td></tr><tr><td>S.D. (%):</td><td>1.4</td><td>2.5</td><td></td><td></td><td>9.9</td></tr><tr><td>t-stat:</td><td>2.98</td><td>0.27</td><td></td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HR} + \varepsilon_{pt}</eq><eq>(\phi = 1.75)</eq></td><td>Mean (%):</td><td>0.3</td><td>0.0</td><td>0.0</td><td></td><td>10.3</td></tr><tr><td>S.D. (%):</td><td>1.4</td><td>2.2</td><td>2.0</td><td></td><td>10.4</td></tr><tr><td>t-stat:</td><td>3.35</td><td>-0.05</td><td>-0.21</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HQ} + \varepsilon_{pt}</eq><eq>(\phi = 2.00)</eq></td><td>Mean (%):</td><td>0.3</td><td>0.0</td><td>-17.9</td><td></td><td>9.4</td></tr><tr><td>S.D. (%):</td><td>1.7</td><td>2.3</td><td>307.4</td><td></td><td>8.5</td></tr><tr><td>t-stat:</td><td>2.86</td><td>-0.23</td><td>-0.94</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.3</td><td>-0.1</td><td>0.1</td><td></td><td>9.3</td></tr><tr><td>S.D. (%):</td><td>1.6</td><td>2.4</td><td>1.3</td><td></td><td>8.3</td></tr><tr><td>t-stat:</td><td>3.58</td><td>-0.97</td><td>1.76</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HML} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.3</td><td>0.0</td><td>-0.1</td><td></td><td>8.8</td></tr><tr><td>S.D. (%):</td><td>1.5</td><td>2.5</td><td>1.8</td><td></td><td>8.4</td></tr><tr><td>t-stat:</td><td>3.35</td><td>-0.05</td><td>-0.78</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{OFP} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.3</td><td>0.0</td><td>0.1</td><td></td><td>6.4</td></tr><tr><td>S.D. (%):</td><td>1.5</td><td>2.2</td><td>1.6</td><td></td><td>7.5</td></tr><tr><td>t-stat:</td><td>2.91</td><td>0.26</td><td>0.71</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \gamma_{3t}\widehat{\beta}_{p}^{HML} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.4</td><td>-0.2</td><td>0.2</td><td>-0.0</td><td>9.3</td></tr><tr><td>S.D. (%):</td><td>1.7</td><td>2.8</td><td>1.5</td><td>1.8</td><td>7.3</td></tr><tr><td>t-stat:</td><td>4.31</td><td>-1.39</td><td>1.8</td><td>-0.37</td><td></td></tr><tr><td colspan="7">January 2002 to December 2004 (156 Weeks)</td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.4</td><td>0.0</td><td></td><td></td><td>3.9</td></tr><tr><td>S.D. (%):</td><td>1.7</td><td>1.3</td><td></td><td></td><td>4.2</td></tr><tr><td>t-stat:</td><td>3.26</td><td>-0.27</td><td></td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HR} + \varepsilon_{pt}</eq><eq>(\phi = 1.75)</eq></td><td>Mean (%):</td><td>0.6</td><td>-0.2</td><td>0.6</td><td></td><td>9.3</td></tr><tr><td>S.D. (%):</td><td>1.7</td><td>2.5</td><td>8.0</td><td></td><td>9.6</td></tr><tr><td>t-stat:</td><td>4.54</td><td>-0.94</td><td>0.94</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HQ} + \varepsilon_{pt}</eq><eq>(\phi = 2.00)</eq></td><td>Mean (%):</td><td>0.7</td><td>-0.3</td><td>-106.5</td><td></td><td>5.8</td></tr><tr><td>S.D. (%):</td><td>2.2</td><td>2.2</td><td>699.7</td><td></td><td>6.2</td></tr><tr><td>t-stat:</td><td>4.29</td><td>-1.71</td><td>-1.90</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.5</td><td>-0.1</td><td>0.1</td><td></td><td>4.2</td></tr><tr><td>S.D. (%):</td><td>2.2</td><td>0.7</td><td>0.6</td><td></td><td>4.9</td></tr><tr><td>t-stat:</td><td>2.71</td><td>-1.43</td><td>1.59</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{HML} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.5</td><td>-0.1</td><td>0.0</td><td></td><td>6.1</td></tr><tr><td>S.D. (%):</td><td>2.0</td><td>1.4</td><td>1.0</td><td></td><td>5.4</td></tr><tr><td>t-stat:</td><td>3.17</td><td>-0.86</td><td>-0.55</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{OFP} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.4</td><td>0.0</td><td>0.0</td><td></td><td>4.1</td></tr><tr><td>S.D. (%):</td><td>1.7</td><td>1.3</td><td>0.4</td><td></td><td>4.0</td></tr><tr><td>t-stat:</td><td>3.15</td><td>0.01</td><td>-0.19</td><td></td><td></td></tr><tr><td rowspan="3"><eq>R_{pt} = \gamma_{0t} + \gamma_{1t}\widehat{\beta}_{p}^{M} + \gamma_{2t}\widehat{\beta}_{p}^{SMB} + \gamma_{3t}\widehat{\beta}_{p}^{HML} + \varepsilon_{pt}</eq></td><td>Mean (%):</td><td>0.4</td><td>0.0</td><td>0.0</td><td>0.1</td><td>5.8</td></tr><tr><td>S.D. (%):</td><td>2.4</td><td>0.5</td><td>0.4</td><td>1.1</td><td>5.3</td></tr><tr><td>t-stat:</td><td>2.03</td><td>0.03</td><td>1.57</td><td>0.75</td><td></td></tr></table>


Table 23b: (continued).


assumptions of perfect competition and symmetric information—assumptions that we have also adopted in our theoretical framework—do not hold in practice. For example, for most individual investors, financial markets have traditionally been considered close to perfectly competitive, so that the size of a typical investment has little impact on prices. For such scale-free investment opportunities, quantities are largely irrelevant and returns become the basic objects of study, not prices. But as institutional investors have grown in size and sophistication over the past several decades, and as frictions in the trading process have become more important because of the sheer volume of trade, it has become clear that securities markets are not perfectly competitive, at least not in the short run. 

Moreover, when investors possess private information—about price movements, their own trading intentions, and other market factors—perfect competition is even less likely to hold. For example, if a large pension fund were to liquidate a substantial position in one security, that security’s price would drop precipitously if the liquidation were attempted through a single sell-order, yielding a significant loss in the value of the security to be sold. Instead, such a liquidation would typically be accomplished over several days, with a professional trading desk managing the liquidation process by breaking up the entire order into smaller pieces, each executed at opportune moments so as to minimize trading costs and the overall price impact of the sale.<sup>48</sup> This suggests that there is information to be garnered from quantities as well as prices; a 50,000-share trade has diferent implications than a 5,000-share trade, and the sequence of trading volume contains information as well. The fact that the demand curves of even the most liquid financial securities are downward-sloping for large institutional investors, and that information is often revealed through the price-discovery process, implies that quantities are as fundamental as prices, and equally worthy of investigation. 

Finally, the presence of market frictions such as transactions costs can influence the level of trading volume, and serves as a bridge between the market microstructure literature and the broader equilibrium asset-pricing literature. In particular, despite the many market microstructure studies that relate trading behavior to market-making activities and the pricediscovery mechanism,<sup>49</sup> the seemingly high level of volume in financial markets has often been considered puzzling from a rational asset-pricing perspective (see, for example, Ross, 1989). Some have even argued that additional trading frictions or “sand in the gears” ought to be introduced in the form of a transactions tax to discourage high-frequency trading.<sup>50</sup> Yet in absence of transactions costs, most dynamic equilibrium models will show that it is quite rational and eficient for trading volume to be infinite when the information flow to the market is continuous, i.e., a difusion. An equilibrium model with fixed transactions costs, e.g., Lo, Mamaysky, and Wang (2004), may reconcile these two disparate views of trading volume. 



Admati, A.R., and P. Pfleiderer, 1988, “A Theory of Intraday Patterns: Volume and Price Variability”, Review of Financial Studies 1, 3-40. 





Ajinkya, B.B., and P.C. Jain, 1989, “The Behavior of Daily Stock Market Trading Volume”, Journal of Accounting and Economics 11, 331–359. 





Amihud, Y. and H. Mendelson, 1986a, “Asset Pricing and the Bid-Ask Spread”, Journal of Financial Economics 17, 223–249. 





Amihud, Y. and H. Mendelson, 1986b, “Liquidity And Stock Returns”, Financial Analysts Journal 42, 43–48. 





Andersen, T., 1996, “Return Volatility and Trading Volume: An Information Flow Interpretation”, Journal of Finance 51, 169–204. 





Antoniewicz, R., 1993, “Relative Volume and Subsequent Stock Price Movements”, working paper, Board of Governors of the Federal Reserve System. 





Atkins, A. and E. Dyl, 1997, “Market Structure and Reported Trading Volume: NASDAQ versus the NYSE”, Journal of Financial Research 20, 291-304. 





Bagehot, W. (a.k.a. J. Treynor), 1971, “The Only Game in Town”, Financial Analysts Journal 22, 12-14. 





Banz, R., 1981, “The Relation between Return and Market Value of Common Stocks”, Journal of Financial Economics 9, 3–18. 





Bamber, L., 1986, “The Information Content of Annual Earnings Releases: A Trading Volume Approach”, Journal of Accounting Research 24, 40–56. 





Black, F., 1976, “Studies of Stock Price Volatility Changes”, in Proceedings of the 1976 Meetings of the Business and Economic Statistics Section, American Statistical Association, 177–181. 





Black, F., M. Jensen, and M. Scholes, 1972, “The Capital Asset Pricing Model: Some Empirical Tests”, Studies in the Theory of Capital Markets (M. Jensen ed.), Praeger Publishers. 





Brown, K., Van Harlow, W. and S. Tinic, 1993, “The Risk and Required Return of Common Stock Following Major Price Innovations”, Journal of Financial and Quantitative Analysis 28, 101–116. 





Campbell, J., Grossman S. and J. Wang, 1993, “Trading Volume and Serial Correlation in Stock Returns”, Quarterly Journal of Economics 108, 905–939. 





Campbell, J., A. Lo and C. MacKinlay, 1996, The Econometrics of Financial Markets, Princeton University Press. 





Campbell, J. and A. Kyle, 1993, “Smart Money, Noise Trading, and Stock Price Behavior”, Review of Economic Studies 60, 1–34. 





Cass, D. and J. Stiglitz, 1970, “The Structure of Investor Preferences and Asset Returns, and Separability in Portfolio Allocation: A Contribution to the Pure Theory of Mutual Funds”, Journal of Economic Theory 2, 122–160. 





Chamberlain, G., 1983, “Funds, Factors, and Diversification in Arbitrage Pricing Models”, Econometrica 51, 1305–1323. 





Chamberlain, G. and M. Rothschild, 1983, “Arbitrage, Factor Structure, and Mean-Variance Analysis on Large Asset Markets”, Econometrica 51, 1281–1304. 





Chan, L. and J. Lakonishok, 1995, “The Behavior of Stock Prices Around Institutional Trades”, Journal of Finance 50, 1147–74. 





Chopra, N., Lakonishok, J. and J. Ritter, 1992, “Measuring Abnormal Performance: Do Stocks Overreact?”, Journal of Financial Economics 31, 235–286. 





Conrad, J., Hameed, A. and C. Niden, 1994, “Volume and Autocovariances in Short-Horizon Individual Security Returns”, Journal of Finance 49, 1305–1329. 





Cox, J., Ingersoll, J. and S. Ross, 1985, “An Intertemporal General Equilibrium Model of Asset Prices”, Econometrica 53, 363–384. 





Cross, F., 1973, “The Behavior of Stock Prices on Fridays and Mondays”, Financial Analysts Journal , 67–69. 





DeBondt, W. and R. Thaler, 1985, “Does the Stock Market Overreact?” Journal ofFinance 40, 793–805. 





Dhillon, U. and H. Johnson, 1991, “Changes in the Standard and Poor’s 500 List”, Journal of Business 64, 75–85. 





Dumas, B., 1989, “Two Person Dynamic Equilibrium in the Capital Market”, Review of Financial Studies 2, 157-188. 





Easley, D., and M. O’Hara, 1987, Price, Trade Size, and Information In Securities Markets, Journal of Financial Economics 18, 69-90. 





Epps, T. and M. Epps, 1976, “The Stochastic Dependence of Security Price Changes and Transaction Volumes: Implications for the Mixture of Distribution Hypothesis”, Econometrica 44, 305–321. 





Fama, E. and K. French, 1992, “The Cross-Section of Expected Stock Returns”, Journal of Finance 47, 427–465. 





Fama, E. and J. MacBeth, 1973, Risk, Return, and Equilibrium: Empirical Tests”, Journal of Political Economy 81, 607–636. 





Foster, F.D., and S. Viswanathan, “Variations in Trading Volume, Return Volatility, and Trading Costs: Evidence on Recent Price Formation Models”, Journal of Finance 48, 187–211. 





Foster, D., Smith, T. and R. Whaley, 1997, “Assessing Goodness-of-Fit of Asset-Pricing Models: The Distribution of the Maximal R-Squared”, Journal of Finance 52, 591–607. 





French, K., 1980, “Stock Returns and the Weekend Efect”, Journal of Financial Economics 8, 55–69. 





Gallant, R., Rossi, P. and G. Tauchen, 1992, “Stock Prices and Volume”, Review of Financial Studies 5, 199–242. 





Gibbons, M. and P. Hess, 1981, “Day of the Week Efects and Asset Returns”, Journal of Business 54, 579–596. 





Goetzmann, W. and M. Garry, 1986, “Does Delisting From the S&P 500 Afect Stock Prices?”, Financial Analysts Journal 42, 64–69. 





Hamilton, J., 1994, Times Series Analysis. Princeton, NJ: Princeton University Press. 





Harris, L., 1986, “A Transaction Data Study of Weekly and Intradaily Patterns in Stock Returns”, Journal of Financial Economics 16, 99–117. 





Harris, L. and E. Gurel, 1986, “Price and Volume Efects Associated with Changes in the S&P 500 List: New Evidence for the Existence of Price Pressures,” Journal of Finance 46, 815–829. 





He, H., and J. Wang, 1995, “Diferential Information and Dynamic Behavior of Stock Trading Volume”, Review of Financial Studies 8, 919–972. 





Hiemstra, C. and J. Jones, 1994, “Testing for Linear and Nonlinear Granger Causality in the Stock Price-Volume Relation”, Journal of Finance 49, 1639–1664. 





Hu, S., 1997, “Trading Turnover and Expected Stock Returns: Does It Matter and Why?”, working paper, National Taiwan University. 





Jacques, W., 1988, “The S&P 500 Membership Anomaly, or Would You Join This Club?”, Financial Analysts Journal 44, 73–75. 





Jafe, J. and R. Westerfield, 1985, “The Week-End Efect in Common Stock Returns: The International Evidence”, Journal of Finance 40, 433–454. 





Jain, P., 1987, “The Efect on Stock Price of Inclusion in or Exclusion from the S&P 500”, Financial Analysts Journal 43, 58–65. 





Jain, P. and G. Joh, 1988, “The Dependence between Hourly Prices and Trading Volume”, Journal of Financial and Quantitative Analysis 23, 269–282. 





James, C., and R. Edmister, 1983, “The Relation between Common Stock Returns, Trading Activity and Market Value”, Journal of Finance 38, 1075-1086. 





Karpof, J., 1987, “The Relation between Price Changes and Trading Volume: A Survey”, Journal of Financial and Quantitative Analysis 22, 109–126. 





Karpof, J. and R. Walkling, 1988, “Short-Term Trading Around Ex-Dividend Days: Additional Evidence”, Journal of Financial Economics 21, 291–298. 





Karpof, J. and R. Walkling, 1990, “Dividend Capture in NASDAQ Stocks”, Journal of Financial Economics 28, 39–65. 





Keim, D. and R. Stambaugh, 1984, “A Further Investigation of the Weekend Efect in Stock Returns”, Journal of Finance 39, 819–840. 





Kwiatkowski, D., Phillips, P., Schmidt, P. and Y. Shin, 1992, “Testing the Null Hypothesis of Stationarity Against the Alternative of a Unit Root: How Sure Are We That Economic Time Series Have a Unit Root?”, Journal of Econometrics 54, 159–178. 





Kyle, A., 1985, “Continuous Auctions and Insider Trading”, Econometrica 53, 1315-1335. 





Lakonishok, J. and M. Levi, 1982, “Weekend Efects on Stock Returns”, Journal of Finance 37, 883–889. 





Lakonishok, J. and S. Smidt, 1986, “Volume for Winners and Losers: Taxation and Other Motives for Stock Trading”, Journal of Finance 41, 951–974. 





Lakonishok, J. and S. Smidt, 1988, “Are Seasonal Anomalies Real? A Ninety-Year Perspective”, Review of Financial Studies 1, 403–425. 





Lakonishok, J. and T. Vermaelen, 1986, “Tax-Induced Trading Around Ex-Dividend Days”, Journal of Financial Economics 16, 287–319. 





Lamoureux, C. and W. Lastrapes, 1990, “Heteroskedasticity in Stock Return Data: Volume vs. GARCH Efects”, Journal of Finance 45, 487–498. 





Lamoureux, C. and W. Lastrapes, 1994 “Endogenous Trading Volume and Momentum in Stock-Return Volatility”, Journal of Business and Economic Statistics 12, 253–160. 





Lamoureux, C. and J. Wansley, 1987, “Market Efects of Changes in the Standard & Poor’s 500 Index”, Financial Review 22, 53–69. 





LeBaron, B., 1992, “Persistence of the Dow Jones Index on Rising Volume”, working paper, University of Wisconsin. 





Lehmann, B., 1990, “Fads, Martingales, and Market Eficiency”, Quarterly Journal of Economics 105, 1–28. 





Lim, T., Lo, A., Wang, J. and P. Adamek, 1998, “Trading Volume and the MiniCRSP Database: An Introduction and User’s Guide”, MIT Laboratory for Financial Engineering Working Paper No. LFE–1038–98. 





Llorente, G., R. Michaely, G. Saar and J. Wang, 2002, “Dynamic Volume-Return Relations for Individual Stocks”, Review of Financial Studies 15, 1005–1047. 





Lo, A. and C. MacKinlay, 1988, “Stock Market Prices Do Not Follow Random Walks: Evidence from a Simple Specification Test”, Review of Financial Studies 1, 41–66. 





Lo, A. and C. MacKinlay, 1997, “Maximizing Predictability in the Stock and Bond Markets”, Macroeconomic Dynamics 1(1997), 102–134. 





Lo, A. and C. MacKinlay, 1999, A Non-Random Walk Down Wall Street. Princeton, NJ: Princeton University Press. 





Lo, A., H. Mamaysky and J. Wang, 2000, “Foundations of Technical Analysis: Computational Algorithms, Statistical Inference and Empirical Implementation”, Journal of Finance 55, 1705–1765. 





Lo, A., H. Mamaysky and J. Wang, 2004, “Asset Prices and Trading Volume under Fixed Transaction Costs”, Journal of Political Economy 112, 1054–1090. 





Lo, A. and J. Wang, 2000, Trading Volume: Definitions, Data Analysis, and Implications of Portfolio Theory, Review of Financial Studies 13, 257–300. 





Lo, A. and J. Wang, 2003, “Trading Volume”, in Dewatripont, M., Hansen, L. and S. Turnovsky, eds., Advances in Economic Theory: Eight World Congress (Econometric Society Monograph). 





Lo, A. and J. Wang, 2006, “Trading Volume: Implications of an Intertemporal Capital Asset-Pricing Model”, Journal of Finance 61, 2805–2840 





Lynch-Koski, J., 1996, “A Microstructure Analysis of Ex-Dividend Stock Price Behavior Before and After the 1984 and 1986 Tax Reform Acts”, Journal of Business 69, 313– 338. 





MacKinlay, C., 1987, “On Multivariate Tests of the CAPM”, Journal of Financial Economics 18, 341–371. 





MacKinlay, C., 1994, “Multi-Factor Models Do Not Explain Deviations from the CAPM”, Journal of Financial Economics 38, 3–28. 





Markowitz, H., 1952, “Portfolio Selection”, Journal of Finance 7, 77–91. 





Marsh, T. and R. Merton, 1987, “Dividend Behavior For The Aggregate Stock Market”, Journal of Business 60, 1–40. 





Merton, R., 1971, “Optimal Consumption and Portfolio Rules in a Continuous-Time Model”, Journal of Economic Theory 3, 373–413. 





Merton, R., 1973, “An Intertemporal Capital Asset Pricing Model”, Econometrica 41, 867– 887. 





Merton, R., 1987, “A Simple Model of Capital Market Equilibrium with Incomplete Information”, Journal of Finance 42, 483–510. 





Michaely, R., 1991, “Ex-Dividend Day Stock Price Behavior: The Case of the 1986 Tax Reform Act”, Journal of Finance 46, 845–860. 





Michaely, R. and J. Vila, 1995, “Investors’ Heterogeneity, Prices and Volume Around the Ex-Dividend Day”, Journal of Financial and Quantitative Analysis 30, 171–198. 





Michaely, R. and J. Vila, 1996, “Trading Volume with Private Valuation: Evidence from the Ex-Dividend Day”, Review of Financial Studies 9, 471–509. 





Michaely, R., J.-L. Vila and J. Wang, “A Model of Trading Volume with Tax-Induced Heterogeneous Valuation and Transaction Costs” Journal of Financial Intermediation 5, 340-371, 1996. 





Morse, D., 1980, “Asymmetric Information in Securities Markets and Trading Volume”, Journal of Financial and Quantitative Analysis 15, 1129–1148. 





Muirhead, R., 1982, Aspects of Multivariate Statistical Theory. New York: John Wiley and Sons. 





Pruitt, S. and J. Wei, 1989, “Institutional Ownership and Changes in the S&P 500”, Journal of Finance 44, 509–513. 





Reinganum, M., 1992, “A Revival of the Small-Firm Efect”, Journal of Portfolio Management 18, 55–62. 





Richardson, G., Sefcik, S. and R. Thompson, 1986, “A Test of Dividend Irrelevance Using Volume Reaction to a Change in Dividend Policy”, Journal of Financial Economics 17, 313–333. 





Roll, R., 1984, “A Simple Implicit Measure of the Efective Bid-Ask Spread in an Eficient Market”, Journal of Finance 39, 1127–1140. 





Ross, S., 1978, “Mutual Fund Separation in Financial Theory—The Separating Distributions”, Journal of Economic Theory 17, 254–286. 





Ross, S., 1989, “Discussion: Intertemporal Asset Pricing,” Theory of Valuation (S. Bhattacharya and G. Constantinides, eds.) Rowman & Littlefield Publishers, Inc., 85-96. 





Shleifer, A., 1986, “Do Demand Curves for Stocks Slope Down?”, Journal of Finance 41, 579–590. 





Smidt, Seymour, 1990, “Long-Run Trends in Equity Turnover”, Journal of Portfolio Management , Fall, 66–73. 





Stickel, S., 1991, “The Ex-Dividend Day Behavior of Nonconvertible Preferred Stock Returns and Trading Volume”, Journal of Financial and Quantitative Analysis 26, 45–61. 





Stickel, S. and R. Verrecchia, 1994, “Evidence that Volume Sustains Price Changes”, Financial Analysts Journal (November-December), 57-67. 





Stiglitz, J., 1989, “Using Tax Policy to Curb Speculative Short-Term Trading”, Journal of Financial Services Research 3, 101–115. 





Summers, L. and V. Summers, 1990a, “The Case for a Securities Transactions Excise Tax”, Tax Notes (August 13), 879–884. 





Summers, L. and V. Summers, 1990b, “When Financial Markets Work Too Well: A Cautious Case for a Securities Transactions Tax”, Journal of Financial Services Research 3, 261–286. 





Tkac, P., 1999, “A Trading Volume Benchmark: Theory and Evidence”, Journal of Financial and Quantitative Analysis 34, 89–114. 





Tobin, J., 1984, “On the Eficiency of the Financial Market System”, Lloyds Bank Review 153, 1–15. 





Tobin, J., 1958, “Liquidity Preference As Behavior Towards Risk”, Review of Economic Studies 25, 68–85. 





Wang, J., 1994, “A Model of Competitive Stock Trading Volume”, Journal of Political Economy 102, 127–168. 





Woolridge, J and C. Ghosh, 1986, “Institutional Trading and Security Prices: The Case of Changes in the Composition of the S&P 500 Market Index”, Journal of Financial Research 9, 13–24. 





Ying, Charles C., 1966, “Stock Market Prices and Volume of Sales”, Econometrica 34, 676–686. 

