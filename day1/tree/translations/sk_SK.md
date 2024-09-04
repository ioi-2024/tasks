# Strom

Uvažujme zakorenený **strom** pozostávajúci z $N$ **vrcholov**
 očíslovaných od $0$ po $N-1$.
Vrchol $0$ nazveme **koreň**.
Každý vrchol (okrem koreňa) má práve jedného **rodiča**.
Pre každé $i$ také, že $1 \leq i < N$ je
 rodičom vrchola $i$ vrchol $P[i]$, kde $P[i] < i$.
Navyše predpokladáme, že $P[0] = -1$.

Pre každý vrchol $i$ ($0 \leq i < N$) nazveme
 **podstromom vrchola $i$** nasledujúcu množinu vrcholov:
 * vrchol $i$,
 * všetky vrcholy, ktorých rodičom je vrchol $i$,
 * všetky vrcholy, ktorých starým rodičom (rodič rodiča) je vrchol $i$,
 * všetky vrcholy, ktorých prarodičom (rodič starého rodiča) je vrchol $i$, 
 * atď.

Obrázok nižšie ukazuje príklad stromu s $N = 6$ vrcholmi.
Každá šípka smeruje od vrchola k jeho rodičovi,
 s výnimkou koreňa, ktorý rodiča nemá.
Podstrom vrchola $2$ obsahuje vrcholy $2, 3, 4$ a $5$.
Podstrom vrchola $0$ obsahuje všetkých šesť vrcholov stromu
 a podstrom vrchola $4$ obsahuje iba vrchol $4$.

![](subtrees.png "150")

Každý vrchol $i$ ($0 \leq i < N)$ má priradenú **váhu** &ndash; nezáporné celé číslo $W[i]$.

Vašou úlohou je napísať program, ktorý zodpovie $Q$ otázok,
každú zadanú dvojicou kladných celých čísel $(L, R)$.
Odpoveď na otázku $(L, R)$ sa vypočíta nasledovne:

Uvažujme priradenie celého čísla,
 nazývaného **koeficient**, každému vrcholu stromu.
Takéto priradenie je popísané postupnosťou $C[0], \ldots, C[N-1]$,
 kde $C[i]$ (pre $0 \leq i < N$) je koeficient priradený vrcholu $i$.
Túto postupnosť nazvime **postupnosť koeficientov**, pričom koeficienty môžu byť záporné, kladné aj nulové.

Pre otázku $(L, R)$ je postupnosť koeficientov **platná** vtedy, ak pre každý vrchol $i$ ($0 \leq i < N$)
 platí, že súčet koeficientov vrcholov podstromu vrchola $i$ nie je menej ako $L$ ani viac ako $R$.

Pre danú postupnosť koeficientov $C[0], \ldots, C[N-1]$ je
 **cena** vrchola $i$ rovná hodnote $|C[i]| \cdot W[i]$,
 kde $|C[i]|$ označuje absolútnu hodnotu $C[i]$.
**Celková cena** je súčet cien všetkých vrcholov.
Vašou úlohou je pre každú otázku spočítať,
**minimálnu celkovú cenu**, ktorá môže byť dosiahnutá platnou postupnosťou koeficientov.

Dá sa ukázať, že pre ľubovoľnú otázku existuje aspoň jedna validná postupnosť koeficientov.

## Implementačné detaily

Implementujte nasledujúce dve funkcie:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$: polia celých čísel dĺžky $N$
   určujúce rodičov a váhy.
* Táto funkcia je volaná v každej testovacej sade
   na začiatku interakcie medzi testovačom a vašim programom práve raz.

```
long long query(int L, int R)
```
* $L$, $R$: celé čísla popisujúce jednu otázku.
* Táto funkcia je po volaní funkcie `init` zavolaná $Q$ krát.
* Táto funkcia má vrátiť odpoveď k zadanej otázke.


## Obmedzenia

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ pre každé $i$ také, že $1 \leq i < N$
* $0 \leq W[i] \leq 1\,000\,000$ pre každé $i$ také, že $0 \leq i < N$
* $1 \leq L \leq R \leq 1\,000\,000$ v každej otázke

## Podúlohy

| Podúloha | Bodovanie | Dodatočné obmedzenia |
| :-----: | :----: | ---------------------- |
|   1     |  $10$  | $Q \leq 10$; $W[P[i]] \leq W[i]$ pre každé $i$ také, že $1 \leq i < N$
|   2     |  $13$  | $Q \leq 10$; $N \leq 2\,000$
|   3     |  $18$  | $Q \leq 10$; $N \leq 60\,000$
|   4     |  $7$   | $W[i] = 1$ pre každé $i$ také, že $0 \leq i < N$
|   5     |  $11$  | $W[i] \leq 1$ pre každé $i$ také, že $0 \leq i < N$
|   6     |  $22$  | $L = 1$
|   7     |  $19$  | Bez dodatočných obmedzení.



## Príklad

Uvažujme nasledovné volanie:

```
init([-1, 0, 0], [1, 1, 1])
```
Strom pozostáva z $3$ vrcholov: koreňa a jeho dvoch potomkov.
Všetky vrcholy majú váhu $1$.

```
query(1, 1)
```

V tejto otázke platí $L = R = 1$,
 čo znamená, že súčet koeficientov každého podstromu musí byť $1$.
Uvažujme postupnosť koeficientov $[-1, 1, 1]$.
Tento strom a prislúchajúce koeficienty (v sivých obdĺžnikoch) sú zobrazené nižšie.

![](ex1.png "150")

Pre každý vrchol $i$ ($0 \leq i < 3$) je súčet koeficientov všetkých vrcholov podstromu vrchola $i$ rovný $1$. 
Táto postupnosť koeficientov je preto platná.
Ceny vrcholov vypočítame nasledovne:

| Vrchol | Váha | Koeficient | Cena                      |
| :----: | :----: | :---------: | :-----------------------: |
|   0    |   1    |     $-1$      | $\mid -1 \mid \cdot 1 = 1$
|   1    |   1    |      $1$      | $\mid 1 \mid \cdot 1 = 1$
|   2    |   1    |      $1$      | $\mid 1 \mid \cdot 1 = 1$

Celková cena je $3$.
Keďže toto je jediná platná postupnosť koeficientov, volanie tejto funkcie musí vrátiť hodnotu $3$.

```
query(1, 2)
```
Najmenšia celková cena pre túto otázku je $2$ a dá sa dosiahnuť postupnosťou koeficientov $[0, 1, 1]$.

## Ukážkový testovač

Formát vstupu:

```
N
P[1]  P[2] ...  P[N-1]
W[0]  W[1] ...  W[N-2] W[N-1]
Q
L[0]  R[0]
L[1]  R[1]
...
L[Q-1]  R[Q-1]
```

kde $L[j]$ a $R[j]$
 (pre $0 \leq j < Q$)
 sú vstupné argumenty v $j$-tom volaní funkcie `query`.
Všimnite si, že druhý riadok vstupu obsahuje **len $N-1$ celých čísel**,
keďže hodnota $P[0]$ je automaticky $-1$.

Formát výstupu:
```
A[0]
A[1]
...
A[Q-1]
```

kde $A[j]$
 (pre $0 \leq j < Q$)
 je hodnota vrátená $j$-tym volaním funkcie `query`.
