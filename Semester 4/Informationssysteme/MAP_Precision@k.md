
---
# Average Precision (AP)
- Sei { $d_{1},....,d_{m}$ } die Menge der relevanten Dokumente der Anfrage $q$
- Sei $R_{k}$ die Menge der geordneten Ergebnisse

$$AP(q)= \frac{1}{m}\sum\limits_{d_{k}\in {d_{1},....,d_{m}}}Precision(R_{k})$$

---
## Mean-Average-Precision
Für die Menge $Q$ von Anfragen kann die __Mean-Average-Precision(MAP)__ berechnet werden durch
$$MAP(Q)=\frac{1}{|Q|}\sum\limits_{q\in Q}AP(q)$$

---
# Precision@k
Precision@k ist die Precision, die in der ersten $k$ Ergebnisse erreicht wird, also wenn 5 relevante Dokumente in den ersten 10 Dokumenten ist dann
$$Precision@10=\frac{5}{10}=\frac{1}{2}=0.5$$
