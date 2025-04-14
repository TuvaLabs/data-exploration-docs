---
sidebar_position: 13.1 # Position after base BoxPlotElement
title: StandardBoxPlotElement
---

# `StandardBoxPlotElement` Class

(`src/lib/dynplot/plotElement/boxPlotElement.js` - *Note: Actual file path might differ*)

This class implements a standard **Box Plot** (Tukey box plot). It displays the five-number summary and potential outliers for a numeric variable, typically compared across categories.

## Overview

`StandardBoxPlotElement` extends the base [`BoxPlotElement`](./BoxPlotElement.md) class.

-   **Functionality:** Visualizes the distribution summary (median, quartiles, range) and identifies outliers.
-   **Data Representation:** Renders:
    -   A **box** from the first quartile (Q1) to the third quartile (Q3).
    -   A **line** inside the box indicating the median (Q2).
    -   **Whiskers** extending from the box. Commonly, the upper whisker goes to Q3 + 1.5*IQR or the maximum value within that limit, and the lower whisker goes to Q1 - 1.5*IQR or the minimum value within that limit.
    -   **Outliers:** Individual points plotted beyond the ends of the whiskers.
-   **Calculation:** Inherits the summary statistics and outlier identification logic from [`BoxPlotElement`](./BoxPlotElement.md).
-   **Axes:** Uses a **numeric** axis for the summarized variable and typically a **categorical** axis for grouping.

## Key Properties & Methods

-   Inherits properties and methods from [`BoxPlotElement`](./BoxPlotElement.md) and [`PlotElement`](./PlotElement.md).
-   `constructor()`: Sets flags appropriate for a standard box plot.
-   `calcPosition()`: Takes the summary statistics calculated by the base class (or its helper) and computes the screen coordinates to draw the box, the median line, the whisker endpoints, and the positions of any outlier points for each category.
-   Defines its own `kDefaultTitle` (e.g., "Box Plot") and `kUndoAction`.

## Usage

-   Created by `PlotShaper` when the user selects the standard "Box Plot" option from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md) and assigns appropriate numeric and categorical [`Attributes`](../../dynDataset/Attribute.md).
-   Used for comparing distributions across groups, identifying skewness, spread (IQR), and outliers.

## Dependencies

-   Extends **[`BoxPlotElement`](./BoxPlotElement.md)**.
-   Relies on the summary statistics calculation from the base class.
-   Depends on **[`Attribute`](../../dynDataset/Attribute.md)** definitions.
-   Interaction with `PlotShaper` and [`<ToolbarComponent />`](../../components/ToolbarComponent.md).
-   Interaction with rendering components and axis components (`AxisView`). 