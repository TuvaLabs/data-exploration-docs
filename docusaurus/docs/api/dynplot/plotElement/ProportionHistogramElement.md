---
sidebar_position: 12.3 # Position after PercentHistogramElement
title: ProportionHistogramElement (Proportion Histogram)
---

# `ProportionHistogramElement` Class

(`src/lib/dynplot/plotElement/histogramElement.js` - *Note: Actual file path might differ*)

This class implements a **Relative Proportion Histogram**. The height of each bar represents the **proportion** (a value between 0 and 1) of the total number of data points that fall within that bar's bin.

## Overview

`ProportionHistogramElement` extends the base [`HistogramElement`](./HistogramElement.md) class.

-   **Functionality:** Visualizes the relative frequency distribution of a single continuous numeric variable, scaled as proportions.
-   **Data Representation:** Uses bars where the width represents a bin. The height represents (Count in Bin / Total Count).
-   **Binning:** Inherits the binning logic from [`HistogramElement`](./HistogramElement.md).
-   **Axes:** Uses a **numeric** axis for the variable being binned (typically x-axis) and a **proportion** axis (typically y-axis) scaled from 0 to 1.

## Key Properties & Methods

-   Inherits properties and methods from [`HistogramElement`](./HistogramElement.md) and [`PlotElement`](./PlotElement.md).
-   `constructor()`: Sets flags indicating it's a proportion histogram (e.g., `isProportion = true`).
-   `calcAxisOptions()` / `calcAxis()`: Overrides or extends the base method to specifically configure the y-axis as a proportion axis (0-1 scale).
-   `calcPlotSpecificRange()`: Sets the range for the proportion (y) axis to 0-1.
-   `calcPosition()`: Calculates bar positions based on the bins. It retrieves the frequency count for each bin and the total count from the binning helper, calculates the proportion (`binCount / totalCount`), and sets the bar height based on this proportion relative to the 0-1 y-axis scale.
-   Defines its own `kDefaultTitle` (e.g., "Histogram of Proportions") and `kUndoAction`.

## Usage

-   Created by `PlotShaper` when the user selects a "Proportion Histogram" option from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md) and assigns a numeric [`Attribute`](../../dynDataset/Attribute.md).
-   Used similarly to the Percentage Histogram to understand relative proportions, but uses a 0-1 scale instead of 0-100.

## Dependencies

-   Extends **[`HistogramElement`](./HistogramElement.md)**.
-   Relies on the binning and counting helper mechanism to provide both bin counts and the total count.
-   Depends on **[`Attribute`](../../dynDataset/Attribute.md)** definition (numeric type).
-   Interaction with `PlotShaper` and [`<ToolbarComponent />`](../../components/ToolbarComponent.md) for creation.
-   Interaction with axis components (`AxisView`). 