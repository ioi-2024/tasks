# חידת הספינקס

לספינקס הגדול יש חידה בשבילכם. 
נתון לכם גרף בעל $N$ צמתים.
הצמתים ממוספרים מ-$0$ עד $N - 1$.
ישנן $M$ קשתות בגרף, ממוספרות מ-$0$ עד $M-1$.
כל קשת מחברת זוג צמתים שונים והיא דו כיוונית.
ספציפית, לכל $j$ מ-$0$ עד $M - 1$ (כולל),
 הקשת $j$ מחברת בין הצמתים $X[j]$ ו-$Y[j]$.
 יש לכל היותר קשת אחת המחברת בין כל זוג צמתים.
שני צמתים נקראים **סמוכים**
 אם הם מחוברים על ידי קשת.

סדרת צמתים $v_0, v_1, \ldots, v_k$ (עבור $k \ge 0$)
 נקראת **מסלול**
 אם כל זוג צמתים עוקבים $v_l$ ו-$v_{l+1}$
 (עבור כל $l$ שמקיים $0 \le l \lt k$)
 הם סמוכים.
נאמר שמסלול $v_0, v_1, \ldots, v_k$ **מחבר** את הצמתים $v_0$ ו-$v_k$.
בגרף הנתון לכם, כל זוג צמתים מחובר באמצעות מסלול כלשהו.

ישנם $N + 1$ צבעים, ממוספרים מ-$0$ עד $N$.
הצבע $N$ מיוחד ונקרא **צבע הספינקס**.
לכל צומת יש צבע.
ספציפית, הצומת $i$ ($0 \le i \lt N$) הוא בצבע $C[i]$.
מספר צמתים יכולים להיות באותו הצבע, 
ויכולים להיות צבעים שלא מוקצים לאף צומת.
אף צומת הוא לא בצבע הספינקס,
 כלומר, $0 \le C[i] \lt N$ ($0 \le i \lt N$).

מסלול $v_0, v_1, \ldots, v_k$ (עבור $k \ge 0$)
 נקרא **חדגוני**
 אם כל הצמתים שלו הם באותו הצבע,
 כלומר $C[v_l] = C[v_{l+1}]$ (עבור כל $l$ שמקיים $0 \le l \lt k$).
בנוסף, נאמר שהצמתים $p$ ו-$q$ ($0 \le p \lt N$, $0 \le q \lt N$)
 הם באותו **הרכיב החדגוני**
 אם ורק אם הם מחוברים באמצעות מסלול חדגוני.

אתם יודעים את הצמתים ואת הקשתות,
 אבל אינכם יודעים באיזה צבע כל צומת.
אתם רוצים למצוא את הצבעים של הצמתים,
 על ידי ביצוע **ניסויי צביעה מחדש**.

בניסוי צביעה מחדש,
 אתם יכולים לצבוע מחדש מספר צמתים לבחירתכם.
ספציפית, כדי לבצע ניסוי צביעה מחדש,
 תחילה אתם בוחרים מערך $E$ באורך $N$,
 כאשר עבור כל $i$ ($0 \le i \lt N$),
  $E[i]$ הוא בין $-1$ לבין $N$ **כולל**.
לאחר מכן, הצבע של כל צומת $i$ הופך ל-$S[i]$, כשהערך של $S[i]$ הוא:
* $C[i]$, כלומר, הצבע המקורי של $i$, אם $E[i] = -1$, או
* $E[i]$, אחרת.

שימו לב שזה אומר שאתם יכולים להשתמש בצבע הספינקס בצביעה שלכם מחדש.

לבסוף, הספינקס הגדול מכריז
 על מספר הרכיבים החדגוניים בגרף,
 לאחר קביעת הצבע של כל צומת $i$ ל-$S[i]$ ($0 \le i \lt N$).
הצביעה החדשה מיושמת רק עבור ניסוי הצביעה מחדש הספציפי הזה,
 אז **הצבעים של כל הצמתים חוזרים להיות הצבעים המקוריים שלהם לאחר שהניסוים מסתיים**.

המשימה שלכם היא לזהות את הצבעים של הצמתים בגרף
 באמצעות ביצוע לכל היותר $2\,750$ ניסויי צביעה מחדש. 
אתם יכולים גם לקבל ניקוד חלקי
 אם אתם קובעים נכונה עבור כל זוג צמתים סמוכים,
 האם הם באותו הצבע.

## פרטי מימוש

עליכם לממש את הפונקציה הבאה.

```
std::vector&lt;int&gt; find_colours(int N,
    std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y)
```

* $N$: מספר הצמתים בגרף.
* $X$, $Y$: מערכים באורך $M$ המתארים את הקשתות.
* על פונקציה זו להחזיר מערך $G$ באורך $N$,
   המתאר את הצבעים של הצמתים בגרף.
* פונקציה זו תיקרא פעם אחת בדיוק בכל טסט.

הפונקציה לעיל יכולה לבצע קריאות לפונקציה הבאה
 כדי לבצע ניסויי צביעה מחדש:

```
int perform_experiment(std::vector&lt;int&gt; E)
```

* $E$: מערך באורך $N$ המתאר כיצד הצמתים צריכים להיצבע מחדש.
* פונקציה זו מחזירה את מספר הרכיבים החדגוניים
   לאחר צביעת הצמתים מחדש לפי $E$.
* ניתן לקרוא לפונקציה זו לכל היותר $2\,750$ פעמים.

הגריידר **אינו אדפטיבי**, כלומר,
 הצבעים של הצמתים נקבעים לפני שנעשית קריאה ל-`find_colours`.

## מגבלות

* $2 \le N \le 250$
* $N - 1 \le M \le \frac{N \cdot (N - 1)}{2}$
* $0 \le X[j] \lt Y[j] \lt N$ עבור כל $j$ שמקיים $0 \le j \lt M$.
* $X[j] \neq X[k]$ או $Y[j] \neq Y[k]$
   עבור כל $j$ ו-$k$ שמקיימים $0 \le j \lt k \lt M$.
* כל זוג צמתים מחובר באמצעות מסלול כלשהו.
* $0 \le C[i] \lt N$ עבור כל $i$ שמקיים $0 \le i \lt N$.

## תתי משימות

| מגבלות נוספות | ניקוד  | תת משימה |
| ----------------------: | :----: | :-----: |
| $N = 2$| $3$    | 1       
| $N \le 50$| $7$    | 2       
| .($0 \leq j < M$) הגרף הוא מסלול: $M = N - 1$ והצמתים $j$ ו-$j+1$ הם סמוכים | $33$   | 3       
| .הגרף הוא מלא: $M = \frac{N \cdot (N - 1)}{2}$ וכל זוג צמתים הם סמוכים| $21$   | 4       
| .ללא מגבלות נוספות| $36$   | 5       

בכל תת משימה, אתם יכולים להשיג ניקוד חלקי אם התוכנית שלכם קובעת בצורה נכונה לכל זוג צמתים סמוכים האם הם באותו צבע.

ליתר דיוק, אתם מקבלים את כל הניקוד בתת משימה, אם בכל הטסטים שלה, המערך $G$ שהוחזר על ידי `find_colours` הוא זהה בדיוק למערך $C$ (כלומר $C[i] = G[i]$ עבור כל $i$ שמקיים $0 \le i \lt N$). אחרת, אתם מקבלים $50\%$ מהניקוד של תת משימה אם התנאים הבאים מתקיימים בכל הטסטים שלה:
* $0 \le G[i] \lt N$ עבור כל $i$ שמקיים $0 \le i \lt N$;
* עבור כל $j$ שמקיים $0 \le j \lt M$:
  * $G[X[j]] = G[Y[j]]$ אם ורק אם $C[X[j]] = C[Y[j]]$.

## דוגמה

הביטו בקריאה הבאה.
```
find_colours(4, [0, 1, 0, 0], [1, 2, 2, 3])
```
עבור דוגמה זו, נניח שהצבעים (הנסתרים) של הצמתים נתונים על ידי $C = [2, 0, 0, 0]$.
תרחיש זה מוצג באיור הבא. הצבעים מיוצגים בנוסף באמצעות מספרים בתוויות לבנות המצורפות לכל צומת.

![example.png](sphinx_example.png "230")

הפונקציה יכולה לקרוא ל-`perform_experiment` באופן הבא.
```
perform_experiment([-1, -1, -1, -1])
```
בקריאה זו, אף צומת לא נצבע מחדש, וכל הצמתים שומרים על צבעם המקורי.

נתבונן בצומת $1$ ובצומת $2$. שניהם בצבע $0$ והמסלול $1, 2$ הוא מסלול חדגוני. כתוצאה מכך, צמתים $1$ ו-$2$ הם באותו הרכיב החדגוני. 

נתבונן בצומת $1$ ובצומת $3$. אף על פי ששניהם צבועים בצבע $0$, הם נמצאים בשני רכיבים חדגוניים שונים, מכיוון שאין מסלול חדגוני המחבר ביניהם.

סך הכול, ישנם $3$ רכיבים חדגוניים, עם הצמתים $\{0\}$, $\{1, 2\}$, ו-$\{3\}$.
לכן, הקריאה הזו מחזירה $3$.

כעת, הפונקציה יכולה לקרוא ל-`perform_experiment` באופן הבא.
```
perform_experiment([0, -1, -1, -1])
```
בקריאה זו, רק צומת $0$ נצבע מחדש לצבע $0$, מה שמוביל לצביעה המוצגת באיור הבא.

![example.png](sphinx_order1.png "230")

קריאה זו מחזירה $1$, מכיוון שכל הצמתים שייכים לאותו הרכיב החדגוני.
אנחנו יכולים להסיק כעת שצמתים $1$, $2$, ו-$3$ הם בצבע $0$.

הפונקציה יכולה לקרוא ל-`perform_experiment` באופן הבא.
```
perform_experiment([-1, -1, -1, 2])
```
בקריאה זו, צומת $3$ נצבע מחדש לצבע $2$,
מה שמוביל לצביעה המוצגת באיור הבא.

![example.png](sphinx_order2.png "230")

קריאה זו מחזירה $2$, מכיוון שיש $2$ רכיבים חדגוניים,
עם הצמתים $\{0, 3\}$ ו-$\{1, 2\}$ בהתאמה. אנחנו יכולים להסיק שצומת $0$ הוא בצבע $2$.

לאחר מכן הפונקציה `find_colours` מחזירה את המערך $[2, 0, 0, 0]$. מכיוון ש-$C = [2, 0, 0, 0]$, מתקבל ניקוד מלא.

שימו לב שיש גם מספר ערכי החזרה, עבורם $50\%$ מהניקוד יינתן, לדוגמה $[1, 2, 2, 2]$ או $[1, 2, 2, 3]$.

## גריידר לדוגמה

פורמט קלט:

```
N  M
C[0]  C[1] ... C[N-1]
X[0]  Y[0]
X[1]  Y[1]
...
X[M-1]  Y[M-1]
```
פורמט פלט:
```
L  Q
G[0]  G[1] ... G[L-1]
```
כאן, $L$ הוא אורך המערך $G$ שהוחזר על ידי `find_colours`,
ו-$Q$ הוא מספר הקריאות ל-`perform_experiment`.






