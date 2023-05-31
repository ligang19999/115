# Multi-period binomial pricing model

初始时刻是 $t=0$, 终止时刻是 $t=N$

市场上有三种资产，两个是基础资产，第三个是衍生资产：

* 无风险资产，也即政府债券，收益率 $r > 0$，定价过程表示为 $B: B_{t+1} = B_t(1+r)$

* 股票，初始价格为已知常数 $S_0$，定价过程表示为 $S:$

$$
S_{t+1}=
\begin{cases}
    uS_t\quad \text{with probability}\ \ 0<p<1\\
    dS_t\quad \text{with probability}\ \ 1-p
\end{cases}
$$

* 看涨期权，执行价格为 K，$t=N$ 时刻的价值为：$V_N = (S_N-K)^{+}$

---