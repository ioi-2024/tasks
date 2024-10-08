# Sphinx's Riddle

Մեծ Սֆինքսը ձեզ համար հանելուկ ունի։ 
Տրված է $N$ գագաթներով գրաֆ։
Գագաթները համարակալված են $0$-ից $N - 1$ թվերով։
Գրաֆն ունի $M$ հատ կող։
Յուրաքանչյուր կող միացնում է տարբեր գագաթների զույգ։ Կողերը երկկողմանի են։
Երկու գագաթ կոչվում են  **կից**,
 եթե նրանք միացված են կողով։
Մասնավորապես, յուրաքանչյուր $j$-ի համար, $0$-ից $M - 1$, ներառյալ,
 $X[j]$ և $Y[j]$ գագաթները կից են։
Յուրաքանչյուր երկու գագաթներ միացված են առավելագույնը մեկ կողով։

$v_0, v_1, \ldots, v_k$ (for $k \ge 0$) գագաթների հաջորդականությունը
 կոչվում է **ճանապարհ**
 եթե բոլոր իրար հաջորդող $v_l$ և $v_{l+1}$ գագաթները
 (որտեղ $0 \le l \lt k$) կից են։
 Կասենք, որ $v_0, v_1, \ldots, v_k$  ճանապարհը **միացնում է իրար**  $v_0$ և $v_k$ գագաթները։
Ձեզ տրված գրաֆում ցանկացած երկու գագաթ ինչ-որ ճանապարհով իրար են միացված։

Կան $N + 1$ գույներ, համարակալված $0$-ից $N$-ով։
$N$ համարի գույն հատուկ է, և կոչվում է **Սֆինքսի գույն**։
Յուրաքանչյուր գագաթի մեկ գույն է վերագրված։
Մասնավորապես, $i$ ($0 \le i \lt N$) գագաթի գույնը $C[i]$ է։
Տարբեր գագաթներ կարող են նույն գույնով ներկված լինել, և կարող են լինել չօգտագործված գույներ։
Ոչ մի գագաթ սֆինքսի գույնը չունի,
 այսինքն, $0 \le C[i] \lt N$ ($0 \le i \lt N$)։

$v_0, v_1, \ldots, v_k$ (for $k \ge 0$) ճանապարհը 
կոչվում է **մոնոխրոմատիկ**
 եթե նրա բոլոր գագաթների գույնը նույնն է,
 այսինքն $C[v_l] = C[v_{l+1}]$ (որտեղ $0 \le l \lt k$)։
Բացի այդ, կասենք, որ $p$ և $q$ ($0 \le p \lt N$, $0 \le q \lt N$) գագաթները 
 պատկանում են միևնույն **մոնոխրոմատիկ կոմպոնենտին**
 այն և միայն այն ժամանակ, եթե նրանք կապված են մոնոխրոմատիկ ճանապարհով։

Դուք գիտեք գագաթները և կողերը,
 բայց դուք չգիտեք, թե որ գագաթն ինչ գույն ունի։
Դուք ցանկանում եք պարզել գագաթների գույները, 
կատարելով **վերաներկման էքսպերիմենտներ**։

Վերաներկման էքսպերիմենտի ժամանակ 
 դուք կարող եք վերաներկել կամայական քանակությամբ գագաթներ։
Մասնավորապես, վերաներկման էքսպերիմենտ կատարելու համար
 դուք սկզբում ընտրում եք $N$ երկարության $E$ զանգված,
 որտեղ յուրաքանչյուր $i$-ի ($0 \le i \lt N$) համար,
 $E[i]$-ն պատկանում է $-1$-ից $N$ տիրույթին **ներառյալ ծայրակետերը**։
Ապա, յուրաքանչյուր $i$ գագաթի գույնը դառնում է $S[i]$, որտեղ $S[i]$-ի արժեքը․
* $C[i]$ է, այսինքն, $i$-ի սկզբնական գույնը, եթե $E[i] = -1$, կամ
* $E[i]$, հակառակ դեպքում։

Նկատենք, որ սա նշանակում է, որ դուք վերանկերկման համար կարող եք օգտագործել Սֆինքսի գույնը։

Վերջում, $i$ գագաթի գույնը $S[i]$ ($0 \le i \lt N$) դարձնելուց հետո, Մեծ Սֆինքսը հայտարարում է 
գրաֆում մոնոխրոմատիկ կոմպոնենտների քանակը։
Նոր գունավորումը կիրառվում է միայն տվյալ մասնավոր վերաներկման էքսպերիմենտում,
 այսինքն **բոլոր գագաթների գույները վերադառնում են իրենց սկզբնականին էքսպերիմենտի ավարտից հետո**.

Ձեր խնդիրն է պարզել գրաֆի գագաթների գույները, կատարելով առավելագյունը վերաներկման $2\,750$ էքսպերիմենտ։ 
Դուք կարող եք նաև ստանալ մասնակի միավոր, եթե բոլոր կից գագաթների համար ճիշտ պարզեք, նրանք նույն գույնի են, թե ոչ։

## Իրականացման մանրամասներ

Դուք պետք է իրականացնեք հետևյալ ֆունկցիան․

```
std::vector&lt;int&gt; find_colours(int N,
    std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y)
```

* $N$․ գրաֆում գագաթների քանակը։
* $X$, $Y$․ կողերը նկարագրող $M$ երկարության զանգվածներ։
* Այս ֆունկցիան պետք է վերադարձնի $N$ երկարության $G$ զանգված,
   որը ներկայացնում է գրաֆի գագաթների գույները։
* Այս ֆունկցիան կանչվում է ճիշտ մեկ անգամ յուրաքանչյուր թեստի համար։

Վերաներկման էքսպերիմենտներ կատարելու համար այս ֆունկցիան կարող է կատարել հետևյալ ֆունկցիայի կանչեր․

```
int perform_experiment(std::vector&lt;int&gt; E)
```

* $E$․ $N$ երկարության զանգված, որը ցույց է տալիս, թե որ գագաթները պետք է ներկվեն։
* Այս ֆունկցիան վերադարձնում է մոնոխրոմատիկ կոմպոնենտների քանակը $E$-ին համապատասխան վերաներկումից հետո։
* Այս ֆունկցիան կարող է կանչվել առավելագույնը $2\,750$ անգամ։

Գրեյդերը **հարմարվող չէ**, այսինքն,
 գագաթների գույները ֆիքսված են նախքան `find_colours`-ի կանչը։

## Սահմանափակումներ

* $2 \le N \le 250$
* $N - 1 \le M \le \frac{N \cdot (N - 1)}{2}$
* $0 \le X[j] \lt Y[j] \lt N$, որտեղ $0 \le j \lt M$.
* $X[j] \neq X[k]$ կամ $Y[j] \neq Y[k]$,
   որտեղ $0 \le j \lt k \lt M$.
* Գագաթների յուրաքանչյուր զույգ միացված են ինչ որ ճանապարհով։
* $0 \le C[i] \lt N$, որտեղ $0 \le i \lt N$.

## Ենթախնդիրներ

| Ենթախնդիր | Միավոր  | Լրացուցիչ սահմանափակումներ |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = 2$
| 2       | $7$    | $N \le 50$
| 3       | $33$   | Գրաֆը ճանապարհ է․ $M = N - 1$, և $j$ ու $j+1$ գագաթները կից են ($0 \leq j < M$).
| 4       | $21$   | Գրաֆը լրիվ է․ $M = \frac{N \cdot (N - 1)}{2}$, և ցանկացած երկու գագաթներ կից են։
| 5       | $36$   | Լրացուցիչ սահմանափակումներ չկան։

Յուրաքանչյուր ենթախնդրում դուք կարող եք ձեռք բերել մասնակի միավորներ,
 եթե ձեր ծրագիրը ճիշտ պարզում է,
 իրար կից բոլոր գագաթների զույգերի համար,
 նրանք նույն գույնն ունեն, թե ոչ։

Ավելի ճշգրիտ,
 դուք ստանում եք ենթախնդրի միավորն ամբողջությամբ,
 եթե նրա բոլոր թեստերում,
 `find_colours`-ի վերադարձրած $G$ զանգվածը 
 համընկնում է $C$ զանգվածի հետ
 (այսինքն $G[i] = C[i]$,
 որտեղ $0 \le i \lt N$).
Հակառակ դեպքում,
 դուք ստանում եք ենթախնդրի միավորի $50\%$-ը,
 եթե բոլոր թեստերում հետևյալ պայմանները 
 բավարարված են․
* $0 \le G[i] \lt N$, որտեղ $0 \le i \lt N$;
* Բոլոր $j$-երի համար, որտեղ $0 \le j \lt M$․
  * $G[X[j]] = G[Y[j]]$ այն և միայն այն ժամանակ, երբ $C[X[j]] = C[Y[j]]$.

## Օրինակ

Դիտարկենք հետևյալ կանչը.

```
find_colours(4, [0, 1, 0, 0], [1, 2, 2, 3])
```

Այս օրինակի համար ենթադրենք, որ
 գագաթների (գաղտնի) գույներն այսպիսին են․
 $C = [2, 0, 0, 0]$.
Այս սցենարը պատկերված է հետևյալ նկարում։
Գույները նշված են յուրաքանչյուր գագաթին կցված սպիտակ շրջանակների ներսի թվերով։

![example.png](sphinx_example.png "230")

Ֆունկցիան կարող է կանչել  `perform_experiment`-ը հետևյալ կերպ․

```
perform_experiment([-1, -1, -1, -1])
```

Այս կանչի արդյունքում ոչ մի գագաթ չի վերաներկվում, բոլոր գագաթները պահում են իրենց սկզբնական գույները։

Դիտարկենք $1$ և $2$ գագաթները։
Նրանք երկուսն էլ $0$ գույնն ունեն, և $1, 2$ ճանապարհը մոնոխրոմատիկ ճանապնարհ է։
Արդյունքում, $1$ և $2$ գագաթներն ընկած են միևնույն մոնոխրոմատիկ կոմպոնենտի մեջ։

Դիտարկենք $1$ և $3$ գագաթները։
Թեկուզ նրանք երկուսն էլ ունեն $0$ գույնը,
 նրանք պատկանում են տարբեր մոնոխրոմատիկ կոմպոնենտների, 
 քանի որ նրանց միացնող մոնոխրոմատիկ ճանապարհ գոյություն չունի։

Ընդամենը կան $3$ մոնոխրոմատիկ կոմպոնենտներ,
 դրանք են․ $\{0\}$, $\{1, 2\}$ և $\{3\}$։
Հետևաբար այս ֆունկցիան կվերադարձնի $3$։

Այժմ կարող է կանչվել `perform_experiment` ֆունկցիան հետևյալ կերպ․

```
perform_experiment([0, -1, -1, -1])
```

Այս կանչի արդյունքում միայն $0$ գագաթը կներկվի $0$ գույնով,
 և կստացվի հետևյալ պատկերը․

![example.png](sphinx_order1.png "230")

Այս կանչը կվերադարձնի $1$, քանի որ բոլոր գագաթները պատկանում են միևնույն մոնոխրոմատիկ կոմպոնենտին։
Մենք կարող ենք եզրակացնել, որ $1$, $2$ և $3$ գագաթներն ունեն միևնույն $0$ գույնը։

Ապա կարող է կանչվել  `perform_experiment` ֆունկցիան հետևյալ կերպ․

```
perform_experiment([-1, -1, -1, 2])
```

Այս կանչի արդյունքում $3$ գագաթը վերաներկվում է $2$ գույնով,
 ստացվում է հետևյալ պատկերը․

![example.png](sphinx_order2.png "230")

Այս կանչը վերադարձնում է $2$, քանի որ կան $2$ մոնոխրոմատիկ կոմպոնենտներ,
 համապատասխանաբար $\{0, 3\}$ և $\{1, 2\}$ գագաթներով։
Մենք կարող ենք եզրակացնել, որ  $0$ գագաթի գույնը $2$ է։

Ապա `find_colours` ֆունկցիան վերադարձնում է $[2, 0, 0, 0]$ զանգվածը։
Քանի որ $C = [2, 0, 0, 0]$, լրիվ միավոր է տրվում։

Նկատենք, որ կան նաև բազմաթիվ վերադարձի արժեքներ, որոնց դեպքում միավորի $50\%$-ն է տրվում, օրինակ  $[1, 2, 2, 2]$ կամ $[1, 2, 2, 3]$։

## Գրեյդերի նմուշ

Մուտքային տվյալների ձևաչափը․

```
N  M
C[0]  C[1] ... C[N-1]
X[0]  Y[0]
X[1]  Y[1]
...
X[M-1]  Y[M-1]
```

Ելքային տվյալների ձևաչափը․

```
L  Q
G[0]  G[1] ... G[L-1]
```

Այստեղ $L$-ը `find_colours` ֆունկցիայի վերադարձրած $G$ զանգվածի երկարությունն է,
 իսկ $Q$-ն  `perform_experiment`-ի կանչերի քանակն է։
