**Model:** $M = h(y_i) = xw + b$
+ $w$ : Slope
+ $b$ : Bias

**Error:** $\frac{1}{n}\sum_{i = b}^{n} d_i$
+ Is the average of all the distances between the `y_pred` to the original `y`
+ $d_i$ : distance between $y_i$ and $\dot y_i$ 

We want to minimize the error to get the best model for our data

> The error is calculated with `MSE` (Minimum Square Error) or `MAE` (Minimum Absolute Error)

$e_i = (y_i - \dot y_{i})^2$ <- *MSE*
$\dot y_i = x_iw + b$

![[Pasted image 20240902001036.png]]

$obj: min(\frac{1}{2n}\sum_{i=0}^{n}e_i) = min(\frac{1}{2n}\sum_{i=0}^{n}(y_i - \dot y_i)^2) = L$

**Loss Function:** $L = \frac{1}{2n}\sum_{i=0}^{n}(y_i - (x_iw + b))^2$
+ The Loss function has the shape of a quadratic function. 
+ L1 has a great slope (w), so it has to decrease
+ L2 has a short slope (w), so it has to increase

![[Pasted image 20240902001139.png]]

**Updating the values:**
+ $w = w - \alpha \frac{\partial L}{\partial w}$
+ $b = b - \alpha \frac{\partial L}{\partial b}$

![[Thing]]
