#Week3 
We want to find a straight line that separate each group the maximum possible
![[Pasted image 20241010194725.png]]

# Logistic Regression
![[Logistic Regression|1000]]
## Hipothesis
$$h(x_i) = w_0 + x_1w_1$$
$$s(x_i) = \frac{1}{1-e^{-h(x_i)}}$$

## Loss Function
+ Binary Cross Entropy
$$L = -\sum_{i=1}^{n}y_ilog(s(x_i))+(1-y_i)log(1-s(x_i))$$

![[Pasted image 20240904152306.png]]

## Derivatives
$$\frac{\partial L}{w_j} = \frac{1}{n}\sum_{i=0}^{n}(y_i - s(x_i))(-x_{ij})$$


