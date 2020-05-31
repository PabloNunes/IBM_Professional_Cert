# Data Visualization with Python - Summary

## Autor: Pablo Nunes

----

## Modules

1. In the first module, we will discuss data visualization and best practices when creating one. 
   - Learn about MatPlotLib
   - Learning how to interpret a dataset in hands-on sessions
   - A crash course in Pandas
2. In the second module, we will learn to use basic data visualizations.
   - Make area plots, histograms, and bar charts using MatPlotLib
   - Make more advanced visualizations with MatPlotLib like pie charts, box plots, scatter plots, and bubble plots.
3. In the last module, learn to use more specialized charts.
   - Learn to use waffle charts, word clouds and choropleth maps.
   - Explore Seaborn and Folium.

## Introduction to Data Visualization

- Why build visuals?
  - For exploratory data analysis
  - Communicate data clearly
  - Share unbiased representation of data
  - Support recommendations to different stakeholders
- Best practices
  1. Less is more effective
  2. Less is more attractive
  3. Less is more impactive

## Introduction to MatPlotLib

- The MatPlotLib archtecture
  1. Backend Layer (FigureCanvas, Renderer, Event)
  2. Artist Layer (Artist)
  3. Scripting Layer (pyplot)
- Basic Plottiing with MatPlotLib
  - MatPlotLib is very well supported
  - We going to use Jupyter Notebook
  - ```%matplotlib notebook``` can be used to plots update in real time
  - We can use Pandas with MatPlotLib, using ```.plot(kind="line")``` we have a plot with our dataframe and ```.plot(kind="hist")``` to have a histogram.
- Line Plot
  - A line plot is a type of plot which displays information as a series of datapoints connected by straight line segments.
  - The best case for a line plot, is when the data is a continous dataset
