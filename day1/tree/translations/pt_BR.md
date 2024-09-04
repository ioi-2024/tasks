# Árvore

Considere uma **árvore** consistindo de $N$ **vértices**,
 numerados de $0$ a $N-1$.
O vértice $0$ é chamado de **raiz**.
Cada vértice, exceto a raiz, tem um único **pai**.
Para cada $i$, tal que $1 \leq i < N$,
 o pai do vértice $i$ é o vértice $P[i]$, onde $P[i] < i$.
Também assumimos $P[0] = -1$.

Para qualquer vértice $i$ ($0 \leq i < N$),
 a **subárvore** de $i$ é o conjunto dos seguintes vértices:
 * $i$, e
 * qualquer vértice cujo pai seja $i$, e
 * qualquer vértice cujo pai do pai seja $i$, e
 * qualquer vértice cujo pai do pai do pai seja $i$, e
 * etc.

A imagem abaixo mostra um exemplo de árvore consistindo de $N = 6$ vértices.
Cada seta conecta um vértice ao seu pai,
 exceto a raiz, que não tem pai.
A subárvore do vértice $2$ contém os vértices $2, 3, 4$ e $5$.
A subárvore do vértice $0$ contém todos os $6$ vértices da árvore
 e a subárvore do vértice $4$ contém apenas o vértice $4$.

![](subtrees.png "150")

Cada vértice recebe um **peso**, que é um inteiro não negativo.
Denotamos o peso do vértice $i$ ($0 \leq i < N$) por $W[i]$.

Sua tarefa é escrever um programa que responda $Q$ consultas,
 cada uma especificada por um par de inteiros positivos $(L, R)$.
A resposta da consulta deve ser calculada da seguinte forma.

Considere atribuir um inteiro,
 chamado de **coeficiente**, para cada vértice da árvore.
Tal atribuição é descrita por uma sequência $C[0], \ldots, C[N-1]$,
 onde $C[i]$ ($0 \leq i < N$) é o coeficiente atribuído ao vértice $i$.
Vamos chamar essa sequência de **sequência de coeficientes**.
Observe que os elementos da sequência de coeficientes podem ser negativos, $0$ ou positivos.

Para uma consulta $(L, R)$,
 uma sequência de coeficientes é chamada de **válida**
 se, para cada vértice $i$ ($0 \leq i < N$),
 a seguinte condição é válida:
 a soma dos coeficientes dos vértices na subárvore do vértice $i$
 não é menor que $L$ e não é maior que $R$.

Para uma dada sequência de coeficientes $C[0], \ldots, C[N-1]$,
 o **custo** de um vértice $i$ é $|C[i]| \cdot W[i]$,
 onde $|C[i]|$ denota o valor absoluto (módulo) de $C[i]$.
Por fim, o **custo total** é a soma dos custos de todos os vértices.
Sua tarefa é calcular, para cada consulta,
 o **custo total mínimo** que pode ser atingido por alguma sequência de coeficientes válida.

Pode ser provado que, para qualquer consulta, existe pelo menos uma sequência de coeficientes válida.

## Detalhes de implementação

Você deve implementar os dois procedimentos a seguir:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$ : vetores de inteiros de tamanho $N$
   especificando os pais e os pesos.
* Este procedimento é chamado exatamente uma vez
   no início da interação entre o avaliador e seu programa em cada caso de teste.

```
long long query(int L, int R)
```
* $L$, $R$ : inteiros que descrevem uma consulta.
* Este procedimento é chamado $Q$ vezes após a invocação de `init` em cada caso de teste.
* Este procedimento deve retornar a resposta para a consulta fornecida.


## Restrições

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ para cada $i$ tal que $1 \leq i < N$
* $0 \leq W[i] \leq 1\,000\,000$ para cada $i$ tal que $0 \leq i < N$
* $1 \leq L \leq R \leq 1\,000\,000$ em cada consulta

## Subtarefas

| Subtarefa | Pontuação | Restrições adicionais |
| :-----: | :----: | ---------------------- |
| 1 | $10$ | $Q \leq 10$ ; $W[P[i]] \leq W[i]$ para cada $i$ tal que $1 \leq i < N$
| 2 | $13$ | $Q \leq 10$ ; $N \leq 2\,000$
| 3 | $18$ | $Q \leq 10$ ; $N \leq 60\,000$
| 4 | $7$ | $W[i] = 1$ para cada $i$ tal que $0 \leq i < N$
| 5 | $11$ | $W[i] \leq 1$ para cada $i$ tal que $0 \leq i < N$
| 6 | $22$ | $L = 1$
| 7 | $19$ | Sem restrições adicionais.



## Exemplos

Considere as seguintes chamadas:

```
init([-1, 0, 0], [1, 1, 1])
```
A árvore consiste em $3$ vértices, a raiz e seus $2$ filhos.
Todos os vértices têm peso $1$.

```
query(1, 1)
```

Nesta consulta $L = R = 1$,
 o que significa que a soma dos coeficientes em cada subárvore deve ser igual a $1$.
Considere a sequência de coeficientes $[-1, 1, 1]$.
A árvore e os coeficientes correspondentes (em retângulos sombreados) são ilustrados abaixo.

![](ex1.png "150")

Para cada vértice $i$ ($0 \leq i < 3$), a soma dos coeficientes de todos os vértices
 na subárvore de $i$ é igual a $1$. 
Portanto, esta sequência de coeficientes é válida.
O custo total é calculado da seguinte forma:


| Vértice | Peso | Coeficiente | Custo |
| :----: | :----: | :---------: | :-----------------------: |
| 0 | 1 | -1 | $\mid -1 \mid \cdot 1 = 1$
| 1 | 1 | 1 | $\mid 1 \mid \cdot 1 = 1$
| 2 | 1 | 1 | $\mid 1 \mid \cdot 1 = 1$

Portanto, o custo total é $3$.
Esta é a única sequência de coeficientes válida,
 portanto esta chamada deve retornar $3$.

```
query(1, 2)
```
O custo total mínimo para esta consulta é de $2$,
 e é obtido quando a sequência de coeficientes é $[0, 1, 1]$.

## Corretor Exemplo

Formato de entrada:

```
N
P[1] P[2] ... P[N-1]
W[0] W[1] ... W[N-2] W[N-1]
Q
L[0] R[0]
L[1] R[1]
...
L[Q-1] R[Q-1]
```

onde $L[j]$ e $R[j]$
 (para $0 \leq j < Q$)
 são os argumentos de entrada na $j$-ésima chamada para `query`.
Observe que a segunda linha da entrada contém **apenas $N-1$ inteiros**,
 como o corretor exemplo não lê o valor de $P[0]$.

Formato de saída:
```
A[0]
A[1]
...
A[Q-1]
```

onde $A[j]$
 (para $0 \leq j < Q$)
 é o valor retornado pela $j$-ésima chamada para `query`.