> Jannis Lauterbach, Eric Schneider, Marcel Wirdel
---
## Aufgabe 1

---
## Aufgabe 2
### _(a)_
```python
def partition(n, m): 
	if n < m: 
		return set() 
	if m == 1: 
		return {(n,)} 
		
	partition_set = set() 
	
	for c in range(1, (n - m) + 1): 
		for subpartition in partition(n - c, m - 1): 
			new_partition = tuple(sorted((c,) + subpartition,reverse=True))
			partition_set.add(new_partition) 
			
	return partition_set 

result = partition(7, 3) 
print(result)
```
### _(b)_
$n=7, m=3$
In unserem Algorithmus wird in diesem Fall kein Base-Case ausgelöst. Dann wird das Set erstellt indem wir unser Ergebnis speichern. Danach geht der Algorithmus in den ersten $for$-Loop, die Variable $c$ ist in der ersten Iteration $1$ und läuft bis $n-m$.

Dann geht der Algorithmus in den zweiten $for$-Loop. In diesem wird die Funktion rekursiv aufgerufen mit $n-c$ und $m-1$.

Rekursiver Aufruf $n=6, m=2$
- $c=1$ 
- Rekursiver Aufruf $n=5,m=1$
	- Da $m=1$ gibt es nur eine Möglichkeit: $[[5]]$
- Zusammenfügen der Ergebnisse $[[1]+[5]]$
- Also ergeben sich für $partition(6,2)$
	- Wenn $c=2$, dann $partition(4,1)$ gibt $[[4]]$, daher ergibt sich $[[2,4]]$
	- Wenn $c=3$, dann $partition(3,1)$ gibt $[[3]]$, daher ergibt sich $[[3,3]]$
	- Wenn $c=4$, dann $partition(2,1)$ gibt $[[2]]$, daher ergibt sich $[[4,2]]$
- Zusammenfügen der Ergebnisse $[[1,5],[2,4],[3,3],[4,2]]$

Zurück zum Aufruf von $partition(7,3)$:
- Die Ergebnisse werden jetzt nochmal jeweils mit $c=1$ aus der äußeren Schleife kombiniert
- dabei werden die Tupel sortiert und doppelte Tupel fallen weg beim hinzufügen ins Set
- $[[5,1,1],[4,2,1],[3,3,1]]$

Alle weiteren Schleifen durchläufe:
- Wenn $c=2$ : $[[2,2,3]]$
- Wenn $c=3$ : $[]$
- Wenn $c=4$ : $[]$

Am Ende wird noch alles in ein Set gepackt.

---
## Aufgabe 3
### _(a)_
```python
def partition(n, m): 
	if n < m: 
		return set() 
	if m == 1: 
		return {(n,)} 
		
	partition_set = set() 
	
	for c in range(0, (n - m) + 1): 
		for subpartition in partition(n - c, m - 1): 
			new_partition = tuple(sorted((c,) + subpartition,reverse=True))
			partition_set.add(new_partition) 
			
	return partition_set 

result = partition(7, 3) 
print(result)
```
### _(b)_
Der Algorithmus funktioniert genau gleich für nichtnegative Zahlen. Es kommt nur eine weiterer Schleifendurchlauf hinzu für $c=0$ :
$$[[7,0,0],[4,3,0],[6,1,0],[5,2,0]]$$
Also hat man am Ende des Algorithmus $8$ verschiedene Partitionen:
$$[[7,0,0],[4,3,0],[6,1,0],[5,2,0],[5,1,1],[4,2,1],[3,3,1],[2,2,3]]$$

---
## Aufgabe 4
### _(a)_ 
Die Wahrscheinlichkeit, dass bei einem Wurf eines sechsseitigen Würfels keine 6 gewürfelt wird liegt bei $\frac{5}{6}$, bei $m$ Würfen liegt die Wahrscheinlichkeit kein einziges Mal eine 6 zu würfeln also bei $\bigl(\frac{5}{6}\bigr)^m$ 
### _(b)_ 
Die Wahrscheinlichkeit bei $m$ Würfen mindestens eine 6 zu würfeln bildet sich aus dem Komplementergebnis keine einzige 6 zu würfeln. Also ist die Wahrscheinlichkeit bei $m$ Würfen mindestens eine 6 zu würfeln $1 - \bigl(\frac{5}{6}\bigr)^m$ Um Anzahl die der Würfe zu berechnen, bei der die Wahrscheinlichkeit mindestens eine 6 zu würfeln, über 50% steigt, stellen wir eine Ungleichung auf und stellen nach $m$ um. $$\begin{align} &1 -\biggl(\frac{5}{6}\biggr)^m > 0.5 \text{\qquad|-1}\\\\ &-\biggl(\frac{5}{6}\biggr)^m > -0.5 \text{\qquad| \(\cdot\) (-1)} \\\\ &\biggl(\frac{5}{6}\biggr)^m < 0.5 \text{\qquad| log} \\\\ &m \ log\biggl(\frac{5}{6}\biggr) < log(0.5) \text{\qquad| /log\(\biggl(\frac{5}{6}\biggr)\)} \\\\ &m > \frac{log(0.5)}{log(\frac{5}{6})} \\\\ &m > \frac{log(0.5)}{log(\frac{5}{6})} \approx 3.801 \end{align}$$ Da $m$ die Anzahl der Würfe darstellt muss das Ergebnis auf eine ganze Zahl aufgerundet werden, somit ist $m \ge 4$ . Also liegt die Wahrscheinlichkeit, das Spiel zu gewinnen, ab 4 Würfen über 50%.