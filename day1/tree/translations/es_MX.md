# Árbol

Considera un **árbol** con $N$ **nodos**,
 numerados de $0$ a $N-1$.
El nodo $0$ se denomina la raíz.
Cada nodo, excepto por la raíz, tiene un **padre**.
Para cada $i$, tal que $1 \leq i < N$,
 el padre del nodo $i$ es $P[i]$, donde $P[i] < i$.
Además, asumimos que $P[0] = -1$.

Para cualquier nodo $i$ ($0 \leq i < N$),
 el **subárbol** de $i$ es el conjunto de los siguientes nodos: 
 * $i$, y
 * cualquier nodo cuyo padre es $i$, y
 * cualquier nodo cuyo padre tiene por padre $i$, y
 * cualquier nodo cuyo padre tiene por padre un nodo cuyo padre es $i$ 
 * etc...

La siguiente imagen muestra un ejemplo de un árbol con $N = 6$ nodos.
Cada flecha conecta un nodo con su padre,
 excepto por la raíz, que no tiene padre.
El subárbol del nodo $2$ contiene los nodos $2, 3, 4$ y $5$.
El subárbol del nodo $0$ contiene los $6$ nodos del árbol
 y el subárbol del nodo $4$ solo contiene el nodo $4$.

![](subtrees.png "150")

A cada nodo se le asigna un **peso** entero no negativo.
Denotamos el peso del nodo $i$ ($0 \leq i < N$) con $W[i]$.

Tu tarea es escribir un programa que responda $Q$ preguntas,
 cada una, contiene una pareja de enteros positivos $(L, R)$.
La respuesta a la pregunta se calcula de la siguiente manera:

Considera asignar un entero llamado **coeficiente**, a cada nodo del árbol. 
Describamos dicha asignación con la secuencia $C[0], \ldots, C[N-1]$,
 Donde $C[i]$ ($0 \leq i < N$) es el coeficiente asignado al nodo $i$.
Llamemos esta secuencia, una **secuencia de coeficientes**.
Observa que los elementos de una secuencia de coeficientes pueden ser negativos, $0$, o positivos.

Para cada pregunta $(L, R)$,
 una secuencia de coeficientes se considera **válida** 
 sí, para cada nodo $i$ ($0 \leq i < N$),
 la siguiente condición se cumple:
 la suma de los coeficientes de los nodos en el subárbol del nodo $i$
 no es menor que $L$ ni mayor que $R$.

Para una secuencia de coeficientes $C[0], \ldots, C[N-1]$,
 el **costo** de la secuencia para el nodo $i$ es $|C[i]| \cdot W[i]$,
 donde $|C[i]|$ denota el valor absoluto de $C[i]$.
Finalmente, el **costo total** es la suma de los costos de todos los nodos.
Tu tarea es calcular, para cada pregunta, 
 el **mínimo costo total** que se puede alcanzar con una secuencia de coeficientes válida. 
 
 Se puede demostrar que para cada pregunta existe al menos una configuración de coeficientes válida.

## Detalles de implementación

Debes implementar dos funciones: 

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$: son arreglos de tamaño $N$
   que describen los padres del árbol y los pesos. 
* Esta función será llamada exactamente una vez
   al inicio de la interacción entre el evaluador y tu programa en cada caso.

```
long long query(int L, int R)
```
* $L$, $R$: Los enteros describiendo la pregunta.
* Esta función es llamada $Q$ veces después de la llamada a la función `init` en cada caso.
* Esta función deberá responder un entero, la respuesta para la pregunta dada. 


## Límites

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ para cada $i$ tal que $1 \leq i < N$
* $0 \leq W[i] \leq 1\,000\,000$ para cada $i$ tal que $0 \leq i < N$
* $1 \leq L \leq R \leq 1\,000\,000$ en cada pregunta.

## Subtareas 

| Subtarea | Puntos | Restricciones adicionales |
| :-----:  | :----: | ---------------------- |
|   1      |  $10$  | $Q \leq 10$; $W[P[i]] \leq W[i]$ para cada  $i$ tal que $1 \leq i < N$
|   2      |  $13$  | $Q \leq 10$; $N \leq 2\,000$
|   3      |  $18$  | $Q \leq 10$; $N \leq 60\,000$
|   4      |  $7$   | $W[i] = 1$ para cada $i$ tal que $0 \leq i < N$
|   5      |  $11$  | $W[i] \leq 1$ para cada $i$ tal que $0 \leq i < N$
|   6      |  $22$  | $L = 1$
|   7      |  $19$  | Sin consideraciones adicionales.



## Ejemplos

Considera las siguientes llamadas:

```
init([-1, 0, 0], [1, 1, 1])
```
El árbol consiste de $3$ nodos, la raíz y sus $2$ hijos.
Todos los nodos tienen peso $1$.

```
query(1, 1)
```

En esta pregunta, $L = R = 1$,
 lo que significa que la suma de los coeficientes en cada subárbol debe ser igual a $1$. 
Considera la secuencia de coeficientes $[-1, 1, 1]$.
El árbol y sus coeficientes correspondientes (en rectángulos sombreados) están ilustrados en la imagen siguiente:

![](ex1.png "150")

Para cada nodo $i$ ($0 \leq i < 3$), la suma de los coeficientes de todos los nodos
 en el subárbol de $i$ es igual a $1$. 
Por lo tanto, esta secuencia de coeficientes es válida.
El costo total se calcula de la siguiente manera:


| Nodo | Peso | Coeficiente | Costo                     |
| :----:  | :--: | :---------: | :-----------------------: |
|   0     |   1  |     -1      | $\mid -1 \mid \cdot 1 = 1$
|   1     |   1  |      1      | $\mid 1 \mid \cdot 1 = 1$
|   2     |   1  |      1      | $\mid 1 \mid \cdot 1 = 1$

Por lo tanto, el costo total es $3$.
Esta es la única secuencia de coeficientes válida,
 entonces, la función deberá regresar $3$.

```
query(1, 2)
```
El mínimo costo total para esta pregunta es $2$,
 y la secuencia de coeficientes que lo alcanza es $[0, 1, 1]$.

## Evaluador de Ejemplo

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

Donde $L[j]$ y $R[j]$
 (para $0 \leq j < Q$)
 son los argumentos de entrada de la $j$-ésima llamada a la función `query`.
Nota que la segunda línea de la entrada consiste de **solo $N-1$ enteros**,
 pues el evaluador de ejemplo no lee el valor de $P[0]$.

Formato de salida:
```
A[0]
A[1]
...
A[Q-1]
```

Donde $A[j]$
 (para $0 \leq j < Q$)
 es el valor que regresa la $j$-ésima llamada a la función `query`.