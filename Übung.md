
```sql
SELECT AVG(semester)
FROM studenten
```

```sql
SELECT v.vorlnr, v.title
FROM pruefen p JOIN vorlesung v ON p.vorlnr = v.vorlnr
GROUP BY v.vorlnr HAVING AVG(p.note) > 3.0;
```

```sql
SELECT v.nachfolger
FROM vorraussetztung v
WHERE (
	SELECT COUNT(*)
	FROM hoeren h1
	WHERE h1.vorln = v.vorgaenger
	)
	<
	(
	SELECT COUNT(*)
	FROM hoeren h2
	WHERE h2.vorln = v.nachfolger
	);
```

```sql
CREATE VIEW Mitarbeiter AS
	SELECT persnr, name
	FROM professoren
	
	UNION
	
	SELECT persnr, name
	FROM assistenten;

```
Einfügen in die VIEW Table?

Nein, da die View auf einer `UNION`-Verknüpfung mehrerer Tabellen basiert und nicht eindeutig bestimmt werden kann, in welche Basistabelle eingefügt werden soll.

```sql
CREATE RECURSIVE Nachfahren(professor, doktorand) AS {
	SELECT professor, doktorand
	FROM betreuer
	
	UNION
	
	SELECT n.professor, b.doktorand
	FROM Nachfahren n JOIN betreuer b ON b.professor = n.doktorand
}
SELECT professor, COUNT(*) AS ANZAHL
FROM Nachfahren
GROUP BY professor;
```

$$
\begin{align*}
\alpha\to\beta\\
\gamma\beta\to\theta\\
\alpha\gamma\to\theta\\
\text{Beweis:}\\
\alpha\to\beta\quad\text{2. Axiom}\quad \alpha\gamma\to\gamma\beta\\
\alpha\gamma\to\gamma\beta,\gamma\beta\to\theta\quad\text{3. Axiom}\quad \alpha\gamma\to\theta\\
\end{align*}
$$
```sql
SELECT matrnr, name
FROM studenten
WHERE semester >= 5
```

```sql
SELECT semester, COUNT(*)
FROM studenten
GROUP BY semester
```

```sql
SELECT v.vorlnr, v.titel
FROM vorlesungen v JOIN professoren p ON v.gelesen_von = p.persnr
WHERE p.rang = "C4"
```

```sql
SELECT vorlnr, COUNT(*)
FROM hoeren
GROUP BY vorlnr
```

```sql
SELECT vorlnr, COUNT(*)
FROM hoeren
GROUP BY vorlnr HAVING COUNT(*) > 5
```

```sql
SELECT s.matrnr, s.name
FROM studenten s JOIN hoeren h ON s.matrnr = h.matrnr JOIN vorlesungen v ON h.vorlnr = v.vorlnr JOIN professoren p ON v.gelesen_von = p.persnr
WHERE p.name = 'Sokrates'
```

```sql
SELECT matrnr, name, semester
FROM studenten
WHERE
	(
	SELECT AVG(semester)
	FROM studenten
	)
	<
	semester
```

```sql
 
```