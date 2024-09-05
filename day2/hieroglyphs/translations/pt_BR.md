# Hieróglifos

Uma equipe de pesquisadores está estudando as semelhanças entre sequências de hieróglifos.
Eles representam cada hieróglifo com um número inteiro não negativo.
Para realizar seu estudo,
 eles usam os seguintes conceitos sobre sequências.

Para uma sequência fixa $A$,
 uma sequência $S$ é chamada de **subsequência** de $A$
 se e somente se $S$ puder ser obtida
 removendo alguns elementos (possivelmente nenhum) de $A$.

A tabela abaixo mostra alguns exemplos de subsequências de uma sequência $A = [3, 2, 1, 2]$.

| Subsequência | Como pode ser obtida de $A$ |
|----------------|---------------------------------|
| [3, 2, 1, 2] | Nenhum elemento é removido.
| [2, 1, 2] | [<s>3</s>, 2, 1, 2]
| [3, 2, 2] | [3, 2, <s>1</s>, 2]
| [3, 2] | [3, <s>2</s>, <s>1</s>, 2] ou [3, 2, <s>1</s>, <s>2</s>]
| [3] | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ] | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Por outro lado, $[3, 3]$ ou $[1, 3]$ não são subsequências de $A$.

Considere duas sequências de hieróglifos, $A$ e $B$.
Uma sequência $S$ é chamada de **subsequência comum** de $A$ e de $B$
 se e somente se $S$ for uma subsequência de $A$ e $B$.
Além disso, dizemos que uma sequência $U$ é uma **subsequência comum universal** de $A$ e $B$
 se e somente se as duas condições seguintes forem atendidas:
* $U$ é uma subsequência comum de $A$ e $B$.
* Toda subsequência comum de $A$ e $B$ também é uma subsequência de $U$.

Pode-se demonstrar que quaisquer duas sequências $A$ e $B$
 têm no máximo uma subsequência comum universal.

Os pesquisadores encontraram duas sequências de hieróglifos $A$ e $B$.
A sequência $A$ consiste em $N$ hieróglifos
 e a sequência $B$ consiste em $M$ hieróglifos.
Ajude os pesquisadores a calcular
 uma subsequência comum universal das sequências $A$ e $B$,
 ou determinar que tal sequência não existe.

## Detalhes de implementação

Você deve implementar o seguinte procedimento.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: vetor de tamanho $N$ descrevendo a primeira sequência.
* $B$: vetor de tamanho $M$ descrevendo a segunda sequência.
* Se existe uma subsequência comum universal de $A$ e $B$,
   o procedimento deve retornar um vetor contendo esta sequência.
  Caso contrário, o procedimento deve retornar $[-1]$
   (um vetor de tamanho $1$, cujo único elemento é $-1$).
* Este procedimento é chamado exatamente uma vez para cada caso de teste.

## Restrições

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ para cada $i$ tal que $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ para cada $j$ tal que $0 \leq j < M$

## Subtarefas

| Subtarefa | Pontuação | Restrições adicionais |
| :-----: | :----: | ---------------------- |
| 1 | $3$ | $N = M$; ambos $A$ e $B$ consistem em $N$ inteiros **distintos** entre $0$ e $N-1$ (inclusive)
| 2 | $15$ | Para qualquer inteiro $k$, (o número de elementos de $A$ igual a $k$) + (o número de elementos de $B$ igual a $k$) é no máximo $3$.
| 3 | $10$ | $A[i] \leq 1$ para cada $i$ tal que $0 \leq i < N$; $B[j] \leq 1$ para cada $j$ tal que $0 \leq j < M$
| 4 | $16$ | Existe uma subsequência comum universal de $A$ e $B$.
| 5 | $14$ | $N \leq 3000$ ; $M \leq 3000$
| 6 | $42$ | Sem restrições adicionais.

## Exemplos

### Exemplo 1

Considere a seguinte chamada.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Aqui, as subsequências comuns de $A$ e $B$ são as seguintes:
 $[\ ]$, $[0]$, $[1]$, $[2]$ $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 0]$, $[0, 0, 2]$, $[1, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ e $[0, 1, 0, 2]$.

Como $[0, 1, 0, 2]$ é uma subsequência comum de $A$ e $B$, e
 todas as subsequências comuns de $A$ e $B$ são subsequências de $[0, 1, 0, 2]$,
 o procedimento deve retornar $[0, 1, 0, 2]$.

### Exemplo 2

Considere a seguinte chamada.

```
ucs([0, 0, 2], [1, 1])
```

Aqui, a única subsequência comum de $A$ e $B$ é a sequência vazia $[\ ]$.
Segue-se que o procedimento deve retornar um vetor vazio $[\ ]$.

### Exemplo 3

Considere a seguinte chamada.
```
ucs([0, 1, 0], [1, 0, 1])
```

Aqui, as subsequências comuns de $A$ e $B$ são
 $[\ ], [0], [1], [0, 1]$ e $[1, 0]$.
Pode-se demonstrar que uma subsequência comum universal não existe.
Portanto, o procedimento deve retornar $[-1]$.

## Corretor Exemplo

Formato de entrada:

```
N  M
A[0] A[1] ... A[N-1]
B[0] B[1] ... B[M-1]
```

Formato de saída:

```
T
R[0] R[1] ... R[T-1]
```

Aqui, $R$ é o vetor retornado por `ucs` e $T$ é seu tamanho.