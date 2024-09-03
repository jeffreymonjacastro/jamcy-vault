## Polynomial Regression
### Model (Hypothesis)
$$h(x_i) = b + x_iw_1 + x_i^2w_2 + x_i^3w_3 + ... + x_i^pw_p$$
Where $p$ is the polynomial degree (hyper-parameter) 
### Loss Function
$$L = \frac{1}{2n} \sum_{i=1}^{n}(y_i - h(x_i))^2 = \frac{\|Y - XW^T\|_{2}^{2}}{2n}$$

+ $Y$ is the original vector of y values
+ $X$ is the original vector of x values
+ $W^T$ is the transpose vector of w
The norm **L2** of a vector is the square root of the sum of the squared elements:
$\| \mathbf{x} \|_2 = \sqrt{x_1^2 + x_2^2 + \cdots + x_n^2}$
For that, we elevate it to pow of 2 to eliminate the root:
$\| \mathbf{x} \|_{2}^{2} = x_1^2 + x_2^2 + \cdots + x_n^2$
That's why the formula is correct
### Derivatives
+ For $w_0 = b$: $\frac{\partial L}{\partial w_0} = \frac{1}{n}\sum_{i=0}^{n}(y_i - h(x_i))(-1)$
+ For $w_j$:
$$\frac{\partial L}{\partial w_j} = \frac{1}{n}\sum_{i=0}^{n}(y_i - h(x_i))(-x_{i}^{j})$$

## Regularization
