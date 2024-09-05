# Mosaic 

Salma planea colorear un mosaico de arcilla en una pared. El mosaico es una cuadrícula de dimensiones $N \times N$ hecha de $N^2$ casillas cuadradas de dimensiones $1 \times 1$ sin colorear.

Las filas del mosaico están enumeradas de $0$ a $N-1$ de arriba hacia abajo, y las columnas están enumeradas de $0$ a $N-1$ de izquierda a derecha.
La casilla en la fila $i$ y la columna $j$ ($0 \leq i < N$, $0 \leq j < N$) es denotada por $(i,j)$.
Cada casilla debe ser coloreada de blanco (denotado por $0$) o de negro (denotada por $1$).

Para colorear el mosaico, Salma primero toma dos arreglos $X$ e $Y$ de tamaño $N$, los cuales contienen ceros ($0$) y unos ($1$), tales que $X[0] = Y[0]$. 
Ella colorea las casillas de la fila de más arriba (la fila $0$) de acuerdo al arreglo $X$, de tal forma que el color de la casilla $(0,j)$ es $X[j]$ ($0 \leq j < N$).
Ella también colorea las casillas de la columna más a la izquierda (la columna $0$) de acuerdo al arreglo $Y$, de tal forma que el color de la casilla $(i,0)$ es $Y[i]$ ($0 \leq i < N$).

Luego, ella repite los siguientes pasos hasta que todas las casillas estén coloreadas:
* Encuentra cualquier casilla $(i,j)$ *sin colorear* tal que su vecina de arriba (la casilla $(i-1,j)$) y su vecina izquierda (la casilla $(i, j-1)$) estén ambas *ya coloreadas*.
* Entonces colorea la casilla $(i,j)$ de negro si ambas vecinas son blancas; de lo contrario colorea la casilla $(i,j)$ de blanco.

Puede demostrarse que la coloración final de las casillas no depende del orden en el cual Salma las colorea.

Yasmin es muy curiosa sobre los colores de las casillas en el mosaico.
Ella le hace a Salma $Q$ preguntas enumeradas de $0$ a $Q-1$. En la pregunta $k$ ($0 \leq k < Q$) Yasmin especifica un subrectángulo del mosaico por:
* Su fila de más arriba $T[k]$ y su fila de más abajo $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* Su columna de más a la izquierda $L[k]$ y su columna de más a la derecha $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

La respuesta a la pregunta es el número de casillas negras en dicho subrectángulo.
Específicamente Salma debe hallar cuántas casillas $(i, j)$ existen tales que $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$, y que su color sea negro.

Escribe un programa que responda a las preguntas de Yasmin.

## Detalles de implementación

Debes implementar la siguiente función.

```
std::vector&lt;long long&gt; mosaic(
    std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: arreglos de longitud $N$ que describen los colores de las casillas en la fila más hacia arriba y la columna más hacia la izquierda,  respectivamente.
* $T$, $B$, $L$, $R$: arreglos de longitud $Q$ que describen las preguntas realizadas por Yasmin.
* La función debe retornar un arreglo $C$ de longitud $Q$, tal que $C[k]$ proporciona la respuesta a la pregunta $k$ ($0 \leq k < Q$).
* La función es llamada exactamente una vez por cada caso de prueba.

## Restricciones

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ y $Y[i] \in \{0, 1\}$
 para cada $i$ tal que $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ y $0 \leq L[k] \leq R[k] < N$
 para cada $k$ tal que $0 \leq k < Q$

## Subtareas

| Subtarea | Puntaje  | Restricciones adicionales |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ (para todo $k$ tal que $0 \leq k < Q$)
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ (para todo $i$ tal que $0 \leq i < N$)
| 6       | $22$   | $T[k] = B[k]$ y $L[k] = R[k]$ (para todo $k$ tal que $0 \leq k < Q$)
| 7       | $19$   | $T[k] = B[k]$ (para todo $k$ tal que $0 \leq k < Q$)
| 8       | $22$   | Sin restricciones adicionales.

## Ejemplo

Considera la siguiente llamada.

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Este ejemplo es ilustrado en las imágenes de abajo.
La imagen de la izquierda muestra los colores de las casillas en el mosaico.
Las imágenes del medio y de la derecha muestran los subrectángulos sobre los que Yasmin preguntó en la primera y segunda pregunta respectivamente.

![](example.png "550")

Las respuestas a las preguntas (esto es, los números de unos en los rectángulos sombreados) son 7 y 3 respectivamente. Por lo tanto, la función debe retornar $[7,3]$.

## Calificador local

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

Aquí $S$ es la longitud del arreglo $C$ retornado por `mosaic`.