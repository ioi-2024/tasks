# Sfinksin arvoitus

Suurella Sfinksillä on sinulle arvoitus. 
Sinulle annetaan verkko, jossa on $N$ solmua.
Solmut on numeroitu välillä $0$: sta $N - 1$ asti.
Verkossa on $M$ kaarta, jotka on numeroitu $0$:sta $M-1$ asti.
Jokainen kaari yhdistää kaksi eri solmua ja on kaksisuuntainen.
Tarkemmin sanottuna jokaista $j$:tä kohden $0$:sta $M - 1$ asti (mukaan lukien)
 kaari $j$ yhdistää solmut $X[j]$ ja $Y[j]$.
Mitä tahansa solmuparia yhdistää enintään yksi kaari.
Kahta solmua kutsutaan **viereisiksi**
 jos ne on yhdistetty kaarella.

Jonoa solmuja $v_0, v_1, \ldots, v_k$ ($k \ge 0$)
 kutsutaan **poluksi**
 jos kaikki peräkkäiset solmut $v_l$ ja $v_{l+1}$
 (jokaista $l$ kohden siten, että $0 \le l \lt k$)
 ovat viereisiä.
Sanomme, että polku $v_0, v_1, \ldots, v_k$ **yhdistää** solmut $v_0$ ja $v_k$.
Sinulle annetussa verkossa jokainen solmupari on yhdistetty jollakin polulla.

On olemassa $N + 1$ väriä, numeroitu $0$:sta $N$ asti.
Väri $N$ on erityinen ja sitä kutsutaan **Sfinksin väriksi**.
Jokaiselle solmulle on määritetty väri.
Tarkemmin sanottuna solmulla $i$ ($0 \le i \lt N$) on väri $C[i]$.
Useilla solmuilla voi olla sama väri, 
ja voi olla värejä, joita ei ole määritetty mihinkään solmuun.
Millään solmulla ei ole sfinksin väriä,
 eli $0 \le C[i] \lt N$ ($0 \le i \lt N$).

Polkua $v_0, v_1, \ldots, v_k$ ($k \ge 0$)
 kutsutaan **monokromaattiseksi**,
 jos
 sen kaikilla solmuilla on sama väri,
 eli $C[v_l] = C[v_{l+1}]$ (jokaiselle $l$:lle siten, että $0 \le l \lt k$).
Lisäksi sanomme, että solmut $p$ ja $q$ ($0 \le p \lt N$ , $0 \le q \lt N$)
 ovat samassa **monokromaattisessa komponentissa**,
 jos ja vain jos ne on yhdistetty monokromaattisella polulla.

Tiedät solmut ja kaaret,
 mutta et tiedä mikä väri kullakin solmulla on.
Haluat selvittää solmujen värit,
 suorittamalla **uudelleenvärjäyskokeita**.

Uudelleenvärjäyskokeessa
 voit värjätä mielivaltaisesti useita solmuja.
Tarkemmin ottaen uudelleenvärjäyskokeen suorittamiseen
 valitset ensin taulukon $E$ jonka koko on $N$,
 missä jokaiselle $i$ ($0 \le i \lt N$),
 $E[i]$ on välillä $-1$ ja $N$ **mukaan lukien**.
Sitten kunkin solmun $i$ väristä tulee $S[i]$, jossa $S[i]$:n arvo on:
* $C[i]$, eli $i$ :n alkuperäinen väri, jos $E[i] = -1$, tai
* $E[i]$, muuten.

Huomaa, että tämä tarkoittaa, että voit käyttää Sfinksin väriä uudelleenvärjäyksessä.

Lopulta Suuri Sfinksi ilmoittaa
 monokromaattisten komponenttien lukumäärän verkossa,
 kun olet asettanut kunkin solmun $i$ väriksi $S[i]$ ( $0 \le i \lt N$ ).
Uusi väritys on käytössä vain tässä uudelleenvärjäyskokeessa,
 joten **kaikkien solmujen värit palautuvat alkuperäisiksi kokeen päätyttyä**.

Sinun tehtäväsi on tunnistaa verkon solmujen värit
 suorittamalla korkeintaan $2\,750$ uudelleenvärjäyskoetta. 
Voit saada myös osittaiset pisteet
 jos määrität oikein jokaiselle vierekkäisten solmujen parille,
 onko niillä sama väri.

## Toteutuksen yksityiskohdat

Sinun tulee toteuttaa seuraava funktio.

```
std::vector&lt;int&gt; find_colours(int N,
    std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y)
```

* $N$: verkon solmujen lukumäärä.
* $X$, $Y$: $M$:n pituiset taulukot, jotka kuvaavat kaaria.
* Tämän funktion pitäisi palauttaa taulukko $G$, jonka pituus on $N$,
   jossa on verkon solmujen värit.
* Tätä funktiota kutsutaan täsmälleen kerran jokaisessa testitapauksessa.

Yllä oleva funktio voi tehdä kutsuja seuraavaan funktioon
 uudelleenvärjäyskokeiden suorittamiseen:

```
int perform_experiment(std::vector&lt;int&gt; E)
```

* $E$: $N$:n pituinen taulukko, joka määrittää kuinka solmut tulee värjätä.
* Tämä funktio palauttaa monokromaattisten komponenttien määrän
   solmujen uudelleenvärjäyksen jälkeen $E$ mukaisesti.
* Tätä funktiota voidaan kutsua enintään $2\,750$ kertaa.

Testijärjestelmä **ei ole mukautuva**, eli
 solmujen värit päätetään ennen kuin `find_colours`:ia kutsutaan.

## Rajat

* $2 \le N \le 250$
* $N - 1 \le M \le \frac{N \cdot (N - 1)}{2}$
* $0 \le X[j] \lt Y[j] \lt N$ kaikilla $j$ siten, että $0 \le j \lt M$.
* $X[j] \neq X[k]$ tai $Y[j] \neq Y[k]$
   kaikilla $j$ ja $k$ siten, että $0 \le j \lt k \lt M$.
* Jokainen solmupari on yhdistetty jollakin polulla
* $0 \le C[i] \lt N$ kaikilla $i$ siten, että $0 \le i \lt N$.

## Osatehtävät

| Osatehtävä | Pisteet  | Lisäehdot |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = 2$
| 2       | $7$    | $N \le 50$
| 3       | $33$   | Verkko on polku: $M = N - 1$ ja solmut $j$ ja $j+1$ ovat viereisiä ($0 \leq j < M$).
| 4       | $21$   | Verkko on täydellinen: $M = \frac{N \cdot (N - 1)}{2}$ ja mitkä tahansa kaksi solmua ovat viereiset.
| 5       | $36$   | Ei lisäehtoja.

Jokaisesta osatehtävästä voit saada osittaisen pistemäärän,
 jos ohjelma määrittää oikein
 jokaiselle vierekkäiselle pisteparille
 onko niillä sama väri.

Tarkemmin sanottuna
 saat osatehtävän koko pistemäärän,
 jos kaikissa testitapauksissa
 taulukko $G$ jonka `find_colours` palauttaa
 on täsmälleen sama kuin taulukko $C$
 (eli $G[i] = C[i]$
 kaikille $i$ siten, että $0 \le i \lt N$).
Muuten,
 saat $50\%$ alatehtävän pisteistä
 jos seuraavat ehdot täyttyvät
 kaikissa testitapauksissaan:
* $0 \le G[i] \lt N$
   jokaiselle $i$ lle siten, että $0 \le i \lt N$;
* Jokaiselle $j$ lle siten, että $0 \le j \lt M$:
  * $G[X[j]] = G[Y[j]]$ jos ja vain jos $C[X[j]] = C[Y[j]]$.

## Esimerkki

Tarkastellaan seuraavaa kutsua

```
find_colours(4, [0, 1, 0, 0], [1, 2, 2, 3])
```

Tässä esimerkissä oletetaan, että
 solmujen (piilotetut) värit annetaan
 $C = [2, 0, 0, 0]$ .
Tämä tapaus on esitetty seuraavassa kuvassa.
Värit esitetään lisäksi numeroilla jokaiseen solmuun kiinnitetyissä valkoisissa tarroissa.

![example.png](sphinx_example.png "230")

Funktio voi kutsua `perform_experiment` seuraavasti.

```
perform_experiment([-1, -1, -1, -1])
```

Tässä kutsussa yhtään solmua ei värjätä uudelleen, koska kaikki solmut säilyttävät alkuperäiset värinsä.

Tarkastele solmuja $1$ ja $2$.
Molemmilla on väri $0$ ja polku $1, 2$ on monokromaattinen polku.
Tämän seurauksena solmut $1$ ja $2$ ovat samassa monokromaattisessa komponentissa.

Tarkastele solmuja $1$ ja $3$.
Vaikka molemmilla on väri $0$,
 ne ovat eri monokromaattisissa komponenteissa,
 koska niitä ei yhdistä monokromaattinen polku.

Kaiken kaikkiaan monokromaattisia komponentteja on $3$,
 joihin kuuluvat solmut $\{0\}$, $\{1, 2\}$ ja $\{3\}$.
Siten tämä kutsu palauttaa $3$.

Nyt funktio voi kutsua `perform_experiment` seuraavasti.

```
perform_experiment([0, -1, -1, -1])
```

Tässä kutsussa vain solmu $0$ värjätään uudelleen väriksi $0$,
 mikä johtaa seuraavassa kuvassa näkyvään väritykseen.

![example.png](sphinx_order1.png "230")

Tämä kutsu palauttaa $1$, koska kaikki solmut kuuluvat samaan monokromaattiseen komponenttiin.
Voimme nyt päätellä, että solmujen $1$ , $2$ ja $3$ väri on $0$ .

Funktio voi sitten kutsua `perform_experiment` seuraavasti.

```
perform_experiment([-1, -1, -1, 2])
```

Tässä kutsussa solmu $3$ on värjätty värillä $2$,
 mikä johtaa seuraavassa kuvassa näkyvään väritykseen.

![example.png](sphinx_order2.png "230")

Tämä kutsu palauttaa $2$, koska monokromaattisia komponentteja on $2$,
 joihin kuuluvat solmut $\{0, 3\}$ ja $\{1, 2\}$. 
Voimme päätellä, että solmussa $0$ on väri $2$ .

Funktio `find_colours` palauttaa sitten taulukon $[2, 0, 0, 0]$.
Koska $C = [2, 0, 0, 0]$, annetaan täydet pisteet.

Huomaa, että on myös useita palautusarvoja, joille annettaisiin $50\%$ pisteestä, esimerkiksi $[1, 2, 2, 2]$ tai $[1, 2, 2, 3]$.

## Esimerkki testijärjestelmästä

Syötteen muoto:

```
N  M
C[0]  C[1] ... C[N-1]
X[0]  Y[0]
X[1]  Y[1]
...
X[M-1]  Y[M-1]
```

Tulosteen muoto:

```
L  Q
G[0]  G[1] ... G[L-1]
```

Tässä, $L$ on taulukon $G$ pituus, jonka palauttaa `find_colours`,
 ja $Q$ on funktion `perform_experiment` kutsujen määrä.
