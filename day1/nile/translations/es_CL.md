# Nilo

Quieres transportar $N$ artefactos a través del Nilo. Los artefactos están enumerados desde $0$ hasta $N-1$. El peso del artefacto $i$ ($0 \leq i < N$) es $W[i]$.

Para transportar los artefactos, utilizas botes especializados. Cada bote puede llevar **a lo más dos** artefactos.

* Si decides transportar un único artefacto en un bote, el peso del artefacto puede ser arbitrario.
* Si quieres transportar dos artefactos en un mismo bote, debes asegurarte de que el bote esté balanceado uniformemente. Específicamente, puedes enviar dos artefactos $p$ y $q$ ($0 \leq p < q < N$) en el mismo sólo si la diferencia absoluta entre sus pesos es a lo más $D$; es decir, si es que $|W[p] - W[q]| \leq D$.

Para transportar un artefacto, tienes que pagar un costo que depende del número de artefactos a transportar en un mismo bote. El costo de transportar el artefacto $i$ ($0 \leq i < N$) es:

* $A[i]$, si lo colocas en su propio bote, o
* $B[i]$, si lo colocas en un bote junto con algún otro artefacto.

Ten en cuenta que en el segundo escenario tienes que pagar por ambos artefactos en el bote. Concretamente, si decides enviar los artefactos $p$ y $q$ ($0 \leq p < q < N$) en el mismo bote, deberás pagar $B[p] + B[q]$.

Enviar un artefacto en un bote por sí solo siempre es más caro que enviarlo junto con otro artefacto compartiendo el mismo bote; es decir, $B[i] < A[i]$ para todo $i$ tal que $0 \leq i < N$.

Desafortunadamente, el río es muy impredecible y el valor de $D$ cambia a menudo. Tu tarea es responder $Q$ preguntas enumeradas de $0$ a $Q-1$. Las preguntas están descritas por un arreglo $E$ de largo $Q$. La respuesta a la pregunta $j$ ($0 \leq j < Q$) es el mínimo costo total de transportar los $N$ artefactos, cuando el valor de $D$ es igual a $E[j]$.

## Detalles de implementación

Debes implementar la siguiente función:

```
std::vector<long long> calculate_costs(
    std::vector<int> W, std::vector<int> A, 
    std::vector<int> B, std::vector<int> E)
```

* $W$, $A$, $B$: arreglos de enteros, de largo $N$, que describen los pesos de los artefactos y los respectivos costos de transportarlos.
* $E$: un arreglo de enteros, de largo $Q$, que describe el valor de $D$ para cada pregunta.
* Esta función debe retornar un arreglo $R$ de $Q$ enteros que contenga el costo mínimo total de transportar los artefactos, donde $R[j]$ representa el costo cuando el valor de $D$ es $E[j]$ (para cada $j$ tal que $0 \leq j < Q$).
* Esta función es llamada exactamente una vez por cada caso de prueba.

## Restricciones

* $1 \leq N \leq 100\,000$
* $1 \leq Q \leq 100\,000$
* $1 \leq W[i] \leq 10^{9}$
   para cada $i$ tal que $0 \leq i < N$
* $1 \leq B[i] < A[i] \leq 10^{9}$
   para cada $i$ tal que $0 \leq i < N$
* $1 \leq E[j] \leq 10^{9}$
   para cada $j$ tal que $0 \leq j < Q$

## Subtareas

| Subtarea | Puntaje  | Restricciones adicionales |
| :-----: | :----: | ---------------------- |
| 1       | $6$    | $Q \leq 5$; $N \leq 2000$; $W[i] = 1$ para cada $i$ tal que $0 \leq i < N$
| 2       | $13$   | $Q \leq 5$; $W[i] = i+1$ para cada $i$ tal que $0 \leq i < N$
| 3       | $17$   | $Q \leq 5$; $A[i] = 2$ and $B[i] = 1$ para cada $i$ tal que $0 \leq i < N$
| 4       | $11$   | $Q \leq 5$; $N \leq 2000$
| 5       | $20$   | $Q \leq 5$
| 6       | $15$   | $A[i] = 2$ and $B[i] = 1$ para cada $i$ tal que $0 \leq i < N$
| 7       | $18$   | Sin restricciones adicionales.

## Ejemplo

Considera la siguiente llamada:

```
calculate_costs([15, 12, 2, 10, 21],
                [5, 4, 5, 6, 3],
                [1, 2, 2, 3, 2],
                [5, 9, 1])
```

En este ejemplo tenemos $N = 5$ artefactos y $Q = 3$ preguntas.

En la primera pregunta, $D = 5$. Puedes enviar los artefactos $0$ y $3$ en un mismo bote (puesto que $|15 - 10| \leq 5$) y el resto de los artefactos en botes separados. Esto produce el costo mínimo para transportar todos los artefactos, el cual es $1+4+5+3+3 = 16$.

En la segunda pregunta, $D = 9$. Puedes enviar los artefactos $0$ y $1$ en un mismo bote (puesto que $|15 - 12| \leq 9$) y enviar los artefactos $2$ y $3$ en un mismo bote (puesto que $|2 - 10| \leq 9$). El artefacto restante puede enviarse en un bote aparte. Esto produce el costo mínimo para transportarlos a todos, el cual es $1+2+2+3+3 = 11$.

En la última pregunta, $D = 1$. Tienes que enviar cada artefacto en su propio bote. Esto produce el costo mínimo para transportar todos los artefactos, el cual es $5+4+5+6+3 = 23$.

Por lo tanto, la función debe retornar $[16, 11, 23]$.

## Evaluador de ejemplo

Formato de entrada: 
```
N
W[0] A[0] B[0]
W[1] A[1] B[1]
...
W[N-1] A[N-1] B[N-1]
Q
E[0]
E[1]
...
E[Q-1]
```

Formato de salida:
```
R[0]
R[1]
...
R[S-1]
```

Aquí, $S$ es el largo del arreglo $R$ retornado por `calculate_costs`.