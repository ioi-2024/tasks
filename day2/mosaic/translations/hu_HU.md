# Mozaik

Salma azt tervezi, hogy agyagmozaikot színez a falra.
A mozaik egy $N \times N$-es rács, $N^2$ darab, kezdetben színezetlen, $1 \times 1$-es négyzet alakú csempéből készül.

A mozaik sorai $0$-tól $N-1$-ig felülről lefelé, az oszlopok $0$-tól $N-1$-ig balról jobbra számozottak.
Az $i$. sorban és a $j$. oszlopban ($0 \leq i < N$ , $0 \leq j < N$) lévő csempét $(i,j)$ jelöli.
Minden csempét fehérre (jelölése $0$) vagy feketére (jelölése $1$) kell színeznie.

A mozaik színezéséhez Salma először kiválaszt két darab $N$ hosszúságú, $0$ és $1$ értékekből áll $X$ és $Y$ sorozatot, amelyben $X[0] = Y[0]$.
A legfelső ($0$.) sor  csempéit az $X$ sorozat szerint színezi úgy, hogy a $(0,j)$ csempe színe $X[j]$ ($0 \leq j < N$) legyen.
A bal szélső ($0$.)  oszlop csempéit az $Y$ sorozat szerint színezi úgy, hogy az $(i,0)$ csempe színe $Y[i]$ ($0 \leq i < N$) legyen.

Ezután  a következő lépéseket ismétli, amíg az összes csempét nem színezi be:
* Megkeres egy olyan *színezetlen* $(i,j)$ csempét, amelynek a felső szomszédja (az $(i-1, j)$ csempe) és bal oldali szomszédja (az $(i, j-1)$ csempe) is *már színezett*.
* Ezután az $(i,j)$ csempét feketére színezi, ha mindkét fent nevezett szomszédja fehér; egyébként fehérre színezi.

Bebizonyítható, hogy a csempék végső színei nem függnek attól, hogy Salma milyen sorrendben színezi őket (a szabályt betartva).
 
Yasmin nagyon kíváncsi a mozaik színeire.
Salmának $Q$ kérdést tesz fel, amelyek $0$-tól $Q-1$-ig számozottak.
A $k$. kérdésben ($0 \leq k < Q$) Yasmin a mozaik egy résztéglalapját a következőképpen határozza meg:
* A $T[k]$ a legfelső sor és a $B[k]$ a legalsó sor ($0 \leq T[k] \leq B[k] < N$),
* A bal szélső oszlop $L[k]$  és a jobb szélső oszlop $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

A kérdésre adandó válasz a fekete csempék száma a résztéglalapban.
Konkrétan Salmának meg kell számolnia azokat az $(i, j)$ csempéket, amire $T[k] \leq i \leq B[k]$ , $L[k] \leq j \leq R[k]$ és az $(i,j)$ csempe színe fekete.

Írj programot, amely választ ad Yasmin kérdéseire.

## Megvalósítás

A következő eljárást kell implementálnod.

```
std::vector&lt;long long&gt; mosaic(
 std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
 std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
 std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$ , $Y$ : a csempék színeit a legfelső sorban, illetve a bal szélső oszlopban leíró, $N$ hosszú sorozatok.
* $T$ , $B$ , $L$ , $R$ : a Yasmin által feltett kérdéseket leíró, $Q$ hosszú sorozatok.
* Az eljárásnak egy ($Q$ hosszú) $C$ sorozatot kell visszaadnia, amiben a $C[k]$ megadja a választ a $k$. kérdésre ($0 \leq k < Q$).
* Ezt az eljárást minden tesztesetben pontosan egyszer hívják meg.

## Korlátok

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ és $Y[i] \in \{0, 1\}$
 minden  $i$-re, ahol $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ és $0 \leq L[k] \leq R[k] < N$
 minden $k$-ra ahol $0 \leq k < Q$

## Részfeladatok

| Részfeladat | Pontszám | További megszorítások |
| :-----: | :----: | ----------------------- |
| 1 | $5$ | $N \leq 2; Q \leq 10$
| 2 | $7$ | $N \leq 200; Q \leq 200$
| 3 | $7$ | $T[k] = B[k] = 0$ (minden $k$-ra, ahol $0 \leq k < Q$ )
| 4 | $10$ | $N \leq 5000$
| 5 | $8$ | $X[i] = Y[i] = 0$ (minden $i$-re, ahol $0 \leq i < N$ )
| 6 | $22$ | $T[k] = B[k]$ és $L[k] = R[k]$ (minden $k$-ra, ahol $0 \leq k < Q$ )
| 7 | $19$ | $T[k] = B[k]$ (minden $k$-ra, ahol $0 \leq k < Q$ )
| 8 | $22$ | Nincsenek további megszorítások.

## Példa

Tekintsük a következő hívást:

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

A példát az alábbi képek illusztrálják.
A bal oldali képen a mozaik látható.
A középső és jobb oldali képen a résztéglalapok láthatók. Yasmin ezekre az első és a második kérdésben kérdezett rá.

![](example.png "550")

A kérdésekre adott válaszok (azaz az egyesek száma az árnyékolt téglalapokban) 7, illetve 3.
Ezért az eljárásnak $[7, 3]$ -t kell visszaadnia.

## Mintaértékelő

Beviteli formátum:

```
N
X[0] X[1] ... X[N-1]
Y[0] Y[1] ... Y[N-1]
Q
T[0] B[0] L[0] R[0]
T[1] B[1] L[1] R[1]
...
T[Q-1] B[Q-1] L[Q-1] R[Q-1]
```

Kimeneti formátum:

```
C[0]
C[1]
...
C[S-1]
```

Itt $S$ a `mosaic` által visszaadott $C$ tömb hossza.