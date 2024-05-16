## Aufgabe 2
### a)

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

### b)
**Eingabe:** $n=7,\ m=3$
**Ausgabe:**
```shell
Eingabe von n: 7
Eingabe von m: 3
{(5, 1, 1), (3, 3, 1), (4, 2, 1), (3, 2, 2)}
```


