
---
# Warenkorbanalyse
Welche Objekte werden häufig zusammen gekauft?
Können wir Regeln angeben der Form: Kunden die Windeln kaufen, kaufen auch oft Bier

![[Pasted image 20240502102931.png]]
- Ein Itemset ist eine Menge von Objekten
	- Eine Transaktion $t$ ist ein Itemset mit dazu gehöriger Transaktions ID $t=(tid,I)$, wobei $I$ das Itemset der Transaktion ist

- Der Support von Itemset $X$ in einer Datenbank $D$ ist die Anzahl der Transaktionen in $D$, die $X$ enthalten
	$$Supp(X,D)=\lbrace t\in D:t\ enthält\ X\rbrace$$
- Die __relative Häufigkeit__ von Itemset $X$ in Datenbank $D$ ist:
$$supp(X,D)/|D|$$
--- 
## Assoziationsregeln
Support einer Regel
$$supp(X \rightarrow Y,D)=supp(X\cup Y,D)$$
Konfidenz der Regel
$$conf(X\rightarrow Y,D)=supp(X\cup Y,D)/supp(X,D)$$
Die Konfidenz ist die bedingte Wahrscheinlichkeit, dass eine Transaktion $Y$ enthält, wenn sie $X$ enthält

---
## Ein naiver Algorithmus
Betrachte jedes mögliche Itemset und teste ob es häufig ist.

Berechnen des Support dauert $O(|I|\times |D|)$ und es gibt $2^{|I|}$ mögliche Itemsets, also im Worstcase: $O(|I|\times|D|\times 2^{|I|})$ 