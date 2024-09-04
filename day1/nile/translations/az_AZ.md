# Nil Çayı

Siz Nil çayı vasitəsilə $N$ artefakt daşımaq istəyirsiniz. 
Artefaktlar $0$-dan $N-1$-ə qədər nömrələnib.
$i$ ($0 \leq i < N$) artefaktının çəkisi $W[i]$ təşkil edir.

Artefaktları daşımaq üçün xüsusi qayıqlardan istifadə edirsiniz.
Hər bir qayıq **ən çox iki** artefakt daşıya bilər.

* Bir qayığa tək bir artefakt qoymaq qərarına gəlsəniz, artefaktın çəkisi ixtiyari ola bilər.
* Eyni qayığa iki artefakt qoymaq istəyirsinizsə, qayığın bərabər balanslı olduğundan əmin olmalısınız.
Xüsusilə, siz $p$ və $q$ ($0 \leq p < q < N$) artefaktlarını eyni qayıqda yalnız onların çəkiləri arasında mütləq fərq ən çox $D$, yəni $|W[p] - W[q]| \leq D$ olduqda göndərə bilərsiniz.

Artefaktı daşımaq üçün eyni qayıqda daşınan artefaktların sayından asılı olan bir xərc ödəməlisiniz.
$i$ ($0 \leq i < N$) artefaktının daşınmasının xərci:

* artefaktı öz qayığına qoysanız $A[i]$ və ya
* onu başqa bir artefaktla birlikdə qayığa qoysanız $B[i]$-dir.

Nəzərə alın ki, sonuncu halda qayıqdakı hər iki artefaktın xərcini ödəməlisiniz.
Xüsusilə, $p$ və $q$ ($0 \leq p < q < N$) artefaktlarını eyni qayıqda göndərmək qərarına gəlsəniz, $B[p] + B[q]$ xərcini ödəməlisiniz.

Bir artefaktın tək başına qayıqda göndərilməsi həmişə qayığı onunla paylaşan digər artefaktla göndərməkdən daha baha başa gəlir, yəni bütün $0 \leq i < N$ bərabərsizliyini ödəyən $i$-lər üçün $B[i] < A[i]$ bərabərsizliyi ödənir.

Təəssüf ki, çay çox gözlənilməzdir və $D$-nin dəyəri tez-tez dəyişir.
Sizin vəzifəniz $0$-dan $Q-1$-ə qədər nömrələnmiş $Q$ sorğuya cavab verməkdir.
Sorğular $Q$ uzunluğunda $E$ massivi ilə təsvir edilmişdir.
$j$ ($0 \leq j < Q$) sorğusunun cavabı $D$ dəyəri $E[j]$-ə bərabər olduqda, bütün $N$ artefaktların daşınmasının minimum toplam xərcidir.

## İcra Təfərrüatları

Aşağıdakı proseduru yerinə yetirməlisiniz.

```
std::vector&lt;long long&gt; calculate_costs(
    std::vector&lt;int&gt; W, std::vector&lt;int&gt; A, 
    std::vector&lt;int&gt; B, std::vector&lt;int&gt; E)
```

* $W$, $A$, $B$: artefaktların çəkilərini və onların daşınması xərclərini təsvir edən $N$ uzunluğunda tam ədəd massivləri.
* $E$: hər sual üçün $D$ dəyərini təsvir edən $Q$ uzunluğunda tam ədəd massivi.
* Bu prosedur artefaktların daşınmasının minimum toplam xərclərindən ibarət $Q$ ölçülü $R$ tam ədəd massivini geri qaytarmalıdır, burada $R[j]$ $D$ dəyəri $E[j]$ olduqdakı xərci göstərir ($0 \leq j < Q$ bərabərsizliyini ödəyən bütün $j$-lər üçün).
* Bu prosedur hər bir test üçün bir dəfə çağırılır.

## Məhdudiyyətlər

* $1 \leq N \leq 100\,000$
* $1 \leq Q \leq 100\,000$
* Hər bir $0 \leq i < N$ bərabərsizliyinə uyğun $i$ üçün $1 \leq W[i] \leq 10^{9}$
* Hər bir $0 \leq i < N$ bərabərsizliyinə uyğun $i$ üçün $1 \leq B[i] < A[i] \leq 10^{9}$
* Hər bir $0 \leq j < Q$ bərabərsizliyinə uyğun $j$ üçün $1 \leq E[j] \leq 10^{9}$

## Alt Tapşırıqlar

| Alt Tapşırıq | Bal  | Əlavə Məhdudiyyətlər |
| :-----: | :----: | ---------------------- |
| 1       | $6$    | $Q \leq 5$; $N \leq 2000$; Hər bir $0 \leq i < N$ bərabərsizliyinə uyğun $i$ üçün $W[i] = 1$
| 2       | $13$   | $Q \leq 5$; Hər bir $0 \leq i < N$ bərabərsizliyinə uyğun $i$ üçün $W[i] = i+1$
| 3       | $17$   | $Q \leq 5$; Hər bir $0 \leq i < N$ bərabərsizliyinə uyğun $i$ üçün $A[i] = 2$ və $B[i] = 1$
| 4       | $11$   | $Q \leq 5$; $N \leq 2000$
| 5       | $20$   | $Q \leq 5$
| 6       | $15$   | Hər bir $0 \leq i < N$ bərabərsizliyinə uyğun $i$ üçün $A[i] = 2$ və $B[i] = 1$
| 7       | $18$   | Əlavə məhdudiyyət yoxdur.

## Nümunə

Aşağıdakı çağırışı nəzərdən keçirin.

```
calculate_costs([15, 12, 2, 10, 21],
                [5, 4, 5, 6, 3],
                [1, 2, 2, 3, 2],
                [5, 9, 1])
```

Bu nümunədə $N = 5$ artefakt və $Q = 3$ sorğu var.

Birinci sorğuda $D = 5$-dir.
Siz $0$ və $3$ artefaktlarını bir qayıqda ($|15 - 10| \leq 5$ olduğu üçün) və qalan artefaktları ayrı-ayrı qayıqlarda göndərə bilərsiniz.
Bu bütün artefaktların daşınması üçün minimum xərc ($1+4+5+3+3 = 16$) verir.

İkinci sorğuda $D = 9$-dur.
Siz $0$ və $1$ artefaktlarını bir qayıqda ($|15 - 12| \leq 9$ olduğu üçün) və $2$ və $3$ artefaktlarını başqa bir qayıqda göndərə bilərsiniz ($|2 - 10| \leq 9$ olduğu üçün).
Qalan artefaktlar ayrı-ayrı qayıqlarda göndərilə bilər.
Bu bütün artefaktların daşınması üçün minimum xərc ($1+2+2+3+3 = 11$) verir.

Son sorğuda $D = 1$-dir. Siz hər artefaktı öz qayığında göndərməlisiniz.
Bu bütün artefaktların daşınması üçün minimum xərc ($5+4+5+6+3 = 23$) verir.

Beləliklə, bu prosedur $[16, 11, 23]$ geri qaytarmalıdır.


## Nümunə Qiymətləndirici

Giriş formatı:

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

Çıxış formatı:

```
R[0]
R[1]
...
R[S-1]
```

Burada, $S$ `calculate_costs` tərəfindən geri qaytarılan $R$ massivinin uzunluğudur.
