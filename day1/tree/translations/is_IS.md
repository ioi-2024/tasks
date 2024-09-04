# Tré

Ímyndaðu þér **tré** sem samanstendur af $N$ **hnútum**,
númeraðir frá $0$ til $N-1$.
Hnútur $0$ er kallaður **rótin**.
Hver hnútur, nema rótin, hefur eitt **foreldri**.
Fyrir hvert $i$, þannig að $1 \leq i < N$,
þá er foreldri hnúts $i$, hnútur $P[i]$, þar sem $P[i] < i$.
Við segjum einnig að $P[0] = -1$.

Fyrir hnút $i$, þar sem $0 \leq i < N$,
þá er **hluttré** hnúts $i$ mengið af eftirfarandi hnútum:
* $i$, og
* hnútur sem sem á foreldri $i$, og
* hnútur sem á foreldri sem á foreldri $i$, og
* hnútur sem á foreldri sem á foreldri sem á foreldri $i$,
* og svo framvegis.

Myndin að neðan sýnir dæmi um tré sem samanstendur af $N = 6$ hnútum.
Hver ör tengir hnút við foreldri sitt,
nema fyrir rótina sem á ekkert foreldri.
Hluttré hnúts $2$ inniheldur hnúta $2, 3, 4$ og $5$.
Hluttré af hnúts $0$ inniheldur alla $6$ hnúta trésins
og hluttré hnúts $4$ inniheldur einungis hnút $4$.

![](subtrees.png "150")

Hver hnútur hefur **vægi**.
Við táknum vægi hnúts $i$ $0 \leq i < N$ með $W[i]$.

Verkefnið þitt er að skrifa forrit sem skal svara $Q$ fyrirspurnum,
þar sem hver fyrirspurn samanstendur af tvem heiltölum $(L, R)$.
Svarið við fyrirspurninni skal vera reiknað á eftirfarandi máta.

Íhugaðu að skrá heiltölu,
sem við köllum **stuðul**, fyrir hvern hnút í trénu.
Skráningu stuðla er hægt að lýsa sem runu $C[0], \ldots, C[N-1]$,
þar sem $C[i]$ $0 \leq i < N$ er stuðullinn á hnút $i$.
Við köllum þessa runu **stuðlarunu**.
Athugið að stök stuðlarununnar geta verið neikvæð, $0$, eða jákvæð.

Fyrir fyrirspurn $(L, R)$,
þá er stuðlaruna sögð vera **gild**
ef, fyrir hvern hnút $i$ $0 \leq i < N$,
gildir eftirfarandi skilyrði:
summa stuðlana af hverjum hnút í hluttré $i$
er ekki minna en $L$ og ekki stærra en $R$.

Fyrir gefna stuðlarunu $C[0], \ldots, C[N-1]$,
þá er **kostnaður** hnúts $i$, $|C[i]| \cdot W[i]$,
þar sem $|C[i]|$ táknar algildi á $C[i]$.
Þá er **heildarkostnaður** summa kostnaðar allra hnúta.
Verkefnið þitt er að reikna fyrir hverja fyrirspurn,
**minnsta heildarkostnað** sem hægt er að fá með því að velja
einhverja gilda stuðlarunu.

## Útfærslusmáatriði

Þú skalt útfæra eftirfarandi tvær stefjur:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$: heiltölufylki sem eru með lengd $N$ og
   sem lýsa foreldra og vægi hvers hnúts.
* Þegar forrit þitt er prófað gegn yfirferðarforriti er kallað í þessa stefju einu sinni í upphafi keyrslunnar fyrir hvert prufutilvik.

```
long long query(int L, int R)
```
* $L$, $R$: heiltölur sem lýsa fyrirspurn.
* Það er kallað $Q$ sinnum á þessa stefju, eftir að kallað hefur verið á `init` í hverju prufutilviki.
* Þessi stefja skal skila svarinu fyrir hverja fyrirspurn.


## Takmarkanir

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ fyrir sérhvert $i$ þar sem $1 \leq i < N$
* $0 \leq W[i] \leq 1\,000\,000$ fyrir sérhvert $i$ þar sem $0 \leq i < N$
* $1 \leq L \leq R \leq 1\,000\,000$ í sérhverri fyrirspurn

## Stigagjöf

| Hópur | Stig  | Frekari takmarkanir |
| :-----: | :----: | ---------------------- |
|   1     |  $10$  | $Q \leq 10$; $W[P[i]] \leq W[i]$ fyrir sérhvert $i$ þar sem $1 \leq i < N$
|   2     |  $13$  | $Q \leq 10$; $N \leq 2\,000$
|   3     |  $18$  | $Q \leq 10$; $N \leq 60\,000$
|   4     |  $7$   | $W[i] = 1$ fyrir sérhvert $i$ þar sem $0 \leq i < N$
|   5     |  $11$  | $W[i] \leq 1$ fyrir sérhvert $i$ þar sem $0 \leq i < N$
|   6     |  $22$  | $L = 1$
|   7     |  $19$  | Engar frekari takmarkanir.



## Sýnidæmi

Íhugið eftirfarandi köll:

```
init([-1, 0, 0], [1, 1, 1])
```
Tréð samanstendur af $3$ hnútum, rótinni og $2$ börnum.
Allir hnútar hafa vægi $1$.

```
query(1, 1)
```

Í þessari fyrirspurn er $L = R = 1$,
sem þýðir að summa alla stuðla í hverju hluttré þarf að vera jöfn $1$.
Íhugið stuðlarununa $[-1, 1, 1]$.
Tréð og stuðlar hvers hnúts (í skyggðum ferningum) eru sýnd hér að neðan.

![](ex1.png "150")

Fyrir hvern hnút $i$, þar sem $0 \leq i < 3$, þá er summa stuðlana á hverjum hnút í hluttré $i$ jöfn $1$ sem gerir þessi stuðlarunu gilda.
Heildarkostnaður er reiknaður á eftifarandi máta:

| Hnútur | Vægi | Stuðull | Kostnaður                      |
| :----: | :----: | :---------: | :-----------------------: |
|   0    |   1    |     -1      | $\mid -1 \mid \cdot 1 = 1$
|   1    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$
|   2    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$

Því er heildarkostnaðurinn $3$.
Þetta er eina gilda stuðlarunan og skal stefjan því skila $3$.

```
query(1, 2)
```
Minnsti heildarkostnaður á þessari fyrirspurn er $2$,
og er sá kostnaðurinn fenginn með stuðlarununni $[0, 1, 1]$.

## Sýnisyfirferðarforrit

Snið inntaks:

```
N
P[1]  P[2] ...  P[N-1]
W[0]  W[1] ...  W[N-2] W[N-1]
Q
L[0]  R[0]
L[1]  R[1]
...
L[Q-1]  R[Q-1]
```

Þar sem $L[j]$ og $R[j]$ fyrir $0 \leq j < Q$
eru inntaksgildi fyrir `query` númer $j$.
Takið eftir að seinni línan í inntakinu inniheldur **einungis $N-1$ heiltölur**,
þar sem sýnisyfirferðarforritið les ekki gildið á $P[0]$.

Snið úttaks:
```
A[0]
A[1]
...
A[Q-1]
```

Þar sem $A[j]$
 fyrir $0 \leq j < Q$
 er skilagildi `query` númer $j$.
