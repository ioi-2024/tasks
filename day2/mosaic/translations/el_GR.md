# Ψηφιδωτό

Η Σάλμα σχεδιάζει να χρωματίσει ένα πήλινο ψηφιδωτό σε έναν τοίχο.
Το ψηφιδωτό είναι ένα πλέγμα $N \times N$, 
αποτελούμενο από $N^2$ αρχικά άβαφα πλακίδια $1 \times 1$.
Οι σειρές του ψηφιδωτού αριθμούνται από το $0$ έως το $N-1$ από πάνω προς τα κάτω,
και οι στήλες αριθμούνται από το $0$ έως το $N-1$ από αριστερά προς τα δεξιά.
Το πλακίδιο στη σειρά $i$ και στήλη $j$ ($0 \leq i < N$, $0 \leq j < N$) σημειώνεται ως $(i,j)$.
Κάθε πλακίδιο πρέπει να χρωματιστεί είτε
λευκό (σημειώνεται με $0$) είτε μαύρο (σημειώνεται με $1$).

Για να χρωματίσει το ψηφιδωτό, η Σάλμα πρώτα επιλέγει δύο πίνακες $X$ και $Y$ μήκους $N$,
κάθε ένας από τους οποίους αποτελείται από τιμές $0$ και $1$, έτσι ώστε $X[0] = Y[0]$.
Χρωματίζει τα πλακίδια της επάνω σειράς (σειρά $0$) σύμφωνα με τον πίνακα $X$,
έτσι ώστε το χρώμα του πλακιδίου $(0,j)$ να είναι $X[j]$ ($0 \leq j < N$).
Επίσης, χρωματίζει τα πλακίδια της αριστερότερης στήλης (στήλη $0$) σύμφωνα με τον πίνακα $Y$,
έτσι ώστε το χρώμα του πλακιδίου $(i,0)$ να είναι $Y[i]$ ($0 \leq i < N$).

Στη συνέχεια, επαναλαμβάνει τα εξής βήματα μέχρι όλα τα πλακίδια να χρωματιστούν:
* Βρίσκει ένα *άβαφο* πλακίδιο $(i,j)$ τέτοιο ώστε
 ο πάνω γείτονάς του (πλακίδιο $(i-1, j)$) και ο αριστερός γείτονάς του (πλακίδιο $(i, j-1)$)
 να είναι και οι δύο *ήδη χρωματισμένοι*.
* Έπειτα, χρωματίζει το πλακίδιο $(i,j)$ μαύρο εάν και οι δύο αυτοί γείτονες είναι λευκοί·
διαφορετικά, χρωματίζει το πλακίδιο $(i,j)$ λευκό.

Μπορεί να αποδειχθεί ότι τα τελικά χρώματα των πλακιδίων δεν εξαρτώνται
από τη σειρά με την οποία η Σάλμα τα χρωματίζει.

Η Γιασμίν είναι πολύ περίεργη για τα χρώματα των πλακιδίων στο ψηφιδωτό.
Ρωτάει τη Σάλμα $Q$ ερωτήσεις, αριθμημένες από το $0$ έως το $Q-1$.
Στην ερώτηση $k$ ($0 \leq k < Q$),
η Γιασμίν καθορίζει ένα υποορθογώνιο του ψηφιδωτού με τα:
* Την ανώτερη σειρά $T[k]$ και την κατώτερη σειρά $B[k]$ ($0 \leq T[k] \leq B[k] < N$),
* Την αριστερότερη στήλη $L[k]$ και τη δεξιότερη στήλη $R[k]$ ($0 \leq L[k] \leq R[k] < N$).

Η απάντηση στην ερώτηση είναι ο αριθμός των μαύρων πλακιδίων σε αυτό το υποορθογώνιο.
Συγκεκριμένα, η Σάλμα πρέπει να βρει πόσα πλακίδια $(i, j)$ υπάρχουν,
ώστε $T[k] \leq i \leq B[k]$, $L[k] \leq j \leq R[k]$,
και το χρώμα του πλακιδίου $(i,j)$ να είναι μαύρο.

Γράψτε ένα πρόγραμμα που απαντά στις ερωτήσεις της Γιασμίν.

## Λεπτομέρειες Υλοποίησης

Πρέπει να υλοποιήσετε την ακόλουθη διαδικασία.

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: πίνακες μήκους $N$ που περιγράφουν τα χρώματα των πλακιδίων
στην επάνω σειρά και την αριστερότερη στήλη, αντίστοιχα.
* $T$, $B$, $L$, $R$: πίνακες μήκους $Q$ που περιγράφουν τις ερωτήσεις της Γιασμίν.
* Η διαδικασία πρέπει να επιστρέψει έναν πίνακα $C$ μήκους $Q$,
ώστε $C[k]$ να παρέχει την απάντηση στην ερώτηση $k$ ($0 \leq k < Q$).
* Αυτή η διαδικασία καλείται ακριβώς μία φορά για κάθε δοκιμαστική περίπτωση.

## Περιορισμοί

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $X[i] \in \{0, 1\}$ και $Y[i] \in \{0, 1\}$
για κάθε $i$ έτσι ώστε $0 \leq i < N$
* $X[0] = Y[0]$
* $0 \leq T[k] \leq B[k] < N$ και $0 \leq L[k] \leq R[k] < N$
για κάθε $k$ έτσι ώστε $0 \leq k < Q$

## Subtasks

| Subtask | Βαθμολογία | Πρόσθετοι Περιορισμοί |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ (για κάθε $k$ έτσι ώστε $0 \leq k < Q$)
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ (για κάθε $i$ έτσι ώστε $0 \leq i < N$)
| 6       | $22$   | $T[k] = B[k]$ και $L[k] = R[k]$ (για κάθε $k$ έτσι ώστε $0 \leq k < Q$)
| 7       | $19$   | $T[k] = B[k]$ (για κάθε $k$ έτσι ώστε $0 \leq k < Q$)
| 8       | $22$   | Χωρίς πρόσθετους περιορισμούς.

## Παράδειγμα

Εξετάστε την ακόλουθη κλήση.

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

Αυτό το παράδειγμα απεικονίζεται στις παρακάτω εικόνες.
Η αριστερή εικόνα δείχνει τα χρώματα των πλακιδίων στο ψηφιδωτό.
Οι μεσαίες και δεξιές εικόνες δείχνουν τα υποορθογώνια
για τα οποία η Γιασμίν ρώτησε στην πρώτη και δεύτερη ερώτηση, αντίστοιχα.

![](example.png "550")

Οι απαντήσεις στις ερωτήσεις
(δηλαδή, οι αριθμοί των μονάδων στα σκιασμένα ορθογώνια)
είναι 7 και 3, αντίστοιχα.
Επομένως, η διαδικασία πρέπει να επιστρέψει $[7, 3]$.

## Sample Grader

Μορφή εισόδου:

```
N
X[0]  X[1]  ...  X[N-1]
Y[0]  Y[1]  ...  Y[N-1]
Q
T[0]  B[0]  L[0]  R[0]
T[1]  B[1]  L[1]  R[1]
...
T[Q-1]

  B[Q-1]  L[Q-1]  R[Q-1]
```

Μορφή εξόδου:

```
C[0]
C[1]
...
C[S-1]
```

Εδώ, $S$ είναι το μήκος του πίνακα $C$ που επιστρέφεται από τη `mosaic`.