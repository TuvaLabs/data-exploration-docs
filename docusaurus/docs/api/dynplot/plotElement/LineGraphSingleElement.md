---
sidebar_position: 4.1 # Adjust as needed
title: LineGraphSingleElement (Simple Line Chart)
---

# `LineGraphSingleElement` Class

(`src/lib/dynplot/plotElement/dotPlotElement.js`)

This class implements a standard, single-line Line Chart.

## Overview

`LineGraphSingleElement` extends the [`LineGraphElement`](./LineGraphElement.md) base class.

-   **Functionality:** It uses the inherited logic from [`LineGraphElement`](./LineGraphElement.md) to position points and draw a connecting line.
-   **Use Case:** Suitable when plotting a single dependent variable against an independent variable (e.g., time series data, Y vs. X with no categorical breakdown).
-   **Configuration:** Sets its specific `primaryType` (`kControlsLineGraphSingle`) and `replaceType` (`kControlsShape`) during initialization.
-   Defines its own `kDefaultTitle` and `kUndoAction`.

## Usage

An instance is created by `PlotShaper` when the user selects the basic "Line Chart" option from the [`<ToolbarComponent />`](../../components/ToolbarComponent.md). It expects appropriate numeric attributes on the X and Y axes.

## Dependencies

-   Extends **[`LineGraphElement`](./LineGraphElement.md)**. 