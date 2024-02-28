---
title: 线性代数速通（三）
date: 2023-11-07
categories: [Path to physics, CAThematics]
tags: [math, linear algebra]
math: true
---

## 张量

### 线性空间的直和

正常来说，两个线性空间中的元素是无法相加的，因为它们属于不同的空间。但是我们可以定义两个线性空间的 **直和** $V\oplus W$，这也是一个线性空间。直和空间中的每一个元素，都可以形式上[^formally]写为一个 $V$ 中的元素加上一个 $W$ 中的元素

$$\ket{v}+\ket{w}\in V\oplus W.$$

直和空间的加法和数乘就是

$$\begin{aligned}
(\ket{v_1}+\ket{w_1})+(\ket{v_2}+\ket{w_2})&=\ket{v_1}+\ket{v_2}+\ket{w_1}+\ket{w_2}\\
\alpha(\ket{v}+\ket{w})&=\alpha\ket{v}+\alpha\ket{w}.
\end{aligned}$$

这样一来，刚刚形式上的加法就是非常自然的了。

对于原本线性空间的基 $\ket{v_i}$ 和 $\ket{w_i}$，直和空间的一组基就是直接把它们拼起来[^sameElem]

$$\{\ket{v_1},\cdots,\ket{v_n},\ket{w_1},\cdots,\ket{w_m}\}.$$

因此，直和空间的维数也就是两个空间维数之和。

除此之外，我们还可以考虑直和空间上的算符，它们是

$$\mathcal{L}(V)\oplus\mathcal{L}(W)$$

中的元素。一个这样的算符 $A_V+B_W$ 作用在直和空间上的结果就是 **对应的部分分别作用在对应空间的部分上**

$$(A_V+B_W)(\ket{v}+\ket{w})=A_V\ket{v}+B_W\ket{w}.$$

在这里似乎不那么直观了，不太符合我们对乘法分配律的理解。但实际上要考虑到 $A_V$ 无法作用在 $W$ 中的矢量上，反之同理。为了避免这种直观上的冲突，算符直和有时也用 $A_V\oplus V_W$ 记。

> 一个记忆的方法是：**苹果削皮器** 可以作用在 **苹果** 上，**香蕉削皮器** 可以作用在 **香蕉** 上。要想给 **苹果加香蕉** 削皮，就需要 **苹果削皮器加香蕉削皮器**，但每种削皮器还是只能处理对应的水果。
{: .prompt-tip }

### 线性空间的张量积

两个线性空间不仅可以相加，还可以「相乘」，称为 **张量积** $V\otimes W$。如果刚才的直和类比，我们可以写出张量积空间中的某些元素

$$\ket{v}\otimes\ket{w}\in V\otimes W.$$

既然是「乘法」，我们自然希望它满足分配律[^commute]，或者说 **双线性性**[^bilinear]

$$\begin{aligned}
\ket{v_1}\otimes\ket{w}+\ket{v_2}\otimes\ket{w}&=(\ket{v_1}+\ket{v_2})\otimes\ket{w},\\
(\alpha\ket{v})\otimes\ket{w}=\ket{v}\otimes(\alpha\ket{w})&=\alpha\ket{v}\otimes\ket{w}.
\end{aligned}$$

但注意到，在张量积空间中做加法的时候，也可能会遇到

$$\ket{v_1}\otimes\ket{w_1}+\ket{v_2}\otimes\ket{w_2}={}?$$

这种无法被简单写为两个矢量张量积的情况。因此，张量积空间中一个一般的矢量应该具有

$$\ket{v_1}\otimes\ket{w_1}+\ket{v_2}\otimes\ket{w_2}+\cdots$$

的形式。不难看出，对于 $V$ 和 $W$ 的一组基 $\ket{v_i}$ 和 $\ket{w_i}$，张量积空间的一组基就是

$$\forall i,j,\qquad\ket{v_i}\otimes\ket{w_j}.$$

换句话说，张量积空间可以被看作是这一组基生成的空间。因此，张量积空间的维数就是两个空间维数的乘积。

张量积空间上的算符也是类似的

$$\mathcal{L}(V)\otimes\mathcal{L}(W)$$

中的元素，作用的方式也同样是 *苹果削皮器和香蕉削皮器* 的规则。

### 算符与张量

作为张量积的一个例子，考虑一个线性空间 $V$ 和它的对偶空间 $V^\ast$，它们的张量积空间是 $V\otimes V^\ast$。这个空间的一组基自然就是 $\ket{v_i}\otimes\bra{v_j}$。但在狄拉克记号中更常见的写法是 $\ket{v_i}\bra{v_j}$。

注意到，在介绍 $V$ 上的算符时，一个算符实际上可以被写为

$$X=\sum_{i,j}\ket{v_i}\braket{v_i|X|v_j}\bra{v_j}
=\sum_{i,j}X^i{}_j\ket{v_i}\bra{v_j}.$$

换句话说，$\ket{v_i}\bra{v_j}$ 实际上也是 $V$ 上算符空间 $\mathcal{L}(V)$ 的一组基。于是我们知道

$$V\otimes V^\ast$$

就是 $V$ 上的算符空间，或者说 $(1,1)$ 型张量构成的空间。

不难猜到，一个更复杂的张量，例如 $T^{ab}{}_{cde}{}^f$ 是

$$V\otimes V\otimes V^\ast\otimes V^\ast\otimes V^\ast\otimes V$$

中的一个元素。这也就是为什么它们要叫做 **张量**[^tensor]。

### 对称与反称

一个线性空间 $V$ 和自己张量积得到的空间可以被分解为两个子空间的直和

$$V\otimes V=(V\otimes_SV)\oplus(V\otimes_AV),$$

分别被称为 **对称积** 和 **反称积** 空间。其中，对称积被定义为

$$\ket{v}\otimes_S\ket{u}=\ket{u}\otimes_S\ket{v}=\frac{1}{2}(\ket{v}\otimes\ket{u}+\ket{u}\otimes\ket{v})$$

而反称积被定义为

$$\ket{v}\otimes_A\ket{u}=-\ket{u}\otimes_A\ket{v}=\frac{1}{2}(\ket{v}\otimes\ket{u}-\ket{u}\otimes\ket{v}).$$

顾名思义，对称积对于两个矢量交换是对称的，而反称积在两个矢量交换时会多出一个负号。另外，$\ket{v}\otimes_A\ket{v}=0$。反称积有时也被称为 **外积**，记作 $\ket{v}\wedge\ket{w}$。

不难发现，对于 $V$ 的一组基 $\ket{v_i}$，可以构造出对称积空间的一组基

$$\ket{v_i}\otimes_S\ket{v_j},\quad i\leqslant j$$

和反称积空间的一组基

$$\ket{v_i}\wedge\ket{v_j},\quad i<j.$$

### 拓展的对称和反称

一个线性空间 $V$ 多次与自己进行张量积可以被简记为

$$V\otimes V\otimes\cdots\otimes V=V^{\otimes n}.$$

这也就是 $(n,0)$ 型张量组成的空间。它的对偶空间是 $(V^\ast)^{\otimes n}$。在这个空间上同样可以定义对称积和反称积空间。

> 注意到，当 $n\ne2$ 时，就无法再将 $V^{\otimes n}$ 写为对称积空间和反称积空间的直和。
{: .prompt-warning }

对称积很好定义，为了使对称积中任意两个矢量交换都是对称的，我们只需要像之前一样将所有可能出现的排序都平均起来就好

$$\ket{v_1}\otimes_S\ket{v_2}\otimes_S\cdots=\frac{1}{N}\sum_{\sigma\in S_n}\ket{v_{\sigma_1}}\otimes\ket{v_{\sigma_2}}\otimes\cdots,$$

其中的求和是对 $(1,2,\cdots)$ 的所有可能排列 $\sigma$ 进行，$N$ 则是可能的排列总数。这样一来，对称积对于任意矢量的交换都是对称的。

对于反称积，我们则希望对于任意两个矢量的交换都是反称的。换句话说，任意交换两个矢量都会使结果多一个负号

$$\ket{v_1}\wedge\ket{v_2}\Big(\cdots\Big)=-\ket{v_2}\wedge\ket{v_1}\Big(\cdots\Big).$$

这样一来，我们就需要给每一种可能的排序规定一个正负号 $\mathrm{sgn}(\sigma)$，每交换两个矢量，正负号就会改变一次。举例来说，如果规定

$$\mathrm{sgn}(1,2,3,4,\cdots)=+1,$$

那么就有

$$\mathrm{sgn}(1,3,2,4,\cdots)=-1.$$

这么一来，反称积就可以被定义为

$$\ket{v_1}\wedge\ket{v_2}\wedge\cdots=\frac{1}{N}\sum_{\sigma\in S_n}\mathrm{sgn}(\sigma)\ket{v_{\sigma_1}}\otimes\ket{v_{\sigma_2}}\otimes\cdots,$$

同样也对所有的排列求和。当我们交换任意两个矢量时，所有排列的 $\mathrm{sgn}$ 都会变号，因此最终的结果也就会多一个负号。

> 事实上，当 $n=\dim V$ 的时候，反称积空间只剩一维，即它的基只剩一个矢量
>
> $$\ket{v_1}\wedge\ket{v_2}\wedge\cdots\wedge\ket{v_n}.$$
>
> 在 $n>\dim V$ 后反称积空间中就没有任何非零矢量了。
{: .prompt-tip }

### 张量代数与格拉斯曼代数

> 在这一小节中，我们直接用字母代表矢量，而暂时不再使用狄拉克记号或爱因斯坦记号。

如果将 $V^{\otimes 0}$ 定义为底数域[^field]，那么我们定义 **张量代数** 为

$$T^\bullet V=\bigoplus_{n\geqslant 0}V^{\otimes n}.$$

其中乘法就是简单的张量积。

用类似的方式也可以定义 **对称积代数** 和 **反称积代数**。后者也被称为 **外代数** 或 **格拉斯曼代数**

$$\wedge^\bullet V=\bigoplus_{n\geqslant 0}V^{\wedge n}.$$

由于外积的性质，这里的直和实际上到 $n=\dim V$ 就停止了。

格拉斯曼代数中的元素通常被称为 **格拉斯曼数**（Grassmann number），它们具有形式

$$z=c_0+\sum_ic_i\theta_i+\sum_{i,j}c_{ij}\theta_i\theta_j+\cdots,$$

其中 $\theta_i\in V$ 表示 $V$ 中的矢量，而系数 $c$ 通常是复数。另外，在讨论格拉斯曼数时通常省略外积的符号 $\wedge$。

由格拉斯曼代数的定义可以发现，这个代数可以被写为两个部分的直和

$$\wedge^\bullet V=V^{\wedge\text{even}}\oplus V^{\wedge\text{odd}},$$

这两个部分分别是由奇数个和偶数个 $V$ 外积而成的线性空间的直和

$$V^{\wedge\text{even/odd}}=\bigoplus_{n\in\text{even/odd}}V^{\wedge n}.$$

其中由偶数个 $V$ 外积而成的空间 $V^{\wedge\text{even}}$ 内的矢量被称为 **$c$-数**，它们和任何格拉斯曼数都对易

$$(\theta_i\theta_j)z=z(\theta_i\theta_j).$$

而 $V^{\wedge\text{odd}}$ 内的矢量被称为 **$a$-数**，任意两个 $a$-数之间是反对易[^antiComm]的。

## 脚注

[^formally]: 之所以称为「形式上」，是因为实际上在定义直和空间之前，我们还不知道如何将这两个空间中的矢量相加——这正是直和空间干的事情。你完全可以把这个形式和看作有序对的另一种表达方式
[^sameElem]: 注意到，鉴于之前形式和的做法，实际上诸如 $\ket{v}$ 其实是空间 $V$ 中的矢量。但我们在这里简单地认为它代表直和空间中的 $\ket{v}+0_W$。
[^commute]: 由于我们已经见过非交换的乘法了，这里的乘法不满足交换律大家应该也是可以接受的吧
[^bilinear]: 实际上满足双线性性的结构有很多，例如实空间上的内积。一种更数学的定义张量积的方式就是 **所有这样的双线性结构中最大的一个**。这一定义的好处在于不需要关注具体的某组基，在物理上这种性质称为 **协变**。
[^tensor]: 或者说 $\otimes$ 为什么要叫做张量积
[^field]: 即实数域 $\mathbb{R}$ 或复数域 $\mathbb{C}$
[^antiComm]: 即交换会多一个负号