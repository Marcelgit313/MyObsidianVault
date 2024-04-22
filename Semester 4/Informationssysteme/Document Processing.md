
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
