# Tree

Considerar un **tree** (arbol) que consiste en  $N$ **vertices**,
numerados desde $0$ hasta $N-1$.
El vertice $0$ es llamado **root**.
Cada vertice, excepto la raiz(root), tiene un unico **parent** (padre).
para cada $i$, dado que $1 \leq i < N$,
el padre del vertice $i$ es el vertice $P[i]$, donde $P[i] < i$.
Tambien asumimos que $P[0] = -1$.

Para cualquier vértice $i$ ($0 \leq i < N$),
el  **subtree** (sub-arbol) de $i$ es el conjunto de los siguientes vértices:
 * $i$, y
 * cualquier vértice cuyo padre sea $i$, y
 * cualquier vertice cuyo padre de su padre sea  $i$, y
 * cualquier vertice cuyo padre del padre de su padre sea $i$, y
 * etc.

La siguiente imagen muestra un ejemplo de árbol que consta de $N = 6$ vértices.
Cada flecha conecta un vértice con su padre,
 excepto la raiz, que no tiene padre.
El sub-árbol de vértice $2$ contiene los vertices $2, 3, 4$ y $5$.
El sub-árbol de vértice $0$ contiene todos los $6$ vertices del árbol
y el sub-árbol de vértice $4$ contiene solo el vértice $4$.

![](subtrees.png "150")

Cada vertice tiene asigando un **weight** (peso) no negativo.
Denotamos el peso del vertice  $i$ ($0 \leq i < N$) como $W[i]$.

Tu tarea es escribir un programa que responda $Q$ consultas,
 cada una especificada por un par de enteros $(L, R)$.
La respuesta a la consulta debe ser calculada como sigue. 

Considera asignar un entero,
 llamado **coefficient** (coeficiente), a cada vertice del árbol.
Tal asignación se describe mediante una secuencia $C[0], \ldots, C[N-1]$,
 donde $C[i]$ ($0 \leq i < N$)  es el coeficiente asignado al vertice $i$.
Lamaremos a esta secuencia **coefficient sequence**.
Nótese que los elementos de la secuencia de coeficientes pueden ser negativos, $0$, o positivos.

Para una consulta $(L, R)$,
Una secuencia de coeficientes se llama **valid**
 si, para cada vertice $i$ ($0 \leq i < N$),
se cumplen las siguientes condicones:
la suma de los coeficientes de los vértices en el subárbol del vértice $i$
no es menor a $L$ ni mas grande que $R$.

Para una secuencia de coeficientes $C[0], \ldots, C[N-1]$,
 el  **cost** (costo) de un vertice $i$ es $|C[i]| \cdot W[i]$,
 donde $|C[i]|$ denota el valor absoluto de $C[i]$.
Finalmente, el **total cost** es la suma de los costos de todos los vértices.
Su tarea es calcular, para cada consulta,
 el  **minimum total cost** (costo minimo total) que puede lograrse mediante alguna secuencia de coeficientes válida.

## Detalles de implementacion

Debes implementar los dos procedimientos siguientes:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$: arreglos de enteros de tamaño $N$
especificando los padres y los pesos.
* Este procedimiento se llama exactamente una vez
	 al comienzo de la interacción entre el grader y tu programa en cada caso de prueba

```
long long query(int L, int R)
```
* $L$, $R$: enteros describiendo una pregunta.
* Este procedimiento es llamado $Q$ veces después de la llamada a `init`
en cada caso de prueba.
* Este procedimiento debe retornar la respuesta a la pregunta dada.


## Restricciones

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ para cada $i$ tal que $1 \leq i < N$
* $0 \leq W[i] \leq 1\,000\,000$ para cada $i$ tal que $0 \leq i < N$
* $1 \leq L \leq R \leq 1\,000\,000$ en cada pregunta

## Subtasks

| Subtask | Score  | Additional Constraints |
| :-----: | :----: | ---------------------- |
|   1     |  $10$  | $Q \leq 10$; $W[P[i]] \leq W[i]$ para cada $i$ tal que $1 \leq i < N$
|   2     |  $13$  | $Q \leq 10$; $N \leq 2\,000$
|   3     |  $18$  | $Q \leq 10$; $N \leq 60\,000$
|   4     |  $7$   | $W[i] = 1$ para cada $i$ tal que $0 \leq i < N$
|   5     |  $11$  | $W[i] \leq 1$ para cada $i$ tal que $0 \leq i < N$
|   6     |  $22$  | $L = 1$
|   7     |  $19$  | Sin restricciones adicionales.



## Ejemplos

Considere las llamadas siguientes:

```
init([-1, 0, 0], [1, 1, 1])
```

El árbol que consiste de $3$ vértices: la raíz y sus $2$ hijos.
Todos los vértices tienen peso $1$.

```
query(1, 1)
```

En esta pregunta $L = R = 1$,
que significa que la suma de los coeficientes en cada subárbol debe ser igual a $1$.
Considere la secuencia de coeficientes $[-1, 1, 1]$.
El árbol y los coeficientes correspondientes (en rectángulos sombreados) son ilustrados a continuación.

![](ex1.png "150")

Para cada vértice $i$ ($0 \leq i < 3$), la suma de los coeficientes de todos los vértices en el subárbol de $i$ es igual a $1$.
Por lo tanto, esta secuencia de coeficientes es válida.
El costo total se calcula de la siguiente manera:


| Vértice | Peso | Coeficiente |           Costo            |
|:-------:|:----:|:-----------:|:--------------------------:|
|    0    |  1   |     -1      | $\mid -1 \mid \cdot 1 = 1$ 
|    1    |  1   |      1      | $\mid 1 \mid \cdot 1 = 1$  
|    2    |  1   |      1      | $\mid 1 \mid \cdot 1 = 1$  

Por lo tanto, el costo total es $3$.
Esta es la única secuencia válida de coeficientes; por lo tanto, esta llamada debe retornar $3$.


```
query(1, 2)
```
El costo total de esta pregunta es $2$,
y es obtenida cuando la secuencia de coeficientes es $[0, 1, 1]$.

## Calificador Local (Grader)

Formato de entrada:

```
N
P[1]  P[2] ...  P[N-1]
W[0]  W[1] ...  W[N-2] W[N-1]
Q
L[0]  R[0]
L[1]  R[1]
...
L[Q-1]  R[Q-1]
```

donde $L[j]$ y $R[j]$
 (para $0 \leq j < Q$)
 son los parámetros de entrada en la $j$-ésima llamada a `query`.
Nota que la segunda línea de entrada contiene **únicamente $N-1$ enteros**,
ya que el calificador local(Grader) no lee el valor de $P[0]$.

Formato de salida:
```
A[0]
A[1]
...
A[Q-1]
```

donde $A[j]$
 (para $0 \leq j < Q$)
es el valor retornado por la $j$-ésima llamada a `query`.