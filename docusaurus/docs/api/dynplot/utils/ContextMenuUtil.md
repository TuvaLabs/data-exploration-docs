---
sidebar_position: 3 # Position after axisUtil
title: ContextMenuUtil
---

# ContextMenuUtil

(*Path likely `src/lib/dynplot/utils/contextMenuUtil.js` or similar*)

This utility module is responsible for determining **which specific context menu options** should be displayed based on the element or plot area that was right-clicked (or triggered the context menu event).

## Overview

The application can display different context menus depending on whether the user clicks on the main plot background, a specific data point, an axis, an annotation, a histogram bar, etc. `ContextMenuUtil` encapsulates the logic to decide the appropriate menu content for the given context.

-   **Functionality:**
    -   Takes context information as input (e.g., the clicked element type, associated data, current plot state).
    -   Contains logic (e.g., switch statements, if/else chains) to analyze the context.
    -   Returns a list of menu item definitions or identifies which specific context menu component (e.g., `HistogramContextMenu`, `AnnotationContextMenu`) should be loaded.
-   **Context Analysis:** Needs to differentiate between various clickable targets within the plot area, including:
    -   Plot background.
    -   Individual case icons/elements.
    -   Axes (`AxisView`).
    -   Annotations (`AnnotateElement`).
    -   Histogram bars.
    -   Standard deviation bands (`PlotMeasure`).
    -   Other plot adornments.

## Key Functions (Conceptual Examples)

-   `getContextMenuItems(clickTarget, plotState)`: Analyzes the `clickTarget` (e.g., element type, associated data) and `plotState` (active plot element, attributes) and returns an array of menu item definitions or the name/reference of the specific context menu component to use.

## Usage

-   Used by the component responsible for rendering the context menu overlay (likely [`ContextMenuWrapper`](../../components/common/ContextMenuWrapper.md) or possibly [`PlotView`](../PlotView.md) directly).
-   When a context menu is triggered, this utility is called to determine the relevant menu items before the menu is displayed.

## Dependencies

-   Needs knowledge of the different **element types** used within [`PlotView`](../PlotView.md) and [`PlotElement`](../plotElement/PlotElement.md) subclasses.
-   May need access to the current **plot state** (active plot element, visible measures) to make decisions.
-   Provides menu definitions or component references to the **[`ContextMenuWrapper`](../../components/common/ContextMenuWrapper.md)**. 