> Lauterbach Jannis, Schneider Eric, Wirdel Marcel
---
## Aufgabe 1
### _(a)_
### _(b)_

---
## Aufgabe 2
### _(a)_
$$A\cdot x= \Bigg(\sum\limits_{j=1}^{n}a_{ij}x_{j}\Bigg)_{i=1..n}$$
Die Formel hat die Laufzeit $O(n^2)$ da, man durch eine $n\times n$ Matrix muss also hat man $n^{2}$ Zahlen in der Matrix also auch $n^2$ Multiplikation. Dadurch hat man eine Laufzeit von $O(n^2)$ 
### _(b)_
$$A\cdot B = \Bigg(\sum\limits_{j=1}^{n}a_{ij}b_{jk}\Bigg)_{i,k=1...n}$$
Wir haben zwei Matrizen mit $n\times n$. Um diese Matrizen jetzt miteinander zu multiplizieren wird jede Zeile von $A$ mal alle Spalten von $B$ multipliziert also haben wir $n^2$ Multiplikationen. Um jetzt die ganze Matrix zu multiplizieren müssen wir das ganze $n$ mal wieder holen, da die Matrizen $n\times n$ sind. Dann haben wir eine Laufzeit von $O(n^3)$ 
### _(c)_
$$A\cdot B =C$$
Eine Idee für einen Monte-Carlo-Algorithmus mit einseitigem Fehler ist:

### Idee
1. Einen zufälligen Vektor der Länge $n$ generieren $r\in\mathbb{R}^n$ 
2. Matrix-Vektor-Multiplikation:
	- Berechne den Vektor $x=B\cdot r$
	- Berechne den Vektor $y=A\cdot x= A\cdot(B\cdot r)$ 
	- Berechne den Vektor $z=C\cdot r$ 
3. Vergleichen der Ergebnisse:
	- Vergleiche die Vektoren $z$ und $y$ 
	- Wenn $z = y$, gebe $true$ zurück
	- Wenn $z\neq y$, gebe $false$ zurück

### Laufzeit
Wir haben eine Matrix-Vektor-Multiplikation diese hat eine Laufzeit von $O(n^{2})$ . Diese wird drei mal im Algorithmus berechnet also $n^{2}+n^{2}+n^2$ also eine Laufzeit von $O(n^2)$ 
 
---
## Aufgabe 3