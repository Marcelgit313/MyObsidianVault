
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

### Asthetics Criteria

![[Pasted image 20250224111759.png]]

