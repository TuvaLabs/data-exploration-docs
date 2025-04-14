---
sidebar_position: 6.7 # Position alongside other CaseCardComponent related items
title: AccessibilitySettingsComponent
---

# AccessibilitySettingsComponent

(*Path likely `src/components/accessibilitySettingsComponent.js` or similar*)

This component provides an interface for configuring accessibility-related features and options within the application.

## Overview

Likely launched from the [`CaseCardComponent`](./CaseCardComponent.md) or a general settings menu, `AccessibilitySettingsComponent` allows users to adjust settings to improve their experience based on specific accessibility needs.

-   **Functionality:** Offers controls to modify settings such as:
    -   **Color Vision Deficiency Modes:** Options to adjust color palettes used in plots ([`PlotView`](../dynplot/PlotView.md)) to be more distinguishable for users with different types of color blindness (e.g., deuteranopia, protanopia, tritanopia).
    -   **Increased Contrast:** Options to enhance the contrast between text, UI elements, and backgrounds.
    -   **Font Size Adjustments:** Controls to increase or decrease the base font size used in the UI.
    -   **Keyboard Navigation Enhancements:** Potentially settings related to focus indicators or keyboard interaction modes.
    -   **Reduced Motion:** Option to disable or reduce animations and transitions.
-   **Scope:** Settings can affect various parts of the application, including plot rendering, UI controls, and text display.
-   **Persistence:** Accessibility settings are typically saved (e.g., in local storage or user preferences) to persist across sessions.

## Key Props (Conceptual)

-   `currentAccessibilitySettings`: An object containing the current values of the accessibility settings.
-   `onSettingsChange`: A callback function to update the settings in the application state (`Dyn`) or persistence layer.

## Rendering

-   Renders labels and controls (e.g., dropdowns for color modes, checkboxes, sliders for font size) for each available accessibility setting.
-   Initializes controls based on `currentAccessibilitySettings`.
-   Attaches handlers to update settings via `onSettingsChange`.

## Usage

-   Launched from [`CaseCardComponent`](./CaseCardComponent.md) or a general settings area.
-   Allows users to customize the application to better suit their accessibility requirements.

## Dependencies

-   Often launched/controlled by **[`CaseCardComponent`](./CaseCardComponent.md)**.
-   Reads and modifies **global application settings** related to accessibility (potentially stored in `Dyn` or local storage).
-   The configured settings can influence rendering in **[`PlotView`](../dynplot/PlotView.md)**, styles applied to various UI components, and potentially event handling. 