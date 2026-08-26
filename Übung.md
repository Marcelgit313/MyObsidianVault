
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