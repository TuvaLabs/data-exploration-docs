---
sidebar_position: 15.5
title: AnnotationStraightLine
---

# AnnotationStraightLine Type

This represents a straight line segment annotation drawn by the user, managed by the base [`AnnotateElement`](./AnnotateElement.md).

## Overview

When the "Line" or "Straight Line" tool is selected within the annotation mode, users can draw straight line segments between two points on the plot.

-   **Drawing Process:**
    -   Typically involves a click-drag-release gesture.
    -   Clicking sets the starting point of the line segment.
    -   Dragging determines the end point.
    -   Releasing finalizes the line segment.
-   **Data Stored:** The data for a straight line annotation usually includes:
    -   Start point coordinates (`x1`, `y1` in plot data space).
    -   End point coordinates (`x2`, `y2` in plot data space).
    -   Style properties (stroke color, stroke width, stroke dasharray for dashed lines).
    -   A unique ID.
    -   Layering information (z-index).
-   **Rendering:** The [`AnnotateElement`](./AnnotateElement.md) renders this as an SVG `<line>` element (or equivalent Canvas line).

## User Interactions

-   **Creation:** Click-drag-release.
-   **Selection:** Clicking on the line selects it.
-   **Modification:**
    -   Selected lines can often be moved by dragging.
    -   The start or end points are usually draggable to change length/angle.
    -   Style (color, thickness, dash style) can be changed via the [`AnnotationContextMenu`](../../components/common/AnnotationContextMenu.md).
    -   Deleting is possible.

## Usage

-   Allows users to draw straight lines, perhaps to connect points, indicate boundaries, or measure distances visually.

## Dependencies

-   Managed and rendered by **[`AnnotateElement`](./AnnotateElement.md)**.
-   Uses plot coordinates derived from user mouse input relative to the **[`PlotView`](../PlotView.md)** canvas.
-   Style modifications handled via **[`AnnotationContextMenu`](../../components/common/AnnotationContextMenu.md)**. 