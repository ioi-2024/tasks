# Hieroglyphen

Eine Gruppe von Forschern untersucht die Ähnlichkeit zwischen verschiedenen Hieroglyphenfolgen.
Sie stellen jede Hieroglyphe durch eine nicht-negative ganze Zahl dar.
Um ihre Forschung durchzuführen, verwenden sie folgende Begriffe über Folgen.

Für eine gegebene Folge $A$
nennen wir eine Folge $S$ genau dann eine **Teilfolge** von $A$, wenn $S$ sich aus der Entfernung von 0 oder mehr Elementen aus $A$ ergeben kann. 

Die folgende Tabelle zeigt einige Beispiele von Teilfolgen der Folge $A = [3, 2, 1, 2]$.

| Die Teilfolge    | ergibt sich aus $A$ so |
|----------------|---------------------------------|
| [3, 2, 1, 2] | Keine Elemente werden entfernt.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] oder [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Andererseits sind $[3, 3]$ oder $[1, 3]$ keine Teilfolgen von $A$.

Betrachte zwei Hieroglyphenfolgen $A$ und $B$.
Eine Folge $S$ ist genau dann eine **gemeinsame Teilfolge** von $A$ und $B$,
wenn $S$ eine Teilfolge von $A$ und von $B$ ist.
Darüber hinaus sagen wir, dass eine Folge $U$ genau dann eine **universelle gemeinsame Teilfolge** von $A$ und $B$ ist, 
wenn die zwei folgenden Bedingungen erfüllt sind:
* $U$ ist eine gemeinsame Teilfolge von $A$ und $B$.
* Jede gemeinsame Teilfolge von $A$ und $B$ ist auch eine Teilfolge von $U$.

Man kann zeigen, dass es für jedes Paar von Folgen $A$ und $B$ höchstens eine universelle gemeinsame Teilfolge gibt.

Die Forscher haben zwei Hieroglyphenfolgen $A$ und $B$ gefunden. 
Folge $A$ besteht aus $N$ Hieroglyphen 
und Folge $B$ besteht aus $M$ Hieroglyphen.
Hilf den Forschern dabei,
eine universelle gemeinsame Teilfolge von $A$ und $B$ zu finden oder stelle fest, dass keine solche Folge existiert.

## Angaben zur Implementierung

Du sollst folgende Funktion implementieren.

```
std::vector<int> ucs(std::vector<int> A, std::vector<int> B)
```

* $A$: ein Array der Länge $N$, das die erste Folge beschreibt.
* $B$: ein Array der Länge $M$, das die zweite Folge beschreibt.
* Falls eine universelle gemeinsame Teilfolge von $A$ und $B$ existiert, dann soll die Funktion ein Array der Folgenglieder zurückgeben.
Ansonsten soll die Funktion $[-1]$ zurückgeben (ein Array der Länge $1$ mit einem einzigen Element $-1$).
* Diese Funktion wird genau einmal für jeden Testfall aufgerufen.

## Beschränkungen

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ für alle $i$ mit $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ für alle $j$ mit $0 \leq j < M$

## Subtasks

| Subtask | Punkte  | Zusätzliche Beschränkungen |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; $A$ und $B$ bestehen jeweils aus $N$ **unterschiedlichen** ganzen Zahlen zwischen $0$ und $N-1$ (inklusiv)
| 2       | $15$   | Für jede ganze Zahl $k$: (Anzahl der Elemente in $A$, die gleich $k$ sind) $+$ (Anzahl der Elemente in $B$, die gleich $k$ sind) $\leq 3$
| 3       | $10$   | $A[i] \leq 1$ für alle $i$ mit $0 \leq i < N$; <br>$B[j] \leq 1$ für alle $j$ mit $0 \leq j < M$
| 4       | $16$   | Es gibt eine universelle gemeinsame Teilfolge von $A$ und $B$.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | Keine weiteren Beschränkungen.

## Beispiele

### Beispiel 1

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Die gemeinsamen Teilfolgen von $A$ und $B$ sind:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ und $[0, 1, 0, 2]$.

$[0, 1, 0, 2]$ ist eine gemeinsame Teilfolge von $A$ und $B$, und jede gemeinsame Teilfolge von $A$ und $B$ ist eine Teilfolge von $[0, 1, 0, 2]$. Also soll die Funktion $[0, 1, 0, 2]$ zurückgeben.

### Beispiel 2

```
ucs([0, 0, 2], [1, 1])
```

Hier gibt es nur eine gemeinsame Teilfolge von $A$ und $B$, nämlich die leere Folge $[\ ]$.
Also soll die Funktion $[\ ]$ zurückgeben.

### Beispiel 3

```
ucs([0, 1, 0], [1, 0, 1])
```

Die gemeinsamen Teilfolgen von $A$ und $B$ sind: 
 $[\ ], [0], [1], [0, 1]$ und $[1, 0]$.
Man kann zeigen, dass es keine universelle gemeinsame Teilfolge gibt. Also soll die Funktion $[-1]$ zurückgeben.

## Beispielgrader

Eingabeformat:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Ausgabeformat:

```
T
R[0]  R[1]  ...  R[T-1]
```

Hier ist $R$ das von `ucs` zurückgegebene Array, und $T$ ist dessen Länge.
