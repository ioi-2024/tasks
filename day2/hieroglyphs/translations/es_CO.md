# Jeroglíficos
Un equipo de investigadores está estudiando las similitudes entre secuencias de jeroglíficos. Cada jeroglífico lo representan con un entero no negativo. Para estudiar estas secuencias, los investigadores usan los siguientes conceptos:

Para una secuencia fija $A$, una secuencia $S$ se denomina **subsecuencia** de $A$ si y solo si $S$ se puede obtener eliminando algunos elementos (o posiblemente ninguno) de $A$.

En la tabla de abajo se muestran algunos ejemplos de subsecuencias de la secuencia $A = [3, 2, 1, 2]$.

| Subsecuencia    | Cómo se obtiene a partir de $A$ |
|----------------|---------------------------------|
| [3, 2, 1, 2] | No se elimina ningún elemento.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] or [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Por otro lado, ni $[3, 3]$ ni $[1, 3]$ son subsecuencias de $A$.

Considera dos secuencias de jeroglíficos $A$ y $B$. Una secuencia $S$ se dice una **subsecuencia común** de $A$ y $B$ si y solo si es una subsecuencia tanto de $A$ como de $B$. Y una secuencia $U$ se dice **subsecuencia común universal** de $A$ y $B$ si y solo si se cumplen las siguientes condiciones:
* $U$ es una subsecuencia común de $A$ y $B$.
* Cada subsecuencia común de $A$ y $B$ es también una subsecuencia de $U$.

Se puede demostrar que cualquier par de secuencias $A$ y $B$ tienen a lo sumo una subsecuencia común universal.

Los investigadores han encontrado dos secuencias de jeroglíficos: $A$ y $B$. La secuencia $A$ tiene $N$ jeroglíficos mientras que la secuencia $B$ tiene $M$ jeroglíficos. Ayudales a calcular una subsecuencia común universal de las secuencias $A$ y $B$, o determina que tal secuencia no existe.

## Detalles de Implementación

Tienes que implementar la siguiente función

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: arreglo de longitud $N$ que describe la primera secuencia.
* $B$: arreglo de longitud $M$ que describe la segunda secuencia.
* Si existe una subsecuencia común universal de $A$ y $B$, la función debe devolver un arreglo que describa esa secuencia. Caso contrario, la función debe devolver $[-1]$ (el arreglo de longitud $1$ cuyo único elemento es $-1$).
* Esta función se llama exactamente una vez por cada caso de prueba.

## Restricciones

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ para cada $i$ tal que $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ para cada $j$ tal que $0 \leq j < M$

## Subtareas

| Subtarea | Puntaje  | Restricciones Adicionales |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; y tanto $A$ como $B$ consisten de $N$ enteros **distintos** entre $0$ y $N-1$ inclusive.
| 2       | $15$   | Para cada entero $k$, $a + b \leq 3$, donde $a$ es la cantidad de veces que aparece $k$ en $A$ y $b$ es la cantidad de veces que aparece $k$ en $B$.
| 3       | $10$   | $A[i] \leq 1$ para cada $i$ tal que $0 \leq i < N$; $B[j] \leq 1$ para cada $j$ tal que $0 \leq j < M$
| 4       | $16$   | Existe una subsecuencia común universal de $A$ y $B$.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | Sin restricciones adicionales.

## Ejemplos

### Ejemplo 1

Considera la siguiente llamada

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Las subsecuencias comunes de $A$ y de $B$ son las siguientes:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ y $[0, 1, 0, 2]$.

Como $[0, 1, 0, 2]$ es una subsecuencia común de $A$ y de  $B$, y además toda subsecuencia común de $A$ y $B$ son subsecuencias de $[0, 1, 0, 2]$, la función debe devolver $[0, 1, 0, 2]$.

### Ejemplo 2

Considera la llamada

```
ucs([0, 0, 2], [1, 1])
```

Aquí, la única subsecuencia común entre $A$ y $B$ es la secuencia vacía $[\ ]$. De esto se deduce que la función debe devolver el arreglo vacío $[\ ]$.

### Ejemplo 3

Considera la siguiente llamada
```
ucs([0, 1, 0], [1, 0, 1])
```

Aquí, las subsecuencias comunes de $A$ y $B$ son
 $[\ ], [0], [1], [0, 1]$ y $[1, 0]$. Se puede demostrar que no existe subsecuencia común universal, entonces la función debe devolver $[-1]$.

## Evaluador de ejemplo

Formato de entrada:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Formato de salida:

```
T
R[0]  R[1]  ...  R[T-1]
```

Aquí, $R$ es el arreglo devuelto por `ucs` y $T$ es su longitud.
