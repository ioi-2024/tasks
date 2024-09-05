# Jeroglíficos

Un equipo de investigadores está estudiando las similitudes entre secuencias de jeroglíficos
Los investigadores representan cada jeroglífico con un número no negativo.
Para realizar sus estudios, los investigadores usan los siguientes conceptos sobre secuencias.

Para una secuencia fija $A$,
 una secuencia $S$ se llama **subsecuencia** de $A$
 sí y solo si $S$ se puede obtener
 removiendo algunos elementos de $A$ o posiblemente ninguno.

La tabla de abajo muestra algunos ejemplos de subsecuencias de una secuencia $A = [3, 2, 1, 2]$.

| Subsecuencia    | Como se puede obtener a partir de $A$ |
|----------------|---------------------------------|
| [3, 2, 1, 2] | Removiendo ningún elemento.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] o [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Por el otro lado, $[3, 3]$ ó $[1, 3]$ no son subsecuencias de $A$.

Considera dos secuencias de jeroglíficos, $A$ y $B$.
Una secuencia $S$ es llamada **subsecuencia común** de $A$ y $B$
 sí y solo si $S$ es una subsecuencia tanto de $A$ como de $B$.
 Además, decimos que una secuencia $U$ es una **subsecuencia común universal** de $A$ y $B$
 sí y solo si las siguientes dos condiciones se cumplen:
* $U$ es una subsecuencia común de $A$ y $B$.
* Toda subsecuencia común de $A$ y $B$ es también una subsecuencia de $U$.

Se puede demostrar que cualesquiera dos secuencias $A$ y $B$
tienen a lo más una subsecuencia común universal.

Los investigadores han encontrado dos secuencias de jeroglíficos $A$ y $B$.
La secuencia $A$ consiste en $N$ jeroglíficos
 y la secuencia $B$ consiste en $M$ jeroglíficos.
Ayuda a los investigadores a computar la
 subsecuencia común universal de las secuencias $A$ y $B$,
o que determine que tal subsecuencia no existe.

## Detalles de implementación

Debes implementar la siguiente función.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: es un arreglo de longitud $N$ describiendo la primera secuencia.
* $B$: es un arreglo de longitud $M$ describiendo la segunda secuencia.
* Si la subsecuencia común universal de $A$ y $B$ existe,
   tu función debe de regresar un arreglo con dicha secuencia.
  De lo contrario, tu función debe de regresar $[-1]$.
* Esta función la va a llamar el evaluador exactamente una vez por cada caso de prueba.

## Límites

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ para cada $i$ tal que $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ para cada $j$ tal que $0 \leq j < M$

## Subtareas

| Subtarea | Puntos  | Condiciones adicionales |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; Tanto $A$ como $B$ consisten en $N$ enteros **distintos** entre $0$ y $N-1$ inclusive
| 2       | $15$   | Para cualquier entero $k$, el número de elementos de $A$ igual a $k$ *más* el número de elementos de $B$ igual a $k$ es a lo más $3$.
| 3       | $10$   | $A[i] \leq 1$ para cada $i$ tal que $0 \leq i < N$; $B[j] \leq 1$ para cada $j$ tal que $0 \leq j < M$
| 4       | $16$   | La subsecuencia común universal de $A$ y $B$ existe.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | Sin condiciones adicionales.

## Ejemplos

### Ejemplo 1

Considera la siguiente llamada a tu función.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

En este ejemplo, las subsecuencias comunes de $A$ y $B$ son las siguientes:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ y $[0, 1, 0, 2]$.

Dado que $[0, 1, 0, 2]$ es una subsecuencia común de $A$ y $B$, y que
 todas las subsecuencias comunes de $A$ y $B$ son subsecuencias de $[0, 1, 0, 2]$,
 esta función debe de regresar $[0, 1, 0, 2]$.

### Ejemplo 2

Considera la siguiente llamada a tu función.

```
ucs([0, 0, 2], [1, 1])
```

En este ejemplo, la única subsecuencia común de $A$ y $B$ es la secuencia vacía $[\ ]$.
Por lo tanto, tu función debe de regresar $[\ ]$.

### Ejemplo 3

Considera la siguiente llamada a tu función.
```
ucs([0, 1, 0], [1, 0, 1])
```

En este ejemplo, las subsecuencias comunes de $A$ y $B$ son
 $[\ ], [0], [1], [0, 1]$ y $[1, 0]$.
Por lo tanto, no existe una subsecuencia común universal y tu función debe de regresar $[-1]$.

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

Donde $R$ es el arreglo regresado por `ucs` y $T$ su longitud.
