# Co-authorship of journal articles

<button-counter>aa</button-counter>

>[!TIP|label:Tips with working together on a publication：]
>• $\ \textcolor{red}{Talk \ a \ lot:}$  adopt a pattern of regular correspondence, swapping ideas, and
points of view $\\$
• $\ \textcolor{red}{Agree \ to \ disagree:}$  do not expect to agree on every issue, keep disagreements
in perspective, and be prepared to compromise $\\$
• $\ \textcolor{red}{Organise \ and \ plan:}$  create roles for each person and make sure there is an
agreed plan of action, with one person designated as the coordinator/
moderator.

>[!NOTE|label:Thomson and Kamlerf’s principles for developing a publication plan：]
>• Begin your publication plan before your PhD is completed
 $\\$
•   Think ahead about <mark>which conferences to go to and what papers to present</mark>
 $\\$
•   Think $\textcolor{red}{beyond}$ a small number of familiar journals $\\$
•  Consider <mark>various types of publications</mark>

>[!ATTENTION|label:The process of peer review as aiming to：]
>• Ensure submitted articles are suitable for the journal and its readers
 $\\$
• Give you $\text{\color{blue}{detailed and constructive feedback}}$  on your work from experts in the field $\\$
• Alert you to any errors or gaps in the literature you may have overlooked $\\$
• $\text{\color{blue}{Create a discussion between the author, reviewers, and editor}}$ around a research field or topic (Taylor & Francis Group 2018, online)

>[!TIP|label:advice to our students when responding to reviewers’ reports：]
>• Don’t send an angry email to the editor if you are not happy with a review$\\$
• Don’t pick a fight with the reviewers (or the editor) $\\$
• <mark>Thank the reviewers for their feedback</mark> $\\$
• Address the reviewers’ comments systematically, and politely, taking each comment $\text{\color{red}{one at a time}}$ $\\$
• Explain how you have made the required changes, or explain why you haven’t made particular changes (with a reasoned justification for not having made them, <mark>not ‘I disagree’</mark>). $\\$

>[!TIP|label:Content]
>
>$\qquad$ Section 1 $\qquad$ Developing a publication plan
>
>$\quad \\$
>$\qquad$ Section 2 $\qquad$ Co-authorship of journal articles
>
>$\quad \\$
>$\qquad$ Section 3 $\qquad$ The peer review process
>
>$\quad \\$















<hr color = 'red'>





<hr color = 'red'>

> [!COMMENT]
> An alert of type 'comment' using style 'callout' with default settings.


[点击跳转](#jump)


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

a

<table border="0" cellpadding="0" cellspacing="0" width="628" style="border-collapse:
 collapse;table-layout:fixed;width:471pt">
 <colgroup><col width="374" style="mso-width-source:userset;mso-width-alt:11968;width:281pt">
 <col width="103" style="mso-width-source:userset;mso-width-alt:3296;width:77pt">
 <col width="79" style="mso-width-source:userset;mso-width-alt:2528;width:59pt">
 <col width="72" style="width:54pt">
 </colgroup><tbody><tr height="19" style="height:14.25pt">
  <td height="19" width="374" style="height:14.25pt;width:281pt">Amounts in million
  dollars</td>
  <td align="right" width="103" style="width:77pt">2010</td>
  <td align="right" width="79" style="width:59pt">2009</td>
  <td align="right" width="72" style="width:54pt">2008</td>
 </tr>
 <tr height="19" style="height:14.25pt">
  <td height="19" style="height:14.25pt">Reported cash flow used in investing</td>
  <td align="right">565656</td>
  <td align="right">555</td>
  <td align="right">56565</td>
 </tr>
 </tr>
 <tr height="19" style="height:14.25pt">
  <td height="19" style="height:14.25pt">Investments in time deposits</td>
  <td align="right">1348</td>
  <td align="right">513</td>
  <td align="right">613</td>
 </tr>
 <tr height="19" style="height:14.25pt">
  <td height="19" style="height:14.25pt">Maturities of time deposits</td>
  <td align="right">1998</td>
  <td align="right">1811</td>
  <td align="right">823</td>
 </tr>
 <!--[if supportMisalignedColumns]-->
 <tr height="0" style="display:none">
  <td width="374" style="width:281pt"></td>
  <td width="103" style="width:77pt"></td>
  <td width="79" style="width:59pt"></td>
  <td width="72" style="width:54pt"></td>
 </tr>
 <!--[endif]-->
</tbody></table>

!> 你可以在一个子目录中创建一个 `README.md` 文件来作为路由的默认网页你可以在一个子目录中创 >建一个文件来作为路由的默认网页你可以在一个子目录中创建一个文件来作为路由的默认网页你可以在一个子目录中创建一个文件来作为路由的默认网页你可以在一个子目录中创建一个文件来作为路由的默认网页你可以在一个子目录中创建一个文件来作为路由的默认网页你可以在一个子目录中创建一个文件来作为路由的默认网页

?> 你可以在一个子目录中创建一个 `README.md` 文件来作为路由的默认网页

?> 你可以在一个子目录中创建一个文件来作为路由的默认网页你可以在一个子目录中创建一个文件来作为路由的默认网页你可以在一个子目录中创建一个文件来作为路由的默认网页

?> `.public` 的解决方法是这样的，`cp` 不会无限循环的将 `public/` 复制到自身。