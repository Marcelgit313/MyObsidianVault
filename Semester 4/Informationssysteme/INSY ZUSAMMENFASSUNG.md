
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
# Precision@k
Precision@k ist die Precision, die in der ersten $k$ Ergebnisse erreicht wird, also wenn 5 relevante Dokumente in den ersten 10 Dokumenten ist dann
$$Precision@10=\frac{5}{10}=\frac{1}{2}=0.5$$

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

## Operationen im Topic-Raum
Wir können eine Anfrage aus dem $m$-dimensionalen Term-Raum in den k-dimensionalen Topic-Raum abbilden durch
$$q\rightarrow U_{k}^{T}q=q'$$
Die Eignung(Score) der Dokumente wird dann im Topic-Raum berechnet durch die Cosinus-Ähnlichkeit oder das Skalarprodukt von $q'$ und den Spalten der Matrix $V_{k}^{T}$ 

---
# PageRank
PageRank sagt, dass eine Webseite $v$ wichtig ist, wenn viele wichtige Seiten auf $v$ verweisen

![[Pasted image 20240429190356.png]]

---
# Random-Surfer-Modell(User)
- folgt zufällig den Links, die von einer Seite ausgehen, mit Wahrscheinlichkeit $(1-\varepsilon)$ 
- springt zu einer zufällig ausgewählten Seite, mit Wahrscheinlichkeit $\varepsilon$ 

__Intuition__: Wichtige Webseiten werden häufiger besucht, da sie öfter verlinkt sind

$$PR(p)=(1-\varepsilon)\times \sum\limits_{q\rightarrow p}\frac{PR(q)}{out(q)}+\varepsilon \times \frac{1}{N}$$
- Die Komponente $\sum\limits_{q\rightarrow p}\frac{PR(q)}{out(q)}$ entspricht dem zufälligen Folgen von Links
- Die Komponente $\frac{1}{N}$ entspricht dem zufälligen Einfügen von Links in die Browser Suchzeile
- $out(q)$ ist die Anzahl der von $q$ ausgehenden Links("outdegree")

---
# Markov-Ketten
Markov-Ketten sind __gedächtnislos__ und __zeithomogen__

>[!Important]
>Man sagt eine Markov-Kette ist **ergodisch** falls sie irreduzibel, positiv rekurrent und aperiodisch ist.
>__Theorem__: Falls eine Markov-Kette endlich und ergodisch ist, dann existiert eine stationäre Zustandsverteilung $\pi$ 

zum Beispiel besitzt die Markov-Kette für den PageRank diese Eigenschaften

### Beispiel:
Wie wird das Wetter morgen sein, wenn es heute regnet?

![[Pasted image 20240429192344.png]]

$P_{ij}$ ist die Wahrscheinlichkeit, dass der folgende Tag vom Typ $j$ ist, wenn der heutige Tag vom Typ $i$ ist.

Wenn man zum Beispiel den heutigen Tag als Vektor darstellt in dem Fall ein Sonniger Tag $x_{0}=(1, 0)$ 
Dann ist das Wetter am nächsten Tag :
$$x_{1}=x_{0}\cdot P=(1,0)\cdot \begin{pmatrix}0.9&0.1\\0.5&0.5\end{pmatrix}=(0.9,0.1)$$

# Markov-Ketten beim PageRank

![[Pasted image 20240429194708.png]]

Um jetzt $\pi$ auszurechnen multipliziert man $\pi^{(0)}$ mit $P$ also:
$$\pi = (0.25,0.125,0.25,0.1875,0.1875)$$
### Berechnung von $\pi$ mit "Power Iteration"-Methode
Idee: Berechne schrittweise Zustandsverteilungen $\pi$ bis diese konvergiert

__Algorithmus__:
- wähle initiale Zustandsverteilung $\pi^{(0)}$ 
- berechne $\pi^{(k)}=\pi^{(k-1)}\cdot P$ bis zur Konvergenz
- gebe $\pi$ aus

Wir berechnen hier also einen Linkseigenvektor

### Matrix Normalisieren

![[Pasted image 20240429195930.png]]

Nun bezieht man noch die ausgehenden Links von jedem Konten mit ein und erhält

![[Pasted image 20240429200055.png]]

Für den letzten Teil für die P-Matrix also $\frac{1}{N}$ bauen wir uns selbst eine Matrix mit den Einträgen $\frac{1}{\text{Anzahl der Knoten}}$ also:

![[Pasted image 20240429200427.png]]

## Startvektor
Als Startvektor nimmt man die gleiche Verteilung auf den ganzen Vektor also in dem oberen Beispiel wäre der Startvektor für 5 Knoten:
$$q^{(0)}=(0.2,0.2,0.2,0.2,0.2)$$

## PageRank und Anfragen
PageRank berechnet ein statisches Ranking von Webseiten und ist unabhängig von Anfragen

Eine Möglichkeit PageRank und "TF$*$IDF " Scores zu kombinieren ist die einfache Linearkombination:
$$a\times sim(q,d)+(1-\alpha)\times PR(d)$$

---
# Itemset Mining
### Warenkorbanalyse
Welche Objekte werden häufig zusammen gekauft?
Können wir Regeln angeben der Form: Kunden die Windeln kaufen, kaufen auch oft Bier

![[Pasted image 20240502102931.png]]
- Ein Itemset ist eine Menge von Objekten
	- Eine Transaktion $t$ ist ein Itemset mit dazu gehöriger Transaktions ID $t=(tid,I)$, wobei $I$ das Itemset der Transaktion ist

- Der Support von Itemset $X$ in einer Datenbank $D$ ist die Anzahl der Transaktionen in $D$, die $X$ enthalten
	$$Supp(X,D)=\lbrace t\in D:t\ enthält\ X\rbrace$$
- Die __relative Häufigkeit__ von Itemset $X$ in Datenbank $D$ ist:
$$supp(X,D)/|D|$$
--- 
## Assoziationsregeln
Support einer Regel
$$supp(X \rightarrow Y,D)=supp(X\cup Y,D)$$
Konfidenz der Regel
$$conf(X\rightarrow Y,D)=supp(X\cup Y,D)/supp(X,D)$$
Die Konfidenz ist die bedingte Wahrscheinlichkeit, dass eine Transaktion $Y$ enthält, wenn sie $X$ enthält

---
## Ein naiver Algorithmus
Betrachte jedes mögliche Itemset und teste ob es häufig ist.

Berechnen des Support dauert $O(|I|\times |D|)$ und es gibt $2^{|I|}$ mögliche Itemsets, also im Worstcase: $O(|I|\times|D|\times 2^{|I|})$ 

---
# Apriori Algorithmus
### Prinzip
![[Pasted image 20240505115546.png]]

![[Pasted image 20240505115618.png]]

## Anti-Monotonie
Sei $I$ eine Menge von Items und sei $J=2^{I}$ die Potenzmenge von $I$. Ein Maß $f$ ist __monoton__
$$\forall X.Y \in J:(X\subseteq Y)\implies f(X)\leq f(Y)$$
Im Gegensatz, $f$ ist __anti-monoton__ falls
$$\forall X.Y \in J:(X\subseteq Y)\implies f(Y)\leq f(X)$$
Der Support ist __anti-monoton__ 

---
# Clustering und K-Means Algorithmus

Gegeben eine Menge von Objekten. Ziel: Finden eines guten Clusterings der Objekten anhand ihrer Eigenschaften

![[Pasted image 20240505121045.png]]

# Clustering-Problem
- Gegeben eine Menge $U$ von Objekten und eine Distanzfunktion $d:U\times U\rightarrow \mathbb{R}^{+}$  
- gleiche Objekte müssen eine möglichst kleine Distanz zueinander haben
- unterschiedliche Objekte müssen eine große Distanz zwischen anderen haben

# Partitionen und Prototypen
Es wird nur __exklusives Clustering__ betrachtet, d.h. ein Objekt ist genau einem Cluster zugeordnet

- Jedes Cluster $C_i$ wird von einem sogenannten Prototypen $\mu$ repräsentiert

# Naiver (Brute-Force) Ansatz
1. Generiere alle möglichen Clusterings, eins nach dem anderen
2. Berechne den quadratischen Fehler
3. Wähle das Cluster mit dem kleinsten Fehler aus

Dieser Ansatz ist leider unbrauchbar: Es gibt viel zu viele mögliche Clusterings, die ausprobiert werden müssen

- Es gibt $k^n$ Möglichkeiten diese $k$ Cluster zu erzeugen bei $n$ Objekten. Davon können einige Cluster leer sein. Also für 50 Objekte und 3 Cluster gibt es $3^{50}$ Möglichkeiten

## K-Means Clustering
- Jedes Cluster wird durch einen Mittelpunkt (Centroid) repräsentiert
- Ein Objekt wird dem Centroid mit der geringsten Distanz zugewiesen
- Es gibt $k$ Cluster. $k$ ist ein Parameter

![[Pasted image 20240505122636.png]]

- Die initialen Centroids werden normalerweise zufällig ausgewählt. Dadurch können verschiedene Durchläufe auf den gleichen Daten unterschiedliche Cluster erzeugen
- Als Distanzmaß wir z.B. die Euklidische Distanz benutzt
- Der K-Menas-Algorithmus konvergiert
- Komplexität ist $O(n\times k\times I \times d)$ $n$ = Anzahl der Objekte, $k$ = Anzahl Cluster, $I$ = Anzahl Iterationen, $d$ = Dimensionalität der Daten

---
# Datenbanksysteme
## Entity/Relationship Modellierung (ER-Modell)
- Entität -> Entitätstyp
- Beziehung -> Beziehungstyp
- Attribut
- Schlüssel
- Rolle

![[Pasted image 20240509141456.png]]

Abbilden des ER-Modells in Relationen:

Zum Beispiel:
- Kunden(ID, Telefon, Adresse, Name)
- Kaufen(Wert, Datum, Preis, Verkäufer, Auto, Kunde)
- Verkaufen(Datum, Wert, Kommission, Kunde, Auto, Verkäufer)

oder...
- Studenten(Name, Matrikel-Nummer, Semester)
- Hören(MatrNR, VorlNr)

---
## Relationale Algebra
- Selektion $\sigma$
- Projektion $\pi$ 
- Kreuzprodukt $\times$
- Join (Verbund) $\bowtie$
- Umbenennung $p$
- Differenz -
- ...

---
# SQL
_Deklarative Anfragen_
- Benutzer beschreiben WAS sie haben möchten
- .. und nicht WIE es berechnet werden soll
- Kein Wissen über die Implementierung erforderlich, d.h. wie und wo die Daten gespeichert sind
$\rightarrow$ weniger anfällig für Fehler

## Integritätsbedingungen
- ... sind ein zusätzliches Sicherheitssystem
- Ziel: Dateninkonsistenzen vermeiden
- Strategie: versuche zu verhindern, dass inkonsistente Daten in die DB eingefügt werden
- Bedingungen an die mögliche Ausprägungen der Datenbank
---
## Normalformen
Vermeiden von Redundanzen
- Regeln für eine guten relationalen Entwurf
- z.B. Este Normalform: keine Mengenwertige Attribute
	- keine Mengen in Attributs Feldern ${1,2,3,4}$ ist nicht erlaubt für jede zahl muss ein eigenes Attribute Feld entstehen

---
## B+ Baum
Lesen geschieht nicht bitweise sondern in ganzen Blöcken
Also, viel besser als binär Bäume

??????

---

## Anfragenoptimierung

- "nach unten schieben" von Selektion
- Reihenfolge von Verbundoperatoren

??????