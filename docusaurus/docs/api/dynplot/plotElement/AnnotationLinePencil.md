---
sidebar_position: 15.1
title: AnnotationLinePencil
---

# AnnotationLinePencil Type

This represents a freehand line annotation drawn by the user, managed by the base [`AnnotateElement`](./AnnotateElement.md).

## Overview

When the "Pencil" or "Freehand Line" tool is selected within the annotation mode, users can draw directly on the plot canvas.

-   **Drawing Process:**
    -   User clicks and holds the mouse button down on the plot area.
    -   As the user drags the mouse, a path is created following the cursor's movement.
    -   Releasing the mouse button completes the drawing of the line.
-   **Data Stored:** The data for a pencil line annotation typically includes:
    -   An array of points (`{x, y}` coordinates in plot data space) defining the path.
    -   Style properties (stroke color, stroke width).
    -   A unique ID.
    -   Layering information (z-index).
-   **Rendering:** The [`AnnotateElement`](./AnnotateElement.md) renders this as an SVG `<path>` element (or equivalent Canvas path) based on the stored points and style.

## User Interactions

-   **Creation:** Click-drag-release.
-   **Selection:** Clicking on the drawn line selects it.
-   **Modification:**
    -   Selected lines can typically be moved by dragging.
    -   Style (color, thickness) can be changed via the [`AnnotationContextMenu`](../../components/common/AnnotationContextMenu.md).
    -   Resizing might not be applicable, but deleting is possible.

## Usage

-   Allows users to draw freeform shapes or highlight areas on the plot in a non-structured way.
-   Useful for quick, informal annotations or pointing things out.

## Dependencies

-   Managed and rendered by **[`AnnotateElement`](./AnnotateElement.md)**.
-   Uses plot coordinates derived from user mouse input relative to the **[`PlotView`](../PlotView.md)** canvas.
-   Style modifications handled via **[`AnnotationContextMenu`](../../components/common/AnnotationContextMenu.md)**. 