
---
# Charts

>[!Important] Definition Chart
Chart a drawing that shows information in a simple way, often using lines and curves to show amounts:
>- There is a chart in the classroom wall showing the relative heights of all the children
>- The sales chart shows a distinct decline in the past few months
>- the TV weather chart

## Components
![[Pasted image 20250223130145.png]]

## Data Types
![[Pasted image 20250223130238.png]]

| Variable Type             | Definition                     | Example                      | Best Chart Types                     |
|---------------------------|--------------------------------|------------------------------|--------------------------------------|
| **Nominal (Categorical)**  | Distinct categories, no order | Countries, Colors, Brands    | Bar Chart, Pie Chart, Treemap       |
| **Ordinal (Categorical)**  | Ordered categories            | Education Level, Ratings     | Bar Chart (Ordered), Heatmap        |
| **Discrete (Numerical)**   | Countable, whole numbers      | Website Clicks, Defects      | Column Chart, Histogram             |
| **Continuous (Numerical)** | Any value within a range      | Temperature, Revenue         | Line Chart, Scatter Plot, Box Plot  |
| **Time-based (Numerical)** | Change over time             | Stock Prices, Sales Trends   | Line Chart, Area Chart              |

### How to choose a chart
![[Pasted image 20250223130809.png]]


---
# Visualization process

## Pipeline
![[Pasted image 20250223163232.png]]

- Data analysis
	- data are prepared for visualization, cleaning data
- Filterung 
	- selection of a subset of the data to be displayed
- Mapping
	- data is mapped to visual primitives
- Rendering
	- geometric data are transformed to image data


---
# Design + Human Visual Processing

>[!Important] Process
>processing of visual information works in two stages:
> - Signal processing in the eye
> - Information processing in the brain
>
>the light reaches the retina, which contains rod (black/white) and cone cells (color) that convert light into electrical signals. These signals are carried into the brain by the optic nerves.
>
>The human eye has a small blind spot as there are no rods and cones in the area where the nerve leaves the eye.

Humans are very bad in reading vertical distance

$\implies$ The _goal_ of information design must be to design displays so that visual queries are _processed_ both _rapidly_ and _correctly_ for every important cognitive task **the display is intended to support**.

## Marks and Channels

>[!Important] Marks
>aka geometric primitives: the type of geometry (point, line, area)
>
![[Pasted image 20250224140225.png]]

>[!Important] Channel
>aka visual variables: the visual properties of the geometric object 
>
>![[Pasted image 20250223130523.png]]


### 3 properties of good chart construction
1. Make the data stand out
2. Facilitate comparison
3. Make the chart information rich

### Information rich design
- each figure needs an informative caption
- add legends and labels
- add context with reference markers
- use the different marks and channels
- use faceting to display multiple aspects of your data
- reduce clutter

### crafting a figure caption
- title explains the figure is about
- Method explains necessary information to understand the figur
- result if not included in the title

---
# High-dimensional-Datasets

**Data transformation**: corresponds to the analysis-centric methods such as dimension reduction, regression, subspace clustering, feature extraction, topological analysis, data sampling, and abstraction.

**Visual mapping**: focuses on organizing the information from the data transformation stage for visual representation. This category includes visual encodings based on axes (e.g., scatterplots and parallel coordinate plots), glyphs, pixels, and hierarchical representations; together with animation and perception.

**View transformation**: corresponds to methods focusing on screen space and rendering, including illustrative rendering for various visual structures, as well as screen space measures for reducing clutter or artifacts and highlighting important features

### SPLOM - Scatter plot Matrix

![[Pasted image 20250224141305.png]]

### PC - Parallel coordinates

![[Pasted image 20250224141408.png]]

### Patterns

![[Pasted image 20250224141432.png]]

## Principle component Analysis

>[!Important] PCA
PCA finds a new coordinate system obtained from the old one by rotation and scaling only. 
>
>The eigendecomposition of the covariance matrix, extracts the rotation and scaling matrices of the linear transformation. Eigenvectors expresses the rotation and root of the eigenvalues the scaling of the matrix


!TODO

---
# Interaction

Hicks law
fits law
???

Design guidelines for interaction
Structure the information: overview first, zoom and filter, details on demand.
Inform about the current status.
Communicate possible interactions.
Use scented widgets to guide interaction.
Animate transitions to help the user adapt the mental model.
Include an ”Undo” and ”Home” button, in case the user makes errors or gets lost.
Provide a history to retrace interactions
## Linking + Brushing

**Linking** means that the interaction with one plot is communicated to others (the linked plots).Possible interactions are e.g. selection, panning, zooming.

**Brushing** is a general term for selection operations done interactively in the chart (e.g.box- or lasso-select).

**Linking+brushing** combines these operations. Making a selection in one plot, causes the other plots to automatically update and highlight the
same selection

---
# Graphs

### Ways to show a tree

![[Pasted image 20250224111505.png]]

### Asthetics Criteria Reingold-Tilford

![[Pasted image 20250224111759.png]]

## Sugiyama Framework

1. remove cycles
2. level nodes (y-coordinate)
3. sort nodes within each level
4. straighten edges (x-coordinate)

## DOT-Algorithmus (Dynamic Ordered Trees)

Der DOT-Algorithmus optimiert die Darstellung von Bäumen, indem er Kantenüberkreuzungen minimiert und die Knoten gleichmäßig verteilt.

## Schrittweise Funktionsweise:
5. **Preorder-Traversierung des Baumes**  
   - Der Baum wird von der Wurzel bis zu den Blättern durchlaufen.  
   - Jeder Knoten speichert seine Unterbäume.  

6. **Initiale Positionierung der Knoten**  
   - Alle Knoten werden zunächst unter ihrem Elternknoten platziert.  
   - Kollisionen werden noch nicht berücksichtigt.  

7. **Berechnung der minimalen Abstände**  
   - Unterbäume erhalten einen Mindestabstand, um Überlappungen zu verhindern.  
   - Die Abstände werden auf Basis der Baumstruktur berechnet.  

8. **Verschiebung der Unterbäume**  
   - Falls Unterbäume zu nahe beieinanderliegen, werden sie verschoben.  
   - Diese Verschiebung wirkt sich auf übergeordnete Knoten aus.  

9. **Optimierung der Baumstruktur**  
   - Knoten werden gleichmäßig verteilt, sodass sich der Baum nicht zu stark neigt.  
   - Symmetrie wird angestrebt.  

10. **Erzeugung der Kanten**  
   - Alle Knoten sind nun optimal platziert.  
   - Kanten zwischen Eltern- und Kindknoten werden gezeichnet, um die Hierarchie sichtbar zu machen.  

## Vorteile:
✅ Weniger Überkreuzungen  
✅ Gleichmäßige Baumstruktur  
✅ Effiziente Hierarchie-Darstellung 

## Force-Directed Layout

Der **Force-Directed Layout-Algorithmus** ist ein **kraftbasierter Algorithmus** zur graphischen Anordnung von Knoten in einem Graphen. Er berechnet **physikalische Kräfte** zwischen Knoten und Kanten, um eine gleichmäßige Anordnung der Knoten zu erreichen.

## Funktionsweise:
1. **Initiale Positionierung**: Zu Beginn werden Knoten zufällig auf dem Raum verteilt.
2. **Berechnung der Kräfte**: 
   - **Abstoßende Kräfte** wirken zwischen allen Knoten (je weiter entfernt, desto stärker die Abstoßung).
   - **Anziehende Kräfte** wirken zwischen benachbarten Knoten, die durch eine Kante verbunden sind.
3. **Bewegung der Knoten**: Knoten werden basierend auf den Kräften verschoben, um eine ausgeglichene Position zu erreichen.
4. **Feinabstimmung durch Kühlung**: Mit jeder Iteration wird die Bewegungsgeschwindigkeit reduziert, um eine stabile Lösung zu finden.
5. **Iteration**: Der Algorithmus wird wiederholt, bis das Layout konvergiert.

## Vorteile:
✅ Gleichmäßige Verteilung der Knoten  
✅ Minimierung von Kantenüberlappungen  
✅ Flexibel für alle Arten von Graphen  

## Nachteile:
❌ Rechenintensiv bei großen Graphen  
❌ Kann lange dauern, bis es konvergiert  
❌ Keine garantierte optimale Lösung

## Furchtman-Reingold-Algorithmus

Der Furchtman-Reingold-Algorithmus ist ein kraftbasierter Algorithmus zur **graphischen Anordnung von Graphen**. Er optimiert die Knotenplatzierung, indem er Kräfte zwischen den Knoten berechnet, um Überlappungen zu vermeiden und die Kanten gleichmäßig zu verteilen.

## Schrittweise Funktionsweise:
6. **Initiale Positionierung der Knoten**  
   - Zu Beginn werden die Knoten zufällig im 2D-Raum verteilt.  
   - Kanten üben Kräfte aus, die Knoten anziehen oder abstoßen.

7. **Berechnung der Kräfte**  
   - **Abstoßende Kräfte**: Knoten stoßen sich mit einer Kraft ab, die **proportional zum Quadrat der Entfernung** ist. Je weiter die Knoten entfernt sind, desto stärker ist die Abstoßung.  
   - **Anziehende Kräfte**: Kanten ziehen die Knoten an, wobei die Anziehungskraft **proportional zur Entfernung** der Knoten ist.

8. **Bewegung der Knoten**  
   - Knoten bewegen sich basierend auf den Kräften. Abstoßungskräfte streuen die Knoten, Anziehungskräfte ziehen sie zusammen.  
   - Die Knotenpositionen werden in jede Iteration angepasst.

9. **Iterationsprozess**  
   - Der Algorithmus wiederholt die Berechnung und Anpassung der Knotenpositionen über mehrere Iterationen.  
   - Ziel ist, den minimalen Energiezustand zu erreichen, wo Abstoßungskräfte und Anziehungskräfte ausgeglichen sind.

10. **Feinabstimmung**  
   - In späteren Iterationen wird die **Bewegungsgeschwindigkeit der Knoten** reduziert (Abkühlung), um die Genauigkeit zu verbessern.

11. **Endergebnis**  
   - Nach den Iterationen haben die Knoten ihre **optimierten Positionen** eingenommen, und das Layout des Graphen ist gleichmäßig ohne Überlappungen.

## Vorteile:
✅ Gleichmäßige Verteilung der Knoten  
✅ Minimierung von Kantenüberkreuzungen  
✅ Optimale Layouts für Hierarchien und Netzwerke  




---
# Scalar Fields
## Isolines
Steps for Marching Squares
- Prepare the tetralateral grif of cells, so each vertex has a value assigned
- Mark every vertex with either above(+) or below(-) the isovalue
- Iterate through cells: Draw isolines through interpolated positions on edges


![[Pasted image 20250224145053.png]]

In the Last Case you calculate a fifth value in the middle of the cell

![[Pasted image 20250224145227.png]]

### Problem with ambiguity cells

if different cells choose different solutions arbitrarily, it can create disconnected or misaligned contour lines, leading to visual artifacts and incorrect topology

### How to fix ambiguity cells

You need more data
- increase Resoulution
- datapoint in the middle of the cell


## Color Mapping

A Colormap defines a mapping between scalar values and color values

![[Pasted image 20250224151632.png]]

### Use colors with distinct names

![[Pasted image 20250224150924.png]]
