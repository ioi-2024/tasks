# Sfinksi mõistatus

Chephreni sfinksil on sulle mõistatus.
Ta annab sulle $N$ tipuga graafi, mille
tipud on nummerdatud $0 \ldots N - 1$.
Graafis on $M$ serva.
Servad on nummerdatud $0 \ldots M - 1$.
Iga serv ühendab kaht erinevat tippu.
Servad on kahesuunalised.
Serv $j$ (kus $j$ on $0 \ldots M - 1$)
 ühendab tippe $X[j]$ ja $Y[j]$.
Iga tipupaari ühendab ülimalt üks serv.
Kaht tippu nimetatakse **naabriteks**,
 kui nad on servaga ühendatud.

Tippude jada $v_0, v_1, \ldots, v_k$ (kus $k \geqslant 0$)
 nimetatakse **ahelaks**,
 kui iga järjestikuste tippude paar
 (st tipud $v_l$ ja $v_{l+1}$ iga $0 \leqslant l \lt k$ korral)
 on naabrid.
Me ütleme, et ahel $v_0, v_1, \ldots, v_k$ **ühendab** tippe $v_0$ ja $v_k$.
Sulle antud graafis on iga tipupaar omavahel ühendatud vähemalt ühe ahelaga.

Selles ülesandes on $N + 1$ värvi.
Värvid on tähistatud $0 \ldots N$.
Värv $N$ on eriline **sfinksi värv**.
Graafi iga tipp on mingit värvi.
Täpsemalt on tipu $i$ ($0 \leqslant i \lt N$) värv $C[i]$.
Mitu tippu võivad olla sama värvi
 ja mõni värv võib olla ka kasutamata.
Algselt pole ükski tipp sfinksi värvi,
 st $0 \leqslant C[i] \lt N$ iga $0 \leqslant i \lt N$ korral.

Nimetame ahelat $v_0, v_1, \ldots, v_k$ (kus $k \geqslant 0$)
 **ühevärviliseks**, kui kõik selle tipud on sama värvi,
 st $C[v_l] = C[v_{l+1}]$ iga $0 \leqslant l \lt k$ korral.
Lisaks ütleme, et tipud $p$ ja $q$ ($0 \leqslant p \lt N$, $0 \leqslant q \lt N$)
 kuuluvad samasse **ühevärvilisse komponenti**
 parajasti siis, kui leidub neid ühendav ühevärviline ahel.

Sa tead graafi tippe ja servi,
 aga ei tea tippude värve.
Sinu ülesanne on tippude värvid teada saada,
 kasutades selleks **ümbervärvimiskatseid**.

Igas ümbervärvimiskatses võid sa
 muuta kuitahes paljude tippude värve.
Selleks valid sa kõigepealt
 $N$-elemendilise massiivi $E$,
 kus iga $0 \leqslant i \lt N$ korral on
 $E[i]$ väärtus $-1 \ldots N$ ($-1$ ja $N$ **kaasa arvatud**).
Seejärel määratakse tipu $i$ värviks $S[i]$, mis on:
* $C[i]$ (st tipu $i$ esialgne värv), kui $E[i] = -1$, või
* $E[i]$ vastasel juhul.

Pane tähele, et see tähendab, et ümbervävrimiskatsetes võid sa kasutada ka sfinksi värvi.

Katse tulemusena ütleb sfinks sulle,
 mitu ühevärvilist komponenti on graafis pärast
 tipu $i$ värvimist värvi $S[i]$ iga $0 \leqslant i \lt N$ korral.
Uued värvid kehtivad ajutiselt ainult katse ajal,
 **pärast katset saab iga tipp tagasi oma esialgse värvi**.

Sinu ülesanne on tuvastada graafi tippude esialgsed värvid
 ülimalt $2\,750$ ümbervärvimiskatse abil.
Osa punkte on võimalik saada ka selle eest, kui sa tuvastad
 iga naabertippude paari kohta, kas nad on sama värvi või mitte.

## Realiseerimine

Sa pead kirjutama ühe funktsiooni:

```
std::vector&lt;int&gt; find_colours(int N,
    std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y)
```

* $N$ on graafi tippude arv.
* $X$, $Y$ on $M$-elemendilised massiivid, mis kirjeldavad graafi servi.
* Funktsioon peab tagastama $N$-elemendilise massiivi $G$,
   mis kirjeldab graafi tippude värve.
* Seda funktsiooni kutsutakse igas testis välja täpselt üks kord.

See funktsioon võib ümbervärvimiskatseteks kasutada järgmist funktsiooni:

```
int perform_experiment(std::vector&lt;int&gt; E)
```

* $E$ on $N$-elemendiline massiiv, mis kirjeldab graafi tippude ümbervärvimist.
* Funktsioon tagastab ühevärviliste komponentide arvu graafis
   pärast selle tippude värvide muutmist vastavalt massiivile $E$.
* Seda funktsiooni võib välja kutsuda ülimalt $2\,750$ korda.

Selle ülesande hindaja **ei ole adaptiivne**. See tähendab,
et tippude värvid on fikseeritud enne funktsiooni `find_colours` väljakutset.

## Piirangud

* $2 \leqslant N \leqslant 250$,
* $N - 1 \leqslant M \leqslant \frac{N \cdot (N - 1)}{2}$,
* $0 \leqslant X[j] \lt Y[j] \lt N$ iga $0 \leqslant j \lt M$ korral,
* $X[j] \neq X[k]$ või $Y[j] \neq Y[k]$ iga $0 \leqslant j \lt k \lt M$ korral,
* iga tipupaar on ühendatud vähemalt ühe ahelaga,
* $0 \leqslant C[i] \lt N$ iga $0 \leqslant i \lt N$ korral.

## Alamülesanded

| Alamülesanne | Väärtus | Lisapiirangud |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = 2$.
| 2       | $7$    | $N \leqslant 50$.
| 3       | $33$   | Terve graaf on üks ahel: $M = N - 1$ ning iga $0 \leqslant j < M$ korral on tipud $j$ ja $j+1$ naabrid.
| 4       | $21$   | Graaf on täisgraaf: $M = \frac{N \cdot (N - 1)}{2}$ ja kõik tipupaarid on naabrid.
| 5       | $36$   | Lisapiiranguid ei ole.

Igas alamülesandes saab osa punkte selle eest,
 kui lahendus leiab iga naabertippude paari kohta,
 kas need on sama värvi või mitte.

Täpsemalt saab lahendus alamülesande eest täispunkid,
 kui igas testis on funktsiooni `find_colours`
 tagastatud massiiiv $G$ täpselt sama kui masiiiv $C$
 (st $G[i] = C[i]$ iga $0 \leqslant i \lt N$ korral).
Vastasel juhul saab lahendus $50\%$ alamülesande väärtusest,
 kui kõigis testides kehtivad järgmised tingimused:
* $0 \leqslant G[i] \lt N$ iga $0 \leqslant i \lt N$ korral;
* iga $0 \leqslant j \lt M$ korral:
  * $G[X[j]] = G[Y[j]]$ parajasti siis, kui $C[X[j]] = C[Y[j]]$.

## Näide

Vaatame järgmist väljakutset:

```
find_colours(4, [0, 1, 0, 0], [1, 2, 2, 3])
```

Oletame, et selles näites on graafi tippude värvid
 $C = [2, 0, 0, 0]$.
Sellele vastab allolev joonis,
 kus valgetes ringides olevad numbrid on tippude värvide tähised.

![example.png](sphinx_example.png "230")

Funktsioon `find_colours` võib funktsiooni `perform_experiment` välja kutusuda järgmiselt:

```
perform_experiment([-1, -1, -1, -1])
```

Selles ümbervärvimiskatses ei muudeta ühegi tipu värvi,
seega säilitavad kõik tipud oma esialgsed värvid.

Vaatame tippe $1$ ja $2$.
Nende mõlema värv on $0$ ja ahel $1, 2$ on seega ühevärviline.
Järelikult on tipud $1$ ja $2$ samas ühevärvilises komponendis.

Vaatame tippe $1$ ja $3$.
Kuigi nende mõlema värv on $0$, on nad erinevates
 ühevärvilistes komponentides, sest ei leidu
 neid ühendavat ühevärvilist ahelat.

Kokku on graafis $3$ ühevärvilist komponenti
 tippudega $\{0\}$, $\{1, 2\}$ ja $\{3\}$.
Seega tagastab see väljakutse $3$.

Järgmiseks võib funktsioon `find_colours` funktsiooni `perform_experiment` välja kutusuda järgmiselt:

```
perform_experiment([0, -1, -1, -1])
```

Selles ümbervärvimiskatses määratakse tipu $0$ uueks värviks $0$,
 mille tulemuseks on alloleval joonisel toodud värvidega graaf.

![example.png](sphinx_order1.png "230")

See väljakutse tagastab $1$, sest kõik tipud on samas ühevärvilises komponendis.
Sellest saame järeldada, et tippude $1$, $2$ ja $3$ esialgne värv on $0$.

Edasi võib funktsioon `find_colours` funktsiooni `perform_experiment` välja kutusuda järgmiselt:

```
perform_experiment([-1, -1, -1, 2])
```

Selles ümbervärvimiskatses määratakse tipu $3$ uueks värviks $2$,
 mille tulemuseks on alloleval joonisel toodud värvidega graaf.

![example.png](sphinx_order2.png "230")

See väljakutse tagastab $2$, sest graafis on $2$ ühevärvilist komponenti
 tippudega $\{0, 3\}$ ja $\{1, 2\}$.
Sellest saame järeldada, et tipu $0$ esialgne värv on $2$.

Funktsioon `find_colours` tagastab seejärel massiivi $G = [2, 0, 0, 0]$.
Kuna ka $C = [2, 0, 0, 0]$, teenib lahendus sellega täispunktid.

Pane tähele, et lisaks on mitu võimalikku tagastatavat väärtust,
 mille eest lahendus teeniks $50\%$ punktidest, näiteks
 $[1, 2, 2, 2]$ või $[1, 2, 2, 3]$.

## Näidishindaja

Sisendi vorming:

```
N  M
C[0]  C[1] ... C[N-1]
X[0]  Y[0]
X[1]  Y[1]
...
X[M-1]  Y[M-1]
```

Väljundi vorming:

```
L  Q
G[0]  G[1] ... G[L-1]
```

kus $L$ on funktsiooni `find_colours` tagastatud massiivi $G$ pikkus
 ja $Q$ on funktsiooni `perform_experiment` väljakutsete arv.
