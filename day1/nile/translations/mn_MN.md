# Нил мөрөн

Та  $N$ олдворыг Нил мөрнөөр тээвэрлэхийг хүсэж байгаа. 
Олдворуудыг $0$-ээс $N-1$ хүртэл дугаарласан.
$i$ ($0 \leq i < N$) дүгээр олдворын жин $W[i]$ байдаг. 

Олдворыг тээвэрлэхийн тулд тусгай зориулалтын завь ашиглана.
Ямар ч завь **хамгийн ихдээ хоёр** олдворыг авч явж чадна.
* Хэрэв зариар нэг олдворыг авч явах бол уг олдворын жин дурын байж болно. 
* Хэрэв хоёр олдворыг нэг завин дээр авч явах бол завийг тэнцвэртэй байлгах ёстой. 
Тодруулбал, та $p$ ба $q$ ($0 \leq p < q < N$) хоёр олдворын жингийн үнэмлэхүй (absolute) зөрүү $D$ ихгүй буюу $|W[p] - W[q]| \leq D$ бол эдгээр олдворыг нэг завин дээр авч явах боломжтой байдаг.  

Та олдворыг тээвэрлэхдээ нэг завиар авч явах олдворын тооноос хамаарч төлбөр төлдөг.
$i$ ($0 \leq i < N$) дүгээр олдворыг тээвэрлэх төлбөр нь:
* Хэрэв олдворыг дангаар тээвэрлэх бол зардал нь $A[i]$ эвсэл
* Хэрэв өөр олдвортой хамт тээвэрлэх бол зардал нь $B[i]$ байдаг.  

Дээрх нөхцөлийн хоёрдугаар тохиолдолд та хоёр олдвор тус бүрд төлбөр төлөх ёстойг анхаарна уу. Тодруулбал, $p$ ба $q$ ($0 \leq p < q < N$) олдворуудыг нэг завиар тээвэрлэх бол $B[p] + B[q]$ гэсэн төлбөр төлнө.

Олдворыг зариар дангаар тээвэрлэх нь өөр олдвортой хамт тээвэрлэхээс ямагт үнэтэй байдаг тул бүх $i$ ( $0 \leq i < N$)-ийн хувьд ямагт $B[i] < A[i]$ байх болно. 

Харамсалтай нь мөрөн маш тогтворгүй байгаагаас гадна $D$-ийн утга байнгын өөрчлөгдөж байдаг. 
Таны даалгавар бол $0$-ээс $Q-1$ хүртэл дугаарлагдсан $Q$ асуултад хариулах явдал юм. Асуултуудыг $Q$ урттай $E$ массиваар дүрсэлнэ. $j$ ($0 \leq j < Q$) дүгээр асуултын хариулт нь $D$-ийн утга нь $E[j]$-тэй тэнцүү байх үед бүх $N$ олдворуудыг тээвэрлэх хамгийн бага нийт зардал юм. 

## Хэрэгжүүлэлтийн мэдээлэл

Та дараах функцийг хэрэгжүүлэх ёстой.

```
std::vector&lt;long long&gt; calculate_costs(
    std::vector&lt;int&gt; W, std::vector&lt;int&gt; A, 
    std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```

* $W$, $A$, $B$: $N$ урттай бүхэл тоон массивууд ба харгалзан олдворуудын жин, тэдгээрийг тээвэрлэх зардалууд байна.
* $E$: $Q$ урттай бүхэл тоон массив бөгөөд асуулт бүрийн $D$ утгыг тодорхойлно.
* Энэхүү функц нь $Q$ бүхэл тоон утга бүхий $R$ массивыг буцаах ба энэ нь олдворуудыг тээвэрлэх хамгийн бага нийт зардал бөгөөд уг массивын $R[j]$ утга нь $D$-ийн утга $E[j]$ ($0 \leq j < Q$ байх $j$ бүрийн хувьд) байх зардлыг тодорхойлно. 
* Уг функцийг тестийн тохиолдол бүрд яг нэг удаа дуудна.

## Хязгаарлалт

* $1 \leq N \leq 100\,000$
* $1 \leq Q \leq 100\,000$
* $1 \leq W[i] \leq 10^{9}$,
   $0 \leq i < N$ байх $i$ бүрийн хувьд 
* $1 \leq B[i] < A[i] \leq 10^{9}$,
   $0 \leq i < N$ байх $i$ бүрийн хувьд 
* $1 \leq E[j] \leq 10^{9}$,
   $0 \leq j < Q$ байх $j$ бүрийн хувьд

## Дэд бодлого

| Дэд бодлого | Оноо  | Нэмэлт хязгаарлалт |
| :-----: | :----: | ---------------------- |
| 1       | $6$    | $Q \leq 5$; $N \leq 2000$; $W[i] = 1$, $0 \leq i < N$ байх $i$ бүрийн хувьд
| 2       | $13$   | $Q \leq 5$; $W[i] = i+1$, $0 \leq i < N$ байх $i$ бүрийн хувьд
| 3       | $17$   | $Q \leq 5$; $A[i] = 2$ and $B[i] = 1$,  $0 \leq i < N$ байх $i$ бүрийн хувьд
| 4       | $11$   | $Q \leq 5$; $N \leq 2000$
| 5       | $20$   | $Q \leq 5$
| 6       | $15$   | $A[i] = 2$ and $B[i] = 1$, $0 \leq i < N$ байх $i$ бүрийн хувьд
| 7       | $18$   | Нэмэлт хязгаарлалт байхгүй.

## Жишээ

Дараах дуудалтыг хийсэн байг.

```
calculate_costs([15, 12, 2, 10, 21],
                [5, 4, 5, 6, 3],
                [1, 2, 2, 3, 2],
                [5, 9, 1])
```

Энэ жишээний хувьд бидэнд $N = 5$ олдвор, $Q = 3$ асуулт байна.
Эхний эсуултад $D = 5$. 
Та $0$ ба $3$ олдворыг нэг завиар ($|15 - 10| \leq 5$ тул) авч явж болох ба бусад олдворыг нэг нэгээр нь тээвэрлэнэ. Иймээс бүх олдворыг тээвэрлэх хамгийн зардал нь $1+4+5+3+3 = 16$ болно.

Хоёрдахь асуултад $D = 9$.
Та $0$ ба $1$ олдворыг нэг завиар ($|15 - 12| \leq 9$ тул), мөн $2$ ба $3$ олдворыг нэг завиар ($|2 - 10| \leq 9$ тул) тээвэрлэж болно.
Үлдсэн олдворыг ганцаар нь тээвэрлэнэ. Иймээс энэ тохиолдолд бүх олдворыг тээвэрлэх хамгийн зардал нь $1+2+2+3+3 = 11$ болно.

Сүүлийн асуултад $D = 1$. Та бүх олдворыг нэг нэгээр нь тээвэрлэх ёстой.
Иймээс энэ тохиолдолд бүх олдворыг тээвэрлэх хамгийн зардал нь $5+4+5+6+3 = 23$ байна.

Иймээс уг функц $[16, 11, 23]$ гэсэн утгыг буцаах болно.


## Жишээ грэйдэр:

Оролтын формат:

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

Гаралтын формат:

```
R[0]
R[1]
...
R[S-1]
```

Энэхүү $S$ урттай $R$ массивыг `calculate_costs` функц буцаана.
