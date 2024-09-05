# Mosaic

Salma planifikon të ngjyros një mozaik balte në një mur.
Mozaiku është një $N \times N$ rrjetë,
 $N^2$ fillimisht i pangjyrosur
 $1 \times 1$ pllaka katrore.
 Rreshtat e mozaikut numërohen nga
 $0$ deri $N-1$ nga lart poshtë,
 dhe kolonat numërohen nga  $0$ deri $N-1$ nga e majta në të djathtë.
Pllaka në rresht $i$  dhe kolona $j$ ($0 \leq i < N$, $0 \leq j < N$) shënohet me
 $(i,j)$.
Çco pllakë duhet ngjyrosur ose e bardhë (shënohet me $0$) ose e zezë (shënohet me $1$).

Për të ngjyrosur mozaikun
, Salma fillimisht zgjedh dy matrica
 $X$ dhe $Y$ me gjatësi  $N$,secila  përbërë nga vlera
 $0$ dhe $1$,të tilla që
 $X[0] = Y[0]$.
Ajo ngjyros pllakat e rreshtit më të lartë
 (row $0$) sipas matricës $X$,
të tillë që ngjyra e pllakës
  $(0,j)$ është $X[j]$ ($0 \leq j < N$).
Ajo gjithashtu ngjyron pllakat e kolonës më të majtë
 (column $0$) sipas matricës $Y$,
të tillë që ngjyra e pllakës
 $(i,0)$ is $Y[i]$ ($0 \leq i < N$).

Pastaj ajo përsërit hapat e mëposhtëm derisa të gjitha pllakat të jenë të ngjyrosura:
* Ajo gjen ndonjë*pa ngjyrë* tile $(i,j)$ siç është fqinji lart (tile $(i-1, j)$) dhe fqinji i majtë
 (tile $(i, j-1)$)
 janë të dyja *tashmë me ngjyrë*.
* Pastaj, ajo ngjyros pllakën
 $(i,j)$ e zezë nëse të dy këta fqinjë janë të bardhë;
përndryshe, ajo ngjyros pllakën
 $(i, j)$ të bardhë.

Mund të tregohet se ngjyrat përfundimtare e pllakave nuk varen 
sipas radhës me të cilën Salma po i ngjyros.

Yasmin është shumë kurioze për ngjyrat e pllakave në mozaik.
Ajo pyet Salmën $Q$ pyetje, të numëruara nga  $0$ deri në $Q-1$.
në petjen $k$ ($0 \leq k < Q$),
Yasmin specifikon një nëndrejtkëndësh të mozaikut :
* Rreshti më i lartë
 $T[k]$ dhe rreshti më i poshtëm $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* Kolona më e majtë $L[k]$ dhe kolona më e djathtë $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

Përgjigja e pyetjes është numri i pllakave të zeza në këtë nëndrejtkëndësh.
Konkretisht, Salma duhet të gjejë sa pllaka $(i, j)$ ekzistojn,
 të tilla që $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$,
dhe ngjyra e pllakës
 $(i,j)$ është e zezë.
Shkruani një program që u përgjigjet pyetjeve të Yasmin.

## Implementation Details

Duhet të zbatoni procedurën më poshtë.

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: matrica me gjatësi $N$ 
duke përshkruar ngjyrat e pllakave
 në rreshtin më të lartë dhe në kolonën më të majtë, përkatësisht.
* $T$, $B$, $L$, $R$: matrica me gjatësi $Q$ duke përshkruar pyetjet e bëra nga Yasmin.
* Procedura duhet të afishoj një matricë $C$ ome gjatësi $Q$,
 të tillë që  $C[k]$ jep përgjigjen e pyetjes
 $k$ ($0 \leq k < Q$).
* Kjo procedurë thirret saktësisht një herë për çdo rast testimi.


## Constraints

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ and $Y[i] \in \{0, 1\}$
 for each $i$ such that $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ and $0 \leq L[k] \leq R[k] < N$
 for each $k$ such that $0 \leq k < Q$

## Subtasks

| Subtask | Score  | Additional Constraints |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ (for each $k$ such that $0 \leq k < Q$)
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ (for each $i$ such that $0 \leq i < N$)
| 6       | $22$   | $T[k] = B[k]$ and $L[k] = R[k]$ (for each $k$ such that $0 \leq k < Q$)
| 7       | $19$   | $T[k] = B[k]$ (for each $k$ such that $0 \leq k < Q$)
| 8       | $22$   | No additional constraints.

## Example

Merrni parasysh thirrjen e mëposhtme.

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Ky shembull është ilustruar në fotot e mëposhtme.
Fotografia e majtë tregon ngjyrat e pllakave në mozaik.
Imazhet e mesme dhe të djathta tregojnë nëndrejtkëndëshat
Jasmin pyeti përkatësisht pyetjen e parë dhe të dytë.


![](example.png "550")

Përgjigjet e pyetjeve
 (pra numrat e njëshave në drejtkëndëshat e hijezuar)
 janë 7 dhe 3.
Prandaj, procedura duhet të kthehet
 $[7, 3]$.

## Sample Grader

Input format:

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

Output format:

```
C[0]
C[1]
...
C[S-1]
```

Ketu, $S$ është gjatësia e matricës $C$ e afishuar nga `mosaic`.
