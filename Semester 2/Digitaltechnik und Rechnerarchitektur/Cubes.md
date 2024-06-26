


## Partielle Ordnung

>[!IMPORTANT] Partielle Ordnung
Wir definieren die Folgende Partielle Ordnung über Cubes
> $$\text{cube}_{v}(v_1, g_1) \prec \text{cube}_v(v_2, g_2): \iff (v_1 \subset v_2) \land (g_1 \subset g_2)$$

Mann nennt dies dann $\text{cube}_v(v_1, g_1)$ überdeckt(covers) $\text{cube}_{v}(v_2, g_2)$



## Infimum/Supremum

>[!IMPORTANT] Supremum
Für die Cubes $C_1 = (v_1, g_1)$ und $C_2 = (v_2, g_2)$ definieren wir deren Infimum und Supremum als
> $\text{inf}(C_1, C_2) := (v_1 \cap v_2, g_1 \cap g_2)$

>[!IMPORTANT] Infimum
> $\text{sup}(C_1, C_2) := (v_1\cup v_2, g_1 \cup g_2)$ unter der Voraussetzung dass $(v_1 \cup v_2) \cap (g_1\cup g_2) = \lbrace\rbrace$



## Absorption

Um DNFs zu minimieren müssen wir wissen wenn wir Cubes durch andere Cubes ersetzen können.

>[!IMPORTANT] Absorption
> Die Disjunktion von Cubes $C_1 = (v_1, g_1)$ und $C_2 = (v_2, g_2)$ ist Äquivalent zu ihrem Infimum genau dann wenn eine der folgenden Bedingungen gilt:
> $C_1 \prec C_2$ also $v_1 \subseteq v_2$ und $g_1 \subseteq g_2$
> $C_2 \prec C_1$ also $v_2 \subseteq v_1$ und $g_2 \subseteq g_1$
> $v_1 \setminus v_2 = g_2 \setminus g_2 = \lbrace x\rbrace$ und $v_2 \setminus v_1 = g_1\setminus x g_2 = \lbrace\rbrace$
> $v_1 \setminus v_2 = g_2 \setminus g_1 = \lbrace\rbrace$ und $v_2 \setminus v_1 = g_1 \setminus g_2 = \lbrace x\rbrace$

## Adjazens

>[!IMPORTANT] Adjazens
> Cubes $\text{cube}_v(v_1, g_1)$ und $\text{cube}_v(v_2, g_2)$ sind Adjazent genau dann wenn eine der folgenden Bedingungen gilt:
> $v_1 = v_2 \cup \lbrace x\rbrace$ und $g_2 = g_1 \cup \lbrace x\rbrace$
> $v_2 = v_1 \cup \lbrace x\rbrace$ und $g_1 = g_2 \cup \lbrace x\rbrace$

fuer Adjazente Cubes $C_1, C_2$ haben wir $\text{cube}_v(C_1) \lor \text{cube}_v(C_2) \iff \text{cube}_v(inf(C_1, C_2))$

## Grad

> [!IMPORTANT] Grad
> Der Grad eines Cubes $\text{cube}_v(v, g)$ wird als die Anzahl an Variablen definiert die nicht in ihm Vorkommen also:
> $$|\text{cube}_v(v, g)| := |V\setminus (v \cup g)|$$

---

Daraus kann man einfach Folgen:

- Minterme haben den Grad 0
- $\text{cube}_v(C_1) \prec \text{cube}_v(C_2) \implies |\text{cube}_v(C_1)| \geq |\text{cube}_v(C_2)|$
- Jeder Cube vom Grad $k$ bedeckt $2^k$ minterme
- Adjazente Cubes $C_1, C_2$, haben den selben Grad
- Für Adjazente Cubes $C_1, C_2$ gilt $|\text{cube}_v(inf(C_1, C_2))| = |\text{cube}_v(C_i)| + 1$ für $i\in\lbrace1, 2\rbrace$



## Notation

Mit einer festen Variablenordnung koenne wir einen Cube $\text{cube}_v(v, g)$ als einen String aus den Symbolen $\lbrace1, 0, *\rbrace$ darstellen, das $i$-te Symbol im String gehoert zur $i$-ten Variable $x$ und das $i$-te Symbol wird so bestimmt:

$$\begin{cases}
1: x\in v\\
0 : x\in g\\
* : \text{sonst}
\end{cases}$$

Ein Cube des Grades $k$ enthält $k$ mal $*$. Cubes sind Adjazen wenn sie Sich an einer Stelle unterscheiden, wobei der eine Cube an der Stelle $1$ und der andere $0$ hat.

## Consens

> [!IMPORTANT] Consensus
> Der Consens $\mathbb C(C_1, C_2, x)$ Cube aus zwei Cubes $C_1 = (v_1, g_1)$ und $C_2 = (v_2, g_2)$ und einer Variable $x\in V$ ist definiert als
> $$\mathbb C(C_1, C_2, x) := (((v_1 \cup v_2) \setminus\lbrace x\rbrace), ((g_1 \cup g_2)\setminus \lbrace x\rbrace))$$
> Vorausgesetzt das $x\in v_1$ und $x\in g_2$,
> $((v_1 \cup v_2) \setminus \lbrace x\rbrace) \cap((g_1 \cup g_2) \setminus \lbrace x\rbrace) = \lbrace\rbrace$

Es gilt:
$$\text{cube}_V(cube_V)(\mathbb C(C_1, C_2, x)) \implies \text{cube}_V(C_1) \lor \text{cube}_V(C_2)$$


$$
\text{cube}_V(C_1) \lor \text{cube}_V(C_2) \iff \text{cube}_v(C_1) \lor \text{cube}_V(\mathbb C(C_1, C_2, x))
$$

Also der Consen von zwei Implikanten ist ein Implikant.

und 

Der Consen von zwei Primimplikanten ist ein Primimplikant.

