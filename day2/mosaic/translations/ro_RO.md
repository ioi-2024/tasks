# Mozaic

Salma planuiește să coloreze un mozaic pe un perete.
Acest mozaic este un tabel de dimensiunea $N \times N$ ,
 compus din $N^2$ celule pătrate de dimensiune $1 \times 1$ inițial necolorate.
Liniile acestui mozaic sunt numerotate de la $0$ la $N-1$ mergând de sus în jos,
 iar coloanele sunt numerotate de la $0$ la $N-1$ mergând de la stânga la dreapta.
Celula de pe linia $i$ și coloana $j$ ($0 \leq i < N$, $0 \leq j < N$) este notată cu $(i,j)$.
Fiecare celula este colorată fie în alb (notat cu $0$), fie în negru (notat cu $1$).

Pentru a colora mozaicul, Salma mai intâi alege două tablouri $X$ și $Y$ de lungime $N$,
 fiecare compus din valori de $0$ și $1$, astfel încât $X[0] = Y[0]$.
Aceasta colorează fiecare celulă de pe prima linie (linia $0$) conform tabloului $X$,
 astfel încât culoarea celulei $(0,j)$ este $X[j]$ ($0 \leq j < N$).
De asemenea, aceasta colorează cea mai de la stânga coloană (coloana $0$) conform tabloului $Y$,
 astfel încât culoarea celulei $(i,0)$ este $Y[i]$ ($0 \leq i < N$).

Apoi aceasta repeta următorii pași până când toate celulele sunt colorate:
* Ea găsește orice celulă *necolorată* $(i,j)$ astfel încât vecinul ei de sus (celula $(i-1, j)$) și vecinul ei din stânga (celula $(i, j-1)$) sunt amândoi *deja colorați*.
* Apoi, aceasta colorează celula $(i,j)$ în negru dacă ambii vecini sunt albi;
 altfel, colorează celula $(i, j)$ în alb.

Se poate demonstra faptul că culoarea finală a celulelor nu depinde
de ordinea în care Salma le colorează.
 
Yasmin este foarte curiosă în legatură cu culoarea celulelor din mozaic.
Aceasta îi pune lui Salma $Q$ întrebări, numerotate de la $0$ la $Q-1$.
În întrebarea $k$ ($0 \leq k < Q$),
Yasmin specifică o submatrice a mozaicului prin:
* Cea mai de sus linie a sa $T[k]$ și cea mai de jos linie a sa $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* Cea mai de la stănga coloană $L[k]$ și cea mai de la dreapta coloană a sa $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

Răspunsul la întrebare este numărul de celule negre din această submatrice.
În particular, Salma are de găsit câte celule $(i, j)$ există,
 astfel încât $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$,
 iar celula $(i,j)$ are culoarea neagră.

Scrie un program care răspunde la intrebările lui Yasmin.

## Detalii de implementare

Trebuie să implementezi următoarea funcție.

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: tablouri de lungimea $N$ descriind culorile
 de pe cea mai de sus linie, respectiv cea mai din stânga coloană.
* $T$, $B$, $L$, $R$: tablouri de lungime $Q$ descriind întrebările puse de Yasmin.
* Această funcție trebuie să returneze un tablou $C$ de lungime $Q$,
 astfel încât $C[k]$ conține răspunsul la întrebarea $k$ ($0 \leq k < Q$).
* Această funcție este apelată exact o singură dată pentru fiecare test.

## Restricții

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ and $Y[i] \in \{0, 1\}$
* pentru orice $i$ astfel încât $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ și $0 \leq L[k] \leq R[k] < N$
pentru orice $k$ astfel încât $0 \leq k < Q$

## Subtaskuri

| Subtask | Scor  | Restricții adiționale |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ (pentru fiecare $k$ astfel încât $0 \leq k < Q$)
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ (pentru fiecare $i$ astfel încât $0 \leq i < N$)
| 6       | $22$   | $T[k] = B[k]$ și $L[k] = R[k]$ (pentru fiecare $k$ astfel încât $0 \leq k < Q$)
| 7       | $19$   | $T[k] = B[k]$ (pentru fiecare $k$ astfel încât $0 \leq k < Q$)
| 8       | $22$   | Fără constrângeri adiționale.

## Exemplu 

Considerăm următorul apel de funcție.

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Acest exemplu este ilustrat in imaginile de mai jos.
Imaginea din stânga arată culorile celulelor din mozaic.
Imaginile din centru si dreapta arată matricele de care
 Yasmin a întrebat în prima și a doua sa întrebare.

![](example.png "550")

Răspunsurile la întrebări
 (anume, numărul de valori de unu curpinse in submatricele în gri)
 sunt 7 si 3.
Astfel, funcția ar trebui să returneze $[7, 3]$.

## Exemplu de grader

Formatul datelor de intrare:

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

Formatul datelor de ieșire:

```
C[0]
C[1]
...
C[S-1]
```

Aici, $S$ reprezintă lungimea tabloului $C$ returnat de `mosaic`.