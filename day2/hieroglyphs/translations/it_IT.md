# Hieroglyphs

Un team di ricercatori sta studiando somiglianze tra sequenze di geroglifici.
Ciascun geroglifico è rappresentato da un numero intero non negativo.
Per svolgere il loro studio, i ricercatori utilizzano le seguenti definizioni sulle sequenze.

Data una sequenza $A$,
 una sequenza $S$ è chiamata **sottosequenza** di $A$
 se e solo se $S$ può essere ottenuto
 rimuovendo alcuni elementi (eventualmente nessuno) da $A$.

La tabella seguente mostra alcuni esempi di sottosequenze di una sequenza $A = [3, 2, 1, 2]$.

| Sottosequenza | Come si può ottenere da $A$ |
|----------------|--------------------------------|
| [3, 2, 1, 2] | Nessun elemento viene rimosso.
| [2, 1, 2] | [<s>3</s>, 2, 1, 2]
| [3, 2, 2] | [3, 2, <s>1</s>, 2]
| [3, 2] | [3, <s>2</s>, <s>1</s>, 2] o [3, 2, <s>1</s>, <s>2</s>]
| [3] | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ] | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Invece, $[3, 3]$ o $[1, 3]$ non sono sottosequenze di $A$.

Consideriamo due sequenze di geroglifici, $A$ e $B$.
Una sequenza $S$ è chiamata **sottosequenza comune** di $A$ e $B$
 se e solo se $S$ è una sottosequenza sia di $A$ che di $B$.
Inoltre, diciamo che una sequenza $U$ è una **sottosequenza comune universale** di $A$ e $B$
 se e solo se sono soddisfatte le due seguenti condizioni:
* $U$ è una sottosequenza comune di $A$ e $B$.
* Ogni sottosequenza comune di $A$ e $B$ è anche una sottosequenza di $U$.

Si può dimostrare che due sequenze qualsiasi $A$ e $B$
 hanno al massimo una sottosequenza comune universale.

I ricercatori hanno trovato due sequenze di geroglifici $A$ e $B$.
La sequenza $A$ è composta da $N$ geroglifici
 e la sequenza $B$ è composta da $M$ geroglifici.
Aiuta i ricercatori a calcolare
 una sottosequenza comune universale delle sequenze $A$ e $B$,
 oppure determina che tale sequenza non esiste.

## Note di implementazione

Devi implementare la seguente funzione.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: un array di lunghezza $N$ che descrive la prima sequenza.
* $B$: un array di lunghezza $M$ che descrive la seconda sequenza.
* Se esiste una sottosequenza comune universale di $A$ e $B$,
   la funzione deve restituire un array contenente questa sequenza.
  Altrimenti la funzione deve restituire $[-1]$
   (un array di lunghezza $1$, il cui unico elemento è $-1$).
* Questa funzione viene chiamata esattamente una volta per ogni caso di test.

## Assunzioni

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ per ogni $i$ tale che $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ per ogni $j$ tale che $0 \leq j < M$

## Subtask

| Subtask | Punteggio | Limitazioni aggiuntive |
| :-----: | :----: | ---------------------- |
| 1 | $3$ | $N = M$; sia $A$ sia $B$ sono costituiti da $N$ numeri interi **distinti** compresi tra $0$ e $N-1$ (inclusi).
| 2 | $15$ | Per qualsiasi intero $k$, (il numero di elementi di $A$ uguali a $k$) più (il numero di elementi di $B$ uguali a $k$) è al massimo $3$.
| 3 | $10$ | $A[i] \leq 1$ per ogni $0 \leq i < N$; $B[j] \leq 1$ per ogni $0 \leq j < M$.
| 4 | $16$ | Esiste una sottosequenza comune universale di $A$ e $B$.
| 5 | $14$ | $N \leq 3000$; $M \leq 3000$.
| 6 | $42$ | Nessuna limitazione aggiuntiva.

## Esempi

### Esempio 1

Consideriamo la seguente chiamata.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

In questo caso, le sottosequenze comuni di $A$ e $B$ sono le seguenti:
 $[\ ]$, $[0]$, $[1]$, $[2]$ $[0, 0]$, $[0, 1]$, $[0, 2]$ $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ e $[0, 1, 0, 2]$.

Poiché $[0, 1, 0, 2]$ è una sottosequenza comune di $A$ e $B$, e
 tutte le sottosequenze comuni di $A$ e $B$ sono sottosequenze di $[0, 1, 0, 2]$,
 la funzione deve restituire $[0, 1, 0, 2]$.

### Esempio 2

Consideriamo la seguente chiamata.

```
ucs([0, 0, 2], [1, 1])
```

In questo caso, l'unica sottosequenza comune di $A$ e $B$ è la sequenza vuota $[\ ]$.
Ne consegue che la funzione deve restituire un array vuoto $[\ ]$.

### Esempio 3

Consideriamo la seguente chiamata.
```
ucs([0, 1, 0], [1, 0, 1])
```

In questo caso, le sottosequenze comuni di $A$ e $B$ sono
 $[\ ], [0], [1], [0, 1]$ e $[1, 0]$.
Si può dimostrare che non esiste una sottosequenza comune universale.
Pertanto, la funzione deve restituire $[-1]$.

## Grader di esempio

Formato di input:

```
N M
A[0] A[1] ... A[N-1]
B[0] B[1] ... B[M-1]
```

Formato di output:

```
T
R[0] R[1] ... R[T-1]
```

dove $R$ è l'array restituito da `ucs` e $T$ è la sua lunghezza.
