# Ιερογλυφικά

Μια ομάδα ερευνητών μελετά τις ομοιότητες μεταξύ ακολουθιών ιερογλυφικών.
Αναπαριστούν κάθε ιερογλυφικό με έναν μη αρνητικό ακέραιο.
Για να εκτελέσουν τη μελέτη τους,
 χρησιμοποιούν τις ακόλουθες έννοιες σχετικά με τις ακολουθίες.

Για μια σταθερή ακολουθία $A$,
 μια ακολουθία $S$ ονομάζεται **υποακολουθία** της $A$
 αν και μόνο αν η $S$ μπορεί να προκύψει
 αφαιρώντας κάποια στοιχεία (ενδεχομένως κανένα) από την $A$.

Ο παρακάτω πίνακας δείχνει μερικά παραδείγματα υποακολουθιών της ακολουθίας $A = [3, 2, 1, 2]$.

| Υποακολουθία   | Πώς μπορεί να προκύψει από την $A$ |
|----------------|------------------------------------|
| [3, 2, 1, 2]   | Δεν αφαιρούνται στοιχεία.
| [2, 1, 2]      | [<s>3</s>, 2, 1, 2]
| [3, 2, 2]      | [3, 2, <s>1</s>, 2]
| [3, 2]         | [3, <s>2</s>, <s>1</s>, 2] ή [3, 2, <s>1</s>, <s>2</s>]
| [3]            | [3, <s>2</s>, <s>1</s>, <s>2</s>]
| [ ]            | [<s>3</s>, <s>2</s>, <s>1</s>, <s>2</s>]

Από την άλλη, το $[3, 3]$ ή το $[1, 3]$ δεν είναι υποακολουθίες της $A$.

Σκεφτείτε δύο ακολουθίες ιερογλυφικών, $A$ και $B$.
Μια ακολουθία $S$ ονομάζεται **κοινή υποακολουθία** των $A$ και $B$
 αν και μόνο αν η $S$ είναι υποακολουθία και των δύο $A$ και $B$.
Επιπλέον, λέμε ότι μια ακολουθία $U$ είναι **καθολική κοινή υποακολουθία** των $A$ και $B$
 αν και μόνο αν ισχύουν οι ακόλουθες δύο συνθήκες:
* Η $U$ είναι κοινή υποακολουθία των $A$ και $B$.
* Κάθε κοινή υποακολουθία των $A$ και $B$ είναι επίσης υποακολουθία της $U$.

Μπορεί να αποδειχθεί ότι κάθε δύο ακολουθίες $A$ και $B$
 έχουν το πολύ μία καθολική κοινή υποακολουθία.

Οι ερευνητές βρήκαν δύο ακολουθίες ιερογλυφικών $A$ και $B$.
Η ακολουθία $A$ αποτελείται από $N$ ιερογλυφικά
 και η ακολουθία $B$ αποτελείται από $M$ ιερογλυφικά.
Βοηθήστε τους ερευνητές να υπολογίσουν
 μια καθολική κοινή υποακολουθία των ακολουθιών $A$ και $B$,
 ή να καθορίσουν ότι μια τέτοια ακολουθία δεν υπάρχει.

## Λεπτομέρειες Υλοποίησης

Πρέπει να υλοποιήσετε την ακόλουθη διαδικασία.

```
std::vector&lt;int&gt; ucs(std::vector&lt;int&gt; A, std::vector&lt;int&gt; B)
```

* $A$: πίνακας μήκους $N$ που περιγράφει την πρώτη ακολουθία.
* $B$: πίνακας μήκους $M$ που περιγράφει τη δεύτερη ακολουθία.
* Αν υπάρχει μια καθολική κοινή υποακολουθία των $A$ και $B$,
   η διαδικασία πρέπει να επιστρέψει έναν πίνακα που περιέχει αυτή την ακολουθία.
  Διαφορετικά, η διαδικασία πρέπει να επιστρέψει $[-1]$
   (ένας πίνακας μήκους $1$, του οποίου το μοναδικό στοιχείο είναι $-1$).
* Αυτή η διαδικασία καλείται ακριβώς μία φορά για κάθε δοκιμαστική περίπτωση.

## Περιορισμοί

* $1 \leq N \leq 100\,000$
* $1 \leq M \leq 100\,000$
* $0 \leq A[i] \leq 200\,000$ για κάθε $i$ τέτοιο ώστε $0 \leq i < N$
* $0 \leq B[j] \leq 200\,000$ για κάθε $j$ τέτοιο ώστε $0 \leq j < M$

## Subtasks

| Subtask | Βαθμολογία | Επιπλέον Περιορισμοί      |
| :--------: | :--------: | ------------------------- |
| 1          | $3$        | $N = M$; $A$ και $B$ αποτελούνται και οι δύο από $N$ *διακριτούς* ακέραιους μεταξύ $0$ και $N-1$ (συμπεριλαμβανομένων)
| 2          | $15$       | Για οποιονδήποτε ακέραιο $k$, (ο αριθμός των στοιχείων του $A$ ίσος με $k$) συν (τον αριθμό των στοιχείων του $B$ ίσος με $k$) είναι το πολύ $3$.
| 3          | $10$       | $A[i] \leq 1$ για κάθε $i$ τέτοιο ώστε $0 \leq i < N$; $B[j] \leq 1$ για κάθε $j$ τέτοιο ώστε $0 \leq j < M$
| 4          | $16$       | Υπάρχει μια καθολική κοινή υποακολουθία των $A$ και $B$.
| 5          | $14$       | $N \leq 3000$; $M \leq 3000$
| 6          | $42$       | Χωρίς επιπλέον περιορισμούς.

## Παραδείγματα

### Παράδειγμα 1

Σκεφτείτε την ακόλουθη κλήση.

```
ucs([0, 0, 1, 0, 1, 2], [2, 0, 1, 0, 2])
```

Εδώ, οι κοινές υποακολουθίες των $A$ και $B$ είναι οι εξής:
 $[\ ]$, $[0]$, $[1]$, $[2]$, $[0, 0]$, $[0, 1]$, $[0, 2]$, $[1, 0]$, $[1, 2]$, $[0, 0, 2]$, $[0, 1, 0]$, $[0, 1, 2]$, $[1, 0, 2]$ και $[0, 1, 0, 2]$.

Εφόσον το $[0, 1, 0, 2]$ είναι κοινή υποακολουθία των $A$ και $B$, και
 όλες οι κοινές υποακολουθίες των $A$ και $B$ είναι υποακολουθίες του $[0, 1, 0, 2]$,
 η διαδικασία πρέπει να επιστρέψει $[0, 1, 0, 2]$.

### Παράδειγμα 2

Σκεφτείτε την ακόλουθη κλήση.

```
ucs([0, 0, 2], [1, 1])
```

Εδώ, η μόνη κοινή υποακολουθία των $A$ και $B$ είναι η κενή ακολουθία $[\ ]$.
Συνεπώς, η διαδικασία πρέπει να επιστρέψει έναν κενό πίνακα $[\ ]$.

### Παράδειγμα 3

Σκεφτείτε την ακόλουθη κλήση.
```
ucs([0, 1, 0], [1, 0, 1])
```

Εδώ, οι κοινές υποακολουθίες των $A$ και $B$ είναι
 $[\ ], [0], [1], [0, 1]$ και $[1, 0]$.
Μπορεί να αποδειχθεί ότι δεν υπάρχει καθολική κοινή υποακολουθία.
Επομένως, η διαδικασία πρέπει να επιστρέψει $[-1]$.

## Sample Grader

Μορφή εισόδου:

```
N

  M
A[0]  A[1]  ...  A[N-1]
B[0]  B[1]  ...  B[M-1]
```

Μορφή εξόδου:

```
T
R[0]  R[1]  ...  R[T-1]
```

Εδώ, το $R$ είναι ο πίνακας που επιστρέφεται από την `ucs` και το $T$ είναι το μήκος του.