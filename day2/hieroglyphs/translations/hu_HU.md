# Hieroglifák

Egy kutatócsoport a hieroglifák sorozatai közötti hasonlóságokat tanulmányozza.
Minden hieroglifát egy-egy nemnegatív egész számmal ábrázolnak.
Tanulmányuk elvégzéséhez a sorozatokról a következő fogalmakat használják.

Egy $A$ rögzített sorozat esetén az $S$ sorozatot az $A$ **részsorozatának** nevezzük akkor és csak akkor, ha az $S$ az $A$-ból előállítható néhány elem eltávolításával (esetleg egyet sem eltávolítva).

Az alábbi táblázat néhány példát mutat az $A = [3, 2, 1, 2]$ sorozat részsorozataira.

| Részsorozat | $A$-ból való előállítása |
|----------------|--------------------------------- -|
| [3, 2, 1, 2] | Egyetlen elem sem kerül eltávolításra.
| [2, 1, 2] | [<s>3</s>, 2, 1, 2]
| [3, 2, 2] | [3, 2, <s>1</s>, 2]
| [3, 2] | [3, <s>2</s>, <s>1</s>, 2] vagy [3, 2, <s>1</s>, <s>2</s>]
| [3] | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ] | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Másrészt a $[3, 3]$ vagy az $[1, 3]$ nem részsorozatai az $A$-nak.

Tekintsünk két hieroglifa-sorozatot: $A$-t és $B$-t.
Az $S$ sorozatot az $A$ és a $B$ **közös részsorozatának** nevezzük akkor és csak akkor, ha $S$ mind az $A$, mind a $B$ részsorozata.
Ezenkívül azt mondjuk, hogy az $U$ sorozat akkor és csak akkor az $A$ és a $B$ **univerzális közös részsorozata**, ha az alábbi két feltétel teljesül:
* $U$ az $A$ és a $B$ közös részsorozata.
* az $A$ és a $B$ minden közös részsorozata egyben $U$ részsorozata is.

Bebizonyítható, hogy bármely két, $A$ és $B$ sorozat esetén legfeljebb egy univerzális közös részsorozat létezik.

A kutatók két hieroglifa-sorozatot találtak: $A$ és $B$.
Az $A$ sorozat $N$ hieroglifából áll, a $B$ sorozat pedig $M$ hieroglifából áll.
Segíts a kutatóknak megállapítani az $A$ és a $B$ sorozatok univerzális közös részsorozatát,
 vagy állapítsd meg, hogy ilyen sorozat nem létezik.

## Megvalósítás

A következő eljárást kell megvalósítanod.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: az első sorozat, amely $N$ elemből áll.
* $B$: a második sorozat, amely $M$ elemből áll.
* Ha létezik az $A$ és a $B$ univerzális közös részsorozata, az eljárásnak ezt a sorozatot kell visszaadnia.
  Ellenkező esetben az eljárásnak a $[-1]$-et kell visszaadnia ($1$ hosszúságú sorozatot, melynek egyetlen eleme a $-1$).
* Ezt az eljárást minden tesztesetre pontosan egyszer hívják meg.

## Korlátok

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ minden $i$-re, ahol $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ minden $j$-re, ahol $0 \leq j < M$

## Részfeladatok

| Részfeladat | Pontszám | További megszorítások |
| :-----: | :----: | ----------------------- |
| 1 | $3$ | $N = M$ ; az $A$ és a $B$  $N$ *különböző* egész számból áll $0$ és $N-1$ között (beleértve a határokat)
| 2 | $15$ | Bármely $k$ egész szám esetén (az $A$ $k$-val egyenlő elemeinek száma) **plusz** ( a $B$ $k$-val egyenlő elemeinek száma) legfeljebb $3$.
| 3 | $10$ | $A[i] \leq 1$ minden $i$-re, ahol $0 \leq i < N$ ; $B[j] \leq 1$ minden $j$-re, ahol $0 \leq j < M$
| 4 | $16$ | Létezik $A$ és $B$ univerzális közös részsorozata
| 5 | $14$ | $N \leq 3000$ ; $M \leq 3000$
| 6 | $42$ | Nincsenek további megszorítások

## Példák

### 1. példa

Tekintsük a következő hívást:

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Itt az a $A$ és a $B$ közös részsorozatai a következők:
 $[\ ]$ , $[0]$ , $[1]$ , $[2]$ $[0, 0]$ , $[0, 1]$ , $[0, 1]$ , $[0, 2]$ , $[1, 0]$ , $[1, 2]$ $[0, 0, 2]$ , $[0, 1, 0]$ , $[0, 1, 2]$ , $[1, 0, 2]$ és $[0, 1, 0, 2]$ .

Mivel $[0, 1, 0, 2]$ az $A$ és a $B$ közös részsorozata, és
 $A$ és $B$ összes közös részsorozata a $[0, 1, 0, 2]$ sorozat részsorozata is,
így az eljárásnak a következőt kell visszaadnia: $[0, 1, 0, 2]$.

### 2. példa

Tekintsük a következő hívást:

```
ucs([0, 0, 2], [1, 1])
```

Itt az $A$ és a $B$ egyetlen közös részsorozata az $[\ ]$ üres sorozat.
Ebből következik, hogy az eljárásnak egy üres $[\ ]$ sorozatot kell visszaadnia.

### 3. példa

Tekintsük a következő hívást:

```
ucs([0, 1, 0], [1, 0, 1])
```

Itt az $A$ és a $B$ közös részsorozatai
 $[\ ], [0], [1], [0, 1]$ és $[1, 0]$.
Kimutatható, hogy nem létezik univerzális közös részsorozat.
Ezért az eljárásnak $[-1]$ értéket kell visszaadnia.

## Mintaértékelő

Beviteli formátum:

```
N M
A[0] A[1] ... A[N-1]
B[0] B[1] ... B[M-1]
```

Kimeneti formátum:

```
T
R[0] R[1] ... R[T-1]
```

Itt $R$ az `ucs` által visszaadott sorozat, $T$ pedig a hossza.
