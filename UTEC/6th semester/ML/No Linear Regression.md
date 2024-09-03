## Polynomial Regression
### Model (Hypothesis)
$$h(x_i) = b + x_iw_1 + x_i^2w_2 + x_i^3w_3 + ... + x_i^pw_p$$
$$h(x_i) = b + \sum_{j=1}^{p}x_{i}^{j}w_j$$

$$h(x_i) = x_{i}^0w_0 + \sum_{j=1}^{p}x_{i}^{j}w_j$$

$$h(x_i) = \sum_{j=0}^{p}x_{i}^{j}w_j$$

Where $p$ is the polynomial degree (hyper-parameter) 
![[Pasted image 20240902232126.png]]

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

## Regularization
How do we decrease the complexity of our model?

![[Pasted image 20240902232546.png]]
### Regularization Term
$$L = \frac{\| Y - h(X) \|_{2}^2}{2n} + \mathcal{R}(w)$$
$$L = \frac{\| Y - h(X) \|_{2}^2}{2n} + \lambda \sum_{j=1}^p w_{j}^2$$
$$L = \frac{\| Y - h(X) \|_{2}^2}{2n} + \lambda \| W \|_{2}^2$$
### The Derivatives

$$\frac{\partial L}{\partial w_j} = \frac{1}{n}[\sum_{i=0}^{n}(y_i - h(x_i))(-x_{i}^{j}) + 2\lambda w_j]$$

## Regularization Methods in Regression
### Ridge
+ Small values of W
+ Generates vectors with low values
$$L = \frac{\| Y - h(X) \|_{2}^2}{2n} + \lambda \| W \|_{2}^2$$
### Lasso
+ Vector with multiple zero values
+ Generates sparse vectors
$$L = \frac{\| Y - h(X) \|_{2}^2}{2n} + \lambda \| W \|_1$$
![[Pasted image 20240903001751.png]]

### Elastinet
+ The union of Ridge and Lasso
$$L = \frac{\| Y - h(X) \|_{2}^2}{2n} + \rho \lambda \| W \|_1 + (1 - \rho)\lambda \| W \|_2 $$
+ Where $\rho$ is an hyperparameter to adjust


