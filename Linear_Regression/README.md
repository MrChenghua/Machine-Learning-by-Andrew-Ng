# 线性回归
(经过了快一个月的学习，总算将吴恩达老师的machine learning课程学完了。希望通过把每周的学习内容记录下来，可以让自己把所学内容全部消化。这里立个flag，每天更新一次学习笔记，两周内更完！)
## 1. 多元线性回归记法：
通过Introduction的学习，知道假设方程h(x)为所建模型。对于多元线性回归模型，h(x)记法如下：
![](http://latex.codecogs.com/gif.latex?h_%5Ctheta%20%28x%29%20%3D%20%5Ctheta_0%20&plus;%20%5Ctheta_1%20x_1%20&plus;%20%5Ctheta_2%20x_2%20&plus;%20%5Ctheta_3%20x_3%20&plus;%20%5Ccdots%20&plus;%20%5Ctheta_n%20x_n)

模型用矩阵也可表示为：

![](http://latex.codecogs.com/gif.latex?%5Cbegin%7Balign*%7Dh_%5Ctheta%28x%29%20%3D%5Cbegin%7Bbmatrix%7D%5Ctheta_0%20%5Chspace%7B2em%7D%20%5Ctheta_1%20%5Chspace%7B2em%7D%20...%20%5Chspace%7B2em%7D%20%5Ctheta_n%5Cend%7Bbmatrix%7D%5Cbegin%7Bbmatrix%7Dx_0%20%5C%5C%20x_1%20%5C%5C%20%5Cvdots%20%5C%5C%20x_n%5Cend%7Bbmatrix%7D%3D%20%5Ctheta%5ET%20x%5Cend%7Balign*%7D)

其中x0 = 1，θ是(n x 1)的向量, X则是(m x n)的矩阵。

变量的标记如下：

![](http://latex.codecogs.com/gif.latex?%5Cbegin%7Balign*%7Dx_j%5E%7B%28i%29%7D%20%26%3D%20%5Ctext%7Bvalue%20of%20feature%20%7D%20j%20%5Ctext%7B%20in%20the%20%7Di%5E%7Bth%7D%5Ctext%7B%20training%20example%7D%20%5C%5C%20x%5E%7B%28i%29%7D%26%20%3D%20%5Ctext%7Bthe%20input%20%28features%29%20of%20the%20%7Di%5E%7Bth%7D%5Ctext%7B%20training%20example%7D%20%5C%5C%20m%20%26%3D%20%5Ctext%7Bthe%20number%20of%20training%20examples%7D%20%5C%5C%20n%20%26%3D%20%5Ctext%7Bthe%20number%20of%20features%7D%20%5Cend%7Balign*%7D)


## 2. cost function 与梯度下降：
对于多元线性回归，cost function为：

![](http://latex.codecogs.com/gif.latex?J%28%5Ctheta%29%20%3D%20%5Cdfrac%20%7B1%7D%7B2m%7D%20%5Cdisplaystyle%20%5Csum%20_%7Bi%3D1%7D%5Em%20%5Cleft%20%28h_%5Ctheta%20%28x_%7Bi%7D%29%20-%20y_%7Bi%7D%20%5Cright%29%5E2)

是关于θ的方程。

梯度下降算法，可以通过迭代计算，沿着θ偏导所在的方向，以特定的步幅α更新θ。从而逐步使J(θ)趋近与最小值。具体计算方式如下:

![](http://latex.codecogs.com/gif.latex?%5Ctheta_j%20%3A%3D%20%5Ctheta_j%20-%20%5Calpha%20%5Cfrac%7B1%7D%7Bm%7D%20%5Csum%5Climits_%7Bi%3D1%7D%5E%7Bm%7D%20%28h_%5Ctheta%28x%5E%7B%28i%29%7D%29%20-%20y%5E%7B%28i%29%7D%29%20%5Ccdot%20x_j%5E%7B%28i%29%7D%20%3B%5Ctext%7B%20for%20j%20%3A%3D%200...n%7D)

### 特征标尺(Feature Scaling)：
观察梯度下降方程，可以看到对应不同的x_i, x_j，相应的θ_i和θ_j的下降速度也不同。在自变量数值标尺较大时，梯度下降的速度会较慢，而在自变量数值标尺较小时，梯度下降的速度会较快。因此为了加快算法下降的速度，通常会将所有自变量的值都缩减到一个大致相同的标尺内，比如-0.5< x <0.5,或者 -1< x <1。
一般实现上述操作有两个方法，特征标尺化和均值归一化。

特征标尺化：

![](http://latex.codecogs.com/gif.latex?x_i%20%3D%20%5Cdfrac%7Bx_i%20-%20%5Cmu_i%7D%7Bmax%28x_i%29-min%28x_i%29%7D)

均值归一化：

![](http://latex.codecogs.com/gif.latex?x_i%20%3A%3D%20%5Cdfrac%7Bx_i%20-%20%5Cmu_i%7D%7Bs_i%7D)

其中mu_i为x_i的均值，s_i为x_i的标准差

### α(Learning Rate)的设定:
根据梯度下降方程可以发现，α的取值往往也会直接影响到算法的运行结果。α太大，可能会导致J(θ)无法收敛，α太小，则会使收敛速度过慢。

可以通过绘制J(θ)随迭代次数变化的图像，来判断α的取值是否合适：

<img src=https://user-images.githubusercontent.com/31018275/30528274-66e40f58-9bff-11e7-9ffb-b6724f6e7dfe.png width = '500'>

上图中，J(θ)的收敛速度很理想，所以α的取值合适。如果J(θ)下降的速度很缓慢可以适当增加α的值。

<img src=https://user-images.githubusercontent.com/31018275/30528277-6daab4e0-9bff-11e7-9d91-f22f73fb83de.png width = '500'>

一般α的值可以从0.01开始尝试，每次增加或减少3倍。






