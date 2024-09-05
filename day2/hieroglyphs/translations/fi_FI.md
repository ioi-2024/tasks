# Hieroglyfit

Tutkijaryhmä tutkii hieroglyfijonojen välisiä yhtäläisyyksiä.
He kuvaavat jokaista hieroglyfiä ei-negatiivisella kokonaisluvulla.
Suorittaakseen tutkimuksensa he käyttävät seuraavia käsitteitä jonoista.

Määrätylle jonolle $A$,
 jonoa $S$ kutsutaan $A$:n **alijonoksi**,
 jos ja vain jos $S$ voidaan saada
 poistamalla joitakin alkioita (mahdollisesti ei yhtään) $A$:sta.

Alla olevassa taulukossa on esimerkkejä jonon $A = [3, 2, 1, 2]$ alijonoista.

| Jono | Kuinka sen saa $A$:sta |
|----------------|--------------------------------- -|
| [3, 2, 1, 2] | Alkioita ei poisteta.
| [2, 1, 2] | [<s>3</s>, 2, 1, 2]
| [3, 2, 2] | [3, 2, <s>1</s>, 2]
| [3, 2] | [3, <s>2</s>, <s>1</s>, 2] tai [3, 2, <s>1</s>, <s>2</s>]
| [3] | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ] | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Toisaalta $[3, 3]$ tai $[1, 3]$ eivät ole $A$:n alijonoja.

Tarkastellaan kahta hieroglyfijonoa, $A$ ja $B$.
Jonoa $S$ kutsutaan $A$ ja $B$:n **yhteiseksi alijonoksi**,
 jos ja vain jos $S$ on sekä $A$ että $B$ alijono.
Lisäksi sanomme, että jono $U$ on $A$ ja $B$ **yleinen yhteinen alijono**,
 jos ja vain jos seuraavat kaksi ehtoa täyttyvät:
* $U$ on $A$:n ja $B$:n yhteinen alijono.
* Jokainen $A$:n ja $B$:n yhteinen alijono on myös $U$:n alijono.

Voidaan osoittaa, että millä tahansa alijonolla $A$ ja $B$
 on enintään yksi yleinen yhteinen alijono.

Tutkijat ovat löytäneet kaksi hieroglyfijonoa $A$ ja $B$.
Jono $A$ koostuu $N$ hieroglyfistä
 ja jono $B$ koostuu $M$ hieroglyfistä.
Auta tutkijoita laskemaan
 jonojen $A$ ja $B$ yleinen yhteinen alijono,
 tai määrittämään, että tällaista jonoa ei ole olemassa.

## Toteutuksen yksityiskohdat

Sinun tulee toteuttaa seuraava funktio.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: $N$:n alkion pituinen taulukko, joka kuvaa ensimmäistä jonoa.
* $B$: $M$:n alkion pituinen taulukko, joka kuvaa toista jonoa.
* Jos $A$:lle ja $B$:lle on olemassa yleinen yhteinen alijono,
   funktion tulee palauttaa taulukko, joka sisältää tämän jonon.
  Muussa tapauksessa funktion tulee palauttaa $[-1]$
   (taulukko, jonka pituus on $1$ ja ainoa elementti on $-1$).
* Tätä funktiota kutsutaan täsmälleen kerran jokaisessa testitapauksessa.

## Rajat

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ kaikilla $i$ siten, että  $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ kaikilla $j$ siten, että $0 \leq j < M$

## Osatehtävät

| Osatehtävä | Pisteet  | Lisäehdot |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; jokainen $A$ ja $B$ sisältää $N$ **uniikkia** kokonaislukua väliltä $0$ ja $N-1$ (inklusiivinen)
| 2       | $15$   | Kaikilla $k$, ($A$:n alkioiden määrä, jotka ovat yhtä suuria kuin $k$) plus ($B$:n alkioiden määrä, jotka ovat yhtä suuria kuin $k$) on korkeintaan $3$. 
| 3       | $10$   | $A[i] \leq 1$ kaikilla $i$ siten, että $0 \leq i < N$; $B[j] \leq 1$ kaikilla $j$ siten, että $0 \leq j < M$
| 4       | $16$   | On olemassa yleinen yhteinen alijono $A$:n ja $B$:n välillä.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | Ei lisäehtoja.

## Esimerkit

### Esimerkki 1

Tarkastellaan seuraavaa kutsua.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Tässä $A$:n ja $B$:n yleiset alijonot ovat seuraavat:
 $[\ ]$, $[0]$, $[1]$, $[2]$ $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$ $[0, 0, 2]$ $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ ja $[0, 1, 0, 2]$.

Koska $[0, 1, 0, 2]$ on $A$:n ja $B$:n yleinen alijono, ja
 kaikki yleiset $A$:n ja $B$:n alijonot ovat $[0, 1, 0, 2]$:n alijonoja,
 funktion tulee palauttaa $[0, 1, 0, 2]$.

### Esimerkki 2

Tarkastellaan seuraavaa kutsua.

```
ucs([0, 0, 2], [1, 1])
```

Tässä ainoa yhteinen alijono $A$:n ja $B$:n on tyhjä alijono $[\ ]$.
Tästä seuraa, että funktion tulee palauttaa tyhjä taulukko $[\ ]$.

### Esimerkki 3

Tarkastellaan seuraavaa kutsua.
```
ucs([0, 1, 0], [1, 0, 1])
```

Tässä $A$:n ja $B$:n yhteiset alijonot ovat
 $[\ ], [0], [1], [0, 1]$ ja $[1, 0]$.
Voidaan osoittaa, että yleistä yhteistä alijonoa ei ole olemassa.
Siksi funktion tulee palauttaa $[-1]$.

## Esimerkki testijärjestelmästä

Syötteen muoto:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Tulosteen muoto:

```
T
R[0]  R[1]  ...  R[T-1]
```

Tässä $R$ on funktion `ucs` palauttama taulukko ja $T$ on sen pituus.
