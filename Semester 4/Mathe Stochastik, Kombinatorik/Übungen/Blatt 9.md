>Jannis Lauterbach, Eric Schneider, Marcel Wirdel

---
## Aufgabe 1
### _(a)_
Da der Würfel fair ist haben $X_1$ und $X_2$ die gleiche Wahrscheinlichkeit
$$P(X_1)=P(X_2)=\frac{1}{6}$$
### _(b)_
#### Wahrscheinlichkeitsverteilung von $X_{1}+X_{2}$ 
Beide Würfe können eine mindest Augenzahl von $2$ erreichen und eine maximale Augenzahl von $12$ also:
$$\begin{align*}\\
&P(X_1+X_2=2)=P(1,1)=\frac{1}{36}\\
&P(X_1+X_2=3)=P(1,2)+P(2,1)=\frac{2}{36}=\frac{1}{18}\\
&P(X_1+X_2=4)=P(2,2)+P(1,3)+P(3,1)=\frac{3}{36}=\frac{1}{12}\\
&P(X_1+X_2=5)=P(1,4)+P(4,1)+P(2,3)+P(3,2)=\frac{4}{36}=\frac{1}{9}\\
&P(X_1+X_2=6)=P(3,3)+P(1,5)+P(5,1)+P(4,2)+P(4,2)=\frac{5}{36}\\
&P(X_1+X_2=7)=P(1,6)+P(2,5)+P(3,4)+P(4,3)+P(5,2)+P(6,1)=\frac{6}{36}=\frac{1}{6}\\
&P(X_1+X_2=8)=P(2,6)+(3,5)+(4,4)+(5,3)+(6,2)=\frac{5}{36}\\
​&P(X_1+X_2=9)=P(4,5)+P(5,4)+P(3,6)+P(6,3)=\frac{4}{36}=\frac{1}{9}\\
&P(X_1+X_2=10)=P(5,5)+P(4,6)+P(6,4)=\frac{3}{36}=\frac{1}{12}\\
&P(X_1+X_2=11)=P(5,6)+P(6,5)=\frac{2}{36}=\frac{1}{18}\\
&P(X_1+X_2=12)=P(6,6)=\frac{1}{36}
\end{align*}$$
### Wahrscheinlichkeitsverteilung von $X_{1}-X_{2}$
Beide Würfel können $-5$ bis $5$ erreichen, also:
$$\begin{align} 
&P(X_1 - X_2 = -5) = \frac{1}{36} \\
&P(X_1 - X_2 = -4) = \frac{2}{36} = \frac{1}{18} \\ 
&P(X_1 - X_2 = -3) = \frac{3}{36} = \frac{1}{12}\\ 
&P(X_1 - X_2 = -2) = \frac{4}{36} = \frac{1}{9} \\ 
&P(X_1 - X_2 = -1) = \frac{5}{36} \\ 
&P(X_1 - X_2 = 0) = \frac{6}{36} = \frac{1}{6} \\ 
&P(X_1 - X_2 = 1) = \frac{5}{36} \\ 
&P(X_1 - X_2 = 2) = \frac{4}{36} = \frac{1}{9} \\ 
&P(X_1 - X_2 = 3) = \frac{3}{36} = \frac{1}{12} \\ 
&P(X_1 - X_2 = 4) = \frac{2}{36} = \frac{1}{18} \\ 
&P(X_1 - X_2 = 5) = \frac{1}{36} \ \end{align}$$

---
## Aufgabe 2
**Zufallsvariablen** 

|     | $X_1$ | $X_2$ | $X_3$ | $X_1\cdot X_3$ | $X_2\cdot X_3$ |
| --- | ----- | ----- | ----- | -------------- | -------------- |
| 000 | 0     | 1     | 0     | 0              | 0              |
| 001 | 1     | 1     | 1     | 1              | 1              |
| 010 | 1     | 0     | 1     | 1              | 0              |
| 011 | 0     | 0     | 2     | 0              | 0              |
| 100 | 1     | 0     | 1     | 1              | 0              |
| 101 | 0     | 0     | 2     | 0              | 0              |
| 110 | 0     | 1     | 2     | 0              | 2              |
| 111 | 1     | 1     | 3     | 3              | 3              |

**Wahrscheinlichkeitsverteilung** $$\begin{align} &P(X_1\cdot X_3 = 0) = \frac{4}{8} \\ &P(X_1\cdot X_3 = 1) = \frac{3}{8} \\ &P(X_1\cdot X_3 = 3) = \frac{1}{8} \\ \\ &P(X_2\cdot X_3 = 0) = \frac{5}{8} \\ &P(X_2\cdot X_3 = 1) = \frac{1}{8} \\ &P(X_2\cdot X_3 = 2) = \frac{1}{8} \\ &P(X_2\cdot X_3 = 3) = \frac{1}{8} \\ \end{align}$$

---
## Aufgabe 3
#### Erwartungswert
$$E(X)=\frac{1+2+3+4+5+6}{6}=3,5$$
$$E(Y)= 2*(E(X)+1)=2*(3,5+1)=9$$
#### Varianz
$$V(X)=E(X^2)-(E(X))^2$$
$$E(X^{2})=(1+4+9+16+25+36)\cdot \frac{1}{6}=\frac{91}{6}$$
$$(E(X))^2=3,5^2=12,25$$
$$V(X)=\frac{91}{6}-12,25=2,92$$
$$V(Y)$$


---
## Aufgabe 4
