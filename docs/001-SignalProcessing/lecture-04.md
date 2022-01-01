# Lecture 4

## 非周期信号的傅立叶变换

### 非周期信号的傅立叶变换的推导过程

上一节我们得出了周期函数的傅立叶级数展开：

\[ f_{T_1}(t) = \sum_{n=-\infty}^{\infty}F_ne^{jn\omega_1 t} \]

\[ F_n = \frac{1}{T_1}\int_{-T_1/2}^{T_1/2}f_{T_1}(t)e^{-jn\omega_1 t}dt \]

或写为：

\[ T_1F_n = \int_{-T_1/2}^{T_1/2}f_{T_1}(t)e^{-jn\omega_1 t}dt = F(jn\omega_1) \]

来引入其中的\(F\)函数。这样原信号的表达式也可变为：

\[ f_{T_1}(t) = \sum_{n=-\infty}^{\infty}\frac{1}{T_1}F(jn\omega_1)e^{jn\omega_1 t} \]

我们发现，非周期函数实际上相当于周期无限大的函数：

\[ f(t) = \lim_{T_1\rightarrow\infty}f_{T_1}(t) \]

随着周期不断变大，角速度也不断缩小：

\[ T\rightarrow \infty \Rightarrow \omega_1\rightarrow \Delta\omega \]

因此：

\[ \begin{align}
f(t) &= \lim_{T_1\rightarrow\infty}f_{T_1}(t) \\
&= \lim_{T_1\rightarrow\infty}\sum_{n=-\infty}^{\infty}\frac{1}{T_1}F(jn\omega_1)e^{jn\omega_1 t} \\
&= \sum_{n=-\infty}^{\infty}\frac{1}{2\pi}F(jn\Delta\omega)e^{jn\Delta\omega t} \Delta\omega \\
&= \frac{1}{2\pi} \int_{-\infty}^{\infty} F(j\omega)e^{j\omega t}d\omega
\end{align} \]

与周期函数的傅立叶级数对照，发现非周期函数的傅立叶变换实际上形式类似，只不过变为了连续函数的积分。我们同样也需要计算系数的表达式：

\[ \begin{align}
F(j\omega) &= \lim_{\Delta\omega\rightarrow 0}F(jn\Delta\omega) \\
&= \lim_{T_1\rightarrow\infty}\int_{-T_1/2}^{T_1/2}f_{T_1}(t)e^{-jn\Delta\omega t}dt \\
&= \int_{-\infty}^{\infty}f(t)e^{-j\omega t}dt
\end{align} \]

### 非周期信号的傅立叶变换的公式

\[ f(t) = \frac{1}{2\pi} \int_{-\infty}^{\infty} F(j\omega)e^{j\omega t}d\omega = \mathfrak{F}[f(t)] \]

\[ F(j\omega) = \int_{-\infty}^{\infty}f(t)e^{-j\omega t}dt = \mathfrak{F}^{-1}[F(j\omega)] \]

称\(F(j\omega)\)为**频谱密度**，简称**频谱**。频谱的幅度和相位分别称为幅度频谱和相位频谱。

由于

\[ \begin{align}
F(\omega) &= R(\omega) + jX(\omega) \\
&= \int_{-\infty}^{\infty}f(t)e^{-j\omega t}dt \\
&= \int_{-\infty}^{\infty}f(t)\cos\omega t dt - j\int_{-\infty}^{\infty}f(t)\sin\omega tdt
\end{align} \]

可以发现，频谱实部是偶对称函数，频谱虚部是奇对称函数，进一步的，幅度频谱的偶对称的，相位频谱是奇对称的。

与周期函数频谱相比，非周期函数频谱是连续函数，表示的是某一频率周围的频谱密度而非绝对大小。

### 常用信号的傅立叶变换

\[ \begin{align}
e^{-at}u(t) &\leftrightarrow \frac{1}{j\omega+a}, &a>0 \\
G_\tau(t) &\leftrightarrow \tau Sa(\frac{\omega\tau}{2}), &\text{其中}G_\tau(t)\text{为单位矩形脉冲信号} \\
\delta(t) &\leftrightarrow 1, &\text{其中}\delta(t)\text{为单位冲激信号} \\
\frac{1}{2\pi} &\leftrightarrow \delta(\omega) \\
u(t) &\leftrightarrow \pi\delta(\omega)+\frac{1}{j\omega}
\end{align} \]

## 傅立叶变换的性质

\[f(t) \overset{\mathbf{FT}}{\longleftrightarrow} F(\omega)\]

1. 唯一性：傅立叶变换或反变换后的函数相等，证明原函数相等
2. 线性
3. 反褶与共轭性质：\( f(-t) \leftrightarrow F(-\omega),\; f^*(t) \leftrightarrow F^*(-\omega) \)
      1. 推论：实信号的频谱共轭对称：\( f(t) = f^*(t) \Rightarrow F(\omega) = F^*(-\omega) \)
4. 保持奇偶性质：如\( f(t) = f(-t) \Rightarrow F(\omega) = F(-\omega) \)
5. FT与IFT的对偶性
      1. \( \mathfrak{F}^{-1}[F(\omega)] = \frac{1}{2\pi}\{\mathfrak{F}_\omega[F^*(\omega)]\}^* \)
      2. \( F(t) \overset{\mathbf{FT}}{\longleftrightarrow} 2\pi f(-\omega) \)
6. 尺度变换性质：\( \mathfrak{F}[f(at)] = \frac{1}{|a|}F(\frac{\omega}{a}) \)
7. 时移性质：\( \mathfrak{F}[f(t+t_0)] = F(\omega)e^{j\omega t_0} \)
      1. 意义：\( F(\omega)e^{j\omega t_0} = |F(\omega)|e^{j(\angle F(j\omega)+\omega t_0)} \)频谱的相位根据时间移动相应的角度，而幅度不变。
8. 频移性质：\( \mathfrak{F}^{-1}[F(\omega-\omega_0)] = f(t)e^{j\omega_0 t} \)
9. 综合上面三条：
      1. \( f(at+b) \leftrightarrow \frac{1}{|a|}F(j\frac{\omega}{a})e^{j\frac{b}{a}\omega} \)
      2. \( \frac{1}{|a|}f(\frac{t}{a})e^{j\omega_0\frac{t}{a}} \leftrightarrow F(a\omega-\omega_0) \)
10. 微分性质
      1. \( \frac{d}{dt}f(t) \leftrightarrow j\omega F(\omega) \)
      2. \( -jtf(t) \leftrightarrow \frac{dF(\omega)}{d\omega} \)
11. 积分性质
      1. \( \int_{-\infty}^{t} f(\tau)d\tau \leftrightarrow (j\omega)^{-1}F(\omega) + \pi F(0)\delta(\omega) \)
      2. \( \pi f(0)\delta(t) + (-jt)^{-1}f(t) \leftrightarrow \int_{-\infty}^{\omega} F(\lambda)d\lambda \)
12. 卷积定理
      1. \( \mathfrak{F}[f_1(t)\ast f_2(t)] = \mathfrak{F}[f_1(t)]\cdot\mathfrak{F}[f_2(t)] \)
      2. \( \mathfrak{F}[f_1(t)\cdot f_2(t)] = \frac{1}{2\pi} \mathfrak{F}[f_1(t)]\ast\mathfrak{F}[f_2(t)] \)
13. 帕斯瓦尔定理：\( \int_{-\infty}^{\infty}||f(t)||^2dt = \frac{1}{2\pi}||F(\omega)||^2d\omega \)

注意理解时域与频域的对应关系，熟练灵活运用相关性质简化傅立叶变换的求解，尤其是注意卷积性质的应用。

## 周期信号的傅立叶变换

我们先求复指数函数的傅立叶变换，再根据欧拉公式求三角函数的傅立叶变换：

\[ \begin{gather}
1 \leftrightarrow 2\pi\delta(\omega) \Rightarrow e^{j\omega_0 t} \leftrightarrow 2\pi\delta(\omega-\omega_0) \\
\cos\omega_0 t = \frac{1}{2}(e^{j\omega_0 t}+e^{-j\omega_0 t}) \Rightarrow \cos\omega_0 t \leftrightarrow \pi\delta(\omega-\omega_0)+\pi\delta(\omega+\omega_0) \\
\sin\omega_0 t = \frac{1}{2}(e^{j\omega_0 t}-e^{-j\omega_0 t}) \Rightarrow \sin\omega_0 t \leftrightarrow \pi\delta(\omega-\omega_0)-\pi\delta(\omega+\omega_0)
\end{gather} \]

可以看到，周期信号的频谱是离散谱。具体来说，是若干个冲激信号组成的离散谱，在每个谐频点的值都是无穷大。这是因为傅立叶变换求的是频谱密度而不是绝对的数值。