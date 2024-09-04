# Nil

Čez Nil želite prepeljati $N$ artefaktov. 
Artefakti so oštevilčeni od $0$ do $N-1$.
Teža artefakta $i$ ($0 \leq i < N$) je $W[i]$.

Za prevoz artefaktov uporabljate posebne čolne.
Vsak čoln lahko nosi **največ dva** artefakta.

* Če se odločite, da v čoln postavite en artefakt, je lahko teža artefakta poljubna.
* Če želite v čoln postaviti dva artefakta, mora biti čoln enakomerno obtežen.
Natančneje,
 artefakta $p$ in $q$ ($0 \leq p < q < N$) lahko pošljete z enim čolnom,
 če je absolutna razlika njunih tež največ $D$ ,
 t.j. $|W[p] - W[q]| \leq D$ .
 
 Za prevoz artefakta morate plačati brodnino, ki je odvisna od števila artefaktov v čolnu.
Brodnina artefakta $i$ ($0 \leq i < N$) je:

* $A[i]$, če v čoln postavite zgolj en artefakt, oziroma
* $B[i]$, če v čoln postavite dva artefakta.

V slednjem primeru morate plačati za oba artefakta v čolnu.
Natančneje, če se odločite prepeljati
 artefakta $p$ in $q$ ($0 \leq p < q < N$) v istem čolnu,
 morate plačati $B[p] + B[q]$ .

Prevoz zgolj enega artefakta v čolnu je vedno dražje, 
kot pa če ga pošljete skupaj z nekim drugim artefaktom,
torej $B[i] < A[i]$ za vse $i$ tako da $0 \leq i < N$ .

Na žalost je reka zelo nepredvidljiva in se vrednost $D$ pogosto spreminja.
Vaša naloga je odgovoriti na $Q$ vprašanj, oštevilčenih od $0$ do $Q-1$ .
Vprašanja so opisana s poljem $E$ dolžine $Q$.
Odgovor na vprašanje $j$ ($0 \leq j < Q$) je
 najmanjša skupna vsota brodnin vseh $N$ artefaktov,
 ko je vrednost $D$ enaka $E[j]$.

<div style="page-break-after: always;"></div>

## Podrobnosti implementacije

Implementirajte naslednjo funkcijo:

```
std::vector&lt;long long&gt; calculate_costs(
    std::vector&lt;int&gt; W, std::vector&lt;int&gt; A, 
    std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```

* $W$ , $A$ , $B$: polja naravnih števil dolžine $N$, ki opisujejo težo artefaktov in njihove brodnine.
* $E$: polje naravnih števil dolžine $Q$, ki opisujejo vrednosti $D$ za vsako vprašanje.
* Funkcija naj vrne polje $R$ naravnih števil $Q$,
   ki vsebuje minimalne skupne vsote brodnin artefaktov,
   kjer je $R[j]$ minimalna skupna vsota brodnin, ko je vrednost $D$ $E[j]$ (za vsak $j$,
   kjer $0 \leq j < Q$).
* Za vsak testni primer se funkcijo pokliče enkrat.

## Omejitve

* $1 \leq N \leq 100\,000$
* $1 \leq Q \leq 100\,000$
* $1 \leq W[i] \leq 10^{9}$
   za vsak $i$ velja $0 \leq i < N$
* $1 \leq B[i] < A[i] \leq 10^{9}$
   za vsak $i$ velja $0 \leq i < N$
* $1 \leq E[j] \leq 10^{9}$
   za vsak $j$ velja $0 \leq j < Q$

## Podnaloge

| Podnaloga | Točke  | Dodatne omejitve |
| :-----: | :----: | ---------------------- |
| 1       | $6$    | $Q \leq 5$; $N \leq 2000$; $W[i] = 1$ za vsak $i$ velja $0 \leq i < N$
| 2       | $13$   | $Q \leq 5$; $W[i] = i+1$ za vsak $i$ velja $0 \leq i < N$
| 3       | $17$   | $Q \leq 5$; $A[i] = 2$ in $B[i] = 1$ za vsak $i$ velja $0 \leq i < N$
| 4       | $11$   | $Q \leq 5$; $N \leq 2000$
| 5       | $20$   | $Q \leq 5$
| 6       | $15$   | $A[i] = 2$ in $B[i] = 1$ za vsak $i$ velja $0 \leq i < N$
| 7       | $18$   | Ni dodatnih omejitev.

<div style="page-break-after: always;"></div>

## Primer

Poglejmo naslednji klic.

```
calculate_costs([15, 12, 2, 10, 21],
                [5, 4, 5, 6, 3],
                [1, 2, 2, 3, 2],
                [5, 9, 1])
```

V tem primeru imamo $N = 5$ artefaktov in $Q = 3$ vprašanj.

Pri prvem vprašanju $D = 5$.
Artefakta $0$ in $3$ lahko pošljete v enem čolnu (ker $|15 - 10| \leq 5$), preostale artefakte pa v ločenih čolnih.
Minimalna vsota brodnin vseh artefaktov je $1+4+5+3+3 = 16$.

V drugem vprašanju $D = 9$.
Artefakta $0$ in $1$ lahko pošljete v enem čolnu (ker $|15 - 12| \leq 9$), ter artefakta $2$ in $3$ lahko pošljete v drugem čolnu (ker $|2 - 10| \leq 9$).
Preostali artefakt lahko pošljete v tretjem čolnu.
Minimalna brodnina vseh artefaktov je $1+2+2+3+3 = 11$.

V zadnjem vprašanju $D = 1$. Vsak artefakt morate poslati v svojem čolnu.
Minimalna vsota brodnin vseh artefaktov je $5+4+5+6+3 = 23$.

Zato mora funkcija vrniti $[16, 11, 23]$ .

<div style="page-break-after: always;"></div>

## Vzorčni ocenjevalnik

Oblika vhoda:

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



Oblika izhoda:

```
R[0]
R[1]
...
R[S-1]
```

Tu je $S$ dolžina polja $R$, ki ga vrne `calculate_costs`.
