# ヒエログリフ (Hieroglyphs)

ある研究者たちがヒエログリフの列の類似性について研究している．ヒエログリフは非負整数として表される．彼らの研究の中では，列に関する以下の概念が用いられている．

ある列 $A,S$ に対し，$A$ からいくつかの要素（$0$ 個でもよい）を削除することで $S$ が得られるとき，かつそのときに限り，$S$ は $A$ の **部分列** であるという．

以下の表は，列 $A = [3, 2, 1, 2]$ の部分列のいくつかの例を表している．

| 部分列    | $A$ から部分列を得る方法 |
|----------------|---------------------------------|
| [3, 2, 1, 2] | どの要素も削除しない．
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] または [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

一方，$[3, 3]$ や $[1, 3]$ は $A$ の部分列ではない．

$2$ つのヒエログリフの列 $A,B$ を考える．ある列 $S$ に対し，$S$ が $A$ と $B$ 双方の部分列であるとき，かつそのときに限り，$S$ は $A$ と $B$ の **共通部分列** であるという．加えて，ある列 $U$ に対し，以下の $2$ つの条件が共に満たされるとき，かつそのときに限り，$U$ は $A$ と $B$ の **ユニバーサル共通部分列** であるという．

* $U$ は $A$ と $B$ の共通部分列である．
* $A$ と $B$ の共通部分列はいずれも $U$ の部分列である．

どんな $2$ つの列 $A,B$ についても，$A$ と $B$ のユニバーサル共通部分列は高々 $1$ 個しか存在しないことが証明できる．

研究者たちは $2$ つのヒエログリフの列 $A,B$ を発見した．列 $A$ は $N$ 個のヒエログリフからなり，列 $B$ は $M$ 個のヒエログリフからなる．研究者たちを手助けするために，$A$ と $B$ のユニバーサル共通部分列を求めるか，あるいはそのような列が存在しないことを報告せよ．

## 実装の詳細

あなたは以下の関数を実装する必要がある．

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: 長さ $N$ の数列であり，$1$ つ目のヒエログリフの列を表す．
* $B$: 長さ $M$ の数列であり，$2$ つ目のヒエログリフの列を表す．
* この関数は，$A$ と $B$ のユニバーサル共通部分列が存在するならばそれを返し，そうでないならば $[-1]$（ひとつの $-1$ からなる長さ $1$ の数列）を返す必要がある．
* この関数は各テストケースにおいてちょうど $1$ 度だけ呼び出される．

## 制約

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ ($0 \leq i < N$)
* $0 \leq B[j] \leq 200\,000$ ($0 \leq j < M$)

## 小課題

| 小課題 | 得点  | 追加の制約 |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; $A$ も $B$ も $N$ 個の **相異なる** $0$ 以上 $N-1$ 以下の整数からなる．
| 2       | $15$   | どの整数 $k$ についても，$A$ の要素のうち値が $k$ に等しいものの個数と $B$ の要素のうち値が $k$ に等しいものの個数の和は $3$ 個以下である．
| 3       | $10$   | $A[i] \leq 1$ ($0 \leq i < N$); $B[j] \leq 1$ ($0 \leq j < M$)
| 4       | $16$   | $A$ と $B$ のユニバーサル共通部分列が存在する．
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | 追加の制約はない．

## 例

### 例 1

次の呼び出しを考える．

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

この例で，$A$ と $B$ の共通部分列は $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$, $[0, 1, 0, 2]$ の $14$ 個である．

$[0, 1, 0, 2]$ は $A$ と $B$ の共通部分列であり，$A$ と $B$ の共通部分列はいずれも $[0, 1, 0, 2]$ の部分列であるので，この関数は $[0, 1, 0, 2]$ を返さなければならない．

### 例 2

次の呼び出しを考える．

```
ucs([0, 0, 2], [1, 1])
```

この例で，$A$ と $B$ の共通部分列は空の列 $[\ ]$ のみである．したがって，この関数は空の列 $[\ ]$ を返さなければならない．

### 例 3

次の呼び出しを考える．

```
ucs([0, 1, 0], [1, 0, 1])
```

この例で，$A$ と $B$ の共通部分列は $[\ ]$, $[0]$, $[1]$, $[0, 1]$, $[1, 0]$ の $5$ 個である．ここで，$A$ と $B$ のユニバーサル共通部分列は存在しないことが証明できる．したがって，この関数は $[-1]$ を返さなければならない．

## 採点プログラムのサンプル

入力形式：

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

出力形式：

```
T
R[0]  R[1]  ...  R[T-1]
```

ここで，$R$ は `ucs` によって返された数列であり，$T$ はその長さである．