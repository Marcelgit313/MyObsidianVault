
---
Gegeben eine Menge von Objekten. Ziel: Finden eines guten Clusterings der Objekten anhand ihrer Eigenschaften

![[Pasted image 20240505121045.png]]

---
# Clustering-Problem
- Gegeben eine Menge $U$ von Objekten und eine Distanzfunktion $d:U\times U\rightarrow \mathbb{R}^{+}$  
- gleiche Objekte müssen eine möglichst kleine Distanz zueinander haben
- unterschiedliche Objekte müssen eine große Distanz zwischen anderen haben

---
# Partitionen und Prototypen
Es wird nur __exklusives Clustering__ betrachtet, d.h. ein Objekt ist genau einem Cluster zugeordnet

- Jedes Cluster $C_i$ wird von einem sogenannten Prototypen $\mu$ repräsentiert

---
# Naiver (Brute-Force) Ansatz
1. Generiere alle möglichen Clusterings, eins nach dem anderen
2. Berechne den quadratischen Fehler
3. Wähle das Cluster mit dem kleinsten Fehler aus

Dieser Ansatz ist leider unbrauchbar: Es gibt viel zu viele mögliche Clusterings, die ausprobiert werden müssen

- Es gibt $k^n$ Möglichkeiten diese $k$ Cluster zu erzeugen bei $n$ Objekten. Davon können einige Cluster leer sein. Also für 50 Objekte und 3 Cluster gibt es $3^{50}$ Möglichkeiten

---
# K-Means Clustering
- Jedes Cluster wird durch einen Mittelpunkt (Centroid) repräsentiert
- Ein Objekt wird dem Centroid mit der geringsten Distanz zugewiesen
- Es gibt $k$ Cluster. $k$ ist ein Parameter

![[Pasted image 20240505122636.png]]

- Die initialen Centroids werden normalerweise zufällig ausgewählt. Dadurch können verschiedene Durchläufe auf den gleichen Daten unterschiedliche Cluster erzeugen
- Als Distanzmaß wir z.B. die Euklidische Distanz benutzt
- Der K-Menas-Algorithmus konvergiert
- Komplexität ist $O(n\times k\times I \times d)$ $n$ = Anzahl der Objekte, $k$ = Anzahl Cluster, $I$ = Anzahl Iterationen, $d$ = Dimensionalität der Daten