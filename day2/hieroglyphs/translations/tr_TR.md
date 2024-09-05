# Hiyeroglifler

Bir grup araştırmacı, seriler ve hiyeroglifler arasındaki benzerlikleri araştırıyor.
Araştırmacılar, her hiyeroglifi negatif olmayan bir tam sayı ile temsil ediyor.
Çalışmalarını gerçekleştirmek için, seriler hakkındaki şu kavramları kullanırlar.

Sabit bir $A$ serisi için, $S$ serisi $A$ serisinin **alt serisi** olarak adlandırılır
 ancak ve ancak 
 $A$ dan bazı elemanları (muhtemelen hiç) çıkararak $S$  elde edilebilirse.

Aşağıdaki tablo $A = [3, 2, 1, 2]$ serisinin alt serisine ait bazı örnekleri göstermektedir.

| Altseri    | $A$ dan nasıl elde edilebileceği |
|----------------|---------------------------------|
| [3, 2, 1, 2] | Hiçbir eleman çıkarılmaz.
| [2, 1, 2]     | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]     | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] or [3, 2, <s>1</s>, <s>2</s>]
| [3]             | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]              | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Diğer taraftan, $[3, 3]$ ya da $[1, 3]$, $A$ nın altserisi değildir.

İki hiyeroglif serisini, $A$ ve $B$, ele alalım. $S$ serisine $A$ ve $B$ serilerinin **ortak alt serisi** denir ancak ve ancak $S$ hem $A$ hem de $B$ serisinin bir alt serisi ise. Ayrıca, $U$ serisi $A$ ve $B$ serilerinin **evrensel ortak bir alt serisi** dir ancak ve ancak aşağıdaki iki koşul sağlanırsa:
* $U$, $A$ ve $B$ serilerinin ortak bir alt serisidir.
* $A$ ve $B$'nin her ortak alt serisi aynı zamanda $U$'nun da bir alt serisidir.

Herhangi iki $A$ ve $B$ serisinin en fazla bir tane evrensel ortak alt seriye sahip olduğu gösterilebilir.

Araştırmacılar $A$ ve $B$ olmak üzere iki adet hiyeroglif serisi bulmuşlardır. $A$ serisi $N$ hiyerogliften oluşur ve $B$ serisi $M$ hiyerogliften oluşur. Araştırmacıların $A$ ve $B$ serilerinin evrensel ortak alt serisini hesaplamasına, veya bir evrensel ortak alt serinin olmadığını belirlemesine yardımcı olun.

## Kodlama detayları

Aşağıdaki prosedürü kodlamanız gerekmektedir.


```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$ : ilk seriyi tanımlayan $N$ uzunluğunda dizi.
* $B$ : ikinci seriyi tanımlayan $M$ uzunluğunda dizi.
* $A$ ve $B$'nin evrensel ortak bir alt serisi varsa, prosedür bu seriyi içeren bir dizi dönmelidir.
  Aksi takdirde, prosedür $[-1]$ değerini dönmelidir (uzunluğu $1$ olan ve tek elemanı $-1$ olan bir dizi).
* Bu prosedür her test durumu için tam olarak bir kez çağrılır.

## Kısıtlar

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* Her $i$ için $0 \leq A[i] \leq 200\,000$ öyle ki $0 \leq i < N$
* Her $j$ için $0 \leq B[j] \leq 200\,000$ öyle ki $0 \leq j < M$

## Altgörevler

| Altgörev | Puan  | Ek Kısıtlar |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = M$;  $A$ ve $B$'nin her ikisi de $0$ ile $N-1$ (sınırlar dahil) arasında $N$ **farklı** tam sayıdan oluşur
| 2       | $15$   | Herhangi bir $k$ tam sayısı için, $A$'nın $k$ sayısına eşit olan eleman sayısı *artı* $B$'nin $k$ sayısına eşit olan eleman sayısı en fazla $3$ olabilir.
| 3       | $10$   |  $A[i] \leq 1$ her $i$ için öyle ki $0 \leq i < N$ ; $B[j] \leq 1$ her $j$ için öyle ki $0 \leq j < M$
| 4       | $16$   | $A$ ve $B$ nin evrensel ortak bir alt serisi vardır.
| 5       | $14$   | $N \leq 3000$; $M \leq 3000$
| 6       | $42$   | Ek kısıt yoktur.

## Örnekler

### Örnek 1

Aşağıdaki çağrıyı göz önüne alın.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Burada, $A$ ve $B$'nin ortak alt serileri şunlardır:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ ve $[0, 1, 0, 2]$.

$[0, 1, 0, 2]$, $A$ ve $B$'nin ortak bir alt serisi olduğundan ve $A$ ve $B$'nin tüm ortak alt serileri $[0, 1, 0, 2]$'nin alt serisi olduğundan, prosedür $[0, 1, 0, 2]$ değerini dönmelidir.

### Örnek 2

Aşağıdaki çağrıyı göz önüne alın.

```
ucs([0, 0, 2], [1, 1])
```

Burada, $A$ ve $B$'nin tek ortak altserisi boş seridir; $[\ ]$. Bu yüzden prosedür boş dizi ($[\ ]$) dönmelidir.

### Örnek 3

Aşağıdaki çağrıyı göz önüne alın.
```
ucs([0, 1, 0], [1, 0, 1])
```

Burada, $A$ ve $B$'nin ortak alt serileri şunlardır: $[\ ], [0], [1], [0, 1]$ and $[1, 0]$. Evrensel bir ortak altserinin olmadığı gösterilebilir. Bu yüzden prosedür $[-1]$ dönmelidir.

## Örnek Değerlendirici

Girdi formatı:

```
N  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Çıktı formatı:

```
T
R[0]  R[1]  ...  R[T-1]
```

Burada, $R$ ile `ucs` tarafından dönülen dizi, $T$ ile ise bu dizinin uzunluğu gösterilmektedir.