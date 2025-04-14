---
sidebar_position: 15.4
title: AnnotationArrow
---

# AnnotationArrow Type

This represents an arrow annotation drawn by the user, managed by the base [`AnnotateElement`](./AnnotateElement.md).

## Overview

When the "Arrow" tool is selected within the annotation mode, users can draw arrows to point to specific features on the plot.

-   **Drawing Process:**
    -   Typically involves a click-drag-release gesture.
    -   Clicking sets the starting point (tail) of the arrow.
    -   Dragging determines the length and direction.
    -   Releasing sets the end point (head) of the arrow.
-   **Data Stored:** The data for an arrow annotation usually includes:
    -   Start point coordinates (`x1`, `y1` in plot data space).
    -   End point coordinates (`x2`, `y2` in plot data space).
    -   Style properties (stroke color, stroke width, arrowhead type/size).
    -   A unique ID.
    -   Layering information (z-index).
-   **Rendering:** The [`AnnotateElement`](./AnnotateElement.md) renders this typically as an SVG `<line>` element plus a `<polygon>` or `<marker>` element for the arrowhead (or equivalent Canvas lines/shapes).

## User Interactions

-   **Creation:** Click-drag-release.
-   **Selection:** Clicking on the arrow line selects it.
-   **Modification:**
    -   Selected arrows can often be moved by dragging the line.
    -   The start or end points might be draggable to change length/direction.
    -   Style (color, thickness, arrowhead) can be changed via the [`AnnotationContextMenu`](../../components/common/AnnotationContextMenu.md).
    -   Deleting is possible.

## Usage

-   Allows users to draw attention to specific points, regions, or trends on the plot.

## Dependencies

-   Managed and rendered by **[`AnnotateElement`](./AnnotateElement.md)**.
-   Uses plot coordinates derived from user mouse input relative to the **[`PlotView`](../PlotView.md)** canvas.
-   Style modifications handled via **[`AnnotationContextMenu`](../../components/common/AnnotationContextMenu.md)**. 