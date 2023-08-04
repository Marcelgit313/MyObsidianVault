Wenn eine Node etwas zu senden hat wird es bei dem Random Access Protokoll direkt gesendet. Falls zwei Nodes gleichzeitig Senden dann kommt es zur "collision".

Random access MAC Protokoll specifies:
- Wie entdeckt man collisions
- Wie recovered man von einer collision (z.B. mit verzögerter Neusendung)

# Slotted ALOHA
---
ALOHA funktioniert so das die der channel in dem alle Geräte verbunden sind in frames eingeteilt wird. Jeder frame ist gleich groß. Die einzelnen Nodes fangen immer am Anfang eines Frames an zu senden und sind synchron. Wenn 2 oder mehr Nodes in einem Frame senden detect alle Nodes eine collision. 

### Ablauf
---
Eine Node überträgt einen Frame in nächsten Slot.

Falls es keine Kollision gibt kann die Node den nächsten Frame im nächsten Slot senden.
Falls es jedoch zur Kollision kommt überträgt die Node im nächsten Slot mit der Wahrscheinlichkeit $p$ bis es Funktioniert, da es sonnst zur selben Kollision erneut kommen würde.

![[Pasted image 20230804152238.png]]

### Vorteile
---
- wenn nur eine Node aktive ist kann sie mit voller Bandbreite des Kanals senden
- es müssen nur die Slots zwischen den Nodes synchronisiert werden
- einfach

### Nachteile
---
- Kollisionen verschwenden Slots
- unnötig leere Slots
- Clocks müssen synchronisiert werden
- Nodes könnten Kollisionen schneller erkennen als es braucht um das Paket zu senden  

## Effizienz
---
$N$ Nodes senden in jedem Slot mit der Wahrscheinlichkeit $p$:

Die Wahrscheinlichkeit das eine Node in einem Slot erfolgreich überträgt ist $p(1-p)^{N-1}$
Die Wahrscheinlichkeit das irgendeine Node in einem Slot erfolgreich überträgt: $Np(1-p)^{N-1}$


$$\begin{align}
P(p) &= Np(1-p)^{N-1}\\
P'(p) &= -N(N p -1)(1-p)^{N-2}
\end{align}$$
Jetzt suchen wir nach den Maxima

$$\begin{align*}
-N(N p -1)(1-p)^{N-2} &= 0\\
-(-p +1)^{N-2} (N p -1) &= -N(N p -1)(1-p)^{N-2}\\
-(-p +1 )^{N-2} (N p -1) &= 0 | \cdot -(-p +1 )^{N-2}\\
Np-1 &= 0\\
Np &= 1\\
p &= \frac{1}{N}\\

\end{align*}$$
Wenn wir jetzt $N$ gegen unendlich Streben lassen erhalten wir die Maximale Effizienz

$$
\begin{align*}
P(p) =& Np(1-p)^{N-1} | p = \frac{1}{N}\\
&N \frac{1}{N}(1- \frac{1}{N})^{N-1}\\
&\frac{\lim_{N\to\infty}\left( 1 - \frac{1}{N}\right)^{N}}{\lim_{N\to\infty}\left(1 - \frac{1}{N}\right)^1}\\\\
&\lim_{N\to\infty}\left( 1 - \frac{1}{N}\right)^{N} = \frac{1}{e}

\end{align*}
$$

Der Channel wird also nur ca $37\%$ der Zeit wirklich genutzt.

