---
sidebar_position: 1
title: PlotElement (Base Class)
---

# `PlotElement` Base Class

(`src/lib/dynplot/plotElement/plotElement.js`)

This class is the abstract foundation for all visual elements that can be dynamically added to or removed from the main plot area managed by [`PlotView`](../PlotView.md). It defines a common interface and shared properties for both primary plot types (like [`DotPlotElement`](./DotPlotElement.md), [`BarElement`](./BarElement.md)) and overlay adornments (like `MeanElement`, `RefLineElement`, `AnnotateElement`).

## Role and Purpose

-   **Interface Definition:** Establishes the standard methods that specific plot elements must implement (or can override) to interact with the `PlotShaper` and [`PlotView`](../PlotView.md) (e.g., `calcPosition`, `calcAdornments`, `save`, `restore`).
-   **Element Identification:** Provides properties (`primaryType`, `replaceType`) used by `PlotShaper` to identify elements and manage conflicts (e.g., ensuring only one primary plot shape is active at a time).
-   **Calculation Priority:** Defines a `priority` to control the order in which elements are processed during plot updates.
-   **Common Functionality:** Includes base implementations for saving/restoring common state and destroying elements.

## Core Concepts for Subclasses

-   **Shaping Elements vs. Adornment Elements:**
    -   **Shaping Elements** (e.g., [`DotPlotElement`](./DotPlotElement.md), [`BarElement`](./BarElement.md)): Primarily override `calcPosition()` to determine *where* the basic case icons (`PlotView.icons`) should be drawn. They define the fundamental layout of the data points.
    -   **Adornment Elements** (e.g., `MeanElement`, `RefLineElement`, `AnnotateElement`): Primarily override `calcAdornments()` to draw *additional* SVG elements (lines, shapes, text) onto the plot via `PlotAdornments`. They typically don't influence the position of the main case icons.
-   **Conflict Resolution (`replaceType`):** Elements with the same `replaceType` (e.g., `kControlsShape` for [`DotPlotElement`](./DotPlotElement.md) and [`BarElement`](./BarElement.md)) usually cannot coexist. When a new element is added, `PlotShaper` checks its `replaceType` against existing elements and removes conflicts based on the `replaces()` method.
-   **Managed by `PlotShaper`:** Instances are created and held within `PlotShaper`, which orchestrates calls to their methods during the plot update cycle.

## Key Properties

-   `dyn`: Reference to the global `Dyn` object.
-   `plotShaper`: Reference back to the managing `PlotShaper` instance.
-   `primaryType`: `string` (Enum `Dyn.EPlotControl`) - Unique identifier for the specific element type (e.g., `kControlsMean`).
-   `replaceType`: `string` (Enum `Dyn.EPlotControl`) - Identifier for the category this element belongs to (e.g., `kControlsAverage`, `kControlsShape`). Used for conflict resolution.
-   `priority`: `number` (Enum `Dyn.EPlotPriority`) - Determines the order of calculation during plot updates.

## Key Methods (for Subclasses to Implement/Override)

-   `constructor(Dyn)`: Subclass constructor.
-   `initElement(types)`: Called after construction to set up base properties (`primaryType`, `replaceType`, `priority`).
-   `save()`: Serialize element-specific state.
-   `restore(savedData)`: Apply previously saved state.
-   `destroy()`: Clean up element-specific resources (e.g., remove adornments).
-   `replaces(existingElement)`: Logic to determine if this element conflicts with and should replace an existing one.
-   `calcAxis(ioWhatChanged, subViewRef)`: Opportunity to influence axis ranges or types.
-   `calcPosition(ioCasePos, iIndex, iAttrIDs, iDataSet)`: **(Shaping Elements)** Calculate `x`, `y`, `width`, `height` etc. for a case icon.
-   `calcAdornments(iCasesToDraw, iCasePositions, iStats, iXAxisView, iYAxisView)`: **(Adornment Elements)** Calculate and draw additional SVG elements using `this.plotShaper.adornments.add*()` methods.
-   `calcIconStyle(ioIconProps, iIndex, iAttrIDs, iDataSet)`: Influence the appearance (shape, color, size) of case icons.
-   `getUndoAction()`: Return a localized string describing the add action for the undo menu.
-   `handleAxisButtonClick()`, `getContextMenuClickHandler()`: Implement custom interactions.

## Interaction

`PlotElement` subclasses interact primarily with:

-   `PlotShaper`: Which manages them and calls their calculation methods.
-   `PlotAdornments` (via `this.plotShaper.adornments`): To add/remove visual SVG elements.
-   [`Dyn.dataSet`](../../dynDataset/DataSet.md): To read data needed for calculations.
-   `AxisView` instances (via `PlotShaper` or [`PlotView`](../PlotView.md)): To get axis scales and ranges. 