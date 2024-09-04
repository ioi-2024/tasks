# Nile

Ju dëshironi të transportoni  $N$ objekte historike përmes Nilit. Objektet historike numërohen nga $0$ në $N-1$.
Pesha e objektit i  $i$ ($0 \leq i < N$) është $W[i]$.

Për të transportuar objektet historike përdoren varka specifike.
Secila nga varkat   **mund të mbajë dy** objektet historike.

* Nëse dëshironi të vendosni një objekt të vetëm në një varkë, pesha e objektit mund të jetë arbitrare.
*Nëse dëshironi të vendosni dy objekte në të njëjtën varkë, duhet të siguroheni që varka të jetë e ekuilibruar. Specifikisht,ju mund të dërgoni objektet historike $p$ dhe $q$ ($0 \leq p < q < N$) në të njëjtën varkë vetëm nëse diferenca absolute midis peshave të tyre është maksimumi  $D$,
kjo është  $|W[p] - W[q]| \leq D$.

Për të transoprtuar një objekt historik, ju duhet të paguani një kosto që varet nga numri i objekteve të vendosura tek e njëjta varkë. Kostoja për trasportin e objektit historik i $i$ ($0 \leq i < N$) është:

* $A[i]$,nëse vendos një  objektin historik në varkën të vetme,ose
* $B[i]$, nëse e vendos në një varkë me disa objekte historike të tjera.

Shënim në rastin e fundit, ju duhet të paguani për të dy objektet historikenë varkë.Specifikisht nqs ju dëshironi të dërgoni objektin historik $p$ dhe $q$ ($0 \leq p < q < N$) me të njëjtën varkë,duhet të paguani  $B[p] + B[q]$.

Dërgimi i një objekti historik të vetëm me një varkë është gjithmonë më i shtrenjtë se dërgimi bashkë me një tjetër,kështu   $B[i] < A[i]$ për të gjitha $i$  $0 \leq i < N$.

Fatkeqësisht, lumi është shumë i paparashikueshëm dhe vlera e  $D$ ndryshon shpesh.
Detyra juaj është që të përgjiigjeni në  $Q$ pyetje duke numëruar nga  $0$ deri $Q-1$.
Pyetjet janë përshkruar në matric  $E$  me gjatësi $Q$.
Përgjigja në pyetjen $j$ ($0 \leq j < Q$) është kostoja minimale nga transporti total i të gjithave is $N$ objektet historikenë,
 kur vlera e $D$ është e barabart me  $E[j]$.

## Implementation Details

Duhet të zbatoni proceduren më poshtë:

```
std::vector&lt;long long&gt; calculate_costs(
    std::vector&lt;int&gt; W, std::vector&lt;int&gt; A, 
    std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```

* $W$, $A$, $B$: array me numra të plotë me gjatësi $N$, përshkruajnë peshën e objektit historik dhe koston e transportit.
* $E$: array me numra të plotë me gjatësi   $Q$ duke përshkruar vlerat e ndryshme të  $D$.
* Kjo procedure duhet të kthejë array $R$ me numra të plotë   $Q$ që përmbajnë koston totale minimale të transportit të objekteve historike, ku $R[j]$ jep coston kur vlera e $D$ është $E[j]$ (për secilën $j$
  të tillë që  $0 \leq j < Q$).
* Kjo procedurë thirret një herë për çdo rast testimi.

## Constraints

* $1 \leq N \leq 100\,000$
* $1 \leq Q \leq 100\,000$
* $1 \leq W[i] \leq 10^{9}$
   for each $i$ such that $0 \leq i < N$
* $1 \leq B[i] < A[i] \leq 10^{9}$
   for each $i$ such that $0 \leq i < N$
* $1 \leq E[j] \leq 10^{9}$
   for each $j$ such that $0 \leq j < Q$

## Subtasks

| Subtask | Score  | Additional Constraints |
| :-----: | :----: | ---------------------- |
| 1       | $6$    | $Q \leq 5$; $N \leq 2000$; $W[i] = 1$ for each $i$ such that $0 \leq i < N$
| 2       | $13$   | $Q \leq 5$; $W[i] = i+1$ for each $i$ such that $0 \leq i < N$
| 3       | $17$   | $Q \leq 5$; $A[i] = 2$ and $B[i] = 1$ for each $i$ such that $0 \leq i < N$
| 4       | $11$   | $Q \leq 5$; $N \leq 2000$
| 5       | $20$   | $Q \leq 5$
| 6       | $15$   | $A[i] = 2$ and $B[i] = 1$ for each $i$ such that $0 \leq i < N$
| 7       | $18$   | No additional constraints.

## Examples

### Example 1

Consider the following call.

```
calculate_costs([15, 12, 2, 10, 21],
                [5, 4, 5, 6, 3],
                [1, 2, 2, 3, 2],
                [5, 9, 1])
```

Në këtë shembull kemi  $N = 5$  objektit historik dhe  $Q = 3$ pyetje.

Në pyetjen e parë, $D = 5$.
Mund të dërgoni objektet historike  $0$ dhe $3$ në një varkë  (që nga  $|15 - 10| \leq 5$)dhe objektet e mbetura në varka të veçanta. Kjo jep koston minimale të transportit të të gjitha objekteve historike, e cila ështëNë pyetjen e parë, $D = 5$.
Mund të dërgoni o $1+4+5+3+3 = 16$.

In the second question, $D = 9$.
Mund të dërgoni objektet historike $0$ dhe $1$ në një varkë  (që nga $|15 - 12| \leq 9$) dhe dërgoni objektet historike $2$ dhe $3$në një varkë (që nga  $|2 - 10| \leq 9$).
Artefaktet e mbetura mund të dërgohen me 
varka të ndryshme. Kjo jep koston minimale të transportit të të gjitha objektet, e cila është  $1+2+2+3+3 = 11$.

Në pyetjen e fundit , $D = 1$. Ju duhet të dërgoni çdo artefaktë në varkën të ndryshme. Kjo jep koston minimale të transportit të  gjitha objektet historike, e cila është  $5+4+5+6+3 = 23$.

Prandaj,kjo procedur do të japi  $[16, 11, 23]$.


## Sample Grader

Input format:

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

Output format:

```
R[0]
R[1]
...
R[S-1]
```

Këtu, $S$ është gjatësia e array $R$ nga  `calculate_costs`.
