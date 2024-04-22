___

![[Pasted image 20240422123827.png]]

$$ T_{1(n)}= n\cdot T_{2(n)} $$
Es wird n-mal die Schleife $T_2$ ausgeführt
$$T_{2(n)}=n\cdot (c + T_{3(n)})$$
Die Schleife wird n-mal ausgeführt und dabei jedes mal die Kosntante c (line 5) und die Schleife $T_3$
$$T_{3(n)}=n\cdot c$$
n weil die $for$-Schleife n-mal ausgeführt wird, wobei n-mal die Konstante Rechnung c (line 8) gerechnet wird

Dann einsetzten:
$$\begin{align*}
&T_{1}=n\cdot T_{2(n)}\\
&=n\cdot (n\cdot (c+T_{3(n)}))\\
&= n\cdot (n\cdot (c+(n\cdot c))\\
&=n^2*(c+(n\cdot c))\\
&=cn^2+cn^3\\
&=c \cdot(n^3+n^2)
\end{align*}$$
