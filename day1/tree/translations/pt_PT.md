# Tree
Considera uma **árvore** formada por $N$ **vértices**,
 numerados de $0$ a $N-1$.
O vértice $0$ é chamado de **raíz**.
Todos os vértices, com excepção da raíz, têm um único **pai**.
Para cada $i$, tal que $1 \leq i < N$,
 o pai do vértice $i$ é o vértice $P[i]$, onde $P[i] < i$.
Assumimos também que $P[0] = -1$.

Para cada vértice $i$ ($0 \leq i < N$),
 a **subárvore** de $i$ é o conjunto dos seguintes vértices
 * $i$, e
 * qualquer vértice cujo pai é $i$, e
 * qualquer vértice cujo pai do pai seja $i$, e
 * qualquer vértice cujo pai do pai do pai seja $i$, e
 * etc.

A imagem abaixo mostra uma árvore exemplo com $N = 6$ vértices.
Cada seta liga um vértice ao seu pai, exceto a raíz, que não tem pai.
A subárvore do vértice $2$ contém os vértices $2, 3, 4$ e $5$.
A subárvore do vértice $0$ contém todos os $6$ vértices da árvore e
a subárvore do vértice $4$ contém apenas o vértice $4$.

![](subtrees.png "150")

A cada vértice é atribuído um **peso** inteiro não negativo
Denotamos o peso do vértice $i$ ($0 \leq i < N$) por $W[i]$.

A tua tarefa é escrever um programa para responder a $Q$ questões,
 cada uma especificada por um par de inteiros positivos $(L, R)$.
 A resposta a uma pergunta deve ser calculada da seguinte maneira.

Considera atribuir um inteiro,
 chamado de **coeficiente**, a cada vértice da árvore.
Estas atribuições são descritas por uma sequência $C[0], \ldots, C[N-1]$,
 onde $C[i]$ ($0 \leq i < N$) é o coeficiente atribuído ao vértice $i$.
Chamemos a esta sequência a **sequência de coeficientes**.
Nota que os elementos da sequência de coeficientes podem ser negativos, $0$, ou positivos.

Para uma pergunta $(L, R)$,
uma sequência de coeficientes é chamada de **válida**
 se, para cada vértice $i$ ($0 \leq i < N$),
 a seguinte condição é válida:
 a soma dos coeficientes dos vértices da subárvore do vértice $i$
 não é menor que $L$ e não é maior que $R$.

Para uma dada sequência de coeficientes $C[0], \ldots, C[N-1]$,
 o **custo** de um vértice $i$ é $|C[i]| \cdot W[i]$,
 onde $|C[i]|$ denota o valor absoluto de $C[i]$.
Finalmente, o **custo total** é a soma dos custos de todos os vértices.
A tua tarefa é calcular, para cada questão,
 o **custo mínimo total** que pode ser obtido por uma sequência de coeficientes válida.

Pode ser mostrado que para qualquer pergunta existe pelo menos uma sequência de coeficientes válida.

## Detalhes de Implementação

Deves implementar as seguintes duas funções:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$: arrays de inteiros de tamanho $N$ especificando os pais e os pesos.
* Esta função é chamada exatamente uma única vez em cada caso de teste no início da interação entre o avaliador o teu programa.

```
long long query(int L, int R)
```
* $L$, $R$: inteiros descrevendo uma pergunta.
* Esta função é chamada $Q$ vezes depois da invocação de `init` em cada caso de teste.
* Esta função deve devolver a resposta para a pergunta correspondente.


## Restrições

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ para cada $i$ tal que $1 \leq i < N$
* $0 \leq W[i] \leq 1\,000\,000$ para cada $i$ tal que $0 \leq i < N$
* $1 \leq L \leq R \leq 1\,000\,000$ em cada pergunta

## Subtarefas

| Subtarefa | Pontos  | Restrições Adicionais |
| :-----: | :----: | ---------------------- |
|   1     |  $10$  | $Q \leq 10$; $W[P[i]] \leq W[i]$ para cada $i$ tal que $1 \leq i < N$
|   2     |  $13$  | $Q \leq 10$; $N \leq 2\,000$
|   3     |  $18$  | $Q \leq 10$; $N \leq 60\,000$
|   4     |  $7$   | $W[i] = 1$ para cada $i$ tal que $0 \leq i < N$
|   5     |  $11$  | $W[i] \leq 1$ para cada $i$ tal que $0 \leq i < N$
|   6     |  $22$  | $L = 1$
|   7     |  $19$  | Sem restrições adicionais.



## Exemplos

Considera as seguintes chamadas:

```
init([-1, 0, 0], [1, 1, 1])
```
A árvore consiste em $3$ vértices, a raíz e os seus $2$ filhos.
Todos os vértices têm peso $1$.

```
query(1, 1)
```

Nesta pergunta $L = R = 1$,
 o que significa que a soma dos coeficientes em cada subárvore deve ser igual a $1$.
Considera a sequência de coeficientes $[-1, 1, 1]$.
A árvore e os coeficientes correspondentes (em retângulos a sombreado) estão ilustrados na figura.

![](ex1.png "150")

Para cada vértice $i$ ($0 \leq i < 3$), a soma dos coeficientes de todos os vértices na subárvore $i$ é igual a $1$. 
Portanto, a sequência de coeficientes é válida. O custo total pode ser calculado da seguinte maneira:


| Vértice | Peso | Coeficiente | Custo                     |
| :----: | :----: | :---------: | :-----------------------: |
|   0    |   1    |     -1      | $\mid -1 \mid \cdot 1 = 1$
|   1    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$
|   2    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$

Portanto o custo total é $3$.
Esta é a única sequência de coeficientes válida, e por isso esta chamada deve devolver $3$.

```
query(1, 2)
```
O custo total mínimo para esta chamada é $2$,
 e pode ser obtido quando a sequência de coeficientes é $[0, 1, 1]$.

## Avaliador Exemplo

Formato de input:

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

onde $L[j]$ and $R[j]$
 (para $0 \leq j < Q$)
 são os argumentos do input na $j$-ésima chamada a `query`.
Nota que a segunda linha de input contém **somente $N-1$ inteiros**,
 uma vez que o avaliador exemplo não lê o valor de $P[0]$.

Formato de output:
```
A[0]
A[1]
...
A[Q-1]
```

onde $A[j]$
 (para $0 \leq j < Q$)
 é o valor devolvido pela $j$-ésima chamada a `query`.
