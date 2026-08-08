
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
