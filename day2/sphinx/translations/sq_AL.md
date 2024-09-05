# Sphinx's Riddle

Sfinksi i Madh ka një enigmë për ju.
Kemi një graf $N$ kulme.
Kulmet janë numra nga  $0$ deri në $N - 1$.
Kemi $M$ skaje tek grafi, duke numëruar nga
 $0$ deri në $M-1$.
 Çdo skaj lidh një çift kulmesh të dallueshme dhe është me dy drejtime.
Konkretisht, për secilën $j$ nga $0$ deri $M - 1$ (përfshihet)
skaj $j$ lidhet me kulmin $X[j]$ dhe $Y[j]$.
Ekziston  një skaj që lidh çdo çift kulmesh.
Dy kulme quhen **të afërt**
 nëse lidhen me një skaj.

Një sekuencë me kulmë $v_0, v_1, \ldots, v_k$ (për $k \ge 0$)
quhet **shteg**nëse ka dy kulme të njëpasnjëshme $v_l$ dhe $v_{l+1}$
 (për secilin  $l$ $ të tillë që $0 \le l \lt k$)
janë ngjitur.

Ne themi se një shteg $v_0, v_1, \ldots, v_k$ **lidh** kulmin $v_0$ dhe $v_k$.
Tek grafi që keni , çdo çift kulmesh është i lidhur me një shteg.

Kemi $N + 1$ ngjyra, duke numëruar nga $0$ deri $N$.
Ngjyra $N$ është speciale dhe quhet  **Ngjyra e Sfinksi**.
Çdo kulmi i caktohet një ngjyrë.
Konkretisht,kulmi $i$ ($0 \le i \lt N$) ka ngjyrën $C[i]$.
Shumë kulme mund të kenë të njëjtën ngjyre, 
dhe mund të ketë dhe ngjyra që nuk i caktohen asnjë kulmi.
Anjë kulm nuk ka ngjyrën e Sfinksi,
 kjo është, $0 \le C[i] \lt N$ ($0 \le i \lt N$).

Një shteg $v_0, v_1, \ldots, v_k$ (for $k \ge 0$)
quhet **njëngjyrësh**
 nëse të gjitha kulmet kanë një njyrë,
 i.e. $C[v_l] = C[v_{l+1}]$ (për secilin $l$ të tillë që $0 \le l \lt k$).
Për më tepër, themi se kulmet
 $p$ dhe$q$ ($0 \le p \lt N$, $0 \le q \lt N$)
janë **komponent njëngjyrësh
**
vetë nëse janë të lidhur me një shteg njëngjyrësh.

Ju i dini kulmet dhe skajet,
 por ju nuk e dini se çfarë ngjyre ka çdo kulm.
Ju doni të gjeni ngjyrën e kulmeve,
 duke përdorur **eksperimentë për ringjyrosje
**.

Në njëeksperimentë për ringjyrosj,
 ju mund të ngjyrosni në mënyrë arbitrare shumë kulme.
Konkretisht,për të kryer një eksperiment ringjyrosje
 ju së pari zgjidhni një matricë $E$ me madhësi $N$,
 për secilën $i$ ($0 \le i \lt N$),
 $E[i]$ ndërmjet $-1$ dhe $N$ **inclusive**.
Pastaj, ngjyra e secilit kulm
 $i$ do bëhet $S[i]$, dhe vlera e  $S[i]$ ëhtë:
* $C[i]$, pra ngjyra origjinale është$i$, if $E[i] = -1$, ose
* $E[i]$, ndryshe.

Vini re se kjo do të thotë që ju mund të përdorni ngjyrën e Sfinksit në ringjyrosjen tuaj.

Më në fund, Sfinksi i Madh njofton
 numrin e komponentëve monokromatikë tek grafi,
 pas vendosjes së ngjyrës së çdo kulmi
 $i$ deri $S[i]$ ($0 \le i \lt N$).
Ngjyrosja e re aplikohet vetëm për këtë eksperiment të veçantë ringjyrosjeje,
 **ngjyrat e të gjitha kulmeve kthehen në ato origjinale pas përfundimit të eksperimentit
**.

Keni për detyrë të gjeni ngjyrat e kulmeve tek grafi
 duke performuar më shumë eksperimente për ringjyrosje
 $2\,750$ .

Ju gjithashtu mund të merrni një pikë të pjesshme
 nëse përcaktoni saktë për çdo çift kulmesh ngjitur,
 nëse kanë të njëjtën ngjyrë.


## Implementation Details

Duhet të zbatoni procedurën më poshtë.

```
std::vector&lt;int&gt; find_colours(int N,
    std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y)
```

* $N$: numri i kulmeve në graf.
* $X$, $Y$: matricat me gjatësi $M$ përshkruajn skajet.
* Procedura duhet të afishij njl matricë $G$ me gjatësi $N$,
   që përfaqëson ngjyrat e kulmeve në grafit.
* Kjo procedurë thirret vetëm një herë për çdo rast testimi.

Procedura e mësipërme mund të bëjë thirrje në procedurën e mëposhtme
 për të kryer eksperimente ringjyrosjeje:

```
int perform_experiment(std::vector&lt;int&gt; E)
```

* $E$: anjë matricë me gjatësi $N$ përcaton sa kulme do të ringjyrosen.
* Kjo procedurë kthen numrin e komponentëve njëngjyrëshe
   pas ringjyrosjes së kulmeve sipas  $E$.
* Kjo procedurë mund të thirret  $2\,750$ herë.

Grader është **jo adaptive**,
ngjyra nga kulmet është rrgulluar para se të thirret  `find_colours` .

## Constraints

* $2 \le N \le 250$
* $N - 1 \le M \le \frac{N \cdot (N - 1)}{2}$
* $0 \le X[j] \lt Y[j] \lt N$ për secilin  $j$ të tillë që  $0 \le j \lt M$.
* $X[j] \neq X[k]$ or $Y[j] \neq Y[k]$
   për secilin  $j$ and $k$ të tillë që  $0 \le j \lt k \lt M$.
* Çdo ciftë me kulme është lidhur me nje shteg.
* $0 \le C[i] \lt N$ për secilin  $i$ të tillë që  $0 \le i \lt N$.

## Subtasks

| Subtask | Score  | Additional Constraints |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = 2$
| 2       | $7$    | $N \le 50$
| 3       | $33$   | Grafi është një shteg: $M = N - 1$ dhe kulme $j$ dhe $j+1$ janë ngjitur($0 \leq j < M$).
| 4       | $21$   | Grafi është i plotë: $M = \frac{N \cdot (N - 1)}{2}$ dhe dy kulme janë ngjytur.
| 5       | $36$   | Nuk ka kufizime shtesë.


Në çdo nëndetyrë, mund të merrni një rezultat të pjesshëm
 nëse programi juaj përcakton saktë
për çdo çift kulmesh ngjitur
 nëse kanë të njëjtën ngjyrë.


Më saktë,
 ju merrni të gjithë rezultatin e një nëndetyre
 nëse në të gjitha rastet e testimit të tij,
matrica $G$ afishohet nga  `find_colours`
është saktësisht e njëjtë me matricën
 $C$
 (i.e. $G[i] = C[i]$
për të gjitha $i$ të cilat $0 \le i \lt N$).
Përndryshe,
 ju merrni $50\%$ të  rezultatin për një nëndetyrë
 nëse ekzistojnë kushtet e mëposhtme
 në të gjitha rastet e testimit:
* $0 \le G[i] \lt N$
   për secilin  $i$ të tillë që $0 \le i \lt N$;
* Për secilin  $j$ të tillë që $0 \le j \lt M$:
  * $G[X[j]] = G[Y[j]]$ if and only if $C[X[j]] = C[Y[j]]$.

## Example

Merrni parasysh thirrjen e mëposhtme.

```
find_colours(4, [0, 1, 0, 0], [1, 2, 2, 3])
```


Për këtë shembull, supozoni se
 ngjyrat (të fshehura) të kulmeve jepen nga
 $C = [2, 0, 0, 0]$.
Kjo afishohet në figurën më poshtë.
Ngjyrat përfaqësohen gjithashtu me numra në etiketat e bardha të bashkangjitura në secilën kulm.


![example.png](sphinx_example.png "230")

Kjo procedurë do të therrasi `perform_experiment` si më poshtë.

```
perform_experiment([-1, -1, -1, -1])
```

Në këtë thirrje, asnjë kulm nuk ngjyroset, pasi të gjitha kulmet ruajnë ngjyrat e tyre origjinale.

Merrni parasysh kulmin
 $1$ dhe kulmin $2$.
Të dyjakanë ngjyrë  $0$ dhe shteg $1, 2$ është një shteg njëngjyrësh.
Si përfundim,kulmi $1$ dhe  $2$ janë në të njëjtin komponent njëngjyresh.

Merrni parasysh kulmin $1$ dhe kulmin $3$.
Edhe pse të dyja kanë ngjyrë $0$,
ato janë në komponentë të ndryshëm njëngjyresh
 pasi nuk ka asnjë shteg njëngjyresh që i lidh ato.

Në përgjithësi, ka
 $3$ komponent njëngjyresh,
 me kulme $\{0\}$, $\{1, 2\}$, dhe $\{3\}$.
kështu kjo afishon $3$.

Tani procedura thërret `perform_experiment` si më poshtë.

```
perform_experiment([0, -1, -1, -1])
```

Në këtë thirrje, vetëm kulmi $0$ është ringjyrosur më ngjyrë
 $0$,
 që rezulton në ngjyrosjen e paraqitur në figurën e mëposhtme.

![example.png](sphinx_order1.png "230")

Kjo thirrje afishon $1$,pasi të gjitha kulmet i përkasin të njëjtës komponentë njëngjyresh

Tani mund të nxjerrim përfundimin se kulmet
 $1$, $2$, dhe $3$ kanë ngjyrë
 $0$.

Procedura thërret  `perform_experiment` si më poshtë.

```
perform_experiment([-1, -1, -1, 2])
```

Në këtë rast, kulmi $3$ është ringjyrosur në ngjyrë
 $2$,
që rezulton në ngjyrosjen e paraqitur në figurën e mëposhtme.

![example.png](sphinx_order2.png "230")

Kjo afishon $2$, siç ka
e $2$ komponentë njëngjyresh,
me kulme $\{0, 3\}$ dhe $\{1, 2\}$ . 
Ne mund ta nxjerrim se kulmi
 $0$ ka ngjyrë $2$.

Procedura `find_colours` afishon matricën $[2, 0, 0, 0]$.
 $C = [2, 0, 0, 0]$,jepen pikët e plotë.


Vini re se ka edhe shumë vlera që kthehen , për të cilat
 $50\%$ do të jepej rezultati
, si për shembull $[1, 2, 2, 2]$ or $[1, 2, 2, 3]$.

## Sample Grader

Input format:

```
N  M
C[0]  C[1] ... C[N-1]
X[0]  Y[0]
X[1]  Y[1]
...
X[M-1]  Y[M-1]
```

Output format:

```
L  Q
G[0]  G[1] ... G[L-1]
```

Ketu, $L$ është gjatësia e matricës $G$ që afishohet nga `find_colours`,
 dhe $Q$ është numri i thirrjeve nga `perform_experiment`.
