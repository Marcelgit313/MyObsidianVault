
---
## DFA
>[!Important]
>Ein __deterministischer endlicher Automat__ $A$ ist ein $5$-Tupel $A = (Q, \Sigma, \delta, q_0, F )$, wobei:
>- $Q$ eine __endliche__ Menge von __Zuständen__ ist
>-  $\Sigma$ ein __endliches Eingabealphabet__ ist
>- $\delta:Q\times\Sigma\rightarrow Q$ die __Transitionsfunktion (Übergangsfunktion)__ ist
>- $q_{0} \in Q$ der __Startzustand__ ist
>- $F\subseteq Q$ die Menge der __Endzustände__ ist

![[Pasted image 20240516123045.png]]

---
## NFA
>[!Important]
>Ein __deterministischer endlicher Automat__ $A$ ist ein $5$-Tupel $A = (Q, \Sigma, \Delta, I, F )$, wobei:
>- $Q$ eine __endliche__ Menge von __Zuständen__ ist
>-  $\Sigma$ ein __endliches Eingabealphabet__ ist
>- $\Delta:Q\times\Sigma\times Q$ die __Transitionsfunktion (Übergangsfunktion)__ ist
>- $I \subseteq Q$ die Menge der __Startzuständ__ ist
>- $F\subseteq Q$ die Menge der __Endzustände__ ist

![[Pasted image 20240516125014.png]]

---
## Satz von Rabin Scott
Jede von NFA erkannte Sprache kann auch von einem DFA erkannt werden

Um einen NFA in einen DFA umzuwandeln nutzt man den Potenzmengenautomat

---
## Potenzmengenautomat

![[Pasted image 20240808134621.png]]

---
## Reguläre Ausdrücke
- von regulären Ausdrücke zu NFA
- von DFA zu regulären Ausdrücken
- Abschlusseigenschaften
- Pumping Lemma für reguläre Sprachen
- Minimalautomat
- Myhill Nerode Auqivalenzrelation
## DFA-minimierung
![[Pasted image 20240808142131.png]]

---
## NFA-minimierung
![[Pasted image 20240808142216.png]]

---
- Wortproblem, Leerheitsproblem, Schnittproblem, Inklusionsproblem, Äqualenzproblem
- Grammatiken
## kontextfreie/ Grammatiken
![[Pasted image 20240808144225.png]]
![[Pasted image 20240808144212.png]]

---
- esiplon freie Grammatik
## Chomsky normalform
![[Pasted image 20240808142332.png]]
![[Pasted image 20240808142346.png]]
![[Pasted image 20240808142400.png]]

### Beispiel
![[Pasted image 20240808142457.png]]
![[Pasted image 20240808142528.png]]

---
## CYK-Algo
![[Pasted image 20240808142603.png]]

---
## Kellerautomat
![[Pasted image 20240808142730.png]]

Ein Kellerautomat ist eine Art Turingmaschine die einen Stack hat

![[Pasted image 20240808142930.png]]


---
## chomsky hierarchie
![[Pasted image 20240808143040.png]]

---
- typ 3 grammatik
## Turingmaschine
![[Pasted image 20240808143229.png]]

---
- church turning these
- while/goto Berechenbarkeit
- Entscheidbarkeit
- halteproblem
- satz von rice
- Postsches Korrespondenzproblem