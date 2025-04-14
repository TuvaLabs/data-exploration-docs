---
sidebar_position: 12.1 # Position after base HistogramElement
title: FreqHistogramElement (Frequency Histogram)
---

# `FreqHistogramElement` Class

(`src/lib/dynplot/plotElement/histogramElement.js` - *Note: Actual file path might differ*)

This class implements a standard **Frequency Histogram**. The height of each bar represents the absolute **count** (frequency) of data points falling within that bar's bin.

## Overview

`FreqHistogramElement` extends the base [`HistogramElement`](./HistogramElement.md) class.

-   **Functionality:** Visualizes the raw frequency distribution of a single continuous numeric variable.
-   **Data Representation:** Uses bars where the width represents a bin (a range of the numeric variable) and the height represents the number of cases whose value falls within that bin.
-   **Binning:** Inherits the binning logic from [`HistogramElement`](./HistogramElement.md).
-   **Axes:** Uses a **numeric** axis for the variable being binned (typically x-axis) and a **frequency** axis (typically y-axis) representing the counts.

## Key Properties & Methods

-   Inherits properties and methods from [`HistogramElement`](./HistogramElement.md) and [`PlotElement`](./PlotElement.md).
-   `constructor()`: Sets flags indicating it's a frequency histogram (e.g., `isFreq = true`).
-   `calcAxisOptions()` / `calcAxis()`: Overrides or extends the base method to specifically configure the y-axis as a frequency (count) axis.
-   `calcPlotSpecificRange()`: Determines the range for the frequency (y) axis based on the maximum bin count obtained from the binning helper.
-   `calcPosition()`: Calculates bar positions based on the bins and sets bar heights based directly on the raw frequency counts for each bin.
-   Defines its own `kDefaultTitle` (e.g., "Histogram of Frequencies") and `kUndoAction`.

## Usage

-   Created by `PlotShaper` when the user selects the standard "Histogram" option from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md) and assigns a numeric [`Attribute`](../../dynDataset/Attribute.md).
-   Used to understand the absolute number of cases within different ranges of a numeric variable.

## Dependencies

-   Extends **[`HistogramElement`](./HistogramElement.md)**.
-   Relies on the binning and counting helper mechanism (like `BarSums`) defined or used by the base class.
-   Depends on **[`Attribute`](../../dynDataset/Attribute.md)** definition (numeric type).
-   Interaction with `PlotShaper` and [`<ToolbarComponent />`](../../components/ToolbarComponent.md) for creation.
-   Interaction with axis components (`AxisView`). 