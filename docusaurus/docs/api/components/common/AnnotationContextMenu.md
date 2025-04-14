---
sidebar_position: 4 # Position after HistogramContextMenu
title: AnnotationContextMenu
---

# AnnotationContextMenu Component

(*Path likely `src/components/common/AnnotationContextMenu.jsx` or `src/components/contextMenus/AnnotationContextMenu.jsx`*)

This component provides the **context-specific menu items** that appear when the user right-clicks on an **annotation element** (created via the [`AnnotateElement`](../../dynplot/plotElement/AnnotateElement.md) plot type).

## Overview

When [`ContextMenuUtil`](../../dynplot/utils/ContextMenuUtil.md) identifies the context as being an annotation, the [`ContextMenuWrapper`](./ContextMenuWrapper.md) incorporates the items from this component.

-   **Functionality:** Defines menu items relevant specifically to the type of annotation clicked (e.g., text, shape, line).
-   **Potential Menu Items:**
    -   **Edit Text:** (For text annotations) Open an editor to change the text content.
    -   **Change Text Size:** (For text annotations) Options to increase/decrease font size.
    -   **Change Color:** Modify the color (fill or stroke) of the annotation element.
    -   **Bring to Front / Send to Back:** Adjust the layering (z-index) of the annotation relative to others.
    -   **Delete Annotation:** Remove the selected annotation.

## Structure (Conceptual)

Likely exports an array of menu item definitions or a function that returns the appropriate definitions based on the specific type of annotation element clicked.

## Usage

-   Its definitions are retrieved by [`ContextMenuUtil`](../../dynplot/utils/ContextMenuUtil.md) and incorporated by [`ContextMenuWrapper`](./ContextMenuWrapper.md) when the context is an annotation.

## Dependencies

-   Provides menu definitions/logic used by **[`ContextMenuWrapper`](./ContextMenuWrapper.md)** via **[`ContextMenuUtil`](../../dynplot/utils/ContextMenuUtil.md)**.
-   Actions modify properties of an annotation managed by **[`AnnotateElement`](../../dynplot/plotElement/AnnotateElement.md)**.
-   Interacts with application state (`Dyn`) to update or remove annotations. 