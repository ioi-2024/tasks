# Puu

Tarkastellaan **puuta**, joka koostuu $N$ **solmusta**,
jotka ovat numeroitu $0$:sta $N-1$ asti.
Solmua $0$ kutsutaan **juureksi**.
Jokaisella solmilla, paitsi juurella, on yksi **vanhempi**.
Jokaista $i$ kohden siten, että $1 \leq i < N$,
 solmun $i$ vanhempi on solmu $P[i]$, missä $P[i] < i$.
Oletetaan myös, että $P[0] = -1$.

Jokaiselle solmulle $i$ ($0 \leq i < N$),
 $i$ :n **alipuu** on seuraavien solmujen joukko:
 * $i$ ja
 * mikä tahansa solmu, jonka vanhempi on $i$, ja
 * mikä tahansa solmu, jonka vanhemman vanhempi on $i$, ja
 * mikä tahansa solmu, jonka vanhemman vanhemman vanhempi on $i$, ja
 * jne.

Alla olevassa kuvassa on esimerkkipuu, joka koostuu $N = 6$ solmuista.
Jokainen nuoli yhdistää solmun vanhempaansa,
 paitsi juuren, jolla ei ole vanhempaa.
Solmun $2$ alipuu sisältää solmut $2, 3, 4$ ja $5$.
Solmun $0$ alipuu sisältää kaikki puun $6$ solmua
 ja solmun $4$ alipuu sisältää vain solmun $4$.

![](subtrees.png "150")

Jokaiselle solmulle on määritetty ei-negatiivinen kokonaisluku **paino**.
Merkitään solmun $i$ ($0 \leq i < N$) painoarvo $W[i]$.

Sinun tehtäväsi on kirjoittaa ohjelma, joka vastaa $Q$ kyselyyn,
joista kukin määritellään parilla positiivisia kokonaislukuja $(L, R)$.
Vastaus kyselyyn tulee laskea seuraavasti.

Määritä kokonaisluku **kerroin** jokaiselle puun solmulle.
Tätä kuvaa jono $C[0], \ldots, C[N-1]$,
 jossa $C[i]$ ($0 \leq i < N$) on kerroin, joka on määritetty solmuun $i$.
Kutsutaan tätä jonoa **kerroinjonoksi**.
Huomaa, että kerroinjonon alkiot voivat olla negatiivisia, $0$ tai positiivisia.

Kyselylle $(L, R)$,
 kerroinjonoa kutsutaan **sallituksi**,
 jos jokaiselle solmulle $i$ ($0 \leq i < N$),
 pätee seuraava ehto:
 solmun $i$ alipuun solmujen kertoimien summa
 on vähintään $L$ eikä suurempi kuin $R$.

Tietylle kerroinjonolle $C[0], \ldots, C[N-1]$,
 solmun $i$ **kustannus** on $|C[i]| \cdot W[i]$,
 jossa $|C[i]|$ tarkoittaa $C[i]$:n itseisarvoa.
Lopuksi **kokonaiskustannus** on kaikkien solmujen kustannusten summa.
Sinun tehtäväsi on laskea jokaiselle kyselylle
 **minimikokonaiskustannus**, joka voidaan saavuttaa jollakin sallitulla kerroinjonolla.

Voidaan osoittaa, että mille tahansa kyselylle on olemassa vähintään yksi sallittu kerroinjono.


## Toteutuksen yksityiskohdat

Sinun tulee toteuttaa seuraavat kaksi funktiota:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$: kokonaislukutaulukot, joiden pituus on $N$:
   vanhemmat ja painot.
* Tätä funktiota kutsutaan täsmälleen kerran
   testijärjestelmän ja ohjelmasi välisen vuorovaikutuksen alussa kussakin testitapauksessa.

```
long long query(int L, int R)
```
* $L$, $R$: kyselyä kuvaavat kokonaisluvut.
* Tätä funktiota kutsutaan $Q$ kertaa `init` kutsun jälkeen kussakin testitapauksessa.
* Tämän funktion pitäisi palauttaa vastaus annettuun kyselyyn.


## Rajoitukset

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ kaikilla $i$ siten, että $1 \leq i < N$
* $0 \leq W[i] \leq 1\,000\,000$ kaikilla $i$ siten, että $0 \leq i < N$
* $1 \leq L \leq R \leq 1\,000\,000$ kaikissa kyselyissä

## Osatehtävät

| Osatehtävä | Pisteet  | Lisäehdot |
| :-----: | :----: | ---------------------- |
|   1     |  $10$  | $Q \leq 10$; $W[P[i]] \leq W[i]$ kaikilla $i$ siten, että $1 \leq i < N$
|   2     |  $13$  | $Q \leq 10$; $N \leq 2\,000$
|   3     |  $18$  | $Q \leq 10$; $N \leq 60\,000$
|   4     |  $7$   | $W[i] = 1$ kaikilla $i$ siten, että $0 \leq i < N$
|   5     |  $11$  | $W[i] \leq 1$ kaikilla $i$ siten, että $0 \leq i < N$
|   6     |  $22$  | $L = 1$
|   7     |  $19$  | Ei lisäehtoja.



## Esimerkit

Tarkastellaan seuraavia kutsuja:

```
init([-1, 0, 0], [1, 1, 1])
```
Puu koostuu $3$ solmusta: juuresta ja sen $2$:sta lapsesta.
Kaikkien solmujen painot ovat $1$ .

```
query(1, 1)
```

Tässä kyselyssä $L = R = 1$,
 mikä tarkoittaa sitä, että kertoimien summan jokaisessa alipuussa on oltava $1$.
Tarkastellaan kerroinjonoa $[-1, 1, 1]$.
Puu ja vastaavat kertoimet (tummennetuissa suorakulmioissa) on kuvattu alla.

![](ex1.png "150")

Jokaiselle solmulle $i$ ( $0 \leq i < 3$ ) kaikkien solmujen kertoimien summa alipuussa
 $i$ on yhtä suuri kuin $1$. 
Näin ollen tämä kerroinjono on sallittu.
Kokonaiskustannukset lasketaan seuraavasti:


| Solmu | Paino | Kerroin | Kustannukset |
| :----: | :----: | :---------: | :------------------------: |
| 0 | 1 | -1 | $\mid -1 \mid \cdot 1 = 1$
| 1 | 1 | 1 | $\mid 1 \mid \cdot 1 = 1$
| 2 | 1 | 1 | $\mid 1 \mid \cdot 1 = 1$

Siis kokonaiskustannus on $3$.
Tämä on ainoa sallittu kerroinjono,
 minkä vuoksi tämän funktion pitäisi palauttaa $3$.

```
query(1, 2)
```
Tämän kyselyn vähimmäishinta on $2$,
 ja se saavutetaan, kun kerroinjono on $[0, 1, 1]$.
## Esimerkki testijärjestelmästä

Syötteen muoto:

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

jossa $L[j]$ ja $R[j]$
 (kaikilla $0 \leq j < Q$)
on $j$:nnen `query`:n kutsun syöte.
Huomaa, että syötteen toisella rivillä on **vain $N-1$ kokonaislukua**,
 koska testijärjestelmä ei lue $P[0]$:n arvoa.

Tulosteen muoto:
```
A[0]
A[1]
...
A[Q-1]
```

jossa $A[j]$
 (kaikilla $0 \leq j < Q$)
on $j$:nnen `query`:n kutsun palauttama arvo.
