变换

对于一个平面图而言，它是多个像素点的组合而成的。

除去颜色，只剩下一张灰度图像；就连黑白都去掉，它就只是一堆点集的二维数组。

> 图片只是一个带有颜色和坐标的点集。

图像变换，就是在不改变集合中点的颜色信息的同时，去对各点的坐标进行变换。
$$
\begin{align}
point &: (x, y)\\ \\
image &: {\Large S}(point) \\ \\
transform &:{\Large S_0} = f({\Large S})
\end{align}
$$
其中单个点的变换
$$
p =\left\{
\begin{matrix}
x \\ y
\end{matrix}
\right.
\Rightarrow 
p_0 = \left\{ 
\begin{matrix}
x_0 \\ 
y_0
\end{matrix}
\right.
=\left\{
\begin{matrix}
f(x) \\
g(y)
\end{matrix}
\right.
$$

# 平移

对于平移而言，只是在基础数值上面进行加减运算
$$
\left\{
\begin{matrix}
x_0 = x \pm \hat x \\
y_0 = y \pm \hat y
\end{matrix}
\right.
$$
使用矩阵的方式进行表示
$$
\left[
\begin{matrix}
x_0 \\ y_0
\end{matrix}
\right] = 
\left[
\begin{matrix}
x_0 \\ y_0
\end{matrix}
\right] +
\left[
\begin{matrix}
\hat x \\ \hat y
\end{matrix}
\right]
$$
填充额外常数项，使用齐次方程进行表示
$$
\left[
\begin{matrix}
x_0 \\ y_0
\end{matrix}
\right] = 
\left[
\begin{matrix}
1 &0  & \hat x \\
0 &1 & \hat y
\end{matrix}
\right]
\left[
\begin{matrix}
x_0 \\ y_0 \\ 1
\end{matrix}
\right]
$$

> 一般来说，我们都可以使用这种形式进行点位置变换的表达：即乘上一个变换矩阵。

# 伸缩

关于伸缩的话，有两种伸缩办法

- 线性
- 非线性

$$
\left\{
\begin{matrix}
x_0 = k_x x \\ 
y_0 = k_y y
\end{matrix}
\right.
$$

当$k_x =k_y$时候，就是线性伸缩，此时的伸缩是等比例的。直线伸缩之后斜率不变。

非线性变换的时候，就不能保证平行了。

<hr>

加上平移，齐次表示一下
$$
\left\{
\begin{matrix}
x_0 = k_x x + \hat x\\ 
y_0 = k_y y + \hat y
\end{matrix}
\right.
\Rightarrow
\left[
\begin{matrix}
x_0 \\ y_0
\end{matrix}  
\right] = 
\left[
\begin{matrix}
k_x & 0 & \hat x \\
0 & k_y & \hat y
\end{matrix}
\right]
\left[
\begin{matrix}
x \\ y \\ 1
\end{matrix}
\right]
$$


# 旋转

![1578320998850](pic\1578320998850.png)

旋转的话需要从线性上面才能更直观的体现
