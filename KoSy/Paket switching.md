[Circuit-switching](Circuit%20switching.md)

Packet switching ist ein Verfahren zur Datenübertragung. Bei längeren Nachrichten werden diese in einzelne Pakete unterteilt.

Ein Paket enthält typischerweise
- die Quelle des Paketes
- das Ziel des Paketes
- die Länge des Datenteils
- die Paketlaufnummer
- die Klassifizierung des Paketes 
- den Datenteil


![[Pasted image 20230802192505.png]]

- Store and forward
	- Packets move one hop at a time
	- Node receives complete packet before forwarding
- User A,B teilen sich das Netzwerk

## Store and Forward
---
Pakete wandern immer einen "Hop" einzelne Knoten erhalten das gesamte Paket bevor es weiter gesendet wird.

## Time Division Multiplexing 
---
Bei TDM bekommt jeder Nutzer immer den selben Zeitslot in einem TDM-Frame

## Beispiel
---
Gegeben ist ein $1 \frac{Gb}{s}$ link. Jeder der $N$ Nutzer verwendet $100\frac{Mb}{s}$ wenn er aktiv ist, jeder Nutzer ist aktiv $10\%$ der Zeit

Wie viele Nutzer können das System Verwenden.

Bei $35$ Benutzern ist die Wahrscheinlichkeit, dass mehr als $10$ Benutzer gleichzeitig aktiv sind, kleiner als $0,0004$.
$$\sum\limits^{35}_{i=11} \left(35 \atop i\right)0.1^{i} \cdot 0.9^{35 -i}$$

## Is Packet switching better then Circuit switching
---
- gut für kurze daten bursts wegen Ressourcen sharing
- mehr delay wenn der buffer zu viele Pakete bekommt
	- braucht Protokolle um das zu verhindern
