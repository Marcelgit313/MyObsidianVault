
---
# Entity/Relationship Modellierung (ER-Modell)
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

__Relationale Algebra__
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
# Normalformen
Vermeiden von Redundanzen
- Regeln für eine guten relationalen Entwurf
- z.B. Este Normalform: keine Mengenwertige Attribute

---
# Fehler-Modell
ACID-Paradigma
- Atomarität
- Konsistenz
- Isolation
- Dauerhaftigkeit

---
# B+ Baum
Lesen geschieht nicht bitweise sondern in ganzen Blöcken
Also, viel besser als binär Bäume