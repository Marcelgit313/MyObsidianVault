
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
	WHERE Nachfahren n JOIN betreuer b ON b.professor = n.doktorand
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