---
sidebar_position: 6.5 # Position alongside other CaseCardComponent related items
title: AttributeDisplaySetting
---

# AttributeDisplaySetting

(*Path likely `src/components/attributeDisplaySetting.js` or similar*)

This component provides an interface for configuring **global display settings** that affect how attributes are presented throughout the application, particularly within the [`AttributeListComponent`](./AttributeListComponent.md).

## Overview

Likely launched from the [`CaseCardComponent`](./CaseCardComponent.md) or a settings menu, `AttributeDisplaySetting` allows users to customize the appearance and information density of the attribute list.

-   **Functionality:** Offers controls to toggle or modify global settings such as:
    -   Show/Hide Color Swatches: Control visibility of the color indicators next to attribute names.
    -   Show/Hide Sparklines/Distributions: Potentially toggle mini-visualizations (like histograms or bar charts) next to each attribute name to show its overall distribution.
    -   Attribute Sorting: Set a default sort order for the attribute list itself (e.g., alphabetical, by type).
    -   Value Display Format: Maybe global settings for numerical precision or date formats if not overridden by individual attribute settings.
-   **Scope:** These settings typically apply globally to the attribute list view, rather than specific individual attributes.
-   **Persistence:** Settings configured here are likely saved (e.g., in local storage or application state) to persist across sessions.

## Key Props (Conceptual)

-   `currentSettings`: An object containing the current values of the global display settings.
-   `onSettingsChange`: A callback function to update the settings in the application state (`Dyn`) or persistence layer.

## Rendering

-   Renders labels and controls (e.g., checkboxes, dropdowns) for each available global setting.
-   Initializes controls based on `currentSettings`.
-   Attaches handlers to update settings via `onSettingsChange`.

## Usage

-   Launched from [`CaseCardComponent`](./CaseCardComponent.md) or a general settings area.
-   Allows users to tailor the attribute list display to their preferences or analytical needs.

## Dependencies

-   Often launched/controlled by **[`CaseCardComponent`](./CaseCardComponent.md)**.
-   Reads and modifies **global application settings** related to attribute display (potentially stored in `Dyn` or local storage).
-   The configured settings influence the rendering behavior of **[`AttributeListComponent`](./AttributeListComponent.md)**. 