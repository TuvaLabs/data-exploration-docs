---
sidebar_position: 2
title: DotPlotBase (Base for Dot/Scatter/Line)
---

# `DotPlotBase` Class

(`src/lib/dynplot/plotElement/dotPlotElement.js`)

This class extends the base [`PlotElement`](./PlotElement.md) and serves as a foundation for several common plot types that represent individual data cases as distinct shapes (dots, bubbles, points on a line). Specifically, it's the parent for Dot Plots, Scatter Plots, Bubble Charts, and Line Graphs.

## Role and Purpose

`DotPlotBase` encapsulates the shared logic for:

-   Calculating the number of icons needed per case, especially when handling multiple attributes plotted on a single axis or using dual Y-axes.
-   Determining which cases have missing or invalid values for the attributes currently assigned to the axes.
-   Calculating the fundamental X and Y pixel coordinates for each case icon based on axis scales.
-   Implementing stacking algorithms (`stackInPlace`, `stackInBins`) using `StackHelper` to arrange icons when multiple cases fall at the same location (common in dot plots).
-   Implementing ordering logic (`orderScatterPlotCases`) for arranging icons within the plot, primarily for keyboard navigation tabindex and potentially for line connection order.

## Core Concepts

-   **Icon Positioning:** Its primary shaping responsibility is calculating the base `x`, `y` coordinates for each icon via `calcPosition`.
-   **Stacking/Binning:** Manages the spatial arrangement of icons that would otherwise overlap.
-   **Multi-Attribute / Dual-Axis:** Contains logic (`_calcNumIconsPerCaseWithX_Y1_Y2_Axes`) to handle plotting data from multiple attributes simultaneously.

## Key Properties (Inherited/Set)

-   Inherits properties from [`PlotElement`](./PlotElement.md) (`dyn`, `plotShaper`, `primaryType`, `replaceType`, `priority`).
-   `wantStackUp`: `boolean` - Controls stacking direction (vertical vs. horizontal).
-   `numAttributesUsedX`, `numAttributesUsedY`, `numAttributesUsedY1`, `numAttributesUsedY2`: `number` - Calculated counts of attributes being used on each axis, determined during `calcNumIconsPerCase`.

## Key Methods (Implementations/Overrides)

-   `calcNumIconsPerCase()`: Overrides base implementation to handle multi-attribute/dual-axis scenarios.
-   `calcMissingValueCases()`: Implements logic to identify cases unusable for the current X/Y attributes.
-   `calcPosition()`: Core implementation calculating initial X/Y coordinates and invoking stacking/ordering logic.
-   `stackInPlace()` / `stackInBins()`: Implement stacking using `StackHelper`.
-   `orderScatterPlotCases()`: Sorts cases within bins for scatter plots (primarily for tab order).

## Subclassing

Concrete plot types extend `DotPlotBase`:

-   `DotOrScatterPlotElement` (intermediate base)
    -   [`DotPlotElement`](./DotPlotElement.md): Standard dot/scatter plots.
    -   `BubbleChartElement`: Dot plot with variable icon size. (Not documented yet)
-   [`LineGraphElement`](./LineGraphElement.md) (intermediate base)
    -   [`LineGraphSingleElement`](./LineGraphSingleElement.md): Simple line graph.
    -   [`LineAndCategoryElement`](./LineAndCategoryElement.md): Multi-line graph based on categories.

These subclasses inherit the positioning and stacking logic but may override methods like `calcAxis`, `calcIconStyle`, or add `calcAdornments` (for `LineGraphElement`) to implement their specific behaviors.

## Dependencies

-   Extends **[`PlotElement`](./PlotElement.md)**.
-   Relies heavily on **`AxisView`** instances (via `subViewRef` passed into methods) to get axis types and convert data values to pixel coordinates.
-   Uses **`StackHelper`** (internal class) for stacking calculations.
-   Interacts with **[`Dyn.dataSet`](../../dynDataset/DataSet.md)** to read case values. 