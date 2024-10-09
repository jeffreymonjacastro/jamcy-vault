## o - Notation
$$f(n) = o(g(n)) \rightarrow \forall \text{ c > 0: eventualmente } c*g(n) \text{ domina a f}$$
$$f(n) = o(g(n)) \rightarrow \forall \text{ c > 0 } \exists \text{ n}_0 : 0 \leq f(n) < c*g(n) \forall \text{ n} > n_0$$
**Analogía:**
Al igual que en álgebra lineal, las combinaciones lineales tenían tres tipos soluciones: infinitas, 1 o 0 soluciones. 

$f(n) = n² + 10^{10}n$ es acotado exactamente por $O(n²)$, mientras que es acotado para toda constante por $O(n³), O(n⁴), O(n²logn)...$ Por otro lado, la función no es acotada por $o(n \sqrt n)$

$$f(n) = o(g(n)) \leftrightarrow \lim_{n\rightarrow \infty} \frac{f(n)}{g(n)} = 0$$
![[jamcy-vault/Excalidraw/Divide & Conquer]]
## Merge Sort
```pseudocode
MERGE-SORT(A,p,r)
	if p >= r
		return
	MERGE-SORT(A, p, r)
```

```
MERGE(A,p,q,r)
	nL = q - p + 1
	nR = r - q
	let L[0:nL-1] and R[0:nR-1]
```

El Merge Sort se puede interpretar como un árbol binario completo cuando n es una potencia de 2