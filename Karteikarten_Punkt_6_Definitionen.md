# Karteikarten Punkt 6: Definitionen

Quelle: Abschnitt 6 aus `Lernplan_Informationssysteme.md` - Definitionen, die auswendig sitzen sollten.

## ACID !

| Vorderseite                               | Rueckseite                                                                                                                                                                     |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Wofuer steht ACID?                        | Atomicity, Consistency, Isolation, Durability. Das sind zentrale Eigenschaften korrekter Transaktionen.                                                                        |
| Was bedeutet Atomicity?                   | Eine Transaktion wird ganz oder gar nicht ausgefuehrt. Bei Fehlern werden bereits ausgefuehrte Aenderungen rueckgaengig gemacht.                                               |
| Beispiel fuer Verletzung von Atomicity?   | Bei einer Ueberweisung wird Geld vom ersten Konto abgebucht, aber wegen Fehler nicht auf dem zweiten Konto gutgeschrieben.                                                     |
| Was bedeutet Consistency?                 | Eine Transaktion ueberfuehrt die Datenbank von einem konsistenten Zustand in einen anderen konsistenten Zustand. Integritaetsbedingungen bleiben erhalten.                     |
| Beispiel fuer Verletzung von Consistency? | Nach einer Buchung zeigt ein Fremdschluessel auf einen nicht existierenden Kunden oder ein Kontostand wird trotz Constraint negativ.                                           |
| Was bedeutet Isolation?                   | Nebenlaeufige Transaktionen sollen sich so verhalten, als wuerden sie nacheinander ausgefuehrt. Zwischenergebnisse anderer Transaktionen duerfen nicht stoeren.                |
| Beispiel fuer Verletzung von Isolation?   | Zwei Transaktionen lesen denselben alten Kontostand und schreiben beide darauf basierend neue Werte; ein Update geht verloren.                                                 |
| Was bedeutet Durability?                  | Nach Commit bleiben Aenderungen dauerhaft gespeichert, auch bei Systemabsturz.                                                                                                 |
| Beispiel fuer Verletzung von Durability?  | Eine Transaktion meldet Commit, aber nach Crash sind ihre Aenderungen verschwunden.                                                                                            |
| Warum ersetzt Atomicity nicht Isolation?  | Atomicity regelt nur ganz oder gar nicht. Isolation verhindert zusaetzlich, dass parallele Transaktionen falsche Zwischenzustaende sehen oder sich gegenseitig ueberschreiben. |

## Precision, Recall, F1 !

| Vorderseite                               | Rueckseite                                                                                                                                     |
| ----------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Was ist Precision?                        | Anteil relevanter Treffer unter allen gelieferten Treffern: `Precision = relevante gelieferte Treffer / gelieferte Treffer`.                   |
| Was ist Recall?                           | Anteil gefundener relevanter Dokumente unter allen relevanten Dokumenten: `Recall = relevante gelieferte Treffer / alle relevanten Dokumente`. |
| Was ist F1?                               | Harmonisches Mittel aus Precision und Recall: `F1 = 2 * Precision * Recall / (Precision + Recall)`.                                            |
| Wann ist Precision hoch?                  | Wenn unter den gelieferten Treffern fast nur relevante Dokumente sind.                                                                         |
| Wann ist Recall hoch?                     | Wenn fast alle relevanten Dokumente im Ergebnis enthalten sind.                                                                                |
| Kann Precision = 1 und Recall < 1 gelten? | Ja. Dann sind alle gelieferten Treffer relevant, aber es wurden nicht alle relevanten Dokumente gefunden.                                      |
| Kann Recall = 1 und Precision < 1 gelten? | Ja. Dann wurden alle relevanten Dokumente gefunden, aber zusaetzlich irrelevante Treffer geliefert.                                            |
| Kann Precision = 1 und Recall = 1 gelten? | Ja. Dann enthaelt die Ergebnisliste genau alle relevanten Dokumente und keine irrelevanten.                                                    |

## Support und Confidence

| Vorderseite | Rueckseite |
|---|---|
| Was ist Support eines Itemsets? | Anzahl oder Anteil der Transaktionen, die dieses Itemset enthalten. |
| Was ist relativer Support? | `supp(X) = Anzahl Transaktionen mit X / Anzahl aller Transaktionen`. |
| Was ist absoluter Support? | Die reine Anzahl der Transaktionen, die ein Itemset enthalten. |
| Was ist Confidence einer Regel `X -> Y`? | Anteil der Transaktionen mit X, die auch Y enthalten: `conf(X -> Y) = supp(X union Y) / supp(X)`. |
| Was bedeutet hohe Confidence? | Wenn X vorkommt, kommt Y mit hoher Wahrscheinlichkeit ebenfalls vor. |
| Was bedeutet Anti-Monotonie des Supports? | Wenn ein Itemset nicht haeufig ist, kann keine Obermenge davon haeufig sein. |
| Formal: Was gilt fuer `X subset Y` beim Support? | `supp(Y) <= supp(X)`. Obermengen koennen hoechstens so oft vorkommen wie Untermengen. |
| Wofuer nutzt Apriori die Anti-Monotonie? | Um Kandidaten frueh zu verwerfen: Obermengen nicht haeufiger Itemsets muessen nicht mehr geprueft werden. |
| Was ist eine Assoziationsregel? | Eine Regel der Form `X -> Y`, die einen Zusammenhang zwischen gemeinsam auftretenden Itemsets beschreibt. |

## Serialisierbarkeit

| Vorderseite | Rueckseite |
|---|---|
| Was ist eine Historie bzw. ein Schedule? | Eine zeitliche Reihenfolge von Operationen mehrerer Transaktionen, z.B. Lesen, Schreiben, Commit, Abort. |
| Wann ist eine Historie seriell? | Wenn die Operationen jeder Transaktion zusammenhaengend ausgefuehrt werden und sich Transaktionen nicht verschraenken. |
| Wann ist eine Historie serialisierbar? | Wenn sie aequivalent zu einer seriellen Historie ist. |
| Was ist Konfliktserialisierbarkeit? | Eine Historie ist konfliktserialisierbar, wenn sie durch Vertauschen nicht konfliktierender Operationen in eine serielle Historie ueberfuehrt werden kann. |
| Wann konfliktieren zwei Operationen? | Wenn sie von verschiedenen Transaktionen stammen, dasselbe Objekt betreffen und mindestens eine Operation ein Schreibzugriff ist. |
| Welche Operationspaare konfliktieren? | `r/w`, `w/r`, `w/w` auf demselben Objekt und aus verschiedenen Transaktionen. |
| Welche Operationspaare konfliktieren nicht? | `r/r` oder Operationen auf verschiedenen Objekten oder Operationen derselben Transaktion. |
| Was ist ein Serialisierungsgraph/Konfliktgraph? | Gerichteter Graph mit Transaktionen als Knoten; Kante `Ti -> Tj`, wenn eine Operation von `Ti` vor einer konfliktierenden Operation von `Tj` steht. |
| Wann ist eine Historie konfliktserialisierbar? | Genau dann, wenn ihr Konfliktgraph azyklisch ist. |
| Was bedeutet ein Zyklus im Konfliktgraphen? | Die Historie ist nicht konfliktserialisierbar. |
| Wie liest man eine serielle Reihenfolge aus dem Konfliktgraphen ab? | Durch topologische Sortierung des azyklischen Graphen. |

## RC, ACA, ST

| Vorderseite | Rueckseite |
|---|---|
| Was bedeutet RC? | Recoverable: Wenn `Tj` von `Ti` liest, darf `Tj` erst committen, nachdem `Ti` committet hat. |
| Was verhindert RC? | Dass eine Transaktion committet, obwohl sie von einer spaeter abgebrochenen Transaktion gelesen hat. |
| Was bedeutet ACA? | Avoids Cascading Aborts: Eine Transaktion darf nur Werte lesen, die bereits von committeten Transaktionen geschrieben wurden. |
| Was verhindert ACA? | Kaskadierendes Ruecksetzen, also dass viele Transaktionen wegen eines Aborts mit zurueckgesetzt werden muessen. |
| Was bedeutet ST bzw. strikt? | Eine Transaktion darf ein Objekt erst lesen oder schreiben, nachdem die letzte schreibende Transaktion auf diesem Objekt committet oder abgebrochen hat. |
| Welche Beziehung gilt zwischen ST, ACA und RC? | `ST => ACA => RC`. Strikt ist am staerksten, RC am schwaechsten. |
| Ist jede ACA-Historie auch RC? | Ja. Wenn nur committete Werte gelesen werden, ist Recoverability erfuellt. |
| Ist jede RC-Historie auch ACA? | Nein. RC erlaubt Lesen uncommitteter Werte, solange Commit-Reihenfolge passt. |
| Ist jede strikte Historie ACA? | Ja. Striktheit verhindert Lesen uncommitteter Schreibwerte. |

## 2PL und striktes 2PL

| Vorderseite | Rueckseite |
|---|---|
| Was ist 2PL? | Two Phase Locking: Jede Transaktion hat eine Wachstumsphase, in der sie Sperren anfordert, und eine Schrumpfphase, in der sie Sperren freigibt. Nach erster Freigabe darf keine neue Sperre angefordert werden. |
| Was ist die Wachstumsphase bei 2PL? | Phase, in der Sperren erworben werden duerfen. |
| Was ist die Schrumpfphase bei 2PL? | Phase, in der Sperren freigegeben werden; danach duerfen keine neuen Sperren mehr erworben werden. |
| Was garantiert 2PL? | Konfliktserialisierbarkeit. |
| Garantiert 2PL automatisch Striktheit? | Nein. Normales 2PL kann Sperren vor Commit freigeben. |
| Was ist striktes 2PL? | Schreibsperren werden bis Commit oder Abort gehalten; dadurch werden schmutzige Lesezugriffe und viele Recovery-Probleme vermieden. |
| Was garantiert striktes 2PL typischerweise? | Konfliktserialisierbarkeit und strikte Historien. |
| Was ist eine Lesesperre? | Eine Sperre, die Lesen erlaubt; mehrere Lesesperren koennen kompatibel sein. |
| Was ist eine Schreibsperre? | Exklusive Sperre zum Schreiben; nicht kompatibel mit anderen Lese- oder Schreibsperren auf demselben Objekt. |

## Verlustlosigkeit und Zerlegung

| Vorderseite | Rueckseite |
|---|---|
| Was bedeutet Zerlegung einer Relation? | Ein Relationenschema `R` wird in mehrere kleinere Schemata `R1, R2, ...` aufgeteilt. |
| Was bedeutet verlustlose Zerlegung? | Der natuerliche Join der zerlegten Relationen ergibt wieder genau die urspruengliche Relation, ohne falsche Zusatz-Tupel. |
| Warum ist Verlustlosigkeit wichtig? | Damit beim Rekonstruieren durch Join keine Information verloren geht oder kuenstliche Tupel entstehen. |
| Hinreichende Bedingung fuer verlustlose Zerlegung in `R1` und `R2`? | `(R1 Schnitt R2) -> R1` oder `(R1 Schnitt R2) -> R2` muss aus den FDs folgen. |
| Was ist das gemeinsame Attributset bei einer Zerlegung? | `R1 Schnitt R2`, also die Attribute, die in beiden Teilschemata vorkommen. |
| Was bedeutet abhaengigkeitserhaltende Zerlegung? | Die funktionalen Abhaengigkeiten koennen auf den Teilrelationen geprueft werden, ohne vorher wieder joinen zu muessen. |
| Ist jede verlustlose Zerlegung abhaengigkeitserhaltend? | Nein. Verlustlosigkeit und Abhaengigkeitserhaltung sind verschiedene Eigenschaften. |

## Superschluessel, Kandidatenschluessel, Attributhuelle

| Vorderseite | Rueckseite |
|---|---|
| Was ist eine funktionale Abhaengigkeit `X -> Y`? | Wenn zwei Tupel in allen Attributen von X gleich sind, muessen sie auch in allen Attributen von Y gleich sein. |
| Was ist die Attributhuelle `X+`? | Menge aller Attribute, die aus X mit den gegebenen funktionalen Abhaengigkeiten ableitbar sind. |
| Wie berechnet man eine Attributhuelle? | Starte mit X; fuege wiederholt rechte Seiten von FDs hinzu, deren linke Seite bereits enthalten ist, bis nichts Neues hinzukommt. |
| Was ist ein Superschluessel? | Eine Attributmenge X, fuer die `X+` alle Attribute der Relation enthaelt. |
| Was ist ein Kandidatenschluessel? | Ein minimaler Superschluessel; kein Attribut kann entfernt werden, ohne die Schluesseleigenschaft zu verlieren. |
| Was ist ein Primaerschluessel? | Ein ausgewaehlter Kandidatenschluessel, der zur Identifikation der Tupel verwendet wird. |
| Kann ein Superschluessel kein Kandidatenschluessel sein? | Ja. Wenn er nicht minimal ist, ist er nur Superschluessel. |
| Kann eine Attributhuelle alle Attribute enthalten, ohne dass X Kandidatenschluessel ist? | Ja. Dann ist X Superschluessel; fuer Kandidatenschluessel muss X zusaetzlich minimal sein. |

## Normalformen

| Vorderseite | Rueckseite |
|---|---|
| Was ist ein Primattribut? | Ein Attribut, das in mindestens einem Kandidatenschluessel vorkommt. |
| Was ist ein Nicht-Primattribut? | Ein Attribut, das in keinem Kandidatenschluessel vorkommt. |
| Was ist 1NF? | Attributwerte sind atomar; keine wiederholten Gruppen oder mengenwertigen Attribute in einer Zelle. |
| Was ist 2NF? | 1NF plus: Kein Nicht-Primattribut haengt nur von einem echten Teil eines zusammengesetzten Kandidatenschluessels ab. |
| Was ist 3NF? | Fuer jede nichttriviale FD `X -> A` gilt: X ist Superschluessel oder A ist Primattribut. |
| Was ist BCNF? | Fuer jede nichttriviale FD `X -> Y` gilt: X ist Superschluessel. |
| Welche Normalform ist strenger: 3NF oder BCNF? | BCNF ist strenger. Jede BCNF-Relation ist in 3NF, aber nicht jede 3NF-Relation ist in BCNF. |
| Was ist eine nichttriviale FD? | Eine FD `X -> Y`, bei der Y nicht Teilmenge von X ist. |
| Was ist eine partielle Abhaengigkeit? | Ein Nicht-Primattribut haengt von einem echten Teil eines zusammengesetzten Schluessels ab. Problem fuer 2NF. |
| Was ist eine transitive Abhaengigkeit? | Ein Attribut haengt indirekt ueber ein anderes Nicht-Schluesselattribut vom Schluessel ab. Problem fuer 3NF. |

## Force, No-Force, Steal, No-Steal und Undo/Redo !

| Vorderseite                                      | Rueckseite                                                                                                  |
| ------------------------------------------------ | ----------------------------------------------------------------------------------------------------------- |
| Was bedeutet Force?                              | Bei Commit muessen alle geaenderten Seiten der Transaktion sofort auf die Platte geschrieben werden.        |
| Was bedeutet No-Force?                           | Bei Commit muessen geaenderte Seiten nicht sofort auf Platte geschrieben werden.                            |
| Was bedeutet Steal?                              | Seiten mit uncommitteten Aenderungen duerfen aus dem Puffer auf die Platte geschrieben werden.              |
| Was bedeutet No-Steal?                           | Uncommittete Aenderungen duerfen nicht auf Platte geschrieben werden.                                       |
| Wann braucht man Redo?                           | Bei No-Force, weil committete Aenderungen beim Crash eventuell noch nicht auf Platte stehen.                |
| Wann braucht man Undo?                           | Bei Steal, weil uncommittete Aenderungen beim Crash bereits auf Platte stehen koennen.                      |
| Welche Kombination braucht weder Undo noch Redo? | No-Steal und Force. Praktisch aber oft ineffizient.                                                         |
| Welche Kombination ist in vielen DBMS typisch?   | Steal und No-Force; dadurch braucht man Undo und Redo.                                                      |
| Warum nutzt man No-Force?                        | Bessere Performance, weil nicht bei jedem Commit sofort alle geaenderten Seiten geschrieben werden muessen. |
| Warum nutzt man Steal?                           | Bessere Pufferausnutzung, weil Seiten auch vor Commit ausgelagert werden duerfen.                           |

## B-Baum, B+-Baum, Binaerbaum

| Vorderseite | Rueckseite |
|---|---|
| Was ist ein B-Baum? | Balancierter Suchbaum mit mehreren Schluesseln pro Knoten, geeignet fuer blockorientierten Speicher. |
| Was ist ein B+-Baum? | Variante des B-Baums, bei der Datensaetze bzw. Datenverweise typischerweise nur in den Blaettern liegen; innere Knoten dienen als Index. |
| Wichtigster Unterschied B-Baum und B+-Baum? | Im B+-Baum liegen Daten in den Blaettern; innere Knoten enthalten nur Such-/Separatorinformationen. |
| Warum sind B+-Baeume gut fuer Datenbanken? | Hoher Fanout, geringe Hoehe, wenige Plattenzugriffe, effiziente Bereichsanfragen durch verkettete Blaetter. |
| Was ist ein Binaerbaum? | Baum, bei dem jeder Knoten hoechstens zwei Kinder hat. |
| Unterschied Binaerbaum und B+-Baum? | B+-Baum hat viele Kinder pro Knoten, ist blockorientiert und balanciert; ein Binaerbaum hat maximal zwei Kinder. |
| Was bedeutet Fanout? | Maximale Anzahl von Kindverweisen eines inneren Knotens. |
| Was bedeutet, dass ein B+-Baum balanciert ist? | Alle Blaetter liegen auf derselben Tiefe. |
| Was passiert beim Insert mit vollem B+-Baum-Knoten? | Der Knoten wird gesplittet; ein Separator wird in den Elternknoten eingefuegt. |
| Was passiert beim Delete mit Unterlauf? | Umverteilung mit Nachbarknoten oder Merge; ggf. muss der Elternknoten angepasst werden. |

## Monotonie von Anfragen

| Vorderseite | Rueckseite |
|---|---|
| Was bedeutet monotone Anfrage? | Wenn zusaetzliche Eingabedaten hinzugefuegt werden, verschwinden keine bisherigen Ergebnis-Tupel. |
| Formal: Wann ist Anfrage Q monoton? | Fuer Datenbanken `D subset D'` gilt `Q(D) subset Q(D')`. |
| Sind konjunktive Anfragen monoton? | Ja, positive konjunktive Anfragen ohne Negation/Differenz sind monoton. |
| Welche Operatoren sind typisch monoton? | Selektion, Projektion, Join, Vereinigung, positive Existenzbedingungen. |
| Welche Operatoren machen Anfragen oft nicht-monoton? | Differenz, Negation, `NOT EXISTS`, `EXCEPT`, manche "keine"-Anfragen. |
| Beispiel fuer nicht-monotone Anfrage? | "Finde Kunden, die nie bestellt haben." Wenn eine neue Bestellung eingefuegt wird, kann ein Kunde aus dem Ergebnis verschwinden. |
| Warum ist Monotonie bei regelbasierten Anfragen wichtig? | Sie beeinflusst, ob Ergebnisse durch Hinzufuegen von Fakten stabil wachsen oder wieder verschwinden koennen. |

## Mengen- und Multimengensemantik

| Vorderseite | Rueckseite |
|---|---|
| Was ist Mengensemantik? | Relationen enthalten jedes Tupel hoechstens einmal; Duplikate werden nicht unterschieden. |
| Was ist Multimengensemantik bzw. Bag-Semantik? | Tupel koennen mehrfach vorkommen; Duplikate zaehlen. |
| Welche Semantik nutzt klassische relationale Algebra meist? | Mengensemantik. |
| Welche Semantik nutzt SQL standardmaessig? | Multimengensemantik, ausser `DISTINCT` wird verwendet. |
| Was macht `DISTINCT` in SQL? | Entfernt Duplikate und erzwingt fuer das Ergebnis Mengensemantik. |
| Warum sind Algebra-Gesetze unter Bag-Semantik gefaehrlich? | Weil Duplikatanzahlen sich aendern koennen; Aequivalenzen aus der Mengensemantik gelten nicht immer. |
| Beispiel fuer Unterschied? | Projektion kann unter SQL ohne `DISTINCT` Duplikate behalten; in klassischer Algebra werden sie entfernt. |
| Was ist bei `UNION` in SQL wichtig? | `UNION` entfernt Duplikate, `UNION ALL` behaelt Duplikate. |
| Was ist bei Aggregation und Bag-Semantik wichtig? | Duplikate beeinflussen `COUNT`, `SUM`, `AVG` und damit das Ergebnis. |

