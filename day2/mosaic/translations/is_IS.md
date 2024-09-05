# Mósaík

Salma ætlar sér að lita alla leir mósaík veggina.
Mósaíkin er $N \times N$ grind,
sem samanstendur af $N^2$ upprunalegum ólituðum $1 \times 1$ ferkantslaga reitum.
Raðirnar af mósaíkinu er númeraðar frá $0$ til $N-1$ frá toppi til botns,
og dálkarnir eru númeraðir frá $0$ til $N-1$ frá vinstri til hægri.
Reiturinn í röð $i$ og dálki $j$, þar sem $0 \leq i < N$, $0 \leq j < N$, er táknaður með $(i,j)$.
Hver reitur þarf að vera litaður annaðhvort
með hvítum (táknað með $0$) eða svörtum (táknað með $1$).

Til að lita mósaík þá velur Salma fyrst tvö fylki $X$ og $Y$ af lengd $N$,
þar sem sérhvert stak er annaðhvort gildi $0$ eða $1$ og $X[0] = Y[0]$.
Hún litar reitina í efstu röðinni (röð $0$) út frá fylki $X$,
þar sem liturinn í reit $(0,j)$ er $X[j]$ ($0 \leq j < N$).
Hún litar einnig reitina í dálkinum lengst til vinstri (dálki $0$) út frá fylkinu $Y$,
þar sem liturinn í reit $(i,0)$ er $Y[i]$ ($0 \leq i < N$).

Svo endurtekur hún eftirfarandi skref þangað til allir reitir eru litaðir:
* Hún finnur *ólitaðan* reit $(i,j)$ þar sem
efri nágranni (reitur $(i-1, j)$) og vinstri nágranni (reitur $(i, j-1)$)
eru báðir *nú þegar litaðir*
* Hún litar svo reitinn $(i,j)$ svartan ef báðir nágrannarnir eru hvítir;
annars litar hún reitinn $(i, j)$ hvítan.

Hægt er að sýna fram á að lokalitunin af reitunum er óháð
röð skrefanna sem Salma tekur til þess að lita þá.

Jasmín er mjög forvitin um liti reitanna í mósaíkinu.
Hún spyr því Sölmu $Q$ spurninga, númeraðar frá $0$ til $Q-1$.
Í spurningu $k$, þar sem $0 \leq k < Q$,
skilgreinir Jasmín hlutrétthyrning í mósaíkinu eftir:
* Efstu röðinni $T[k]$ og neðstu röðinni $B[k]$, þar sem $0 \leq T[k] \leq B[k] < N$,
* dálkinum lengst til vinstri $L[k]$ og dálkinum lengst til hægri $R[k]$, þar sem $0 \leq L[k] \leq R[k] < N$.
 
Svarið við spurningunni er fjöldi svarta reita í hlutrétthyrningnum.
Þá sérstaklega skal Salma finna hversu margir reitir $(i, j)$ eru til,
þar sem $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$,
og liturinn af reit $(i,j)$ er svartur.

Skrifaðu forrit sem svarar spurningum Jasmínar.

## Útfærslusmáatriði

Þú skalt útfæra eftirfarandi stefju.

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$: fylki af lengd $N$ sem lýsir litum reitanna í
efstu röðinni.
* $Y$: fylki af lengd $N$ sem lýsir litum reitanna í
dálknum lengst til vinstri.
* $T$, $B$, $L$, $R$: fylki af lengd $Q$ sem lýsa spurningum Jasmínar.
* Stefjan skal skila frá sér fylkinu $C$ af lengd $Q$,
þar sem $C[k]$ er svarið við spurningu $k$ ($0 \leq k < Q$).
* Kallað er á stefjuna nákvæmlega einu sinni fyrir sérhvert prufutilvik.

## Takmarkanir

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ og $Y[i] \in \{0, 1\}$
 fyrir sérhvert $i$ þar sem $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ og $0 \leq L[k] \leq R[k] < N$
 fyrir sérhvert $k$ þar sem $0 \leq k < Q$

## Stigagjöf

| Hópur | Stig  | Frekari takmarkanir |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ fyrir sérhvert $k$ þar sem $0 \leq k < Q$
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ fyrir sérhvert $i$ þar sem $0 \leq i < N$
| 6       | $22$   | $T[k] = B[k]$ og $L[k] = R[k]$ fyrir sérhvert $k$ þar sem $0 \leq k < Q$
| 7       | $19$   | $T[k] = B[k]$ fyrir sérhvert $k$ þar sem $0 \leq k < Q$
| 8       | $22$   | Engar frekari takmarkanir.

## Sýnidæmi

Íhugið eftirfarandi kall.

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Þetta sýnidæmi má sjá á myndinni að neðan.
Myndin til vinstri sýnir litina af reitunum í mósaíkinu.
Myndin fyrir miðju og myndin til hægri sýna hlutrétthyrningana
sem Jasmín spyr um í fyrstu og annari spurningunni.

![](example.png "550")

Svarið við spurningunni
(eða fjöldi ása í skyggðu rétthyrningunum)
eru $7$ og $3$.
Þannig stefjan skal skila frá sér $[7, 3]$.

## Sýnisyfirferðarforrit

Snið inntaks:

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

Snið úttaks:

```
C[0]
C[1]
...
C[S-1]
```

Hérna er $S$ lengd fylkisins $C$ sem `mosaic` skilar.
