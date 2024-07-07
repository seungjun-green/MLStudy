# Data Visualization Guide

## Categorical Data Visualization
(For counting occurrences in categorical data)

- `sns.countplot()`: Draws a bar chart showing the count of observations in each categorical bin
- `sns.catplot()`: Flexible function for plotting categorical data across multiple axes

## Trend Visualization
(For categorical columns with values recorded over time)

- `sns.lineplot()`: Displays trends over time
- `sns.barplot()`: Shows comparisons between categories
- `sns.heatmap()`: Visualizes data intensity across multiple categories and time periods

## Scatter Plots
(For categorical columns with individual records of discrete numerical features)

- `sns.scatterplot()`: Displays relationship between two numerical variables
- `sns.regplot()`: Adds a regression trend line to scatterplot
- `sns.lmplot()`: Used with 'hue' parameter, adds multiple regression lines to scatterplot
- `sns.swarmplot()`: Shows the distribution of data points without overlap

## Distribution Plots
(For categorical columns with individual records of continuous numerical features)

- `sns.histplot()`: 
  - Displays distribution in bar graph form
  - Can be used with 'hue' parameter for group comparison
- `sns.kdeplot()`: Shows distribution using Kernel Density Estimation
- `sns.jointplot()`: Displays distribution of two variables using KDE
- `sns.boxplot()`: Shows distribution with quartiles and outliers
- `sns.violinplot()`: Combines box plot with KDE on sides

## Pair-wise Relationship Plots
(For visualizing relationships between multiple variables)

- `sns.pairplot()`: Creates a grid of scatter plots for all pair-wise relationships
- `sns.heatmap()`: Can be used with correlation matrix to show relationships
- `sns.clustermap()`: Hierarchically clustered heatmap

## Faceted Plots
(For creating multi-plot grids)

- `sns.FacetGrid()`: Creates a grid of plots based on up to three variables
- `sns.relplot()`: High-level interface for drawing relational plots onto a FacetGrid
