---
title: 回顾 Faddeev-Popov 方法
date:  2026-06-23
categories: [Path to physics]
tags: [physics, Faddeev-Popov, gauge theory]
math: true
---

Faddeev-Popov 方法是规范理论进行路径积分量子化的通用方法.

## 0 维量子场论示例

在 0 维量子场论中, 一个标量场就是一个数 $x$.

考虑场空间为 $\mathbb{R}^2$, 构造出如下路径积分

$$Z = \int r\mathrm{d}{r}\mathrm{d}\theta\, S(r,\theta),$$

其中作用量[^action]是

$$S = \mathrm{e}^{-L} = \mathrm{e}^{-x^2} = \mathrm{e}^{-r^2\cos^2\theta}.$$

显然, 这里的 "规范群" 是 $y$ 方向的平移 $y\mapsto y-\eta$ 构成的群 $G=\mathbb{R}_y$. 我们刻意用 $r$ 和 $\theta$ 作为变量只是为了让这个问题看起来没那么傻.

现在让我们引入如下单位分解

$$1 = \int\mathrm{d}\eta\, \delta(r\sin\theta - \eta).$$

则配分函数变为

$$Z = \int r\mathrm{d}{r}\mathrm{d}\theta\int\mathrm{d}\eta\, \delta(r\sin\theta - \eta)\, S(r,\theta).$$

我们知道这是个没有反常的理论, 即 $S$ 和积分测度都在 $\mathbb{R}_y$ 平移下不变. 如果这一步看起来不显然, 那让我们暂时回到 $x$ 和 $y$ 的坐标下, 有

$$\begin{aligned}
Z &= \int\mathrm{d}x\mathrm{d}y\int\mathrm{d}\eta\,\delta(y-\eta)\,S(x,y) \\
&= \int\mathrm{d}x\mathrm{d}(y-\eta)\int\mathrm{d}\eta\,\delta(y-\eta)\,S(x,y-\eta) \\
&= \int\mathrm{d}x\mathrm{d}y\int\mathrm{d}\eta\,\delta(y)\,S(x,y).
\end{aligned}$$

> 这里第二行的等号没有做换元, 我们只利用了 **等式** $\mathrm{d}y = \mathrm{d}(y-\eta)$ 以及 $S(x,y) = S(x,y-\eta)$.
{: .prompt-tip }

于是我们可以把 $\displaystyle\int\mathrm{d}\eta$ 单独提出来, 并把它替换为 "规范群" 的体积 $V_G$. 于是配分函数变为

$$Z = V_G\int r\mathrm{d}r\mathrm{d}\theta\,\delta(r\sin\theta) S(r,\theta).$$

### 消去 $\delta$ 函数

依照和刚才相同的论证, 我们可以把 $\delta$ 函数内部替换成 $\delta(r\sin\theta-\zeta)$, 而最终的配分函数 $Z$ 应当不依赖于 $\zeta$. 于是我们可以插入一个新的单位分解

$$1 = \frac{1}{\sqrt{2\pi\xi}} \int \mathrm{d}\zeta\, \mathrm{e}^{-\frac{1}{2\xi}\zeta^2},$$

配分函数就变为

$$\begin{aligned}
Z &= \frac{V_G}{\sqrt{2\pi\xi}} \int r\mathrm{d}r\mathrm{d}\theta\int\mathrm{d}\zeta\,\mathrm{e}^{-\frac{1}{2\xi}\zeta^2}\,\delta(r\sin\theta-\zeta) S(r,\theta) \\
&= \frac{V_G}{\sqrt{2\pi\xi}} \int r\mathrm{d}r\mathrm{d}\theta\,\mathrm{e}^{-\frac{1}{2\xi}r^2\sin^2\theta} S(r,\theta).
\end{aligned}$$

至此, 我们相当于在原本的作用量中加入了一项 $\mathrm{e}^{-\frac{1}{2\xi}r^2\sin^2\theta}$ 作为规范固定项, 这一项破坏了原本的 $\mathbb{R}_y$ 规范对称性. 另外, 我们把沿规范群轨道积分的贡献 $V_G$ 单独提取了出来, 剩下的就是真正物理的配分函数.

### 计算验算

作为验算, 我们代入一开始给出的作用量 $S$, 计算可得

$$\begin{aligned}
Z &= V_G \frac{1}{\sqrt{2\pi\xi}} \int r\mathrm{d}r\mathrm{d}\theta\,\mathrm{e}^{-\frac{1}{2\xi}r^2\sin^2\theta}\mathrm{e}^{-r^2\cos^2\theta} \\
&= V_G \frac{1}{\sqrt{2\pi\xi}} \int_0^{2\pi}\mathrm{d}\theta \int_0^\infty r\mathrm{d}r\,\exp\left\{-\left(\frac{1}{2\xi}\sin^2\theta+\cos^2\theta\right)r^2\right\} \\
&= V_G \frac{1}{\sqrt{2\pi\xi}} \int_0^{2\pi} \frac{\mathrm{d}\theta}{\frac{1}{\xi}\sin^2\theta+2\cos^2\theta} \\
&= V_G \sqrt{\pi}.
\end{aligned}$$

这和直接计算 $S$ 的全平面积分得到的结果一致.

> 在我们的例子中, 最后的作用量还获得了一个意外的 $\mathrm{SO}(2)$ 对称性, 但这只是因为我们选取了一个方便计算的 $S$.
{: .prompt-tip }

### Nakanishi-Lautrup 辅助场

我们的操作相当于在作用量上乘了一项高斯项, 这一项人为地破坏了规范对称性, 因此相当于等价地选定了一个规范条件. 这一项可以被转化成一个辅助场的高斯积分, 注意到

$$\mathrm{e}^{-\frac{1}{2\xi}(r\sin\theta)^2} = \sqrt{\frac{\xi}{2\pi}} \int \mathrm{d}\omega\, \mathrm{e}^{-\frac{\xi}{2}\omega^2 +\omega\cdot r\sin\theta},$$

于是配分函数可以变成

$$Z = V_G \frac{1}{2\pi} \int r\mathrm{d}r\mathrm{d}\theta\,\mathrm{d}\omega\,\exp\left\{-\left(L(r,\theta) + \frac{\xi}{2}\omega^2 - \omega\cdot r\sin\theta\right)\right\},$$

其中 $\omega$ 就是一个具有动力学的辅助场, 它有助于 BRST 算符的构造.

## 鬼场

让我们换一种方式思考我们的构造, 事实上我们的作用量还存在一种等价但又有一些不同的规范变换[^gauge], 即 $y\mapsto y+\alpha x$. 这启发我们插入一个略微不同的规范固定

$$1 = \Delta_{FP} \int\mathrm{d}\alpha\, \delta(r\sin\theta + \alpha\, r\cos\theta),$$

其中 $\Delta_{FP} = \left\|\frac{\partial}{\partial\alpha}(r\sin\theta + \alpha\, r\cos\theta)\right\| = \|r\cos\theta\|$ 称为 Faddeev-Popov 行列式[^determinant].

把这个规范固定插入配分函数中就会得到

$$Z = \int r\mathrm{d}r\mathrm{d}\theta\, \Delta_{FP}\int\mathrm{d}\alpha\, \delta(r\sin\theta+\alpha\, r\cos\theta) S(r,\theta).$$

出于和之前相同的论证, $\alpha$ 的积分可以被提出来, 得到规范群体积 $V_G$. 同时我们可以用上一节相同的办法处理 $\delta$ 函数. 于是配分函数就可以写为

$$Z = \frac{V_G}{\sqrt{2\pi\xi}} \int r\mathrm{d}r\mathrm{d}\theta\, \Delta_{FP}\, \mathrm{e}^{-\frac{1}{2\xi}r^2\sin^2\theta} S(r,\theta),$$

但此时 $\Delta_{FP}$ 不是一个能被提到积分号外的常数. 为了解决这个问题, 我们利用如下 Grassmann 数的高斯积分公式

$$\Delta = \int\mathrm{d}c\mathrm{d}\bar{c}\, \mathrm{e}^{-c\Delta\bar{c}},$$

其中 $c$ 和 $\bar{c}$ 都是反对易的 Grassmann 数. 于是我们最终获得了如下的配分函数

$$Z = \frac{V_G}{\sqrt{2\pi\xi}} \int r\mathrm{d}r\mathrm{d}\theta\,\mathrm{d}c\mathrm{d}\bar{c}\, \exp\left\{-\left(L(r,\theta) + \frac{1}{2\xi}r^2\sin^2\theta + c\bar{c}\, |r\cos\theta|\right)\right\}.$$

我们会发现, 这里相当于引入了一对费米子场 (反对易场) $c$ 和 $\bar{c}$. 尽管它们有动力学, 但它们只是来自求解过程中的数学技巧, 因此它们应当是非物理的. 这一对费米子场称为鬼场.

## 脚注

[^action]: 这里的作用量与平时的定义略有不同.
[^gauge]: 这个规范变换会把问题大大复杂化, 我们使用它只是为了展示鬼场是怎么出现并且和物理场耦合的. 在通常的非阿贝尔规范理论中鬼场的出现比这里自然很多.
[^determinant]: 如果是一个更高维的版本 $\int\mathrm{d}\vec{\alpha}\,\delta(F_{\vec{\alpha}}(\vec{v}))$, 那这里的 $\Delta_{FP}$ 就是 $\|\partial F/\partial\vec{\alpha}\|$ 的雅可比行列式. 这就是为什么它称为 **行列式**. 这时我们只需要用高维的 Grassmann 数高斯积分公式就能得到对应的鬼场构造.