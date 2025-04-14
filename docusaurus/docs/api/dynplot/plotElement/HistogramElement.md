---
sidebar_position: 12 # Adjust position relative to other PlotElement types
title: HistogramElement (Base Class)
---

# `HistogramElement` (Base Class)

(`src/lib/dynplot/plotElement/histogramElement.js` - *Note: Actual file path might differ*)

This class serves as the **base** for various Histogram implementations. Histograms provide a graphical representation of the distribution of a single numeric dataset by grouping numbers into ranges (bins).

## Overview

`HistogramElement` likely extends the base [`PlotElement`](./PlotElement.md).

-   **Functionality:** Provides the core logic for handling a single continuous numeric [`Attribute`](../../dynDataset/Attribute.md) and dividing its range into bins.
-   **Binning:** A key shared aspect is the automatic or user-configurable calculation of bin widths and boundaries based on the range and distribution of the data for the chosen numeric attribute.
-   **Axes:** Manages the primary **numeric** axis (typically the x-axis) representing the variable being analyzed. The configuration of the secondary axis (y-axis) depends on the specific histogram type (frequency, percentage, or proportion).

## Key Properties & Methods (Inherited by Subclasses)

-   Inherits core properties and methods from [`PlotElement`](./PlotElement.md).
-   `constructor()`: Basic setup.
-   `calcAxisOptions()` / `calcAxis()`: Manages the numeric data axis. May include logic to suggest or calculate appropriate bin widths (`setBinningSpec`). Subclasses override parts to handle the y-axis type.
-   Methods related to handling bin width adjustments (e.g., `adjustBinWidth`).
-   `calcBinCounts()` (Conceptual): A core responsibility (likely via a helper class similar to `BarSums`) is to iterate through the relevant cases and count how many fall into each calculated bin.
-   `calcPosition()`: Subclasses implement this to calculate bar positions (based on bins) and heights (based on frequency, percentage, or proportion).

## Subclasses

Specific histogram types are implemented as subclasses:

-   **[`FreqHistogramElement`](./FreqHistogramElement.md):** Displays raw frequency counts on the y-axis.
-   **[`PercentHistogramElement`](./PercentHistogramElement.md):** Displays relative percentages (0-100%) on the y-axis.
-   **[`ProportionHistogramElement`](./ProportionHistogramElement.md):** Displays relative proportions (0-1) on the y-axis.

## Usage

-   Specific histogram types (like [`FreqHistogramElement`](./FreqHistogramElement.md)) are typically created by `PlotShaper` when the user selects a histogram option from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md) and assigns a numeric attribute.

## Dependencies

-   Extends **[`PlotElement`](./PlotElement.md)**.
-   Requires a helper mechanism (similar to `BarSums`) for binning and counting cases per bin.
-   Depends on **[`Attribute`](../../dynDataset/Attribute.md)** definitions (specifically numeric type).
-   Interaction with `PlotShaper` and [`<ToolbarComponent />`](../../components/ToolbarComponent.md) for creation of specific subclass instances.
-   Interaction with axis components (`AxisView`). 