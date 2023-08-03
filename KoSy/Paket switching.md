
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

## Time Division Multiplexing 
---
Bei TDM bekommt jeder Nutzer immer den selben Zeitslot in einem TDM-Frame


## Is Packet switching better then Circuit switching
---
- gut für kurze daten bursts wegen Ressourcen sharing
- mehr delay wenn der buffer zu viele Pakete bekommt
	- braucht Protokolle um das zu verhindern
