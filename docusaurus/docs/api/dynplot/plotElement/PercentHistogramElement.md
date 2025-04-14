---
sidebar_position: 12.2 # Position after FreqHistogramElement
title: PercentHistogramElement (Percentage Histogram)
---

# `PercentHistogramElement` Class

(`src/lib/dynplot/plotElement/histogramElement.js` - *Note: Actual file path might differ*)

This class implements a **Relative Percentage Histogram**. The height of each bar represents the **percentage** of the total number of data points that fall within that bar's bin.

## Overview

`PercentHistogramElement` extends the base [`HistogramElement`](./HistogramElement.md) class.

-   **Functionality:** Visualizes the relative frequency distribution of a single continuous numeric variable, scaled as percentages.
-   **Data Representation:** Uses bars where the width represents a bin. The height represents (Count in Bin / Total Count) * 100.
-   **Binning:** Inherits the binning logic from [`HistogramElement`](./HistogramElement.md).
-   **Axes:** Uses a **numeric** axis for the variable being binned (typically x-axis) and a **percentage** axis (typically y-axis) scaled from 0 to 100 (or the maximum percentage observed).

## Key Properties & Methods

-   Inherits properties and methods from [`HistogramElement`](./HistogramElement.md) and [`PlotElement`](./PlotElement.md).
-   `constructor()`: Sets flags indicating it's a percentage histogram (e.g., `isPercent = true`).
-   `calcAxisOptions()` / `calcAxis()`: Overrides or extends the base method to specifically configure the y-axis as a percentage axis (0-100 scale).
-   `calcPlotSpecificRange()`: Sets the range for the percentage (y) axis, typically 0-100, possibly adjusting the maximum based on the highest calculated percentage if desired.
-   `calcPosition()`: Calculates bar positions based on the bins. It retrieves the frequency count for each bin and the total count from the binning helper, calculates the percentage (`(binCount / totalCount) * 100`), and sets the bar height based on this percentage relative to the y-axis scale.
-   Defines its own `kDefaultTitle` (e.g., "Histogram of Percentages") and `kUndoAction`.

## Usage

-   Created by `PlotShaper` when the user selects a "Percentage Histogram" option from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md) and assigns a numeric [`Attribute`](../../dynDataset/Attribute.md).
-   Used to understand the relative proportion of cases within different ranges, facilitating comparison especially when total counts differ between datasets.

## Dependencies

-   Extends **[`HistogramElement`](./HistogramElement.md)**.
-   Relies on the binning and counting helper mechanism to provide both bin counts and the total count.
-   Depends on **[`Attribute`](../../dynDataset/Attribute.md)** definition (numeric type).
-   Interaction with `PlotShaper` and [`<ToolbarComponent />`](../../components/ToolbarComponent.md) for creation.
-   Interaction with axis components (`AxisView`). 