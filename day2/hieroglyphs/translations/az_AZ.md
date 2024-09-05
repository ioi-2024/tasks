# Heroqliflər

Tədqiqatçılar qrupu heroqlif ardıcıllıqları arasındakı oxşarlıqları öyrənir.
Onlar hər bir heroqlifi mənfi olmayan tam ədədlə təmsil edirlər.
Tədqiqatlarını yerinə yetirmək üçün ardıcıllıqla bağlı aşağıdakı anlayışlardan istifadə edirlər.

Sabit $A$ ardıcıllığından bəzi elementləri (bəlkə də heç birini) silməklə əldə edilə bilən $S$ ardıcıllığı $A$-nın **alt ardıcıllığı** adlanır.

Aşağıdakı cədvəl $A = [3, 2, 1, 2]$ ardıcıllığının alt ardıcıllıqlarının bəzi nümunələrini göstərir.

| Alt Ardıcıllıq    | $A$-dan necə əldə edilə bilər |
|----------------|---------------------------------|
| [3, 2, 1, 2] | Heç bir element silinmir.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] or [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Digər tərəfdən, $[3, 3]$ və ya $[1, 3]$ $A$-nın alt ardıcıllığı deyil.

$A$ və $B$ heroqlif ardıcıllıqlarını nəzərdən keçirin.
$S$ ardıcıllığı yalnız və yalnız həm $A$ həm də $B$-nin alt ardıcıllığı olarsa, $S$ $A$ və $B$-nin **ortaq alt ardıcıllığı** adlanır.
Bundan əlavə, biz deyirik ki, $U$ ardıcıllığı yalnız və yalnız aşağıdakı iki şərti yerinə yetirildikdə $A$ və $B$-nin **universal ortaq alt ardıcıllığı**dır:
* $U$ $A$ və $B$-nin ortaq alt ardıcıllığıdır.
* $A$ və $B$-nin hər bir ortaq alt ardıcıllığı həm də $U$-nun alt ardıcıllığıdır.

Göstərilə bilər ki, hər hansı iki $A$ və $B$ ardıcıllığının ən çox bir universal ortaq alt ardıcıllığı var.

Tədqiqatçılar $A$ və $B$ heroqlif ardıcıllıqlarını tapıblar.
$A$ ardıcıllığı $N$ heroqlifdən, $B$ ardıcıllığı isə $M$ heroqlifdən ibarətdir.
Tədqiqatçılara $A$ və $B$ ardıcıllıqlarının universal ortaq alt ardıcıllığını hesablamağa kömək edin və ya belə bir ardıcıllığın mövcud olmadığını müəyyən edin.

## İcra Təfərrüatları

Aşağıdakı proseduru yerinə yetirməlisiniz.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: birinci ardıcıllığı göstərən $N$ uzunluqlu massiv.
* $B$: ikinci ardıcıllığı göstərən $M$ uzunluqlu massiv.
* $A$ və $B$-nin universal ortaq alt ardıcıllığı varsa, prosedur bu ardıcıllığı massivdə geri qaytarmalıdır.
  Əks halda, prosedur geriyə $[-1]$ qaytarmalıdır (yeganə elementi $-1$ olan $1$ uzunluğunda massiv).
* Bu prosedur hər bir test üçün bir dəfə çağırılır.

## Məhdudiyyətlər

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* Hər bir $0 \leq i < N$ bərabərsizliyinə uyğun $i$ üçün $0 \leq A[i] \leq 200\,000$
* Hər bir $0 \leq j < M$ bərabərsizliyinə uyğun $j$ üçün $0 \leq B[j] \leq 200\,000$

## Alt Tapşırıqlar

| Alt Tapşırıq | Bal  | Əlavə Məhdudiyyətlər |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$; $A$ və $B$ ardıcıllıqlarının hər biri $0$ və $N-1$ (daxil) aralığında $N$ **fərqli** tam ədəddən ibarətdir.
| 2       | $15$   | Hər hansı $k$ tam ədədi üçün, ($A$-nın $k$-ya bərabər elementlərinin sayı) üstəgəl ($B$-nin $k$-ya bərabər elementlərinin sayı) ən çox $3$-dür.
| 3       | $10$   | Hər bir $0 \leq i < N$ bərabərsizliyinə uyğun $i$ üçün $A[i] \leq 1$; Hər bir $0 \leq j < M$ bərabərsizliyinə uyğun $j$ üçün $B[j] \leq 1$.
| 4       | $16$   | $A$ və $B$-nin universal ortaq alt ardıcıllığı mövcuddur.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | Əlavə məhdudiyyət yoxdur.

## Nümunələr

### Nümunə 1

Aşağıdakı çağırışı nəzərdən keçirin.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Burada $A$ və $B$-nin ortaq alt ardıcıllıqları bunlardır: $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ və $[0, 1, 0, 2]$.

$[0, 1, 0, 2]$ $A$ və $B$-nin ortaq alt ardıcıllığı, və $A$ və $B$-nin bütün ortaq alt ardıcıllıqları $[0, 1, 0, 2]$-nin alt ardıcıllığı olduğuna görə, prosedur $[0, 1, 0, 2]$ geri qaytarmalıdır.


### Nümunə 2

Aşağıdakı çağırışı nəzərdən keçirin.

```
ucs([0, 0, 2], [1, 1])
```

Burada $A$ və $B$-nin yeganə ortaq alt ardıcıllığı $[\ ]$ boş ardıcıllıqdır.
Buradan belə nəticə çıxır ki, prosedur $[\ ]$ boş massivini geri qaytarmalıdır.

### Nümunə 3

Aşağıdakı çağırışı nəzərdən keçirin.
```
ucs([0, 1, 0], [1, 0, 1])
```

Burada $A$ və $B$-nin ortaq alt ardıcıllıqları $[\ ], [0], [1], [0, 1]$ və $[1, 0]$ ardıcıllıqlarıdır.
Göstərmək olar ki, universal ortaq alt ardıcıllıq mövcud deyil.
Beləliklə, prosedur $[-1]$ geri qaytarmalıdır.

## Nümunə Qiymətləndirici

Giriş formatı:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Çıxış formatı:

```
T
R[0]  R[1]  ...  R[T-1]
```

Burada, $R$ `ucs` tərəfindən geri qaytarılan massivdir və $T$ onun uzunluğudur.
