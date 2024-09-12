## Logistic Regression
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

![[SVM]]