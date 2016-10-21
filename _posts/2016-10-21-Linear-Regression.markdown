###Linear Regression

<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>

Linear Regression is one of the most fundamental and classic regresion method. In Linear Regression, we assume that given an input  vector $X^T = (X_{1}, X_{2},..., X_{p})$, we predict output $Y$ from the model:
$$\hat{Y} = f(X) = \hat\beta_0 + \sum_{j=1}^{p} X_j \hat{\beta}_{j} \qquad(1)$$ where $\hat\beta_0$ is bias. Also, we can write euqation 1 to: $$\hat{Y} = X^T\hat\beta \qquad(2)$$ if we assume all elements in $X_0$ is $1$.

In this model, we want to obtain a vector $\hat\beta = (\hat\beta_0, \hat\beta_1,...,\hat\beta_j)$, which can minimize the residual of the sum of squares, in matrix form, we have $$RRS(\beta) = (\mathbf{y} - \mathbf{X}\beta)^T(\mathbf{y} - \mathbf{X}\beta) \qquad(3).$$ Now we differentiating with respect to $\beta$ we have $$\frac{\partial{RSS}}{\partial{\beta}} = -2\mathbf{X}^T(\mathbf{y} - \mathbf{X}\beta) \qquad(4).$$ When the first derivative equals to zero, the $RSS$ comes to the minimum. Thus, we want to solve the equation: $$\mathbf{X}^T(\mathbf{y} - \mathbf{X}\beta) = 0 \qquad (5).$$ Then we obtain $$ \hat\beta = (\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y} \qquad(6).$$ According to quation 2, we obtain the predict value: $$\mathbf{\hat{y}} = $$
