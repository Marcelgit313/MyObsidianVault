
---
## Wörter
- Ein _Alphabet_ ist eine nicht leere endliche Menge $\Sigma$
- Ein Element $a\in\Sigma$ eines Alphabets $\Sigma$ nennen wir _Symbol_ oder _Zeichen_
- Ein _Wort_ über dem Alphabet $\Sigma$ ist eine endliche Zeichenkette der Form:
	- $a_{1}a_{2}....a_{n}$ mit $a_{i}\in\Sigma$ für $1\le i\le n$ 
- Das _leere Wort_ ist das Wort der länge $0$ und wird dargestellt mit $\varepsilon$

- Die länge eines Wortes $w=a_0a_1...a_n$ ist $n$. Man schreibt auch $|w|=n$ 
- Die Menge aller Wörter über dem Alphabet $\Sigma$ wird bezeichnet als $\Sigma^*$ 
- Die Menge aller nicht leeren Wörter ist $\Sigma^{+}=\Sigma^{*}\setminus \varepsilon$ 

#### Konvention
- Üblicherweise verwenden wir Kleinbuchstaben a, b, c, . . . als Symbole und u, v , w , x, y , z, . . . als Bezeichnet für Wörter.

#### Konkatenation von Wörtern
- Das aneinander hängen von Wörtern ist die __Konkatenation__ von Wörtern
- das ist eine binäre Operation $\Sigma^{*}\times\Sigma^*\rightarrow\Sigma^*$ 

---
## Sprachen
Sei $\Sigma$ ein Alphabet. Eine (formale) Sprache L über dem Alphabet $\Sigma$ ist eine beliebige
Teilmenge von $\Sigma^*$, d.h. $L\subseteq \Sigma^*$ 

![[Pasted image 20240516121133.png]]

Sei $\Sigma$ eine Alpabet:
- Die _leere Sprache_ $\emptyset$ ist eine Sprache
- $\lbrace\varepsilon\rbrace$ ist eine Sprache
- $\Sigma^*$ ist eine Sprache


