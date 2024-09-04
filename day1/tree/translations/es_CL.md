# Árbol

Considera un  **árbol** compuesto de $N$ **vértices** numerados de  $0$ a $N-1$. El vértice $0$ corresponde a la  **raíz**.
Cada vértice, excepto la raíz, tiene un único **padre**. Para cada  $i$, tal que $1 \leq i < N$, el padre del vértice $i$ es el vértice $P[i]$, con $P[i] < i$. Además, asumimos que  $P[0] = -1$.

Para cada vértice $i$ ($0 \leq i < N$), el **subárbol** de  $i$ es el conjunto conformado por los siguientes vértices:
 * $i$, y
 * cualquier vértice cuyo padre sea $i$, y
 * cualquier vértice tal que el padre de su padre sea $i$, y
 * cualquier vértice tal que el padre del padre de su padre sea $i$, y
 * así sucesivamente.

La siguiente figura muestra un ejemplo de un árbol con $N = 6$ vértices. Cada flecha conecta un vértice a su padre, excepto para la raíz, que no tiene padre. El subárbol del vértice $2$ está conformado por los vértices $2, 3, 4$ y $5$. El subárbol del vértice $0$ contiene los $6$ vértices del árbol y el subárbol del vértice $4$ está conformado solamente por el vértice $4$.

![](subtrees.png "150")

A cada vértice se le asigna un **peso** entero no negativo. Denotamos el peso del vértice  $i$ ($0 \leq i < N$) como $W[i]$.

Tu tarea es escribir un programa que responda $Q$ consultas, cada una especificada por un par de enteros positivos $(L, R)$. La respuesta a la consulta se debe calcular como sigue.

Considera asignar un entero, llamado **coeficiente**, a cada vértice del árbol. Tal asignación se describe con una secuencia $C[0], \ldots, C[N-1]$, donde $C[i]$ ($0 \leq i < N$) es el coeficiente asignado al vértice $i$. Llamemos a esta secuencia una **secuencia de coeficientes**. Ten en cuenta que los elementos de la secuencia de coeficientes pueden ser negativos, $0$, o positivos.

Dada una consulta  $(L, R)$, decimos que una secuencia de coeficientes es válida para esa consulta  e para cada vértice $i$ ($0 \leq i < N$), se cumple la siguiente condición: la suma de los coeficientes de los vértices en el subárbol del vértice $i$ no es menor que $L$ y no es mayor que $R$.

Para una secuencia de coeficientes $C[0], \ldots, C[N-1]$, el **costo** de un vértice $i$ es $|C[i]| \cdot W[i]$, donde $|C[i]|$ denota el valor absoluto de $C[i]$. Finalmente, el **costo total** es la suma de los costos de todos los vértices. Tu tarea es calcular, para cada consulta, el **costo mínimo total** que se puede obtener por alguna secuencia válida de coeficientes.
 
Se puede demostrar que para cualquier consulta, existe al menos una secuencia de coeficientes válida.

## Detalles de Implementación

Debes implementar las siguientes dos funciones:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$: arreglos de enteros de largo $N$, especificando los padres y los pesos.
* Esta función es llamada exactamente una vez al comienzo de la interacción entre el evaluador y tu programa en cada caso de prueba.

```
long long query(int L, int R)
```
* $L$, $R$: enteros que describen una consulta.
* Esta función se llama $Q$ veces después de la invocación de `init` en cada caso de prueba.
* Esta función debe retornar la respuesta a la consulta dada.


## Restricciones

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ para cada  $i$ tal que $1 \leq i < N$
* $0 \leq W[i] \leq 1\,000\,000$ para cada  $i$ tal que $0 \leq i < N$
* $1 \leq L \leq R \leq 1\,000\,000$ en cada consulta

## Subtareas

| Subtarea | Puntaje  | Restricciones Adicionales |
| :-----: | :----: | ---------------------- |
|   1     |  $10$  | $Q \leq 10$; $W[P[i]] \leq W[i]$ para cada $i$ tal que $1 \leq i < N$
|   2     |  $13$  | $Q \leq 10$; $N \leq 2\,000$
|   3     |  $18$  | $Q \leq 10$; $N \leq 60\,000$
|   4     |  $7$   | $W[i] = 1$ para cada $i$ tal que $0 \leq i < N$
|   5     |  $11$  | $W[i] \leq 1$ para cada $i$ tal que $0 \leq i < N$
|   6     |  $22$  | $L = 1$
|   7     |  $19$  | Sin restricciones adicionales.


## Ejemplos

Considera las siguientes llamadas:

```
init([-1, 0, 0], [1, 1, 1])
```
El árbol consta de $3$ vértices, la raíz y sus $2$ hijos. Todos los vértices tienen peso $1$.

```
query(1, 1)
```

En esta consulta $L = R = 1$, lo cual significa que la suma de los coeficientes en cada subárbol debe ser igual a $1$. Considera la secuencia de coeficientes $[-1, 1, 1]$. El árbol y sus respectivos coeficientes (en rectángulos sombreados) se ilustran a continuación.

![](ex1.png "150")

Para cada vértice $i$ ($0 \leq i < 3$), la suma de los coeficientes de todos los vértices en el subárbol $i$ es igual a $1$. Por lo tanto, esta secuencia de coeficientes es válida. El costo total se calcula como sigue:


| Vértice | Peso | Coeficiente | Costo                      |
| :----: | :----: | :---------: | :-----------------------: |
|   0    |   1    |     -1      | $\mid -1 \mid \cdot 1 = 1$
|   1    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$
|   2    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$

Luego, el costo total es $3$. Esta es la única secuencia de coeficientes válida, por lo tanto esta llamada debe retornar $3$.

```
query(1, 2)
```
El costo mínimo total para esta consulta es  $2$ y se obtiene con la secuencia de coeficientes $[0, 1, 1]$.

## Evaluador de Ejemplo

Formato de Entrada:

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

donde $L[j]$ y $R[j]$ (para $0 \leq j < Q$) son los argumentos de entrada en la $j$-ésima llamada a `query`. Nota que la segunda línea de la entrada contiene **solamente $N-1$ enteros**, dado que el evaluador de ejemplo no lee el valor de  $P[0]$.

Formato de salida:
```
A[0]
A[1]
...
A[Q-1]
```

donde  $A[j]$ (para $0 \leq j < Q$) es el valor retornado por la  $j$-ésima llamada a `query`.