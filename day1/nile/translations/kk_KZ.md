# Nile

Сіз Ніл арқылы $N$ артефакттарды тасымалдағыңыз келеді. 
Артефакттар $0$-ден бастап $N-1$-ге дейін нөмірленген.
$i$-ші ($0 \leq i < N$) артефакттың салмағы  $W[i]$-ға тең.

Артефакттарды тасымалдау үшін сіз арнайы қайықтарды пайдаланасыз.
Әрбір қайық **ең көбі екі** артефактты алып жүре алады.

* Егер сіз бір қайыққа бір артефактты салуды шешсеңіз, артефакт салмағы кез келген бола алады.
* Егер сіз бір қайыққа екі артефакттарды салғыңыз келсе, қайықтың тепе-теңдігіне көз жеткізуіңіз керек. 
Атап айтқанда, бір қайыққа $p$ және $q$ ($0 \leq p < q < N$) артефакттарын салу үшін олардың салмақтары арасындағы абсолютті айырмашылығы $D$ мәнінен аспауы керек, яғни $|W[p] - W[q]| \leq D$ .

Артефактты тасымалдау үшін сіз ақы төлеуіңіз керек, бұл бір қайықта тасымалданатын артефакттардың санына байланысты. $i$-ші ($0 \leq i < N$) артефактты тасымалдау құны:

* $A[i]$, егер сіз артефактты жалғыз өзің қайыққа салсаңыз немесе
* $B[i]$, егер сіз оны басқа артефактпен бірге бір қайыққа салсаңыз.

Назар аударыңыз, соңғы жағдайда сіз қайықтағы екі артефактқада төлеуіңіз керек. 
Атап айтқанда, егер сіз бір қайықта $p$ және $q$ ($0 \leq p < q < N$) артефакттарын жіберуді шешсеңіз, $B[p] + B[q]$ төлеуіңіз керек.

Артефактты бір қайықпен жіберу әрқашан оны басқа артефактпен бірге бір қайықта жіберуден гөрі қымбатырақ, сондықтан барлық $i$($0 \leq i < N$) үшін $B[i] < A[i]$.

Өкінішке орай, өзен өте күтімсіз және $D$ мәні жиі өзгеріп отырады.
Сізге $0$-ден $Q-1$-ге дейін нөмірленген $Q$ сұрақтарына жауап беруіңіз керек.
Сұрақтар ұзындығы $Q$ болатын $E$ массивімен сипатталады.
$j$-ші ($0 \leq j < Q$) сұрақтың жауабы $D$ мәні $E[j]$ мәніне тең болғанда барлық $N$ артефакттарды тасымалдаудың ең төменгі жалпы құнына тең.

## Implementation Details

Сіз келесі функцияны іске асыруыңыз керек.

```
std::vector&lt;long long&gt; calculate_costs(
    std::vector&lt;int&gt; W, std::vector&lt;int&gt; A, 
    std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```

* $W$, $A$, $B$: артефакттардың салмағын және оларды тасымалдау құнын сипаттайтын ұзындығы $N$ болатын бүтін сандар массивтері.
* $E$: әрбір сұрақ үшін $D$ мәнін сипаттайтын ұзындығы $Q$ болатын бүтін сандар массиві.
* Бұл функция $Q$ бүтін сандардан тұратын артефакттарды тасымалдаудың ең аз жалпы құнын қамтитын $R$ массивін қайтаруы керек, мұндағы $R[j]$ мәні $D$ мәні $E[j]$-ға тең болған кездегі жалпы құнына тең ($0 \leq j < Q$ орындалатындай әр $j$ үшін).
* Бұл функция әрбір сынақ жағдайы үшін бір рет шақырылады.

## Constraints

* $1 \leq N \leq 100\,000$
* $1 \leq Q \leq 100\,000$
* $1 \leq W[i] \leq 10^{9}$
   әрбір $i$($0 \leq i < N$) үшін  
* $1 \leq B[i] < A[i] \leq 10^{9}$
   әрбір $i$($0 \leq i < N$) үшін 
* $1 \leq E[j] \leq 10^{9}$
   әрбір $j$($0 \leq j < Q$) үшін 

## Subtasks

| Ішкі есеп | Ұпай | Қосымша шектеулер |
| :-----: | :----: | -------------------------------- |
| 1 | $6$ | $Q \leq 5$; $N \leq 2000$; әрбір $i$($0 \leq i < N$) үшін $W[i] = 1$ 
| 2 | $13$ | $Q \leq 5$; әрбір $i$($0 \leq i < N$) үшін $W[i] = i+1$ 
| 3 | $17$ | $Q \leq 5$;  әрбір $i$($0 \leq i < N$) үшін $A[i] = 2$ және $B[i] = 1$
| 4 | $11$ | $Q \leq 5$; $N \leq 2000$
| 5 | $20$ | $Q \leq 5$
| 6 | $15$ | әрбір $i$($0 \leq i < N$) үшін $A[i] = 2$ және $B[i] = 1$
| 7 | $18$ | Қосымша шектеулер жоқ.

## Example

Келесі мысалды қарастырыңыз.

```
calculate_costs([15, 12, 2, 10, 21],
 [5, 4, 5, 6, 3],
 [1, 2, 2, 3, 2],
 [5, 9, 1])
```

Бұл мысалда бізде $N = 5$ артефакттар және $Q = 3$ сұрақтар бар.

Бірінші сұрақта $D = 5$.
Сіз $0$-ші және $3$-ші артефакттарды бір қайықта ($|15 - 10| \leq 5$ болғандықтан) және қалған артефакттарды бөлек қайықтарда жібере аласыз.
Бұл барлық артефакттарды тасымалдаудың ең төменгі құнын береді, яғни $1+4+5+3+3 = 16$.

Екінші сұрақта $D = 9$.
Сіз $0$-ші және $1$-ші артефакттарды бір қайықта ($|15 - 12| \leq 9$ болғандықтан) және $2$-ші және $3$-ші артефакттарды бір қайықта ($|2 - 10| \leq 9$ болғандықтан) жібере аласыз.
Қалған артефактты бөлек қайықпен жіберуге болады.
Бұл барлық артефакттарды тасымалдаудың ең төменгі құнын береді, яғни $1+2+2+3+3 = 11$.

Соңғы сұрақта $D = 1$. Әр артефактты өз қайығында жіберу керек.
Бұл барлық артефакттарды тасымалдаудың ең төменгі құнын береді, яғни $5+4+5+6+3 = 23$.

Демек, бұл функция $[16, 11, 23]$ қайтаруы керек.


## Sample Grader

Енгізу форматы:

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

Шығару форматы:

```
R[0]
R[1]
...
R[S-1]
```

Мұнда $S$ мәні `calculate_costs` арқылы қайтарылатын $R$ массивінің ұзындығына тең.