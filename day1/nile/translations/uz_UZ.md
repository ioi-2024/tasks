# Nil

$N$ ta yukni Nil daryosi orqali olib o'tishingiz kerak.
Yuklar $0$ dan $N-1$ gacha raqamlangan.
$i$-yukni ($0 \leq i < N$) og'irligi $W[i]$.

Yukni olib o'tish uchun, siz maxsus kemalardan foydalanasiz.
Har bir kema **ko'pi bilan ikkita** yukni ko'tarishi mumkin.

* Agar kemaga bitta yukni yuklamoqchi bo'lsangiz, yukni og'irligi ixtiyoriy bo'lishi mumkin.
* Agar kemaga ikkita yukni yuklamoqchi bo'lsangiz, kema muvozanatda tura olishiga ishonch komil qilishingiz lozim. Aniqroq aytganda, $p$ va $q$ yukni ($0 \leq p < q < N$) bitta kemada olib o'tish uchun, yuklarni og'irliklarini absolyut farqi ko'pi bilan $D$ bo'lishi lozim, ya'ni $|W[p] - W[q]| \leq D$ bo'lishi shart.

Yukni olib o'tish uchun, bitta kemadagi yuklarni soniga qarab pul to'lashingiz lozim. $i$-yukni ($0 \leq i < N$) olib o'tish narxi:

* $A[i]$, agar yukni o'zini alohida kemaga qo'ysangiz, yoki
* $B[i]$, agar yukni boshqa bir yuk bilan bitta kemaga qo'ysangiz.

Yodda tutingki, ikkinchi holda, kemadagi ikkala yuk uchun alohida pul to'lash lozim. Ya'ni, agar $p$ va $q$ ($0 \leq p < q < N$) yuklarni bir xil kemada olib o'tishga qaror qilsangiz, olib o'tish narxi $B[p] + B[q]$ bo'ladi.

Yukni kemada bir o'zini olib o'tish har doim boshqa yuk bilan birga bitta kemada olib o'tishdan ko'ra qimmatroq bo'ladi. Ya'ni har bir $0 \leq i < N$ bo'lgan $i$ uchun $B[i] < A[i]$ shart qanoatlantiriladi.

Afsuski, daryo bir xil turmaydi va $D$ni qiymatlari o'zgarishi mumkin. 
Sizning vazifangsz $0$dan $Q-1$ gacha raqamlangan Q ta so'rovga javob berishdan iborat. So'rovlar uzungligi $Q$ bo'lgan $E$ massiv orqali ifodalanadi.
$j$ so'rovning ($0 \leq j < Q$) javobi $D$ni qiymati $E[j]$ bo'gandagi umumiy olib o'tish narxining minimum qiymati bo'lishi kerak.

## Kod yozish detallari

Quyidagi funksiyani kodlashingiz lozim.

```
std::vector&lt;long long&gt; calculate_costs(
    std::vector&lt;int&gt; W, std::vector&lt;int&gt; A, 
    std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```

* $W$, $A$, $B$: Yuklarni og'irligi va olib o'tish narxlarini ifodalovchi butun sonlardan tashkil topgan $N$ uzunlikdagi massiv.
* $E$: har bir so'rov uchun $D$ni qiymatini ifodalovchi uzunligi $Q$ bo'lgan butun sonli massiv.
* Bu funksiya $Q$ ta butun sondan iborat $R$ massivni qaytarishi lozim. Bunda $R[j]$ $D$ ning qiymati $E[j]$ (har bir $0 \leq j < Q$ bo'lgan $j$ uchun) bo'lganda minimum umumiy olib o'tish narxini bildiradi. 
* Bu funksiya har bir test uchun aniq bir marta chaqiriladi.

## Chegaralar

* $1 \leq N \leq 100\,000$
* $1 \leq Q \leq 100\,000$
* $1 \leq W[i] \leq 10^{9}$
   $0 \leq i < N$ bo'lgan har bir $i$ uchun
* $1 \leq B[i] < A[i] \leq 10^{9}$
   $0 \leq i < N$ bo'lgan har bir $i$ uchun
* $1 \leq E[j] \leq 10^{9}$
   $0 \leq j < Q$ bo'lgan har bir $j$ uchun

## Qism masalalar

| Qism masala | Ball  | Qo'shimcha cheklovlar |
| :-----: | :----: | ---------------------- |
| 1       | $6$    | $Q \leq 5$; $N \leq 2000$; $W[i] = 1$ har bir $0 \leq i < N$ bo'lgan $i$ uchun
| 2       | $13$   | $Q \leq 5$; $W[i] = i+1$ har bir $0 \leq i < N$ bo'lgan $i$ uchun
| 3       | $17$   | $Q \leq 5$; $A[i] = 2$ and $B[i] = 1$ har bir $0 \leq i < N$ bo'lgan $i$ uchun
| 4       | $11$   | $Q \leq 5$; $N \leq 2000$
| 5       | $20$   | $Q \leq 5$
| 6       | $15$   | $A[i] = 2$ and $B[i] = 1$ har bir $0 \leq i < N$ bo'lgan $i$ uchun
| 7       | $18$   | Qo'shimcha cheklovlarsiz.

## Misol

Quyidagi funksiyani ko'raylik.

```
calculate_costs([15, 12, 2, 10, 21],
                [5, 4, 5, 6, 3],
                [1, 2, 2, 3, 2],
                [5, 9, 1])
```

Bu misolda, $N = 5$ ta yuk va $Q = 3$ ta so'rov bor. 

Birinchi so'rovda, $D = 5$.
$0$- va $3$-yuklarni bitta kemada(chunki $|15-10| \leq 5$) va qolgan yuklarni alohida kemalarda olib o'tish mumkin.
Bu bizga minimum umumiy olib o'tish narxini beradi, u esa $1+4+5+3+3 = 16$.

Ikkinchi so'rovda, $D = 9$.
$0$- va $1$-yuklarni bitta kemada(chunki $|15 - 12| \leq 9$) va $2$- va $3$- yuklarni bitta kemada (chunki $|2 - 10| \leq 9$) olib o'tish mumkin.
Bu bizga minimum umumiy olib o'tish narxini beradi, u esa $1+2+2+3+3 = 11$.

Oxirgi so'rovda, $D = 1$. Har bir yukni alohida kemalarda olib o'tish lozim. 
Bu bizga minimum umumiy olib o'tish narxini beradi, u esa $5+4+5+6+3 = 23$.

Shuning uchun, bu funksiya $[16, 11, 23]$ qaytarishi lozim.

## Namunaviy Grader

Kiritish formati:

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

Chiqarish formati:

```
R[0]
R[1]
...
R[S-1]
```

Bu yerda, $S$ `calculate_costs` qaytargan $R$ massiv uzunligini bildiradi.
