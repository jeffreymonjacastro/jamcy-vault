#Week2 #Week3
# Univariate Polynomial Regression 
### Model (Hypothesis)
$$h(x_i) = b + x_iw_1 + x_i^2w_2 + x_i^3w_3 + ... + x_i^pw_p$$
$$h(x_i) = b + \sum_{j=1}^{p}x_{i}^{j}w_j$$

$$h(x_i) = x_{i}^0w_0 + \sum_{j=1}^{p}x_{i}^{j}w_j$$

$$h(x_i) = \sum_{j=0}^{p}x_{i}^{j}w_j$$

Where $p$ is the polynomial degree (hyper-parameter) 
![[Pasted image 20240902232126.png|600]]


### Loss Function
$$L = \frac{1}{2n} \sum_{i=1}^{n}(y_i - h(x_i))^2 = \frac{\|Y - XW^T\|_{2}^{2}}{2n} = \frac{EE^T}{2n}$$
+ $Y$ is the original vector of y values
+ $X$ is the original vector of x values
+ $W^T$ is the transpose vector of parameter w
+ $E$ is the error vector $y - h(x)$

> The norm **L2** of a vector is the square root of the sum of the squared elements: 
> $\| \mathbf{x} \|_2 = \sqrt{x_1^2 + x_2^2 + \cdots + x_n^2}$
> For that, we elevate it to pow of 2 to eliminate the root:
> $\| \mathbf{x} \|_{2}^{2} = x_1^2 + x_2^2 + \cdots + x_n^2$
> That's why the formula is correct
### Derivatives
+ For $w_0 = b$: $\frac{\partial L}{\partial w_0} = \frac{1}{n}\sum_{i=0}^{n}(y_i - h(x_i))(-1)$
+ For $w_j$:
$$\frac{\partial L}{\partial w_j} = \frac{1}{n}\sum_{i=0}^{n}(y_i - h(x_i))(-x_{i}^{j})$$
$$\frac{\partial L}{\partial w} = \frac{1}{n}[(Y-h(X))^T \times (-1)(X)]$$
### Uploading parameters
$$W = W - \alpha \frac{\partial L}{\partial w}$$

# Regularization
How do we decrease the complexity of our model?

![[Pasted image 20240902232546.png]]
### Regularization Term
$$L = \frac{\| Y - h(X) \|_{2}^2}{2n} + \mathcal{R}(w)$$
$$L = \frac{\| Y - h(X) \|_{2}^2}{2n} + \lambda \sum_{j=1}^p w_{j}^2$$
$$L = \frac{\| Y - h(X) \|_{2}^2}{2n} + \lambda \| W \|_{2}^2$$
### The Derivatives

$$\frac{\partial L}{\partial w_j} = \frac{1}{n}[\sum_{i=0}^{n}(y_i - h(x_i))(-x_{i}^{j}) + 2\lambda w_j]$$

## Regularization Methods in Regression
### Ridge (L2)
+ **Small values of W**
+ Generates vectors with low values
+ Square the W values
$$L = \frac{\| Y - h(X) \|_{2}^2}{2n} + \lambda \| W \|_{2}^2$$
### Lasso (L1)
+ **Vector with multiple zero values**
+ Generates sparse vectors
+ Absolute Value of W
$$L = \frac{\| Y - h(X) \|_{2}^2}{2n} + \lambda \| W \|_1$$
> Careful! If the parameter $\lambda$ is too big, it will cause an underfitting. Otherwise, if $\lambda$ is too small, it will cause an overfitting 

![[Univariate Polynomial Regression|900]]


![[Pasted image 20240903001751.png]]
+  The blue point represents the minimum loss  
### Elastinet
+ The union of Ridge and Lasso
$$L = \frac{\| Y - h(X) \|_{2}^2}{2n} + \rho \lambda \| W \|_1 + (1 - \rho)\lambda \| W \|_2 $$
+ Where $\rho$ is an hyperparameter to adjust L1 and L2
+ $\rho = [0,1]$ Indicates how much of one regularization method you want
+ $\rho = 1$ Choose Lasso and $\rho = 0$ Choose Ridge 

# Coefficient of determination R²
Mean of Y: 
$$\bar Y = \frac{1}{n}\sum_{i = 0}^n{y_i}$$
Distance between y predicted and mean
$$\sum_{i=0}^n(\hat y_i - \bar Y)^2 = \lVert \hat Y - \bar Y\rVert_{2}^{2}$$
Distance between y real and Mean:
$$\sum_{i=0}^n(y_i - \bar Y)^2 = \lVert Y - \bar Y\rVert_{2}^{2}$$
So, the coefficient is:
$$R^2 = \frac{\sum_{i=0}^n(\hat y_i - \bar Y)^2}{\sum_{i=0}^n(y_i - \bar Y)^2} = \frac{\lVert \hat Y - \bar Y\rVert_{2}^{2}}{\lVert Y - \bar Y\rVert_{2}^{2}}$$
+ If $R^2$ is 1 the model predicts exactly the data (overfitting)
+ If $R^2$ is 0 the model doesn't predict the data (underfitting)
![[Pasted image 20241010190522.png|900]]
# Adjusted R²
$$R_{ajustado}^{2} = 1 - (1 - R^2) \frac{n-1}{n-p-1}$$
![[Pasted image 20241010190719.png|900]]
Is not possible to determine the amount of predictors to use

![[Pasted image 20241010192008.png|900]]

# Training, Bias and Variance
![[Pasted image 20241010191317.png|600]]
![[Pasted image 20241010191336.png|600]]
![[Pasted image 20241010191457.png|600]]
![[Pasted image 20241010191553.png]]
![[Pasted image 20241010191650.png]]
![[Pasted image 20241010191857.png]]
Overfitting: High Variance and Low Bias
Undefitting: Low Variance and High Bias
Optimal: Low Variance and Low Bias
![[Pasted image 20241010192705.png]]
# Method for evaluating the quality of generalization
![[Pasted image 20241010192757.png]]
