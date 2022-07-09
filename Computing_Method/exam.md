# 数值分析
说明：考试迫使记的:sob: 都是公式而已，没有公式说明,没有推导过程，懂自懂
# 1、误差
- $x^{*}$ 为 $x$ 一个近似值
- 绝对误差：$e^{*} = x^{*} - x$
- 相对误差：$\displaystyle e_r^{*} = \frac{e^{*}}{x} = \frac{x^{*} - x}{x}$，由于真值 $x$ 总是不知道的，通常取 $\displaystyle e_r^{*} = \frac{e^{*}}{x^{*}} = \frac{x^{*} - x}{x^{*}}$
- 误差限：$|x^{*} - x| \le \varepsilon^{*}$
- 相对误差限：$\varepsilon_r^{*} = \displaystyle \frac{\varepsilon^{*}}{|x^{*}|}$
- $\varepsilon(f(x^{*})) \approx |f^{'}(x^{*})|\varepsilon(x^{*})$

# 2、插值法

- 记 $\omega_{n+1}(x) = (x-x_{0})(x-x_1)\cdots (x-x_n)$
- $Lagrange$ 插值多项式系数：$$ l_k(x_k) = \displaystyle \frac{(x-x_0)\cdots (x-x_{k-1})(x-x_{k+1})\cdots (x-x_n)}{(x_k-x_0)\cdots (x_k-x_{k-1})(x-x_{k+1})\cdots (x-x_n)} $$
- $Lagrange$ 插值多项式：$$ L_n(x) = \displaystyle \sum_{k=0}^{n} l_k(x)y_k = \sum_{k=0}^{n} y_k \frac{\omega_{n+1}(x)}{\omega^{'}_{n+1}(x_k)(x-x_k)} $$
- 余项：记 $M_{n+1} =\displaystyle  \max_{a\le x\le b}|f^{n+1}(x)|$ $$ \displaystyle R(x) = \frac{f^{n+1}(\xi)\omega_{n+1}(x)}{(n+1)!} \le \frac{M_{n+1}}{(n+1)!}|\omega_{n+1}(x)| $$

## 均差与 *NewTon* 插值多项式
- 一阶均差：$\displaystyle f[x_0, x_k] = \frac{f(x_k) - f(x_0)}{x_k-x_0}$
- $k$ 阶均差：$$ f[x_0,x_1,\cdots ,x_k] = \frac{f[x_0,\cdots ,x_{k-2},x_k] - f[x_0,\cdots ,x_{k-2},x_{k-1}]}{x_k - x_{k-1}} $$
- $\displaystyle f[x_0,x_1,\cdots ,x_n] = \frac{f^{(n)}(\xi)}{n!} \qquad (x_0,x_1,\cdots ,x_n,\xi \in [a,b])$
- $\displaystyle f[x_0,x_1,\cdots ,x_k] = \sum_{j=0}^{k}\frac{f(x_j)}{\omega_{k+1}^{'}(x_j)}$
- $NewTon$ 插值多项式：$$ P_n(x) = f(x_0)+f[x_0,x_1](x-x_0)+f[x_0,x_1,x_2](x-x_0)(x-x_1)+\cdots \\ +f[x_0,x_1,\cdots ,x_n](x-x_0)(x-x_1)\cdots (x-x_{n-1}) $$
- 余项：$R(x) = f[x_0,x_1,\cdots ,x_n]\omega_{n+1}(x)$

## *Hermite* 插值
- $Taylor$ 多项式：$$ \displaystyle P_n(x) = f(x_0) + f^{'}(x_0)(x-x_0) + \cdots + \frac{f^{(n)}(x_0)}{n!}(x-x_0)^{n}$$
  - 余项：$\displaystyle R(x) = \frac{f^{(n+1)}(\xi)}{(n+1)!}(x-x_0)^{n+1}$
- 若已知 $f(x_0),f^{'}(x_1),f(x_1),f(x_2)$：$$ P(x) = f(x_0) + f[x_0,x_1](x-x_0) + f[x_0,x_1,x_2](x-x_0)(x-x_1) \\ + A(x-x_0)(x-x_1)(x-x_2) $$ 其中 $A$ 由 $P^{'}(x_1) = f^{'}(x_1)$ 可得
  - 余项：$$ R(x) = \frac{1}{4!}f^{(4)}(\xi)(x-x_0)(x-x_1)^{2}(x-x_2) $$
- 两点三次 $Hermite$ 插值多项式：$$ H_3(x) = \alpha_k(x)y_k + \alpha_{k+1}(x)y_{k+1} + \beta_k(x)m_k + \beta_{k+1}(x)m_{k+1} $$ 其中 $m_k = f^{'}(x_k), m_{k+1} = f^{'}(x_{k+1})$
$$
\begin{cases}
\displaystyle 
    \alpha_k(x) = (1+2\frac{x-x_k}{x_{k+1}-x_k})(\frac{x-x_{k+1}}{x_k-x_{k+1}})^{2} \\
\\ \displaystyle
    \alpha_{k+1}(x) = (1+2\frac{x-x_{k+1}}{x_k-x_{k+1}})(\frac{x-x_k}{x_{k+1}-x_k})^{2} \\
\end{cases}
$$
$$
\begin{cases}
\displaystyle 
    \beta_k(x) = (x-x_k)(\frac{x-x_{k+1}}{x_k-x_{k+1}})^{2} \\
\\ \displaystyle 
    \beta_{k+1}(x) = (x-x_{k+1})(\frac{x-x_k}{x_{k+1}-x_k})^{2} \\
\end{cases}
$$
  - 余项：$$ \displaystyle R(x) = \frac{f^{(4)}(\xi)}{4!}(x-x_k)^{2}(x-x_{k+1})^{2} $$

## 分段低次插值
- $\displaystyle h = \frac{b-a}{n}$
- 对每个小区间使用对应插值公式求 $I_h(x)$
- 余项
  - 对分段线性插值函数：$$ \max_{a\le x\le b}|f(x) - I_h(x)| \le \frac{M_2}{8}h^{2} $$
  - 对分段三次埃尔米特插值：$$ \max_{a\le x\le b}|f(x) - I_h(x)| \le \frac{M_4}{384}h^{4} $$

# 3、数值积分
## 代数精度
定义：
- 如果某个求积公式对于次数不超过 $m$ 的多项式均能够准确成立，但对于 $m+1$ 次多项式就不准确成立，则称该公式具有 **$m$ 次代数精度**

## 梯形公式公式与中矩形公式
- 梯形公式：$$ \displaystyle \int_{a}^{b}f(x)dx \approx \frac{b-a}{2}f(a) + \frac{b-a}{2}f(b) $$
  - 余项：$$ \displaystyle R[f] = -\frac{(b-a)^{3}}{12}f^{''}(\eta)\qquad (\eta \in (a,b)) $$
- 矩形公式：$$ \displaystyle \int_{a}^{b}f(x)dx \approx (b-a)f(\frac{a+b}{2}) $$
  - 余项：$$ \displaystyle R[f] = \frac{(b-a)^{3}}{24}f^{''}(\eta)\qquad (\eta \in (a,b)) $$

## *Newton-Cotes* 公式
将积分区间 $[a,b]$ 分成 $n$ 等分
- $Simpson$ 公式（$n=2$）：$$ \displaystyle \int_{a}^{b}f(x)dx \approx \frac{b-a}{6}f(a) + \frac{b-a}{6}f(b) + \frac{2(b-a)}{3}f(\frac{a+b}{2}) $$
  - 余项：$$ R[f] = -\frac{(b-a)^{5}}{180*2^{4}}f^{(4)}(\eta)\qquad (\eta \in (a,b)) $$
- $Cotes$ 公式（$n=4$）：$$C = \frac{b-a}{90}[7f(x_0)+32f(x_1)+12f(x_2)+32f(x_3)+7f(x_4)]$$
  - 余项：$$ R[f] = -\frac{2(b-a)^{7}}{945*4^{6}}f^{(6)}(\eta)\qquad (\eta \in (a,b)) $$

## 复合求积公式

积分区间 $[a,b]$ 分成 $n$ 等分，步长 $\displaystyle h = \frac{b-a}{n}$
- 复合梯形公式：$$ T_n = \frac{h}{2}[f(a)+2\sum_{k=0}^{n-1}f(x_k)+f(b)] $$
  - 余项：$$ R_n(f) = -\frac{b-a}{12}h^{2}f^{''}(\eta) $$
- 复合 $Simpson$ 求积公式：$$ S_n = \frac{h}{6}[f(a)+2\sum_{k=0}^{n-1}f(x_k)+4\sum_{k=1}^{n-2}f(x_{(k+1)/2})+f(b)] $$ 其中 $\displaystyle x_{(k+1)/2} = x_k+\frac{h}{2}$
  - 余项：$$ R_n(f) = -\frac{b-a}{180}(\frac{h}{2})^{4}f^{(4)}(\eta) $$

## 龙贝格求积算法
- $T_0^{(0)} = \displaystyle \frac{h}{2}[f(a)+f(b)]$
- 求梯形值 $\displaystyle T_0(\frac{b-a}{2^{k}})$，利用递推公式求 $T_0^{(k)}$，递推公式：$$ \displaystyle T_{2n} = \frac{1}{2}T_n + \frac{h}{2}\sum_{k=0}^{n-1}f(x_{k+\frac{1}{2}}) $$
- 求加速值：$$ T_m^{(k)} = \frac{4^{m}}{4^{m}-1}T_{m-1}^{k+1} - \frac{1}{4^{m}-1}T_{m-1}^{(k)} \qquad k = 1,2,\cdots $$

## 高斯-勒让德求积公式
- 积分区间为 $[-1,1]$
- $\displaystyle \int_{-1}^{1}f(x)dx \approx \sum_{k=0}^{n}A_kf(x_k)$
- 余项：$n=1$ 时，$\displaystyle  R_1[f] = \frac{1}{135}f^{(4)}(\eta) $

# 4、解线性方程组的直接方法
## 列主元高斯消去法
- 在每次消元时，选取列主元在最前面，列主元为该列最大值

## 矩阵三角分解法
- 如果 $n$ 阶矩阵 $A$ 的各阶顺序主子式 $D_k \left( k = 1,2,\cdots ,n-1 \right)$ 均不为零，则必有单位下三角矩阵 $L$ 和上三角矩阵 $U$，使得 $A = LU$，并且 $L$ 和 $U$ 是唯一的。
- 对矩阵进行 $LU$ 分解后（杜利特尔分解）
  - 解 $Ly = b$ 得到 $y$
  - 解 $Ux = y$ 得到 $x$

## 矩阵范数
- 行范数：$\displaystyle ||A||_{\infty} = \max_{1 \le i \le n}\sum_{j=1}^{n}|a_{ij}|$
- 列范数：$\displaystyle ||A||_{1} = \max_{1 \le j \le n}\sum_{i=1}^{n}|a_{ij}|$
- 2- 范数：$\displaystyle ||A||_{2} = \sqrt{\lambda_{max}(A^{T}A)}$ ，其中 $\lambda_{max}(A^{T}A)$ 表示 $A^{T}A$ 的最大特征值
  - 特征值计算：$|\lambda E - A| = 0$，解得 $\lambda$ 即为 $A$ 的特征值
- F- 范数：$\displaystyle ||A||_F = \sqrt{\sum_{i=1,j=1}^{n}(a_{ij})^{2}}$

## 条件数
- $cond(A)_{\infty} = ||A^{-1}||_{\infty}||A||_{\infty}$
- $A$ 的谱条件数 $$ cond(A)_{2} = ||A||_2||A^{-1}||_2 = \sqrt{\frac{\lambda_{max}(A^{T}A)}{\lambda_{min}(A^{T}A)}}$$
  - 当 $A$ 为对称矩阵时，$$ cond(A)_2 = \frac{|\lambda_1|}{|\lambda_n|} $$ 其中，$\lambda_1$ 和 $\lambda_n$ 分别代表 $A$ 绝对值最大和绝对值最小的特征值

# 5、解线性方程组的迭代方法
- $Jacobi$ 迭代 
$$ 
\begin{cases}
  \displaystyle x_1^{(k+1)} = \frac{1}{a_{11}}(-a_{12}x_2^{(k)}-a_{13}x_3^{(k)}\cdots -a_{1n}x_n^{(k)}+b_1) \\
  \\ \displaystyle x_2^{(k+1)} = \frac{1}{a_{22}}(-a_{21}x_1^{(k)}-a_{23}x_3^{(k)}\cdots -a_{2n}x_n^{(k)}+b_2) \\
  \cdots \\
  \displaystyle x_n^{(k+1)} = \frac{1}{a_{nn}}(-a_{n1}x_1^{(k)}-a_{n2}x_2^{(k)}\cdots -a_{n(n-1)}x_{n-1}^{(k)}+b_n) \\
\end{cases} $$
- $Gauss-Seidel$ 迭代
$$
\begin{cases}
  \displaystyle x_1^{(k+1)} = \frac{1}{a_{11}}(-a_{12}x_2^{(k)}-a_{13}x_3^{(k)}\cdots -a_{1n}x_n^{(k)}+b_1) \\
  \\ \displaystyle x_2^{(k+1)} = \frac{1}{a_{22}}(-a_{21}x_1^{(k+1)}-a_{23}x_3^{(k)}\cdots -a_{2n}x_n^{(k)}+b_2) \\
  \cdots \\
  \displaystyle x_n^{(k+1)} = \frac{1}{a_{nn}}(-a_{n1}x_1^{(k+1)}-a_{n2}x_2^{(k+1)}\cdots -a_{n(n-1)}x_{n-1}^{(k+1)}+b_n) \\
\end{cases}
$$
- 收敛性：
  - 若 $A$ 严格对角占有，即 $\displaystyle |a_{ii}| > \sum_{j=0}^{i-1}|a_{ij}| + \sum_{j=i+1}^{n}|a_{ij}|$，则两种迭代方法均收敛
  - 迭代法 $x^{(k+1)} = Bx^{(k)}+f$ 对任意 $x^{(0)}$ 和 $f$ 均收敛的充要条件为 $\rho(B) < 1$。其中 $B$ 为迭代矩阵，谱半径 $\rho(B)$ 为矩阵 $B$ 特征值的模的最大值。
  - 矩阵的谱半径越小，收敛速度越快

# 6、非线性方程和方程组的数值解法
## 二分法
计算步骤：
1. **准备**：计算 $f(x)$ 在有根区间 $[a,b]$ 端点处的值 $f(a),f(b)$
2. **二分**：计算 $f(x)$ 在区间中点 $\displaystyle \frac{a+b}{2}$ 处的值 $\displaystyle f(\frac{a+b}{2})$
3. **判断**：若 $\displaystyle f(\frac{a+b}{2}) = 0$，则 $\displaystyle x = \frac{a+b}{2}$ 即为方程的根，计算过程结束，否则检验：若 $\displaystyle f(\frac{a+b}{2})f(a) < 0$，则 $\displaystyle b = \frac{a+b}{2}$，否则 $\displaystyle a = \frac{a+b}{2}$
4. 反复执行步骤 2-3，直到区间 $[a,b]$ 的长度小于允许误差 $\varepsilon$，此时区间中点 $\displaystyle \frac{a+b}{2}$ 即为所求近似根

二分法总是收敛的

## 不动点迭代
计算步骤：
- 将方程 $f(x)=0$ 转换为 $x=\varphi(x)$
- 要求 $x^{*}$ 满足 $f(x^{*})=0$，则 $x^{*} = \varphi(x^{*})$，称 $x^{*}$ 为函数 $\varphi(x)$ 的一个不动点
- 选择一个初始近似值 $x_0$，将其代入 $x = \varphi(x)$ 式的右端可求得 $x_1 = \varphi(x_0)$
- 如上迭代计算 $x_{k+1} = \varphi(x_k)$，$\varphi(x)$ 称为迭代函数

收敛性：
- 若 $x^{*}$ 为 $\varphi(x)$ 的不动点，$\varphi(x)$ 在 $x^{*}$ 某领域内有连续导数，且 $\varphi(x^{*}) < 1$，则该迭代法是局部收敛的。

收敛阶：
- 若迭代函数 $x=\varphi(x)$ 的根 $x^{*}$ 邻近具有 $p$ 阶连续导数，并且有 $$ \varphi^{'}(x^{*}) = \varphi^{''}(x^{*}) = \cdots =\varphi^{(p-1)}(x^{*}) ,\ \varphi^{(p)}(x^{*}) \neq 0$$ 那么迭代过程在 $x^{*}$ 附近是 $p$ 阶收敛的
  - 若 $0<\varphi^{'}(x^{*})<1$，则迭代法 **线性收敛**
  - 若 $\varphi^{'}(x^{*})=0,\ \varphi^{''}(x^{*}) \neq 0$，则迭代法 **平方收敛**

## *Newton* 法
- $Newton$ 迭代法的构造：
$$
x_{k+1} = x_k - \frac{f(x_k)}{f'(x_k)}
$$
- 牛顿法是 **平方收敛** 的

### 简化牛顿法
构造迭代公式：
$$
x_{k+1} = x_k-\frac{f(x_k)}{f^{'}(x_0)}
$$
只有一阶收敛

### 牛顿下山法
构造迭代公式：
$$
x_{k+1} = x_k - \lambda \frac{f(x_k)}{f^{'}(x_k)}
$$
可以通过选取 $\lambda$ 值使得 $|f(x_k)| > |f(x_{k+1})|$，通常先令 $\lambda=1$，若上式子不成立则 $\lambda$ 减半，直到上式成立

### 重根情况
若 $f(x) = (x-x^{*})^{m}g(x)$，即 $x^{*}$ 为方程 $m$ 重根，在无需提前知道 $m$ 取值的情况下，可构造平方收敛的 迭代公式
$$
x_{k+1} = x_k - \frac{f(x_k)f^{'}(x_k)}{[f^{'}(x_k)]^{2}-f(x_k)f^{''}(x_k)}
$$