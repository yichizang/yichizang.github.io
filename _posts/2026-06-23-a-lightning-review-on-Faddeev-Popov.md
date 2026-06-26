---
title: 0 维量子场论中的 Faddeev-Popov 方法
date:  2026-06-23
categories: [Path to physics]
tags: [physics, Faddeev-Popov, gauge theory]
math: true
---

Faddeev-Popov 方法是规范理论进行路径积分量子化的通用方法.

## 第一个例子

### 规范理论配分函数

在 0 维量子场论中, 一个标量场就是一个数 $x$.

考虑场空间为 $\mathbb{R}^2$, 场的构型就是 $\vec{v}=(x,y)\in\mathbb{R}^2$. 构造出如下路径积分

$$Z = \int \mathrm{d}x\mathrm{d}y\, S(x,y),$$

其中作用量[^action]是

$$S = \mathrm{e}^{-L} = \mathrm{e}^{-x^2}.$$

显然, 这里的 "规范群" 是 $y$ 方向的平移 $y\mapsto y+\alpha$ 构成的群 $G=\mathbb{R}\_y$. 这个问题看起来非常平凡, 但我们将以这个最简单的玩具模型入手解释一下 Faddeev-Popov 方法的基本思路.

由于规范自由度是冗余的自由度, 我们希望在配分函数中引入一个规范固定项 $\delta(y-\omega)$, 这样就只有 $y=\omega$ 的构型会对路径积分有贡献. 为此, 考虑如下单位分解

$$1 = \int\mathrm{d}\alpha\, \delta(y + \alpha - \omega).$$

则配分函数变为

$$Z = \int \mathrm{d}x\mathrm{d}y\int\mathrm{d}\alpha\, \delta(y + \alpha - \omega)\, S(x,y).$$

我们知道这是个没有反常的理论, 即 $S$ 和积分测度都在 $\mathbb{R}\_y$ 平移下不变. 于是有

$$\begin{aligned}
Z &= \int\mathrm{d}x\mathrm{d}y\int\mathrm{d}\alpha\,\delta(y+\alpha - \omega)\,S(x,y) \\
&= \int\mathrm{d}x\mathrm{d}(y+\alpha)\int\mathrm{d}\alpha\,\delta(y+\alpha - \omega)\,S(x,y+\alpha) \\
&= \int\mathrm{d}x\mathrm{d}y\int\mathrm{d}\alpha\,\delta(y - \omega)\,S(x,y).
\end{aligned}$$

> 这里第二行的等号不是换元, 而是利用了 *积分测度和作用量在规范变换下都不变* 这一性质, 即 $\mathrm{d}y = \mathrm{d}(y+\alpha)$ 以及 $S(x,y) = S(x,y+\alpha)$.
{: .prompt-tip }

于是我们可以把 $\displaystyle\int\mathrm{d}\alpha$ 单独提出来, 并把它替换为 "规范群" 的体积 $V\_G$. 于是配分函数变为

$$Z = V_G\int \mathrm{d}x\mathrm{d}y\,\delta(y - \omega) S(x,y).$$

### 消去 $\delta$ 函数

由于我们的理论是规范不变的, 最终的配分函数 $Z$ 应当不依赖于规范固定 $\omega$ 的具体选取. 于是我们可以插入一个新的单位分解

$$1 = \frac{1}{\sqrt{2\pi\xi}} \int \mathrm{d}\omega\, \mathrm{e}^{-\frac{1}{2\xi}\omega^2},$$

配分函数就变为

$$\begin{aligned}
Z &= \frac{V_G}{\sqrt{2\pi\xi}} \int \mathrm{d}x\mathrm{d}y\int\mathrm{d}\omega\,\mathrm{e}^{-\frac{1}{2\xi}\omega^2}\,\delta(y-\omega) S(x,y) \\
&= \frac{V_G}{\sqrt{2\pi\xi}} \int \mathrm{d}x\mathrm{d}y\,\mathrm{e}^{-\frac{1}{2\xi}y^2} S(x,y).
\end{aligned}$$

至此, 我们相当于在原本的作用量中加入了一项 $\mathrm{e}^{-\frac{1}{2\xi}y^2}$ 作为规范固定项, 这一项破坏了原本的 $\mathbb{R}\_y$ 规范对称性. 另外, 我们把沿规范群轨道积分的贡献 $V\_G$ 单独提取了出来, 剩下的就是真正物理的配分函数.

### 计算验算

作为验算, 我们代入一开始给出的作用量 $S$, 计算可得

$$\begin{aligned}
Z &= V_G \frac{1}{\sqrt{2\pi\xi}} \int \mathrm{d}x\mathrm{d}y\,\mathrm{e}^{-\frac{1}{2\xi}y^2}\mathrm{e}^{-x^2} \\
&= V_G \frac{1}{\sqrt{2\pi\xi}} \sqrt{\pi} \sqrt{2\pi\xi} = V_G \sqrt{\pi}.
\end{aligned}$$

这和直接计算 $S$ 的全平面积分得到的结果一致.

> 在我们的例子中, 最后的作用量还获得了一个意外的 $\mathrm{SO}(2)$ 对称性, 但这只是因为我们选取了一个方便计算的 $S$.
{: .prompt-tip }

### Nakanishi-Lautrup 辅助场

我们的操作相当于在作用量上乘了一项高斯项, 这一项人为地破坏了规范对称性, 因此相当于等价地选定了一个规范条件. 这一项可以被转化成一个辅助场的高斯积分, 注意到

$$\mathrm{e}^{-\frac{1}{2\xi}y^2} = \sqrt{\frac{\xi}{2\pi}} \int \mathrm{d}\omega\, \mathrm{e}^{-\frac{\xi}{2}\omega^2 +\omega y},$$

于是配分函数可以变成

$$Z = \frac{V_G}{2\pi} \int \mathrm{d}x\mathrm{d}y\,\mathrm{d}\omega\,\exp\left\{-\left(L(x,y) + \frac{\xi}{2}\omega^2 - \omega y\right)\right\},$$

其中 $\omega$ 是一个具有动力学的辅助场, 它有助于 BRST 算符的构造.

## 一般构造和鬼场

### Faddeev-Popov 行列式

在更一般的情况中, 假设规范变换是 $\vec{v}\mapsto \vec{v}\_\alpha = R(\alpha)\vec{v}$, 其中 $\alpha$ 是规范变换的参数. 我们希望选取规范固定 $F(\vec{v}) = \omega$. 和上一个例子中一样, 让我们考虑如下单位分解

$$1 = \Delta_{FP} \int\mathrm{d}\alpha\, \delta(F(\vec{v}_\alpha) - \omega).$$

对于一个良好定义的"规范固定", 我们要求对于每个场构型 $\vec{v}$, 存在 **唯一** 的 $\alpha\_0$ 满足 $F(\vec{v}\_{\alpha\_0}) = \omega$. 因此我们可以用 $\delta$ 函数的积分公式求得

$$\Delta_{FP}(\vec{v}) = \left|\frac{\partial}{\partial\alpha}F(\vec{v}_\alpha)\right|_{\alpha = \alpha_0},$$

这称为 Faddeev-Popov 行列式[^determinant]. 注意到这个表达式在规范变化下保持不变, 这是因为规范群 $G$ 在自身作用下不变, 因而用于定义 $\Delta\_{FP}(\vec{v})$ 的积分 $\int\mathrm{d}\alpha\,\delta(F(\vec{v}\_\alpha)-\omega)$ 也在规范变换下不变. 由于这个性质, 就有

$$\Delta_{FP}(\vec{v}) = \Delta_{FP}(\vec{v}_{\alpha_0}) = \left|\frac{\partial}{\partial\alpha}F(\vec{v}_{\alpha_0\cdot\alpha})\right|_{\alpha = 0}.$$

这意味着我们可以考虑无穷小规范变换 $\vec{v}\mapsto \vec{v} + T(\vec{v})\alpha + O(\alpha^2)$, 进而

$$\Delta_{FP}(\vec{v}) = \det(F'\,T(\vec{v}_{\alpha_0})).$$

> 这里 $T(\vec{v})$ 是一个作用在 $\alpha$ 上的线性变换, 因此这个表达式里的 $\det$ 是在 $\alpha$ 所在的线性空间上定义的. 在 Yang-Mills 理论中规范变换参数和规范场定义在同一个空间中, 这个 $\det$ 因此就是这个空间上的泛函行列式. 对我们现在的例子而言参数空间是一维的, 因此 $\det$ 只是出于形式上的意义存在.
{: .prompt-info }

### 鬼场

把这个规范固定插入配分函数中就会得到

$$Z = \int \mathrm{d}x\mathrm{d}y\, \det(F'\,T(\vec{v}_{\alpha_0})) \int\mathrm{d}\alpha\, \delta(F(\vec{v}_\alpha) - \omega) S(x,y).$$

因为其他所有项都是规范不变的, 出于和之前相同的论证, $\alpha$ 的积分可以被提出来, 得到规范群体积 $V\_G$. 于是就有

$$Z = V_G \int\mathrm{d}x\mathrm{d}y\, \det(F'\,T(\vec{v}_{\alpha_0}))\, \delta(F(\vec{v}) - \omega) S(x,y).$$

由于 $\delta$ 函数的存在, 对积分有贡献的实际上只有满足规范固定条件 $F(\vec{v}) = \omega$ 的场构型, 也就是形如 $\vec{v}\_{\alpha\_0}$ 的构型. 这意味着我们可以把 Faddeev-Popov 行列式里的 $\vec{v}\_{\alpha\_0}$ 替换为 $\vec{v}$ 而积分结果不变. 随后我们可以用上一节相同的办法处理 $\delta$ 函数. 于是配分函数就可以写为

$$Z = \frac{V_G}{\sqrt{2\pi\xi}} \int \mathrm{d}x\mathrm{d}y\, \det(F'\,T(\vec{v}))\, \mathrm{e}^{-\frac{1}{2\xi} F^2(\vec{v})} S(x,y),$$

最后让我们处理 Faddeev-Popov 行列式, 我们利用如下 Grassmann 数的高斯积分公式

$$\det\Delta = \int\mathrm{d}c\mathrm{d}\bar{c}\, \mathrm{e}^{\bar{c}\Delta c},$$

其中 $c$ 和 $\bar{c}$ 都是反对易的 Grassmann 数. 于是我们最终获得了如下的配分函数

$$Z = \frac{V_G}{\sqrt{2\pi\xi}} \int \mathrm{d}x\mathrm{d}y\,\mathrm{d}c\mathrm{d}\bar{c}\, \exp\left\{-\left(L(\vec{v}) + \frac{1}{2\xi}F^2(\vec{v}) - \bar{c}\, F'(\vec{v})T(\vec{v})\, c\right)\right\}.$$

我们会发现, 这里相当于引入了一对费米子场 (反对易场) $c$ 和 $\bar{c}$. 尽管它们有动力学, 但它们只是来自求解过程中的数学技巧, 因此它们应当是非物理的. 这一对费米子场称为鬼场.

## 第二个例子

### 转动规范变换

现在让我们考察如下作用量

$$S(\vec{v}) = \mathrm{e}^{-(x^2+y^2)} = \mathrm{e}^{-r^2},$$

规范变换显然是 $\mathrm{SO}(2)$ 转动[^reflection], 由

$$\vec{v}\mapsto R(\alpha)\vec{v},\quad R(\alpha) = \begin{pmatrix}
\cos\alpha & -\sin\alpha \\
\sin\alpha & \cos\alpha
\end{pmatrix}$$

给出. 我们提出如下规范固定条件

$$F(\vec{v}) = \frac{y}{x} = \tan\theta = \omega,$$

依照刚才的说法, 可以算出 Faddeev-Popov 行列式[^fp]

$$\Delta_{FP}(\vec{v}) = \frac{1}{2}\left|\frac{\partial}{\partial\theta}\tan\theta\right| = \frac{1}{2\cos^2\theta} = \frac{1}{2} + \frac{y^2}{2x^2}.$$

这里的系数 $1/2$ 是因为我们的规范固定条件实际上并不完美, 它与每个规范轨道的交点数是两个而非一个. 所幸在这个玩具模型中这可以通过一个简单的 $1/2$ 系数解决.

把这些结合起来, 我们就可以写出配分函数

$$\begin{aligned}
Z &= \frac{V_G}{\sqrt{2\pi\xi}} \int r\mathrm{d}r\mathrm{d}\theta\,\frac{1}{2\cos^2\theta}\mathrm{e}^{-\frac{1}{2\xi}\tan^2\theta}\mathrm{e}^{-r^2} \\
&= \frac{V_G}{2\pi} \int r\mathrm{d}r\mathrm{d}\theta\,\mathrm{d}\omega\,\mathrm{d}c\mathrm{d}\bar{c}\, \exp\left\{-\left(r^2 + \frac{\xi}{2}\omega^2 - \omega \tan\theta - \frac{\bar{c}c}{2\cos^2\theta}\right)\right\}.
\end{aligned}$$

物理计算中通常把配分函数写成第二行的形式, 这相当于给出了一个等效作用量. 不过在我们的例子中第一行的结果更便于计算. 读者可以自行验证这和直接高斯积分的结果一致, 其中 $V_G=2\pi$ 是规范群的体积.

### BRST 对称性

可以看到, 由于鬼场和可选的 Nakanishi-Lautrup 辅助场的引入, 我们原本希望消除希尔伯特空间中的规范冗余自由度, 却最终获得了一个比原先更大的希尔伯特空间. 尽管这在计算上可以得到正确的结果, 但我们还需要一套方法排除掉新的希尔伯特空间中的非物理自由度. 这一套方法就是 BRST 上同调.

一个关键的观察是, 引入鬼场的 Grassmann 数积分

$$\det\Delta = \int\mathrm{d}c\mathrm{d}\bar{c}\, \mathrm{e}^{\bar{c}\Delta c}$$

实际上暗示了鬼场 $c$ 和 $\bar{c}$ 与玻色的规范参数 $\alpha$ 都接受 $\Delta$ 的线性作用, 因此我们可以认为鬼场的场空间实际上就是规范参数空间, 只不过变成了反对易数. 这启发我们把 (无穷小) 规范变换参数替换为鬼场, 得到 $\delta_Q x = -cy$ 以及 $\delta_Q y = cx$. 我们可以补全鬼场以及辅助场 $\omega$ 的变换来使得作用量在 $\delta_Q$ 的作用下不变, 用 $(r,\theta)$ 坐标可以写得更清楚

$$\begin{aligned}
\delta_Q r &= 0, & \delta_Q \theta &= c, && \\
\delta_Q c &= 0, & \delta_Q \bar{c} &= -2\omega, & \delta_Q \omega &= 0.
\end{aligned}$$

可以看到因为把变换参数替换成了 Grassmann 变量, 这一变换满足 $\delta_Q^2 = 0$. 这称为 BRST (Becchi-Rouet-Stora-Tyutin) 变换.

BRST 变换的幂零特性启发我们考虑 $\delta_Q$ 的上同调, 把物理的希尔伯特空间定义为

$$\mathcal{H}_{\text{phys}} = \mathrm{Ker}\,\delta_Q / \mathrm{Im}\,\delta_Q.$$

可以看出在这个定义下, 只有 $r$ 成为了物理的自由度, 而规范自由度 $\theta$, 辅助场以及鬼场都自然成为了非物理的, 这完全符合我们的期望.

## 脚注

[^action]: 这里的作用量与平时的定义略有不同.
[^determinant]: 将它称为行列式是因为在更高维的版本中它就是 $F$ 关于 $\alpha$ 的雅可比行列式.
[^reflection]: 让我们先不考虑离散规范变换.
[^fp]: 我们直接给出最终出现在配分函数里的项.