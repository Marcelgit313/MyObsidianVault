
---
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
