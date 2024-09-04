# Fa 

Tekintsünk egy **fát**, amely $N$ **csúcsból** áll,
 $0$-tól $N-1$-ig számozva.
A $0$ csúcsot **gyökérnek** nevezzük.
A gyökér kivételével minden csúcsnak egyetlen **szülője** van.
Minden $i$-re ($1 \leq i < N$) jelölje az
 $i$ csúcs szülőjét $P[i]$, ahol $P[i] < i$ teljesül.
Az is teljesül, hogy $P[0] = -1$ .

Bármely $i$ ($1 \leq i < N$) csúcs **részfája** a következő csúcsok halmaza:
 * $i$,
 * minden olyan csúcs, amelynek szülője $i$,
 * minden olyan csúcs, amely szülőjének a szülője $i$,
 * minden olyan csúcs, amely szülőjének szülöjének  a szülője $i$,
 * és így tovább.

Az alábbi ábra egy példa fát mutat, amely $N = 6$ csúcsból áll.
Minden nyíl egy csúcsot köt össze a szülőjével,
 kivéve a gyökeret, amelynek nincs szülője.
A $2.$ csúcs részfája a $2., 3., 4.$ és $5.$ csúcsokat tartalmazza.
A $0.$ csúcs részfája tartalmazza a fa mind a $6$ csúcsát
 és a $4.$ csúcs részfája csak a $4.$ csúcsot tartalmazza.

![](subtrees.png "150")

Minden csúcshoz hozzá van rendelve egy nemnegatív **súly**.
Az $i$ ( $0 \leq i < N$ ) csúcs súlyát $W[i]$-vel jelöljük.

Írj programot, amely megválaszol $Q$ lekérdezést.
Minden lekérdezést egy $(L, R)$ egész számpár határoz meg.
A lekérdezésre adott választ a következőképpen kell kiszámítani.

A fa minden csúcsához rendelhetünk egy egész számot, amelyet 
 **együtthatónak** nevezünk.
Egy ilyen hozzárendelést a $C[0], \ldots, C[N-1]$ sorozat írja le,
 ahol $C[i]$ ( $0 \leq i < N$ ) az $i$ csúcshoz rendelt együttható.
Nevezzük ezt a sorozatot **együttható sorozatnak**.
Vegyük figyelembe, hogy az együttható sorozat minden eleme lehet negatív, $0$ vagy pozitív.

Egy $(L, R)$ lekérdezéshez
 egy együttható sorozatot **érvényes**-nek nevezünk,
 ha minden $i$ csúcsra ( $0 \leq i < N$ ),
 a következő feltétel teljesül:
 az $i$ csúcs részfájában lévő csúcsok együtthatóinak összege
 nem kisebb, mint $L$ és nem nagyobb, mint $R$ .

Egy adott $C[0], \ldots, C[N-1]$ együttható sorozat esetén
 egy $i$ csúcs **költsége** $|C[i]| \cdot W[i]$ ,
 ahol $|C[i]|$ a $C[i]$ abszolút értékét jelöli.
Végül a **teljes költség** az összes csúcs költségének összege.

Az a feladatod, hogy minden egyes lekérdezéshez számítsd ki
 azt a **minimális összköltség**et, amely valamilyen érvényes együtthatósorozattal elérhető.

## Megvalósítás

A következő két eljárást kell elkészítened:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$ , $W$ : $N$ elemű sorozatok, $P$ a szülőket, $W$ a súlyokat adja meg.

* Az értékelő ezt az eljárást pontosan egyszer hívja meg
   minden tesztesetben, az értékelő és a programod közötti interakció elején.

```
long long query(int L, int R)
```
* $L$ , $R$ : a lekérdezést leíró egész számok.
* Ezt az eljárást minden tesztesetben $Q$-szor hívják meg, az `init` meghívása után.
* Ennek az eljárásnak vissza kell adnia a választ az adott lekérdezésre.


## Korlátok

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ minden $i$-re, ahol $1 \leq i < N$
* $0 \leq W[i] \leq 1\,000\,000$ minden $i$-re, ahol $0 \leq i < N$
* $1 \leq L \leq R \leq 1\,000\,000$ minden lekérdezésben

## Részfeladatok

| Részfeladat | Pontszám | További megkötések |
| :-----: | :----: | ----------------------- |
| 1 | $10$ | $Q \leq 10$ ; $W[P[i]] \leq W[i]$ minden $i$-re, ahol $1 \leq i < N$
| 2 | $13$ | $Q \leq 10$ ; $N \leq 2\,000$
| 3 | $18$ | $Q \leq 10$ ; $N \leq 60\,000$
| 4 | $7$ | $W[i] = 1$ minden $i$-re, ahol $0 \leq i < N$
| 5 | $11$ | $W[i] \leq 1$ minden $i$-re, ahol $0 \leq i < N$
| 6 | $22$ | $L = 1$
| 7 | $19$ | Nincsenek további megkötések.



## Példák

Tekintsük a következő hívásokat:

```
init([-1, 0, 0], [1, 1, 1])
```
A fa $3$ csúcsból, a gyökérből és annak $2$ gyermekéből áll.
Minden csúcs súlya $1$ .

```
query(1, 1)
```

Ebben a lekérdezésben $L = R = 1$ ,
 ami azt jelenti, hogy az együtthatók összegének minden részfában egyenlőnek kell lennie $1$-gyel.
Tekintsük a $[-1, 1, 1]$ együttható sorozatot.
A fa és a megfelelő együtthatók (az árnyékolt téglalapokban) az alábbi ábrán láthatók.

![](ex1.png "150")

Minden $i$ ( $0 \leq i < 3$ ) csúcsra a csúcsok együtthatóinak összege $i$ részfájában egyenlő $1$-gyel. 
Ezért ez az együttható sorozat érvényes.
A teljes költséget a következőképpen számítják ki:


| Csúcs | Súly | Együttható | Költség |
| :----: | :----: | :---------: | :-----------------------: |
| 0 | 1 | -1 | $\mid -1 \mid \cdot 1 = 1$
| 1 | 1 | 1 | $\mid 1 \mid \cdot 1 = 1$
| 2 | 1 | 1 | $\mid 1 \mid \cdot 1 = 1$

Ezért a teljes költség $3$.
Ez az egyetlen érvényes együttható sorozat,
 ezért ennek a hívásnak hármat kell visszaadnia.

```
query(1, 2)
```
A lekérdezés minimális összköltsége $2$,
 és akkor érhető el, ha az együttható sorozat $[0, 1, 1]$.

## Mintaértékelő

Beviteli formátum:

```
N
P[1] P[2] ... P[N-1]
W[0] W[1] ... W[N-2] W[N-1]
Q
L[0] R[0]
L[1] R[1]
...
L[Q-1] R[Q-1]
```

ahol $L[j]$ és $R[j]$
 ( $0 \leq j < Q$ esetén)
 a bemeneti paraméterek a $j$-edik `query` hívásban.
Vedd figyelembe, hogy a bemenet második sora **csak $N-1$ egész számot tartalmaz**,
 mivel a minta értékelő nem olvassa be a $P[0]$ értékét.

Kimeneti formátum:
```
A[0]
A[1]
...
A[Q-1]
```

ahol $A[j]$
 ( $0 \leq j < Q$ esetén)
 a $j$ -edik `query` hívás által visszaadott érték.