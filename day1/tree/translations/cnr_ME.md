# Stablo

Razmotrite **stablo** koje se sastoji od $N$ **čvorova**, označenih brojevima od $0$ do $N-1$. Čvor $0$ se naziva **korijen**. Svaki čvor, osim korijena, ima jednog **roditelja**. 
Za svaki $i$, gdje je $1 \leq i < N$, roditelj čvora $i$ je čvor $P[i]$, gdje $P[i] < i$. 
Takođe pretpostavljamo da je $P[0] = -1$.

Za bilo koji čvor $i$ ($0 \leq i < N$), 
**podstablo** od $i$ je skup sljedećih čvorova:

* $i$, i
* bilo koji čvor čiji je roditelj $i$, i
* bilo koji čvor čiji je roditelj od roditelja $i$, i
* bilo koji čvor čiji je roditelj od roditelja od roditelja $i$, i 
* itd.

Slika ispod prikazuje primjer stabla koje se sastoji od $N = 6$ čvorova. 
Svaka strelica povezuje čvor sa njegovim roditeljem, osim korijena, koji nema roditelja. 
Podstablo čvora $2$ sadrži čvorove $2, 3, 4$ i $5$. 
Podstablo čvora $0$ sadrži svih $6$ čvorova stabla, 
a podstablo čvora $4$ sadrži samo čvor $4$.

![](subtrees.png "150")

Svaki čvor ima dodijeljenu nenegativnu cjelobrojnu **težinu**. Težinu čvora $i$ ($0 \leq i < N$) označavamo sa $W[i]$.

Vaš zadatak je da napišete program koji će odgovoriti na $Q$ upita, svaki specifikovan parom pozitivnih cijelih brojeva $(L, R)$. Odgovor na upit treba biti izračunat na sljedeći način.

Razmotrite dodjeljivanje cijelog broja, koji se naziva **koeficijent**, svakom čvoru stabla. 
Takva dodjela je opisana nizom $C[0], \ldots, C[N-1]$, gdje je $C[i]$ ($0 \leq i < N$) koeficijent dodijeljen čvoru $i$. Nazovimo ovaj niz **nizom koeficijenata**. Napominjemo da elementi niza koeficijenata mogu biti negativni, $0$, ili pozitivni.

Za upit $(L, R)$, niz koeficijenata se naziva **važećim** ako za svaki čvor $i$ ($0 \leq i < N$) 
 vrijedi sljedeći uslov:  suma koeficijenata čvorova u podstablu čvora $i$  nije manja od $L$ i nije veća od $R$.

Za dati niz koeficijenata $C[0], \ldots, C[N-1]$, **trošak** čvora $i$ je $|C[i]| \cdot W[i]$, 
 gdje $|C[i]|$ označava apsolutnu vrijednost $C[i]$. Konačno, **ukupni trošak** je suma troškova svih čvorova. Vaš zadatak je izračunati, za svaki upit, minimalni **ukupni trošak** koji se može postići pomoću nekog važećeg niza koeficijenata.
 
Može se pokazati da za svaki upit postoji barem jedan važeći niz koeficijenata.

## Detalji Implementacije
Trebate implementirati sljedeće dvije procedure:
```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```
* $P$, $W$: nizovi cijelih brojeva dužine $N$ koji specifikuju roditelje i težine.
* Ova procedura se poziva tačno jednom
 na početku interakcije između grejdera i vašeg programa u svakom testnom slučaju.

```
long long query(int L, int R)
```
* $L$, $R$: cijeli brojevi koji opisuju upit.
* Ova procedura se poziva $Q$ puta nakon poziva init u svakom testnom slučaju.
* Ova procedura treba vratiti odgovor na dati upit.

## Ograničenja

* $1 \leq N \leq 200,000$
* $1 \leq Q \leq 100,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ za svaki $i$ takav da $1 \leq i < N$
* $0 \leq W[i] \leq 1,000,000$ za svaki $i$ takav da $0 \leq i < N$
* $1 \leq L \leq R \leq 1,000,000$ u svakom upitu

## Podzadaci

| Podzadatak | Bodovi  | Dodatna ograničenja|
| :-----: | :----: | ---------------------- |
|   1     |  $10$  | $Q \leq 10$; $W[P[i]] \leq W[i]$ for each $i$ such that $1 \leq i < N$
|   2     |  $13$  | $Q \leq 10$; $N \leq 2\,000$
|   3     |  $18$  | $Q \leq 10$; $N \leq 60\,000$
|   4     |  $7$   | $W[i] = 1$ for each $i$ such that $0 \leq i < N$
|   5     |  $11$  | $W[i] \leq 1$ for each $i$ such that $0 \leq i < N$
|   6     |  $22$  | $L = 1$
|   7     |  $19$  | Nema dodatnih ograničenja.



## Primjeri

Razmotri sljedeće pozive:

```
init([-1, 0, 0], [1, 1, 1])
```
Stablo se sastoji od $3$ čvora, korijena i njegova $2$ djeteta. 
Svi čvorovi imaju težinu $1$.

```
query(1, 1)
```
U ovom upitu $L = R = 1$, što znači da suma koeficijenata u svakom podstablu mora biti jednaka $1$.
 Razmotrite niz koeficijenata $[-1, 1, 1]$. 
 Stablo i odgovarajući koeficijenti (u zasjenčenim pravougaonicima) prikazani su ispod.
 
![](ex1.png "150")

Za svaki čvor $i$ ($0 \leq i < 3$), suma koeficijenata svih čvorova u podstablu od $i$ je jednaka $1$.
 Dakle, ovaj niz koeficijenata je važeći.  Ukupni trošak se računa na sljedeći način:

|  Čvor  | Težina | Koeficijent | Trošak                    |
| :----: | :----: | :---------: | :-----------------------: |
|   0    |   1    |     -1      | $\mid -1 \mid \cdot 1 = 1$
|   1    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$
|   2    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$


Stoga, ukupni trošak je $3$. Ovo je jedini važeći niz koeficijenata, stoga ovaj poziv treba vratiti $3$.

```
query(1, 2)
```

Minimalni ukupni trošak za ovaj upit je $2$, 
a postiže se kada je niz koeficijenata $[0, 1, 1]$.

## Grejder

Format ulaza:

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

Gdje su $L[j]$ i $R[j]$ (za $0 \leq j < Q$) ulazni argumenti u $j$-tom pozivu funkcije `query`. 
 
Napomena: Drugi red ulaza sadrži **samo $N-1$ cijelih brojeva**, jer GREJDER ne čita vrijednost $P[0]$.

Format izlaza:

```
A[0]
A[1]
...
A[Q-1]
```

Gdje je $A[j]$ (za $0 \leq j < Q$) vrijednost koju vraća $j$-ti poziv funkcije `query`.