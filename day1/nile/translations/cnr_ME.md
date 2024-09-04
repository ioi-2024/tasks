# Nil

Želite prenijeti $N$ artefakta preko Nila.
Artefakti su označeni brojevima od $0$ do $N-1$.
Težina artefakta $i$ ($0 \leq i < N$) je $W[i]$.

Da prenesete artefakte koristićete posebne čamce.
Svaki čamac može nositi **najviše dva** artefakta.

* Ako odlučite staviti jedan artefakt na čamac nije važna težina artefakta.
* Ako želite staviti dva artefakta na jedan čamac morate se pobrinuti da je čamac balansiran.
Specifično, možete poslati artefakte $p$ i $q$ ($0 \leq p < q < N$) istim čamcem ako i samo ako apsolutna razlika njihovih težina je najviše $D$, odnosno $|W[p] - W[q]| \leq D$.

Da prenesete artefakt morate platiti cijenu u zavisnosti od broja artefakta na čamcu.
Cijena transporta artefakta $i$ ($0 \leq i < N$) je:

* $A[i]$, ako stavite artefakt sam na čamac, ili
* $B[i]$, ako ga stavite zajedno sa još nekim drugim artefaktom.

Napominjemo da u drugom slučaju morate platiti cijenu za oba artefakta u čamcu.
Specifično, ako odlučite poslati artefakte $p$ i $q$ ($0 \leq p < q < N$) morate platiti $B[p] + B[q]$.

Cijena artefakta kada je sam je uvijek veća nego cijena u slučaju da ga šaljete zajedno sa jos nekim drugim artefaktom,
dakle $B[i] < A[i]$ za sve $i$ takve da $0 \leq i < N$.

Nažalost, Nil je vrlo nepredvidiv i vrijednost $D$ se često mijenja.
Vaš zadatak je da odgovorite na $Q$ upita pobrojanih od $0$ do $Q-1$.
Pitanja su opisana nizom $E$ dužine $Q$.
Odgovor na pitanje $j$ ($0 \leq j < Q$) je
minimalna ukupna cijena prevoza svih $N$ artefakta,
kada je vrijednost $D$ jednaka $E[j]$.

## Detalji implementacije

Potrebno je da implementirate sljedeću proceduru.

```
std::vector&lt;long long&gt; calculate_costs(
    std::vector&lt;int&gt; W, std::vector&lt;int&gt; A, 
    std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```
<br/>
* $W$, $A$, $B$: nizovi cijelih brojeva dužine $N$ koji opisuju težine artefakta i cijene prenošenja istih.
* $E$: niz cijelih brojeva dužine $Q$ koji opisuje vrijednosti $D$ za svaki upit.
* Ova procedura treba vratiti niz $R$ koji sadrži $Q$ cijelih brojeva jednakih minimalnim cijenama prenošenja svih artefakta, gdje je $R[j]$ cijena kada je $D$ jednako $E[j]$ (za svaki $j$ takav da $0 \leq j < Q$).
* Ova procedura će biti pozvana tačno jednom za svaki testni primjer.

## Ograničenja

* $1 \leq N \leq 100\,000$
* $1 \leq Q \leq 100\,000$
* $1 \leq W[i] \leq 10^{9}$
   za svaki $i$ takav da $0 \leq i < N$
* $1 \leq B[i] < A[i] \leq 10^{9}$
   za svaki $i$ takav da $0 \leq i < N$
* $1 \leq E[j] \leq 10^{9}$
   za svaki $j$ takav da $0 \leq j < Q$

## Podzadaci

| Podzadatak | Bodovi  | Dodatna ograničenja |
| :-----: | :----: | ---------------------- |
| 1       | $6$    | $Q \leq 5$; $N \leq 2000$; $W[i] = 1$ za svaki $i$ takav da $0 \leq i < N$
| 2       | $13$   | $Q \leq 5$; $W[i] = i+1$ za svaki $i$ takav da $0 \leq i < N$
| 3       | $17$   | $Q \leq 5$; $A[i] = 2$ and $B[i] = 1$ za svaki $i$ takav da $0 \leq i < N$
| 4       | $11$   | $Q \leq 5$; $N \leq 2000$
| 5       | $20$   | $Q \leq 5$
| 6       | $15$   | $A[i] = 2$ and $B[i] = 1$ za svaki $i$ takav da $0 \leq i < N$
| 7       | $18$   | Bez dodatnih ograničenja.

## Primjer

Razmotrimo sljedeći poziv.

```
calculate_costs([15, 12, 2, 10, 21],
                [5, 4, 5, 6, 3],
                [1, 2, 2, 3, 2],
                [5, 9, 1])
```

U ovom primjeru imamo $N = 5$ artefakta i $Q = 3$ upita.

U prvom upitu $D = 5$.
Možete poslati artefakte $0$ i $3$ u jednom čamcu (pošto $|15 - 10| \leq 5$) i preostale artefakte u odvojenim čamcima. Ovo daje minimalnu cijenu prenosa svih artefakta, $1+4+5+3+3 = 16$.

U drugom upitu $D = 9$.
Možete poslati artefakte $0$ i $1$ istim čamcem (pošto $|15 - 12| \leq 9$) i poslati artefakte $2$ i $3$ istim čamcem (pošto $|2 - 10| \leq 9$).
Preostali artefakt se može prenijeti sam u čamcu.
Ovo daje minimalnu cijenu prenosa svih artefakta $1+2+2+3+3 = 11$.

U posljednjem upitu $D = 1$. Morate poslati svaki artefakt na odvojenom čamcu.
Ovo daje minimalnu cijenu svih artefakta $5+4+5+6+3 = 23$.

Dakle, ova procedura treba vratiti $[16, 11, 23]$.

## Grejder

Format ulaza:

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

Format izlaza:

```
R[0]
R[1]
...
R[S-1]
```

Ovdje je $S$ dužina niza $R$ koju vrati `calculate_costs`.

