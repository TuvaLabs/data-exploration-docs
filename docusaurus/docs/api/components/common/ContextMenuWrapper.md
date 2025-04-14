---
sidebar_position: 1 # Position first within common components
title: ContextMenuWrapper
---

# ContextMenuWrapper Component

(*Path: `src/components/common/ContextMenuWrapper.jsx`*)

This React component is responsible for rendering the context menu overlay at the correct position on the screen. It dynamically determines the menu content based on the context provided (likely using [`ContextMenuUtil`](../../dynplot/utils/ContextMenuUtil.md)) and includes global menu items.

## Overview

When a user performs an action to trigger a context menu (e.g., right-click), this component is likely mounted or updated to display the appropriate menu near the event location.

-   **Functionality:**
    -   Receives information about the context menu trigger event (e.g., click coordinates, target element/context).
    -   Calls [`ContextMenuUtil`](../../dynplot/utils/ContextMenuUtil.md) to get the list of context-specific menu items or the specific menu component to render.
    -   Retrieves the list of global menu items from [`GlobalContextMenu`](./GlobalContextMenu.md).
    -   Combines the specific and global menu items (filtering global items based on context if necessary).
    -   Renders the menu UI overlay (e.g., a positioned `<div>` containing list items) at the correct screen coordinates.
    -   Handles menu item clicks, triggering the associated actions/callbacks.
    -   Handles closing the menu (e.g., on outside click).

## Key Props (Conceptual)

-   `eventContext`: An object containing details about the trigger event (e.g., `x`, `y`, `targetType`, `targetData`).
-   `isVisible`: Boolean controlling whether the menu is displayed.
-   `onClose`: Callback function to hide the menu.

## Rendering

-   Conditionally renders based on `isVisible`.
-   Calculates the menu's position based on `eventContext.x`, `eventContext.y`.
-   Fetches context-specific items/component using `ContextMenuUtil`.
-   Fetches global items from `GlobalContextMenu`.
-   Renders the combined list of menu items, attaching click handlers.
-   Includes logic for closing the menu.

## Usage

-   Likely rendered at a high level in the application tree, possibly controlled by a global state or context provider.
-   Its visibility and content are updated dynamically based on user interactions that trigger context menus.

## Dependencies

-   Uses **[`ContextMenuUtil`](../../dynplot/utils/ContextMenuUtil.md)** to determine context-specific content.
-   Includes or references **[`GlobalContextMenu`](./GlobalContextMenu.md)** for common items.
-   May render specific menu components like **[`HistogramContextMenu`](./HistogramContextMenu.md)**, **[`AnnotationContextMenu`](./AnnotationContextMenu.md)**, **[`StdDeviationsContextMenu`](./StdDeviationsContextMenu.md)** based on the context.
-   Likely interacts with application state (`Dyn` or React context) to get context and trigger actions. 