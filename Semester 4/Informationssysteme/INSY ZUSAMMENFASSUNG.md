
---
## Was ist ein Dokument?
Ein Dokument ist in einem vereinfachten Textformat wie ASCII oder UTF-8, wenn dies nicht der fall ist muss es konvertiert werden aus z.B. PDF, Word, HTML

---
## Tokenisierung (Tokenization)
- Beim Tokenisieren wird Text in einzelne Tokens aufgeteilt
- Wir betrachten ganz allgemein Terme, normalerweise einfache Worte, die mögliche noch normalisiert sind
![[Bildschirmfoto 2024-04-22 um 16.03.10.png]]

### Mögliche Probleme
- can‘t $\rightarrow$ can t , man müsste das Word als ein Token nehmen oder umformen in can not
- Webadressen
- Los Angeles Identität feststellen um es als ein Wort zu sehen
- Oder Sprachen die kein Leerzeichen haben

---
## Stopwörter
- Stopwörter sind sehr häufig auftretende Wörter, die somit kaum oder keine Information enthalten
- daher werden sie oft ignoriert
- Beispiel: ein, der , die, das

---
## Stammformreduktion
Verschiedene Varianten eines Wortes können zusammen betrachtet werden, z.B. Plural, Adverbien, verschiedene Zeitformen

Beispiel:

kaufen -> kauf , käufer -> kauf , knives -> knife

Idealerweise werden Varianten eines Wortes auf die gleiche Grundform reduziert

---
## Tippfehler
- Oft enthalten von Benutzer geschriebene Texte **Tippfehler**
- Dafür braucht man ein Distanzmaß auf Zeichenketten
- Dies sollte berücksichtig werden
	- Extra Zeichen
	- Vergessene Zeichen
	- Fehlerhafte Zeichen

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
Eine gemeinsame Teilsequenz zweier Strings x und y ist ein String s, so dass alle Zeichen von s in x und y in der gleichen Reihenfolge auftreten (aber eben nicht notwendigerweise zusammenhängend)

$$d_{(x,y)}= max(|x|,|y|)-max_{(s\in S(x,y))}|S|$$
wobei $S_{(x,y})$ die Menge aller gemeinsamer Teilsequenzen von x und y ist.

Beispiel:
- $d(house,huse)=1$
weil $max(|house|,|huse|)=5$ (Längstes Wort) und $max_{(s\in S(x,y))}|4|$ (Längste Gemeinsame Teilsequenz) also ist die Distanz $1$.

---
## Levenshtein Editier Distanz
>[!Important]
>Levenshtein-Editier-Distanz zwischen zwei Strings $x$ und $y$ ist die minimale Anzahl von Änderungsoperationen $insert$, $replace$, $delete$, die benötigt werden um $x$ in $y$ zu transformieren
>\
>Gelöst mit Hilfe von Dynamischer Programmierung


![[Pasted image 20240423131652.png]]

#### Laufzeit
Die Levenshtein-Distanz kann mittels dynamischer Programmierung in $O(|x|\cdot|y|)$ berechnet werden.

Anmerkung: Die Kosten können sich für die verschiedenen Operationen unterscheiden.
### Initialisierung
![[Pasted image 20240423132128.png]]

### Berechnung
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
# TF\*IDF
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
## TF * IDF
>[!Important] Termfrequenz *$tf_{t,d}$* als die Anzahl des Auftreten von Term $t$ in Dokument $d$, also die Häufikeit

- **Dokumentfrequenz** $df_{t}$ als die Anzahl der Dokumente, in denen Term t auftritt
- *Inverse Dokumentfrequenz* $idf_{t}$ als $$idf_{t}= \frac{|D|}{df_{t}}$$wobei |D| die Anzahl der Dokumente in der Kollektion sind. Dadurch bekommt man eine Gewichtung für Terme die seltener sind z.B. 

- ein Term der in jedem Dokument ist hat ein $idf_{t}=1$
- ein Term der nur in jedem 2. Dokumente ist hat ein $idf_{t}=2$ 

Das Gewicht von Term $t$ in Dokument $d$ ist dann definiert als 
$$tf.idf_{t,d}=tf_{t,d}\times idf_{t}$$
Beobachtung: $tf.idf_{t,d}$ ist ...
- größer falls $t$ oft in $d$ auftritt
- kleiner falls $t$  nicht oft in $d$ auftritt und/oder $t$ in vielen Dokumenten auftritt

Nun können wir im Vektorraummodell die einzelnen Komponenten der Vektoren bestimmen
$$d_{t}=tf.idf_{t,d}$$
$$q_{t}=tf.idf_{t,q}$$
Eine einfachere Möglichkeit die Güte von Dokument $d$ zu berechnen ist durch eine einfache Summe der einzelnen $tf.idf$ Werte:
- Alternative zur Kosinus-Ähnlichkeit

$$score(q,d)= \sum\limits_{t\in q}tf.idf_{t,d}$$

---
# Dämpfung, Längennormalisierung etc.

## Logarithmische Dämpfung der inverse Dokumentfrequenz
$$idf_{t}=\log \frac{|D|}{df_{t}}$$
Mit dem Logarithmus flachen die Spitzen der sehr seltnen Terme ab also erhalten die sehr exotischen Terme nicht zu viel Gewicht.

## Sublineare Skalierung der Termfrequenz
$$wf_{t,d}=\begin{cases}1+\log tf_{t,d}\text{ falls } tf_{t,d}>0 \\
0\text{ sonst}\end{cases}$$
### Längennormalisierung und max-tf Normalisierung
verhindert, dass sehr lange Dokumente zu sehr favorisiert werden

---
## Präzision(Precision) und Ausbeute(Recall)
Precision P ist der Anteil der relevanten Dokumente in den zurückgegebenen Dokumenten
$$P=\frac{tp}{tp+fp}$$

Recall R ist der Anteil der relevanten zurückgegebenen Dokumente an allen relevanten Dokumenten
$$R=\frac{tp}{tp+fn}$$
## F-Measure
F-measure kombiniert Precision und Recall
$$F_{\beta}=\frac{(\beta^{2}+1)P\cdot R}{\beta^{2}\cdot P+R}$$
wobei der Parameter $\beta$ zwischen Precision und Recall die Gewichtung entscheidet
- $\beta = 1$ ist balanciert
- $\beta <1$ höherer Einfluss von Precision
- $\beta > 1$ höherer Einfluss von Recall
# Average Precision (AP)
- Sei { $d_{1},....,d_{m}$ } die Menge der relevanten Dokumente der Anfrage $q$
- Sei $R_{k}$ die Menge der geordneten Ergebnisse

$$AP(q)= \frac{1}{m}\sum\limits_{d_{k}\in {d_{1},....,d_{m}}}Precision(R_{k})$$
## Mean-Average-Precision
Für die Menge $Q$ von Anfragen kann die __Mean-Average-Precision(MAP)__ berechnet werden durch
$$MAP(Q)=\frac{1}{|Q|}\sum\limits_{q\in Q}AP(q)$$

---
# Maximale Marginale Relevanz(MMR)
Das nächste zurückgegebene Dokument soll relevant sein zur Anfrage sein, aber auch verschieden zu den bislang zurückgegebenen Dokumenten
$$argmax_{d_{i\in D}}=(\lambda \cdot sim(q,d_{i})-(1-\lambda)max_{d_{j}:1<j<i}sim(d_{i},d_{j}))$$

![[Pasted image 20240428122744.png]]

---
## Jaccard-Koeffizient
Die __k-shingles__ eines Dokuments werden $S(d_{i})$ genannt

Beispiel:

Dokument mit den Worten $\lbrace a,b,b,c\rbrace$ wäre der $2-shingle$ dieses Dokuments $\lbrace ab,bb,bc\rbrace$ 

$$sim(d_{1},d_2)=\frac{|S(d_{1})\cap S(d_{2})|}{|S(d_{1}\cup S(d_2)|}$$
Wenn die Menge gleich sind ist der Wert $1$ 

Zur Berechnung der Ähnlichkeit von Text Dokumenten zwecks Duplikaterkennung werden in der Regel *k-grams* benutzt bzw *k-shingle*

Beispiel:

Dokument mit den Worten $\lbrace a,b,b,c\rbrace$ wäre der $2-shingle$ dieses Dokuments $\lbrace ab,bb,bc\rbrace$ 


---
## LSI
Betrachte __Singulärwertzerlegung__ der $m\times n$ Term-Dokument-Matrix $A$ 

![[Pasted image 20240428130548.png]]

## Singulärwertzerlegung Beispiel
![[Pasted image 20240428130723.png]]

### Rang-k Approximation
Man möchte $A$ gar nicht korrekt wiederherstellen sondern approximieren durch die Auswahl der wichtigsten Topics.

Wir wählen die k größten Singulärwerte aus $\Sigma$  aus, d.h. wir setzten die übrigen Singulärwerte auf $0$ und entsprechend die dazugehörigen Einträge in $U$ und $V^T$ 

![[Pasted image 20240428131212.png]]**Faustregel**: Es sollten etwa 90% der Summe der Quadrate der Singulärwerte erhalten bleiben