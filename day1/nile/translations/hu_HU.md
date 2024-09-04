# Nílus

A Níluson $N$ darab műtárgyat akarsz elszállítani. A műtárgyak $0$ és $N-1$ között számozottak.
Az $i$. ( $0 \leq i < N$ ) műtárgy súlya $W[i]$.

A műtárgyak szállításához speciális csónakokat tudsz használni.
Minden csónakban **legfeljebb kettő** darab műtárgyat szállíthatsz.

* Ha úgy döntesz, hogy egyetlen műtárgyat helyezel egyedül egy csónakba, akkor a műtárgy súlya tetszőleges lehet.
* Ha két műtárgyat szeretnél ugyanabba a csónakba tenni, akkor ügyelned kell arra, hogy a csónak egyensúlyban maradjon.
Pontosabban csak akkor helyezheted el a $p$. és a $q$. ( $0 \leq p < q < N$ ) műtárgyat ugyanabba a csónakba, ha a súlyuk közötti abszolút különbség legfeljebb $D$, azaz $|W[p] - W[q]| \leq D$.

A műtárgyak szállításánál szállítási költséget kell fizetned, ami az ugyanabban a csónakban szállított műtárgyak számától függ.

Az $i$. ( $0 \leq i < N$ ) műtárgy szállításának költsége:

* $A[i]$, ha a műtárgy egyedül van a csónakban, vagy
* $B[i]$, ha más műtárggyal együtt helyezed egy csónakba.

Ne feledd, hogy az utóbbi esetben a csónakban levő mindkét műtárgyért fizetned kell.
Pontosabban, ha úgy döntesz, hogy elküldöd a $p$. és a $q$. ( $0 \leq p < q < N$ ) műtárgyakat ugyanabban a csónakban, akkor összesen $B[p] + B[q]$ költséget kell fizetned.

Egy műtárgy önmagában való elküldése mindig drágább, mintha másikkal együtt egy csónakba teszed,
tehát $B[i] < A[i]$ minden $i$-re ($0 \leq i < N$).

Sajnos a folyó nagyon kiszámíthatatlan és a $D$ értéke gyakran változik.
A feladatod, hogy válaszolj $Q$ kérdésre, amelyek számozása $0$ és $Q-1$ között van.
A kérdéseket egy $E$ nevű, $Q$ hosszúságú sorozat írja le.
A válasz a $j$. ( $0 \leq j < Q$ ) kérdésre az összes ($N$ darab) műtárgy szállításának minimális összköltsége,
 amikor a $D$ értéke egyenlő a $E[j]$ értékkel.

## Megvalósítás

A következő függvényt kell implementálnod:

```
std::vector&lt;long long&gt; calculate_costs(
 std::vector&lt;int&gt; W, std::vector&lt;int&gt; A,
 std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```

* $W$, $A$, $B$: $N$ hosszú, egész számokat tartalmazó sorozatok, amik a műtárgyak súlyait és szállítási költségeit tartalmazzák.
* $E$ : $Q$ hosszú, egész számokat tartalmazó sorozat, amely leírja a $D$ értékeit az egyes kérdésekben.
* A függvénynek egy $Q$ hosszú, egész számokból álló $R$ sorozatot kell visszaadnia, amely tartalmazza a műtárgyak szállításának minimális összköltségét, azaz $R[j]$ megadja azt a minimális összköltséget, amikor a $D$ értéke $E[j]$ (minden $j$-re, ahol  $0 \leq j < Q$ ).
* Ezt a függvényt minden tesztesetre pontosan egyszer hívják meg.

## Korlátok

* $1 \leq N \leq 100\,000$
* $1 \leq Q \leq 100\,000$
* $1 \leq W[i] \leq 10^{9}$ minden $i$-re, ahol $0 \leq i < N$
* $1 \leq B[i] < A[i] \leq 10^{9}$ minden $i$-re, ahol $0 \leq i < N$
* $1 \leq E[j] \leq 10^{9}$ minden $j$-re, ahol  $0 \leq j < Q$

## Részfeladatok

| Részfeladat | Pontszám | További megszorítások |
| :-----: | :----: | ----------------------- |
| 1 | $6$ | $Q \leq 5$ ; $N \leq 2000$ ; $W[i] = 1$ minden $i$-re, ahol $0 \leq i < N$
| 2 | $13$ | $Q \leq 5$ ; $W[i] = i+1$ minden  $i$-re, ahol $0 \leq i < N$
| 3 | $17$ | $Q \leq 5$ ; $A[i] = 2$ és $B[i] = 1$ minden  $i$-re, ahol $0 \leq i < N$
| 4 | $11$ | $Q \leq 5$ ; $N \leq 2000$
| 5 | $20$ | $Q \leq 5$
| 6 | $15$ | $A[i] = 2$ és $B[i] = 1$ minden $i$-re, ahol $0 \leq i < N$
| 7 | $18$ | Nincsenek további megszorítások.

## Példa

Tekintsük a következő függvényhívást:

```
calculate_costs([15, 12, 2, 10, 21],
 [5, 4, 5, 6, 3],
 [1, 2, 2, 3, 2],
 [5, 9, 1])
```

Ebben a példában $N = 5$ műtárgy és $Q = 3$ kérdés van.

Az első kérdésben $D = 5$.
A $0$. és a $3$. műtárgyakat egy csónakba teheted (mivel $|15 - 10| \leq 5$ ), a többit pedig külön-külön csónakba.
Ez adja az összes műtárgy szállításának minimális költségét, ami $1+4+5+3+3=16$ .

A második kérdésben $D = 9$ .
A $0$. és az $1$. műtárgyat egy csónakba (mivel $|15 - 12| \leq 9$ ), és a $2$. és $3$. műtárgyat egy másik egy csónakba teheted (mivel $|2 - 10| \leq 9$ ).
A fennmaradó egyetlen műtárgyat külön csónakba tudod csak tenni.
Ez adja az összes műtárgy szállításának minimális költségét, ami $1+2+2+3+3 = 11$ .

Az utolsó kérdésben $D = 1$. Minden műtárgyat a saját csónakjában kell elküldened, egyesével.
Ez adja az összes műtárgy szállításának minimális költségét, ami $5+4+5+6+3 = 23$ .

Így az eljárásnak $[16, 11, 23]$ -t kell visszaadnia.


## Mintaértékelő

Beviteli formátum:

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

Kimeneti formátum:

```
R[0]
R[1]
...
R[S-1]
```

Itt $S$ a `calculate_costs` által visszaadott $R$ sorozat hossza.
