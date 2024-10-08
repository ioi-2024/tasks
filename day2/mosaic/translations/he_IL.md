# פסיפס

סאלמה מתכננת לצבוע פסיפס חרס על קיר.
הפסיפס הוא גריד $N \times N$, המורכב מ-$N^2$ אריחי $1 \times 1$ ריבועיים שתחילה אינם צבועים. 
השורות של הפסיפס ממוספרות מ-$0$ עד $N-1$ מלמעלה למטה, והעמודות ממוספרות מ-$0$ עד $N-1$ משמאל לימין.
האריח בשורה $i$ ובעמודה $j$ ($0 \leq i < N$, $0 \leq j < N$) מסומן על ידי $(i,j)$.
כל אריח חייב להיות צבוע או בלבן (מיוצג על ידי $0$) או בשחור (מיוצג על ידי $1$).

כדי לצבוע את הפסיפס, ראשית סאלמה בוחרת שני מערכים $X$ ו-$Y$ באורך $N$, המורכבים מהערכים $0$ ו-$1$, כך ש-$X[0] = Y[0]$. 
היא צובעת את האריחים של השורה העליונה ביותר (שורה $0$) לפי המערך $X$, כך שהצבע של האריח $(0,j)$ הוא $X[j]$ ($0 \leq j < N$).
בנוסף, היא צובעת את האריחים של העמודה השמאלית ביותר (עמודה $0$) על פי המערך $Y$, כך שהצבע של האריח $(i,0)$ הוא $Y[i]$ ($0 \leq i < N$).

אחר כך, היא חוזרת על הצעדים הבאים עד שכל האריחים צבועים:
* היא מוצאת אריח $(i,j)$ כלשהו *שאינו צבוע* כך שהשכן שלו מלמעלה (אריח $(i-1, j)$) והשכן שלו משמאל (אריח $(i, j-1)$) שניהם *כבר צבועים*.
* אחר כך, היא צובעת את אריח $(i,j)$ בשחור אם שני השכנים האלו לבנים; אחרת, היא צובעת את אריח $(i, j)$ בלבן.

ניתן להראות שהצבעים הסופיים של האריחים לא תלויים בסדר בו סאלמה צובעת אותם.
 
יסמין מאוד סקרנית לגבי צבעי האריחים בפסיפס. 
היא שואלת את סאלמה $Q$ שאילתות, ממוספרות מ-$0$ עד $Q-1$.
בשאילתה $k$ ($0 \leq k < Q$),
יסמין מציינת תת מלבן מהפסיפס על ידי:
* השורה העליונה ביותר שלו $T[k]$ והשורה התחתונה ביותר שלו $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* העמודה השמאלית ביותר שלו $L[k]$ והעמודה הימנית ביותר שלו $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

התשובה לשאילתה היא מספר האריחים השחורים בתת מלבן זה.
ספציפית, סאלמה צריכה למצוא כמה אריחים $(i, j)$ קיימים, כך ש-$T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$,
ושהצבע של אריח $(i,j)$ הוא שחור.

כתבו תוכנית שעונה על השאילתות של יסמין.
<br><br><br><br><br><br>

## פרטי מימוש

עליכם לממש את הפונקציה הבאה:

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: מערכים באורך $N$ המתארים את צבעי האריחים בשורה העליונה ביותר ובעמודה השמאלית ביותר, בהתאמה.
* $T$, $B$, $L$, $R$: מערכים באורך $Q$ המתארים את השאילתות שנשאלות על ידי יסמין.
* על הפונקציה להחזיר מערך $C$ באורך $Q$,
 כך ש-$C[k]$ מספק את התשובה לשאילתה $k$ ($0 \leq k < Q$).
* פונקציה זו תיקרא פעם אחת בדיוק בכל טסט.

## מגבלות

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ וגם $Y[i] \in \{0, 1\}$
 עבור כל $i$ שמקיים $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ וגם $0 \leq L[k] \leq R[k] < N$
 עבור כל $k$ שמקיים $0 \leq k < Q$

## תתי משימות

| מגבלות נוספות | ניקוד  | תת משימה |
| ----------------------: | :----: | :-----: |
| $Q \leq 10; N \leq 2$| $5$    | 1       
| $Q \leq 200; N \leq 200$| $7$    | 2       
|  ($0 \leq k < Q$ עבור כל $k$ שמקיים) $T[k] = B[k] = 0$| $7$    | 3       
| $N \leq 5000$| $10$   | 4       
|  ($0 \leq i < N$ עבור כל $i$ שמקיים) $X[i] = Y[i] = 0$| $8$    | 5       
|  וגם $L[k] = R[k]$ (עבור כל $k$ שמקיים $0 \leq k < Q$) $T[k] = B[k]$| $22$   | 6       
| ($0 \leq k < Q$ עבור כל $k$ שמקיים) $T[k] = B[k]$ | $19$   | 7       
|.ללא מגבלות נוספות| $22$   | 8        

<br><br>

## דוגמה

הביטו בקריאה הבאה.

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

דוגמה זו מומחשת בתמונות למטה.
התמונה השמאלית מציגה את הצבעים של האריחים בפסיפס.
התמונות האמצעית והימנית מציגות את תת המלבנים 
שיסמין שאלה עליהם בשאילתות הראשונה והשנייה, בהתאמה.

![](example.png "550")

התשובות לשאילתות
 (כלומר, כמות האחדות במלבנים המוצללים)
 הן 7 ו-3, בהתאמה.
לכן, על הפונקציה להחזיר $[7, 3]$.

## גריידר לדוגמה

פורמט קלט:

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

פורמט פלט:

```
C[0]
C[1]
...
C[S-1]
```

כאן, $S$ הוא אורך המערך $C$ המוחזר על ידי `mosaic`.




