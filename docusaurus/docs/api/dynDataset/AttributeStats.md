---
sidebar_position: 3 # Position after DataSet
title: AttributeStats
---

# AttributeStats Class

(*Path likely `src/lib/dynDataset/attributeStats.js` or `src/lib/dynDataset/dataUtil.js`*)

This helper class is responsible for calculating and storing summary statistics for the data values associated with a specific [`Attribute`](./Attribute.md).

## Overview

`AttributeStats` takes an array of data values (typically from an `Attribute` instance) and computes various descriptive statistics based on the attribute's data type. These statistics are crucial for many downstream operations like setting axis ranges, determining plot types, and displaying summaries.

-   **Functionality:** Calculates statistics relevant to the data type:
    -   **Numerical:** Min, Max, Mean, Median, Standard Deviation, Sum, Count, Missing Count.
    -   **Categorical:** List of unique categories, Count per category, Mode (most frequent category), Count, Missing Count.
    -   **Date:** Min Date, Max Date, Count, Missing Count.
    -   *(Other types might have specific relevant stats)*
-   **Data Source:** Operates on an array of case values provided by an [`Attribute`](./Attribute.md) instance.
-   **Usage:** Instances of `AttributeStats` are likely created and managed *by* the [`Attribute`](./Attribute.md) class itself. An `Attribute` might hold two instances: one for pre-filter stats (`statsPreFilter`) and one for post-filter/sample stats (`stats`).

## Key Properties (Conceptual)

Instances of `AttributeStats` would store the calculated values:

-   `count`: Total number of non-missing values.
-   `missingCount`: Number of missing values.
-   `min`: Minimum value (numerical, date).
-   `max`: Maximum value (numerical, date).
-   `mean`: Mean/average (numerical).
-   `median`: Median value (numerical).
-   `stdDev`: Standard Deviation (numerical).
-   `sum`: Sum of values (numerical).
-   `categories`: Array of unique category names (categorical).
-   `categoryCounts`: Map or object storing counts for each category (categorical).
-   `mode`: Most frequent category (categorical).

## Key Methods (Conceptual)

-   `constructor(values, dataType)`: Initializes and potentially calculates stats immediately based on input values and type.
-   `calculate(values, dataType)`: Performs the statistical calculations.
-   `update(values, dataType)`: Recalculates statistics based on a new set of values.

## Usage

-   Used internally by the **[`Attribute`](./Attribute.md)** class to keep track of summary statistics.
-   The calculated stats are accessed by:
    -   [`PlotElement`](../dynplot/plotElement/PlotElement.md) subclasses for setting axis ranges (`calcPlotSpecificRange`), determining bar heights/positions, etc.
    -   [`AxisView`](../dynplot/AxisView.md) for determining scales and tick marks.
    -   UI components like [`CaseCardComponent`](../components/CaseCardComponent.md) or summary views to display statistical information.

## Dependencies

-   Works closely with the **[`Attribute`](./Attribute.md)** class.
-   Operates on raw data arrays.
-   Likely uses mathematical utility functions (e.g., from `Dyn.mathUtil` or external libraries like `d3-array`) for calculations. 