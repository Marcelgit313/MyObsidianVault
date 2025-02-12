### Essence Machine learning
- pick a family of parameterized functions $y^{\overrightarrow{w}}$ with $a$ parameter vector $\overrightarrow{W}$
- Define an error/cost function $E$ on all points $x_{i}$, their correct classes $t_{i}$ and the classifier outputs $y^{\overrightarrow{w}}$ 
- find $\overrightarrow{W}_{opt}$ that minimizes $E$ on a given trainings sample $X$ 

$$E(X,t,y^{\overrightarrow{w}})=\sum_{x_{i}\in X} E(x_{i},t_{i},y^{\overrightarrow{w}}(x_{i}))$$
$$W_{opt}=min(E(X,t,y^{\overrightarrow{w}})$$
---
### Machine Learning as programing paradigm
- Spezifizieren die Semantik von $f$ indirekt durch Datensatz $X$ und Fehlerfunktion $E$
- Repräsentieren von $f$ in parametriesierter Form $K$  Parameter $\pi_{1},. . .,\pi_{k}$
- Optimierungsalgorithmus der Werte $\pi_{1},. . . \pi_{k}$ findet, die $L,E$ mit Respekt auf $X$ minimieren

---
### Fundamentale Limit von Machine learning
- das die Beispiel Daten richtig Klassifiziert sind
	- the assumption about he hypthesis class is correct
- das Trainings Set ist korrekt
	- trainings data is "perfect" (no noise)

![[Pasted image 20250212115630.png]]

---
### Overfitting, Underfitting und Generalization

![[Pasted image 20250212115755.png]]

---

