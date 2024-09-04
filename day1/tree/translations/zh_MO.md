# 樹

考慮一棵由 $N$ 個**頂點**組成的**樹**，頂點編號從 $0$ 到 $N-1$ ，其中頂點 $0$ 被稱為**根**。對於除了根以外的所有頂點，都只會有一個**父親**。對每個 $i$ ， $1 \leq i < N$ ，頂點 $i$ 的父節點會是頂點 $P[i]$ ，其中 $P[i] < i$ 。我們假設$P[0] = -1$ 。

對任何一個頂點 $i$ ( $0 \leq i < N$ )，$i$ 的 **子樹** 是以下頂點的集合：
 * $i$ ，以及
 * 父親為 $i$ 的任何頂點，以及
 * 父親的父親為 $i$ 的任何頂點，以及
 * 父親的父親的父親為 $i$ 的任何頂點，以及
 * 如此類推。

下圖顯示了由 $N = 6$ 個頂點組成的樣例樹。每個頂點都透過一個箭頭連接到其父親，
根頂點除外，因為它並沒有父親。頂點 $2$ 的子樹包含頂點 $2, 3, 4$ 和 $5$ 。
頂點 $0$ 的子樹包含樹的所有 $6$ 個頂點，而頂點 $4$ 的子樹僅包含頂點 $4$ 。

![](subtrees.png "150")

每個頂點被分配了一個非負的**權重**。
我們用 $W[i]$ 表示頂點 $i$ ( $0 \leq i < N$ ) 的權重。

你的任務是編寫一個程式來回答 $Q$ 個查詢，每個查詢由一對整數 $(L, R)$ 指定。
對於每一個查詢，其答案應用如下方法計算：

考慮為每個頂點分配一個整數，稱為該頂點的**系數**。
這樣的分配由一個序列 $C[0], \ldots, C[N-1]$ 所描述，
 其中$C[i]$ ( $0 \leq i < N$ ) 是分配給頂點 $i$ 的系數。
讓我們稱這個序列為**系數序列**。
請注意，系數序列內的元素可以是負數、  $0$ 或正數。

對於查詢 $(L, R)$ ，一個系數序列被稱為**有效**的，當且僅當對於每個頂點 $i$ ( $0 \leq i < N$ )
 都有以下條件成立：
 頂點 $i$ 的子樹中，所有頂點的系數總和不小於 $L$ 且不大於 $R$ 。

對於給定的系數序列 $C[0], \ldots, C[N-1]$ ，頂點 $i$ 的 **成本** 是 $|C[i]| \cdot W[i]$  , 其中 $|C[i]|$ 表示 $C[i]$ 的絕對值。
最後，**總成本**是所有頂點的成本的總和。
您的任務是對於每個查詢，去計算透過某些有效系數序列可以達到的**最小總成本**。

## 實現細節

您應該實現以下兩個子程式：

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$ ：長度為 $N$ 的整數數組，指定每個頂點的父親及權重。
* 該子程式僅被調用一次，在每個測試案例中，評分程式和您的程式之間的互動開始時調用。

```
long long query(int L, int R)
```
* $L$ , $R$ ：兩個整數，用於描述一個查詢。
* 在每個測試案例中，調用 `init` 之後，此子程序會被調用 $Q$ 次。
* 此子程序應傳回給定查詢的答案。


## 約束條件

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ ，對每個 $i$，$1 \leq i < N$
* $0 \leq W[i] \leq 1\,000\,000$ ，對每個 $i$ ，$0 \leq i < N$
* 在每個查詢中，有 $1 \leq L \leq R \leq 1\,000\,000$

## 子任務

|子任務|分數 |附加限制 |
| :-----: | :----: | ---------------------- |
| 1 | $10$ | $Q \leq 10$ ; $W[P[i]] \leq W[i]$ 對於每個 $i$ ，$1 \leq i < N$
| 2 | $13$ | $Q \leq 10$ ; $N \leq 2\,000$
| 3 | $18$ | $Q \leq 10$ ; $N \leq 60\,000$
| 4 | $7$ |對每個 $i$， $W[i] = 1$，$0 \leq i < N$
| 5 | $11$ | $W[i] \leq 1$，對於每個 $i$ ，$1 \leq i < N$
| 6 | $22$ | $L = 1$
| 7 | $19$ |沒有額外的限制。



## 範例

考慮以下調用：

```
init([-1, 0, 0], [1, 1, 1])
```
該樹由 $3$ 個頂點：根以及其 $2$ 個子節點組成。
所有頂點的權重為 $1$ 。

```
query(1, 1)
```

在此查詢中， $L = R = 1$ ，
 這意味著每個子樹中的系數總和必須等於$1$ 。
考慮系數序列$[-1, 1, 1]$ 。
樹和相應的系數（陰影矩形）如下所示。

![](ex1.png "150")

對於每個頂點 $i$ ( $0 \leq i < 3$ )，在 $i$ 的子樹中所有頂點的系數總和等於 $1$ 。 
因此，此系數序列是有效的。
總成本計算如下：


|頂點|重量 |系數|成本|
| :----: | :----: | :---------: | :------------------------: |
| 0 | 1 | -1 | $\mid -1 \mid \cdot 1 = 1$
| 1 | 1 | 1 | $\mid 1 \mid \cdot 1 = 1$
| 2 | 1 | 1 | $\mid 1 \mid \cdot 1 = 1$

因此總成本為 $3$ 。
這是唯一有效的系數序列，
 因此這個調用應該回傳 $3$ 。

```
query(1, 2)
```
此查詢的最低總成本為 $2$ ，當系數序列為 $[0, 1, 1]$ 時達到。

## 樣例評分程式

輸入格式：

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

其中 $L[j]$ 和 $R[j]$ 
 （對於 $0 \leq j < Q$ ）
 是 `query` 的第 $j$ 次調用中的輸入參數。
請注意，輸入的第二行**僅包含 $N-1$ 個整數**，
 因為範例評分器不會讀取 $P[0]$ 的值。

輸出格式：
```
A[0]
A[1]
...
A[Q-1]
```

其中 $A[j]$ 
 （對於$0 \leq j < Q$ ）
 是第 $j$ 次調用 `query` 傳回的值。