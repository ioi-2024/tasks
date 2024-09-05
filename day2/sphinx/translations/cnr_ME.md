# Zagonetka Sfinge

Velika Sfinga ima zagonetku za vas. Dat vam je graf sa $N$ čvorova. Čvorovi su numerisani od $0$ do $N - 1$. Graf sadrži $M$ grana, numerisanih od $0$ do $M-1$. Svaka grana povezuje par različitih čvorova i  dvosmjerna je. Konkretno, za svaki $j$ od $0$ do $M - 1$ (uključujući) grana $j$ povezuje čvorove $X[j]$ i $Y[j]$. Postoji najviše jedna grana koja povezuje bilo koji par čvorova.
Za dva čvora kažemo da su **susjedni** ako su povezani granom.

Niz čvorova $v_0, v_1, \ldots, v_k$ (za $k \ge 0$) naziva se **put** ako su svaka dva uzastopna čvora $v_l$ i $v_{l+1}$ (za svaki $l$ takav da $0 \le l < k$) susjedni. Kažemo da putanja $v_0, v_1, \ldots, v_k$ povezuje čvorove $v_0$ i $v_k$. U grafu koji vam je dat, svaki par čvorova je povezan nekom putanjom. Za dva čvora kažemo da su **susjedni** ako su povezani granom.

Ovdje je $N + 1$ boja, numerisane od $0$ do $N$. Boja $N$ je posebna i zove se **boja Sfinge**. Svakom čvoru je dodeljena boja. Konkretno, čvor $i$ ($0 \le i < N$) ima boju $C[i]$. Više čvorova može imati istu boju, a može biti boja koja nije dodeljena nijednom čvoru. Nijedan čvor nema boju Sfinge, tj. $0 \le C[i] < N$ ($0 \le i < N$).

Putanja $v_0, v_1, \ldots, v_k$ (za $k \ge 0$) naziva se **monohromatska** ako svi njeni čvorovi imaju istu boju, tj. $C[v_l] = C[v_{l+1}]$ (za svaki $l$ takav da $0 \le l < k$). Pored toga, kažemo da su čvorovi $p$ i $q$ ($0 \le p < N$, $0 \le q < N$) u istoj **monohromatskoj komponenti** ako i samo ako su povezani monohromatskom putanjom.

Znate čvorove i grane, ali ne znate koju boju svaki čvor ima. Želite da saznate boje čvorova izvođenjem **eksperimenata farbanja**.

U eksperimentu farbanja, možete prefarbati proizvoljan broj čvorova. Konkretno, da biste izveli eksperiment farbanja prvo birate niz $E$ veličine $N$, gdje za svaki $i$ ($0 \le i < N$), $E[i]$ je između $-1$ i $N$ **uključujući**.

Zatim, boja svakog čvora $i$ postaje $S[i]$, gdje je vrijednost $S[i]$:

* $C[i]$, tj. originalna boja $i$, ako je $E[i] = -1$, ili
* $E[i]$, inače.

Napomena: Ovo znači da možete koristiti boju Sfinge u vašem farbanju.

Na kraju, Velika Sfinga objavljuje broj monohromatskih komponenti u grafu, nakon što se boja svakog čvora $i$ postavi na $S[i]$ ($0 \le i < N$). Nova boja se primjenjuje samo za ovaj konkretan eksperiment farbanja, tako da se boje svih čvorova vraćaju na originalne nakon što eksperiment završi.

Vaš zadatak je da identifikujete boje čvorova u grafu izvođenjem najviše $2,750$ eksperimenata farbanja. Takođe možete dobiti djelimične bodove ako ispravno odredite za svaki par susjednih čvorova da li imaju istu boju.

## Detalji implementacije

Trebate implementirati sljedeću proceduru.

```
std::vector&lt;int&gt; find_colours(int N,
    std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y)
```
* $N$: broj čvorova u grafu.
* $X$, $Y$: nizovi dužine $M$ koji opisuju grane.
* Ova procedura treba vratiti niz $G$ dužine $N$, koji predstavlja boje čvorova u grafu.
* Ova procedura se poziva tačno jednom za svaki test slučaj.

Gore navedena procedura može pozvati sljedeću proceduru za izvođenje eksperimenata farbanja:

```
int perform_experiment(std::vector&lt;int&gt; E)
```

* $E$: niz dužine $N$ koji specifikuje kako čvorovi treba da budu prefarbani.
* Ova procedura vraća broj monohromatskih komponenti nakon farbanja čvorova prema $E$.
* Ova procedura može biti pozvana najviše $2,750$ puta.

Grejder je neadaptivan, tj. boje čvorova su fiksne prije nego što se pozove `find_colours`.

## Ograničenja

* $2 \le N \le 250$
* $N - 1 \le M \le \frac{N \cdot (N - 1)}{2}$
* $0 \le X[j] < Y[j] < N$ za svaki $j$ takav da $0 \le j < M$.
* $X[j] \neq X[k]$ ili $Y[j] \neq Y[k]$ za svaki $j$ i $k$ takav da $0 \le j < k < M$.
* Svaki par čvorova je povezan nekom putanjom.
* $0 \le C[i] < N$ za svaki $i$ takav da $0 \le i < N$.

## Podzadaci

| Podzadatak | Bodovi  | Dodatna ograničenja |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = 2$
| 2       | $7$    | $N \le 50$
| 3       | $33$   | Graf je putanja: $M = N - 1$ i čvorovi $j$ i $j+1$ su susjedi ($0 \leq j < M$).
| 4       | $21$   | Graf je potpun: $M = \frac{N \cdot (N - 1)}{2}$ i svaki par čvorova je povezan.
| 5       | $36$   | Nema dodatnih ograničenja

U svakom podzadatku možete dobiti djelimične bodove ako vaš program ispravno odredi za svaki par susjednih čvorova imaju li istu boju.

Tačnije, dobijate cijeli broj bodova za podzadatak ako u svim njegovim test slučajevima, niz $G$ koji vraća `find_colours` je tačno isti kao niz $C$ (tj. $G[i] = C[i]$ za sve $i$ takve da $0 \le i < N$). U suprotnom, dobijate $50%$ bodova za podzadatak ako su ispunjeni sljedeći uslovii u svim njegovim test slučajevima:

$0 \le G[i] < N$ za svaki $i$ takav da $0 \le i < N$;
Za svaki $j$ takav da $0 \le j < M$:
$G[X[j]] = G[Y[j]]$ ako i samo ako $C[X[j]] = C[Y[j]]$.

## Primjer

Razmotri sljedeći poziv.

```
find_colours(4, [0, 1, 0, 0], [1, 2, 2, 3])
```
Za ovaj primjer, pretpostavimo da su (skrivene) boje čvorova dane s $C = [2, 0, 0, 0]$. Ova situacija je prikazana na sljedećoj slici. Boje su dodatno predstavljene brojevima na bijelim oznakama pričvršćenim za svaki čvor.

![example.png](sphinx_example.png "230")

Procedura može pozvati `perform_experiment` na sljedeći način:

```
perform_experiment([-1, -1, -1, -1])
```

U ovom pozivu, nijedan čvor ne mijenja boju, jer svi čvorovi zadržavaju svoje originalne boje.

Razmotrimo čvorove $1$ i $2$. Oba čvora imaju boju $0$ i putanja $1, 2$ je monochromatska putanja. Kao rezultat, čvorovi $1$ i $2$ su u istoj monohromatskoj komponenti.

Razmotrimo čvorove $1$ i $3$. Iako oba imaju boju $0$, oni su u različitim monochromatskim komponentama jer ne postoji monochromatska putanja koja ih povezuje.

Ukupno, postoje $3$ monochromatske komponente: sa čvorovima $\{0\}$, $\{1, 2\}$, i $\{3\}$. Dakle, ovaj poziv vraća $3$.


Sada procedura može pozvati `perform_experiment` na sljedeći način:

```
perform_experiment([0, -1, -1, -1])
```
U ovom pozivu, samo čvor $0$ mijenja boju u boju $0$, što rezultira bojenjem prikazanim na sljedećoj slici.

![example.png](sphinx_order1.png "230")

Ovaj poziv vraća $1$, pošto svi čvorovi pripadaju istoj jednobojnoj komponenti.
Možemo sada zaključiti da čvorovi $1$, $2$ i $3$ imaju boju $0$.

Procedura može nakon toga pozvati `perform_experiment` na sljedeći način:

```
perform_experiment([-1, -1, -1, 2])
```

U ovom pozivu čvoru $3$ je promjenjena boja na boju $2$,
 što vodi do situacije prikazane na sljedećoj slici:

![example.png](sphinx_order2.png "230")

Ovaj poziv vraća $2$, pošto postoje $2$ jednobojne komponente,
 sa čvorovima $\{0, 3\}$ i $\{1, 2\}$. 
Možemo zaključiti da čvor $0$ ima boju $2$.

Procedura `find_colours` vraća niz $[2, 0, 0, 0]$.
Pošto $C = [2, 0, 0, 0]$, puni bodovi su dodjeljeni.

Napominjemo da postoji više povratnih vrijednosti za koje bi se dodijelilo $50\%$ bodova, na primjer $[1, 2, 2, 2]$ ili $[1, 2, 2, 3]$.

## Grejder

Format ulaza:

```
N  M
C[0]  C[1] ... C[N-1]
X[0]  Y[0]
X[1]  Y[1]
...
X[M-1]  Y[M-1]
```

Format izlaza:

```
L  Q
G[0]  G[1] ... G[L-1]
```

Ovdje, $L$ je dužina niza $G$ koju vrati `find_colours`,
 i $Q$ je broj poziva procedure `perform_experiment`.



