---
layout: post
title:  "Learning Notes:Linear Regression"
categories: Notes of ML
---
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>
Linear Regression is one of the most fundamental and classic regresion method. In Linear Regression, we assume that given an input  vector $$X^T = (X_{1}, X_{2},..., X_{p})$$, we predict output $$Y$$ from the model:

$$\hat{Y} = f(X) = \hat\beta_0 + \sum_{j=1}^{p} X_j \hat{\beta}_{j} \qquad(1)$$ 

where $$\hat\beta_0$$ is bias. Also, we can write euqation 1 to: 

$$\hat{Y} = X^T\hat\beta \qquad(2)$$ 

if we assume all elements in $$X_0$$ is $$1$$.

In this model, we want to obtain a vector $$\hat\beta = (\hat\beta_0, \hat\beta_1,...,\hat\beta_j)$$, which can minimize the residual of the sum of squares, in matrix form, we have 

$$RRS(\beta) = (\mathbf{y} - \mathbf{X}\beta)^T(\mathbf{y} - \mathbf{X}\beta) \qquad(3).$$ 

Now we differentiating with respect to $$\beta$$ we have 

$$\frac{\partial{RSS}}{\partial{\beta}} = -2\mathbf{X}^T(\mathbf{y} - \mathbf{X}\beta) \qquad(4).$$ 

When the first derivative equals to zero, the $$RSS$$ comes to the minimum. Thus, we want to solve the equation: 

$$\mathbf{X}^T(\mathbf{y} - \mathbf{X}\beta) = 0 \qquad (5).$$ 

Then we obtain 

$$ \hat\beta = (\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y} \qquad(6).$$ 

According to quation 2, we obtain the predict value: 

$$\mathbf{\hat{y}} = \mathbf{X}\hat\beta \qquad(7)$$

where the $$\hat{y}$$ is the estimation of $$Y$$.

### Implementing with Python
For full code, click [here](https://github.com/AllenCX/toyML/blob/master/Linear_Regression/linear_regression.ipynb)

#### 2D example:

{% highlight python %}
from mpl_toolkits.mplot3d import Axes3D
import numpy as np
import matplotlib.pyplot as plt
from numpy.linalg import inv
N = 50

#simple 2D linear regression example
x = np.linspace(0, 10, num=N).reshape(N, 1)
y = np.linspace(0, 10, num=N).reshape(N, 1)
t = np.random.normal(0, 1, (N, 1))
y += t
beta_hat = inv(x.T.dot(x)).dot(x.T).dot(y)

fig, ax = plt.subplots()
ax.plot(x, y, 'bo')
ax.plot(x, x.dot(beta_hat), 'r')
plt.show()
{% endhighlight python %} 

![2D example][1]

#### 3D example:
{% highlight python %}

# Continueing the 2D example
z = np.linspace(10, 20, num=N).reshape(N, 1)
x_3d = np.concatenate((x, z), axis=1)

beta_hat_3d = inv(x_3d.T.dot(x_3d)).dot(x_3d.T).dot(y)
fig_3d = plt.figure()
ax_3d = fig_3d.add_subplot(111, projection='3d')
ax_3d.scatter(x, z, y)
y_3d_hat = x_3d.dot(beta_hat_3d)
ax_3d.plot(x, z, y_3d_hat.reshape(N), color='red')
plt.show()
{% endhighlight python %}


![3D example][2]


  [1]: https://raw.githubusercontent.com/AllenCX/toyML/master/Linear_Regression/2d_example.png
  [2]: https://raw.githubusercontent.com/AllenCX/toyML/master/Linear_Regression/3d_example.png