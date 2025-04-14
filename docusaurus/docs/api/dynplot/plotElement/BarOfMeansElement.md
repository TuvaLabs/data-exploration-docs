---
sidebar_position: 9 # Adjust position relative to other BarElement subclasses
title: BarOfMeansElement (Bar Chart of Means)
---

# `BarOfMeansElement` Class

(`src/lib/dynplot/plotElement/barElement.js`)

This class implements a **Bar Chart of Means**. Each bar represents the **average** (mean) value of a numeric attribute for all cases within a specific category or bin.

## Overview

`BarOfMeansElement` extends the base [`BarElement`](./BarElement.md) class.

-   **Functionality:** Visualizes the average value of a numeric variable, broken down by categories or bins.
-   **Data Representation:** The length (or height) of each bar corresponds to the mean of a specified numeric attribute for all cases belonging to that bar's category/bin. The mean is calculated as (Sum of values) / (Count of cases).
-   **Configuration:** Sets flags in its constructor (e.g., potentially `isMean`, although this might be inferred) to signal to the base [`BarElement`](./BarElement.md) logic that bar lengths should be based on means.
-   **Axes:** Requires a categorical axis (or a binned numeric axis) to define the bars, a numeric axis representing the means, and a **value attribute** (another numeric attribute from the dataset) whose values will be averaged.

## Key Properties & Methods

-   Inherits most properties and methods from [`BarElement`](./BarElement.md).
-   Requires a `valueAttribute` to be defined.
-   Sets relevant flags (e.g., `negativeCaseValuesOK` might be true).
-   Overrides `replaces()`.
-   Defines its own `kDefaultTitle` (e.g., "bar chart of means") and `kUndoAction`.
-   The core logic for calculating the mean happens within the `BarSums` helper, which computes both sums and counts.

## Usage

-   Created by `PlotShaper` when the user selects an option like "Bar Chart of Means" from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md), requiring selection of a categorical/binning attribute and a numeric attribute to average.
-   Used to answer questions like "What is the average value (e.g., average score, average height) for each category?".

## Helper Class: `BarSums`

-   Relies heavily on the `BarSums` helper class. `BarSums` calculates both the **sum** (`sumArray`) of the `valueAttribute` and the **count** (`weightArray`) of cases for each category/bin. The `BarOfMeansElement` (or the base `BarElement` logic when configured for means) then divides the sum by the count for each bar to determine its length.

## Dependencies

-   Extends **[`BarElement`](./BarElement.md)**.
-   Uses **`BarSums`** helper class for sum and count calculation.
-   Requires **[`Attribute`](../Attribute.md)** definitions for axis roles and the value attribute.
-   Interaction with `PlotShaper` and [`<ToolbarComponent />`](../../components/ToolbarComponent.md) for creation. 