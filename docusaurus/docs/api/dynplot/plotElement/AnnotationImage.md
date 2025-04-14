---
sidebar_position: 15.7
title: AnnotationImage
---

# AnnotationImage Type

This represents an image annotation placed by the user, managed by the base [`AnnotateElement`](./AnnotateElement.md).

## Overview

When the "Image" tool is selected within the annotation mode, users can place external images onto the plot canvas.

-   **Drawing/Placement Process:**
    -   User likely clicks on the plot to set the image position.
    -   A prompt or file selector appears, allowing the user to provide the image source (e.g., upload a file or paste a URL).
    -   The image is then placed at the clicked location.
-   **Data Stored:** The data for an image annotation typically includes:
    -   Position (`x`, `y` coordinates of the top-left corner or center in plot data space).
    -   Image source (`src` - URL or potentially base64 data).
    -   Dimensions (`width`, `height` - either intrinsic or user-defined).
    -   Style properties (opacity, maybe border).
    -   A unique ID.
    -   Layering information (z-index).
-   **Rendering:** The [`AnnotateElement`](./AnnotateElement.md) renders this as an SVG `<image>` element (or equivalent Canvas image drawing).

## User Interactions

-   **Creation:** Click to place, provide image source.
-   **Selection:** Clicking on the image selects it.
-   **Modification:**
    -   Selected images can be moved by dragging.
    -   Selected images can often be resized by dragging corner handles.
    -   Style (opacity) might be changeable via the [`AnnotationContextMenu`](../../components/common/AnnotationContextMenu.md).
    -   Deleting is possible.

## Usage

-   Allows users to embed relevant images (e.g., logos, diagrams, photos) directly onto the plot for context or explanation.

## Dependencies

-   Managed and rendered by **[`AnnotateElement`](./AnnotateElement.md)**.
-   Uses plot coordinates derived from user mouse input relative to the **[`PlotView`](../PlotView.md)** canvas.
-   Requires handling of image loading and display (potentially browser capabilities or library support).
-   Style modifications handled via **[`AnnotationContextMenu`](../../components/common/AnnotationContextMenu.md)**. 