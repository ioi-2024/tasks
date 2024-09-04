# Níl
Cez rieku Níl chcete prepraviť $N$ artefaktov, ktoré sú očíslované od $0$ po $N-1$. Hmotnosť artefaktu $i$ ($0 \leq i < N$) je $W[i]$ .

Na prepravu artefaktov sa používajú špecializované člny, pričom každý čln môže niesť **najviac dva** artefakty.

* Ak sa rozhodnete umiestniť do člna len jeden artefakt, jeho hmotnosť môže byť ľubovoľná.
* Ak však chcete do jedného člna umiestniť naraz dva artefakty, musíte sa uistiť, že je čln rovnomerne vyvážený.
Konkrétne, na tom istom člne môžete poslať artefakty $p$ a $q$ ($0 \leq p < q < N$) len vtedy, ak je absolútny rozdiel medzi ich váhami najviac $D$, t.j., $|W[p] - W[q]| \leq D$ .

Za prepravu každého artefaktu musíte zaplatiť cenu, ktorá závisí od toho, či je na člne s iným artefaktom. Presnejšie, náklady na prepravu artefaktu $i$ ($0 \leq i < N$) sú:

* $A[i]$ , ak artefakt vložíte do samostatného člna, resp.
* $B[i]$ , ak ho vložíte do člna spolu s nejakým iným artefaktom.

V druhom prípade je potrebné zaplatiť za oba artefakty v člne. Teda ak sa rozhodnete poslať
 artefakty $p$ a $q$ ($0 \leq p < q < N$) na tom istom člne, musíte zaplatiť $B[p] + B[q]$ peňazí.
 
Platí, že vždy je drahšie poslať artefakt sám, ako spolu s iným artefaktom. Teda $B[i] < A[i]$ pre všetky $i$ také, že $0 \leq i < N$.

Bohužiaľ, rieka je veľmi nepredvídateľná a hodnota $D$ sa často mení.
Vašou úlohou je zodpovedať $Q$ otázok očíslovaných od $0$ po $Q-1$ .

Všetky otázky sú popísané poľom $E$ dĺžky $Q$. Odpoveďou na $j$-tu otázku ($0 \leq j < Q$) sú
 minimálne celkové náklady na prepravu všetkých $N$ artefaktov, ak sa hodnota $D$ rovná $E[j]$ .


## Implementačné detaily

Vašou úlohou je implementovať nasledujúcu funkciu:

```
std::vector&lt;long long&gt; calculate_costs(
    std::vector&lt;int&gt; W, std::vector&lt;int&gt; A, 
    std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```

* $W$, $A$, $B$: polia celých čísel dĺžky $N$ popisujúce hmotnosti artefaktov a náklady na ich prepravu.
* $E$ : pole celých čísel dĺžky $Q$ popisujúce hodnotu $D$ pre každú otázku.
* Táto funkcia by mala vrátiť pole $R$ obsahujúce $Q$ celých čísel &ndash;
   minimálne celkové náklady na prepravu artefaktov,
   kde $R[j]$ udáva náklady, ak je hodnota $D$ rovná $E[j]$ (pre každé $j$
   také, že $0 \leq j < Q$).
* Táto funkcia sa volá presne raz pre každú testovaciu sadu.

## Obmedzenia

* $1 \leq N \leq 100\,000$
* $1 \leq Q \leq 100\,000$
* $1 \leq W[i] \leq 10^{9}$
  pre každé $i$ také, že $0 \leq i < N$
* $1 \leq B[i] < A[i] \leq 10^{9}$
   pre každé $i$ také, že $0 \leq i < N$
* $1 \leq E[j] \leq 10^{9}$
   pre každé $j$ také, že $0 \leq j < Q$

## Podúlohy

| Podúloha | Body  | Dodatočné obmedzenia |
| :-----: | :----: | ---------------------- |
| 1       | $6$    | $Q \leq 5$; $N \leq 2000$; $W[i] = 1$ pre každé $i$ také, že $0 \leq i < N$
| 2       | $13$   | $Q \leq 5$; $W[i] = i+1$ pre každé $i$ také, že $0 \leq i < N$
| 3       | $17$   | $Q \leq 5$; $A[i] = 2$ a $B[i] = 1$ pre každé $i$ také, že $0 \leq i < N$
| 4       | $11$   | $Q \leq 5$; $N \leq 2000$
| 5       | $20$   | $Q \leq 5$
| 6       | $15$   | $A[i] = 2$ a $B[i] = 1$ pre každé $i$ také, že $0 \leq i < N$
| 7       | $18$   | Bez dodatočných obmedzení.

## Príklad

Uvažujme nasledujúce volanie:

```
calculate_costs([15, 12, 2, 10, 21],
                [5, 4, 5, 6, 3],
                [1, 2, 2, 3, 2],
                [5, 9, 1])
```

V tomto príklade máme $N = 5$ artefaktov a $Q = 3$ otázok.

V prvej otázke je $D = 5$ .
V jednom člne môžeme poslať artefakty $0$ a $3$ (keďže $|15 - 10| \leq 5$ ), zvyšné artefakty sa budú plaviť samostatne.
Výsledkom sú minimálne náklady na prepravu všetkých artefaktov, ktoré sú $1+4+5+3+3 = 16$ .

V druhej otázke je $D = 9$ .
Spolu môžeme poslať artefakty $0$ a $1$ (keďže $|15 - 12| \leq 9$ ) a artefakty $2$ a $3$ (keďže $|2 - 10| \leq 9$ ).
Zostávajúci artefakt $4$ pošleme samostatne.
Výsledkom sú minimálne náklady na prepravu všetkých artefaktov, ktoré sú $1+2+2+3+3 = 11$ .

V poslednej otázke je $D = 1$. Každý artefakt musíme poslať samostatne, výsledkom čoho dostaneme náklady $5+4+5+6+3 = 23$ .

Funkcia by teda mala vrátiť pole $[16, 11, 23]$.


## Ukážkový testovač

Formát vstupu:

```
N
W[0] A[0] B[0]
W[1] A[1] B[1]
...
W[N-1] A[N-1] B[N-1]
Q
E[0]
E[1]
...
E[Q-1]
```

Formát výstupu:

```
R[0]
R[1]
...
R[S-1]
```

Hodnota $S$ je dĺžka poľa $R$ vráteného parametrom `calculate_costs`.

