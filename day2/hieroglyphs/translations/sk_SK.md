# Hieroglyfy

Skupina výskumníkov študuje podobnosti medzi postupnosťami hieroglyfov. Každý hieroglyf označujú nezáporným celým číslom.

Pre danú postupnosť $A$ sa postupnosť $S$ nazýva **podpostupnosť** postupnosti $A$ práve vtedy, keď je možné postupnosť $S$ vytvoriť z postupnosti $A$ odstránením niektorých jej prvkoch (vrátane žiadneho).

Tabuľka nižšie ukazuje niektoré podpostupnosti postupnosti $A = [3, 2, 1, 2]$.

| Podpostupnosť    | Ako ju môžeme dosiahnuť z postupnosti $A$ |
|----------------|---------------------------------|
| [3, 2, 1, 2] | Nebol odstránený žiadny prvok.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] alebo [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Postupnosti $[3, 3]$ a $[1, 3]$ nie sú podpostupnosťami vyššie uvedenej postupnosti $A$.

Uvažujme dve postupnosti hieroglyfov $A$ a $B$.
Postupnosť $S$ sa nazýva **spoločná podpostupnosť** postupností $A$ a $B$ práve vtedy, keď $S$ je podpostupnosťou $A$ a zároveň je aj podpostupnosťou $B$. Postupnosť $U$ nazývame **univerzálnou spoločnou podpostupnosťou** postupností $A$ a $B$ práve vtedy, keď platia nasledovné podmienky:
* $U$ je spoločná podpostupnosť postupností $A$ a $B$.
* každá spoločná podpostupnosť postupností $A$ a $B$ je taktiež podpostupnosťou postupnosti $U$.

Dá sa dokázať, že ľubovoľné dve postupnosti $A$ a $B$ majú *najviac jednu* univerzálnu spoločnú podpostupnosť.

Výskumníci objavili dve postupnosti hieroglyfov $A$ a $B$.
Postupnosť $A$ pozostáva z $N$ hieroglyfov a postupnosť $B$ z $M$ hieroglyfov.
Pomôžte výskumníkom spočítať univerzálnu spoločnú podpostupnosť postupností $A$ a $B$, resp. určte, že žiadna univerzálna spoločná podpostupnosť neexistuje.

## Implementačné detaily

Implementujte nasledovnú funkciu:

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: pole dĺžky $N$ popisujúce prvú postupnosť.
* $B$: pole dĺžky $M$ popisujúce druhú postupnosť.
* Ak univerzálna spoločná podpostupnosť postupností $A$ a $B$ existuje, funkcia má vrátiť pole obsahujúce túto podpostupnosť. V opačnom prípade má vrátiť $[-1]$,  teda jednoprvkové pole obsahujúce hodnotu  $-1$.
* Táto funkcia je zavolaná práve raz pre každý vstup.

## Obmedzenia

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ pre každé $i$ také, že $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ pre každé $j$ také, že $0 \leq j < M$

## Podúlohy

| Podúloha | Body  | Dodatočné obmedzenia |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; každá z postupností $A$ a $B$ obsahuje $N$ *rôznych* celých čísel z rozsahu $0$ až $N-1$ (vrátane)
| 2       | $15$   | Pre každé celé číslo $k$ platí, že (počet prvkov postupnosti $A$ rovnajúcich sa hodnote $k$) *plus* (počet prvkov postupnosti $B$ rovnajúcich sa hodnote $k$) je najviac $3$.
| 3       | $10$   | $A[i] \leq 1$ pre každé $i$ také, že $0 \leq i < N$; $B[j] \leq 1$ pre každé $j$ také, že $0 \leq j < M$
| 4       | $16$   | Univerzálna spoločná podpostupnosť postupností $A$ a $B$ existuje.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | Bez dodatočných obmedzení.

## Príklady

### Príklad 1

Uvažujme nasledovné volanie:

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

V tomto prípade sú spoločné podpostupnosti postupností $A$ a $B$:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ a $[0, 1, 0, 2]$.

Keďže $[0, 1, 0, 2]$ je spoločná podpostupnosť postupností $A$ a $B$ a zároveň všetky spoločné podpostupnosti postupností $A$ a $B$ sú podpostupnosťou postupnosti $[0, 1, 0, 2]$, funkcia má vrátiť  pole $[0, 1, 0, 2]$.

### Príklad 2

Uvažujme nasledovné volanie:

```
ucs([0, 0, 2], [1, 1])
```

V tomto prípade jedinou spoločnou podpostupnosťou postupností $A$ a $B$ je prázdna postupnosť $[\ ]$.
To znamená, že funkcia má vrátiť prázdne pole $[\ ]$.

### Príklad 3

Uvažujme nasledovné volanie:
```
ucs([0, 1, 0], [1, 0, 1])
```

V tomto prípade spoločné podpostupnosti postupností $A$ a $B$ sú
 $[\ ], [0], [1], [0, 1]$ a $[1, 0]$.
Dá sa ukázať, že univerzálna spoločná podpostupnosť v tomto prípade neexistuje. Funkcia má preto vrátiť pole $[-1]$.

## Vzorový testovač

Formát vstupu:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Formát výstupu:

```
T
R[0]  R[1]  ...  R[T-1]
```

$R$ je pole vrátené funkciou `ucs` a $T$ je jeho dĺžka.
