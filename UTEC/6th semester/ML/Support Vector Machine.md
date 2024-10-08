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

![[SVM|900]]

![[Pasted image 20240913091145.png]]
![[Pasted image 20240913091517.png]]
![[Pasted image 20240913091801.png]]
![[Pasted image 20240913092806.png]]
### Multiplicadores de Lagrange
![[Pasted image 20240913102059.png]]
Karash-Kuhn-Tucker

![[testing.pdf#page=1&rect=14,734,356,830|testing, p.1]]
> [!PDF|sky] [[A user guide to SVM.pdf#page=1&selection=4,0,4,8&color=sky|A user guide to SVM, p.1]]
> > Abstract
> 
> Skyblue

> [!PDF|pink] [[A user guide to SVM.pdf#page=1&selection=6,4,6,33&color=pink|A user guide to SVM, p.1]]
> > Support Vector Machine (SVM) 
> 
> Pink!

