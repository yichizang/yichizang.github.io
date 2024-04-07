---
title: 量子力学（二）
date: 2024-04-07
categories: [Path to physics, Quantum Mechanics]
tags: [physics, qm]
math: true
---

## 连续谱和波函数

### 连续谱

自旋的例子中，可能的测量值是分立的，但我们也会遇到连续的可观测量的情况。一个例子就是 **空间坐标**。

先考虑一维的情况，此时空间坐标算符 $x$ 的本征态就是所有

$$
\ket{x=x_0},\quad x_0\in\mathbb{R}.
$$

我们将其简记为 $\ket{x}$。

> 要注意区分 $x$ 在何时表示算符，何时表示本征值（数）。有时为了区分，我们会用 $\hat{x}$ 来表示算符。
{: .prompt-warning }

类比我们如何在一组离散的基下展开某个量子态

$$
\ket{\psi}=\sum_ic_i\ket{a_i},\quad\sum_i|c_i|^2=1,
$$

在这组连续的基下展开量子态就可以通过将求和改为积分[^int]实现

$$
\ket{\psi}=\int\mathrm{d}x\,\psi(x)\ket{x},\quad\int\mathrm{d}x\,|\psi(x)|^2=1.
$$

这里的 $\psi(x)$ 就是我们常说的 **波函数**。类比于 $c_i=\braket{a_i\|\psi}$，波函数实际上就是量子态 $\ket{\psi}$ 在坐标算符本征基下的分量

$$
\psi(x)=\braket{x|\psi}.
$$

> 这件事可以通过线性代数中提到的单位分解得到。对于连续谱，就是
>
> $$1=\int\mathrm{d}x\,\ket{x}\bra{x}.$$
>
> 应用单位分解，就有
>
> $$\ket{\psi}=\int\mathrm{d}x\ket{x}\braket{x|\psi}.$$
{: .prompt-tip }

对于三维空间坐标 $\pmb{x}=(x,y,z)$，三个空间分量的算符是对易的[^comm]

$$
[x,y]=[y,z]=[x,z]=0.
$$

因此一个量子态可以在它们的共同本征基下展开

$$
\ket{\psi}=\int\mathrm{d}^3x\,\ket{\pmb{x}}\braket{\pmb{x}|\psi},
$$

得到三维的波函数

$$
\psi(\pmb{x})=\braket{\pmb{x}|\psi}.
$$

### Delta 函数

> 这一小节是对数学内容的一点补充，在这里我们暂时显式写出积分上下限，以提醒读者这些积分是 **定积分**。
{: .prompt-info }

之所以单位分解成立，是因为在离散的正交归一基中

$$\braket{a_i|a_j}=\delta_{ij}.$$

因此在计算 $\braket{a_i\|\psi}$ 时，只有 $\ket{\psi}$ 的 $\ket{a_i}$ 分量才会有非零的贡献值。

对于连续谱，正交归一基则给出

$$
\braket{x_1|x_2}=\delta(x_1-x_2).
$$

这里的 $\delta(x)$ 是 **狄拉克 $\delta$ 函数**。它满足

$$
\delta(x)=\left\{\begin{aligned}
&0,&&x\ne 0\\
&\infty,&&x=0
\end{aligned}\right.
$$

以及

$$
\int_{-\infty}^\infty\mathrm{d}x\,\delta(x)=1.
$$

这看起来非常奇怪，事实上严格的定义需要用到 *广义函数*。但我们只需要记住其最重要的性质：

$$
\int_{-\infty}^\infty\mathrm{d}\xi\,f(\xi)\delta(x-\xi)=f(x).
$$

这样一来，就有

$$
\braket{x|\psi}=\int_{-\infty}^\infty\mathrm{d}\xi\,\psi(\xi)\braket{x|\xi}=\int_{-\infty}^\infty\mathrm{d}\xi\,\psi(\xi)\delta(x-\xi)=\psi(x).
$$

> 注意到，这里的 $\ket{x}$ 似乎就不满足我们刚刚提到的归一化条件。一种处理方法是认为，我们无法将一个微观粒子的空间坐标 *无限精准* 地测量出来，因此有意义的物理态实际上是带有一个小展宽的
>
> $$\ket{x^{(\Delta)}}=\frac{1}{\sqrt{2\Delta}}\int_{x-\Delta}^{x+\Delta}\mathrm{d}\xi\,\ket{\xi}.$$
>
> 这样的态就满足归一化条件了[^genFunc]
>
> $$\braket{x^{(\Delta)}|x^{(\Delta)}}=1.$$
{: .prompt-tip }

### 波函数

我们知道，连续函数构成的集合同样也可以作为线性空间。因此，我们可以把这个函数集合作为连续谱的希尔伯特空间[^contFunc]

$$
\mathcal{H}=\{\psi(x)\}.
$$

其中每一个函数就是所谓的 **波函数**。

> 简单来说，我们前文讨论的线性空间和矢量都是一些 *抽象的概念*，但我们实际上也可以依托某些 *具体的对象* 来讨论。在这个例子中这个具体的对象就是各种连续函数，它们的加法和数乘就和抽象概念中的矢量一样，这实际上就是这个抽象概念的一个 *具体实现*。
{: .prompt-tip }

两个波函数的内积定义为

$$
\braket{\phi,\psi}=\int\mathrm{d}x\,\phi^\ast(x)\psi(x).
$$

读者可以自行验证这个定义满足线性性、共轭对称性等等性质。事实上，这个定义和我们之前的结果是一致的

$$
\braket{\phi|\psi}=\int\mathrm{d}x\,\braket{\phi|x}\braket{x|\psi}.
$$

在波函数上也可以定义线性算符。以下是一些例子
1. 乘 $x$；
1. 求导算符 $\partial_x$；

事实上，很快我们将会看到，这两个是函数空间上最重要的线性算符。在狄拉克记号下，线性算符的作用对应为[^calFont]

$$
\mathcal{A}\psi(x)=\braket{x|A|\psi}.
$$

## 平移对称和动量

在经典力学中，对称性是体系十分重要的性质。接下来我们在量子力学中讨论一种很基本的对称性：平移对称性。

### 空间平移

既然量子力学的基础是线性代数，我们自然想到，可以直接定义一个线性算符来表示平移操作

$$
T(a)\ket{x}=\ket{x+a}.
$$

这个算符作用在一个一般的量子态上得到

$$
\begin{aligned}
T(a)\ket{\psi}&=\int\mathrm{d}x\,T(a)\ket{x}\braket{x|\psi}\\
&=\int\mathrm{d}x\,\ket{x+a}\psi(x)\\
&=\int\mathrm{d}x\,\ket{x}\psi(x-a).
\end{aligned}
$$

这意味着平移算符会将 $\psi(x)$ 变换到 $\psi(x-a)$。换句话说

$$
\braket{x|T(a)|\psi}=\braket{x-a|\psi}.
$$

这也可以被看作平移算符作用在左矢的结果

$$
\bra{x}T(a)=\bra{x-a}.
$$

根据左矢和右矢的自然对应，我们知道

$$
T^\dagger(a)\ket{x}\quad\leftrightarrow\quad\bra{x}T(a)=\bra{x-a}\quad\leftrightarrow\quad\ket{x-a}.
$$

这就表示

$$
T^\dagger(a)=T(-a).
$$

另外我们知道，连续进行两次平移操作总可以等价为一个新的平移，平移距离为 $0$ 则相当于什么都不做。把这两条性质用算符形式写出来就是

$$
T(a)T(b)=T(a+b),\quad
T(0)=1_{\mathcal{H}}.
$$

从中，立刻可以得到一个推论：平移算符是 **幺正** 的

$$
T^\dagger(a)T(a)=T(-a)T(a)=1_{\mathcal{H}}.
$$

因此，将整个系统进行平移是不会改变任何物理的。

接下来我们考虑平移算符 $T(a)$ 和 $x$ 的对易子。在这一段中我们暂时恢复算符的上标 $\hat{x}$ 以作区分。将这些算符按不同顺序作用在 $\ket{x}$ 上，分别得到

$$
\begin{aligned}
\hat{x}\,\hat{T}(a)\ket{x}&=\hat{x}\ket{x+a}=(x+a)\ket{x+a}\\
\hat{T}(a)\hat{x}\ket{x}&=x\,\hat{T}(a)\ket{x}=x\ket{x+a}.
\end{aligned}
$$

注意到，这个结果对任意 $\ket{x}$ 都成立，而 $\ket{x}$ 构成希尔伯特空间的基。这就意味着[^commutator]

$$
[\hat{x},\hat{T}(a)]=\hat{x}\hat{T}(a)-\hat{T}(a)\hat{x}=a.
$$

### 平移生成元

> 有关生成元和指数映射的严格数学描述，可以参考有关李群和李代数的内容。
{: .prompt-info }

我们总结一下上一小节关于平移算符的三个性质

$$
T^\dagger(a)=T(-a),\quad T(a)T(b)=T(a+b),\quad T(0)=1_{\mathcal{H}}.
$$

熟悉函数方程的话，我们立刻就会发现，后两条性质恰恰就是指数函数 $f(x)=e^x$ 的性质。事实上，对于算符，我们也可以定义指数函数[^infi]

$$
e^A=1_{\mathcal{H}}+A+\frac{1}{2}A^2+\cdots=\sum_n\frac{1}{n!}A^n.
$$

考虑到平移算符的幺正性，我们可以把平移算符写为

$$
T(a)=e^{-ika},
$$

其中 $k$ 是一个厄米算符 $k=k^\dagger$，称为平移的 **生成元**。可以验证这个平移算符确实满足以上三个性质

$$
(e^{-ika})^\dagger=e^{ika},\quad e^{-ika}e^{-ikb}=e^{-ik(a+b)},\quad e^0=1.
$$

现在，我们考察 **无穷小平移** 的情况，即 $a\to 0$ 的情况。此时由泰勒展开可以写出

$$
T(a)\approx 1_{\mathcal{H}}-ika.
$$

从 $x$ 和 $T(a)$ 的对易关系出发，我们立刻可以得到

$$
[x,T(a)]=-ia[x,k]=a.
$$

即

$$
[x,k]=i.
$$

### 动量算符

出于以下几个原因，我们定义 **动量算符** 为

$$
p=\hbar k,
$$

这就是粒子动量这一可观测量所对应的算符，$\hbar$ 在这里是为了匹配量纲。这样定义有如下几个原因：

- 这样定义的动量算符是厄米的；
- 经典力学中的动量是平移对称性的守恒荷；
- 经典力学中无穷小平移变换的生成函数也是由动量生成；
- 计算可知，动量算符的期望值和经典情形下的动量一致；

> 以上理由更多应该被当做这样定义的「动机」，实际上完全可以将量子力学看作是全新的理论，只不过其部分要素恰好可以与经典力学相对应。
{: .prompt-tip }

动量算符和位置算符的对易关系满足

$$
[x,p]=i\hbar.
$$

这与经典力学中的 **泊松括号** 之间存在某种对应关系

$$
\{x,p\}=1\quad\leftrightarrow\quad\frac{1}{i\hbar}[x,p].
$$

这样的对应关系实际上是普适的[^lieBraket]。这种对应关系也可以作为我们定义动量算符的动机之一。

这个对易关系告诉我们，动量算符和位置算符无法被同时对角化，或者说 **动量和位置无法被同时准确测量**。

对于三维空间的平移，平移算符应该具有形式

$$
T(\pmb{a})=e^{-i\pmb{k}\cdot\pmb{a}}=e^{-i\pmb{p}\cdot\pmb{a}/\hbar}.
$$

此时，动量算符 $\pmb{p}=(p_1,p_2,p_3)$ 和位置算符一样有三个分量。它与位置算符 $\pmb{x}=(x^1,x^2,x^3)$ 之间满足对易关系

$$
[x^m,p_n]=i\hbar\,\delta^m_n.
$$

### 波函数空间动量算符

现在，我们考虑一下波函数空间中的动量算符应该是什么形式的。回顾平移算符在波函数上的作用

$$
\mathcal{T}(a)\psi(x)=\psi(x-a).
$$

则在无穷小变换下

$$
\left(1-\frac{i}{\hbar}a\mathcal{P}\right)\psi(x)=\psi(x)-a\partial_x\psi(x),
$$

其中等式右边我们对 $\psi(x)$ 做了泰勒展开。对比之下，我们立刻会发现波函数空间中的动量算符就是

$$
\mathcal{P}\psi(x)=-i\hbar\partial_x\psi(x).
$$

或者说

$$
\braket{x|p|\psi}=-i\hbar\partial_x\braket{x|\psi}.
$$

我们可以验证一下这个动量算符确实是厄米的。回忆起厄米共轭的定义是

$$
\braket{\phi,\mathcal{P}\psi}=\braket{\mathcal{P}^\dagger\phi,\psi}.
$$

在波函数空间中定义的内积下，可以写出

$$
\begin{aligned}
\braket{\phi,\mathcal{P}\psi}&=\int\mathrm{d}x\,\phi^\ast(x)(-i\hbar\partial_x\psi(x))\\
&=-\int\mathrm{d}x\,(-i\hbar\partial_x\phi^\ast(x))\psi(x)\\
&=\int\mathrm{d}x\,(-i\hbar\partial_x\phi(x))^\ast\psi(x)=\braket{\mathcal{P}\phi,\psi}.
\end{aligned}
$$

其中，第二个等号使用了分部积分法，由于有意义的波函数在 $x\to\infty$ 时应当趋于零[^local]，分部积分的边界项消失。于是我们发现，动量算符确实满足 $\mathcal{P}=\mathcal{P}^\dagger$。

> 读者还可以验证对易关系满足
>
>$$[x,-i\hbar\partial_x]=i\hbar.$$
{: .prompt-tip }

### 动量本征态

> 在本节中，暂时恢复 $\hat{p}$ 的上标。
{: .prompt-info }

动量算符的本征态给出

$$
\hat{p}\ket{p}=p\ket{p}.
$$

我们可以研究一下动量本征态和位置本征态之间的关系。根据波函数空间动量算符的结果，我们可以写出

$$
-i\hbar\partial_x\braket{x|p}=\braket{x|\hat{p}|p}=p\braket{x|p}.
$$

将上式作为一个关于 $\braket{x|p}$ 的微分方程，可以解出

$$
\braket{x|p}=e^{ipx / \hbar}.
$$

也就是说，动量本征态的波函数是一个平面波解。需要注意的是，尽管这和平移算符的形式很像，但这是一个数而不是算符，也不表示任何平移操作。

回忆起，$\braket{x\|p}$ 也可以被看作是基变换操作，也就是说，我们可以把波函数（量子态）在动量空间中展开

$$
\begin{aligned}
\braket{p|\psi}&=\int\mathrm{d}x\,\braket{p|x}\braket{x|\psi}\\
&=\int\mathrm{d}x\,\psi(x)e^{-ipx/ \hbar}.
\end{aligned}
$$

这实际上就是我们熟悉的傅里叶变换。这个结果有时被称为 **动量表象下的波函数**

$$
\braket{p|\psi}=\tilde{\psi}(p).
$$

## 脚注

[^int]: 这里的积分是全空间上的定积分而不是不定积分，我只是懒得打上下标
[^comm]: 也就是说我们可以同时测量粒子的三个空间分量
[^genFunc]: 更准确地说：$\bra{x}$ 应该被理解为某种 *只能作为左矢/对偶矢量* 的东西，对于无穷维线性空间，不能保证每个矢量和对偶矢量的一一对应。从泛函分析的角度说，如果我们考虑函数空间作为希尔伯特空间的实现，则 $\delta$ 函数只能定义在广义函数空间上（即函数空间的线性泛函空间）
[^contFunc]: 更严格的定义需要考虑诸如平方可积的性质，我们暂且不论
[^calFont]: 这里花体和斜体用来表示这是同一个算符的不同实现，接下来我们就会看到一些例子说明这点
[^commutator]: 严格来说，这里等式右边应该是 $a$ 倍的单位算符
[^infi]: 事实上，我们还没有严格定义算符的无穷求和，不过作为物理学家让我们暂时忽略这点。更严格的说法请参考关于李群和李代数的内容
[^lieBraket]: 从某种角度来说，它们的一大共同点在于它们都是李括号
[^local]: 可以从波函数的归一化条件看出