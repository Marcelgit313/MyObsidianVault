## CRC
---
$n = r-1$ wobei $r$ die Länge des Generatorpolynoms ist. An die den Daten Frame werden $n$ Nullen angehängt. Anschließend wird der Datenframe durch den Generator geteilt. Die ersten $n$ Bits(von Links) des Rests werden anstatt der angehängten Nullen an den Datenframe angehängt.
- eine bessere error-detection Methode

[CRC berechnen](CRC.md)

## Single bit parity
---
- Entdeckt einzelne bit Errors
- [[Even parity]] man setzt das parity bit so das es eine gerade Anzahl an 1 gibt

![[Pasted image 20230803142504.png]]

## Two-dimensional bit parity
---
Mit Two-dimensional bit parity kann man Errors entdecken und auch korrigieren. Es wir noch eine zweiter parity bit eingeführt mit dem man Fehler auch beheben kann

![[Pasted image 20230803142848.png]]
