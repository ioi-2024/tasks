# Tree
 $0$-ден бастап $N-1$-ге дейін нөмірленген $N$ **төбеден** тұратын **дарақты** қарастырайық.
$0$ төбесі **түбір** деп аталады.
Түбірден басқа әрбір төбенің жалғыз **әкесі** болады.
$1 \leq i < N$ орындалатын әрбір $i$ үшін,  $i$ төбесінің әкесі $P[i]$ болады, мұндағы $P[i] < i$ .
Біз сондай-ақ $P[0] = -1$ деп есептейміз.

Кез келген $i$ төбесі үшін ( $0 \leq i < N$ ), $i$ **ішкі дарағы** келесі төбелердің жиыны болып табылады:
 * $i$ , және
 * әкесі $i$ болатын кез келген төбе және
 * әкесінің әкесі $i$ болатын кез келген төбе және
 * әкесінің әкесінің әкесі $i$ болатын кез келген төбе және
 * т.б.

Төмендегі суретте $N = 6$ төбеден тұратын мысал дарақ көрсетілген.
Әрбір көрсеткіш төбені өзінің әкесімен қосады, тек әкесі жоқ түбірден басқа.
$2$ төбесінің ішкі дарағында $2, 3, 4$ және $5$ төбелері бар.
$0$ төбесінің ішкі дарағы барлық $6$ төбеден тұрады, ал $4$ төбесінің ішкі дарағы тек $4$ төбесін қамтиды.

![](subtrees.png "150")

Әрбір төбенің белгілі бір **салмағы** ретінде теріс емес бүтін сан тағайындалады. $i$ ( $0 \leq i < N$ ) төбесінің салмағын $W[i]$ деп белгілейміз.

Сіздің тапсырмаңыз - $(L, R)$ оң бүтін сандар жұбымен көрсетілген $Q$ сұрауларына жауап беретін бағдарламаны жазу. Сұрауға жауапты келесідей есептеу керек.

Дарақтың әрбір төбесіне **коэффицент** деп аталатын бүтін санды тағайындауды қарастырыңыз.
Мұндай тағайындау $C[0], \ldots, C[N-1]$ ретімен сипатталады, мұндағы $C[i]$ ( $0 \leq i < N$ ) $i$ төбесіне тағайындалған коэффициент. 
Бұл тізбекті **коэффиценттер тізбегі** деп атайық.
Коэффициенттер тізбегінің элементтері теріс, $0$ немесе оң болуы да мүмкін екенін ескеріңіз.

$(L, R)$ сұрауы үшін коэффициент тізбегі **жарамды** деп аталады, егер әрбір $i$ төбесі үшін ( $0 \leq i < N$ ) $i$ төбесінің ішкі дарағындағы төбелердің коэффициенттерінің қосындысы $L$ -ден кем емес және $R$ -ден көп емес болатын болса.
 
$C[0], \ldots, C[N-1]$ берілген коэффициент тізбегі үшін $i$ төбесінің **құны** $|C[i]| \cdot W[i]$ , мұндағы $|C[i]|$ дегеніміз  $C[i]$-дың абсолютті мәнін білдіреді.
Соңында, **жалпы құн** барлық төбелердің құнынын қосындысы болып табылады.
Сіздің тапсырмаңыз - әрбір сұрау үшін жарамды коэффициент тізбегі арқылы қол жеткізуге болатын **ең төменгі жалпы құнды** есептеу.

Кез келген сұрау үшін кем дегенде бір жарамды коэффициент тізбегі бар екенін көрсетуге болады.
## Implementation Details

Сізге келесі екі функцияны іске асыру керек:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```
* $P$ , $W$ : ұзындықтары $N$ болатын әкелер мен салмақтарды көрсететін массив.
* Бұл функция әрбір тест жағдайында грейдер мен сіздің бағдарламаңыз арасындағы өзара әрекеттесу басында бір рет шақырылады.

```
long long query(int L, int R)
```
* $L$, $R$: сұрауларды сипаттайтын бүтін сандар.
* Бұл функция әрбір сынақ жағдайында `init` шақырылғаннан кейін $Q$ рет шақырылады.
* Бұл функция берілген сұрауға жауапты қайтаруы керек.


## Constraints

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ кез келген $i$ ($1 \leq i < N$) үшін 
* $0 \leq W[i] \leq 1\,000\,000$ кез келген $i$ ($0 \leq i < N$) үшін 
* $1 \leq L \leq R \leq 1\,000\,000$ кез келген сұрау үшін

## Subtasks

| Ішкі есеп | Ұпай  | Қосымша шектеу |
| :-----: | :----: | ---------------------- |
|   1     |  $10$  | $Q \leq 10$; $W[P[i]] \leq W[i]$ кез келген $i$ ($1 \leq i < N$) үшін 
|   2     |  $13$  | $Q \leq 10$; $N \leq 2\,000$
|   3     |  $18$  | $Q \leq 10$; $N \leq 60\,000$
|   4     |  $7$   | $W[i] = 1$ кез келген $i$ ($0 \leq i < N$) үшін 
|   5     |  $11$  | $W[i] \leq 1$ кез келген $i$ ($0 \leq i < N$) үшін
|   6     |  $22$  | $L = 1$
|   7     |  $19$  | Қосымша шектеу жоқ.



## Examples

Келесі функция шақырылуын қарастырайық:

```
init([-1, 0, 0], [1, 1, 1])
```
Дарақта $3$ төбе бар: түбірі және оның $2$ баласы.
Әр төбенің салмағы $1$.

```
query(1, 1)
```

Бұл сұрауда $L = R = 1$, ол дегеніміз әрбір төбенің ішкі дарағының коэффициентер қосындысы $1$ болуы керек.
$[-1, 1, 1]$ коэффициенттер тізбегін қарастырайық.
Дарақ және сәйкес коэффициенттер (көлеңкеленген шаршыларда) төмендегі сүретте көрсетілген.

![](ex1.png "150")

Әрбір $i$ төбесі үшін ( $0 \leq i < 3$ ), $i$ ішкі дарағындағы барлық төбелердің коэффициенттерінің қосындысы $1$-ге тең. Демек, бұл коэффициенттер тізбегі жарамды.
Жалпы құн келесідей есептеледі:


| Төбе | Салмағы | Коэффициенті | Құны                      |
| :----: | :----: | :---------: | :-----------------------: |
|   0    |   1    |     -1      | $\mid -1 \mid \cdot 1 = 1$
|   1    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$
|   2    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$

Сондықтан жалпы құны $3$ болады.
Бұл жалғыз жарамды коэффициенттер тізбегі болғандықтан бұл шақырылуы $3$ қайтаруы керек.

```
query(1, 2)
```
Бұл сұраудың ең төменгі жалпы құны $2$ құрайды және коэффициенттер тізбегі $[0, 1, 1]$ болғанда қол жеткізіледі.
## Sample Grader

Үлгі грейдер енгізбені келесі форматта оқиды:

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

мұндағы $L[j]$ және $R[j]$ ($0 \leq j < Q$ үшін) $j$-ші `query` шақыруындағы кіріс аргументтері болып табылады.
Енгізудің екінші жолында **тек $N-1$ бүтін сандар** бар екенін ескеріңіз, өйткені үлгі грейдер $P[0]$ мәнін оқымайды.

Үлгі бағалаушы жауабыңызды келесі форматта басып шығарады:
```
A[0]
A[1]
...
A[Q-1]
```

мұндағы $A[j]$  ($0 \leq j < Q$ үшін)  $j$-ші `query` шақыруындағы қайтарылған мән.