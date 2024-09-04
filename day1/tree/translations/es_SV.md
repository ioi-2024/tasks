# Árbol

Considera un **árbol** que consiste de $N$ **vertices**
numerados del $0$ al $N-1$.
El vértice $0$ es llamado la **raíz**.
Cada vértice, excepto por la raíz, tiene un sólo **padre**.
Para cada $i$, tal que $1 \leq i < N$,
el padre del vértice $i$ es un vértice $P[i]$, donde $P[i] < i$.
También asumimos $P[0] = -1$.

Para cualquier vértice $i$ ($0 \leq i < N$),
el **subárbol** de $i$ es el conjunto de los siguientes vértices:
 * $i$, y
 * cualquier vértice cuyo padre es $i$, y
 * cualquier vértice para el cual el padre de su padre es $i$, y
 * cualquier vértice para el cual el padre de su padre de su padre es $i$, y
 * etc.

La figura siguiente muestra un árbol de ejemplo que consiste de $N = 6$ vértices.
Cada flecha conecta un vértice a su padre,
excepto por la raíz, que no tiene padre.
El subárbol del vértice $2$ contiene a los vértices $2, 3, 4$ y $5$. 
El subárbol del vértice $0$ contiene a todos los $6$ vértices del árbol y el subárbol del vértice $4$ contiene únicamente al vértice $4$.

![](subtrees.png "150")

A cada vértice se le asigna un **peso** entero no negativo.
Denotamos al peso del vértice $i$ ($0 \leq i < N$) como $W[i]$.

Tu tarea es escribir un programa que conteste $Q$ preguntas, cada
una especificada por un par de enteros positivos $(L, R)$.
La respuesta a la pregunta debe ser calculada de la siguiente manera.

Considera asignar un entero, llamado un **coeficiente**, a cada vértice del árbol.
Dicha asignación es descrita por una secuencia $C[0], \ldots, C[N-1]$,
donde $C[i]$ ($0 \leq i < N$) es el coeficiente asignado al vértice $i$. 
Llamemos a esta secuencia una **secuencia de coeficientes**.
Nota que los elementos de la secuencia de coeficientes puede ser negativos, $0$, o positivos.

Para una pregunta $(L, R)$,
una secuencia de coeficientes es **válida**
si, para cada vértice $i$ ($0 \leq i < N$), se cumple
la siguiente condición:
la suma de los coeficientes de los vértices en el subárbol del vértice $i$ no es menor que $L$ ni mayor que $R$.

Para una secuencia de coeficientes $C[0], \ldots, C[N-1]$,
el **costo** de un vértice $i$ es $|C[i]| \cdot W[i]$,
donde $|C[i]|$ denota el valor absoluto de $C[i]$.
Finalmente, el **costo total** es la suma de los costos de todos los vértices.
Tu tarea es calcular, para cada pregunta, el **mínimo costo total** que puede ser obtenido por una secuencia de coeficientes válida.

Puede demostrarse que para cualquier pregunta, existe al menos una secuencia de coeficientes válida.

## Detalles de implementación

Debes implementar los siguientes dos procedimientos:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$: arreglos de enteros de largo  $N$
   especificando los padres y los pesos.
* Este procedimiento es llamado exactamente una vez al inicio de la interacción entre el calificador y tu programa en cada caso de prueba.

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
* $1 \leq L \leq R \leq 1\,000\,000$ en cada pregunta.

## Subtasks

| Subtarea | Puntuación | Restricciones Adicionales                                             |
|:--------:|:----------:|-----------------------------------------------------------------------|
|    1     |    $10$    | $Q \leq 10$; $W[P[i]] \leq W[i]$ para cada $i$ tal que $1 \leq i < N$ 
|    2     |    $13$    | $Q \leq 10$; $N \leq 2\,000$                                          
|    3     |    $18$    | $Q \leq 10$; $N \leq 60\,000$                                         
|    4     |    $7$     | $W[i] = 1$ para cada $i$ tal que $0 \leq i < N$                       
|    5     |    $11$    | $W[i] \leq 1$ para cada $i$ tal que $0 \leq i < N$                    
|    6     |    $22$    | $L = 1$                                                               
|    7     |    $19$    | Sin restricciones adicionales.                                        



## Ejemplo

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
El costo mínimo total de esta pregunta es $2$,
y es obtenida cuando la secuencia de coeficientes es $[0, 1, 1]$.

## Calificador Local

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
ya que el calificador local no lee el valor de $P[0]$.

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
