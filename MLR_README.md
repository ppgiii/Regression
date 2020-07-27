This notebook shows the derivation and application of multiple linear regression with linear coefficients.

It is important to identify the eqaution in question that it can be dervied as linear coefficients even if the variables are not, e.g.
$$y = \beta_0 + \beta_1 x + \beta_2 x^2$$

can be transformed to a linear equation with $x_1 = x$ and $x_2 = x^2$,
$$y = \beta_0 + \beta_1 x_1 + \beta_2 x_2$$

For $x_1 = x_2 = 0$, "$\beta_0$ is the mean of $y$; otherwise, it has no physical interpretation."   $\beta_1$ is the expected change in response $y$ per unit change in $x_1$.  Similarly, $\beta_2$ interpreted with $x_2$.

For a general response $y$ with $k$ regressors, the equation  
$$y = \beta_0 + \beta_1 x_1 + ... + \beta_k x_k + \epsilon$$  

is the multiple linear regression with $k$ regressors.

For multiple functions of y,
$$y_i = \beta_0 + \beta_1 x_{i_1} + ... + \beta_k x_{i_k} + \epsilon_i$$

$$ = \beta_0 + \sum_{j=1}^{k}\beta_j x_{i_j} + \epsilon_i$$  

The least square function:  
$$S(\beta_0, \beta_1, ... , \beta_k) =  
\sum_{i=1}^{n} \epsilon_i^2 = \sum_{i=1}^{n} (y_i - \beta_0 - \sum_{j=1}^{k} \beta_j x_{i_j})$$  

minimizing S partial to the coefficients, the least squares estimators must satisfy:  
$$\frac{\partial S}{\partial \beta_0}|_{\hat{\beta_0},\hat{\beta_1},...,\hat{\beta_k}} = -2 \sum_{i=1}^{n}(y_i - \hat{\beta_0} - \sum_{j=1}^{k} \hat{\beta_j} x_{i_j}) = 0$$  

and
$$\frac{\partial S}{\partial \beta_j}|_{\hat{\beta_0},\hat{\beta_1},...,\hat{\beta_k}} = -2 \sum_{i=1}^{n}(y_i - \hat{\beta_0} - \sum_{j=1}^{k} \hat{\beta_j} x_{i_j}) x_{i_j} = 0, j = 1,..,k $$  

After simplification, the equation reduces to the familiar linear equation in vector form,
$$\mathbf{y} = \mathbf{X} \boldsymbol{\beta} + \boldsymbol{\epsilon}$$  

where
$$\mathbf{y} = \begin{bmatrix} y_1 \\ y_2 \\ .\\.\\.\\ y_n \end{bmatrix}  \quad
\mathbf{X} = \begin{bmatrix}
1 & x_{11} & x_{12} & ... & x_{1k} \\
1 & x_{21} & x_{22} & ... & x_{2k} \\
. & . & . & & . \\
1 & x_{n1} & x_{n2} & ... & x_{nk}
\end{bmatrix}$$  

$$\boldsymbol{\beta} = \begin{bmatrix} \beta_0 \\ \beta_1 \\ .\\.\\.\\ \beta_k \end{bmatrix}  \quad \boldsymbol{\epsilon} = \begin{bmatrix} \epsilon_1 \\ \epsilon_2 \\ .\\.\\.\\ \epsilon_n \end{bmatrix}$$  
