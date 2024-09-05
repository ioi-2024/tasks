# Mosaico

Salma planea pintar un mosaico de cerámica en una pared.
El mosaico es una cuadrícula de $N \times N$ formada por $N^2$ baldosas cuadradas de $1 \times 1$ que inicialmente están sin pintar.
Las filas del mosaico están numeradas desde $0$ hasta $N-1$, de arriba hacia abajo, y las columnas están numeradas desde $0$ hasta $N-1$, de izquierda a derecha.
La baldosa en la fila $i$ y la columna $j$ ($0 \leq i < N$, $0 \leq j < N$) está denotada por $(i,j)$.
Cada baldosa deber ser pintada de blanco (denotado por $0$) o de negro (denotado por $1$).

Para pintar el mosaico, Salma primero selecciona dos arreglos $X$ y $Y$ de tamaño $N$, cada uno compuesto por los valores $0$ y $1$, tal que $X[0] = Y[0]$.
Ella pinta las baldosas de la fila superior (fila $0$) de acuerdo al arreglo $X$, de forma tal que el color de la baldosa $(0,j)$ es $X[j]$ ($0 \leq j < N$). Ella también pinta las baldosas de la columna más a la izquierda (columna $0$) de acuerdo al arreglo $Y$, de forma tal que el color de la baldosa $(i,0)$ es $Y[i]$ ($0 \leq i < N$).

Luego ella repite los siguientes pasos hasta que todas las baldosas estén pintadas:
* Primero, encuentra cualquier baldosa *sin pintar* $(i,j)$ tal que su vecino de arriba (baldosa $(i-1,j)$) y su vecino a la izquierda (baldosa $(i,j-1)$) *ya están pintados*.
* Luego, si ambos vecinos son blancos pinta la baldosa $(i,j)$ de negro; de lo contrario, pinta la baldosa $(i,j)$ de blanco.

Se puede probar que el color final de las baldosas no depende del orden en el que Salma las pinta.

Yasmin siente mucha curiosidad por los colores de las baldosas en el mosaico. Ella le hace $Q$ preguntas a Salma, las preguntas están numeradas desde $0$ hasta $Q-1$. En la pregunta $k$ ($0 \leq k < Q$), Yasmin especifica un subrectángulo del mosaico por su:
* Fila superior $T[k]$ y fila inferior $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* Columna más a la izquierda $L[k]$ y columna más a la derecha $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

La respuesta a la pregunta es la cantidad de baldosas negras en ese subrectángulo. Formalmente, Salma debe contar cuántas celdas $(i,j)$ existen, tal que $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$, y el color de la baldosa $(i,j)$ es negra.

Escribe un programa que responda las preguntas de Yasmin.

## Detalles de implementación

Debes implementar la siguiente función.

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: arreglos de tamaño $N$ que describen los colores de las baldosas en la fila superior y en la columna más a la izquierda, respectivamente. 
* $T$, $B$, $L$, $R$: arreglos de tamaño $Q$ que describen las preguntas hechas por Yasmin.
* La función debe retornar un arreglo $C$ de tamaño $Q$, donde $C[k]$ es la respuesta a la pregunta $k$ ($0 \leq k < Q$).
* Esta función es llamada exactamente una vez por cada caso de prueba.

## Restricciones

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ y $Y[i] \in \{0, 1\}$
 para cada $i$ tal que $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ y $0 \leq L[k] \leq R[k] < N$
 por cada $k$ tal que $0 \leq k < Q$

## Subtareas

| Subtarea | Puntos  | Restricciones Adicionales |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ (para cada $k$ tal que $0 \leq k < Q$)
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ (para cada $i$ tal que $0 \leq i < N$)
| 6       | $22$   | $T[k] = B[k]$ y $L[k] = R[k]$ (para cada $k$ tal que $0 \leq k < Q$)
| 7       | $19$   | $T[k] = B[k]$ (para cada $k$ tal que $0 \leq k < Q$)
| 8       | $22$   | Sin restricciones adicionales.

## Ejemplo

Considera la siguiente llamada.

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Este ejemplo está ilustrado en las siguientes imágenes.
La imagen de la izquierda muestra los colores en el mosaico.
Las imágenes del medio y de la derecha muestran los subrectángulos por los que Yasmin preguntó en la primera y la segunda pregunta, respectivamente.

![](example.png "550")

Las respuestas a las preguntas
(es decir, la cantidad de unos en los rectángulos sombreados)
son $7$ y $3$, respectivamente.
Por lo que la función debe retornar $[7,3]$.

## Evaluador de prueba

Formato de entrada:

```
N
X[0]  X[1]  ...  X[N-1]
Y[0]  Y[1]  ...  Y[N-1]
Q
T[0]  B[0]  L[0]  R[0]
T[1]  B[1]  L[1]  R[1]
...
T[Q-1]  B[Q-1]  L[Q-1]  R[Q-1]
```

Formato de salida:

```
C[0]
C[1]
...
C[S-1]
```

Aquí, $S$ es el tamaño del arreglo $C$ retornado por `mosaic`.
