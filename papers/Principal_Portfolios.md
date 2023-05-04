# Principal Portfolios

<font size = 5> **Journal:**</font>

<font size = 4>

Journal of Finance
</font>

<font size = 5> **Authors:**</font>

<font size = 4>

* Bryan Kelly:
  
  AQR Capital Management, Yale School of Management, and NBER
* Semyon Malamud:
  
  Swiss Finance Institute, EPFL, and CEPR, and is a consultant to AQR
* Lasse Heje Pedersen:
  
  AQR Capital Management, Copenhagen Business School, and CEPR
</font>

## Abstract

We propose a new asset pricing framework in which all securities’ signals predict each individual return. While the literature focuses on securities’ own-signal predictability, assuming equal strength across securities, our framework includes crosspredictability—leading to three main results. First, we derive the optimal strategy in closed form. It consists of eigenvectors of a “prediction matrix,” which we call “principal portfolios.” Second, we decompose the problem into alpha and beta, yielding optimal strategies with, respectively, zero and positive factor exposure. Third, we provide a new test of asset pricing models. Empirically, principal portfolios deliver significant out-of-sample alphas to standard factors in several data sets.

## Introducion

本文提出了一种新的方法，通过 **“预测矩阵”** 来分析资产价格

$$
\Pi=E(R_{t+1}S_t')\in\mathbb{R}^{N\times N}
$$

$R_{t+1}=(R_{i,t+1})\in\mathbb{R}^N \qquad i=1,\dotsb,N$：收益率向量

$S_t=(S_{i,t})\in\mathbb{R}^N \qquad i=1,\dotsb,N$：信号向量

预测矩阵 $\Pi$ 的对角线部分跟踪自身信号的预测效果，这是标准资产定价的重点

$\Pi_{i,i} = E(R_{i,t+1}S_{i,t})$：资产 i 基于自身动量信号的预期利润

而预测矩阵还可以做到横截面预测：矩阵的非对角线元素

$\Pi_{i,j} = E(R_{i,t+1}S_{j,t})$：资产 j 的信号对资产 i 的收益的预测作用

>原文：$\\$ Knowledge of the entire prediction matrix, as opposed to the typical focus on diagonal elements alone, is critical to devising optimal portfolios and understanding their risk-return trade-off.

>原文：$\\$ Our main contribution is to develop an extensive theoretical understanding of the prediction matrix and the asset pricing information it carries.

定义 $\Pi$ 的奇异向量为：“principal portfolios” (PPs)

将 $\Pi$ 分解为对称的和反对称的两个部分：

$$
\Pi=\underbrace{\dfrac{1}{2}(\Pi+\Pi')}_{\Pi^s}+\underbrace{\dfrac{1}{2}(\Pi-\Pi')}_{\Pi^a}
$$

## 1. Methodology

变量设定：

* 市场上有 N 个证券，这些证券的交易时间是离散的

* $R_{i,t}$：证券 i 在时刻 t 的超额收益率，
  * 所有 $R_{i,t}$ 组成一个收益率向量：
  $$R_t = (R_{i,t})_{i=1}^N$$
  * 所有 $R_{i,t}$ 的条件协方差矩阵(conditional variancecovariance matrix)：
  $$\Sigma_{R,t}=\operatorname{var}_t(R_{t+1})$$

* $S_{i,t}$：证券 i 在时刻 t 的“信号”或“特征”
  * 所有 $S_{i,t}$ 组成一个收益率向量：
  $$S_t = (S_{i,t})_{i=1}^N$$

### Linear Trading Strategies

$L\in\mathbb{R}^{N\times N}$：权重矩阵

$$
\begin{aligned}
R_{t+1}^{w_t}&=w_t'R_{t+1}\\
\\
&=\sum_j\underbrace{(S_t'L_j)}_{\text{position in j}}\qquad \underbrace{R_{j,t+1}}_{\text{return of j}}\\
\\
&=S_t'LR_{t+1}
\end{aligned}
$$

Proposition 1：一个线性交易策略 $w_t'=S_t'L$ 的期望超额收益率是：

$$
E\bigl(R_{t+1}^{w_t}\bigr)=E\bigl(S_t'LR_{t+1}\bigr)=\text{tr}(L\Pi) \tag{7}
$$

Proposition 2：如果 M 是任意一个半正定矩阵，则线性交易策略 $L=M\Pi'$ 的期望超额收益率是：

$$
E(S'_t L R_{t+1})=\operatorname{tr}(M\Pi/\Pi)=\operatorname{tr}((\Pi M^{1/2})'(\Pi M^{1/2}))\ge0 \tag{8}
$$

>[!TIP|label:半正定矩阵(positive semidefinite)]
>给定一个大小为 $n\times n$ 的实对称矩阵 A，若对于任意长度为 n 的向量 x，$x^TAx \geq 0$ 恒成立，则矩阵 A 是一个半正定矩阵

### The Prediction Matrix versus a Predictive Regression

$$
R_{t+1}=BS_t+\varepsilon_{t+1} \tag{9}
$$

### Objective Function

$$
\max\limits_{L:\|L\|\leq1}E\big(S_t'LR_{t+1}\big) \tag{11}
$$

对 $\Pi$ 进行奇异值分解：

$$
\Pi = U \bar{\Lambda} V'
$$

$\bar{\Lambda}=\text{diag}(\bar{\lambda}_1,\ldots,\bar{\lambda}_N)$

U,V 都是正交矩阵，它们的列分别表示为：$u_k$ 和 $v_k$

Proposition 3 的最优 L 可以写成：

$$
\begin{aligned}
(\Pi'\Pi)^{-1/2}\Pi'&=V\bar{\Lambda}^{-1}VV\bar{\Lambda}U'\\
\\
&=VU'\\
\\
&=\sum_{k=1}^N v_k u'_k
\end{aligned}
$$
