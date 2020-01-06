# 变换

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
x_1 \\ y_1
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
x_1 \\ y_1
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

平移参数中，可变参数有两个，为两个自由度。

# 伸缩

关于伸缩的话，有两种伸缩办法

- 线性
- 非线性

$$
\left\{
\begin{matrix}
x_1 = k_x x_0 \\ 
y_1 = k_y y_0
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
x_1 = k_x x_0 + \hat x\\ 
y_1 = k_y y_0 + \hat y
\end{matrix}
\right.
\Rightarrow
\left[
\begin{matrix}
x_1 \\ y_1
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
x_0 \\ y_0 \\ 1
\end{matrix}
\right]
$$
加上平移，自由度为4，如果是线性变换，自由度为3，因为$k_x = k_y$

# 旋转

![1578320998850](pic\1578320998850.png)

旋转的话需要从线性上面才能更直观的体现。
$$
\begin{align}
假设线段长度为R &:\left\{
\begin{matrix}
x_0 = R\cos{b} \\
y_0 = R \sin {b}
\end{matrix}
\right.\\
并且 &:\left\{
\begin{matrix}
x_1 = R\cos(a+b) = R\cos a \cos b - R\sin a \sin b \\
y_1 = R\sin(a+b) = R\cos a \sin b + R \sin a \cos b
\end{matrix}
\right.\\
得到 &:\left\{
\begin{matrix}
x_1 = x_0 \cos a - y_0 \sin a \\
y_1 = y_0 \sin b + x_0 \sin a
\end{matrix}
\right.\\
齐次&:\left[
\begin{matrix}
x_1 \\ y_1
\end{matrix}
\right] = 
\left[
\begin{matrix}
\cos a & -\sin a \\ \sin b & \sin a
\end{matrix}
\right]\left[
\begin{matrix}
x_0 \\ y_0
\end{matrix}
\right] \\
加上平移&:\left[
\begin{matrix}
x_1 \\ y_1 \\ m
\end{matrix}
\right] = 
\left[
\begin{matrix}
\cos a & -\sin a & \hat x\\ \sin b & \sin a & \hat y
\end{matrix}
\right]\left[
\begin{matrix}
x_0 \\ y_0 \\ 1
\end{matrix}
\right] 
\end{align}
$$
虽然有六个参数，但是其中四个都分别依赖$a和b$,总自由度为4.

# 仿射

$$
\left[
\begin{matrix}
x_1 \\ y_1 \\ m
\end{matrix}
\right] = 
\left[
\begin{matrix}
a & b & c\\ d & e & f
\end{matrix}
\right]\left[
\begin{matrix}
x_0 \\ y_0 \\ 1
\end{matrix}
\right]
$$

仿射变换和旋转的区别可以类比于缩放中的线性和非线性，这里会出现比较大的变化。

其中的每个参数之间关联不大，自由度由原来的4提升为6，在这里会丧失原图的更多性质。

相较而言，之前的变换有如下性质

- 保角性：角度不变
- 保线性：直线不弯
- 保比例：比例不变

仿射变换之后，只遗留了保线性。

# 投影

$$
\left[
\begin{matrix}
x_1 \\ y_1 \\ m
\end{matrix}
\right] = 
\left[
\begin{matrix}
a & b & c\\ d & e & f \\ g & h & i
\end{matrix}
\right]\left[
\begin{matrix}
x_0 \\ y_0 \\ 1
\end{matrix}
\right]
$$



投影变换相较于之前的变换，使用的是三阶的变换矩阵。

变换的效果不再局限于$2D$，$3D$变换带有空间的透视感。但是丢失了最后的保线性。

从变换矩阵上看，总共有九个自由度，但是变换矩阵$A$需要满足如下条件
$$
A A^T = E
$$
所以投影变换的自由度为8，需要四个点才能进行确定。

# 补充

##自由度

其中所说的自由度可以简单的理解为变换矩阵中的未知数个数。

因为改变其中一个，变换都会发生改变，自由度也就是改变变换方式的维度。

## 求解

需要确定的点的个数，主要取决于求解变换矩阵未知数的点的个数。



# 