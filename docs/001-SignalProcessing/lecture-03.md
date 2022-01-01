# Lecture 3

## 函数的正交分解

### 向量的正交分解

一组正交向量\(\mathbfit{e}_i\)满足以下条件：

\[
\mathbfit{e}_i^T\mathbfit{e}_j =
    \begin{cases}
        a^2, & i=j \\
        0,   & i\neq j
    \end{cases}
\]

其中若\(a=1\)，那么称之为**单位正交基**。

正交基的价值在于，若其为**完备的**，那么它们的线性组合可以表示线性空间内任意一个向量：

\[ \mathbfit{a} = \sum_{i=1}^{\infty} a_i\mathbfit{e}_i \]

完备性的形式化定义为：除了正交基内的向量外，不存在非零向量\(\mathbfit{v}\)满足

\[ \langle \mathbfit{v}, \mathbfit{e}_i \rangle = 0 \]

正交基的完备性依赖于线性空间的维数，即正交基内的向量个数与线性空间内的维数相同时，即可证明其为完备的。

同时我们也可以通过正交基的性质求出各个系数：

\[ a_i = \mathbfit{a}^T\mathbfit{e}_i \]

### 推广到函数上

由向量正交分解的启发，对于函数，应该也存在这样的分解方法：

\[ f(t) = \sum_{i=1}^{\infty}c_i\varphi_i(t) \]

事实上，我们已经接触到了一个广泛使用的正交分解方法，即泰勒展开：

\[ f(t) = \sum_{i=0}^{\infty}\frac{f^{(n)}(a)}{n!}(x-a)^n \]

若要建立相同的理论，我们需要函数空间的内积作为基础。我们定义实函数和复函数的内积分别为：

\[
\begin{align*}
\langle \varphi_i(t), \varphi_j(t) \rangle &= \int_{t_1}^{t_2} \varphi_i(t)\varphi_j(t) dt = 0, & \varphi_i(t), \varphi_j(t) \in \mathbb{R} \\
\langle \varphi_i(t), \varphi_j(t) \rangle &= \int_{t_1}^{t_2} \varphi_i(t)\varphi_j^*(t) dt = 0, &  \varphi_i(t), \varphi_j(t) \in \mathbb{C} \\
\end{align*}
\]

函数的模和正交的定义于向量中的相同。

所研究的线性空间为模收敛的函数集合，或平方可积函数集：

\[ L^2(R) = {f(t)|\int_{-\infty}^{\infty}f^2(t)dt < \infty} \]

正交函数集、标准正交函数集与完备正交函数集的定义都于向量中的类似。

### 函数的正交分解

当函数\(f(t)\)在\([t1,t2]\)区间具有连续的一阶导数和逐段连续的二阶导数时，\(f(t)\)可以用完备正交函数集\(\{\varphi_i(t)\}\)来表示，即：

\[ f(t) = \sum_{i=1}^{\infty} c_i\varphi_i(t) \]

则此称为函数的正交分解。其中\(c_i\)为常数，计算方法为：

\[ c_i = \frac{\langle f(t), \varphi_i(t) \rangle}{\langle \varphi_i(t), \varphi_i(t) \rangle} = \frac{1}{||\varphi_i(t)||^2} \langle f(t), \varphi_i(t) \rangle \]

### 帕斯瓦尔定理 (Parseval's theorem)

由函数正交分解：

\[ f(t) = \sum_{i=1}^{\infty} c_i\varphi_i(t) \]

可得：

\[ \int_{t_1}^{t_2}||f(t)||^2dt = \sum_{i=1}^{\infty} ||c_i||^2 k_i \]

其中：

\[ k_i = \langle \varphi_i(t), \varphi_i(t) \rangle = ||\varphi_i(t)||^2 \]

帕斯瓦尔定理表示了可积函数与其正交分解系数之间的关系。我们也可以发现，左式实际上为\(f(t)\)的能量函数，因此：

\[ E[f(t)] = \sum_{i=1}^{\infty} ||c_i||^2 k_i \]

## 傅立叶级数

### 周期信号的傅里叶级数

若正交展开使用的正交基为下面两种之一：

**三角函数集**

\[ \{\sin k\omega_0 t, \cos k\omega_0 t, 1|\: k = 1,2,\cdots\} \]

**虚指数函数集**

\[ \{ e^{jk\omega_0 t}|\: k=0,\pm 1, \pm 2, \cdots \} \]

那么称之为傅里叶级数展开，相应的级数被称为**三角形式傅里叶级数**和**指数形式傅里叶级数**。

要会证明这两个函数集确实是正交的。

### 狄利克雷条件

满足狄利克雷条件的**周期函数**都可以在一组正交基函数上展开为无穷级数。

狭义狄利克雷条件为：在一个周期内

1. 间断点个数有限
2. 极值点个数有限
3. 绝对积分收敛

### 三角形式傅里叶级数

设周期函数\(f(t)\)的周期为\(T\)，令角速度\(\omega_1=\frac{2\pi}{T}\)，那么三角形式傅里叶级数可以写为：

\[ f(t) = a_0 + \sum_{n=1}^{\infty}(a_n\cos n\omega_1 t+b_n\sin n\omega_1 t) \]

其中：

\[
\begin{align}
a_0 &= \frac{1}{T} \int_{t_0}^{t_0+T} f(t) dt \\
a_n &= \frac{2}{T} \int_{t_0}^{t_0+T} f(t) \cos n\omega_1 tdt \\
b_n &= \frac{2}{T} \int_{t_0}^{t_0+T} f(t) \sin n\omega_1 tdt \\
\end{align}
\]

注意积分区间为一个周期，而且\(a_n,b_n\)表达式中积分前的系数为\(2/T\)。

### 紧凑型三角形式傅里叶级数

\[ f(t) = c_0 + \sum_{n=1}^{\infty} c_n\cos(n\omega_1 t+\varphi_n) \]

其中：

\[
\begin{align}
a_0 &= c_0 \\
a_n &= c_n \cos \varphi_n \\
b_n &= -c_n \sin \varphi_n \\
c_n &= \sqrt{a_n^2+b_n^2} \\
\tan\varphi_n &= -\frac{b_n}{a_n}
\end{align}
\]

\(c_n,\varphi_n\)为\(n\)的函数，也即频率\(\omega=n\omega_1\)的函数，称其图形为频谱图。\(c_n\sim\omega\)的图像为振幅图，\(\varphi_n\sim\omega\)的图像为相位图。

### 奇偶信号的特例

奇信号不含余弦分量，偶函数不含正弦分量：

\[
\begin{align}
f(-t) = f(t) &\Rightarrow f(t) = a_0+\sum_{i=1}^{\infty}a_n\cos n\omega_1 t \\
f(-t) = -f(t) &\Rightarrow f(t) = \sum_{i=1}^{\infty}b_n\sin n\omega_1 t
\end{align}
\]

### 矩形脉冲信号的傅里叶级数

矩形脉冲信号为：

\[ f(t) = \begin{cases}
E, & kT-\frac{\tau}{2} < t < kT+\frac{\tau}{2} \\
0, & \text{otherwise}
\end{cases} \]

因为其为偶函数，因此\(b_n = 0\)。

\[ a_0 = \frac{1}{T}\int_{-T/2}^{T/2}f(t)dt = \frac{E\tau}{T} \]

\[ \begin{align}
a_n &= \frac{2}{T}\int_{-T/2}^{T/2}f(t)\cos n\omega_1tdt \\
&= \frac{2E}{T}\int_{-\tau/2}^{\tau/2}\cos n\omega_1tdt \\
&= \frac{2E}{T} \frac{2}{n\omega_1} \sin(\frac{n\omega_1\tau}{2}) \\
&= \frac{2E\tau}{T} \frac{\sin(\frac{n\omega_1\tau}{2})}{\frac{n\omega_1\tau}{2}} \\
&= \frac{2E\tau}{T} Sa(\frac{n\omega_1\tau}{2})
\end{align} \]

### 复指数形式傅里叶级数

由欧拉公式的推论可以从三角形式转化为复指数形式，最后简写为：

\[ f(t) = \sum_{n=-\infty}^{\infty} F_ne^{jn\omega_1 t} \]

其中系数为：

\[ F_n = \frac{1}{T_1}\int_{t_0}^{t_0+T_1}f(t)e^{-jn\omega_1 t}dt \]

实际上，系数计算的基本思想都一样，即将原函数乘系数对应的项的共轭再积分，构造一系列内积的和，因为正交函数的性质消除其他项即得到本系数的值。

### 时域与频域的能量关系

时域与频率能量守恒：周期信号的平均功率等于傅立叶级数展开各谐波分量有效值的平方和。

\[ P[f(t)] = \sum_{n=-\infty}^{\infty}|F_n|^2 = |F_0|^2 + 2\sum_{n=1}^{\infty} |F_n|^2 \]