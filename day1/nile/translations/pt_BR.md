# Nilo

Você quer transportar $N$ artefatos através do rio Nilo. 
Os artefatos são numerados de $0$ a $N-1$ .
O peso do artefato $i$ ( $0 \leq i < N$ ) é $W[i]$ .

Para transportar os artefatos, você usa barcos especializados.
Cada barco pode transportar **no máximo dois** artefatos.

* Se você decidir colocar um único artefato em um barco, o peso do artefato pode ser arbitrário.
* Se você quiser colocar dois artefatos no mesmo barco, você precisa ter certeza de que o barco esteja equilibrado.
Especificamente, você pode enviar os
 artefatos $p$ e $q$ ( $0 \leq p < q < N$ ) no mesmo barco
 somente se a diferença absoluta (módulo) entre seus pesos for no máximo $D$ ,
 isto é $|W[p] - W[q]| \leq D$ .

Para transportar um artefato, você tem que pagar um custo
 que depende do número de artefatos transportados no mesmo barco.
O custo de transporte do artefato $i$ ( $0 \leq i < N$ ) é:

* $A[i]$ , se você colocar o artefato em seu próprio barco, ou
* $B[i]$ , se você colocá-lo em um barco junto com algum outro artefato.

Observe que, no último caso, você terá que pagar pelos dois artefatos no barco.
Especificamente, se você decidir enviar os
 artefatos $p$ e $q$ ( $0 \leq p < q < N$ ) no mesmo barco,
 você precisa pagar $B[p] + B[q]$ .

Enviar um artefato sozinho em um barco é sempre mais caro 
do que enviá-lo com algum outro artefato compartilhando o barco com ele,
então $B[i] < A[i]$ para todo $i$ tal que $0 \leq i < N$ .

Infelizmente, o rio é muito imprevisível e o valor de $D$ muda com frequência.
Sua tarefa é responder $Q$ perguntas numeradas de $0$ a $Q-1$ .
As perguntas são descritas por um vetor $E$ de tamanho $Q$ .
A resposta da pergunta $j$ ( $0 \leq j < Q$ ) é
 o custo total mínimo do transporte de todos os $N$ artefatos,
 quando o valor de $D$ é igual a $E[j]$ .

## Detalhes de implementação

Você deve implementar o seguinte procedimento.

```
std::vector&lt;long long&gt; calculate_costs(
 std::vector&lt;int&gt; W, std::vector&lt;int&gt; A,
 std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```

* $W$ , $A$ , $B$ : vetores de inteiros de tamanho $N$ , descrevendo os pesos dos artefatos e os custos de transportá-los.
* $E$ : um vetor de inteiros de tamanho $Q$ descrevendo o valor de $D$ para cada pergunta.
* Este procedimento deve retornar um vetor $R$ de $Q$ inteiros
   contendo o custo total mínimo de transporte dos artefatos,
   onde $R[j]$ fornece o custo quando o valor de $D$ é $E[j]$ (para cada $j$
   tal que $0 \leq j < Q$ ).
* Este procedimento é chamado exatamente uma vez para cada caso de teste.

## Restrições

* $1 \leq N \leq 100\,000$
* $1 \leq Q \leq 100\,000$
* $1 \leq W[i] \leq 10^{9}$
   para cada $i$ tal que $0 \leq i < N$
* $1 \leq B[i] < A[i] \leq 10^{9}$
   para cada $i$ tal que $0 \leq i < N$
* $1 \leq E[j] \leq 10^{9}$
   para cada $j$ tal que $0 \leq j < Q$

## Subtarefas

| Subtarefa | Pontuação | Restrições adicionais |
| :-----: | :----: | ---------------------- |
| 1 | $6$ | $Q \leq 5$ ; $N \leq 2000$ ; $W[i] = 1$ para cada $i$ tal que $0 \leq i < N$
| 2 | $13$ | $Q \leq 5$ ; $W[i] = i+1$ para cada $i$ tal que $0 \leq i < N$
| 3 | $17$ | $Q \leq 5$ ; $A[i] = 2$ e $B[i] = 1$ para cada $i$ tal que $0 \leq i < N$
| 4 | $11$ | $Q \leq 5$ ; $N \leq 2000$
| 5 | $20$ | $Q \leq 5$
| 6 | $15$ | $A[i] = 2$ e $B[i] = 1$ para cada $i$ tal que $0 \leq i < N$
| 7 | $18$ | Sem restrições adicionais.

## Exemplo

Considere a seguinte chamada.

```
calculate_costs([15, 12, 2, 10, 21],
 [5, 4, 5, 6, 3],
 [1, 2, 2, 3, 2],
 [5, 9, 1])
```

Neste exemplo temos $N = 5$ artefatos e $Q = 3$ perguntas.

Na primeira pergunta, $D = 5$ .
Você pode enviar os artefatos $0$ e $3$ em um barco (já que $|15 - 10| \leq 5$ ) e os artefatos restantes em barcos separados.
Isso produz o custo mínimo de transporte de todos os artefatos, que é $1+4+5+3+3 = 16$ .

Na segunda pergunta, $D = 9$ .
Você pode enviar os artefatos $0$ e $1$ em um barco (já que $|15 - 12| \leq 9$ ) e enviar os artefatos $2$ e $3$ em um barco (já que $|2 - 10| \leq 9$ ).
O artefato restante pode ser enviado em um barco separado.
Isso produz o custo mínimo de transporte de todos os artefatos, que é $1+2+2+3+3 = 11$ .

Na pergunta final, $D = 1$ . Você precisa enviar cada artefato em seu próprio barco.
Isso produz o custo mínimo de transporte de todos os artefatos, que é $5+4+5+6+3 = 23$ .

Portanto, este procedimento deve retornar $[16, 11, 23]$ .


## Corretor Exemplo

Formato de entrada:

```
N
W[0] A[0] B[0]
W[1] A[1] B[1]
...
W[N-1] A[N-1] B[N-1]
Q
E[0]
E[1]
...
E[Q-1]
```

Formato de saída:

```
R[0]
R[1]
...
R[S-1]
```

Aqui, $S$ é o tamanho do vetor $R$ retornado por `calculate_costs` .