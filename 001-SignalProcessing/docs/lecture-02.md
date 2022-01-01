# Lecture 2

## 卷积

### 定义

\begin{align}
    f(t)*g(t) &= \int_{-\infty}^{+\infty} f(\tau)g(t-\tau)d\tau \\
    f(n)*g(n) &= \sum_{m=-\infty}^{+\infty} f(m)g(n-m)dm
\end{align}

### 性质

1. 交换律：\(f_1*f_2=f_2*f_1\)
2. 分配律：\(f_1*(f_2+f_3)=f_1*f_2+f_1*f_3\)
3. 结合律：\((f_1*f_2)*f_3=f_1*(f_2*f_3)\)
4. 微分：
      1. 单次：\(\frac{d}{dt}[f_1(t)*f_2(t)]=f_1(t)*\left[\frac{d}{dt}f_2(t)\right]=\left[\frac{d}{dt}f_1(t)\right]*f_2(t)\)
      2. 多次：\((f_1*f_2)^{(n)}(t)=f_1^{(m)}(t)*f_2^{(n-m)}(t)\)
5. 积分：\(\int_{-\infty}^t(f_1*f_2)(\lambda)d\lambda=f_1(t)*\left(\int_{-\infty}^tf_2(\lambda)d\lambda\right)=\left(\int_{-\infty}^tf_1(\lambda)d\lambda\right)*f_2(t)\)

## 相关运算

\[ R_{f_1f_2}(t)=R(f_1(t),f_2(t))=\int_{-\infty}^{+\infty}f_1(\tau)f_2^*(\tau-t)d\tau=\int_{-\infty}^{+\infty}f_1(\tau+t)f_2^*(\tau)d\tau \]

- 相关运算与次序有关：\(R_{f_1f_2}(t)=R_{f_2f_1}^*(-t)\)
- 相关运算与卷积的关系：\(R_{f_2f_1}(t)=f_1^*(-t)*f_2(t)\)
- 自相关运算：用来检测准周期函数的准周期

## 奇异信号

### 典型的奇异信号

单位斜变信号

:   \[ R(t) = \begin{cases} 0,\; &t<0 \\ t,\; &t\geqslant 0 \end{cases} \]

单位阶跃信号

:   \[ u(t) = \begin{cases} 0,\; &t<0 \\ 1,\; &t\geqslant 0 \end{cases} \]

上面两个信号函数互相有微积分关系。

单位矩形脉冲信号

:   \[ G_\tau(t) = \begin{cases} 1,\; &|t|\leqslant \tau/2 \\ 0,\; &|t| > \tau/2 \end{cases} \]

符号函数信号

:   \[ \mathrm{sgn}(t) = \begin{cases} 1,\; &t > 0 \\ -1,\; &t < 0 \end{cases} \]

\[ \mathrm{sgn}(t) + 1 = 2u(t) \]

### 单位冲激信号

\[
    \begin{cases}
    \delta(t) = 0,\; &t\neq0 \\
    \delta(t) = \infty,\; &t=0 \\
    \int_{-\infty}^{+\infty}\delta(t)dt = 1
    \end{cases}
\]

#### 性质

1. 筛选特性
      1. \( x(t)\delta(t) = x(0)\delta(t) \)
      2. \( x(t)\delta(t-t_0) = x(t_0)\delta(t-t_0) \)
2. 取样特性
      1. \( \int_{-\infty}^{+\infty}x(t)\delta(t)dt = x(0) \)
      2. \( \int_{-\infty}^{+\infty}x(t)\delta(t-t_0)dt = x(t_0) \)
3. 时扩特性：\( \delta(at) = \frac{1}{|a|}\delta(t) \)
4. 信号的脉冲分解：\( f(t) = \int_{-\infty}^{+\infty}f(\tau)\cdot\delta(t-\tau)d\tau \)