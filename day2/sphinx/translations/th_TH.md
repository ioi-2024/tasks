# ปริศนามหาสฟิงซ์

มหาสฟิงซ์ (Great Sphinx) มีปริศนาให้คุณ &nbsp;&nbsp;&nbsp;
คุณจะได้รับกราฟที่มี $N$ จุดยอด แต่ละจุดยอดมีหมายเลขตั้งแต่ $0$ ถึง $N-1$ &nbsp;
กราฟดังกล่าวมีเส้นเชื่อมจำนวน $M$ เส้น ที่มีหมายเลขตั้งแต่ $0$ ถึง $M-1$ แต่ละเส้นเชื่อมจะเชื่อมจุดยอดสองจุดที่แตกต่างกัน โดยเชื่อมทั้งสองทิศทาง &nbsp;&nbsp;&nbsp;&nbsp;
กล่าวคือ สำหรับ $j$ ใด ๆ ตั้งแต่ $0$ ถึง $M-1$ &nbsp; เส้นเชื่อม $j$ จะเชื่อมจุดยอด $X[j]$ และ $Y[j]$ &nbsp;&nbsp;
จะมีเส้นเชื่อมไม่เกินหนึ่งเส้นที่เชื่อมระหว่างคู่ของจุดยอดใด ๆ &nbsp;&nbsp;&nbsp;
เราจะกล่าวว่าจุดยอดสองจุดนั้น**ติดกัน** ถ้ามีเส้นเชื่อมบางเส้นเชื่อมจุดยอดทั้งสอง


ลำดับของจุดยอด  $v_0, v_1, \ldots, v_k$ (สำหรับ $k \ge 0$)
จะเรียกว่า **เส้นทาง**
ถ้าทุก ๆ คู่ของจุดยอดที่ต่อกัน $v_l$ และ $v_{l+1}$ นั้นติดกัน (สำหรับ $l$ ที่ $0 \le l \lt k$) &nbsp;&nbsp;&nbsp;
เราจะกล่าวว่าเส้นทาง $v_0, v_1, \ldots, v_k$ **เชื่อมต่อ** จุดยอด $v_0$ และ $v_k$ &nbsp;&nbsp;
ในกราฟที่คุณได้รับ จะมีบางเส้นทางที่เชื่อมต่อคู่ของจุดยอดใด ๆ


มีสีจำนวน $N + 1$ สี ที่มีหมายเลขตั้งแต่ $0$ ถึง $N$ &nbsp;&nbsp;
สี $N$ จะเป็นสีพิเศษ ที่เรียกว่า **สีของสฟิงซ์** &nbsp;&nbsp;
จุดยอดแต่ละจุดจะมีสีกำหนดไว้ &nbsp;
กล่าวคือ จุดยอด $i$ (สำหรับ  $0 \le i \lt N$) จะมีสี $C[i]$ &nbsp;&nbsp;
จุดยอดหลายจุดอาจมีสีซ้ำกันได้
และเป็นไปได้ที่บางสีจะไม่ถูกกำหนดให้กับจุดยอดใดเลย &nbsp;&nbsp;
ไม่มีจุดยอดใดที่ได้รับสีของสฟิงซ์
นั่นคือ $0 \le C[i] \lt N$ (สำหรับ $0 \le i \lt N$)


เราจะกล่าวว่าเส้นทาง $v_0, v_1, \ldots, v_k$ (สำหรับ $k \ge 0$)
**มีหนึ่งสี** (monochromatic)
ถ้าทุกจุดยอดในเส้นทางดังกล่าวมีสีเดียวกัน
 นั่นคือ $C[v_l] = C[v_{l+1}]$ (สำหรับทุก ๆ  $l$ ที่ $0 \le l \lt k$) &nbsp;&nbsp;
นอกจากนี้ เราจะกล่าวว่าจุดยอด $p$ และ $q$ (สำหรับ $0 \le p \lt N$, $0 \le q \lt N$)
อยู่ใน**คอมโพเนนท์หนึ่งสี** (monochromatic component) อันเดียวกัน ก็ต่อเมื่อมีบางเส้นทางหนึ่งสีเชื่อมต่อจุดยอดทั้งสอง


คุณทราบจุดยอดและเส้นเชื่อมทั้งหมด แต่คุณไม่ทราบสีของแต่ละจุดยอด &nbsp;
คุณต้องการหาว่าจุดยอดต่าง ๆ มีสีอะไรบ้าง โดย**การทดลองกำหนดสี**


ในการทดลองกำหนดสี คุณสามารถกำหนดสีให้กับจุดยอดกี่จุดก็ได้ &nbsp;
กล่าวคือ ในการทดลองกำหนดสี คุณจะต้องระบุอาร์เรย์ $E$ ที่มีขนาด $N$ โดยที่แต่ละ $i$ (สำหรับ $0 \le i \lt N$)
 $E[i]$ จะมีค่าตั้งแต่ $-1$ ถึง $N$ **รวมหัวท้าย** &nbsp;
จากนั้น สีของจุดยอด $i$ จะเปลี่ยนเป็น $S[i]$ โดยค่าของ $S[i]$ จะเป็น:
* $C[i]$, นั่นคือ สีตั้งต้นของจุดยอด $i$ ถ้า $E[i] = -1$ &nbsp;&nbsp; หรือ
* $E[i]$, ในกรณีอื่น ๆ 


สังเกตว่า คุณสามารถใช้สีของสฟิงซ์ในการกำหนดสีใหม่ได้

สุดท้าย มหาสฟิงซ์จะประกาศจำนวนคอมโพเนนท์หนึ่งสีในกราฟ ภายหลังจากการกำหนดสีให้กับทุก ๆ จุดยอด $i$ เป็น $S[i]$ ($0 \le i \lt N$) &nbsp;&nbsp;
การกำหนดสีดังกล่าวมีผลเฉพาะในการทดลองกำหนดสีครั้งนี้เท่านั้น 
ดังนั้น **สีของจุดยอดทั้งหมดจะเปลี่ยนกลับเป็นสีตั้งต้นภายหลังการทดลองเสร็จสิ้นแล้ว**

งานของคุณคือการหาสีทั้งหมดของจุดยอดในกราฟ 
โดยทำการทดลองกำหนดสีได้ไม่เกิน $2\,750$ ครั้ง &nbsp;&nbsp;&nbsp;
คุณจะได้รับคะแนนบางส่วน (partial score) 
ถ้าคุณสามารถระบุได้ว่าระหว่างคู่ของจุดยอดที่ติดกันทุกคู่นั้น จุดยอดทั้งสองมีสีเดียวกันหรือไม่

## รายละเอียดการเขียนโปรแกรม

คุณจะต้องเขียนฟังก์ชันต่อไปนี้

```
std::vector&lt;int&gt; find_colours(int N,
    std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y)
```

* $N$: จำนวนจุดยอดในกราฟ
* $X$, $Y$: อาร์เรย์ความยาว $M$ ที่ระบุเส้นเชื่อม
* ฟังก์ชันดังกล่าวจะต้องคืนอาร์เรย์ $G$ ที่มีความยาว $N$
   ที่แทนสีของจุดยอดในกราฟ
* ฟังก์ชันดังกล่าวจะถูกเรียกหนึ่งครั้งพอดีสำหรับแต่ละกรณีทดสอบ

ฟังก์ชันดังกล่าวสามารถเรียกใช้ฟังก์ชันด้านล่างเพื่อทำการทดลองกำหนดสี:

```
int perform_experiment(std::vector&lt;int&gt; E)
```

* $E$: อาร์เรย์ความยาว $N$ ที่ระบุว่าจุดยอดจะถูกกำหนดสีใหม่อย่างไร
* ฟังก์ชันนี้จะคืนจำนวนคอมโพเนนท์หนึ่งสีในกราฟ ภายหลังการกำหนดสีตาม $E$
* สามารถเรียกฟังก์ชันนี้ได้ไม่เกิน $2\,750$ ครั้ง

เกรดเดอร์จะไม่ทำงานแบบ **ปรับเปลี่ยนได้** (adaptive) นั่นคือ
สีของจุดยอดทั้งหมดจะถูกระบุก่อนที่จะมีการเรียกใช้ `find_colours`

## เงื่อนไข

* $2 \le N \le 250$
* $N - 1 \le M \le \frac{N \cdot (N - 1)}{2}$
* $0 \le X[j] \lt Y[j] \lt N$ สำหรับแต่ละ $j$ ที่ $0 \le j \lt M$
* $X[j] \neq X[k]$ หรือ $Y[j] \neq Y[k]$
   สำหรับทุก ๆ $j$ และ $k$ ที่ $0 \le j \lt k \lt M$
* แต่ละคู่ของจุดยอดจะเชื่อมต่อกันด้วยบางเส้นทาง
* $0 \le C[i] \lt N$ สำหรับแต่ละ $i$ ที่ $0 \le i \lt N$

## ปัญหาย่อย

| ปัญหาย่อย | คะแนน  | เงื่อนไขเพิ่มเติม |
| :-----: | :----: | ---------------------- |
| 1       | $3$    | $N = 2$
| 2       | $7$    | $N \le 50$
| 3       | $33$   | กราฟเป็นกราฟเส้นทาง: $M = N - 1$ และจุดยอด $j$ กับ $j+1$ นั้นติดกัน (สำหรับ $0 \leq j < M$)
| 4       | $21$   | กราฟเป็นกราฟบริบูรณ์ (complete graph): $M = \frac{N \cdot (N - 1)}{2}$ และจุดยอดสองจุดใดๆ จะติดกัน
| 5       | $36$   | ไม่มีเงื่อนไขเพิ่มเติม

ในแต่ละปัญหาย่อย คุณจะได้รับคะแนนบางส่วน 
ถ้าโปรแกรมของคุณสามารถระบุได้อย่างถูกต้องว่าในทุก ๆ คู่ของจุดยอดที่ติดกัน
จุดยอดทั้งสองมีสีเดียวกันหรือไม่

กล่าวคือ
คุณจะได้คะแนนเต็มในปัญหาย่อยนี้
ถ้าในทุก ๆ กรณีทดสอบ
อาร์เรย์ $G$ ที่คืนค่าโดย `find_colours`
นั้นเหมือนกับอาร์เรย์ $C$
 (นั่นคือ $G[i] = C[i]$
 สำหรับทุก ๆ  $i$ ที่ $0 \le i \lt N$) &nbsp;&nbsp;&nbsp;
ถ้าไม่เช่นนั้น
 คุณจะได้คะแนน $50\%$ ของคะแนนในปัญหาย่อย
 ถ้าเงื่อนไขต่อไปนี้เป็นจริง
 ในทุกกรณีทดสอบ:
* $0 \le G[i] \lt N$
   สำหรับทุก ๆ  $i$ ที่ $0 \le i \lt N$
* สำหรับทุก ๆ $j$ ที่ $0 \le j \lt M$:
  * $G[X[j]] = G[Y[j]]$ ก็ต่อเมื่อ $C[X[j]] = C[Y[j]]$

## ตัวอย่าง

พิจารณาการเรียกฟังก์ชันดังนี้

```
find_colours(4, [0, 1, 0, 0], [1, 2, 2, 3])
```

ในตัวอย่างนี้ สมมติว่าสีของจุดยอด (ที่ถูกซ่อนไว้) ถูกระบุโดย
 $C = [2, 0, 0, 0]$.
สถานการณ์ดังกล่าวเป็นดังภาพ &nbsp;&nbsp;
ตัวเลขในป้ายสีขาวที่ติดกับจุดยอดแต่ละจุดระบุสีของจุดยอดดังกล่าวนั้น

![example.png](sphinx_example.png "230")

ฟังก์ชันสามารถเรียก `perform_experiment` ดังนี้

```
perform_experiment([-1, -1, -1, -1])
```

ในตัวอย่างนี้ ไม่มีจุดยอดใดเลยที่ถูกกำหนดสีใหม่ นั่นคือทุกจุดยอดจะมีสีเหมือนสีตั้งต้น

พิจารณาจุดยอด $1$ และจุดยอด $2$ &nbsp;
ทั้งสองจุดยอดมีสี $0$ และเส้นทาง $1, 2$ เป็นเส้นทางหนึ่งสี &nbsp;
ดังนั้นจุดยอด $1$ และ $2$ จะอยู่ในคอมโพเนนท์หนึ่งสี อันเดียวกัน

พิจารณาจุดยอด $1$ และจุดยอด $3$ &nbsp;
แม้ว่าทั้งสองจุดยอดจะมีสีเดียวกันคือสี $0$ &nbsp;
แต่จุดยอดทั้งสองอยู่ในคอมโพเนนท์หนึ่งสีที่แตกต่างกัน
เนื่องจากไม่มีเส้นทางหนึ่งสีที่เชื่อมต่อระหว่างทั้งสองจุด

ดังนั้น เราจะมี $3$ คอมโพเนนท์หนึ่งสี 
ที่มีจุดยอด $\{0\}$, $\{1, 2\}$, และ $\{3\}$ &nbsp;&nbsp;
ดังนั้นฟังก์ชันนี้จะคืนค่า  $3$

ต่อมาฟังก์ชันอาจจะเรียก `perform_experiment` ดังด้านล่าง

```
perform_experiment([0, -1, -1, -1])
```

ในตัวอย่างนี้ มีแค่จุดยอด $0$ เท่านั้นที่ถูกกำหนดสีใหม่ให้เป็นสี $0$
ทำให้ได้กราฟที่มีสีดังภาพ

![example.png](sphinx_order1.png "230")

การเรียกนี้จะคืนค่า $1$ เนื่องจากทุกจุดยอดจะอยู่ในคอมโพเนนท์หนึ่งสี อันเดียวกันทั้งหมด
เราจึงสามารถสรุปได้ว่าจุดยอด $1$, $2$ และ $3$ ต่างมีสี $0$

หลังจากนั้น ฟังก์ชันสามารถเรียก `perform_experiment` ดังด้านล่าง

```
perform_experiment([-1, -1, -1, 2])
```

ในการเรียกนี้จุดยอด $3$ ถูกกำหนดสีใหม่เป็นสี $2$
 ทำให้ได้สีของจุดยอดดังภาพ

![example.png](sphinx_order2.png "230")

การเรียกนี้จะคืนค่า $2$ เนื่องจากในกราฟมีคอมโพเนนท์หนึ่งสีจำนวน $2$ คอมโพเนนท์
 ที่มีจุดยอด $\{0, 3\}$ และ $\{1, 2\}$ ตามลำดับ &nbsp;
เราสามารถสรุปได้ว่าจุดยอด $0$ มีสี $2$

ฟังก์ชัน `find_colours` จึงคืนอาร์เรย์ $[2, 0, 0, 0]$
เนื่องจาก $C = [2, 0, 0, 0]$ คำตอบนี้จึงได้คะแนนเต็ม

สังเกตว่ามีคำตอบที่ฟังก์ชันคืนกลับไปหลายรูปแบบที่ทำให้ได้คะแนน $50\%$ ยกตัวอย่างเช่น $[1, 2, 2, 2]$ หรือ $[1, 2, 2, 3]$

## เกรดเดอร์ตัวอย่าง

รูปแบบข้อมูลนำเข้า:

```
N  M
C[0]  C[1] ... C[N-1]
X[0]  Y[0]
X[1]  Y[1]
...
X[M-1]  Y[M-1]
```

รูปแบบข้อมูลส่งออก:

```
L  Q
G[0]  G[1] ... G[L-1]
```

ในที่นี้ $L$ คือความยาวของอาร์เรย์ $G$ ที่คืนจากฟังก์ชัน `find_colours`
 และ $Q$ ระบุจำนวนครั้งของการเรียกฟังก์ชัน `perform_experiment`