## Aufgabe 2
### a)

| Würfel                                                         | Ergebnis |
| -------------------------------------------------------------- | -------- |
| 5 + 2 = 7                                                      | +1€      |
| 4 + 3 = 7                                                      | +1€      |
| 1 + 6 = 7                                                      | +1€      |
| 3 + 1 = 4<br>5 + 1 = 6<br>5 + 5 = 10<br>6 + 2 = 8<br>2 + 2 = 4 | +1€      |
| 2 + 3 = 5<br>6 + 1 = 7                                         | -1€      |
| 4 + 1 = 5<br>2 + 3 = 5                                         | +1€      |
| 2 + 4 = 6<br>4 + 6 = 10<br>5 + 2 = 7                           | -1€      |
| 5 + 3 = 8<br>2 + 4 = 6<br>5 + 2 = 7                            | -1€      |
| 3 + 1 = 4<br>1 + 2 = 3<br>4 + 1 = 5<br>6 + 3 = 9<br>1 + 3 = 4  | +1€      |
| 5 + 4 = 9<br>4 + 2 = 6<br>6 + 5 = 11<br>1 + 4 = 5<br>5 + 4 = 9 | +1€      |
Bei $N=10$ Durchläufen habe ich $+4$€, mein Mittlerer Gewinn:
$$\frac{1+1+1+1-1+1-1-1+1+1}{10} = \frac{2}{5} = 0.4\text{€}$$
### b)

```python
import random

def roll_dice():
    return random.randint(1,6) + random.randint(1,6)

def game():
    roll = roll_dice()
    if roll == 7 or roll == 11:
        return 1
    elif roll == 2 or roll == 3 or roll == 12:
        return -1
    else:
        s = roll
        while True:
            roll = roll_dice()
            if roll == 7:
                return -1
            elif roll == s:
                return 1

account = 0
N = int(input("Eingabe von N: "))
for i in range(N):
    account += game()
win_value = account / N
print("Unser Konto beträgt nach", N, "Durchläufen", str(account) + "€, mit einem mittleren Gewinn von", win_value)
```

**Eingabe:** $N=1000$
**Ausgabe:** 
```shell
Eingabe von N: 1000 
Unser Konto beträgt nach 1000 Durchläufen -4€, mit einem mittleren Gewinn von -0.004
```

## Aufgabe 3
### a)

![[wahrscheinlichkeitsbaum.png]]
### b)
**Erster Wurf**
$$\frac{8}{36} \cdot 1 + \frac{4}{36} \cdot - 1 = \frac{1}{9}$$
**Weitere Würfe**
$S=4$:
$$(\frac{3}{36} + \frac{3}{36}) \cdot 1 + (\frac{3}{36} + \frac{6}{36}) \cdot - 1 = -\frac{1}{12}$$
$S=5$:
$$(\frac{4}{36} + \frac{4}{36}) \cdot 1 + (\frac{4}{36} + \frac{6}{36}) \cdot - 1 = -\frac{1}{18}$$
$S=6$:
$$(\frac{5}{36} + \frac{5}{36}) \cdot 1 + (\frac{5}{36} + \frac{6}{36}) \cdot - 1 = -\frac{1}{36}$$
$S=8$:
$$(\frac{5}{36} + \frac{5}{36}) \cdot 1 + (\frac{5}{36} + \frac{6}{36}) \cdot - 1 = -\frac{1}{36}$$
$S=9$:
$$(\frac{4}{36} + \frac{4}{36}) \cdot 1 + (\frac{4}{36} + \frac{6}{36}) \cdot - 1 = -\frac{1}{18}$$
$S=10$:
$$(\frac{3}{36} + \frac{3}{36}) \cdot 1 + (\frac{3}{36} + \frac{6}{36}) \cdot - 1 = -\frac{1}{12}$$
**Gesamt**
$$\begin{align}
&\frac{1}{9} + -\frac{1}{12} + -\frac{1}{18} + -\frac{5}{36} + -\frac{5}{36} + -\frac{1}{18} + -\frac{1}{12} \\
=& -\frac{4}{9}=-0.\overline{4}
\end{align}$$
