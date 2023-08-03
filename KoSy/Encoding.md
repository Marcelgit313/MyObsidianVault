
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

## Manchester