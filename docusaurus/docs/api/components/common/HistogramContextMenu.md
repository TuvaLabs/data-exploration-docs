---
sidebar_position: 3 # Position after GlobalContextMenu
title: HistogramContextMenu
---

# HistogramContextMenu Component

(*Path likely `src/components/common/HistogramContextMenu.jsx` or `src/components/contextMenus/HistogramContextMenu.jsx`*)

This component provides the **context-specific menu items** that appear when the user right-clicks on elements related to a Histogram plot (e.g., a histogram bar).

## Overview

When [`ContextMenuUtil`](../../dynplot/utils/ContextMenuUtil.md) identifies the context as being a histogram or part of one, the [`ContextMenuWrapper`](./ContextMenuWrapper.md) will incorporate the items defined or provided by this component.

-   **Functionality:** Defines menu items relevant specifically to histograms.
-   **Potential Menu Items:**
    -   Select Cases in Bin: Action to select all data cases represented by the clicked bar.
    -   Hide Cases in Bin: Action to hide cases represented by the clicked bar.
    -   Change Bin Width: Action to open controls for adjusting histogram binning.
    -   Show Count/Percentage: Options related to measures displayed on histogram bars.

## Structure (Conceptual)

Similar to `GlobalContextMenu`, this might be a module exporting an array of menu item definitions specific to the histogram context, or a simple component returning those definitions.

## Usage

-   Its definitions are retrieved by [`ContextMenuUtil`](../../dynplot/utils/ContextMenuUtil.md) and incorporated by [`ContextMenuWrapper`](./ContextMenuWrapper.md) when the context is appropriate.

## Dependencies

-   Provides menu definitions/logic used by **[`ContextMenuWrapper`](./ContextMenuWrapper.md)** via **[`ContextMenuUtil`](../../dynplot/utils/ContextMenuUtil.md)**.
-   Actions likely interact with **[`DataSet`](../../dynDataset/DataSet.md)** for selection/filtering or trigger changes related to the active **[`HistogramElement`](../../dynplot/plotElement/HistogramElement.md)** (or its subclasses). 