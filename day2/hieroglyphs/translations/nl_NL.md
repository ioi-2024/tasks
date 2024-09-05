# Hiërogliefen
Een team onderzoekers bestudeert de overeenkomsten tussen rijen hiërogliefen.
Ze stellen elk hiëroglief voor met een positief geheel getal.
Om hun studie uit te voeren,
 Ze gebruiken de volgende concepten over rijen.

Voor een rij $A$:
 een rij $S$ wordt een **deelrij** van $A$ genoemd
 dan en slechts dan als $S$ verkregen kan worden
 door sommige elementen (mogelijk geen) uit $A$ te verwijderen.

De onderstaande tabel toont een paar voorbeelden van deelrijen van een rij $A = [3, 2, 1, 2]$.

| Deelrij    | Hoe de deelrij verkregen wordt uit $A$ |
|----------------|---------------------------------|
| [3, 2, 1, 2] | Geen elementen zijn verwijderd.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] or [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Aan de andere kant zijn $[3, 3]$ or $[1, 3]$ geen deelrijen van $A$.

Laten we nu twee rijen bekijken, $A$ en $B$.
Een rij $S$ is een **gemeenschappelijke deelrij** van $A$ en $B$
 dan en slechts dan als $S$ een deelrij is van $A$ en van $B$.
Daarnaast zeggen we dat een rij $U$ een **universele gemeenschappelijke deelrij** is van $A$ en $B$
 dan en slechts dan als deze voldoet aan de volgende twee voorwaarden:
* $U$ is een gemeenschappelijke deelrij van $A$ en $B$.
* Elke gemeenschappelijke deelrij van $A$ en $B$ is ook een deelrij van $U$.

Er kan worden aangetoond dat voor elke twee rijen $A$ en $B$ hoogstens één universele gemeenschappelijke deelrij hebben.

De onderzoekers hebben twee rijen hiërogliefen $A$ en $B$ gevonden.
Rij $A$ bestaat uit $N$ hiërogliefen
 en rij $B$ bestaat uit $M$ hiërogliefen.
Help de onderzoekers met het berekenen
van een universele gemeenschappelijke deelrij van de rijen $A$ en $B$,
 of stel vast dat een dergelijke rij niet bestaat.

## Implementatiedetails

Je moet de volgende procedure uit voeren.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: array met lengte $N$, de eerste rij.
* $B$: array met lengte $M$, de tweede rij.
* Als er een universele gemeenschappelijke deelrij van $A$ en $B$ bestaat, moet de procedure een array returnen die deze sequentie bevat.
  Anders moet de procedure $[-1]$ returnen.
   (een array met lengte $1$, waarvan het enige element $-1$ is).
* Deze procedure wordt voor elke testcase precies één keer aangeroepen.

## Beperkingen

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ voor elke $i$ zodat $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ voor elke $j$ zodat $0 \leq j < M$

## Subtaken

| Subtaak | Score  | Extra Beperkingen |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; $A$ en $B$ bestaan beide uit $N$ **unieke** integers tussen $0$ en $N-1$ (inclusief)
| 2       | $15$   | Voor alle integers $k$ geldt dat (het aantal elementen in $A$ gelijk aan $k$) plus (het aantal elementen in $B$ gelijk aan $k$) niet meer dan $3$ is.
| 3       | $10$   | $A[i] \leq 1$ voor elke $i$ zodat $0 \leq i < N$; $B[j] \leq 1$ voor elke $j$ zodat $0 \leq j < M$
| 4       | $16$   | Er bestaat een universele gemeenschappelijke deelrij van $A$ en $B$.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | Geen extra beperkingen.

## Voorbeelden

### Voorbeeld 1

Bekijk de volgende call.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Hier zijn de gemeenschappelijke deelrijen van $A$ en $B$ de volgende:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ and $[0, 1, 0, 2]$.

Omdat $[0, 1, 0, 2]$ een gemeenschappelijke deelrij is van $A$ en $B$, en
 alle gemeenschappelijke deelrijen van $A$ en $B$ deelrijen zijn van $[0, 1, 0, 2]$,
 moet de procedure $[0, 1, 0, 2]$ returnen.
### Voorbeeld 2

Bekijk de volgende call.

```
ucs([0, 0, 2], [1, 1])
```

Hier is de enige gemeenschappelijke deelrij van $A$ en $B$ de lege rij $[\ ]$.
Hieruit volgt dat de procedure een lege array $[\ ]$ moet returnen.

### Example 3

Bekijk de volgende call.
```
ucs([0, 1, 0], [1, 0, 1])
```

Hier zijn de gemeenschappelijke deelrijen van $A$ en $B$
 $[\ ], [0], [1], [0, 1]$ $[1, 0]$.
Er kan worden aangetoond dat er geen universele gemeenschappelijke deelrij bestaat.
Daarom moet de procedure $[-1]$ returnen.

## Voorbeeldgrader

Invoerformaat:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Uitvoerformaat:

```
T
R[0]  R[1]  ...  R[T-1]
```

Hier is $R$ de array gereturnt door `ucs` en $T$ de lengte van de array.
