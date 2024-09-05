# Hieroglify

Zespół amerykańskich naukowców bada podobieństwa pomiędzy ciągami hieroglifów.
Naukowcy reprezentują każdy hieroglif za pomocą nieujemnej liczby całkowitej.
Aby przeprowadzić swoje badania, korzystają z następujących pojęć dotyczących ciągów.

Dla ustalonego ciągu $A$, ciąg $S$ nazywany jest **podciągiem** ciągu $A$ wtedy i tylko wtedy, gdy można uzyskać $S$ usuwając niektóre elementy (być może żadne) z $A$.

Poniższa tabela przedstawia przykłady podciągów ciągu $A = [3, 2, 1, 2]$.

| Podciąg | Jak można go uzyskać z $A$ |
|----------------|------------------------------------------------|
| [3, 2, 1, 2] | Żaden element nie został usunięty.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] lub [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Z drugiej strony, $[3, 3]$ oraz $[1, 3]$ nie są podciągami $A$.

Rozważmy dwa ciągi hieroglifów, $A$ i $B$.
Ciąg $S$ nazywany jest **wspólnym podciągiem** ciagów $A$ i $B$
 wtedy i tylko wtedy, gdy $S$ jest podciągiem zarówno $A$, jak i $B$.
Ponadto mówimy, że ciąg $U$ jest **uniwersalnym wspólnym podciągiem** ciągów $A$ i $B$
 wtedy i tylko wtedy, gdy spełnione są następujące dwa warunki:
* $U$ jest wspólnym podciągiem $A$ i $B$.
* Każdy wspólny podciąg $A$ i $B$ jest również podciągiem $U$.

Można udowodnić, że dowolne dwa ciągi $A$ i $B$
 mają co najwyżej jeden uniwersalny wspólny podciąg.

Naukowcy znaleźli dwa ciągi hieroglifów $A$ i $B$.
Ciąg $A$ składa się z $N$ hieroglifów,
 a ciąg $B$ składa się z $M$ hieroglifów.
Pomóż badaczom wyznaczyć
 uniwersalny wspólny podciąg ciągów $A$ i $B$,
 lub ustalić, że taki ciąg nie istnieje.

## Szczegóły implementacji

Powinieneś zaimplementować następującą procedurę.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: tablica o długości $N$ opisująca pierwszy ciąg.
* $B$: tablica o długości $M$ opisująca drugi ciąg.
* Jeżeli istnieje uniwersalny wspólny podciąg $A$ i $B$,
   procedura powinna zwrócić tablicę zawierającą ten ciąg.
  W przeciwnym wypadku procedura powinna zwrócić $[-1]$
   (tablicę o długości $1$, której jedynym elementem jest $-1$).
* Ta procedura jest wywoływana dokładnie raz dla każdego testu.

## Ograniczenia

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ dla każdego $i$ takiego, że $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ dla każdego $j$ takiego, że $0 \leq j < M$

## Podzadania

| Podzadanie | Punkty | Dodatkowe ograniczenia |
| :-----: | :----: | -------------------------------- |
| 1 | $3$ | $N = M$; każdy z $A$ i $B$ składa się z $N$ **różnych** liczb całkowitych pomiędzy $0$ a $N-1$ (włącznie)
| 2 | $15$ | Dla dowolnej liczby całkowitej $k$, (liczba elementów $A$ równych $k$) plus (liczba elementów $B$ równych $k$) wynosi co najwyżej $3$.
| 3 | $10$ | $A[i] \leq 1$ dla każdego $i$ takiego, że $0 \leq i < N$; $B[j] \leq 1$ dla każdego $j$ takiego, że $0 \leq j < M$
| 4 | $16$ | Istnieje uniwersalny wspólny podciąg $A$ i $B$.
| 5 | $14$ | $N \leq 3000$; $M \leq 3000$
| 6 | $42$ | Brak dodatkowych ograniczeń.

## Przykłady

### Przykład 1

Rozważmy następujące wywołanie.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

W tym przypadku wspólne podciągi $A$ i $B$ są następujące:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ oraz $[0, 1, 0, 2]$.

Ponieważ $[0, 1, 0, 2]$ jest wspólnym podciągiem $A$ i $B$, a
 wszystkie wspólne podciągi $A$ i $B$ są podciągami $[0, 1, 0, 2]$,
 procedura powinna zwrócić $[0, 1, 0, 2]$.

### Przykład 2

Rozważmy następujące wywołanie.

```
ucs([0, 0, 2], [1, 1])
```

W tym przypadku jedynym wspólnym podciągiem $A$ i $B$ jest pusty ciąg $[\ ]$.
Z tego wynika, że procedura powinna zwrócić pustą tablicę $[\ ]$.

### Przykład 3

Rozważmy następujące wywołanie.
```
ucs([0, 1, 0], [1, 0, 1])
```

Tutaj wspólne podciągi $A$ i $B$ to
 $[\ ], [0], [1], [0, 1]$ oraz $[1, 0]$.
Można udowodnić, że nie istnieje żaden uniwersalny wspólny podciąg.
Dlatego procedura powinna zwrócić $[-1]$.

## Przykładowy program oceniający

Format wejścia:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Format wyjścia:

```
T
R[0]  R[1]  ...  R[T-1]
```

$R$ jest tablicą zwróconą przez `ucs`, a $T$ jest jej długością.