>Jannis Lauterbach, Eric Schneider, Marcel Wirdel
---
## Aufgabe 1
### _(a)_
Grundsätzlich gibt es $n!$ Möglichkeiten $n$ Personen anzuordnen. In $n!$ Anordnungen sind noch die Drehungen enthalten. Um die Drehungen zu entfernen, fixieren wir eine Person an ihrem Platz und betrachten die Permutationen der übrig gebliebenen. Dadurch erhalten wir: $$\begin{align} \frac{n!}{n} = (n-1)! \end{align}$$ Also $(n-1)!$ Möglichkeiten $n$ Personen an einem runden Tisch zu setzen.
### _(b)_
Für $n=4$ Personen haben wir also $(4-1)!=3!=6$ Anordnungen. Wir haben folgende $6$ Anordnungen: $$\begin{align} 1,2,3,4 \\ 1,2,4,3 \\ 1,4,2,3 \\ 1,4,3,2 \\ 1,3,2,4 \\ 1,3,4,2 \\ \end{align}$$

---
## Aufgabe 2
### _(a)_
Um die Wahrscheinlichkeit, die Zahl $n$ zu würfeln, proportional zu $n$ dazustellen multiplizieren wir $n$ mit einer Konstante $c$. Die Wahrscheinlichkeit für die Zahl $n$ gewürfelt zu werden ist dann: $c \cdot n$. Da die Summe der Wahrscheinlichkeiten 1 sein muss können wir $c$ einfach durch umstellen herausfinden $$\begin{align} & 1 \cdot c + 2 \cdot c + 3 \cdot c + 4\cdot c+5\cdot c+6\cdot c=1 \\ & c \cdot (1+2+3+4+5+6) = 1 \\ & c \cdot 21 = 1 \ |\div21 \\ & c = \frac{1}{21} \end{align}$$ Somit erhalten wir für die Würfe eine Wahrscheinlichkeit von: $$\begin{align} &1 \cdot \frac{1}{21} = \frac{1}{21} \ | \ \text{für n = 1} \\ \\ &2 \cdot\frac{1}{21} = \frac{2}{21} \ | \ \text{für n = 2} \\ \\ &3 \cdot \frac{1}{21} = \frac{3}{21} \ | \ \text{für n = 3} \\ \\ &4 \cdot \frac{1}{21} = \frac{4}{21} \ | \ \text{für n = 4} \\ \\ &5 \cdot \frac{1}{21} = \frac{5}{21} \ | \ \text{für n = 5} \\ \\ &6 \cdot\frac{1}{21} = \frac{6}{21} \ | \ \text{für n = 6} \\ \end{align}$$
### _(b)_
Die Wahrscheinlichkeit eine ungerade Zahl zu würfeln ist die Summe der Wahrscheinlichkeiten eine 1, 3 oder 5 zu würfeln. $$\begin{align} \frac{1}{21} + \frac{3}{21} + \frac{5}{21} = \frac{9}{21} = \frac{3}{7} \end{align}$$ Die Wahrscheinlichkeit eine ungerade Zahl zu würfeln beträgt $\frac{3}{7} \approx 0.428$

---
## Aufgabe 3
### _(a)_
Die Wahrscheinlichkeit in dem Spiel keine $1$ zu würfeln wird durch die Formel beschrieben:
$$\bigg(1-\frac{1}{n}\bigg)^m$$
Dabei stellt $\frac{1}{n}$ die Wahrscheinlichkeit da eine $1$ zu würfeln mit einem Würfel welcher $n$ Seiten hat.
$1-\frac{1}{n}$ ist die Gegenwahrscheinlichkeit keine $1$ zu würfeln und da jeder Wurf unabhängig ist, multipliziert sich die Wahrscheinlichkeit $m$ mal.
### _(b)_
Zeigen das:
$$\lim\limits_{n\to\infty}\bigg(1-\frac{1}{n}\bigg)^{n\cdot ln(2)}=\frac{1}{2}$$
Da $1-\frac{1}{n}$ immer größer als $0$ :
$$\lim\limits_{n\to\infty} exp((n\cdot ln(2))\cdot ln\bigg(1-\frac{1}{n}\bigg))$$
Jetzt kann man den Grenzwert reinziehen:
$$exp(ln(2)\cdot \lim\limits_{n\to\infty} n\cdot ln\bigg(1-\frac{1}{n}\bigg))$$
Dann kann man $n$ umschreiben und $ln$ in den Zähler ziehen:
$$exp(ln(2)\cdot \lim\limits_{n\to\infty} \frac{ln\bigg(1-\frac{1}{n}\bigg)}{\frac{1}{n}})$$
Dann den Satz von l´Hospital:
$$\begin{align}
\iff& exp\Bigg(ln(2)\cdot \lim\limits_{n\to\infty} \frac{\frac{1}{(n-1)n}}{-\frac{1}{n^2}}\Bigg)\\
\iff& exp\Bigg(ln(2)\cdot \lim\limits_{n\to\infty} \frac{-n^2}{n^2-n}\Bigg)\\
\iff& exp\Bigg(ln(2)\cdot \frac{1}{-\frac{n}{n}}\Bigg)\\
\iff& exp\Bigg(ln(2)\cdot \frac{1}{-\frac{1}{1}}\Bigg)\\
\iff& exp(ln(2)\cdot -1)\\
\iff& 2^{-ln(2)}\\
\iff&\frac{1}{2}
\end{align}$$



---
## Aufgabe 4
```python
def multiset(M, n, pos):
    if n == 0:
        latest_tuple = tuple(latest_list)
        result_set.add(latest_tuple)
        return
  
    for i in range(pos, len(M)):
        latest_list.append(M[i])
        multiset(M, n - 1, i)
        latest_list.pop()

M_raw = input("Eingabe von Elementen von M, getrennt durch ein Freizeichen: ")
M = M_raw.split(" ")  
n = int(input("Eingabe von n: "))
latest_list = []
result_set = set()

multiset(M, n, 0)
print(sorted(result_set))
```

**Eingabe:** $M=\{a, b, c, d\},\ n = 3$
**Ausgabe:**
```shell
Eingabe von Elementen von M, getrennt durch ein Freizeichen: a b c d
Eingabe von n: 3
[('a', 'a', 'a'), ('a', 'a', 'b'), ('a', 'a', 'c'), ('a', 'a', 'd'), ('a', 'b', 'b'), ('a', 'b', 'c'), ('a', 'b', 'd'), ('a', 'c', 'c'), ('a', 'c', 'd'), ('a', 'd', 'd'), ('b', 'b', 'b'), ('b', 'b', 'c'), ('b', 'b', 'd'), ('b', 'c', 'c'), ('b', 'c', 'd'), ('b', 'd', 'd'), ('c', 'c', 'c'), ('c', 'c', 'd'), ('c', 'd', 'd'), ('d', 'd', 'd')]
```
