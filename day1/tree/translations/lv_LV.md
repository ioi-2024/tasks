# Koks

Aplūkosim **koku**, kas sastāv no $N$ **virsotnēm**,
 kas numurētas ar skaitļiem no $0$ līdz $N-1$.
Virsotni $0$ sauc par **sakni**.
Katrai virsotnei, izņemot sakni, ir viens **vecāks**.
Katram $i$, kur $1 \leq i < N$,
 virsotnes $i$ vecāks ir virsotne $P[i]$ , kur $P[i] < i$.
Mēs arī pieņemam, ka $P[0] = -1$ .

Jebkurai virsotnei $i$ ( $0 \leq i < N$ ),
 $i$ **apakškoks** ir šādu virsotņu kopa:
 * $i$ un
 * jebkura virsotne, kuras vecāks ir $i$, un
 * jebkura virsotne, kuras vecāka vecāks ir $i$, un
 * jebkura virsotne, kuras vecāka vecāka vecāks ir $i$, un
 * utt.

Zemāk esošajā attēlā parādīts koka, kas sastāv no $N = 6$ virsotnēm, piemērs.
Katrai virsotnei bultiņa savieno to ar tās vecāku,
 izņemot sakni, kurai nav vecāku.
Virsotnes $2$ apakškoks satur virsotnes $2, 3, 4$ un $5$.
Virsotnes $0$ apakškoks satur visas sešas koka virsotnes
 un virsotnes $4$ apakškoks satur tikai virsotni $4$.

![](subtrees.png "150")

 
Katrai virsotnei tiek piešķirts **svars** - nenegatīvs vesels skaitlis.
Virsotnes $i$ ($0 \leq i < N$) svaru apzīmējam ar $W[i]$.

Jūsu uzdevums ir uzrakstīt programmu, kas atbildēs uz $Q$ vaicājumiem,
kur katru vaicājumu raksturo naturālu skaitļu pāris $(L, R)$.
Atbilde uz vaicājumu aprēķina kārtība aprakstīta tālāk.

Aplūkosim iespēju katrai koka virsotnei piešķirt veselu skaitli,
 ko sauc par **koeficientu**.
Šādu piešķiršanu apraksta **koeficientu virkne** $C[0], \ldots, C[N-1]$ ,
 kur $C[i]$ ($0 \leq i < N$) ir virsotnei $i$ piešķirtais koeficients.
Ņemiet vērā, ka koeficientu virknes elementi var būt negatīvi, $0$ vai pozitīvi.

Vaicājumam $(L, R)$,
 koeficientu virkni sauc par **derīgu**,
 ja katrai virsotnei $i$ ($0 \leq i < N$),
 ir spēkā šāds nosacījums:
 virsotnes $i$ apakškoka virsotņu koeficientu summa
 nav mazāka par $L$ un nav lielāka par $R$.
 
 Dotai koeficientu virknei $C[0], \ldots, C[N-1]$,
 virsotnes $i$ **izmaksas** ir $|C[i]| \cdot W[i]$,
 kur $|C[i]|$ apzīmē $C[i]$ absolūto vērtību.
Visbeidzot, **kopējās izmaksas** ir visu virsotņu izmaksu summa.
Jūsu uzdevums ir katram vaicājumam aprēķināt
 **minimālās kopējās izmaksas**, ko var sasniegt ar kādu derīgu koeficientu virkni.
 
 Var pierādīt, ka jebkuram vaicājumam eksistē vismaz viena derīga koeficientu virkne.

## Implementēšanas detaļas

Jums jāimplementē šādas divas procedūras:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$ : veselu skaitļu masīvi garumā $N$, kas norāda vecākus un svarus.
* Šī procedūra katram testam tiek izsaukta tieši vienreiz
   vērtētāja un jūsu programmas mijiedarbības sākumā.

```
long long query(int L, int R)
```
* $L$, $R$ : veseli skaitļi, kas apraksta vaicājumu.
* Šī procedūra katram testam tiek izsaukta $Q$ reizes pēc `init` izsaukuma.
* Šai procedūrai jāatgriež atbilde uz doto vaicājumu.

## Ierobežojumi

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ katram $i$, kur $1 \leq i < N$
* $0 \leq W[i] \leq 1\,000\,000$ katram $i$, kur $0 \leq i < N$
* Katram vaicājumam $1 \leq L \leq R \leq 1\,000\,000$

## Apakšuzdevumi

| Apakšuzdevums | Punkti  | Papildu ierobežojumi |
| :-----: | :----: | ---------------------- |
|   1     |  $10$  | $Q \leq 10$; $W[P[i]] \leq W[i]$ visiem $i$, kur $1 \leq i < N$
|   2     |  $13$  | $Q \leq 10$; $N \leq 2\,000$
|   3     |  $18$  | $Q \leq 10$; $N \leq 60\,000$
|   4     |  $7$   | $W[i] = 1$ visiem $i$, kur $0 \leq i < N$
|   5     |  $11$  | $W[i] \leq 1$ visiem $i$, kur $0 \leq i < N$
|   6     |  $22$  | $L = 1$
|   7     |  $19$  | Bez papildu ierobežojumiem.



## Piemērs

Aplūkosim šādus izsaukumus:

```
init([-1, 0, 0], [1, 1, 1])
```
Koks sastāv no trim virsotnēm, saknes un tās diviem bērniem.
Visām virsotnēm ir svars $1$.

```
query(1, 1)
```

Šajā vaicājumā $L = R = 1$,
 kas nozīmē, ka koeficientu summai katrā apakškokā jābūt vienādai ar $1$.
Aplūkosim koeficientu virkni $[-1, 1, 1]$.
Koks un atbilstošie koeficienti (ēnotos taisnstūros) ir parādīti attēlā zemāk.

![](ex1.png "150")

Katrai virsotnei $i$ ($0 \leq i < 3$) visu virsotņu koeficientu summa
 $i$ apakškokā ir vienāda ar $1$. 
Tādējādi šī koeficientu virkne ir derīga.
Kopējās izmaksas tiek aprēķinātas šādi:

| Virsotne | Svars | Koeficients | Vērtība                      |
| :----: | :----: | :---------: | :-----------------------: |
|   0    |   1    |     -1      | $\mid -1 \mid \cdot 1 = 1$
|   1    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$
|   2    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$

Tāpēc kopējās izmaksas ir $3$.
Šī ir vienīgā derīgā koeficientu virkne, tāpēc šim izsaukumam vajadzētu atgriezt $3$.

```
query(1, 2)
```
Minimālās kopējās izmaksas šim vaicājumam ir $2$,
 un tiek sasniegtas, ja koeficientu virkne ir $[0, 1, 1]$.

## Paraugvērtētājs

Ievaddatu formāts:

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

kur $L[j]$ un $R[j]$
 (visiem $0 \leq j < Q$)
 ir ievaddatu argumenti $j$-tajā `query` izsaukumā.
Ņemiet vērā, ka ievaddatu otrajā rindā ir **tikai $N-1$ vesels skaitlis**,
 jo paraugvērtētājs nenolasa $P[0]$ vērtību.

Izvaddatu formāts:
```
A[0]
A[1]
...
A[Q-1]
```

kur $A[j]$
 (visiem $0 \leq j < Q$)
 ir $j$-tā `query` izsaukuma atgrieztā vērtība.
