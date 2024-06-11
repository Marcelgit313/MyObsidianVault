> Lauterbach Jannis, Schneider Eric, Wirdel Marcel
---
## Aufgabe 1
### _(a)_
Damit der Algorithmus $\binom{n}{2}$ Vergleiche benötigt suchen wir unsere Pivots so aus, dass wir den Worst Case erreichen. Dafür muss das Pivotelement immer das kleinste oder größte Element der Menge sein. In unseren Beispiel wählen wir als erstes Pivot 8 aus, dann 10, 15 und dann im selben Muster immer das nächst kleinste Element. So unterteilen wir die Menge immer in möglichst große Teilmengen und benötigen die maximale Anzahl an Vergleichen $\binom{15}{2} = 105$
### _(b)_
Damit der Algorithmus weniger als $n \cdot ln(n)$ Vergleiche benötigt suchen wir unsere Pivots so aus, dass wir den Best Case erreichen. Dafür muss als Pivotelement immer das Median-Element gewählt werden, um die Menge in möglichst gleich große Teilmengen aufzuteilen, was für möglichst wenige Vergleiche sorgt. In unseren Fall wählen wir als Pivot die folgenden Elemente: 
![[Pasted image 20240611173307.png]] 
Der Algorithmus benötigt dann 14 Vergleiche mit dem Pivot 62, jeweils 6 Vergleiche mit den Pivots 50, 75 und jeweils 2 Vergleiche mit den Pivots 10, 58, 67, 87. Insgesamt kommen wir dann auf $2+2+2+2+6+6+14 = 34$ Vergleiche, da $15*ln(15) \approx 40,6$ und $34<40,6$ brauchen wir weniger als $n \cdot ln(n)$ Vergleiche.

---
## Aufgabe 2
### _(a)_
$$A\cdot x= \Bigg(\sum\limits_{j=1}^{n}a_{ij}x_{j}\Bigg)_{i=1..n}$$
Die Formel hat die Laufzeit $O(n^2)$ da, man durch eine $n\times n$ Matrix muss also hat man $n^{2}$ Zahlen in der Matrix also auch $n^2$ Multiplikation. Dadurch hat man eine Laufzeit von $O(n^2)$ 
### _(b)_
$$A\cdot B = \Bigg(\sum\limits_{j=1}^{n}a_{ij}b_{jk}\Bigg)_{i,k=1...n}$$
Wir haben zwei Matrizen mit $n\times n$. Um diese Matrizen jetzt miteinander zu multiplizieren wird jede Zeile von $A$ mal alle Spalten von $B$ multipliziert also haben wir $n^2$ Multiplikationen. Um jetzt die ganze Matrix zu multiplizieren müssen wir das ganze $n$ mal wieder holen, da die Matrizen $n\times n$ sind. Dann haben wir eine Laufzeit von $O(n^3)$ 
### _(c)_
$$A\cdot B =C$$
Eine Idee für einen Monte-Carlo-Algorithmus mit einseitigem Fehler ist:

### Idee
1. Einen zufälligen Vektor der Länge $n$ generieren $r\in\mathbb{R}^n$ 
2. Matrix-Vektor-Multiplikation:
	- Berechne den Vektor $x=B\cdot r$
	- Berechne den Vektor $y=A\cdot x= A\cdot(B\cdot r)$ 
	- Berechne den Vektor $z=C\cdot r$ 
3. Vergleichen der Ergebnisse:
	- Vergleiche die Vektoren $z$ und $y$ 
	- Wenn $z = y$, gebe $true$ zurück
	- Wenn $z\neq y$, gebe $false$ zurück

### Laufzeit
Wir haben eine Matrix-Vektor-Multiplikation diese hat eine Laufzeit von $O(n^{2})$ . Diese wird drei mal im Algorithmus berechnet also $n^{2}+n^{2}+n^2$ also eine Laufzeit von $O(n^2)$ 
 
---
## Aufgabe 3
### _(a)_
```python
import random

comparison_count = 0  

def quicksort(a):
    global comparison_count
    if len(a) <= 1:
        return a
    else:
        pivot_index = random.randint(0, len(a) - 1)
        pivot = a[pivot_index]
        a.append(pivot)
        a.pop(pivot_index)
        pop_count = 0
        for i in range(0, len(a)-1):
            comparison_count += 1
            if a[i-pop_count] >= pivot:
                a.append(a[i-pop_count])
                a[i-pop_count]
                a.pop(i-pop_count)
                pop_count += 1
        pivot_index = len(a)-1-pop_count

        left = quicksort(a[0:pivot_index:1])
        right = quicksort(a[pivot_index+1:len(a):1])
  
        return left + [a[pivot_index]] + right

a = [9,3,8,4,8,6,2,8,3,7,0,10,7,4,1,5]
result = quicksort(a)
print(result)
```
**Eingabe:** $a = [9,3,8,4,8,6,2,8,3,7,0,10,7,4,1,5]$
**Ausgabe:** $[0, 1, 2, 3, 3, 4, 4, 5, 6, 7, 7, 8, 8, 8, 9, 10]$
### _(b)_
```python
import matplotlib.pyplot as plt
import random

comparison_count = 0  

def quicksort(a):
    global comparison_count
    if len(a) <= 1:
        return a
    else:
        pivot_index = random.randint(0, len(a) - 1)
        pivot = a[pivot_index]
        a.append(pivot)
        a.pop(pivot_index)
        pop_count = 0
        for i in range(0, len(a)-1):
            comparison_count += 1
            if a[i-pop_count] >= pivot:
                a.append(a[i-pop_count])
                a[i-pop_count]
                a.pop(i-pop_count)
                pop_count += 1
        pivot_index = len(a)-1-pop_count

        left = quicksort(a[0:pivot_index:1])
        right = quicksort(a[pivot_index+1:len(a):1])

        return left + [a[pivot_index]] + right

def random_array(size):
    a = []
    for i in range(size):
        a.append(random.randint(0, 1000000))
    return a
    
sizes = [10, 50, 100, 250, 500, 1000, 1500,2500, 5000, 100000]
comparisons = []

for s in sizes:
    comparison_count = 0
    a  = random_array(s)
    quicksort(a)
    comparisons.append(comparison_count)

print("Getestet mit folgenden Array-Größen:", sizes, "ergaben folgende Anzahl an vergleichen:", comparisons)
plt.plot(sizes, comparisons, marker="x")
plt.xlabel("Size")
plt.ylabel("Comparisons")
plt.show()
```
**Eingabe:** $\text{sizes} = [10, 50, 100, 250, 500, 1000, 1500,2500, 5000, 100000]$
**Ausgabe:** 
```shell
Getestet mit folgenden Array-Größen: [10, 50, 100, 250, 500, 1000, 1500, 2500, 5000, 10000] ergaben folgende Anzahl an vergleichen: [23, 305, 608, 2168, 4787, 10161, 17703, 30706, 68631, 153758]
```
![[Pasted image 20240611173951.png]]