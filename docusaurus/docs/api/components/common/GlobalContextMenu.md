---
sidebar_position: 2 # Position after ContextMenuWrapper
title: GlobalContextMenu
---

# GlobalContextMenu Component

(*Path: `src/components/common/GlobalContextMenu.jsx`*)

This component defines and provides the list of **globally available context menu items** that are common across different interaction contexts within the plot area.

## Overview

The [`ContextMenuWrapper`](./ContextMenuWrapper.md) combines the context-specific menu items (determined by [`ContextMenuUtil`](../../dynplot/utils/ContextMenuUtil.md)) with the standard items provided by `GlobalContextMenu`.

-   **Functionality:** Acts as a source or definition for standard context menu actions.
-   **Common Global Items (Examples):**
    -   **Copy Image:** Action to copy the current plot visualization to the clipboard.
    -   **Export Data:** Action to export the currently displayed (or selected) data (e.g., as CSV).
    -   **Reset Plot:** Action to reset zoom/pan or visual settings.
    -   **Hide/Show All Cases:** Actions related to global case visibility.
-   **Conditional Visibility:** While the items are "global", their actual visibility in the final rendered menu might still depend on the specific context (e.g., "Export Data" might be disabled if no data is plotted).

## Structure (Conceptual)

This might not be a traditional rendered React component but rather a module that exports an array of menu item definitions. Each definition could include:

-   `label`: The text displayed for the menu item.
-   `action`: A callback function or identifier for the action to perform when clicked.
-   `isVisible(context)`: An optional function that determines if the item should be shown based on the current context.
-   `isEnabled(context)`: An optional function that determines if the item should be enabled/disabled.

## Usage

-   Imported or referenced by [`ContextMenuWrapper`](./ContextMenuWrapper.md) when constructing the final list of menu items to display.

## Dependencies

-   Provides menu definitions used by **[`ContextMenuWrapper`](./ContextMenuWrapper.md)**.
-   The `action` handlers likely interact with application state (`Dyn`) or specific functionalities (e.g., plot export logic, data filtering logic). 