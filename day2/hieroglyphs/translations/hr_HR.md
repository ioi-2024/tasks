# Hieroglyphs

Mr. Malnar dolazi do realizacije da su dobra stara vremena daleko iza nas.
Jedna od stvari gdje to najviše dolazi do izražaja su žurke. Trenutačna situacija
klubova, koji su tek blijeda sjena nekadašnjim diskoteka pa i glazbe koja pati od
utjecaja masovne produkcije i manjka emocija u ovom zadatku osvrnut ćemo se
ipak na privatno organizirane partije te susrete organizirane u sklopu neke manifestacije,
priredbe ili pak svečanosti.
Problem koji se javlja je da zbog visokih cijena, teške organizacije ili pak neiskustva često
na takvih događanjima ne možemo probati kvalitetnu domaću hranu, deserte koji nešto valjaju
pa ni kvalitetna pića jer su često ona poslužena kupljena na prvoj polici kada se uđe u konzum iznad
znaka na kojem piše "akcija". Koliko je situacija kritična ilustrira i činjenica da smo loša vina počeli nadjevati epitetom "kvalitetna", a ona koja tek nešto malo vrijede i koriste se samo u slučaju
krajnje nužde i nemogućnosti nabave boljeg u kratkom vremenu imaju ukras "vrhunska".
Gdje je to od vrhunskog pomislio Mr. Malnar.

Nakon što je uberom došao do hotela i opustio se uz 30 minutnu masažu dolazi do "super ideje" (dodo Krk, 2018).
Shvatio je naime da je jedino rješenje za ovaj problem čuvena metoda BYOB. Metoda koju
bi naši preci možda nazvali metodom očajnika ili pak krajnje rješenje, danas je ipak nužna.
BYOB stoji za Bring your own bottle, strategiju koja zahtjeva mnoštvo znanja i
iskustva za uspješnu provedbu. Naime kako bi žurka prošla glatko, a da se opet uspije ušlagirati
do zadovoljavajuće razine treba stvari dobro dozirati. Također ako poslije treba ići šljakati mora se
paziti da nakon konzumacije postupak ne ostavi previše posljedica za hour odnosno day after.

Pića koja će se kroz noć konzumirati mogu biti opisana nizu nenegativnih brojeva.

Kako bi odabrao odabrao savršen niz, mister je prokopao kroz hsin arhive i
pronašao podatke o dvije po njegovom mišljenju skoro pa savršene žurke. Sjeća se da je u jednoj
od njih dosegao razinu maksimalne opuštenosti, a s druge strane je pak mogao i dalje olako koristiti metodu
"Sankalpe", koju osim njega vješto koristi tek par redovnika joga nidre u svijetu (jedini je takav izvan Indije). U drugoj je pak pomoću samadhija izmislio rekurziju. Činjenica koju znaju mnogi, ali tajnu njegove intelektualne premoći otkrivate možda tek sad.

Ovaj zadatak služi tome da pomognete misteru da na temelju tih već sad čuvenih nizova
konstruirate novi koji će još jednom ispisati povijesti.

Za to će biti bitno razumjeti što je to podniz (ne nužno uzastopan).
Za dani niz $A$,
 niz $S$ zovemo *podniz* od $A$
 akko $S$ možemo iz $A$ dobiti brisanjem nekih (možda i 0 elemenata).

Tabela ispod pokazuje primjere nekih podnizova od $A = [3, 2, 1, 2]$.

| Podniz    | Kako ga dobiti iz $A$ |
|----------------|---------------------------------|
| [3, 2, 1, 2] | No elements are removed.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] or [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

S druge strane, $[3, 3]$ ili $[1, 3]$ nisu podnizovi $A$.

Promotrimo sad dva drevna niza, $A$ i $B$.
Niz $S$ zovemo *zajednički podniz* od $A$ i $B$
 akko je $S$ istovremeno podniz i od $A$ id od $B$.
Nadalje, za niz $U$ kažemo da je *ultimativni zajednički podniz* od $A$ i $B$
 akko vrijedi:
* $U$ je zajednički podniz $A$ i $B$.
* Svaki zajednički podniz od $A$ i $B$ je također i podniz od $U$.

Može se pokazati da za svaki $A$ i $B$
 postoji najviše jedan ultimativni zajednički podniz.

The researchers have found two sequences of hieroglyphs $A$ and $B$.
Niz od prve žurke $A$ ima $N$ pića, niz od druge
 $B$ ima $M$ pića.
Kako bi se ušlagirali na savršen način uz sve dragosti i pozitivne efekt koje to može donijeti, 
pronađite ultimativni zajednički podniz od $A$ i $B$, to će biti tajna formula.
 Ako takav ne postoji program to također mora odgonetnuti, u tom slučaju rješenje je otići
 na jacuzzi.

## Implementation details

You should implement the following procedure.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: array of length $N$ describing the first sequence.
* $B$: array of length $M$ describing the second sequence.
* If there exists a universal common subsequence of $A$ and $B$,
   the procedure should return an array containing this sequence.
  Otherwise, the procedure should return $[-1]$
   (an array of length $1$, whose only element is $-1$).
* This procedure is called exactly once for each test case.

## Constraints

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ for each $i$ such that $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ for each $j$ such that $0 \leq j < M$

## Subtasks

| Subtask | Score  | Additional Constraints |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; $A$ and $B$ both consist of $N$ *distinct* integers between $0$ and $N-1$ (inclusive)
| 2       | $15$   | For any integer $k$, the number of elements of $A$ equal to $k$ *plus* the number of elements of $B$ equal to $k$ is at most $3$.
| 3       | $10$   | $A[i] \leq 1$ for each $i$ such that $0 \leq i < N$; $B[j] \leq 1$ for each $j$ such that $0 \leq j < M$
| 4       | $16$   | There exists a universal common subsequence of $A$ and $B$.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | No additional constraints.

## Examples

### Example 1

Consider the following call.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Here, the common subsequences of $A$ and $B$ are the following:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ and $[0, 1, 0, 2]$.

Since $[0, 1, 0, 2]$ is a common subsequence of $A$ and $B$, and
 all common subsequences of $A$ and $B$ are subsequences of $[0, 1, 0, 2]$,
 the procedure should return $[0, 1, 0, 2]$.

### Example 2

Consider the following call.

```
ucs([0, 0, 2], [1, 1])
```

Here, the only common subsequence of $A$ and $B$ is the empty sequence $[\ ]$.
It follows that the procedure should return an empty array $[\ ]$.

### Example 3

Consider the following call.
```
ucs([0, 1, 0], [1, 0, 1])
```

Here, the common subsequences of $A$ and $B$ are
 $[\ ], [0], [1], [0, 1]$ and $[1, 0]$.
It can be shown that a universal common subsequence does not exist.
Therefore, the procedure should return $[-1]$.

## Sample Grader

Input format:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Output format:

```
T
R[0]  R[1]  ...  R[T-1]
```

Here, $R$ is the array returned by `ucs` and $T$ is its length.
