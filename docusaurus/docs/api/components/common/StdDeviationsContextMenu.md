---
sidebar_position: 5 # Position after AnnotationContextMenu
title: StdDeviationsContextMenu
---

# StdDeviationsContextMenu Component

(*Path likely `src/components/common/StdDeviationsContextMenu.jsx` or `src/components/contextMenus/StdDeviationsContextMenu.jsx`*)

This component provides the **context-specific menu items** that appear when the user right-clicks on the **Standard Deviation bands** annotation/measure displayed on a plot (managed by [`PlotMeasure`](../../dynplot/PlotMeasure.md)).

## Overview

When [`ContextMenuUtil`](../../dynplot/utils/ContextMenuUtil.md) identifies the context as being the Standard Deviation measure, the [`ContextMenuWrapper`](./ContextMenuWrapper.md) incorporates the items from this component.

-   **Functionality:** Defines menu items allowing the user to adjust the display of the standard deviation bands.
-   **Potential Menu Items:**
    -   **±1 Standard Deviation:** Toggle or select the display of bands covering one standard deviation from the mean.
    -   **±2 Standard Deviations:** Toggle or select the display of bands covering two standard deviations.
    -   **±3 Standard Deviations:** Toggle or select the display of bands covering three standard deviations.
    -   **Hide Standard Deviations:** Remove the bands from the plot.

## Structure (Conceptual)

Likely exports an array of menu item definitions or a function that returns definitions for adjusting the standard deviation level.

## Usage

-   Its definitions are retrieved by [`ContextMenuUtil`](../../dynplot/utils/ContextMenuUtil.md) and incorporated by [`ContextMenuWrapper`](./ContextMenuWrapper.md) when the context is the standard deviation measure.
-   Provides convenient shortcuts for changing the displayed SD levels.

## Dependencies

-   Provides menu definitions/logic used by **[`ContextMenuWrapper`](./ContextMenuWrapper.md)** via **[`ContextMenuUtil`](../../dynplot/utils/ContextMenuUtil.md)**.
-   Actions modify the configuration or visibility state of the Standard Deviation measure managed by **[`PlotMeasure`](../../dynplot/PlotMeasure.md)**. 