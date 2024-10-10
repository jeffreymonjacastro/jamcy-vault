---
noteID: 3b1adb2f-cecf-4fca-b573-d796e45d117d
---
## Univariable Linear Regression

### Model
+ $M = h(y_i) = xw + b$
+ $w$ : Slope
+ $b$ : Bias

### Error
+ $\frac{1}{n}\sum_{i = b}^{n} d_i$
+ Is the average of all the distances between the `y_pred` to the original `y`
+ $d_i$ : distance between $y_i$ and $\dot y_i$ 

We want to minimize the error to get the best model for our data

> The error is calculated with `MSE` (Mean Square Error) or `MAE` (Mean Absolute Error)

$e_i = (y_i - \dot y_{i})^2$ <- *MSE*
$\dot y_i = x_iw + b$

![[Pasted image 20240902001036.png]]

$obj: min(\frac{1}{2n}\sum_{i=0}^{n}e_i) = min(\frac{1}{2n}\sum_{i=0}^{n}(y_i - \dot y_i)^2) = L$

### Loss Function
+ $L = \frac{1}{2n}\sum_{i=0}^{n}(y_i - (x_iw + b))^2$
+ The Loss function has the shape of a quadratic function
	+ x-axis = Slope $(w)$ 
	+ y-axis = Loss $(L)$
![[Pasted image 20240902001139.png]]
+ `L1` has a great slope (w), so it has to decrease
+ `L2` has a short slope (w), so it has to increase
#### Example of a Loss Function only depending on $w$
$L(w) = \frac{1}{2n}\sum_{i=0}^{n}(y_i - x_iw)^2$

![[Pasted image 20240902085149.png]]

Python plot of Loss Function
```python
import numpy as np
import matplotlib.pyplot as plt

# Datos de ejemplo
x_i = np.array([1, 2, 3, 4])
y_i = np.array([2, 3, 5, 7])

# Calcular parámetros A y B
A = np.sum(y_i * x_i)
B = np.sum(x_i ** 2)
print(A)
print(B)

# Definir el rango de w
w = np.linspace(-10, 10, 100)
print(w[0])

# Calcular la función de pérdida
L = (1 / (2 * len(x_i))) * (np.sum(y_i ** 2) - 2 * w * A + w ** 2 * B)
print(L[0])

# Graficar la función de pérdida
plt.plot(w, L)
plt.xlabel('w')
plt.ylabel('Loss')
plt.title('Gráfico de la Función de Pérdida para Regresión Lineal')
plt.show()
```

### Derivatives
+ $\frac{\partial L}{\partial w} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \dot y_i) (-x_i)$
+ $\frac{\partial L}{\partial b} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \dot y_i) (-1)$

When $\frac{\partial L}{\partial w} > 0$ means that the $w$ is big, so it has to decrease, but when $\frac{\partial L}{\partial w} < 0$ means that the $w$ is short, so it has to increase.

Demostration:
![[Univariable Loss function derivative demostration]]
### Updating the values
+ $w = w - \alpha \frac{\partial L}{\partial w}$
+ $b = b - \alpha \frac{\partial L}{\partial b}$
where $\alpha$ is a learning rate given by the user
### Some practice

## Multivariable Linear Regression
Is used for models that depends on more than one variable or feature
### Bidimensional (2 variables)
Instead of a line, we need a plane that best fits the set of points

#### Plane Equation
$$ax_1 + bx_2 + c = 0 \rightarrow x_1w_1 + x_2w_2 + b = 0$$
![[Pasted image 20240902192041.png]]
#### Model (Hypothesis)
$$h(x_i) = x_{i1}w_1 + x_{i2}w_2 + b$$
+ $x_1, x_2$ are the features
+ $w_1, w_2$ are angles
+ $b$ is the bias

#### Loss Function
![[Pasted image 20240902192615.png]]
$$L = \frac{1}{2n} \sum_{i = 1}^{n}(y_i - h(x_i))^2$$
+ x-axis = Slope $(w)$ 
+ y-axis = Loss $(L)$

#### Derivates
+ $\frac{\partial L}{\partial w_1} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \dot y_i) (-x_{i1})$
+ $\frac{\partial L}{\partial w_2} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \dot y_i) (-x_{i2})$
+ $\frac{\partial L}{\partial b} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \dot y_i) (-1)$

#### Upload parameters
$$w_i = w_i - \alpha \frac{\partial L}{\partial w_i}, \forall i \le n$$
#### Matrix operations
![[Matrix operations in 2-Dimensional|900]]
### K-Dimensional (k variables)
Various features

#### Model (Hypothesis)
$$h(x_i) = x_{i1}w_1 + x_{i2}w_2 + ... + x_{ik}w_k + b$$
![[Pasted image 20240902231611.png]]

#### Loss Function
$$L = \frac{1}{2n} \sum_{i = 1}^{n}(y_i - h(x_i))^2$$
![[Pasted image 20240902231642.png]]
#### Derivatives
$$\frac{\partial L}{\partial w_j} = \frac{1}{n} \sum_{i = 0}^{n}(y_i - h(x_i))(-x_{ij})$$
Where $w_0 = b$ : $\frac{\partial L}{\partial w_0} = \frac{1}{n} \sum_{i=1}^{n} (y_i - h(x_i)) (-1)$
![[Pasted image 20240902231704.png]]

#### Update parameters
$$w_i = w_i - \alpha \frac{\partial L}{\partial w_i}, \forall i \le n$$
$$W = W - \alpha \frac{\partial L}{\partial w}$$
Where $W$ is the vector of w
#### Matrix operations
![[Matrix operations in k dimensions|900]]

