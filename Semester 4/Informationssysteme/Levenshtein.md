
---
>[!Important]
>Levenshtein-Editier-Distanz zwischen zwei Strings $x$ und $y$ ist die minimale Anzahl von Änderungsoperationen $insert$, $replace$, $delete$, die benötigt werden um $x$ in $y$ zu transformieren

![[Pasted image 20240423131652.png]]

---
## Laufzeit
Die Levenshtein-Distanz kann mittels dynamischer Programmierung in $O(|x||y|)$ berechnet werden.

