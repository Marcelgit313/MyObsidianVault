> Jannis Lauterbach, Eric Schneider, Marcel Wirdel
---
## Aufgabe 1

 Wir müssen den Erwartungswert für zwei Fälle von $n$ betrachten, bei $n \le 47$ beträgt der Gewinn $2^n$, bei $n > 47$ bleibt der Gewinn jedoch bei $2^n$. Wir erhalten folgende Formel zum ausrechnen des erwarteten Gewinns: $$\begin{align} E = \sum\limits_{n = 1}^{47} 2^n \cdot \bigg(\frac{1}{2}\bigg)^n + \sum\limits_{n = 48}^{\infty} 2^{47} \cdot \bigg(\frac{1}{2}\bigg)^n \end{align}$$  Da $2^n \cdot (\frac{1}{2})^n = 1$ für jedes beliebige $n$, gilt für den ersten Teil der Formel: $$\begin{align} \sum\limits_{n = 1}^{47} 2^n \cdot \bigg(\frac{1}{2}\bigg)^n = \sum\limits_{n = 1}^{47} 1 = 47 \end{align}$$  Der zweite Teil der Formel kann zunächst umgeschrieben werden: $$\begin{align} \sum\limits_{n = 48}^{\infty} 2^{47} \cdot \bigg(\frac{1}{2}\bigg)^n = 2^{47} \sum\limits_{n = 48}^{\infty}   \bigg(\frac{1}{2}\bigg)^n \end{align}$$ Die Summe ist eine geometrische Reihe, wir verschieben die Indizes und ziehen den konstanten Faktor wieder aus der Summe heraus: $$\begin{align} 2^{47} \sum\limits_{n = 48}^{\infty}   \bigg(\frac{1}{2}\bigg)^n = 2^{47} \sum\limits_{k = 0}^{\infty}   \bigg(\frac{1}{2}\bigg)^{k+48} = 2^{47} \cdot \bigg(\frac{1}{2}\bigg)^{48} \sum\limits_{k = 0}^{\infty}   \bigg(\frac{1}{2}\bigg)^{k} \end{align}$$ Die geometrische Reihe konvergiert, da $\frac{1}{2} < 1$: $$\begin{align} \sum\limits_{k = 0}^{\infty}   \bigg(\frac{1}{2}\bigg)^{k} = \frac{1}{1-{\frac{1}{2}}} = 2 \end{align}$$  Endgültig bleibt dann: $$\begin{align} &E = 47 + 2^{47} \cdot \bigg(\frac{1}{2}\bigg)^{48} \cdot 2 \\ &E = 47 + 2^{47} \cdot \bigg(\frac{1}{2}\bigg)^{47} \\ &E = 47 + 1 \\ &E = 48 \end{align}$$ Somit ist der erwartete Gewinn 48€`

---
## Aufgabe 2
### _(a)_

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
### _(b)_

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

---
## Aufgabe 3
### _(a)_

![[Pasted image 20240620191853.png]]
### _(b)_
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

---
## Aufgabe 4

Zeigen, dass für $M_{1},....,M_{n}\in\Omega$ gilt:
$$P(M_{1}\cup ...\cup M_{n})= \sum\limits_{k=1}^{n}(-1)^{k-1}\sum\limits_{|T|=k}P(M_T)$$
Sei $x\in M_{1}\cup ...\cup M_{n}$. Wir wollen zeigen, dass $x$ zu der rechten Seite genau mit $1$ beiträgt.  Angenommen $x$ liegt in genau $r$ Mengen $M_{i}$, ohne Einschränkung $x\in M_{1}\cap ...\cap M_{i}$. Dann wird $x$ in $\sum\limits_{|T|=k}|M_T|$ genau $\binom{r}{k}$-mal gezählt, also:
$$a=\sum\limits_{k=1}^{r}(-1)^{k-1}\binom{r}{k}$$
Da mit Corollar $1.2.26$
$$0=\sum\limits_{k=1}^{r}(-1)^{k-1}\binom{r}{k}=1-a$$
gilt, ist $a=1$.$\blacksquare$ 