# Drzewo

Rozważmy **drzewo** składające się z $N$ **wierzchołków**,
 ponumerowanych od $0$ do $N-1$.
Wierzchołek $0$ nazywamy **korzeniem**.
Każdy wierzchołek, z wyjątkiem korzenia, ma jednego **rodzica**.
Dla każdego $i$ takiego, że $1 \leq i < N$,
 rodzicem wierzchołka $i$ jest wierzchołek $P[i]$, gdzie $P[i] < i$.
Przyjmujemy, że $P[0] = -1$.

Dla dowolnego wierzchołka $i$ ($0 \leq i < N$),
 **poddrzewo** $i$ jest zbiorem następujących wierzchołków:
 * $i$, oraz
 * dowolny wierzchołek, którego rodzicem jest $i$, oraz
 * dowolny wierzchołek, którego rodzicem jest wierzchołek, którego rodzicem jest $i$, oraz
 * dowolny wierzchołek, którego rodzicem jest wierzchołek, którego rodzicem jest wierzchołek, którego rodzicem jest $i$, oraz
 * itd.

Poniższy rysunek przedstawia przykładowe drzewo składające się z $N = 6$ wierzchołków.
Każda strzałka łączy wierzchołek z jego rodzicem,
 z wyjątkiem korzenia, który nie ma rodzica.
Poddrzewo wierzchołka $2$ zawiera wierzchołki $2$, $3$, $4$ i $5$.
Poddrzewo wierzchołka $0$ zawiera wszystkie $6$ wierzchołków drzewa, a poddrzewo wierzchołka $4$ zawiera tylko wierzchołek $4$.

![](subtrees.png "150")

Każdemu wierzchołkowi przypisana jest nieujemna liczba całkowita: **waga**.
Oznaczamy wagę wierzchołka $i$ ($0 \leq i < N$) przez $W[i]$.

Twoim zadaniem jest napisanie programu, który odpowie na $Q$ zapytań,
 z których każde jest opisane parą dodatnich liczb całkowitych $(L, R)$.
Odpowiedź na zapytanie należy obliczyć w następujący sposób.

Rozważmy przypisanie liczby całkowitej,
 nazywanej **współczynnikiem**, do każdego wierzchołka drzewa.
Takie przypisanie jest opisane ciągiem $C[0], \ldots, C[N-1]$,
 gdzie $C[i]$ ($0 \leq i < N$) jest współczynnikiem przypisanym wierzchołkowi $i$.
Nazwijmy ten ciąg **ciągiem współczynników**.
Należy pamiętać, że elementy ciągu współczynników mogą być ujemne, równe $0$ lub dodatnie.

Dla zapytania $(L, R)$,
 sekwencję współczynników nazywa się **prawidłową**,
 jeśli dla każdego wierzchołka $i$ ($0 \leq i < N$)
 spełniony jest następujący warunek:
 suma współczynników wierzchołków w poddrzewie wierzchołka $i$
 nie jest mniejsza niż $L$ i nie jest większa niż $R$.

Dla danego ciągu współczynników $C[0], \ldots, C[N-1]$,
 **koszt** wierzchołka $i$ wynosi $|C[i]| \cdot W[i]$,
 gdzie $|C[i]|$ oznacza wartość bezwzględną $C[i]$.
Wreszcie, **całkowity koszt** jest sumą kosztów wszystkich wierzchołków.
Twoim zadaniem jest obliczenie, dla każdego zapytania,
 **minimalnego całkowitego kosztu**, który można osiągnąć przy zastosowaniu pewnej prawidłowej sekwencji współczynników.

Można wykazać, że dla dowolnego zapytania istnieje co najmniej jedna prawidłowa sekwencja współczynników.

## Szczegóły implementacji

Należy zaimplementować następujące dwie funkcje:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$: tablice liczb całkowitych o długości $N$ określające rodziców i wagi.
* Ta procedura wywoływana jest dokładnie raz,
   na początku interakcji pomiędzy programem oceniającym a Twoim programem, dla każdego testu.
	 
```
long long query(int L, int R)
```
* $L$ , $R$ : liczby całkowite opisujące zapytanie.
* Ta procedura jest wywoływana $Q$ razy po wywołaniu `init` dla każdego testu.
* Ta procedura powinna zwrócić odpowiedź na podane zapytanie.

## Ograniczenia

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ dla każdego $i$ takiego, że $1 \leq i < N$
* $0 \leq W[i] \leq 1\,000\,000$ dla każdego $i$ takiego, że $0 \leq i < N$
* $1 \leq L \leq R \leq 1\,000\,000$ w każdym zapytaniu

## Podzadania

| Podzadanie | Punkty  | Dodatkowe ograniczenia |
| :-----: | :----: | ---------------------- |
|   1     |  $10$  | $Q \leq 10$; $W[P[i]] \leq W[i]$ dla każdego $i$ takiego, że $1 \leq i < N$
|   2     |  $13$  | $Q \leq 10$; $N \leq 2\,000$
|   3     |  $18$  | $Q \leq 10$; $N \leq 60\,000$
|   4     |  $7$   | $W[i] = 1$ dla każdego $i$ takiego, że $0 \leq i < N$
|   5     |  $11$  | $W[i] \leq 1$ dla każdego $i$ takiego, że $0 \leq i < N$
|   6     |  $22$  | $L = 1$
|   7     |  $19$  | brak dodatkowych ograniczeń


## Przykłady

Rozważmy następujące wywołania:

```
init([-1, 0, 0], [1, 1, 1])
```
Drzewo składa się z $3$ wierzchołków: korzenia i jego $2$ dzieci.
Wszystkie wierzchołki mają wagi $1$.

```
query(1, 1)
```

W tym zapytaniu $L = R = 1$,
czyli suma współczynników w każdym poddrzewie musi być równa $1$.
Rozważmy ciąg współczynników $[-1, 1, 1]$.
Drzewo i współczynniki przypisane jego wierzchołkom (w szarych prostokątach) są przedstawione na poniższym rysunku.

![](ex1.png "150")

Dla każdego wierzchołka $i$ ($0 \leq i < 3$) suma współczynników wszystkich wierzchołków
 w poddrzewie $i$ jest równa $1$. 
Zatem taka sekwencja współczynników jest prawidłowa.
Całkowity koszt oblicza się następująco:

| Wierzchołek | Waga | Współczynnik | Koszt                      |
| :----: | :----: | :---------: | :-----------------------: |
|   0    |   1    |     -1      | $\mid -1 \mid \cdot 1 = 1$
|   1    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$
|   2    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$

Zatem całkowity koszt wynosi $3$.
Jest to jedyny prawidłowy ciąg współczynników, dlatego wywołanie powinno zwrócić $3$.
```
query(1, 2)
```
Minimalny całkowity koszt dla tego zapytania wynosi $2$ i jest osiągany dla ciągu współczynników $[0, 1, 1]$.

## Przykładowy program oceniający

Format wejścia:

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

gdzie $L[j]$ i $R[j]$
 (dla $0 \leq j < Q$)
 są argumentami $j$-tego wywołania `query`.
Należy zauważyć, że drugi wiersz danych wejściowych zawiera **tylko $N-1$ liczb całkowitych**,
 ponieważ przykładowa oceniarka nie wczytuje wartości $P[0]$.

Format wyjścia:
```
A[0]
A[1]
...
A[Q-1]
```

gdzie $A[j]$
 (dla $0 \leq j < Q$)
 jest wartością zwróconą przez $j$-te wywołanie `query`.