---
sidebar_position: 13.2 # Position after StandardBoxPlotElement
title: OutlierBoxPlotElement
---

# `OutlierBoxPlotElement` Class

(`src/lib/dynplot/plotElement/boxPlotElement.js` - *Note: Actual file path might differ*)

This class implements a **Box Plot that explicitly visualizes outliers**. While the standard Tukey Box Plot (often represented by [`StandardBoxPlotElement`](./StandardBoxPlotElement.md)) also shows outliers, this class name might designate the specific implementation focusing on this feature.

## Overview

`OutlierBoxPlotElement` extends the base [`BoxPlotElement`](./BoxPlotElement.md) class.

-   **Functionality:** Renders the box plot summary (box, median, whiskers) and clearly displays individual data points identified as outliers.
-   **Data Representation:** Similar to [`StandardBoxPlotElement`](./StandardBoxPlotElement.md):
    -   Box (Q1 to Q3), Median line (Q2).
    -   Whiskers (typically extending to 1.5*IQR limits).
    -   **Explicit Outliers:** Individual points plotted for all data falling beyond the whisker limits.
-   **Calculation:** Leverages the summary statistics and outlier identification from [`BoxPlotElement`](./BoxPlotElement.md).
-   **Axes:** Uses a **numeric** axis and typically a **categorical** axis.

## Key Properties & Methods

-   Inherits properties and methods from [`BoxPlotElement`](./BoxPlotElement.md) and [`PlotElement`](./PlotElement.md).
-   `constructor()`: Sets flags indicating it should render outliers.
-   `calcPosition()`: Uses the calculated summary statistics and identified outliers to compute the coordinates for drawing the box, median, whiskers, and *each individual outlier point*.
-   Defines its own `kDefaultTitle` (perhaps identical to the standard Box Plot) and `kUndoAction`.

## Usage

-   Likely created by `PlotShaper` when the user selects the standard "Box Plot" option from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md), assuming the standard implementation includes outlier display. It uses numeric and categorical [`Attributes`](../../dynDataset/Attribute.md).
-   Its primary use is identical to the standard box plot: comparing distributions and identifying outliers.

## Dependencies

-   Extends **[`BoxPlotElement`](./BoxPlotElement.md)** (and very similar to **[`StandardBoxPlotElement`](./StandardBoxPlotElement.md)**).
-   Relies on the summary statistics and outlier calculation from the base class.
-   Depends on **[`Attribute`](../../dynDataset/Attribute.md)** definitions.
-   Interaction with `PlotShaper` and [`<ToolbarComponent />`](../../components/ToolbarComponent.md).
-   Interaction with rendering components and axis components (`AxisView`). 