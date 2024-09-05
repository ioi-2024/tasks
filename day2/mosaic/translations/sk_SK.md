# Stena

V T2 je čerstvo vymaľovaná *sivá* stena. Krtkovi sa to príliš nepozdáva a rád by ju zafarbil. Nebude to však robiť len tak hala-bala.

Stenu si môžete predstaviť ako mriežku $N \times N$ štvorcov, pričom na začiatku je všetkých $N^2$ štvorcov *neofarbených*. Riadky steny očíslujeme od $0$ po $N-1$ zvrchu nadol. Stĺpce steny očíslujeme od $0$ po $N - 1$ zľava doprava. Štvorec v riadku $i$ a stĺpci $j$ ($0 \leq i < N$, $0 \leq j < N$) označíme $(i, j)$. Každé políčko steny *musí Krtko zafarbiť*, a to buď bielou farbou (označená hodnotou $0$) alebo čiernou farbou (označená hodnotou $1$).

Pred začiatkom farbenia si Krtko zvolí dve polia $X$ a $Y$ dĺžky $N$, ktoré obsahujú hodnoty $0$ a $1$, pričom musí platiť, že $X[0] = Y[0]$. Vrchný riadok (riadok číslo $0$) zafarbí Krtko podľa poľa $X$ tak, aby farba štvorca $(0, j)$ bola farba $X[j]$ (pre všetky $0 \leq j < N$). Ľavý stĺpec (stĺpec číslo $0$) zafarbí Krtko podľa poľa $Y$ tak, aby farba štvorca $(i, 0)$ bola farba $Y[i]$ (pre všetky $0 \leq i < N$).

Následne opakuje nasledovné kroky, až kým nezafarbí všetky štvorce steny:
* Krtko nájde ľubovoľný *nezafarbený* štvorec $(i,j)$ taký, že horný sused (štvorec $(i-1, j)$) aj jeho ľavý sused (štvorec $(i, j-1)$) sú oba *už zafarbené*.
* Následne zafarbí štvorec $(i,j)$ čiernou farbou (farba $1$) ak sú obaja spomenutí susedia bieli (farba $0$); inak zafarbí štvorec $(i,j)$ bielou farbou (farba $0$).

Dá sa ukázať, že výsledné ofarbenie steny je jednoznačné bez ohľadu na poradie, v ktorom Krtko štvorce farbí.

Emmu Krtkova maľba veľmi zaujala, položila mu preto $Q$ otázok očíslovaných od $0$ po $Q-1$. V $k$-tej ($0 \leq k < Q$) otázke si Emma vyberie výsek steny. Ten určí zadaním jeho:
* vrchného riadku $T[k]$ a spodného riadku $B[k]$ ($0 \leq T[k] \leq B[k] < N$)
* ľavého stĺpca $L[k]$ a pravého stĺpca $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

Krkovou úlohou je zistiť, koľko čiernych (farba $1$) štvorcov je v určenom výseku steny. Presnejšie, koľko je takých štvorcov $(i, j)$, že $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$ a farba štvorca $(i,j)$ je čierna (farba $1$).

Pomôžte Krtkovi, kým sa on učí na štátnice (určite zase nejaké bude mať).

## Implementačné detaily

Vašou úlohou je implementovať funkciu:

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: polia dĺžky $N$ popisujúce farbu štvorcov v najvrchnejšom riadku a najľavejšom stĺpci.
* $T$, $B$, $L$, $R$: polia dĺžky $Q$ popisujúce Emmine otázky.
* Funkcia musí vrátiť pole $C$ dĺžky $Q$ také, že hodnota $C[k]$ je odpoveďou na otázku $k$ ($0 \leq k < Q$).
* Táto funkcia je zavolaná práve raz pre každý vstup.

## Obmedzenia

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ a $Y[i] \in \{0, 1\}$ pre všetky $i$ také, že $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ a $0 \leq L[k] \leq R[k] < N$ pre všetky $k$ také, že $0 \leq k < Q$

## Podúlohy

| Podúloha | Skóre  | Dodatočné obmedzenia |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ (pre všetky $k$ také, že $0 \leq k < Q$)
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ (pre všetky $i$ také, že $0 \leq i < N$)
| 6       | $22$   | $T[k] = B[k]$ a $L[k] = R[k]$ (pre všetky $k$ také, že $0 \leq k < Q$)
| 7       | $19$   | $T[k] = B[k]$ (pre všetky $k$ také, že $0 \leq k < Q$)
| 8       | $22$   | Bez dodatočných obmedzení.

## Príklad

Uvažujte nasledovné volanie:

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Tento príklad je zobrazený na obrázku nižšie. Ľavý obrázok ukazuje pomocou čísel $0$ a $1$ farby štvorcov na celej stene. Stredný a pravý obrázok majú vyfarbené výseky, na ktoré sa pýta Emma v otázke nula a otázke jedna.

![](example.png "550")

Vo výseku z otázky nula je $7$ jednotiek, vo výseku z otázky jedna sú $3$. Výsledkom funkcie preto má byť pole $[7, 3]$.

## Ukážkový testovač

Formát vstupu:

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

Formát výstupu:

```
C[0]
C[1]
...
C[S-1]
```

Hodnota $S$ je dĺžka poľa $C$ vráteného funkciou `mosaic`.