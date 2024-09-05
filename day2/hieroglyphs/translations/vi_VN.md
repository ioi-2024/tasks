# Hieroglyphs

Một nhóm các nhà nghiên cứu đang nghiên cứu những điểm tương đồng giữa các dãy chữ tượng hình.
Họ biểu diễn mỗi chữ tượng hình bằng một số nguyên không âm.
Để thực hiện nghiên cứu, họ sử dụng các khái niệm sau đây về các dãy.

Với một dãy $A$ cố định,
 dãy $S$ được gọi là **dãy con** của $A$
khi và chỉ khi $S$ có thể nhận được bằng cách
 xoá bỏ một số phần tử (hoặc không xoá phần tử nào) của $A$.

Bảng sau cho thấy một số ví dụ về dãy con của dãy  $A = [3, 2, 1, 2]$.

| Dãy con    | Cách tạo dãy con từ $A$ |
|----------------|---------------------------------|
| [3, 2, 1, 2] | Không phần tử nào bị xoá.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] hoặc [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Mặt khác, $[3, 3]$ hoặc $[1, 3]$ không phải dãy con của $A$.

Xét hai dãy chữ tượng hình, $A$ và $B$.
Một dãy $S$ được gọi là **dãy con chung** của $A$ và $B$
 khi và chỉ khi $S$ là dãy con của cả $A$ và $B$.
Hơn nữa, ta nói dãy  $U$ là **dãy con chung vũ trụ** of $A$ và $B$
 khi và chỉ khi hai điều kiện sau thoả mãn:
* $U$ là dãy con chung của $A$ và $B$.
* Mọi dãy con chung của  $A$ và $B$ đều là dãy con của $U$.

Có thể chứng minh được rằng mọi cặp dãy $A$ và $B$ có nhiều nhất một dãy con chung vũ trụ.

Các nhà nghiên cứu đã tìm thấy hai dãy chữ tượng hình $A$ và $B$.
Dãy $A$ có  $N$ chữ tượng hình
 và dãy $B$ có $M$ chữ tượng hình.
Hãy giúp các nhà nghiên cứu tìm ra dãy con chung vũ trụ của hai dãy $A$ và $B$,
 hoặc xác định dãy như vậy không tồn tại.

## Chi tiết cài đặt

Bạn cần cài đặt hàm sau.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: mảng có độ dài $N$ mô tả dãy đầu tiên.
* $B$: mảng có độ dài $M$ mô tả dãy thứ hai.
* Nếu tồn tại dãy con chung vũ trụ của  $A$ và $B$,
   hàm cần trả về mảng chứa dãy này.
  Ngược lại, hàm cần trả về $[-1]$
   (mảng có độ dài $1$, có đúng một phần tử $-1$).
* Hàm này được gọi đúng một lần cho mỗi trường hợp test.

## Các ràng buộc

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ với mỗi $i$ thoả mãn $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ với mỗi $j$ thoả mãn $0 \leq j < M$

## Các Subtask

| Subtask | Điểm  | Các ràng buộc thêm |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; mỗi dãy $A$ và $B$ chứa $N$ số nguyên **phân biệt** giữa $0$ và $N-1$ (bao gồm cả $0$ và $N-1$)
| 2       | $15$   | Với số nguyên $k$ bất kì, (số lượng phần tử của $A$ bằng  $k$) cộng (số lượng phần tử của $B$ bằng $k$) nhiều nhất là $3$.
| 3       | $10$   | $A[i] \leq 1$ với mỗi $i$ thoả mãn $0 \leq i < N$; $B[j] \leq 1$ với mỗi $j$ thoả mãn $0 \leq j < M$
| 4       | $16$   | Tồn tại dãy con chung vũ trụ của $A$ và $B$.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | Không có ràng buộc nào thêm.

## Các ví dụ

### Ví dụ 1

Xét lời gọi hàm sau.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Trong đó, các dãy con chung của $A$ và $B$ là:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ và $[0, 1, 0, 2]$.

Vì dãy $[0, 1, 0, 2]$ là dãy con chung của $A$ và $B$, và
 mọi dãy con chung của $A$ và $B$ là dãy con của dãy $[0, 1, 0, 2]$,
hàm cần trả về mảng $[0, 1, 0, 2]$.

### Ví dụ 2

Xét lời gọi hàm sau.

```
ucs([0, 0, 2], [1, 1])
```

Trong đó, dãy con chung duy nhất của  $A$ và $B$ là dãy rỗng $[\ ]$.
Vì vậy, hàm cần trả về mảng rỗng  $[\ ]$.

### Ví dụ 3

Xét lời gọi hàm sau.
```
ucs([0, 1, 0], [1, 0, 1])
```

Trong đó, dãy con chung của  $A$ và $B$ là
 $[\ ], [0], [1], [0, 1]$ và $[1, 0]$.
Có thể chứng minh rằng dãy con chung vũ trụ không tồn tại. Vì vậy, hàm cần trả về mảng $[-1]$.

## Trình chấm mẫu

Định dạng dữ liệu vào:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Định dạng kết quả ra:

```
T
R[0]  R[1]  ...  R[T-1]
```

Trong đó, $R$ là mảng trả về bởi hàm `ucs` và $T$ là độ dài của nó.
