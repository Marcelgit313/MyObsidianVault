
---
![[Pasted image 20240423161649.png]]![[Pasted image 20240423161733.png]]

---
## Präzision(Precision) und Ausbeute(Recall)
Precision P ist der Anteil der relevanten Dokumente in den zurückgegebenen Dokumenten
$$P=\frac{tp}{tp+fp}$$

Recall R ist der Anteil der relevanten zurückgegebenen Dokumente an allen relevanten Dokumenten
$$R=\frac{tp}{tp+fn}$$

---
## F-Measure
F-measure kombiniert Precision und Recall
$$F_{\beta}=\frac{(\beta^{2}+1)P\cdot R}{\beta^{2}\cdot P+R}$$
wobei der Parameter $\beta$ zwischen Precision und Recall die Gewichtung entscheidet
- $\beta = 1$ ist balanciert
- $\beta <1$ höherer Einfluss von Precision
- $\beta > 1$ höherer Einfluss von Recall