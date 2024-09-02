## Univariable Linear Regression

**Model:** $M = h(y_i) = xw + b$
+ $w$ : Slope
+ $b$ : Bias

**Error:** $\frac{1}{n}\sum_{i = b}^{n} d_i$
+ Is the average of all the distances between the `y_pred` to the original `y`
+ $d_i$ : distance between $y_i$ and $\dot y_i$ 

We want to minimize the error to get the best model for our data

> The error is calculated with `MSE` (Mean Square Error) or `MAE` (Mean Absolute Error)

$e_i = (y_i - \dot y_{i})^2$ <- *MSE*
$\dot y_i = x_iw + b$


![[Pasted image 20240902001036.png]]

$obj: min(\frac{1}{2n}\sum_{i=0}^{n}e_i) = min(\frac{1}{2n}\sum_{i=0}^{n}(y_i - \dot y_i)^2) = L$

**Loss Function:** $L = \frac{1}{2n}\sum_{i=0}^{n}(y_i - (x_iw + b))^2$
+ The Loss function has the shape of a quadratic function. 
+ `L1` has a great slope (w), so it has to decrease
+ `L2` has a short slope (w), so it has to increase

![[Pasted image 20240902001139.png]]

Example of a Loss Function only depending on $w$
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

**Updating the values:**
+ $w = w - \alpha \frac{\partial L}{\partial w}$
+ $b = b - \alpha \frac{\partial L}{\partial b}$
where 
+ $\frac{\partial L}{\partial w} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \dot y_i) (-x_i)$
+ $\frac{\partial L}{\partial w} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \dot y_i) (-1)$
Demostration:

![[Pasted image 20240902092640.png]]
![[Thing]]

## Multivariable Linear Regression
