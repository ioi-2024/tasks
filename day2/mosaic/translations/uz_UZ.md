# Mozaika

Salma devordagi mozaikani bo'yamoqchi.
Mozaika $N \times N$ doskadan iborat bo'lib, $N^2$ ta dastlab bo'yalmagan $1 \times 1$ kvadratlardan iborat. Mozaikani qatorlari tepadan pastga $0$ dan $N-1$ gacha raqamlangan va ustunlari esa chapdan o'ngga $0$ dan $N-1$ gacha raqamlangan.
$i$-qator va $j$-ustundagi ($0 \leq i < N$, $0 \leq j < N$)  kvadrat $(i,j)$ orqali ifodalanadi. Har bir kvadrat oq ($0$ soni) yoki qora ($1$ soni) rangda bo'yalishi mumkin.

Mozaikani bo'yash uchun, Salma dastlab uzunligi $N$ bo'lgan $X$ va $Y$ massivlarni tanlaydi, bunda massivlardagi qiymatlar $0$ yoki $1$ dan iborat va  $X[0] = Y[0]$ bo'ladi.
U eng yuqori qatordagi($0$-qator) kvadratlarni $X$ massivga ko'ra bo'yaydi, bunda $(0,j)$ kvadratning rangi $X[j]$ ($0 \leq j < N$) bo'ladi.
Shuningdek u eng chapgi ustundagi($0$-ustun) kvadratlarni $Y$ massivga ko'ra bo'yaydi, bunda $(i,0)$ kvadratning rangi $Y[i]$ ($0 \leq i < N$) bo'ladi.

So'ng u barcha kvadratlar bo'yalmaguncha quyidagi amalni takrorlaydi:
* Yuqoridagi qo'shinisi ($(i-1, j)$ kvadrat) va chapgi qo'shnisi ($(i, j-1)$ kvadrat) *allaqachon bo'yalgan* 
$(i,j)$ *bo'yalmagan* kvadratni topadi.
* So'ng agar shu ikkala qo'shnisini rangi oq bo'lsa, $(i,j)$ kvadratni qora rangga bo'yaydi, aks holda esa $(i,j)$ni oq rangda bo'yaydi.

Kvadratlarning jarayon so'nggidagi rangi Salmani kvadratlarni bo'yash tartibiga bog'liq emasligini isbotlash mumkin.

Yasmin mozaika kvadratlarining ranglariga qiziqmoqda. 
U Salmadan $0$ dan $Q-1$ gacha raqamlangan $Q$ ta savol so'raydi. 
$k$-savolda ($0 \leq k < Q$), Yasmin to'g'ri to'rtburchakni quyidagi qiymatlar orqali ifodalaydi:
* Eng yuqori qator $T[k]$ va eng quyi qator $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* Eng chap ustun $L[k]$ va eng o'ng ustun $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

Savolning javobi shu berilgan qism to'g'ri to'rtburchakdagi qora kvadratlar soniga teng.
Aniqrog'i, Salma $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$ bo'lgan va $(i,j)$ qora bo'lgan kvadratlar sonini topishi lozim.

Yasminning savollariga javob beradigan dastur tuzing.

## Kod yozish detallari

Quyidagi funksiyani kodlashingiz lozim:

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: eng yuqori qator va eng chap ustundagi kvadratlarning rangini ifodalovchi uzunligi $N$ bo'lgan massivlar.
* $T$, $B$, $L$, $R$: Yasminning savollarini ifodalaydigan uzunligi $Q$ bo'lgan massivlar.
* Funksiya uzunligi $Q$ bo'lgan $C$ massivni qaytarishi lozim, bunda $C[k]$ ning qiymati $k$ ($0 \leq k < Q$) savolning javobi bo'lishi lozim.
* Bu funksiya har bir test uchun faqat bir marta chaqiriladi.

## Chegaralar

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ va $Y[i] \in \{0, 1\}$
har bir $0 \leq i < N$ bo'lgan $i$ uchun
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ va $0 \leq L[k] \leq R[k] < N$
har bir $0 \leq k < Q$ bo'lgan $k$ uchun

## Qism masalalar

| Qism masala | Ball  | Qo'shimcha cheklovlar |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ (har bir $0 \leq k < Q$ bo'lgan $k$ uchun)
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ (har bir $0 \leq i < N$ bo'lgan $i$ uchun )
| 6       | $22$   | $T[k] = B[k]$ va $L[k] = R[k]$ (har bir $0 \leq k < Q$ bo'lgan $k$ uchun)
| 7       | $19$   | $T[k] = B[k]$ (har bir $0 \leq k < Q$ bo'lgan $k$ uchun)
| 8       | $22$   | Qo'shimcha cheklovlar yo'q.

## Misol

Quyidagi funksiya chaqiruvini ko'raylik

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Bu misol quyidagi rasmlarda ifodalangan.
Chapdagi rasm mozaikadagi kvadratlar ranglarini ko'rsatadi.
O'rtadagi va o'ngdagi rasmlar Yasmin birinchi va ikkinchi so'rovlarida so'ragan qism to'g'ri to'rtburchaklarni ko'rsatadi.

![](example.png "550")

So'rovlarga javoblar(ya'ni kulrang kvadratlardagi birlar soni) mos ravishda $7$ va $3$. Shuning uchun funksiya $[7, 3]$ qaytaradi.

## Namunaviy Grader

Kiritish formati:

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

Chiqarish formati:

```
C[0]
C[1]
...
C[S-1]
```

Bunda, $S$ `mosaic` qaytargan $C$ massivni uzunligini bildiradi.
