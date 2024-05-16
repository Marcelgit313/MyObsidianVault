>Jannis Lauterbach, Eric Schneider, Marcel Wirdel
---
## Aufgabe 1
### _(a)_
Zu zeigen ist, dass $\sum\limits_{j=0}^{n} \binom{n}{j} = 2^{n}$. $\binom{n}{j}$ bezeichnet die Anzahl der $j$-elementigen Teilmengen einer $n$-elementigen Menge ist. Somit entspricht die Summe $\sum\limits_{j=0}^{n} \binom{n}{j}$ der Anzahl aller Teilmengen der $n$-elementigen Menge, also die Mächtigkeit Potenzmenge. Gemäß Satz 1.1.2 aus der Vorlesung gilt $|2^{M}| = 2^{|M|}$ für eine beliebige endliche Menge $M$. Da $M$ hier die Menge aller Teilmengen der $n$-elementigen Menge ist, gilt also $|\sum\limits_{j=0}^{n} \binom{n}{j}| = 2^{n}$. Daraus folgt, dass $\sum\limits_{j=0}^{n} \binom{n}{j} = 2^{n}$. 
### _(b)_
Zeigen für alle $n\in \mathbb{N_{0}}$ :
$$\sum\limits_{j=0}^{n}\dbinom{n}{j}^{2}=\dbinom{2n}{n}$$
Umschreiben der $2$er Potenz
$$\begin{align}
\sum\limits_{j=0}^{n}\dbinom{n}{j}^{2}&=\sum\limits_{j=0}^{n}\dbinom{n}{j}\cdot \dbinom{n}{j} \\
\iff\sum\limits_{j=0}^{n}\dbinom{n}{j}\cdot \dbinom{n}{j}&=\sum\limits_{j=0}^{n}\dbinom{n}{j}\cdot \dbinom{n}{n-j}\text{\qquad|Proposition 1.2.5}\\
\iff\sum\limits_{j=0}^{n}\dbinom{n}{j}\cdot \dbinom{n}{n-j}&=\sum\limits_{j=0}^{n}\dbinom{n+n}{n}\text{\qquad |Proposition 1.2.12}\\ 
\iff\sum\limits_{j=0}^{n}\dbinom{n+n}{n}&=\dbinom{2n}{n}\\
\end{align}$$
$\blacksquare$

---
## Aufgabe 2
### _(a)_
```python
def partition(n, m):
    if m > n:
        return []
    if m == 1:
        return [[n]]
    
    result = []
    for c in range(1, n - (m - 1) + 1):
        for subpartition in partition(n - c, m - 1):
            result.append([c] + subpartition)
    
    return result  
  
n = int(input("Eingabe von n: "))
m = int(input("Eingabe von m: "))
result = partition(n, m)
result_set = set()
for sr in result:
    sorted_sr = sorted(sr, reverse=True)
    tuple_sr = tuple(sorted_sr)
    result_set.add(tuple_sr)
  
print(result_set)
```

**Eingabe:** $n=7,\ m=3$
**Ausgabe:**
```shell
Eingabe von n: 7
Eingabe von m: 3
{(5, 1, 1), (3, 3, 1), (4, 2, 1), (3, 2, 2)}
```

### _(b)_
$n=7, m=3$
In unserem Algorithmus wird in diesem Fall kein Base-Case ausgelöst. Dann wird die Liste erstellt indem wir unser Ergebnis speichern. Danach geht der Algorithmus in den ersten $for$-Loop, die Variable $c$ ist in der ersten Iteration $1$ und läuft bis $n-(m-1)$.

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
	- Wenn $c=5$, dann $partition(5,1)$ gibt $[[5]]$, daher ergibt sich $[[5,1]]$
- Zusammenfügen der Ergebnisse $[[1,5],[2,4],[3,3],[4,2],[5,1]]$

Zurück zum Aufruf von $partition(7,3)$:
- Die Ergebnisse werden jetzt nochmal jeweils mit $c=1$ aus der äußeren Schleife kombiniert
- $[[1,1,5],[1,2,4],[1,3,3],[1,4,2],[1,5,1]]$

Alle weiteren Schleifen durchläufe:
- Wenn $c=2$ : $[[2,1,4],[2,2,3],[2,3,2],[2,4,1]]$
- Wenn $c=3$ : $[[3,1,3],[3,2,2],[3,3,1]]$
- Wenn $c=4$ : $[[4,1,2],[4,2,1]]$
- Wenn $c=5$ : $[[5,1,1]]$

Nach der letzten Iteration gehen wir ein letztes mal durch unsere Ergebnisliste und sortieren die einzelnen Partitionen absteigend. Dann werden diese einem Set hinzugefügt, dadurch fallen doppelt Partitionen weg. 


---
## Aufgabe 3


---
## Aufgabe 4
### _(a)_
Die Menge $M=\lbrace1,2,3,4 \rbrace$ hat $15$ verschiedene Äquivalenzrelationen:
$$\begin{align} &\lbrace \lbrace 1, 2, 3, 4\rbrace\rbrace\\ &\lbrace \lbrace 1, 2, 3 \rbrace, \lbrace 4\rbrace\rbrace\\ &\lbrace \lbrace 1, 2, 4 \rbrace, \lbrace 3\rbrace\rbrace\\ &\lbrace \lbrace 1, 3, 4 \rbrace, \lbrace 2\rbrace\rbrace\\ &\lbrace \lbrace 2, 3, 4 \rbrace, \lbrace 1\rbrace\rbrace\\ &\lbrace \lbrace 1, 2 \rbrace, \lbrace 3, 4\rbrace\rbrace\\ &\lbrace \lbrace 1, 3 \rbrace, \lbrace 2, 4\rbrace\rbrace\\ &\lbrace \lbrace 1, 4 \rbrace, \lbrace 3, 2\rbrace\rbrace\\ &\lbrace\lbrace 1, 2\rbrace,\lbrace 3\rbrace,\lbrace4\rbrace\rbrace\\ &\lbrace\lbrace 1,3\rbrace, \lbrace2\rbrace,\lbrace4\rbrace\rbrace\\ &\lbrace\lbrace 1, 4\rbrace,\lbrace 2\rbrace, \lbrace 3\rbrace\rbrace\\ &\lbrace\lbrace 2, 3\rbrace,\lbrace 1\rbrace,\lbrace 4\rbrace\rbrace\\ &\lbrace\lbrace 2, 4\rbrace, \lbrace 1\rbrace,\lbrace3\rbrace\rbrace\\ &\lbrace\lbrace 3, 4\rbrace,\lbrace 1 \rbrace,\lbrace 2\rbrace\rbrace\\ &\lbrace\lbrace 1\rbrace,\lbrace 2\rbrace, \lbrace 3\rbrace,\lbrace 4\rbrace\rbrace \end{align}$$
### _(b)_

### _(c)_
$$B_{n}=\sum\limits_{k=0}^{n}S(n,k)$$
$S(n,k)$ ist die Anzahl der Partitionen einer n-elementigen Mengen in $k$ nichtleeren Teilmengen.
$$\begin{align}
S(4,0)=0\\
S(4,1)=1\\
S(4,2)=7\\
S(4,3)=6\\
S(4,4)=1
\end{align}$$
Also haben wir:
$$B_{4}=0+1+7+6+1=15$$

---
## Aufgabe 5
```Python
def partition(n, m):
	if m > n:
		return []
	if m == 1:
		return [[n]]
		
	result = []
	for c in range(1, n - (m - 1) + 1):
		for subpartition in partition(n - c, m - 1):
			result.append([c] + subpartition)
			
return result
print(partition(7,3))
```

## Ausgabe 
```shell
[[1, 1, 5], [1, 2, 4], [1, 3, 3], [1, 4, 2], [1, 5, 1], [2, 1, 4], [2, 2, 3], [2, 3, 2], [2, 4, 1], [3, 1, 3], [3, 2, 2], [3, 3, 1], [4, 1, 2], [4, 2, 1], 
[5, 1, 1]]
```
