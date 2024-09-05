# Hieroglüüfid

Teadlaste meeskond uurib hieroglüüfide jadasid ja nende sarnasusi. Nad esitavad iga hieroglüüfi mittenegatiivse täisarvuna. Uurimistöös kasutavad nad järgmisi jadade kohta käivaid mõisteid.

Jada $S$ nimetatakse jada $A$ **osajadaks** parajasti siis, kui $S$ on võimalik saada jadast $A$ elementide eemaldamise teel (võimalik, et midagi ei pea eemaldama).

Allolevas tabelis on näiteid jada $A = [3, 2, 1, 2]$ osajadadest.

| Osajada       | Kuidas see saadakse jadast $A$  |
|---------------|---------------------------------|
| [3, 2, 1, 2]  | Ühtegi elementi ei eemaldata.   |
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]             |
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]             |
| [3, 2]        | [3, <s>2</s>, <s>1</s>, 2] või [3, 2, <s>1</s>, <s>2</s>] |
| [3]           | [3, <s>2</s>, <s>1</s>, <s>2</s>]|
| [ ]           | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>] |

Teisest küljest jadad $[3, 3]$ või $[1, 3]$ ei ole jada $A$ osajadad.

Vaatleme kaht hieroglüüfide jada $A$ ja $B$. Jada $S$ nimetatakse jadade $A$ ja $B$ **ühiseks osajadaks** parajasti siis, kui $S$ on nii jada $A$ kui ka jada $B$ osajada. Lisaks nimetatakse jada $U$ jadade $A$ ja $B$ **universaalseks ühiseks osajadaks** parajasti siis, kui on täidetud järgmised kaks tingimust:
* $U$ on jadade $A$ ja $B$ ühine osajada.
* Iga jadade $A$ ja $B$ ühine osajada on ka jada $U$ osajada.

Saab tõestada, et igal kahel jadal $A$ ja $B$ on ülimalt üks universaalne ühine osajada.

Teadlased on leidnud kaks hieroglüüfide jada $A$ ja $B$. Jada $A$ koosneb $N$ hieroglüüfist ja jada $B$ koosneb $M$ hieroglüüfist. Aita teadlastel leida jadade $A$ ja $B$ universaalne ühine osajada või teha kindlaks, et sellist jada ei eksisteeri.

## Realisatsioon

Pead kirjutama järgmise funktsiooni.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$ on $N$-elemendiline massiiv, mis kirjeldab esimest jada.
* $B$ on $M$-elemendiline massiiv, mis kirjeldab teist jada.
* Kui eksisteerib jadade $A$ ja $B$ universaalne ühine osajada, peab funktsioon tagastama massiivi, mis sisaldab seda jada.
  Vastasel juhul peab funktsioon tagastama $[-1]$ ($1$-elemendilise massiivi, mille ainus element on $-1$).
* Seda funktsiooni kutsutakse igas testis välja täpselt üks kord.

## Piirangud

* $1 \leqslant N \leqslant 100\,000$,
* $1 \leqslant M \leqslant 100\,000$,
* $0 \leqslant A[i] \leqslant 200\,000$ iga $0 \leqslant i < N$ korral,
* $0 \leqslant B[j] \leqslant 200\,000$ iga $0 \leqslant j < M$ korral.

## Alamülesanded

| Alamülesanne | Väärtus | Lisapiirangud |
|:-----------:|:-------:|----------------------|
| 1           | $3$     | $N = M$; $A$ ja $B$ koosnevad mõlemad $N$ **erinevast** täisarvust vahemikus $0$ kuni $N-1$ (kaasa arvatud). |
| 2           | $15$    | Iga täisarvu $k$ korral on (jada $A$ elementide arv, mis on võrdsed $k$-ga) pluss (jada $B$ elementide arv, mis on võrdsed $k$-ga) maksimaalselt $3$. |
| 3           | $10$    | $A[i] \leqslant 1$ iga $0 \leqslant i < N$ korral; $B[j] \leqslant 1$ iga $0 \leqslant j < M$ korral. |
| 4           | $16$    | Jadadel $A$ ja $B$ leidub universaalne ühine osajada. |
| 5           | $14$    | $N \leqslant 3000$; $M \leqslant 3000$. |
| 6           | $42$    | Lisapiirangud puuduvad. |

## Näited

### Näide 1

Vaatleme järgmist väljakutset.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Siin on jadade $A$ ja $B$ ühised osajadad järgmised:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ ja $[0, 1, 0, 2]$.

Kuna $[0, 1, 0, 2]$ on jadade $A$ ja $B$ ühine osajada ning kõik jadade $A$ ja $B$ ühised osajadad on jada $[0, 1, 0, 2]$ osajadad, peab funktsioon tagastama $[0, 1, 0, 2]$.

### Näide 2

Vaatleme järgmist väljakutset.

```
ucs([0, 0, 2], [1, 1])
```

Siin on jadade $A$ ja $B$ ainus ühine osajada tühi jada $[\ ]$.
Sellest tulenevalt peab funktsioon tagastama tühja massiivi $[\ ]$.

### Näide 3

Vaatleme järgmist väljakutset.

```
ucs([0, 1, 0], [1, 0, 1])
```

Siin on jadade $A$ ja $B$ ühised osajadad
 $[\ ], [0], [1], [0, 1]$ ja $[1, 0]$.
Saab näidata, et universaalset ühist osajada ei eksisteeri.
Seetõttu peab funktsioon tagastama $[-1]$.

## Näidishindaja

Sisendi vorming:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Väljundi vorming:

```
T
R[0]  R[1]  ...  R[T-1]
```

Siin on $R$ massiiv, mille `ucs` tagastab, ja $T$ on selle pikkus.
