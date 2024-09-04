# Puu

Vaatleme **puud**, mille $N$ **tippu** on
 nummerdatud $0 \ldots N-1$.
Tipp $0$ on puu **juur**.
Igal tipul, mis pole juur, on täpselt üks **eellane**.
Iga $1 \leqslant i < N$ korral on tipu $i$ eellane tipp $P[i]$,
 kusjuures $P[i] < i$.
Lisaks ütleme, et $P[0] = -1$.

Iga tipu $i$ ($0 \leqslant i < N$),
 korral koosneb tipu $i$ **alampuu** järgmistest tippudest:
 * tipp $i$ ise,
 * kõik tipud, mille eellane on $i$,
 * kõik tipud, mille eellase eellane on $i$,
 * kõik tipud, mille eellase eellase eellane on $i$,
 * jne.

Allolev joonis kujutab $N = 6$ tipuga puud.
Iga nool ühendab üht tippu selle eellasega
 (välja arvatud juurtipp, millel pole eellast).
Tipu $2$ alampuu koosneb tippudest $2$, $3$, $4$ ja $5$.
Tipu $0$ alampuu koosneb kõigist $6$ tipust
 ja tipu $4$ alampuu ainult tipust $4$.

![](subtrees.png "150")

Puu igal tipul on mittenegatiivne täisarvuline **kaal**.
Tähistame tipu $i$ ($0 \leqslant i < N$) kaalu $W[i]$.

Sinu ülesanne on kirjutada programm, mis vastab $Q$ päringule,
 kus iga päring koosneb positiivsete täisarvude paarist $(L, R)$
 ja päringu vastus arvutatakse järgmiselt.

Määrame puu igale tipule täisarvulise **koefitsiendi**.
Seda saame kirjeldada jadana $C[0], \ldots, C[N-1]$,
 kus $C[i]$ ($0 \leqslant i < N$) on tipule $i$ määratud koefitsient.
Nimetame jada $C$ **koefitsientide jadaks**.
Pane tähele, et selle jada elemendid võivad olla nii negatiivsed, nullid kui ka positiivsed.

Päringu $(L, R)$, korral nimetame koefitsientide jada **heaks**,
 kui iga tipu $i$ ($0 \leqslant i < N$) korral kehtib:
 tipu $i$ alampuu tippude koefitsientide summa
 pole väiksem kui $L$ ega suurem kui $R$.

Koefitsientide jada $C[0], \ldots, C[N-1]$ korral on
 tipu $i$ **hind** $|C[i]| \cdot W[i]$,
 kus $|C[i]|$ on $C[i]$ absoluutväärtus.
**Koguhind** on kõigi tippude hindade summa.
Sinu ülesanne on leida iga päringu jaoks
 **minimaalne koguhind**, mis on võimalik saavutada mõne hea koefitsientide jadaga.

On võimalik näidata, et iga päringu korral leidub vähemalt üks hea koefitsientide jada.

## Realiseerimine

Sa pead realiseerima kaks funktsiooni:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$ on $N$-elemendilised täisarvude massiivid,
   mis kirjeldavad tippude eellasi ja kaale.
* Seda funktsiooni kutsutakse igas testis välja täpselt üks kord
   sinu lahenduse ja hindamisprogrammi suhtluse alguses.

```
long long query(int L, int R)
```

* $L$, $R$ on ühe päringu täisarvulised parameetrid.
* Seda funktsiooni kutsutakse välja $Q$ korda pärast funktsiooni `init` väljakutset.
* Funktsioon peab tagastama päringu vastuse.

## Piirangud

* $1 \leqslant N \leqslant 200\,000$,
* $1 \leqslant Q \leqslant 100\,000$,
* $P[0] = -1$,
* $0 \leqslant P[i] < i$ iga $1 \leqslant i < N$ korral,
* $0 \leqslant W[i] \leqslant 1\,000\,000$ iga $0 \leqslant i < N$ korral,
* Kõigis päringutes on $1 \leqslant L \leqslant R \leqslant 1\,000\,000$.

## Alamülesanded

| Alamülesanne | Väärtus | Lisapiirangud |
| :-----: | :----: | ---------------------- |
|   1     |  $10$  | $Q \leqslant 10$; $W[P[i]] \leqslant W[i]$ iga $1 \leqslant i < N$ korral.
|   2     |  $13$  | $Q \leqslant 10$; $N \leqslant 2\,000$.
|   3     |  $18$  | $Q \leqslant 10$; $N \leqslant 60\,000$.
|   4     |  $7$   | $W[i] = 1$ iga $0 \leqslant i < N$ korral.
|   5     |  $11$  | $W[i] \leqslant 1$ iga $0 \leqslant i < N$ korral.
|   6     |  $22$  | $L = 1$.
|   7     |  $19$  | Lisapiiranguid ei ole.

## Näide

Vaatame järgnevaid väljakutseid:

```
init([-1, 0, 0], [1, 1, 1])
```

Puu koosneb $3$ tipust: juurest ja selle kahest järglasest.
Kõigi tippude kaalud on $1$.

```
query(1, 1)
```

Selles päringus on $L = R = 1$,
 mis tähendab, et iga alampuu koefitsientide summa peab olema $1$.
Vaatleme koefitsientide jada $[-1, 1, 1]$.
Alloleval joonisel on kujutatud puu ja selle tippude koefitsiendid (hallides ruutudes).

![](ex1.png "150")

Iga tipu $i$ ($0 \leqslant i < 3$) korral on tipu $i$ alampuu koefitsientide summa $1$.
Seega on see koefitsientide jada hea.
Tippude hinnad on järgmised:

| Tipp | Kaal | Koefitsient | Hind |
| :----: | :----: | :---------: | :-----------------------: |
|   0    |   1    |     -1      | $\mid -1 \mid \cdot 1 = 1$
|   1    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$
|   2    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$

Koguhind on seega $3$.
See on ainus hea koefitsientide jada,
 seega peab funktsioon tagastama $3$.

```
query(1, 2)
```

Sel juhul on vähim võimalik koguhind $2$
 ja selle saavutatab koefitsientide jada $[0, 1, 1]$.

## Näidishindaja

Sisendi vorming:

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

kus $L[j]$ ja $R[j]$ ($0 \leqslant j < Q$) on funktsiooni `query`
 $j$-nda väljakutse parameetrid.
Pane tähele, et sisendi teisel real on **ainult $N-1$ arvu**,
 sest näidishindaja ei loe sisendist $P[0]$ väärtust.

Väljundi vorming:

```
A[0]
A[1]
...
A[Q-1]
```

kus $A[j]$ ($0 \leqslant j < Q$)
 on funktsiooni `query` $j$-nda väljakutse tagastatud väärtus.
