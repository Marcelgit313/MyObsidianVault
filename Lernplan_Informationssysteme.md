# Informationssysteme: Lernplan und Zusammenfassung

Stand: 30.06.2026

Grundlage: `skript-insy-2026.pdf` und die alten Klausuren/Gedaechtnisprotokolle in `Prüfungen/`. Die PDF von 2008 liess sich nicht sinnvoll als Text extrahieren und ist deshalb nicht inhaltlich ausgewertet.

## 1. Klausurbild: was sehr wahrscheinlich drankommt

Die Klausur ist typischerweise 120 Minuten lang, meist 120 Punkte plus 10 Bonuspunkte. Die Aufgaben sind breit gestreut; man besteht nicht durch ein einziges Lieblingsthema, sondern durch solide Punkte in vielen Bloecken.

Sehr hohe Prioritaet:

- SQL: SELECT, JOIN, GROUP BY/HAVING, EXISTS/NOT EXISTS, Mengenoperationen, Aggregation, Auswertung gegebener Queries, CREATE TABLE, Constraints, Views, Trigger, UDFs, Fensteranfragen, rekursives SQL.
- Relationale Algebra, konjunktive Anfragen, Tupel- und Domaenenkalkuel: Anfragen formulieren, Ergebnisse berechnen, Monotonie, Umformungen, Division, SQL <-> Algebra.
- ER-Modellierung und Relationenmodell: Kardinalitaeten, Schluessel, schwache Entitaeten, Generalisierung, ternaere Beziehungen, ER -> Relationen, SQL-DDL -> ER.
- Entwurfstheorie: funktionale Abhaengigkeiten, Attributhuelle, Schluessel, kanonische Ueberdeckung, Verlustlosigkeit, Abhaengigkeitserhaltung, 2NF/3NF/BCNF, 3NF-Synthese.
- Transaktionen: ACID, Anomalien, Serialisierbarkeit, Konfliktgraph, RC/ACA/ST, 2PL/striktes 2PL, Force/Steal, Undo/Redo, Recovery.
- Indexe und Puffer: B+-Baum, Einfuegen/Loeschen/Bulkloading, Fanout, LRU/LFU/FIFO, Break-even-Rechnungen, Kostenabschaetzung.

Hohe Prioritaet:

- Informationssuche und Data Mining: Precision/Recall/F1, Distanzmasse, Jaccard/Shingles, Levenshtein, TF-IDF, LSI, MMR, PageRank/Markov-Ketten, Frequent Itemsets, Support/Confidence, K-Means/Clustering.
- Anfrageoptimierung und Kosten: Operatorbaeume, Selektion/Projektion pushdown, Join-Umordnung, Kardinalitaetsabschaetzungen, Histogramme, Mengen- vs. Multimengensemantik.

Mittlere Prioritaet:

- JDBC, SQL-Injection, Prepared Statements, Trigger-Details.
- NoSQL, Big Data, CAP, Key/Value-Systeme. In den ausgewerteten Klausuren weniger dominant, aber im aktuellen Skript enthalten.
- XML/XPath/DTD: in alten Klausuren 2009-2013 sehr haeufig, in neueren Klausuren nicht mehr klar sichtbar. Lernen, falls es noch Teil des aktuellen Stoffumfangs ist.

## 2. Kompakte Themenzusammenfassung

### Informationssuche und Data Mining

Precision = relevante Treffer / gelieferte Treffer. Recall = relevante Treffer / alle relevanten Dokumente. F1 ist das harmonische Mittel. Typische Klausuraufgabe: bester/schlechtester Fall aus Korpusgroessen.

Distanzmasse: Hamming nur bei gleicher Laenge; Levenshtein per DP-Tabelle mit Einfuegen, Loeschen, Ersetzen; Jaccard ueber Token- oder Shingle-Mengen. Bei Shingles genau auf Normalisierung achten.

TF-IDF: Terme zaehlen, Dokumentfrequenz bestimmen, IDF einsetzen, Query-Score je Dokument berechnen. Fehlerquelle: Termfrequenz und Dokumentfrequenz verwechseln.

LSI: gegebene Zerlegung `A = U Sigma V^T` nutzen, Query in reduzierten Raum transformieren, Aehnlichkeit/Score berechnen. Klausuren geben meist Matrizen vor; wichtig sind saubere Zwischenschritte.

PageRank/Markov-Ketten: Uebergangsmatrix aus Graph bauen, Wahrscheinlichkeitsvektor multiplizieren, ggf. Daempfung beachten. Markov-Aufgaben fragen oft nach Zustand in ein/zwei Schritten.

Frequent Itemset Mining: Support ist anti-monoton: wenn ein Itemset nicht haeufig ist, sind alle Obermengen nicht haeufig. Confidence fuer Regeln `X -> Z\X` berechnen und Ableitungen begruenden.

K-Means/Clustering: Cluster sind Gruppen aehnlicher Punkte; Guete ueber geringe Intra-Cluster-Distanz und hohe Inter-Cluster-Trennung. K-Means: Zuordnen, Zentren neu berechnen, wiederholen.

### ER-Modellierung und Relationenmodell

Sicher beherrschen: Entitaetstyp, Beziehungstyp, Attribut, Schluessel, Rolle, Kardinalitaet, Min/Max-Notation, schwache Entitaet, partielle Funktionen, Generalisierung/Spezialisierung.

ER -> Relationen: Entitaeten werden Tabellen, 1:n meist Fremdschluessel auf n-Seite, n:m eigene Beziehungstabelle, 1:1 je nach Totalitaet, schwache Entitaeten mit Schluessel des Besitzers, Generalisierung je nach Strategie vertikal/horizontal/volle Redundanz.

Klausurtypisch sind Textaufgaben, unvollstaendige Diagramme und Aussagen zu Kardinalitaeten. Immer zuerst Entitaeten, dann Beziehungen, dann Schluessel, dann Kardinalitaeten eintragen.

### Relationale Algebra, Kalkuele, regelbasierte Anfragen

Operatoren: Selektion, Projektion, Umbenennung, Vereinigung, Differenz, kartesisches Produkt, Join, Division, Gruppierung/Aggregation falls erweitert. Uebersetzungen SQL <-> Algebra kommen regelmaessig.

Konjunktive Anfragen und Anfrageprogramme: Variablenbelegung, Gueltigkeit, Ergebnisberechnung, Monotonie. Konjunktive positive Anfragen sind monoton; Differenz/Negation macht oft nicht-monoton.

Tupel- und Domaenenkalkuel: Praedikatenlogik sauber mit Existenz- und Allquantoren formulieren. Typische Stolperfalle: "alle" korrekt mit `NOT EXISTS`/Implikation ausdruecken.

### SQL

Pflichtmuster:

- einfache Joins und Self-Joins
- `GROUP BY`, `HAVING`, `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`
- `EXISTS`, `NOT EXISTS`, `IN`, `NOT IN`
- Division/"alle"-Aufgaben
- `CREATE TABLE` mit `PRIMARY KEY`, `FOREIGN KEY`, `CHECK`, `ON DELETE/UPDATE`
- Views und Trigger/UDFs
- Fensterfunktionen: `OVER`, `PARTITION BY`, `ORDER BY`, Frames, `RANK`
- rekursives SQL: `WITH RECURSIVE ... UNION ...`

Pruefungstaktik: Bei SQL-Aufgaben erst das Ergebnis sprachlich formulieren, dann Join-Pfad bauen, dann Filter, dann Aggregation. Bei "nie"/"alle" fast immer mit `NOT EXISTS` arbeiten.

### Entwurfstheorie

Funktionale Abhaengigkeit `X -> Y`: gleiche Werte auf X erzwingen gleiche Werte auf Y. Attributhuelle `X+`: alle Attribute, die aus X ableitbar sind.

Schluessel: Superschluessel bestimmt alle Attribute; Kandidatenschluessel ist minimaler Superschluessel. Eine Attributhuelle kann Superschluessel zeigen, aber Kandidatenschluessel braucht Minimalitaetspruefung.

Kanonische Ueberdeckung: rechte Seiten zerlegen, links/rechts extraneous Attribute entfernen, redundante FDs entfernen.

Verlustlosigkeit: Zerlegung darf beim natuerlichen Join keine falschen Tupel erzeugen. Fuer `R -> R1, R2` hinreichend: `(R1 Schnitt R2) -> R1` oder `(R1 Schnitt R2) -> R2`.

Normalformen: 2NF gegen partielle Abhaengigkeiten von Nicht-Schluesselattributen, 3NF erlaubt rechte Seite als Primattribut oder linke Seite als Superschluessel, BCNF fordert fuer jede nichttriviale FD links einen Superschluessel.

### Anfrageoptimierung und Kosten

Regeln: Selektionen aufbrechen und nach unten schieben, Projektionen frueh einsetzen, kartesische Produkte mit Selektion zu Joins kombinieren, Join-Reihenfolge optimieren, gemeinsame Teilausdruecke beachten.

Kostenabschaetzung: Kardinalitaeten, Selektivitaeten, Histogramme, Min/Max-Ergebnisse. Bei Mengen vs. Multimengen genau pruefen: viele Algebra-Gesetze gelten unter Bag-Semantik nicht unveraendert.

### Puffer und Indexe

Pufferstrategien:

- FIFO: aelteste Seite raus.
- LRU: am laengsten nicht benutzt raus.
- LFU: am seltensten benutzt raus; Tie-Breaker beachten, falls angegeben.

B+-Baum: Daten in Blaettern, innere Knoten enthalten Separatoren, alle Blaetter auf gleicher Tiefe, Knotenbelegung gemaess Typ `(k, k*)`, Blaetter oft verkettet. Ueben: Fehler finden, Einfuegen mit Split, Loeschen mit Umverteilung/Merge, Bulkloading.

Fanout-Rechnungen: Knotengroesse durch Groesse von Schluesseln und Verweisen teilen; auf Off-by-one bei `n` Schluesseln und `n+1` Kindverweisen achten.

### Transaktionen und Recovery

ACID: Atomicity, Consistency, Isolation, Durability. Atomicity ersetzt Isolation nicht: "alles oder nichts" verhindert nicht, dass parallele Transaktionen falsche Zwischenzustaende sehen.

Anomalien: Lost Update, Dirty Read, Non-repeatable Read, Phantom, inconsistent analysis.

Serialisierbarkeit: Konfliktgraph bauen; Kante `Ti -> Tj`, wenn konfliktierende Operationen auf demselben Objekt in dieser Reihenfolge auftreten und mindestens eine schreibt. Zyklus bedeutet nicht konfliktserialisierbar.

RC/ACA/ST: ruecksetzbar, vermeidet kaskadierendes Ruecksetzen, strikt. Strikt ist am staerksten. 2PL: Wachstumsphase mit Sperren, Schrumpfphase mit Freigaben; striktes 2PL haelt Schreibsperren bis Commit.

Force/Steal: Force beeinflusst Redo, Steal beeinflusst Undo. No-Force braucht Redo, Steal braucht Undo.

### XML/XPath

Historisch wichtig: Wohlgeformtheit, Validitaet gegen DTD, Pflichtattribute, Elementreihenfolge, XPath formulieren und auswerten. Falls XML im aktuellen Stoff nicht mehr behandelt wurde, nur als Reserve lernen.

## 3. Gewichtung fuer die 5 Wochen

Empfohlene Zeitverteilung:

- 25% SQL, Views, Trigger, rekursives SQL, Fensteranfragen
- 20% Relationale Algebra, Kalkuele, Anfrageoptimierung
- 15% Entwurfstheorie
- 15% Transaktionen und Recovery
- 10% ER-Modellierung
- 10% Informationssuche/Data Mining
- 5% Indexe/Puffer und Reserve XML/NoSQL

Wenn ihr pro Woche 12-15 Stunden schafft, reicht das fuer solide Vorbereitung. Bei weniger Zeit zuerst SQL, Algebra/Kalkuele, Entwurfstheorie und Transaktionen sichern.

## 4. Fuenf-Wochen-Lernplan

### Woche 1: Fundament und erste Punkte sichern

Ziel: Grundbegriffe sitzen, erste Aufgaben loesen koennen.

Tag 1: Klausurueberblick, Formelsammlung anfangen, ACID, Precision/Recall/F1, Support/Confidence.

Tag 2: ER-Grundlagen, Kardinalitaeten, Min/Max, schwache Entitaeten, Generalisierung.

Tag 3: ER -> Relationenmodell, Schluessel/Fremdschluessel, SQL `CREATE TABLE`.

Tag 4: Relationale Algebra Basisoperatoren, Joins, Division.

Tag 5: SQL Basis: Joins, Aggregation, `GROUP BY`, `HAVING`.

Tag 6: Uebungstag: alte ER/SQL/Algebra-Aufgaben aus 2016, 2017, 2022.

Tag 7: Review: Fehlerliste erstellen, 60-Minuten-Mini-Test.

### Woche 2: Anfragen hart trainieren

Ziel: SQL, Algebra und Kalkuel werden Routine.

Tag 1: SQL mit `EXISTS`, `NOT EXISTS`, "alle"/"keine"/"nie"-Aufgaben.

Tag 2: SQL-Auswertung auf konkreten Tabellen; Ergebnisrelationen berechnen.

Tag 3: Fensteranfragen: `RANK`, `SUM OVER`, Frames; Umschreiben ohne Fensterfunktion.

Tag 4: rekursives SQL mit `WITH RECURSIVE`; Pfade/Vorgaenger/Nachfolger.

Tag 5: Tupel- und Domaenenkalkuel, konjunktive Anfragen, regelbasierte Anfragen.

Tag 6: Anfrageoptimierung: Operatorbaum, Pushdown, Algebra-Gesetze, Bag-Semantik.

Tag 7: 90-Minuten-Anfrageblock aus Altklausuren unter Zeitdruck.

### Woche 3: Entwurfstheorie, Transaktionen, Indexe

Ziel: Rechen- und Beweisaufgaben sicher loesen.

Tag 1: FDs, Attributhuelle, Super-/Kandidatenschluessel.

Tag 2: kanonische Ueberdeckung, Armstrong-Axiome, Herleitungsregeln.

Tag 3: Verlustlosigkeit, Abhaengigkeitserhaltung, 3NF-Synthese, BCNF.

Tag 4: Transaktionsanomalien, ACID, RC/ACA/ST, Historien klassifizieren.

Tag 5: Serialisierbarkeitsgraphen und 2PL/striktes 2PL.

Tag 6: Force/Steal, Undo/Redo, Recovery; danach Puffer LRU/LFU/FIFO.

Tag 7: B+-Baum: Belegung, Fanout, Insert, Delete, Bulkloading.

### Woche 4: Informationssuche/Data Mining und komplette Altklausuren

Ziel: Rechenaufgaben schnell und fehlerarm.

Tag 1: Distanzmasse: Hamming, Jaccard/Shingles, Levenshtein-DP.

Tag 2: TF-IDF und LSI mit Matrixrechnungen.

Tag 3: PageRank, Markov-Ketten, MMR.

Tag 4: Frequent Itemsets, Apriori-Idee, Confidence, K-Means/Clustering.

Tag 5: komplette Klausur 2016 Nachklausur unter Zeitdruck.

Tag 6: komplette Klausur 2017 Nachklausur unter Zeitdruck.

Tag 7: Auswertung: Punkte nach Thema schaetzen, Top-10-Fehlerliste aktualisieren.

### Woche 5: Klausurmodus

Ziel: Geschwindigkeit, Priorisierung, sichere Standardantworten.

Tag 1: Schwachstellen aus Woche 4 gezielt nachlernen.

Tag 2: komplette neuere Klausur/Gedaechtnisprotokoll 2022/2023 als Simulation.

Tag 3: SQL/Algebra-Sprint: 10 kurze Anfragen, 5 Auswertungen, 3 "alle/keine"-Aufgaben.

Tag 4: Transaktionen/Entwurfstheorie-Sprint: 3 Konfliktgraphen, 3 Attributhuellen, 2 Zerlegungen.

Tag 5: B+-Baum/Puffer/Optimierung-Sprint.

Tag 6: Generalprobe: 120 Minuten, keine Unterlagen, danach Korrektur.

Tag 7: Leichtes Wiederholen: Formelsammlung, Definitionen, Standardmuster, frueh aufhoeren.

## 5. Konkrete Altklausur-Priorisierung

Zuerst bearbeiten:

- 2016 Nachklausur: sehr vollstaendig, gute Breite, viele Punktgewichte.
- 2017 Nachklausur: sehr klausurnah fuer SQL, Algebra, Puffer, Indexe, Transaktionen, Informationssuche.
- 2022 und 2023 Gedaechtnisprotokolle: wichtig fuer neuere Gewichtung.

Danach:

- 2016 Hauptklausurprotokoll und 2017 Haupt-/Nachklausurprotokolle fuer weitere Varianten.
- 2009-2013 fuer klassische Themen, besonders XML/XPath, ER, B-Baeume, Transaktionen.

## 6. Definitionen, die ihr auswendig koennen solltet

- ACID mit je einem Verletzungsbeispiel.
- Precision, Recall, F1.
- Support, Confidence, Anti-Monotonie.
- Serialisierbarkeit und Konfliktserialisierbarkeit.
- RC, ACA, ST.
- 2PL und striktes 2PL.
- Verlustlosigkeit und hinreichende Bedingung.
- Superschluessel, Kandidatenschluessel, Attributhuelle.
- 2NF, 3NF, BCNF.
- Force, No-Force, Steal, No-Steal und Undo/Redo.
- Unterschied B-Baum/B+-Baum bzw. Binaerbaum/B+-Baum.
- Monotonie von Anfragen.
- Unterschied Mengen- und Multimengensemantik.

## 7. Klausurtaktik

1. Erst alle Aufgaben ueberfliegen und sichere Punkte markieren.
2. Warm-up/Definitionen sofort beantworten, aber nicht ausufern.
3. SQL/Algebra-Aufgaben sauber, aber pragmatisch loesen: Teilergebnisse bringen Punkte.
4. Bei B+-Baum und Serialisierbarkeit jeden Zwischenschritt sichtbar machen.
5. Bei Beweis-/Widerlegungsaufgaben reicht oft ein klares Gegenbeispiel.
6. Wenn eine Aufgabe klemmt: nach 4-5 Minuten markieren und weiter.
7. Am Ende Fremdschluessel, Gruppierungen, Quantoren und Kanten im Konfliktgraphen pruefen.

## 8. Woechentliche Checkliste

Jede Woche sollte mindestens einmal erledigt werden:

- 20 kurze Karteikarten/Definitionen wiederholen.
- 5 SQL-Anfragen schreiben.
- 3 relationale Algebra/Kalkuel-Aufgaben loesen.
- 2 Entwurfstheorie-Aufgaben rechnen.
- 2 Transaktionshistorien klassifizieren.
- 1 B+-Baum- oder Pufferaufgabe loesen.
- 1 Informationssuche/Data-Mining-Rechenaufgabe loesen.

## 9. Was ihr am Ende koennen muesst

Ihr seid klausurbereit, wenn ihr in 120 Minuten:

- eine SQL-Aufgabe mit Joins, Aggregation und `NOT EXISTS` sauber loest,
- eine Algebra- oder Kalkuelanfrage formuliert,
- ein ER-Modell in Relationen ueberfuehrt,
- Attributhuellen und Normalformen bestimmen koennt,
- einen Konfliktgraphen ohne vergessene Kanten baut,
- B+-Baum/Pufferaufgaben mechanisch abarbeitet,
- TF-IDF/Levenshtein/PageRank-Aufgaben mit Rechenweg loest,
- Definitionen kurz und korrekt erklaert.
