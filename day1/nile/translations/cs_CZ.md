# Nil

Vaším úkolem je přepravit $N$ artefaktů po Nilu. Artefakty jsou očíslované $0$ až $N-1$.
Váha artefaktu $i$ ($0 \leq i < N$) je $W[i]$.

Na přepravu artefaktů používáte specializované čluny. Každý člun může přepravovat **nejvýše dva** artefakty.

* Pokud se rozhodnete člunem přepravit jeden artefakt, může mít libovolnou váhu.
* Při přepravě dvou artefaktů musíte zajistit, že člun je dobře vyvážený. Přesněji, můžete poslat artefakty $p$ a $q$ ($0 \leq p < q < N$)
ve stejném čluny právě tehdy, když absolutní hodnota rozdílu hmotností předmětů je nejvýš $D$, tedy $|W[p] - W[q]| \leq D$.

Abyste přepravili artefakt, musíte zaplatit. Cena záleží na počtu artefaktů ve stejné lodi. Cena přepravy artefaktu $i$ je:

* $A[i]$, pokud přepravujete artefakt ve své vlastní lodi.
* $B[i]$, pokud ho přepravujete spolu s jiným artefaktem.

Poznamenejme, že v druhém případě musíte zaplatit za oba artefakty na lodi.
Přesněji, pokud pošlete artefakty $p$ a $q$ ($0 \leq p < q < N$) ve stejné lodi, zaplatíte $B[p] + B[q]$.

Poslat artefakt na lodi samostatně je vždy dražší než poslat ho spolu s jiným artefaktem,
tedy $B[i] < A[i]$ pro všechna $i$ taková, že $0 \leq i < N$.

Bohužel, řeka je velmi nepředvídatelná a hodnota $D$ se často mění. Vaším úkolem
je zodpovědět $Q$ dotazů očíslovaných od $0$ do $Q-1$. Dotazy jsou popsány polem $E$ délky $Q$.
Odpověď na otázku $j$ ($0 \leq j < Q$) je minimální celková cena přepravy všech $N$ artefaktů, když se hodnota $D$ rovná $E[j]$.

## Implementační detaily

Máte za úkol implementovat následující funkci:

```
std::vector&lt;long long&gt; calculate_costs(
    std::vector&lt;int&gt; W, std::vector&lt;int&gt; A, 
    std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```

* $W$, $A$, $B$: pole celých čísel délky $N$, popisujících váhy artefaktů a ceny jejich přepravy.
* $E$: pole celých čísel délky $Q$ popisující hodnotu $D$ pro každý dotaz.
* Tato funkce by měla vracet pole $R$ tvořené $Q$ celými čísly, popisující minimální cenu přepravy artefaktů. $R[j]$ udává minimální cenu, když hodnota $D$ je $E[j]$ (pro každé $j$ takové, že $0 \leq j < Q$).
* Tato funkce je zavolána právě jednou pro každý vstup.

## Omezení

* $1 \leq N \leq 100\,000$
* $1 \leq Q \leq 100\,000$
* $1 \leq W[i] \leq 10^{9}$
   pro každé $i$ takové, že $0 \leq i < N$
* $1 \leq B[i] < A[i] \leq 10^{9}$
   pro každé $i$ takové, že $0 \leq i < N$
* $1 \leq E[j] \leq 10^{9}$
   pro každé $j$ takové, že $0 \leq j < Q$

## Podúlohy

| Podúloha | Počet bodů  | Dodatečná omezení |
| :-----: | :----: | ---------------------- |
| 1       | $6$    | $Q \leq 5$; $N \leq 2000$; $W[i] = 1$ pro každé $i$ takové, že $0 \leq i < N$
| 2       | $13$   | $Q \leq 5$; $W[i] = i+1$ pro každé $i$ takové, že $0 \leq i < N$
| 3       | $17$   | $Q \leq 5$; $A[i] = 2$ and $B[i] = 1$ pro každé $i$ takové, že $0 \leq i < N$
| 4       | $11$   | $Q \leq 5$; $N \leq 2000$
| 5       | $20$   | $Q \leq 5$
| 6       | $15$   | $A[i] = 2$ and $B[i] = 1$ pro každé $i$ takové, že $0 \leq i < N$
| 7       | $18$   | Bez dalších omezení.

## Příklad

Uvažme následující zavolání:

```
calculate_costs([15, 12, 2, 10, 21],
                [5, 4, 5, 6, 3],
                [1, 2, 2, 3, 2],
                [5, 9, 1])
```

V tomto příkladě máme $N = 5$ artefaktů a $Q = 3$ dotazů.

V prvním dotazu $D = 5$. Můžeme poslat artefakty $0$ a $3$ v jedné lodi (protože $|15 - 10| \leq 5$)
a zbývající artefakty v lodích po jednom. To dává minimální cenu přepravy artefaktů, která je $1+4+5+3+3 = 16$.

V druhém dotazu $D = 9$. Artefakty $0$ a $1$ pošleme v jedné lodi (protože $|15 - 12| \leq 9$),
stejně tak $2$ a $3$ pošleme v jedné lodi (protože $|2 - 10| \leq 9$).
Zbývající artefakty pošleme v lodích po jednom.
To dává minimální cenu přepravy artefaktů, která je $1+2+2+3+3 = 11$.

V poslední otázce $D = 1$. Je zapotřebí poslat každý artefakt ve vlastní lodi.
To dává minimální cenu přepravy artefaktů, která je  $5+4+5+6+3 = 23$.

Tedy, tato funkce má vrátit $[16, 11, 23]$.


## Ukázkový grader

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

$S$ je délka pole $R$ vráceného `calculate_costs`.
