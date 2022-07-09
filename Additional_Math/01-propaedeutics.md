# 高数预备知识
---
## 函数概念和特性

- 函数 $y = f(x)$
- 反函数 $y = f^{-1}(x)$
- 复合函数 $y = f[g(x)]$
- 函数四种特性：
  - 有界性
  - 单调性
  - 奇偶性
  - 周期性

> 重要结论
- 若 $f(x)$ 是可导的偶函数，则 $f^{\prime}(x)$ 是奇函数 
- 若 $f(x)$ 是可导的奇函数，则 $f^{\prime}(x)$ 是偶函数
- 若 $f(x)$ 是可导的周期为 $T$ 的周期函数，则 $f^{\prime}(x)$ 也是以 $T$ 为周期的周期函数
- 连续的奇函数的一切原函数都是偶函数
- 连续的偶函数的原函数中仅有一个是奇函数
- 若连续函数 $f(x)$ 以为 $T$ 为周期且 $\displaystyle \int_{0}^{T} f(x) \mathrm{d} x=0$，则 $f(x)$ 的一切原函数也以 $T$ 为周期
- 若 $f(x)$ 在 $(a,b)$ 内可导且 $f^{\prime}(x)$ 有界，则 $f(x)$ 在 $(a,b)$ 内有界
---
## 常用基础知识

### 数列
> 等差数列

$\text { 首项为 } a_{1} \text {, 公差为 } d(d \neq 0) \text { 的数列 } a_{1}, a_{1}+d, a_{1}+2 d, \cdots, a_{1}+(n-1) d, \cdots \text {. }$
- 通项公式：$a_{n}=a_{1}+(n-1) d$
- 前 $n$ 项和：$\displaystyle S_{n}=\frac{n}{2}\left[2 a_{1}+(n-1) d\right]=\frac{n}{2}\left(a_{1}+a_{n}\right)$

> 等比数列

$\text { 首项为 } a_{1} \text {, 公比为 } r(r \neq 0) \text { 的数列 } a_{1}, a_{1} r, a_{1} r^{2}, \cdots, a_{1} r^{n-1}, \cdots \text {. }$
- 通项公式：$a_{n}=a_{1} r^{n-1}$
- 前 $n$ 项和：$\displaystyle S_{n}= \begin{cases}n a_{1}, & r=1 \\ \displaystyle \frac{a_{1}\left(1-r^{n}\right)}{1-r}, & r \neq 1\end{cases}$
- 常用：$\displaystyle 1+r+r^{2}+\cdots+r^{n-1}=\frac{1-r^{n}}{1-r}(r \neq 1)$

> 常见数列前 $n$ 项和
> - $\displaystyle \sum_{k=1}^{n} k=1+2+3+\cdots+n=\frac{n(n+1)}{2}$
> - $\displaystyle \sum_{k=1}^{n} k^{2}=1^{2}+2^{2}+3^{2}+\cdots+n^{2}=\frac{n(n+1)(2 n+1)}{6}$
> - $\displaystyle \sum_{k=1}^{n} \frac{1}{k(k+1)}=\frac{1}{1 \times 2}+\frac{1}{2 \times 3}+\frac{1}{3 \times 4}+\cdots+\frac{1}{n(n+1)}=\frac{n}{n+1}$

### 三角函数
> 三角函数的基本关系

$$
\begin{array}{l}
\displaystyle 
\csc \alpha=\frac{1}{\sin \alpha}, \quad \sec \alpha=\frac{1}{\cos \alpha}, \quad \cot \alpha=\frac{1}{\tan \alpha}, \quad \tan \alpha=\frac{\sin \alpha}{\cos \alpha}, \quad \cot \alpha=\frac{\cos \alpha}{\sin \alpha},
\end{array}
$$
$$
\begin{array}{l}
\displaystyle 
\sin ^{2} \alpha+\cos ^{2} \alpha=1, \quad 1+\tan ^{2} \alpha=\sec ^{2} \alpha, \quad 1+\cot ^{2} \alpha=\csc ^{2} \alpha
\end{array}
$$

> 诱导公式
> 如下表所示，*奇变偶不变，符号看象限*

![诱导公式.png](https://s2.loli.net/2022/07/08/oLv7birsmk8SnY4.png)

> 常用重要公式

- 倍角公式

$$
\begin{array}{l}
\sin 2 \alpha=2 \sin \alpha \cos \alpha, \quad \cos 2 \alpha=\cos ^{2} \alpha-\sin ^{2} \alpha=1-2 \sin ^{2} \alpha=2 \cos ^{2} \alpha-1 \\
\sin 3 \alpha=-4 \sin ^{3} \alpha+3 \sin \alpha, \quad \cos 3 \alpha=4 \cos ^{3} \alpha-3 \cos \alpha \\
\displaystyle 
\tan 2 \alpha=\frac{2 \tan \alpha}{1-\tan ^{2} \alpha}, \quad \cot 2 \alpha=\frac{\cot ^{2} \alpha-1}{2 \cot \alpha}
\end{array}
$$

- 半角公式

$$
\sin ^{2} \frac{\alpha}{2} = \frac{1}{2}(1-\cos \alpha), \quad \cos ^{2} \frac{\alpha}{2} = \frac{1}{2}(1+\cos \alpha) , (降幂公式)  \\
 \sin \frac{\alpha}{2} = \pm \sqrt{\frac{1-\cos \alpha}{2}}, \quad \cos \frac{\alpha}{2} = \pm \sqrt{\frac{1+\cos \alpha}{2}} ,\\
 \tan \frac{\alpha}{2} = \frac{1-\cos \alpha}{\sin \alpha} = \frac{\sin \alpha}{1+\cos \alpha} = \pm \sqrt{\frac{1-\cos \alpha}{1+\cos \alpha}} \\ 
\\
\cot \frac{\alpha}{2} = \frac{\sin \alpha}{1-\cos \alpha} = \frac{1+\cos \alpha}{\sin \alpha} = \pm \sqrt{\frac{1+\cos \alpha}{1-\cos \alpha}}
$$

- 和差公式

$$
\begin{array}{l}
\displaystyle 
\sin (\alpha \pm \beta)=\sin \alpha \cos \beta \pm \cos \alpha \sin \beta, \quad \cos (\alpha \pm \beta)=\cos \alpha \cos \beta \mp \sin \alpha \sin \beta \\ \displaystyle 
\tan (\alpha \pm \beta)=\frac{\tan \alpha \pm \tan \beta}{1 \mp \tan \alpha \tan \beta}, \quad \cot (\alpha \pm \beta)=\frac{\cot \alpha \cot \beta \mp 1}{\cot \beta \pm \cot \alpha}
\end{array}
$$

- 积化和差 & 和差化积
  - 积化和差
  $$\begin{cases}
    \displaystyle \sin \alpha \cos \beta=\frac{1}{2}[\sin (\alpha+\beta)+\sin (\alpha-\beta)]\\ \\
    \displaystyle \cos \alpha \sin \beta=\frac{1}{2}[\sin (\alpha+\beta)-\sin (\alpha-\beta)] \\ \\
    \displaystyle \cos \alpha \cos \beta=\frac{1}{2}[\cos (\alpha+\beta)+\cos (\alpha-\beta)]\\ \\ 
    \displaystyle \sin \alpha \sin \beta=\frac{1}{2}[\cos (\alpha-\beta)-\cos (\alpha+\beta)] 
  \end{cases}$$
  - 和差化积
  $$\begin{cases}
    \displaystyle  \sin \alpha+\sin \beta=2 \sin \frac{\alpha+\beta}{2} \cos \frac{\alpha-\beta}{2}\\ \\
    \displaystyle \sin \alpha-\sin \beta=2 \sin \frac{\alpha-\beta}{2} \cos \frac{\alpha+\beta}{2} \\ \\
    \displaystyle \cos \alpha+\cos \beta=2 \cos \frac{\alpha+\beta}{2} \cos \frac{\alpha-\beta}{2}\\ \\
    \displaystyle \cos \alpha-\cos \beta=-2 \sin \frac{\alpha+\beta}{2} \sin \frac{\alpha-\beta}{2}
  \end{cases}$$

- 万能公式

$$
\text { 若 } u=\tan \frac{x}{2}(-\pi<x<\pi) \text {, 则 } \sin x=\frac{2 u}{1+u^{2}}, \cos x=\frac{1-u^{2}}{1+u^{2}} \text {. }
$$

### 指数运算
$$
a^{\alpha} \cdot a^{\beta}=a^{a+\beta}, \quad \frac{a^{\alpha}}{a^{\beta}}=a^{\alpha-\beta}, \quad\left(a^{\alpha}\right)^{\beta}=a^{\alpha \beta}, \quad(a b)^{\alpha}=a^{\alpha} b^{\alpha}, \quad\left(\frac{a}{b}\right)^{\alpha}=\frac{a^{\alpha}}{b^{\alpha}}
$$
其中 $a,b$ 是正实数，$\alpha,\beta$ 是任意实数

### 对数运算
$$
\log _{a}(M N)=\log _{a} M+\log _{a} N, \quad \log _{a} \frac{M}{N}=\log _{a} M-\log _{a} N \\
\log _{a} M^{n}=n \log _{a} M, \quad \log _{a} \sqrt[n]{M}=\frac{1}{n} \log _{a} M .
$$
> 常用
> - $\displaystyle \ln \sqrt{x}=\frac{1}{2} \ln x $
> - $\displaystyle \ln \frac{1}{x}=-\ln x$
> - $\displaystyle \ln \left(1+\frac{1}{x}\right)=\ln \frac{x+1}{x}=\ln (x+1)-\ln x$

### 一元二次方程
- 一元二次方程 $a x^{2}+b x+c=0(a \neq 0)$
- 方程的根 $\displaystyle z=\frac{-b \pm \sqrt{b^{2}-4 a c}}{2 a}$
- 韦达定理 $\displaystyle x_1+x_2=-\frac{b}{a},x_1x_2=\frac{c}{a}$
- 判别式 $\Delta = b^{2}-4ac$
  - $\Delta>0$，方程有两个不相等的实根
  - $\Delta=0$，方程有两个相等的实根
  - $\Delta<0$，方程有两个共轭的复根
- 抛物线 $y = a x^{2}+b x+c=0$ 的顶点 $\displaystyle (-\frac{b}{2a},c-\frac{b^{2}}{4a})$

### 因式分解公式
$
①\ (a\pm b)^{2} = a^{2}\pm 2 a b+b^{2} \\
②\ (a+b)^{3} = a^{3}\pm 3 a^{2} b+3 a b^{2}\pm b^{3} \\
③\ a^{2}-b^{2} = (a+b)(a-b) \\
④\ a^{3}\pm b^{3} = (a\pm b)\left(a^{2}\mp a b+b^{2}\right) \\
⑤\ a^{n}-b^{n} = (a-b)\left(a^{n-1}+a^{n-2} b+\cdots+a b^{n-2}+b^{n-1}\right) \text{(n为正整数)} \\
⑥\ \text{n  是正偶数时},  a^{n}-b^{n} = (a+b)\left(a^{n-1}-a^{n-2} b+\cdots+a b^{n-2}-b^{n-1}\right) \\
⑦\ \text{n  是正奇数时},  a^{n}+b^{n} = (a+b)\left(a^{n-1}-a^{n-2} b+\cdots-a b^{n-2}+b^{n-1}\right) \\
⑧\ \text{二项式定理：}
$
$$
\begin{aligned}
(a+b)^{n} = \sum_{k = 0}^{n} \mathrm{C}_{n}^{k} a^{n-k} b^{k} =& a^{n}+n a^{n-1} b+\frac{n(n-1)}{2 !} a^{n-2} b^{2}+\cdots+\\
& \frac{n(n-1) \cdots(n-k+1)}{k !} a^{n-k} b^{k}+\cdots+n a b^{n-1}+b^{n} .
\end{aligned}
$$

### 阶乘与双阶乘
- $n !=1 \cdot 2 \cdot 3 \cdots \cdots \cdot n$，规定 $0 !=1$
- $(2 n) ! !=2 \cdot 4 \cdot 6 \cdot \cdots \cdot(2 n)=2^{n} \cdot n !$
- $(2n-1)!! = 1 \cdot 3 \cdot 5 \cdot \cdots \cdot (2n-1)$

### 常用不等式
- 设 $a,b$ 为实数，则
  - $|a\pm b| \le |a|+|b|$
  - $||a|-|b|| \le |a-b|$
  - 推广：设 $f(x)$ 在 $[a,b](a<b)$ 上可积，则 $\displaystyle |\int_a^{b}f(x)\mathrm{d}x| \le \int_a^{b}|f(x)|\mathrm{d}x$
- \
  - $\displaystyle \sqrt{a b} \leqslant \frac{a+b}{2} \leqslant \sqrt{\frac{a^{2}+b^{2}}{2}}(a, b>0)$
  - $\displaystyle \sqrt[3]{a b c} \leqslant \frac{a+b+c}{3} \leqslant \sqrt{\frac{a^{2}+b^{2}+c^{2}}{3}}(a, b, c>0)$
- 设 $a>b>0$，则 $\displaystyle \{\begin{array}{l}\text { 当 } n>0 \text { 时, } a^{n}>b^{n} \text {, } \\ \text { 当 } n<0 \text { 时, } a^{n}<b^{n} \text {. }\end{array}$
- 若 $0<a<x<b, 0<c<y<d$，则 $\displaystyle \frac{c}{b}<\frac{y}{x}<\frac{d}{a}$
- $\displaystyle \sin x<x<\tan x\left(0<x<\frac{\pi}{2}\right)$
- $\sin x<x(x>0)$
  - 当 $x_{n}>0$ 时，$x_{n+1}=\sin x_n < x_n$，故 $\{ x_n \}$ 单调递减
- $\arctan x \leqslant x \leqslant \arcsin x(0 \leqslant x \leqslant 1)$
- $\mathrm{e}^{x} \geqslant x+1(\forall x)$
- $x-1 \geqslant \ln x(x>0)$
- $\displaystyle \frac{1}{1+x}<\ln \left(1+\frac{1}{x}\right)<\frac{1}{x}(x>0)$