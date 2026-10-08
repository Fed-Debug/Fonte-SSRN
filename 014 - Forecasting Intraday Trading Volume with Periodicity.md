# Forecasting Intraday Trading Volume with Periodicity<sup>∗</sup>

Dahao Tan<sup>†</sup>, Chao Zhang<sup>‡</sup>, Haibin Zhu<sup>§</sup> 

## Abstract

We develop the Separated Periodic AutoRegressive (SPAR) model for forecasting intraday trading volume, illustrating its potential as a general framework for modeling periodic patterns without pre-specifying functional forms. Our approach treats intraday periodicity as a time-of-day fixed efect and eliminates it via the standard within-transformation. The outof-sample results indicate that SPAR significantly outperforms standard benchmarks across various assets and market conditions. Beyond forecasting, we apply the SPAR model to a dynamic Volume-Weighted Average Price (VWAP) replication strategy, thereby reducing tracking error and highlighting its value for algorithmic execution. Finally, SPAR yields an asset-specific intraday periodic curve, and a factor analysis of these estimated curves reveals that volume patterns are primarily driven by two common factors: a U-shaped curve and a morning-afternoon asymmetry. The corresponding factor loadings also help predict future VWAP-tracking errors. 

JEL Classification: C53, C58, G12, G17 

Keywords: Trading volume, intraday periodicity, panel forecasting, high-frequency data. 

## 1. Introduction

Trading volume, the total number of shares traded in a given period, plays a key role in financial markets. Understanding its patterns provides valuable insights into market dynamics. Empirical studies have established that volume is correlated with the magnitude of price changes (Karpof, 1987; Wang, 1994), the strength and persistence of price momentum (Lee and Swaminathan, 2000), and market structure (Atkins and Dyl, 1997; Anderson and Dyl, 2005). Volume also interacts with other financial series, such as stock returns (Chordia and Swaminathan, 2000), volatility (Andersen, 1996; Brailsford, 1996; Suominen, 2001), and trading costs (Goyenko et al., 2024). Others study the reaction of trading volume to public news (Darrat et al., 2007; Bollerslev et al., 2018) and link it to the economic phenomenon called staleness (Bandi et al. (2020)). 

Given its importance, accurately forecasting intraday trading volume ofers significant practical advantages. First, it enables real-time nowcasting of market trading conditions, providing timely signals on liquidity and market activity (Chordia et al., 2001, 2011). Second, it plays a central role in optimal trade execution strategies, notably the Volume-Weighted Average Price (VWAP) strategy (Berkowitz et al., 1988; Konishi, 2002; Bia lkowski et al., 2008; Humphery-Jenner, 2011). Accurate volume forecasts enable traders to break down large orders into smaller trades, thereby minimizing transaction costs and market impact. In essence, executing trades during periods of high market volume, i.e., when liquidity is abundant, can reduce trading costs and conceal trading intentions, as shown in Goyenko et al. (2024). 

A central challenge in forecasting intraday volume lies in its pronounced periodicity. The most well-documented pattern is the U-shaped curve observed across many equity markets, where trading is concentrated at the open and close (Admati and Pfleiderer, 1988; Jain and Joh, 1988). Accordingly, prominent models for intraday volume forecasting explicitly incorporate this feature. The workhorse method, Component Multiplicative Error Model (CMEM) of Brownlees et al. (2011), for instance, decomposes volume into daily, non-periodic, and periodic components. This approach, however, typically requires the functional form of the periodic component, such as a U-shape modeled by splines, to be specified ex ante. 

This pre-specification is a notable limitation, as empirical evidence reveals that a single, static U-shape fails to capture the rich diversity of intraday patterns. Prior research has already documented important deviations, such as J-shaped curves in certain assets (Lee et al., 2001; Cucuringu et al., 2025), and nested periodicities at multiple time scales linked to algorithmic trading (Broussard and Nikiforov, 2014). We also observe both U- and J-shaped patterns in our sample assets, as illustrated in Figure 1, respectively. Furthermore, intraday volume curves exhibit significant heterogeneity across markets.<sup>1</sup> This evidence underscores a critical point: relying on a pre-specified periodic curve hinders the development of a unified forecasting framework and increases the risk of model misspecification. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/6fc295095fca9b8f4dc2f1b2e9fc1049779a82c1461f9bffe62cca7ec5f3a495.jpg)



(a) Intraday trading volume periodicity of BAC.


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/aae71a05c5b6e4aa91d04c129ba6701768058d108933ae50545e01a8a12ee993.jpg)



(b) Intraday trading volume periodicity of MTB.



Figure 1: Observed average intraday trading volume at a 5-minute frequency. Panel 1a is the intraday trading volume periodicity of BAC, and Panel 1b is for MTB. The y-axis represents the normalized trading volume with a mean of one.


To address this limitation, subsequent research has explored more flexible techniques. One line of research employs state-space models with the Kalman filter, treating the unobserved periodic component as a dynamic latent variable (Chen et al., 2016b). Another prominent approach is spectral analysis, which models periodicity by decomposing the intraday curve into a combination of sinusoidal waves via Fourier analysis (Wu et al., 2025). More recently, machine learning models have been applied to the task, learning the periodic pattern implicitly from time-based features rather than explicitly modeling a separate component (Cucuringu et al., 2025). While these advanced frameworks are powerful in capturing complex intraday dynamics, they estimate the periodic component by treating it as a latent variable within a complex model or by learning it implicitly. As a result, they do not yield a directly interpretable estimate of the periodic curve conditional on exogenous variables, making it challenging to conduct a deeper structural analysis.<sup>2</sup> 

In this paper, we propose a novel framework, the Separated Periodic AutoRegressive (SPAR) model, which achieves a unified solution by reframing the problem in a novel way<sup>3</sup>. Instead of attempting to model the specific shape of the volume curve, we treat intraday periodicity as a time-of-day fixed efect. This simple but powerful re-conceptualization allows us to remove the periodic component using a robust and well-established within-transformation technique. The resulting stationary series can be modeled using a standard autoregressive framework, allowing consistent and eficient parameter estimation. 

The contributions of this paper are threefold. First, our framework serves as a data pre-processing technique that removes deterministic periodicity from the data prior to forecasting. This model-agnostic approach can be integrated into any forecasting method, from simple linear regressions to complex machine learning algorithms, ofering substantial flexibility for practical implementation. We demonstrate that this pre-processing is useful across a range of models, including OLS, Lasso, Ridge, and Random Forest. Our empirical results show that, in every case, models trained on the transformed data consistently outperform their unadjusted counterparts. 

Second, we examine the economic magnitude of the forecasting gains in a dynamic Volume-Weighted Average Price (VWAP) replication exercise. We compare SPAR with the KF benchmark, a simple OLS benchmark, and an equal-weight trading rule. SPAR reduces VWAP tracking errors relative to all three benchmarks. To assess economic relevance, we translate the reduction in tracking error into dollar values for a representative institutional order size. 

Finally, our framework provides an estimate of the intraday periodic curve conditional on explanatory variables, ofering a powerful tool for structural analysis. We leverage this result by conducting a factor analysis on the estimated curves across all assets. This analysis reveals a key empirical finding: the diverse patterns observed in the market can be attributed to two common factors: a U-shaped curve and a morning-versus-afternoon asymmetry. We further show that the corresponding factor loadings are related to average trading volume and help predict future VWAP-tracking errors. 

The remainder of this paper is organized as follows. Section 2 describes the dataset and notation. Section 3 introduces the SPAR framework, and Section 4 outlines the alternative models used for comparison. We then present our empirical analysis, beginning with an evaluation of out-of-sample forecasting performance in Section 5. Building on these results, Section 6 assesses the economic significance of our forecasts in a VWAP trading application, and Section 7 develops a factor model to analyze the estimated periodic curves. Section 8 concludes. 

## 2. Data

Our empirical analysis is based on a high-frequency intraday trading dataset containing minute-level data from April 1, 2010, to June 30, 2020, obtained from the QuantQuote database. To construct a robust and representative evaluation sample, we apply a multistage screening procedure to the intraday dataset. First, to mitigate calendar efects around holidays, all trading days with only half-day sessions were excluded, resulting in 2,557 full trading days. Second, following Zhu et al. (2023), we remove assets with zero trades on at least one trading day during the sample period, resulting in 392 initial assets. To further reduce the influence of zero trading volume, we exclude assets that had no trading activity for more than 10% of the trading time during trading days exceeding 10% of the sample period, resulting in a final sample of 305 assets. The complete list of assets is provided in Table C.9 in Appendix C. Finally, similar to Dumitru et al. (2025), assets were ranked by descending average daily trading volume. The top 10 (high-volume), middle 10 (medium-volume), and bottom 10 (low-volume) assets were selected as the primary research subjects.<sup>4</sup> This design allows us to compare performance across high-, medium-, and relatively low-volume stocks within the sample. It is not intended to represent micro-cap securities with frequent no-trade days, which are outside the scope of our high-frequency forecasting exercise. Table 1 lists the selected assets along with their corresponding average daily trading volumes. 


Table 1: List of tickers and average daily trading volume.


<table><tr><td>Ticker</td><td>Volume</td><td>Ticker</td><td>Volume</td><td>Ticker</td><td>Volume</td></tr><tr><td>BAC</td><td>118.361</td><td>KBH</td><td>3.496</td><td>MTB</td><td>0.873</td></tr><tr><td>SPY</td><td>114.984</td><td>ROST</td><td>3.457</td><td>ORLY</td><td>0.859</td></tr><tr><td>AAPL</td><td>74.315</td><td>SWKS</td><td>3.423</td><td>PSA</td><td>0.858</td></tr><tr><td>GE</td><td>56.073</td><td>CTXS</td><td>3.342</td><td>GPC</td><td>0.847</td></tr><tr><td>MSFT</td><td>40.506</td><td>ETN</td><td>3.314</td><td>AVY</td><td>0.832</td></tr><tr><td>CSCO</td><td>38.551</td><td>DE</td><td>3.293</td><td>VAR</td><td>0.830</td></tr><tr><td>INTC</td><td>38.538</td><td>ANF</td><td>3.260</td><td>AVB</td><td>0.808</td></tr><tr><td>AMD</td><td>37.827</td><td>BEN</td><td>3.215</td><td>SHW</td><td>0.795</td></tr><tr><td>PFE</td><td>33.376</td><td>PEG</td><td>3.190</td><td>LH</td><td>0.784</td></tr><tr><td>T</td><td>31.923</td><td>YUM</td><td>3.175</td><td>NBR</td><td>0.185</td></tr></table>


Note: This table reports the list of selected asset tickers and their average daily trading volume from April 1, 2010, to June 30, 2020. The unit for al results is $1 0 ^ { 6 }$ shares. 


We begin by introducing the notation used throughout the paper. Let V denote trading volume. Assets are indexed with $i \in \{ 1 , \ldots , N \}$ ; days by $t \in \{ 1 , \ldots , T \}$ ; each day is divided into K equally spaced intervals indexed by $k \in \{ 1 , \ldots , K \}$ , with interval length $\Delta _ { K } = 1 / K$ Accordingly, $V _ { i , t , k }$ denotes the trading volume of asset i at interval k on day t. Besides, we apply a logarithmic transformation to all observations. For observations with zero trading volume, $V _ { i , t , k } = 0$ , we first add 1 to them before taking the logarithm. 

Selecting the time interval for forecasting requires careful consideration. As Satish et al. (2014) point out, the shorter the time interval used for forecasting, the greater the forecast variance. This occurs because trading volume exhibits considerable volatility over shorter time intervals, particularly in the presence of block or odd-lot trades. To balance granularity and stability, we use 5-minute average trading volume, yielding 78 observations per trading day (based on 6.5 trading hours). This sampling frequency is commonly used in the financial literature, including Liu et al. (2015) and Dumitru et al. (2025). 

Figure 2 summarizes the fundamental time-series properties of the log-transformed trading volume in our dataset. The autocorrelation plots, in particular, reveal two distinct and complementary patterns that are critical for forecasting. The Average Intraday ACF plot (Figure 2c) reveals strong and significant autocorrelation at short lags. This indicates that trading volume in recent intervals is highly informative about current volume, highlighting the importance of intraday persistence and momentum. Simultaneously, the Average Crossday ACF plot (Figure 2d) shows that the correlation between volumes at the same time of day remains high across many preceding days, demonstrating the importance of cross-day dependence. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/1621c7c04776b52f0ff9ebf3800a54257b95df1c7d955d599bee8f66e3862831.jpg)



(a) Daily average trading volume


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/0a2ccd5cc4e11f7960aa0b38e8581ec1d9e4091b6e624d578fb603fcd835c632.jpg)



(b) Distribution of trading volume


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/0486331c58c7f50847c0e4387d23ef6f39ef534ea84bff3ce0d6adf370c70a18.jpg)



(c) Intraday autocorrelation function


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/8bb17fda5974ed9d5ca5e13210d8f1d2c6de1c51063dde97a71aca8c12654a85.jpg)



(d) Cross-day autocorrelation function



Figure 2: Time-series characteristics of intraday trading volume. This figure summarizes the main statistical properties of 5-minute log trading volume for the 30 sample assets in our datasets. Panel 2a plots the average daily trading volume over time for the full sample together with the highest- and lowest-volume portfolios. Panel 2b presents the cross-sectional distribution of intraday trading volume. Panels 2c and 2d show intraday and cross-day autocorrelation functions (95% CI in red) of intraday trading volumes, respectively


## 3. Proposed Method

We begin by outlining the forecasting framework. To simplify notation, we omit the asset index i throughout this section. Since we focus on forecasting, we follow Andersen et al. (2019) and let trading volume exhibit a periodic pattern with a one-day cycle. We write 

$$
V _ {t, k} = \tilde {V} _ {t, k} F _ {t, k},\tag{1}
$$

where $F : \mathbb { N } _ { + } \times [ 0 , 1 ] \to \mathbb { R } _ { + }$ is an almost surely positive time-of-day component and $\tilde { V } _ { t , k }$ denotes the stationary component. 

Following Andersen et al. (2019) and Andersen et al. (2024), the periodic term depends only on the time of day, so we set $F _ { t , k } = F _ { k }$ for grid points $k = 1 , \ldots , K$ . For identification, we impose $\textstyle \int _ { 0 } ^ { 1 } F _ { k } \mathrm { d } k = 1 ^ { 5 }$ . Under this specification, intraday volume across trading days is driven by the same time-of-day component $F _ { ; }$ , while $\tilde { V } _ { t , k }$ captures the scale. 

Relation to CMEM. The decomposition in (1) nests the Component Multiplicative Error Model (CMEM) of Brownlees et al. (2011), built on Engle (2002). CMEM writes 

$$
V _ {t, k} = \underbrace {\eta_ {t} \mu_ {t , k} \epsilon_ {t , k}} _ {\tilde {V} _ {t, k}} \cdot \underbrace {\phi_ {k}} _ {F _ {k}} = \tilde {V} _ {t, k} F _ {k},
$$

where $\phi _ { k }$ is a deterministic intraday periodic component, $\eta _ { t }$ and $\mu _ { t , k }$ capture persistent dynamics across and within days, and $\epsilon _ { t , k }$ is an i.i.d. innovation. The crucial diference, however, lies in the treatment of the periodic component. CMEM relies on a pre-specified functional form for $\phi _ { k }$ , forcing the explicit and costly estimation of all components via Generalized Method of Moments. By contrast, SPAR treats $F _ { k }$ nonparametrically and removes it with a simple within-transformation, thereby avoiding complex joint estimation and reducing the risk of misspecification when the true periodic shape deviates from a chosen parametric form. 

We start with the following log transformation: 

$$
\log V _ {t, k} = \log \tilde {V} _ {t, k} + \log F _ {k}.\tag{2}
$$

Define $y _ { t , k } = \log V _ { t , k } , \tilde { y } _ { t , k } = \log \tilde { V } _ { t , k } ,$ , and $f _ { k } \ = \ \log { \cal F } _ { k }$ . Let $X _ { t , k - 1 }$ denote predictors available up to time $t + ( k - 1 ) \Delta _ { K }$ , and let $h ( \cdot )$ be a (possibly nonlinear) mapping from predictors to the conditional mean of $\tilde { y } _ { t , k } { : }$ 

$$
\tilde {y} _ {t, k} = h (X _ {t, k - 1}) + u _ {t, k}
$$

where u are i.i.d. errors over t and k. Throughout this article, we assume strict exogeneity, i.e., for all $t \geq 0$ and $k = 1 , \ldots , K$ 2 

$$
\mathbb {E} \left(u _ {t, k} \Big | f _ {k ^ {\prime}}, X _ {t ^ {\prime}, k ^ {\prime}}, \text { for   any } t ^ {\prime} \geq 0 \text { and } k ^ {\prime} \in [ 1, K ]\right) = 0.\tag{3}
$$

This implies that the error term has a mean of zero conditional on past, current, and future values of X. Given all notations above, we could rewrite (2) as 

$$
y _ {t, k} = \tilde {y} _ {t, k} + f _ {k} = h (X _ {t, k - 1}) + f _ {k} + u _ {t, k}.\tag{4}
$$

Hence, forecasting reduces to estimating $h ( \cdot )$ so that 

$$
\mathbb {E} \big [ y _ {t, k} \mid \mathcal {F} _ {t, k - 1} \big ] = h (X _ {t, k - 1}) + f _ {k},
$$

where $\mathcal { F } _ { t , k - 1 }$ is the σ-field generated by information available up to time $t + ( k - 1 ) \Delta _ { K }$ 

A convenient baseline takes h to be linear (extensions appear in Section 4). Stacking (4) within day t yields 

$$
\mathbf {y} _ {t} = \mathbf {1} _ {K} \beta_ {0} + \mathbf {X} _ {t} \boldsymbol {\beta} + \mathbf {f} + \mathbf {u} _ {t},\tag{5}
$$

where $\mathbf { y } _ { t } = ( y _ { t , 1 } , \ldots , y _ { t , K } ) ^ { \prime }$ is a K-dimensional vector of the log trading volume, ${ \bf 1 } _ { K }$ is a $K \mathfrak { - }$ dimensional vector of ones, $\beta = ( \beta _ { 1 } , \ldots , \beta _ { p } ) ^ { \prime }$ is a p-dimensional vector of loadings, and $\beta _ { 0 }$ is an intercept. Here, $\mathbf { X } _ { t } = ( X _ { t , 0 } ^ { \prime } , X _ { t , 1 } ^ { \prime } , . . . , X _ { t , K - 1 } ^ { \prime } ) ^ { \prime }$ is a $K \times p$ matrix of $\dot { p }$ explanatory variables available upon one grid point prior to $y .$ with $X _ { t , k } = ( x _ { t , k } ^ { 1 } , \ldots , x _ { t , k } ^ { p } )$ for all $k = 0 , \ldots , K - 1$ The vectors $\mathbf { f } = ( f _ { 1 } , \ldots , f _ { K } ) ^ { \prime }$ and $\mathbf { u } _ { t } = ( u _ { t , 1 } , \ldots , u _ { t , K } ) ^ { \prime }$ collect the time-of-day fixed efects and disturbances, respectively. 

## 3.1. Periodicity separation and regression

Naturally, (5) can be viewed as a panel data model, with a time-series dimension over training days and a cross-sectional dimension over within-day grids. The periodic component f, which varies by time-of-day k but not by day t, is analogous to an individual-specific fixed efect in classical panel data. Following standard practice for consistently estimating panel models with fixed efects, we apply a within transformation to remove the periodic component, thereby allowing the model to be consistently estimated. 

We let W denote the cross-day averaging window. For any process $Z _ { t , k }$ , define the crossday mean at time-of-day k by 

$$
\bar {Z} _ {t, k} = \frac {1}{W} \sum_ {\omega = 1} ^ {W} Z _ {t - \omega + 1, k}, \quad \dot {Z} _ {t, k} = Z _ {t, k} - \bar {Z} _ {t, k},
$$

and, stacking within day t, set $\dot { \mathbf Z } _ { t } = \mathbf Z _ { t } - \bar { \mathbf Z } _ { t }$ . Applying this within (demeaning) operator to (4) yields, for $t = 1 , \ldots , W$ and $k = 1 , \ldots , K$ 2 

$$
\dot {y} _ {t, k} = \left(X _ {t, k - 1} - \bar {X} _ {t, k - 1}\right) \boldsymbol {\beta} + \left(u _ {t, k} - \bar {u} _ {t, k}\right) = \dot {X} _ {t, k - 1} \boldsymbol {\beta} + \dot {u} _ {t, k},\tag{6}
$$

since the periodic component satisfies ${ \dot { f } } _ { k } = f _ { k } - W ^ { - 1 } \sum _ { t = 1 } ^ { W } f _ { k } = 0$ , and the intercept is likewise removed. In matrix form, stacking observations within day t, 

$$
\dot {\mathbf {y}} _ {t} = \mathbf {y} _ {t} - \bar {\mathbf {y}} _ {t} = \dot {\mathbf {X}} _ {t} \boldsymbol {\beta} + \dot {\mathbf {u}} _ {t}.
$$

The within-transformation reduces the problem to a standard panel forecasting regression (cf. Zhu et al. (2023)), and $\beta$ can then be estimated by OLS on the within-transformed data: 

$$
\hat {\boldsymbol {\beta}} = \left(\sum_ {t = 1} ^ {W} \dot {\mathbf {X}} _ {t} ^ {\prime} \dot {\mathbf {X}} _ {t}\right) ^ {- 1} \left(\sum_ {t = 1} ^ {W} \dot {\mathbf {X}} _ {t} ^ {\prime} \dot {\mathbf {y}} _ {t}\right).\tag{7}
$$

Under the strict exogeneity condition in (3) and standard regularity $( \mathrm { e . g . , } K \times W \to \infty ) , { \hat { \beta } }$ is consistent. 

For simplicity, Equations (5) and (7) use a common coeficient vector, $\beta ,$ across all intraday intervals. Since the information available for forecasting difers across the opening, middle, and closing sessions, Appendix D considers an extension that estimates a separate coeficient vector for each session. The results show that this extension yields performance comparable to that of our proposed models. We therefore retain the common-coeficient specification as the baseline. 

Given $\hat { \beta }$ from the within-transformed regression, we first recover the unnormalized timeof-day fixed efect by 

$$
\widehat {f} _ {k} ^ {\mathrm{raw}} = \bar {y} _ {t, k} - \bar {X} _ {t, k - 1} \hat {\pmb {\beta}}.
$$

Since the intercept is removed by the within-transformation, ${ \widehat { f } } _ { k } ^ { \mathrm { r a w } }$ is identified only up to a common additive constant. We therefore normalize it to obtain the identifiable periodic curve by 

$$
\widehat {F} _ {k} = \frac {K \exp (\widehat {f} _ {k} ^ {\mathrm{raw}})}{\sum_ {j = 1} ^ {K} \exp (\widehat {f} _ {j} ^ {\mathrm{raw}})} = \frac {K \exp (\bar {y} _ {t , k} - \bar {X} _ {t , k - 1} \hat {\pmb {\beta}})}{\sum_ {j = 1} ^ {K} \exp (\bar {y} _ {t , j} - \bar {X} _ {t , j - 1} \hat {\pmb {\beta}})}.\tag{8}
$$

for all k and suficiently large $W ^ { 6 }$ . By construction, the estimated curve satisfies the discrete normalization $\begin{array} { r } { \frac { 1 } { K } \sum _ { k = 1 } ^ { K } \widehat { F } _ { k } = 1 } \end{array}$ . Since F is assumed to be static over a short interval of trading days, (8), in fact, provides another way to estimate the periodicity component of volume, as a by-product. 

Remark 1. This normalization fixes the scale of the periodic component but does not afect the estimation of $\hat { \beta }$ , because $\hat { \beta }$ is obtained from the within-transformed regression before $\widehat { F } _ { k }$ is constructed. It also does not afect the shape of the curve. $I f \ \widehat { f } _ { k } ^ { \mathrm { r a w } }$ is shifted by any common constant $^ { c , }$ the normalized curve is unchanged since 

$$
\frac {K \exp (\widehat {f} _ {k} ^ {\mathrm{raw}} + c)}{\sum_ {j = 1} ^ {K} \exp (\widehat {f} _ {j} ^ {\mathrm{raw}} + c)} = \frac {K \exp (\widehat {f} _ {k} ^ {\mathrm{raw}})}{\sum_ {j = 1} ^ {K} \exp (\widehat {f} _ {j} ^ {\mathrm{raw}})}.
$$

Thus, Equation $( \delta )$ should be viewed as the normalized estimate of the periodic shape, rather than as an additional restriction imposed during the estimation $o f { \hat { \boldsymbol { \beta } } }$ 

The final one-step-ahead forecast is constructed by combining the model’s output with the estimated periodic component, as below<sup>7</sup> 

$$
\hat {\mathbf {y}} _ {t + 1} = \dot {\mathbf {X}} _ {t + 1} \hat {\boldsymbol {\beta}} + \bar {\mathbf {y}} _ {t}, \quad \mathrm{or,} \quad \hat {y} _ {t + 1, k + 1} = (X _ {t + 1, k} - \bar {X} _ {t, k}) \hat {\boldsymbol {\beta}} + \bar {y} _ {t, k + 1} \quad \mathrm{for} \quad k = 0, \ldots , K - 1.
$$

Remark 2. In the forecasting formula above, the bars are computed using a rolling window that ends on day t. Hence, $\bar { X } _ { t , k }$ and $\bar { y } _ { t , k + 1 }$ are known when forecasting $y _ { t + 1 , k + 1 }$ We do not use $\bar { y } _ { t + 1 , k + 1 }$ because it would include the target value $y _ { t + 1 , k + 1 }$ and therefore introduce look-ahead bias. For the same timing reason, the demeaned predictor uses $\bar { X } _ { t , k }$ rather than a mean computed with day $t + 1$ information. 

This means that we use a rolling forward within-transformation in our forecasting process. Our implementation treats this as an online forecasting model. The coeficient vector $\hat { \beta }$ is estimated once at the end of day t. Then, throughout day $t + 1$ , as new information arrives at each time grid k, the model generates a forecast for the subsequent point, $k + 1$ 

Following the above setting, within-transformation is designed to isolate the predictable intraday periodic patterns from the more random daily fluctuations in trading volume. By subtracting the average volume at each specific time of day, we can focus on forecasting the stationary component, simplifying our forecasting task. In summary, we can refer to this model as the Separated Periodic AutoRegressive model, abbreviated as SPAR. 

Remark 3. In Appendix A, we consider an alternative approach that first estimates the periodic component, $\hat { F } _ { i }$ , and then regresses the adjusted volume, $y _ { t } - { \hat { f } } _ { : }$ , on the unadjusted predictors, X<sub>t</sub>. Appendix A also provides the corresponding suficient condition for nonlinear models. The empirical results in Table A.8 are consistent with this omitted-periodicity mechanism and show that adjusting only the dependent variable generally produces less accurate forecasts than applying the within-transformation to both the dependent variable and the predictors. 

## 3.2. Feature description

To keep the model parsimonious and operational, we utilize explanatory variables directly obtainable from market data. Motivated by the intraday and cross-day autocorrelation patterns in Figure 2, we adopt a HAR-style specification (Corsi, 2009) that captures persistence over multiple horizons. 

We first focus on intraday lags as trading volume exhibits short-horizon persistence in continuous markets (cf. Brownlees et al. (2011)). Guided by the intraday ACF, we include the most informative recent history: the last six intraday observations (30 minutes at 5-minute sampling), 

$$
\mathcal {X} _ {1} = \left\{y _ {t, k - 1}, \dots , y _ {t, k - 6} \right\}.
$$

This choice captures the most influential short-term dynamics, as the autocorrelation is still substantial at lag 6. Thus, when forecasting the first interval of day $t \left( k = 1 \right)$ , the intraday set becomes $\mathcal { X } _ { 1 } = \left\{ y _ { t - 1 , K } , y _ { t - 1 , K - 1 } , . . . , y _ { t - 1 , K - 5 } \right\}$ 

Secondly, we incorporate cross-day information. In the spirit of the monthly component in HAR (Corsi, 2009), we include lags from the previous 22 trading days to capture this monthly efect. That is, 

$$
\mathcal {X} _ {2} = \left\{y _ {t - 1, k}, \dots , y _ {t - 2 2, k} \right\}.
$$

In our empirical experiment, the results are robust to the choice of cross-day lags within the range of 5 to 30. 

Thirdly, we also incorporate volatility as a predictor, given extensive evidence of its tight linkage with trading volume. For instance, Brooks (1998) employed Granger causality tests to examine the bidirectional relationship between trading volume and volatility, finding that volatility exerts a stronger, more persistent causal influence on trading volume. Xu et al. (2006) estimate a time-consistent VAR model for volatility and volume, reporting that volatility and trading volume are highly correlated with past volatility and volume. These findings motivate the inclusion of a volatility proxy among the regressors. 

Because spot volatility is latent, we adopt the Optimal Candlestick (OK) range-based estimator of Li et al. (2024). Let ${ \mathcal { T } } _ { K , j } = [ ( j - 1 ) \Delta _ { K } , j \Delta _ { K } ]$ denote the j-th intraday interval on day $t , j = 1 , \ldots , K$ . Let $O _ { j } , C _ { j } , H _ { j }$ , and $L _ { j }$ be the open, close, high, and low of log prices over $\mathcal { T } _ { K , j }$ . Define the scaled log return and range 

$$
r _ {j} = \frac {C _ {j} - O _ {j}}{\sqrt {\Delta_ {K}}}, \quad \omega_ {j} = \frac {H _ {j} - L _ {j}}{\sqrt {\Delta_ {K}}}
$$

respectively. The OK estimator combines these into a spot volatility proxy (for any $\tau \in \mathcal { T } _ { K , j } )$ 

$$
\hat {\sigma} _ {\tau} = 0. 8 1 1 \omega_ {j} - 0. 3 6 9 | r _ {j} |, \quad \text { for   any } \tau \in \mathcal {I} _ {K, j}.\tag{9}
$$

The weights are optimally determined by minimizing the asymptotic variance. For any missing value, we set $\hat { \sigma } _ { t , k } = \hat { \sigma } _ { t , k - 1 }$ . To parallel the intraday volume lags, we include six recent volatility lags, 

$$
\mathcal {X} _ {3} = \{\hat {\sigma} _ {t, k - 1}, \ldots , \hat {\sigma} _ {t, k - 6} \}.
$$

Finally, we combine these three sets of features to construct our model’s full set of explanatory variables. This unified feature set, $\mathbf { X } = { \mathcal { X } } _ { 1 } \cup { \mathcal { X } } _ { 2 } \cup { \mathcal { X } } _ { 3 }$ , captures the key stylized facts of intraday trading volume: short-horizon persistence (recent intraday lags), cross-day dependence at the same time-of-day, and the documented influence of market volatility. 

## 4. Alternative Models

This section describes the benchmark and alternative models—both linear and nonlinear—used in our empirical study<sup>8</sup>. Our objective is to fit a forecasting function h such that 

$$
g (\mathbf {y} _ {t}) = h \big (g (\mathbf {X} _ {t}) | \theta \big) + \mathbf {e} _ {t},\tag{10}
$$

where $\theta$ are some parameters of the corresponding models and e are errors. $g$ is a transformation function, which can be either $g ( x ) = x$ or within transformation. 

## 4.1. Benchmark: CMEM with Kalman filter

We adopt the CMEM as the benchmark, a widely used model for intraday trading volume forecasting. Because the CMEM’s components are not directly observable, we follow Chen et al. (2016b), who recast the CMEM in state-space form and estimate it using a Kalman filter. Specifically, a logarithmic transformation renders the model linear–Gaussian, enabling parameter estimation by the expectation–maximization (EM) algorithm. During the E-step, the Kalman filter and smoothing techniques are utilized to compute the expected values of the posterior distribution of the hidden states. All model parameters are updated in closed form in the M-step based on these expected values. Empirical studies in Chen et al. (2016b) show that the proposed method significantly outperforms the CMEM model. For brevity, we use KF to denote this method. Since the KF model does not require additional feature inputs, we have fixed its sample window to 22 days. 

## 4.2. Lasso regression

Lasso (Least Absolute Shrinkage and Selection Operator), proposed by Tibshirani (1996), is a widely employed regularization technique in linear model estimation. Its core principle is to augment the least-squares loss function with a regularization term based on the sum of the absolute values of the regression coeficients. This regularization term imposes a penalty that tends to shrink a subset of the regression coeficients to exactly zero. Consequently, it automatically selects features by retaining only the most significant predictors while promoting model sparsity. The objective of Lasso is to solve the following: 

$$
\hat {\beta} ^ {l a s s o} = \operatorname{argmin} \left\{\| y - \mathbf {X} \beta \| ^ {2} + \lambda \| \beta \| _ {1} \right\}
$$

where λ is a hyperparameter that controls the strength of the penalty. The magnitude of λ directly governs the strength of the regularization penalty applied to the model. The larger the value of λ is, the more coeficients shrink to zero. In this study, the model automatically determines the range of λ values when λ is unconstrained, and selects the optimal λ based on the validation-set prediction error from the in-sample data. 

## 4.3. Ridge regression

Ridge regression, proposed by Hoerl and Kennard (1970), is a specialized, improved leastsquares estimation technique designed to address multicollinearity. When high correlation exists among independent variables, standard ordinary least squares estimators may become unstable and exhibit excessive variance. To mitigate this issue, Ridge Regression introduces a penalty term on the sum of squared regression coeficients into the OLS objective function, thereby reformulating the problem as a constrained minimization. Its core optimization objective is to minimize a regularized combination of the residual sum of squares and the squared norm of coeficients: 

$$
\hat {\beta} ^ {r i d g e} = a r g m i n \left\{\| y - \mathbf {X} \beta \| ^ {2} + \lambda \| \beta \| _ {2} ^ {2} \right\}
$$

where λ is a hyperparameter that controls the strength of the penalty. A larger λ compresses more coeficients to approach zero without ever reaching exact zero, significantly reducing model variance while introducing additional bias. The choice of λ follows the same protocol as in Lasso. 

## 4.4. Random Forest

Random Forest (RF), proposed by Breiman (2001), is an ensemble algorithm used for classification and regression tasks. It enhances model performance by constructing multiple decision trees and aggregating their outputs. The core principle of the algorithm integrates two strategies: Bootstrap Aggregation (Bagging) and random feature selection, efectively mitigating the overfitting risk inherent in single decision trees and improving generalization capability. 

In regression tasks, RF employs resampling techniques to generate multiple subsets from the original dataset. Each subset is used to train an individual base learner, and the final prediction is derived by averaging the outputs of all learners. Since the base model is a tree structure, RF inherently possesses strong nonlinear modeling capabilities, enabling it to capture complex interactions and nonlinear relationships among variables. 

In this study, the RF model is configured with 500 trees. The splitting criterion at each node is based on the minimization of Mean Squared Error (MSE), and the number of features considered for splitting at each node is set to $m _ { t r y } = p / 3$ , where p is the total number of input features. 

## 4.5. A summary of models

We consider four feature combinations: (1) intraday variables, (2) intraday and crossday variables, (3) intraday and volatility variables, and (4) intraday, cross-day, and volatility variables. For OLS and SPAR, we report all four specifications separately. For Lasso, Ridge, Random Forest, and their SPAR-based versions, we estimate each method under all four feature combinations. The complete results are reported in Table C.10. 

The main tables report the best feature configuration for each method. We select the configuration that obtains the best value in the largest number of the following three metrics: out-of-sample $R ^ { 2 }$ , RMSE, and RMAE. If two configurations have the same count, we choose the one with fewer predictors. This rule selects specification (3) for $\mathrm { L A } _ { \mathrm { S P } }$ and $\mathrm { R F _ { S P } }$ specification (1) for $\mathrm { R I } _ { \mathrm { S P } }$ , and specification (4) for Lasso, Ridge, and RF. All variables in the models were standardized<sup>9</sup>, and when both within-transformation and standardization are required, we first apply the within-transformation. Table 2 summarizes the explanatory variables used in the forecasting model and their notations. 


Table 2: Feature Combinations and Model Notation


<table><tr><td>Feature Combinations</td><td>Models</td></tr><tr><td>Intraday</td><td>OLS1, SPAR1 and RISP</td></tr><tr><td>Intraday and cross-day</td><td>OLS2 and SPAR2</td></tr><tr><td>Intraday and volatility</td><td>OLS3, SPAR3, LASP and RFSP</td></tr><tr><td>Intraday, cross-day and volatility</td><td>OLS4, SPAR4, Lasso, Ridge and RF</td></tr></table>


Note: This table summarizes the explanatory variables used in the forecasting models. The symbols $\mathrm { L A } _ { \mathrm { S P } } .$ $\mathrm { R I } _ { \mathrm { S P } }$ , and $\mathrm { R F _ { S P } }$ indicate that we integrated the SPAR framework into machine learning methods, which means each of these models (Lasso, Ridge, and Random Forest) is trained on within-transformed data. $\mathrm { S P A R _ { 2 } }$ and $\mathrm { S P A R _ { 4 } }$ are estimated using the SPJ correction described below. 


For $\mathrm { S P A R _ { 2 } }$ and $\mathrm { S P A R _ { 4 } }$ , after the within-transformation, the transformed lagged variables can be correlated with the transformed error term, which violates the strict exogeneity condition in Equation (3). As a result, the fixed-efects estimator can be biased. This is the usual Nickell-bias problem in a dynamic fixed-efects model. To reduce this bias, we use the split-panel jackknife (SPJ) estimator proposed by Mei et al. (2026). Let $\widehat { \beta } ^ { \mathrm { F E } }$ denote the fixed-efects estimate based on the full training window, and let $\widehat { \beta } _ { a } ^ { \mathrm { F E } }$ and $\widehat { \beta } _ { b } ^ { \mathrm { F E } }$ denote the estimates based on the first and second halves of the training window, with $\lfloor W / 2 \rfloor$ and $\lceil W / 2 \rceil$ windows, respectively. The SPJ estimator is 

$$
\hat {\beta} ^ {\mathrm{SPJ}} = 2 \hat {\beta} ^ {\mathrm{FE}} - (\hat {\beta} _ {a} ^ {\mathrm{FE}} + \hat {\beta} _ {b} ^ {\mathrm{FE}}) / 2.
$$

Consequently, we obtain 15 comparable models. We employ a single-asset training scheme within our training framework, in which each asset is trained and predicted separately using its own dedicated model. 

## 5. Out-of-Sample Performance

In this section, we evaluate the comparative performance of the forecasting methods. We start forecasting on the 91st trading day. We conduct the out-of-sample evaluation over 2,376 trading days. We are excluding the remaining 91 days and treating this as a termination. The evaluation proceeds in three steps. 

First, we assess the predictive accuracy of each model using out-of-sample $R ^ { 2 }$ , a metric that compares the model’s mean-squared prediction error to that of a benchmark forecast based on the historical average. The out-of-sample $R ^ { 2 }$ is computed by 

$$
R _ {i} ^ {2} = 1 - \frac {\sum_ {t \in \mathcal {T}} \sum_ {k = 1} ^ {K} (V _ {i , t , k} - \hat {V} _ {i , t , k}) ^ {2}}{\sum_ {t \in \mathcal {T}} \sum_ {k = 1} ^ {K} (V _ {i , t , k} - \bar {V} _ {i , t , k}) ^ {2}},
$$

where $\tau$ is the collection of all forecast days in the test samples, and $\bar { V } _ { i , t , k }$ is the historical average trading volume of each asset i in the interval k based on the optimal training window, $W _ { t } ^ { * }$ , obtained from each model update. That is, $\begin{array} { r } { \bar { V } _ { i , t , k } = ( W _ { t } ^ { * } ) ^ { - 1 } \sum _ { \omega = 1 } ^ { W _ { t } ^ { * } } V _ { i , t - \omega , k } } \end{array}$ . The details of the choice of tuning parameters and the model update are illustrated in Appendix B. 

Remark 4. A key characteristic of the out-of-sample $R ^ { 2 }$ is that it is not bounded at zero and can take on negative values. Specifically, a negative $R ^ { 2 }$ indicates that the forecasting model yields a larger prediction error than the simple historical mean, suggesting the model’s predictions are worse than this benchmark. See discussion in Section 1.8 of Gu et al. (2020). 

Second, we treat the CMEM with a Kalman filter (KF) as our benchmark model to assess whether the proposed models significantly improve over a sophisticated baseline. We then evaluate the relative predictive performance of our proposed models against the benchmark forecasts. To this end, we define a KF-benchmark $R ^ { 2 }$ as follows: 

$$
R _ {\mathrm{KF}, i} ^ {2} = 1 - \frac {\sum_ {t \in \mathcal {T}} \sum_ {k = 1} ^ {K} (V _ {i , t , k} - \hat {V} _ {i , t , k}) ^ {2}}{\sum_ {t \in \mathcal {T}} \sum_ {k = 1} ^ {K} (V _ {i , t , k} - \hat {V} _ {i , t , k} ^ {K F}) ^ {2}},
$$

where $\hat { V } _ { i , t , k } ^ { K F }$ represents the forecast generated by the benchmark KF model. The metric $R _ { \mathrm { K F } } ^ { 2 }$ quantifies how much a proposed model’s forecasting accuracy outperforms or underperforms the benchmark KF model. Compared to KF predictions, superior forecasts should yield a lower out-of-sample mean squared error, which results in $R _ { \mathrm { K F } } ^ { 2 }$ values approaching 1. Conversely, a negative value signifies that the model’s predictions are less accurate than the benchmark’s. 

While the out-of-sample $R ^ { 2 }$ is informative for evaluating performance, they have certain limitations. Primarily, these metrics quantify the relative improvement over a benchmark rather than the absolute magnitude of the prediction error. Furthermore, they do not provide a statistical basis for concluding whether one model is significantly better, which is critical when comparing competing models. 

We consider two loss functions to address the first issue: the relative mean squared error (RMSE) and the relative mean absolute error (RMAE). The former measures the average of the squares of the relative prediction errors, particularly sensitive to larger errors, while the latter measures the average of the absolute errors and is consequently more robust to outliers. Using these functions allows for a direct assessment of the size of forecasting errors and will form the basis for subsequent statistical tests of predictive ability. 

$$
\mathrm{RMSE} _ {i} = \frac {1}{K \times N _ {\mathcal {T}}} \sum_ {t \in \mathcal {T}} \sum_ {k = 1} ^ {K} \left(\frac {V _ {i , t , k} - \hat {V} _ {i , t , k}}{\bar {V} _ {i , t}}\right) ^ {2}, \quad \mathrm{RMAE} _ {i} = \frac {1}{K \times N _ {\mathcal {T}}} \sum_ {t \in \mathcal {T}} \sum_ {k = 1} ^ {K} \left| \frac {V _ {i , t , k} - \hat {V} _ {i , t , k}}{\bar {V} _ {i , t}} \right|.
$$

where $\begin{array} { r } { \bar { V } _ { i , t } = K ^ { - 1 } \sum _ { k = 1 } ^ { K } V _ { i , t , k } } \end{array}$ is the average intraday trading volume<sup>10</sup> and $N _ { \mathcal { T } }$ is the number of forecast days in the test samples. 

To address the second limitation and compare multiple forecasting models simultaneously, we employ the Model Confidence Set (MCS) procedure of Hansen et al. (2011). The MCS methodology ofers significant advantages over traditional pairwise comparison tests. It does not require the pre-specification of a benchmark model. Instead, it identifies a subset of models, $\widehat { { \mathcal { M } } ^ { * } }$ , that contains the best-performing models with a given confidence level. 

Finally, we implement the MCS procedure to identify a robust set of models. We begin with an initial set of models, $\mathcal { M } ^ { 0 }$ , and their associated forecasting errors, $\mathit { L } _ { \ell , \tau }$ , for model ℓ at every forecast point $\tau .$ The relative performance between models $\ell$ and $\ell ^ { \prime }$ is measured by their loss diferential, $d _ { \ell \ell ^ { \prime } , \tau } = L _ { \ell , \tau } - L _ { \ell ^ { \prime } , \tau }$ . The objective is to identify the set of superior models, defined as 

$$
\mathcal {M} ^ {*} = \left\{\ell \in \mathcal {M} ^ {0}: \mathbb {E} \left[ d _ {\ell \ell^ {\prime}, \tau} \right] \leq 0, \text {for all} \ell^ {\prime} \in \mathcal {M} ^ {0} \right\}.
$$

The MCS is a sequential testing procedure that eliminates the worst-performing models at each step. The process starts with the full set $\mathcal { M } = \mathcal { M } ^ { 0 }$ and tests the null hypothesis of equal predictive ability, $H _ { 0 } : \mathbb { E } [ d _ { \ell \ell ^ { \prime } , \tau } ] = 0$ for all $\ell , \ell ^ { \prime } \in \mathcal { M }$ . If the null hypothesis is not rejected at a significance level $\alpha ,$ the procedure stops, and the current set M constitutes the final MCS, denoted $\widehat { \mathcal { M } _ { 1 - \alpha } ^ { * } }$ . If the hypothesis is rejected, the model with the poorest performance is eliminated, and the test is repeated on the reduced set. This iterative process continues until the null hypothesis is not rejected. 

For the hypothesis testing, we utilize the range statistic 

$$
T _ {R, \mathcal {M}} = \max _ {\ell , \ell^ {\prime} \in \mathcal {M}} \frac {| \bar {d} _ {\ell \ell^ {\prime}} |}{\sqrt {\widehat {\mathrm{var}} (\bar {d} _ {\ell \ell^ {\prime}})}},
$$

where $\bar { d } _ { \ell \ell ^ { \prime } }$ is the sample mean of the loss diferentials between models $\ell ^ { \prime }$ and $\ell ,$ and $\widehat { \mathrm { v a r } } \left( \bar { d } _ { \ell \ell ^ { \prime } } \right)$ is an estimate of its variance. We obtain its p-values via a block bootstrap procedure with 5,000 resamples. 

## 5.1. Results for $R ^ { 2 }$

We begin our evaluation by examining the out-of-sample $R ^ { 2 }$ and the benchmarked $R _ { \mathrm { K F } } ^ { 2 } .$ Aggregate results are shown in Table 3, and asset-level results are presented in Tables C.11 and C.12 in the Appendix C. All results reveal a clear and consistent finding, i.e., the within-transformation significantly improves forecasting performance across assets. 


Table 3: Average Out-of-sample $R ^ { 2 }$ and $R _ { \mathrm { K F } } ^ { 2 }$


<table><tr><td></td><td>Level</td><td>KF</td><td><eq>\text{SPAR}_1</eq></td><td><eq>\text{OLS}_1</eq></td><td><eq>\text{SPAR}_2</eq></td><td><eq>\text{OLS}_2</eq></td><td><eq>\text{SPAR}_3</eq></td><td><eq>\text{OLS}_3</eq></td><td><eq>\text{SPAR}_4</eq></td><td><eq>\text{OLS}_4</eq></td><td><eq>\text{LA}_{\text{SP}}</eq></td><td>Lasso</td><td><eq>\text{RI}_{\text{SP}}</eq></td><td>Ridge</td><td><eq>\text{RF}_{\text{SP}}</eq></td><td>RF</td></tr><tr><td rowspan="4"><eq>R^2</eq></td><td>Top.</td><td>0.251</td><td>0.291</td><td>0.107</td><td>0.285</td><td>0.166</td><td>0.295</td><td>0.127</td><td>0.288</td><td>0.188</td><td>0.263</td><td>0.164</td><td>0.255</td><td>0.150</td><td>0.273</td><td>0.182</td></tr><tr><td>Mid.</td><td>0.300</td><td>0.321</td><td>0.146</td><td>0.309</td><td>0.206</td><td>0.318</td><td>0.161</td><td>0.311</td><td>0.219</td><td>0.271</td><td>0.187</td><td>0.267</td><td>0.160</td><td>0.284</td><td>0.194</td></tr><tr><td>Bot.</td><td>0.226</td><td>0.262</td><td>0.006</td><td>0.253</td><td>0.139</td><td>0.265</td><td>0.023</td><td>0.257</td><td>0.150</td><td>0.233</td><td>0.122</td><td>0.223</td><td>0.106</td><td>0.228</td><td>0.131</td></tr><tr><td>Avg.</td><td>0.259</td><td>0.291</td><td>0.087</td><td>0.282</td><td>0.170</td><td>0.293</td><td>0.103</td><td>0.285</td><td>0.186</td><td>0.256</td><td>0.158</td><td>0.248</td><td>0.139</td><td>0.262</td><td>0.169</td></tr><tr><td rowspan="4"><eq>R_{\text{KF}}^2</eq></td><td>Top.</td><td>/</td><td>0.050</td><td>-0.227</td><td>0.043</td><td>-0.147</td><td>0.053</td><td>-0.198</td><td>0.046</td><td>-0.106</td><td>0.003</td><td>-0.161</td><td>-0.007</td><td>-0.187</td><td>0.027</td><td>-0.117</td></tr><tr><td>Mid.</td><td>/</td><td>0.037</td><td>-0.230</td><td>0.025</td><td>-0.147</td><td>0.034</td><td>-0.203</td><td>0.028</td><td>-0.124</td><td>-0.036</td><td>-0.190</td><td>-0.042</td><td>-0.228</td><td>-0.018</td><td>-0.165</td></tr><tr><td>Bot.</td><td>/</td><td>0.046</td><td>-0.305</td><td>0.035</td><td>-0.127</td><td>0.051</td><td>-0.282</td><td>0.042</td><td>-0.115</td><td>0.009</td><td>-0.163</td><td>-0.005</td><td>-0.179</td><td>-0.003</td><td>-0.135</td></tr><tr><td>Avg.</td><td>/</td><td>0.044</td><td>-0.254</td><td>0.034</td><td>-0.140</td><td>0.046</td><td>-0.228</td><td>0.038</td><td>-0.115</td><td>-0.008</td><td>-0.171</td><td>-0.018</td><td>-0.198</td><td>0.002</td><td>-0.139</td></tr></table>


Note: This table reports the average out-of-sample $R ^ { 2 }$ and $R _ { \mathrm { K F } } ^ { 2 }$ for diferent levels of trading volume. For the $R ^ { 2 }$ results, boldfaced values represent the highest $R ^ { 2 }$ for each group. For the $R _ { \mathrm { K F } } ^ { 2 }$ results, positive values represent the model’s predictions are more accurate than the benchmark’s. The results of each asset are presented in Table C.11 and Table C.12. 


Table 3 shows that SPAR models consistently and substantially outperform their OLS counterparts when benchmarked against the historical mean. For instance, the average $R ^ { 2 }$ for $\mathrm { S P A R _ { 3 } } , 0 . 2 9 2 8$ , is almost three times that of $\mathrm { O L S _ { 3 } , 0 . 1 0 3 5 }$ . This substantial improvement highlights the importance of removing periodic fixed efects to better model intraday volume dynamics. 

This outperformance is even more surprising when compared against the sophisticated KF benchmark, as shown in Table C.12. SPAR models almost universally yield positive $R _ { \mathrm { K F } } ^ { 2 }$ values, indicating a significant improvement over the KF model. In contrast, OLS models frequently fail to surpass the benchmark, producing large negative values. 

Table 3 also shows that the specifications with separate cross-day lags do not outperform the simpler SPAR specifications. All SPAR forecasts already use cross-day information through the rolling same-time-of-day mean, $\overline { { y } } _ { t , k } .$ , while $X _ { 2 }$ adds 22 individual cross-day lags. Hence, the results suggest that these additional lags provide limited incremental predictive value. On the other hand, though the SPJ correction reduces bias from lagged dependent variables, estimating many additional coeficients in short rolling windows may increase estimation error. We therefore treat $\mathrm { S P A R _ { 1 } }$ and $\mathrm { S P A R _ { 3 } }$ as the preferred specifications and use $\mathrm { { S P A R _ { 2 } } }$ and $\mathrm { S P A R _ { 4 } }$ to examine the additional role of cross-day lags. 

Beyond these relative gains, the SPAR models also demonstrate strong absolute predictive power, with $\mathrm { S P A R _ { 3 } , \ S P A R _ { 1 } }$ , and $\mathrm { S P A R _ { 4 } }$ ranking as the top-performing models on average. The instability of the OLS models underscores the unreliability of forecasting on non-stationary data with such a periodic efect. Collectively, these results establish that our proposed periodicity separation is a crucial and robust strategy for enhancing predictive accuracy in this context. 

## 5.2. Analysis of the model confidence set

Next, we assess the models based on forecast errors, RMSE, and RMAE, based on an analysis of the Model Confidence Set. Table 4 shows the average results of RMSE and RMAE with the corresponding results of the MCS test. We can see that $\mathrm { S P A R _ { 1 } }$ consistently achieves the lowest average RMSE, while $\mathrm { S P A R _ { 3 } }$ achieves the lowest average RMAE. This finding indicates that including volatility features enhances the model’s ability to capture overall volume dynamics, thereby minimizing the impact of extreme outliers. 

The asset-level results presented in Tables C.13 and C.15 reveal a consistent pattern. Notably, SPAR-type models consistently yield the lowest RMSE and RMAE across all assets, demonstrating advantages in average error control. Specifically, both $\mathrm { S P A R _ { 1 } }$ and $\mathrm { S P A R _ { 3 } }$ achieve the lowest RMSE for nearly half of the assets, while $\mathrm { S P A R _ { 3 } }$ stands out with the best performance in terms of RMAE. This result demonstrates consistency in rankings across diferent indicators, underscoring the efectiveness of isolating the periodic efect, which enhances both the robustness and generalization capabilities of the models. 


Table 4: RMSE and RMAE loss with the MCS test.


<table><tr><td></td><td>Level</td><td>KF</td><td><eq>\text{SPAR}_1</eq></td><td><eq>\text{OLS}_1</eq></td><td><eq>\text{SPAR}_2</eq></td><td><eq>\text{OLS}_2</eq></td><td><eq>\text{SPAR}_3</eq></td><td><eq>\text{OLS}_3</eq></td><td><eq>\text{SPAR}_4</eq></td><td><eq>\text{OLS}_4</eq></td><td><eq>\text{LA}_{\text{SP}}</eq></td><td>Lasso</td><td><eq>\text{RI}_{\text{SP}}</eq></td><td>Ridge</td><td><eq>\text{RF}_{\text{SP}}</eq></td><td>RF</td></tr><tr><td rowspan="4">RMSE</td><td>Top.</td><td>0.556</td><td>0.470</td><td>0.682</td><td>0.472</td><td>0.577</td><td>0.470</td><td>0.659</td><td>0.473</td><td>0.557</td><td>0.475</td><td>0.574</td><td>0.478</td><td>0.578</td><td>0.474</td><td>0.515</td></tr><tr><td>Mid.</td><td>0.538</td><td>0.507</td><td>0.788</td><td>0.512</td><td>0.636</td><td>0.507</td><td>0.760</td><td>0.512</td><td>0.622</td><td>0.518</td><td>0.643</td><td>0.523</td><td>0.644</td><td>0.519</td><td>0.570</td></tr><tr><td>Bot.</td><td>0.658</td><td>0.612</td><td>1.001</td><td>0.617</td><td>0.746</td><td>0.612</td><td>0.970</td><td>0.620</td><td>0.737</td><td>0.625</td><td>0.758</td><td>0.631</td><td>0.761</td><td>0.626</td><td>0.675</td></tr><tr><td>Avg.</td><td>0.584</td><td>0.529</td><td>0.824</td><td>0.534</td><td>0.653</td><td>0.530</td><td>0.796</td><td>0.535</td><td>0.639</td><td>0.539</td><td>0.658</td><td>0.544</td><td>0.661</td><td>0.540</td><td>0.586</td></tr><tr><td rowspan="4">MCS</td><td>Top.</td><td>0.119*</td><td>1.000**</td><td>-</td><td>0.478**</td><td>-</td><td>0.766**</td><td>-</td><td>0.478**</td><td>-</td><td>0.252**</td><td>-</td><td>0.119*</td><td>-</td><td>0.478**</td><td>0.000</td></tr><tr><td>Mid.</td><td>-</td><td>1.000**</td><td>-</td><td>-</td><td>-</td><td>0.358**</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td></tr><tr><td>Bot.</td><td>-</td><td>1.000**</td><td>-</td><td>-</td><td>-</td><td>0.395**</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td></tr><tr><td>Avg.</td><td>0.014</td><td>1.000**</td><td>-</td><td>0.014</td><td>-</td><td>0.234*</td><td>-</td><td>0.014</td><td>-</td><td>0.014</td><td>-</td><td>0.014</td><td>-</td><td>0.014</td><td>-</td></tr><tr><td rowspan="4">RMAE</td><td>Top.</td><td>0.344</td><td>0.338</td><td>0.390</td><td>0.341</td><td>0.383</td><td>0.338</td><td>0.385</td><td>0.341</td><td>0.375</td><td>0.344</td><td>0.381</td><td>0.346</td><td>0.386</td><td>0.344</td><td>0.361</td></tr><tr><td>Mid.</td><td>0.383</td><td>0.374</td><td>0.438</td><td>0.378</td><td>0.423</td><td>0.373</td><td>0.431</td><td>0.378</td><td>0.414</td><td>0.382</td><td>0.422</td><td>0.383</td><td>0.426</td><td>0.381</td><td>0.399</td></tr><tr><td>Bot.</td><td>0.423</td><td>0.412</td><td>0.490</td><td>0.417</td><td>0.458</td><td>0.412</td><td>0.483</td><td>0.417</td><td>0.452</td><td>0.421</td><td>0.458</td><td>0.422</td><td>0.461</td><td>0.419</td><td>0.434</td></tr><tr><td>Avg.</td><td>0.383</td><td>0.375</td><td>0.439</td><td>0.379</td><td>0.421</td><td>0.374</td><td>0.433</td><td>0.379</td><td>0.414</td><td>0.382</td><td>0.420</td><td>0.384</td><td>0.424</td><td>0.381</td><td>0.398</td></tr><tr><td rowspan="4">MCS</td><td>Top.</td><td>0.002</td><td>0.059</td><td>-</td><td>0.002</td><td>-</td><td>1.000**</td><td>-</td><td>0.002</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td></tr><tr><td>Mid.</td><td>-</td><td>0.001</td><td>-</td><td>-</td><td>-</td><td>1.000**</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td></tr><tr><td>Bot.</td><td>-</td><td>0.128*</td><td>-</td><td>-</td><td>-</td><td>1.000**</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td></tr><tr><td>Avg.</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>1.000**</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td></tr></table>


Note: This table shows the average RMSE and RMAE results for diferent levels of trading volume and the corresponding p-values of the MCS test. For RMSE and RMAE, boldfaced values represent the lowest results for each group. For MCS results, a dash ‘-’ indicates a p-value of zero. The forecasts in $\widehat { \mathcal { M } _ { 9 0 \% } ^ { * } }$ and $\widehat { \mathcal { M } _ { 7 5 \% } ^ { * } }$ are identified by one and two asterisks, respectively. The results of each asset are presented in Table C.13, Table C.14, Table C.15 and Table C.16, respectively. 


In Tables C.14 and C.16, we present the p-values for the RMSE and RMAE loss functions, setting $\alpha = 0 . 1 0 .$ A model with a p-value greater than α survives in the confidence set. The straightforward results provide decisive statistical evidence that corroborates our earlier findings. The SPAR-type models demonstrate overwhelming statistical superiority. For nearly every asset, $\mathrm { S P A R _ { 1 } }$ and $\mathrm { S P A R _ { 3 } }$ are included in the 75% confidence set, $\widehat { \mathcal { M } } _ { 0 . 7 5 } ^ { * }$ , often with p-values of 1.000, indicating their superiority, and they remain in the superior set. In contrast, their OLS counterparts are almost universally eliminated, with p-values near zero, confirming their inferior performance. 

Overall, the MCS results are consistent with the rankings based on $R ^ { 2 }$ , RMSE, and RMAE. $\mathrm { S P A R _ { 1 } }$ and $\mathrm { S P A R _ { 3 } }$ are retained most often in the model confidence sets, while the machine learning benchmarks do not provide an improvement over the SPAR models. Together with the results in Tables 3 and 4, these findings support the importance of removing the intraday periodic component before forecasting. 

## 5.3. Robustness across trading volume regimes

To verify that our findings are robust and not driven by specific market conditions, we analyze model performance across diferent trading-volume regimes. For each asset, we sort the out-of-sample trading days into quintiles based on the average intraday trading volume. This partitions the evaluation period into five distinct subsets, from the lowest-volume days to the highest, denoted Low, Med-Low, Medium, Med-High, and High, respectively, with each group containing about 475 days. We then compute the average performance metrics within each quintile. 


Table 5: The average $R ^ { 2 }$ of each subset.


<table><tr><td>Group</td><td>Subsets</td><td>KF</td><td><eq>\text{SPAR}_1</eq></td><td><eq>\text{OLS}_1</eq></td><td><eq>\text{SPAR}_2</eq></td><td><eq>\text{OLS}_2</eq></td><td><eq>\text{SPAR}_3</eq></td><td><eq>\text{OLS}_3</eq></td><td><eq>\text{SPAR}_4</eq></td><td><eq>\text{OLS}_4</eq></td><td><eq>\text{LA}_{\text{SP}}</eq></td><td>Lasso</td><td><eq>\text{RI}_{\text{SP}}</eq></td><td>Ridge</td><td><eq>\text{RF}_{\text{SP}}</eq></td><td>RF</td></tr><tr><td rowspan="5">Top</td><td>High</td><td>0.187</td><td>0.287</td><td>-0.103</td><td>0.275</td><td>0.104</td><td>0.289</td><td>-0.059</td><td>0.277</td><td>0.140</td><td>0.280</td><td>0.122</td><td>0.272</td><td>0.115</td><td>0.273</td><td>0.219</td></tr><tr><td>Med-High</td><td>0.120</td><td>0.310</td><td>-0.151</td><td>0.300</td><td>-0.028</td><td>0.312</td><td>-0.088</td><td>0.299</td><td>0.122</td><td>0.304</td><td>0.095</td><td>0.298</td><td>0.054</td><td>0.294</td><td>0.242</td></tr><tr><td>Medium</td><td>0.119</td><td>0.310</td><td>-0.236</td><td>0.298</td><td>0.062</td><td>0.313</td><td>-0.169</td><td>0.296</td><td>0.095</td><td>0.309</td><td>0.065</td><td>0.300</td><td>0.064</td><td>0.296</td><td>0.230</td></tr><tr><td>Med-Low</td><td>-0.147</td><td>0.314</td><td>-0.278</td><td>0.303</td><td>0.062</td><td>0.316</td><td>-0.217</td><td>0.304</td><td>0.086</td><td>0.316</td><td>0.054</td><td>0.306</td><td>0.068</td><td>0.305</td><td>0.237</td></tr><tr><td>Low</td><td>0.095</td><td>0.307</td><td>-0.335</td><td>0.291</td><td>0.039</td><td>0.306</td><td>-0.268</td><td>0.290</td><td>0.068</td><td>0.314</td><td>0.027</td><td>0.304</td><td>0.036</td><td>0.300</td><td>0.231</td></tr><tr><td rowspan="5">Mid</td><td>High</td><td>0.265</td><td>0.305</td><td>-0.038</td><td>0.289</td><td>0.135</td><td>0.304</td><td>-0.004</td><td>0.290</td><td>0.160</td><td>0.293</td><td>0.141</td><td>0.287</td><td>0.128</td><td>0.288</td><td>0.232</td></tr><tr><td>Med-High</td><td>0.269</td><td>0.318</td><td>-0.097</td><td>0.300</td><td>0.133</td><td>0.316</td><td>-0.065</td><td>0.298</td><td>0.152</td><td>0.305</td><td>0.131</td><td>0.299</td><td>0.123</td><td>0.297</td><td>0.244</td></tr><tr><td>Medium</td><td>0.263</td><td>0.311</td><td>-0.142</td><td>0.295</td><td>0.107</td><td>0.309</td><td>-0.096</td><td>0.293</td><td>0.131</td><td>0.299</td><td>0.105</td><td>0.292</td><td>0.106</td><td>0.291</td><td>0.233</td></tr><tr><td>Med-Low</td><td>0.270</td><td>0.311</td><td>-0.298</td><td>0.300</td><td>0.057</td><td>0.309</td><td>-0.249</td><td>0.300</td><td>0.075</td><td>0.299</td><td>0.054</td><td>0.292</td><td>0.057</td><td>0.288</td><td>0.228</td></tr><tr><td>Low</td><td>0.258</td><td>0.311</td><td>-0.410</td><td>0.295</td><td>0.038</td><td>0.309</td><td>-0.359</td><td>0.297</td><td>0.049</td><td>0.305</td><td>0.032</td><td>0.297</td><td>0.042</td><td>0.284</td><td>0.233</td></tr><tr><td rowspan="5">Bot</td><td>High</td><td>0.202</td><td>0.263</td><td>-0.258</td><td>0.252</td><td>0.094</td><td>0.262</td><td>-0.217</td><td>0.250</td><td>0.104</td><td>0.251</td><td>0.084</td><td>0.245</td><td>0.077</td><td>0.248</td><td>0.195</td></tr><tr><td>Med-High</td><td>0.194</td><td>0.252</td><td>-0.324</td><td>0.241</td><td>0.073</td><td>0.251</td><td>-0.270</td><td>0.240</td><td>0.086</td><td>0.242</td><td>0.066</td><td>0.236</td><td>0.061</td><td>0.237</td><td>0.195</td></tr><tr><td>Medium</td><td>0.207</td><td>0.268</td><td>-0.378</td><td>0.254</td><td>0.050</td><td>0.266</td><td>-0.325</td><td>0.251</td><td>0.062</td><td>0.259</td><td>0.043</td><td>0.251</td><td>0.040</td><td>0.251</td><td>0.195</td></tr><tr><td>Med-Low</td><td>0.193</td><td>0.260</td><td>-0.435</td><td>0.248</td><td>0.029</td><td>0.258</td><td>-0.387</td><td>0.241</td><td>0.047</td><td>0.250</td><td>0.024</td><td>0.242</td><td>0.018</td><td>0.237</td><td>0.188</td></tr><tr><td>Low</td><td>0.202</td><td>0.269</td><td>-0.508</td><td>0.252</td><td>0.030</td><td>0.267</td><td>-0.453</td><td>0.246</td><td>0.044</td><td>0.258</td><td>0.025</td><td>0.250</td><td>0.016</td><td>0.247</td><td>0.195</td></tr><tr><td rowspan="5">Avg.</td><td>High</td><td>0.218</td><td>0.285</td><td>-0.133</td><td>0.272</td><td>0.111</td><td>0.285</td><td>-0.094</td><td>0.272</td><td>0.135</td><td>0.274</td><td>0.116</td><td>0.268</td><td>0.107</td><td>0.269</td><td>0.215</td></tr><tr><td>Med-High</td><td>0.194</td><td>0.293</td><td>-0.191</td><td>0.280</td><td>0.059</td><td>0.293</td><td>-0.141</td><td>0.279</td><td>0.120</td><td>0.284</td><td>0.097</td><td>0.277</td><td>0.079</td><td>0.276</td><td>0.227</td></tr><tr><td>Medium</td><td>0.196</td><td>0.296</td><td>-0.252</td><td>0.282</td><td>0.073</td><td>0.296</td><td>-0.197</td><td>0.280</td><td>0.096</td><td>0.289</td><td>0.071</td><td>0.281</td><td>0.070</td><td>0.279</td><td>0.219</td></tr><tr><td>Med-Low</td><td>0.105</td><td>0.295</td><td>-0.337</td><td>0.284</td><td>0.050</td><td>0.294</td><td>-0.284</td><td>0.282</td><td>0.069</td><td>0.288</td><td>0.044</td><td>0.280</td><td>0.048</td><td>0.277</td><td>0.218</td></tr><tr><td>Low</td><td>0.185</td><td>0.296</td><td>-0.418</td><td>0.279</td><td>0.036</td><td>0.294</td><td>-0.360</td><td>0.278</td><td>0.054</td><td>0.292</td><td>0.028</td><td>0.283</td><td>0.031</td><td>0.277</td><td>0.219</td></tr></table>


Note: This table reports the average out-of-sample $R ^ { 2 }$ across diferent trading-volume regimes. For each asset, out-of-sample trading days are partitioned into five equal-sized groups based on average intraday trading volume. The reported values are averaged across assets within each volume group. Bold values denote the best-performing model in each regime. 


Table 5 shows that the superiority of the SPAR framework is remarkably consistent across all volume regimes. The $R ^ { 2 }$ values for all SPAR specifications remain higher than the KF benchmark and the OLS counterpart, regardless of whether the trading volume is high or low. In contrast, OLS models consistently underperform, with their $R ^ { 2 }$ values often negative and becoming increasingly so on days with lower volume. This pattern confirms that the benefits of the within-transformation are not conditional on a specific market state, but are a robust feature of the modeling approach. 

In summary, our empirical analysis provides strong and consistent evidence that explicitly accounting for intraday periodicity via a within-transformation is the most critical element for accurately forecasting trading volume. The resulting SPAR framework performs well across the high-, medium-, and low-volume groups in our main sample. These results show that the gains from removing intraday periodicity are not driven only by the highest-volume assets. 

## 5.4. Results of intraday forecasts

We evaluated the performance of diferent models throughout the day. The series of trading volumes typically exhibits a U-shaped pattern, with high volumes at the opening and closing of the market and a drop in the middle of the trading day. For each asset, we divide one trading day into three periods: the first 30 minutes after the market opens, when we use overnight information; the last 30 minutes before the market closes, when volume sharply increases; and the remaining trading time, during which volume is stable. Then, we calculate $R ^ { 2 }$ of all assets by averaging the values. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/589a4739f786465773888dec5dae8553591a638569d8375bad031b4d0dbd5d8b.jpg)



Figure 3: Forecasting performance across intraday trading sessions. This figure reports the average $R ^ { 2 }$ across methods for three periods: the open session (the first 30 minutes after the market opens), the close session (the last 30 minutes before the market closes), and the middle session (the remaining trading time). Results of $R ^ { 2 }$ are calculated by averaging all 30 assets. The close-session bars for $\mathrm { O L S _ { 1 } }$ and $\mathrm { O L S _ { 3 } }$ do not show up because of the negative $R ^ { 2 }$ with -0.6611 and -0.5586, respectively.


Figure 3 presents the performance of our proposed SPAR-type models against benchmarks in three intraday periods. The SPAR-type models perform better in the last 30 minutes before the market closes. An interesting finding is that when the cross-day variables are considered, the performance of the OLS models decreases in the second period but improves in the third period. In contrast, the SPAR model shows no obvious change, indicating greater robustness to the inclusion of cross-day predictors. During the opening period, the slightly higher $R ^ { 2 }$ of the KF benchmark is attributed to a structural break following the overnight session, which hinders our model’s use of lagged predictors from the previous day. 

In addition, we provide two examples of intraday curves fitted by the $\mathrm { S P A R _ { 3 } }$ model: one for an asset with high trading volume (BAC) and one for an asset with low trading volume (MTB). Figure 4 displays the observed trading volume, in red, and the fitted intraday curves, in blue, for both assets. For comparability, both curves are scaled to have a mean of one. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/78d531878a746c0b7ebbfe88d16d45c1f48bafade153042e133dc8ff02c636eb.jpg)



(a) Intraday curve and trading volume of BAC.


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/ccd84b321c5e5b86b93ef54e5b920a6e72ec78399c29dc42bd4f9a3e25549111.jpg)



(b) Intraday curve and trading volume of MTB.


Figure 4: Estimated periodic curves for representative assets. This figure shows the intraday trading volumes (red) and fitted intraday curves (blue) for BAC (left) and MTB (right), averaged from the 91st to the 2466th day. The y-axis represents normalized trading volume, with a mean of 1. 

As shown in the figure, the model’s fitted curves for BAC and MTB closely track the trends in their respective actual trading volumes. However, the model correctly identifies their distinct intraday patterns: a U-shape for BAC and a J-shape for MTB. This diference suggests that the observed patterns may not be entirely idiosyncratic. The J-shape, for instance, can be viewed as a ’back-loaded’ U-shape, where morning trading is inactive relative to the close. This observation raises a question: can these diferent shapes be explained as combinations of a few common periodic components? The finding motivates a formal factor model analysis, which we introduce in the following Section 7 to determine whether diferent intraday patterns are constructed from shared systematic factors and to better understand the fundamental structure of intraday volume dynamics. 

## 6. Volume Weighted Average Price Strategy

In this section, we use our forecasts to enhance the analysis of the Volume Weighted Average Price (VWAP), as initially introduced by Berkowitz et al. (1988). The VWAP serves as a reference for assessing market trading costs and is considered a more reliable indicator than metrics based solely on individual price points. The calculation of this metric is expressed as follows: 

$$
\mathrm{VWAP} _ {i, t} = \frac {\sum_ {k = 1} ^ {K} V _ {i , t , k} \times P _ {i , t , k}}{\sum_ {k = 1} ^ {K} V _ {i , t , k}} = \sum_ {k = 1} ^ {K} w _ {i, t, k} \times P _ {i, t, k},\tag{11}
$$

where $w _ { i , t , k }$ represents the weight and $P _ { i , t , k }$ denotes the transaction price in interval k on day t for each asset. In our empirical analysis, we adopt the last closing price within a fiveminute interval as a proxy for the prices $P _ { i , t , k }$ . As evident from equation (11), the weights are derived by normalizing the intraday volume with respect to the total trading volume for the day. Consequently, intraday volume forecasting is a significant application that facilitates the execution of the VWAP replication strategy. As discussed in Bia lkowski et al. (2008) and Brownlees et al. (2011), the VWAP replication strategy requires dividing a predetermined number of shares into smaller orders, which are executed at various intervals to achieve an average price that aligns with the VWAP benchmark. 

We consider the dynamic VWAP replication strategy proposed by Bia lkowski et al. (2008). First, we determine the weight of each grid point on the execution day in advance. Then, weights are dynamically adjusted based on updates in the prediction of intraday trading volume. Each modification of the weight applies only to the remaining volume to be traded after grid k. Finally, the remaining trading volume is traded in the last grid K. 

Formally, we denote $\hat { w } _ { i , t , k } ^ { ( \mathcal { D } ) }$ as the dynamic weights, $\widehat { V } _ { i , t , j } ^ { ( S ) }$ indicates the prediction of the day ahead, and $\widehat { V } _ { i , t , j } ^ { ( { D } ) }$ is the intraday online prediction. Specifically, $\hat { w } _ { i , t , k } ^ { ( { D } ) }$ are calculated by 

$$
\hat {w} _ {i, t, k} ^ {(\mathcal {D})} = \left\{ \begin{array}{l l} \frac {\widehat {V} _ {i , t , k} ^ {(\mathcal {D})}}{\sum_ {j = k} ^ {K} \widehat {V} _ {i , t , j} ^ {(\mathcal {S})}} \left(1 - \sum_ {j = 1} ^ {k - 1} \hat {w} _ {i, t, j} ^ {(\mathcal {D})}\right), & k = 1, \ldots , K - 1 \\ \left(1 - \sum_ {k = 1} ^ {K - 1} \hat {w} _ {i, t, k} ^ {(\mathcal {D})}\right), & k = K \end{array} \right.\tag{12}
$$

Following Brownlees et al. (2011) and Goyenko et al. (2024), we use a moving average of the historical volume at each grid point k as the proxy for $\hat { V } _ { i , t , k } ^ { ( S ) } ,$ , i.e., $\begin{array} { r } { \hat { V } _ { i , t , k } ^ { ( S ) } = \frac { 1 } { 2 2 } \sum _ { \omega = 1 } ^ { 2 2 } V _ { i , t - \omega , k } } \end{array}$ 

We use VWAP tracking error to measure the risk of order execution and the efectiveness of predictive models in the application of the strategy. Following the definition in Cucuringu et al. (2025), the tracking error is defined as 

$$
\mathrm{VWAP} _ {i} ^ {\mathrm{TE}} = \frac {1}{\mathcal {T}} \sum_ {t \in \mathcal {T}} \frac {\left| \mathrm{VWAP} _ {i , t} - \mathrm{VWAP} _ {i , t} ^ {\mathrm{rep}} \right|}{\mathrm{VWAP} _ {i , t}},
$$

where $\mathrm { V W A P } _ { i , t } ^ { \mathrm { r e p } }$ is the VWAP generated by the replication strategy. The tracking error is reported in basis points (bp), where 1 bp equals 0.01%. A lower tracking error means that the replication price is closer to the market VWAP. In a guaranteed VWAP order, for example, the broker bears the diference between its own execution price and the market VWAP. Thus, the tracking error provides a simple measure of VWAP execution risk. 

In the VWAP exercise, we use $\mathrm { S P A R _ { 3 } }$ because it has the best overall forecasting performance in the main empirical analysis. In addition, we compare $\mathrm { S P A R _ { 3 } }$ with two simple alternatives: $\mathrm { O L S _ { 3 } }$ and equal-weight trading (EW). Equal-weight trading does not use any volume forecast and splits the order evenly across all intraday intervals. 

Table 6 reports the VWAP tracking errors for the 30 sample assets. $\mathrm { S P A R _ { 3 } }$ has the lowest tracking error for every asset in the sample. The average tracking error is 7.013 bp for $\mathrm { S P A R _ { 3 } } .$ , compared with 7.275 bp for $\mathrm { O L S _ { 3 } , 8 . 0 0 7 }$ bp for KF, and 8.804 bp for EW. 

The comparison with OLS<sub>3</sub> shows that the gain is not only due to the choice of predictors, since $\mathrm { O L S _ { 3 } }$ uses the same intraday and volatility information as $\mathrm { S P A R _ { 3 } }$ . The comparison with EW shows that the gain is also meaningful relative to a simple no-forecast execution rule. Overall, the VWAP exercise confirms that SPAR’s forecasting gains translate into lower replication errors in a trading application. 


Table 6: VWAP tracking errors under alternative execution rules


<table><tr><td></td><td>BAC</td><td>SPY</td><td>AAPL</td><td>GE</td><td>MSFT</td><td>CSCO</td><td>INTC</td><td>AMD</td><td>PFE</td><td>T</td></tr><tr><td><eq>\text{SPAR}_3</eq></td><td>7.148</td><td>3.609</td><td>6.373</td><td>6.248</td><td>5.566</td><td>5.221</td><td>6.141</td><td>18.075</td><td>4.454</td><td>4.011</td></tr><tr><td><eq>\text{OLS}_3</eq></td><td>7.584</td><td>3.749</td><td>6.433</td><td>6.662</td><td>5.586</td><td>5.341</td><td>6.383</td><td>18.943</td><td>4.701</td><td>4.223</td></tr><tr><td>KF</td><td>8.212</td><td>3.846</td><td>6.814</td><td>7.085</td><td>6.096</td><td>5.949</td><td>6.641</td><td>20.775</td><td>5.052</td><td>4.463</td></tr><tr><td>EW</td><td>9.205</td><td>4.328</td><td>8.000</td><td>7.295</td><td>7.096</td><td>6.923</td><td>8.028</td><td>19.615</td><td>5.876</td><td>4.909</td></tr><tr><td></td><td>KBH</td><td>ROST</td><td>SWKS</td><td>CTXS</td><td>ETN</td><td>DE</td><td>ANF</td><td>BEN</td><td>PEG</td><td>YUM</td></tr><tr><td><eq>\text{SPAR}_3</eq></td><td>13.102</td><td>6.085</td><td>10.397</td><td>8.287</td><td>5.688</td><td>5.574</td><td>13.361</td><td>6.267</td><td>4.241</td><td>5.321</td></tr><tr><td><eq>\text{OLS}_3</eq></td><td>13.698</td><td>6.159</td><td>10.792</td><td>8.579</td><td>5.931</td><td>5.860</td><td>13.770</td><td>6.542</td><td>4.497</td><td>5.643</td></tr><tr><td>KF</td><td>15.103</td><td>7.042</td><td>11.853</td><td>9.225</td><td>6.493</td><td>6.424</td><td>15.394</td><td>7.250</td><td>4.754</td><td>6.179</td></tr><tr><td>EW</td><td>14.923</td><td>7.729</td><td>11.920</td><td>10.148</td><td>7.569</td><td>7.118</td><td>14.081</td><td>8.942</td><td>6.844</td><td>6.761</td></tr><tr><td></td><td>MTB</td><td>ORLY</td><td>PSA</td><td>GPC</td><td>AVY</td><td>VAR</td><td>AVB</td><td>SHW</td><td>LH</td><td>NBR</td></tr><tr><td><eq>\text{SPAR}_3</eq></td><td>5.771</td><td>6.602</td><td>4.705</td><td>5.229</td><td>5.929</td><td>5.791</td><td>5.008</td><td>5.907</td><td>5.848</td><td>14.420</td></tr><tr><td><eq>\text{OLS}_3</eq></td><td>5.838</td><td>6.709</td><td>4.849</td><td>5.274</td><td>5.932</td><td>5.997</td><td>5.255</td><td>5.996</td><td>5.966</td><td>15.353</td></tr><tr><td>KF</td><td>6.635</td><td>7.696</td><td>5.447</td><td>6.049</td><td>6.844</td><td>6.925</td><td>5.873</td><td>7.046</td><td>6.825</td><td>16.208</td></tr><tr><td>EW</td><td>8.150</td><td>7.708</td><td>7.924</td><td>7.560</td><td>8.740</td><td>7.584</td><td>7.987</td><td>7.525</td><td>7.358</td><td>16.269</td></tr></table>


Note: This table reports the VWAP tracking errors (in basis points, bp) of the dynamic replication strategy for the 30 sample assets using forecasts generated by SPAR<sub>3</sub>, OLS<sub>3</sub>, KF, and an equal-weighted (EW) benchmark. A lower tracking error indicates that the execution price is closer to the market VWAP and therefore reflects better execution quality. 


We next translate the tracking-error reductions into dollar values. Let Q denote the dollar size of the order and let $\Delta b$ denote the reduction in tracking error in basis points. The dollar value of the reduced VWAP deviation is 

$$
\Delta \mathrm{Dollar} = Q \times \Delta b \times 1 0 ^ {- 4}.
$$

Following Van Kervel and Menkveld (2019), we use $Q = \$ 2.2$ million as a representative institutional order size. Relative to KF, $\mathrm { S P A R _ { 3 } }$ reduces the average tracking error by 0.994 bp. This corresponds to about $219 per order, calculated as 2.2 million $\times 0 . 9 9 4 \times 1 0 ^ { - 4 }$ . If one such order is executed on each of 250 trading days, the annual dollar value is about $54,669. Relative to ${ \mathrm { O L S } } _ { 3 } ,$ the reduction of 0.262 bp corresponds to about $58 per order, or about $14,421 over 250 trading days. Relative to EW, the reduction of 1.791 bp corresponds to about $394 per order, or about $98,516 over 250 trading days. These calculations show the economic scale of the tracking-error reduction. 

## 7. Factor Model of Periodic Curves

This section describes how we build a factor model to analyze the periodic curves that we have estimated. To test the robustness of the factor model, we not only estimate it for the selected subsample but also provide it for the full sample for comparison. The analysis has two parts. We first use the full set of fitted periodic curves to describe the cross-sectional shape of intraday volume profiles. We then use recursively estimated factor loadings to predict future execution risk. 

We first define the notations. Denote $\hat { F } _ { i , m , k }$ as the ith asset’s fitted periodic curve at the kth grid in the mth month. By stacking values of all assets at the same time, we denote $\hat { \mathbf { F } } _ { m , k } = \left( \hat { F } _ { 1 , m , k } , \ldots , \hat { F } _ { N , m , k } \right)$ . We assume that the estimated periodic curves can be represented by c common factors, $\Gamma _ { k } = \left( \gamma _ { 1 , k } , \ldots , \gamma _ { c , k } \right) ^ { \prime }$ . The factor model follows 

$$
\hat {\mathbf {F}} _ {m, k} = \boldsymbol {\Phi} \cdot \boldsymbol {\Gamma} _ {k} + \mathbf {e} _ {m, k}, \quad \mathrm{for} m = 1, \ldots , M, \mathrm{and} k = 1, \ldots , K,
$$

where M is the number of times we update the model and thus the number of estimated periodic curves available over time, $\Phi$ is a $N \times c$ matrix of factor loadings, and $\mathbf { e } _ { m , k }$ is a $N \times 1$ vector of idiosyncratic components. 

In our analysis, following a similar setting in Wu et al. (2025), we set $\gamma _ { s , k } = s i n \left( \pi ( s + 1 ) k / K \right)$ for s to be odd and $\gamma _ { s , k } = c o s \left( \pi s k / K \right)$ for s to be even, where $s = 1 , \ldots , c .$ . Then, for c common factors, the loading matrix, $\Phi ^ { ( c ) }$ , can be obtained by the following algebraic manipulation 

$$
\hat {\boldsymbol {\Phi}} ^ {(c)} = \left(\left(\boldsymbol {\Gamma} ^ {(c)} \boldsymbol {\Gamma} ^ {(c) ^ {\prime}}\right) ^ {- 1} \boldsymbol {\Gamma} ^ {(c)} \hat {\mathbf {F}} ^ {\prime}\right) ^ {\prime},
$$

where $\hat { \mathbf { F } }$ is a $N \times ( K \cdot M )$ matrix containing all $\hat { \mathbf { F } } _ { m , k }$ , and $\mathbf { \Gamma } \Gamma ^ { \left( c \right) }$ is a $c \times ( K \cdot M )$ matrix with c number common factors. 

To choose the optimal number of factors, i.e., the quantity $c _ { 0 } .$ , we follow the information criterion method proposed by Ouysse (2006). That is, given a set $\mathcal { C } = \left\{ c ^ { ( 1 ) } , \dots , c ^ { ( L ) } \right\}$ , where $c ^ { ( 1 ) } < \cdots < c ^ { ( L ) }$ , we solve that 

$$
c _ {0} = \underset {c \in \mathcal {C}} {\arg \min} \left((N \cdot K \cdot M) ^ {- 1} \operatorname{Tr} \left(\left(\hat {\mathbf {F}} - \hat {\boldsymbol {\Phi}} ^ {(c)} \boldsymbol {\Gamma} ^ {(c)}\right) ^ {\prime} \left(\hat {\mathbf {F}} - \hat {\boldsymbol {\Phi}} ^ {(c)} \boldsymbol {\Gamma} ^ {(c)}\right)\right) + \frac {c}{M}\right).
$$

In this paper, we set $\mathcal { C } = \{ 1 , \ldots , 8 \}$ . As shown in Figure 5, which reports the results of information criteria with diferent numbers of factors, the optimal number of factors is two in the full sample and the subsample. The consistency of this result across both a large and a smaller, more specific group of assets suggests that two common factors are suficient to explain the dynamics of intraday periodic curves. 

Remark 5. For the descriptive analysis in Figures 5-7, we estimate one loading matrix using all fitted periodic curves over the period. For the predictive exercise in Section $\ 7 . 1 ,$ however, we do not use future curves. At each month m, we re-estimate the loading matrix using the fitted curves. Denote this estimated loading matrix $b y \ \widehat \Phi _ { m - 1 }$ . Its ith row, $\phi _ { i , m - 1 } =$ $( \widehat { \phi } _ { 1 , i , m - 1 } , \widehat { \phi } _ { 2 , i , m - 1 } )$ , is then used for prediction in month m. 

The two factors have diferent interpretations. For factor 1, it is positive in the first half of the day and negative in the second half. This pattern represents the morning-afternoon asymmetry. A high positive loading on Factor 1 indicates that trading volume is higher in the morning than in the afternoon. This pattern is called front-loaded. On the contrary, a negative loading on Factor 1 implies the pattern is back-loaded. For factor 2, it starts high, drops to its lowest point at midday, and rises again to high at the close, perfectly representing the classic U-shaped intraday volume pattern. A high positive loading on Factor 2 means a stock’s volume profile is strongly U-shaped. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/50d28a11a86eabe12084ac7d7471273182dc2757e21d6ceb834afc2b9c51e169.jpg)



Figure 5: Selection of the number of common factors in periodic curves. This figure reports the optimal number of factors using Information Criteria. The criterion is minimized for a two-factor model for both the full sample (305 stocks) and a subsample (30 stocks).


In Figure 6, we visualize how the intraday volume pattern of 30 diferent assets relates to the two periodic factors described above, i.e., the cross-sectional distribution of factor loadings for 30 stocks. The position of an asset on the plot reveals its intraday volume characteristics. For example, BAC has a positive Factor 2 loading and a Factor 1 loading close to zero. This indicates a strong U-shaped pattern with relatively mild morning-afternoon asymmetry, which is consistent with the left panel of Figure 4. MTB has a more negative Factor 1 loading and a positive Factor 2 loading. This indicates a morning-afternoon asymmetry, where trading volume after the open is lower relative to the close, consistent with the J-shaped pattern in the right panel of Figure 4. Therefore, the two loadings jointly describe the shape of an asset’s intraday trading volume. 

Figure 7 visualizes the intraday volume patterns of 305 assets (assets HBAN and SAN are removed as outliers based on the Mahalanobis distance) in Table C.9 by plotting their loadings on two fundamental periodic factors. We can find that assets with high trading volumes tend to show a U-shaped pattern, while assets with low trading volumes tend to have lower trading volume after the market opens than before it closes, which looks like a J-shaped pattern. The Spearman rank correlation test further confirmed our results, which show that the loadings of Factor 1 have a significant positive correlation, $\rho = 0 . 8 0 7$ and $p < 0 . 0 0 1$ ， with the magnitude of trading volume. Factor 2 shows a much weaker correlation, with $\rho = - 0 . 1 4 8$ and $p = 0 . 0 1$ 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/02ffe2907b9aee6aa747a8b4f7c447d6240346cec14f4bc47c331984d45a3866.jpg)



Figure 6: Cross-sectional distribution of periodic-factor loadings. The scatter plot visualizes the intraday volume patterns of 30 assets in Table 1 by plotting their loadings on two fundamental periodic factors. The stocks are categorized into three groups (High, Middle, and Bottom) based on their average daily trading volume. The dashed vertical and horizontal lines represent the averages of the Factor 1 and Factor 2 loadings, respectively.


Remark 6. Figures 6 and 7 show that the loadings on Factor 2 are positive and generally larger in magnitude than those on Factor 1. This implies that the U-shaped component is the dominant common component of the estimated intraday periodic curves. Factor 1 should instead be interpreted as a secondary shape component that captures morning-versusafternoon asymmetry around this common U-shaped profile. Thus, Factor 2 measures the strength of the common U-shaped pattern, while negative Factor 1 helps distinguish more symmetric U-shaped profiles from more J-shaped profiles. 

## 7.1. Factor loadings and execution risk

The factor loadings summarize the shape of an asset’s intraday volume curve. This shape matters for VWAP execution because tracking errors arise when the scheduled execution weights difer from the realized distribution of market volume. A smooth, stable intraday volume profile is easier to track, while one with a strong U-shape or a clear morning-afternoon imbalance is harder to replicate accurately. Thus, factor loadings may contain useful information about future execution risk. 

To examine this prediction, we use the monthly average tracking error as the dependent variable. Let $\mathrm { M A T E } _ { i , m }$ denote the log of 100 times the average daily VWAP tracking error of asset i in month m. We compare a simple autoregressive benchmark with a model that also includes lagged factor loadings. The predictive regression is 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/f799635e7757dd451cc373bf9dadf6f5fb603a8b526809c36d26fd5d9fbe382c.jpg)



Figure 7: Cross-sectional distribution of periodic-factor loadings of full sample. The scatter plot visualizes the intraday volume patterns of 303 assets (HBAN and SAN are removed as outliers based on the Mahalanobis distance) in Table C.9 by plotting their loadings on two fundamental periodic factors. After taking the logarithm of trading volume, the color (light to dark) and size (large to small) of the points reflect the high-to-low trading volume. The dashed vertical and horizontal lines represent the averages of the Factor 1 and Factor 2 loadings, respectively.


$$
\mathrm{MATE} _ {i, m} = \alpha + \beta_ {1} \mathrm{MATE} _ {i, m - 1} + \beta_ {2} \hat {\phi} _ {1, i, m - 1} + \beta_ {3} \hat {\phi} _ {2, i, m - 1} + \varepsilon_ {i, m},
$$

where the loadings $\widehat { \phi } _ { 1 , i , m - 1 }$ and $\widehat { \phi } _ { 2 , i , m - 1 }$ are estimated using only periodic curves available before month $m$ . Factor 1 is a signed measure of morning-versus-afternoon asymmetry, while Factor 2 measures the strength of the U-shaped component. We use the first 80% of monthly observations to estimate the predictive regression and reserve the remaining 20% for out-of-sample evaluation. 

Table 7 shows that MATE is persistent. The coeficient on lagged MATE is positive and significant in all specifications. More importantly, adding the two lagged factor loadings improves out-of-sample performance. In the subsample, the out-of-sample (OOS) $R ^ { 2 }$ increases from 0.040 in the AR(1) benchmark to 0.083 after adding factor loadings. In the full sample, the OOS $R ^ { 2 }$ increases from 0.094 to 0.112. The OOS MSE also decreases in both samples. 

The coeficients on the factor loadings show that the shape of the intraday periodic curve contains information about future execution risk. Factor 1 captures the morningversus-afternoon asymmetry, and Factor 2 captures the U-shaped component. The positive coeficients indicate that these shape characteristics help predict future MATE beyond the persistence captured by lagged MATE. These results show that the estimated periodic curves yield useful state variables for assessing future VWAP-tracking errors. 


Table 7: Predictive regressions for monthly average tracking error


<table><tr><td rowspan="2">Coeff.</td><td colspan="2">Subsample</td><td colspan="2">Full sample</td></tr><tr><td>AR(1)</td><td>AR(1) + Loadings</td><td>AR(1)</td><td>AR(1) + Loadings</td></tr><tr><td><eq>\alpha</eq></td><td>-0.9784***(0.0437)</td><td>-0.9579***(0.0568)</td><td>-1.0108***(0.0138)</td><td>-1.0414***(0.0185)</td></tr><tr><td><eq>\beta_1</eq></td><td>0.6550***(0.0150)</td><td>0.6614***(0.0155)</td><td>0.6427***(0.0048)</td><td>0.6499***(0.0048)</td></tr><tr><td><eq>\beta_2</eq></td><td></td><td>0.6086**(0.2810)</td><td></td><td>0.4775***(0.0950)</td></tr><tr><td><eq>\beta_3</eq></td><td></td><td>0.1503(0.2025)</td><td></td><td>0.4117***(0.0575)</td></tr><tr><td>In-sample <eq>R^2</eq></td><td>0.428</td><td>0.429</td><td>0.411</td><td>0.414</td></tr><tr><td>Adj.<eq>R^2</eq></td><td>0.427</td><td>0.429</td><td>0.411</td><td>0.414</td></tr><tr><td>OOS <eq>R^2</eq></td><td>0.040</td><td>0.083</td><td>0.094</td><td>0.112</td></tr><tr><td>OOS MSE</td><td>0.167</td><td>0.160</td><td>0.201</td><td>0.197</td></tr></table>


Note: This table reports predictive regressions of monthly average tracking errors (MATE) on lagged MATE and lagged factor loadings. Standard errors are reported in parentheses. Out-of-sample (OOS) $R ^ { 2 }$ and OOS MSE (with unit $\times 1 0 ^ { - 2 } )$ are calculated using the test sample. ***, **, and * denote significance at the 1%, 5%, and 10% levels, respectively. 


## 8. Conclusion

In this paper, we introduce the Separated Periodic AutoRegressive (SPAR) model, a novel panel-data framework that isolates the deterministic periodic component of intraday trading volume via a within-transformation. This approach allows for a more focused and accurate forecast of the underlying stationary dynamics. Our out-of-sample results demonstrate that the SPAR model consistently and significantly outperforms both traditional OLS and a sophisticated Kalman filter benchmark. This superiority is robust across diferent trading volume regimes and is statistically validated by Model Confidence Set analysis. Furthermore, our factor analysis identifies two common periodic patterns, a U-shaped curve and a morning versus-afternoon asymmetry, that efectively characterize the intraday volume profiles of diferent assets. The factor loadings are also useful in practice, as they improve the prediction of future VWAP tracking errors beyond a simple autoregressive benchmark. 

We acknowledge that our model’s features are derived solely from minute-by-minute price and volume data. Future research could yield significant performance gains by incorporating limit-order-book data (see Cucuringu et al. (2025)). Features such as order book depth, bid-ask spreads, and order flow imbalance could provide a richer set of explanatory variables to capture more complex market microstructure. It would also be useful to examine its performance in other asset classes, such as futures and cryptocurrencies, and in a broader set of international markets. 

## References



Admati, A.R., Pfleiderer, P., 1988. A theory of intraday patterns: Volume and price variability. Review of Financial Studies 1, 3–40. 





A¨ıt-sahalia, Y., Brandt, M.W., 2001. Variable selection for portfolio choice. Journal of Finance 56(4), 1297–1351. 





Andersen, T.G., 1996. Return volatility and trading volume: An information flow interpretation of stochastic volatility. Journal of Finance 51, 169–204. 





Andersen, T.G., Su, T., Todorov, V., Zhang, Z., 2024. Intraday periodic volatility curves. Journal of the American Statistical Association 119(546), 1181–1191. 





Andersen, T.G., Thyrsgaard, M., Todorov, V., 2019. Time-varying periodicity in intraday volatility. Journal of the American Statistical Association 114(528), 1695–1707. 





Anderson, A.M., Dyl, E.A., 2005. Market structure and trading volume. Journal of Financial Research 28, 115–131. 





Atkins, A.B., Dyl, E.A., 1997. Market structure and reported trading volume: NASDAQ versus the NYSE. Journal of Financial Research 20, 291–304. 





Bandi, F.M., Kolokolov, A., Pirino, D., Ren`o, R., 2020. Zeros. Management Science 66, 3466–3479. 





Barroso, P., Boons, M., Karehnke, P., 2021. Time-varying state variable risk premia in the ICAPM. Journal of Financial Economics 139(2), 428–451. 





Berkowitz, S.A., Logue, D.E., Noser Jr, E.A., 1988. The total cost of transactions on the NYSE. Journal of Finance 43(1), 97–112. 





Bia lkowski, J., Darolles, S., Le Fol, G., 2008. Improving VWAP strategies: A dynamic volume approach. Journal of Banking & Finance 32(9), 1709–1722. 





Bollerslev, T., Li, J., Xue, Y., 2018. Volume, volatility, and public news announcements. Review of Economic Studies 85, 2005–2041. 





Brailsford, T.J., 1996. The empirical relationship between trading volume, returns and volatility. Accounting & Finance 36, 89–111. 





Brandt, M.W., 1999. Estimating portfolio and consumption choice: A conditional euler equations approach. Journal of Finance 54(5), 1609–1645. 





Breiman, L., 2001. Random forests. Machine learning 45, 5–32. 





Brini, A., Toscano, G., 2025. SpotV2Net: Multivariate intraday spot volatility forecasting via vol-of-vol-informed graph attention networks. International Journal of Forecasting 41(3), 1093–1111. 





Brooks, C., 1998. Predicting stock index volatility: Can market volume help? Journal of Forecasting 17, 59–80. 





Broussard, J.P., Nikiforov, A., 2014. Intraday periodicity in algorithmic trading. Journal of International Financial Markets, Institutions and Money 30, 196–204. 





Brownlees, C.T., Cipollini, F., Gallo, G.M., 2011. Intra-daily volume modeling and prediction for algorithmic trading. Journal of Financial Econometrics 9(3), 489–518. 





Chen, J., Li, D., Linton, O., 2019. A new semiparametric estimation approach for large dynamic covariance matrices with multiple conditioning variables. Journal of Econometrics 212(1), 155–176. 





Chen, J., Li, D., Linton, O., Lu, Z., 2016a. Semiparametric dynamic portfolio choice with multiple conditioning variables. Journal of Econometrics 194(2), 309–318. 





Chen, R., Feng, Y., Palomar, D., 2016b. Forecasting intraday trading volume: A kalman filter approach. Available at SSRN 3101695 . 





Cheung, Y.L., 2024. Identification of time-varying factor models. Journal of Business & Economic Statistics 42(1), 76–94. 





Chordia, T., Roll, R., Subrahmanyam, A., 2001. Market liquidity and trading activity. Journal of Finance 56(2), 501–530. 





Chordia, T., Roll, R., Subrahmanyam, A., 2011. Recent trends in trading activity and market quality. Journal of Financial Economics 101(2), 243–263. 





Chordia, T., Swaminathan, B., 2000. Trading volume and cross-autocorrelations in stock returns. Journal of Finance 55, 913–935. 





Corsi, F., 2009. A simple approximate long-memory model of realized volatility. Journal of Financial Econometrics 7, 174–196. 





Cucuringu, M., Li, K., Zhang, C., 2025. Forecasting intraday volume in equity markets with machine learning. arXiv preprint arXiv:2505.08180 . 





Darrat, A.F., Zhong, M., Cheng, L.T., 2007. Intraday volume and volatility relations with and without public news. Journal of Banking & Finance 31, 2711–2729. 





Dumitru, A.M.H., Hizmeri, R., Izzeldin, M., 2025. Forecasting the realized variance in the presence of intraday periodicity. Journal of Banking & Finance 170, 107342. 





Engle, R., 2002. New frontiers for ARCH models. Journal of Applied Econometrics 17(5), 425–446. 





Goyenko, R., Kelly, B.T., Moskowitz, T.J., Su, Y., Zhang, C., 2024. Trading volume alpha. Technical Report. National Bureau of Economic Research. 





Gu, S., Kelly, B., Xiu, D., 2020. Empirical asset pricing via machine learning. Review of Financial Studies 33(5), 2223–2273. 





Hansen, P.R., Lunde, A., Nason, J.M., 2011. The model confidence set. Econometrica 79, 453–497. 





Hoerl, A.E., Kennard, R.W., 1970. Ridge regression: Applications to nonorthogonal problems. Technometrics 12, 69–82. 





Humphery-Jenner, M.L., 2011. Optimal VWAP trading under noisy conditions. Journal of Banking & Finance 35(9), 2319–2329. 





Jain, P.C., Joh, G.H., 1988. The dependence between hourly prices and trading volume. Journal of Financial and Quantitative Analysis 23, 269–283. 





Karpof, J.M., 1987. The relation between price changes and trading volume: A survey. Journal of Financial and Quantitative Analysis 22, 109–126. 





Konishi, H., 2002. Optimal slice of a VWAP trade. Journal of Financial Markets 5(2), 197–221. 





Lee, C.M., Swaminathan, B., 2000. Price momentum and trading volume. Journal of Finance 55, 2017–2069. 





Lee, Y.T., Fok, R.C., Liu, Y.J., 2001. Explaining intraday pattern of trading volume from the order flow data. Journal of Business Finance & Accounting 28, 199–230. 





Li, J., Li, Y., Patton, A.J., Xie, T., 2025. Online forecast evaluation with high-frequency proxies. Available at SSRN: https://papers.ssrn.com/sol3/papers.cfm?abstract id=5167337 . 





Li, J., Wang, D., Zhang, Q., 2024. Reading the candlesticks: An ok estimator for volatility. Review of Economics and Statistics 106, 1114–1128. 





Liu, L.Y., Patton, A.J., Sheppard, K., 2015. Does anything beat 5-minute RV? A comparison of realized measures across multiple asset classes. Journal of Econometrics 187, 293–311. 





Mei, Z., Sheng, L., Shi, Z., 2026. Nickell bias in panel local projection: Financial crises are worse than you think. Journal of International Economics 160, 104210. 





Ouysse, R., 2006. Consistent variable selection in large panels when factors are observable. Journal of Multivariate Analysis 97, 946–984. 





Satish, V., Saxena, A., Palmer, M., 2014. Predicting intraday trading volume and volume percentages. The Journal of Trading 9, 15–25. 





Suominen, M., 2001. Trading volume and information revelation in stock market. Journal of Financial and Quantitative Analysis 36, 545–565. 





Tibshirani, R., 1996. Regression shrinkage and selection via the lasso. Journal of the Royal Statistical Society Series B: Statistical Methodology 58, 267–288. 





Van Kervel, V., Menkveld, A.J., 2019. High-frequency trading around large institutional orders. Journal of Finance 74, 1091–1137. 





Wang, J., 1994. A model of competitive stock trading volume. Journal of political Economy 102, 127–168. 





Wu, L., Zhang, R., Dai, Y., 2025. Spectral volume models: Universal high-frequency periodicities in intraday trading activities. Management Science 0(0). 





Xu, X.E., Chen, P., Wu, C., 2006. Time and dynamic volume–volatility relation. Journal of Banking & Finance 30, 1535–1558. 





Zhang, C., Zhang, Y., Cucuringu, M., Qian, Z., 2024. Volatility forecasting with machine learning and intraday commonality. Journal of Financial Econometrics 22, 492–530. 





Zhu, H., Bai, L., He, L., Liu, Z., 2023. Forecasting realized volatility with machine learning: Panel data perspective. Journal of Empirical Finance 73, 251–271. 



## Appendix A. On the Inconsistency of OLS

Compared to the SPAR model, an alternative way to estimate the linear model (5) is to first estimate $\hat { \mathbf { f } }$ and then regress $\mathbf { y } _ { t } - \hat { \mathbf { f } }$ on $\mathbf { X } _ { t }$ . In the optimistic case, we assume that $\hat { \mathbf { f } }$ consistently estimates f. In this section, we demonstrate why SPAR achieves our objective more efectively than this alternative approach. 

We stack all $L : = K \times W$ observations and assume that the matrix of explanatory variables X is composed of stationary and deterministic periodic components. We write 

$$
\mathbf {X} = \tilde {\mathbf {X}} + \mathbf {G},
$$

where $\tilde { \mathbf { X } }$ contains the stationary components and G is the deterministic periodic component. If an intercept is included in X, the corresponding column of G is set to zero. The following assumption describes the true data-generating process. 

Assumption 1 (True data-generating process). We assume that the true econometric relationship is a linear model connecting the stationary components of the variables, 

$$
\tilde {\mathbf {y}} = \tilde {\mathbf {X}} \boldsymbol {\beta} + \mathbf {u},\tag{A.1}
$$

where $\beta$ is the $p \times 1$ vector of true coeficients, including the intercept, and u is an $L \times 1$ vector of error terms satisfying 

$$
\mathbb {E} \left(\mathbf {u} \mid \mathbf {f}, \mathbf {G}, \tilde {\mathbf {X}}\right) = \mathbf {0}, \quad \mathbb {E} \left(\mathbf {u u} ^ {\prime} \mid \mathbf {f}, \mathbf {G}, \tilde {\mathbf {X}}\right) = \tilde {\sigma} ^ {2} I _ {L \times L}.\tag{A.2}
$$

We further impose the standard regularity conditions 

$$
\frac {1}{L} \mathbf {X} ^ {\prime} \mathbf {X} \xrightarrow {p} \boldsymbol {Q} _ {X X}, \quad \frac {1}{L} \mathbf {X} ^ {\prime} \mathbf {G} \xrightarrow {p} \boldsymbol {Q} _ {X G},
$$

where $Q _ { X X }$ is finite and positive definite. We also assume that the estimation error in the periodic component is asymptotically negligible in the following sense: 

$$
\frac {1}{L} \mathbf {X} ^ {\prime} (\mathbf {f} - \hat {\mathbf {f}}) \xrightarrow {p} \mathbf {0}.
$$

This condition formalizes the favorable scenario in which $\hat { \bf f }$ is suficiently accurate so that the efect of estimating f vanishes asymptotically. 

Because G is deterministic, the conditional exogeneity condition in (A.2), together with standard law-of-large-numbers conditions, implies that 

$$
\frac {1}{L} \mathbf {X} ^ {\prime} \mathbf {u} = \frac {1}{L} \left(\tilde {\mathbf {X}} + \mathbf {G}\right) ^ {\prime} \mathbf {u} \xrightarrow {p} \mathbf {0}.
$$

The proposed regression attempts to estimate $\beta$ from the following misspecified model: 

$$
\dot {\mathbf {y}} = \mathbf {X} \boldsymbol {\beta} _ {o l s} + \mathbf {e},
$$

where the dependent variable is $\dot { \mathbf { y } } = \mathbf { y } - \hat { \mathbf { f } }$ . The OLS estimator is 

$$
\hat {\pmb {\beta}} _ {o l s} = (\mathbf {X} ^ {\prime} \mathbf {X}) ^ {- 1} \mathbf {X} ^ {\prime} \dot {\mathbf {y}}.
$$

Substituting the definitions yields 

$$
\hat {\boldsymbol {\beta}} _ {o l s} = \boldsymbol {\beta} - (\mathbf {X} ^ {\prime} \mathbf {X}) ^ {- 1} (\mathbf {X} ^ {\prime} \mathbf {G}) \boldsymbol {\beta} + (\mathbf {X} ^ {\prime} \mathbf {X}) ^ {- 1} \mathbf {X} ^ {\prime} \mathbf {u} + (\mathbf {X} ^ {\prime} \mathbf {X}) ^ {- 1} \mathbf {X} ^ {\prime} (\mathbf {f} - \hat {\mathbf {f}}).
$$

The following theorem characterizes the probability limit of this estimator. 

Theorem 1. Under the conditions above, 

$$
\mathrm{plim} _ {L \to \infty} \hat {\pmb {\beta}} _ {o l s} = \pmb {\beta} - \pmb {Q} _ {X X} ^ {- 1} \pmb {Q} _ {X G} \pmb {\beta}.
$$

Consequently, the OLS estimator $\hat { \beta } _ { o l s }$ is inconsistent for the true parameter $\beta$ whenever 

$$
Q _ {X G} \beta \neq 0.
$$

Proof of Theorem 1. By definition, we have 

$$
\begin{array}{r l} & {\hat {\boldsymbol {\beta}} _ {o l s} = (\mathbf {X} ^ {\prime} \mathbf {X}) ^ {- 1} \mathbf {X} ^ {\prime} (\mathbf {y} - \hat {\mathbf {f}})} \\ & {\quad = (\mathbf {X} ^ {\prime} \mathbf {X}) ^ {- 1} \mathbf {X} ^ {\prime} [ (\tilde {\mathbf {y}} + \mathbf {f}) - \hat {\mathbf {f}} ]} \\ & {\quad = (\mathbf {X} ^ {\prime} \mathbf {X}) ^ {- 1} \mathbf {X} ^ {\prime} [ (\tilde {\mathbf {X}} \boldsymbol {\beta} + \mathbf {u}) + \mathbf {f} - \hat {\mathbf {f}} ]} \\ & {\quad = (\mathbf {X} ^ {\prime} \mathbf {X}) ^ {- 1} \mathbf {X} ^ {\prime} \tilde {\mathbf {X}} \boldsymbol {\beta} + (\mathbf {X} ^ {\prime} \mathbf {X}) ^ {- 1} \mathbf {X} ^ {\prime} \mathbf {u} + (\mathbf {X} ^ {\prime} \mathbf {X}) ^ {- 1} \mathbf {X} ^ {\prime} (\mathbf {f} - \hat {\mathbf {f}})} \\ & {\quad = (\mathbf {X} ^ {\prime} \mathbf {X}) ^ {- 1} \mathbf {X} ^ {\prime} (\mathbf {X} - \mathbf {G}) \boldsymbol {\beta} + (\mathbf {X} ^ {\prime} \mathbf {X}) ^ {- 1} \mathbf {X} ^ {\prime} \mathbf {u} + (\mathbf {X} ^ {\prime} \mathbf {X}) ^ {- 1} \mathbf {X} ^ {\prime} (\mathbf {f} - \hat {\mathbf {f}})} \\ & {\quad = \boldsymbol {\beta} - (\mathbf {X} ^ {\prime} \mathbf {X}) ^ {- 1} (\mathbf {X} ^ {\prime} \mathbf {G}) \boldsymbol {\beta} + (\mathbf {X} ^ {\prime} \mathbf {X}) ^ {- 1} \mathbf {X} ^ {\prime} \mathbf {u} + (\mathbf {X} ^ {\prime} \mathbf {X}) ^ {- 1} \mathbf {X} ^ {\prime} (\mathbf {f} - \hat {\mathbf {f}}).} \end{array}
$$

Equivalently, this can be written as 

$$
\hat {\boldsymbol {\beta}} _ {o l s} - \boldsymbol {\beta} = - \left(\frac {\mathbf {X} ^ {\prime} \mathbf {X}}{L}\right) ^ {- 1} \left(\frac {\mathbf {X} ^ {\prime} \mathbf {G}}{L}\right) \boldsymbol {\beta} + \left(\frac {\mathbf {X} ^ {\prime} \mathbf {X}}{L}\right) ^ {- 1} \left(\frac {\mathbf {X} ^ {\prime} \mathbf {u}}{L}\right) + \left(\frac {\mathbf {X} ^ {\prime} \mathbf {X}}{L}\right) ^ {- 1} \left[ \frac {\mathbf {X} ^ {\prime} (\mathbf {f} - \hat {\mathbf {f}})}{L} \right].
$$

By (A.2) and the law of iterated expectations, 

$$
\mathbb {E} \left[ \frac {1}{L} \mathbf {X} ^ {\prime} \mathbf {u} \right] = \mathbb {E} \left[ \frac {1}{L} \mathbf {X} ^ {\prime} \mathbb {E} \left(\mathbf {u} \mid \mathbf {f}, \mathbf {G}, \tilde {\mathbf {X}}\right) \right] = \mathbf {0}.
$$

Under the stated law-of-large-numbers conditions, it follows that 

$$
\frac {1}{L} \mathbf {X ^ {\prime}} \mathbf {u} \xrightarrow {p} \mathbf {0}.
$$

Since 

$$
\frac {1}{L} \mathbf {X} ^ {\prime} \mathbf {X} \xrightarrow {p} \boldsymbol {Q} _ {X X},
$$

where $Q _ { X X }$ is positive definite, the continuous mapping theorem and Slutsky’s theorem imply that 

$$
\left(\frac {\mathbf {X} ^ {\prime} \mathbf {X}}{L}\right) ^ {- 1} \left(\frac {\mathbf {X} ^ {\prime} \mathbf {u}}{L}\right) \xrightarrow {p} \boldsymbol {Q} _ {X X} ^ {- 1} \mathbf {0} = \mathbf {0}.
$$

Similarly, by the assumed consistency condition for $\hat { \bf f } _ { 1 }$ 

$$
\left(\frac {\mathbf {X} ^ {\prime} \mathbf {X}}{L}\right) ^ {- 1} \left[ \frac {\mathbf {X} ^ {\prime} (\mathbf {f} - \hat {\mathbf {f}})}{L} \right] \xrightarrow {p} Q _ {X X} ^ {- 1} \mathbf {0} = \mathbf {0}.
$$

The remaining term contains the periodic component of the regressors. By the continuous 

mapping theorem and Slutsky’s theorem, 

$$
\left(\frac {\mathbf {X} ^ {\prime} \mathbf {X}}{L}\right) ^ {- 1} \left(\frac {\mathbf {X} ^ {\prime} \mathbf {G}}{L}\right) \boldsymbol {\beta} \xrightarrow {p} \boldsymbol {Q} _ {X X} ^ {- 1} \boldsymbol {Q} _ {X G} \boldsymbol {\beta}.
$$

Therefore, 

$$
\mathrm{plim} _ {L \to \infty} \hat {\pmb {\beta}} _ {o l s} = \pmb {\beta} - \pmb {Q} _ {X X} ^ {- 1} \pmb {Q} _ {X G} \pmb {\beta}.
$$

Since $Q _ { X X }$ is nonsingular, the estimator is consistent if and only if 

$$
\pmb {Q} _ {X G} \pmb {\beta} = \pmb {0}.
$$

Thus, whenever $Q _ { X G } \beta \neq \mathbf { 0 }$ , the probability limit difers from $\beta ,$ and $\hat { \beta } _ { o l s }$ is inconsistent. 

To provide a simple suficient condition for inconsistency, we define 

$$
\pmb {Q} _ {\tilde {X} G} = \mathrm{plim} _ {L \to \infty} \frac {\tilde {\mathbf {X}} ^ {\prime} \mathbf {G}}{L}, \qquad \pmb {Q} _ {G G} = \mathrm{plim} _ {L \to \infty} \frac {\mathbf {G} ^ {\prime} \mathbf {G}}{L}.
$$

Since $\mathbf { X } = \tilde { \mathbf { X } } + \mathbf { G }$ , we have 

$$
\boldsymbol {Q} _ {X G} = \boldsymbol {Q} _ {\tilde {X} G} + \boldsymbol {Q} _ {G G}.
$$

For instance, if 

$$
\boldsymbol {Q} _ {\tilde {X} G} = \mathbf {0} \qquad \mathrm{and} \qquad \beta^ {\prime} \boldsymbol {Q} _ {G G} \beta > 0,
$$

then $Q _ { X G } \beta \neq { \bf 0 }$ , rendering the estimator inconsistent. These conditions formalize the scenario in which the periodic component of the predictors has a nonzero projection onto the relevant forecasting direction. Note that $\mathbf G \neq \mathbf 0$ alone is insuficient to establish inconsistency, as the corresponding bias may trivially be zero in certain special cases. 

The root of this inconsistency can also be diagnosed by rewriting the adjusted regression as 

$$
\mathbf {y} - \hat {\mathbf {f}} = \mathbf {X} \boldsymbol {\beta} + \left[ \mathbf {u} - \mathbf {G} \boldsymbol {\beta} + (\mathbf {f} - \hat {\mathbf {f}}) \right].
$$

Even when u is exogenous and $\hat { \bf f }$ consistently estimates f, the misspecified regression error absorbs the omitted predictor-periodicity term $- \mathbf G \beta$ . Whenever $Q _ { X G } \beta \neq 0$ , this term becomes asymptotically correlated with $\mathbf { X } ,$ , thereby inducing an omitted-variable bias. 

The SPAR methodology resolves this problem by applying a within-transformation to both y and X, structurally eliminating both f and G prior to estimation. Furthermore, SPAR circumvents the need for separate consistent estimators for both f and G, which can be empirically challenging to obtain. In the Appendix, we provide forecasting results comparing these two approaches. 

A similar identification issue can manifest when the true data-generating process is nonlinear. Let the stationary components of trading volume and the explanatory variables satisfy 

$$
\tilde {y} _ {t, k} = h \left(\tilde {\mathbf {X}} _ {t, k}, \beta_ {0}\right) + e _ {t, k},\tag{A.3}
$$

where $h ( \cdot )$ is a nonlinear function that is continuously diferentiable with respect to its parameter, $\beta _ { 0 }$ is the $p \times 1$ vector of true parameters, and $e _ { t , k }$ is an error term. We denote the nonlinear forecasting function by $h ( \cdot )$ rather than $f ( \cdot )$ to distinguish it from the periodic component $f _ { k }$ 

We impose the following exogeneity condition. 

Assumption 2. The error term e satisfies 

$$
\mathbb {E} \left[ \mathbf {e} \mid \tilde {\mathbf {X}}, \mathbf {G}, \mathbf {f} \right] = \mathbf {0}.
$$

Consider a naive Nonlinear Least Squares (NLS) regression of the observed $y _ { t , k }$ on the observed $\mathbf { X } _ { t , k }$ . The corresponding misspecified model is 

$$
y _ {t, k} = h \left(\mathbf {X} _ {t, k}, \beta\right) + f _ {k} + \epsilon_ {t, k}.\tag{A.4}
$$

The NLS estimator is given by 

$$
\hat {\beta} _ {n l s} = \arg \min _ {\beta} \frac {1}{W K} \sum_ {t = 1} ^ {W} \sum_ {k = 1} ^ {K} \left[ y _ {t, k} - h \left(\mathbf {X} _ {t, k}, \beta\right) - \hat {f} _ {k} \right] ^ {2},\tag{A.5}
$$

where $\hat { f } _ { k }$ is an estimator of the periodic component satisfying 

$$
\max _ {1 \leq k \leq K} \left| \hat {f} _ {k} - f _ {k} \right| \xrightarrow {p} 0.
$$

We now provide a suficient condition under which ${ \hat { \beta } } _ { n l s }$ is inconsistent for the true parameter $\beta _ { 0 }$ 

Theorem 2. Suppose that the conditions above and the standard regularity conditions for NLS estimation hold, including uniform convergence of the sample objective function to a population objective function with a unique minimizer. If 

$$
\frac {1}{K} \sum_ {k = 1} ^ {K} \mathbb {E} \left[ \nabla_ {\beta} h \left(\mathbf {X} _ {t, k}, \beta_ {0}\right) \left\{h \left(\tilde {\mathbf {X}} _ {t, k}, \beta_ {0}\right) - h \left(\mathbf {X} _ {t, k}, \beta_ {0}\right) \right\} \right] \neq \mathbf {0},
$$

then the NLS estimator ${ \hat { \beta } } _ { n l s }$ from the misspecified model is inconsistent for $\beta _ { 0 }$ 

Proof of Theorem 2. The first-order conditions for the NLS minimization problem are 

$$
\frac {1}{W K} \sum_ {t = 1} ^ {W} \sum_ {k = 1} ^ {K} \nabla_ {\beta} h (\mathbf {X} _ {t, k}, \hat {\beta} _ {n l s}) [ y _ {t, k} - h (\mathbf {X} _ {t, k}, \hat {\beta} _ {n l s}) - \hat {f} _ {k} ] = \mathbf {0}.
$$

Since $\hat { f } _ { k }$ consistently estimates $f _ { k }$ , the limiting population objective function is 

$$
Q (\beta) = \frac {1}{K} \sum_ {k = 1} ^ {K} \mathbb {E} \left[ \left\{h \left(\tilde {\mathbf {X}} _ {t, k}, \beta_ {0}\right) + e _ {t, k} - h \left(\mathbf {X} _ {t, k}, \beta\right) \right\} ^ {2} \right].
$$

The gradient of the population objective function evaluated at the true parameter $\beta _ { 0 }$ is 

$$
\nabla_ {\beta} Q (\beta_ {0}) = - \frac {2}{K} \sum_ {k = 1} ^ {K} \mathbb {E} \left[ \nabla_ {\beta} h \left(\mathbf {X} _ {t, k}, \beta_ {0}\right) \left\{h \left(\tilde {\mathbf {X}} _ {t, k}, \beta_ {0}\right) - h \left(\mathbf {X} _ {t, k}, \beta_ {0}\right) + e _ {t, k} \right\} \right].
$$

Because $\mathbf { X } _ { t , k } = \tilde { \mathbf { X } } _ { t , k } + \mathbf { G } _ { k }$ is measurable with respect to $\tilde { \mathbf { X } }$ and G, the exogeneity assumption and the law of iterated expectations imply that 

$$
\mathbb {E} \left[ \nabla_ {\beta} h \left(\mathbf {X} _ {t, k}, \beta_ {0}\right) e _ {t, k} \right] = \mathbb {E} \left[ \nabla_ {\beta} h \left(\mathbf {X} _ {t, k}, \beta_ {0}\right) \mathbb {E} \left(e _ {t, k} \mid \tilde {\mathbf {X}}, \mathbf {G}, \mathbf {f}\right) \right] = \mathbf {0}.
$$

Therefore, 

$$
\nabla_ {\beta} Q (\beta_ {0}) = - \frac {2}{K} \sum_ {k = 1} ^ {K} \mathbb {E} \left[ \nabla_ {\beta} h \left(\mathbf {X} _ {t, k}, \beta_ {0}\right) \left\{h \left(\tilde {\mathbf {X}} _ {t, k}, \beta_ {0}\right) - h \left(\mathbf {X} _ {t, k}, \beta_ {0}\right) \right\} \right].
$$

Under the condition in Theorem 2, 

$$
\nabla_ {\beta} Q (\beta_ {0}) \neq \mathbf {0}.
$$

Hence, $\beta _ { 0 }$ cannot be the minimizer of the population objective function. Under the standard NLS regularity and identification conditions, ${ \hat { \beta } } _ { n l s }$ converges to a pseudo-true parameter diferent from $\beta _ { 0 }$ . Therefore, ${ \hat { \beta } } _ { n l s }$ is inconsistent for $\beta _ { 0 }$ □ 

Notice that the condition $\mathbf { G } _ { k } \neq \mathbf { 0 }$ alone is not suficient to establish nonlinear inconsistency. The relevant condition is that the periodic component of the predictors produces a nonzero population score at the true parameter, as formally stated in Theorem 2. 

Table A.8 shows the $R ^ { 2 }$ of the inconsistency of the OLS estimates where we use $\mathrm { D y O L S _ { 1 } }$ and DyOLS<sub>2</sub> as an example, where $\mathrm { D y O L S _ { 1 } }$ only uses intraday features and $\mathrm { D y O L S _ { 2 } }$ uses both intraday and cross-day features. The notation of DyOLS means that the withintransformation is applied only to y. We find that compared to the results of $\mathrm { S P A R _ { 1 } }$ and $\mathrm { S P A R _ { 2 } }$ in Table C.11, the prediction accuracy of the inconsistent OLS estimates is lower than that of our consistent estimate model, which supports the correctness of our model specification. 

## Appendix B. The Choice of Tuning Parameters

In this section, we introduce how to select the optimal tuning parameter $W _ { ; }$ , the training window size. To forecast intraday volume on day t+1, we tune $W$ on day t, which determines how many days we need before t for training the models. Denoted as $W _ { t } ^ { * }$ , the leave-oneout cross-validation method in Zhu et al. (2023) determines the optimal training window size. That is, first initialize a set of possible choices of W, ${ \mathcal { W } } = { \bar { \{ W ^ { ( 1 ) } , . . . , W ^ { ( L ) } \} } }$ , where $W ^ { ( 1 ) } < \cdots < W ^ { ( L ) }$ are the ordered candidate values. 

Subsequently, each sample set covering W days is further partitioned into a training set comprising the first $( W - 1 )$ days and a test set of the last day. After training the model in the training set, the predicted trading volume values are obtained for each time point on the final day. The optimal $W _ { t } ^ { * }$ is selected by identifying the window size corresponding to the minimum Mean Absolute Error (MAE) calculated on the test set. That is, 


Table A.8: Out-of-sample $R ^ { 2 }$ by direct OLS.


<table><tr><td></td><td>BAC</td><td>SPY</td><td>AAPL</td><td>GE</td><td>MSFT</td><td>CSCO</td><td>INTC</td><td>AMD</td><td>PFE</td><td>T</td></tr><tr><td><eq>DyOLS_1</eq></td><td>0.103</td><td>0.042</td><td>0.076</td><td>0.144</td><td>0.074</td><td>0.117</td><td>0.056</td><td>0.124</td><td>0.077</td><td>0.096</td></tr><tr><td><eq>DyOLS_2</eq></td><td>0.241</td><td>0.233</td><td>0.161</td><td>0.190</td><td>0.105</td><td>0.166</td><td>0.098</td><td>0.244</td><td>0.167</td><td>0.161</td></tr><tr><td></td><td>KBH</td><td>ROST</td><td>SWKS</td><td>CTXS</td><td>ETN</td><td>DE</td><td>ANF</td><td>BEN</td><td>PEG</td><td>YUM</td></tr><tr><td><eq>DyOLS_1</eq></td><td>0.118</td><td>0.085</td><td>0.150</td><td>0.069</td><td>0.064</td><td>0.108</td><td>0.153</td><td>0.037</td><td>0.019</td><td>0.164</td></tr><tr><td><eq>DyOLS_2</eq></td><td>0.223</td><td>0.157</td><td>0.279</td><td>0.230</td><td>0.202</td><td>0.248</td><td>0.308</td><td>0.169</td><td>0.102</td><td>0.265</td></tr><tr><td></td><td>MTB</td><td>ORLY</td><td>PSA</td><td>GPC</td><td>AVY</td><td>VAR</td><td>AVB</td><td>SHW</td><td>LH</td><td>NBR</td></tr><tr><td><eq>DyOLS_1</eq></td><td>0.055</td><td>0.091</td><td>-0.059</td><td>-0.003</td><td>0.037</td><td>0.094</td><td>0.020</td><td>0.096</td><td>0.054</td><td>0.090</td></tr><tr><td><eq>DyOLS_2</eq></td><td>0.141</td><td>0.171</td><td>0.098</td><td>0.178</td><td>0.177</td><td>0.200</td><td>0.136</td><td>0.198</td><td>0.170</td><td>0.139</td></tr></table>


Note: This table reports the out-of-sample $R ^ { 2 }$ of 30 assets of $\mathrm { D y O L S _ { 1 } }$ and $\mathrm { D y O L S _ { 2 } }$ when the explanatory variables are used in direct OLS estimation without removing periodicity.


$$
W _ {t} ^ {*} = \arg \min _ {W \in \mathcal {W}} \frac {1}{K} \sum_ {k = 1} ^ {K} \left| V _ {W, k} - \hat {V} _ {W, k} \right|,\tag{B.1}
$$

where $V _ { W , k }$ and $\hat { V } _ { W , k }$ refer to the true and predicted volume on Wth day of the sample set, respectively. Finally, we refit the model with $W _ { t } ^ { * }$ as our final forecast model. We use a rolling-forward forecasting framework to update our model each month, and the model is updated at the end of each month. When the model has been refitted, we use it to forecast trading volume for the next month. 

For most models, we use $\mathcal { W } = \{ 5 , 2 2 , 4 4 , 6 6 \}$ , corresponding to one week, one month, two months, and one quarter of trading days. For $\mathrm { S P A R _ { 2 } }$ and $\mathrm { S P A R _ { 4 } }$ , which are estimated using the SPJ correction, we use $\mathcal { W } = \{ 2 2 , 4 4 , 6 6 \}$ . The five-day window is excluded because the two half-panels would contain only two and three trading days, which is too short for the SPJ correction. 

Remark 7. The selection of the training window size W is a critical design choice and must be carefully balanced. On the one hand, it cannot be too short, as this would provide insuficient training samples to fit the forecasting function reliably. On the other hand, W cannot be too long, as a substantial window risks failing to capture potential dynamic relationships between the predictive features and the target variable. See Barroso et al. (2021) and Cheung (2024). 

## Appendix C. Additional Empirical Results

In this section, we present additional supplementary results. 

Table C.9 provides a complete list of tickers for the 305 assets in our sample, sorted alphabetically. 


Table C.9: List of tickers of 305 assets.


<table><tr><td>AAPL</td><td>ABC</td><td>ABT</td><td>ADBE</td><td>ADI</td><td>ADM</td><td>ADP</td><td>ADSK</td><td>AEE</td><td>AEP</td><td>AES</td><td>AFL</td><td>AIG</td><td>AIV</td></tr><tr><td>ALL</td><td>ALXN</td><td>AMAT</td><td>AMD</td><td>AMGN</td><td>AMZN</td><td>ANF</td><td>AON</td><td>APD</td><td>ATI</td><td>ATVI</td><td>AVB</td><td>AVY</td><td>AXP</td></tr><tr><td>BA</td><td>BAC</td><td>BAX</td><td>BBBY</td><td>BBY</td><td>BDX</td><td>BEN</td><td>BK</td><td>BLL</td><td>BMY</td><td>BSX</td><td>BWA</td><td>BXP</td><td>C</td></tr><tr><td>CAG</td><td>CAH</td><td>CAR</td><td>CAT</td><td>CB</td><td>CCL</td><td>CDNS</td><td>CERN</td><td>CHRW</td><td>CI</td><td>CIEN</td><td>CL</td><td>CLF</td><td>CLX</td></tr><tr><td>CMA</td><td>CMI</td><td>CMS</td><td>CNP</td><td>COF</td><td>COG</td><td>COP</td><td>COST</td><td>CPB</td><td>CSCO</td><td>CSX</td><td>CTXS</td><td>CVS</td><td>CVX</td></tr><tr><td>D</td><td>DD</td><td>DE</td><td>DGX</td><td>DHI</td><td>DHR</td><td>DIS</td><td>DISH</td><td>DLTR</td><td>DOV</td><td>DRE</td><td>DRI</td><td>DTE</td><td>DUK</td></tr><tr><td>DVA</td><td>EA</td><td>ECL</td><td>ED</td><td>EIX</td><td>EL</td><td>EMN</td><td>EMR</td><td>EOG</td><td>EQR</td><td>EQT</td><td>ES</td><td>ETFC</td><td>ETN</td></tr><tr><td>ETR</td><td>EXPD</td><td>FAST</td><td>FCX</td><td>FDX</td><td>FE</td><td>FHN</td><td>FISV</td><td>FITB</td><td>FL</td><td>GD</td><td>GE</td><td>GIS</td><td>GLW</td></tr><tr><td>GPC</td><td>GPS</td><td>GT</td><td>HAL</td><td>HAS</td><td>HBAN</td><td>HD</td><td>HES</td><td>HIG</td><td>HOG</td><td>HOLX</td><td>HON</td><td>HP</td><td>HPQ</td></tr><tr><td>HRB</td><td>HST</td><td>HSY</td><td>HUM</td><td>IBM</td><td>IGT</td><td>INCY</td><td>INTC</td><td>INTU</td><td>IP</td><td>IPG</td><td>IRM</td><td>ITW</td><td>JBL</td></tr><tr><td>JCI</td><td>JEF</td><td>JNJ</td><td>JPM</td><td>JWN</td><td>K</td><td>KBH</td><td>KEY</td><td>KIM</td><td>KLAC</td><td>KMB</td><td>KO</td><td>KR</td><td>KSS</td></tr><tr><td>KSU</td><td>L</td><td>LB</td><td>LEG</td><td>LEN</td><td>LH</td><td>LLY</td><td>LM</td><td>LMT</td><td>LNC</td><td>LOW</td><td>LPX</td><td>LRCX</td><td>LUV</td></tr><tr><td>M</td><td>MAC</td><td>MAS</td><td>MAT</td><td>MCD</td><td>MCHP</td><td>MCK</td><td>MCO</td><td>MDT</td><td>MGM</td><td>MMC</td><td>MMM</td><td>MO</td><td>MRK</td></tr><tr><td>MRO</td><td>MS</td><td>MSFT</td><td>MSI</td><td>MTB</td><td>MTG</td><td>MU</td><td>MUR</td><td>MYL</td><td>NBR</td><td>NCR</td><td>NE</td><td>NEE</td><td>NEM</td></tr><tr><td>NI</td><td>NKE</td><td>NOC</td><td>NOV</td><td>NSC</td><td>NTAP</td><td>NTRS</td><td>NUE</td><td>NWL</td><td>O</td><td>ODP</td><td>OI</td><td>OKE</td><td>OMC</td></tr><tr><td>ORCL</td><td>ORLY</td><td>OXY</td><td>PAYX</td><td>PBCT</td><td>PBI</td><td>PCAR</td><td>PCG</td><td>PEG</td><td>PEP</td><td>PFE</td><td>PG</td><td>PGR</td><td>PH</td></tr><tr><td>PHM</td><td>PLD</td><td>PNC</td><td>PPG</td><td>PPL</td><td>PSA</td><td>PVH</td><td>PXD</td><td>QCOM</td><td>RCL</td><td>RF</td><td>RHI</td><td>RIG</td><td>RL</td></tr><tr><td>ROK</td><td>ROST</td><td>RRC</td><td>SAN</td><td>SBUX</td><td>SCHW</td><td>SHW</td><td>SLB</td><td>SLM</td><td>SNV</td><td>SO</td><td>SPG</td><td>SPGI</td><td>SPY</td></tr><tr><td>STT</td><td>STZ</td><td>SWK</td><td>SWKS</td><td>SWN</td><td>SYK</td><td>SYY</td><td>T</td><td>TAP</td><td>TER</td><td>TEX</td><td>TGNA</td><td>TGT</td><td>THC</td></tr><tr><td>TIF</td><td>TJX</td><td>TMO</td><td>TROW</td><td>TRV</td><td>TSN</td><td>TT</td><td>TXN</td><td>TXT</td><td>UDR</td><td>UNH</td><td>UNM</td><td>UNP</td><td>URI</td></tr><tr><td>USB</td><td>VAR</td><td>VFC</td><td>VIAV</td><td>VLO</td><td>VNO</td><td>VTR</td><td>VZ</td><td>WBA</td><td>WDC</td><td>WEC</td><td>WELL</td><td>WFC</td><td>WHR</td></tr><tr><td>WM</td><td>WMB</td><td>WMT</td><td>WY</td><td>X</td><td>XEL</td><td>XLNX</td><td>XOM</td><td>XRX</td><td>YUM</td><td>ZION</td><td></td><td></td><td></td></tr></table>

Table C.10 reports the average out-of-sample performance of the machine-learning methods under the four feature combinations defined in Table 2. For each method, we count the number of metrics for which each feature configuration obtains the best value. We select the configuration with the largest count. This rule selects the intraday and volatility variables, specification (3), for $\mathrm { L A } _ { \mathrm { S P } }$ and $\operatorname { R F } _ { \operatorname { S P } } ;$ intraday variables, specification (1), for $\mathrm { R I } _ { \mathrm { S P } } ;$ and all variables, specification (4), for Lasso, Ridge, and RF. These configurations are used in the main empirical tables. Since the selection is based on the full evaluation sample, the resulting comparison gives the competing machine-learning methods their strongest observed specifications. 


Table C.10: Out-of-sample performance of machine learning models across feature combinations


<table><tr><td>level</td><td>(1)</td><td>(2)</td><td>(3)</td><td>(4)</td><td>(1)</td><td>(2)</td><td>(3)</td><td>(4)</td></tr><tr><td></td><td colspan="4"><eq>LA_{SP}</eq></td><td colspan="4">Lasso</td></tr><tr><td><eq>R^2</eq></td><td>0.250</td><td>0.244</td><td>0.256</td><td>0.245</td><td>0.034</td><td>0.146</td><td>0.064</td><td>0.158</td></tr><tr><td>RMSE</td><td>0.540</td><td>0.547</td><td>0.539</td><td>0.546</td><td>0.850</td><td>0.670</td><td>0.823</td><td>0.658</td></tr><tr><td>RMAE</td><td>0.383</td><td>0.388</td><td>0.382</td><td>0.387</td><td>0.448</td><td>0.427</td><td>0.441</td><td>0.420</td></tr><tr><td></td><td colspan="4"><eq>RI_{SP}</eq></td><td colspan="4">Ridge</td></tr><tr><td><eq>R^2</eq></td><td>0.248</td><td>0.230</td><td>0.249</td><td>0.232</td><td>0.036</td><td>0.122</td><td>0.058</td><td>0.139</td></tr><tr><td>RMSE</td><td>0.544</td><td>0.555</td><td>0.546</td><td>0.556</td><td>0.856</td><td>0.670</td><td>0.830</td><td>0.661</td></tr><tr><td>RMAE</td><td>0.384</td><td>0.391</td><td>0.384</td><td>0.392</td><td>0.447</td><td>0.430</td><td>0.440</td><td>0.424</td></tr><tr><td></td><td colspan="4"><eq>RF_{SP}</eq></td><td colspan="4">RF</td></tr><tr><td><eq>R^2</eq></td><td>0.259</td><td>0.243</td><td>0.262</td><td>0.246</td><td>0.056</td><td>0.167</td><td>0.065</td><td>0.169</td></tr><tr><td>RMSE</td><td>0.544</td><td>0.540</td><td>0.540</td><td>0.539</td><td>0.773</td><td>0.589</td><td>0.752</td><td>0.586</td></tr><tr><td>RMAE</td><td>0.384</td><td>0.383</td><td>0.381</td><td>0.381</td><td>0.434</td><td>0.400</td><td>0.427</td><td>0.398</td></tr></table>


Note: This table reports the average out-of-sample forecasting performance of machine learning models under four alternative feature specifications defined in Table 2. Boldfaced entries denote the best-performing specification within each model class. The selected feature combinations are subsequently used as the final benchmark specifications in the main empirical analysis. 


The remaining tables show the out-of-sample performance of all assets under diferent models. Tables C.11 and C.12 show $R ^ { 2 }$ and $R _ { \mathrm { K F } } ^ { 2 }$ based on the KF model separately. Table C.11 demonstrates that SPAR-type models universally and significantly outperform their OLS counterparts. This advantage is further quantified in Table C.12. A substantial majority of SPAR-type models exhibit positive values $R _ { \mathrm { K F } } ^ { 2 }$ (indicating superiority over the KF benchmark). In contrast, the corresponding OLS models predominantly show negative $R _ { K F } ^ { 2 } .$ 


Table C.11: Out-of-sample $R ^ { 2 }$ across forecasting models


<table><tr><td>Ticker</td><td>KF</td><td><eq>\text{SPAR}_1</eq></td><td><eq>\text{OLS}_1</eq></td><td><eq>\text{SPAR}_2</eq></td><td><eq>\text{OLS}_2</eq></td><td><eq>\text{SPAR}_3</eq></td><td><eq>\text{OLS}_3</eq></td><td><eq>\text{SPAR}_4</eq></td><td><eq>\text{OLS}_4</eq></td><td><eq>\text{LAS}_P</eq></td><td>Lasso</td><td><eq>\text{RISP}</eq></td><td>Ridge</td><td><eq>\text{RF}_{\text{SP}}</eq></td><td>RF</td></tr><tr><td>BAC</td><td>0.337</td><td>0.374</td><td>0.225</td><td>0.352</td><td>0.251</td><td>0.382</td><td>0.256</td><td>0.350</td><td>0.274</td><td>0.351</td><td>0.242</td><td>0.341</td><td>0.246</td><td>0.364</td><td>0.258</td></tr><tr><td>SPY</td><td>0.369</td><td>0.434</td><td>0.143</td><td>0.436</td><td>0.230</td><td>0.441</td><td>0.141</td><td>0.443</td><td>0.245</td><td>0.422</td><td>0.209</td><td>0.419</td><td>0.222</td><td>0.428</td><td>0.309</td></tr><tr><td>AAPL</td><td>0.260</td><td>0.319</td><td>0.137</td><td>0.325</td><td>0.195</td><td>0.319</td><td>0.161</td><td>0.322</td><td>0.190</td><td>0.300</td><td>0.183</td><td>0.309</td><td>0.149</td><td>0.281</td><td>0.227</td></tr><tr><td>GE</td><td>0.290</td><td>0.295</td><td>0.137</td><td>0.297</td><td>0.208</td><td>0.297</td><td>0.152</td><td>0.300</td><td>0.238</td><td>0.257</td><td>0.187</td><td>0.241</td><td>0.154</td><td>0.268</td><td>0.164</td></tr><tr><td>MSFT</td><td>0.036</td><td>0.149</td><td>-0.003</td><td>0.139</td><td>0.093</td><td>0.148</td><td>0.012</td><td>0.136</td><td>0.090</td><td>0.140</td><td>0.093</td><td>0.142</td><td>0.083</td><td>0.128</td><td>0.093</td></tr><tr><td>CSCO</td><td>0.194</td><td>0.237</td><td>0.135</td><td>0.242</td><td>0.131</td><td>0.270</td><td>0.159</td><td>0.277</td><td>0.146</td><td>0.217</td><td>0.137</td><td>0.223</td><td>0.128</td><td>0.252</td><td>0.117</td></tr><tr><td>INTC</td><td>0.164</td><td>0.176</td><td>-0.010</td><td>0.166</td><td>0.028</td><td>0.174</td><td>0.009</td><td>0.164</td><td>0.101</td><td>0.162</td><td>0.079</td><td>0.151</td><td>0.055</td><td>0.161</td><td>0.111</td></tr><tr><td>AMD</td><td>0.360</td><td>0.408</td><td>0.240</td><td>0.402</td><td>0.255</td><td>0.406</td><td>0.259</td><td>0.395</td><td>0.307</td><td>0.347</td><td>0.278</td><td>0.319</td><td>0.249</td><td>0.381</td><td>0.229</td></tr><tr><td>PFE</td><td>0.239</td><td>0.251</td><td>0.025</td><td>0.239</td><td>0.136</td><td>0.249</td><td>0.038</td><td>0.232</td><td>0.135</td><td>0.200</td><td>0.122</td><td>0.180</td><td>0.109</td><td>0.230</td><td>0.158</td></tr><tr><td>T</td><td>0.262</td><td>0.264</td><td>0.040</td><td>0.251</td><td>0.128</td><td>0.267</td><td>0.084</td><td>0.260</td><td>0.157</td><td>0.232</td><td>0.112</td><td>0.224</td><td>0.107</td><td>0.242</td><td>0.156</td></tr><tr><td>KBH</td><td>0.295</td><td>0.321</td><td>0.193</td><td>0.302</td><td>0.200</td><td>0.321</td><td>0.212</td><td>0.318</td><td>0.220</td><td>0.263</td><td>0.170</td><td>0.268</td><td>0.138</td><td>0.288</td><td>0.179</td></tr><tr><td>ROST</td><td>0.207</td><td>0.213</td><td>0.059</td><td>0.208</td><td>0.136</td><td>0.211</td><td>0.067</td><td>0.205</td><td>0.135</td><td>0.189</td><td>0.119</td><td>0.189</td><td>0.079</td><td>0.198</td><td>0.130</td></tr><tr><td>SWKS</td><td>0.385</td><td>0.393</td><td>0.291</td><td>0.386</td><td>0.292</td><td>0.391</td><td>0.315</td><td>0.387</td><td>0.310</td><td>0.308</td><td>0.276</td><td>0.324</td><td>0.266</td><td>0.355</td><td>0.254</td></tr><tr><td>CTXS</td><td>0.302</td><td>0.344</td><td>0.241</td><td>0.333</td><td>0.249</td><td>0.339</td><td>0.242</td><td>0.328</td><td>0.252</td><td>0.271</td><td>0.215</td><td>0.256</td><td>0.191</td><td>0.305</td><td>0.197</td></tr><tr><td>ETN</td><td>0.291</td><td>0.314</td><td>0.115</td><td>0.304</td><td>0.195</td><td>0.313</td><td>0.129</td><td>0.301</td><td>0.202</td><td>0.264</td><td>0.171</td><td>0.249</td><td>0.134</td><td>0.287</td><td>0.193</td></tr><tr><td>DE</td><td>0.327</td><td>0.335</td><td>0.218</td><td>0.329</td><td>0.243</td><td>0.337</td><td>0.237</td><td>0.329</td><td>0.247</td><td>0.300</td><td>0.226</td><td>0.295</td><td>0.202</td><td>0.306</td><td>0.214</td></tr><tr><td>ANF</td><td>0.416</td><td>0.420</td><td>0.343</td><td>0.420</td><td>0.281</td><td>0.418</td><td>0.355</td><td>0.425</td><td>0.317</td><td>0.352</td><td>0.268</td><td>0.343</td><td>0.229</td><td>0.348</td><td>0.264</td></tr><tr><td>BEN</td><td>0.259</td><td>0.303</td><td>-0.049</td><td>0.288</td><td>0.140</td><td>0.297</td><td>-0.046</td><td>0.287</td><td>0.154</td><td>0.276</td><td>0.127</td><td>0.272</td><td>0.126</td><td>0.281</td><td>0.176</td></tr><tr><td>PEG</td><td>0.164</td><td>0.200</td><td>-0.205</td><td>0.184</td><td>0.061</td><td>0.197</td><td>-0.170</td><td>0.183</td><td>0.072</td><td>0.181</td><td>0.052</td><td>0.181</td><td>0.027</td><td>0.184</td><td>0.113</td></tr><tr><td>YUM</td><td>0.356</td><td>0.363</td><td>0.260</td><td>0.337</td><td>0.268</td><td>0.358</td><td>0.265</td><td>0.344</td><td>0.278</td><td>0.306</td><td>0.249</td><td>0.289</td><td>0.205</td><td>0.293</td><td>0.220</td></tr><tr><td>MTB</td><td>0.287</td><td>0.335</td><td>0.112</td><td>0.293</td><td>0.152</td><td>0.374</td><td>0.138</td><td>0.365</td><td>0.193</td><td>0.350</td><td>0.110</td><td>0.279</td><td>0.105</td><td>0.291</td><td>0.105</td></tr><tr><td>ORLY</td><td>0.241</td><td>0.249</td><td>0.122</td><td>0.247</td><td>0.171</td><td>0.250</td><td>0.139</td><td>0.248</td><td>0.178</td><td>0.204</td><td>0.174</td><td>0.185</td><td>0.147</td><td>0.207</td><td>0.132</td></tr><tr><td>PSA</td><td>0.160</td><td>0.210</td><td>-0.411</td><td>0.203</td><td>0.007</td><td>0.214</td><td>-0.372</td><td>0.200</td><td>0.033</td><td>0.184</td><td>-0.026</td><td>0.176</td><td>-0.045</td><td>0.204</td><td>0.107</td></tr><tr><td>GPC</td><td>0.235</td><td>0.283</td><td>-0.008</td><td>0.269</td><td>0.157</td><td>0.281</td><td>0.013</td><td>0.271</td><td>0.157</td><td>0.261</td><td>0.141</td><td>0.249</td><td>0.119</td><td>0.246</td><td>0.151</td></tr><tr><td>AVY</td><td>0.221</td><td>0.263</td><td>0.026</td><td>0.252</td><td>0.163</td><td>0.260</td><td>0.035</td><td>0.247</td><td>0.169</td><td>0.220</td><td>0.155</td><td>0.229</td><td>0.127</td><td>0.234</td><td>0.151</td></tr><tr><td>VAR</td><td>0.232</td><td>0.288</td><td>0.143</td><td>0.291</td><td>0.179</td><td>0.287</td><td>0.142</td><td>0.280</td><td>0.176</td><td>0.264</td><td>0.162</td><td>0.262</td><td>0.153</td><td>0.227</td><td>0.136</td></tr><tr><td>AVB</td><td>0.216</td><td>0.246</td><td>-0.178</td><td>0.242</td><td>0.072</td><td>0.248</td><td>-0.163</td><td>0.241</td><td>0.092</td><td>0.216</td><td>0.057</td><td>0.219</td><td>0.037</td><td>0.218</td><td>0.104</td></tr><tr><td>SHW</td><td>0.259</td><td>0.272</td><td>0.109</td><td>0.269</td><td>0.187</td><td>0.272</td><td>0.116</td><td>0.265</td><td>0.185</td><td>0.232</td><td>0.167</td><td>0.222</td><td>0.151</td><td>0.249</td><td>0.162</td></tr><tr><td>LH</td><td>0.206</td><td>0.232</td><td>0.099</td><td>0.226</td><td>0.152</td><td>0.226</td><td>0.109</td><td>0.218</td><td>0.154</td><td>0.205</td><td>0.144</td><td>0.203</td><td>0.138</td><td>0.195</td><td>0.130</td></tr><tr><td>NBR</td><td>0.203</td><td>0.237</td><td>0.050</td><td>0.233</td><td>0.148</td><td>0.237</td><td>0.071</td><td>0.238</td><td>0.159</td><td>0.197</td><td>0.136</td><td>0.201</td><td>0.124</td><td>0.209</td><td>0.129</td></tr></table>


Note: This table reports the out-of-sample $\overline { { R ^ { 2 } } }$ of all competing forecasting models for each asset. Higher values indicate better forecasting performance. For each stock, the best-performing model is shown in bold. 


Next, we will evaluate the model based on RMSE and RMAE, and provide the p-values of their Model Confidence Set test. The results are straightforward. The smaller the error or the larger the p-value, the better the performance of the model. Tables C.13, C.14, C.15 and C.16 show a common trend: the model with the lowest error is either $\mathrm { S P A R _ { 1 } }$ or $\mathrm { S P A R _ { 3 } } .$ and the p-values of the MCS test further confirm this result. 


Table C.12: Out-of-sample $R _ { \mathrm { K F } } ^ { 2 }$ across forecasting models


<table><tr><td>Ticker</td><td><eq>\text{SPAR}_1</eq></td><td><eq>\text{OLS}_1</eq></td><td><eq>\text{SPAR}_2</eq></td><td><eq>\text{OLS}_2</eq></td><td><eq>\text{SPAR}_3</eq></td><td><eq>\text{OLS}_3</eq></td><td><eq>\text{SPAR}_4</eq></td><td><eq>\text{OLS}_4</eq></td><td><eq>\text{LA}_{\text{SP}}</eq></td><td>Lasso</td><td><eq>\text{RI}_{\text{SP}}</eq></td><td>Ridge</td><td><eq>\text{RF}_{\text{SP}}</eq></td><td>RF</td></tr><tr><td>BAC</td><td>0.043</td><td>-0.215</td><td>0.010</td><td>-0.160</td><td>0.041</td><td>-0.175</td><td>0.004</td><td>-0.125</td><td>-0.010</td><td>-0.201</td><td>-0.013</td><td>-0.202</td><td>0.022</td><td>-0.152</td></tr><tr><td>SPY</td><td>0.064</td><td>-0.363</td><td>0.056</td><td>-0.246</td><td>0.075</td><td>-0.387</td><td>0.068</td><td>-0.220</td><td>0.046</td><td>-0.275</td><td>0.043</td><td>-0.264</td><td>0.060</td><td>-0.142</td></tr><tr><td>AAPL</td><td>0.062</td><td>-0.238</td><td>0.059</td><td>-0.152</td><td>0.059</td><td>-0.219</td><td>0.060</td><td>-0.123</td><td>0.008</td><td>-0.168</td><td>0.023</td><td>-0.216</td><td>0.029</td><td>-0.099</td></tr><tr><td>GE</td><td>0.008</td><td>-0.221</td><td>-0.001</td><td>-0.130</td><td>0.008</td><td>-0.196</td><td>0.005</td><td>-0.099</td><td>-0.049</td><td>-0.175</td><td>-0.076</td><td>-0.221</td><td>-0.040</td><td>-0.194</td></tr><tr><td>MSFT</td><td>0.122</td><td>-0.070</td><td>0.128</td><td>0.021</td><td>0.126</td><td>-0.056</td><td>0.126</td><td>0.034</td><td>0.110</td><td>0.010</td><td>0.116</td><td>-0.003</td><td>0.100</td><td>0.050</td></tr><tr><td>CSCO</td><td>0.065</td><td>-0.083</td><td>0.089</td><td>-0.094</td><td>0.106</td><td>-0.041</td><td>0.123</td><td>-0.065</td><td>0.040</td><td>-0.098</td><td>0.044</td><td>-0.103</td><td>0.092</td><td>-0.095</td></tr><tr><td>INTC</td><td>0.023</td><td>-0.230</td><td>0.023</td><td>-0.181</td><td>0.022</td><td>-0.198</td><td>0.020</td><td>-0.084</td><td>0.007</td><td>-0.124</td><td>-0.004</td><td>-0.164</td><td>0.014</td><td>-0.068</td></tr><tr><td>AMD</td><td>0.074</td><td>-0.218</td><td>0.066</td><td>-0.186</td><td>0.068</td><td>-0.146</td><td>0.055</td><td>-0.090</td><td>-0.032</td><td>-0.173</td><td>-0.077</td><td>-0.224</td><td>0.027</td><td>-0.184</td></tr><tr><td>PFE</td><td>0.022</td><td>-0.307</td><td>0.005</td><td>-0.145</td><td>0.018</td><td>-0.278</td><td>-0.008</td><td>-0.132</td><td>-0.044</td><td>-0.171</td><td>-0.072</td><td>-0.198</td><td>-0.013</td><td>-0.109</td></tr><tr><td>T</td><td>0.013</td><td>-0.325</td><td>-0.003</td><td>-0.198</td><td>0.007</td><td>-0.280</td><td>0.004</td><td>-0.162</td><td>-0.040</td><td>-0.234</td><td>-0.049</td><td>-0.272</td><td>-0.025</td><td>-0.178</td></tr><tr><td>KBH</td><td>0.046</td><td>-0.162</td><td>0.022</td><td>-0.142</td><td>0.051</td><td>-0.123</td><td>0.043</td><td>-0.110</td><td>-0.036</td><td>-0.196</td><td>-0.028</td><td>-0.253</td><td>-0.006</td><td>-0.173</td></tr><tr><td>ROST</td><td>0.028</td><td>-0.213</td><td>0.019</td><td>-0.100</td><td>0.022</td><td>-0.191</td><td>0.017</td><td>-0.094</td><td>-0.006</td><td>-0.137</td><td>-0.007</td><td>-0.180</td><td>0.009</td><td>-0.111</td></tr><tr><td>SWKS</td><td>0.016</td><td>-0.169</td><td>0.025</td><td>-0.159</td><td>0.014</td><td>-0.126</td><td>0.025</td><td>-0.126</td><td>-0.123</td><td>-0.194</td><td>-0.100</td><td>-0.220</td><td>-0.038</td><td>-0.222</td></tr><tr><td>CTXS</td><td>0.065</td><td>-0.102</td><td>0.062</td><td>-0.095</td><td>0.059</td><td>-0.095</td><td>0.056</td><td>-0.085</td><td>-0.037</td><td>-0.161</td><td>-0.062</td><td>-0.190</td><td>0.012</td><td>-0.154</td></tr><tr><td>ETN</td><td>0.032</td><td>-0.286</td><td>0.022</td><td>-0.147</td><td>0.029</td><td>-0.254</td><td>0.018</td><td>-0.133</td><td>-0.032</td><td>-0.195</td><td>-0.051</td><td>-0.242</td><td>-0.007</td><td>-0.161</td></tr><tr><td>DE</td><td>0.029</td><td>-0.175</td><td>0.022</td><td>-0.142</td><td>0.031</td><td>-0.156</td><td>0.019</td><td>-0.123</td><td>-0.019</td><td>-0.178</td><td>-0.025</td><td>-0.214</td><td>-0.018</td><td>-0.174</td></tr><tr><td>ANF</td><td>0.036</td><td>-0.106</td><td>0.036</td><td>-0.212</td><td>0.034</td><td>-0.087</td><td>0.047</td><td>-0.146</td><td>-0.079</td><td>-0.250</td><td>-0.092</td><td>-0.299</td><td>-0.083</td><td>-0.226</td></tr><tr><td>BEN</td><td>0.053</td><td>-0.463</td><td>0.029</td><td>-0.185</td><td>0.045</td><td>-0.430</td><td>0.029</td><td>-0.156</td><td>0.014</td><td>-0.208</td><td>0.012</td><td>-0.209</td><td>0.018</td><td>-0.123</td></tr><tr><td>PEG</td><td>0.042</td><td>-0.471</td><td>0.031</td><td>-0.148</td><td>0.039</td><td>-0.433</td><td>0.029</td><td>-0.136</td><td>0.021</td><td>-0.180</td><td>0.017</td><td>-0.199</td><td>0.023</td><td>-0.076</td></tr><tr><td>YUM</td><td>0.023</td><td>-0.152</td><td>-0.016</td><td>-0.142</td><td>0.020</td><td>-0.134</td><td>-0.002</td><td>-0.126</td><td>-0.066</td><td>-0.204</td><td>-0.082</td><td>-0.270</td><td>-0.094</td><td>-0.229</td></tr><tr><td>MTB</td><td>0.060</td><td>-0.277</td><td>-0.005</td><td>-0.204</td><td>0.113</td><td>-0.244</td><td>0.098</td><td>-0.184</td><td>0.076</td><td>-0.282</td><td>-0.022</td><td>-0.273</td><td>-0.019</td><td>-0.281</td></tr><tr><td>ORLY</td><td>0.009</td><td>-0.166</td><td>0.011</td><td>-0.112</td><td>0.012</td><td>-0.156</td><td>0.009</td><td>-0.095</td><td>-0.052</td><td>-0.121</td><td>-0.077</td><td>-0.144</td><td>-0.045</td><td>-0.148</td></tr><tr><td>PSA</td><td>0.058</td><td>-0.689</td><td>0.048</td><td>-0.189</td><td>0.059</td><td>-0.643</td><td>0.045</td><td>-0.163</td><td>0.034</td><td>-0.234</td><td>0.021</td><td>-0.257</td><td>0.044</td><td>-0.073</td></tr><tr><td>GPC</td><td>0.051</td><td>-0.349</td><td>0.043</td><td>-0.126</td><td>0.048</td><td>-0.315</td><td>0.046</td><td>-0.117</td><td>0.014</td><td>-0.161</td><td>0.005</td><td>-0.181</td><td>0.008</td><td>-0.126</td></tr><tr><td>AVY</td><td>0.057</td><td>-0.289</td><td>0.047</td><td>-0.085</td><td>0.055</td><td>-0.264</td><td>0.040</td><td>-0.076</td><td>0.000</td><td>-0.114</td><td>0.016</td><td>-0.148</td><td>0.015</td><td>-0.104</td></tr><tr><td>VAR</td><td>0.092</td><td>-0.132</td><td>0.093</td><td>-0.056</td><td>0.091</td><td>-0.131</td><td>0.078</td><td>-0.069</td><td>0.063</td><td>-0.095</td><td>0.059</td><td>-0.102</td><td>0.012</td><td>-0.113</td></tr><tr><td>AVB</td><td>0.039</td><td>-0.540</td><td>0.031</td><td>-0.191</td><td>0.039</td><td>-0.505</td><td>0.028</td><td>-0.169</td><td>-0.001</td><td>-0.236</td><td>0.005</td><td>-0.262</td><td>-0.011</td><td>-0.160</td></tr><tr><td>SHW</td><td>0.025</td><td>-0.221</td><td>0.019</td><td>-0.119</td><td>0.030</td><td>-0.216</td><td>0.016</td><td>-0.122</td><td>-0.027</td><td>-0.152</td><td>-0.042</td><td>-0.168</td><td>-0.012</td><td>-0.138</td></tr><tr><td>LH</td><td>0.037</td><td>-0.160</td><td>0.031</td><td>-0.076</td><td>0.033</td><td>-0.154</td><td>0.026</td><td>-0.067</td><td>0.002</td><td>-0.106</td><td>0.000</td><td>-0.117</td><td>-0.008</td><td>-0.092</td></tr><tr><td>NBR</td><td>0.030</td><td>-0.223</td><td>0.029</td><td>-0.107</td><td>0.026</td><td>-0.196</td><td>0.032</td><td>-0.085</td><td>-0.022</td><td>-0.132</td><td>-0.016</td><td>-0.136</td><td>-0.014</td><td>-0.112</td></tr></table>


Note: This table reports the relative out-of-sample $R _ { \mathrm { K F } } ^ { 2 }$ for each forecasting model, where the Kalman filter (KF) serves as the benchmark. Positive (negative) values indicate that the competing model achieves a lower (higher) out-of-sample mean squared prediction error than the KF benchmark. Bold values denote the best-performing model for each asset. 



Table C.13: Out-of-sample RMSE across forecasting models


<table><tr><td>Ticker</td><td>KF</td><td><eq>\text{SPAR}_1</eq></td><td><eq>\text{OLS}_1</eq></td><td><eq>\text{SPAR}_2</eq></td><td><eq>\text{OLS}_2</eq></td><td><eq>\text{SPAR}_3</eq></td><td><eq>\text{OLS}_3</eq></td><td><eq>\text{SPAR}_4</eq></td><td><eq>\text{OLS}_4</eq></td><td><eq>\text{LA}_{\text{SP}}</eq></td><td>Lasso</td><td><eq>\text{RI}_{\text{SP}}</eq></td><td>Ridge</td><td><eq>\text{RF}_{\text{SP}}</eq></td><td>RF</td></tr><tr><td>BAC</td><td>0.349</td><td>0.305</td><td>0.426</td><td>0.310</td><td>0.380</td><td>0.303</td><td>0.407</td><td>0.310</td><td>0.365</td><td>0.312</td><td>0.375</td><td>0.315</td><td>0.383</td><td>0.311</td><td>0.347</td></tr><tr><td>SPY</td><td>0.285</td><td>0.267</td><td>0.451</td><td>0.272</td><td>0.366</td><td>0.267</td><td>0.450</td><td>0.272</td><td>0.368</td><td>0.271</td><td>0.374</td><td>0.270</td><td>0.372</td><td>0.271</td><td>0.304</td></tr><tr><td>AAPL</td><td>0.440</td><td>0.449</td><td>0.616</td><td>0.448</td><td>0.528</td><td>0.454</td><td>0.599</td><td>0.451</td><td>0.523</td><td>0.437</td><td>0.528</td><td>0.439</td><td>0.532</td><td>0.432</td><td>0.466</td></tr><tr><td>GE</td><td>0.415</td><td>0.406</td><td>0.599</td><td>0.410</td><td>0.498</td><td>0.405</td><td>0.573</td><td>0.409</td><td>0.482</td><td>0.411</td><td>0.507</td><td>0.419</td><td>0.513</td><td>0.414</td><td>0.461</td></tr><tr><td>MSFT</td><td>1.213</td><td>0.624</td><td>0.894</td><td>0.625</td><td>0.732</td><td>0.623</td><td>0.877</td><td>0.625</td><td>0.721</td><td>0.623</td><td>0.731</td><td>0.620</td><td>0.734</td><td>0.625</td><td>0.658</td></tr><tr><td>CSCO</td><td>0.706</td><td>0.568</td><td>0.859</td><td>0.569</td><td>0.687</td><td>0.570</td><td>0.819</td><td>0.568</td><td>0.668</td><td>0.576</td><td>0.689</td><td>0.583</td><td>0.681</td><td>0.574</td><td>0.615</td></tr><tr><td>INTC</td><td>0.591</td><td>0.583</td><td>0.854</td><td>0.578</td><td>0.762</td><td>0.582</td><td>0.818</td><td>0.580</td><td>0.676</td><td>0.587</td><td>0.701</td><td>0.590</td><td>0.720</td><td>0.585</td><td>0.629</td></tr><tr><td>AMD</td><td>0.770</td><td>0.723</td><td>0.913</td><td>0.730</td><td>0.842</td><td>0.723</td><td>0.883</td><td>0.731</td><td>0.819</td><td>0.740</td><td>0.844</td><td>0.745</td><td>0.850</td><td>0.739</td><td>0.797</td></tr><tr><td>PFE</td><td>0.410</td><td>0.399</td><td>0.635</td><td>0.403</td><td>0.495</td><td>0.399</td><td>0.612</td><td>0.405</td><td>0.488</td><td>0.405</td><td>0.512</td><td>0.412</td><td>0.509</td><td>0.408</td><td>0.447</td></tr><tr><td>T</td><td>0.382</td><td>0.375</td><td>0.576</td><td>0.380</td><td>0.477</td><td>0.377</td><td>0.551</td><td>0.379</td><td>0.462</td><td>0.383</td><td>0.480</td><td>0.387</td><td>0.490</td><td>0.384</td><td>0.430</td></tr><tr><td>KBH</td><td>0.619</td><td>0.580</td><td>0.837</td><td>0.590</td><td>0.709</td><td>0.579</td><td>0.816</td><td>0.587</td><td>0.701</td><td>0.597</td><td>0.719</td><td>0.609</td><td>0.727</td><td>0.595</td><td>0.656</td></tr><tr><td>ROST</td><td>0.649</td><td>0.619</td><td>0.919</td><td>0.627</td><td>0.740</td><td>0.622</td><td>0.885</td><td>0.628</td><td>0.724</td><td>0.630</td><td>0.749</td><td>0.632</td><td>0.752</td><td>0.631</td><td>0.680</td></tr><tr><td>SWKS</td><td>0.454</td><td>0.430</td><td>0.625</td><td>0.428</td><td>0.551</td><td>0.429</td><td>0.588</td><td>0.429</td><td>0.524</td><td>0.444</td><td>0.546</td><td>0.444</td><td>0.548</td><td>0.439</td><td>0.488</td></tr><tr><td>CTXS</td><td>0.662</td><td>0.621</td><td>0.947</td><td>0.626</td><td>0.785</td><td>0.621</td><td>0.915</td><td>0.629</td><td>0.772</td><td>0.637</td><td>0.798</td><td>0.645</td><td>0.790</td><td>0.637</td><td>0.703</td></tr><tr><td>ETN</td><td>0.436</td><td>0.410</td><td>0.646</td><td>0.414</td><td>0.513</td><td>0.410</td><td>0.621</td><td>0.415</td><td>0.506</td><td>0.420</td><td>0.521</td><td>0.424</td><td>0.522</td><td>0.421</td><td>0.469</td></tr><tr><td>DE</td><td>0.447</td><td>0.425</td><td>0.622</td><td>0.429</td><td>0.522</td><td>0.424</td><td>0.600</td><td>0.431</td><td>0.510</td><td>0.433</td><td>0.526</td><td>0.439</td><td>0.528</td><td>0.437</td><td>0.473</td></tr><tr><td>ANF</td><td>0.502</td><td>0.465</td><td>0.719</td><td>0.474</td><td>0.637</td><td>0.467</td><td>0.695</td><td>0.473</td><td>0.613</td><td>0.479</td><td>0.634</td><td>0.480</td><td>0.634</td><td>0.477</td><td>0.540</td></tr><tr><td>BEN</td><td>0.544</td><td>0.503</td><td>0.864</td><td>0.509</td><td>0.644</td><td>0.505</td><td>0.835</td><td>0.510</td><td>0.632</td><td>0.516</td><td>0.651</td><td>0.520</td><td>0.643</td><td>0.515</td><td>0.563</td></tr><tr><td>PEG</td><td>0.584</td><td>0.553</td><td>0.963</td><td>0.560</td><td>0.682</td><td>0.553</td><td>0.933</td><td>0.559</td><td>0.674</td><td>0.560</td><td>0.696</td><td>0.567</td><td>0.702</td><td>0.564</td><td>0.607</td></tr><tr><td>YUM</td><td>0.485</td><td>0.459</td><td>0.738</td><td>0.465</td><td>0.579</td><td>0.459</td><td>0.710</td><td>0.464</td><td>0.565</td><td>0.468</td><td>0.585</td><td>0.469</td><td>0.591</td><td>0.475</td><td>0.516</td></tr><tr><td>MTB</td><td>0.694</td><td>0.626</td><td>1.070</td><td>0.635</td><td>0.781</td><td>0.628</td><td>1.038</td><td>0.637</td><td>0.778</td><td>0.642</td><td>0.804</td><td>0.654</td><td>0.802</td><td>0.646</td><td>0.715</td></tr><tr><td>ORLY</td><td>0.747</td><td>0.715</td><td>1.000</td><td>0.723</td><td>0.836</td><td>0.714</td><td>0.968</td><td>0.723</td><td>0.822</td><td>0.728</td><td>0.836</td><td>0.738</td><td>0.837</td><td>0.727</td><td>0.771</td></tr><tr><td>PSA</td><td>0.670</td><td>0.618</td><td>1.189</td><td>0.622</td><td>0.782</td><td>0.620</td><td>1.152</td><td>0.627</td><td>0.768</td><td>0.631</td><td>0.796</td><td>0.638</td><td>0.803</td><td>0.631</td><td>0.673</td></tr><tr><td>GPC</td><td>0.631</td><td>0.585</td><td>1.012</td><td>0.587</td><td>0.725</td><td>0.587</td><td>0.966</td><td>0.587</td><td>0.716</td><td>0.603</td><td>0.741</td><td>0.607</td><td>0.741</td><td>0.601</td><td>0.646</td></tr><tr><td>AVY</td><td>0.684</td><td>0.636</td><td>1.074</td><td>0.643</td><td>0.772</td><td>0.635</td><td>1.035</td><td>0.649</td><td>0.767</td><td>0.650</td><td>0.784</td><td>0.654</td><td>0.796</td><td>0.651</td><td>0.702</td></tr><tr><td>VAR</td><td>0.642</td><td>0.583</td><td>0.947</td><td>0.591</td><td>0.708</td><td>0.584</td><td>0.917</td><td>0.594</td><td>0.705</td><td>0.593</td><td>0.724</td><td>0.593</td><td>0.725</td><td>0.597</td><td>0.646</td></tr><tr><td>AVB</td><td>0.684</td><td>0.628</td><td>1.206</td><td>0.636</td><td>0.799</td><td>0.629</td><td>1.170</td><td>0.638</td><td>0.783</td><td>0.642</td><td>0.805</td><td>0.643</td><td>0.812</td><td>0.640</td><td>0.695</td></tr><tr><td>SHW</td><td>0.607</td><td>0.570</td><td>0.867</td><td>0.575</td><td>0.697</td><td>0.570</td><td>0.846</td><td>0.576</td><td>0.694</td><td>0.582</td><td>0.708</td><td>0.589</td><td>0.708</td><td>0.583</td><td>0.634</td></tr><tr><td>LH</td><td>0.755</td><td>0.713</td><td>1.019</td><td>0.717</td><td>0.834</td><td>0.714</td><td>0.995</td><td>0.722</td><td>0.817</td><td>0.728</td><td>0.845</td><td>0.737</td><td>0.848</td><td>0.726</td><td>0.772</td></tr><tr><td>NBR</td><td>0.466</td><td>0.444</td><td>0.628</td><td>0.446</td><td>0.531</td><td>0.443</td><td>0.610</td><td>0.444</td><td>0.519</td><td>0.455</td><td>0.538</td><td>0.461</td><td>0.537</td><td>0.453</td><td>0.491</td></tr></table>


Note: This table reports the relative mean squared error (RMSE) of the out-of-sample forecasts for each forecasting model and each asset. Lower values indicate smaller prediction errors and therefore better forecasting performance. For each asset, the model with the lowest RMSE is highlighted in bold. 



Table C.14: Model Confidence Set p-values based on RMSE


<table><tr><td>Ticker</td><td>KF</td><td><eq>\text{SPAR}_1</eq></td><td><eq>\text{OLS}_1</eq></td><td><eq>\text{SPAR}_2</eq></td><td><eq>\text{OLS}_2</eq></td><td><eq>\text{SPAR}_3</eq></td><td><eq>\text{OLS}_3</eq></td><td><eq>\text{SPAR}_4</eq></td><td><eq>\text{OLS}_4</eq></td><td><eq>\text{LA}_{\text{SP}}</eq></td><td>Lasso</td><td><eq>\text{RI}_{\text{SP}}</eq></td><td>Ridge</td><td><eq>\text{RF}_{\text{SP}}</eq></td><td>RF</td></tr><tr><td>BAC</td><td>0.320**</td><td>0.320**</td><td>-</td><td>0.320**</td><td>-</td><td>1.000**</td><td>-</td><td>0.320**</td><td>-</td><td>0.320**</td><td>-</td><td>0.320**</td><td>-</td><td>0.320**</td><td>-</td></tr><tr><td>SPY</td><td>-</td><td>0.826**</td><td>-</td><td>0.112*</td><td>-</td><td>1.000**</td><td>-</td><td>0.112*</td><td>-</td><td>0.112*</td><td>-</td><td>0.120*</td><td>-</td><td>0.112*</td><td>-</td></tr><tr><td>AAPL</td><td>0.782**</td><td>0.631**</td><td>-</td><td>0.782**</td><td>-</td><td>0.588**</td><td>-</td><td>0.660**</td><td>-</td><td>0.782**</td><td>-</td><td>0.782**</td><td>-</td><td>1.000**</td><td>0.083</td></tr><tr><td>GE</td><td>0.031</td><td>0.399**</td><td>-</td><td>0.210*</td><td>-</td><td>1.000**</td><td>-</td><td>0.210*</td><td>-</td><td>0.210*</td><td>-</td><td>0.031</td><td>-</td><td>0.031</td><td>-</td></tr><tr><td>MSFT</td><td>0.530**</td><td>0.914**</td><td>-</td><td>0.827**</td><td>0.530**</td><td>0.914**</td><td>0.001</td><td>0.914**</td><td>0.530**</td><td>0.914**</td><td>0.530**</td><td>1.000**</td><td>0.530**</td><td>0.914**</td><td>0.530**</td></tr><tr><td>CSCO</td><td>0.463**</td><td>1.000**</td><td>-</td><td>0.794**</td><td>-</td><td>0.617**</td><td>-</td><td>0.871**</td><td>0.001</td><td>0.463**</td><td>-</td><td>0.463**</td><td>0.000</td><td>0.463**</td><td>0.080</td></tr><tr><td>INTC</td><td>0.023</td><td>0.251**</td><td>-</td><td>1.000**</td><td>0.008</td><td>0.370**</td><td>-</td><td>0.370**</td><td>-</td><td>0.047</td><td>-</td><td>0.037</td><td>-</td><td>0.142*</td><td>0.008</td></tr><tr><td>AMD</td><td>0.001</td><td>0.709**</td><td>-</td><td>0.031</td><td>-</td><td>1.000**</td><td>-</td><td>0.003</td><td>-</td><td>0.003</td><td>-</td><td>0.001</td><td>-</td><td>0.003</td><td>-</td></tr><tr><td>PFE</td><td>0.003</td><td>0.537**</td><td>-</td><td>0.032</td><td>-</td><td>1.000**</td><td>-</td><td>0.032</td><td>-</td><td>0.032</td><td>-</td><td>0.003</td><td>-</td><td>0.003</td><td>-</td></tr><tr><td>T</td><td>0.116*</td><td>1.000**</td><td>-</td><td>0.116*</td><td>-</td><td>0.123*</td><td>-</td><td>0.116*</td><td>-</td><td>0.116*</td><td>-</td><td>0.036</td><td>-</td><td>0.036</td><td>-</td></tr><tr><td>KBH</td><td>-</td><td>0.068</td><td>-</td><td>0.009</td><td>-</td><td>1.000**</td><td>-</td><td>0.009</td><td>-</td><td>0.009</td><td>-</td><td>0.009</td><td>-</td><td>0.009</td><td>-</td></tr><tr><td>ROST</td><td>-</td><td>1.000**</td><td>-</td><td>0.065</td><td>-</td><td>0.065</td><td>-</td><td>0.065</td><td>-</td><td>0.065</td><td>-</td><td>0.065</td><td>-</td><td>0.065</td><td>-</td></tr><tr><td>SWKS</td><td>-</td><td>0.663**</td><td>-</td><td>1.000**</td><td>-</td><td>0.735**</td><td>-</td><td>0.735**</td><td>-</td><td>0.000</td><td>-</td><td>0.007</td><td>-</td><td>0.007</td><td>-</td></tr><tr><td>CTXS</td><td>-</td><td>0.979**</td><td>-</td><td>0.052</td><td>-</td><td>1.000**</td><td>-</td><td>0.009</td><td>-</td><td>0.007</td><td>-</td><td>0.009</td><td>-</td><td>0.009</td><td>-</td></tr><tr><td>ETN</td><td>-</td><td>0.942**</td><td>-</td><td>0.034</td><td>-</td><td>1.000**</td><td>-</td><td>0.034</td><td>-</td><td>0.014</td><td>-</td><td>0.010</td><td>-</td><td>0.014</td><td>-</td></tr><tr><td>DE</td><td>-</td><td>0.688**</td><td>-</td><td>0.000</td><td>-</td><td>1.000**</td><td>-</td><td>0.000</td><td>-</td><td>0.000</td><td>-</td><td>0.000</td><td>-</td><td>0.000</td><td>-</td></tr><tr><td>ANF</td><td>-</td><td>1.000**</td><td>-</td><td>0.008</td><td>-</td><td>0.100</td><td>-</td><td>0.008</td><td>-</td><td>0.008</td><td>-</td><td>0.002</td><td>-</td><td>0.008</td><td>-</td></tr><tr><td>BEN</td><td>-</td><td>1.000**</td><td>-</td><td>0.044</td><td>-</td><td>0.177*</td><td>-</td><td>0.044</td><td>-</td><td>0.043</td><td>-</td><td>0.043</td><td>-</td><td>0.043</td><td>-</td></tr><tr><td>PEG</td><td>-</td><td>1.000**</td><td>-</td><td>0.100</td><td>-</td><td>0.940**</td><td>-</td><td>0.100</td><td>-</td><td>0.100</td><td>-</td><td>0.027</td><td>-</td><td>0.027</td><td>-</td></tr><tr><td>YUM</td><td>-</td><td>0.752**</td><td>-</td><td>0.016</td><td>-</td><td>1.000**</td><td>-</td><td>0.016</td><td>-</td><td>0.004</td><td>-</td><td>0.004</td><td>-</td><td>0.001</td><td>-</td></tr><tr><td>MTB</td><td>-</td><td>1.000**</td><td>-</td><td>0.029</td><td>-</td><td>0.278**</td><td>-</td><td>0.029</td><td>-</td><td>0.029</td><td>-</td><td>0.006</td><td>-</td><td>0.006</td><td>-</td></tr><tr><td>ORLY</td><td>-</td><td>0.384**</td><td>-</td><td>0.047</td><td>-</td><td>1.000**</td><td>-</td><td>0.047</td><td>-</td><td>0.000</td><td>-</td><td>-</td><td>-</td><td>0.047</td><td>-</td></tr><tr><td>PSA</td><td>-</td><td>1.000**</td><td>-</td><td>0.196*</td><td>-</td><td>0.351**</td><td>-</td><td>0.020</td><td>-</td><td>0.020</td><td>-</td><td>0.009</td><td>-</td><td>0.013</td><td>-</td></tr><tr><td>GPC</td><td>-</td><td>1.000**</td><td>-</td><td>0.904**</td><td>-</td><td>0.904**</td><td>-</td><td>0.887**</td><td>-</td><td>0.009</td><td>-</td><td>0.007</td><td>-</td><td>0.007</td><td>-</td></tr><tr><td>AVY</td><td>-</td><td>0.652**</td><td>-</td><td>0.041</td><td>-</td><td>1.000**</td><td>-</td><td>0.037</td><td>-</td><td>0.037</td><td>-</td><td>0.037</td><td>-</td><td>0.037</td><td>-</td></tr><tr><td>VAR</td><td>-</td><td>1.000**</td><td>-</td><td>0.066</td><td>-</td><td>0.318**</td><td>-</td><td>0.066</td><td>-</td><td>0.066</td><td>-</td><td>0.066</td><td>-</td><td>0.002</td><td>-</td></tr><tr><td>AVB</td><td>-</td><td>1.000**</td><td>-</td><td>0.109*</td><td>-</td><td>0.444**</td><td>-</td><td>0.109*</td><td>-</td><td>0.109*</td><td>-</td><td>0.109*</td><td>-</td><td>0.109*</td><td>-</td></tr><tr><td>SHW</td><td>-</td><td>0.807**</td><td>-</td><td>0.041</td><td>-</td><td>1.000**</td><td>-</td><td>0.025</td><td>-</td><td>0.003</td><td>-</td><td>0.002</td><td>-</td><td>0.003</td><td>-</td></tr><tr><td>LH</td><td>-</td><td>1.000**</td><td>-</td><td>0.144*</td><td>-</td><td>0.592**</td><td>-</td><td>0.018</td><td>-</td><td>0.012</td><td>-</td><td>0.018</td><td>-</td><td>0.018</td><td>-</td></tr><tr><td>NBR</td><td>-</td><td>0.943**</td><td>-</td><td>0.242*</td><td>-</td><td>1.000**</td><td>-</td><td>0.943**</td><td>-</td><td>0.000</td><td>-</td><td>-</td><td>-</td><td>0.000</td><td>-</td></tr></table>


Note: This table reports the p-values from the Model Confidence Set (MCS), using the RMSE loss function. The MCS is constructed at the $9 0 \%$ confidence level $( \alpha = 0 . 1 0 )$ . Models with p-values greater than 0.10 remain in the final model confidence set, while models with p-values below $0 . 1 0$ are eliminated. One (two) asterisk(s) indicate inclusion in the 90% (75%) model confidence set. A dash $\cdot _ { - } ,$ indicates a p-value of zero. 



Table C.15: Out-of-sample RMAE across forecasting models


<table><tr><td>Ticker</td><td>KF</td><td><eq>\text{SPAR}_1</eq></td><td><eq>\text{OLS}_1</eq></td><td><eq>\text{SPAR}_2</eq></td><td><eq>\text{OLS}_2</eq></td><td><eq>\text{SPAR}_3</eq></td><td><eq>\text{OLS}_3</eq></td><td><eq>\text{SPAR}_4</eq></td><td><eq>\text{OLS}_4</eq></td><td><eq>\text{LAS}_\text{SP}</eq></td><td>Lasso</td><td><eq>\text{RI}_{\text{SP}}</eq></td><td>Ridge</td><td><eq>\text{RF}_{\text{SP}}</eq></td><td>RF</td></tr><tr><td>BAC</td><td>0.353</td><td>0.337</td><td>0.373</td><td>0.341</td><td>0.374</td><td>0.336</td><td>0.369</td><td>0.341</td><td>0.368</td><td>0.344</td><td>0.372</td><td>0.345</td><td>0.379</td><td>0.342</td><td>0.358</td></tr><tr><td>SPY</td><td>0.314</td><td>0.307</td><td>0.357</td><td>0.311</td><td>0.350</td><td>0.306</td><td>0.358</td><td>0.310</td><td>0.350</td><td>0.309</td><td>0.349</td><td>0.308</td><td>0.353</td><td>0.310</td><td>0.327</td></tr><tr><td>AAPL</td><td>0.282</td><td>0.275</td><td>0.321</td><td>0.275</td><td>0.323</td><td>0.275</td><td>0.317</td><td>0.274</td><td>0.315</td><td>0.281</td><td>0.319</td><td>0.281</td><td>0.328</td><td>0.280</td><td>0.298</td></tr><tr><td>GE</td><td>0.357</td><td>0.356</td><td>0.405</td><td>0.359</td><td>0.397</td><td>0.356</td><td>0.399</td><td>0.360</td><td>0.388</td><td>0.362</td><td>0.396</td><td>0.366</td><td>0.404</td><td>0.363</td><td>0.381</td></tr><tr><td>MSFT</td><td>0.317</td><td>0.306</td><td>0.369</td><td>0.308</td><td>0.355</td><td>0.306</td><td>0.365</td><td>0.309</td><td>0.347</td><td>0.310</td><td>0.352</td><td>0.309</td><td>0.359</td><td>0.312</td><td>0.323</td></tr><tr><td>CSCO</td><td>0.346</td><td>0.341</td><td>0.405</td><td>0.342</td><td>0.393</td><td>0.340</td><td>0.397</td><td>0.342</td><td>0.385</td><td>0.347</td><td>0.389</td><td>0.351</td><td>0.387</td><td>0.345</td><td>0.362</td></tr><tr><td>INTC</td><td>0.333</td><td>0.331</td><td>0.392</td><td>0.331</td><td>0.383</td><td>0.330</td><td>0.384</td><td>0.332</td><td>0.370</td><td>0.336</td><td>0.377</td><td>0.339</td><td>0.382</td><td>0.335</td><td>0.353</td></tr><tr><td>AMD</td><td>0.480</td><td>0.472</td><td>0.509</td><td>0.474</td><td>0.510</td><td>0.470</td><td>0.503</td><td>0.475</td><td>0.499</td><td>0.484</td><td>0.509</td><td>0.486</td><td>0.515</td><td>0.480</td><td>0.499</td></tr><tr><td>PFE</td><td>0.336</td><td>0.336</td><td>0.393</td><td>0.340</td><td>0.374</td><td>0.335</td><td>0.387</td><td>0.341</td><td>0.371</td><td>0.342</td><td>0.380</td><td>0.347</td><td>0.381</td><td>0.343</td><td>0.357</td></tr><tr><td>T</td><td>0.321</td><td>0.321</td><td>0.375</td><td>0.325</td><td>0.368</td><td>0.322</td><td>0.368</td><td>0.324</td><td>0.360</td><td>0.328</td><td>0.365</td><td>0.330</td><td>0.374</td><td>0.328</td><td>0.350</td></tr><tr><td>KBH</td><td>0.439</td><td>0.428</td><td>0.483</td><td>0.434</td><td>0.473</td><td>0.427</td><td>0.478</td><td>0.432</td><td>0.464</td><td>0.439</td><td>0.471</td><td>0.443</td><td>0.481</td><td>0.436</td><td>0.453</td></tr><tr><td>ROST</td><td>0.372</td><td>0.364</td><td>0.430</td><td>0.368</td><td>0.410</td><td>0.365</td><td>0.421</td><td>0.368</td><td>0.398</td><td>0.371</td><td>0.407</td><td>0.371</td><td>0.412</td><td>0.372</td><td>0.388</td></tr><tr><td>SWKS</td><td>0.371</td><td>0.365</td><td>0.413</td><td>0.365</td><td>0.416</td><td>0.364</td><td>0.403</td><td>0.364</td><td>0.403</td><td>0.375</td><td>0.412</td><td>0.374</td><td>0.417</td><td>0.370</td><td>0.390</td></tr><tr><td>CTXS</td><td>0.390</td><td>0.379</td><td>0.447</td><td>0.383</td><td>0.437</td><td>0.378</td><td>0.438</td><td>0.384</td><td>0.429</td><td>0.390</td><td>0.438</td><td>0.392</td><td>0.439</td><td>0.387</td><td>0.411</td></tr><tr><td>ETN</td><td>0.362</td><td>0.354</td><td>0.416</td><td>0.358</td><td>0.398</td><td>0.353</td><td>0.409</td><td>0.358</td><td>0.392</td><td>0.362</td><td>0.397</td><td>0.363</td><td>0.400</td><td>0.361</td><td>0.379</td></tr><tr><td>DE</td><td>0.354</td><td>0.345</td><td>0.400</td><td>0.350</td><td>0.387</td><td>0.344</td><td>0.394</td><td>0.351</td><td>0.378</td><td>0.352</td><td>0.386</td><td>0.354</td><td>0.389</td><td>0.352</td><td>0.368</td></tr><tr><td>ANF</td><td>0.406</td><td>0.396</td><td>0.457</td><td>0.401</td><td>0.459</td><td>0.395</td><td>0.450</td><td>0.400</td><td>0.444</td><td>0.405</td><td>0.453</td><td>0.405</td><td>0.459</td><td>0.403</td><td>0.426</td></tr><tr><td>BEN</td><td>0.398</td><td>0.387</td><td>0.465</td><td>0.391</td><td>0.435</td><td>0.387</td><td>0.459</td><td>0.391</td><td>0.427</td><td>0.395</td><td>0.435</td><td>0.397</td><td>0.437</td><td>0.394</td><td>0.411</td></tr><tr><td>PEG</td><td>0.382</td><td>0.375</td><td>0.455</td><td>0.379</td><td>0.418</td><td>0.374</td><td>0.448</td><td>0.378</td><td>0.415</td><td>0.379</td><td>0.420</td><td>0.382</td><td>0.425</td><td>0.380</td><td>0.392</td></tr><tr><td>YUM</td><td>0.355</td><td>0.347</td><td>0.416</td><td>0.352</td><td>0.396</td><td>0.346</td><td>0.407</td><td>0.351</td><td>0.388</td><td>0.353</td><td>0.397</td><td>0.353</td><td>0.404</td><td>0.357</td><td>0.374</td></tr><tr><td>MTB</td><td>0.426</td><td>0.409</td><td>0.494</td><td>0.415</td><td>0.458</td><td>0.409</td><td>0.486</td><td>0.415</td><td>0.453</td><td>0.418</td><td>0.461</td><td>0.422</td><td>0.460</td><td>0.418</td><td>0.434</td></tr><tr><td>ORLY</td><td>0.418</td><td>0.412</td><td>0.472</td><td>0.417</td><td>0.458</td><td>0.411</td><td>0.463</td><td>0.417</td><td>0.450</td><td>0.422</td><td>0.454</td><td>0.426</td><td>0.455</td><td>0.418</td><td>0.432</td></tr><tr><td>PSA</td><td>0.428</td><td>0.416</td><td>0.512</td><td>0.419</td><td>0.462</td><td>0.416</td><td>0.506</td><td>0.420</td><td>0.457</td><td>0.422</td><td>0.462</td><td>0.425</td><td>0.465</td><td>0.420</td><td>0.434</td></tr><tr><td>GPC</td><td>0.408</td><td>0.399</td><td>0.487</td><td>0.402</td><td>0.450</td><td>0.399</td><td>0.476</td><td>0.402</td><td>0.443</td><td>0.410</td><td>0.452</td><td>0.411</td><td>0.455</td><td>0.407</td><td>0.420</td></tr><tr><td>AVY</td><td>0.418</td><td>0.408</td><td>0.501</td><td>0.412</td><td>0.457</td><td>0.406</td><td>0.490</td><td>0.414</td><td>0.450</td><td>0.416</td><td>0.455</td><td>0.417</td><td>0.463</td><td>0.414</td><td>0.432</td></tr><tr><td>VAR</td><td>0.420</td><td>0.405</td><td>0.485</td><td>0.412</td><td>0.451</td><td>0.404</td><td>0.477</td><td>0.412</td><td>0.448</td><td>0.411</td><td>0.453</td><td>0.410</td><td>0.456</td><td>0.410</td><td>0.429</td></tr><tr><td>AVB</td><td>0.431</td><td>0.418</td><td>0.516</td><td>0.422</td><td>0.464</td><td>0.418</td><td>0.509</td><td>0.422</td><td>0.458</td><td>0.426</td><td>0.463</td><td>0.425</td><td>0.468</td><td>0.423</td><td>0.438</td></tr><tr><td>SHW</td><td>0.438</td><td>0.430</td><td>0.497</td><td>0.435</td><td>0.477</td><td>0.430</td><td>0.492</td><td>0.436</td><td>0.474</td><td>0.439</td><td>0.479</td><td>0.441</td><td>0.479</td><td>0.437</td><td>0.457</td></tr><tr><td>LH</td><td>0.440</td><td>0.428</td><td>0.497</td><td>0.432</td><td>0.473</td><td>0.427</td><td>0.490</td><td>0.434</td><td>0.462</td><td>0.437</td><td>0.473</td><td>0.439</td><td>0.476</td><td>0.434</td><td>0.450</td></tr><tr><td>NBR</td><td>0.402</td><td>0.397</td><td>0.443</td><td>0.399</td><td>0.432</td><td>0.397</td><td>0.438</td><td>0.398</td><td>0.423</td><td>0.405</td><td>0.429</td><td>0.407</td><td>0.432</td><td>0.403</td><td>0.414</td></tr></table>


Note: This table reports the relative mean absolute error (RMAE) of the out-of-sample forecasts for each forecasting model and each asset. Lower values indicate smaller prediction errors and therefore better forecasting performance. For each asset, the model with the lowest RMAE is highlighted in bold. 



Table C.16: Model Confidence Set p-values based on RMAE


<table><tr><td>Ticker</td><td>KF</td><td><eq>\text{SPAR}_1</eq></td><td><eq>\text{OLS}_1</eq></td><td><eq>\text{SPAR}_2</eq></td><td><eq>\text{OLS}_2</eq></td><td><eq>\text{SPAR}_3</eq></td><td><eq>\text{OLS}_3</eq></td><td><eq>\text{SPAR}_4</eq></td><td><eq>\text{OLS}_4</eq></td><td><eq>\text{LA}_{\text{SP}}</eq></td><td>Lasso</td><td><eq>\text{RI}_{\text{SP}}</eq></td><td>Ridge</td><td><eq>\text{RF}_{\text{SP}}</eq></td><td>RF</td></tr><tr><td>BAC</td><td>0.474**</td><td>0.474**</td><td>-</td><td>0.474**</td><td>-</td><td>1.000**</td><td>-</td><td>0.474**</td><td>-</td><td>0.474**</td><td>-</td><td>0.442**</td><td>-</td><td>0.474**</td><td>-</td></tr><tr><td>SPY</td><td>-</td><td>0.110*</td><td>-</td><td>0.052</td><td>-</td><td>1.000**</td><td>-</td><td>0.052</td><td>-</td><td>0.052</td><td>-</td><td>0.052</td><td>-</td><td>0.052</td><td>-</td></tr><tr><td>AAPL</td><td>0.016</td><td>0.706**</td><td>-</td><td>0.319**</td><td>-</td><td>0.706**</td><td>-</td><td>1.000**</td><td>-</td><td>0.017</td><td>-</td><td>0.019</td><td>-</td><td>0.019</td><td>-</td></tr><tr><td>GE</td><td>0.553**</td><td>0.553**</td><td>-</td><td>0.092</td><td>-</td><td>1.000**</td><td>-</td><td>0.092</td><td>-</td><td>0.092</td><td>-</td><td>0.010</td><td>-</td><td>0.033</td><td>-</td></tr><tr><td>MSFT</td><td>0.487**</td><td>0.674**</td><td>-</td><td>0.487**</td><td>-</td><td>1.000**</td><td>-</td><td>0.487**</td><td>-</td><td>0.487**</td><td>-</td><td>0.487**</td><td>-</td><td>0.270**</td><td>-</td></tr><tr><td>CSCO</td><td>0.570**</td><td>0.714**</td><td>-</td><td>0.570**</td><td>-</td><td>1.000**</td><td>-</td><td>0.570**</td><td>-</td><td>0.033</td><td>-</td><td>0.033</td><td>-</td><td>0.153*</td><td>-</td></tr><tr><td>INTC</td><td>0.072</td><td>0.638**</td><td>-</td><td>0.638**</td><td>-</td><td>1.000**</td><td>-</td><td>0.326**</td><td>-</td><td>0.018</td><td>-</td><td>0.008</td><td>-</td><td>0.018</td><td>-</td></tr><tr><td>AMD</td><td>0.005</td><td>0.156*</td><td>-</td><td>0.010</td><td>-</td><td>1.000**</td><td>-</td><td>0.005</td><td>-</td><td>0.005</td><td>-</td><td>0.005</td><td>-</td><td>0.005</td><td>0.005</td></tr><tr><td>PFE</td><td>0.882**</td><td>0.882**</td><td>-</td><td>0.004</td><td>-</td><td>1.000**</td><td>-</td><td>0.004</td><td>-</td><td>0.004</td><td>-</td><td>0.002</td><td>-</td><td>0.002</td><td>0.000</td></tr><tr><td>T</td><td>0.833**</td><td>1.000**</td><td>-</td><td>0.020</td><td>-</td><td>0.631**</td><td>-</td><td>0.020</td><td>-</td><td>0.020</td><td>-</td><td>0.020</td><td>-</td><td>0.020</td><td>-</td></tr><tr><td>KBH</td><td>0.017</td><td>0.097</td><td>-</td><td>0.017</td><td>-</td><td>1.000**</td><td>-</td><td>0.017</td><td>-</td><td>0.017</td><td>-</td><td>0.017</td><td>-</td><td>0.017</td><td>-</td></tr><tr><td>ROST</td><td>0.013</td><td>1.000**</td><td>-</td><td>0.013</td><td>-</td><td>0.213*</td><td>-</td><td>0.013</td><td>-</td><td>0.013</td><td>-</td><td>0.013</td><td>-</td><td>0.003</td><td>-</td></tr><tr><td>SWKS</td><td>0.001</td><td>0.890**</td><td>-</td><td>0.890**</td><td>-</td><td>1.000**</td><td>-</td><td>0.911**</td><td>-</td><td>0.000</td><td>-</td><td>0.005</td><td>-</td><td>0.005</td><td>-</td></tr><tr><td>CTXS</td><td>-</td><td>0.128*</td><td>-</td><td>0.010</td><td>-</td><td>1.000**</td><td>-</td><td>0.010</td><td>-</td><td>-</td><td>-</td><td>0.010</td><td>-</td><td>0.010</td><td>-</td></tr><tr><td>ETN</td><td>0.077</td><td>0.077</td><td>-</td><td>0.077</td><td>-</td><td>1.000**</td><td>-</td><td>0.077</td><td>-</td><td>0.077</td><td>-</td><td>0.077</td><td>-</td><td>0.077</td><td>-</td></tr><tr><td>DE</td><td>-</td><td>0.359**</td><td>-</td><td>0.001</td><td>-</td><td>1.000**</td><td>-</td><td>0.001</td><td>-</td><td>0.001</td><td>-</td><td>0.001</td><td>-</td><td>0.001</td><td>-</td></tr><tr><td>ANF</td><td>0.000</td><td>0.525**</td><td>-</td><td>0.000</td><td>-</td><td>1.000**</td><td>-</td><td>0.000</td><td>-</td><td>0.000</td><td>-</td><td>0.000</td><td>-</td><td>0.000</td><td>-</td></tr><tr><td>BEN</td><td>-</td><td>1.000**</td><td>-</td><td>0.049</td><td>-</td><td>0.945**</td><td>-</td><td>0.049</td><td>-</td><td>0.049</td><td>-</td><td>0.021</td><td>-</td><td>0.049</td><td>-</td></tr><tr><td>PEG</td><td>0.002</td><td>0.159*</td><td>-</td><td>0.061</td><td>-</td><td>1.000**</td><td>-</td><td>0.061</td><td>-</td><td>0.061</td><td>-</td><td>0.045</td><td>-</td><td>0.045</td><td>-</td></tr><tr><td>YUM</td><td>0.000</td><td>0.050</td><td>-</td><td>0.028</td><td>-</td><td>1.000**</td><td>-</td><td>0.028</td><td>-</td><td>0.028</td><td>-</td><td>0.028</td><td>-</td><td>0.000</td><td>-</td></tr><tr><td>MTB</td><td>0.001</td><td>1.000**</td><td>-</td><td>0.032</td><td>-</td><td>0.290**</td><td>-</td><td>0.032</td><td>-</td><td>0.032</td><td>-</td><td>0.032</td><td>-</td><td>0.032</td><td>-</td></tr><tr><td>ORLY</td><td>0.065</td><td>0.224*</td><td>-</td><td>0.065</td><td>-</td><td>1.000**</td><td>-</td><td>0.065</td><td>-</td><td>0.000</td><td>-</td><td>0.000</td><td>-</td><td>0.065</td><td>-</td></tr><tr><td>PSA</td><td>-</td><td>1.000**</td><td>-</td><td>0.061</td><td>-</td><td>0.865**</td><td>-</td><td>0.061</td><td>-</td><td>0.061</td><td>-</td><td>0.013</td><td>-</td><td>0.061</td><td>-</td></tr><tr><td>GPC</td><td>0.022</td><td>1.000**</td><td>-</td><td>0.119*</td><td>-</td><td>0.972**</td><td>-</td><td>0.119*</td><td>-</td><td>0.022</td><td>-</td><td>0.022</td><td>-</td><td>0.022</td><td>-</td></tr><tr><td>AVY</td><td>0.008</td><td>0.048</td><td>-</td><td>0.031</td><td>-</td><td>1.000**</td><td>-</td><td>0.031</td><td>0.000</td><td>0.031</td><td>-</td><td>0.027</td><td>-</td><td>0.031</td><td>0.000</td></tr><tr><td>VAR</td><td>-</td><td>0.403**</td><td>-</td><td>0.054</td><td>-</td><td>1.000**</td><td>-</td><td>0.054</td><td>-</td><td>0.054</td><td>-</td><td>0.054</td><td>-</td><td>0.054</td><td>-</td></tr><tr><td>AVB</td><td>-</td><td>0.854**</td><td>-</td><td>0.016</td><td>-</td><td>1.000**</td><td>-</td><td>0.016</td><td>-</td><td>0.016</td><td>-</td><td>0.016</td><td>-</td><td>0.016</td><td>-</td></tr><tr><td>SHW</td><td>0.023</td><td>0.618**</td><td>-</td><td>0.023</td><td>-</td><td>1.000**</td><td>-</td><td>0.023</td><td>-</td><td>0.023</td><td>-</td><td>0.010</td><td>-</td><td>0.023</td><td>-</td></tr><tr><td>LH</td><td>-</td><td>0.317**</td><td>-</td><td>0.016</td><td>-</td><td>1.000**</td><td>-</td><td>0.016</td><td>-</td><td>0.003</td><td>-</td><td>0.016</td><td>-</td><td>0.016</td><td>-</td></tr><tr><td>NBR</td><td>0.002</td><td>1.000**</td><td>-</td><td>0.046</td><td>-</td><td>0.891**</td><td>-</td><td>0.340**</td><td>-</td><td>0.002</td><td>-</td><td>0.001</td><td>-</td><td>0.001</td><td>-</td></tr></table>


Note: This table reports the p-values from the Model Confidence Set (MCS), using the RMAE loss function. One (two) asterisk(s) indicate inclusion in the 90% (75%) model confidence set. A dash ‘-’ indicates a p-value of zero. 


Figure C.8 shows the fitted intraday trading volume curves using diferent lengths of training days, W, averaged from the 91st day to the 2466th day. The figure shows that the estimation of f is insensitive to the number of training days. The examples we chose include high (Figure C.8a), medium high (Figure C.8b), medium (Figure C.8c), and low (Figure C.8d) trading volumes. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/5649cbacfd652c0eb76ab61ec2ac6a65d285ae8a5f8e957054cf061e352fa61d.jpg)



(a) AAPL.


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/ee39477df5b86832dd68bdce14bbe0ac78aaf06bbff2fc7d7a2561d0a5c53440.jpg)



(b) T.


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/2adc01505b1949d142a66a7e6cf8f6386693803de9c0cda1a927f0bf0e0494e9.jpg)



(c) ANF.


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/6edacaddd4ac7b349e1251deaae1840d5c1ea96d7820af311da9d77c4b81d056.jpg)



(d) PSA.


Figure C.8: Intraday trading volume curves fitted using diferent lengths of training days W. Results are averaged from the 91st day to the 2466th day. The y-axis represents normalized trading volume, with a mean of 1. In the legend, ’Volume’ refers to the trading volume curve, ’Model-select’ indicates that the number of training days is not fixed but is automatically selected by the model according to (B.1), while the rest indicate a fixed number of training days, W<sub>s</sub>. 

## Appendix D. An Extension with Session-Specific Coeficients

The baseline specification in Equations (4), (5) and (7) assumes that all intraday intervals share the same coeficient vector $\beta .$ . This assumption may be restrictive because the information available for forecasting changes throughout the trading day. Forecasts near the market open rely mainly on information from the previous trading day, whereas forecasts during the middle and closing sessions use more current-day intraday information. 

To examine whether this diference requires separate forecasting functions, we divide each trading day into three sessions: the opening session (the first 30 minutes), the closing session (the last 30 minutes), and the middle session (the remaining intervals). We then estimate a separate coeficient vector for each session. All other settings, including the predictors, within-transformation, model-update schedule, estimation method, and forecast evaluation, are the same as in the baseline analysis. 

The only diference concerns the candidate training windows. After the trading day is divided into separate sessions, each regression uses fewer intraday observations. In particular, when $W = 5$ , the opening and closing regressions contain only 30 within-session observations before accounting for the lag structure, which is too small for specifications with many predictors. We therefore use $W = \{ 2 2 , 4 4 , 6 6 \}$ 


Table D.17: Out-of-sample results with session-specific coeficients


<table><tr><td></td><td>Level</td><td><eq>\text{SPAR}_1</eq></td><td><eq>\text{OLS}_1</eq></td><td><eq>\text{SPAR}_2</eq></td><td><eq>\text{OLS}_2</eq></td><td><eq>\text{SPAR}_3</eq></td><td><eq>\text{OLS}_3</eq></td><td><eq>\text{SPAR}_4</eq></td><td><eq>\text{OLS}_4</eq></td></tr><tr><td rowspan="4"><eq>R^2</eq></td><td>Top.</td><td>0.295</td><td>0.182</td><td>0.232</td><td>0.178</td><td>0.294</td><td>0.201</td><td>0.246</td><td>0.233</td></tr><tr><td>Mid.</td><td>0.327</td><td>0.263</td><td>0.296</td><td>0.279</td><td>0.324</td><td>0.265</td><td>0.290</td><td>0.275</td></tr><tr><td>Bot.</td><td>0.268</td><td>0.191</td><td>0.234</td><td>0.222</td><td>0.267</td><td>0.193</td><td>0.233</td><td>0.220</td></tr><tr><td>Avg.</td><td>0.297</td><td>0.212</td><td>0.254</td><td>0.227</td><td>0.295</td><td>0.220</td><td>0.256</td><td>0.242</td></tr><tr><td rowspan="4">RMSE</td><td>Top.</td><td>0.471</td><td>0.575</td><td>0.518</td><td>0.563</td><td>0.476</td><td>0.571</td><td>0.514</td><td>0.518</td></tr><tr><td>Mid.</td><td>0.507</td><td>0.590</td><td>0.531</td><td>0.545</td><td>0.511</td><td>0.585</td><td>0.538</td><td>0.546</td></tr><tr><td>Bot.</td><td>0.609</td><td>0.721</td><td>0.642</td><td>0.651</td><td>0.613</td><td>0.718</td><td>0.644</td><td>0.656</td></tr><tr><td>Avg.</td><td>0.529</td><td>0.629</td><td>0.564</td><td>0.586</td><td>0.533</td><td>0.625</td><td>0.565</td><td>0.574</td></tr><tr><td rowspan="4">RMAE</td><td>Top.</td><td>0.337</td><td>0.363</td><td>0.348</td><td>0.351</td><td>0.337</td><td>0.359</td><td>0.348</td><td>0.349</td></tr><tr><td>Mid.</td><td>0.373</td><td>0.391</td><td>0.384</td><td>0.385</td><td>0.374</td><td>0.391</td><td>0.385</td><td>0.385</td></tr><tr><td>Bot.</td><td>0.411</td><td>0.433</td><td>0.423</td><td>0.422</td><td>0.412</td><td>0.433</td><td>0.424</td><td>0.423</td></tr><tr><td>Avg.</td><td>0.374</td><td>0.396</td><td>0.385</td><td>0.386</td><td>0.375</td><td>0.394</td><td>0.386</td><td>0.386</td></tr></table>


Note: This table reports the out-of-sample forecasting performance of models that estimate separate coeficient vectors for the opening, middle, and closing sessions. Boldfaced entries denote the best-performing specification for each metric. 


Table D.17 reports the out-of-sample results of the session-specific specifications. The results are compared with the baseline findings in Tables 3 and 4. For $\mathrm { S P A R _ { 1 } }$ and $\mathrm { S P A R _ { 3 } }$ the average $R ^ { 2 } .$ , RMSE, and RMAE remain close to the baseline results. By contrast, allowing separate session coeficients does not improve $\mathrm { S P A R _ { 2 } }$ or $\mathrm { S P A R _ { 4 } }$ . Thus, the weaker performance of the specifications containing cross-day predictors cannot be explained by the common-coeficient restriction. More generally, the results do not provide clear evidence that the preferred SPAR specifications require separate forecasting functions across the trading day. 

The OLS models, especially $\mathrm { O L S _ { 1 } }$ and $\mathrm { O L S _ { 3 } }$ , improve more noticeably when separate regressions are estimated for each session. This suggests that the relationship between the predictors and trading volume varies over the trading day. Nevertheless, the session-specific OLS models remain less accurate than the corresponding SPAR models. 

Figure D.9 reports the performance of the session-specific models within the three trading sessions. Forecasting remains more dificult during the opening session and generally improves later in the day. This pattern confirms that forecast performance difers across sessions, but allowing the SPAR coeficients to vary across sessions does not change the main empirical conclusions. We therefore retain the common-coeficient specification because it is simpler and performs similarly for $\mathrm { S P A R _ { 1 } }$ and $\mathrm { S P A R _ { 3 } }$ 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/eb49ab90c9a6e0b41b139a930d473d27a835d8823e2824f72c952c09fb3549ce.jpg)



Figure D.9: Forecasting performance under session-specific regressions. This figure reports the average $R ^ { 2 }$ across methods for three periods: the open session (the first 30 minutes after the market opens), the close session (the last 30 minutes before the market closes), and the middle session (the remaining trading time). Results are averaged across the 30 representative assets.


## Appendix E. Robustness Check in the Chinese A-Share Market

This appendix provides an external-market check using the Chinese A-share market. We use the constituent stocks of the Shanghai Stock Exchange 50 Index as the initial A-share sample. The sample period is from January 2, 2018, to April 25, 2022, covering 1,040 trading days. The intraday data are obtained from WIND. We apply the same filtering rules as in Section 2 and obtain 23 stocks. We then rank these stocks by average daily trading volume and classify them into Top, Middle, and Bottom groups. Table E.18 reports the selected tickers and their average daily trading volumes. 

The A-share market difers from the U.S. market in its trading schedule. In particular, it has a midday trading halt from 11:30 AM to 1:00 PM. This trading halt creates an intraday volume pattern diferent from the standard U-shape often observed in U.S. equities. Figure E.10 gives two examples from our A-share sample. SH600050 shows a clear W-shaped pattern, while SH601919 shows a volume concentrated near the open. These two examples show that the A-share market contains heterogeneous intraday volume curves. This setting is useful for evaluating SPAR because the model does not require the periodic component’s shape to be specified in advance. 

![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/e95ce0e506b9e24763e9454a91fccc63ebfd96fa55d341c82791767bb7673fb4.jpg)



(a) Zhongguoliantong (stock ticker: SH600050).


![image](https://cdn-mineru.openxlab.org.cn/result/2026-09-24/55652ac2-ae70-46f4-a5be-4462e3b37b0e/043375d4c1c161de0d99ac6b6b1c81636803367e6c53f2207a2090e7ea8ee07b.jpg)



(b) Zhongyuanhaikong (stock ticker: SH601919).



Figure E.10: Average intraday trading volume for the A-share market at a 5-min frequency. This figure shows the average intraday trading volume periodicity on the A-share market from January 2, 2018, to April 25, 2022. Panel E.10a shows the unique W-shaped pattern in the A-share market caused by the midday break, while Panel E.10b shows a front-loaded pattern with trading volume concentrated near the open. The y-axis represents normalized trading volume, with a mean of 1.



Table E.18: List of A-share tickers and average daily trading volume.


<table><tr><td>Ticker</td><td>Volume</td><td>Ticker</td><td>Volume</td><td>Ticker</td><td>Volume</td></tr><tr><td>SH601288</td><td>2506688</td><td>SH600031</td><td>987192.7</td><td>SH600104</td><td>352274.2</td></tr><tr><td>SH601398</td><td>2079973</td><td>SH601328</td><td>980368.2</td><td>SH601088</td><td>313363.6</td></tr><tr><td>SH601668</td><td>1861725</td><td>SH601919</td><td>957793.3</td><td>SH601601</td><td>306336.1</td></tr><tr><td>SH600028</td><td>1373522</td><td>SH601166</td><td>907920.2</td><td>SH600276</td><td>280642.7</td></tr><tr><td>SH601988</td><td>1316929</td><td>SH600111</td><td>868151.2</td><td>SH600406</td><td>213463.1</td></tr><tr><td>SH600050</td><td>1278232</td><td>SH601318</td><td>704848.6</td><td>SH600760</td><td>150152.8</td></tr><tr><td>SH601857</td><td>1061466</td><td>SH600036</td><td>586306.8</td><td>SH601888</td><td>118607.2</td></tr><tr><td></td><td></td><td>SH600887</td><td>582743.3</td><td>SH600519</td><td>40126.9</td></tr></table>


Note: This table reports the list of selected A-share asset tickers and their average daily trading volume from January 2, 2018, to April 25, 2022.


Table E.19 reports the forecasting results for the A-share sample. The main conclusion is similar to that in the U.S. market: removing the intraday periodic component improves forecasting performance. Among the SPAR specifications, $\mathrm { S P A R _ { 3 } }$ achieves the highest average out-of-sample $R ^ { 2 }$ , equal to 0.337, followed by $\mathrm { S P A R _ { 1 } }$ . These values are higher than the average $R ^ { 2 }$ of the KF benchmark and much higher than the corresponding OLS specifications. The relative performance against KF is positive on average for $\mathrm { S P A R _ { 1 } }$ and $\mathrm { S P A R _ { 3 } }$ . The improvement is greatest for the middle- and bottom-volume groups, while in the top-volume group the SPAR specifications are comparable to, but do not uniformly dominate, the KF benchmark. 

The error metrics give the same general message. $\mathrm { S P A R _ { 3 } }$ has the lowest average RMSE, equal to 0.438, and the lowest average RMAE, equal to 0.376. For comparison, the KF benchmark has average RMSE and RMAE values of 0.455 and 0.387, respectively. The OLS models remain less accurate, which confirms that directly forecasting volume with periodicity is dificult. 


Table E.19: Out-of-sample results of the Chinese A-share market


<table><tr><td></td><td>Level</td><td>KF</td><td><eq>\text{SPAR}_1</eq></td><td><eq>\text{OLS}_1</eq></td><td><eq>\text{SPAR}_2</eq></td><td><eq>\text{OLS}_2</eq></td><td><eq>\text{SPAR}_3</eq></td><td><eq>\text{OLS}_3</eq></td><td><eq>\text{SPAR}_4</eq></td><td><eq>\text{OLS}_4</eq></td><td><eq>\text{LA}_{\text{SP}}</eq></td><td>Lasso</td><td><eq>\text{RI}_{\text{SP}}</eq></td><td>Ridge</td><td><eq>\text{RF}_{\text{SP}}</eq></td><td>RF</td></tr><tr><td rowspan="4"><eq>R^2</eq></td><td>Top.</td><td>0.273</td><td>0.273</td><td>0.141</td><td>0.245</td><td>0.199</td><td>0.271</td><td>0.137</td><td>0.245</td><td>0.201</td><td>0.223</td><td>0.159</td><td>0.212</td><td>0.145</td><td>0.244</td><td>0.139</td></tr><tr><td>Mid.</td><td>0.325</td><td>0.361</td><td>0.164</td><td>0.340</td><td>0.225</td><td>0.367</td><td>0.181</td><td>0.346</td><td>0.259</td><td>0.325</td><td>0.203</td><td>0.330</td><td>0.204</td><td>0.323</td><td>0.214</td></tr><tr><td>Bot.</td><td>0.331</td><td>0.343</td><td>0.195</td><td>0.318</td><td>0.248</td><td>0.365</td><td>0.193</td><td>0.331</td><td>0.270</td><td>0.299</td><td>0.222</td><td>0.306</td><td>0.215</td><td>0.302</td><td>0.197</td></tr><tr><td>Avg.</td><td>0.311</td><td>0.328</td><td>0.168</td><td>0.303</td><td>0.225</td><td>0.337</td><td>0.172</td><td>0.310</td><td>0.245</td><td>0.285</td><td>0.196</td><td>0.286</td><td>0.190</td><td>0.292</td><td>0.185</td></tr><tr><td rowspan="4"><eq>R_{\text{KF}}^2</eq></td><td>Top.</td><td>/</td><td>-0.027</td><td>-0.212</td><td>-0.069</td><td>-0.136</td><td>-0.031</td><td>-0.213</td><td>-0.069</td><td>-0.134</td><td>-0.097</td><td>-0.196</td><td>-0.119</td><td>-0.213</td><td>-0.064</td><td>-0.219</td></tr><tr><td>Mid.</td><td>/</td><td>0.026</td><td>-0.273</td><td>-0.002</td><td>-0.176</td><td>0.027</td><td>-0.251</td><td>0.001</td><td>-0.126</td><td>-0.024</td><td>-0.198</td><td>-0.027</td><td>-0.205</td><td>-0.057</td><td>-0.217</td></tr><tr><td>Bot.</td><td>/</td><td>-0.001</td><td>-0.227</td><td>-0.048</td><td>-0.145</td><td>0.029</td><td>-0.220</td><td>-0.031</td><td>-0.109</td><td>-0.066</td><td>-0.178</td><td>-0.061</td><td>-0.195</td><td>-0.062</td><td>-0.217</td></tr><tr><td>Avg.</td><td>/</td><td>0.001</td><td>-0.239</td><td>-0.038</td><td>-0.153</td><td>0.010</td><td>-0.229</td><td>-0.032</td><td>-0.122</td><td>-0.061</td><td>-0.190</td><td>-0.067</td><td>-0.204</td><td>-0.048</td><td>-0.200</td></tr><tr><td rowspan="4">RMSE</td><td>Top.</td><td>0.634</td><td>0.628</td><td>0.712</td><td>0.648</td><td>0.668</td><td>0.628</td><td>0.707</td><td>0.642</td><td>0.661</td><td>0.637</td><td>0.679</td><td>0.642</td><td>0.683</td><td>0.636</td><td>0.666</td></tr><tr><td>Mid.</td><td>0.410</td><td>0.381</td><td>0.461</td><td>0.391</td><td>0.428</td><td>0.381</td><td>0.451</td><td>0.391</td><td>0.412</td><td>0.388</td><td>0.428</td><td>0.390</td><td>0.431</td><td>0.391</td><td>0.417</td></tr><tr><td>Bot.</td><td>0.344</td><td>0.336</td><td>0.399</td><td>0.348</td><td>0.372</td><td>0.330</td><td>0.391</td><td>0.344</td><td>0.356</td><td>0.341</td><td>0.371</td><td>0.342</td><td>0.378</td><td>0.342</td><td>0.366</td></tr><tr><td>Avg.</td><td>0.455</td><td>0.440</td><td>0.516</td><td>0.454</td><td>0.482</td><td>0.438</td><td>0.508</td><td>0.451</td><td>0.468</td><td>0.448</td><td>0.485</td><td>0.450</td><td>0.489</td><td>0.449</td><td>0.475</td></tr><tr><td rowspan="4">RMAE</td><td>Top.</td><td>0.456</td><td>0.452</td><td>0.477</td><td>0.463</td><td>0.470</td><td>0.451</td><td>0.475</td><td>0.459</td><td>0.466</td><td>0.461</td><td>0.471</td><td>0.462</td><td>0.475</td><td>0.458</td><td>0.473</td></tr><tr><td>Mid.</td><td>0.364</td><td>0.353</td><td>0.378</td><td>0.361</td><td>0.378</td><td>0.352</td><td>0.376</td><td>0.359</td><td>0.372</td><td>0.359</td><td>0.375</td><td>0.359</td><td>0.381</td><td>0.361</td><td>0.375</td></tr><tr><td>Bot.</td><td>0.347</td><td>0.335</td><td>0.358</td><td>0.342</td><td>0.359</td><td>0.334</td><td>0.355</td><td>0.341</td><td>0.352</td><td>0.341</td><td>0.355</td><td>0.342</td><td>0.364</td><td>0.343</td><td>0.358</td></tr><tr><td>Avg.</td><td>0.387</td><td>0.377</td><td>0.401</td><td>0.385</td><td>0.399</td><td>0.376</td><td>0.399</td><td>0.383</td><td>0.393</td><td>0.384</td><td>0.397</td><td>0.384</td><td>0.404</td><td>0.385</td><td>0.399</td></tr></table>


Note: Out-of-Sample Performance Comparison in the A-Share Market. This table reports the out-of-sample R<sup>2</sup>, $\mathrm { R } _ { \mathrm { K F } } ^ { 2 } ,$ , RMSE, and RMAE for various forecasting models using SSE 50 constituent stocks. $\mathrm { L A } _ { \mathrm { S P } }$ $\mathrm { R I } _ { \mathrm { S P } } .$ and $\mathrm { R F } _ { \mathrm { S P } }$ all use intraday variables and volatility variables, whereas their counterparts use the full feature combination. 


Overall, the A-share evidence supports the external validity of the SPAR framework in a market with a diferent trading schedule and heterogeneous intraday volume curves. We view it as an additional market check. 