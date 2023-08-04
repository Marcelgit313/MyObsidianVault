## Polling
--- 
Es gibt einen Master der nacheinander die anderen Geräte im Netz frag ob sie daten schicken wollen. Normal wird das nur im Zusammenhang mit "dummen" Geräten benutzt. Ein Vorteil ist das es nur einen Fehlerpunkt geben kann und das ist der Master. Außerdem kann die Latency deutlich höher sein als sonnst. 

![[Pasted image 20230804145426.png]]


## Token Passing
---
Ein Token wird im Kreis zu jedem Gerät weiter gegeben. Wer den Token hat darf senden wenn er was zu senden hat. Fehlerpunkt: Token

![[Pasted image 20230804145503.png]]