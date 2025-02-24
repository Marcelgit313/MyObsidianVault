
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

## 3 properties of good chart construction
1. Make the data stand out
2. Facilitate comparison
3. Make the chart information rich

## Information rich design
- each figure needs an informative caption
- add legends and labels
- add context with reference markers
- use the different marks and channels
- use faceting to display multiple aspects of your data
- reduce clutter

## crafting a figure caption
- title explains the figure is about
- Method explains necessary information to understand the figur
- result if not included in the title


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




