
---
![[Pasted image 20240516103639.png]]

---
## Klassendiagramm

![[Pasted image 20240516104326.png]]
Bemerkungen:
- Bei den Attributen handelt es sich um sogenannte Instanzattribute, d.h. sie gehören zu den Instanzen einer Klasse (nicht zur Klasse selbst)

- Mehrstellige Operationen mit Rückgabewert, werden mit ihren Typen folgendermaßen notiert:
![[Pasted image 20240516104628.png]]



---
# Sichtbarkeiten in Java
![[Pasted image 20240516104225.png]]![[Pasted image 20240516104254.png]]
- Sie ist beispielsweise nützlich, um in aufwendigeren Paketen intern zugängige Hilfsklassen zu realisieren, die außerhalb des Pakets nicht sichtbar sind

---
# Generalisierung/Spezialisierung/Überladung/Überschreiben
![[Pasted image 20240516104758.png]]
### Generalisierung/Spezialisierung
- Die Klasse _ColoredSquare_ spezialisiert die Klasse Square
- Die Klasse _Square_ generalisiert die Klasse ColoredSquare
- In dieser Situation nennt man _Square_ __Superklasse__ und _ColoredSquare_ __Subklasse__
- Da die Subklasse die Attribute, Operationen und Assoziationen der Superklasse erbt (und diesen noch weitere hinzufügen kann), spricht man auch von __Vererbung__

### Überladung/Überschreiben
- Die Funktion $draw()$ wird in der Klasse ColoredSquare überschrieben, da diese schonmal in Square implementiert wurde
	- Beim Überschreiben von Funktionen ist es auch erlaubt die Sichtbarkeit zu ändern
	- Es ist in der UML auch erlaubt die Funktion beim überschreiben umzubenennen aber das muss dann im Diagramm angegeben werde
- Die Funktion $modify()$ ist überladen das diese zweimal in ColoredSquare implementiert wird aber mit verschiedenen Signaturen. Welche Funktion aufgerufen wird entscheidet sich durch die gegebenen Argumente
