# Мозаика

Сальма дубалга чопо мозаика боёгусу келет. Мозаика $N \times N$ тор, $N^2$ башында түсү жок $1 \times 1$ чарчы плиткаларынан жасалган. Мозаиканын сапчалары $0$ дөн $N-1$ ге чейин жогорудан ылдыйга чейин номерленген, жана мамычалар солдон оңго карай $0$ дөн $N-1$ге чейин номерленет. $i$ сапчасындагы жана $j$ мамычасындагы плитка  $(i,j)$ ( $0 \leq i < N$ , $0 \leq j < N$ ) менен белгиленет. Ар бир плитка ак ( $0$ менен белгиленген) же кара ( $1$ менен белгиленген) түстө болушу керек.

Мозаиканы боёш үчүн Сальма адегенде  $X[0] = Y[0]$ болгон узундугу $N$ болгон $X$ жана $Y$ эки массивди тандап алат, алардын ар бири $0$ же $1$ ден турат. $X$ массивине ылайык эң жогорку $0$ сапчадагы $(0,j)$  ( $0 \leq j < N$ ) плиткаларды $X[j]$ түсүнө боёйт. Ал ошондой эле $Y$ массивине ылайык эң сол $0$ мамычадагы $(i,0)$  ( $0 \leq i < N$ ) плиткаларды $Y[i]$ түсүнө боёйт 

Андан кийин ал бардык плиткалар боелуп бүткөнчө төмөнкү кадамдарды кайталайт:
* Ал жогорудагы кошунасы $(i-1, j)$ жана сол кошунасы  $(i, j-1)$ экөө тең * буга чейин боёлгон *  каалаган *түссүз* $(i,j)$ плитканы табат.
* Андан кийин, эгерде бул кошуналардын экөө тең ак болсо, ал $(i,j)$ плиткасын кара түскө боёйт; антпесе, $(i, j)$ плиткасын ак түскө боёйт.

Плиткалардын акыркы түстөрү Салма аларды боёп жаткан тартипке көз каранды эмес экенин көрсөтсө болот.
 
Ясмин мозаикадагы плиткалардын түстөрүнө абдан кызыгат. Ал Салмага $0$ дөн $Q-1$ ге чейин номерленген $Q$ суроолорун берет.
$k$ ( $0 \leq k < Q$ ) суроосунда Ясмин мозаиканын бир төрт бурчтукчасын төмөнкүдөй түшүндүрүп берет:
* Эң жогорку сапча $T[k]$ жана эң төмөнкү сапча $B[k]$ ( $0 \leq T[k] \leq B[k] < N$ ),
* Эң сол жактагы мамыча $L[k]$ жана оң жактагы мамыча $R[k]$ ( $0 \leq L[k] \leq R[k] < N$ ).

Суроонун жообу - бул төрт бурчтукчадагы кара плиткалардын саны.
Тактап айтканда, Салма $T[k] \leq i \leq B[k]$ , $L[k] \leq j \leq R[k]$ жана түсү кара болгон канча $(i, j)$ бар экенин табышы керек.

Ясминдин суроолоруна жооп берген программа жаз.

## Ишке ашыруу чоо-жайы

Сиз төмөнкү процедураны ишке ашырууңуз керек.

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```


* $X$ , $Y$ : узундугу $N$ массивдери, эң жогорку сапчадагы жана эң сол мамычадагы плиткалардын түстөрүн сүрөттөйты.
* $T$ , $B$ , $L$ , $R$ : $Q$ узундуктагы массивдер Ясмин берген суроолорду сүрөттөйт.
* Процедура узундугу $Q$ болгон $C$ массивин кайтарышы керек. $C[k]$ бул $k$ - инчи суроосуна жооп ( $0 \leq k < Q$ ).
* Бул процедура ар бир сыноо учуру үчүн бир жолу чакырылат.

## Чектөөлөр

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* Ар бир $i$ ( $0 \leq i < N$ ) үчүн $X[i] \in \{0, 1\}$ жана $Y[i] \in \{0, 1\}$ 
* $X[0] = Y[0]$
* Ар бир $k$ ($0 \leq k < Q$) үчүн $0 \leq T[k] \leq B[k] < N$ жана $0 \leq L[k] \leq R[k] < N$
 
## Кошумча тапшырмалар


|  Кошумча тапшырмача | Упай | Кошумча чектөөлөр |
| :-----: | :----: | -------------------------------- |
| 1 | $5$ | $N \leq 2; Q \leq 10$
| 2 | $7$ | $N \leq 200; Q \leq 200$
| 3 | $7$ | $T[k] = B[k] = 0$ (ар бир $k$ ( $0 \leq k < Q$ ) үчүн)
| 4 | $10$ | $N \leq 5000$
| 5 | $8$ | $X[i] = Y[i] = 0$ (ар бир $i$ ( $0 \leq i < N$ ) үчүн)
| 6 | $22$ | $T[k] = B[k]$ жана $L[k] = R[k]$ (ар бир $k$ ( $0 \leq k < Q$ ) үчүн)
| 7 | $19$ | $T[k] = B[k]$ (ар бир $k$ ( $0 \leq k < Q$ ) үчүн)
| 8 | $22$ | Кошумча чектөөлөр жок.

## Мисал

Төмөнкү чакырыкты карап көрөлү.
```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```


Бул мисал төмөнкү сүрөттөрдө көрсөтүлгөн.
Сол сүрөттө мозаикадагы плиткалардын түстөрү көрсөтүлгөн.
Ортодогу жана оңдогу сүрөттөрдө биринчи жана экинчи суроодо Ясмин сураган тик бурчтукчалар көрсөтүлгөн.

![](example.png "550")

Суроолорго жооптор (башкача айтканда, көлөкөлүү тик бурчтукчалардагы бирлердин сандары) тиешелүү түрдө 7 жана 3.
Демек, процедура $[7, 3]$ кайтарышы керек.

## Үлгү Грейдер

Киргизүү форматы:

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

Чыгуу форматы:

```
C[0]
C[1]
...
C[S-1]
```

Демек, $S$ бул `mosaic` тарабынан кайтарылган $C$ массивинин  узундугу.