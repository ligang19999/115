# General probability theory, asset price models and B-S formulas

## Probability Space

$\Omega$ 是给定的集合，其 $\sigma$ 代数 $\mathcal{F}$ 是由 $\Omega$ 的子集组成，$\sigma$-algebra $\mathcal{F}$ 具有如下性质：

* $\emptyset \in \mathcal{F}$
* $F\in\mathcal{F}\Rightarrow F^C\in\mathcal{F}, F^C=\Omega\backslash F (补集)$
* $A_1,\ A_2,\ \cdots \in \mathcal{F} \implies A \equiv \cup_{i=1}^{\infty} A_i \in \mathcal{F}$

$(\Omega,\ \mathcal{F})$ 称作 **可测空间 (measurable space)**

基于可测空间 $(\Omega,\ \mathcal{F})$ 上的概率测度 $\mathbb{P}$ 是一个函数：$\mathcal{F} \to [0,\ 1]$：

* $\mathbb{P}(\emptyset)=0, \mathbb{P}(\Omega)=1$
* If $A_1,\ A_2,\ \cdots \in \mathcal{F}$ and $A_i \cap A_j = \emptyset \ (i\neq j)$, then $\mathbb{P}\left( \cup_{i=1}^{\infty} A_i \right) = \sum\limits_{i=1}^{\infty} \mathbb{P}(A_i) $

$(\Omega,\ \mathcal{F},\ \mathbb{P})$ 称作 **概率空间 (probability space)**

## Random Variable and Distribution

## Expectations

$X$ 是概率空间 $(\Omega,\ \mathcal{F},\ \mathbb{P})$ 上的一个随机变量，则：

$$
\mathrm{E}(X) = \int_\Omega X(\omega)\ \mathrm{d}\mathbb{P}(\omega)
$$

$$
\mathrm{E}(\left\vert X \right\vert ) = \int_\Omega \left\vert X(\omega) \right\vert\ \mathrm{d}\mathbb{P}(\omega) < \infty
$$

