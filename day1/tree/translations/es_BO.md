# Árbol

Considera un **árbol** formado por $N$ **vértices**,
 enumerados de $0$ a $N-1$.
El vértice $0$ es llamado vértice **raíz**.
Todos los vértices, a excepción del vértice raíz, tienen un solo **padre**.
Para todo $i$, tal que $1 \leq i < N$,
 el padre del vértice $i$ es el vértice $P[i]$, donde $P[i] < i$.
También asumimos que $P[0] = -1$.

Para todo vértice $i$ ($0 \leq i < N$),
 el **subárbol** de $i$ es el conjunto formado por los siguientes vértices:
 * vértice $i$, 
 * cualquier vértice cuyo padre sea $i$,
 * cualquier vértice que tenga como padre del padre al vértice $i$,
 * cualquier vértice que tenga como padre del padre del padre al vértice $i$,
 * etc.

La imagen de abajo muestra un árbol de ejemplo que consiste de $N = 6$ vértices.
Las flechas muestran la conexión de un vértice con su padre,
 a excepción de la raíz, que no tiene vértice padre.
El subárbol del vértice $2$ contiene a los vértices $2, 3, 4$ y $5$.
El subárbol del vértice $0$ contiene a los $6$ vértices del árbol
 y el subárbol del vértice $4$ contiene únicamente al vértice $4$.

![](subtrees.png "150")

A todos los vértices se les asigna un **peso**, el cual es un número entero no negativo.
Denotamos al peso del vértice $i$ ($0 \leq i < N$) por $W[i]$.

Tu tarea es escribir un programa que responda $Q$ consultas,
 cada una de las consultas contendrá dos números enteros positivos $(L, R)$.
La respuesta a cada consulta debe ser calculada de la siguiente forma.

Considera: Asignamos un numero entero a cada vértice del árbol,
 a este número lo llamamos **coeficiente**.
Tal asignación esta descrita por la secuencia $C[0], \ldots, C[N-1]$,
 donde $C[i]$ ($0 \leq i < N$) es el coeficiente asignado al vértice $i$.
Denominemos a esta secuencia como **secuencia de coeficientes**.
Es importante notar que los elementos de la secuencia de coeficientes pueden ser negativos, $0$, o positivos.

Para una consulta con los valores $(L, R)$,
 una secuencia de coeficientes es considerada **valida**
 si, para todo vértice $i$ ($0 \leq i < N$),
 las siguientes condiciones se cumplen:
 la suma de los coeficientes de los vértices presentes en el subárbol del vértice $i$
 es no menor a $L$ y no mayor a $R$.

Para una secuencia de coeficientes $C[0], \ldots, C[N-1]$,
 el **costo** de un vértice $i$ es $|C[i]| \cdot W[i]$,
 donde $|C[i]|$ es igual al valor absoluto de $C[i]$.
Finalmente, el **costo total** es la suma de los costos de todos los vértices.
Tu tarea es calcular, para cada consulta,
 el **mínimo costo total** que se puede obtener con alguna secuencia de coeficientes valida.

Se puede demostrar que para cada consulta existe al menos una secuencia de coeficientes valida.

## Detalles de implementación

Debes implementar las dos siguientes funciones:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$: arreglos de números enteros con tamaño $N$
   especificando los padres y los pesos de los vertices.
* Esta función es llamada exactamente una vez al inicio de la interacción entre el evaluador y tu programa en cada caso de prueba.

```
long long query(int L, int R)
```
* $L$, $R$: números enteros que describen una consulta.
* Esta función será llamada $Q$ veces luego de la llamada a la función `init` en cada caso de prueba.
* Esta función debe devolver la respuesta a la consulta dada.


## Limites

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ para todo $i$ tal que $1 \leq i < N$
* $0 \leq W[i] \leq 1\,000\,000$ para todo $i$ tal que $0 \leq i < N$
* $1 \leq L \leq R \leq 1\,000\,000$ en cada consulta

## Subtareas

| Subtarea | Puntaje  | Restricciones adicionales |
| :-----: | :----: | ---------------------- |
|   1     |  $10$  | $Q \leq 10$; $W[P[i]] \leq W[i]$ para todo $i$ tal que $1 \leq i < N$
|   2     |  $13$  | $Q \leq 10$; $N \leq 2\,000$
|   3     |  $18$  | $Q \leq 10$; $N \leq 60\,000$
|   4     |  $7$   | $W[i] = 1$ para todo $i$ tal que $0 \leq i < N$
|   5     |  $11$  | $W[i] \leq 1$ para todo $i$ tal que $0 \leq i < N$
|   6     |  $22$  | $L = 1$
|   7     |  $19$  | Limites originales.



## Ejemplos

Considera las siguientes llamadas:

```
init([-1, 0, 0], [1, 1, 1])
```
El árbol en este caso consiste de $3$ vértices, el vértice raíz y sus $2$ hijos.
Todos los vértices tienen un peso igual a $1$.

```
query(1, 1)
```

En esta consulta $L = R = 1$,
 lo que significa que la suma de coeficientes en cada subárbol debe ser igual a $1$.
Considera la secuencia de coeficientes $[-1, 1, 1]$.
El árbol y sus correspondientes coeficientes (en rectángulos sombreados) están ilustrados en la siguiente imagen.

![](ex1.png "150")

Para todo vértice $i$ ($0 \leq i < 3$), la suma de los coeficientes de todos los vértices
 en el subárbol de $i$ es igual a $1$. 
Por lo tanto, esta secuencia de coeficientes es válida.
El costo total es calculado de la siguiente forma:


| Vértice | Peso | Coeficiente | Costo                      |
| :----: | :----: | :---------: | :-----------------------: |
|   0    |   1    |     -1      | $\mid -1 \mid \cdot 1 = 1$
|   1    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$
|   2    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$

Por lo tanto, el costo total es igual a $3$.
Esta es la única secuencia de coeficientes valida,
 entonces la función debe devolver $3$.

```
query(1, 2)
```
El costo mínimo para esta consulta es igual a $2$,
 y esta se consigue cuando la secuencia de coeficientes es $[0, 1, 1]$.

## Evaluador

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
 son los argumentos de entrada en la $j$-esima llamada a la función `query`.
Nota que la segunda línea de la entrada contiene **solo $N-1$ enteros**,
 porque el evaluador no lee el valor de $P[0]$.

Formato de salida:
```
A[0]
A[1]
...
A[Q-1]
```

donde $A[j]$
 (para $0 \leq j < Q$)
 es el valor devuelto por la $j$-esima llamada a la función `query`.
