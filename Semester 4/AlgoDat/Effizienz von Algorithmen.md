
---
Um die Effizienz von Algorithmen zu bestimmen, konzentriert man sich im Regelfall auf das Zählen von Elementaroperationen. Dies können z.B. folgende sein:

- Zuweisungen (allgemein Speicherzugriffe)
- Vergleiche
- arithmetische Operationen (Addieren, Multiplizieren,...)

### Beispiel
![[Pasted image 20240904135247.png]]

Die Laufzeit für folgenden Code ist:

- $T_{1}(n)=n \cdot T_2(n)$
- $T_{2}(n)= n \cdot (c + T_{3}(n))$
- $T_{3}(n) = n \cdot c$

