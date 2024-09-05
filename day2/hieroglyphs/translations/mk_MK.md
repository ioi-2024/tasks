# Хиероглифи

Еден истражувачки тим ги проучува сличностите помеѓу низи од хиероглифи.
Секој хиероглиф тие го претставуваат со ненегативен цел број.
За да го спроведат своето истражување,
 тимот ги користи следниве концепти во врска со низите.

За дадена фиксна низа $A$,
 низата $S$ се нарекува **подниза** на $A$
 ако и само ако $S$ може да се добие со отстранување на некои елементи (може да биде и ниеден) од $A$.

Табелата подолу прикажува некои примери за поднизи на низата $A = [3, 2, 1, 2]$.

| Подниза    | Како таа може да се добие од $A$ |
|----------------|---------------------------------|
| [3, 2, 1, 2] | Не се отстрануваат елементи.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] или [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Од друга страна, $[3, 3]$ или $[1, 3]$ не се поднизи на $A$.

Да разгледаме две низи од хиероглифи, $A$ и $B$.
Една низа $S$ се нарекува **взаемна подниза** на $A$ и $B$
 ако и само ако $S$ е подниза и на $A$ и на $B$.
Уште повеќе, велиме дека една низа $U$ е **универзална взаемна подниза** на $A$ и $B$
 ако и само ако се исполнети следните два услови:
* $U$ е взаемна подниза на $A$ и $B$.
* Секоја взаемна подниза на $A$ и $B$ е исто така подниза на $U$.

Може да се покаже дека кои било две низи $A$ и $B$
 имаат најмногу една универзална взаемна подниза.

Истражувачите пронашле две низи од хиероглифи $A$ и $B$.
Низата $A$ се состои од $N$ хиероглифи, а низата $B$ се состои од $M$ хиероглифи.
Помогнете им на истражувачите да ја пресметаат универзалната взаемна подниза на низите $A$ и $B$,
 или пак да утврдат дека не постои таква низа.

## Имплементациски детали

Треба да ја имплементирате следната процедура.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: низа со должина $N$ што ја опишува првата низа.
* $B$: низа со должина $M$ што ја опишува втората низа.
* Ако постои универзална взаемна подниза на $A$ и $B$,
   процедурата треба да ја врати таа низа.
  Инаку, процедурата треба да врати $[-1]$
   (низа со должина $1$, чијшто единствен елемент е $-1$).
* Оваа процедура се повикува точно еднаш за секој тест случај.

## Ограничувања

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ за секое $i$ такво што $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ за секое $j$ такво што $0 \leq j < M$

## Подзадачи

| Подзадача | Поени  | Дополнителни ограничувања |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; секоја од низите $A$ и $B$ се состои од $N$ **различни** цели броеви помеѓу $0$ и $N-1$ (вклучувајќи ги $0$ и $N-1$)
| 2       | $15$   | За кој било цел број $k$, (бројот на елементи на $A$ еднакви на $k$) плус (бројот на елементи на $B$ еднакви на $k$) е најмногу $3$.
| 3       | $10$   | $A[i] \leq 1$ за секое $i$ такво што $0 \leq i < N$; $B[j] \leq 1$ за секое $j$ такво што $0 \leq j < M$
| 4       | $16$   | Постои универзална взаемна подниза на $A$ и $B$.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | Нема дополнителни ограничувања.

## Примери

### Пример 1

Да го разгледаме следниот повик.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Овде, взаемните поднизи на $A$ и $B$ се следните:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ и $[0, 1, 0, 2]$.

Бидејќи $[0, 1, 0, 2]$ е взаемна подниза на $A$ и $B$, и сите взаемни поднизи на $A$ и $B$ се поднизи на $[0, 1, 0, 2]$,
 процедурата треба да врати $[0, 1, 0, 2]$.

### Пример 2

Да го разгледаме следниот повик.

```
ucs([0, 0, 2], [1, 1])
```

Овде, единствената взаемна подниза на $A$ и $B$ е празната низа $[\ ]$.
Следува дека процедурата треба да врати празна низа $[\ ]$.

### Пример 3

Да го разгледаме следниот повик.
```
ucs([0, 1, 0], [1, 0, 1])
```

Овде, взаемните поднизи на $A$ и $B$ се
 $[\ ], [0], [1], [0, 1]$ и $[1, 0]$.
Може да се покаже дека не постои универзална взаемна подниза.
Според тоа, процедурата треба да врати $[-1]$.

## Пример-оценувач

Формат на влез:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Формат на излез:

```
T
R[0]  R[1]  ...  R[T-1]
```

Овде, $R$ е низата што е вратена од `ucs`, а $T$ е нејзината должина.