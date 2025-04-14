---
sidebar_position: 6.6 # Position alongside other CaseCardComponent related items
title: PlotSettingComponent
---

# PlotSettingComponent

(*Path likely `src/components/plotSettingComponent.js` or similar*)

This component provides an interface for customizing the appearance and behavior of the main plot area, rendered by [`PlotView`](../dynplot/PlotView.md).

## Overview

Likely launched from the [`CaseCardComponent`](./CaseCardComponent.md) or a dedicated settings menu/toolbar, `PlotSettingComponent` offers controls to fine-tune the visual elements of the current plot.

-   **Functionality:** Offers controls to modify plot-wide settings, which might include:
    -   **Point/Mark Appearance:** Size, opacity, shape of plotted points (e.g., in scatter plots, dot plots).
    -   **Connecting Lines:** Toggle visibility of lines connecting points (e.g., in line graphs).
    -   **Gridlines:** Show/hide horizontal and vertical gridlines.
    -   **Axis Labels:** Toggle visibility of axis titles or tick labels.
    -   **Background Color:** Change the plot background.
    -   **Plot Reset:** Button to reset plot settings or zoom/pan to default.
    -   **Specific Plot Options:** Settings relevant only to the current [`PlotElement`](../dynplot/plotElement/PlotElement.md) type (e.g., bar width, histogram bin count controls if not handled elsewhere).
-   **Scope:** Settings generally apply to the entire `PlotView` rendering area.
-   **Persistence:** Settings might be saved to persist across sessions or reset each time.

## Key Props (Conceptual)

-   `currentPlotSettings`: An object containing the current values of the plot settings.
-   `onSettingsChange`: A callback function to update the settings in the application state (`Dyn`) or directly signal `PlotView`.

## Rendering

-   Renders labels and controls (e.g., sliders, checkboxes, dropdowns) for each available plot setting.
-   Initializes controls based on `currentPlotSettings`.
-   Attaches handlers to update settings via `onSettingsChange`.

## Usage

-   Launched from [`CaseCardComponent`](./CaseCardComponent.md) or a general settings area/toolbar.
-   Allows users to customize the visual presentation of the plot.

## Dependencies

-   Often launched/controlled by **[`CaseCardComponent`](./CaseCardComponent.md)**.
-   Reads and modifies settings that affect the rendering within **[`PlotView`](../dynplot/PlotView.md)** and potentially specific **[`PlotElement`](../dynplot/plotElement/PlotElement.md)** types.
-   Interacts with application state (`Dyn`) or signals `PlotView` to apply changes. 