
>Jannis Lauterbach, Eric Schneider, Marcel Wirdel
## Aufgabe 1
### a)

```python
def variationen(z, zz, aktuelle_variation, k):
    if z == 0 and zz == 0:
        print(aktuelle_variation)
    else:
        if z > 0:
            variationen(z - 1, zz, aktuelle_variation + [10], k + 10)
        if zz > 0 and (k > 0):
            variationen(z, zz - 1, aktuelle_variation + [20], k - 10)

zehner = int(input("Anzahl Zehner: "))
zwanzig = int(input("Anzahl Zwanziger: "))
kasse = 0
aktuelle_variation = []
print("Es gibt folgende möglichen Reihenfolgen:")
variationen(zehner, zwanzig, aktuelle_variation, kasse)
```

**Eingabe:** $zehner=4,\ zwanziger=3$
**Ausgabe:**
```shell
Anzahl Zehner: 4
Anzahl Zwanziger: 3
Es gibt folgende Reihenfolgen:
[10, 10, 10, 10, 20, 20, 20]
[10, 10, 10, 20, 10, 20, 20]
[10, 10, 10, 20, 20, 10, 20]
[10, 10, 10, 20, 20, 20, 10]
[10, 10, 20, 10, 10, 20, 20]
[10, 10, 20, 10, 20, 10, 20]
[10, 10, 20, 10, 20, 20, 10]
[10, 10, 20, 20, 10, 10, 20]
[10, 10, 20, 20, 10, 20, 10]
[10, 20, 10, 10, 10, 20, 20]
[10, 20, 10, 10, 20, 10, 20]
[10, 20, 10, 10, 20, 20, 10]
[10, 20, 10, 20, 10, 10, 20]
[10, 20, 10, 20, 10, 20, 10]
```

Es gibt folgende 14 mögliche Reihenfolgen:
$$\begin{align}
&[10, 10, 10, 10, 20, 20, 20] \\
&[10, 10, 10, 20, 10, 20, 20] \\
&[10, 10, 10, 20, 20, 10, 20] \\
&[10, 10, 10, 20, 20, 20, 10] \\
&[10, 10, 20, 10, 10, 20, 20] \\
&[10, 10, 20, 10, 20, 10, 20] \\
&[10, 10, 20, 10, 20, 20, 10] \\
&[10, 10, 20, 20, 10, 10, 20] \\
&[10, 10, 20, 20, 10, 20, 10] \\
&[10, 20, 10, 10, 10, 20, 20] \\
&[10, 20, 10, 10, 20, 10, 20] \\
&[10, 20, 10, 10, 20, 20, 10] \\
&[10, 20, 10, 20, 10, 10, 20] \\
&[10, 20, 10, 20, 10, 20, 10] \\
\end{align}$$


### b)
Wir wissen schon das $\dbinom{n+m}{n}$ die Anzahl der kürzesten Wege zurück gibt also müssen wir nur noch Beweisen das $\dbinom{n+m}{n+1}$ die Anzahl der unsicheren Wege ist. 

---
## Aufgabe 2

Identität:
$$\begin{pmatrix} 1&2&3&4&5\\1&2&3&4&5 \end{pmatrix}$$
Spiegelung an Punkt 1:
$$\begin{pmatrix} 1&2&3&4&5\\1&5&4&3&2 \end{pmatrix}$$
Spiegelung an Punkt 2:
$$\begin{pmatrix} 1&2&3&4&5\\3&2&1&5&4 \end{pmatrix}$$
Spiegelung an Punkt 3:
$$\begin{pmatrix} 1&2&3&4&5\\5&4&3&2&1 \end{pmatrix}$$
Spiegelung an Punkt 4:
$$\begin{pmatrix} 1&2&3&4&5\\2&1&5&4&3 \end{pmatrix}$$
Spiegelung an Punkt 5:
$$\begin{pmatrix} 1&2&3&4&5\\4&3&2&1&5 \end{pmatrix}$$
Drehung um $72\degree$ 
$$\begin{pmatrix} 1&2&3&4&5\\2&3&4&5&1 \end{pmatrix}$$
Drehung um $144\degree$
$$\begin{pmatrix} 1&2&3&4&5\\3&4&5&1&2 \end{pmatrix}$$
Drehung um $216\degree$
$$\begin{pmatrix} 1&2&3&4&5\\4&5&1&2&3 \end{pmatrix}$$
Drehung um $288\degree$
$$\begin{pmatrix} 1&2&3&4&5\\5&1&2&3&4 \end{pmatrix}$$

---
## Aufgabe 3
### a)

Man hat mit $4$ verschiedenen Briefen und $4$ Adressaten $24$ verschiedene Möglichkeiten die Briefe zu versenden. Davon sind $9$ Kombinationen so angeordnet das kein Empfänger den richtigen Brief bekommt. Also hat man eine Wahrscheinlichkeit von $\frac{9}{24}=37,5\%$      

### b)

---
## Aufgabe 4
### a)
Um eine positive Gewinnwahrscheinlichkeit zu erreichen muss mindestens $6$ mal gewürfelt werden, $n$ muss mindestens $6$ sein.
Die Gewinnwahrscheinlichkeit bei $n=6$ liegt bei:
$$\frac{6}{6}\cdot\frac{5}{6}\cdot\frac{4}{6}\cdot\frac{3}{6}\cdot\frac{2}{6}\cdot\frac{1}{6}=\frac{5}{324}$$
### c)
Damit die Bank den Vorteil behält darf die Anzahl der Würfe nicht größer als $12$ sein.
```python
import random

def play(n):
    zahlen = [0,0,0,0,0,0]
    gefunden = 0
    for i in range(n):
        n = random.randrange(1, 7)
        if zahlen[n-1] == 0:
            zahlen[n-1] = 1
            gefunden += 1
        if gefunden == 6:
            return 1
    return 0

def durchlauf(n):
    gewinner = 0
    for i in range(100000):
        gewinner += play(n)
    durchschnitt = gewinner/100000
    return durchschnitt
  
würfe = 6
chance = 0
while chance < 0.5:
    würfe += 1
    chance = durchlauf(würfe)
    print("Die Gewinnwahrscheinlichkeit beträgt: " + str(chance))

print("Die maximalen Würfe zum Vorteil der Bank sind: " + str(würfe-2))
```

**Ausgabe:**
```shell
Die Gewinnwahrscheinlichkeit für 6 Würfe beträgt: 0.01564
Die Gewinnwahrscheinlichkeit für 7 Würfe beträgt: 0.05388
Die Gewinnwahrscheinlichkeit für 8 Würfe beträgt: 0.11363
Die Gewinnwahrscheinlichkeit für 9 Würfe beträgt: 0.18958
Die Gewinnwahrscheinlichkeit für 10 Würfe beträgt: 0.27025
Die Gewinnwahrscheinlichkeit für 11 Würfe beträgt: 0.35438
Die Gewinnwahrscheinlichkeit für 12 Würfe beträgt: 0.43575
Die Gewinnwahrscheinlichkeit für 13 Würfe beträgt: 0.51233
Die maximalen Würfe zum Vorteil der Bank sind: 12
```

---
## Aufgabe 5
### a)

```python
def wege(n, m, aktueller_weg):
    if n == 0 and m == 0:
        print(aktueller_weg)
    else:
        if n > 0:
            wege(n - 1, m, aktueller_weg + [1])
        if m > 0:
            wege(n, m - 1, aktueller_weg + [0])

n = int(input("Eingabe von n: "))
m = int(input("Eingabe von m: "))
aktueller_weg = []
print("Es gibt folgende kürzeste Wege:")
wege(n, m, aktueller_weg)
```

**Eingabe:** $n=4,\ m=3$
**Ausgabe:**
```shell
Eingabe von n: 4
Eingabe von m: 3
Es gibt folgende kürzeste Wege:
[1, 1, 1, 1, 0, 0, 0]
[1, 1, 1, 0, 1, 0, 0]
[1, 1, 1, 0, 0, 1, 0]
[1, 1, 1, 0, 0, 0, 1]
[1, 1, 0, 1, 1, 0, 0]
[1, 1, 0, 1, 0, 1, 0]
[1, 1, 0, 1, 0, 0, 1]
[1, 1, 0, 0, 1, 1, 0]
[1, 1, 0, 0, 1, 0, 1]
[1, 1, 0, 0, 0, 1, 1]
[1, 0, 1, 1, 1, 0, 0]
[1, 0, 1, 1, 0, 1, 0]
[1, 0, 1, 1, 0, 0, 1]
[1, 0, 1, 0, 1, 1, 0]
[1, 0, 1, 0, 1, 0, 1]
[1, 0, 1, 0, 0, 1, 1]
[1, 0, 0, 1, 1, 1, 0]
[1, 0, 0, 1, 1, 0, 1]
[1, 0, 0, 1, 0, 1, 1]
[1, 0, 0, 0, 1, 1, 1]
[0, 1, 1, 1, 1, 0, 0]
[0, 1, 1, 1, 0, 1, 0]
[0, 1, 1, 1, 0, 0, 1]
[0, 1, 1, 0, 1, 1, 0]
[0, 1, 1, 0, 1, 0, 1]
[0, 1, 1, 0, 0, 1, 1]
[0, 1, 0, 1, 1, 1, 0]
[0, 1, 0, 1, 1, 0, 1]
[0, 1, 0, 1, 0, 1, 1]
[0, 1, 0, 0, 1, 1, 1]
[0, 0, 1, 1, 1, 1, 0]
[0, 0, 1, 1, 1, 0, 1]
[0, 0, 1, 1, 0, 1, 1]
[0, 0, 1, 0, 1, 1, 1]
[0, 0, 0, 1, 1, 1, 1]
```
### b)

```python
def wege(n, m, aktueller_weg):
    if n == 0 and m == 0:
        print(aktueller_weg)
    else:
        if n > 0 and (((aktueller_weg + [1]).count(1)) > aktueller_weg.count(0)):
            wege(n - 1, m, aktueller_weg + [1])
        if m > 0 and (((aktueller_weg + [0]).count(1)) > aktueller_weg.count(0)):
            wege(n, m - 1, aktueller_weg + [0])

n = int(input("Eingabe von n: "))
m = int(input("Eingabe von m: "))
aktueller_weg = []
print("Es gibt folgende kürzeste Wege, welche nicht durch die Gebiete der Gängs führen:")
wege(n, m, aktueller_weg)
```

**Eingabe:** $n=4,\ m=3$
**Ausgabe:**
```shell
Eingabe von n: 4
Eingabe von m: 3
Es gibt folgende kürzeste Wege, welche nicht durch die Gebiete der Gängs führen:
[1, 1, 1, 1, 0, 0, 0]
[1, 1, 1, 0, 1, 0, 0]
[1, 1, 1, 0, 0, 1, 0]
[1, 1, 1, 0, 0, 0, 1]
[1, 1, 0, 1, 1, 0, 0]
[1, 1, 0, 1, 0, 1, 0]
[1, 1, 0, 1, 0, 0, 1]
[1, 1, 0, 0, 1, 1, 0]
[1, 1, 0, 0, 1, 0, 1]
[1, 0, 1, 1, 1, 0, 0]
[1, 0, 1, 1, 0, 1, 0]
[1, 0, 1, 1, 0, 0, 1]
[1, 0, 1, 0, 1, 1, 0]
[1, 0, 1, 0, 1, 0, 1]
```