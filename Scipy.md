# Scipy学习笔记

## 一.基本情况

### 导入

```python
>>> import numpy as np
>>> import matplotlib as mpl
>>> import matplotlib.pyplot as plt
```

### 子包

| 子包                                                         | 描述                   |
| ------------------------------------------------------------ | ---------------------- |
| `cluster`                                                    | 聚类算法               |
| `constants`                                                  | 物理和数学常数         |
| `fftpack`                                                    | 快速傅立叶变换程序     |
| `integrate`                                                  | 积分和常微分方程求解器 |
| `interpolate`                                                | 插值和平滑样条         |
| [`io`](https://docs.python.org/dev/library/io.html#module-io) | 输入和输出             |
| `linalg`                                                     | 线性代数               |
| `ndimage`                                                    | N维图像处理            |
| `odr`                                                        | 正交距离回归           |
| `optimize`                                                   | 优化和根查找例程       |
| [`signal`](https://docs.python.org/dev/library/signal.html#module-signal) | 信号处理               |
| `sparse`                                                     | 稀疏矩阵和相关例程     |
| `spatial`                                                    | 空间数据结构和算法     |
| `special`                                                    | 特殊功能               |
| `stats`                                                      | 统计分布和功能         |

### 导入scipy子包

```python
>>> from scipy import linalg, optimize
```

### 查看某个函数信息

```
>>>np.info(optimize.fmin)
```

## 二.基本功能

### 与numpy交互

```
>>> import numpy as np
>>> np.some_function()
```

```
>>> from scipy import some_module
>>> some_module.some_function()
```

顶级`scipy`还包含来自[`numpy`](https://docs.scipy.org/doc/numpy/reference/index.html#module-numpy)和的功能 [`numpy.lib.scimath`](https://docs.scipy.org/doc/numpy/reference/routines.emath.html#module-numpy.lib.scimath)。但是，最好直接从[`numpy`](https://docs.scipy.org/doc/numpy/reference/index.html#module-numpy)模块中使用它们。

### 创建数组

```
>>>a = np.r_[3,[0]*5,-1:1:10j]
```

```
array([ 3.，0., 0.,0.,0.,0., -1.,-0.77777778,-0.55555556,-0.33333333, -0.11111111, 0.11111111,0.33333333,0.55555556,0.77777778,1.])
```

创建数组采用**np.r_**连接不同元素组成一元列表，注意10j代表在给的范围中插入10个点，包括开头和结尾，然而普通的arange语法是不包括结尾的。

```
>>>np.mgrid[0:5,0:5]
```

    array([[[0, 0, 0, 0, 0],[1, 1, 1, 1, 1],[2, 2, 2, 2, 2],[3, 3, 3, 3, 3],[4, 4, 4, 4, 4]],[[0, 1, 2, 3, 4],[0, 1, 2, 3, 4],[0, 1, 2, 3, 4],[0, 1, 2, 3, 4],[0, 1, 2, 3, 4]]])
**mgrid**用于创建多维数组

### 创建多项式

处理多项式的方法：

- 采用numpy中的poly1d
- 将系数作为序列储存，第一个数为最高项系数

```
>>> from numpy import poly1d
>>> p = poly1d([3,4,5])
>>> print(p)
3 x^2 + 4 x + 5
>>> print(p*p)#平方
9 x^4 + 24 x^3 + 46 x^2 + 40 x + 25
>>> print(p.integ(k=6))#不定积分，积分常数为6
1 x^3 + 2 x^2 + 5 x + 6
>>> print(p.deriv())#求导
6 x + 4
>>> p([4, 5])
array([ 69, 100])
```

### 标量函数向量化

numpy中**vectorize**函数能将本来标量的函数向量化，即原本处理一个数的函数能够逐个处理一个数组中的每个数，这样如果要批量处理数据的话，只要编写对一个函数的处理方法即可，这种方法可以避免循环

```
>>> def addsubtract(a,b):
...    if a > b:
...        return a - b
...    else:
...        return a + b
>>> vec_addsubtract = np.vectorize(addsubtract)
>>> vec_addsubtract([0,3,6,9],[1,3,5,7])
array([1, 6, 1, 2])
```

### 选择数组中的元素

numpy中的**select**函数可以在其中用if语句的向量化形式选择数据，即select([条件列表],[输出列表]，default=0）

```
>>> x = np.r_[-2:3]
>>> x
array([-2, -1,  0,  1,  2])
>>> np.select([x > 3, x >= 0], [0, x+2])
array([0, 0, 2, 3, 4])
```

### 其他功能

在模块中还可以找到一些其他有用的功能 [`scipy.misc`](https://docs.scipy.org/doc/scipy-1.1.0/reference/misc.html#module-scipy.misc)。例如，`factorial`和`comb` 函数计算n! 和 n!/k!(n−k)!使用精确整数运算（感谢Python的Long整数对象），或者使用浮点精度和gamma函数。另一个函数返回图像处理中使用的公共图像：`lena`。

最后，提供了两个函数，用于使用离散差来近似函数的导数。该函数`central_diff_weights`返回等间距的加权系数N点*o*的导数的点近似。必须将这些权重乘以对应于这些点的函数，并将结果相加以获得导数近似值。此功能仅在仅有功能样本可用时使用。当函数是可以传递给例程并进行`derivative`评估的对象时，该函数 可用于在正确的点处自动评估对象，以获得给定点处的第*o*个导数的N点近似

## 三、特殊函数（scipy.special）

scipy.special种包含数学物理里的一些特殊函数，包括：

- 艾里函数airy
- 椭圆积分elliptic
- 贝塞尔函数bessel
- 伽马函数gamma
- 贝塔函数beta
- 超几何函数hypergeometric
-  抛物柱面函数parabolic cylinder
- 马丢函数mathieu
- 球型波函数spheroidal wave
- 斯特鲁夫函数struve
- 开尔文函数kelvin. 

大部分函数接受复数参数，参考资料见 help(special)

## 四、积分（scipy.integrate）

```
>>> help(integrate)
 函数积分

   quad          -- 一般积分
   dblquad       -- 二重积分
   tplquad	     -- 三重积分
   nquad         -- 累次积分
   fixed_quad    -- 使用阶数n的高斯积分来积分func（x）。
   quadrature    -- 使用给定的容差求高斯积分。
   romberg       -- 龙贝格积分

 数值积分

   trapz         -- 梯形积分
   cumtrapz      -- 梯形累次积分
   simps         -- 辛普森积分
   romb          -- 龙贝格积分（2^(k+1))均匀间隔
   
   ODE（微分方程）系统的数值积分接口

   odeint        -- 一般常微分方程积分
   ode           -- VODE和ZVODE路径积分ODE方程
```

