>Jannis Lauterbach, Eric Schneider, Marcel Wirdel
## Aufgabe 1
Zeigen für alle $n\in \mathbb{N_{0}}$ :
$$\sum\limits_{j=0}^{n}\dbinom{n}{j}^{2}=\dbinom{2n}{n}$$
Um schreiben der Potenz
$$\begin{align}
\sum\limits_{j=0}^{n}\dbinom{n}{j}^{2}&=\dbinom{n}{j}\cdot \dbinom{n}{j} \\
\sum\limits_{j=0}^{n}\dbinom{n}{j}\cdot \dbinom{n}{j}&=\dbinom{n}{j}\cdot \dbinom{n}{n-j}\text{\qquad|Proposition 1.2.5}\\
\sum\limits_{j=0}^{n}\dbinom{n}{j}\cdot \dbinom{n}{n-j}&=\dbinom{n+n}{n}\text{\qquad |Proposition 1.2.12}\\ 
\sum\limits_{j=0}^{n}\dbinom{n+n}{n}&=\dbinom{2n}{n}\\
\end{align}$$
$\blacksquare$

## Aufgabe 2
IA:  $n=1,m=1$

IV:

## Aufgabe 3

$$\begin{align}
|M_{1}\cup M_{2}\cup M_{3}\cup M_{4}|&=|M_{1}|+|M_2|+|M_3|+|M_4|\\
&-|M_{1}\cap M_2|-|M_{1}\cap M_3|-|M_{1}\cap M_4|\\
&-|M_{2}\cap M_3|-|M_{2}\cap M_4|\\
&-|M_{3}\cap M_4|\\
&+|M_{1}\cap M_{2}\cap M_3|\\
&+|M_{2}\cap M_{3}\cap M_4|\\
&+|M_{1}\cap M_{2}\cap M_4|\\
&+|M_{1}\cap M_{3}\cap M_4|\\
&-|M_{1}\cap M_{2}\cap M_{3}\cap M_4|
\end{align}$$

$|M_{1}|=|T_3|=\lfloor \frac{100000}{3}\rfloor =33333$
$|M_2|=|T_5|=\lfloor \frac{100000}{5}\rfloor =20000$
$|M_3|=|T_7|=\lfloor \frac{100000}{7}\rfloor =14285$
$|M_4|=|T_{11}|=\lfloor \frac{100000}{11}\rfloor =9090$

$|M_{1}\cap M_2|=\lfloor\frac{100000}{3\cdot 5}\rfloor=6666$
$|M_{1}\cap M_3|=\lfloor\frac{100000}{3\cdot 7}\rfloor=4761$
$|M_{1}\cap M_4|=\lfloor\frac{100000}{3\cdot 11}\rfloor=3030$
$|M_{2}\cap M_3|=\lfloor\frac{100000}{5\cdot 7}\rfloor=2857$
$|M_{2}\cap M_4|=\lfloor\frac{100000}{5\cdot 11}\rfloor=1818$
$|M_{3}\cap M_4|=\lfloor\frac{100000}{7\cdot 11}\rfloor=1298$

$|M_{1}\cap M_{2}\cap M_3|=\lfloor \frac{100000}{3\cdot 5\cdot 7}\rfloor =952$
$|M_{2}\cap M_{3}\cap M_4|=\lfloor \frac{100000}{5\cdot 7\cdot 11}\rfloor =259$
$|M_{1}\cap M_{2}\cap M_4|=\lfloor \frac{100000}{3\cdot 5\cdot 11}\rfloor =606$
$|M_{1}\cap M_{3}\cap M_4|=\lfloor \frac{100000}{3\cdot 7\cdot 11}\rfloor =432$

$|M_{1}\cap M_{2}\cap M_{3}\cap M_{4}|=\lfloor \frac{100000}{3\cdot 5\cdot 7\cdot 11}\rfloor =86$

$$\begin{align}
|M_{1}\cup M_{2}\cup M_{3}\cup M_{4}|&=33333+20000+14285+9090\\
&-6666-4761-3030\\
&-2857-1818\\
&-1298\\
&+952\\
&+259\\
&+606\\
&+432\\
&-86\\
&=58613
\end{align}$$

## Aufgabe 4
### a)



