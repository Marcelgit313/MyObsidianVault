>Jannis Lauterbach, Eric Schneider, Marcel Wirdel
## Aufgabe 1
Zeigen für alle $n\in \mathbb{N_{0}}$ :
$$\sum\limits_{j=0}^{n}\dbinom{n}{j}^{2}=\dbinom{2n}{n}$$
Umschreiben der $2$er Potenz
$$\begin{align}
\sum\limits_{j=0}^{n}\dbinom{n}{j}^{2}&=\dbinom{n}{j}\cdot \dbinom{n}{j} \\
\sum\limits_{j=0}^{n}\dbinom{n}{j}\cdot \dbinom{n}{j}&=\dbinom{n}{j}\cdot \dbinom{n}{n-j}\text{\qquad|Proposition 1.2.5}\\
\sum\limits_{j=0}^{n}\dbinom{n}{j}\cdot \dbinom{n}{n-j}&=\dbinom{n+n}{n}\text{\qquad |Proposition 1.2.12}\\ 
\sum\limits_{j=0}^{n}\dbinom{n+n}{n}&=\dbinom{2n}{n}\\
\end{align}$$
$\blacksquare$
---
## Aufgabe 2


---
## Aufgabe 3

$$\begin{align}
|M_{1}\cup M_{2}\cup M_{3}\cup M_{4}|&=|M_{1}|+|M_2|+|M_3|+|M_4|\\
&-|M_{1}\cap M_2|-|M_{1}\cap M_3|-|M_{1}\cap M_4|\\
&-|M_{2}\cap M_3|-|M_{2}\cap M_4|\\
&-|M_{3}\cap M_4|\\
&+|M_{1}\cap M_{2}\cap M_3|\\
&+|M_{2}\cap M_{3}\cap M_4|\\
&+|M_{1}\cap M_{2}\cap M_4|\\
&+|M_{1}\cap M_{3}\cap M_4|\\
&-|M_{1}\cap M_{2}\cap M_{3}\cap M_4|
\end{align}$$

$|M_{1}|=|T_3|=\lfloor \frac{100000}{3}\rfloor =33333$
$|M_2|=|T_5|=\lfloor \frac{100000}{5}\rfloor =20000$
$|M_3|=|T_7|=\lfloor \frac{100000}{7}\rfloor =14285$
$|M_4|=|T_{11}|=\lfloor \frac{100000}{11}\rfloor =9090$

$|M_{1}\cap M_2|=\lfloor\frac{100000}{3\cdot 5}\rfloor=6666$
$|M_{1}\cap M_3|=\lfloor\frac{100000}{3\cdot 7}\rfloor=4761$
$|M_{1}\cap M_4|=\lfloor\frac{100000}{3\cdot 11}\rfloor=3030$
$|M_{2}\cap M_3|=\lfloor\frac{100000}{5\cdot 7}\rfloor=2857$
$|M_{2}\cap M_4|=\lfloor\frac{100000}{5\cdot 11}\rfloor=1818$
$|M_{3}\cap M_4|=\lfloor\frac{100000}{7\cdot 11}\rfloor=1298$

$|M_{1}\cap M_{2}\cap M_3|=\lfloor \frac{100000}{3\cdot 5\cdot 7}\rfloor =952$
$|M_{2}\cap M_{3}\cap M_4|=\lfloor \frac{100000}{5\cdot 7\cdot 11}\rfloor =259$
$|M_{1}\cap M_{2}\cap M_4|=\lfloor \frac{100000}{3\cdot 5\cdot 11}\rfloor =606$
$|M_{1}\cap M_{3}\cap M_4|=\lfloor \frac{100000}{3\cdot 7\cdot 11}\rfloor =432$

$|M_{1}\cap M_{2}\cap M_{3}\cap M_{4}|=\lfloor \frac{100000}{3\cdot 5\cdot 7\cdot 11}\rfloor =86$

$$\begin{align}
|M_{1}\cup M_{2}\cup M_{3}\cup M_{4}|&=33333+20000+14285+9090\\
&-6666-4761-3030\\
&-2857-1818\\
&-1298\\
&+952\\
&+259\\
&+606\\
&+432\\
&-86\\
&=58441
\end{align}$$

---
## Aufgabe 4
### a)
$$M=\{1,2,3,4\}$$  $$\begin{align} &\{\emptyset\} \\ \\ &\{\emptyset\} \cup \{1\} \\ \\ &\{\emptyset, \{1\}\} \cup \{\{\emptyset\} \cup \{2\}\} \cup \{\{1\}\cup\{2\}\} \\ \\ &\{\emptyset, \{1\},\{2\},\{1,2\}\} \cup \{\{\emptyset\} \cup \{3\}\} \cup \{\{1\} \cup \{3\}\} \cup \{\{2\} \cup \{3\}\} \cup \{\{1,2\} \cup \{3\}\} \\ \\ &\{\emptyset, \{1\},\{2\},\{3\},\{1,2\},\{1,3\},\{2,3\},\{1,2,3\}\} \cup \{\{\emptyset\} \cup \{4\}\} \cup \{\{1\} \cup \{4\}\} \cup \\ &\{\{2\} \cup \{4\}\} \cup \{\{1\} \cup \{3\}\} \cup \{\{1,2\} \cup \{4\}\} \{\{1,3\} \cup \{4\}\} \cup \{\{2,3\} \cup \{4\}\} \cup \\ &\{\{1,2,3\} \cup \{4\}\} \\ \\ &\{\emptyset, \{1\},\{2\},\{3\},\{4\},\{1,2\},\{1,3\},\{1,4\},\{2,3\},\{2,4\},\{3,4\}, \\ &\{1,2,3\},\{1,2,4\},\{1,3,4\},\{2,3,4\},\{1,2,3,4\}\} \end{align}$$

### b)
```python
def teilmengen(m, e):
    if len(m) == 0:
        e.append([0])
    else:
        for i in range(len(e)):
            e.append([e[i], m[len(m)-1]])
        m.pop()
        teilmengen(m,e)
    return e
    
e = [0]
m = [int(x) for x in input("Eingabe der Menge M: ").split(",")]
ergebnis = teilmengen(m, e)
print("Auflistung der Teilmengen:")
for i in range(1, len(ergebnis)):
    print(ergebnis[i])
```

Eingabe $M=\lbrace1,2,3,4\rbrace$
Ausgabe:
```shell
Auflistung der Teilmengen:
[0, 4]
[0, 3] 
[[0, 4], 3] 
[0, 2] 
[[0, 4], 2] 
[[0, 3], 2] 
[[[0, 4], 3], 2] 
[0, 1]
[[0, 4], 1] 
[[0, 3], 1] 
[[[0, 4], 3], 1] 
[[0, 2], 1] 
[[[0, 4], 2], 1] 
[[[0, 3], 2], 1] 
[[[[0, 4], 3], 2], 1] 
[0]
```
---
## Aufgabe 5
```python
def teilbare_zahlen(n):
    l = []
    for i in range(1, n + 1):
        if i % 3 == 0 or i % 5 == 0 or i % 7 == 0 or i % 11 == 0:
            l.append(i)
    return l
    
eingabe = input("Eingabe von N: ")
n = int(eingabe)
ergebnis = teilbare_zahlen(n)
print("Anzahl der teilbaren Zahlen bis ", n, " ist ", len(ergebnis))
print("Folgende Zahlen sind teilbar: ")
print(ergebnis)
```

Eingabe: $N=100$ Ausgabe:

```
Eingabe von N: 100 Anzahl der teilbaren Zahlen bis  100  ist  59 Folgende Zahlen sind teilbar: [3, 5, 6, 7, 9, 10, 11, 12, 14, 15, 18, 20, 21, 22, 24, 25, 27, 28, 30, 33, 35, 36, 39, 40, 42, 44, 45, 48, 49, 50, 51, 54, 55, 56, 57, 60, 63, 65, 66, 69, 70, 72, 75, 77, 78, 80, 81, 84, 85, 87, 88, 90, 91, 93, 95, 96, 98, 99, 100]
```


Eingabe: $N=500$ Ausgabe:

```
Eingabe von N: 500 Anzahl der teilbaren Zahlen bis  500  ist  292 Folgende Zahlen sind teilbar: [3, 5, 6, 7, 9, 10, 11, 12, 14, 15, 18, 20, 21, 22, 24, 25, 27, 28, 30, 33, 35, 36, 39, 40, 42, 44, 45, 48, 49, 50, 51, 54, 55, 56, 57, 60, 63, 65, 66, 69, 70, 72, 75, 77, 78, 80, 81, 84, 85, 87, 88, 90, 91, 93, 95, 96, 98, 99, 100, 102, 105, 108, 110, 111, 112, 114, 115, 117, 119, 120, 121, 123, 125, 126, 129, 130, 132, 133, 135, 138, 140, 141, 143, 144, 145, 147, 150, 153, 154, 155, 156, 159, 160, 161, 162, 165, 168, 170, 171, 174, 175, 176, 177, 180, 182, 183, 185, 186, 187, 189, 190, 192, 195, 196, 198, 200, 201, 203, 204, 205, 207, 209, 210, 213, 215, 216, 217, 219, 220, 222, 224, 225, 228, 230, 231, 234, 235, 237, 238, 240, 242, 243, 245, 246, 249, 250, 252, 253, 255, 258, 259, 260, 261, 264, 265, 266, 267, 270, 273, 275, 276, 279, 280, 282, 285, 286, 287, 288, 290, 291, 294, 295, 297, 300, 301, 303, 305, 306, 308, 309, 310, 312, 315, 318, 319, 320, 321, 322, 324, 325, 327, 329, 330, 333, 335, 336, 339, 340, 341, 342, 343, 345, 348, 350, 351, 352, 354, 355, 357, 360, 363, 364, 365, 366, 369, 370, 371, 372, 374, 375, 378, 380, 381, 384, 385, 387, 390, 392, 393, 395, 396, 399, 400, 402, 405, 406, 407, 408, 410, 411, 413, 414, 415, 417, 418, 420, 423, 425, 426, 427, 429, 430, 432, 434, 435, 438, 440, 441, 444, 445, 447, 448, 450, 451, 453, 455, 456, 459, 460, 462, 465, 468, 469, 470,  471, 473, 474, 475, 476, 477, 480, 483, 484, 485, 486, 489, 490, 492, 495, 497, 498, 500]
```


Eingabe: $N=100000$ Ausgabe (bei der hohen Anzahl haben wir die Auflistung der einzelnen Zahlen weg gelassen und nur die Anzahl rausgegeben):

```
Eingabe von N: 100000 Anzahl der teilbaren Zahlen bis  100000  ist  58441
```