
---
## 1
Kosten für jede Operation auf Konto zahlen
pop: +0M
push: +2M
clear: +0M
## 2
Zeigen dass Konto bei beliebiger Operationenfolge nicht negativ wird

### worst case
push
1) +2M -1M = 1M
2) -n * M +1M

$-n \cdot M$ wurde bereits bezahlt, da zu löschende Elemente vorher eingefügt


# Potential Methode

## 1
Wähle geeignete Potenzialmethode $\phi D\to R$, die folgende Bedingungen erfüllt
$\phi(D_{n})\geq \phi(D_0)$
$\phi(D)\geq 0$
$\phi(D)=|S|$

## 2
${C_{i}} = C_{i}+\phi (D_i)-\phi(D_{i-1})$


pop:
$$\begin{align*}
	C_{i}&= C + \phi (D)- \phi (D_{i-1})\\
	&=1+(n-1)-n\\
	&=0
\end{align*}$$
push:
$$\begin{align*}
C&=C+\phi(D)-\phi(D_{i-1})\\
&=1+n+1-n\\
&=2
\end{align*}$$
