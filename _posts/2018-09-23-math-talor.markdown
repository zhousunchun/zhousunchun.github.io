---
layout: post
title: 泰勒展开式
date: 2018-09-23
tags: SLAM | Math
categories: slam
---



## 多元函数的泰勒展开式

在学习高等数学的时候，对于一元函数$f(x)$在ｋ点，即$x=x^{(k)}$的　泰勒展开式为：

$$f(x) = f(x^{(k)}) + f'(x^{(k)})(x-x^{(k)}) + \frac{1}{2!} f''(x^{(k)}(x-x^{(k)})^2+\dots + \frac{1}{n!}f^{(n)}(x^{(k)}(x-x^{(k)})^n +R_n$$

其中$R_n$是：

$$R_n = \frac{1}{(n+1)!} f^{(n+1)}(\xi)(x-x^{(k)})^{(n+1)}$$

其中$\xi$在$x$和$x^{(k)}$ 之间。在$x^{(k)}$点充分小的临域内，余项$R_n$的极限为零，因此可以用多项式来逼近函数$f(x)$。



## 二元函数的泰勒展开式

------

定理：设$z=f(x,y)$在的某一邻域内连续且有直到$n+1$阶的连续偏导数，$(x_0+h,y_0+h)$为此领域内任一点，则有

$$f(x_0+h,y_0+h) = f(x_0,y_0) + (h\frac{\partial}{\partial x} + k \frac{\partial}{\partial y})f(x_0,y_0) + \frac{1}{2!} (h\frac{\partial}{\partial x} + k \frac{\partial}{\partial y})^2 f(x_0,y_0) + \dots \\ + \frac{1}{n!}(h\frac{\partial}{\partial x}+ k\frac{\partial}{\partial y})^n f(x_0,y_0)+\frac{1}{(n+1)!}(h\frac{\partial}{\partial x} + k \frac{\partial}{\partial y})^{(n+1)}(f(x_0+\theta h, y_0 +\theta k)), (0 < \theta <1)$$

函数$f(X) = f(x_1,x_2)$在点$X^{(k)} = (x_1^{(k)},x_2^{(k)})$附近的泰勒展开，若只是取到二次项，可以写成如下形式

$$f(X) \approx f(X^{(k)})+\frac{\partial f}{\partial x_1}|_{X=X^{(k)}}(x_1-x_1^{(k)}) + \frac{\partial f}{\partial x_2}|_{X=X^{(k)}}(x_2-x_2^{(k)}) + \\\frac{1}{2!} [ \frac{\partial^2 f}{\partial x_1^2}|_{X=X^{(k)}}(x_1-x_1^{(k)}) + 2\frac{\partial^2 f}{\partial x_1 \partial x_2}(x_1-x_1^{(k)})(x_2 - x_2^{(k)}) + \frac{\partial^2f}{\partial x_2^2}|_{X=X^{(k)}}(x_2-x_2^{(k)})^2]$$

如果将上面的写成矩阵的形式，可以得到更加整洁的表示方式

$$f(X)\approx f(X^{(k)}) + \left( \begin{matrix}\frac{\partial f}{\partial x_1 } & \frac{\partial f}{\partial x_2 }\end{matrix} \right) \left(\begin{matrix} x_1  - x_1^{(k)} \\ x_2 - x_2^{(k)}\end{matrix}\right) + \frac{1}{2}\left(\begin{matrix} x_1-x_1^{(k)} & x_2 - x_2^{(k)}\end{matrix}\right)\left(\begin{matrix} \frac{\partial^2 f }{\partial x_1^2} & \frac{\partial^2 f}{\partial x_1 \partial x_2} \\ \frac{\partial^2 f}{\partial x_1 \partial x_2 } &  \frac{\partial^2f}{\partial x_2^2} \end{matrix}\right) \left(\begin{matrix} x_1 - x_1^{(k)} \\ x_2 - x_2^{(k)}\end{matrix}\right)$$

公式中，我们令

$X-X^{(k)} = \left(\begin{matrix} x_1  - x_1^{(k)} \\ x_2 - x_2^{(k)}\end{matrix}\right) $

$$\nabla f = \left( \begin{matrix}\frac{\partial f}{\partial x_1 } & \frac{\partial f}{\partial x_2 }\end{matrix} \right)$$ 是函数$f(X)$ 在$X^{(k)}$的梯度

$\nabla^2 f＝\left(\begin{matrix} \frac{\partial^2 f }{\partial x_1^2} & \frac{\partial^2 f}{\partial x_1 \partial x_2} \\ \frac{\partial^2 f}{\partial x_1 \partial x_2 } &  \frac{\partial^2f}{\partial x_2^2} \end{matrix}\right) \　$ 是函数$f(X)$在$X^{(k)}$点的二阶偏导数，也就是常说的**Hessian**矩阵

这样就可以进一步简洁的表达上述公式为：

$$f(X) \approx f(X^{(k)}) + \nabla f(X^{(k)})(X-X^{(k)}) + \frac{1}{2} (X-X^{(k)}) ^TH(X^{(k)})(X-X^{(k)}) $$