---
sidebar_position: 8 # Adjust position relative to other BarElement subclasses
title: BarOfSumsElement (Bar Chart of Sums)
---

# `BarOfSumsElement` Class

(`src/lib/dynplot/plotElement/barElement.js`)

This class implements a **Bar Chart of Sums**. Each bar represents the **sum** of the values of a numeric attribute for all cases within a specific category or bin.

## Overview

`BarOfSumsElement` extends the base [`BarElement`](./BarElement.md) class.

-   **Functionality:** Visualizes the total sum of a numeric variable, broken down by categories or bins.
-   **Data Representation:** The length (or height) of each bar corresponds to the sum of a specified numeric attribute for all cases belonging to that bar's category/bin.
-   **Configuration:** Sets flags in its constructor (e.g., potentially `isSum`, although the specific flag might be inferred by the presence of a value attribute) to signal to the base [`BarElement`](./BarElement.md) logic that bar lengths should be based on sums.
-   **Axes:** Requires a categorical axis (or a binned numeric axis) to define the bars, a numeric axis representing the sums, and crucially, a **value attribute** (another numeric attribute from the dataset) whose values will be summed.

## Key Properties & Methods

-   Inherits most properties and methods from [`BarElement`](./BarElement.md).
-   Requires a `valueAttribute` to be defined (likely passed during construction or set based on `Dyn` state).
-   Sets relevant flags (e.g., `negativeCaseValuesOK` might be true if the value attribute can be negative).
-   Overrides `replaces()`.
-   Defines its own `kDefaultTitle` (e.g., "bar chart of sums") and `kUndoAction`.

## Usage

-   Created by `PlotShaper` when the user selects an option like "Bar Chart of Sums" from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md), usually requiring the selection of both a categorical/binning attribute and a numeric attribute to sum.
-   Used to answer questions like "What is the total value (e.g., total sales, total weight) for each category?".

## Helper Class: `BarSums`

-   Relies heavily on the `BarSums` helper class. When configured for sums, `BarSums` iterates through the data (`iCases`), determines the category/bin for each case, fetches the value of the specified `valueAttribute` for that case, and accumulates the sums (`sumArray`) for each bar. It might also track counts (`weightArray`) if needed for related calculations (like means).

## Dependencies

-   Extends **[`BarElement`](./BarElement.md)**.
-   Uses **`BarSums`** helper class for sum calculation.
-   Requires **[`Attribute`](../Attribute.md)** definitions for axis roles and the value attribute.
-   Interaction with `PlotShaper` and [`<ToolbarComponent />`](../../components/ToolbarComponent.md) for creation. 