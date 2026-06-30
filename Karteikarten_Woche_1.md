# Karteikarten Woche 1: Informationssysteme

Format: Frage vorne, Antwort hinten. Ziel fuer Woche 1: Begriffe sicher erklaeren und einfache Aufgaben starten koennen.

## Warm-up und Datenarten

| Vorderseite                                      | Rueckseite                                                                                                                                                                  |
| ------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Was ist ein Informationssystem?                  | Ein System zur Erfassung, Speicherung, Verarbeitung, Suche und Bereitstellung von Informationen. In der Vorlesung meist mit Fokus auf Datenbanken, Suche und Transaktionen. |
| Was ist ein Schema?                              | Die Strukturdefinition von Daten, z.B. Relationennamen, Attribute, Datentypen, Schluessel und Constraints.                                                                  |
| Was ist eine Auspraegung/Instanz einer Relation? | Die konkrete Menge von Tupeln, die zu einem Zeitpunkt in der Relation gespeichert ist.                                                                                      |

## Informationssuche

| Vorderseite                                            | Rueckseite                                                                                                                                     |
| ------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Was misst Precision?                                   | Anteil relevanter Treffer unter allen gelieferten Treffern: `Precision = relevante gelieferte Treffer / gelieferte Treffer`.                   |
| Was misst Recall?                                      | Anteil gefundener relevanter Dokumente unter allen relevanten Dokumenten: `Recall = relevante gelieferte Treffer / alle relevanten Dokumente`. |
| Was ist F1?                                            | Harmonisches Mittel aus Precision und Recall: `F1 = 2PR / (P + R)`.                                                                            |
| Kann Precision = 1 und Recall = 1 gleichzeitig gelten? | Ja. Dann wurden genau alle relevanten Dokumente und keine irrelevanten Dokumente geliefert.                                                    |
| Was ist ein Dokument in der Informationssuche?         | Die betrachtete Einheit der Suche, z.B. Webseite, Buchkapitel, PDF oder einzelner Absatz. Die Granularitaet muss festgelegt werden.            |
| Was ist Tokenisierung?                                 | Zerlegung eines Textes in Tokens, meist Woerter oder Terme.                                                                                    |
| Was ist Normalisierung bei Text?                       | Vereinheitlichung von Tokens, z.B. Kleinschreibung, Entfernen von Satzzeichen, Stemming.                                                       |

## ER-Modellierung

| Vorderseite                                 | Rueckseite                                                                                                                             |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Was ist eine Entitaet?                      | Ein eindeutig identifizierbares Objekt der realen oder modellierten Welt, z.B. Student, Buch, Bestellung.                              |
| Was ist ein Attribut?                       | Eine Eigenschaft eines Entitaets- oder Beziehungstyps, z.B. Name, Datum, Preis.                                                        |
| Was ist ein Schluessel im ER-Modell?        | Ein Attribut oder eine Attributmenge, die Entitaeten eindeutig identifiziert.                                                          |
| Was ist ein Beziehungstyp?                  | Eine Beziehung zwischen Entitaetstypen, z.B. `Student besucht Vorlesung`.                                                              |
| Was ist eine Rolle?                         | Die Funktion eines Entitaetstyps innerhalb einer Beziehung, wichtig besonders bei rekursiven Beziehungen.                              |
| Was bedeutet Kardinalitaet?                 | Beschreibt, wie viele Entitaeten eines Typs an einer Beziehung teilnehmen koennen oder muessen.                                        |
| Was bedeutet Min/Max-Notation?              | `(min,max)` gibt an, wie oft eine Entitaet mindestens und hoechstens an einer Beziehung teilnehmen muss/kann.                          |
| Was ist eine 1:1-Beziehung?                 | Jede Entitaet auf beiden Seiten ist mit hoechstens einer Entitaet der anderen Seite verbunden.                                         |
| Was ist eine 1:n-Beziehung?                 | Eine Entitaet auf der 1-Seite kann mit vielen Entitaeten der n-Seite verbunden sein; jede n-Seite gehoert hoechstens zu einer 1-Seite. |
| Was ist eine n:m-Beziehung?                 | Entitaeten beider Seiten koennen jeweils mit mehreren Entitaeten der anderen Seite verbunden sein.                                     |
| Was ist eine schwache Entitaet?             | Eine Entitaet, die keinen eigenen vollstaendigen Schluessel besitzt und ueber eine besitzende Entitaet identifiziert wird.             |
| Was ist Generalisierung/Spezialisierung?    | Modellierung von Ober- und Untertypen, z.B. `Angestellter` als Obertyp von `Professor` und `Assistent`.                                |
| Was bedeutet disjunkte Generalisierung?     | Eine Entitaet des Obertyps darf hoechstens einem Untertyp angehoeren.                                                                  |
| Was bedeutet ueberlappende Generalisierung? | Eine Entitaet des Obertyps darf mehreren Untertypen angehoeren.                                                                        |
| Was bedeutet totale Generalisierung?        | Jede Entitaet des Obertyps muss mindestens einem Untertyp angehoeren.                                                                  |
| Was bedeutet partielle Generalisierung?     | Eine Entitaet des Obertyps muss keinem Untertyp angehoeren.                                                                            |

## ER zu Relationenmodell

| Vorderseite | Rueckseite |
|---|---|
| Wie wird ein Entitaetstyp ins Relationenmodell ueberfuehrt? | Als Tabelle mit Attributen; der ER-Schluessel wird Primaerschluessel. |
| Wie wird eine 1:n-Beziehung meist umgesetzt? | Fremdschluessel der 1-Seite wird in die Tabelle der n-Seite aufgenommen; Beziehungsattribute ebenfalls auf n-Seite. |
| Wie wird eine n:m-Beziehung umgesetzt? | Durch eigene Beziehungstabelle mit Fremdschluesseln auf beide Entitaetstabellen; Kombination meist Primaerschluessel. |
| Wie wird eine 1:1-Beziehung umgesetzt? | Fremdschluessel auf einer Seite, bevorzugt auf der Seite mit totaler Teilnahme; ggf. `UNIQUE` setzen. |
| Wie wird eine schwache Entitaet umgesetzt? | Eigene Tabelle mit Fremdschluessel auf Besitzer; Primaerschluessel meist Besitzer-Schluessel plus partieller Schluessel. |
| Wie kann Generalisierung vertikal umgesetzt werden? | Obertyp-Tabelle fuer gemeinsame Attribute, Untertyp-Tabellen mit gleichem Primaerschluessel als Fremdschluessel. |
| Was ist ein Fremdschluessel? | Attribut oder Attributmenge, die auf den Primaer-/Kandidatenschluessel einer anderen Relation verweist. |
| Was bedeutet referentielle Integritaet? | Jeder Fremdschluesselwert muss auf einen existierenden Zielwert verweisen oder, falls erlaubt, `NULL` sein. |

## Relationenmodell

| Vorderseite | Rueckseite |
|---|---|
| Was ist eine Relation? | Mathematisch eine Menge von Tupeln ueber Attributen; praktisch eine Tabelle. |
| Was ist ein Tupel? | Eine Zeile einer Relation, also eine konkrete Kombination von Attributwerten. |
| Was ist ein Attribut im Relationenmodell? | Eine benannte Spalte einer Relation. |
| Was ist eine Domaene? | Wertebereich eines Attributs, z.B. Integer, Datum, String oder definierte Menge. |
| Was ist ein Primaerschluessel? | Ausgewaehlter Kandidatenschluessel, der Tupel eindeutig identifiziert und nicht `NULL` sein darf. |
| Was ist ein Kandidatenschluessel? | Minimaler Superschluessel. Entfernt man ein Attribut, ist er kein Superschluessel mehr. |
| Was ist ein Superschluessel? | Attributmenge, die jedes Tupel eindeutig identifiziert; muss nicht minimal sein. |
| Was ist ein zusammengesetzter Schluessel? | Ein Schluessel aus mehreren Attributen. |
| Was ist ein Constraint? | Eine Integritaetsbedingung, z.B. `PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, `NOT NULL`, `CHECK`. |

## Relationale Algebra

| Vorderseite | Rueckseite |
|---|---|
| Was ist relationale Algebra? | Formale Anfragesprache mit Operatoren auf Relationen; Ergebnis ist wieder eine Relation. |
| Was macht Selektion `sigma`? | Filtert Tupel nach einer Bedingung, also Zeilen. |
| Was macht Projektion `pi`? | Waehlt Attribute aus, also Spalten; unter Mengensemantik werden Duplikate entfernt. |
| Was macht Umbenennung `rho`? | Benennt Relationen oder Attribute um, wichtig bei Self-Joins. |
| Was ist das kartesische Produkt? | Kombiniert jedes Tupel der ersten Relation mit jedem Tupel der zweiten Relation. |
| Was ist ein Join? | Kombination von Relationen mit Join-Bedingung; entspricht oft Selektion ueber kartesischem Produkt. |
| Was ist ein natuerlicher Join? | Join ueber gleichnamige Attribute mit Gleichheitsbedingung; gemeinsame Attribute erscheinen nur einmal. |
| Was macht Vereinigung `union`? | Liefert alle Tupel, die in mindestens einer der beiden kompatiblen Relationen vorkommen. |
| Was macht Differenz `-`? | Liefert Tupel, die in der ersten, aber nicht in der zweiten Relation vorkommen. |
| Was bedeutet Vereinigungskompatibilitaet? | Beide Relationen haben gleiche Stelligkeit und kompatible Attributdomaenen. |
| Wofuer nutzt man Division? | Fuer "fuer alle"-Anfragen, z.B. Kunden, die alle Produkte gekauft haben. |

## SQL Basis

| Vorderseite | Rueckseite |
|---|---|
| Grundstruktur einer SQL-Anfrage? | `SELECT ... FROM ... WHERE ... GROUP BY ... HAVING ... ORDER BY ...`. |
| Unterschied `WHERE` und `HAVING`? | `WHERE` filtert Tupel vor Gruppierung; `HAVING` filtert Gruppen nach Aggregation. |
| Was macht `GROUP BY`? | Fasst Tupel mit gleichen Gruppierungsattributen zusammen, damit Aggregatfunktionen berechnet werden koennen. |
| Wichtige Aggregatfunktionen? | `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`. |
| Was zaehlt `COUNT(*)`? | Alle Tupel einer Gruppe, unabhaengig von `NULL`-Werten. |
| Was zaehlt `COUNT(attribut)`? | Nur Tupel, bei denen das Attribut nicht `NULL` ist. |
| Was macht `DISTINCT`? | Entfernt Duplikate aus dem Ergebnis. |
| Was ist ein Inner Join? | Liefert nur Kombinationen, fuer die die Join-Bedingung erfuellt ist. |
| Was ist ein Self-Join? | Eine Relation wird mit sich selbst verknuepft, meist mit Aliasnamen. |
| Wofuer nutzt man `EXISTS`? | Testet, ob eine Unteranfrage mindestens ein Tupel liefert. |
| Wofuer nutzt man `NOT EXISTS`? | Typisch fuer "keine", "nie" und "alle"-Aufgaben. |
| Warum ist `NOT IN` mit `NULL` gefaehrlich? | `NULL` kann zu unbekannten Wahrheitswerten fuehren; `NOT EXISTS` ist oft robuster. |
| Was macht `LIKE`? | Mustervergleich in Strings, z.B. `%systeme%`. |
| Was ist ein Alias? | Kurzname fuer Tabelle oder Attribut, z.B. `Studenten s`. |

## SQL DDL und Constraints

| Vorderseite | Rueckseite |
|---|---|
| Was macht `CREATE TABLE`? | Legt eine neue Tabelle mit Attributen, Datentypen und Constraints an. |
| Was bedeutet `PRIMARY KEY`? | Definiert den Primaerschluessel; impliziert Eindeutigkeit und nicht `NULL`. |
| Was bedeutet `FOREIGN KEY`? | Definiert einen Fremdschluessel auf eine andere Tabelle. |
| Was bedeutet `UNIQUE`? | Werte oder Wertkombinationen duerfen nicht mehrfach vorkommen. |
| Was bedeutet `NOT NULL`? | Das Attribut darf keinen `NULL`-Wert haben. |
| Was bedeutet `CHECK`? | Erzwingt eine Bedingung fuer Attributwerte oder Tupel. |
| Was bedeutet `ON DELETE CASCADE`? | Wird ein referenziertes Tupel geloescht, werden referenzierende Tupel automatisch mitgeloescht. |
| Was bedeutet `ON DELETE SET NULL`? | Wird ein referenziertes Tupel geloescht, wird der Fremdschluesselwert der referenzierenden Tupel auf `NULL` gesetzt. |
| Was bedeutet `ON UPDATE CASCADE`? | Aendert sich der referenzierte Schluesselwert, wird der Fremdschluesselwert automatisch angepasst. |

## Klausur-Standardmuster Woche 1

| Vorderseite | Rueckseite |
|---|---|
| Wie geht man bei einer ER-Textaufgabe vor? | 1. Entitaeten markieren. 2. Attribute und Schluessel bestimmen. 3. Beziehungen finden. 4. Kardinalitaeten setzen. 5. Sonderfaelle pruefen: schwach, ternar, Generalisierung. |
| Wie geht man bei ER -> Relationen vor? | Entitaeten zuerst, dann Beziehungen nach Kardinalitaet, dann Schluessel/Fremdschluessel/Constraints pruefen. |
| Wie geht man bei SQL-Schreibaufgaben vor? | Ergebnis sprachlich formulieren, Tabellen/Join-Pfad bestimmen, Filter setzen, Aggregation/Grouping, Sonderfaelle `EXISTS`/`NOT EXISTS`. |
| Wie erkennt man "alle"-Aufgaben in SQL? | Woerter wie "alle", "jeder", "saemtliche"; oft mit doppeltem `NOT EXISTS` loesen. |
| Wie erkennt man n:m im ER-Modell? | Beide Seiten koennen an mehreren Beziehungsausprägungen teilnehmen; Umsetzung als eigene Relation. |
| Was ist ein haeufiger Fehler bei Projektion? | Unter Mengensemantik verschwinden Duplikate; unter SQL ohne `DISTINCT` bleiben sie erhalten. |
| Was ist ein haeufiger Fehler bei Joins? | Join-Bedingung vergessen; dann entsteht kartesisches Produkt mit zu vielen Tupeln. |
| Was ist ein haeufiger Fehler bei Kardinalitaeten? | Minimum und Maximum verwechseln: Pflichtteilnahme ist Minimum, maximale Anzahl ist Maximum. |

