# 第六周

## The one-period binomial framework

均衡定价对基础资产而言

$$
(S_1 - K)^+ :
\begin{cases}
S_1 - K,\quad \ S_1\geq K\\
0, \qquad \qquad S_1<K
\end{cases}
\tag{1}
$$

$S\left(t\right)=S_{0}e^{r t-\frac{1}{2}\sigma^{2}t+\sigma w\left(t\right)}$

利用伊藤引理求 $dS(t)$：

令 $r t-\frac{1}{2}\sigma^{2}t+\sigma w\left(t\right) = \square$

$$
\begin{aligned}
d s\left(t\right) &=\frac{\partial s}{\partial t}d t+\frac{\partial s}{\partial w}d w+\frac{1}{2}\frac{\partial^2 s}{\partial w^{2}}d t \\
\\
&=S_{0}\cdot e^{\square}\left(r-\frac{1}{2}\sigma^{2}\right)d t+S_{0}\cdot e^{\square}d w+\frac{1}{2}S_{0}\cdot e^{\square}\cdot \sigma^{2}d t\\
\\
&=S_{0}\cdot e^{\square}rdt + S_{0}\cdot e^{\square}\sigma dw\\
\\
&=rS_{t}dt + \sigma S_{t}dw\\
\end{aligned}
$$