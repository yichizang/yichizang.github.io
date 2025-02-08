---
title: p-进数简介
date: 2025-02-08
categories: [Fun with frontiers]
tags: [math, p-adic number]
math: true
---

读者可能在各种科普资料中听说过 $p$-进数，假设我们抛开理智考虑这样一个数

$$\cdots999.0$$

并且尝试将它加一，由于每一位上的 $9$ 加一后得到 $0$ 并且进一位，进行一个希尔伯特旅馆式的无穷尽进位后，最终会得到

$$\cdots999+1=0.$$

这似乎暗示了 $\cdots999=-1$。对于一个素数 $p$，在 $p$ 进制下考察类似这样形式的数就被称为 $p$-进数。事实上，这样的数是可以被严格化描述的。令人惊讶的是，甚至存在基于这种数域的弦论和量子理论。

## p-进数简介

### 何为 p-进数

一个 $p$-进整数（$p$-adic integer）可以在形式上被定义为如下级数

$$x=a_0+a_1p+a_2p^2+\cdots,$$

其中 $a\_n\in\mathbb{Z}$ 且 $0\leqslant a\_n\leqslant p-1$，$p$ 是一个质数；而一个 $p$-进数（$p$-adic number）可以被定义为级数

$$x=a_{-k}p^{-k}+\cdots+a_{-1}p^{-1}+a_0+a_1p+a_2p^2+\cdots.$$

这两个级数之所以收敛，是因为我们使用的不是通常的绝对值范数，而是 $p$-进范数（$p$-adic norm），定义为

$$\left|a_kp^k+a_{k+1}p^{k+1}+\cdots\right|_p=p^{-k},\quad a_k\ne 0.$$

我们特别规定 $\|0\|\_p=0$。这个范数满足强三角不等式（strong triangular inequality）

$$|x+y|_p\leqslant\max(|x|_p,|y|_p).$$

因此有时它被称为超范数。

> 在这个范数下，无穷级数 $\sum\_na\_n$ 收敛只需要 $a\_n$ 收敛于 $0$ 即可。
{: .prompt-info }

在 $p$-进范数的意义下，$p^k$ 随着指数 $k$ 增大，模反而减小，因此以上定义中的级数是收敛的。

$p$-进数的加、减、乘法都是自然的。为了计算除法，我们需要考虑如何计算 $x^{-1}$。首先让我们考虑 $\|x\|\_p=1$ 即求解整数列 $(b\_0,b\_1,\cdots)$ 满足

$$xx^{-1}=(a_0+a_1p+\cdots)(b_0+b_1p+\cdots)=1.$$

为此，只需要迭代求解 $b\_0$ 满足 $a\_0b\_0=1+c\_1p\equiv1(\mathrm{mod}\,p)$，$b\_1$ 满足 $a\_0b\_1+a\_1b\_0+c\_1=c\_2p\equiv0$，以此类推，即可解出 $x^{-1}$。

一般而言，如果 $x=p^ku$ 而 $\|u\|\_p=1$，则 $x^{-1}=p^{-k}u^{-1}$。另外 $\|x^{-1}\|\_p=(\|x\|\_p)^{-1}$。

对于一个 $p$-进数，我们记

$$\nu(x)=-\log_p|x|_p$$

称为 $p$-进赋值（valuation）。这是一个整数，用于表明 $x$ 最低的非零数位，$\nu(0)=\infty$。

$p$-进整数和 $p$-进数全体通常分别记作 $\mathbb{Z}\_p$ 和 $\mathbb{Q}\_p$，显然它们分别构成一个环和域。

> $\mathbb{Q}\_p$ 是 $\mathbb{Q}$ 在 $p$-进度量下的完备化。虽然同样是不可数集，但它和 $\mathbb{Q}$ 在绝对值度量下的完备化 $\mathbb{R}$ 性质有很大差异。举例来说，当 $p$ 除以 $4$ 余 $1$ 时，$\mathbb{Q}\_p$ 中存在平方为 $-1$ 的数。此外，对于不同的素数 $p,q$，$\mathbb{Q}\_p$ 和 $\mathbb{Q}\_q$ 也是不同构的。
>
> 拓扑来看，$\mathbb{Q}\_p$ 上的每一个球都是既开又闭的，并且任意两个球都只可能完全不交或者完全包含。这也意味着 $\mathbb{Q}\_p$ 是一个完全不连通的豪斯多夫空间。
>
> $\mathbb{Q}\_p$ 的代数闭包是它的一个无限扩张 $\bar{\mathbb{Q}}\_p$，但这个空间不是完备的。它的完备化称为 $p$-进复数 $\mathbb{C}\_p$，和 $\mathbb{C}$ 同构，可以被视为一个装备了不同范数的复数域。
{: .prompt-info }

> 我们简单说明 $\mathbb{Q}$ 是如何嵌入 $\mathbb{Q}\_p$。首先注意到整数可以直接直接写为其对应的 $p$-进制形式，因而 $\mathbb{Z}\subset\mathbb{Z}\_p$。将一个整数写为 $n=p^{\nu(n)}k$ 的形式，其中 $k$ 与 $p$ 互素，则
>
> $$\frac{1}{n}=p^{-\nu(n)}k^{-1},\quad k^{-1}\in\mathbb{Z}_p.$$
>
> 而我们知道，任何有理数 $\alpha$ 都可以写为 $p^{\nu(\alpha)}n/m$ 的形式，其中 $m,n$ 都和 $p$ 互素。因此 $n/m$ 也是一个 $p$-进整数。于是我们就把 $\alpha$ 写成了一个 $p$-进数，且 $\|\alpha\|\_p=p^{-\nu(\alpha)}$。
{: .prompt-info }

### p-进数的积分

接下来我们想要计算在 $p$-进数上的积分[^integral]，为此我们希望定义一个 $p$-进数上的积分测度 $\mathrm{d}x$。出于各种考虑，我们显然希望这个测度是平移 $x\mapsto x+a$ 不变的，并且我们选取归一化使得 $\mathbb{Z}\_p$ 的测度

$$\int_{\mathbb{Z}_p}\mathrm{d}x=1.$$

由于我们可以将 $\mathbb{Z}\_p$ 分成互不相交的 $p$ 个部分 $\mathbb{Z}\_p=\bigcup\_{k=0}^{p-1}C\_k$，其中

$$C_k=\{a_0+a_1p+\cdots\in\mathbb{Z}_p|a_0=k\}$$

显然不同的 $C\_k$ 可以通过平移相互转化，因此它们的测度应该相等。于是

$$\int_{C_k}\mathrm{d}x=p^{-1}.$$

重复这一推理过程，如果我们进一步划分 $C\_k$ 为更小的互不相交的子集

$$C_{k_1,k_2,\cdots,k_n}=\{a_0+a_1p+\cdots\in\mathbb{Z}_p|a_{i-1}=k_i,i=1,\cdots,n\},$$

那么就可以得出

$$\int_{C_{k_1,\cdots,k_n}}\mathrm{d}x=p^{-n}.$$

有了这些知识，我们就可以计算 $p$-进数的积分了。

作为一个例子，让我们考察如下积分[^subscript]

$$I=\int_{\mathbb{Z}_p}\mathrm{d}x\,|x|^s.$$

注意到 $p$-进范数在 $C\_{k\ne0}$ 上是常数 $\|x\|=1$，于是

$$I=(p-1)p^{-1}+\int_{C_0}\mathrm{d}x\,|x|^s.$$

进一步地，在 $C\_{0,k\ne0}$ 上 $p$-进范数也是常数，因此这个积分可以被进一步写为

$$I=\frac{p-1}{p}+\frac{p-1}{p^2}p^{-s}+\int_{C_{0,0}}\mathrm{d}x\,|x|^s.$$

以此类推，这个积分最终可以被写成一个级数

$$\begin{aligned}
I&=\frac{p-1}{p}+\frac{p-1}{p^2}p^{-s}+\frac{p-1}{p^3}p^{-2s}+\cdots\\
&=\frac{p-1}{p}\frac{1}{1-p^{-s-1}},\quad \mathrm{Re}\,s>-1.
\end{aligned}$$

这个积分结果在 $\mathrm{Re}\,s>-1$ 时是收敛的。注意到这与在 $\mathbb{R}$ 上 $(-a,a)$ 区间内同样的积分收敛条件是一样的。

以上的讨论完全可以自然推广到 $\mathbb{Q}\_p$ 中，例如考虑

$$C^{(-1)}=\{a_{-1}p^{-1}+a_0+a_1p+\cdots\in\mathbb{Q}_p\},$$

则有

$$\int_{C^{(-n)}}\mathrm{d}x=p^n$$

以及

$$\int_{C^{(-n)}}\mathrm{d}x\,|x|^s=\frac{p-1}{p}\frac{p^{n+ns}}{1-p^{-s-1}}.$$

如果把积分区域推到全 $\mathbb{Q}\_p$，则积分发散，同样的积分在 $\mathbb{R}$ 上也是发散的。

> 根据以上关于收敛性的讨论，我们可以发现，场论中常见的利用量纲（即缩放行为）判断积分发散的准则在 $p$-进数中也有可能适用。
{: .prompt-tip }

另一个 $p$-进数和实/复数相似的地方是，考察 $\mathrm{SL}(2,\mathbb{Q}\_p)$ 对 $p$-进数的作用

$$\begin{pmatrix}
a & b\\
c & d
\end{pmatrix}:~x\mapsto\frac{ax+b}{cx+d},$$

其中 $a,b,c,d\in\mathbb{Q}\_p$ 且 $ad-bc=1$，这一变换将积分测度变为

$$\mathrm{d}x\mapsto\frac{\mathrm{d}x}{|cx+d|^2}.$$

### p-进数特征标

考虑 $p$-进数域的加法特征标（additive character）和乘法特征标（multiplicative character）[^character][^mult]

$$\chi(x)=\exp(2\pi ix),\quad\pi_s(x)=|x|^s.$$

这意味着

$$\chi(x+y)=\chi(x)\chi(y),\quad\pi_s(xy)=\pi_s(x)\pi_s(y),$$

其中 $\chi(x)$ 可以直接按照通常 $\mathbb{C}$ 上的指数计算，这是因为只有 $x$ 的小数部分有贡献，因此它在整个数域 $\mathbb{Q}\_p$ 上都是良定义的。

#### 伽马函数

结合这两个函数，我们可以定义 $p$-进数上的伽马函数

$$\Gamma_p(s)=\int_{\mathbb{Q}_p}\mathrm{d}x\,\chi(x)\pi_{s-1}(x).$$

通过将这个积分分为对 $\mathbb{Z}\_p$ 和 $\mathbb{Q}\_p\backslash\mathbb{Z}\_p$ 的积分，可以求得这个函数的表达式

$$\Gamma_p(x)=\frac{1-p^{x-1}}{1-p^{-x}}.$$

根据这个表达式我们立刻可以推知

$$\Gamma_p(x)\Gamma_p(1-x)=1.$$

考虑将这个伽马函数的定义式推至 $p\to\infty$，即 $\mathbb{Q}\_\infty=\mathbb{R}$ 的情况，不难发现其对应于通常的

$$\Gamma_\infty(s)=\int_{-\infty}^\infty\mathrm{d}x\,e^{ix}|x|^{s-1}=2\Gamma(s)\cos\frac\pi2s,$$

其中 $\Gamma(s)$ 就是欧拉伽马函数。

在计算 $p$-进数弦论中的开弦散射振幅时[^CP]，结果就可以用 $p$-进数伽马函数表示

$$\begin{aligned}
\mathcal{A}(k_i)&=\int_{\mathbb{Q}_p}\mathrm{d}x\,|x|^{k_1\cdot k_2}|1-x|^{k_1\cdot k_3}\\
&=\prod\Gamma_p(1+k_1\cdot k_i)\\
&=\frac{\Gamma_p(1+k_1\cdot k_2)\Gamma_p(1+k_1\cdot k_4)}{\Gamma_p(1+k_1\cdot k_2+1+k_1\cdot k_4)}
\end{aligned}$$

其中 $k\_i^2=2$，$\sum\_ik\_i=0$。这里最后的表达式实际上就是 $p$-进数中的贝塔函数。

#### 傅里叶变换

利用 $p$-进数的加法特征标，我们可以写出一个 $p$-进数函数的傅里叶变换

$$\tilde{f}(k)=\int_{\mathbb{Q}_p}\mathrm{d}x\,\chi(kx)f(x)$$

以及它的逆变换

$$f(x)=\int_{\mathbb{Q}_p}\mathrm{d}k\,\chi(-kx)\tilde{f}(k).$$

我们可以考察一个熟悉的特例

$$\delta(x)=\int_{\mathbb{Q}_p}\mathrm{d}k\,\chi(kx).$$

不难发现，它在 $x=0$ 时发散，而在 $x\ne0$ 时永远为零。

#### 高斯积分

$p$-进数中同样有高斯积分

$$\int_{\mathbb{Q}_p}\mathrm{d}x\,\chi(ax^2+bx)=\frac{\lambda_{(p)}(a)}{\pi_{1/2}(2a)}\chi(-b^2/4a).$$

其中 $\lambda\_{(p)}(a)$ 是一个勒让德符号，它的具体表达式比较复杂，因此我们不赘述。

### p-进数求导

一种定义 $p$-进数求导的方式是对它的傅里叶变换求导。我们定义这样的一个算符

$$\partial^s \psi(x)=\int_{\mathbb{Q}_p}\mathrm{d}k\,\pi_s(k)\chi(-kx)\tilde{\psi}(k).$$

除了直接从定义出发，我们还可以用卷积的方式计算这个积分。考虑如下的一族函数

$$f_s(x)=\frac{\pi_{s-1}(x)}{\Gamma_p(s)},\quad s\ne1.$$

注意到 $f\_0$ 就是 $\delta$ 函数，并且这族函数在 $s=1$ 处有一个奇点。计算函数的卷积可以发现

$$(f_s\ast f_r)(x)=\int_{\mathbb{Q}_p}\mathrm{d}y\,f_s(y)f_r(x-y)=f_{s+r}(x).$$

特别地，我们定义 $s=1$ 时

$$f_1(x)=\frac{1-p}{p\log p}\log|x|.$$

不难，验证这个定义也满足 $f\_s$ 的卷积性质。

另一方面，我们注意到，$f\_s$ 的傅里叶变换在 $s\ne1$ 时为

$$\tilde{f}_s(k)=\pi_{-s}(k),$$

这意味着当 $f\_{-s}$ 和一个任意函数卷积时，有

$$\begin{aligned}
(f_{-s}\ast\psi)(x)&=\int_{\mathbb{Q}_p}\mathrm{d}k\,\chi(-kx)\tilde{f}_{-s}(k)\tilde\psi(k)\\
&=\int_{\mathbb{Q}_p}\mathrm{d}k\,\pi_s(k)\chi(-kx)\tilde\psi(k)=\partial^s\psi(x).
\end{aligned}$$

这意味着我们定义的 $s$ 阶导数算符的作用可以用卷积计算

$$\partial^s\psi(x)=\Gamma_p(s+1)\int_{\mathbb{Q}_p}\mathrm{d}y\,\frac{\psi(y)}{\pi_{s+1}(x-y)}.$$

> 这个结果和柯西积分公式非常相像。
{: .prompt-tip }

我们可以通过计算一些例子来验证这个结果确实和定义式一致，例如

$$\begin{aligned}
\partial^s\chi(ax)&=\pi_s(a)\chi(ax),\\
\partial^s\pi_r(x)&=\frac{\Gamma_p(r+1)}{\Gamma_p(r+1-s)}\pi_{r-s}(x).
\end{aligned}$$

这些结果确实和我们通常期待的导数结果相一致。

注意到这个导数算符的定义甚至可以延拓到 $s<0$ 时，一个特殊情况是 $s=-1$ 时

$$\partial^{-1}\psi(x)=\frac{1-p}{p\log p}\int_{\mathbb{Q}_p}\mathrm{d}y\,\psi(y)\log|x-y|.$$

## 域扩张和阿代尔

在数学物理领域中，涉及 $p$-进数的讨论中通常会涉及到它的两种扩展，分别是它的二次扩张（quadratic extension）和阿代尔（Adele），在这一段中我们简略介绍一下这两者。

### 二次扩张

数域的二次扩张实际上是我们很熟悉的内容。考虑 $\mathbb{R}$，我们不难注意到，不存在 $x\in\mathbb{R}$ 使得 $x^2=-1$。于是我们想到，可以通过引入 $\sqrt{-1}$ 来构造一个更大的数域，记为 $\mathbb{R}[\sqrt{-1}]$。这个数域中的所有元素都可以写为

$$\mathbb{R}[\sqrt{-1}]\ni z=x+y\sqrt{-1},\quad x,y\in\mathbb{R}.$$

换而言之，这个新的数域可以被看作由 $\{1,\sqrt{-1}\}$ 张成的 $\mathbb{R}$ 上的二维线性空间，并且形式上继承了原来数域上的乘法。以上例子表明，复数域就是实数域的一个二次扩张。

我们想要讨论的对于 $p$-进数的二次扩张就是这样一个数域 $\mathbb{Q}\_p[\sqrt{\tau}]$，记为 $K$。首先，我们需要定义其上的范数，这个定义方式和实数域的二次扩张类似。对于扩张后数域里的一个元素

$$z=x+y\sqrt{\tau},$$

我们可以定义它的共轭为

$$\bar{z}=x-y\sqrt{\tau}.$$

这样一来 $z\bar{z}$ 就是 $\mathbb{Q}\_p$ 中的元素，于是我们可以通过原本的 $p$-进范数来定义 $K$ 上的范数

$$|z|_K=\sqrt{|z\bar{z}|_p}=\sqrt{|x^2-y^2\tau|_p}.$$

### 阿代尔

一个阿代尔（Adele）是这样一个无穷序列

$$a=(a_\infty,a_2,a_3,\cdots,a_p,\cdots),$$

其中 $a\_p\in\mathbb{Q}\_p$，特别地 $\mathbb{Q}\_\infty=\mathbb{R}$，且从某个足够大的素数 $P\_a$ 以后，所有的 $a\_{p>P\_a}\in\mathbb{Z}\_p$。所有阿代尔的集合记作 $\mathbb{A}$，显然它构成一个环，称为阿代尔环。

由于对任何 $p$-进数域，都包含有理数域 $\mathbb{Q}\subset\mathbb{Q}\_p$，因此有理数自然也包括在阿代尔环中。具体来说可以考察所有形如

$$(\alpha,\alpha,\cdots)\in\mathbb{A}$$

的阿代尔，这里 $\alpha\in\mathbb{Q}$。这个构造称为有理数的对角嵌入（diagonal embedding）。

> 为了说明对角嵌入的有效性，我们需要说明对任意一个 $\alpha\in\mathbb{Q}$，当素数 $p$ 足够大时都有 $\alpha\in\mathbb{Z}\_p$。为此，注意到 $\alpha$ 总可以写为 $n/m$ 且 $m,n$ 互素，则当 $p$ 大于 $mn$ 的最大素因数时 $n/m$ 是一个 $p$-进整数。
{: .prompt-tip }

在阿代尔环上，可以很直接地定义加法特征标和范数

$$\begin{aligned}
\chi(a)&=\chi_\infty(a_\infty)\prod_p\chi_p(a_p),\\
|a|_{\mathbb{A}}&=|a_\infty|\prod_p|a_p|_p.
\end{aligned}$$

其中 $\chi\_p$ 是 $\mathbb{Q}\_p$ 上的加法特征标，$\chi\_\infty(x)=\exp(-2\pi ix)$ 是实数上的加法特征标，$\|x\|$ 是实数的绝对值。由于我们要求每一个阿代尔只有有限的非「整数」分量，这两个无穷求积总是良定义的。

关于这个特征标，一个重要的定理是当 $a$ 是有理数（的嵌入）时 $\chi(a)=1$。由这个定理出发，可以立刻得到欧拉乘积公式

$$e^{-2\pi i\alpha}=\prod_p\frac{1}{\chi_p(\alpha)},\quad\alpha\in\mathbb{Q}.$$

另一个类似的公式是关于范数

$$|\alpha|=\prod_p\frac{1}{|\alpha|_p},\quad\alpha\in\mathbb{Q}.$$

要证明这个公式只需要写出 $\alpha=n/m$ 的素因数分解即可。

### 阿代尔的傅里叶变换

现在，我们考虑如下的阿代尔环上的函数

$$\psi(a)=\psi_\infty(a_\infty)\prod_{p\in S}\psi_p(a_p)\prod_{p\notin S}\Omega_p(a_p),$$

其中，$S$ 是素数集的一个有限子集。我们要求 $\psi\_\infty(x)$ 是 $\mathbb{R}$ 上的光滑函数，且任意阶导数在无穷远处以快于任意多项式的速度收敛到 $0$；$\psi\_p(a\_p)$ 是局域常值且紧支撑的函数；$\Omega\_p(a\_p)$ 在 $a\_p\in\mathbb{Z}\_p$ 时为 $1$，否则为 $0$。满足这一系列条件的函数构成阿代尔上的施瓦茨函数（Schwartz function）集，记作 $\mathcal{S}(\mathbb{A})$。

阿代尔环上的傅里叶变换将一个 $\mathcal{S}(\mathbb{A})$ 中的函数变换为另一个 $\mathcal{S}(\mathbb{A})$ 中的函数

$$\tilde\psi(b)=\int_{\mathbb{A}}\mathrm{d}a\,\chi_{\mathbb{A}}(ab)\psi(a),$$

其中积分测度是乘积测度 $\mathrm{d}a=\mathrm{d}a\_\infty\mathrm{d}a\_2\cdots$。

## 脚注

[^integral]: 这里的积分都是实/复值函数积分
[^subscript]: 在以下讨论中，我们将省去 $p$-进范数的下标 ${}_p$
[^character]: 加法特征标和乘法特征标可以简单理解为域加法和乘法的一维实/复表示
[^mult]: 乘法特征标的选择实际上不止一种，可以在 $\|x\|\_p^s$ 上额外乘一个 $\mathbb{Z}\_p^\ast$ 的有限阶特征标
[^CP]: 这里并未考虑 Chan-Paton 规则