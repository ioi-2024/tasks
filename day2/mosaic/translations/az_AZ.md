# Mozaika

Səlma divarda gil mozaika rəngləməyi planlaşdırır.
Mozaika əvvəlcə $N^2$ sayda $1 \times 1$ ölçülü rəngsiz kvadrat plitələrdən ibarət $N \times N$ ölçülü şəbəkədir.
Mozaikanın sətirləri yuxarıdan aşağıya $0$-dan $N-1$-ə, sütunları isə soldan sağa $0$-dan $N-1$-ə kimi nömrələnir.
$i$-ci sətir və $j$-ci sütunda ($0 \leq i < N$, $0 \leq j < N$) yerləşən plitə $(i,j)$ ilə işarələnir.
Hər bir plitə ya ağ ($0$ ilə işarələnir) ya da qara ($1$ ilə işarələnir) rəngdə rənglənməlidir.

Mozaikanı rəngləmək üçün Səlma əvvəlcə hər biri $0$ və $1$ dəyərlərindən ibarət $N$ uzunluqlu, $X[0] = Y[0]$ şərtini ödəyən $X$ və $Y$ massivləri seçir.
O, $X$ massivinə uyğun olaraq ən yuxarı sətrin ($0$-cı sətir) plitələrini elə rəngləyir ki, $(0,j)$ plitəsinin rəngi $X[j]$ ($0 \leq j < N$) olsun.
O, həmçinin $Y$ massivinə uyğun olaraq ən sol sütunun ($0$-cı sütun) plitələrini elə rəngləyir ki, $(i,0)$ plitəsinin rəngi $Y[i]$ ($0 \leq i < N$) olsun.

Sonra bütün plitələr rənglənənə qədər aşağıdakı addımları təkrarlayır:
* O, hər hansı elə *rəngsiz* $(i,j)$ plitəsi tapır ki, onun yuxarı qonşusu ($(i-1, j)$ plitəsi) və sol qonşusu ($(i, j-1)$ plitəsi) hər ikisi * artıq rənglənib*.
* Sonra, bu qonşuların hər ikisi ağdırsa, o, $(i,j)$ plitəsini qara rəngdə, əks halda ağ rəngdə rəngləyir. 

Göstərilə bilər ki, plitələrin yekun rəngləri Səlmanın onları rəngləmə ardıcıllığından asılı deyil.

Yasəmin mozaikadakı plitələrin rəngləri ilə çox maraqlanır.
O, Səlmadan $0$-dan $Q-1$-ə qədər nömrələnmiş $Q$ sayda sual soruşur.
$k$ ($0 \leq k < Q$) nömrəli sualda Yasəmin mozaikanın alt düzbucaqlısını onun:
* Ən yuxarı sətri $T[k]$ və ən aşağı sətri $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* Ən sol sütunu $L[k]$ və ən sağ sütunu $R[k]$ ($0 \leq L[k] \leq R[k] < N$) əsasında müəyyən edir.
 
Sualın cavabı bu alt düzbucaqlıdakı qara plitələrin sayıdır.
Konkret olaraq, Səlma $T[k] \leq i \leq B[k]$ , $L[k] \leq j \leq R[k]$ şərtlərini ödəyən qara rəngli $(i, j)$ plitələrinin sayını tapmalıdır.

Yasəminin suallarına cavab verən proqram yazın.

## İcra Təfərrüatları

Aşağıdakı proseduru icra etməlisiniz.

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: müvafiq olaraq ən yuxarı sətir və ən sol sütunda olan plitələrin rənglərini təsvir edən $N$ uzunluğunda massivlər.
* $T$, $B$, $L$, $R$: Yasəmin tərəfindən verilən sualları təsvir edən $Q$ uzunluğunda massivlər.
* Bu prosedur $k$-cı ($0 \leq k < Q$) suala cavabın $C[k]$ olduğu $Q$ uzunluğunda $C$ massivi qaytarmalıdır.
* Bu prosedur hər bir test üçün bir dəfə çağrılır.

## Məhdudiyyətlər

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $0 \leq i < N$ olan hər bir $i$ üçün $X[i] \in \{0, 1\}$ və $Y[i] \in \{0, 1\}$
* $X[0] = Y[0]$
* $0 \leq k < Q$ olan hər bir $k$ üçün $0 \leq T[k] \leq B[k] < N$ və $0 \leq L[k] \leq R[k] < N$

## Alt Tapşırıqlar

| Alt Tapşırıq | Bal  | Əlavə Məhdudiyyətlər |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ ($0 \leq k < Q$ olan hər bir $k$ üçün)
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ ($0 \leq i < N$ olan hər bir $i$ üçün)
| 6       | $22$   | $T[k] = B[k]$ və $L[k] = R[k]$ ($0 \leq k < Q$ olan hər bir $k$ üçün)
| 7       | $19$   | $T[k] = B[k]$ ($0 \leq k < Q$ olan hər bir $k$ üçün)
| 8       | $22$   | Əlavə məhdudiyyət yoxdur.

## Nümunə

Aşağıdakı çağırışı nəzərdən keçirin.

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Bu nümunə aşağıdakı şəkillərdə təsvir edilmişdir.
Sol şəkil mozaikadakı plitələrin rənglərini göstərir.
Orta və sağ şəkillər Yasəminin müvafiq olaraq birinci və ikinci sualda soruşduğu alt düzbucaqlıları göstərir.

![](example.png "550")

Sualların cavabları (yəni kölgəli düzbucaqlılardakı birlərin sayı) müvafiq olaraq 7 və 3-dür.
Beləliklə, prosedur $[7, 3]$ qaytarmalıdır.


## Nümunə Qiymətləndirici

Giriş formatı:

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

Çıxış formatı:

```
C[0]
C[1]
...
C[S-1]
```

Burada $S$ `mosaic` tərəfindən qaytarılan $C$ massivinin uzunluğudur.