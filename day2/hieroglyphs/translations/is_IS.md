# Helgirúnir

Lið rannsakenda er að rannsaka svipleika á milli runa af helgirúnum.
Þau tákna hverja helgirún sem ekki neikvæða heiltölu.
Til að framkvæma rannsóknina,
þá nota þau eftirfarandi eiginleika um runurnar.

Fyrir fasta runu $A$,
þá er runa $S$ kölluð **hlutruna** í $A$
þá og því aðeins að hægt sé að fá rununa $S$ úr $A$
með því að fjarlæga (mögulega engin) stök úr $A$.

Taflan að neðan sýnir nokkur dæmi um hlutrunur úr rununni $A = [3, 2, 1, 2]$.

| Hlutruna    | Hvernig hún er fengin úr $A$ |
|----------------|---------------------------------|
| [3, 2, 1, 2] | Engin stök eru fjarlæg.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] or [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Á hinn mátan eru $[3, 3]$ eða $[1, 3]$ ekki hlutrunur úr $A$.

Íhugið tvær runur af helgirúnum, $A$ og $B$.
Hlutruna $S$ er kölluð **sameiginleg hlutruna** af $A$ og $B$
þá og því aðeins að $S$ er hlutruna í bæði $A$ og $B$.
Einnig segjum við að hlutruna $U$ er **allsherja sameiginleg hlutruna** í $A$ og $B$
þá og því aðeins að eftirfarandi tvö skilyrði gilda:
* $U$ er sameiginleg hlutruna í $A$ og $B$.
* Allar sameiginlegar hlutrunur í $A$ og $B$ eru einnig hlutrunur í $U$.

Hægt er að sýna fram á að allar runur $A$ og $B$
innihaldi mest eina allsherja sameiginlega hlutrunu.

Rannsakendurnir hafa fundið tvær runur af helgirúnum $A$ og $B$.
Runa $A$ samanstendur af $N$ helgirúnum
og runa $B$ samanstendur af $M$ helgirúnum.
Þú átt að hjálpa rannsakendunum að finna
allsherja sameiginlega hlutrunu í rununum $A$ og $B$,
eða ákvarða að engin þannig runa sé til.

## Útfærslusmáatriði

Þú skalt útfæra eftirfarandi stefju.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: fylki af lengd $N$ sem lýsir fyrstu rununni.
* $B$: fylki af lengd $M$ sem lýsir seinni rununni.
* Ef það er til allsherja sameiginleg hlutruna í $A$ og $B$,
þá skal stefjan skila fylki sem inniheldur hlutrununa.
Annars skal stefjan skila $[-1]$
(fylki af lengd $1$, þar sem eina stakið er $-1$).
* Kallað er á stefjuna nákvæmlega einu sinni fyrir sérhvert prufutilvik.

## Takmarkanir

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ fyrir sérhvert $i$ þar sem $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ fyrir sérhvert $j$ þar sem $0 \leq j < M$

## Stigagjöf

| Hópur | Stig  | Frekari takmarkanir |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$;  $A$ og $B$ hvor fyrir sig samanstanda af $N$ **mismunandi** heiltölum milli $0$ og $N-1$, þar sem báðir endapunktaru eru meðtalnir.
| 2       | $15$   | Fyrir hvaða heiltölu sem er $k$, þá er (fjöldi staka í $A$ jafnt og $k$) plús (fjöldi staka i $B$ jafnt og $k$) í mesta lagi $3$.
| 3       | $10$   | $A[i] \leq 1$ fyrir sérhvert $i$ þar sem $0 \leq i < N$; $B[j] \leq 1$ fyrir sérhvert $j$ þar sem $0 \leq j < M$
| 4       | $16$   | Til er allsherja sameiginleg hlutruna í $A$ og $B$.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | Engar frekari takmarkanir.

## Sýnidæmi

### Sýnidæmi 1

Íhugið eftirfarandi kall.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Hérna eru sameiginlegu hlutrunurnar í $A$ og $B$ eftirfarandi:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ and $[0, 1, 0, 2]$.

Þar sem  $[0, 1, 0, 2]$ er sameiginleg hlutruna í $A$ og $B$, og
allar sameiginlegar hlutrunur í $A$ og $B$ eru hlutrunur í $[0, 1, 0, 2]$,
þá skilar stefjan $[0, 1, 0, 2]$.

### Sýnidæmi 2

Íhugið eftirfarandi kall.

```
ucs([0, 0, 2], [1, 1])
```

Hérna eru sameiginlegu hlutrunurnar í $A$ og $B$ tóma hlutrunan $[\ ]$.
Skal því stefjan skila tóma fylkinu $[\ ]$.

### Sýnidæmi 3

Íhugið eftirfarandi kall.

```
ucs([0, 1, 0], [1, 0, 1])
```

Hérna eru sameiginlegu hlutrunurnar í $A$ og $B$ eftirfarandi:
 $[\ ], [0], [1], [0, 1]$ and $[1, 0]$.
Hægt er að sýna að allsherja sameiginleg hlutruna sé ekki til.
Skal því stefjan skila $[-1]$.

## Sýnisyfirferðarforrit

Snið inntaks:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Snið úttaks:

```
T
R[0]  R[1]  ...  R[T-1]
```

Hérna er $R$ fylkið sem `ucs` skilar frá sér og $T$ lengd þess.
