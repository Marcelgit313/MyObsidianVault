## Context
---
Hosts und Router werden auch Nodes genannt, Kommunikationskanäle die verschiedene Nodes verbinden nennt man [Links](Link.md), diese können über Kabel, Kabellos oder LANs funktionieren.
Ein Paket der Link Layer nennt man Frame, dieser encapsulated Daten.

> Die Link-Layer hat die Verantwortung dafür das die Daten von einer Node zu einer anderen Physisch benachbarten Node über einen Link Transportiert werden

Ein Datagram wird über verschiedene Link Protokolle über verschiedene Links verschickt, z.b. WiFi -> Ethernet. Jedes Protokoll bietet unterschiedliche Services, ein Protokoll könnte z.b eine zuverlässige Datenübertragung sicherstellen, oder eben nicht.

Die Link Layer bietet folgende Services:
Encapsulte die Daten in einen Frame und füge sowohl einen Header als auch einen Trailer hinzu, falls wir über ein [geteiltes Medium](Multiplexing.md) senden bietet die Layer Kanalzugriff und die MAC Adresse im Header des Frames identifiziert die Quell und Zieladresse.

## Link Layer Services
---
- Flow control:
	- Pacing zwischen angrenzendem Senden und Empfangsknoten

- Error detection:
	- Errors durch signal attenuation(Signal abschwächung) oder noise im channel
	- Empfänger detect Errors

- Error correction:
	- Empfänger identifiziert und korrigiert bit error(s) ohne neu Übermittlung

- Half-duplex and full-duplex
	- mit einem half-duplex können beide nodes an beiden Enden übertragen, aber nicht zur gleichen Zeit
