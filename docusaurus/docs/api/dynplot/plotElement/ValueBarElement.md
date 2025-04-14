---
sidebar_position: 10 # Adjust position as needed relative to other BarElement subclasses
title: ValueBarElement (Bar Chart of Values)
---

# `ValueBarElement` Class

(`src/lib/dynplot/plotElement/barElement.js`)

This class implements a specific type of Bar Chart where each bar represents the raw **value** of a single case or potentially an aggregated value if combined with categorical axes in a specific way. It appears less commonly used than frequency, sum, or mean-based bar charts.

## Overview

`ValueBarElement` extends the base [`BarElement`](./BarElement.md) class.

-   **Functionality:** It primarily uses the [`BarElement`](./BarElement.md) logic.
-   **Data Representation:** The length of each bar corresponds directly to a numeric value from the dataset, rather than an aggregation like count or sum.
-   **Configuration:** It sets flags in its constructor to reflect this behavior.
-   **Axis Requirements:** Likely requires a numeric axis to represent the values and often another axis (potentially categorical or case-based) to define the individual bars.

## Key Methods

-   Relies mostly on inherited methods from [`BarElement`](./BarElement.md).
-   `calcPosition()` would calculate bar lengths based on direct case values rather than aggregates from `BarSums`.
-   Defines its own `kDefaultTitle` and `kUndoAction`.
-   Overrides `replaces()`.

## Usage

Created by `PlotShaper` when selected from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md). Its specific use case might be for visualizing individual data points as bars, perhaps similar to a histogram but without automatic binning, or in specific configurations with categorical axes.

## Dependencies

-   Extends **[`BarElement`](./BarElement.md)**. 