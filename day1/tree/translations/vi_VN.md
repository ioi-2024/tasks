# Tree

Xét một **cây** gồm $N$ **đỉnh**,
các đỉnh được đánh số từ $0$ đến $N-1$.
Đỉnh $0$ được gọi là **gốc**.
Mỗi đỉnh, ngoại trừ gốc, có một đỉnh **cha** duy nhất.
Với mọi $i$, thỏa mãn $1 \leq i < N$,
cha của đỉnh $i$ là đỉnh $P[i]$, trong đó $P[i] < i$.
Giả sử $P[0] = -1$.

Với đỉnh $i$ ($0 \leq i < N$) bất kì,
**cây con** của $i$ là tập hợp các đỉnh sau:
* $i$, và
* bất kì đỉnh nào có đỉnh cha là $i$, và
* bất kì đỉnh nào có đỉnh cha của đỉnh cha là $i$, và
* bất kì đỉnh nào có đỉnh cha của đỉnh cha của đỉnh cha là $i$, và
* v.v.

Hình bên dưới là ví dụ một cây gồm $N = 6$ đỉnh.
Mỗi mũi tên nối một đỉnh với đỉnh cha của nó,
ngoại trừ gốc không có đỉnh cha.
Cây con của đỉnh $2$ chứa các đỉnh $2, 3, 4$ và $5$.
Cây con của đỉnh $0$ chứa tất cả $6$ đỉnh của cây
và cây con của đỉnh $4$ chỉ chứa đỉnh $4$.

![](subtrees.png "150")

Mỗi đỉnh được gán một **trọng số** nguyên không âm.
Kí hiệu trọng số của đỉnh $i$ ($0 \leq i < N$) là $W[i]$.

Nhiệm vụ của bạn là viết một chương trình trả lời $Q$ truy vấn,
mỗi truy vấn được mô tả bởi một cặp số nguyên dương $(L, R)$.
Câu trả lời cho truy vấn sẽ được tính như sau.

Xét việc gán một số nguyên (gọi là **hệ số**) cho mỗi đỉnh của cây.
Một phép gán như vậy được mô tả bằng một dãy $C[0], \ldots, C[N-1]$,
trong đó $C[i]$ ($0 \leq i < N$) là hệ số được gán cho đỉnh $i$.
Ta gọi dãy này là **dãy hệ số**.
Chú ý rằng các phần tử của dãy hệ số có thể là số âm, $0$ hoặc số dương.

Với truy vấn $(L, R)$,
một dãy hệ số được gọi là **hợp lệ**
nếu, đối với mỗi đỉnh $i$ ($0 \leq i < N$),
thỏa mãn điều kiện sau:
tổng hệ số của các đỉnh trong cây con của đỉnh $i$
không nhỏ hơn $L$ và không lớn hơn $R$.

Với một dãy hệ số xác định $C[0], \ldots, C[N-1]$,
**chi phí** của một đỉnh $i$ là $|C[i]| \cdot W[i]$,
trong đó $|C[i]|$ là giá trị tuyệt đối của $C[i]$.
Khi đó, **tổng chi phí** là tổng các chi phí của tất cả các đỉnh.
Nhiệm vụ của bạn là đối với mỗi truy vấn tính
**tổng chi phí nhỏ nhất** có thể đạt được bằng một dãy hệ số hợp lệ nào đó.

Có thể chứng minh được rằng đối với bất kì truy vấn nào, luôn tồn tại ít nhất một dãy hệ số hợp lệ.

## Chi tiết cài đặt

Bạn cần cài đặt hai hàm sau:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$: các mảng số nguyên có độ dài $N$
   cho biết đỉnh cha và trọng số của các đỉnh.
* Hàm này được gọi đúng một lần
khi bắt đầu tương tác giữa trình chấm và chương trình của bạn trong mỗi trường hợp test.

```
long long query(int L, int R)
```
* $L$, $R$: hai số nguyên mô tả một truy vấn.
* Hàm này được gọi $Q$ lần sau khi gọi `init` trong mỗi trường hợp test.
* Hàm này sẽ trả về kết quả cho truy vấn đã cho.


## Các ràng buộc

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ với mỗi $i$ thỏa mãn $1 \leq i < N$
* $0 \leq W[i] \leq 1\,000\,000$ với mỗi $i$ thỏa mãn $0 \leq i < N$
* $1 \leq L \leq R \leq 1\,000\,000$ với mỗi truy vấn

## Các Subtask

| Subtask | Điểm  | Các ràng buộc thêm |
| :-----: | :----: | ---------------------- |
|   1     |  $10$  | $Q \leq 10$; $W[P[i]] \leq W[i]$ với mỗi $i$ thỏa mãn $1 \leq i < N$
|   2     |  $13$  | $Q \leq 10$; $N \leq 2\,000$
|   3     |  $18$  | $Q \leq 10$; $N \leq 60\,000$
|   4     |  $7$   | $W[i] = 1$ với mỗi $i$ thỏa mãn $0 \leq i < N$
|   5     |  $11$  | $W[i] \leq 1$ với mỗi $i$ thỏa mãn $0 \leq i < N$
|   6     |  $22$  | $L = 1$
|   7     |  $19$  | Không có ràng buộc nào thêm.



## Các ví dụ

Xét các lời gọi hàm sau:

```
init([-1, 0, 0], [1, 1, 1])
```

Cây bao gồm $3$ đỉnh, gốc và $2$ con của nó.
Mọi đỉnh đều có trọng số $1$ .

```
query(1, 1)
```

Trong truy vấn này $L = R = 1$ ,
 điều này có nghĩa là tổng các hệ số trong mỗi cây con phải bằng $1$.
Xét dãy hệ số $[-1, 1, 1]$ .
Cây và các hệ số tương ứng (trong hình chữ nhật tô đậm) được minh họa bên dưới.

![](ex1.png "150")

Đối với mỗi đỉnh $i$ ($0 \leq i < 3$), tổng các hệ số của tất cả các đỉnh
trong cây con của $i$ bằng $1$.
Do đó, dãy hệ số này là hợp lệ.
Tổng chi phí được tính như sau:


| Đỉnh | Trọng số | Hệ số | Chi phí                      |
| :----: | :----: | :---------: | :-----------------------: |
|   0    |   1    |     -1      | $\mid -1 \mid \cdot 1 = 1$
|   1    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$
|   2    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$

Do đó tổng chi phí là $3$.
Đây là dãy hệ số hợp lệ duy nhất,
do đó lệnh gọi này sẽ trả về $3$.

```
query(1, 2)
```
 
Tổng chi phí nhỏ nhất cho truy vấn này là $2$,
và đạt được khi dãy hệ số là $[0, 1, 1]$.

## Trình chấm mẫu

Định dạng dữ liệu vào:

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

trong đó $L[j]$ và $R[j]$
(đối với $0 \leq j < Q$)
là các tham số đầu vào trong lệnh gọi hàm `query` thứ $j$.
Chú ý rằng dòng thứ hai của dữ liệu vào chỉ chứa **$N-1$ số nguyên**,
vì trình chấm mẫu không đọc giá trị của $P[0]$.

Định dạng kết quả ra:
```
A[0]
A[1]
...
A[Q-1]
```
 
trong đó $A[j]$
(với $0 \leq j < Q$)
là giá trị trả về khi gọi hàm `query` thứ $j$.
