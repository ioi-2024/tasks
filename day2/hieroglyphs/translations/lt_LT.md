# Hieroglifai

Mokslininkų komanda tyrinėja hieroglifų sekų panašumus.
Kiekvieną hieroglifą jie vaizduoja neneigiamu sveikuoju skaičiumi.
Savo tyrime jie naudoja šias su seka susijusias sąvokas.

Seka $S$ vadinama sekos $A$ **posekiu** 
 tada ir tik tada, jei $S$ galima gauti
 pašalinus kuriuos nors (ar nepašalinus nei vieno) $A$ narius.

Žemiau esančioje lentelėje pateikta sekos $A = [3, 2, 1, 2]$ posekių pavyzdžių.

| Posekis    | Kaip jis gaunamas iš $A$ |
|----------------|---------------------------------|
| [3, 2, 1, 2] | Nepašalinami jokie nariai.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] or [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Kita vertus, $[3, 3]$ ar $[1, 3]$ nėra $A$ posekiai.
Panagrinėkime dvi hieroglifų sekas $A$ ir $B$.
Seka $S$ vadinama sekų $A$ ir $B$ **bendru posekiu**  
 tada ir tik tada, jei $S$ yra ir $A$ posekis, ir $B$ posekis.
 Taip pat sakome, kad seka $U$ yra sekų $A$ ir $B$ **universalus bendras posekis**  
 tada ir tik tada, jei galioja šios dvi sąlygos:
* $U$ yra sekų $A$ ir $B$ bendras posekis.
* Kiekvienas sekų $A$ ir $B$ bendras posekis taip pat yra sekos $U$ posekis.

Galima parodyti, kad bet kurios dvi sekos $A$ ir $B$
turi ne daugiau kaip vieną universalų bendrą posekį. 

Mokslininkai rado dvi hieroglifų sekas $A$ ir $B$.
Seką $A$ sudaro $N$ hieroglifų, o 
 seką $B$ sudaro $M$ hieroglifų.
 Padėkite mokslininkams surasti sekų $A$ ir $B$ universalų bendrą posekį,
 arba nustatyti, kad toks posekis neegzistuoja.

## Realizacija

Parašykite šią procedūrą:

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: $N$ ilgio masyvas, nusakantis pirmąją seką.
* $B$: $M$ ilgio masyvas, nusakantis antrąją seką.
* Jei egzistuoja universalus bendras $A$ ir $B$ posekis,
   procedūra turi grąžinti masyvą su šiuo posekiu.
  Kitu atveju procedūra turi grąžinti $[-1]$
   (masyvą, kurio ilgis $1$ ir kurio vienintelis narys yra $-1$).
* Ši procedūra kiekvienam testui iškviečiama lygiai vieną kartą.

## Ribojimai

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ kiekvienam $i$, kuriam $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ kiekvienam $j$, kuriam $0 \leq j < M$

## Dalinės užduotys

| Dalinė užduotis | Taškai  | Papildomi ribojimai |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; kiekvieną iš sekų $A$ ir $B$ sudaro $N$ **skirtingų** sveikųjų skaičių nuo $0$ iki $N-1$ (imtinai)
| 2       | $15$   | Bet kuriam sveikajam skaičiui $k$ (sekos $A$ narių, lygių skaičiui $k$, kiekio) ir (sekos $B$ narių, lygių 
skaičiui $k$, kiekio) suma neviršija $3$.
| 3       | $10$   | $A[i] \leq 1$ kiekvienam $i$, kuriam $0 \leq i < N$; $B[j] \leq 1$ kiekvienam $j$, kuriam $0 \leq j < M$
| 4       | $16$   | Sekų $A$ ir $B$ universalus bendras posekis egzistuoja.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | Papildomų ribojimų nėra.

## Pavyzdžiai

### Pavyzdys nr. 1

Panagrinėkime tokį iškvietimą.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Sekų $A$ ir $B$ bendri posekiai yra šie:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ ir 
 $[0, 1, 0, 2]$.

Kadangi $[0, 1, 0, 2]$ yra sekų $A$ ir $B$ bendras posekis, ir
 visi sekų $A$ ir $B$ posekiai taip pat yra sekos $[0, 1, 0, 2]$ posekiai,
 procedūra turi gražinti $[0, 1, 0, 2]$.

### Pavyzdys nr. 2

Panagrinėkime tokį iškvietimą.

```
ucs([0, 0, 2], [1, 1])
```

Šiuo atveju vienintelis bendras $A$ ir $B$ posekis yra tuščia seka $[\ ]$.
Taigi, procedūra turi grąžinti tuščią masyvą $[\ ]$.

### Pavyzdys nr. 3

Panagrinėkime tokį iškvietimą:
```
ucs([0, 1, 0], [1, 0, 1])
```

Šiuo atveju bendri sekų $A$ ir $B$ posekiai yra
 $[\ ], [0], [1], [0, 1]$ and $[1, 0]$.
 Galima paroyti, kad universalus bendras posekis neegzistuoja.
Taigi, procedūra turi grąžinti $[-1]$.

## Pavyzdinė vertinimo programa

Pradinių duomenų formatas:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Rezultatų formatas:

```
T
R[0]  R[1]  ...  R[T-1]
```

Čia, $R$ yra procedūros `ucs`  grąžinamas masyvas, o $T$ yra jo ilgis.
