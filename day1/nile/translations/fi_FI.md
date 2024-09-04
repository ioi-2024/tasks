# Niili

Haluat kuljettaa $N$ esinettä Niilin läpi. 
Artefaktit on numeroitu $0$:sta $N-1$ asti.
Artefaktin $i$ ($0 \leq i < N$) paino on $W[i]$.

Kuljetat esineitä käyttämällä erikoisveneitä.
Jokainen vene voi kuljettaa **korkeintaan kaksi** esinettä.

* Jos haluat laittaa yhden esineen veneeseen, artefaktin paino voi olla kuinka suuri tahansa.
* Jos haluat laittaa kaksi esinettä samaan veneeseen, sinun on varmistettava, että vene on tasapainossa.
Tarkemmin sanottuna voit lähettää
 artefaktit $p$ ja $q$ ($0 \leq p < q < N$) samassa veneessä
 vain, jos niiden painojen absoluuttinen ero on enintään $D$,
 eli $|W[p] - W[q]| \leq D$.

Artefaktin kuljettamisesta on maksettava kulu, 
joka riippuu samassa veneessä kuljetettavien esineiden määrästä.
Artefaktin $i$ ($0 \leq i < N$) kuljetuskustannukset ovat:

* $A[i]$, jos laitat artefaktin omaan veneeseensä tai
* $B[i]$, jos laitat sen veneeseen yhdessä jonkin muun esineen kanssa.

Huomaa, että jälkimmäisessä tapauksessa sinun on maksettava kuljetuskustannukset molemmista veneessä olevista esineistä.
Erityisesti, jos päätät lähettää
 artefaktit $p$ ja $q$ ($0 \leq p < q < N$) samassa veneessä,
 sinun on maksettava $B[p] + B[q]$.

Artefaktin lähettäminen yksin veneessä on aina kalliimpaa 
kuin lähettää se jonkun muun esineen kanssa, samassa veneessä,
joten $B[i] < A[i]$ kaikille $i$:lle siten, että $0 \leq i < N$.

Valitettavasti joki on hyvin arvaamaton ja $D$:n arvo vaihtelee usein.
Sinun tehtäväsi on vastata $Q$ kysymykseen, jotka on numeroitu $0$:sta $Q-1$ asti.
Kysymykset on annettu taulukossa $E$ jonka pituus on $Q$.
Vastaus kysymykseen $j$ ($0 \leq j < Q$) on
 vähimmäiskokonaiskustannukset kaikkien $N$ esineiden kuljettamisesta,
 kun $D$ n arvo on yhtä suuri kuin $E[j]$ .

## Toteutuksen yksityiskohdat

Sinun tulee toteuttaa seuraava funktio.

```
std::vector&lt;long long&gt; calculate_costs(
    std::vector&lt;int&gt; W, std::vector&lt;int&gt; A, 
    std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```

* $W$, $A$, $B$: taulukot, joiden pituus on $N$, jotka kuvaavat esineiden painoja ja niiden kuljetuskustannuksia.
* $E$: taulukko, jonka pituus on $Q$, joka kuvaa $D$:n arvot.
* Tämän funktion tulee palauttaa $Q$ kokonaislukua sisältävä taulukko $R$, joka
   sisältää vähimmäiskokonaiskustannukset esineiden kuljetuksesta,
   missä $R[j]$ sisältää kustannukset, kun $D$:n arvo on $E[j]$ (jokaiselle $j$
   siten, että $0 \leq j < Q$).
* Tätä funktiota kutsutaan tarkalleen kerran jokaisessa testitapauksessa.

## Rajat

* $1 \leq N \leq 100\,000$
* $1 \leq Q \leq 100\,000$
* $1 \leq W[i] \leq 10^{9}$
   jokaisella $i$, missä $0 \leq i < N$
* $1 \leq B[i] < A[i] \leq 10^{9}$
   jokaisella $i$, missä $0 \leq i < N$
* $1 \leq E[j] \leq 10^{9}$
   jokaisella $j$, missä $0 \leq j < Q$

## Osatehtävät

| Osatehtävä | Pisteet  | Lisärajoitukset |
| :-----: | :----: | ---------------------- |
| 1       | $6$    | $Q \leq 5$; $N \leq 2000$; $W[i] = 1$ jokaisella $i$, missä $0 \leq i < N$
| 2       | $13$   | $Q \leq 5$; $W[i] = i+1$ jokaisella $i$, missä $0 \leq i < N$
| 3       | $17$   | $Q \leq 5$; $A[i] = 2$ ja $B[i] = 1$ jokaisella $i$, missä $0 \leq i < N$
| 4       | $11$   | $Q \leq 5$; $N \leq 2000$
| 5       | $20$   | $Q \leq 5$
| 6       | $15$   | $A[i] = 2$ ja $B[i] = 1$ jokaisella $i$, missä $0 \leq i < N$
| 7       | $18$   | Ei lisärajoituksia.

## Esimerkki

Tarkastellaan seuraavaa funktiokutsua.

```
calculate_costs([15, 12, 2, 10, 21],
                [5, 4, 5, 6, 3],
                [1, 2, 2, 3, 2],
                [5, 9, 1])
```

Tässä esimerkissä meillä on $N = 5$ artefaktia ja $Q = 3$ kysymystä.

Ensimmäisessä kysymyksessä $D = 5$.
Voit lähettää esineet $0$ ja $3$ yhdessä veneessä ($|15 - 10| \leq 5$) ja loput artefaktit erillisissä veneissä.
Tämä minimoi kaikkien esineiden kuljetuskustannukset, jotka ovat $1+4+5+3+3 = 16$.

Toisessa kysymyksessä $D = 9$.
Voit lähettää esineet $0$ ja $1$ yhdessä veneessä ($|15 - 12| \leq 9$ ) ja lähettää esineet $2$ ja $3$ yhdessä veneessä ($|2 - 10| \leq 9$ ).
Loput esineet voidaan lähettää erillisessä veneessä.
Tämä minimoi kaikkien esineiden kuljetuskustannukset, jotka ovat $1+2+2+3+3 = 11$ .

Viimeisessä kysymyksessä $D = 1$ . Sinun on lähetettävä jokainen artefakti omassa veneessään.
Tämä minimoi kaikkien esineiden kuljetuskustannukset, jotka ovat $5+4+5+6+3 = 23$ .

Tästä syystä tämän funktion tulee palauttaa $[16, 11, 23]$ .


## Esimerkki testijärjestelmästä

Syötteen muoto:

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

Tulosteen muoto:

```
R[0]
R[1]
...
R[S-1]
```

Tässä $S$ kuvaa taulukon $R$ pituutta, jonka  `calculate_costs` palauttaa.