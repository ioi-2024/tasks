# Mozaika
Salma plánuje obarvit hliněnou mozaiku na zdi.
Mozaika je $N \times N$ mřížka, vyrobená z $N^2$ na začátku neobarvených dlaždiček.
Řádky mozaiky jsou očíslované od $0$ do $N-1$ svrchu dolů, a sloupce jsou očíslované
od $0$ do $N-1$ zleva doprava. Dlaždičku v řádku $i$ a sloupci $j$ ($0 \leq i < N$, $0 \leq j < N$)
značíme $(i, j)$. Každá dlaždička může být obarvena bíle (značíme $0$), nebo černě (značíme $1$).

Aby obarvila mozaiku, Salma si nejprve vybere dvě pole $X$ a $Y$ délky $N$,
každé skládající se z hodnot $0$ a $1$, kde $X[0] = Y[0]$.
Dlaždičky vrchní řady (řady $0$) obarví podle pole $X$ tak, že barva dlaždičky $(0,j)$ je $X[j]$ ($0 \leq j < N$).
Dále, dlaždičky nejlevějšího sloupce (sloupce $0$) obarví podle pole $Y$ tak,
že barva dlaždičky $(i, 0)$ je $Y[i]$ ($0 \leq i < N$).

Potom opakuje následující kroky, dokud všechny dlaždičky nejsou nabarvené:
* Najde libovolnou *neobarvenou* dlaždičku $(i,j)$ takovou, že její horní soused (dlaždička $(i-1,j)$) a levý soused (dlaždička $(i,j-1)$) jsou obě *již obarvené*.
* Dále, obarví dlaždičku $(i,j)$ černě, pokud oba tito sousedé jsou bílí, jinak tuto dlaždičku obarví bíle.

Lze dokázat, že závěrečné obarvení dlaždiček nezáleží na pořadí, v jakém je Salma barví.

Yasmin je velmi zvědavá ohledně barev dlaždiček v mozaice. Ptá se Salmy na $Q$ dotazů
očíslovaných od $0$ do $Q-1$. V dotazu $k$ ($0 \leq k < Q$), Yasmin určí obdélník daný:
* Jeho vrchním řádkem $T[k]$ a spodním řádkem $B[k]$ ($0 \leq T[k] \leq B[k] < N$).
* Jeho nejlevějším sloupcem $L[k]$ a nejpravějším sloupcem $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

Odpovědí na tento dotaz je počet černých dlaždiček v tomto podobdélníku. Konkrétně,
Salma by měla zjistit, kolik existuje dlaždiček $(i, j)$ takových, že $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$,
a barva dlaždičky $(i,j)$ je černá.

Napište program zodpovídající dotazy od Yasmin.

## Implementační detaily

Vaším úkolem je implementovat následující funkci.

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: pole délky $N$ popisující barvy dlaždiček ve vrchním řádku a nejlevějším sloupci (v tomto pořadí).
* $T$, $B$, $L$, $R$: pole délky $Q$ popisující dotazy od Yasmin.
* Tato funkce by měla vrátit pole $C$ délky $Q$, kde $C[k]$ je odpověď na dotaz $k$ ($0 \leq k < Q$).
* This funkce je zavolána právě jednou pro každý vstup.

## Omezení

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ a $Y[i] \in \{0, 1\}$
 pro každé $i$ takové, že $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ a $0 \leq L[k] \leq R[k] < N$
 pro každé $k$ takové, že $0 \leq k < Q$

## Podúlohy

| Podúloha | Počet bodů  | Dodatečná omezení |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ (pro každé $k$ takové, že $0 \leq k < Q$)
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ (pro každé $i$ takové, že $0 \leq i < N$)
| 6       | $22$   | $T[k] = B[k]$ a $L[k] = R[k]$ (pro každé $k$ takové, že $0 \leq k < Q$)
| 7       | $19$   | $T[k] = B[k]$ (pro každé $k$ takové, že $0 \leq k < Q$)
| 8       | $22$   | Žádná další omezení.

## Příklad

Uvažujme následující zavolání.

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Tento příklad je ilustrován na obrázcích níže. Levý obrázek zobrazuje barvy dlaždiček v mozaice.
Prostřední a pravý obrázek ukazují podobdélníky, na které se Yasmin ptala v prvním a druhém dotazu.

![](example.png "550")

Odpovědí na tyto dotazy (tedy počet jedniček v šedých obdélnících) jsou 7 a 3 (v tomto pořadí).
Tedy, funkce by měla vrátit $[7, 3]$.

## Ukázkový grader

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

Zde $S$ je délka pole $C$ vráceného `mosaic`.