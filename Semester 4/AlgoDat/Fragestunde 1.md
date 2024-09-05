
---
## 1
Kosten für jede Operation auf Konto zahlen
pop: +0M
push: +2M
clear: +0M
## 2
Zeigen dass Konto bei beliebiger Operationenfolge nicht negativ wird

### worst case
push
1) +2M -1M = 1M
2) -n * M +1M

$-n \cdot M$ wurde bereits bezahlt, da zu löschende Elemente vorher eingefügt