
---
# Boolesches Modell
In dem Booleschen Modell gibt es eine Term-Dokument-Matrix in der alle Dokumente in der Spalte stehen und in den Zeilen stehen die Terme also die Wörter. Als Beispiel Dokument Rapunzel und als ein Term Vater. Wenn die Terme im Dokument vorkommen steht im dazu gehörigem Feld eine $1$ ansonsten eine $0$.

![[Pasted image 20240423150621.png]]

- **Boolesche Operatoren:** AND, OR, NOT
- Anfragen können verschieden kompliziert verschachtelte Konstrukte aus den Operatoren sein
- Das Ergebnis ist eine **nicht geordnete Menge** von Dokumenten, die diese Anfrage erfüllen

-> nicht die beste Methode weil das erste Ergebnis nicht das beste ist

---
## Häufigkeit
Wenn man anstatt wie im Booleschen Modell nur erfasst ob ein Term im Dokument ist wird hier die Häufigkeit des Term im Dokument erfasst, wodurch man auch eine geordnete Menge erstellen könnte.

![[Pasted image 20240423150543.png]]

---
# Vektorraummodell
- Boolesches Modell hat keine Möglichkeit Resultate nach Güte zu Ordnen, was bei großen Datenmengen wie bei Google ein Problem ist

Im Vektorraummodell wird **jedes Dokument als v-dimensionaler Vektor** betrachtet, wobei $v$ = |V| die Anzahl an Worten ist. Das heißt eine Dimension pro Wort.

Bsp.: $d_{7}= \langle 1,0,19,10,1,0,2\rangle$ 

Ebenso wird die Anfrage als Vektor ausgedrückt, z.B. die Anfrage {Zwerg, Gold} entspricht dem Vektor $q=c 

---
## Vektorraummodell: Kosinus-Ähnlichkeit
>[!Importent] Die Kosinus Ähnlichkeit zwischen zwei Vektoren $q$ und $p$ ist der Kosinus des Winkels zwischen den Vektoren

![[Pasted image 20240423151746.png]]


$$sim(q,d)=\frac{q\cdot d}{||q||\cdot||d||}$$

Mit $d=\langle 1,0,19,10,1,0,2\rangle$ und $q=\langle 1,0,19,10,1,0,2\rangle$ haben wir $q\cdot d=12$ , $||d||= \sqrt{467}$ und $||q||=\sqrt{2}$ dann erhalten wir $sim(q,d)= 0.392652$ 

---
# TF * IDF
>[!Important] Termfrequenz *$tf_{t,d}$* als die Anzahl des Auftreten von Term $t$ in Dokument $d$, also die Häufikeit

- **Dokumentfrequenz** $df_{t}$ als die Anzahl der Dokumente, in denen Term t auftritt
- *Inverse Dokumentfrequenz* $idf_{t}$ als $$idf_{t}= \frac{|D|}{df_{t}}$$wobei |D| die Anzahl der Dokumente in der Kollektion sind. Dadurch bekommt man eine Gewichtung für Terme die seltener sind z.B. 

- ein Term der in jedem Dokument ist hat ein $idf_{t}=1$
- ein Term der nur in jedem 2. Dokumente ist hat ein $idf_{t}=2$ 

Das Gewicht von Term $t$ in Dokument $d$ ist dann definiert als 
$$tf.idf_{t,d}=tf_{t,d}\times idf_{t}$$
Beobachtung: $tf.idf_{t,d}$ ist .

