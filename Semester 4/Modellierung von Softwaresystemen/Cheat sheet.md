
---
## Modelle 
>[!Important] Modelle Definition
>Ein Modell ist eine Abstraktion, die dazu dient, ein System zu verstehen, bevor
>es gebaut wird. Weil ein Modell auf unwesentliche Details verzichtet, lässt es
>sich leichter manipulieren als das Original

- Ein Modell ist eine Vereinfachung der Realität.
- Ein bestimmtes Modell kann nicht für alles verwendet werden.
- Besseres Verständnis komplexer Systeme, die als Gesamtsystem aufgrund ihrer Komplexität nicht zu begreifen wären

### Argumente gegen Modelle
- Modelle bedeuten Zusatzaufwand
- Modelle müssen erstellt und gepflegt werden
- Quellcode muss erstellt und gepflegt werden
- Modelle veralten schnell – gepflegt wird nur der Quellcode

---
## Was bedeutet Objektorientierung?
>[!Important] Definition
>Die reale Welt besteht aus Objekten, die untereinander in Beziehung stehen.
Diese Sichtweise wird auch auf die Modellierung und Software-Entwicklung
übertragen. Objekte können – einmal erstellt – in verschiedenen Kontexten
wiederverwendet werden

### Vorteile
- Leichte Wiederverwendbarkeit dadurch, dass Daten und Funktionalität zusammen verwaltet werden und es Konzepte zur Modifikation von Code gibt (Stichwort: Vererbung)
- Nähe zur realen Welt: Viele Dinge der realen Welt können als Objekte modelliert werden.
- Verträglichkeit mit Nebenläufigkeit und Parallelität

---
## Diagramme der UML
![[Pasted image 20240729105549.png]]

---
## Programmablauf Plan (PAP)

![[Pasted image 20240729105806.png]]

---
## Nassi-Shneiderman-Diagramm (Struktogramm)

![[Pasted image 20240729110040.png]]

- Übersichtlich
- Erzwingt lineare Kontrollstrukturen
- Keine Modellierung der Daten

---
## Jackson-Structured-Programming (JSP)

![[Pasted image 20240729110605.png]]

- Struktur entspricht grob der Aufrufstruktur in der prozeduralen Programmierung
- Nur Zerlegung der syntaktischen Struktur von Daten

---
## Structured Analysis and Design Technique (SADT)

![[Pasted image 20240729110753.png]]

- Keine Darstellung der Systemumgebung
- Aufwändige Erstellung und Änderung der Diagramme
- Spezifikation der Daten nur über die Pfeilbezeichnungen
- Nur Zerlegung der syntaktischen Struktur von Daten
-  Keine Spezifikation der Kontroll-Logik

---
## Entity-Relationship-Modell

![[Pasted image 20240729111754.png]]

- Modellierung der Beziehungen zwischen Daten
- Grundlage des relationalen Datenbankentwurfs
- Optimierungskriterien (Normalformen)
- Adressiert nur die Daten, keine Kontrollstrukturen

---
## Structured Analysis (SA)

![[Pasted image 20240729112006.png]]

![[Pasted image 20240729112032.png]]

---
# UML
## Klassendiagramm

![[Pasted image 20240729112428.png]]

- Bei den Attributen handelt es sich um sogenannte __Instanzattribute__, d.h. sie gehören zu den Instanzen einer Klasse (nicht zur Klasse selbst)

![[Pasted image 20240729112642.png]]

- die Standard Sichtbarkeit in Java ist package, indem kein Modifikator angegeben wird 

### weitere Bemerkungen

![[Pasted image 20240729112859.png]]

---
## Generalisierung/Spezialisierung/Überladung/Überschreiben
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
	- beim überladen darf man in UML auch den Rückgabetypen der Funktion ändern

---
## Assoziation
- schwächste Relation

![[Pasted image 20240729113443.png]]

### Multiplizitäten

![[Pasted image 20240729113643.png]]

---
## Aggregation

![[Pasted image 20240729114220.png]]

- die leeren Kästchen heißen das das Menü auch ohne ein Hauptspeise existieren kann

---
## Komposition
- stärkste Relation

![[Pasted image 20240729131247.png]]

- das ausgefüllte Kästchen steht dafür das es einen Raum gegeben muss sonst kann das Restaurante nicht existieren

---
## Mehrfachvererbung
Es ist auch möglich das eine Klasse von verschiedenen Klassen erbt das nennt man Mehrfachvererbung

---
## late binding und Polymorphismus

late binding:
- Polymorphismus und spätes Binden (late binding) sind untrennbar verbunden.
-  Ist zur Übersetzungszeit die Klasse des Objekts nicht bekannt, dann kann noch nicht bestimmt werden, welche Methode ausgeführt wird.
-  Spätes Binden: Methode wird erst zur Ausführungszeit an ein bestimmtes Objekt gebunden

Polymorphismus:
- Polymorphismus ermöglicht es, den gleichen Namen für gleichartige Operationen zu verwenden, die auf Objekten verschiedener Klassen auszuführen sind.
-  Der Sender muss nur wissen, dass ein Empfängerobjekt das gewünschte Verhalten besitzt

---
## Objektdiagramme

![[Pasted image 20240729132346.png]]

Man dar auch Aggregationen benutzten im Objektdiagramm:

![[Pasted image 20240729132440.png]]

---
## Übersetzung und Konsistenzprobleme

![[Pasted image 20240729133436.png]]

---
## Aktivitätsdiagramme








