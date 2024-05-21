> Jannis Lauterbach, Eric Schneider, Marcel Wirdel

---
## Aufgabe 1
### _(a)_
Der Professor hat diese Partitionen bereits $S(4,3)$:
$$\begin{align}
\lbrace\lbrace1,2\rbrace\lbrace3\rbrace\lbrace4\rbrace\rbrace\\
\lbrace\lbrace1,3\rbrace\lbrace2\rbrace\lbrace4\rbrace\rbrace\\
\lbrace\lbrace1,4\rbrace\lbrace2\rbrace\lbrace3\rbrace\rbrace\\
\lbrace\lbrace2,3\rbrace\lbrace1\rbrace\lbrace4\rbrace\rbrace\\
\lbrace\lbrace2,4\rbrace\lbrace1\rbrace\lbrace3\rbrace\rbrace\\
\lbrace\lbrace3,4\rbrace\lbrace1\rbrace\lbrace2\rbrace\rbrace\\
\end{align}$$
Um jetzt seinen Fehler zu korrigieren fügt er in jede Teilmenge der einzelnen Partitionen die $5$ ein, dadurch entstehen pro Partition die der Professor momentan hat $3$ neue Partitionen also hat er dann $18$ Partitionen. Die letzten $7$ bekommt er indem er alle Partitionen aufschreibt aus $4$-Elementen und $2$ Teilmengen und einfach die $\lbrace5\rbrace$ als eigene Teilmenge dran hängt.
$$S(5,3)=S(4,2)+3\cdot S(4,3)$$
### _(b)_


### _(c)_
$$\begin{align}
S(5,0)&=0\\
S(5,1)&=S(4,1)=S(3,1)=S(2,1)=S(1,1)=1\\
S(5,2)&=S(4,1)+2\cdot S(4,2)=S(4,1)+2\cdot(S(3,1)+2\cdot(S(3,2)))\\
&=1+2\cdot(1+2\cdot (S(2,1)+2\cdot(S(2,2))))=1+2\cdot(1+2\cdot(1+2\cdot1))=15\\
S(5,3)&=S(4,2)+3\cdot S(4,3)=S(3,1)+2\cdot S(3,2)+3\cdot(S(3,2)+ 3 \cdot S(3,3))\\
&=1+2\cdot(S(2,1)+2\cdot S(2,2))+3\cdot((S(2,1)+2\cdot S(2,2))+3\cdot 1)\\
&=1+2\cdot (1+2\cdot1)+3\cdot(1+2\cdot1+3)=25
\end{align}$$


---
## Aufgabe 2


---
## Aufgabe 3
### _(a)_
**Gesamtkombinationen**
Wir haben ein Dreieck mit $3$ Kanten und pro Kante die Optionen: 
- Pfeil im Uhrzeigersinn 
- Pfeil gegen den Uhrzeigersinn 
- keinen Pfeil 
Wir haben $3$ Optionen pro Kante. Wir kommen somit auf $3^3=27$ mögliche Kombinationen.
**Verlustkombinationen**
Wir haben folgende Verlustkombinationen:
- alle Pfeile in eine Richtung
- Pfeil, Pfeil, kein Pfeil
- Pfeil, kein Pfeil, Pfeil
- kein Pfeil, Pfeil, Pfeil
Diese $4$ Kombinationen können jeweils für Pfeile im Uhrzeigersinn und für Pfeile gegen den Uhrzeigersinn auftreten somit haben wir insgesamt $4\cdot 2=8$ Verlustkombinationen.
**Gewinnkombinationen**
Da wir $8$ Verlustkombinationen haben und insgesamt $27$ Kombinationen haben wir also $27-8=19$ Gewinnkombinationen. 
**Gewinnwahrscheinlichkeit**
$$\frac{19}{27}=0.\overline{703}\approx 0.703$$
Somit haben wir eine Gewinnwahrscheinlichkeit von ca. $70.37 \%$.
### _(b)_
Wir bestimmen nun alle Halbordnungen auf der Menge $M=\{1,2,3\}$ 
**Einzeln**
$$\{(1,1),(2,2),(3,3)\}$$
**Paarweise**
$$\begin{align}
&\{(1,1),(2,2),(3,3),(1,2)\} \\
&\{(1,1),(2,2),(3,3),(2,3)\} \\
&\{(1,1),(2,2),(3,3),(1,3)\} \\
&\{(1,1),(2,2),(3,3),(1,2),(2,3)\} \\
&\{(1,1),(2,2),(3,3),(1,2),(1,3)\} \\
&\{(1,1),(2,2),(3,3),(1,3),(2,3)\} \\
&\{(1,1),(2,2),(3,3),(1,2),(2,3),(1,3)\} \\
\end{align}$$
Somit haben wir folgende $8$ Halbordnungen:
$$\begin{align}
&\{(1,1),(2,2),(3,3)\} \\
&\{(1,1),(2,2),(3,3),(1,2)\} \\
&\{(1,1),(2,2),(3,3),(2,3)\} \\
&\{(1,1),(2,2),(3,3),(1,3)\} \\
&\{(1,1),(2,2),(3,3),(1,2),(2,3)\} \\
&\{(1,1),(2,2),(3,3),(1,2),(1,3)\} \\
&\{(1,1),(2,2),(3,3),(1,3),(2,3)\} \\
&\{(1,1),(2,2),(3,3),(1,2),(2,3),(1,3)\} \\
\end{align}$$
In diesen $8$ Halbordnungen befindet sich eine Totalordnung:
$$\{(1,1),(2,2),(3,3),(1,2),(2,3),(1,3)\}$$
Da bei dieser Ordnung jedes Elementepaar vergleichbar ist handelt es sich um eine Totalordnung.


---
## Aufgabe 4
### _(a)_
$$\begin{align}
&\{(1,1),(2,2)\} \\
&\{(1,1),(2,2),(1,2)\} \\
&\{(1,1),(2,2),(2,1)\} \\
&\{(1,1),(2,2),(1,2),(2,1)\} \\
\end{align}$$

### _(b)_
### _(c)_
Die Anzahl der Totalordnung von einer Menge $M$ mit $n$ Elementen, kann man mithilfe der Anzahl der Permutationen herausgefunden werden. Die Anzahl der Permutationen kann mit der Fakultät berechnet werden, also $n!$. 
Angenommen wir haben eine Menge $M=\{1,2,3\}$, die Menge $M$ hat $3$ Elemente also $n=3$.
$$3!=3\cdot 2\cdot 1=6$$
Somit ist die Anzahl der Totalordnungen von einer Menge $M$ mit $n$ Elementen $n!$. In diesem Beispiel haben wir $6$ Totalordnungen.