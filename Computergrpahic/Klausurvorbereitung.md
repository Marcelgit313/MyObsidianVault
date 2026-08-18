# Klausurvorbereitung Computer Graphics

Basis: alte Klausuren in `exams/` von Summer 2018 bis Winter 2023 und Folien in `slides/`.

## 1. Was in den Klausuren wirklich drankommt

Die alten Klausuren sind sehr stabil aufgebaut. Fast jedes Jahr kommen dieselben Themenbloecke vor, oft nur in anderer Reihenfolge.

| Thema | Haeufigkeit in alten Klausuren | Typische Punkte | Relevante Folien |
|---|---:|---:|---|
| Lighting Models, Phong/Blinn-Phong, BRDFs | 10/10 | ca. 12-15 | `05 - Surfaces`, `04 - Light Transport` |
| Path/Ray Tracing | 10/10 | ca. 12-16 | `06 - Ray Tracing`, `07 - Path Tracing` |
| Data Structures & Texture Mapping | 10/10 | ca. 12-15 | `08 - Geometric Models`, `11 - Mapping`, `10 - Rasterization Pipelines` |
| Modeling | 10/10 | ca. 10-13 | `08 - Geometric Models`, `11 - Mapping` |
| Shading / barycentric interpolation | 10/10 | ca. 8-11 | `03 - 2D Raster Graphics`, `08 - Geometric Models` |
| Color Spaces | 10/10 | ca. 8-11 | `02 - Light and Color` |
| Transformations | 9/10 | ca. 10-14 | `09 - Transformations` |
| Graphics Pipeline / Rasterization | 8/10 | ca. 14-17 | `10 - Rasterization Pipelines`, `03 - 2D Raster Graphics` |

Pragmatische Prioritaet:

1. Sicher beherrschen: Phong/Blinn-Phong, Path Tracing, Data Structures/Texturing, Transformations, Pipeline.
2. Rechnen koennen: baryzentrische Interpolation, Speicherbedarf von Mesh-Repraesentationen, Transformationsketten, maximale diffuse/specular Positionen.
3. Kurz erklaeren koennen: Farbmodelle, Shading-Arten, Modeling-Techniken, GI-Phaenomene, Variance Reduction.

## 2. Schnell-Check vor dem Lernen

Wenn du die folgenden Fragen ohne Unterlagen beantworten kannst, bist du in der Klausur auf einem guten Niveau:

- Kannst du Phong und Blinn-Phong inklusive Ambient/Diffuse/Specular-Term sauber hinschreiben?
- Kannst du erklaeren, wann diffuse bzw. specular Reflection maximal ist?
- Kannst du aus einem Mesh ein Indexed Face Set und eine Triangle Soup bauen und den Speicherbedarf berechnen?
- Kannst du baryzentrische Koordinaten fuer einen Punkt im Dreieck nutzen, um Farbe/Normalen/UVs zu interpolieren?
- Kannst du Transformationsketten mit lokalen, Welt- und inversen Transformationen aufstellen?
- Kannst du die Rasterisierungspipeline in der richtigen Reihenfolge sortieren und Vertex/Fragment/Raster-Stages zuordnen?
- Kannst du Path Tracing von klassischem Whitted Ray Tracing abgrenzen?
- Kannst du mindestens zwei Importance-Sampling- oder Varianzreduktionsmethoden nennen und kurz begruenden?

## 3. Themenblaetter

### 3.1 Farbmodelle

Typische Klausuraufgaben:

- RGB, CMY/CMYK, HSV/HSL, YUV und CIE kurz erklaeren oder vergleichen.
- Additive vs. subtraktive Farbmischung.
- Warum YUV/YCrCb fuer Kompression sinnvoll ist.
- Farbinterpolation in RGB vs. HSV qualitativ beurteilen.

Wissen:

- RGB ist additiv: Rot, Gruen, Blau als Lichtanteile. Schwarz ist keine Emission, Weiss ist volle Emission aller Kanaele.
- CMY/CMYK ist subtraktiv: Tinten/Farbstoffe absorbieren Licht. `K` wird fuer Schwarz/Key genutzt, weil echtes Schwarz mit CMY unpraktisch ist.
- YUV trennt Helligkeit `Y` von Chrominanz. Das passt zur menschlichen Wahrnehmung, weil Helligkeitsdetails wichtiger wahrgenommen werden als Farbdetails.
- HSV/HSL sind intuitivere Umparametrisierungen fuer Hue/Saturation/Value bzw. Lightness, aber nicht linear-physikalisch.
- CIE-Farbmodelle beschreiben wahrnehmungsorientierte Farbraeume und Gamut-Fragen.

Klausurtipp: Bei Farbraum-Fragen nicht nur Begriffe nennen, sondern immer den Zweck nennen: Display, Druck, Kompression, Wahrnehmung oder Interpolation.

### 3.2 Shading und baryzentrische Interpolation

Typische Klausuraufgaben:

- Farbe an einem Punkt im Dreieck aus Vertex-Farben berechnen.
- Baryzentrische Koordinaten erklaeren und im Dreieck einzeichnen.
- Flat, Gouraud und Phong Shading unterscheiden.
- Unterschied zwischen Phong Lighting Model und Phong Shading erklaeren.

Grundform:

Fuer ein Dreieck mit Eckpunkten `p0, p1, p2` gilt fuer einen Punkt `p`:

```text
p = beta0 * p0 + beta1 * p1 + beta2 * p2
beta0 + beta1 + beta2 = 1
```

Ein Attribut `A`, z. B. Farbe, Normale oder Texturkoordinate, wird entsprechend interpoliert:

```text
A(p) = beta0 * A0 + beta1 * A1 + beta2 * A2
```

Interpretation:

- Alle `beta_i >= 0`: Punkt liegt im Dreieck.
- Ein `beta_i = 0`: Punkt liegt auf gegenueberliegender Kante.
- Negative Koordinate: Punkt liegt ausserhalb.

Shading-Arten:

- Flat Shading: eine Normale/Farbe pro Flaeche, facettierter Look.
- Gouraud Shading: Lighting an Vertices berechnen, resultierende Farben interpolieren.
- Phong Shading: Normalen interpolieren, dann Lighting pro Fragment/Pixel berechnen.

Stolperstelle: Phong Shading ist nicht dasselbe wie das Phong Lighting Model. Phong Shading beschreibt, wo und womit interpoliert wird; Phong Lighting beschreibt die Beleuchtungsformel.

### 3.3 Phong, Blinn-Phong und BRDFs

Typische Klausuraufgaben:

- Drei Terme des Phong Lighting Models nennen und Formeln angeben.
- Diffuse/specular Maxima in Skizzen auf Ebene, Kugel oder Wuerfel finden.
- Phong vs. Blinn-Phong Specular vergleichen.
- BRDF qualitativ als Polarplot zeichnen.
- Lambertian, Phong, Blinn-Phong oder Cook-Torrance einordnen.

Notation:

- `N`: normierte Oberflaechennormale.
- `L`: normierte Richtung vom Punkt zur Lichtquelle.
- `V`: normierte Richtung vom Punkt zur Kamera.
- `R`: perfekte Reflexionsrichtung von `L` an `N`.
- `H = normalize(L + V)`: Halfway Vector bei Blinn-Phong.

Phong Lighting Model:

```text
I = I_ambient + I_diffuse + I_specular

I_ambient  = k_a * I_a
I_diffuse  = k_d * I_l * max(0, dot(N, L))
I_specular = k_s * I_l * max(0, dot(R, V))^n
```

Blinn-Phong ersetzt im Specular-Term `dot(R, V)` durch `dot(N, H)`:

```text
I_specular = k_s * I_l * max(0, dot(N, H))^n
```

Maxima:

- Diffuse ist maximal, wenn `L` parallel zu `N` ist.
- Phong-Specular ist maximal, wenn `V` parallel zu `R` ist.
- Blinn-Phong-Specular ist maximal, wenn `N` parallel zu `H` ist.
- Ambient ist positionsunabhaengig konstant.

BRDF:

- Eine BRDF beschreibt, wie viel eingehende Radiance aus Richtung `omega_i` als ausgehende Radiance in Richtung `omega_o` reflektiert wird.
- Lambertian BRDF ist konstant: ideal diffuse Oberflaeche.
- Specular BRDFs haben eine Lobe um Reflexionsrichtung bzw. Halfway-Konfiguration.
- Physikalisch plausible BRDFs beachten Energieerhaltung und Reziprozitaet.

Klausurtipp: Bei Maxima-Aufgaben erst `N`, `L`, `V`, `R` bzw. `H` geometrisch einzeichnen. Danach ist die Rechnung meist nur noch Vektorvergleich.

### 3.4 Ray Tracing und Path Tracing

Typische Klausuraufgaben:

- Klassisches Ray Tracing vs. Path Tracing vergleichen.
- GI-Phaenomene benennen, die klassisches Ray Tracing nicht korrekt abbildet.
- Path-Notation mit `L`, `D`, `S`, `E` eintragen.
- Varianzreduktion/Importance Sampling nennen und erklaeren.
- Prinzip von Monte-Carlo-Integration erklaeren.
- Ray-Object-Intersection oder Beschleunigungsstrukturen nennen.

Klassisches Whitted Ray Tracing:

- Kamera-Ray durch Pixel.
- Naechsten Schnittpunkt finden.
- Schattenstrahlen zu Punktlichtern.
- Lokales Beleuchtungsmodell am Hitpoint.
- Rekursive Rays fuer perfekte Reflexion/Refraction.
- Gut fuer harte Schatten, Spiegelungen, transparente Objekte.
- Schwach bei indirekter diffuser Beleuchtung, Color Bleeding, Caustics, weichen Flaechenlicht-Schatten.

Path Tracing:

- Approximation der Rendering Equation per Monte Carlo.
- Es werden zufaellige Pfade durch die Szene gesampelt.
- Kann globale Beleuchtung natuerlicher abbilden: indirektes Licht, Color Bleeding, weiche Schatten, Glossy Effects, Depth of Field, Motion Blur.
- Ergebnis ist verrauscht; mehr Samples reduzieren Noise ungefaehr mit `1/sqrt(N)`.

Monte-Carlo-Grundform:

```text
Integral f(x) dx ~= (1/N) * sum_i f(x_i) / p(x_i)
```

Dabei ist `p(x)` die Sampling-Dichte. Gute Wahl von `p` reduziert Varianz.

Typische Varianzreduktion:

- Importance Sampling nach BRDF: mehr Samples in Richtungen mit grossem BRDF-Beitrag.
- Importance Sampling nach Lichtquellen / Next Event Estimation: direkte Lichtbeitraege gezielt abfragen.
- Russian Roulette: Pfade zufaellig terminieren, aber Beitrag durch Ueberlebenswahrscheinlichkeit korrigieren.
- Stratified Sampling: Samples gleichmaessiger ueber Pixel/Hemisphaere verteilen.
- Multiple Importance Sampling: mehrere Sampling-Strategien kombinieren.

Beschleunigung fuer Ray Tracing:

- Bounding Volumes / Bounding Volume Hierarchy.
- Spatial Data Structures wie kd-tree, octree, uniform grid.
- Early termination, back-face culling, hierarchische Tests.

### 3.5 Datenstrukturen, Meshes und Texture Mapping

Typische Klausuraufgaben:

- Aus Skizze ein Indexed Face Set angeben.
- Equivalent Face Set / Triangle Soup angeben.
- Texture Coordinates passend zur Skizze setzen.
- Speicherbedarf mit und ohne Indizes berechnen.
- Vertex-Normalen aus Face-Normalen mitteln.
- Erkennen, wann dieselbe Position mehrere Vertices braucht, z. B. wegen UV-Seams oder unterschiedlicher Normalen.

Repraesentationen:

- Face Set / Triangle Soup: jedes Dreieck speichert seine drei Vertex-Positionen direkt. Einfach, aber redundant.
- Indexed Face Set: Vertex-Array plus Index-Array. Spart Speicher, wenn Vertices geteilt werden.
- Winged Edge / Half Edge: speichert Topologie expliziter, besser fuer Nachbarschaftsoperationen, aber speicherintensiver.

Speicherrechnung:

```text
Position vec3 float  = 3 * 4 bytes = 12 bytes
Normal   vec3 float  = 3 * 4 bytes = 12 bytes
UV       vec2 float  = 2 * 4 bytes = 8 bytes
Index    int         = 4 bytes
```

Beispiel:

```text
Triangle Soup mit F Dreiecken und Position+UV:
F * 3 * (12 + 8) bytes

Indexed Face Set mit V Vertices, F Dreiecken und Position+UV:
V * (12 + 8) + F * 3 * 4 bytes
```

Texture Mapping:

- Texture Coordinates `(u, v)` liegen typischerweise in `[0, 1]^2`.
- Per-Vertex UVs werden ueber das Dreieck interpoliert.
- Eine 3D-Position kann mehrfach im Vertex-Array vorkommen, wenn sie unterschiedliche UVs oder Normalen braucht.
- Texture Mapping veraendert Farbe/Materialparameter.
- Bump/Normal Mapping veraendert die fuer Lighting genutzte Normale, aber nicht die Geometrie.
- Displacement Mapping veraendert tatsaechlich die Geometrie bzw. Oberflaechenposition.
- Environment Mapping nutzt Blick-/Reflexionsrichtung zur Abfrage einer Umgebungstextur.

### 3.6 Modeling

Typische Klausuraufgaben:

- Drei grundlegende Modeling-Techniken nennen.
- Fuer Beispielobjekte passende Technik waehlen.
- Oberflaechendetails fuer geometrisch einfache Objekte modellieren.
- Explizite, implizite und parametrische Modelle vergleichen.

Grundtypen:

- Explizite Modelle: z. B. Polygonmesh, Punkt-/Vertexlisten. Gut fuer Rendering-Pipelines, direkt diskret.
- Implizite Modelle: Oberflaeche als `f(x, y, z) = 0` oder Distance Function. Gut fuer glatte Formen, Booleans, Ray Marching.
- Parametrische Modelle: Flaeche/Kurve als Funktion von Parametern, z. B. `S(u, v)`. Gut fuer kontrollierte glatte Formen.

Weitere wichtige Begriffe:

- Bezier-Kurven/-Flaechen, Splines: glatte parametrische Modellierung.
- Subdivision: aus grobem Kontrollmesh entsteht glattere Geometrie.
- Polygonale Meshes: Standard fuer Echtzeitgrafik.
- Normale eines impliziten Modells: Richtung des Gradienten `grad f`.

Klausurtipp: Bei "welche Technik fuer Objekt X?" immer mit Eigenschaften argumentieren: glatt vs. kantig, Detailtiefe, Topologie, Echtzeitfaehigkeit, einfache Texturierbarkeit.

### 3.7 Transformationen

Typische Klausuraufgaben:

- Transformationsketten zwischen lokalen Koordinatensystemen aufstellen.
- Inverse Transformationen korrekt einsetzen.
- Translation, Rotation, Skalierung als Matrizen oder Kompositionen angeben.
- View/Projection/NDC/Viewport-Konzept erklaeren.
- Normal Matrix nennen.

Koordinatenkette:

```text
object/local -> world -> view/eye -> clip -> NDC -> window/pixel
```

Homogene Koordinaten:

- Position: `w = 1`, Translation wirkt.
- Richtung/Vektor: `w = 0`, Translation wirkt nicht.

Kompositionsregel:

- Bei Spaltenvektoren wirkt die rechte Matrix zuerst.
- Wenn ein Punkt aus Koordinatensystem A nach B gebracht wird, brauchst du die Transformation `T_B_from_A`.
- Fuer Rueckrichtung nutzt du die inverse Transformation.

Beispielmuster:

```text
p_world = T_world_from_object * p_object
p_object = inverse(T_world_from_object) * p_world

p_camera = T_camera_from_world * p_world
```

Normalen:

```text
N' = transpose(inverse(A)) * N
```

Das ist wichtig bei nicht-uniformer Skalierung. Danach Normalen wieder normalisieren.

Klausurtipp: Zeichne fuer Transformationsaufgaben zuerst die Koordinatensysteme und Pfeile. Schreibe dann nur Pfeile als Matrizenprodukt. Nicht direkt mit Zahlen anfangen.

### 3.8 Graphics Pipeline und Rasterization

Typische Klausuraufgaben:

- Pipeline-Stufen sortieren.
- Operationen Vertex-, Rasterization- oder Fragment-Stage zuordnen.
- GLSL-Begriffe erklaeren: attributes, uniforms, varyings, `gl_Position`, `gl_FragColor`.
- Clipping, perspective division, viewport transform, z-buffer, blending einordnen.
- Shader-Code-Luecken fuellen.

Grobe Reihenfolge:

```text
Vertex input
-> vertex shader
-> primitive assembly
-> clipping
-> perspective division
-> viewport transform
-> rasterization / scan conversion
-> fragment shader
-> depth test / blending / framebuffer
```

Begriffe:

- Attribute: per-Vertex Eingaben, z. B. Position, Normale, Farbe, UV.
- Uniforms: konstante Werte fuer Draw Call/Shader, z. B. Matrizen, Lichtposition.
- Varyings: Werte vom Vertex Shader zum Fragment Shader, werden interpoliert.
- `gl_Position`: homogene Clip-Koordinate aus dem Vertex Shader.
- `gl_FragColor`: Fragment-Farbe aus dem Fragment Shader in aelterem GLSL.

Stage-Zuordnung:

- Vertex Shader: Koordinatentransformation, Normalentransformation, Vertex-Lighting.
- Rasterization: Primitive zu Fragmenten, baryzentrische Interpolation, Scan Conversion.
- Fragment Shader: Texturzugriff, Phong/Blinn-Phong per Fragment, Bump Mapping.
- Output/Merger: Depth Test, Stencil, Blending.

Rasterization-Basis:

- Clipping verwirft/kuerzt Geometrie ausserhalb des View Volumes.
- Perspective division: `x, y, z` durch `w`.
- Z-buffer loest Sichtbarkeit pro Pixel.
- Back-face culling verwirft Rueckseiten anhand Orientierung/Normalenrichtung.

### 3.9 Sampling und Filtering

Dieses Thema ist in den alten Klausuren weniger als eigener Block sichtbar, taucht aber in Path Tracing, Texturing und Rasterization auf.

Wissen:

- Sampling wandelt kontinuierliche Signale in diskrete Samples.
- Aliasing entsteht bei zu niedriger Samplingrate oder fehlender Tiefpassfilterung.
- Nyquist-Idee: Samplingrate muss hoch genug fuer die hoechste Frequenz sein.
- Antialiasing reduziert Treppchen/Kantenflimmern durch mehr oder bessere Samples.
- Texture Minification braucht Filtering/Mipmaps, weil ein Pixel viele Texel abdecken kann.
- Nearest Neighbor ist schnell, aber blockig.
- Bilinear Filtering interpoliert zwischen vier Texeln.
- Trilinear Filtering interpoliert zusaetzlich zwischen Mipmap-Leveln.

## 4. Typische Aufgabenmuster und Antwortschema

### Phong-Maximum bestimmen

1. `N`, `L`, `V` am gesuchten Punkt bestimmen.
2. Diffuse: `dot(N, L)` maximieren.
3. Phong-Specular: Reflexionsrichtung `R` so waehlen, dass `R` und `V` parallel sind.
4. Blinn-Specular: Halfway Vector `H = normalize(L + V)` so waehlen, dass `H` und `N` parallel sind.
5. Begruendung in einem Satz: "Maximal, weil der jeweilige Skalarprodukts-Term 1 wird."

### Mesh-Speicher berechnen

1. Zaehle eindeutige Vertices im jeweiligen Datenmodell.
2. Klaere, welche Attribute pro Vertex gespeichert werden: Position, Normale, UV, Farbe.
3. Zaehle Indizes pro Face: Dreieck `3`, Quad `4`.
4. Multipliziere mit Bytegroessen.
5. Bei Texturkoordinaten pruefen: gleiche Position, aber andere UV = separater Vertex.

### Transformationskette aufstellen

1. Schreibe fuer jedes Objekt sein lokales Koordinatensystem.
2. Formuliere `T_world_from_local`.
3. Fuer eine Messung von A aus nach B: erst von A nach Welt, dann Welt nach B.

```text
p_B = inverse(T_world_from_B) * T_world_from_A * p_A
```

4. Inverse vereinfachen: `inverse(T(a) * R(b)) = inverse(R(b)) * inverse(T(a))`.

### Pipeline sortieren

1. Vertex-Operationen zuerst: Attribute lesen, Vertex Shader, `gl_Position`.
2. Dann primitivebezogen: Assembly, Clipping, Perspective Division.
3. Dann Rasterisierung: Fragmente und Interpolation.
4. Dann Fragment Shader: Texturen, Lighting pro Fragment.
5. Dann Tests/Blending/Framebuffer.

### Path-Tracing-Antwort formulieren

Gute Standardantwort:

```text
Path Tracing approximiert die Rendering Equation mit Monte-Carlo-Sampling von Lichtpfaden.
Im Gegensatz zu klassischem Whitted Ray Tracing werden nicht nur perfekte Spiegel-/Brechungs-
pfade und direkte Punktlichtbeitraege verfolgt, sondern zufaellige indirekte Bounces gemaess
BRDF/PDF gesampelt. Dadurch werden globale Beleuchtungseffekte wie Color Bleeding und weiche
indirekte Schatten moeglich, allerdings mit Varianz/Noise.
```

## 5. Mini-Uebungsklausur

Bearbeitungsziel: 90 Minuten, ohne Folien. Danach mit den alten Klausuren vergleichen.

1. Color Spaces: Erklaere RGB, CMYK, HSV und YUV. Warum ist YUV fuer Bild-/Videokompression nuetzlich?
2. Shading: Gegeben seien `beta = (0.2, 0.3, 0.5)` und Vertex-Farben `C0=(1,0,0)`, `C1=(0,1,0)`, `C2=(0,0,1)`. Berechne `C`.
3. Phong: Schreibe Ambient-, Diffuse- und Specular-Term auf. Wann ist jeder Term maximal?
4. Blinn-Phong: Erklaere den Halfway Vector und den Unterschied zum Phong-Specular-Term.
5. Meshes: Ein Mesh hat 8 eindeutige Vertices, 12 Dreiecke, pro Vertex Position+UV, Indizes als 32-bit int. Berechne den Speicherbedarf als Indexed Face Set.
6. Triangle Soup: Berechne fuer dasselbe Mesh den Speicherbedarf als Triangle Soup mit Position+UV pro Dreiecksecke.
7. Transformationen: Objekt A und B haben `T_world_from_A` und `T_world_from_B`. Gib die Transformation von A-Koordinaten nach B-Koordinaten an.
8. Pipeline: Sortiere: fragment shader, clipping, vertex shader, primitive assembly, rasterization, perspective division, framebuffer blending.
9. Path Tracing: Nenne zwei GI-Phaenomene, die Path Tracing besser als klassisches Ray Tracing abbildet.
10. Sampling: Nenne zwei Varianzreduktionsmethoden und erklaere jeweils in einem Satz die Idee.

Loesungsskizze:

1. RGB additiv/displaynah; CMYK subtraktiv/drucknah; HSV hue-saturation-value/intuitiv; YUV trennt Luminanz und Chrominanz, dadurch Chroma-Unterabtastung.
2. `C = 0.2*(1,0,0) + 0.3*(0,1,0) + 0.5*(0,0,1) = (0.2, 0.3, 0.5)`.
3. Siehe Phong-Formeln; ambient konstant, diffuse bei `N || L`, specular bei `R || V`.
4. `H = normalize(L + V)`; Blinn-Phong nutzt `dot(N,H)^n`, Phong nutzt `dot(R,V)^n`.
5. `8*(12+8) + 12*3*4 = 160 + 144 = 304 bytes`.
6. `12*3*(12+8) = 720 bytes`.
7. `p_B = inverse(T_world_from_B) * T_world_from_A * p_A`.
8. vertex shader -> primitive assembly -> clipping -> perspective division -> rasterization -> fragment shader -> framebuffer blending.
9. Color bleeding, indirekte diffuse Beleuchtung, weiche Schatten von Flaechenlichtern, Caustics je nach Samplingstrategie.
10. BRDF Importance Sampling, Light Sampling/Next Event Estimation, Russian Roulette, Stratified Sampling.

## 6. Lernplan fuer 4 Tage

Tag 1:

- `05 - Surfaces`, `04 - Light Transport`: Phong, Blinn-Phong, BRDF, Lambertian.
- Danach alle Lighting-Aufgaben aus Winter 2019, Winter 2020, Winter 2022, Winter 2023 rechnen.

Tag 2:

- `06 - Ray Tracing`, `07 - Path Tracing`: Whitted, Rendering Equation, Monte Carlo, Importance Sampling.
- Danach Path-Tracing-Aufgaben aus Summer 2019, Winter 2020, Winter 2021, Winter 2023.

Tag 3:

- `08 - Geometric Models`, `11 - Mapping`: Mesh-Datenstrukturen, UVs, Speicher, Normalen, Mapping.
- Danach Data-Structures-Aufgaben aus Winter 2020, Winter 2021, Winter 2022, Winter 2023.

Tag 4:

- `09 - Transformations`, `10 - Rasterization Pipelines`, `03 - 2D Raster Graphics`.
- Fokus: Transformationsketten, Pipeline-Sortierung, baryzentrische Interpolation.
- Abschliessend eine komplette alte Klausur unter Zeitbedingungen.

## 7. Last-Minute-Spickzettel

```text
Phong:
I = ka Ia + kd Il max(0,N.L) + ks Il max(0,R.V)^n

Blinn-Phong:
H = normalize(L+V)
Is = ks Il max(0,N.H)^n

Barycentric:
p = beta0 p0 + beta1 p1 + beta2 p2, sum beta = 1
A(p) = beta0 A0 + beta1 A1 + beta2 A2

Transform A -> B:
p_B = inverse(T_world_from_B) * T_world_from_A * p_A

Normal Matrix:
N' = transpose(inverse(A)) * N

Mesh bytes:
vec3 float = 12, vec2 float = 8, int = 4
Indexed = vertices * attributes + faces * corners * index_size
Soup = faces * corners * attributes

Pipeline:
Vertex input -> VS -> Assembly -> Clipping -> Perspective division
-> Viewport -> Rasterization -> FS -> Depth/Blend -> Framebuffer

Path tracing:
Monte Carlo estimator: average f(x_i)/p(x_i)
Noise decreases roughly with 1/sqrt(N)
```

## 8. Welche alten Klausuren zuerst?

1. `Exam - Winter 2023.pdf`: moderne Struktur, sehr repraesentativ.
2. `Exam - Winter 2022.pdf`: fast gleicher Stil, gut zum Festigen.
3. `Exam - Winter 2020.pdf` plus `Exam - Winter 2020 solutions.pdf`: beste Kontrolle mit Loesungen.
4. `Exam - Summer 2019 - English with Solutions.pdf`: zweite Klausur mit Loesungsbezug.
5. Aeltere deutsche Klausuren fuer zusaetzliche Routine bei gleichen Aufgabentypen.

