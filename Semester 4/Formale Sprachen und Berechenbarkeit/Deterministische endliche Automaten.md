
---
>[!Important]
>Ein __deterministischer endlicher Automat__ $A$ ist ein $5$-Tupel $A = (Q, \Sigma, \delta, q_0, F )$, wobei:
>- $Q$ eine __endliche__ Menge von __Zuständen__ ist
>-  $\Sigma$ ein __endliches Eingabealphabet__ ist
>- $\delta:Q\times\Sigma\rightarrow Q$ die __Transitionsfunktion (Übergangsfunktion)__ ist
>- $q_{0} \in Q$ der __Startzustand__ ist
>- $F\subseteq Q$ die Menge der __Endzustände__ ist

![[Pasted image 20240516122959.png]]

---
# DFA erkannte Sprache
Die von einem DFA $A=(Q,\Sigma,\delta,q_0,F)$ __erkannte Sprache__ ist
$$L(A)=\lbrace w\in\Sigma^*|\hat{\delta}(q0, w ) ∈ F \rbrace$$
Wir sagen, dass ein Wort $w\in\Sigma^*$ von $A$ _akzeptiert_ wird wenn $\hat{\delta}(q_{0},w)\in F$ 

---
# Reguläre Sprache
Eine Sprache $L\in \Sigma^*$ heißt __regulär__, wenn sie von einem DFA erkannt wird, d.h. es gibt einen DFA $A$ mit $L(A)=L$  

---
## Beispiel
![[Pasted image 20240516123045.png]]

---
