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
$|T_3|=\lfloor \frac{100000}{3}\rfloor =33333$
$|T_5|=\lfloor \frac{100000}{5}\rfloor =20000$
$|T_7|=\lfloor \frac{100000}{7}\rfloor =14285$
$|T_{11}|=\lfloor \frac{100000}{11}\rfloor =9090$

$$\begin{align}
|M_{1}\cup M_{2}\cup M_{3}\cup M_{4}|&=|M_{1}|+|M_2|+|M_3|+|M_4|\\
&-|M_{1}\cap M_2|-|M_{1}\cap M_3|-|M_{1}\cap M_4|\\
&-|M_{2}\cap M_3|-|M_{2}\cap M_4|\\
&-|M_{3}\cap M_4|\\
&+|M_{1}\cap M_{2}\cap M_{3}\cap M_4|
\end{align}$$



## Aufgabe 4
### a)



