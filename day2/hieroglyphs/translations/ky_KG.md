# Иероглифтер

Изилдөөчүлөр тобу иероглифтердин тизмегинин окшоштуктарын изилдеп жатышат.
Алар ар бир иероглифти терс эмес бүтүн сан менен билдирет.
Изилдөө жүргүзүү үчүн алар тизмектер жөнүндө төмөнкү түшүнүктөрдү колдонушат.

Белгиленген $A$ ырааттуулугу үчүн $S$ ырааттуулугу $A$ нын **ички ырааттуулугу** деп аталат, эгерде $S$ $A$ дан кээ бир элементтерди (мүмкүн эч кайсыл) алып салуу менен алынса гана.

Төмөнкү таблица $A = [3, 2, 1, 2]$ ырааттуулугунун кээ бир мисалдарын көрсөтөт.

| ички ырааттуулугу | $A$ дан кантип алса болот  |
|----------------|-------------------------------- -|
| [3, 2, 1, 2] | Эч кандай элементтер жок кылынбайт.
| [2, 1, 2] | [<s>3</s>, 2, 1, 2]
| [3, 2, 2] | [3, 2, <s>1</s>, 2]
| [3, 2] | [3, <s>2</s>, <s>1</s>, 2] же [3, 2, <s>1</s>, <s>2</s>]
| [3] | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ] | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Башка жагынан алганда, $[3, 3]$ же $[1, 3]$ $A$ нын ички ырааттуулугу эмес.

$A$ жана $B$ иероглифтеринин эки ырааттуулугун карап көрөлү.
$S$ ырааттуулугу $A$ жана $B$ нын **жалпы ички ырааттуулугу** деп аталат, эгерде $S$ $A$ жана $B$ экөөнүн тең кичи ырааттуулугу болгондо гана.
Андан тышкары, биз $U$ ырааттуулугу $A$ жана $B$ нын **универсалдуу жалпы ырааттуулугу** деп айтабыз, эгерде төмөнкү эки шарт аткарылса гана:
* $U$ — $A$ жана $B$ жалпы тизмеги.
* $A$ жана $B$ ар бир ички ырааттуулугу, ошондой эле $U$ ички ырааттуулугу болуп саналат.

$A$ жана $B$ каалаган эки ырааттуулугунда эң көп дегенде бир универсалдуу жалпы ырааттуулук бар экенин көрсөтсө болот.

Изилдөөчүлөр $A$ жана $B$ иероглифтеринин эки ырааттуулугун табышкан.
$A$ ырааттуулугу $N$ иероглифтеринен, $B$ ырааттуулугу $M$ иероглифтеринен турат.
Изилдөөчүлөргө $A$ жана $B$ катарларынын универсалдуу жалпы ырааттуулугун эсептөөгө жардам бериңиз же андай ырааттуулук жок экенин аныктаңыз.

## Ишке ашыруу чоо-жайы

Сиз төмөнкү процедураны ишке ашырууңуз керек.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$ : биринчи ырааттуулукту сүрөттөгөн $N$ узундуктагы массив.
* $B$ : экинчи ырааттуулукту сүрөттөгөн $M$ узундуктагы массив.
* Эгерде $A$ жана $B$ универсалдуу жалпы ырааттуулугу бар болсо, процедура ушул ырааттуулукту камтыган массивди кайтарышы керек.
  Болбосо, процедура $[-1]$ кайтарышы керек ( $1$ узундуктагы массив, анын жалгыз элементи $-1$ ).
* Бул процедура ар бир процедура учуру үчүн бир жолу чакырылат.

## Чектөөлөр

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ ар бир $i$ үчүн $0 \leq i < N$
* Ар бир $j$ үчүн $0 \leq B[j] \leq 200\,000$ $0 \leq j < M$

## Кошумча тапшырмалар

| Кошумча тапшырмача | Упай | Кошумча чектөөлөр |
| :-----: | :----: | -------------------------------- |
| 1 | $3$ | $N = M$ ; $A$ жана $B$ ар бири $0$ менен $N-1$ (кошкондо) ортосундагы $N$ **ар түрдүү** бүтүн сандардан турат 
| 2 | $15$ | Ар кандай $k$ бүтүн сан үчүн, ( $A$ элементтеринин саны $k$га барабар) плюс ( $B$ элементтеринин саны $k$ барабар) эң көп $3$ болот.
| 3 | $10$ | $A[i] \leq 1$ ар бир $i$ үчүн $0 \leq i < N$ ; $B[j] \leq 1$ ар бир $j$ үчүн $0 \leq j < M$
| 4 | $16$ | $A$ жана $B$ универсалдуу жалпы тизмеги бар.
| 5 | $14$ | $N \leq 3000$ ; $M \leq 3000$
| 6 | $42$ | Эч кандай кошумча чектөөлөр.

## Мисалдар

### 1-мисал

Төмөнкү чакырыкты карап көрөлү.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Бул жерде $A$ жана $B$ жалпы тизмектери төмөнкүлөр:
$[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ жана $[0, 1, 0, 2]$. .

$[0, 1, 0, 2]$ жалпы $A$ жана $B$ ырааттуулугу болгондуктан, ал эми $A$ жана $B$ бардык жалпы кичи ырааттуулугу $[0, 1, 0, 2]$ , процедура $[0, 1, 0, 2]$ кайтарышы керек.

### 2-мисал

Төмөнкү чакырыкты карап көрөлү.

```
ucs([0, 0, 2], [1, 1])
```

Бул жерде $A$ жана $B$ бирден-бир жалпы кийинки катар $[\ ]$ бош ырааттуулугу болуп саналат.
Демек, процедура $[\ ]$ бош массивди кайтарышы керек.

### 3-мисал

Төмөнкү чакырыкты карап көрөлү.
```
ucs([0, 1, 0], [1, 0, 1])
```

Бул жерде $A$ жана $B$ жалпы тизмектери $[\ ], [0], [1], [0, 1]$ жана $[1, 0]$ болуп саналат.
Универсалдуу жалпы ырааттуулугу жок экенин көрсөтсө болот.
Ошондуктан, процедура $[-1]$ кайтарышы керек.

## Үлгү Грейдер

Киргизүү форматы:

```
NM
A[0] A[1] ... A[N-1]
B[0] B[1] ... B[M-1]
```

Чыгаруу форматы:

```
T
R[0] R[1] ... R[T-1]
```

Бул жерде, $R$ – `ucs` тарабынан кайтарылган массив жана $T$ – анын узундугу.
