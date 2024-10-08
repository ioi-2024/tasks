# Ієрогліфи

Команда дослідників вивчає подібність між послідовностями ієрогліфів.
Вони представляють кожен ієрогліф цілим невід’ємним числом.
Щоб виконати своє дослідження,
 вони використовують наступні поняття про послідовності.

Для фіксованої послідовності $A$,
 послідовність $S$ називається **підпослідовністю** $A$,
 тоді і тільки тоді, коли можна отримати $S$
 шляхом видалення деяких елементів (можливо жодного) з $A$.

У таблиці нижче наведено кілька прикладів підпослідовностей послідовності $A = [3, 2, 1, 2]$.

| Послідовність    | Як її можна отримати з $A$ |
|----------------|---------------------------------|
| [3, 2, 1, 2] | Жоден елемент не видаляється.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] or [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

З іншого боку, $[3, 3]$ або $[1, 3]$ не є підпослідовностями $A$.

Розглянемо дві послідовності ієрогліфів $A$ і $B$.
Послідовність $S$ називається **спільною підпослідовністю** $A$ і $B$
 тоді і тільки тоді, коли $S$ є підпослідовністю як $A$ так і $B$.
Крім того, ми говоримо, що послідовність $U$ є **універсальною спільною підпослідовністю** $A$ і $B$
 тоді і тільки тоді, коли виконуються такі дві умови:
* $U$ є спільною підпослідовністю $A$ і $B$.
* Кожна спільна підпослідовність $A$ і $B$ також є підпослідовністю $U$.

Можна показати, що будь-які дві послідовності $A$ і $B$
 мають не більше однієї універсальної спільної підпослідовності.

Дослідники знайшли дві послідовності ієрогліфів $A$ і $B$.
Послідовність $A$ складається з $N$ ієрогліфів,
 а послідовність $B$ складається з $M$ ієрогліфів.
Допоможіть дослідникам обчислити
 універсальну спільну підпослідовність послідовностей $A$ і $B$,
 або визначити, що такої послідовності не існує.

## Деталі реалізації

Ви повинні реалізувати наступну функцію.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```
* $A$: масив довжини $N$, що описує першу послідовність.
* $B$: масив довжини $M$, що описує другу послідовність.
* Якщо існує універсальна спільна підпослідовність $A$ і $B$, то
   функція повинна повернути масив, що містить цю послідовність.
  В іншому випадку функція має повернути $[-1]$
   (масив довжиною $1$ , єдиним елементом якого є $-1$ ).
* Ця функція викликається рівно один раз для кожного тесту.

## Обмеження

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ для кожного $i$ такого, що  $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ для кожного $j$ такого, що $0 \leq j < M$

## Підзадачі

| Підзадача | Балів  | Додаткові обмеження |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; кожен з $A$ і $B$ складається з $N$ **різних** цілих чисел від $0$ до $N-1$ (включно)
| 2       | $15$   | Для будь-якого цілого $k$ (кількість елементів $A$, що дорівнює $k$) плюс (кількість елементів $B$, що дорівнює $k$) не перевищує $3$.
| 3 | $10$ | $A[i] \leq 1$ для кожного $i$ такого, що $0 \leq i < N$; $B[j] \leq 1$ для кожного $j$ такого, що $0 \leq j < M$
| 4 | $16$ | Існує універсальна спільна підпослідовність $A$ і $B$.
| 5 | $14$ | $N \leq 3000$; $M \leq 3000$
| 6 | $42$ | Без додаткових обмежень.

## Приклади

### Приклад 1

Розглянемо наступний виклик.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Тут спільні підпослідовності $A$ і $B$ такі:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ і $[0, 1, 0, 2]$.

Оскільки $[0, 1, 0, 2]$ є спільною підпослідовністю $A$ і $B$, і
 усі спільні підпослідовності $A$ і $B$ є підпослідовностями $[0, 1, 0, 2]$,
 функція має повернути $[0, 1, 0, 2]$.

### Приклад 2

Розглянемо наступний виклик.

```
ucs([0, 0, 2], [1, 1])
```

Тут єдиною спільною підпослідовністю $A$ і $B$ є порожня послідовність $[\ ]$.
З цього випливає, що функція повинна повертати порожній масив $[\ ]$.

### Приклад 3

Розглянемо наступний виклик.
```
ucs([0, 1, 0], [1, 0, 1])
```

Тут спільні підпослідовності $A$ і $B$
 $[\ ], [0], [1], [0, 1]$ і $[1, 0]$.
Можна показати, що універсальної спільної підпослідовності не існує.
Отже, функція має повернути $[-1]$.

## Приклад градера

Формат вхідних даних:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Формат вихідних даних:

```
T
R[0]  R[1]  ...  R[T-1]
```

Тут $R$ — це масив, який повертає `ucs`, а $T$ — його довжина.
