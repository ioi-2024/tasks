# Nilo

Quieres transportar $N$ artefactos por el Nilo. Los artefactos están numerados desde $0$ hasta $N-1$. El peso del artefacto $i$ ($0 \leq i < N$) es $W[i]$.

Para transportar los artefactos usas barcos especiales. Cada barco puede transportar **a lo más dos** artefactos.
* Si decides transportar un solo artefacto en un barco, el peso del artefacto puede ser cualquiera.
* Si quieres transportar dos artefactos en el mismo barco, tienes que estar seguro de que el barco quedará balanceado. Formalmente, puedes enviar los artefactos $p$ y $q$ ($0 \leq p < q < N$) en el mismo barco solo si la diferencia absoluta entre sus pesos es a lo más $D$, es decir $|W[p] - W[q]| \leq D$.

Para transportar un artefacto, tienes que pagar un costo que depende del número total de artefactos transportados en el mismo barco. El costo de transportar el artefacto $i$ ($0 \leq i < N$) es:

* $A[i]$, si colocas el artefacto en su propio barco, o
* $B[i]$, si colocas el artefacto junto a otro artefacto.

Notar que en el segundo caso, tienes que pagar por ambos artefactos transportados en el barco. Formalmente, si transportas los artefactos $p$ y $q$ ($0  \leq p < q < N$) en el mismo barco, tienes que pagar $B[p] + B[q]$.

Transportar un solo artefacto en un barco es siempre más costoso que transportarlo junto a otro artefacto en el mismo barco, es decir $B[i] < A[i]$ para todo $i$ tal que $0 \leq i < N$.

Desafortunadamente, el río es muy impredecible y el valor de $D$ cambia frecuentemente. Tu tarea es responder $Q$ preguntas, numeradas desde $0$ hasta $Q-1$. Las preguntas están descritas por un arreglo $E$ de tamaño $Q$. La respuesta a la pregunta $j$ ($0 \leq j < Q$) es el mínimo costo total de transportar todos los $N$ artefactos, cuando el valor de $D$ es igual a $E[j]$.

## Detalles de Implementación

Debes implementar la siguiente función.

```
std::vector&lt;long long&gt; calculate_costs(
    std::vector&lt;int&gt; W, std::vector&lt;int&gt; A, 
    std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```

* $W$, $A$, $B$: arreglos de enteros de tamaño $N$ que describen los pesos de los artefactos y los costos de transportarlos.
* $E$: un arreglo de enteros de longitud $Q$ que describen los diferentes valores de $D$.
* Esta función debe retornar un arreglo $R$ de $Q$ enteros que contiene el mínimo costo total de transportar los artefactos, donde $R[j]$ representa el costo cuando el valor de $D$ es $E[j]$ (para cada $j$ tal que $0 \leq j < Q$).
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

| Subtarea | Puntos  | Restricciones adicionales |
| :-----: | :----: | ---------------------- |
| 1       | $6$    | $Q \leq 5$; $N \leq 2000$; $W[i] = 1$ para cada $i$ tal que $0 \leq i < N$
| 2       | $13$   | $Q \leq 5$; $W[i] = i+1$ para cada $i$ tal que $0 \leq i < N$
| 3       | $17$   | $Q \leq 5$; $A[i] = 2$ and $B[i] = 1$ para cada $i$ tal que $0 \leq i < N$
| 4       | $11$   | $Q \leq 5$; $N \leq 2000$
| 5       | $20$   | $Q \leq 5$
| 6       | $15$   | $A[i] = 2$ and $B[i] = 1$ para cada $i$ tal que $0 \leq i < N$
| 7       | $18$   | Sin restricciones adicionales.

## Ejemplos

### Ejemplo 1

Considera la siguiente llamada.

```
calculate_costs([15, 12, 2, 10, 21],
                [5, 4, 5, 6, 3],
                [1, 2, 2, 3, 2],
                [5, 9, 1])
```


En este ejemplo se tiene $N = 5$ artefactos y $Q = 3$ preguntas.

En la primera pregunta, $D = 5$.
Puedes transportar los artefactos $0$ y $3$ en un mismo barco (ya que $|15 - 10| \leq 5$) y los demás artefactos los puedes transportar en barcos separados. Este es el mínimo costo de transportar todos los artefactos, que es $1+4+5+3+3 = 16$.

En la segunda pregunta, $D = 9$.
Puedes transportar los artefactos $0$ y $1$ en un mismo barco (ya que $|15 - 12| \leq 9$) y los artefactos $2$ y $3$ en un mismo barco (ya que $|2 - 10| \leq 9$).
El otro artefacto puede ser transportado en un barco separado.
Este es el mínimo costo de transportar todos los artefactos, que es $1+2+2+3+3 = 11$.

En la última pregunta, $D = 1$. Tienes que enviar cada artefacto en barcos separados. Este es el mínimo costo de transportar todos los artefactos, que es $5+4+5+6+3 = 23$.

Por tanto, la función debe retornar $[16, 11, 23]$.

## Evaluador de prueba

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

Aquí, $S$ es el tamaño del arreglo $R$ retornado por `calculate_costs`.
