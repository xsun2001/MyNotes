# Lecture 5

## 采样与采样定理

### 采样的定义与相关概念

采样在某些离散的时间点上提取连续时间信号值的过程。采样的时间间隔被称为采样周期\(T_s\)，对应的有采样频率\(f_s=1/T_s\)和采样角频率\(\omega_s=2\pi/T_s\)。

### 采样信号的时域表示与频域表示

时间上，我们用一系列单位冲激函数表示对某个时间点的信号进行采样：

- 冲激串（理想采样）：\( p(t) = \sum_{n=-\infty}^{\infty}\delta(t-nT_s) \)
- 采样信号：\( x_p(t) = x(t)p(t) = \sum_{n=-\infty}^{\infty}x(nT_s)\delta(t-nT_s) \)
- 频域表示，或采样信号的傅立叶变换：\( X_p(\omega)=\frac{1}{2\pi}X(\omega)\ast P(\omega) \)

现在我们求冲激串的傅立叶变换：

先求傅立叶级数：

\[ \begin{align}
\alpha_n &= \frac{1}{T_1} \int_{-T_1/2}^{T_1/2}p(t)e^{-jn\omega_s t}dt \\
&= \frac{1}{T_1} \int_{-T_1/2}^{T_1/2}\delta(t)e^{-jn\omega_s t}dt \\
&= \frac{1}{T_1}
\end{align} \]

即：

\[ p(t) = \frac{1}{T_s}\sum_{n=-\infty}^{\infty}e^{jn\omega_s t} \]

因为\( e^{jn\omega_st}\leftrightarrow 2\pi\delta(\omega-n\omega_s) \)，所以：

\[ P(\omega) = \frac{2\pi}{T_s}\sum_{n=-\infty}^{\infty}\delta(\omega-n\omega_s) \]

最后采样信号的频谱为：

\[ \begin{align}
X_p(\omega) &= \frac{1}{2\pi}X(\omega)\ast P(\omega) \\
&= \frac{1}{2\pi}X(\omega)\ast\frac{2\pi}{T_s}\sum_{n=-\infty}^{\infty}\delta(\omega-n\omega_s) \\
&= \frac{1}{T_s}\sum_{n=-\infty}^{\infty}X(j(\omega-n\omega_s))
\end{align} \]

这证明了，时域上的理想采样信号的频谱相当于原频谱以\(\omega_s\)为周期进行延拓。

### 采样定理

上面的推导也说明了，如果原始信号的频谱范围超过了\(\omega_s\)这一周期，那么在延拓再相加的过程中，会有一部分频谱产生重叠。如果在这一周期之内，那么抽样信号的频谱中还保存了完整的原始频谱的信息，进而可以恢复出原始信号。这样我们引出了采样定理：

**对带限于最高频率\(\omega_M\)的连续时间信号\(x(t)\)，如果以\(\omega_s\geqslant\omega_M\)对频率进行理想采样，那么\(x(t)\)可以唯一的由其样本\(x(nT)\)来确定。**

这个定理又称**奈奎斯特-香农采样定理(Nyquist–Shannon sampling theorem)**。

在实际应用中，理想采样于理想滤波器自然不可能实现，因此实际采样时，应当令\(\omega_s>\omega_M\)。

## 连续信号的采样重构

### 理想滤波器

理想滤波器在频谱上实际上是一个矩阵脉冲函数：

\[ H(\omega) = \begin{cases}
T_s, &|\omega|\leqslant\omega_c \\
0, &|\omega| > \omega_c \\
\end{cases} \]

这里的\(T_s\)出现是因为采样后的频谱有一个\(1/T_s\)的系数。

其时域函数为：

\[ h(t)=T_s\frac{\omega_c}{\pi}Sa(\omega_ct) \]

通过这一理想滤波器提取原信号的频谱：

\[\hat{X}(\omega) = X_p(\omega)\cdot H(\omega)\]

通过频谱恢复信号：

\[ \begin{align}
\hat{x}(t) &= x_p(t)\ast h(t) \\
&=\sum_{n=-\infty}^{\infty}x(nT_s)\delta(t-nT_s)\ast h(t) \\
&=\frac{\omega_cT_s}{\pi}\sum_{n=-\infty}^{\infty}x(nT_s)Sa(\omega_c(t-nT_s))
\end{align} \]

### 其他的内插函数

**零阶保持内插**意为保持每个采样点本身的值，其内插函数为矩形脉冲函数：

\[ h_0(t) = \begin{cases}
1, & 0< t < T \\
0, & \text{otherwise}
\end{cases} \]

其频谱为：

\[ H_0(\omega) = \int_0^T e^{-j\omega t}dt = \frac{1}{-j\omega}(e^{-j\omega T}-1) \]

\[ |H_0(\omega)| = \frac{2-2\cos T\omega}{\omega^2}\]

**一阶保持内插**可以看做每相邻两点进行连接，其内插函数为三角形脉冲函数：

\[ h_1(t) = \begin{cases}
1-\frac{t}{T}, & 0< t < T \\
1+\frac{t}{T}, & -T< t < 0 \\
0, & \text{otherwise}
\end{cases} \]

其频谱为：

\[ \begin{align}
H_1(\omega) &= \int_{-T}^0 (1+\frac{t}{T})e^{-j\omega t}dt + \int_0^T (1-\frac{t}{T})e^{-j\omega t}dt \\
&= \int_0^T (1-\frac{t}{T})(e^{-j\omega t}+e^{j\omega t})dt \\
&= \int_0^T 2(1-\frac{t}{T})\cos\omega tdt \\
&= \frac{2-2\cos T\omega}{T \omega^2}
\end{align} \]

### 欠采样

如果采样频率低于采样定理的需求，那么采样频谱会发生混叠。导致无法准确还原原信号。采样频率等同于两倍信号最高频率实际上也不可以还原信号。

### 频域采样

与时域采样相对应，我们也可以对信号的频域进行采样。

- 采样函数：\( P(j\omega) = \sum_{k=-\infty}^{\infty}\delta(\omega-k\omega_0) \)
- 采样后的频率信号：\( \hat{X}_P(j\omega) = X(j\omega)P(j\omega) = \sum_{k=-\infty}^{\infty}X(k\omega_0)\delta(\omega-k\omega_0) \)
- 采样信号的时域：\( \hat{x}_p(t) = x(t)\ast p(t) = x(t)\ast [\frac{1}{\omega_0}\sum_{k=-\infty}^{\infty} \delta(t-\frac{2\pi}{\omega_0}k)] = \frac{1}{\omega_0}\sum_{k=-\infty}^{\infty}x(t-\frac{2\pi}{\omega_0}k) \)

同样的，也需要对采样信号的时域进行加窗处理使其变为非周期函数，这样再计算频域就是连续的了。加窗的要求也和时域采样时相同。若为矩形窗，那么最后恢复的频域信号为：

\[ X(j\omega) = \sum_{k=-\infty}^{\infty}X(k\omega_0)Sa(\frac{\omega-k\omega_0}{\omega_0}) \]