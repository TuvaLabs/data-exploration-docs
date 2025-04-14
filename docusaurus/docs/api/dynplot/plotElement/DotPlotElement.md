---
sidebar_position: 3
title: DotPlotElement / ScatterPlotElement
---

# `DotPlotElement` & `ScatterPlotElement` Classes

(`src/lib/dynplot/plotElement/dotPlotElement.js`)

These classes represent the standard Dot Plot and Scatter Plot visualizations. They extend the [`DotPlotBase`](./DotPlotBase.md) class (via the intermediate `DotOrScatterPlotElement`) and inherit its core logic for icon positioning, stacking, and handling missing values.

## Role and Purpose

-   **`DotPlotElement`:** Typically used when one axis is categorical and the other is numeric. It relies heavily on the stacking logic (`stackInPlace` or `stackInBins`) from [`DotPlotBase`](./DotPlotBase.md) to arrange icons.
-   **`ScatterPlotElement`:** Typically used when both axes are numeric. While it inherits stacking logic, the primary arrangement comes from the direct mapping of X/Y numeric values to pixel coordinates. It uses `orderScatterPlotCases` from the base class mainly for keyboard navigation ordering.

## Functionality

These classes primarily:

-   Inherit `calcPosition` and stacking/ordering logic from [`DotPlotBase`](./DotPlotBase.md).
-   May override `calcAxis` slightly to set specific defaults or constraints suitable for dot/scatter plots (e.g., potentially preferring certain axis types if attributes are ambiguous).
-   Define specific default titles (`kDefaultTitle`) and undo action text (`kUndoAction`).
-   Set their unique `primaryType` (e.g., `kControlsDotPlot`) and `replaceType` (`kControlsShape`) during initialization.

Most of the complex calculation logic resides in the [`DotPlotBase`](./DotPlotBase.md) parent class.

## Usage

Instances of `DotPlotElement` or `ScatterPlotElement` are created and managed by `PlotShaper` when the user selects the corresponding plot type from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md). Their methods are then called by `PlotShaper` during the plot update cycle.

## Dependencies

-   Extend **[`DotPlotBase`](./DotPlotBase.md)** (via `DotOrScatterPlotElement`). 