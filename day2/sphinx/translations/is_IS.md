# Þraut Meyljónsins

Hið Mikla Meyljón er með þraut fyrir þig.
Þér er gefið net með $N$ hnútum.
Hnútarnir eru númeraðir frá $0$ til $N - 1$.
Það eru $M$ leggir í netinu sem eru númeraðir frá $0$ upp í $M - 1$.
Hver leggur tengir par af mismunandi hnútum og er tvístefndur.
Þá sérstaklega má segja að fyrir hvert $j$ á bilinu $0$ upp í $M - 1$,
 þar sem báðir endapunkar eru talnir með, tengir leggur $j$ hnútana $X[j]$ og $Y[j]$.
Það er mest einn leggur sem tengir hvert par af hnútum.
Tveir hnútar eru sagðir vera **aðlægir** ef leggur tengir þá.

Runa af hnútum $v_0, v_1, \ldots, v_k$, þar sem $k \ge 0$,
er sögð vera **leið** ef sérhverjir samliggjandi hnútar $v_l$ og $v_{l+1}$ eru aðlægir,
fyrir sérhvert $l$ þar sem $0 \leq l \lt k$.
Við segjum að leið $v_0, v_1, \ldots, v_k$ **tengi** hnúta $v_0$ og $v_k$.
Í netinu sem þér er gefið er sérhvert par hnúta tengt með einhverri leið.

Það eru $N + 1$ litir, númeraðir frá $0$ upp í $N$.
Litur $N$ er sérstakur og er kallaður **litur Meyljónsins**.
Sérhverjum hnút er úthlutað lit.
Margir hnútar geta verið litaðir með sama litnum og það geta verið einhverjir
ónotaðir litir, sem er ekki úthlutað á neinn hnút.
Enginn hnútur fær lit Meyljónsins, það er $0 \le C[i] \lt N$ fyrir sérhvert $i$ þar sem $0 \le i \lt N$.

Leið $v_0, v_1, \ldots, v_k$, þar sem $k \ge 0$,
er sögð vera **einlita** ef allir hnútarnir í leiðinni
eru litaðir með sama lit, það er $C[v_l] = C[v_{l+1}]$ fyrir sérhvert $l$ þar sem $0 \le l \lt k$.
Enn fremur segjum við að hnútar $p$ og $q$, þar sem $0 \le p \lt N$, $0 \le q \lt N$, eru í 
sama **einlita samliggjandi þætti** þá og því aðeins ef þeir eru tengdir með einlita leið.

Þú veist hnútana og leggina en þú veist ekki hvaða
lit hefur verið úthlutað á hvern hnút.
Þú vilt finna liti hnútanna með því að framkvæma
**endurlitunartilraunir**.

Í endurlitunartilraun máttu endurlita handahófskenndan fjölda hnúta.
Þá sérstaklega til að framkvæma endurlitunartilraunir velur þú fyrst
fylki $E$ af stærð $N$, þar sem fyrir sérhvert $i$, þar sem $0 \leq i \lt N$,
er $E[i]$ milli $-1$ og $N$, þar sem báðir endapunktar eru talnir með.
Þá verður liturinn á hnút $i$ að $S[i]$, þar sem gildið á $S[i]$ er:
* $C[i]$, það er upprunalegi liturinn á hnút $i$, ef $E[i] = -1$, eða
* $E[i]$, annars.

Athugaðu að þetta þýðir að þú mátt nota lit Meyljónsins í endurlituninni þinni.

Að lokum tilkynnir hið Mikla Meyljón hver fjöldi einlita samhangandi þátta er eftir að
hafa stillt lit hvers hnúts $i$ sem $S[i]$, þar sem $0 \le i \lt N$.
Nýja litunin er í gildi einungis fyrir þessa sérstöku endurlitunartilraun, þannig
**litir allra hnúta breytast aftur í upprunalegu litina eftir að tilraunin hefur klárast**.

Verkefni þitt er að finna liti hnútanna í netinu með því að framkvæma
mest $2\,750$ endurlitunartilraunir.
Þú getur einnig fengið hlutstig ef þú ákvarðar rétt fyrir sérhvert par
aðlægra hnúta hvort hnútarnir séu litaðir eins.

## Útfærlsusmáatriði

Þú skalt útfæra eftirfarandi stefju.

```
std::vector&lt;int&gt; find_colours(int N,
    std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y)
```

* $N$: fjöldi hnúta í netinu.
* $X$, $Y$: fylki af lengd $N$ sem lýsir leggjunum.
* Stefjan skal skila fylki $G$ af lengd $N$ sem táknar liti hnúta netsins.
* Kallað er í stefjuna nákvæmlega einu sinni í hverju prufutilviki.

Stefjan að ofan má kalla í eftirfarandi stefju til að framkvæma endurlitunartilraunirnar:

```
int perform_experiment(std::vector&lt;int&gt; E)
```

* $E$: fylki af lengd $N$ sem lýsir hvernig skal endurlita hnútana.
* Þessi stefja skilar fjölda einlita samhangandi þátta eftir að hafa endurlitað hnútana út frá $E$.
* Kalla má í þessa stefju mest $2\,750$ sinnum.

Yfirferðarforritið **aðlagar sig ekki** að útfærslu þinni.
Í öðrum orðum þá er ákvarðað liti hnútanna áður en kallað er í `find_colours`.

## Takmarkanir

* $2 \le N \le 250$
* $N - 1 \le M \le \frac{N \cdot (N - 1)}{2}$
* $0 \le X[j] \lt Y[j] \lt N$ fyrir sérhvert $j$ þar sem $0 \le j \lt M$.
* $X[j] \neq X[k]$ or $Y[j] \neq Y[k]$
   fyrir sérhvert $j$ og $k$ þar sem $0 \le j \lt k \lt M$.
* Sérhvert par hnúta er tengt með einhverri leið.
* $0 \le C[i] \lt N$ fyrir sérhvert $i$ þar sem $0 \le i \lt N$.

## Stigagjöf

| Hópur | Stig  | Frekari takmarkanir |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = 2$
| 2       | $7$    | $N \le 50$
| 3       | $33$   | Netið er leið: $M = N - 1$ og $j$ hnútar $j+1$ eru aðlægir þar sem $0 \leq j < M$.
| 4       | $21$   | Netið er fulltengt: $M = \frac{N \cdot (N - 1)}{2}$ og hvaða tveir hnútar sem er eru aðlægir.
| 5       | $36$   | Engar frekari takmarkanir.

Í sérhverjum stigahóp getur þú fengið hlutstig
ef forritið þitt ákvarðar rétt fyrir sérhvert
par hnúta hvort þeir séu litaðir eins.

Þá nákvæmlega færðu öll stigin fyrir stigahóp ef
fylkið $G$ sem `find_colours` skilar er nákvæmlega
hið sama og fylkið $C$ í öllum prufutilvikum innan hans.
Það er $G[i] = C[i]$ fyrir öll $i$ þar sem $0 \le i \lt N$.
Annars færðu nákvæmlega $50\%$ stiganna fyrir stigahóp ef
eftirfarandi skilyrði standast fyrir öll prufutilvik innan hans:
* $0 \le G[i] \lt N$ fyrir sérhvert $i$ þar sem $0 \le i \lt N$;
* Fyrir sérhvert $j$ þar sem $0 \le j \lt M$:
   * $G[X[j]] = G[Y[j]]$ þá og því aðeins ef $C[X[j]] = C[Y[j]]$.


## Sýnidæmi

Íhugaðu eftirfarandi kall.

```
find_colours(4, [0, 1, 0, 0], [1, 2, 2, 3])
```

Í þessu sýnidæmi skulum við hugsa okkur að (földu) litir hnútanna séu
 $C = [2, 0, 0, 0]$.
Þessi atburðarás er sýnd í eftirfarandi mynd.
Litir eru aukalega táknaðir með tölum á hvítum merkjum sem hanga á sérhverjum hnút.


![example.png](sphinx_example.png "230")

Þessi stefja gæti kallað á `perform_experiment` á eftirfarandi máta.

```
perform_experiment([-1, -1, -1, -1])
```

Í þessu kalli er ekki endurlitað neinn hnút, þannig sérhver hnútur heldur upprunalega litnum sínum.

Íhugaðu hnút $1$ og hnút $2$.
Þeir eru báðir litaðir með lit $0$ og leiðin $1, 2$ er einlita leið.
Þess vegna eru hnútar $1$ og $2$ í sama einlita samhangandi þætti.

Íhugaðu hnút $1$ og hnút $3$.
Þó að báðir hnútarnir séu litaðir með lit $0$,
 þá eru þeir í mismunandi einlita samhangandi þáttum
 þar sem það er engin einlita leið sem tengir þá.

Í heildina eru $3$ einlita samhangandi þættir með hnútana
$\{0\}$, $\{1, 2\}$, og $\{3\}$.
Því skilar þetta kall $3$.

Núna getur stefjan kallað á `perform_experiment` á eftirfarandi máta.

```
perform_experiment([0, -1, -1, -1])
```

Í þessu kalli er einungis endurlitað hnút $0$ sem gefur litunina
sem er sýnd á eftirfarandi mynd.

![example.png](sphinx_order1.png "230")

Þetta kall skilar $1$, þar sem allir hnútarnir tilheyra sama einlita samhangandi þættinum.
Við getum núna dregið ályktunina að hnútar $1$, $2$, og $3$ séu litaðir með litnum $0$.

Stefjan getur núna kallað á `perform_experiment` á eftirfarandi máta.

```
perform_experiment([-1, -1, -1, 2])
```

Í þessu kalli er endurlitað hnút $3$ með litnum $2$ sem  gefur litunina
sem er sýnd á eftirfarandi mynd.

![example.png](sphinx_order2.png "230")

Þetta kall skilar $2$ þar sem það eru $2$ einlita samhangandi þættir
 með hnútana  $\{0, 3\}$ and $\{1, 2\}$.
Við getum núna dregið ályktunina að hnútur $0$ sé litaður með liti $2$.

Stefjan `find_colours` skilar þá fylkinu $[2, 0, 0, 0]$.
Þar sem $C = [2, 0, 0, 0]$ þá er gefið full stig.

Athugaðu að það eru til mörg mögulega skilagildi þar sem $50\%$ stiganna yrðu gefin, til dæmis $[1, 2, 2, 2]$ eða $[1, 2, 2, 3]$.

## Sýnisyfirferðarforrit

Snið inntaks:

```
N  M
C[0]  C[1] ... C[N-1]
X[0]  Y[0]
X[1]  Y[1]
...
X[M-1]  Y[M-1]
```

Snið úttaks:

```
L  Q
G[0]  G[1] ... G[L-1]
```

Hér er $L$ lengdin á fylkinu $G$ sem er skilagildi `find_colours`,
 og $Q$ er fjöldi kalla í `perform_experiment`.
