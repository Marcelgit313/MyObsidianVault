
---
## Aufgabe 1
### a)
__Hamming-Editier-Distanz
$d(Oktupus, Kaktus)=7$

__Längste Gemeinsame Teilsequenz__

$d(Oktupus,Kaktus)=3$

Längste Teilsequenz: ktus

__Levenshtein-Distanz


|     | -   | K   | a   | k   | t   | u   | s   |
| --- | --- | --- | --- | --- | --- | --- | --- |
| -   | 0   | 1   | 2   | 3   | 4   | 5   | 6   |
| O   | 1   | 1   | 2   | 3   | 4   | 5   | 6   |
| k   | 2   | 1   | 2   | 2   | 3   | 4   | 5   |
| t   | 3   | 2   | 2   | 3   | 2   | 3   | 4   |
| u   | 4   | 3   | 3   | 3   | 3   | 2   | 3   |
| p   | 5   | 4   | 4   | 4   | 4   | 3   | 3   |
| u   | 6   | 5   | 5   | 5   | 5   | 4   | 4   |
| s   | 7   | 6   | 6   | 6   | 6   | 5   | 4   |

### b)




### c)
$k=3$
$$S(d_{1})={\text{Im Sommer ist},\text{Sommer ist es},\text{ist es wärmer},\text{es wärmer als},\text{wärmer als zuvor},\text{als zuvor im},\text{zuvor im Winter}}$
$$$$S(d_{2})={\text{Dieser Sommer ist},\text{Sommer ist wärmer},\text{ist wärmer als},\text{wärmer als je},\text{als je zuvor}}$$
${\text{Sommer},\text{ist},\text{wärmer},\text{als},\text{zuvor}}$

## Aufgabe 2
### a)
$score(q,d_{7})=2 \cdot \frac{7}{5} + 0$
$score(q,d_{6})=4 \cdot \frac{7}{5} + 0$


## Aufgabe 3

$argmax_{d_{1}}=0.5\cdot \frac{63}{5}-(1-0.5)\cdot 0=6.3$ 
