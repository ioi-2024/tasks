# Mosaic 
Salma dự định tô màu một bức tranh khảm đất sét trên tường.
Bức tranh là một lưới $N \times N$,
được tạo thành từ $N^2$ ô vuông $1 \times 1$ chưa tô màu.
Các hàng của bức tranh được đánh số từ $0$ đến $N-1$ từ trên xuống dưới,
và các cột được đánh số từ $0$ đến $N-1$ từ trái sang phải.
Ô vuông ở hàng $i$ và cột $j$ ($0 \leq i < N$, $0 \leq j < N$) được kí hiệu là $(i,j)$.
Mỗi ô phải được tô màu
trắng (kí hiệu là $0$) hoặc đen (kí hiệu là $1$).

Để tô màu cho bức tranh, trước tiên Salma chọn hai mảng $X$ và $Y$ có độ dài $N$, chỉ gồm các giá trị $0$ và $1$, thỏa mãn $X[0] = Y[0]$.
Cô ấy tô màu các ô của hàng trên cùng (hàng $0$) theo mảng $X$,
sao cho màu của ô $(0,j)$ là $X[j]$ ($0 \leq j < N$).
Cô ấy cũng tô màu các ô của cột ngoài cùng bên trái (cột $0$) theo mảng $Y$,
sao cho màu của ô $(i,0)$ là $Y[i]$ ($0 \leq i < N$).

Sau đó, cô ấy lặp lại các bước sau cho đến khi tất cả các ô đều được tô màu:
* Cô ấy tìm một ô $(i,j)$ bất kì *chưa tô màu* mà có
ô kề cạnh bên trên (ô $(i-1, j)$) và ô kề cạnh bên trái (ô $(i, j-1)$)
đều *đã được tô màu*.
* Sau đó, cô ấy tô màu ô $(i,j)$ thành màu đen nếu cả hai ô kề này đều có màu trắng;
trái lại, cô ấy tô màu ô $(i, j)$ thành màu trắng.

Có thể thấy rằng màu cuối cùng của các ô không phụ thuộc
vào thứ tự các ô được Salma tô màu.

Yasmin rất tò mò về màu của các ô trong bức tranh.
Cô ấy hỏi Salma $Q$ câu hỏi, được đánh số từ $0$ đến $Q-1$.
Trong câu hỏi $k$ ($0 \leq k < Q$),
Yasmin chỉ định một hình chữ nhật con của bức tranh bởi:
* Hàng trên cùng $T[k]$ và hàng dưới cùng $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* Cột ngoài cùng bên trái $L[k]$ và cột ngoài cùng bên phải $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

Câu trả lời cho câu hỏi là số ô màu đen trong hình chữ nhật con này.
Cụ thể, Salma cần đếm có bao nhiêu ô $(i, j)$ mà $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$,
và màu của ô $(i,j)$ là màu đen.

Hãy viết một chương trình trả lời các câu hỏi của Yasmin.

## Chi tiết cài đặt

Bạn cần cài đặt hàm sau.

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: hai mảng có độ dài $N$ tương ứng mô tả màu của các ô
ở hàng trên cùng và cột ngoài cùng bên trái.
* $T$, $B$, $L$, $R$: các mảng có độ dài $Q$ mô tả các câu hỏi do Yasmin đặt ra.
* Hàm cần trả về một mảng $C$ có độ dài $Q$,
mà $C[k]$ là câu trả lời cho câu hỏi $k$ ($0 \leq k < Q$).
* Hàm này được gọi đúng một lần cho mỗi trường hợp test.

## Các ràng buộc

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ và $Y[i] \in \{0, 1\}$
 với mỗi $i$ thỏa mãn $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ và $0 \leq L[k] \leq R[k] < N$
 với mỗi $k$ thỏa mãn $0 \leq k < Q$

## Các subtask

| Subtask | Điểm  | Các ràng buộc thêm |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ (với mỗi $k$ thỏa mãn $0 \leq k < Q$)
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ (với mỗi $i$ thỏa mãn $0 \leq i < N$)
| 6       | $22$   | $T[k] = B[k]$ and $L[k] = R[k]$ (với mỗi $k$ thỏa mãn $0 \leq k < Q$)
| 7       | $19$   | $T[k] = B[k]$ (với mỗi $k$ thỏa mãn $0 \leq k < Q$)
| 8       | $22$   | Không có ràng buộc nào thêm.

## Ví dụ

Xét lời gọi hàm sau

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Ví dụ này được minh họa trong các hình bên dưới.
Hình bên trái cho biết màu của các ô trong bức tranh.
Hình ở giữa và bên phải tương ứng cho biết hình chữ nhật con trong câu hỏi thứ nhất và thứ hai của Yasmin.

![](example.png "550")

Câu trả lời cho các câu hỏi
(tức là số lượng số 1 trong các hình chữ nhật được tô đậm)
lần lượt là 7 và 3.
Do đó, hàm cần trả về $[7, 3]$.

## Trình chấm mẫu

Định dạng dữ liệu vào:

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

Định dạng kết quả ra:

```
C[0]
C[1]
...
C[S-1]
```

Trong đó, $S$ là độ dài của mảng $C$ được trả về bởi hàm `mosaic`.
