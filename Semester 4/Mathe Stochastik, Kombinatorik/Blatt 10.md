## Aufgabe 3
### a)
$$\begin{align}
&P((X_1 + X_2) \cdot (X_1 - X_2) = 35) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = 32) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = 27) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = 24) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = 21) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = 20) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = 16) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = 15) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = 12) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = 11) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = 9) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = 8) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = 7) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = 5) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = 3) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = 0) = \frac{6}{36} = \frac{1}{6} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = -3) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = -5) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = -7) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = -8) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = -9) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = -11) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = -12) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = -15) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = -16) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = -20) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = -21) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = -24) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = -27) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = -32) = \frac{1}{36} \\
&P((X_1 + X_2) \cdot (X_1 - X_2) = -35) = \frac{1}{36} \\
\end{align}$$
### b)
**Erwartungswerte**
$$E(X_1)=\frac{1+2+3+4+5+6}{6}=\frac{21}{6}=3.5$$
$$E(X_2)=\frac{1+2+3+4+5+6}{6}=\frac{21}{6}=3.5$$
$$E(X_1 + X_2)=3.5 + 3.5 = 7$$
$$E(X_1 - X_2)=3.5 - 3.5 = 0$$
$$E((X_1 + X_2) \cdot (X_1 - X_2))=E(X_1 + X_2) \cdot E(X_1 - X_2)$$
$$E((X_1 + X_2) \cdot (X_1 - X_2)) = 7 \cdot 0 = 0$$
**Covarianz**
$$Cov((X_1 + X_2)​,(X_1 - X_2)​) = E(Y_1​\cdot Y_2​)-E(Y_1​)\cdot E(Y_2​)$$
$$Cov((X_1 + X_2)​,(X_1 - X_2)​) = 0 - 7 \cdot 0 = 0$$
Covarianz, $Cov(X_1 + X_2, X_1 − X_2)$ beträgt $0$.
## Aufgabe 4

![[Pasted image 20240702132142.png]]

Wie in dem Baum zu sehen ist gewinnt man in 2 von 3 Fällen falls man sich entscheidet die Tür zu wechseln. Wenn man sich dazu entscheidet nicht zu wechseln gewinnt man in 1 von 3 Fällen somit kommen wir auf folgende Wahrscheinlichkeiten:
Mit Wechseln: $\frac{2}{3}$
Ohne Wechseln: $\frac{1}{3}$
## Aufgabe 4

```python
import random

def game(change):
    car_pos = random.randint(1, 3)
    player_door = random.randint(1, 3)

    if change:
        rest_doors = [1,2,3]
        if car_pos != player_door:
            rest_doors.remove(car_pos)
            rest_doors.remove(player_door)
        else:
            rest_doors.remove(car_pos)

        mod_door = random.choice(rest_doors)
        rest_doors = [1,2,3]
        rest_doors.remove(player_door)
        rest_doors.remove(mod_door)
        player_door = random.choice(rest_doors)
        
    if car_pos == player_door:
        return 1
    else:
        return 0

trials = input("Anzahl der Durchläufe: ")
n = int(trials)
win_change = 0
win_no_change = 0
for i in range(n):
    win_change += game(True)
    win_no_change += game(False)

print("Bei", n, "Durchläufen haben wir Folgedende Gewinnwahrscheinlichkeiten:")
print("Mit Wechsel:", win_change/n)
print("Ohne Wechsel:", win_no_change/n)
```

**Eingabe:** $n=1000000$
**Ausgabe:** 
Mit Wechsel: $0.666044 \approx \frac{2}{3}$
Ohne Wechsel: $0.332778 \approx \frac{1}{3}$

```shell
Anzahl der Durchläufe: 1000000
Bei 1000000 Durchläufen haben wir Folgedende Gewinnwahrscheinlichkeiten:
Mit Wechsel: 0.666044
Ohne Wechsel: 0.332778
```