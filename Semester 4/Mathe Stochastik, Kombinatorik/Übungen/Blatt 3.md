>Jannis Lauterbach, Eric Schneider, Marcel Wirdel
---
## Aufgabe 1
### _(a)_
Zeigen für alle $n\in\mathbb{N}_{0}$ :
$$\sum\limits_{j=0}^{n}\dbinom{n}{j}=2^{n}$$ 
### _(b)_
Zeigen für alle $n\in \mathbb{N_{0}}$ :
$$\sum\limits_{j=0}^{n}\dbinom{n}{j}^{2}=\dbinom{2n}{n}$$
Umschreiben der $2$er Potenz
$$\begin{align}
\sum\limits_{j=0}^{n}\dbinom{n}{j}^{2}&=\sum\limits_{j=0}^{n}\dbinom{n}{j}\cdot \dbinom{n}{j} \\
\iff\sum\limits_{j=0}^{n}\dbinom{n}{j}\cdot \dbinom{n}{j}&=\sum\limits_{j=0}^{n}\dbinom{n}{j}\cdot \dbinom{n}{n-j}\text{\qquad|Proposition 1.2.5}\\
\iff\sum\limits_{j=0}^{n}\dbinom{n}{j}\cdot \dbinom{n}{n-j}&=\sum\limits_{j=0}^{n}\dbinom{n+n}{n}\text{\qquad |Proposition 1.2.12}\\ 
\iff\sum\limits_{j=0}^{n}\dbinom{n+n}{n}&=\dbinom{2n}{n}\\
\end{align}$$
$\blacksquare$

---
## Aufgabe 2
### _(a)_

### _(b)_


---
## Aufgabe 3


---
## Aufgabe 4
### _(a)_
Die Menge $M=\lbrace1,2,3,4 \rbrace$ hat $15$ verschiedene Äquivalenzrelationen:
$$\begin{align} &\lbrace \lbrace 1, 2, 3, 4\rbrace\rbrace\\ &\lbrace \lbrace 1, 2, 3 \rbrace, \lbrace 4\rbrace\rbrace\\ &\lbrace \lbrace 1, 2, 4 \rbrace, \lbrace 3\rbrace\rbrace\\ &\lbrace \lbrace 1, 3, 4 \rbrace, \lbrace 2\rbrace\rbrace\\ &\lbrace \lbrace 2, 3, 4 \rbrace, \lbrace 1\rbrace\rbrace\\ &\lbrace \lbrace 1, 2 \rbrace, \lbrace 3, 4\rbrace\rbrace\\ &\lbrace \lbrace 1, 3 \rbrace, \lbrace 2, 4\rbrace\rbrace\\ &\lbrace \lbrace 1, 4 \rbrace, \lbrace 3, 2\rbrace\rbrace\\ &\lbrace\lbrace 1, 2\rbrace,\lbrace 3\rbrace,\lbrace4\rbrace\rbrace\\ &\lbrace\lbrace 1,3\rbrace, \lbrace2\rbrace,\lbrace4\rbrace\rbrace\\ &\lbrace\lbrace 1, 4\rbrace,\lbrace 2\rbrace, \lbrace 3\rbrace\rbrace\\ &\lbrace\lbrace 2, 3\rbrace,\lbrace 1\rbrace,\lbrace 4\rbrace\rbrace\\ &\lbrace\lbrace 2, 4\rbrace, \lbrace 1\rbrace,\lbrace3\rbrace\rbrace\\ &\lbrace\lbrace 3, 4\rbrace,\lbrace 1 \rbrace,\lbrace 2\rbrace\rbrace\\ &\lbrace\lbrace 1\rbrace,\lbrace 2\rbrace, \lbrace 3\rbrace,\lbrace 4\rbrace\rbrace \end{align}$$
### _(b)_

### _(c)_
$$B_{n}=\sum\limits_{k=0}^{n}S(n,k)$$
$S(n,k)$ ist die Anzahl der Partitionen einer n-elementigen Mengen in $k$ nichtleeren Teilmengen.
$$\begin{align}
S(4,0)=0\\
S(4,1)=1\\
S(4,2)=7\\
S(4,3)=6\\
S(4,4)=1
\end{align}$$
Also haben wir:
$$B_{4}=0+1+7+6+1=15$$
