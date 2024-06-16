
## Aufgabe 1
### a)
View $v1$:

Es können alle drei Tupel eingefügt werden, aber keiner von den Tupeln würde angezeigt werden, da sie alle die $WHERE$-Bedingung nicht erfüllen.

View $v2$:

In der View $v2$ können zwei von drei Tupeln eingefügt werden, da wir mit $CHECK OPTION$ auf die $WHERE$-Bedingung achten müssen und wir dann nur Tupel mit dem $Semester \geq 4$ hinzufügen können. Also können wir ii) nicht hinzufügen.

View $v3$:

Das gleiche wie bei View $v2$ das wir mit $CASCADED\ CHECK\ OPOTION$ auch auf die Bedingen der View davor schauen und alle Tupel haben eine $Matrnr \geq 400000$ also wird wieder nur ii) nicht eingefügt 

View $v4$:

Es können alle Tupel hinzugefügt werden wie bei View $v1$

### c)

```sql
CREATE FUNCTION  neues_semester() RETURNS VOID AS $$
BEGIN
	UPDATE studenten
	SET semester = semester + 1
	WHERE
```
