
---
## Präzision(Precision) und Ausbeute(Recall)
Precision P ist der Anteil der relevanten Dokumente in den zurückgegebenen Dokumenten
$$P=\frac{tp}{tp+fp}$$

Recall R ist der Anteil der relevanten zurückgegebenen Dokumente an allen relevanten Dokumenten
$$R=\frac{tp}{tp+fn}$$

---
## F-Measure
F-measure kombiniert Precision und Recall
$$F_{\beta}=\frac{(\beta^{2}+1)P\cdot R}{\beta^{2}\cdot P+R}$$
wobei der Parameter $\beta$ zwischen Precision und Recall die Gewichtung entscheidet
- $\beta = 1$ ist balanciert
- $\beta <1$ höherer Einfluss von Precision
- $\beta > 1$ höherer Einfluss von Recall

---
# Average Precision (AP)
- Sei { $d_{1},....,d_{m}$ } die Menge der relevanten Dokumente der Anfrage $q$
- Sei $R_{k}$ die Menge der geordneten Ergebnisse

$$AP(q)= \frac{1}{m}\sum\limits_{d_{k}\in {d_{1},....,d_{m}}}Precision(R_{k})$$
---
## Mean-Average-Precision
Für die Menge $Q$ von Anfragen kann die __Mean-Average-Precision(MAP)__ berechnet werden durch
$$MAP(Q)=\frac{1}{|Q|}\sum\limits_{q\in Q}AP(q)$$
---
# Precision@k
Precision@k ist die Precision, die in der ersten $k$ Ergebnisse erreicht wird, also wenn 5 relevante Dokumente in den ersten 10 Dokumenten ist dann
$$Precision@10=\frac{5}{10}=\frac{1}{2}=0.5$$
---
# TF * IDF

- **Dokumentfrequenz** $df_{t}$ als die Anzahl der Dokumente, in denen Term t auftritt
- *Inverse Dokumentfrequenz* $idf_{t}$ als $$idf_{t}= \frac{|D|}{df_{t}}$$
Das Gewicht von Term $t$ in Dokument $d$ ist dann definiert als 
$$tf.idf_{t,d}=tf_{t,d}\times idf_{t}$$
$$score(q,d)= \sum\limits_{t\in q}tf.idf_{t,d}$$
## MMR
$$argmax_{d_{i\in D}}=(\lambda \cdot sim(q,d_{i})-(1-\lambda)max_{d_{j}:1<j<i}sim(d_{i},d_{j}))$$
- erste Runde max TF * IDF auswählen $\implies$ erster platz
- zweite Runde alle MMR zu dem ersten Platz ausrechen und daraus den größten Wert nehmen $\implies$ zweiter Platz
- dritte Runde maximalen Ähnlichkeitswert aus den schon vorhanden Plätzen wählen 

---
## ACID
- **Atomicity (A)**: Datentransaktionen, bspw. die Eintragung eines neuen Datensatzes oder das Löschen eines alten, sollen entweder ganz oder gar nicht ausgeführt werden. Für andere User ist die Transaktion erst sichtbar, wenn sie vollständig ausgeführt ist.
-  **Consistency (C)**: Diese Eigenschaft ist erfüllt, wenn jede Datentransaktion die Datenbank von einem konsistenten in einen konsistenten Zustand überführt.
- **Isolation (I)**: Wenn mehrere Transaktionen gleichzeitig stattfinden, muss der Endzustand derselbe sein, als wenn die Transaktionen getrennt voneinander stattfinden würden. Das heißt die Datenbank sollte den Stresstest bestehen. Also nicht durch Überlastung zu falschen Datenbanktransaktionen kommen.
- **Durability (D)**: Die Daten innerhalb der Datenbank dürfen sich nur durch eine Transaktion ändern und nicht durch äußere Einflüsse veränderbar sein. Ein Softwareupdate darf beispielsweise nicht versehentlich dazu führen, dass sich Daten ändern oder womöglich gelöscht werden.

---
- __Rücksetzbare Historien (RC)__ TA darf erst committen, wenn alle TAs, von denen sie gelesen hat, beendet sind.
- __Historien ohne kaskadierendes Rücksetzen (ACA)__ Es dürfen nur Änderungen von abgeschlossenen TAs gelesen werden.
- __Strikte Historien__ Geänderte Daten nicht-abgeschlossener TAs dürfen weder gelesen noch überschrieben werden.
- __serialisierbar__ ist wenn der Konfliktgraph keine Zykle enthält 

![[Pasted image 20240724144921.png]]

---
## Jaccard-Koeffizient
Die __k-shingles__ eines Dokuments werden $S(d_{i})$ genannt

Beispiel:

Dokument mit den Worten $\lbrace a,b,b,c\rbrace$ wäre der $2-shingle$ dieses Dokuments $\lbrace ab,bb,bc\rbrace$ 

$$sim(d_{1},d_2)=\frac{|S(d_{1})\cap S(d_{2})|}{|S(d_{1}\cup S(d_2)|}$$
---
## Zwei Phasen Sperrprotokol ($2$PL)
Ein sperrprotokol ist zweiphasig (2PL) wenn alle Locks $q_il$ vor den Unlocks $q_iu$ kommen  
2Pl erzeugt nur serialisierbare Historien $\implies$ 2PL garantiert Serialisierbarkeit 

![[Pasted image 20240725115333.png]]

## Konservatives $2$PL
Unter konservativen 2PL fordert der TA alle Locks an bevor der erste Read oder Write Befehl kommt das heißt Preclaiming. Schwierig da man am Anfang wissen muss welche Locks benötigt werden

![[Pasted image 20240725115804.png]]

## Striktes $2$PL
Bei striktem 2PL werden alle exklusiven Locks also Write Locks bis zum Ende gehalten. Wird am häufigsten eingesetzt da striktes 2Pl serialisierbare und strikte Historien erzeugt

## Starkes $2$PL
Anders als bei Strikten 2Pl werden hier alle Locks bis zur Terminierung gehalten

![[Pasted image 20240725120759.png]]

### Locks 
Wenn kein Lock auf einem Objekt ist darf man ein Read Lock oder Write Lock setzten. Auf eine Read Lock dürfen mehrere Read Locks gesetzt werden aber kein Write Lock. Ein Write Lock darf nur gesetzt werden wenn kein Lock auf dem Objekt ist und auf ein Write Lock dürfen keine weitern Locks gesetzt werden.

![[Pasted image 20240725121635.png]]

---
## LSI
Man nimmt die Anfrage $q$ 
$$q\rightarrow U_{k}^{T}q=q'$$
Die Eignung(Score) der Dokumente wird dann im Topic-Raum berechnet durch die Cosinus-Ähnlichkeit oder das Skalarprodukt von $q'$ und den Spalten der Matrix $V_{k}^{T}$ 

Um eine Matrix zu transposen  werden die Spalten zur Zeile also:
$$\begin{pmatrix} 1&2 \\ 4&3\end{pmatrix}$$
$$\begin{pmatrix} 1&4 \\ 2&3\end{pmatrix}^T$$

---
# K-Means Clustering
- Jedes Cluster wird durch einen Mittelpunkt (Centroid) repräsentiert
- Ein Objekt wird dem Centroid mit der geringsten Distanz zugewiesen
- Es gibt $k$ Cluster. $k$ ist ein Parameter

![[Pasted image 20240505122636.png]]

- Die initialen Centroids werden normalerweise zufällig ausgewählt. Dadurch können verschiedene Durchläufe auf den gleichen Daten unterschiedliche Cluster erzeugen
- Als Distanzmaß wir z.B. die Euklidische Distanz benutzt

---
# Markov-Ketten
Markov-Ketten sind __gedächtnislos__ und __zeithomogen__

>[!Important]
>Man sagt eine Markov-Kette ist **ergodisch** falls sie irreduzibel, positiv rekurrent und aperiodisch ist.
>__Theorem__: Falls eine Markov-Kette endlich und ergodisch ist, dann existiert eine stationäre Zustandsverteilung $\pi$
### Beispiel:
Wie wird das Wetter morgen sein, wenn es heute regnet?

![[Pasted image 20240429192344.png]]

$P_{ij}$ ist die Wahrscheinlichkeit, dass der folgende Tag vom Typ $j$ ist, wenn der heutige Tag vom Typ $i$ ist.

Wenn man zum Beispiel den heutigen Tag als Vektor darstellt in dem Fall ein Sonniger Tag $x_{0}=(1, 0)$ 
Dann ist das Wetter am nächsten Tag :
$$x_{1}=x_{0}\cdot P=(1,0)\cdot \begin{pmatrix}0.9&0.1\\0.5&0.5\end{pmatrix}=(0.9,0.1)$$
---
## Levenshtein
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
## Hamming-Editier-Distanz
Die Hamming-Editier-Distanz beschreibt die Anzahl an Positionen an denen die beiden Strings x und y verschieden sind, dabei werden kürzere String mit "NULL" aufgefüllt

Beispiel:
- $d(car,cat) = 1$
- $d(house,hot) = 3$
- $d(house,hoouse)= 4 \leftarrow$ sehr hohe Distanz für kleinen Fehler

---
## Längste Gemeinsame Teilsequenz
Eine Teilsequenz ist eine Sequenz, die von einer anderen Sequenz durch weglassen von Zeichen aber unter Beibehaltung der Reihenfolge der Zeichen entsteht.
$$d_{(x,y)}= max(|x|,|y|)-max_{(s\in S(x,y))}|S|$$
wobei $S_{(x,y})$ die Menge aller gemeinsamer Teilsequenzen von x und y ist.

Beispiel:
- $d(house,huse)=1$
weil $max(|house|,|huse|)=5$ (Längstes Wort) und $max_{(s\in S(x,y))}|4|$ (Längste Gemeinsame Teilsequenz) also ist die Distanz $1$.

---
## Itemsets
- Ein Itemset ist eine Menge von Objekten
	- Eine Transaktion $t$ ist ein Itemset mit dazu gehöriger Transaktions ID $t=(tid,I)$, wobei $I$ das Itemset der Transaktion ist

- Der Support von Itemset $X$ in einer Datenbank $D$ ist die Anzahl der Transaktionen in $D$, die $X$ enthalten
	$$Supp(X,D)=\lbrace t\in D:t\ enthält\ X\rbrace$$
- Die __relative Häufigkeit__ von Itemset $X$ in Datenbank $D$ ist:
$$supp(X,D)/|D|$$
## Assoziationsregeln
Support einer Regel
$$supp(X \rightarrow Y,D)=supp(X\cup Y,D)$$
Konfidenz der Regel
$$conf(X\rightarrow Y,D)=supp(X\cup Y,D)/supp(X,D)$$
Die Konfidenz ist die bedingte Wahrscheinlichkeit, dass eine Transaktion $Y$ enthält, wenn sie $X$ enthält

---
## Regelbasierte Konjunktive Anfrage
$$ans(x_{TH},x_{ad})\leftarrow Movies(x_{ti}, Bergman, x_{ac}) Pariscope(x_{TH}x_{ti}, x_{s}) Location(x_{TH},x_{ad},x_P)$$

- Alles links vom Pfeil ist der Kopf
- Alles recht vom Pfeil ist der Rumpf

$$ans(u)\leftarrow R_1(u_{1}),...,R_n(u_n)$$
- $u,u_1,...,u_n$ sind Tupel
- Jede Variable aus $u$ muss mindestens einmal vorkommen

## Konjunktives Kalkül

wie Konjunktive Anfrage bis auf das alle Variablen in der Antwort Menge sein müssen oder Existenzquantiviziert
$$\lbrace e_1...e_{m}\mid \exists x_{1}....x_{k}(R_{1}(u_{1})\land R_{2}(u_2))\rbrace $$

---
## Domänenkalkül

wie Konjunktives Kalkül nur darf man die komplette logische Palette benutzen darunter fällt z.B. $\forall, \lor$ 

---
## Tupelkalkül
# TODO
---
## Break Even Point
Sei $a$ die Positionierungs Zeit, $s$ die Leserate, $p$ die Seitengröße und $d$ die Dateigröße. Dann ist der Break Even Point gegeben durch:
$$n\cdot (a+\frac{p}{s})=a+\frac{d}{s}$$
$$n=\frac{a\cdot s +d}{a\cdot s +p}$$

---
## Optimierung

![[Pasted image 20240726133035.png]]

---
## Puffer
### First In First Out (FIFO)
Ersetzt die Seite die am längsten im Puffer ist

### Least Frequently Used (LFU)
- Ersetzt Seite mit der geringsten Referenz- (Zugriffs-) Häufigkeit
- Für jede Seite wird ein Zugriffszähler (aka. Referenzzähler RZ) geführt.

### Least Recently Used (LRU)
- Ersetzung basierend auf Zeit seit dem letzten Zugriff auf Seite.
- Halte Seiten in Form eines Stacks:
	- Eine Seite kommt bei jeder Referenz auf oberste Position
	- Seite auf der untersten Position des Stacks wird bei Bedarf ersetzt

---
![[Pasted image 20250918134436.png]]
![[Pasted image 20250918140516.png]]
![[Pasted image 20250918140530.png]]
![[Pasted image 20250918141317.png]]

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;

public class PostgresTriggerExample {
    public static void main(String[] args) {
        String url = "jdbc:postgresql://localhost:5432/deinedatenbank";
        String user = "postgres";
        String password = "passwort";

        // Funktion erstellen (Trigger-Handler)
        String createFunctionSQL = """
            CREATE OR REPLACE FUNCTION log_user_insert()
            RETURNS TRIGGER AS $$
            BEGIN
                INSERT INTO user_audit(user_id, action, created_at)
                VALUES (NEW.id, 'INSERT', NOW());
                RETURN NEW;
            END;
            $$ LANGUAGE plpgsql;
        """;

        // Trigger erstellen, der die Funktion aufruft
        String createTriggerSQL = """
            DROP TRIGGER IF EXISTS after_user_insert ON users;
            CREATE TRIGGER after_user_insert
            AFTER INSERT ON users
            FOR EACH ROW
            EXECUTE FUNCTION log_user_insert();
        """;

        try (Connection conn = DriverManager.getConnection(url, user, password);
             Statement stmt = conn.createStatement()) {

            // Funktion anlegen
            stmt.executeUpdate(createFunctionSQL);

            // Trigger anlegen
            stmt.executeUpdate(createTriggerSQL);

            System.out.println("Trigger erfolgreich in PostgreSQL erstellt!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}

```
---

### 1. ER-Modell & Relationenmodellierung

- **Was:** Konzeptionelle Modellierung der Miniwelt und deren Abbildung auf das relationale Datenmodell.
- **Wichtig:**
    - **ER-Diagramme:** Entitätstypen, Beziehungstypen (binär, ternär), Attribute (Schlüsselattribute sind unterstrichen), Rollen.
    - **Kardinalitäten:** Chen-Notation (z.B. N:M, 1:N), MinMax-Notation (z.B. (0,1), (1,*)), Existenzabhängigkeit (schwache Entitäten).
    - **Generalisierung/Spezialisierung (is-a):** Disjunkt/überlappend, vollständig/partiell (Kardinalitäten für Subklassen: (1,1), (0,1), (1,_), (0,_)).
    - **Abbildung auf Relationenmodell:** Regeln zur Übersetzung von Entitätstypen, Beziehungstypen (insbesondere 1:N, N:M, ternär, Generalisierung, schwache Entitäten) in Relationen und Fremdschlüssel.
    - **Integritätsbedingungen:** Primärschlüssel, Fremdschlüssel (`ON UPDATE/DELETE CASCADE/SET NULL/RESTRICT`).
- **Aufgaben:** ER-Diagramme erstellen, Kardinalitäten eintragen/begründen, Abbildung auf SQL-`CREATE TABLE` Statements inklusive aller Constraints.

### 2. Entwurfstheorie (FDs & Normalformen)

- **Was:** Analyse und Verbesserung von Relationenschemata zur Vermeidung von Redundanz und Änderungsanomalien.
- **Wichtig:**
    - **Funktionale Abhängigkeiten (FDs):** Definition (`α → β`), Einhaltung prüfen.
    - **Schlüssel:** Superschlüssel (`α → R`), Kandidatenschlüssel (minimale Superschlüssel), Attributhülle (`AttrHülle(F, α)`) berechnen.
    - **Armstrong-Axiome:** Reflexivität, Augmentierung, Transitivität (und erweiterte Regeln wie Dekomposition, Pseudotransitivität).
    - **Kanonische Überdeckung (Fc):** Algorithmus zur Links- und Rechtsreduktion.
    - **Zerlegung:** Verlustlosigkeit (`R = R1 ⋈ R2`) und Abhängigkeitserhaltung prüfen/begründen.
    - **Normalformen:** 1NF, 2NF, 3NF, BCNF (Definitionen und Beispiele für Anomalien/Verletzungen). Algorithmen zur Überführung in 3NF (Synthese) oder BCNF (Dekomposition).
    - **Mehrwertige Abhängigkeiten (MVDs):** Definition (`α ↠ β`), Verlustlose Zerlegung bei MVDs.
- **Aufgaben:** FDs bestimmen, Attributhülle berechnen, Schlüsselkandidaten/Superschlüssel identifizieren, Armstrong-Axiome anwenden, Kanonische Überdeckung finden, Zerlegungen prüfen, Relationen normalisieren.

### 3. Relationale Algebra (RA)

- **Was:** Prozedurale Anfragesprache mit Operatoren zur Schritt-für-Schritt-Beschreibung von Datenmanipulationen.
- **Wichtig:**
    - **Grundoperatoren:** Selektion (`σ`), Projektion (`π`), Kartesisches Produkt (`×`), Vereinigung (`∪`), Differenz (`-`), Umbenennung (`ρ`).
    - **Abgeleitete Operatoren:** Join (`⋈`, verschiedene Typen wie Equi-Join, Natural Join), Division (`÷`).
    - **Erweiterungen:** Gruppierung und Aggregation (`γ`).
    - **Mengensemantik vs. Multimengensemantik:** Auswirkungen auf Duplikate bei Projektion und Mengenoperationen.
- **Aufgaben:** Textanfragen in RA formulieren, RA-Ausdrücke auf gegebenen Instanzen auswerten, Äquivalenz von RA-Ausdrücken prüfen, RA-Ausdrücke umgangssprachlich beschreiben.

### 4. Relationenkalküle (Domänenkalkül, Tupelkalkül, Konjunktive Anfragen)

- **Was:** Deklarative Anfragesprachen, die _was_ gesucht wird, statt _wie_ es zu berechnen ist.
- **Wichtig:**
    - **Konjunktive Anfragen:** Kopf und Rumpf, intensionale vs. extensionale Relationen, Anfrageprogramme, Monotonie.
    - **Domänenkalkül (DK):** Formeln mit Domänenvariablen, Konstanten, relationalen Atomen, Vergleichsoperatoren (`=, ≠, ≥`), logischen Operatoren (`∧, ∨, ¬`) und Quantoren (`∃, ∀`).
    - **Tupelkalkül (TK):** Formeln mit Tupelvariablen, Relation-Member (`t ∈ R`), Attributzugriff (`t.x`), Vergleichsoperatoren.
    - **Sicherheit von Anfragen:** Bedingungen für endliche Ergebnisse, Domäne einer Formel.
    - **Äquivalenz:** Kalküle und RA sind gleich mächtig (für sichere Ausdrücke).
- **Aufgaben:** Textanfragen in DK/TK/konjunktiven Anfragen formulieren, Sicherheit von Anfragen begründen, Anfragen umschreiben, Auswertung auf Instanzen.

### 5. SQL Anfragen (DML, DDL)

- **Was:** Die primäre, standardisierte Datenbanksprache.
- **Wichtig:**
    - **`SELECT` Statement:** `FROM`, `WHERE`, `GROUP BY`, `HAVING`, `ORDER BY`, `LIMIT`.
    - **Datentypen und Constraints:** `CREATE TABLE`, `PRIMARY KEY`, `FOREIGN KEY`, `NOT NULL`, `UNIQUE`, `CHECK`, `DEFAULT`.
    - **Aggregatfunktionen:** `COUNT`, `SUM`, `AVG`, `MAX`, `MIN` (Verwendung mit `GROUP BY`, `HAVING`).
    - **Subqueries:** Unkorreliert (`IN`), Korreliert (`EXISTS`), All- und Any-Quantifizierung (`ALL`, `ANY`, `SOME`), Allquantifizierung mittels Negation formulieren.
    - **`JOIN`s:** Kreuzprodukt (`CROSS JOIN`), natürlicher Join (`NATURAL JOIN`), innerer Join (`INNER JOIN`), Outer Joins.
    - **`NULL`-Werte:** Dreiwertige Logik (`TRUE`, `FALSE`, `UNKNOWN`), Verhalten in arithmetischen Ausdrücken, Vergleichen und Aggregatfunktionen.
    - **`INSERT`, `UPDATE`, `DELETE`:** mit `WHERE`-Klausel.
    - **Fensteranfragen:** `OVER (PARTITION BY ... ORDER BY ...)` mit Ranking-Funktionen (`RANK`, `DENSE_RANK`, `SUM(...) OVER(...)`).
    - **Rekursive SQL Anfragen:** `WITH RECURSIVE`.
- **Aufgaben:** SQL-Anfragen formulieren (von einfach bis komplex, Uni-Schema und andere Schemata), `CREATE TABLE` Statements, SQL-Anfragen (insb. Fenster- und Rekursion) auswerten.

### 6. Sichten (Views) & Trigger

- **Was:** Abstraktionsmechanismen und proaktive Erweiterungen der Datenbank.
- **Wichtig:**
    - **Sichten (`VIEW`s):** Definition (`CREATE VIEW`), Eigenschaften (virtuell/materialisiert), änderbare Sichten, `WITH CHECK OPTION`, `WITH`-Klausel für temporäre Sichten/Unteranfragen.
    - **Trigger:** Motivation, Grundprinzip (`AFTER/BEFORE/INSTEAD OF`, `INSERT/UPDATE/DELETE`, `ON <table>`, `FOR EACH ROW/STATEMENT`, `WHEN`-Bedingung), Trigger-Aktion als UDF.
- **Aufgaben:** Views definieren und diskutieren, Trigger-Statements und UDFs zu Szenarien schreiben.

### 7. Transaktionen (ACID, Serialisierbarkeit, Recovery)

- **Was:** Gewährleistung der Korrektheit und Zuverlässigkeit bei parallelem Betrieb und Systemfehlern.
- **Wichtig:**
    - **ACID-Paradigma:** Atomarität, Konsistenz, Isolation, Dauerhaftigkeit (Definition, Beispiele für Verletzungen/Anomalien wie Lost Update, Dirty Read).
    - **Historien:** Definition, serielle Historie, serialisierbare Historie, Konfliktoperationen, Konfliktgraph (Zeichnen, auf Zyklen prüfen).
    - **Serialisierbarkeitsklassen:** Rücksetzbar (RC), Avoids Cascading Aborts (ACA), Strikt (ST) (Definitionen, Beziehungen untereinander).
    - **Sperrverfahren:** Zwei-Phasen-Sperrprotokoll (2PL), Konservatives 2PL (C2PL), Striktes 2PL (S2PL), Starkes Striktes 2PL (SS2PL).
    - **Verklemmungen (Deadlocks):** Entstehung, Erkennung (Wartegraph), Auflösung.
    - **Recovery:** WAL-Prinzip, Force/Steal-Matrix (Redo/Undo-Bedarf), Wiederanlauf nach Crash.
- **Aufgaben:** ACID-Eigenschaften erklären, Historien auf Anomalien/Eigenschaften prüfen (Konfliktgraph zeichnen), Force/Steal-Matrix ausfüllen, Sperrprotokolle anwenden/analysieren.

### 8. DB-Puffer und E/A-Architektur

- **Was:** Effiziente Verwaltung der Datenübertragung zwischen Haupt- und Sekundärspeicher.
- **Wichtig:**
    - **Speicherhierarchie:** Kosten für verschiedene Speichertypen, Zugriffslücke zwischen Hauptspeicher und Festplatte.
    - **E/A-Kostenmodell:** Positionierungszeit (`a`), Leserate (`s`), Seitengröße (`p`), Dateigröße (`d`). Unterschied sequentieller vs. wahlfreier Zugriff.
    - **Break-Even-Point:** Berechnung (`n = (as+d)/(as+p)`).
    - **Datenbankpuffer:** Motivation, `5-Minuten-Regel`.
    - **Ersetzungsstrategien:** FIFO, LFU, LRU, RANDOM, Optimal (Algorithmen, Funktionsweise, Vor-/Nachteile). Berechnung der Cache Misses bei gegebener Zugriffsfolge und Puffergröße.
- **Aufgaben:** Break-Even-Point berechnen, Pufferzustand und Cache Misses für eine Zugriffsfolge und Strategie bestimmen.

### 9. Indexstrukturen (B+ Bäume)

- **Was:** Datenstrukturen zur Beschleunigung von Suchoperationen.
- **Wichtig:**
    - **Motivation:** Nachteile der linearen/binären Suche auf Festplatten, hohe E/A-Kosten.
    - **B-Bäume:** Definition, Eigenschaften (balanciert, Füllgrad), Knotenformat, Einfügen/Löschen (Splits, Mischen).
    - **B+-Bäume:** Wichtigste Variante, Vorteile gegenüber B-Bäumen (Daten nur in Blättern, sequentiell verknüpfte Blätter, höherer Fan-Out, flacherer Baum), (k,k*)-Definition, Knotenformate, Grundoperationen (Suchen, Einfügen, Löschen), Fan-Out Berechnung.
    - **Bulkloading:** Effizienter Aufbau eines B+ Baums aus vorsortierten Daten.
    - **Präfix-B-Bäume:** Schlüsselkomprimierung in inneren Knoten.
    - **Hashverfahren:** Punktanfragen, Kollisionen, Hashfunktionen.
    - **Nachteile von Indexen:** Platzverbrauch, Pflegeaufwand bei Änderungen.
- **Aufgaben:** Gegebenen B+ Baum zeichnen/korrigieren, Operationen (Insert/Delete) schrittweise durchführen, Fanout berechnen, Vor-/Nachteile/Unterschiede von Indexstrukturen erklären.

### 10. Anfrageoptimierung (Kostenschätzung, Heuristiken)

- **Was:** Prozess zur Auswahl des effizientesten Ausführungsplans für eine Anfrage.
- **Wichtig:**
    - **Anfrageplan:** Übersetzung von SQL in Operatoren der relationalen Algebra, Operatorbäume.
    - **Regelbasierte Optimierung:** Heuristiken (Selektionen früh schieben, Projektionen früh schieben, Join-Reihenfolge optimieren).
    - **Kostenbasierte Optimierung:** Kostenmodelle (Anzahl Zwischenergebnisse), Statistiken, Histogramme.
    - **Selektivitätsschätzung:** `T(R)` (Anzahl Tupel), `V(R,A)` (Anzahl verschiedener Werte), Formeln für Selektionen (`σA=c(R)`, `σA≠c(R)`, `σC1∨C2(R)`) und Joins (`R ⋈ S`), Projektion (`πA(R)` unter Mengensemantik).
    - **Histogramme:** Erstellung (Equi-Height), Punktanfragen, Bereichsanfragen, Fehlermaße (absoluter/relativer Fehler).
- **Aufgaben:** RA-Anfragen optimieren (Operatorbäume umformen), Selektivitäten/Ergebnismengen abschätzen, Histogramme erstellen/auswerten, Fehler berechnen.

### 11. Informationssuche (IR-Modelle, Metriken, Distanzmaße)

- **Was:** Methoden zur effizienten Suche, Bewertung und Rangfolge von Informationen.
- **Wichtig:**
    - **Dokumentverarbeitung:** Tokenisierung, Stopwörter, Stemming.
    - **Distanzmaße auf Zeichenketten:** Hamming-Distanz, Levenshtein-Distanz (DP-Tabelle ausfüllen), Längste gemeinsame Teilsequenz.
    - **Retrieval-Modelle:** Boolesches Modell, Vektorraummodell (Kosinus-Ähnlichkeit).
    - **TF*IDF:** Termfrequenz (`tf`), Dokumentfrequenz (`df`), Inverse Dokumentfrequenz (`idf`), Gewichtung (`tf.idf = tf × idf`), Skalarprodukt-Ähnlichkeit.
    - **Bewertung der Resultatgüte:** Klassifizierung von Ergebnissen (True/False Positives/Negatives), **Precision** (`P = tp / (tp + fp)`), **Recall** (`R = tp / (tp + fn)`), **F-Measure** (`Fβ`), **Average Precision (AP)**, **Mean Average Precision (MAP)**, **Precision@k (P@k)** (Berechnung auf Beispiel-Ranglisten).
    - **Vielfalt & Neuheit:** Maximale Marginale Relevanz (MMR) (Vorgehensweise).
    - **Latent-Semantic-Indexing (LSI):** SVD, Rang-k Approximation, Operationen im Topic-Raum.
    - **PageRank:** Random-Surfer-Modell, Power Iteration.
- **Aufgaben:** Distanzmaße berechnen, TF*IDF Scores ermitteln, Precision/Recall/F-Measure/P@k berechnen/diskutieren, MMR/LSI Vorgehen beschreiben.

### 12. Data Mining (Frequent Itemsets, Clustering)

- **Was:** Entdeckung von Mustern und Strukturen in großen Datenmengen.
- **Wichtig:**
    - **Warenkorbanalyse:** Itemsets, Support, Konfidenz, Assoziationsregeln.
    - **Apriori-Prinzip:** Anti-Monotonie des Supports (häufige Teilmengen sind auch häufig), Kandidatengenerierung und Eliminierung.
    - **Clustering:** Definition, Gütebestimmung von Clusterings.
- **Aufgaben:** Häufige Itemsets zu gegebenen Transaktionen und `minsupp` finden, Assoziationsregeln herleiten, Anti-Monotonie des Supports begründen.

---

**Zusätzlicher Hinweis:** Die "Warm-Up"-Aufgaben in den Klausurprotokollen zeigen, dass auch grundlegende Konzepte und deren Begründungen abgefragt werden können, die sich über verschiedene Themen erstrecken. Daher ist es wichtig, nicht nur zu wissen _wie_ etwas funktioniert, sondern auch _warum_.

Konzentrieren Sie sich auf das Verständnis der Kernkonzepte, üben Sie das Lösen von Beispielaufgaben und können Sie die wichtigsten Definitionen und Schritte prägnant wiedergeben. Viel Erfolg bei der Prüfung!