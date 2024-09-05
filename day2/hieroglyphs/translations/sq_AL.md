# Hieroglyphs
Një ekip studiuesish po studiojnë ngjashmëritë midis sekuencave të hieroglifeve.
Ata paraqesin çdo hieroglifi menjë numër të plotë jo negativ.
Për të kryer studimin e tyre,
 ata përdorin konceptet e mëposhtme për sekuencat.


Për një sekuencë të caktuar  $A$,
një sekuencë  $S$ quhet një **nënsekuecë** e  $A$
vetëm nëse  $S$ mund të merret
duke hequr disa elementë (ndoshta asnjë) nga  $A$.

Tabela më poshtë tregon shembuj nga nënsekuncat e sekuencës  $A = [3, 2, 1, 2]$.

| Subsequence    | How it can be obtained from $A$ |
|----------------|---------------------------------|
| [3, 2, 1, 2] | No elements are removed.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] or [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Nga ana tjetër, $[3, 3]$ ose $[1, 3]$ nuk janë nënsekuencatë   of $A$.

Konsideroni dy sekuenca të hieroglifeve, $A$ dhe $B$.
Një sekuencë $S$ quhet **nënsekuencë e përnashkët ** e $A$ dhe $B$
 vetëm nëse $S$ është një nënsekuncë e  $A$ dhe $B$.
Për më tepër, ne themi se një sekuencë  $U$ iështë një  **nënsekuencë e përnashkët universale ** e  $A$ dhe  $B$
vetëm nëse plotësohen dy kushtet e mëposhtme:
* $U$është një nënsekuencë e përnashkët e  $A$ dhe $B$.
* Çdo nënsekuencë e përnashkët e   $A$ dhe  $B$ është një nënsekuncë e $U$.

Mund të tregohet se dy sekuenca $A$ dhe $B$
kanë më së shumti një e përnashkët universale.

Studiuesit kanë gjetur dy sekuenca hieroglifesh  $A$ dhe $B$.
Sekuenca e  $A$ përbëhet nga hieroglifi  $N$ 
 dhe sekuenca $B$ përbëhet nga hieroglifi $M$ .
Ndihmoni studiuesit të llogaritin
 një nënsekuencë të përnashkët universale të sekuencës $A$ dhe $B$,
ose përcaktoni se një sekuencë e tillë nuk ekziston.Ju duhet të zbatoni procedurën si më poshtë.


## Implementation details

You should implement the following procedure.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$:matrica me gjatësi $N$ përshkruar sekuencën e parë.
* $B$:matrica me gjatësi $M$ depërshkruar sekuencën e dytë.
* Nëse ekziston një nënsekuencë e përnashkët universale për $A$ dhe $B$,
 procedura do afishoj një matricë që the procedure should return an array përmbankëtë sekuencën.
  Përndryshe, procedura duhet të afishoj  $[-1]$
   (një matricë me gjatësi  $1$, i cili ka vetëm elementin $-1$).
* Kjo procedurë thirret vetëm një herë për çdo rast testimi.


## Constraints

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ për secilin   $i$  të tillë që  $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ për secilin   $j$  të tillë që  $0 \leq j < M$

## Subtasks

| Subtask | Score  | Additional Constraints |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; secila  $A$ dhe $B$ të dyja përbëhen nga $N$ numra të plotë të dallueshëm midis  $0$ dhe   $N-1$ (duke përfshirëse)
| 2       | $15$   |Për çdo numër të plotë $k$, numri i elementeve të  $A$ është e barabart me $k$ *plus* numrat e elementeve të $B$ të barabarta me $k$ është më së shumti $3$.
| 3       | $10$   | $A[i] \leq 1$ për secilën $i$ të tilla që $0 \leq i < N$; $B[j] \leq 1$ për secilën  $j$ të tilla që $0 \leq j < M$
| 4       | $16$   | Ekziston një nënsekuencë e përnashkët universale për $A$ dhe  $B$.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | Nuk ka kufizime shtesë.


## Examples

### Example 1

Merrni parasysh thirrjen e mëposhtme.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Këtu, sekuencat e zakonshme të
 $A$ adhe $B$ si më poshtë:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ and $[0, 1, 0, 2]$.

$[0, 1, 0, 2]$ është nënsekuencë e përnashkët $A$ dhe  $B$, dhe të gjitha 
 nënsekuencë e përnashkët $A$ dhe $B$ janë nënprocedura e  $[0, 1, 0, 2]$,
procedura do afishoj $[0, 1, 0, 2]$.

### Example 2

Merrni parasysh thirrjen e mëposhtme.


```
ucs([0, 0, 2], [1, 1])
```

Këtu, e vetmja nënsekuencë e përnashkët është  $A$ dhe $B$ është një sekuencë boshe $[\ ]$.
Procedura afishon një matricë boshe $[\ ]$.


### Example 3

Merrni parasysh thirrjen e mëposhtme.

```
ucs([0, 1, 0], [1, 0, 1])
```

Këto, nënsekuencë e përnashkët e $A$ dhe  $B$ është
 $[\ ], [0], [1], [0, 1]$ and $[1, 0]$.
Mund të shikojm që ënsekuencë e përnashkët universale nuk ekziston.
Procedura do të afishoj $[-1]$.

## Sample Grader

Input format:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Output format:

```
T
R[0]  R[1]  ...  R[T-1]
```

Ketu , $R$ është matrica që afishohet nga `ucs`dhe $T$ është gjatësia.
