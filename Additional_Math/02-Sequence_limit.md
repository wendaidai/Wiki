# 数列极限
---
## 定义
设 $\{ x_n \}$ 为一数列，若存在常数 $a$，对于任意的 $\varepsilon>0$，总存在正整数 $N$，使得当 $n<N$ 时，$|x_n-a|<\varepsilon$ 恒成立，则称数 $a$ 是数列 $\{x_n\}$ 的极限，或者称数列 $\{x_n\}$ 收敛于 $a$，记为
$$
\lim_{x\to \infty}x_n=a \text{或}x_n\to a(n\to \infty)
$$
若不存在这样的常数 $a$，则称数列 $\{x_n\}$ 是发散的
$$
\lim _{n \rightarrow \infty} x_{n}=a \Leftrightarrow \forall \varepsilon>0, \exists N \in \mathbf{N}_{+} \text {, 当 } n>N \text { 时,恒有 }\left|x_{n}-a\right|<\varepsilon \text {. }
$$
> **定理** 若数列 $\{a_n\}$ 收敛，则其任何子列 $\{a_{n_k}\}$ 也收敛，且 $\displaystyle \lim_{n \to \infty}a_n = \lim_{k \to \infty}a_{n_k}$

## 收敛数列的性质
- **唯一性**：对于数列 $\{x_n\}$，若 $\displaystyle \lim_{n \to \infty}x_n=a$ (存在)，则 $a$ 是唯一的
- **有界性**：若数列 $\{x_n\}$ 极限存在，则数列 $\{x_n\}$ 有界
- **保号性**：设数列 $\{x_n\}$ 存在极限 $a$，且 $a>0(\text{或}a<0)$，则存在正整数 $N$，当 $n<N$ 时，有 $x_n>0(\text{或}x_n<0)$
> **推论** 若数列 $\{x_n\}$ 从某项起有 $x_n\ge 0$，且 $\displaystyle \lim_{n \to \infty}x_n=a$，则 $a\ge 0$

## 极限运算规则
（运算规则可以推广至有限个数列的情况）
设  $\displaystyle \lim _{n \rightarrow \infty} x_{n}=a, \lim _{n \rightarrow \infty} y_{n}=b$ , 则
- $\displaystyle \lim _{n \rightarrow \infty}\left(x_{n} \pm y_{n}\right)=a \pm b$
- $\displaystyle \lim _{n \rightarrow \infty} x_{n} y_{n}=a b$
- 若 $\displaystyle b \neq 0, y_{n} \neq 0$ , 则 $\displaystyle \lim _{n \rightarrow \infty} \frac{x_{n}}{y_{n}}=\frac{a}{b}$

## 两个准则
> 夹逼准则
> 若数列 $\{ x_n \}$，$\{ y_n \}$ 和 $\{ z_n \}$ 满足下列条件
> $\displaystyle \text { (1) } y_{n} \leqslant x_{n} \leqslant z_{n}(n=1,2,3, \cdots) \text {; (2) } \lim _{n \rightarrow \infty} y_{n}=a, \lim _{n \rightarrow \infty} z_{n}=a \text {. }$
> 则数列 $\{ x_n \}$ 的极限存在，且 $\displaystyle \lim_{n \to \infty}x_n=a$

> 单调有界准则
> 单调有界数列必有极限，即若数列 $\{ x_n \}$ 单调递增（或递减）且有上界（或下界），则 $\displaystyle \lim_{n \to \infty}x_n$ 存在