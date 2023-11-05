$n = r-1$ wobei $r$ die Länge des Generatorpolynoms ist. An die den Daten Frame werden $n$ Nullen angehängt. Anschliessend wird der Datenframe durch den Generator geteilt. Die ersten $n$ Bits(von Links) des Rests werden anstatt der angehängten Nullen an den Datenframe angehängt.

Gegeben sei eine Nachricht in binärer Form: `1010100`.

1. Schritt: Füge 3 Nullen (CRC-Bits) zur Nachricht hinzu, da der Generator 4-Bit lang ist (1101). Die erweiterte Nachricht lautet jetzt: `1010100000`.
    
2. Schritt: Teile die erweiterte Nachricht durch das CRC-Polynom (bitweise XOR).

