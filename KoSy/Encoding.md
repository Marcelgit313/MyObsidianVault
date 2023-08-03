
## Binary Encoding (Non-Return To Zero)
---
Bei Binary Encoding wird für eine 1 zu übertragen die Amplitude angehoben und bleibt solange wie 1 übertragen wird auf dieser höhe und fällt danach wieder ab. Aufeinander folgende 1s oder 0s sind immer schlecht, weil es schwierig ist diese Richtig zu erkennen oder Fehler zu erkennen.

![[Pasted image 20230803120934.png]]
### Vorteile
- simple und günstig
- gute Bandbreite 1 baut $\leftrightarrow$ 1 bit/s 

### Nachteile
- Kein "[self-clocking](self%20clocking-baseline%20drift.md)"
- Problem von [baseline drift](self%20clocking-baseline%20drift.md)

## Binary Encoding (Non-Return To Zero Inverted)
---
Bei Inverted Binary Encoding wird das Problem von aufeinander folgenden 1s behoben aber nicht von 0s. Hierbei wird immer shifted wenn eine 1 übertragen wird.

![[Pasted image 20230803122849.png]]

### Vorteile
- simple und günstig
- gute Bandbreite 1 baut $\leftrightarrow$ 1 bit/s 

### Nachteile
- Kein "[self-clocking](self%20clocking-baseline%20drift.md)"
- Problem von [baseline drift](self%20clocking-baseline%20drift.md)
- aufeinander folgende 0s

## Manchester Encoding
---
Bei Manchester Encoding wird immer in der Mitte einer Übertragung von einem bit einen Übergang von High to low oder anderes herum. Wie rum das passiert entscheidet ob eine 1 oder 0 übertragen wird. Wenn von Low-High dann wird eine 0 übertragen, wenn von High-Low dann wird eine 1 Übertragen.

![[Pasted image 20230803123631.png]]

### Vorteile
- Self-clocking möglich


## Nachteile
- Zwei Symbole pro bit: 1 baud $\leftrightarrow$ 0.5 bit/s
- bisschen complexer

>benutzt in 10 Mbit/s-Ethernet


## 4B5B Encoding
---
Bei 4B5B Encoding wird NRZ-I benutzt. Bei jeder Übertragenen 1 ist ein Übergang aber die Übertragenen 1 und 0 werden dann noch encoded. Man nimmt 5 übertragene bits und encoded diese mit einer Tabelle auf 4 bits.

![[Pasted image 20230803130340.png]]

### Tabelle zum Encoden

![[Pasted image 20230803130353.png]]