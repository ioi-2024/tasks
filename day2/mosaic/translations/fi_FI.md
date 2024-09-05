# Mosaiikki

Salma aikoo värittää seinälle savimosaiikin.
Mosaiikki on $N \times N$ ruudukko,
 valmistettu $N^2$ alunperin värittömistä $1 \times 1$ neliölaatoista.
Mosaiikin rivit on numeroitu $0$:sta $N-1$ asti ylhäältä alas,
 ja sarakkeet on numeroitu $0$:sta $N-1$ asti vasemmalta oikealle.
Laatta rivillä $i$ ja sarakkeessa $j$ ($0 \leq i < N$ , $0 \leq j < N$) on merkitty $(i,j)$.
Jokainen laatta on joko väritettävä
 valkoiseksi (merkitty $0$) tai mustaksi (merkitty $1$).

Mosaiikin väritystä varten Salma valitsee ensin kaksi taulukkoa $X$ ja $Y$, joiden pituus on $N$ ja jotka koostuvat arvoista $0$ ja $1$ siten, että $X[0] = Y[0]$.
Hän värittää ylimmän rivin (rivi $0$) laatat taulukon $X$ mukaan,
 siten, että ruudun $(0,j)$ väri on $X[j]$ ($0 \leq j < N$).
Hän värittää myös vasemmanpuoleisimman sarakkeen (sarake $0$) laatat taulukon $Y$ mukaan,
 siten, että ruudun $(i,0)$ väri on $Y[i]$ ($0 \leq i < N$).

Sitten hän toistaa seuraavat vaiheet, kunnes kaikki laatat on väritetty:
* Hän löytää minkä tahansa *värittömän* laatan $(i,j)$, jonka
 ylempi ruutu (ruutu $(i-1, j)$) ja vasemmanpuoleinen ruutu (ruutu $(i, j-1)$)
 ovat molemmat *jo värillisiä*.
* Sitten hän värjää ruudun $(i,j)$ mustaksi, jos molemmat näistä ruuduista ovat valkoisia;
 muuten hän värjää ruudun $(i, j)$ valkoiseksi.

Voidaan osoittaa, että laattojen lopulliset värit eivät riipu 
siitä järjestyksestä, jossa Salma ne värjää.
 
Yasmin on erittäin utelias mosaiikin laattojen väreistä.
Hän kysyy Salmalta $Q$ kysymyksiä, numeroitu $0$:sta $Q-1$ asti.
Kysymyksessä $k$ ($0 \leq k < Q$),
 Yasmin määrittää mosaiikin osasuorakulmion seuraavasti:
* Ylin rivi $T[k]$ ja alin rivi $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* Vasen sarake $L[k]$ ja oikea sarake $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

Vastaus kysymykseen on mustien laattojen määrä tässä osasuorakulmiossa.
Tarkemmin sanottuna Salman pitäisi selvittää kuinka monta laattaa $(i, j)$ on olemassa,
 siten, että $T[k] \leq i \leq B[k]$ , $L[k] \leq j \leq R[k]$ ,
 ja laatan $(i,j)$ väri on musta.

Kirjoita ohjelma, joka vastaa Yasminin kysymyksiin.
## Toteutuksen yksityiskohdat

Sinun tulee toteuttaa seuraava funktio.

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: $N$:n pituisia taulukoita, jotka kuvaavat laattojen värejä
 ylimmällä rivillä ja vasemmanpuoleisimmassa sarakkeessa.
* $T$, $B$, $L$, $R$: $Q$:n pituiset taulukot, jotka kuvaavat Yasminin esittämiä kysymyksiä.
* Funktion tulee palauttaa taulukko $C$ jonka pituus on $Q$,
 siten, että $C[k]$ antaa vastauksen kysymykseen $k$ ($0 \leq k < Q$).
* Tätä funktiota kutsutaan täsmälleen kerran jokaisessa testitapauksessa.

## Rajat

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ ja $Y[i] \in \{0, 1\}$
 kaikilla $i$ siten, että $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ ja $0 \leq L[k] \leq R[k] < N$
 kaikilla $k$ siten, että $0 \leq k < Q$

## Osatehtävät

| Osatehtävä | Pisteet  | Lisäehdot |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ (kaikilla $k$ siten, että $0 \leq k < Q$)
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ (kaikilla $i$ siten, että $0 \leq i < N$)
| 6       | $22$   | $T[k] = B[k]$ ja $L[k] = R[k]$ (kaikilla $k$ siten, että $0 \leq k < Q$)
| 7       | $19$   | $T[k] = B[k]$ (kaikilla $k$ siten, että $0 \leq k < Q$)
| 8       | $22$   | Ei lisäehtoja.

## Esimerkki

Tarkastellaan seuraavaa kutsua.

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Tämä esimerkki on havainnollistettu alla olevissa kuvissa.
Vasemmassa kuvassa näkyy mosaiikin laattojen värit.
Keskimmäisessä ja oikeanpuoleisessa kuvassa näkyy osasuorakulmiot, jotka
 Yasmin kysyi ensimmäisessä ja toisessa kyselyssä.

![](example.png "550")

Vastaus näihin kysymyksiin
 (eli ykkösten lukumäärät varjostetuissa suorakulmioissa)
 ovat 7 ja 3 vastaavasti.
Täten funktion tulisi palauttaa $[7, 3]$.

## Esimerkki testijärjestelmästä

Syötteen muoto:

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

Tulosteen muoto:

```
C[0]
C[1]
...
C[S-1]
```

Tässä, $S$ on taulukon $C$ pituus, jonka `mosaic` palautti.
