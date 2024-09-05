# Mosaik

Salma berencana untuk mewarnai dinding mosaik tanah liat.
Mosaik tersebut merupakan sebuah *grid* $N \times N$ yang terbuat dari $N^2$ petak persegi $1 \times 1$ yang belum diwarnai.
Baris-baris dari mosaik dinomori dari $0$ hingga $N-1$ dari atas ke bawah, dan kolom-kolom dinomori dari $0$ hingga $N-1$ dari kiri ke kanan.
Petak pada baris $i$ dan kolom $j$ ($0 \leq i < N$, $0 \leq j < N$) dinotasikan dengan $(i, j)$.
Setiap petak harus diwarnai dengan warna putih (dinotasikan dengan $0$) atau hitam (dinotasikan dengan $1$).

Untuk mewarnai mosaiknya, pertama-tama Salma membuat dua *array* $X$ dan $Y$ dengan panjang $N$, yang masing-masing terdiri dari nilai $0$ dan $1$, sedemikian sehingga $X[0] = Y[0]$.
Ia mewarnai petak-petak di baris teratas (baris $0$) menurut *array* $X$, sehingga warna dari petak $(0, j)$ adalah $X[j]$ ($0 \leq j < N$).
Ia mewarnai petak-petak di kolom terkiri (kolom $0$) menurut *array* $Y$, sehingga warna dari petak $(i, 0)$ adalah $Y[i]$ ($0 \leq i < N$).

Kemudian, ia mengulangi langkah-langkah berikut sampai semua petak diwarnai:
* Ia mencari petak mana pun yang *belum diwarnai* sedemikian sehingga tetangga di atasnya (petak $(i-1, j)$) dan tetangga di kirinya (petak $(i, j-1)$) sudah diwarnai.
* Kemudian, ia mewarnai petak $(i, j)$ dengan warna hitam jika kedua tetangganya berwarna putih; jika tidak, ia mewarnai petak $(i, j)$ dengan warna putih.

Bisa ditunjukkan bahwa hasil akhir pewarnaan petak-petak tidak bergantung pada urutan pewarnaan oleh Salma.

Yasmin sangatlah penasaran terhadap warna-warna dari petak-petak mosaik.
Ia menanyakan Salma $Q$ buah pertanyaan, dinomori dari $0$ hingga $Q - 1$.
Pada pertanyaan $k$ ($0 \leq k < Q$), Yasmin memberikan sebuah subpersegi panjang sebagai:
* Baris paling atasnya $T[k]$ dan baris paling bawahnya $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* Kolom paling kirinya $L[k]$ dan kolom paling kanannya $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

Jawaban dari pertanyaannya adalah banyaknya petak hitam di subpersegi panjang ini.
Lebih tepatnya, Salma harus mencari banyaknya petak $(i, j)$ sehingga $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$, dan petak $(i,j)$ berwarna hitam.

Tulislah sebuah program yang menjawab pertanyaan-pertanyaan Yasmin.

## Detail Implementasi

Anda harus mengimplementasikan prosedur berikut.

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: *array* sepanjang $N$ yang secara berturut-turut mendeskripsikan warna-warna petak di baris paling atas dan kolom paling kiri.
* $T$, $B$, $L$, $R$: *array* sepanjang $Q$ yang mendeskripsikan pertanyaan-pertanyaan yang ditanyakan Yasmin.
* Prosedur harus mengembalikan sebuah *array* $C$ sepanjang $Q$, sehingga $C[k]$ memberikan jawaban untuk pertanyaan $k$ ($0 \leq k < Q$).
* Prosedur ini dipanggil tepat sekali untuk setiap kasus uji.

## Batasan

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ dan $Y[i] \in \{0, 1\}$
 untuk setiap $i$ sehingga $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ dan $0 \leq L[k] \leq R[k] < N$
 untuk setiap $k$ sehingga $0 \leq k < Q$

## Subsoal

| Subsoal | Nilai  | Batasan Tambahan |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ (untuk setiap $k$ sehingga $0 \leq k < Q$)
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ (untuk setiap $i$ sehingga $0 \leq i < N$)
| 6       | $22$   | $T[k] = B[k]$ dan $L[k] = R[k]$ (untuk setiap $k$ sehingga $0 \leq k < Q$)
| 7       | $19$   | $T[k] = B[k]$ (untuk setiap $k$ sehingga $0 \leq k < Q$)
| 8       | $22$   | Tidak ada batasan tambahan.

## Contoh

Perhatikan pemanggilan berikut.

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Contoh ini diilustrasikan dengan gambar di bawah.
Gambar di kiri menunjukkan warna-warna dari petak mosaik.
Gambar di tengah dan kanan secara berturut-turut menunjukkan subpersegi panjang yang ditanyakan Yasmin pada pertanyaan pertama dan kedua.

![](example.png "550")

Jawaban-jawaban dari pertayaan (yaitu banyaknya angka satu di persegi panjang yang diarsir) secara berturut-turut adalah $7$ dan $3$.
Oleh karena itu, prosedur harus mengembalikan $[7, 3]$.

## Contoh *Grader*

Format masukan:

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

Format keluaran:

```
C[0]
C[1]
...
C[S-1]
```

Di sini, $S$ adalah panjang dari *array* $C$ yang dikembalikan oleh `mosaic`.
