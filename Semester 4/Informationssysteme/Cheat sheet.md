
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
- __Rücksetzbare Historien (RC)__ TA darf erst committen, wenn alle TAs, von denen sie gelesen hat, beendet sind.
- __Historien ohne kaskadierendes Rücksetzen (ACA)__ Es dürfen nur Änderungen von abgeschlossenen TAs gelesen werden.
- __Strikte Historien__ Geänderte Daten nicht-abgeschlossener TAs dürfen weder gelesen noch überschrieben werden.
- __serialisierbar__ ist wenn der Konfliktgraph keine Zykle enthält 

![[Pasted image 20240724144921.png]]

---
## Jaccard-Koeffizient
Die __k-shingles__ eines Dokuments werden $S(d_{i})$ genannt

Beispiel:

Dokument mit den Worten $\lbrace a,b,b,c\rbrace$ wäre der $2-shingle$ dieses Dokuments $\lbrace ab,bb,bc\rbrace$ 

$$sim(d_{1},d_2)=\frac{|S(d_{1})\cap S(d_{2})|}{|S(d_{1}\cup S(d_2)|}$$
---
## Zwei Phasen Sperrprotokol ($2$PL)
Ein sperrprotokol ist zweiphasig (2PL) wenn alle Locks $q_il$ vor den Unlocks $q_iu$ kommen  
2Pl erzeugt nur serialisierbare Historien $\implies$ 2PL garantiert Serialisierbarkeit 

![[Pasted image 20240725115333.png]]

## Konservatives $2$PL
Unter konservativen 2PL fordert der TA alle Locks an bevor der erste Read oder Write Befehl kommt das heißt Preclaiming. Schwierig da man am Anfang wissen muss welche Locks benötigt werden

![[Pasted image 20240725115804.png]]

## Striktes $2$PL
Bei striktem 2PL werden alle exklusiven Locks also Write Locks bis zum Ende gehalten. Wird am häufigsten eingesetzt da striktes 2Pl serialisierbare und strikte Historien erzeugt

## Starkes $2$PL
Anders als bei Strikten 2Pl werden hier alle Locks bis zur Terminierung gehalten

![[Pasted image 20240725120759.png]]

### Locks 
Wenn kein Lock auf einem Objekt ist darf man ein Read Lock oder Write Lock setzten. Auf eine Read Lock dürfen mehrere Read Locks gesetzt werden aber kein Write Lock. Ein Write Lock darf nur gesetzt werden wenn kein Lock auf dem Objekt ist und auf ein Write Lock dürfen keine weitern Locks gesetzt werden.

![[Pasted image 20240725121635.png]]

---
## LSI
Man nimmt die Anfrage $q$ 
$$q\rightarrow U_{k}^{T}q=q'$$
Die Eignung(Score) der Dokumente wird dann im Topic-Raum berechnet durch die Cosinus-Ähnlichkeit oder das Skalarprodukt von $q'$ und den Spalten der Matrix $V_{k}^{T}$ 

Um eine Matrix zu transposen  werden die Spalten zur Zeile also:
$$\begin{pmatrix} 1&2 \\ 4&3\end{pmatrix}$$
$$\begin{pmatrix} 1&4 \\ 2&3\end{pmatrix}^T$$

---
# K-Means Clustering
- Jedes Cluster wird durch einen Mittelpunkt (Centroid) repräsentiert
- Ein Objekt wird dem Centroid mit der geringsten Distanz zugewiesen
- Es gibt $k$ Cluster. $k$ ist ein Parameter

![[Pasted image 20240505122636.png]]

- Die initialen Centroids werden normalerweise zufällig ausgewählt. Dadurch können verschiedene Durchläufe auf den gleichen Daten unterschiedliche Cluster erzeugen
- Als Distanzmaß wir z.B. die Euklidische Distanz benutzt

---
# Markov-Ketten
Markov-Ketten sind __gedächtnislos__ und __zeithomogen__

>[!Important]
>Man sagt eine Markov-Kette ist **ergodisch** falls sie irreduzibel, positiv rekurrent und aperiodisch ist.
>__Theorem__: Falls eine Markov-Kette endlich und ergodisch ist, dann existiert eine stationäre Zustandsverteilung $\pi$
### Beispiel:
Wie wird das Wetter morgen sein, wenn es heute regnet?

![[Pasted image 20240429192344.png]]

$P_{ij}$ ist die Wahrscheinlichkeit, dass der folgende Tag vom Typ $j$ ist, wenn der heutige Tag vom Typ $i$ ist.

Wenn man zum Beispiel den heutigen Tag als Vektor darstellt in dem Fall ein Sonniger Tag $x_{0}=(1, 0)$ 
Dann ist das Wetter am nächsten Tag :
$$x_{1}=x_{0}\cdot P=(1,0)\cdot \begin{pmatrix}0.9&0.1\\0.5&0.5\end{pmatrix}=(0.9,0.1)$$
---
## Levenshtein
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

---
## Hamming-Editier-Distanz
Die Hamming-Editier-Distanz beschreibt die Anzahl an Positionen an denen die beiden Strings x und y verschieden sind, dabei werden kürzere String mit "NULL" aufgefüllt

Beispiel:
- $d(car,cat) = 1$
- $d(house,hot) = 3$
- $d(house,hoouse)= 4 \leftarrow$ sehr hohe Distanz für kleinen Fehler

---
## Längste Gemeinsame Teilsequenz
Eine Teilsequenz ist eine Sequenz, die von einer anderen Sequenz durch weglassen von Zeichen aber unter Beibehaltung der Reihenfolge der Zeichen entsteht.
$$d_{(x,y)}= max(|x|,|y|)-max_{(s\in S(x,y))}|S|$$
wobei $S_{(x,y})$ die Menge aller gemeinsamer Teilsequenzen von x und y ist.

Beispiel:
- $d(house,huse)=1$
weil $max(|house|,|huse|)=5$ (Längstes Wort) und $max_{(s\in S(x,y))}|4|$ (Längste Gemeinsame Teilsequenz) also ist die Distanz $1$.

---
## Itemsets
- Ein Itemset ist eine Menge von Objekten
	- Eine Transaktion $t$ ist ein Itemset mit dazu gehöriger Transaktions ID $t=(tid,I)$, wobei $I$ das Itemset der Transaktion ist

- Der Support von Itemset $X$ in einer Datenbank $D$ ist die Anzahl der Transaktionen in $D$, die $X$ enthalten
	$$Supp(X,D)=\lbrace t\in D:t\ enthält\ X\rbrace$$
- Die __relative Häufigkeit__ von Itemset $X$ in Datenbank $D$ ist:
$$supp(X,D)/|D|$$
## Assoziationsregeln
Support einer Regel
$$supp(X \rightarrow Y,D)=supp(X\cup Y,D)$$
Konfidenz der Regel
$$conf(X\rightarrow Y,D)=supp(X\cup Y,D)/supp(X,D)$$
Die Konfidenz ist die bedingte Wahrscheinlichkeit, dass eine Transaktion $Y$ enthält, wenn sie $X$ enthält

---
