Gegeben sei eine Nachricht in binärer Form: `1100011`.

1. Schritt: Füge 4 Nullen (CRC-Bits) zur Nachricht hinzu, da der Generator 5-Bit lang ist. Die erweiterte Nachricht lautet jetzt: `11000110000`.
    
2. Schritt: Teile die erweiterte Nachricht durch das CRC-Polynom (bitweise XOR).
$$

11000110000 / 10101

$$