# Mosaic

A Salma planeia colorir um mosaico de de barro numa parede.
O mosaico é uma matriz de $N \times N$,
composta por $N^2$ azulejos quadrados de $1 \times 1$ que estão inicialmente sem nenhuma cor.
As linhas do mosaico são numeradas de $0$ a $N-1$ de cima para baixo,
e as colunas são numeradas de $0$ a $N-1$ da esquerda para a direita.
O azulejo na linha $i$ e coluna $j$ ($0 \leq i < N$, $0 \leq j < N$) é denotado por $(i,j)$.
Cada azulejo deve ser colorido a branco (denotado por $0$) ou a preto (denotado por $1$).

Para colorir o mosaico, a Salma escolhe primeiro dois arrays $X$ e $Y$ de tamanho $N$,
cada um consistindo em valores $0$ e $1$, tal que $X[0] = Y[0]$.
Ela pinta os azulejos da linha de cima (linha $0$) de acordo com o array $X$,
de modo que a cor do azulejo $(0,j)$ é $X[j]$ ($0 \leq j < N$).
Ela também pinta os azulejos da coluna mais à esquerda (coluna $0$) de acordo com o array $Y$,
de tal modo que a cor do azulejo $(i,0)$ é $Y[i]$ ($0 \leq i < N$).

Depois ela repete os seguintes passos, até todos os azulejos estarem coloridos:
* Ela descobre um qualquer azulejo $(i,j)$ *sem cor* tal que o seu vizinho de cima (azulejo $(i-1, j)$ e o seu vizinho da esquerda (azulejo $(i, j-1)$) estão ambos *já coloridos*.
* Então, ela pinta o azulejo $(i,j)$ de preto se ambos os vizinhos foram brancos; caso contrário ela pinta o azulejo $(i, j)$ de branco.

Pode ser mostrado que as cores finais dos azulejos não dependem da ordem em que a Salma os pinta.

A Yasmin está muito curiosa com as cores dos azulejos no mosaico.
Ela faz $Q$ perguntas à Salma, numeradas de $0$ a $Q-1$.
Na questão $k$ ($0 \leq k < Q$), a Yasmin especifica um subretângulo do mosaico através de:
* A sua linha mais em cima $T[k]$ e a sua linha mais em baixo $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* A sua coluna mais à esquerda $L[k]$ e a sua coluna mais à direita $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

A resposta à questão é o número de azulejos pretos neste subretângulo.
Mais especificamente, a Salma deve descobrir quantos azulejos $(i, j)$ existem,
tal que $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$,
e a cor do azulejo $(i,j)$ é preto.

Escreve um programa para responder às questões de Yasmin.

## Detalhes de Implementação

Deves implementar a seguinte função.

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: arrays de tamanho $N$ descrevendo as cores dos azulejos na linha de cima e as cores dos azulejos da coluna mais à esquerda, respetivamente.
* $T$, $B$, $L$, $R$: arrays de tamanho $Q$ descrevendo as questões feitas pela Yasmin.
* A função deve devolver um array $C$ de tamanho $Q$, tal que 
 $C[k]$ fornece a resposta à questão $k$ ($0 \leq k < Q$).
* Esta função é chamada exatamente uma vez para cada caso de teste.

## Restrições

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ e $Y[i] \in \{0, 1\}$
 para cada $i$ tal que $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ e $0 \leq L[k] \leq R[k] < N$
 para cada $k$ tal que $0 \leq k < Q$

## Subtarefa

| Subtarefa | Pontos  | Restrições Adicionais |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ (para cada $k$ tal que $0 \leq k < Q$)
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ (para cada $i$ tal que $0 \leq i < N$)
| 6       | $22$   | $T[k] = B[k]$ e $L[k] = R[k]$ (para cada $k$ tal que $0 \leq k < Q$)
| 7       | $19$   | $T[k] = B[k]$ (para cada $k$ tal que $0 \leq k < Q$)
| 8       | $22$   | Nenhuma restrição adicional.

## Exemplo

Considera a seguinte chamada.

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Este exemplo está ilustrado nas figuras seguintes.
A figura da esquerda mostra as cores dos azulejos do mosaico.
As figuras do meio e da direita mostram os subretangulos da primeira e da segunda pergunta da Yasmin, respetivamente.

![](example.png "550")

As respostas às perguntas (isto é, o número de uns nos retângulos sombreados) são 7 e 3, respetivamente.
Deste modo, a função deve devolver $[7, 3]$.

## Avaliador Exemplo

Formato de input:

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

Formato de output:

```
C[0]
C[1]
...
C[S-1]
```

Aqui, $S$ é o tamanho do array $C$ devolvido por `mosaic`.
