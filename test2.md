开始=>start: 开始
结束=>end: 结束
输入=>inputoutput: 输入年份n
条件1=>condition: n能否被4整除？
条件2=>condition: n能被100整除？
条件3=>condition: n能被400整除？
输出1=>inputoutput: 输出闰年
输出2=>inputoutput: 输出非闰年

开始->输入->条件1(yes)->条件2(yes)->条件3(yes)->输出1->结束
条件1(no)->输出2->结束
条件2(no,left)->输出1
条件3(no)->输出2


$\rho_{\theta e}$ 和 $\rho_{\theta M}$ 成比例，等式(9)可近似为 $\beta_{\theta}$






<label for="name">姓名</label>
<input type="text" id="name">

<label for="age">年龄</label>
<input type="number" id="age">

<span>性别</span>
<input type="radio" id="boy" name="age" value="男">
<label for="boy">男</label>

<input type="radio" id="girl" name="age" value="女">
<label for="girl">女</label>


[<kbd> <br> Title <br> </kbd>][Link]

[Link]: # 'readcourse.md'

<button>e</button>

<a href=www.baidu.com><input type="button" οnclick="window.open('连接')"></a>

<input type="button" value="建站资源网" οnclick='http://www.jzzy.com'>

button{
    width: 60px;
    height: 20px;
    font-size: 12px;
    text-decoration: underline;
    border-radius: 4px;
    color: skyblue;
}




<hr color = 'red'>

- This text is {% em %}highlighted !{% endem %}
- This text is {% em %}highlighted with **markdown**!{% endem %}
- This text is {% em type="green" %}highlighted in green!{% endem %}
- This text is {% em type="red" %}highlighted in red!{% endem %}
- This text is {% em color="#ff0000" %}highlighted with a custom color!{% endem %}

>[!ATTENTION|label:提示]
>第二个不对劲

> [!COMMENT]
> An alert of type 'comment' using style 'callout' with default settings.


[点击跳转](#jump)



其中下标 $2$ 代表验证集或测试集。

> [!NOTE|label:注意]
> 在交叉验证的时候是用验证集的数据来计算“样本外” R 方，实验部分则先是用验证集的 R 方作为评估指标，后面又用测试集做了真正的样本外检验。

### Fama-French ME/BE 5x5 组合

用 Fama 和 French 对市值和市净率做双重排序得到的 5x5 组合（FF25）的示性函数作为公司特征，即假设公司属于 FF25 中的某一个组合，那么它在这一个组合上的值为 $1$，在其他组合上的值为 $0$。从而我们得到了25个公司特征，用这些特征构造的因子与市场因子进行正交化，得到了市场中性的因子：

$$
F_{i,\ t} = \widetilde{F}_{i,\ t} - \beta_i R_{m,\ t}
$$

其中 $\widetilde{F}_{i,\ t}$ 为原始的因子值，$F_{i,\ t}$ 为市场中性因子，$\beta_i$ 由整个样本回归得到，$R_{m,\ t}$ 则为市场指数的收益率。

#### 结果

<div align='center'>

![](image/2022-12-27-16-51-57.png)
</div align='center'>

上图中颜色深浅代表了不同大小的样本外 R 方，横坐标代表 $L^{2}$ 正则化的强度，纵坐标代表 $L^{1}$ 正则化的强度，坐标轴做了对数化处理，即数字小的时候宽，数字大的时候窄。

如图 (a)，如果完全不做 $L^{2}$ 正则化，即完全不压缩，则因子数量需要降到两三个才能得到好的样本外 R 方；而如果做一定的压缩，用全部因子（25个）都可以达到不错的样本外 R 方而不会过拟合。

如图 (b)，如果我们对这个25个市场中性因子做 PCA，因子数量并不会对结果产生太大的影响，只需要做一定的压缩就可以得到不错的样本外 R 方。最优的样本外 R 方在因子数量为2的时候取到，这也从侧面印证了 Fama 三因子的效力。

> [!NOTE|label:注意]
> 因子数量的多少通过控制 $L^{1}$ 正则化的强度来实现，并非手动剔除特征值小的成分。
> 
> 这里所谓的“样本外”实际上是验证集。

### 高维特征

作者从前人的工作中总结出了50个与异象相关的特征，然后从 WRDS 取了68个金融比率，外加12个收益率（从一个月到一年的动量）构成80个特征（WRF）。这些特征又做一阶交互、平方、立方，得到 $C_2^{n} + 3 n$ 个特征。对于50个异象特征，我们可以得到 $C_2^{50} + 3 \times 50 = 1,375$ 个特征，对于 WRF，我们可以得到 $C_2^{80} + 3 \times 80 = 3,400$ 个特征。

对这些特征作者做了排序处理，即公司在截面上的特征排名作为真正使用的特征。同样也对这些特征构造的因子做了市场中性化的处理。

#### 结果

<div align='center'>

![](image/2022-12-27-17-20-58.png)
</div align='center'>

在高维特征的结果与在 FF25 的结果相似，做 PCA 后可以将因子数量降到个位数，不做的话是不行的。

### 纯样本外对比

将50个异象组合、80个 WFR 组合以及1375个高阶项组合分别构建切点组合，即 $R_{t}^{\text{mv}} = \hat{b}^{\mathsf{T}} F_t$，把这些切点组合在测试集上的收益率回归到不同的模型上，比较它们的截距项 $\alpha$。

> [!TIP|label:提示]
> 传统方法对 test assets 进行检验是每个 test asset 分别回归得到 $\alpha$。而本文直接利用 SDF 系数构造 test assets 中的切点组合，这样就解决了高维 test assets 难以检验的问题。

#### 结果

下图是构建出来的切点组合的表现，其中图 (a) 和 (b) 是测试集的表现，图 (c) 是全样本的表现。

<div style='display: none'> 公司电话够解释</div>

<div align='center'>

![](image/2022-12-27-17-46-34.png)
</div align='center'>

<!-- slide:break-# -->

可以看到其实过拟合还是挺严重的。

与其他模型的对比如下：

<div align='center'>

![](image/2022-12-27-17-34-08.png)
</div align='center'>

DrawTextStyle("~Hellooo~ :D", 100,100, )


可以看到定价效果是 CAPM < FF 6-factor ≈ Char.-sparse < PC-sparse，即对 test assets（因子）做 PCA 再用本文的压缩估计量，效果是最好的。

## 参考文献

Hansen, L. P., & Jagannathan, R. (1991). Implications of Security Market Data for Models of Dynamic Economies. Journal of Political Economy, 99(2), 225–262. https://doi.org/10.1086/261749

Hansen, L. P., & Jagannathan, R. (1997). Assessing Specification Errors in Stochastic Discount Factor Models. The Journal of Finance, 52(2), 557–590. https://doi.org/10.1111/j.1540-6261.1997.tb04813.x

Kozak, S., Nagel, S., & Santosh, S. (2018). Interpreting Factor Models. The Journal of Finance, 73(3), 1183–1223. https://doi.org/10.1111/jofi.12612

<span id="jump">跳转到的地方</span>

Kozak, S., Nagel, S., & Santosh, S. (2020). Shrinking the cross-section. Journal of Financial Economics, 135(2), 271–292. https://doi.org/10.1016/j.jfineco.2019.06.008

$$
\begin{matrix}
{}&{\frac{1}{N} \sum\limits_{n=1}^{N}(\overline{X}_n- \overline{F}\land_n^T)^2}\\
{}&{}\\
{=}&{\frac{1}{N} \sum\limits_{n=1}^{N} \big((\overline{X}_n- \overline{F}\land_n^T) - E(\overline{X}_n- \overline{F}\land_n^T)\big)^2}\\
{}&{}\\
{=}&{\frac{1}{N} \sum\limits_{n=1}^{N} \big((e_n) - E(e_n)\big)^2}\\
{}&{}\\
{=}&{var(e_n)}\\
\end{matrix}
$$

$$
\frac{1}{N} \sum\limits_{n=1}^{N}(\overline{X}_n- \overline{F}\land_n^T)^2
$$

$$
= \frac{1}{N} \sum\limits_{n=1}^{N} \big((\overline{X}_n- \overline{F}\land_n^T) - E(\overline{X}_n- \overline{F}\land_n^T)\big)^2
$$

$$
= \frac{1}{N} \sum\limits_{n=1}^{N} \big((e_n) - E(e_n)\big)^2
$$

$$
= var(e_n)
$$


