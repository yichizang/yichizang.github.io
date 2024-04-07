---
title: 共形场论笔记（一）
date: 2024-02-28
categories: [Path to physics, CFT]
tags: [physics, cft]
math: true
---

## 共形变换

### 共形变换定义

> 对于共形变换严格的定义，例如是否改变度规或者度规分量，以及不同流形之间的映射，我目前还没有完全明白，网上关于这个问题的讨论似乎也没有统一的结论。暂时搁浅此事。
{: .prompt-info }

简单来说，**共形场论** 即是在相对论性量子场论基础上加上额外的对称性：**缩放对称性** 和 **特殊共形对称性**。

为了了解这些新的对称性，我们需要知道 **共形变换**。这是一种坐标变换 $x\mapsto x'$，其无穷小形式为

$$
x^\mu\mapsto x^\mu+\epsilon^\mu(x).
$$

假设该变换保持线元 $\mathrm{d}l^2=g_{\mu\nu}\mathrm{d}x^\mu\mathrm{d}x^\nu$ 不变，并且变换前的度规是平直的[^flat]，则可以写出度规的无穷小变换

$$
\begin{aligned}
g'_{\mu\nu}=&g_{\sigma\lambda}\frac{\partial x^\sigma}{\partial x^\mu}\frac{\partial x^\lambda}{\partial x^\nu}\\
=&g_{\mu\nu}-(\partial_\mu\epsilon_\nu+\partial_\nu\epsilon_\mu).
\end{aligned}
$$

> 举例来说，如果要求 $g^\prime_{\mu\nu}=g_{\mu\nu}$，则可以得到约束方程
> 
> $$(\partial_\mu\epsilon_\nu+\partial_\nu\epsilon_\mu)=0,$$
> 
> 其解为庞加莱变换的 **基灵矢量**（Killing vector）
> 
> $$\epsilon^\mu=a^\mu+\omega^\mu{}_\nu x^\nu.$$
{: .prompt-tip }

对于共形变换，我们要求 $g^\prime_{\mu\nu}=\Omega(x)g_{\mu\nu}$，将新的约束方程写为

$$
\partial_\mu\epsilon_\nu+\partial_\nu\epsilon_\mu=2\sigma(x) g_{\mu\nu},\quad\Omega(x)=e^{-2\sigma(x)}\approx 1-2\sigma(x).
$$

可以将其化简为

$$
(d-1)\Box\sigma=0,\quad(2-d)\partial_\mu\partial_\nu\sigma=g_{\mu\nu}\Box\sigma,\quad\partial_\mu\epsilon^\mu=\sigma d.
$$

于是我们知道，在 $d>2$ 的情况下，有 $\partial_\mu\partial_\nu\sigma=0$，则

$$
\epsilon^\mu=a^\mu+\omega^\mu{}_\nu x^\nu+\lambda x^\mu+2(b\cdot x)x^\mu-x^2b^\mu.
$$

可以发现这里额外包含了 **缩放变换** 和另一个新的变换，后者称为 **特殊共形变换**。

#### 二维情况

对于 $d=2$ 的情况，约束则变为了 $\Box\sigma=0$。为了解出这个方程，可以做坐标变换

$$
x^\pm=\frac{x^0\pm x^1}{2},
$$

则方程变为 $\partial_+\partial_-\sigma=0$，任意形如

$$
\sigma=f(x^+)+g(x^-)
$$

的函数都可以满足这个方程。我们在以后会详细讨论二维的情况。

### 共形代数

可以通过考察变换在函数上的作用，写出其微分算符表示。

> 举例来说，对于无限小平移，可以写出
>
> $$f(x)\mapsto f(x+a)=f(x)+a^\mu\partial_\mu f(x).$$
>
> 这样一来，可以将平移生成算符写为 $P_\mu=i\partial_\mu$。
{: .prompt-info }

用这种方式，可以写出现有的四种共形变换的微分算符表示：

|变换名称|微分算符表示|自由度数量|
|---|---|---|
| 平移 | $P^\mu=i\partial^\mu$ | $d$ |
| 转动 | $M^{\mu\nu}=i(x^\mu\partial^\nu-x^\nu\partial^\mu)$ | $d(d-1)/2$ |
| 缩放 | $D=ix^\mu\partial_\mu$ | $1$ |
| 特殊共形变换 | $K^\mu=i(2x^\mu x^\nu\partial_\nu-x^2\partial^\mu)$ | $d$ |

总共的自由度数量就是 $(d+1)(d+2)/2$。

> 这个数字看着眼熟。确实，在欧氏空间中，这个代数同构于 $\mathfrak{so}(d+1,1)$，而在闵氏空间中，它同构于 $\mathfrak{so}(d,2)$。具体来说，给出度规
>
> $$\mathrm{d}s^2=g_{\mu\nu}\mathrm{d}x^\mu\mathrm{d}x^\nu+\mathrm{d}x^{d+1}\mathrm{d}x^{d+1}-\mathrm{d}x^{d+2}\mathrm{d}x^{d+2},$$
>
> 则可以构造同构
>
> $$\begin{aligned}
M^{\mu\nu}=J^{\mu\nu},&\quad P^\mu=J^{\mu,d+1}+J^{\mu,d+2},\\
D=J^{d+1,d+2},&\quad K^\mu=J^{\mu,d+1}-J^{\mu,d+2}.
\end{aligned}$$
{: .prompt-info }

通过微分算符表示，可以写出对易关系
- $[M^{\mu\nu},M^{\rho\sigma}]=-i(g^{\mu\rho}M^{\nu\sigma}-g^{\mu\sigma}M^{\nu\rho}-g^{\nu\rho}M^{\mu\sigma}+g^{\nu\sigma}M^{\mu\rho})$；
- $[M^{\mu\nu},P^\rho]=-i(g^{\mu\rho}P^\nu-g^{\nu\rho}P^\mu)$；
- $[M^{\mu\nu},K^\rho]=-i(g^{\mu\rho}K^\nu-g^{\nu\rho}K^\mu)$；
- $[D,P^\mu]=-iP^\mu$；
- $[D,K^\mu]=iK^\mu$；
- $[P^\mu,K^\nu]=2i(g^{\mu\nu}D-M^{\mu\nu})$；
- 其它对易子为零。

### 有限变换

对于 **平移**，**转动** 和 **缩放** 变换，有限变换我们已经很熟悉了，而 **特殊共形变换** 的有限变换略微复杂。在这里给出[^proof]：

| 变换名称 | 有限变换 | 不动点 |
|---|---|---|
| 平移 | $x^\mu\mapsto x^\mu+a^\mu$ | 无 |
| 转动 | $x^\mu\mapsto \Lambda^\mu{}_\nu x^\nu$ | 原点和无穷远点 |
| 缩放 | $x^\mu\mapsto \lambda x^\mu$ | 原点和无穷远点 |
| 特殊共形变换 | $x^\mu\mapsto\dfrac{x^\mu-x^2b^\mu}{1-2b\cdot x+b^2x^2}$ | 原点 |

关于特殊共形变换，注意到
- 无穷远点 $\infty$ 被映射到 $-b^\mu/b^2$；
- $b^\mu/b^2$ 被映射到无穷远点。

有趣的一点是，共形变换可以将任意三个点 $(x_1,x_2,x_3)$ 变换到任意另外三个点 $(x'_1,x'_2,x'_3)$：
1. 首先将 $x_1$ 平移至原点；
1. 利用特殊共形变换，将 $x_3$ 推至无穷远点，此时三点变为 $(0,x^{\prime\prime}_2,\infty)$；
1. 用转动和缩放将 $x^{\prime\prime}_2$ 转动至新的一点 $x^{\prime\prime\prime}_2$；
1. 用特殊共形变换，将无穷远点变回 $x'_3-x'_1$；
1. 再次平移，将原点移至 $x'_1$。

只要计算出 $x^{\prime\prime\prime}_2$ 的值，即可完成这个变换。

## 共形对称性

### 自由场

以自由场为例，我们可以写出一个共形不变的作用量

$$
S=\int\mathrm{d}^dx\left[-\frac{1}{2}\partial_\mu\phi\partial^\mu\phi\right].
$$

其中，设自由场在无穷小共形变换下变换为

$$
\phi(x)\mapsto e^{\Delta\sigma(x)}\phi(x+\epsilon),
$$

其中 $\sigma(x)=\partial_\mu\epsilon^\mu/d$。$\Delta$ 是一个与场有关的参数，在我们的例子中可以算出，为了使得作用量具有共形不变性，有 $\Delta=(d-2)/2$。

将场的变换展开为

$$
\phi(x)\mapsto\left[1+\frac{d-2}{2d}\partial_\mu\epsilon^\mu+\epsilon^\mu\partial_\mu\right]\phi(x).
$$

可以发现作用量的变分是一个全导数

$$
\delta\mathcal{L}=\partial_\mu\left(-\frac{1}{2}\epsilon^\mu\partial_\nu\phi\partial^\nu\phi-\frac{d-2}{2d}\partial_\nu\epsilon^\nu\phi\partial^\mu\phi\right).
$$

### 诺特定理

> 回顾一下，**诺特定理** 说的是：对于一个场的连续对称性
>
> $$\phi\mapsto\delta_\epsilon\phi,\quad\mathcal{L}\mapsto\mathcal{L}+\partial_\mu\Lambda^\mu_\epsilon,$$
>
> 系统在壳时具有如下守恒流
>
> $$J^\mu_\epsilon=\Lambda^\mu_\epsilon-\frac{\partial\mathcal{L}}{\partial(\partial_\mu\phi)}\delta_\epsilon\phi.$$
{: .prompt-info }

对于共形变换，可以算出这个守恒流是

$$
J^\mu_\epsilon=\epsilon_\nu\left(\partial^\mu\phi\partial^\nu\phi-\frac{1}{2}g^{\mu\nu}\partial_\rho\phi\partial^\rho\phi\right)=\epsilon_\nu T^{\mu\nu}_c.
$$

其中括号中的部分就是正则能动张量。

> 但是如果你真的计算一下，就会发现这个守恒流的在壳全导数
>
> $$\partial_\mu J^\mu_\epsilon=-\frac{d-2}{2}\sigma\partial_\mu\phi\partial^\mu\phi$$
>
> 不为零。
{: .prompt-warning }

这是因为上文所说的 *诺特第一定理* 只有在 $\delta_\epsilon$ 不显式依赖于坐标 $x$ 的时候才成立，此时 $\partial_\mu$ 和 $\delta_\epsilon$ 对易。

对于这里的情况，我们可以定义一个新的能动张量

$$
T^{\mu\nu}=T^{\mu\nu}_c+\frac{d-2}{2(d-1)}(\partial^\mu\partial^\nu-g^{\mu\nu}\partial^2)\phi^2.
$$

这是一个 *无迹* 的能动张量，可以证明，将它代入刚才的 $J^\mu_\epsilon$，得到的就是一个正确的守恒流。

> 事实上，任何一个局域的共形场论都具有一个无迹的能动张量。
{: .prompt-info }

通过对守恒流的时间分量积分，我们可以得到对应的 **守恒荷**。共形变换中的四种守恒荷给出

$$
\begin{aligned}
P^\mu=&-i\int\mathrm{d}^{d-1}x~T^{0\mu}(x)\\
M^{\mu\nu}=&-i\int\mathrm{d}^{d-1}x\left[x^\mu T^{0\nu}(x)-x^\nu T^{0\mu}(x)\right]\\
D=&-i\int\mathrm{d}^{d-1}x~x_\mu T^{0\mu}(x)\\
K^\mu=&-i\int\mathrm{d}^{d-1}x\left[2x^\mu x_\nu T^{0\nu}(x)-x^2T^{0\mu}(x)\right].
\end{aligned}
$$

### 对局域算符的作用

如果在作用量中加入一项外部的源 $J(x)$

$$
S_{\text{source}}=\int\mathrm{d}^dx~J(x)\phi(x),
$$

运动方程就会变为

$$
\partial^2\phi+J=0.
$$

此时原本能动张量的导数也会变得非零

$$
\partial_\nu T^{\mu\nu}=-J\partial^\mu\phi.
$$

如果考虑一个局域的源

$$
J(x)=\delta^{(d)}(x-x_\ast),
$$

那么

$$
\partial_\nu T^{\mu\nu}(x)=-\delta^{(d)}(x-x_\ast)\partial^\mu\phi(x).
$$

我们可以在这个局域的源前后[^beforeAfter]分别考察动量守恒荷，即

$$
P_\pm^\mu=-i\int_{x^0\gtrless x^0_\ast}\mathrm{d}^{d-1}x~T^{0\mu}(x).
$$

则在这两个等时面之间的动量变化就给出 $P_\ast^\mu=P_+^\mu-P_-^\mu$。我们可以将这两个积分曲面形变为一个包住 $x_\ast$ 点的超曲面[^deform]，再通过斯托克斯公式将这个积分变为对时空区域内的积分

$$
P_\ast^\mu=-i\int_{\partial\Sigma}\mathrm{d}^{d-1}x~n_\nu T^{\mu\nu}=-i\int_\Sigma\mathrm{d}^dx~\partial_\nu T^{\mu\nu}=i\partial^\mu\phi(x_\ast).
$$

> 当我们在讨论 $P^\mu$ 和某个局域算符 $\phi(x)$ 之间的对易关系时，实际上我们就是在做以上的事：考察某个包围住局域算符的超曲面，以及在其上的动量算符积分。由于这个动量算符的表现和具体 $\Sigma$ 的形状无关，它被称为 **拓扑算符**。
{: .prompt-tip }

### 量子版本

从路径积分量子化的角度，上文提到的积分操作 $P_\ast=P_+-P_-$ 就可以被看作对易子

$$
[P_\mu,\phi(x)]=i\partial_\mu\phi(x).
$$

## 脚注

[^flat]: 显然要求空间（时空）也是平直的，度规平直则意味着 $g_{\mu\nu}$ 不依赖于坐标
[^proof]: 证明留做习题
[^beforeAfter]: 即考虑 $x^0>x^0_\ast$ 和 $x^0<x^0_\ast$ 的两个等时面
[^deform]: 这是因为在源以外的地方都满足动量守恒