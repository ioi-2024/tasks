# Mosaico

Salma planea pintar un mosaico de cerámica sobre una pared. El mosaico es un tablero de tamaño $N \times N$, hecho de $N^2$ casillas cuadradas de $1 \times 1$, inicialmente sin color.
Las filas del mosaico están enumeradas de $0$ a $N-1$, de arriba hacia abajo, y las columnas están enumeradas de $0$ a $N-1$, de izquierda a derecha.
Denotamos la casilla en la fila $i$ y columna $j$ ($0 \leq i < N$, $0 \leq j < N$) como $(i,j)$.
Cada casilla debe ser pintada de blanco (denotado por $0$) o de negro (denotado por $1$).

Para pintar el mosaico, Salma primero elige dos arreglos $X$ e $Y$ de tamaño $N$, cada uno compuesto de valores $0$ y $1$, tal que $X[0] = Y[0]$.
Ella pinta las casillas de la fila superior (fila $0$) de acuerdo al arreglo $X$, de modo que el color de la casilla $(0,j)$ es $X[j]$ ($0 \leq j < N$).
Salma también pinta las casillas de la columna de más a la izquierda (columna $0$) de acuerdo al arreglo $Y$, de modo que el color de la casilla $(i,0)$ es $Y[i]$ ($0 \leq i < N$).

Luego, repite los siguientes pasos hasta que todos las casillas estén pintadas:
* Primero, encuentra cualquier casilla *sin color* $(i,j)$ tal que tanto su vecina de arriba (la casilla $(i-1,j)$) como su vecina de la izquierda (la casilla $(i,j-1)$) *ya estén pintadas*.
* A continuación, si ambas de las vecinas mencionadas son blancas, pinta la casilla $(i,j)$ de negro; de lo contrario, pinta la casilla $(i,j)$ de blanco.

Se puede demostrar que los colores finales de las casillas no dependen del orden en el que Salma las pinte.

Yasmín siente mucha curiosidad sobre los colores de las casillas en el mosaico.
Ella realiza $Q$ preguntas a Salma, enumeradas de $0$ a $Q-1$.
En la pregunta $k$-ésima ($0 \leq k < Q$), Yasmín especifica un subtablero del mosaico según:
* La fila superior $T[k]$ y la fila inferior $B[k]$ ($0 \leq T[k] \leq B[k] < N$) del subtablero, y
* La columna de más a la izquierda $L[k]$ y la columna de más a la derecha $R[k]$ ($0 \leq L[k] \leq R[k] < N$) del subtablero.
 
La respuesta a la pregunta es la cantidad de casillas negras en dicho subtablero.
Concretamente, Salma debe descubrir cuántas casillas $(i,j)$ existen, tal que $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$, y el color de la casilla $(i,j)$ sea negro.

Tu tarea es escribir un programa que responda las preguntas de Yasmín.

## Detalles de Implementación

Debes implementar la siguiente función:

```
std::vector&lt;long long&gt; mosaic(
  std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: arreglos de tamaño $N$ que describen los colores de las casillas en la fila superior y la columna de más a la izquierda, respectivamente.
* $T$, $B$, $L$, $R$: arreglos de tamaño $Q$ que describen las preguntas realizadas por Yasmín.
* La función debe retornar un arreglo $C$ de tamaño $Q$, tal que $C[k]$ entrega la respuesta a la pregunta $k$ ($0 \leq k < Q$).
* Esta función es llamada exactamente una vez por cada caso de prueba.

## Restricciones

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ e $Y[i] \in \{0, 1\}$
 para cada $i$ tal que $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ y $0 \leq L[k] \leq R[k] < N$
 para cada $k$ tal que $0 \leq k < Q$

## Subtareas

| Subtareas | Puntaje  | Restricciones Adicionales |
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

Este ejemplo se ilustra en las siguientes imágenes.
La imagen de la izquierda muestra los colores de las casillas en el mosaico.
La imagen central y la imagen de la derecha muestran los subtableros por los que Yasmín consultó en la primera y segunda pregunta, respectivamente.

![](example.png "550")

Las respuestas a las preguntas (es decir, la cantidad de unos en los rectángulos sombreados) son 7 y 3, respectivamente. Por lo tanto, la función debería retornar $[7,3]$.

## Evaluador de Ejemplo

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

Aquí, $S$ es el tamaño del arreglo $C$ retornado por la función `mosaic`.
