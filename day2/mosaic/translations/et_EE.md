# Mosaiik

Salma plaanib seinale maalida savimosaiigi.
Mosaiik on $N \times N$ ruudustik, mis koosneb $N^2$ algselt värvimata $1 \times 1$ plaadist.
Mosaiigi read on nummerdatud ülevalt alla $0$ kuni $N-1$ ja veerud vasakult paremale $0$ kuni $N-1$.
Ruudustikus paiknevat plaati reas $i$ ja veerus $j$ ($0 \leqslant i < N$, $0 \leqslant j < N$) tähistatakse $(i,j)$-ga.
Salma värvib iga plaadi kas valgeks (tähistatud $0$-ga) või mustaks (tähistatud $1$-ga).

Mosaiigi värvimiseks valib Salma esmalt kaks $N$-elemendilist massiivi $X$ ja $Y$, mis koosnevad väärtustest $0$ ja $1$ selliselt, et $X[0] = Y[0]$.
Ta värvib mosaiigi ülemise rea (rida $0$) vastavalt massiivile $X$, nii et plaadi $(0,j)$ värv on $X[j]$ ($0 \leqslant j < N$).
Ta värvib ka vasakpoolseima veeru (veeru $0$) vastavalt massiivile $Y$, nii et plaadi $(i,0)$ värv on $Y[i]$ ($0 \leqslant i < N$).

Seejärel kordab ta järgmisi samme, kuni kõik plaadid on värvitud:
* Ta leiab suvalise **värvimata** plaadi $(i,j)$, mille ülemine naaber (plaat $(i-1, j)$) ja vasak naaber (plaat $(i, j-1)$) on juba **värvitud**.
* Nüüd, kui need naabrid on mõlemad valged, värvib ta plaadi $(i,j)$ mustaks, vastasel juhul värvib ta plaadi $(i,j)$ valgeks.

On võimalik näidata, et plaatide lõplikud värvid ei sõltu järjekorrast, milles Salma neid värvib.

Yasmin on mosaiigi plaatide värvide suhtes väga uudishimulik.
Ta esitab Salmale $Q$ küsimust, mis on nummerdatud $0$ kuni $Q-1$.
Küsimuses $k$ ($0 \leqslant k < Q$) määrab Yasmin mosaiigi alamristküliku järgmiselt:
* Kõrgeim rida $T[k]$ ja madalaim rida $B[k]$ ($0 \leqslant T[k] \leqslant B[k] < N$),
* Vasakpoolseim veerg $L[k]$ ja parempoolseim veerg $R[k]$ ($0 \leqslant L[k] \leqslant R[k] < N$).

Küsimuse vastus on mustade plaatide arv selles alamristkülikus.
Täpsemalt peab Salma leidma, kui palju on plaate $(i,j)$,
 kus $T[k] \leqslant i \leqslant B[k]$, $L[k] \leqslant j \leqslant R[k]$ ja plaadi $(i,j)$ värv on must.

Kirjuta programm, mis vastab Yasmini küsimustele.

## Realisatsioon

Sa pead kirjutama järgmise funktsiooni.

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$ on $N$-elemendilised massiivid, mis kirjeldavad plaatide värve
vastavalt mosaiigi ülemises reas ja vasakpoolses veerus.
* $T$, $B$, $L$, $R$ on $Q$-elemendilised massiivid, mis kirjeldavad Yasmini esitatud küsimusi.
* Funktsioon peab tagastama $Q$-elemendilise massiivi $C$,
 nii et $C[k]$ annab vastuse küsimusele $k$ ($0 \leqslant k < Q$).
* Seda funktsiooni kutsutakse igas testis välja täpselt üks kord.

## Piirangud

* $1 \leqslant N \leqslant 200\,000$,
* $1 \leqslant Q \leqslant 200\,000$,
* $X[i] \in \{0, 1\}$ ja $Y[i] \in \{0, 1\}$ iga $0 \leqslant i < N$ korral,
* $X[0] = Y[0]$,
* $0 \leqslant T[k] \leqslant B[k] < N$ ja $0 \leqslant L[k] \leqslant R[k] < N$ iga $0 \leqslant k < Q$ korral.

## Alamülesanded

| Alamülesanne | Väärtus | Lisapiirangud |
| :---------: | :-----: | --------------------- |
| 1           | $5$     | $N \leqslant 2$; $Q \leqslant 10$. |
| 2           | $7$     | $N \leqslant 200$; $Q \leqslant 200$. |
| 3           | $7$     | $T[k] = B[k] = 0$ iga $0 \leqslant k < Q$ korral. |
| 4           | $10$    | $N \leqslant 5000$.         |
| 5           | $8$     | $X[i] = Y[i] = 0$ iga $0 \leqslant i < N$ korral. |
| 6           | $22$    | $T[k] = B[k]$ ja $L[k] = R[k]$ iga $0 \leqslant k < Q$ korral. |
| 7           | $19$    | $T[k] = B[k]$ iga $0 \leqslant k < Q$ korral. |
| 8           | $22$    | Lisapiirangud puuduvad. |

## Näide

Vaatleme järgmist väljakutset.

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Allolevad pildid illustreerivad seda näidet.
Vasakul pildil on kujutatud mosaiigi plaatide värvid.
Keskmisel ja paremal pildil on kujutatud alamristkülikud, mille kohta Yasmin küsis vastavalt esimeses ja teises küsimuses.

![](example.png "550")

Küsimuste vastused (ehk ühtede arvud varjutatud alamristkülikutes) on vastavalt 7 ja 3.
Seega peab funktsioon tagastama $[7, 3]$.

## Näidishindaja

Sisendi vorming:

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

Väljundi vorming:

```
C[0]
C[1]
...
C[S-1]
```

Siin on $S$ massiivi $C$ pikkus, mille `mosaic` tagastab.
