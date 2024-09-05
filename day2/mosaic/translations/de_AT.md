# Mosaik

Salma hat vor, ein Wandmosaik einzufärben.
Das Mosaik ist angeordnet als $N \times N$ Gitter
 und besteht aus $N^2$ nicht gefärbten $1 \times 1$ Steinchen.
Die Zeilen des Mosaiks sind nummeriert von $0$ bis $N-1$ von oben bis unten;
 die Spalten sind nummeriert von $0$ bis $N-1$ von links nach rechts.
Das Steinchen in der $i$-ten Zeile und $j$-ten Spalte ($0 \leq i < N$, $0 \leq j < N$)
 bezeichnen wir mit Steinchen $(i,j)$.

Jedes Steinchen wird von Salma entweder weiß (beschrieben mit $0$)
 oder schwarz (beschrieben mit $1$) eingefärbt.
Dazu bestimmt Salma zuerst zwei Arrays $X$ und $Y$ mit Länge $N$.
 Die Elemente der Arrays haben die Werte $0$ und $1$.
 Für die Arrays gilt außerdem $X[0] = Y[0]$.

Salma färbt zuerst die Steinchen in der obersten Zeile (Zeile $0$) gemäß Array $X$ ein,
 wobei Steinchen $(0,j)$ Farbe $X[j]$ ($0 \leq j < N$) erhält.
Analog färbt sie die Steinchen in der linkesten Spalte (Spalte $0$) gemäß Array $Y$ ein,
 wobei Steinchen $(i,0)$ Farbe $Y[i]$ ($0 \leq i < N$) erhält.

Danach wiederholt Salma folgende Schritte, bis alle Steinchen eingefärbt sind:
* Sie wählt ein *nicht gefärbtes* Steinchen $(i,j)$ aus, dessen
 oberer Nachbar (Steinchen $(i-1, j)$) und linker Nachbar (Steinchen $(i, j-1)$)
 bereits *eingefärbt* sind.
* Anschließend färbt sie Steinchen $(i,j)$ schwarz, falls beide dieser Nachbarn weiß sind;
 andernfalls färbt sie Steinchen $(i, j)$ weiß.

Man kann beweisen, dass die resultierenden Farben der Steinchen
nicht von der Zeilenfolge abhängen, in welcher Salma sie einfärbt.

Yasmin ist sehr neugierig über die Farben der Mosaiksteinchen.
Sie stellt Salma $Q$ Fragen, nummeriert von $0$ bis $Q-1$.
In der $k$-ten Frage ($0 \leq k < Q$) fragt Yasmin ein Teilrechteck des Mosaiks ab, beschrieben durch
* dessen oberste Zeile $T[k]$ und unterste Zeile $B[k]$ ($0 \leq T[k] \leq B[k] < N$), sowie
* dessen linkeste Spalte $L[k]$ und rechteste Spalte $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

Bestimme die Anzahl schwarzer Steinchen in diesem Teilrechteck.
Genauer, hilf Salma, herauszufinden, wie viele Steinchen $(i, j)$ es gibt mit
 $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$, deren Farbe schwarz ist.

Schreibe ein Programm, das Yasmins Fragen beantwortet.

## Angaben zur Implementierung

Du sollst die folgende Funktion implementieren:

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: Arrays der Länge $N$, welche die Farben der Steinchen in der obersten Zeile und der linkesten Spalte angeben.
* $T$, $B$, $L$, $R$: Arrays der Länge $Q$, welche die von Yasmin gestellten Fragen beschreiben.
* Die Funktion soll ein Array $C$ der Länge $Q$ zurückgeben, sodass $C[k]$ die Antwort auf Frage $k$ ($0\le k < Q$) enthält.
* Diese Funktion wird genau einmal pro Testfall aufgerufen.

## Beschränkungen

* $1 \leq N \leq 200\,000$.
* $1 \leq Q \leq 200\,000$.
* $X[i] \in \{0, 1\}$ und $Y[i] \in \{0, 1\}$ für alle $i$ mit $0 \leq i < N$.
* $X[0] = Y[0]$.
* $0 \leq T[k] \leq B[k] < N$ und $0 \leq L[k] \leq R[k] < N$ für alle $k$ mit $0 \leq k < Q$.

## Subtasks

| Subtask | Punkte  | Weitere Beschränkungen |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$.
| 2       | $7$    | $N \leq 200; Q \leq 200$.
| 3       | $7$    | $T[k] = B[k] = 0$ (für alle $k$ mit $0 \leq k < Q$).
| 4       | $10$   | $N \leq 5000$.
| 5       | $8$    | $X[i] = Y[i] = 0$ (für alle $i$ mit $0 \leq i < N$).
| 6       | $22$   | $T[k] = B[k]$ und $L[k] = R[k]$ (für alle $k$ mit $0 \leq k < Q$)
| 7       | $19$   | $T[k] = B[k]$ (für alle $k$ mit $0 \leq k < Q$)
| 8       | $22$   | Keine weiteren Beschränkungen.

## Beispiel

Betrachte den folgenden Aufruf:

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Dieses Beispiel ist im untenstehenden Bild dargestellt. Das linke Bild zeigt die Farben der Steinchen im Mosaik. Das mittlere und das rechte Bild zeigen die Teilrechtecke, welche Yasmin in der ersten beziehungsweise zweiten Frage abfragt.

![](example.png "550")

Die Antwort auf die Frage (die Anzahl der Einsen in den grau schattierten Rechtecken) ist $7$, beziehungsweise $3$.
Also sollte die Funktion $[7, 3]$ zurückgeben.

## Beispielgrader

Eingabeformat:

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

Ausgabeformat:

```
C[0]
C[1]
...
C[S-1]
```

Dabei ist $S$ die Länge des von `mosaic` zurückgegebenen Arrays $C$ ist.
