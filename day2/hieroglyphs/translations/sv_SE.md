# 象形文字 (Hieroglyfer)
En grupp av forskare studerar likheter mellan sekvenser av 象形文字 (hieroglyfer).
Varje 象形文字 (hieroglyf) kan representeras med ett icke-negativt heltal.
För att utföra sina studier använder de följande begrepp när de pratar om sekvenser.
 
 För en given sekvens $A$, så säger vi att sekvens $S$ är en **delsekvens** av $A$ om och endast om $S$ kan skapas genom att ta bort några element (möjligen inga) från $A$.

Tabellen nedan visar några exempel på delsekvenser av en sekvens $A = [3, 2, 1, 2]$ .

| Delsekvens    | Hur den kan skapas från $A$ |
|----------------|---------------------------------|
| [3, 2, 1, 2] | Inga element tas bort.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] or [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Å andra sidan är $[3, 3]$ eller $[1, 3]$ inte delsekvenser av $A$.

Betrakta två sekvenser av 象形文字 (hieroglyfer), $A$ och $B$.
Vi säger att en sekvens $S$ är en **gemensam delsekvens** av $A$ och $B$ om och endast om $S$ är en delsekvens av både $A$ och $B$.
Dessutom säger vi att en sekvens $U$ är en **universellt gemensam delsekvens** av $A$ och $B$ om och endast om följande två villkor är uppfyllda:
* $U$ är en gemensam delsekvens av $A$ och $B$ .
* Varje gemensam delsekvens av $A$ och $B$ är också en delsekvens av $U$ .

Det kan bevisas att för alla sekvenser $A$ och $B$ finns det som mest en universell gemensam följd.

Forskarna har hittat två sekvenser av 象形文字 (hieroglyfer) $A$ och $B$.
Sekvens $A$ består av $N$ 象形文字 (hieroglyfer) och sekvensen $B$ består av $M$ 象形文字 (hieroglyfer).
Hjälp forskarna att beräkna en universell gemensam delsekvens av sekvenserna $A$ och $B$, eller bestämma att en sådan sekvens inte existerar.

## Implementationsdetaljer

Sofie, du *bör* nu implementera följande funktioner (annars blir det svårt att lösa problemet (!)):

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```
* $A$: en array av längd $N$ som beskriver den första sekvensen.
* $B$: en array av längd $M$ som beskriver den andra sekvensen.
* Om det finns en universell gemensam delsekvens av $A$ och $B$, så bör funktionen returnera en array som innehåller denna sekvens.
  Annars bör funktionen returnera $[-1]$
   (en array av längd $1$, vars enda element är $-1$).
* Denna funktion anropas exakt en gång för varje testfall.


## Begränsningar

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ för alla $i$ sådan att $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ för alla $j$ sådan att $0 \leq j < M$

## Subtasks

| Grupp | Poäng  | Ytterligare Begränsningar |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; för varje array $A$ och $B$, så består arrayen av $N$ **unika** heltal mellan $0$ och $N-1$ (inklusivt).
| 2       | $15$   | För alla heltal $k$, så gäller: (antalet element i $A$ som är lika med $k$) + (antalet element i $B$ som är lika med $k$) $\leq 3$.
| 3       | $10$   | $A[i] \leq 1$ för alla $i$ sådan att $0 \leq i < N$; $B[j] \leq 1$ för alla $j$ sådan att $0 \leq j < M$.
| 4       | $16$   | Det finns en universell gemensam delsekvens av $A$ och $B$.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$.
| 6       | $42$   | Inga ytterligare begränsningar.

## Exempel

### Exempel 1

Fundera hårt på följande anrop:

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Alla gemensamma delsekvenser av $A$ och $B$ är de följande:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ and $[0, 1, 0, 2]$.

Eftersom $[0, 1, 0, 2]$ är en gemensam delsekvens av $A$ och $B$, och alla gemensamma delsekvenser av $A$ och $B$ är delsekvenser av $[0, 1, 0, 2]$,
 så bör funktionen returnera $[0, 1, 0, 2]$.

### Exempel 2

Fundera mjukt på föjande anrop:

```
ucs([0, 0, 2], [1, 1])
```

Här är den enda gemensamma delsekvensen av $A$ och $B$ den tomma sekvensen $[\ ]$.
Det innebär att funktionen bör returnera en tom array $[\ ]$.

### Exempel 3

Locka nu in för följande anrop:
```
ucs([0, 1, 0], [1, 0, 1])
```

Här är de gemensamma delsekvenserna av $A$ och $B$:
 $[\ ], [0], [1], [0, 1]$ och $[1, 0]$.
Det kan visas att universell gemensam delsekvens inte existerar.
Därför ska funktionen returnera $[-1]$ .

## Exempelgrader

Input-format är givet på följande sätt:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Output-format är givet på följande sätt:

```
T
R[0]  R[1]  ...  R[T-1]
```

Här är $R$ arrayen som returneras av `ucs` och $T$ är dess längd.