
---
# Ähnlichkeitsmaß Jaccard-Koeffizient
Bekanntes Maß zur Berechnung von Ähnlichkeiten zweier Mengen.

$$J(A,B)=\frac{|A\cap B|}{|A\cup B|}$$
Zur Berechnung der Ähnlichkeit von Text-Dokumenten zwecks Duplikaterkennung werden in der Regel nicht die einzelnen Worte benutzt sondern __k-shingles__ oder auch k-grams .

Die __k-shingles__ eines Dokuments werden $S(d_{i})$ genannt

Beispiel:

Dokument mit den Worten $\lbrace a,b,b,c\rbrace$ wäre der $2-shingle$ dieses Dokuments $\lbrace ab,bb,bc\rbrace$ 

## Jaccard-Koeffizient
$$sim(d_{1},d_2)=\frac{|S(d_{1})\cap S(d_{2})|}{|S(d_{1}\cup S(d_2)|}$$

---
# LSI
Betrachte __Singulärwertzerlegung__ der $m\times n$ Term-Dokument-Matrix $A$   
![[Pasted image 20240428130548.png]]

---
## Singulärwertzerlegung Beispiel
![[Pasted image 20240428130723.png]]

---
## Rang-k Approximation
Man möchte $A$ gar nicht korrekt wiederherstellen sondern approximieren durch die Auswahl der wichtigsten Topics.

Wir wählen die k größten Singulärwerte aus $\Sigma$  aus, d.h. wir setzten die übrigen Singulärwerte auf $0$ und entsprechend die dazugehörigen Einträge in $U$ und $V^T$ 

![[Pasted image 20240428131212.png]]**Faustregel**: Es sollten etwa 90% der Summe der Quadrate der Singulärwerte erhalten bleiben

---
# Operationen im Topic-Raum
Wir können eine Anfrage aus dem $m$-dimensionalen Term-Raum in den k-dimensionalen Topic-Raum abbilden durch
$$q\rightarrow U_{k}^{T}q=q'$$
Die Eignung(Score) der Dokumente wird dann im Topic-Raum berechnet durch die Cosinus-Ähnlichkeit oder das Skalarprodukt von $q'$ und den Spalten der Matrix $V_{k}^{T}$ 