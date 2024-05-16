
---
>[!Important]
>Ein __deterministischer endlicher Automat__ $A$ ist ein $5$-Tupel $A = (Q, \Sigma, \Delta, I, F )$, wobei:
>- $Q$ eine __endliche__ Menge von __Zuständen__ ist
>-  $\Sigma$ ein __endliches Eingabealphabet__ ist
>- $\Delta:Q\times\Sigma\times Q$ die __Transitionsfunktion (Übergangsfunktion)__ ist
>- $I \subseteq Q$ die Menge der __Startzuständ__ ist
>- $F\subseteq Q$ die Menge der __Endzustände__ ist

Notation: Statt $(p,a,q)\in \Delta$  schreibt man oft $p\overset{a}{\rightarrow} q$ für Transitionen

---
# Beispiel
![[Pasted image 20240516125014.png]]