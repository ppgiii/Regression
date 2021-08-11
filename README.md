
## Linear Regression through python.
---
See the [README.ipynb](https://github.com/ppgiii/Regression/blob/master/README.ipynb) version of this README for the math images not displayed in this format.

### Introduction  
This exercise attempts to learn linear regression by using equations from the textbook "Introduction to Linear Regression Analysis" with python.  It will use python libraries' statsmodels, scipy, and scikit-learn for comparison and show the differences in implementation.  Visualization of the results uses matplotlib, pandas plot(), & seaborn.  

Linear regression is a very common method to do regression analysis.  The interest is to find the relationship between the feature variable and its response.  This is hopefully the first of many notes on how to apply python for regression analysis.

### Methods  
The data comes from the textbook with one feature variable, regressor, and one observe data, response.  This is loaded using panda and arranged to show two panda methods for data preparation:  
- rename()  
- set_index()  

For best practice, raw data should not be manipulated but should be either copied to a new dataset or extract the relevant variables into a new dataset.  For this exercise, the dataset is small and already modified for the calculation so will directly use and manipulate it.

A scatter plot suffices to show the relationship between the variables of interest as well as an overlay of the predicted equation or model over the data.

Three python visualization tools plot the relationship: matplotlib, pandas extension of matplotlib, and seaborn.

Lastly, the python libraries statsmodels, scipy and scikit learn that specifically computes linear regression provides an example for practical use.

##### A note about seaborn.  
The library contains 2 linear regression [methods](https://seaborn.pydata.org/tutorial/regression.html): regplot() & lmplot().   regplot() is used to show certain methods but both can be used.  Also, it computes the residuals and plots the 95% confidence interval.  This is helpful for quick exploratory data analysis.

### Discussion  
To learn linear regression, it is ideal to understand how the method derives from the equations.  To generate the linear equation for the model of the dataset, <div align="center">$\hat{y} = \hat{\beta_0} + \hat{\beta_1} x$  
</div>

the coefficients need to be calculated as follows:  
$$\hat{\beta_1} = \frac{S_{xy}}{S_{xx}}$$  
where  
$$S_{xy} = \displaystyle\sum_{i=1}^{n} {(x_i - \bar{x})}^2$$  
$$S_{xx} = \displaystyle\sum_{i=1}^{n} (x_i - \bar{x})$$  
Then the residuals are  
$$e_i = y_i - \hat{y_i}$$  
then $\hat{\beta_0} = \bar{y} - \hat{\beta_1}\bar{x}$ , where $\bar{y}$ and $\bar{x}$ are the variables mean, respectively.  

Notes:  
$i=1$ counts nominally while in python index starts at 0.  
$x_i$ & $y_i$ are the independent observations of the data  
$n$ is the number of samples  

Residuals are important because they show how good the fit of the predicted model is in relation to the data.  A large variation within the residuals would indicate the model is not fitting the data.

There is need to estimate the errors of the fitted data because obtaining the accuracy of the model is based on assumptions.  To obtain this estimate, the calculation of the **residual** or **error sum of squares** is obtained by
$$SS_{Res} = SS_{T} - \hat{\beta_1}S_{xy}$$
For the **unbiased estimator of $\sigma^2$**,
$$\hat{\sigma^2} = \frac{SS_{Res}}{n-2} = MS_{Res}$$  
and is called the **residual mean square**.  The square root value is the standard deviation or **standard error of regression**.  This is the **model-dependent** estimate of $\sigma^2$.  
To compute $SS_{T}$,  
$$SS_{T} = \sum_{i=1}^{n} (y_{i}^2 - n\bar{y}^2)$$  
so,
$$\hat{\sigma}^2 = \frac{SS_{Res}}{n-2}$$  
and the standard error of regression,
$$se = \sqrt{\hat\sigma^2}$$  

#### Hypothesis Test on the slope and intercept.  

The estimation of the data through the use of a model has many assumptions.  To test to see if the model fit the data and confined within the assumptions, this requires the procedure of at least 2 well common test, hypothesis testing and confidence interval.

Another assumption is that the error must be normally and independently distributed within the mean and variance.  The hypothesis test of the linear regression is known as the **significance of regression**.  The null hypothesis $H_{0}:\beta_1 = 0$ and the alternate hypothesis $H_{1}:\beta_1\neq 0$ examines the relationship between the variables of interest.  If the slope is 0, the null hypothesis means there is no linear relationship between the variables.  Thus, the test rejects the null hypothesis if there is a linear relationship or fails to reject if there is no relationship.

The test procedure is to evaluate $t_0$, the test statistic,
$$t_0 = \frac{\hat{\beta_1}}{\sqrt{\frac{MS_{Res}}{S_{xx}}}}$$  
the denominator is the **standard error of the slope**,
$$se(\hat\beta_1)=\sqrt{\frac{MS_{Res}}{S_{xx}}}$$  
Similarly, for the intercept,
$$t_0 = \frac{\hat{\beta_0}}{ \sqrt{ MS_{Res}(\frac{1}{n} + \frac{\bar{x}^2}{S_{xx}}) } }$$  
where the denominator is the **standard error of the intercept**,
$$se(\hat{\beta_0}) = \sqrt{ MS_{Res}(\frac{1}{n} + \frac{\bar{x}^2}{S_{xx}}) }$$  
The residual sum of squares follow a $\chi_{n-2}^{2}$ distribution so the observe value of $t_0$ is compared with the t-distribution value for a given $\alpha$, the confidence level typically 5%.  Thus,
$$\mid{t_0}\mid > t_{\alpha/2,n-2}$$  
rejects the null hypothesis, implying there is a linear relationship among the variables.


### Results  
Upon loading the data, examination shows one feature variable, xi, and one response variable, yi.  Also, the variables are continuous and quantitative.

In preparing the data, variable names are changed or renamed simply for convenience and to intuitively identify its purpose based on the name.  It also makes it easy to plot with shorter names.  In addition, the computation of several results such as $S_{xx}$ & $S_{xy}$ expands the dataset to hold the values.

Plots show the clear relationship between the two variables and a fitted line from the calculated regression is also shown.  A comparison of the three different ways to plot the data provides examples of visual inspection.

Seaborn's plot library computes the [linear regression](https://seaborn.pydata.org/tutorial/regression.html) as well as the 95% confidence interval range.  A useful feature for examining the relationship right away.

Lastly, the python libraries compute the results of the regression and these are compared to the calculations.

Statsmodels provide two ways of implementing the OLS class (Ordinary Least Squares).  The built-in method of using the design matrix requires the additional step of invoking add_constant().  The other method uses the R style invocation.  Both methods are shown.

Scipy provides a simple linear regression method for univariate variables.  However, for more in-depth computation in regression analysis, 2 other methods can be found in the optimize class:  
- curve_fit  
- leastsq  

The hypothesis test is calculated using the equations above and compares well with the results obtained from the other libraries.

### TODO
Additional writeup will cover confidence interval, multivariate regression with linear coefficients and validation.
