# Ağac

$0$ ilə $N-1$ arasında nömrələnmiş $N$ **təpədən** ibarət **ağacı** nəzərdən keçirək.
Təpə $0$ **kök** adlanır.
Kökdən başqa hər təpənin tək **valideyni** var.
Hər $1 \leq i < N$ bərabərsizliyini ödəyən $i$ təpəsinin valideyni $P[i]$ ($P[i] < i$) təpəsidir.
Biz həmçinin $P[0] = -1$ olduğunu fərz edirik.

Hər hansı $i$ təpəsinin ($0 \leq i < N$) **alt ağacı** aşağıdakı təpələrin çoxluğudur:
 * $i$ və
 * valideyni $i$ olan istənilən təpə və
 * valideyninin valideyni $i$ olan istənilən təpə və
 * valideyninin valideyninin valideyni $i$ olan istənilən təpə və
 * və s.

Aşağıdakı şəkil $N = 6$ təpədən ibarət nümunə ağacı göstərir.
Hər bir ox, heç bir valideyni olmayan kök istisna olmaqla, bir təpəni valideyni ilə əlaqələndirir.
$2$ təpəsinin alt ağacı $2, 3, 4$ və $5$ təpələrinindən ibarətdir.
$0$ təpəsinin alt ağacına ağacın bütün $6$ təpəsi, $4$ təpəsinin alt ağacına isə yalnız təpə $4$ daxildir.

![](subtrees.png "150")

Hər bir təpəyə qeyri-mənfi tam ədəd olan bir **çəki** təyin edilir.
$i$ ($0 \leq i < N$) təpəsinin çəkisi $W[i]$ ilə işarə edilir.

Sizin vəzifəniz hər biri müsbət tam ədədlər cütü $(L, R)$ ilə müəyyən edilən $Q$ sorğuya cavab verəcək proqram yazmaqdır.
Sorğunun cavabı aşağıdakı kimi hesablanmalıdır.

Ağacın hər təpəsinə **əmsal** adlanan tam ədəd təyin edilir.
Belə təyinat $C[0], \ldots, C[N-1]$ ardıcıllığı ilə təsvir olunur, burada $C[i]$ ( $0 \leq i < N$ ) $i$ təpəsinə təyin edilmiş əmsaldır.
Bu ardıcıllığı **əmsal ardıcıllığı** adlandıraq.
Qeyd edək ki, əmsal ardıcıllığının elementləri mənfi, $0$ və ya müsbət ola bilər.

Əgər hər $i$ təpəsi üçün ($0 \leq i < N$) aşağıdakı şərt yerinə yetirilərsə, $(L, R)$ sorğusu üçün əmsal ardıcıllığı **etibarlı** adlanır: $i$ təpəsinin alt ağacındakı təpələrin əmsallarının cəmi $L$-dən az və $R$-dən çox deyil.

Verilmiş $C[0], \ldots, C[N-1]$ əmsal ardıcıllığı üçün, $i$ təpəsinin **dəyəri** $|C[i]| \cdot W[i]$ olaraq hesablanır, burada $|C[i]|$ $C[i]$ -nın mütləq dəyərini bildirir.
Nəhayət, **ümumi dəyər** bütün təpələrin dəyərlərinin cəmidir.
Sizin vəzifəniz hər bir sorğu üçün hər hansı etibarlı əmsal ardıcıllığı ilə əldə edilə bilən **minimum ümumi dəyəri** hesablamaqdır.

Göstərilə bilər ki, istənilən sorğu üçün ən az bir etibarlı əmsal ardıcıllığı mövcuddur.

## İcra Təfərrüatları

Aşağıdakı iki proseduru yerinə yetirməlisiniz:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$: valideynləri və çəkiləri təyin edən $N$ uzunluğunda tam ədədlərdən ibarət massivlər.
* Bu prosedur hər bir test üçün qiymətləndirici ilə proqramınız arasında qarşılıqlı əlaqənin başlanğıcında bir dəfə çağırılır.

```
long long query(int L, int R)
```
* $L$, $R$: bir sorğunu təsvir edən tam ədədlər.
* Bu prosedur, hər bir test üçün `init` çağırışından sonra $Q$ dəfə çağrılır.
* Bu prosedur verilən sorğuya cavabı geri qaytarmalıdır.


## Məhdudiyyətlər

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* Hər bir $1 \leq i < N$ bərabərsizliyinə uyğun $i$ üçün $0 \leq P[i] < i$
* Hər bir $0 \leq i < N$ bərabərsizliyinə uyğun $i$ üçün $0 \leq W[i] \leq 1\,000\,000$
* Hər sorğuda $1 \leq L \leq R \leq 1\,000\,000$

## Alt Tapşırıqlar

| Alt Tapşırıq | Bal  | Əlavə Məhdudiyyətlər |
| :-----: | :----: | ---------------------- |
|   1     |  $10$  | $Q \leq 10$; Hər bir $1 \leq i < N$ bərabərsizliyinə uyğun $i$ üçün $W[P[i]] \leq W[i]$
|   2     |  $13$  | $Q \leq 10$; $N \leq 2\,000$
|   3     |  $18$  | $Q \leq 10$; $N \leq 60\,000$
|   4     |  $7$   | Hər bir $0 \leq i < N$ bərabərsizliyinə uyğun $i$ üçün$W[i] = 1$
|   5     |  $11$  | Hər bir $0 \leq i < N$ bərabərsizliyinə uyğun $i$ üçün$W[i] \leq 1$
|   6     |  $22$  | $L = 1$
|   7     |  $19$  | Əlavə məhdudiyyət yoxdur.



## Nümunələr

Aşağıdakı çağırışları nəzərdən keçirin:

```
init([-1, 0, 0], [1, 1, 1])
```
Ağac $3$ təpədən - kök və onun $2$ uşağından ibarətdir.
Bütün təpələrin çəkisi $1$-dir.

```
query(1, 1)
```

Bu sorğuda $L = R = 1$, yəni hər bir alt ağacdakı əmsalların cəmi $1$-ə bərabər olmalıdır.
$[-1, 1, 1]$ əmsal ardıcıllığını nəzərdən keçirək.
Ağac və müvafiq əmsallar (kölgəli düzbucaqlılarda) aşağıda təsvir edilmişdir.

![](ex1.png "150")

Hər $i$ təpəsi üçün ($0 \leq i < 3$), o təpənin alt ağacındakı bütün təpələrin əmsallarının cəmi $1$-ə bərabərdir. 
Deməli, bu əmsal ardıcıllığı etibarlıdır.
Ümumi dəyər aşağıdakı kimi hesablanır:


| Təpə | Çəki | Əmsal | Dəyər                      |
| :----: | :----: | :---------: | :-----------------------: |
|   0    |   1    |     -1      | $\mid -1 \mid \cdot 1 = 1$
|   1    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$
|   2    |   1    |      1      | $\mid 1 \mid \cdot 1 = 1$

Beləliklə, ümumi dəyər $3$-dür.
Bu yeganə etibarlı əmsal ardıcıllığıdır, ona görə də bu çağrı geriyə $3$ qaytarmalıdır.

```
query(1, 2)
```
Bu sorğu üçün minimum ümumi dəyər $2$-dir və əmsal ardıcıllığı $[0, 1, 1]$ olduqda əldə edilir.

## Nümunə Qiymətləndirici

Giriş formatı:

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

burada $L[j]$ və $R[j]$ ($0 \leq j < Q$ üçün) `query` proseduruna $j$ nömrəli çağırışın giriş parametrləridir.
Qeyd edək ki, nümunə qiymətləndirici $P[0]$ dəyərini oxumadığına görə girişin ikinci sətri **yalnız $N-1$ tam ədəddən** ibarətdir.

Çıxış formatı:
```
A[0]
A[1]
...
A[Q-1]
```

burada $A[j]$ ($0 \leq j < Q$ üçün) `query` proseduruna $j$ nömrəli çağırışın geriyə dönüş dəyəridir.
