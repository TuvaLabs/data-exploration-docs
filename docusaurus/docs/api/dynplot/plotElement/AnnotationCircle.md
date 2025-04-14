---
sidebar_position: 15.3
title: AnnotationCircle
---

# AnnotationCircle Type

This represents a circle or ellipse annotation drawn by the user, managed by the base [`AnnotateElement`](./AnnotateElement.md).

## Overview

When the "Circle" or "Ellipse" tool is selected within the annotation mode, users can draw circular or elliptical shapes on the plot canvas.

-   **Drawing Process:**
    -   Typically involves a click-drag-release gesture.
    -   The drag might define the radius (for a circle starting from the center) or the bounding box (for an ellipse).
-   **Data Stored:** The data for a circle/ellipse annotation typically includes:
    -   Center position (`cx`, `cy` coordinates in plot data space).
    -   Radii (`rx`, `ry` - potentially just `r` for a circle) in plot data space units.
    -   Style properties (fill color, stroke color, stroke width, opacity).
    -   A unique ID.
    -   Layering information (z-index).
-   **Rendering:** The [`AnnotateElement`](./AnnotateElement.md) renders this as an SVG `<circle>` or `<ellipse>` element (or equivalent Canvas arc/ellipse) based on the stored position, radii, and style.

## User Interactions

-   **Creation:** Click-drag-release (exact behavior might vary based on implementation - center-out or bounding-box).
-   **Selection:** Clicking inside the shape selects it.
-   **Modification:**
    -   Selected shapes can be moved by dragging the center or body.
    -   Selected shapes can often be resized by dragging handles on their bounding box.
    -   Style (fill, stroke) can be changed via the [`AnnotationContextMenu`](../../components/common/AnnotationContextMenu.md).
    -   Deleting is possible.

## Usage

-   Allows users to draw circular or elliptical highlights on the plot.
-   Useful for encircling clusters of points or features.

## Dependencies

-   Managed and rendered by **[`AnnotateElement`](./AnnotateElement.md)**.
-   Uses plot coordinates derived from user mouse input relative to the **[`PlotView`](../PlotView.md)** canvas.
-   Style modifications handled via **[`AnnotationContextMenu`](../../components/common/AnnotationContextMenu.md)**. 