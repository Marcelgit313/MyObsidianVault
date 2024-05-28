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
	
	for c in range(1, n - m + 1): 
		for subpartition in partition(n - c, m - 1): 
				new_partition = tuple(sorted((c,) + subpartition, reverse=True))partition_set.add(new_partition) return partition_set result = partition(7, 3) print(result)
```