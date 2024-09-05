# Mosaico

Salma planea colorear un mosaico de arcilla en una pared.
El mosaico es un tablero de tamaño $N \times N$,
 compuesto por $N^2$ casillas cuadradas de $1 \times 1$, inicialmente sin color.
Las filas del mosaico están numeradas del $0$ al $N-1$ de arriba a abajo,
 y las columnas están numeradas de $0$ a $N-1$ de izquierda a derecha.
La casilla en la fila $i$ y la columna $j$ ($0 \leq i < N$, $0 \leq j < N$) se denota con $(i,j)$.
Cada casilla deberá ser coloreada con:
 blanco (representado por un $0$) o negro (representado por un $1$).

Para colorear el mosaico, Salma primero toma dos arreglos $X$ y $Y$ de tamaño $N$,
 cada uno con los elementos $0$ o $1$, y además $X[0] = Y[0]$.
Ella colorea las casillas de la primera fila (la fila $0$) acorde al arreglo $X$,
 tal que el color de la casilla $(0,j)$ es $X[j]$ ($0 \leq j < N$).
También ella colorea las casillas de la primera columna de izquierda a derecha (la columna $0$) de acuerdo con el arreglo $Y$,
 tal que el color de la casilla $(i,0)$ es $Y[i]$ ($0 \leq i < N$).

Luego ella repite los siguientes pasos hasta que todas las casillas estén coloreadas:
* Ella encuentra alguna casilla *no coloreada* $(i,j)$ tal que
  su casilla vecina de arriba (la casilla $(i-1, j)$) y su vecina izquierda (la casilla $(i, j-1)$)
 ambas fueron anteriormente *coloreadas*.
* Luego, ella colorea la casilla $(i,j)$ negro si ambos vecinos son blancos;
 de lo contrario, colorea la casilla $(i, j)$ blanco.

Es posible demostrar que los colores finales de las casillas no depende en el orden en el que Salma las colorea.
 
A Yasmin le da mucha curiosidad los colores de las casillas en el mosaico.
Ella le pregunta a Salma $Q$ preguntas, numeradas de $0$ a $Q-1$.
En la pregunta $k$ ($0 \leq k < Q$),
 Yasmin especifica un subrectángulo del mosaico por su:
* Primera fila $T[k]$ y su última fila $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* Su columna más a la izquierda $L[k]$ y su columna más a la derecha $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

La respuesta de esa pregunta debe ser el número de casillas negras en este subrectángulo.
Formalmente, Salma debe determinar cuántas casillas $(i, j)$ existen,
 tal que $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$,
 y el color de la casilla $(i,j)$ es negra.

Escribe un programa que responde las preguntas de Yasmin.

## Detalles de Implementación 

Debes implementar la siguiente función.

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: arreglos de tamaño $N$ describiendo los colores de las casillas
 en la primera fila y la columna más a la izquierda, respectivamente.
* $T$, $B$, $L$, $R$: arreglos de tamaño $Q$ describiendo las preguntas de Yasmin.
* La función debe regresar un arreglo $C$ de tamaño $Q$,
 tal que $C[k]$ contenga la respuesta a la pregunta $k$ ($0 \leq k < Q$).
* Esta función solo es llamada una vez por cada caso de prueba.

## Límites

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ y $Y[i] \in \{0, 1\}$
 para cada $i$ tal que $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ y $0 \leq L[k] \leq R[k] < N$
 para cada $k$ tal que $0 \leq k < Q$

## Subtareas

| Subtareas | Puntajes | Consideraciones Adicionales |
| :-----:   | :----:   | ----------------------      |
| 1         | $5$      | $N \leq 2; Q \leq 10$
| 2         | $7$      | $N \leq 200; Q \leq 200$
| 3         | $7$      | $T[k] = B[k] = 0$ (para cada $k$ tal que $0 \leq k < Q$)
| 4         | $10$     | $N \leq 5000$
| 5         | $8$      | $X[i] = Y[i] = 0$ (para cada $i$ tal que $0 \leq i < N$)
| 6         | $22$     | $T[k] = B[k]$ y $L[k] = R[k]$ (para cada $k$ tal que $0 \leq k < Q$)
| 7         | $19$     | $T[k] = B[k]$ (para cada $k$ tal que $0 \leq k < Q$)
| 8         | $22$     | Sin consideraciones adicionales.
<br><br><br>
## Ejemplos 

Considera la siguiente llamada a la función.

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Este ejemplo se ilustra en la imagen siguiente.
La imagen de la izquierda muestra los colores de las casillas del mosaico.
Las imágenes de enmedio y derecha muestran los subrectángulos 
  que Yasmin preguntó en su primera y segunda pregunta, respectivamente.

![](example.png "550")

Las respuestas a estas preguntas
 (es decir, el número de unos en las regiones sombreadas)
 son 7 y 3, respectivamente.
Por lo tanto, la función debería regresar $[7, 3]$.

## Evaluador de ejemplo

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

Aquí, $S$ es el tamaño del arreglo $C$ que regresa la función `mosaic`.
