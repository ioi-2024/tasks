# Sfinkso galvosūkis

Didysis Sfinksas tau paruošė galvosūkį.
Tau duotas grafas su $N$ viršūnių.
Viršūnės sunumeruotos nuo $0$ iki $N - 1$.
Grafe yra $M$ briaunų, sunumeruotų nuo $0$ iki $M - 1$.
Kiekviena briauna jungia skirtingų viršūnių porą ir yra dvikryptė.
Kitaip tariant, kiekvienam $j$ nuo $0$ iki $M - 1$ imtinai,
 briauna $j$ jungia viršūnes $X[j]$ ir $Y[j]$.
Kiekvieną viršūnių porą jungia ne daugiau kaip viena briauna.
Dvi viršūnės vadinamos **gretimomis**,
 jeigu jos sujungtos briauna.
 
<!-- The Great Sphinx has a riddle for you. 
You are given a graph on $N$ vertices.
The vertices are numbered from $0$ to $N - 1$.
There are $M$ edges in the graph.
Each edge connects a pair of distinct vertices and is bidirectional.
Two vertices are called **adjacent**
 if they are connected by an edge.
Specifically, for each $j$ from $0$ to $M - 1$, inclusive,
 vertices $X[j]$ and $Y[j]$ are adjacent.
There is at most one edge connecting any pair of vertices. -->

Viršūnių seka $v_0, v_1, \ldots, v_k$ (čia $k \ge 0$)
 vadinama **keliu**,
 jei sekoje greta esančios viršūnių poros $v_l$ ir $v_{l+1}$,
 (visiems $l$, kur $0 \le l \lt k$)
 yra gretimos.
<!-- A sequence of vertices $v_0, v_1, \ldots, v_k$ (for $k \ge 0$)
 is called a **path**
 if each two consecutive vertices $v_l$ and $v_{l+1}$
 (for each $l$ such that $0 \le l \lt k$)
 are adjacent. -->
Sakome, kad kelias $v_0, v_1, \ldots, v_k$ **jungia** viršūnes $v_0$ ir $v_k$.
Jums duotame grafe kiekvieną viršūnių porą jungia kažkoks kelias.
<!-- We say that a path $v_0, v_1, \ldots, v_k$ **connects** vertices $v_0$ and $v_k$.
In the graph given to you, each pair of vertices is connected by some path. -->

Yra $N + 1$ spalvų, sunumeruotų nuo $0$ iki $N$.
Spalva $N$ yra ypatinga ir mes ją vadiname **Sfinkso spalva**.
Kiekviena viršūnė nuspalvinta viena iš spalvų.
$i$-oji viršūnė ($0 \le i \lt N$) nuspalvinta spalva $C[i]$.
Skirtingos viršūnės gali būti tos pačios spalvos
ir gali būti spalvų, kuriomis nenuspalvinta nei viena viršūnė.
Jokia viršūnė nėra nuspalvinta Sfinkso spalva,
 taigi $0 \le C[i] \lt N$ ($0 \le i \lt N$).
<!-- There are $N + 1$ colours, numbered from $0$ to $N$.
Colour $N$ is special and is called the **Sphinx's colour**.
Each vertex is assigned a colour.
Specifically, vertex $i$ ($0 \le i \lt N$) has colour $C[i]$.
Multiple vertices may have the same colour, 
and there might be colours not assigned to any vertex.
No vertex has the Sphinx's colour,
 that is, $0 \le C[i] \lt N$ ($0 \le i \lt N$). -->

Kelias $v_0, v_1, \ldots, v_k$ (kur $k \ge 0$)
 vadinamas **vienspalviu**
 jeigu
 visos jo viršūnės nuspalvintos ta pačia spalva,
 t. y. $C[v_l] = C[v_{l+1}]$ (kiekvienam $l$, kuriam $0 \le l \lt k$).
<!-- A path $v_0, v_1, \ldots, v_k$ (for $k \ge 0$)
 is called **monochromatic**
 if
 all of its vertices have the same colour,
 i.e. $C[v_l] = C[v_{l+1}]$ (for each $l$ such that $0 \le l \lt k$). -->
Taip pat sakome, kad viršūnės $p$ ir $q$ ($0 \le p \lt N$, $0 \le q \lt N$)
 priklauso tam pačiam **vienspalviam komponentui**
 tada ir tik tada, jei jas jungia vienspalvis kelias.
<!-- Additionally, we say that vertices $p$ and $q$ ($0 \le p \lt N$, $0 \le q \lt N$)
 are in the same **monochromatic component**
 if and only if they are connected by a monochromatic path. -->

Jūs žinote viršūnes ir briaunas,
 bet nežinote, kokios spalvos yra kiekviena viršūnė.
<!-- You know the vertices and edges,
 but you do not know which colour each vertex has. -->
Jūs norite sužinoti viršūnių spalvas
 atlikdami **perspalvinimo eksperimentus**.
<!-- You want to find out the colours of the vertices,
 by performing **recolouring experiments**. -->

Perspalvinimo eksperimento metu
 jūs galite perspalvinti bet kiek viršūnių.
<!-- In a recolouring experiment,
 you may recolour arbitrarily many vertices. -->
 Norint atlikti perspalvinimo eksperimentą,
 jūs pirmiausiai pasirenkate $N$ dydžio masyvą $E$,
 kur kiekvienam $i$ ($0 \le i \lt N$),
 $E[i]$ yra tarp $-1$ ir $N$ **imtinai**.
<!-- Specifically, to perform a recolouring experiment
 you first choose an array $E$ of size $N$,
 where for each $i$ ($0 \le i \lt N$),
 $E[i]$ is between $-1$ and $N$ **inclusive**. -->
Tada viršūnės $i$ spalva tampa $S[i]$, kur $S[i]$ lygi:
* $C[i]$, taigi pradinei viršūnės $i$ spalvai, jei $E[i] = -1$, arba
* $E[i]$ kitu atveju.

Atkreipkite dėmesį, kad tai reiškia, kad perspalvindami galite naudoti Sfinkso spalvą.
<!-- Note that this means that you can use the Sphinx's colour in your recolouring. -->

Galiausiai Didysis Sfinksas praneša
 vienspalvių komponentų kiekį grafe
 po to, kai kiekviena viršūnė $i$ nuspalvinama $S[i]$ ($0 \le i \lt N$) spalva.
<!-- Finally, the Great Sphinx announces
 the number of monochromatic components in the graph,
 after setting the colour of each vertex $i$ to $S[i]$ ($0 \le i \lt N$). -->
Kiekvienas spalvinimas naudojamas tik tam nuspalvinimo eksperimentui,
 taigi **pasibaigus eksperimentui visos viršūnės vėl yra pradinių spalvų**.
<!-- The new colouring is applied only for this particular recolouring experiment,
 so **the colours of all vertices return to the original ones after the experiment finishes**. -->

Nustatykite grafo viršūnių spalvas
 atlikdami daugiausiai $2\,750$ perspalvinimo eksperimentų.
<!-- Your task is to identify the colours of the vertices in the graph
 by performing at most $2\,750$ recolouring experiments.  -->
Jūs taip pat galite gauti dalinių taškų,
 jei kiekvienai gretimų viršūnių porai nustatote,
 ar jos turi tą pačią spalvą.
<!-- You may also receive a partial score
 if you correctly determine for every pair of adjacent vertices,
 whether they have the same colour. -->

## Realizacija

Jums reikia parašyti šią procedūrą.
<!-- You should implement the following procedure. -->

```
std::vector&lt;int&gt; find_colours(int N,
    std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y)
```

* $N$: viršūnių grafe skaičius.
* $X$, $Y$: $M$ ilgių masyvai, nusakantys briaunas.
* Ši procedūra turi grąžinti $N$ ilgio masyvą $G$,
  nurodantį grafo viršūnių spalvas.
* Ši procedūra kiekvienam testui iškviečiama lygiai vieną kartą.

<!-- * $N$: the number of vertices in the graph.
* $X$, $Y$: arrays of length $M$ describing the edges.
* This procedure should return an array $G$ of length $N$,
   representing the colours of vertices in the graph.
* This procedure is called exactly once for each test case. -->

Aukščiau esanti procedūra gali iškviesti šią procedūrą,
 kad atliktų perspalvinimo eksperimentus:
<!-- The above procedure can make calls to the following procedure
 to perform recolouring experiments: -->

```
int perform_experiment(std::vector&lt;int&gt; E)
```

* $E$: $N$ ilgio masyvas, nurodantis, kaip perspalvinti viršūnes.
* Ši procedūra grąžina vienspalvių komponentų skaičių
  po to, kai viršūnės perspalvinamos pagal masyve $E$ nurodytas spalvas.
* Ši procedūra gali būti iškviesta daugiausiai $2\,750$ kartų.

<!-- * $E$: an array of length $N$ specifying how vertices should be recoloured.
* This procedure returns the number of monochromatic components
   after recolouring the vertices according to $E$.
* This procedure can be called at most $2\,750$ times. -->

Vertinimo programa **nėra adaptyvi**, taigi
 viršūnės yra nuspalvinamos prieš iškviečiant `find_colours`.
<!-- The grader is **not adaptive**, that is,
 the colours of the vertices are fixed before a call to `find_colours` is made. -->

## Ribojimai

* $2 \le N \le 250$
* $N - 1 \le M \le \frac{N \cdot (N - 1)}{2}$
* $0 \le X[j] \lt Y[j] \lt N$ visiems $j$, kur $0 \le j \lt M$.
* $X[j] \neq X[k]$ arba $Y[j] \neq Y[k]$
   visiems $j$ ir $k$, kur $0 \le j \lt k \lt M$.
* Kiekvieną viršūnių porą jungia kažkoks kelias.
* $0 \le C[i] \lt N$ visiems $i$, kur $0 \le i \lt N$.

## Dalinės užduotys

| Dalinė užduotis | Taškai  | Papildomi ribojimai |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = 2$
| 2       | $7$    | $N \le 50$
| 3       | $33$   | Grafas yra kelias: $M = N - 1$ ir viršūnės $j$ ir $j+1$ yra gretimos ($0 \leq j < M$).
| 4       | $21$   | Grafas yra pilnas: $M = \frac{N \cdot (N - 1)}{2}$ ir bet kurios dvi viršūnės yra gretimos.
| 5       | $36$   | Jokių papildomų ribojimų.

Kiekvienoje dalinėje užduotyje jūs galite surinkti dalį taškų,
 jei jūsų programa kiekvienai viršūnių porai
 teisingai nustato,
 ar tos viršūnės turi tą pačią spalvą.
<!-- In each subtask, you can obtain a partial score
 if your program determines correctly
 for every pair of adjacent vertices
 whether they have the same colour. -->

Jūs gausite visus dalinės užduoties taškus,
 jei visuose jos testuose
 procedūros `find_colours` grąžintas masyvas $G$
 sutaps su masyvu $C$
 (t. y. $G[i] = C[i]$
 visiems $i$, kur $0 \le i \lt N$).
Kitu atveju
 gausite $50\%$ dalinės užduoties taškų,
 jeigu visiems tos dalinės užduoties testams
 galioja:
* $0 \le G[i] \lt N$
  visiems $i$, kur $0 \le i \lt N$;
* Visiems $j$, kur $0 \le j \lt M$:
  * $G[X[j]] = G[Y[j]]$ tada ir tik tada, kai $C[X[j]] = C[Y[j]]$.

<!-- More precisely,
 you get the whole score of a subtask
 if in all of its test cases,
 the array $G$ returned by `find_colours`
 is exactly the same as array $C$
 (i.e. $G[i] = C[i]$
 for all $i$ such that $0 \le i \lt N$).
Otherwise,
 you get $50\%$ of the score for a subtask
 if the following conditions hold
 in all of its test cases:
* $0 \le G[i] \lt N$
   for each $i$ such that $0 \le i \lt N$;
* For each $j$ such that $0 \le j \lt M$:
  * $G[X[j]] = G[Y[j]]$ if and only if $C[X[j]] = C[Y[j]]$. -->

## Pavyzdys

Panagrinėkime šį iškvietimą.
<!-- Consider the following call. -->

```
find_colours(4, [0, 1, 0, 0], [1, 2, 2, 3])
```

Tarkime, kad šiam pavyzdžiui
 (mums nežinomos) viršūnių spalvos yra
 $C = [2, 0, 0, 0]$.
<!-- For this example, suppose that
 the (hidden) colours of the vertices are given by
 $C = [2, 0, 0, 0]$. -->
Šis scenarijus pavaizduotas žemiau esančioje diagramoje.
<!-- This scenario is shown in the following figure. -->
Spalvas taip pat žymi prie kiekvienos viršūnės esantis skaičius baltame fone.
<!-- Colours are additionally represented by numbers on white labels attached to each vertex. -->

![example.png](sphinx_example.png "230")

Procedūra gali iškviesti `perform_experiment` tokiu būdu.
<!-- The procedure may call `perform_experiment` as follows. -->

```
perform_experiment([-1, -1, -1, -1])
```

Šiame iškvietime nei viena viršūnė nėra perspalvinama, taigi visos viršūnės lieka nuspalvintos pradinėmis spalvomis.
<!-- In this call, no vertex is recoloured, as all vertices keep their original colours. -->

Panagrinėkime $1$-ą ir $2$-ą viršūnes.
<!-- Consider vertex $1$ and vertex $2$. -->
Jos abi nuspalvintos $0$-ine spalva ir kelias $1, 2$ yra vienspalvis.
<!-- They both have colour $0$ and the path $1, 2$ is a monochromatic path. -->
Taigi viršūnės $1$ ir $2$ yra tame pačiame vienspalviame komponente.
<!-- As a result, vertices $1$ and $2$ are in the same monochromatic component. -->

Panagrinėkime $1$-ą ir $3$-ią viršūnes.
<!-- Consider vertex $1$ and vertex $3$. -->
Nors abi viršūnės nuspalvintos $0$-ine spalva,
 jos yra skirtinguose vienspalviuose komponentuose,
 nes nėra jokio vienspalvio kelio, kuris jas jungia.
<!-- Even though both of them have colour $0$,
 they are in different monochromatic components
 as there is no monochromatic path connecting them. -->

Iš viso yra $3$ vienspalviai komponentai,
 kuriuos sudaro viršūnės $\{0\}$, $\{1, 2\}$, bei $\{3\}$.
<!-- Overall, there are $3$ monochromatic components,
 with vertices $\{0\}$, $\{1, 2\}$, and $\{3\}$. -->
Taigi šis iškvietimas grąžina $3$.
<!-- Thus, this call returns $3$. -->

Dabar procedūra gali iškviesti `perform_experiment` tokiu būdu.
<!-- Now the procedure may call `perform_experiment` as follows. -->

```
perform_experiment([0, -1, -1, -1])
```

Šiame iškvietime tik $0$-inė viršūnė perspalvinama $0$-ine spalva,
 taigi mūsų grafas tampa nuspalvintas, kaip pavaizduota žemiau esančioje diagramoje.
<!-- In this call, only vertex $0$ is recoloured to colour $0$,
 which results in the colouring shown in the following figure. -->

![example.png](sphinx_order1.png "230")

Šis iškvietimas grąžina $1$, nes visos viršūnės priklauso tam pačiam vienspalviam komponentui.
<!-- This call returns $1$, as all the vertices belong to the same monochromatic component. -->
Mes dabar galime nustatyti, kad $1$-a, $2$-a ir $3$-ia viršūnės yra nuspalvintos $0$-ine spalva.
<!-- We can now deduce that vertices $1$, $2$, and $3$ have colour $0$. -->

Procedūra tada gali iškviesti `perform_experiment` tokiu būdu.
<!-- The procedure may then call `perform_experiment` as follows. -->

```
perform_experiment([-1, -1, -1, 2])
```

Šiame iškvietime $3$-ia viršūnė perspalvinama $2$-aja spalva,
 taigi mūsų grafas tampa nuspalvintas, kaip pavaizduota žemiau esančioje diagramoje.
<!-- In this call, vertex $3$ is recoloured to colour $2$,
 which results in the colouring shown in the following figure. -->

![example.png](sphinx_order2.png "230")

Šis iškvietimas grąžina $2$, nes yra $2$ vienspalviai komponentai,
 kuriems atitinkamai priklauso viršūnės $\{0, 3\}$ bei $\{1, 2\}$.
<!-- This call returns $2$, as there are $2$ monochromatic components,
 with vertices $\{0, 3\}$ and $\{1, 2\}$ respectively.  -->
Mes galime nustatyti, kad $0$-inė viršūnė nuspalvinta $2$-aja spalva.
<!-- We can deduce that vertex $0$ has colour $2$. -->

Procedūra `find_colours` grąžina masyvą $[2, 0, 0, 0]$.
<!-- The procedure `find_colours` then returns the array $[2, 0, 0, 0]$. -->
Kadangi $C = [2, 0, 0, 0]$, surenkami visi taškai.
<!-- Since $C = [2, 0, 0, 0]$, full score is given. -->

Taip pat yra daugiau nei vienas masyvas, kurį grąžinus galima gauti $50\%$ taškų, pavyzdžiui $[1, 2, 2, 2]$ arba $[1, 2, 2, 3]$.
<!-- Note that there are also multiple return values, for which $50\%$ of the score would be given, for example $[1, 2, 2, 2]$ or $[1, 2, 2, 3]$. -->

## Pavyzdinė vertinimo programa

Pradinių duomenų formatas:
<!-- Input format: -->

```
N  M
C[0]  C[1] ... C[N-1]
X[0]  Y[0]
X[1]  Y[1]
...
X[M-1]  Y[M-1]
```

Rezultatų formatas
<!-- Output format: -->

```
L  Q
G[0]  G[1] ... G[L-1]
```

Čia $L$ yra procedūros `find_colours` grąžinto masyvo $G$ ilgis,
 o $Q$ yra procedūros `find_colours` atliktų `perform_experiment` iškvietimų kiekis.
<!-- Here, $L$ is the length of the array $G$ returned by `find_colours`,
 and $Q$ is the number of calls to `perform_experiment`. -->
