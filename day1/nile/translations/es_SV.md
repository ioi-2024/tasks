# Nilo

Quieres transportar $N$ artefactos a través del Nilo.
Los artefactos son numerados del $0$ al $N-1$.
El peso del artefacto $i$ ($0 \leq i < N$) es $W[i]$.

Para transportar los artefactos, utilizas botes especializados.
Cada bote puede transportar **a lo sumo dos** artefactos. 

* Si decides poner un sólo artefacto en un bote, el peso del artefacto puede ser arbitrario.
* Si deseas poner dos artefactos en el mismo bote, debes asegurarte que el bote está debidamente balanceado.
Específicamente, puedes enviar los artefactos $p$ y $q$ ($0 \leq p < q < N$) en el mismo bote sólo si la diferencia absoluta entre sus pesos es a lo sumo $D$; es decir, $|W[p] - W[q]| \leq D$.

Para transportar un artefacto, debes pagar un costo que depende del número
de artefactos cargados en el mismo bote.
El costo de transportar al artefacto $i$ ($0 \leq i < N$) es:

* $A[i]$, si pones al artefacto en su propio bote, o
* $B[i]$, si lo pones en un bote junto a algún otro artefacto.

Nota que en el segundo caso, debes pagar por ambos artefactos en el bote. Específicamente, si decides enviar a los artefactos $p$ y $q$ ($0 \leq p < q < N$) en el mismo bote, necesitas pagar $B[p] + B[q]$.

Enviar un artefacto en un bote por sí mismo siempre es más caro
que enviarlo junto a algún otro artefacto que comparta el bote con él,
así que $B[i] < A[i]$ para todo $i$ tal que $0 \leq i < N$.

Desafortunadamente, el río es muy impredecible y el valor de $D$ cambia contínuamente.
Tu tarea consiste en responder $Q$ preguntas, numeradas del $0$ al $Q-1$.
Las preguntas son descritas por un arreglo $E$ de largo $Q$.
La respuesta a la pregunta $j$ ($0 \leq j < Q$) es
el costo mínimo total de transportar todos los artefactos $N$,
cuando el valor de $D$ es igual a $E[j]$.



## Detalles de implementación

Debes implementar el siguiente procedimiento.

```
std::vector&lt;long long&gt; calculate_costs(
    std::vector&lt;int&gt; W, std::vector&lt;int&gt; A, 
    std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```

* $W$, $A$, $B$: arreglo de enteros de largo $N$, describiendo los pesos de los artefactos y los costos de transportarlos.
* $E$: un arreglo de enteros de largo $Q$ describiendo el valor de $D$ para cada pregunta.
* Este procedimiento debe retornar un arreglo $R$ de $Q$ enteros
  conteniendo el mínimo costo total para transportar los artefactos,
   donde $R[j]$ corresponde al costo cuando el valor de  $D$ es $E[j]$ (para cada $j$
   tal que $0 \leq j < Q$).
* Este procedimiento es llamado exactamente una vez para cada caso de prueba.

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

| Subtarea | Puntuación | Restricciones Adicionales                                                   |
|:--------:|:----------:|-----------------------------------------------------------------------------|
|    1     |    $6$     | $Q \leq 5$; $N \leq 2000$; $W[i] = 1$ para cada $i$ tal que $0 \leq i < N$ 
|    2     |    $13$    | $Q \leq 5$; $W[i] = i+1$ para cada $i$ tal que $0 \leq i < N$              
|    3     |    $17$    | $Q \leq 5$; $A[i] = 2$ y $B[i] = 1$ para cada $i$ tal que $0 \leq i < N$ 
|    4     |    $11$    | $Q \leq 5$; $N \leq 2000$                                                   
|    5     |    $20$    | $Q \leq 5$                                                                  
|    6     |    $15$    | $A[i] = 2$ y $B[i] = 1$ para cada $i$ tal que $0 \leq i < N$             
|    7     |    $18$    | Sin restricciones adicionales.                                                  

## Ejemplo

Considera la siguiente llamada.

```
calculate_costs([15, 12, 2, 10, 21],
                [5, 4, 5, 6, 3],
                [1, 2, 2, 3, 2],
                [5, 9, 1])
```

En este ejemplo tenemos $N = 5$ artefactos y $Q = 3$ preguntas.

En la primera pregunta, $D = 5$.
Puedes enviar los artefactos $0$ y $3$ en un bote (ya que  $|15 - 10| \leq 5$) y los artefactos restantes en botes separados.
Esto da el costo mínimo de transportar todos los artefactos, que es 
 $1+4+5+3+3 = 16$.

En la segunda pregunta, $D = 9$.
Puedes enviar los artefactos $0$ y $1$ en un bote (ya que $|15 - 12| \leq 9$) y enviar los artefactos $2$ and $3$ juntos en otro bote (ya que $|2 - 10| \leq 9$).
El artefacto restante puede ser enviado en un bote aparte.
Esto da como resultado el mínimo costo de transportar todos los artefactos, que es $1+2+2+3+3 = 11$. 

En la pregunta final, $D = 1$. Necesitas enviar cada artefacto en su propio bote.
Esto da como resultado el mínimo costo de transportar todos los artefactos, que es $5+4+5+6+3 = 23$.

Por lo tanto, este procedimiento debe retornar $[16, 11, 23]$.


## Calificador local

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
