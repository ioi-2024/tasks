# Mosaico

Salma planeja colorir um mosaico de argila em uma parede.
O mosaico é um reticulado $N \times N$,
 feito de $N^2$ ladrilhos quadrados  $1 \times 1$ inicialmente incolores.
As linhas do mosaico são numeradas de $0$ a $N-1$ de cima para baixo,
 e as colunas são numeradas de $0$ a $N-1$ da esquerda para a direita.
O ladrilho na linha $i$ e na coluna $j$ ($0 \leq i < N$, $0 \leq j < N$) é denotado por $(i,j)$.
Cada ladrilho deve ser colorido de
 branco (denotado por $0$) ou de preto (denotado por $1$).

Para colorir o mosaico, Salma primeiro escolhe dois vetores $X$ e $Y$ de tamanho $N$,
 cada um consistindo de valores $0$ e $1$, tais que $X[0] = Y[0]$.
Ela colore os ladrilhos da linha superior (linha $0$) de acordo com o vetor $X$,
 de modo que a cor do ladrilho $(0,j)$ seja $X[j]$ ($0 \leq j < N$).
Ela também colore os ladrilhos da coluna mais à esquerda (coluna $0$) de acordo com o vetor $Y$,
 de modo que a cor do ladrilho $(i,0)$ seja $Y[i]$ ($0 \leq i < N$).

Em seguida, ela repete os seguintes passos até que todas os ladrilhos estejam coloridos:
* Ela encontra qualquer ladrilho *incolor* $(i,j)$ tal que
 seu vizinho superior (ladrilho $(i-1, j)$) e vizinho esquerdo (ladrilho $(i, j-1)$)
 ambos *já estejam coloridos*.
* Então, ela colore o ladrilho $(i,j)$ de preto se ambos os vizinhos forem brancos;
 caso contrário, ela pinta o ladrilho $(i, j)$ de branco.

Pode-se demonstrar que as cores finais dos ladrilhos não dependem 
da ordem em que Salma os colore.
 
Yasmin está muito curiosa sobre as cores dos azulejos do mosaico.
Ela faz $Q$ perguntas a Salma, numeradas de $0$ a $Q-1$.
Na questão $k$ ($0 \leq k < Q$),
 Yasmin especifica um sub-retângulo do mosaico por:
* Linha superior $T[k]$ e linha inferior $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* Coluna mais à esquerda $L[k]$ e coluna mais à direita $R[k]$ ( $0 \leq L[k] \leq R[k] < N$).

A resposta para a pergunta é o número de ladrilhos pretos nesse sub-retângulo.
Especificamente, Salma deve descobrir quantos ladrilhos $(i, j)$ existem
 tal que $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$,
 e a cor do ladrilho $(i,j)$ é preto.

Escreva um programa que responda às perguntas de Yasmin.

## Detalhes de implementação

Você deve implementar o seguinte procedimento.

```
std::vector&lt;long long&gt; mosaic(
 std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
 std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
 std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: vetores de tamanho $N$ descrevendo as cores dos ladrilhos
 na linha mais acima e na coluna mais à esquerda, respectivamente.
* $T$, $B$, $L$, $R$: vetores de tamanho $Q$ descrevendo as perguntas feitas por Yasmin.
* O procedimento deve retornar um vetor $C$ de tamanho $Q$,
 de modo que $C[k]$ fornece a resposta à pergunta $k$ ( $0 \leq k < Q$).
* Este procedimento é chamado exatamente uma vez para cada caso de teste.

## Restrições

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ e $Y[i] \in \{0, 1\}$
 para cada $i$ tal que $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ e $0 \leq L[k] \leq R[k] < N$
 para cada $k$ tal que $0 \leq k < Q$

## Subtarefas

| Subtarefa | Pontuação | Restrições adicionais |
| :-----: | :----: | ---------------------- |
| 1 | $5$ | $N \leq 2; Q \leq 10$
| 2 | $7$ | $N \leq 200; Q \leq 200$
| 3 | $7$ | $T[k] = B[k] = 0$ (para cada $k$ tal que $0 \leq k < Q$)
| 4 | $10$ | $N \leq 5000$
| 5 | $8$ | $X[i] = Y[i] = 0$ (para cada $i$ tal que $0 \leq i < N$)
| 6 | $22$ | $T[k] = B[k]$ e $L[k] = R[k]$ (para cada $k$ tal que $0 \leq k < Q$)
| 7 | $19$ | $T[k] = B[k]$ (para cada $k$ tal que $0 \leq k < Q$)
| 8 | $22$ | Sem restrições adicionais.

## Exemplo

Considere a seguinte chamada.

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Este exemplo é ilustrado nas imagens abaixo.
A imagem da esquerda mostra as cores dos azulejos do mosaico.
As imagens do meio e da direita mostram os sub-retângulos sobre os quais
 Yasmin perguntou na primeira e segunda perguntas, respectivamente.

![](example.png "550")

As respostas para as perguntas
 (isto é, o número de 1's nos retângulos sombreados)
 são 7 e 3, respectivamente.
Portanto, o procedimento deve retornar $[7, 3]$.

## Corretor Exemplo

Formato de entrada:

```
N
X[0] X[1] ... X[N-1]
Y[0] Y[1] ... Y[N-1]
Q
T[0] B[0] L[0] R[0]
T[1] B[1] L[1] R[1]
...
T[Q-1] B[Q-1] L[Q-1] R[Q-1]
```

Formato de saída:

```
C[0]
C[1]
...
C[S-1]
```

Aqui, $S$ é o tamanho do vetor $C$ retornado por `mosaic`.