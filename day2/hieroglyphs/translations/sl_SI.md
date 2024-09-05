# Hieroglifi

Raziskovalci preučujejo podobnosti med zaporedji hieroglifov.
Vsakemu hieroglifu dodelijo nenegativno celo število.
Za svoje raziskave uporabljajo naslednje načelo.

Za fiksno zaporedje $A$,
 zaporedje $S$ imenujemo **podzaporedje** zaporedja $A$,
 če in samo če se $S$ lahko dobi
 tako, da iz $A$ odstranimo nekaj elementov (morda nobenega).

Spodnja tabela navaja nekaj primerov podzaporedij zaporedja $A = [3, 2, 1, 2]$.

| Podzaporedje    | Kako ga dobimo iz $A$ |
|----------------|---------------------------------|
| [3, 2, 1, 2] | Noben element ni odstranjen.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] ali [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Po drugi strani, $[3, 3]$ in $[1, 3]$ nista podzaporedji $A$.

Razmislimo o zaporedjih hieroglifov, $A$ in $B$.
Zaporedje $S$ imenujemo **skupno podzaporedje** $A$ in $B$,
 če in samo če je $S$ podzaporedje tako $A$ kot $B$.
Poleg tega rečemo, da je zaporedje $U$ **univerzalno skupno podzaporedje** $A$ in $B$,
 če in samo če sta izpolnjena naslednja pogoja:
* $U$ je skupno podzaporedje $A$ in $B$.
* Vsako skupno podzaporedje $A$ in $B$ je tudi podzaporedje $U$.

Pokažemo lahko, da imata katerikoli zaporedji $A$ in $B$
 največ eno univerzalno skupno podzaporedje.

Raziskovalci so našli zaporedji hieroglifov $A$ in $B$.
Zaporedje $A$ se sestoji iz $N$ hieroglifov
 in zaporedje $B$ iz $M$ hieroglifov.
Pomagajte raziskovalcem ugotoviti,
 katero je univerzalno skupno podzaporedje zaporedij $A$ in $B$,
 oziroma ugotovite, da takšno zaporedje ne obstaja.

## Podrobnosti implementacije

Implementirati morate naslednjo funkcijo:

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: polje dolžine $N$, ki opisuje prvo zaporedje.
* $B$: polje dolžine $M$, ki opisuje drugo zaporedje.
* Če obstaja univerzalno skupno podzaporedje $A$ in $B$,
   mora funkcija vrniti polje, ki vsebuje to zaporedje.
  V nasprotnem primeru mora funkcija vrniti $[-1]$
   (polje dolžine $1$, katerega edini element je $-1$).
* Funkcija se kliče natanko enkrat za vsak testni primer.

## Omejitve

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ za vsak $i$ velja $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ za vsak $j$ velja $0 \leq j < M$

## Podnaloge

| Podnaloga | Točke  | Dodatne omejitve |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; $A$ in $B$ vsebujeta $N$ **različnih** celih števil med $0$ in $N-1$ (vključno)
| 2       | $15$   | Za katerokoli celo število $k$ je seštevek pojavnosti $k$ v $A$ in $B$ največ $3$.
| 3       | $10$   | $A[i] \leq 1$ za vsak $i$ velja $0 \leq i < N$; $B[j] \leq 1$ za vsak $j$ velja $0 \leq j < M$
| 4       | $16$   | Obstaja univerzalno skupno podzaporedje $A$ in $B$.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | Ni dodatnih omejitev.


## Primeri

### 1. primer 

Razmislimo o naslednjem klicu.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Tukaj so skupna podzaporedja $A$ in $B$ naslednja:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ in $[0, 1, 0, 2]$.

Ker je $[0, 1, 0, 2]$ skupno podzaporedje $A$ in $B$, in
 ker so vsa skupna podzaporedja $A$ in $B$ tudi podzaporedja $[0, 1, 0, 2]$,
 funkcija vrne $[0, 1, 0, 2]$.

### 2. primer

Razmislimo o naslednjem klicu.

```
ucs([0, 0, 2], [1, 1])
```

Tukaj je edino skupno podzaporedje $A$ in $B$ prazno zaporedje $[\ ]$.
Iz tega sledi, da funkcija vrne prazno polje $[\ ]$.

### 3. primer

Razmislimo o naslednjem klicu.
```
ucs([0, 1, 0], [1, 0, 1])
```

Tukaj so skupna podzaporedja $A$ in $B$
 $[\ ], [0], [1], [0, 1]$ in $[1, 0]$.
Pokažemo lahko, da univerzalno skupno podzaporedje ne obstaja.
Zato funkcija vrne $[-1]$.

## Vzorčni ocenjevalnik

Oblika vhoda:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```



Oblika izhoda:

```
T
R[0]  R[1]  ...  R[T-1]
```

Tu je $R$ polje, ki ga vrne `ucs`, in $T$ je njegova dolžina.