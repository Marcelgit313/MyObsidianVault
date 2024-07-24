
---
## Präzision(Precision) und Ausbeute(Recall)
Precision P ist der Anteil der relevanten Dokumente in den zurückgegebenen Dokumenten
$$P=\frac{tp}{tp+fp}$$

Recall R ist der Anteil der relevanten zurückgegebenen Dokumente an allen relevanten Dokumenten
$$R=\frac{tp}{tp+fn}$$

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
---
# TF * IDF

- **Dokumentfrequenz** $df_{t}$ als die Anzahl der Dokumente, in denen Term t auftritt
- *Inverse Dokumentfrequenz* $idf_{t}$ als $$idf_{t}= \frac{|D|}{df_{t}}$$
Das Gewicht von Term $t$ in Dokument $d$ ist dann definiert als 
$$tf.idf_{t,d}=tf_{t,d}\times idf_{t}$$
$$score(q,d)= \sum\limits_{t\in q}tf.idf_{t,d}$$

---
## ACID
- **Atomicity (A)**: Datentransaktionen, bspw. die Eintragung eines neuen Datensatzes oder das Löschen eines alten, sollen entweder ganz oder gar nicht ausgeführt werden. Für andere User ist die Transaktion erst sichtbar, wenn sie vollständig ausgeführt ist.
-  **Consistency (C)**: Diese Eigenschaft ist erfüllt, wenn jede Datentransaktion die Datenbank von einem konsistenten in einen konsistenten Zustand überführt.
- **Isolation (I)**: Wenn mehrere Transaktionen gleichzeitig stattfinden, muss der Endzustand derselbe sein, als wenn die Transaktionen getrennt voneinander stattfinden würden. Das heißt die Datenbank sollte den Stresstest bestehen. Also nicht durch Überlastung zu falschen Datenbanktransaktionen kommen.
- **Durability (D)**: Die Daten innerhalb der Datenbank dürfen sich nur durch eine Transaktion ändern und nicht durch äußere Einflüsse veränderbar sein. Ein Softwareupdate darf beispielsweise nicht versehentlich dazu führen, dass sich Daten ändern oder womöglich gelöscht werden.

---
