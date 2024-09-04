# Nilo

Quieres transportar $N$ objetos a través del Nilo. 
Los objetos están numerados del $0$ al $N-1$.
El peso del objeto $i$ ($0 \leq i < N$) es $W[i]$.

Para transportar los objetos, tienes botes especiales.
Cada bote puede cargar **a lo más dos** objetos.

* Si decides poner únicamente un objeto en un bote, el peso puede ser el que sea.
* Si decides poner dos objetos en un bote, tienes que asegurarte de que el bote esté balanceado.
Especificamente, puedes enviar
 los objetos $p$ y $q$ ($0 \leq p < q < N$) en el mismo bote
 si y solo si la diferencia absoluta entre sus pesos es a lo más $D$,
 en otras palabras $|W[p] - W[q]| \leq D$.

Para transportar un objeto, tienes que pagar un costo
que depende en el número de objetos que van en el mismo bote.
El costo de transportar el objeto $i$ ($0 \leq i < N$) es:

* $A[i]$, si pusiste el objeto en su propio bote, o
* $B[i]$, si lo pusiste en un bote junto a otro objeto.

Nótese que en el segundo caso, tienes que pagar por los dos objetos en el bote.
Específicamente, si decides mandar objetos 
$p$ y $q$ ($0 \leq p < q < N$) en el mismo bote,
necesitas pagar  $B[p] + B[q]$.

Mandar un objeto en un bote por sí mismo siempre es más costoso
que mandarlo en un bote con otro objeto,
es decir $B[i] < A[i]$ para todo $i$ tal que $0 \leq i < N$.

Desafortunadamente, el río es bastante impredecible y el valor de $D$ cambia constantemente.
Tu tarea es responder $Q$ preguntas numeradas de $0$ a $Q-1$.
Las preguntas vienen en un arreglo $E$ de longitud $Q$.
La respuesta a la pregunta $j$ ($0 \leq j < Q$) es 
el costo mínimo total de transportar todos los $N$ objetos
cuando el valor de $D$ es igual a $E[j]$.

## Detalles de implementación

Tienes que implementar la siguiente función.

```
std::vector&lt;long long&gt; calculate_costs(
    std::vector&lt;int&gt; W, std::vector&lt;int&gt; A, 
    std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```

* $W$, $A$, y $B$: son arreglos de longitud $N$, describiendo el peso de los objetos, así como los costos de transportarlos solos o acompañados, respectivamente.
* $E$: es un arreglo de enteros de longitud $Q$ describiendo el valor de $D$ para cada pregunta.
* Tu función debe de regresar un arreglo $R$ con $Q$ enteros
   conteniendo el costo mínimo total de transportar los objetos,
   donde $R[j]$ contiene el costo cuando el valor de $D$ es $E[j]$ (para cada $j$
   tal que $0 \leq j < Q$).
* Esta función se llama exactamente una vez para cada caso de prueba.

## Límites

* $1 \leq N \leq 100\,000$
* $1 \leq Q \leq 100\,000$
* $1 \leq W[i] \leq 10^{9}$
   para cada $i$ tal que $0 \leq i < N$
* $1 \leq B[i] < A[i] \leq 10^{9}$
   para cada $i$ tal que $0 \leq i < N$
* $1 \leq E[j] \leq 10^{9}$
   para cada $j$ tal que $0 \leq j < Q$

## Subtareas

| Subtarea | Puntos  | Condiciones adicionales |
| :-----: | :----: | ---------------------- |
| 1       | $6$    | $Q \leq 5$; $N \leq 2000$; $W[i] = 1$ para cada $i$ tal que $0 \leq i < N$
| 2       | $13$   | $Q \leq 5$; $W[i] = i+1$ para cada $i$ tal que $0 \leq i < N$
| 3       | $17$   | $Q \leq 5$; $A[i] = 2$ y $B[i] = 1$ para cada $i$ tal que $0 \leq i < N$
| 4       | $11$   | $Q \leq 5$; $N \leq 2000$
| 5       | $20$   | $Q \leq 5$
| 6       | $15$   | $A[i] = 2$ y $B[i] = 1$ para cada $i$ tal que $0 \leq i < N$
| 7       | $18$   | Sin condiciones adicionales.

## Ejemplo

Considera la siguiente llamada a tu función.

```
calculate_costs([15, 12, 2, 10, 21],
                [5, 4, 5, 6, 3],
                [1, 2, 2, 3, 2],
                [5, 9, 1])
```

En este ejemplo tenemos $N = 5$ objetos y $Q = 3$ preguntas.

En la primera pregunta, $D = 5$,
puedes mandar objetos $0$ y $3$ en el mismo bote (ya que $|15 - 10| \leq 5$) y los demás objetos en sus propios botes.
Esto nos da el costo mínimo de transportar todos los objetos, el cual es $1+4+5+3+3 = 16$.

En la segunda pregunta, $D = 9$,
Puedes mandar a los objetos $0$ y $1$ en el mismo bote (ya que $|15 - 12| \leq 9$) y mandar a los objetos $2$ y $3$ en el mismo bote (ya que $|2 - 10| \leq 9$).
El objeto restante se puede mandar en su propio bote.
Esto nos da el costo mínimo de transportar todos los objetos, el cual es $1+2+2+3+3 = 11$.

En la última pregunta, $D = 1$. necesitas mandar a cada objeto en su propio bote.
Esto nos da el costo mínimo de transportar todos los objetos, el cual es $5+4+5+6+3 = 23$.

Entonces, tu función debe de regresar $[16, 11, 23]$.


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
R[Q-1]
```
