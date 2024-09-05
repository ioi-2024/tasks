# Hádanka Sfingy

Velká sfinga pro vás má hádanku.
Dostanete graf s $N$ vrcholy.
Tyto vrcholy jsou očíslované od $0$ do $N - 1$.
V grafu je $M$ hran, očíslovaných od $0$ do $M - 1$.
Každá hrana spojuje dva různé vrcholy a je obousměrná.
Konkrétně pro každé $j$ od $0$ do $M - 1$ (včetně) platí,
 že hrana $j$ spojuje vrcholy $X[j]$ a $Y[j]$.
Jednu dvojici vrcholů spojuje maximálně jedna hrana.
Dva vrcholy nazveme **sousední**
 pokud jsou spojeny hranou.

Posloupnost vrcholů $v_0, v_1, \ldots, v_k$ (pro $k \ge 0$)
 nazveme **cesta**
 pokud pro každé dva po sobě jdoucí vrcholy $v_l$ a $v_{l+1}$
 (pro každé $l$ kde $0 \le l \lt k$)
 jsou sousední.
Říkáme, že cesta $v_0, v_1, \ldots, v_k$ **spojuje** vrcholy $v_0$ a $v_k$.
V grafu, který dostanete, spojuje každou dvojici vrcholů nějaká cesta.

Existuje $N + 1$ barev očíslovaných od $0$ do $N$.
Barva $N$ je speciální a říká se jí **barva Sfingy**.
Každý vrchol má přiřazenou barvu.
Konkrétně má vrchol $i$ ($0 \le i \lt N$) barvu $C[i]$.
Více vrcholů může mít stejnou barvu
 a mohou být barvy, které nemá žádný vrchol.
Žádný vrchol nemá barvu Sfingy,
 tedy $0 \le C[i] \lt N$ ($0 \le i \lt N$).

Cestu $v_0, v_1, \ldots, v_k$ (for $k \ge 0$)
 nazveme **jednobarevnou**
 pokud všechny její vrcholy mají stejnou barvu,
 tj. $C[v_l] = C[v_{l+1}]$ (pro každé $l$ kde $0 \le l \lt k$).
Dále řekneme, že vrcholy $p$ a $q$ ($0 \le p \lt N$, $0 \le q \lt N$)
 jsou ve stejné **jednobarevné komponentě**
 právě tehdy, když je spojuje jednobarevná cesta.

Znáte vrcholy a hrany,
 ale neznáte, jakou barvu má každý z vrcholů.
Chcete najít barvy jednotlivých vrcholů tím,
 že provedete **přebarvovací experimenty**.

Během přebarvovacího experimentu
 můžete přebarvit libovolné množství vrcholů.
Abyste provedli přebarvovací experiment
 musíte nejprve určit pole $E$ o velikosti $N$,
 kde pro každé $i$ ($0 \le i \lt N$)
 leží $E[i]$ mezi $-1$ a $N$ **včetně**.
Poté se barva každého vrcholu $i$ změní na $S[i]$, kde $S[i]$ je:
* $C[i]$, tedy původní barva $i$, pokud $E[i] = -1$, nebo
* $E[i]$ v ostatních případech.

Všimněte si, že to znamená, že ve vašem přebarvování můžete použít barvu Sfingy.

Nakonec Velká sfinga vyhlásí 
 počet jednobarevných komponent v grafu
 po přebarvení všech vrcholů $i$ na barvu $S[i]$ ($0 \le i \lt N$).
Toto nové obarvení se použije jen pro tento konkrétní přebarvovací experiment,
 takže **se barvy všech vrcholů na konci přebarvovacího experimentu změní zpátky**.

Vaším úkolem je zjistit barvy vrcholů grafu
 provedením nejvýše $2\,750$ přebarvovacích experimentů. 
Můžete také získat část bodů
 pokud pro každou dvojici sousedních vrcholů zjistíte,
 jestli mají stejnou barvu.

## Implementační detaily

Měli byste implementovat následující funkci:

```
std::vector&lt;int&gt; find_colours(int N,
    std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y)
```

* $N$: počet vrcholů v grafu.
* $X$, $Y$: pole délky $M$ popisující hrany.
* Tato funkce by měla vrátit pole $G$ délky $N$
   reprezentující barvy vrcholů v grafu.
* Tato funkce je v každém vstupu zavolána právě jednou.

Výše uvedená funkce může zavolat následující funkci
 k provedení přebarvovacího experimentu:

```
int perform_experiment(std::vector&lt;int&gt; E)
```

* $E$: pole délky $N$ udávající, jak mají být vrcholy přebarveny.
* Tato funkce vrátí počet jednobarevných komponent
   po přebarvení vrcholů podle $E$.
* Tato funkce smí být zavolána maximálně $2\,750$krát.

Grader **není adaptivní**,
 tedy barvy vrcholů jsou pevně určeny před tím, než je zavolána funkce `find_colours`.

## Omezení

* $2 \le N \le 250$
* $N - 1 \le M \le \frac{N \cdot (N - 1)}{2}$
* $0 \le X[j] \lt Y[j] \lt N$ pro každý $j$ takové, že $0 \le j \lt M$.
* $X[j] \neq X[k]$ nebo $Y[j] \neq Y[k]$
   pro každé $j$ a $k$ takové, že $0 \le j \lt k \lt M$.
* Každou dvojici vrcholů spojuje nějaká cesta.
* $0 \le C[i] \lt N$ pro každé $i$ takové, že $0 \le i \lt N$.

## Podúlohy

| Podúloha | Počet bodů | Další omezení |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = 2$
| 2       | $7$    | $N \le 50$
| 3       | $33$   | Graf je cesta: $M = N - 1$ a vrcholy $j$ a $j+1$ jsou sousední ($0 \leq j < M$).
| 4       | $21$   | Graf je úplný: $M = \frac{N \cdot (N - 1)}{2}$ a každé dva vrcholy jsou sousední.
| 5       | $36$   | Žádná další omezení.

V každé podúloze můžete získat částečné body
 pokud váš program pro každou dvojici sousedních vrcholů
 správně určí, jestli mají stejnou barvu.

Přesněji dostanete za nějakou podúlohu plný počet bodů,
 pokud je ve všech jeho vstupech pole $G$ vrácené `find_colours`
 přesně stejné jako pole $C$
 (tj. $G[i] = C[i]$ pro každé $i$ takové, že $0 \le i \lt N$).
Jinak dostanete za podúlohu $50\%$ bodů,
 pokud ve všech jeho vstupech platí následující podmínky:
* $0 \le G[i] \lt N$
   pro každé $i$ takové, že $0 \le i \lt N$;
* Pro každé $j$ takové, že $0 \le j \lt M$:
  * $G[X[j]] = G[Y[j]]$ právě tehdy, když $C[X[j]] = C[Y[j]]$.

## Příklad

Uvažujme následující volání:

```
find_colours(4, [0, 1, 0, 0], [1, 2, 2, 3])
```

Pro tento příklad předpokládejme,
 že (skryté) barvy vrcholů udává
 $C = [2, 0, 0, 0]$.
Tento scénář znázorňuje následující ilustrace.
Barvy jsou navíc znázorněny čísly v bílých štítcích na každém z vrcholů.

![example.png](sphinx_example.png "230")

Funkce může zavolat `perform_experiment` následujícím způsobem:

```
perform_experiment([-1, -1, -1, -1])
```

V tomto volání není přebarven žádný vrchol, protože si všechny vrcholy zachovají svoji původní barvu.

Uvažujme vrchol $1$ a vrchol $2$.
Oba mají barvu $0$ cesta $1, 2$ je jednobarevnou cestou.
Vrcholy $1$ a $2$ jsou proto ve stejné jednobarevné komponentě.

Uvažujme vrchol $1$ a vrchol $3$.
Přestože oba mají barvu $0$,
 tak jsou v různých jednobarevných komponentách,
 protože neexistuje jednobarevná cesta, která je spojuje.

Celkem existují $3$ jednobarevné komponenty
 s vrcholy $\{0\}$, $\{1, 2\}$, a $\{3\}$.
Tedy toto volání vrátí $3$.

Teď může funkce zavolat `perform_experiment` následujícím způsobem:

```
perform_experiment([0, -1, -1, -1])
```

V tomto volání je jen vrchol $0$ přebarven na barvu $0$,
 což vyústí v obarvení zobrazeném na následující ilustraci:

![example.png](sphinx_order1.png "230")

Toto volání vrátí $1$, protože všechny vrcholy leží ve stejné jednobarevné komponentě.
Teď si můžeme odvodit, že vrcholy $1$, $2$, a $3$ mají barvu $0$.

Funkce může dále zavolat `perform_experiment` následujícím způsobem:

```
perform_experiment([-1, -1, -1, 2])
```

V tomto volání je vrchol $3$ přebarven na barvu $2$,
 což vyústí v obarvení zobrazeném na následující ilustraci:

![example.png](sphinx_order2.png "230")

Toto volání vrátí $2$, protože existují $2$ jednobarevné komponenty,
 po řadě s vrcholy $\{0, 3\}$ a $\{1, 2\}$. 
Teď si můžeme odvodit, že vrchol $0$ má barvu $2$.

Funkce `find_colours` poté vrátí $[2, 0, 0, 0]$.
Protože $C = [2, 0, 0, 0]$, tak jsou uděleny plné body.

Všimněte si, že existuje několik návratových hodnot, za které by bylo uděleno $50\%$ bodů,
 například $[1, 2, 2, 2]$ nebo $[1, 2, 2, 3]$.

## Ukázkový grader

Formát vstupu:

```
N  M
C[0]  C[1] ... C[N-1]
X[0]  Y[0]
X[1]  Y[1]
...
X[M-1]  Y[M-1]
```

Formát výstupu:

```
L  Q
G[0]  G[1] ... G[L-1]
```

Zde je $L$ délka pole $G$ vráceného `find_colours`
 a $Q$ počet volání `perform_experiment`.
