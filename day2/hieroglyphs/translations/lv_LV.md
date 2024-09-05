# Hieroglifi

Pētnieku komanda pēta līdzības starp hieroglifu virknēm, kur katrs hieroglifs tiek apzīmēts ar veselu nenegatīvu skaitli.
Lai veiktu savu pētījumu, viņi izmanto zemāk dotās definīcijas.

Fiksētai virknei $A$,
 virkni $S$ sauc par $A$ **apakšvirkni**
 tad un tikai tad, ja $S$ var iegūt no $A$, izmetot no tās dažus (iespējams, nevienu) elementus.

Tālāk esošajā tabulā ir parādīti daži virknes $A = [3, 2, 1, 2]$ apakšvirkņu piemēri.

| Virkne | Kā to var iegūt no $A$ |
|----------------|--------------------------------- -|
| [3, 2, 1, 2] | Neviens elements netiek izmests.
| [2, 1, 2] | [<s>3</s>, 2, 1, 2]
| [3, 2, 2] | [3, 2, <s>1</s>, 2]
| [3, 2] | [3, <s>2</s>, <s>1</s>, 2] vai [3, 2, <s>1</s>, <s>2</s>]
| [3] | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ] | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

No otras puses, $[3, 3]$ vai $[1, 3]$ nav $A$ apakšvirknes.

Aplūkosim divas hieroglifu virknes $A$ un $B$.

Virkni $S$ sauc par $A$ un $B$ **kopīgu apakšvirkni**
 tad un tikai tad, ja $S$ ir gan $A$, gan $B$ apakšvirkne.
 
Virkni $U$ sauc par $A$ un $B$ **universālu kopīgu apakšvirkni**
 tad un tikai tad, ja ir izpildīti šādi divi nosacījumi:
* $U$ ir $A$ un $B$ kopīga apakšvirkne.
* Katra $A$ un $B$ kopīga apakšvirkne ir arī $U$ apakšvirkne.

Var pierādīt, ka jebkurām divām virknēm $A$ un $B$
 ir ne vairāk kā viena universāla kopīga apakšvirkne.

Pētnieki ir atraduši divas hieroglifu $A$ un $B$ virknes.
Virkne $A$ sastāv no $N$ hieroglifiem
 un virkne $B$ sastāv no $M$ hieroglifiem.
Palīdziet pētniekiem aprēķināt virkņu $A$ un $B$ universālo kopīgo apakšvirkni,
 vai noteikt, ka šāda virkne neeksistē.


## Implementēšanas detaļas

Jums jāimplementē šāda procedūra:

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: masīvs garumā $N$, kas apraksta pirmo virkni.
* $B$: masīvs garumā $M$, kas apraksta otro virkni.
* Ja pastāv universāla kopīga $A$ un $B$ apakšvirkne,
   procedūrai ir jāatgriež masīvs, kas satur šo virkni.
  Pretējā gadījumā procedūrai ir jāatgriež $[-1]$
   (masīvs garumā $1$, kura vienīgais elements ir $-1$).
* Šī procedūra tiek izsaukta tieši vienreiz katram testam.

## Ierobežojumi

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ visiem $i$, kur $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ visiem $j$, kur $0 \leq j < M$

## Apakšuzdevumi

| Apakšuzdevums | Punkti | Papildu ierobežojumi |
| :-----: | :----: | ----------------------- |
| 1 | $3$ | $N = M$; $A$ un $B$ katra sastāv no $N$ **atšķirīgiem** veseliem skaitļiem starp $0$ un $N-1$ (ieskaitot)
| 2 | $15$ | Jebkuram veselam skaitlim $k$ to $A$ elementu skaits, kas vienāds ar $k$, plus to $B$ elementu skaits, kas vienāds ar $k$, ir ne vairāk kā $3$.
| 3 | $10$ | $A[i] \leq 1$ katram $i$, kur $0 \leq i < N$; $B[j] \leq 1$ katram $j$, kur $0 \leq j < M$
| 4 | $16$ | Pastāv universāla kopīga $A$ un $B$ apakšvirkne.
| 5 | $14$ | $N \leq 3000$; $M \leq 3000$
| 6 | $42$ | Nav papildu ierobežojumu.

## Piemēri

### 1. piemērs

Aplūkosim šādu izsaukumu:

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Šajā gadījumā kopīgās $A$ un $B$ apakšvirknes ir:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ un $[0, 1, 0, 2]$.

Tā kā $[0, 1, 0, 2]$ ir $A$ un $B$ kopīga apakšvirkne, un visas $A$ un $B$ kopīgās apakšvirknes ir $[0, 1, 0, 2]$ apakšvirknes,
 procedūrai jāatgriež $[0, 1, 0, 2]$.

### 2. piemērs

Aplūkosim šādu izsaukumu:

```
ucs([0, 0, 2], [1, 1])
```

Šajā gadījumā vienīgā $A$ un $B$ kopīgā apakšvirkne ir tukšā apakšvirkne $[\ ]$.
Tāpēc procedūrai jāatgriež tušs masīvs $[\ ]$.

### 3. piemērs

Aplūkosim šādu izsaukumu:

```
ucs([0, 1, 0], [1, 0, 1])
```

Šajā gadījumā kopīgās $A$ un $B$ apakšvirknes ir:
 $[\ ], [0], [1], [0, 1]$ un $[1, 0]$.
Var pierādīt, ka šajā gadījumā universāla kopīga apakšvirkne neeksistē.
Tādējādi, procedūrai jāatgriež $[-1]$.

## Paraugvērtētājs

Ievaddatu formāts:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Izvaddatu formāts:

```
T
R[0]  R[1]  ...  R[T-1]
```

Šeit $R$ ir `ucs` atgrieztais masīvs garumā $T$.
