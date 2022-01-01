# Lecture 10

## 离散傅立叶变换的性质

1. 线性
2. 时移性质
      1. 这里的时移实际上是**圆周位移**，是将原来的主值区间按周期进行延拓后整体平移再重新取主值区间内的\(N\)个点构造的，记作：\(y(n)=x((n-m))_NR_N(n)\)。
      2. \( \mathbf{DFT}[y(n)] = W_N^{mk}X(k) \)
3. 频移特性
      1. \( \mathbf{IDFT}[X(k-l)] = W_N^{-nl}x(n) \)
4. 共轭对称性
      1. \( \mathbf{DFT}[x^*(n)] = X^*(N-k) \)
      2. 推论：实信号的DFT是共轭对称的：\( x(n)=x^*(n) \Rightarrow X(k) = X^*(N-k) \)
5. 对偶性：\( \mathbf{DFT}[X(n)] = Nx(-k) \)
6. 卷积性质：
      1. 这里的卷积是**圆周卷积**，同样也和圆周位移是相同的思想，记作：\( x(n)\circledast h(n) = \sum_{m=0}^{N-1}x(m)h((n-m))_NR_N(n) \)。
            1. 圆周卷积可以看做是线性卷积的回绕序列。
      2. \( \mathbf{DFT}[x_1(n)\cdot x_2(n)] = \frac{1}{N}X_1(k)\circledast X_2(k) \)
      3. \( \mathbf{IDFT}[X_1(k)\cdot X_2(k)] = x_1(n)\circledast x_2(n) \)
7. 帕斯瓦尔定理：\( \sum_{n=0}^{N-1}|x(n)|^2 = \frac{1}{N}\sum_{k=0}^{N-1}|X(k)|^2 \)

## 应用DFT

DFT中的\(k\)只代表点的编号，其对应的数字频率和模拟频率分别为：

\[ \Omega_k = \frac{2\pi}{N}k = \frac{\omega_k}{f_s} = 2\pi\frac{f_k}{f_S}, f_k = k\frac{f_s}{N} \]

### 使用DFT计算非周期信号的FT

\[ F(\omega_k) = F(\Omega_kf_s) = T_sX(k) \]

然后逐点绘制即可得到近似的FT。

### 使用IDFT计算非周期信号的IFT

\[ f(n) = \frac{1}{T_s}\mathbf{IDFT}[F(\omega_k)] \]

### 使用DFT计算周期信号的FS

\[ F_k = \frac{1}{N}X(k) \]
