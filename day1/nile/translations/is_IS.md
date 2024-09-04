# Níl

Þú vilt flytja $N$ gripi með fram ánni Níl.
Gripirnir eru númeraðir frá $0$ upp í $N - 1$.
Vægi grips $i$, þar sem $0 \leq i < N$, er $W[i]$.

Til að flytja gripina notarðu sérsmíðaða báta.
Sérhver bátur getur flutt **mest tvo** gripi.

* Ef þú ákveður að setja einn grip í bát má vægi gripsins vera handahófskennd.
* Ef þú vilt setja tvo gripi með sama bát þarftu að tryggja að báturinn haldi jafnvægi.
Þá sérstaklega geturðu sent grip $p$ og $q$, þar sem $0 \leq p < q < N$ með sama bát aðeins ef munurinn milli vægis $p$ og vægis $q$ er mest $D$, það er $|W[p] - W[q]| \leq D$.

Til að flytja grip þarftu að borga kostnað sem byggist á fjölda gripa
sem eru fluttir með sama bátnum.
Kostnaðurinn við að flytja grip $i$, þar sem $0 \leq i < N$, er:

* $A[i]$, ef þú setur gripinn í sinn eigin bát, eða
* $B[i]$, ef þú setur hann í bát með einhverjum öðrum grip.

Athugaðu að í seinna tilvikinu þarftu að borga fyrir báða gripina í bátnum.
Þá sérstaklega, ef þú ákveður að senda gripi $p$ og $q$, þar sem $0 \leq p < q < N$ með sama bátnum,
þarftu að borga $B[p] + B[q]$.

Að senda grip með sér bát er alltaf dýrara en að senda hann með einhverjum öðrum grip og þar með láta gripina deila bát.
Þannig að $B[i] < A[i]$ fyrir öll $i$ þar sem $0 \leq i < N$.

Því miður er áin mjög ófyrirsjáanleg og gildið á $D$ breytist oft.
Verkefni þitt er að svara $Q$ fyrirspurnum, sem eru númeraðar frá $0$ upp í $Q - 1$.
Fyrirspurnunum er lýst með fylki $E$ sem hefur lengd $Q$.
Svarið við fyrirspurn $j$, þar sem $0 \leq j < Q$, er lágmarks kostnaður við að flytja
alla $N$ gripina, þegar gildið á $D$ er jafnt $E[j]$.

## Útfærslusmáatriði

Þú skalt útfæra eftirfarandi stefju.

```
std::vector&lt;long long&gt; calculate_costs(
    std::vector&lt;int&gt; W, std::vector&lt;int&gt; A, 
    std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```

* $W$, $A$, $B$: heiltölufylki sem hefur lengd $N$, sem lýsa vigtum gripanna og flutningskostnaði þeirra.
* $E$: heiltölufylki sem hefur lengd $Q$ sem lýsir gildinu á $D$ fyrir hverja fyrirspurn.
* Þessi stefja skal skila heiltölufylki $R$ með lengd $Q$ sem inniheldur lágmarks kostnaðinn
   við að flytja gripina, þar sem $R[j]$ segir til um kostnaðinn þegar gildið á $D$ er $E[j]$,
   fyrir sérhvert $j$ þar sem $0 \leq j < Q$.
* Kallað er í þessa stefju nákvæmlega einu sinni fyrir hvert prufutilvik.

## Takmarkanir

* $1 \leq N \leq 100\,000$
* $1 \leq Q \leq 100\,000$
* $1 \leq W[i] \leq 10^{9}$
   fyrir sérhvert $i$ þar sem $0 \leq i < N$
* $1 \leq B[i] < A[i] \leq 10^{9}$
   fyrir sérhvert $i$ þar sem $0 \leq i < N$
* $1 \leq E[j] \leq 10^{9}$
   fyrir sérhvert $j$ þar sem $0 \leq j < Q$

## Stigagjöf

| Hópur   | Stig   | Frekari takmarkanir |
| :-----: | :----: | ---------------------- |
| 1       | $6$    | $Q \leq 5$; $N \leq 2000$; $W[i] = 1$ fyrir sérhvert $i$ þar sem $0 \leq i < N$
| 2       | $13$   | $Q \leq 5$; $W[i] = i+1$ fyrir sérhvert $i$ þar sem $0 \leq i < N$
| 3       | $17$   | $Q \leq 5$; $A[i] = 2$ og $B[i] = 1$ fyrir sérhvert $i$ þar sem $0 \leq i < N$
| 4       | $11$   | $Q \leq 5$; $N \leq 2000$
| 5       | $20$   | $Q \leq 5$
| 6       | $15$   | $A[i] = 2$ og $B[i] = 1$ fyrir sérhvert $i$ þar sem $0 \leq i < N$
| 7       | $18$   | Engar frekari takmarkanir.

## Sýnidæmi

Íhugaðu eftirfarandi kall.

```
calculate_costs([15, 12, 2, 10, 21],
                [5, 4, 5, 6, 3],
                [1, 2, 2, 3, 2],
                [5, 9, 1])
```

Í þessu sýnidæmi erum við með $N = 5$ gripi og $Q = 3$ fyrirspurnir.

Í fyrstu fyrirspurninni er $D = 5$.
Þú getur sent gripi $0$ og $3$ í einum bát, þar sem $|15 - 10| \leq 5$, og gripina sem eru afgangs í sér bátum.
Þetta gefur lágmarks kostnaðinn við að flytja alla gripina, sem er $1 + 4 + 5 + 3 + 3 = 16$.

Í annarri fyrirspurninni er $D = 9$.
Þú getur sent gripi $0$ og $1$ í einum bát, þar sem $|15 - 12| \leq 9$, og sent gripi $2$ og $3$ í einum bát, þar sem $|2 - 10| \leq 9$.
Gripurinn sem er í afgang má senda í sér bát.
Þetta gefur lágmarks kostnaðinn við að flytja alla gripina, sem er $1 + 2 + 2 + 3 + 3 = 11$.

Í síðustu fyrirspurninni er $D = 1$.
Þú þarft að senda hvern grip í sér bát.
Þetta gefur lágmarks kostnaðinn við að flytja alla gripina, sem er $5 + 4 + 5 + 6 + 3 = 23$.

Því skal stefjan skila $[16, 11, 23]$.


## Sýnisyfirferðarforrit

Snið inntaks:

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

Snið úttaks:

```
R[0]
R[1]
...
R[S-1]
```

Hér er $S$ lengd fylkisins $R$ sem `calculate_costs` skilar.
