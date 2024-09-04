# Niilus

Sa tahad mööda Niilust transportida $N$ objekti.
Objektid on nummerdatud $0 \ldots N-1$.
Objekti $i$ ($0 \leqslant i < N$) kaal on $W[i]$.

Objektide transportimiseks kasutatakse spetsiaalseid laevu.
Iga laev suudab kanda **maksimaalselt kaht** objekti.

* Kui sa paned laevale ühe objekti, võib selle kaal olla ükskõik milline.
* Kui sa tahad panna laevale kaks objekti, pead sa tagama, et laev on tasakaalus.
Täpsemalt võid sa objektid $p$ ja $q$ ($0 \leqslant p < q < N$) ühele laevale panna
 ainult siis, kui nende kaalude vahe absoluutväärtus on ülimalt $D$,
 s.t $|W[p] - W[q]| \leqslant D$.

Objekti transportimise hind sõltub sellest, kui palju objekte on ühel laeval.
Obekti $i$ ($0 \leqslant i < N$) transport maksab:
* $A[i]$, kui sa transpordid selle objekti eraldi laevaga, või
* $B[i]$, kui sa transpordid selle objekti mõne teise objektiga koos.

Pane tähele, et teisel juhul pead sa siiski maksma mõlema laeval oleva objekti eest.
Täpsemalt, kui sa transpordid objektid $p$ ja $q$ ($0 \leqslant p < q < N$) ühe laevaga,
 siis on selle hind $B[p] + B[q]$.

Objekti transportimine eraldi laevaga on alati kallim kui selle transportimine
koos mõne teise objektiga: iga $0 \leqslant i < N$ korral kehtib $B[i] < A[i]$.

Kahjuks on veeolud ettearvamatud ja $D$ väärtus muutub sageli.
Sinu ülesanne on vastata $Q$ päringule, mis on nummerdatud $0 \ldots Q-1$.
Päringuid kirjeldab $Q$-elemendiline massiiv $E$.
Päringu $j$ ($0 \leqslant j < Q$) vastuseks on
 kõigi $N$ objekti transportimise minimaalne koguhind,
 kui $D$ väärtus on $E[j]$.

## Realiseerimine

Sa pead realiseerima ühe funktsiooni:

```
std::vector&lt;long long&gt; calculate_costs(
    std::vector&lt;int&gt; W, std::vector&lt;int&gt; A,
    std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```

* $W$, $A$, $B$ on $N$-elemendilised täisarvude massiivid,
   mis kirjeldavad objektide kaale ja nende transportimise hindu.
* $E$ on $Q$-elemendiline täisarvude massiiv,
   mis kirjeldab $D$ väärtusi päringutes.
* Funktsioon peab tagastama $Q$-elemendilise täisarvude massiivi $R$,
   mis kirjeldab objektide transportimise minimaalseid koguhindu:
   iga $0 \leqslant j < Q$ korral peab $R[j]$ näitama kõigi $N$ objekti
   transportimise minimaalset koguhinda,
   kui $D$ väärtus on $E[j]$.
* Seda funktsiooni kutsutakse igas testis välja täpselt üks kord.

## Piirangud

* $1 \leqslant N \leqslant 100\,000$,
* $1 \leqslant Q \leqslant 100\,000$,
* $1 \leqslant W[i] \leqslant 10^{9}$
   iga $0 \leqslant i < N$ korral,
* $1 \leqslant B[i] < A[i] \leqslant 10^{9}$
   iga $0 \leqslant i < N$ korral,
* $1 \leqslant E[j] \leqslant 10^{9}$
   iga $0 \leqslant j < Q$ korral.

## Alamülesanded

| Alamülesanne | Väärtus | Lisapiirangud |
| :-----: | :----: | ---------------------- |
| 1       | $6$    | $Q \leqslant 5$; $N \leqslant 2000$; $W[i] = 1$ iga $0 \leqslant i < N$ korral.
| 2       | $13$   | $Q \leqslant 5$; $W[i] = i+1$ iga $0 \leqslant i < N$ korral.
| 3       | $17$   | $Q \leqslant 5$; $A[i] = 2$ ja $B[i] = 1$ iga $0 \leqslant i < N$ korral.
| 4       | $11$   | $Q \leqslant 5$; $N \leqslant 2000$.
| 5       | $20$   | $Q \leqslant 5$.
| 6       | $15$   | $A[i] = 2$ ja $B[i] = 1$ iga $0 \leqslant i < N$ korral.
| 7       | $18$   | Lisapiiranguid ei ole.

## Näide

Vaatame järgmist väljakutset:

```
calculate_costs([15, 12, 2, 10, 21],
                [5, 4, 5, 6, 3],
                [1, 2, 2, 3, 2],
                [5, 9, 1])
```

Selles näites on $N = 5$ objekti ja $Q = 3$ päringut.

Esimeses päringus on $D = 5$.
Sa võid transportida objektid $0$ ja $3$ ühe laevaga (sest $|15 - 10| \leqslant 5$)
 ning ülejäänud objektid kõik eraldi laevadega.
Nii on kogukulu $1+4+5+3+3 = 16$, mis on ka minimaalne võimalik.

Teises päringus on $D = 9$.
Sa võid transportida objektid $0$ ja $1$ ühe laevaga (sest $|15 - 12| \leqslant 9$),
 objektid $2$ ja $3$ teise laevaga (sest $|2 - 10| \leqslant 9$)
 ning viimase objekti eraldi laevaga.
Nii on kogukulu $1+2+2+3+3 = 11$, mis on ka minimaalne võimalik.

Viimases päringus on $D = 1$. Sa pead transportima iga objekti eraldi laevaga.
Nii on kogukulu $5+4+5+6+3 = 23$, mis on ka minimaalne võimalik.

Seega peaks funktsioon tagastama $[16, 11, 23]$.

## Näidishindaja

Sisendi vorming:

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

Väljundi vorming:

```
R[0]
R[1]
...
R[S-1]
```

kus $S$ on funktsiooni `calculate_costs` tagastatud massiivi $R$ elementide arv.
