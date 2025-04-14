---
sidebar_position: 15.2
title: AnnotationRectangle
---

# AnnotationRectangle Type

This represents a rectangle annotation drawn by the user, managed by the base [`AnnotateElement`](./AnnotateElement.md).

## Overview

When the "Rectangle" tool is selected within the annotation mode, users can draw rectangular shapes on the plot canvas.

-   **Drawing Process:**
    -   User clicks and holds the mouse button down at one corner of the desired rectangle.
    -   As the user drags the mouse, a rectangle shape is dynamically drawn from the starting point to the current cursor position.
    -   Releasing the mouse button finalizes the rectangle's position and size.
-   **Data Stored:** The data for a rectangle annotation typically includes:
    -   Position (e.g., `x`, `y` coordinates of the top-left corner in plot data space).
    -   Dimensions (`width`, `height` in plot data space).
    -   Style properties (fill color, stroke color, stroke width, opacity).
    -   A unique ID.
    -   Layering information (z-index).
-   **Rendering:** The [`AnnotateElement`](./AnnotateElement.md) renders this as an SVG `<rect>` element (or equivalent Canvas rectangle) based on the stored position, dimensions, and style.

## User Interactions

-   **Creation:** Click-drag-release.
-   **Selection:** Clicking inside the rectangle selects it.
-   **Modification:**
    -   Selected rectangles can be moved by dragging the main body.
    -   Selected rectangles can often be resized by dragging corner or edge handles.
    -   Style (fill, stroke) can be changed via the [`AnnotationContextMenu`](../../components/common/AnnotationContextMenu.md).
    -   Deleting is possible.

## Usage

-   Allows users to highlight rectangular regions of interest on the plot.
-   Useful for framing groups of points or specific areas of the visualization.

## Dependencies

-   Managed and rendered by **[`AnnotateElement`](./AnnotateElement.md)**.
-   Uses plot coordinates derived from user mouse input relative to the **[`PlotView`](../PlotView.md)** canvas.
-   Style modifications handled via **[`AnnotationContextMenu`](../../components/common/AnnotationContextMenu.md)**. 