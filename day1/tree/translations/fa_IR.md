# درخت

درختی شامل $N$ **رأس** را در نظر بگیرید که رأس‌های آن از $0$ تا $N-1$ شماره‌گذاری شده‌اند. رأس $0$ به عنوان **ریشه** شناخته می‌شود. هر رأس به جز ریشه دارای یک **پدر** است. برای هر $i$ با شرط $1 \leq i < N$، پدر رأس $i$ رأس $P[i]$ است که در آن $P[i] < i$ است. همچنین فرض می‌کنیم $P[0] = -1$.

برای هر رأس $i$ ($0 \leq i < N$)، **زیردرخت** $i$ مجموعه‌ای از رأس‌های زیر را شامل می‌شود:
*  رأس $i$،
* هر رأسی که پدرش $i$ است،
* هر رأسی که پدر پدرش $i$ است،
* هر رأسی که پدر پدر پدرش $i$ است،
* و الی آخر.

تصویر زیر یک درخت شامل $N = 6$ رأس را نشان می‌دهد. هر پیکان یک رأس را به پدر آن متصل می‌کند، به جز ریشه که پدر ندارد. زیردرخت رأس $2$ شامل رأس‌های $2$، $3$، $4$ و $5$ است. زیردرخت رأس $0$ شامل همه $6$ رأس درخت است و زیردرخت رأس $4$ فقط شامل رأس $4$ است.

![](subtrees.png "150")

به هر رأس یک عدد صحیح غیرمنفی به عنوان **وزن** اختصاص داده شده است که وزن رأس $i$ ($0 \leq i < N$) را با $W[i]$ نشان می‌دهیم.

وظیفه شما این است که برنامه‌ای بنویسید که به $Q$ پرسش پاسخ دهد، که هر پرسش با یک زوج عدد صحیح مثبت $(L, R)$ مشخص می‌شود. پاسخ به هر پرسش باید به صورت زیر محاسبه شود.

فرض کنید به هر رأس درخت یک عدد صحیح به عنوان **ضریب** اختصاص یافته است.
به دنباله $C[0], \ldots, C[N-1]$  از اعداد صحیح که در آن $C[i]$ ($0 \leq i < N$) ضریب اختصاص‌یافته به رأس $i$ است، **دنباله ضرایب** می‌گوییم. توجه داشته باشید که عناصر دنباله ضرایب می‌توانند منفی، $0$ یا مثبت باشند.

برای یک پرسش $(L, R)$، یک دنباله ضرایب **معتبر** نامیده می‌شود اگر برای هر رأس $i$ ($0 \leq i < N$)، شرط زیر برقرار باشد: مجموع ضرایب رأس‌های موجود در زیردرخت رأس $i$ نباید کمتر از $L$ و نباید بیشتر از $R$ باشد.

برای یک دنباله ضرایب $C[0], \ldots, C[N-1]$، **هزینه** رأس $i$ برابر است با $|C[i]| \cdot W[i]$، که در آن $|C[i]|$ قدر مطلق $C[i]$ را نشان می‌دهد. در نهایت، **هزینه کل** برابر است با مجموع هزینه‌های تمام رأس‌ها. وظیفه شما این است که برای هر پرسش، **کم‌ترین هزینه کل** را که می‌تواند توسط یک دنباله ضرایب معتبر به دست آید، محاسبه کنید.

می‌توان نشان داد که برای هر پرسش، حداقل یک دنباله ضرایب معتبر وجود دارد.

## جزئیات پیاده‌سازی

شما باید دو تابع زیر را پیاده‌سازی کنید:

```
void init(std::vector&lt;int&gt; P, std::vector&lt;int&gt; W)
```

* $P$, $W$: آرایه‌هایی از اعداد صحیح با طول $N$ که پدرها و وزن‌ها را مشخص می‌کنند.
* این تابع دقیقاً یک بار در ابتدای تعامل بین ارزیاب و برنامه شما در هر تست فراخوانی می‌شود.

```
long long query(int L, int R)
```
* $L$, $R$: اعداد صحیحی که یک پرسش را توصیف می‌کنند.
* این تابع $Q$ بار پس از فراخوانی `init` در هر تست فراخوانی می‌شود.
* این تابع باید پاسخ پرسش داده شده را بازگرداند.

## محدودیت‌ها

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 100\,000$
* $P[0] = -1$
* $0 \leq P[i] < i$ برای هر $i$ که $1 \leq i < N$ باشد
* $0 \leq W[i] \leq 1\,000\,000$ برای هر $i$ که $0 \leq i < N$ باشد
* $1 \leq L \leq R \leq 1\,000\,000$ در هر پرسش

## زیرمسئله‌ها

| زیرمسئله | امتیاز  | محدودیت‌های اضافی        |
| :-------: | :-----: | ------------------------ |
|   1       |  $10$   | $Q \leq 10$؛ $W[P[i]] \leq W[i]$ برای هر $i$ که $1 \leq i < N$ باشد |
|   2       |  $13$   | $Q \leq 10$؛ $N \leq 2\,000$ |
|   3       |  $18$   | $Q \leq 10$؛ $N \leq 60\,000$ |
|   4       |  $7$    | $W[i] = 1$ برای هر $i$ که $0 \leq i < N$ باشد |
|   5       |  $11$   | $W[i] \leq 1$ برای هر $i$ که $0 \leq i < N$ باشد |
|   6       |  $22$   | $L = 1$ |
|   7       |  $19$   | هیچ محدودیت اضافی‌ای وجود ندارد |

## مثال‌ها

فراخوانی‌های زیر را در نظر بگیرید:

```
init([-1, 0, 0], [1, 1, 1])
```
درخت از $3$ رأس شامل یک ریشه و $2$ فرزند آن تشکیل شده است. همه رأس‌ها وزن $1$ دارند.

```
query(1, 1)
```

در این پرسش $L = R = 1$ است، که به معنای آن است که مجموع ضرایب در هر زیردرخت باید برابر با $1$ باشد. دنباله ضرایب $[-1, 1, 1]$ را در نظر بگیرید. درخت و ضرایب متناظر (داخل مستطیل‌های خاکستری) در زیر نشان داده شده‌اند.

![](ex1.png "150")

برای هر رأس $i$ ($0 \leq i < 3$)، مجموع ضرایب همه رأس‌های موجود در زیردرخت $i$ برابر با $1$ است. بنابراین، این دنباله ضرایب معتبر است. هزینه کل به صورت زیر محاسبه می‌شود:

| رأس  | وزن   | ضریب    | هزینه                            |
| :--: | :--:  | :-----: | :------------------------------: |
|  0   |  1    |   -1    | $\mid -1 \mid \cdot 1 = 1$ |
|  1   |  1    |    1    | $\mid 1 \mid \cdot 1 = 1$  |
|  2   |  1    |    1    | $\mid 1 \mid \cdot 1 = 1$  |

بنابراین هزینه کل $3$ است. این تنها دنباله ضرایب معتبر است، بنابراین این فراخوانی باید $3$ را بازگرداند.

```
query(1, 2)
```
کم‌ترین هزینه کل برای این پرسش برابر $2$ است و وقتی دنباله ضرایب برابر $[0, 1, 1]$ باشد، به دست می‌آید.

## ارزیاب نمونه

فرمت ورودی:

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

که در آن $L[j]$ و $R[j]$ 
 (برای $0 \leq j < Q$)
 پارامترهای ورودی در $j$-امین فراخوانی به `query` هستند.
توجه داشته باشید که خط دوم ورودی **فقط شامل $N-1$ عدد صحیح** است،
 زیرا ارزیاب نمونه مقدار $P[0]$ را نمی‌خواند.

فرمت خروجی:
```
A[0]
A[1]
...
A[Q-1]
```

که در آن $A[j]$
 (برای $0 \leq j <  Q$)
 مقداری است که توسط $j$-امین فراخوانی به `query` بازگردانده می‌شود.
