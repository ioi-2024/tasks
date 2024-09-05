# Hijeroglifi

Tim istraživača u Visokom proučava sličnosti između nizova hijeroglifa iz doba faraona Ramiza II. Svaki hijeroglif predstavljaju nenegativnim cijelim brojem. Za izvođenje svog istraživanja koriste sljedeće pojmove o nizovima.

Za fiksni niz $A$, niz $S$ se naziva podniz niza $A$ ako i samo ako (akko) se $S$ može dobiti uklanjanjem nekih elemenata (potencijalno nijednog) iz niza $A$.

Tabela ispod prikazuje neke primjere podnizova niza $A = [3, 2, 1, 2]$.

| Podniz    | Kako se može dobiti iz $A$|
|----------------|---------------------------------|
| [3, 2, 1, 2] | Nijedan element nije uklonjen.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] ili [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

S druge strane, $[3, 3]$ ili $[1, 3]$ nisu podnizovi niza $A$.

Razmotrite dva niza hijeroglifa, $A$ i $B$. Niz $S$ se naziva **zajednički podniz** niza $A$ i $B$ ako i samo ako je $S$ podniz i niza $A$ i niza $B$. Nadalje, kažemo da je niz $U$ **univerzalni zajednički podniz** nizova $A$ i $B$ ako i samo ako su ispunjena sljedeća dva uslova:

* $U$ je zajednički podniz nizova $A$ i $B$.
* Svaki zajednički podniz nizova $A$ i $B$ je također podniz niza $U$.

Može se pokazati da bilo koja dva niza $A$ i $B$ imaju najviše jedan univerzalni zajednički podniz.

Istraživači su pronašli dva niza hijeroglifa $A$ i $B$. Niz $A$ se sastoji od $N$ hijeroglifa, a niz $B$ se sastoji od $M$ hijeroglifa. Pomozite istraživačima da izračunaju univerzalni zajednički podniz nizova $A$ i $B$, ili da utvrde da takav niz ne postoji.

## Detalji implementacije

Potrebno je implementirati sljedeću proceduru.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: niz dužine $N$ koji opisuje prvi niz.
* $B$: niz dužine $M$ koji opisuje drugi niz.
* Ako postoji univerzalni zajednički podniz nizova $A$ i $B$, procedura treba vratiti niz koji sadrži ovaj podniz. U suprotnom, procedura treba vratiti $[-1]$ (niz dužine $1$, čiji je jedini element $-1$).
* Ova procedura se poziva tačno jednom za svaki testni slučaj.

## Ograničenja

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ za svaki $i$ takav da $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ za svaki $j$ takav da $0 \leq j < M$

## Podzadaci

| Podzadatak | Bodovi  | Dodatna ograničenja |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; Nizovi $A$ i $B$ se sastoje od $N$ **različitih** cijelih brojeva između $0$ i $N-1$ (uključujući oba)
| 2       | $15$   | Za bilo koji cijeli broj $k$ vrijedi: (zbir broja elemenata $A$ jednakih $k$) plus (broj elemenata $B$ jednakih $k$) je najviše $3$.
| 3       | $10$   | $A[i] \leq 1$ za svaki $i$ takav da $0 \leq i < N$; $B[j] \leq 1$ za svaki $j$ takav da $0 \leq j < M$
| 4       | $16$   | Postoji univerzalni zajednički podniz nizova $A$ i $B$.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | Nema dodatnih ograničenja.


## Primjeri

### Primjer 1

Razmotrite sljedeći poziv.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Ovdje su zajednički podnizovi niza $A$ i $B$ sljedeći:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ i $[0, 1, 0, 2]$.
 
Budući da je $[0, 1, 0, 2]$ zajednički podniz nizova $A$ i $B$, i svi zajednički podnizovi $A$ i $B$ su podnizovi $[0, 1, 0, 2]$, procedura treba vratiti $[0, 1, 0, 2]$.

### Primjer 2

Razmotrite sljedeći poziv.

```
ucs([0, 0, 2], [1, 1])
```

Ovdje je jedini zajednički podniz nizova $A$ i $B$ prazni niz $[\ ]$. Iz toga slijedi da procedura treba vratiti prazan niz $[\ ]$.

### Primjer 3

Razmotri sljedeći poziv.

```
ucs([0, 1, 0], [1, 0, 1])
```
Ovdje su zajednički podnizovi nizova $A$ i $B$: $[\ ], [0], [1], [0, 1]$ i $[1, 0]$. Može se pokazati da univerzalni zajednički podniz ne postoji. Stoga, procedura treba vratiti $[-1]$.

## Grader

Ulazni format:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Izlazni format:

```
T
R[0]  R[1]  ...  R[T-1]
```

Ovdje je $R$ niz koji vraća `ucs`, a $T$ je njegova dužina.