
---
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

---
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

---
### Matrix Normalisieren

![[Pasted image 20240429195930.png]]

Nun bezieht man noch die ausgehenden Links von jedem Konten mit ein und erhält

![[Pasted image 20240429200055.png]]

Für den letzten Teil für die P-Matrix also $\frac{1}{N}$ bauen wir uns selbst eine Matrix mit den Einträgen $\frac{1}{\text{Anzahl der Knoten}}$ also:

![[Pasted image 20240429200427.png]]

---
## Startvektor
Als Startvektor nimmt man die gleiche Verteilung auf den ganzen Vektor also in dem oberen Beispiel wäre der Startvektor für 5 Knoten:
$$q^{(0)}=(0.2,0.2,0.2,0.2,0.2)$$

---
# PageRank und Anfragen
PageRank berechnet ein statisches Ranking von Webseiten und ist unabhängig von Anfragen

Eine Möglichkeit PageRank und "TF$*$IDF " Scores zu kombinieren ist die einfache Linearkombination:
$$a\times sim(q,d)+(1-\alpha)\times PR(d)$$



