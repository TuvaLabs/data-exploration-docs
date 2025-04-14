---
sidebar_position: 15.6
title: AnnotationText
---

# AnnotationText Type

This represents a text annotation added by the user, managed by the base [`AnnotateElement`](./AnnotateElement.md).

## Overview

When the "Text" tool is selected within the annotation mode, users can click on the plot to place and enter text labels.

-   **Drawing/Placement Process:**
    -   User clicks on the plot canvas where they want the text to appear.
    -   An input box or prompt likely appears, allowing the user to type the text content.
    -   Confirming the text places the annotation.
-   **Data Stored:** The data for a text annotation typically includes:
    -   Position (`x`, `y` coordinates of the anchor point in plot data space).
    -   Text content (the string entered by the user).
    -   Style properties (font size, font family, text color, text alignment/anchor).
    -   A unique ID.
    -   Layering information (z-index).
-   **Rendering:** The [`AnnotateElement`](./AnnotateElement.md) renders this as an SVG `<text>` element (or equivalent Canvas text).

## User Interactions

-   **Creation:** Click to place, type text, confirm.
-   **Selection:** Clicking on the text selects it.
-   **Modification:**
    -   Selected text can be moved by dragging.
    -   Text content can often be edited (e.g., by double-clicking).
    -   Style (font size, color) can be changed via the [`AnnotationContextMenu`](../../components/common/AnnotationContextMenu.md).
    -   Deleting is possible.

## Usage

-   Allows users to add labels, notes, or explanations directly onto the plot visualization.

## Dependencies

-   Managed and rendered by **[`AnnotateElement`](./AnnotateElement.md)**.
-   Uses plot coordinates derived from user mouse input relative to the **[`PlotView`](../PlotView.md)** canvas.
-   Text editing might involve temporary HTML input overlays or prompts.
-   Style modifications handled via **[`AnnotationContextMenu`](../../components/common/AnnotationContextMenu.md)**. 