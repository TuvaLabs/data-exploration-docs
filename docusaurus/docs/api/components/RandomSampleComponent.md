---
sidebar_position: 6.8 # Position alongside other CaseCardComponent related items
title: RandomSampleComponent
---

# RandomSampleComponent

(*Path likely `src/components/randomSampleComponent.js` or similar*)

This component provides an interface for configuring and applying random sampling techniques to the dataset.

## Overview

Working with large datasets can sometimes be slow or computationally intensive. This component allows users to draw a smaller, random subset of the data for exploration or analysis. It might be presented as a distinct view within the [`CaseCardComponent`](./CaseCardComponent.md) or launched from a menu.

-   **Functionality:** Offers controls to:
    -   Select the sampling method (e.g., simple random sample).
    -   Specify the sample size (either as a fixed number of cases or a percentage of the total dataset).
    -   Potentially configure options like sampling with or without replacement.
    -   Trigger the sampling process.
    -   Display information about the current sample (if active).
    -   Option to clear the sample and return to the full dataset.
-   **Impact:** Applying a sample typically filters the data used by all other components ([`PlotView`](../dynplot/PlotView.md), [`CaseTableComponent`](./CaseTableComponent.md), calculations) to only include the sampled cases.

## Key Props (Conceptual)

-   `totalCaseCount`: The total number of cases in the full dataset.
-   `currentSampleSettings`: An object reflecting the active sample configuration (e.g., `size: 100`, `method: 'simple'`) or null/undefined if no sample is active.
-   `onApplySample`: Callback function to trigger the sampling logic, passing the desired settings.
-   `onClearSample`: Callback function to remove the active sample filter.

## Rendering

-   Displays options for sample size (number/percentage inputs).
-   May include dropdowns for sampling method or other options.
-   Provides buttons like "Apply Sample" and "Clear Sample".
-   Shows status information about the current sample size if one is active.

## Usage

-   Launched from [`CaseCardComponent`](./CaseCardComponent.md) or a data/sampling menu.
-   Allows users to work with a representative subset of large datasets to improve performance or for specific statistical purposes.

## Dependencies

-   Often launched/controlled by **[`CaseCardComponent`](./CaseCardComponent.md)**.
-   Requires information about the total dataset size.
-   Interacts with application state (`Dyn`) or data management functions to:
    -   Trigger the sampling algorithm.
    -   Apply/remove the filter representing the active sample.
-   The applied sample affects data used by **[`PlotView`](../dynplot/PlotView.md)**, **[`CaseTableComponent`](./CaseTableComponent.md)**, **[`AttributeListComponent`](./AttributeListComponent.md)** value display, etc. 