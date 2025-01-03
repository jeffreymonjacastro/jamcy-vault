# Ariana Villegas
What is the optimization objective?
**Likelihood:** Measures if a event x correspond to a distribution
Is the probability that a point comes to a function (logistic regression)
Example:
+ Event X = approve an exam
+ $X \in [0,1]$ Approve, disapprove

Cualquier función que tenga valores entre 0 o 1 y sea diferenciable ayuda en la clasificación, como la función logística.

El objetivo es maximizar el Likehood, para que todos los puntos se aproximen a la función

La regresión lineal se le aplica una función Sigmoidea para que su dominio esté entre $-\infty$  a $\infty$ y su rango esté entre 0 y 1

Encuentra los valores de $w$ que maximicen la productoria, es decir, maximizar el Likelihood:

$$max_{w} L(w) = max_w \prod_{i=1}^{N} p(t^{(i)} | x^{(i)}; w)$$
**t:** Valores esperados (y)
**x:** Datos en los escenarios

![[Pasted image 20240911153251.png]]

Datos linealmente separables: Cuando existe una recta que puede separar los puntos en dos clases

![[Pasted image 20240911163222.png]]

![[SVM|900]]

![[Pasted image 20240913091145.png]]
![[Pasted image 20240913091517.png]]
![[Pasted image 20240913091801.png]]
![[Pasted image 20240913092806.png]]
### Multiplicadores de Lagrange
![[Pasted image 20240913102059.png]]
Karash-Kuhn-Tucker

# Profe Christian
The Logistic Regression can return any straight line, but not the best
![[Pasted image 20241010202121.png]]
SVM find the best line that best separates both groups

## Hard SVM
![[Pasted image 20241010211641.png]]
## Soft SVM
![[Soft SVM|900]]
### Hypothesis
$$h(x_i) = x_i * w^t + b$$
### Loss
$$L = \frac{1}{2} \lVert w\rVert_2^2 + C\sum_{i=0}^{n} max(0,1-y_i(x_i * w^t + b))$$
### Derivatives
If $y_i(x_iw^t+b)<1$
$$\frac{\partial L}{\partial w} = w + C \sum_{i=0}^n -y_ix_i$$
else 
$$\frac{\partial L}{\partial w} = w$$
### Update
If $y_i(x_iw^t+b)<1$
$$w = w - \alpha(w+C \sum_{i=0}^n -y_ix_i)$$
else
$$w = w - \alpha*w$$
