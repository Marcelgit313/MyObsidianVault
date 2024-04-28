
---
# Maximale Marginale Relevanz
Das nächste zurückgegebene Dokument soll relevant sein zur Anfrage sein, aber auch verschieden zu den bislang zurückgegebenen Dokumenten
$$argmax_{d_{i\in D}}=(\lambda \cdot sim(q,d_{i})-(1-\lambda)max_{d_{j}:1<j<i}sim(d_{i},d_{j}))$$
![[Pasted image 20240428122744.png]]