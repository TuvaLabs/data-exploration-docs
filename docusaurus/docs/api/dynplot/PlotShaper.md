---
sidebar_position: 5 # Position after rightMarginView
title: PlotShaper
---

# PlotShaper Class

(*Path likely `src/lib/dynplot/plotShaper.js` or similar*)

This class acts as a factory and manager for the active **plot type**. It is responsible for creating the appropriate [`PlotElement`](./plotElement/PlotElement.md) subclass instance based on user selections (e.g., from the [`ToolbarComponent`](../components/ToolbarComponent.md)) and the attributes assigned to the plot axes and legend.

## Overview

`PlotShaper` sits between the UI controls (like the Toolbar) and the actual plot rendering logic (`PlotView` and `PlotElement`). It determines *what* kind of plot should be displayed.

-   **Functionality:**
    -   **Plot Type Selection:** Listens for user actions selecting a plot type (e.g., Scatter Plot, Bar Chart, Histogram).
    -   **Attribute Analysis:** Examines the data types and roles of attributes assigned to the X-axis, Y-axis, and Legend.
    -   **Instantiation:** Based on the selected plot type and attribute configuration, instantiates the correct `PlotElement` subclass (e.g., [`ScatterPlotElement`](./plotElement/ScatterPlotElement.md), [`FreqBarElement`](./plotElement/FreqBarElement.md), [`LineAndCategoryElement`](./plotElement/LineAndCategoryElement.md)).
    -   **Management:** Holds the reference to the currently active `PlotElement` instance.
    -   **Communication:** Signals the [`PlotView`](./PlotView.md) to update its rendering when the active `PlotElement` changes.
-   **Decision Logic:** Contains the logic mapping combinations of plot type selections and attribute types/roles to specific `PlotElement` implementations.

## Key Properties (Conceptual)

-   `activePlotElement`: The currently instantiated `PlotElement` subclass.
-   `plotTypeRegistry`: A mapping or registry of available plot types and their corresponding `PlotElement` classes.

## Key Methods (Conceptual)

-   `setPlotType(plotTypeName, axisAttributes, legendAttribute)`: The main method called when the user changes the plot configuration. It analyzes the inputs and creates/updates `activePlotElement`.
-   `getActivePlotElement()`: Returns the current `PlotElement` instance.
-   `_determinePlotElement(plotTypeName, attributes)`: Internal logic to select the correct `PlotElement` class.
-   `_createPlotElement(PlotElementClass, config)`: Instantiates the chosen class with necessary configuration.

## Usage

-   Likely managed by the main application state (`Dyn`) or the [`PlotView`](./PlotView.md).
-   Receives commands from the [`ToolbarComponent`](../components/ToolbarComponent.md) or other UI elements responsible for plot configuration.
-   Provides the active `PlotElement` instance to [`PlotView`](./PlotView.md) for rendering calculations and drawing.

## Dependencies

-   Interacts with application state (`Dyn`) to get selected attributes and plot type commands.
-   Instantiates various **[`PlotElement`](./plotElement/PlotElement.md)** subclasses.
-   Provides the active plot element to **[`PlotView`](./PlotView.md)**.
-   Receives input triggered by **[`ToolbarComponent`](../components/ToolbarComponent.md)**. 