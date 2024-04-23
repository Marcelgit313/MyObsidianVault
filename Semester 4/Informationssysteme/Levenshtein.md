
---
>[!Important]
>Levenshtein-Editier-Distanz zwischen zwei Strings $x$ und $y$ ist die minimale Anzahl von Änderungsoperationen $insert$, $replace$, $delete$, die benötigt werden um $x$ in $y$ zu transformieren

![[Pasted image 20240423131652.png]]

---
## Laufzeit
Die Levenshtein-Distanz kann mittels dynamischer Programmierung in $O(|x|\cdot|y|)$ berechnet werden.

Anmerkung: Die Kosten können sich für die verschiedenen Operationen unterscheiden.

---
# Initialisierung
![[Pasted image 20240423132128.png]]

---
## Berechnung
![[Pasted image 20240423132455.png]]

Drei Möglichkeiten:
- $\nwarrow$ Distanz von "-" zu "-" plus Kosten $0$ (weil $y[1]=x[1]$) = $0+0=0$
- $\uparrow$ Distanz von "-" zu "s" plus Kosten $1= m[0,1]+1=2$ 
- $\leftarrow$ Distanz von "s" zu "-" plus Kosten $1= m[0,1]+1=2$ 

$$min[i,j]=min \begin{cases}m[0,0]+(x[1]=y[1]?0:1) \text{ Distanz 0 weil x = y        (ersetze x[1])}\nwarrow\\
 m[0,1]+1 \text{ Distanz 2 (lösche x[1])}\uparrow\\ 
m[1,0]+1 \text{ Distanz 2 (füge ein y[1])}\leftarrow
\end{cases}$$
Also wird in das Feld $0$ eingetragen weil die $min$ Distanz $0$ ist.

