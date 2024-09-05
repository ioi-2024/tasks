# Hieroglyfy

Tým výzkumníků studuje podobnosti mezi posloupnostmi hieroglyfů. Výzkumníci reprezentují
každý hieroglyf nezáporným celým číslem. Při provádění výzkumu používají následující
koncepty o posloupnostech.

Pro zadanou posloupnost $A$ se posloupnost $S$ nazývá **podposloupnost** $A$ právě tehdy,
když $S$ může být získána odstraněním některých (případně žádných) prvků $A$.

Tabulka níže obsahuje některé podposloupnosti posloupnosti $A = [3, 2, 1, 2]$.

| Podposloupnost    | Jak se dá získat z $A$ |
|----------------|---------------------------------|
| [3, 2, 1, 2] | Žádné prvky nebyly odstraněny.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] nebo [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Naopak $[3, 3]$ nebo $[1, 3]$ nejsou podposloupnosti $A$.

Uvažujme dvě posloupnosti hieroglyfů, $A$ a $B$. Sekvence $S$ se nazývá
**společná podposloupnost** $A$ a $B$ právě tehdy, když $S$ je podposloupnost $A$ i $B$.
Dále, posloupnost $U$ nazýváme **univerzální společnou podposloupností** $A$ a $B$ právě tehdy,
když následující dvě podmínky jsou splněny:
* $U$ je společná podposloupnost $A$ a $B$.
* Každá společná podposloupnost $A$ a $B$ je podposloupností $U$.

Lze dokázat, že jakékoliv dvě posloupnosti $A$ a $B$ mají nejvýše jednu
univerzální společnou podposloupnost.

Vědci našli dvě posloupnosti hieroglyfů $A$ a $B$. Posloupnost $A$ se skládá z $N$ hieroglyfů
a posloupnost $B$ se skládá z $M$ hieroglyfů. Pomozte vědcům najít univerzální společnou
podposloupnost $A$ a $B$, nebo určete, že taková posloupnost neexistuje.

## Implementační detaily

Vaším úkolem je implementovat následující funkci.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: pole délky $N$ popisující první posloupnost.
* $B$: pole délky $M$ popisující druhou posloupnost.
* Pokud existuje univerzální společná podposloupnost $A$ a $B$,
   tato funkce by měla vrátit pole obsahující tuto posloupnost.
	 Jinak by tato funkce měla vrátit $[-1]$ (pole délky $1$ s jediným prvkem $-1$).
* Tato funkce je zavolána právě jednou v každém vstupu.

## Omezení

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ pro každé $i$ takové, že $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ pro každé $j$ takové, že $0 \leq j < M$

## Podúlohy

| Podúloha | Počet bodů  | Dodatečná omezení |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; $A$ i $B$ se skládají z $N$ **různých** celých čísel mezi $0$ a $N-1$ (včetně).
| 2       | $15$   | Pro jakékoliv celé číslo $k$, (počet prvků $A$ rovných $k$) plus (počet prvků $B$ rovných $k$) je nejvýše $3$.
| 3       | $10$   | $A[i] \leq 1$ pro každé $i$ takové, že $0 \leq i < N$; $B[j] \leq 1$ pro každé $j$ takové, že $0 \leq j < M$
| 4       | $16$   | Existuje univerzální společná podposloupnost $A$ a $B$.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | Žádná další omezení.

## Příklady

### Příklad 1

Uvažujme následující zavolání.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Zde jsou společné podposloupnosti $A$ a $B$ následující:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ a $[0, 1, 0, 2]$.

Protože $[0, 1, 0, 2]$ je společná podposloupnost $A$ a $B$ a všechny společné podposloupnosti $A$ a $B$
jsou podposloupnosti $[0, 1, 0, 2]$, by funkce měla vrátit $[0, 1, 0, 2]$.

### Příklad 2

Uvažujme následující zavolání.

```
ucs([0, 0, 2], [1, 1])
```

Jediná společná podposloupnost $A$ a $B$ je prázdná posloupnost $[\ ]$.
Proto by tato funkce měla vrátit prázdné pole $[\ ]$.

### Příklad 3

Uvažujme následující zavolání.
```
ucs([0, 1, 0], [1, 0, 1])
```

Společné podposloupnosti $A$ a $B$ jsou $[\ ], [0], [1], [0, 1]$ and $[1, 0]$.
Lze dokázat, že univerzální společná podposloupnost neexistuje. Proto by funkce měla vrátit $[-1]$.

## Ukázkový grader

Formát vstupu:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Formát výstupu:

```
T
R[0]  R[1]  ...  R[T-1]
```

Zde je $R$ pole vrácené `ucs` a $T$ je jeho délka.
