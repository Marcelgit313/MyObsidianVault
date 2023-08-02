
## Abkürzungen
---

- RFC $\rightarrow$ Request for Comments
- IETF $\rightarrow$ Internet Engineering Task Force
- Datentransfer zwischen Startpunkt und Ziel
	- Connection-oriented reliable $\rightarrow$ TCP
	- Connection-less unreliable $\rightarrow$ UDP
- FDM $\rightarrow$ Frequency Division Multiplexing
- TDM $\rightarrow$ Time Division Multiplexing



## Protokoll
---
>Protokolle definieren das Format, Reihenfolge von Nachrichten, versendet und empfangen, für Netzwerkgeräte und ergriffene Maßnahmen für die Übermittlung und den Empfang von Nachrichten


## Circuit switching
---
Circuit switching ist eine Übertragungstechnik bei der Zeitweise eine durchgeschaltete Verbindung mit konstanter Bandbreite zugeordnet wird. z.B. ein Kabel verbindet direkt zwei PCs


![[Pasted image 20230802191335.png ]]


- End-to-end
- man bekommt eine Leitung zugeordnet
- no sharing of resources
	- Leitung wird nicht genutzt wenn nicht vom Anruf gebraucht
- garantierte performance


## Packet switching
---
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


---
