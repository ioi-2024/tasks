# Das Rätsel der Sphinx

Die grosse Sphinx hat ein Rätsel für dich. Sie gibt dir einen Graphen mit $N$ Knoten, nummeriert von $0$ bis $N - 1$.
Der Graph hat $M$ ungerichtete Kanten, nummeriert von $0$ bis $M-1$.
Jede Kante verbindet zwei unterschiedliche Knoten.
Genauer, für jedes $j$ zwischen $0$ und $M - 1$ (inklusive) verbindet Kante $j$ Knoten $X[j]$ und $Y[j]$.
Zwischen je zwei Knoten gibt es höchstens eine Kante.
Zwei Knoten heissen **benachbart**, wenn sie durch eine Kante verbunden sind.

Eine Folge von Knoten $v_0, v_1, \ldots, v_k$ (für $k \ge 0$)
 heisst **Pfad**,
 wenn zwei aufeinanderfolgende Knoten $v_l$ und $v_{l+1}$
 (für jedes $l$ mit $0 \le l \lt k$) benachbart sind.
Wir sagen, dass ein Pfad $v_0, v_1, \ldots, v_k$ die Knoten $v_0$ und $v_k$ **verbindet**.
Im gegebenen Graphen ist jedes Paar von Knoten durch einen Pfad verbunden.

Es gibt $N + 1$ Farben, nummeriert von $0$ bis $N$.
Die Farbe $N$ ist besonders und heisst **die Farbe der Sphinx**.
Jedem Knoten wird eine Farbe zugewiesen: Der Knoten $i$ ($0 \le i \lt N$) hat die Farbe $C[i]$.
Mehrere Knoten können die gleiche Farbe haben,
und es kann Farben geben, die keinem Knoten zugewiesen sind.
Kein Knoten hat die Farbe der Sphinx,
 das heisst, $0 \le C[i] \lt N$ ($0 \le i \lt N$).

Ein Pfad $v_0, v_1, \ldots, v_k$ (mit $k \ge 0$)
 heisst **einfarbig**, wenn alle seine Knoten die gleiche Farbe haben,
 das heisst $C[v_l] = C[v_{l+1}]$ für alle $l$ mit $0 \le l \lt k$.
Ausserdem sagen wir, dass die Knoten $p$ und $q$ ($0 \le p \lt N$, $0 \le q \lt N$)
 zur selben **einfarbigen Komponente** gehören,
 wenn und nur wenn sie durch einen einfarbigen Pfad verbunden sind.

Du kennst die Knoten und Kanten, aber du weisst nicht, welche Farbe die Knoten haben.
Also willst du die Farben der Knoten herausfinden, indem du **Umfärbeexperimente** durchführst.

In einem Umfärbeexperiment darfst du beliebig viele Knoten umfärben.
Um ein Umfärbeexperiment durchzuführen,
 wählst du zuerst ein Array $E$ mit Länge $N$,
 wobei $E[i]$ zwischen $-1$ und $N$ (**inklusive**) liegt,
 für jedes $i$ mit $0 \le i \lt N$.

Dann wird die Farbe eines jeden Knoten $i$ auf $S[i]$ geändert, wobei $S[i]$ wie folgt definiert ist:
* $C[i]$, also die ursprüngliche Farbe von $i$, wenn $E[i] = -1$, oder
* $E[i]$ andernfalls.

Das bedeutet, dass du auch die Farbe der Sphinx in deiner Umfärbung verwenden kannst.

Am Ende des Experiments verkündet die grosse Sphinx die Anzahl der einfarbigen Komponenten im Graphen, nachdem die Farbe jedes Knotens $i$ auf $S[i]$ ($0 \le i \lt N$) geändert wurde.
Die neue Färbung wird nur für dieses Umfärbeexperiment angewendet, dementsprechend werden **die Farben nach dem Experiment wieder auf den Originalzustand zurückgesetzt**.

Deine Aufgabe ist es, die Farben der Knoten des Graphen herauszufinden. Hierfür darfst du bis zu $2\,750$ Umfärbeexperimente durchführen.
Du bekommst Teilpunkte, wenn du für jedes Paar benachbarter Knoten korrekt bestimmst, ob sie die gleiche Farbe haben.

## Angaben zur Implementierung

Du sollst die folgende Funktion implementieren.

```
std::vector&lt;int&gt; find_colours(int N,
    std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y)
```

* $N$ ist die Anzahl an Knoten im Graph.
* $X$ und $Y$ sind Arrays mit Länge $M$, die die Kanten beschreiben.
* Diese Funktion soll ein Array $G$ mit Länge $N$ zurückgeben, das die Farben der Knoten im Graph enthält.
* Diese Funktion wird in jedem Testfall genau einmal aufgerufen.

Die obige Funktion kann folgende Funktion aufrufen, um Umfärbeexperimente durchzuführen.

```
int perform_experiment(std::vector&lt;int&gt; E)
```

* $E$ ist ein Array mit Länge $N$, das angibt, wie die Knoten umgefärbt werden sollen.
* Diese Funktion gibt die Anzahl der einfarbigen Komponenten, nachdem die Knoten wie durch $E$ angegeben umgefärbt wurden, zurück.
* Diese Funktion kann bis zu $2\,750$ Mal aufgerufen werden.

Der Grader ist **nicht adaptiv**, das bedeutet, dass die Farben der Knoten feststehen, bevor `find_colours` aufgerufen wird.

## Beschränkungen

* $2 \le N \le 250$.
* $N - 1 \le M \le \frac{N \cdot (N - 1)}{2}$.
* $0 \le X[j] \lt Y[j] \lt N$ für alle $j$ mit $0 \le j \lt M$.
* $X[j] \neq X[k]$ oder $Y[j] \neq Y[k]$
   für alle $j$ und $k$ mit $0 \le j \lt k \lt M$.
* Jedes Paar von Knoten ist durch mindestens einen Pfad verbunden.
* $0 \le C[i] \lt N$ für alle $i$ mit $0 \le i \lt N$.

## Subtasks

| Subtask | Punkte  | Zusätzliche Beschränkungen |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = 2$.
| 2       | $7$    | $N \le 50$.
| 3       | $33$   | Der Graph ist ein Pfad: $M = N - 1$ und Knoten $j$ und $j+1$ sind benachbart ($0 \leq j < M$).
| 4       | $21$   | Der Graph ist vollständig: $M = \frac{N \cdot (N - 1)}{2}$ und jedes Paar von Knoten ist benachbart.
| 5       | $36$   | Keine weiteren Beschränkungen.

In jedem Subtask kannst du Teilpunkte erhalten, wenn dein Programm für jedes Paar benachbarter Knoten korrekt bestimmt, ob sie die gleiche Farbe haben.

Genauer gesagt erhältst du für einen Subtask alle Punkte, wenn in allen seinen Testfällen das durch `find_colours` zurückgegebene Array $G$ mit dem Array $C$ übereinstimmt (also $G[i] = C[i]$ für alle $i$ mit $0 \le i \lt N$).
Andernfalls erhältst du für einen Subtask $50\%$ der Punkte, wenn in allen seinen Testfällen das von dir zurückgegebene Array $G$ folgende Bedingungen erfüllt:
* $0 \le G[i] \lt N$
   für alle $i$ mit $0 \le i \lt N$;
* Für alle $j$ mit $0 \le j \lt M$:
  * $G[X[j]] = G[Y[j]]$ genau dann, wenn $C[X[j]] = C[Y[j]]$.

## Beispiel

```
find_colours(4, [0, 1, 0, 0], [1, 2, 2, 3])
```

Der Graph, der durch diesen Aufruf angegeben wird, ist im Bild unten zu sehen.
Die (unbekannten) Farben der Knoten sind $C = [2, 0, 0, 0]$,
wie in den kleinen weissen Kreisen angegeben.

![example.png](sphinx_example.png "230")

Nun wird `perform_experiment` einige Male aufgerufen:

```
perform_experiment([-1, -1, -1, -1])
```
In diesem Umfärbeexperiment behalten alle Knoten ihre Farben.

Knoten $1$ und $2$ haben beide die Farbe $0$, und $1, 2$ ist ein einfarbiger Pfad.
Die Knoten $1$ und $2$ gehören also zur selben einfarbigen Komponente.

Knoten $1$ und $3$ wiederum gehören zu unterschiedlichen einfarbigen Komponenten.
Sie haben zwar beide die Farbe $0$, sind aber nicht durch einen einfarbigen Pfad verbunden.

Insgesamt gibt es $3$ einfarbige Komponenten mit den Knoten
$\{0\}$, $\{1, 2\}$, and $\{3\}$.
Dieser Aufruf von `perform_experiment` gibt also $3$ zurück.

```
perform_experiment([0, -1, -1, -1])
```

In diesem Experiment wird nur die Farbe von Knoten $0$ geändert, nämlich auf $0$.
Insgesamt ergibt sich diese Färbung:

![example.png](sphinx_order1.png "230")

Dieser Aufruf gibt $1$ zurück, denn alle Knoten gehören zur selben einfarbigen Komponente.
Daraus lässt sich schliessen, dass auch die Knoten $1$, $2$ und $3$ die Farbe $0$ haben.

```
perform_experiment([-1, -1, -1, 2])
```

In diesem Aufruf wird die Farbe von Knoten $3$ auf $2$ geändert.
Insgesamt ergibt sich diese Färbung:

![example.png](sphinx_order2.png "230")

Dieser Aufruf gibt $2$ zurück, denn es gibt $2$ einfarbige Komponenten:
$\{0, 3\}$ und $\{1, 2\}$.

Die Funktion `find_colours` gibt nun das Array $[2, 0, 0, 0]$ zurück.
Dafür gibt es die volle Punktzahl, denn $C = [2, 0, 0, 0]$.

Für einige andere Rückgabewerte gäbe es $50\%$ der Punkte,
zum Beispiel für $[1, 2, 2, 2]$ oder $[1, 2, 2, 3]$.

## Beispielgrader

Eingabeformat:

```
N  M
C[0]  C[1] ... C[N-1]
X[0]  Y[0]
X[1]  Y[1]
...
X[M-1]  Y[M-1]
```

Ausgabeformat:

```
L  Q
G[0]  G[1] ... G[L-1]
```

Hier ist $L$ die Länge des Arrays $G$, das `find_colours` zurückgibt.
$Q$ ist die Anzahl der Aufrufe von `perform_experiment`.
