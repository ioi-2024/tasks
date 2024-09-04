# Medis

Panagrinėkime **medį** iš $N$ **viršūnių**,
 sunumeruotų nuo $0$ iki $N-1$.
Viršūnė, kurios numeris $0$, vadinama **šaknine viršūne**.
Kiekviena viršūnė, išskyrus šakninę, turi vieną **tėvinę viršūnę**.
Kiekvienam $i$, kuriam $1 \leq i < N$,
 viršūnės $i$ tėvinė viršūnė yra viršūnė $P[i]$, kur $P[i] < i$.
Taip pat pažymime $P[0] = -1$.

Kiekvienai viršūnei $i$ ($0 \leq i < N$),
 jos  **pomedis** yra šių viršūnių rinkinys:
 * $i$, ir
 * bet kuri viršūnė, kurios tėvinė viršūnė yra $i$, ir
 * bet kuri viršūnė, kurios tėvinės viršūnės tėvinė viršūnė yra $i$, ir
 * bet kuri viršūnė, kurios tėvinės viršūnės tėvinės viršūnės tėvinė viršūnė yra $i$, ir
 * t. t.

Žemiau esančiame paveikslėlyje pateiktas medis iš $N = 6$ viršūnių.
Kiekviena rodyklė jungia viršūnę su jos tėvine viršūne,
išskyrus šakninę, kuri neturi tėvinės viršūnės.
Viršūnės $2$ pomedžiui priklauso viršūnės $2, 3, 4$ ir $5$.
Viršūnės $0$ pomedžiui priklauso visos $6$-ios medžio viršūnės, o
viršūnės $4$ pomedį sudaro tik pati viršūnė $4$.

![](subtrees.png "150")

Kiekvienai viršūnei priskirtas neneigiamas sveikasis skaičius **svoris**.
Pažymėkime viršūnės $i$ ($0 \leq i < N$) svorį $W[i]$.

Parašykite programą, kuri atsakys į $Q$ užklausų.
Kiekvieną užklausą nusako teigiamų sveikųjų skaičių pora $(L, R)$.
Užklausos atsakymas randamas tokiu būdu.

Kiekvienai medžio viršūnei priskirkite sveikąjį skaičių, pavadintą 
**koeficientu**.
Tokį priskyrimą nusako seka $C[0], \ldots, C[N-1]$,
 kur $C[i]$ ($0 \leq i < N$) yra viršūnės $i$ koeficientas.
Pavadinkime šią seką **koeficientų seka**.
Atkreipkite dėmesį, kad koeficientų sekos nariai gali būti neigiami, lygūs $0$ ar teigiami.

Užklausai $(L, R)$,
 koeficientų seka vadinama **leistina**,
 jei kiekvienos viršūnės $i$ ($0 \leq i < N$)
pomedžio viršūnių koeficientų suma yra ne mažesnė už $L$ ir ne didesnė už $R$.

Duotai koeficientų sekai $C[0], \ldots, C[N-1]$,
viršūnės $i$ **kaina** lygi $|C[i]| \cdot W[i]$,
 kur $|C[i]|$ žymi $C[i]$ modulį.
Galiausiai, **bendra kaina** lygi visų viršūnių kainų sumai.
Kiekvienai užklausai apskaičiuokite,
 **mažiausią bendrą kainą**, kurią įmanoma pasiekti su kažkuria leistina koeficientų seka.
 
 Galima įrodyti, kad bet kuriai užklausai egzistuoja bent viena leistina koeficientų seka.

## Realizacija

Parašykite šias dvi procedūras:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$: masyvai, kurių ilgis $N$, nusakantys viršūnių tėvines viršūnes ir svorius.
* Ši procedūra kiekvienam testui iškviečiama lygiai vieną kartą, vertinimo programos sąveikavimo su jūsų programa pradžioje. 
 

```
long long query(int L, int R)
```
* $L$, $R$: užklausą nusakantys sveikieji skaičiai.
* Ši procedūra kiekvienam testui iškviečiama $Q$ kartų po procedūros `init` iškvietimo.
* Ši procedūra gražina duotos užklausos atsakymą.


## Ribojimai

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ kiekvienam $i$, kuriam $1 \leq i < N$
* $0 \leq W[i] \leq 1\,000\,000$ kiekvienam $i$, kuriam $0 \leq i < N$
* $1 \leq L \leq R \leq 1\,000\,000$ kiekvienai užklausai

## Dalinės užduotys

| Dalinė užduotis | Taškai  | Ribojimai |
| :-----: | :----: | ---------------------- |
|   1     |  $10$  | $Q \leq 10$; $W[P[i]] \leq W[i]$ kiekvienam $i$, kur $1 \leq i < N$
|   2     |  $13$  | $Q \leq 10$; $N \leq 2\,000$
|   3     |  $18$  | $Q \leq 10$; $N \leq 60\,000$
|   4     |  $7$   | $W[i] = 1$ kiekvienam $i$, kur $0 \leq i < N$
|   5     |  $11$  | $W[i] \leq 1$ kiekvienam $i$, kur $0 \leq i < N$
|   6     |  $22$  | $L = 1$
|   7     |  $19$  | Papildomų ribojimų nėra.



## Pavyzdžiai

Panagrinėkime tokias užklausas:

```
init([-1, 0, 0], [1, 1, 1])
```
Medį sudaro $3$ viršūnės: šakninė viršūnė ir jos $2$ vaikai.
Visų viršūnių svoriai lygūs $1$.

```
query(1, 1)
```

Šioje užklausoje $L = R = 1$. Tai reiškia, kad kiekvieno pomedžio koeficientų suma turi būti lygi $1$.
Panagrinėkite tokią koeficientų seką $[-1, 1, 1]$.
Žemiau pavaizduotas medis ir atitinkami koeficientai (užtušuotuose stačiakampiuose).

![](ex1.png "150")

Kiekvienai viršūnei $i$ ($0 \leq i < 3$), pomedžio $i$ visų viršūnių koeficientų suma lygi $1$. 
Taigi, ši koeficientų seka yra leistina.
Bendra suma skaičiuojama taip:

| Viršūnė | Svoris | Koeficientas | Kaina                      |
| :----: | :----: | :---------: | :-----------------------: |
|   0    |   1    |     -1      | $\mid -1 \mid \cdot 1 = 1$
|   1    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$
|   2    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$

Taigi, bendra kaina lygi  $3$.
Ši koeficientų seka yra vienintelė leistina, tad turi būti grąžinamas užklausos atsakymas $3$.

```
query(1, 2)
```
Šiai užklausiai mažiausia bendra kaina lygi $2$.
Ji gaunama su koeficientų seka $[0, 1, 1]$.

## Pavyzdinė vertinimo programa

Pradinių duomenų formatas:

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

kur $L[j]$ ir $R[j]$
 (visiems $0 \leq j < Q$)
 yra argumentai $j$-ajam `query` iškvietimui.
 Atkreipkite dėmesį, kad antrojoje pradinių duomenų eilutėje yra **tik $N-1$ sveikųjų skaičių**, 
 nes pavyzdinė vertinimo programa neskaito $P[0]$ vertės.

Rezultatų formatas:
```
A[0]
A[1]
...
A[Q-1]
```

kur $A[j]$
 (visiems $0 \leq j < Q$) yra
 vertė, kuri grąžinama $j$-ąjį kartą iškvietus `query`.
