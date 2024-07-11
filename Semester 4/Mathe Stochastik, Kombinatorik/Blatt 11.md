## Aufgabe 1

| $\omega$ | $X_1(\omega)$ | $X_2(\omega)$ | $X_3(\omega)$ | $X_1\cdot X_3(\omega)$ | $X_2\cdot X_3(\omega)$ |
| -------- | ------------- | ------------- | ------------- | ---------------------- | ---------------------- |
| 000      | 0             | 1             | 0             | 0                      | 0                      |
| 001      | 1             | 1             | 1             | 1                      | 1                      |
| 010      | 1             | 0             | 1             | 1                      | 0                      |
| 011      | 0             | 0             | 2             | 0                      | 0                      |
| 100      | 1             | 0             | 1             | 1                      | 0                      |
| 101      | 0             | 0             | 2             | 0                      | 0                      |
| 110      | 0             | 1             | 2             | 0                      | 2                      |
| 111      | 1             | 1             | 3             | 3                      | 3                      |

**Erwartungswerte**
$$E(X_1)=\frac{0+1+1+0+1+0+0+1}{8}=\frac{1}{2}=0.5$$
$$E(X_2)=\frac{1+1+0+0+0+0+1+1}{8}=\frac{1}{2}=0.5$$
$$E(X_3)=\frac{0+1+1+2+1+2+2+3}{8}=\frac{3}{2}=1.5$$
$$\begin{align}
E(X_1\cdot X_3)&=\frac{(0+1+1+0+1+0+0+1)\cdot (0+1+1+2+1+2+2+3)}{64} \\ &=\frac{3}{4}=0.75 \\
\end{align}$$
$$\begin{align}
E(X_2\cdot X_3)&=\frac{(1+1+0+0+0+0+1+1)\cdot (0+1+1+2+1+2+2+3)}{64} \\ &=\frac{3}{4}=0.75 \\
\end{align}$$
**Covarianz**
$$\text{Cov}(X_1,X_3)=E(X_1\cdot X_3)-E(X_1)\cdot E(X_3)=0.75-0.5\cdot 1.5=0$$
$$\text{Cov}(X_2,X_3)=E(X_2\cdot X_3)-E(X_2)\cdot E(X_3)=0.75-0.5\cdot 1.5=0$$
**Varianz**
$$\begin{align}
V(X_1)=E(X_1^2) - E(X_1)^2&=\frac{0^2+1^2+1^2+0^2+1^2+0^2+0^2+1^2}{8} - 0.5^2 \\
&=\frac{1}{4}=0.25 \\
\end{align}$$
$$\begin{align}
V(X_2)=E(X_2^2) - E(X_2)^2&=\frac{1^2+1^2+0^2+0^2+0^2+0^2+1^2+1^2}{8} - 0.5^2 \\
&=\frac{1}{4}=0.25 \\
\end{align}$$
$$\begin{align}
V(X_3)=E(X_3^2) - E(X_3)^2&=\frac{0^2+1^2+1^2+2^2+1^2+2^2+2^2+3^2}{8} - 1.5^2 \\
&=\frac{3}{4}=0.75 \\
\end{align}$$
**Korrelation**
$$\text{Corr}(X_1,X_3)=\frac{\text{Cov}(X_1,X_3)}{\sqrt{V(X_1)}\cdot \sqrt{V(X_3)}}=\frac{0}{\sqrt{0.25}\cdot \sqrt{0.75}}=0$$
$$\text{Corr}(X_2,X_3)=\frac{\text{Cov}(X_2,X_3)}{\sqrt{V(X_2)}\cdot \sqrt{V(X_3)}}=\frac{0}{\sqrt{0.25}\cdot \sqrt{0.75}}=0$$
## Aufgabe 3
**Augensumme $< 7$**
Zutreffende Ergebnisse:
$$\begin{align}
&(1, 1), (1, 2), (1, 3), (1, 4), (1, 5), \\ 
&(2, 1), (2, 2), (2, 3), (2, 4), \\ 
&(3, 1), (3, 2), (3, 3), \\
&(4, 1), (4, 2), \\
&(5, 1) \\
\end{align}$$
Insgesamt haben wir $36$ mögliche Ergebnisse, somit haben wir folgende Wahrscheinlichkeit mit einer Augensumme $< 7$ zu gewinnen:
$$P(Augensumme < 7)\frac{15}{36} = \frac{5}{12} = 0.41\overline{6}$$
**(a) Der erste Wurf eine 1 geliefert hat**
Zutreffende Ergebnisse:
$$\begin{align}
&(1, 1), (1, 2), (1, 3), (1, 4), (1, 5) \\ 
\end{align}$$
Insgesamt haben wir $36$ mögliche Ergebnisse, somit haben wir folgende Wahrscheinlichkeit mit einer Augensumme $< 7$ und einer $1$ im ersten Wurf zu gewinnen:
$$P((a))=\frac{5}{36}=0.13\overline{8}$$
**(b) Der erste Wurf eine 3 geliefert hat**
Zutreffende Ergebnisse:
$$\begin{align}
&(3, 1), (3, 2), (3, 3) \\ 
\end{align}$$
Insgesamt haben wir $36$ mögliche Ergebnisse, somit haben wir folgende Wahrscheinlichkeit mit einer Augensumme $< 7$ und einer $3$ im ersten Wurf zu gewinnen:
$$P((b))=\frac{3}{36}=\frac{1}{12}=0.08\overline{3}$$
**(c) Der erste Wurf eine 6 geliefert hat**
Zutreffende Ergebnisse:
$$\begin{align}
\text {Keine} \\ 
\end{align}$$
Insgesamt haben wir $36$ mögliche Ergebnisse, somit haben wir folgende Wahrscheinlichkeit mit einer Augensumme $< 7$ und einer $6$ im ersten Wurf zu gewinnen:
$$P((c))=\frac{0}{36}=0$$
**(d) Der erste Wurf eine Zahl kleiner als 5 geliefert hat**
Zutreffende Ergebnisse:
$$\begin{align}
&(1, 1), (1, 2), (1, 3), (1, 4), (1, 5), \\ 
&(2, 1), (2, 2), (2, 3), (2, 4), \\ 
&(3, 1), (3, 2), (3, 3), \\
&(4, 1), (4, 2), \\
\end{align}$$
Insgesamt haben wir $36$ mögliche Ergebnisse, somit haben wir folgende Wahrscheinlichkeit mit einer Augensumme $< 7$ und einer $6$ im ersten Wurf zu gewinnen:
$$P((d))=\frac{14}{36}=\frac{7}{18}=0.3\overline{8}$$
## Aufgabe 4
Nach $100$ mal drehen haben wir folgende Werte:
Blau: $55$ 
Gelb: $29$
Rot: $16$
Somit haben wir folgende relative Häufigkeiten:
Blau: $\frac{55}{100}=\frac{11}{20}=0.55$
Gelb: $\frac{29}{100}=0.29$
Rot: $\frac{16}{100}=\frac{5}{25}=0.16$
