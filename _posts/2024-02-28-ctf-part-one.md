---
title: 共形场论笔记（一）
date: 2024-02-28
categories: [Path to physics, CFT]
tags: [physics, cft]
math: true
---

## 共形变换

### 共形变换定义

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

> 举例来说，如果要求 $g'_{\mu\nu}=g_{\mu\nu}$，则可以得到约束方程
> $$(\partial_\mu\epsilon_\nu+\partial_\nu\epsilon_\mu)=0,$$
> 其解为庞加莱变换的 **基灵矢量**（Killing vector）
> $$\epsilon^\mu=a^\mu+\omega^\mu{}_\nu x^\nu.$$
{: .prompt-tips }

对于共形变换，我们要求 $g'_{\mu\nu}=\Omega(x)g_{\mu\nu}$，将新的约束方程写为

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
> $$f(x)\mapsto f(x+a)=f(x)+a^\mu\partial_\mu f(x).$$
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
> $$\mathrm{d}s^2=g_{\mu\nu}\mathrm{d}x^\mu\mathrm{d}x^\nu+\mathrm{d}x^{d+1}\mathrm{d}x^{d+1}-\mathrm{d}x^{d+2}\mathrm{d}x^{d+2},$$
> 则可以构造同构
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
1. 利用特殊共形变换，将 $x_3$ 推至无穷远点，此时三点变为 $(0,x''_2,\infty)$；
1. 用转动和缩放将 $x''_2$ 转动至新的一点 $x'''_2$；
1. 用特殊共形变换，将无穷远点变回 $x'_3-x'_1$；
1. 再次平移，将原点移至 $x'_1$。

只要计算出 $x'''_2$ 的值，即可完成这个变换。

## 脚注

[^flat]: 显然要求空间（时空）也是平直的，度规平直则意味着 $g_{\mu\nu}$ 不依赖于坐标
[^proof]: 证明留做习题