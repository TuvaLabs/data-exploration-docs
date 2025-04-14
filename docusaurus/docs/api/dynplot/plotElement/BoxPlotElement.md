---
sidebar_position: 13 # Adjust position relative to other PlotElement types
title: BoxPlotElement (Base Class)
---

# `BoxPlotElement` (Base Class)

(`src/lib/dynplot/plotElement/boxPlotElement.js` - *Note: Actual file path might differ*)

This class serves as the **base** for various Box Plot implementations. Box Plots (or box-and-whisker plots) provide a graphical summary of the distribution of a numeric variable, often broken down by categories.

## Overview

`BoxPlotElement` likely extends the base [`PlotElement`](./PlotElement.md).

-   **Functionality:** Provides the core logic for calculating summary statistics (minimum, first quartile (Q1), median (Q2), third quartile (Q3), maximum, Interquartile Range (IQR)) for a numeric [`Attribute`](../../dynDataset/Attribute.md), potentially for different groups defined by a categorical attribute.
-   **Outlier Detection:** Includes the logic to identify potential outliers, typically defined as points falling below Q1 - 1.5*IQR or above Q3 + 1.5*IQR.
-   **Axes:** Manages the primary **numeric** axis representing the variable being summarized and usually a **categorical** axis to define different groups for comparison.
-   **Calculation:** Relies on internal logic or a helper class to perform the statistical calculations for each group.

## Key Properties & Methods (Inherited by Subclasses)

-   Inherits core properties and methods from [`PlotElement`](./PlotElement.md).
-   `constructor()`: Basic setup.
-   `calcAxisOptions()` / `calcAxis()`: Manages the numeric data axis and the categorical axis.
-   `calcPlotSpecificRange()`: Determines the range for the numeric axis based on min/max values, including potential outliers.
-   `calculateSummaryStats()` (Conceptual): A core responsibility (likely via a helper) to compute the five-number summary and identify outliers for each category.
-   `calcPosition()`: Subclasses implement this to use the calculated statistics to determine the coordinates for drawing the specific elements (box, whiskers, median line, outliers, dots).
-   May include methods for handling hover interactions.

## Subclasses

Specific box plot variations are implemented as subclasses:

-   **[`StandardBoxPlotElement`](./StandardBoxPlotElement.md):** Renders the classic box, median, and whiskers (potentially showing outliers by default).
-   **[`OutlierBoxPlotElement`](./OutlierBoxPlotElement.md):** Explicitly renders outliers as individual points beyond the whiskers (may be functionally similar to the standard implementation).
-   **[`BoxAndDotPlotElement`](./BoxAndDotPlotElement.md):** Combines the box plot summary with overlaid individual data points (dots).

## Usage

-   Specific box plot types (like [`StandardBoxPlotElement`](./StandardBoxPlotElement.md)) are typically created by `PlotShaper` when the user selects a box plot option from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md) and assigns appropriate numeric and categorical attributes.

## Dependencies

-   Extends **[`PlotElement`](./PlotElement.md)**.
-   Requires a helper class or internal logic for calculating summary statistics and outliers.
-   Depends on **[`Attribute`](../../dynDataset/Attribute.md)** definitions (numeric and often categorical).
-   Interaction with `PlotShaper` and [`<ToolbarComponent />`](../../components/ToolbarComponent.md) for creation of specific subclass instances.
-   Interaction with rendering components and axis components (`AxisView`). 