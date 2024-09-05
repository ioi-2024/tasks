# Mozaika

Salma nori nuspalvinti ant sienos esančią molinę mozaiką.
<!-- Salma plans to colour a clay mosaic on a wall. -->
Mozaika yra $N \times N$ lentelė,
<!-- The mosaic is an $N \times N$ grid,  -->
sudaryta iš $N^2$ kvadratinių $1 \times 1$ dydžio langelių, kurie iš pradžių nenuspalvinti.
 <!-- made of $N^2$ initially uncoloured $1 \times 1$ square tiles. -->
Mozaikos eilutės sunumeruotos nuo $0$ iki $N-1$ iš viršaus į apačią,
<!-- The rows of the mosaic are numbered from $0$ to $N-1$ from top to bottom, -->
o stulpeliai sunumeruoti nuo $0$ iki $N-1$ iš kairės į dešinę.
 <!-- and the columns are numbered from $0$ to $N-1$ from left to right. -->
$i$-oje eilutėje ir $j$-ame stulpelyje ($0 \leq i < N$, $0 \leq j < N$) esantis langelis žymimas $(i,j)$.
<!-- The tile in row $i$ and column $j$ ($0 \leq i < N$, $0 \leq j < N$) is denoted by $(i,j)$. -->
Kiekvienas langelis turi būti nuspalvintas arba
<!-- Each tile must be coloured either -->
baltai (žymima $0$), arba juodai (žymima $1$).
 <!-- white (denoted by $0$) or black (denoted by $1$). -->

Tam, kad nuspalvintų mozaiką, Salma pirmiausiai pasirenka du $N$ ilgio masyvus $X$ ir $Y$,
<!-- To colour the mosaic, Salma first picks two arrays $X$ and $Y$ of length $N$, -->
kurie abu sudaryti iš $0$ ir $1$, ir kuriems galioja $X[0] = Y[0]$.
 <!-- each consisting of values $0$ and $1$, such that $X[0] = Y[0]$. -->
Ji naudoja masyvą $X$ nuspalvinti viršutinės (0-inės) eilutės langelius:
<!-- She colours the tiles of the topmost row (row $0$) according to array $X$, -->
langeliui $(0,j)$ parenkama spalva $X[j]$ ($0 \leq j < N$).
 <!-- such that the colour of tile $(0,j)$ is $X[j]$ ($0 \leq j < N$). -->
Ji taip pat naudoja masyvą $Y$ nuspalvinti kairiausio (0-inio) stulpelio langelius:
<!-- She also colours the tiles of the leftmost column (column $0$) according to array $Y$, -->
langeliui $(i,0)$ parenkama spalva $Y[i]$ ($0 \leq i < N$).
 <!-- such that the colour of tile $(i,0)$ is $Y[i]$ ($0 \leq i < N$). -->

Tada ji kartoja šiuos veiksmus, kol visi langeliai tampa nuspalvinti:
<!-- Then she repeats the following steps until all tiles are coloured: -->
* Ji randa bet kurį *nenuspalvintą* langelį $(i,j)$, kurio
  viršutinis kaimynas (langelis $(i-1, j)$) ir kairysis kaimynas (langelis $(i, j-1)$)
  abu yra *jau nuspalvinti*.
<!-- * She finds any *uncoloured* tile $(i,j)$ such that
 its up neighbor (tile $(i-1, j)$) and left neighbor (tile $(i, j-1)$)
 are both *already coloured*. -->
* Tada ji nuspalvina langelį $(i,j)$ juodai, jeigu abu šie kaimynai yra balti;
  kitu atveju ji nuspalvina langelį $(i, j)$ baltai.
<!-- * Then, she colours tile $(i,j)$ black if both of these neighbors are white;
 otherwise, she colours tile $(i, j)$ white. -->

Galima įrodyti, kad galutinės langelių spalvos nepriklauso
nuo to, kokia tvarka Salma juos spalvina.
<!-- It can be shown that the final colours of the tiles do not depend 
on the order in which Salma is colouring them. -->
 
Jazminą labai domina mozaikos langelių spalvos.
Ji užduoda Salmai $Q$ klausimų, sunumeruotų nuo $0$ iki $Q-1$.
<!-- Yasmin is very curious about the colours of the tiles in the mosaic.
She asks Salma $Q$ questions, numbered from $0$ to $Q-1$. -->
$k$-ajame klausime ($0 \leq k < Q$)
Jazmina nusako stačiakampį mozaikoje, kurio
<!-- In question $k$ ($0 \leq k < Q$),
 Yasmin specifies a subrectangle of the mosaic by its: -->
* Viršutinė eilutė yra $T[k]$, o apatinė eilutė yra $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* Kairysis stulpelis yra $L[k]$, o dešinysis stulpelis yra $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

<!-- * Topmost row $T[k]$ and bottommost row $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* Leftmost column $L[k]$ and rightmost column $R[k]$ ($0 \leq L[k] \leq R[k] < N$). -->

Atsakymas į klausimą yra juodų langelių kiekis šiame stačiakampyje.
Taigi Salmai reikia rasti, kiek yra juodų langelių $(i, j)$,
kuriems galioja $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$.
<!-- The answer to the question is the number of black tiles in this subrectangle.
Specifically, Salma should find how many tiles $(i, j)$ exist,
 such that $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$,
 and the colour of tile $(i,j)$ is black. -->

Parašykite programą, kuri atsako į Jazminos klausimus.
<!-- Write a program that answers Yasmin's questions. -->

## Realizacija

Jums reikia parašyti šią procedūrą.
<!-- You should implement the following procedure. -->

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: $N$ ilgio masyvai, atitinkamai nurodantys langelių spalvas
 viršutinėje eilutėje ir kairiajame stulpelyje.
* $T$, $B$, $L$, $R$: $Q$ ilgio masyvai, aprašantys Jazminos užduotus klausimus.
* Procedūra turėtų grąžinti $Q$ ilgio masyvą $C$,
 kur $C[k]$ yra atsakymas į $k$-ąjį klausimą ($0 \leq k < Q$).
* Ši procedūra kiekvienam testui iškviečiama lygiai vieną kartą.

<!-- * $X$, $Y$: arrays of length $N$ describing the colours of the tiles
 in the topmost row and the leftmost column, respectively.
* $T$, $B$, $L$, $R$: arrays of length $Q$ describing the questions asked by Yasmin.
* The procedure should return an array $C$ of length $Q$,
 such that $C[k]$ provides the answer to question $k$ ($0 \leq k < Q$).
* This procedure is called exactly once for each test case. -->

## Ribojimai

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ ir $Y[i] \in \{0, 1\}$
  kiekvienam $i$, kur $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ ir $0 \leq L[k] \leq R[k] < N$
 kiekvienam $k$, kur $0 \leq k < Q$

## Dalinės užduotys

| Dalinė užduotis | Taškai  | Papildomi ribojimai |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ (kiekvienam $k$, kur $0 \leq k < Q$)
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ (kiekvienam $i$, kur $0 \leq i < N$)
| 6       | $22$   | $T[k] = B[k]$ ir $L[k] = R[k]$ (kiekvienam $k$, kur $0 \leq k < Q$)
| 7       | $19$   | $T[k] = B[k]$ (kiekvienam $k$, kur $0 \leq k < Q$)
| 8       | $22$   | Papildomų ribojimų nėra

## Pavyzdys

Panagrinėkime šį iškvietimą.
<!-- Consider the following call. -->

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Šis pavyzdys pavaizduotas paveikslėliuose žemiau.
Kairysis paveikslėlis vaizduoja mozaikos langelių spalvas.
Vidurinysis ir dešinysis paveikslėliai atitinkamai rodo stačiakampius,
apie kuriuos Jazmina paklausė pirmajame ir antrajame klausimuose.
<!-- This example is illustrated in the pictures below.
The left picture shows the colours of the tiles in the mosaic.
The middle and right pictures show the subrectangles
 Yasmin asked about in the first and second question, respectively. -->

![](example.png "550")

Atsakymai į klausimus
(t. y., skaičius vienetų paryškintuose stačiakampiuose)
yra atitinkamai 7 ir 3.
Todėl procedūra turi grąžinti $[7, 3]$.
<!-- The answers to the questions
 (that is, the numbers of ones in the shaded rectangles)
 are 7 and 3, respectively.
Hence, the procedure should return $[7, 3]$. -->

## Pavyzdinė vertinimo programa

Pradinių duomenų formatas:

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

Rezultatų formatas:

```
C[0]
C[1]
...
C[S-1]
```

Čia $S$ yra `mosaic` procedūros grąžinto masyvo $C$ ilgis.
<!-- Here, $S$ is the length of the array $C$ returned by `mosaic`. -->
