# Mozaīka

Salma plāno uz sienas izveidot māla flīžu mozaīku.
Mozaīku veido $N \times N$ režģis, kas sastāv
 no $N^2$ sākotnēji nekrāsotām $1 \times 1$ kvadrātveida flīzēm.
Mozaīkas rindas ir numurētas no $0$ līdz $N-1$ no augšas uz leju,
 un kolonnas ir numurētas no $0$ līdz $N-1$ no kreisās puses uz labo.
Flīzi $i$-tajā rindā un $j$-tajā kolonnā ($0 \leq i < N$, $0 \leq j < N$) apzīmē ar $(i,j)$.
Katrai flīzei jābūt nokrāsotai baltai (apzīmē ar $0$) vai melnai (apzīmē ar $1$).

Lai izkrāsotu mozaīku, Salma vispirms izvēlas divus masīvus $X$ un $Y$ garumā $N$,
kur katrs sastāv no vērtībām $0$ un $1$, lai $X[0] = Y[0]$.
Viņa nokrāso augšējās ($0$-tās) rindas flīzes atbilstoši masīvam $X$,
 tā, lai flīzes $(0,j)$ krāsa būtu $X[j]$ ($0 \leq j < N$).
Viņa arī nokrāso kreisākās ($0$-tās) kolonnas flīzes atbilstoši masīvam $Y$,
 tā, lai flīzes $(i,0)$ krāsa būtu $Y[i]$ ($0 \leq i < N$).
 
 Pēc tam viņa atkārto šādas darbības, līdz visas flīzes ir nokrāsotas:
* Viņa atrod jebkuru *nekrāsotu* flīzi $(i,j)$, kuras
 augšējais kaimiņš (flīze $(i-1, j)$) un kreisais kaimiņš (flīze $(i, j-1)$)
 abi *jau ir nokrāsoti*.
* Pēc tam viņa nokrāso flīzi $(i,j)$ melnā krāsā, ja abi šie kaimiņi ir balti;
 pretējā gadījumā viņa nokrāso flīzi $(i, j)$ baltā krāsā.

Var pierādīt, ka flīžu beigu krāsojums nav atkarīgs no secības, kādā Salma tās nokrāso.
 
Jasmīnai ļoti interesē mozaīkas flīžu krāsas.
Viņa uzdod Salmai $Q$ jautājumus, kas numurēti no $0$ līdz $Q-1$.
Jautājumā $k$ ($0 \leq k < Q$),
 Jasmīna interesējas par kādu mozaīkas flīžu taisnstūri, norādot:
* augšējo rindu $T[k]$ un apakšējo rindu $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* kreisāko kolonnu $L[k]$ un labējāko kolonnu $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

Atbilde uz katru jautājumu ir melno flīžu skaits šajā apakštaisnstūrī.
Konkrēti, Salmai ir jāatrod, cik daudz ir tādu flīžu $(i, j)$, kurām $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$,
 un flīze $(i,j)$ ir nokrāsota melnā krāsā.

Uzrakstiet programmu, kas atbild uz Jasmīnas jautājumiem!

## Implementēšanas detaļas

Jums jāimplementē šāda procedūra:

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: masīvi garumā $N$, kas apraksta flīžu krāsu attiecīgi augšējā rindā un kreisākajā kolonnā.
* $T$, $B$, $L$, $R$: masīvi garumā $Q$, kas apraksta Jasmīnas uzdotos jautājumus.
* Procedūrai jāatgriež masīvs $C$ garumā $Q$, tāds, ka $C[k]$ satur atbildi uz $k$-to ($0 \leq k < Q$) jautājumu.
* Šī procedūra katram testam tiek izsaukta vienreiz.

## Ierobežojumi

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ un $Y[i] \in \{0, 1\}$
 visiem $i$, kur $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ un $0 \leq L[k] \leq R[k] < N$
visiem $k$, kur $0 \leq k < Q$

## Apakšuzdevumi

| Apakšuzdevums | Punkti  | Papildu ierobežojumi |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ (visiem $k$, kur $0 \leq k < Q$)
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ (visiem $i$, kur $0 \leq i < N$)
| 6       | $22$   | $T[k] = B[k]$ un $L[k] = R[k]$ (visiem $k$, kur $0 \leq k < Q$)
| 7       | $19$   | $T[k] = B[k]$ (visiem $k$, kur $0 \leq k < Q$)
| 8       | $22$   | Bez papildu ierobežojumiem.

## Piemērs

Aplūkosim šādu procedūras izsaukumu:

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Šī piemēra ilustrācijas ir dotas attēlos zemāk.
Attēlā pa kreisi ir parādīta mozaīkas flīžu krāsa.
Attēlos vidū un pa labi ir parādīti Jasmīnas jautājumos (attiecīgi pirmajā un otrajā) izmantotie mozaīkas apakštaisnstūri.

![](example.png "550")

Atbildes uz jautājumiem (t.i., vieninieku skaits iekrāsotajos taisnstūros) ir attiecīgi 7 un 3. Tādējādi, procedūrai jāatgriež $[7, 3]$.

## Paraugvērtētājs

Ievaddatu formāts:

```
N
X[0]  X[1]  ...  X[N-1]
Y[0]  Y[1]  ...  Y[N-1]
Q
T[0]  B[0]  L[0]  R[0]
T[1]  B[1]  L[1]  R[1]
...
T[Q-1]  B[Q-1]  L[Q-1]  R[Q-1]
```

Izvaddatu formāts:

```
C[0]
C[1]
...
C[S-1]
```

Šeit $S$ ir `mosaic` atgrieztā masīva $C$ garums.
