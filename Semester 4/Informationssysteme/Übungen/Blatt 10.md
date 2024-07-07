## Aufgabe 4
### a)
![[Untitled (Draft).jpeg]]

![[Untitled (Draft) 2.jpeg]]

### b)
Häufigkeit von Zahlen kleiner oder gleich 13
### 1.
$12+17+10+14+12+14+15/2=76.5$
### 2.
$29+24+26+40/4=109$
### 3.
$13\cdot 7.5 =97.5$
### 4. 
$\int_{1}^{13}p(x)dx=157.94$

Häufigkeit von Zahlen im Intervall $[17,20]$
### 1.
$19+12=31$
### 2.
31
### 3.
$4\cdot 7.5=30$
### 4.
$\int_{17}^{20}p(x)dx=34.68$

## Fehler
Für Zahlen $\le 13$ (Tatsächliche Häufigkeit $88$):
- $H_2$ $\frac{76.5-88}{88}=-0.1306$ ($13.06\%$ Fehler)
- $H_{4}$ $\frac{109-88}{88}=0.2386$ ($23.86\%$ Fehler)
- Gleichverteilung $\frac{97.5-88}{88}=0.107$ ($10.7\%$ Fehler)
- Polynom $\frac{157.94-88}{88}=0.794$ ($79.4\%$ Fehler)

Für Zahlen im Intervall $[17,20]$ (Tatsächliche Häufigkeit 31):
-  $H_2$ $\frac{31-31}{31}=0$ ($0\%$ Fehler)
- $H_{4}$ $\frac{31-31}{31}=0$ ($0\%$ Fehler)
- Gleichverteilung $\frac{30-31}{31}=-0.032$ ($3.2\%$ Fehler)
- Polynom $\frac{34.68-31}{31}=0.1187$ ($11.87\%$ Fehler)
### c)

Intervalle: $[1,6],[6,11],[11,16],[16,21]$ 
Häufigkeiten Für Intervalle:
- $[1,6]: 33$
- $[6,11]: 32$
- $[11,16]: 41$
- $[16,21]: 44$

SSE für $H_4$ :
$$\begin{align*}
(5-7.25)^{2}+(7-7.25)^{2}+(10-7.25)^{2}+(7-7.25)^2\\
+(4-6)^2+(6-6)^2+(8-6)^2+(6-6)^2+(8-6.5)^2+(4-6.5)^2\\
+(8-6.5)^2+(6-6.5)^2+(9-10)^2+(12-10)^2+(13-10)^2+(6-10)^2\\
+(10-7.75)^2+(9-7.75)^2+(4-7.75)^2+(8-7.75)^2\\
&= 45,75
\end{align*}$$
