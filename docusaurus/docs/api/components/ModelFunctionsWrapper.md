---
sidebar_position: 6.9 # Position alongside other CaseCardComponent related items
title: ModelFunctionsWrapper
---

# ModelFunctionsWrapper

(*Path likely `src/components/modelFunctionsWrapper.js` or similar*)

This component likely acts as a container or entry point for accessing and applying various statistical models or functions to the data.

## Overview

Presented as a view within [`CaseCardComponent`](./CaseCardComponent.md) or launched from a dedicated menu, `ModelFunctionsWrapper` provides access to more advanced analytical capabilities.

-   **Functionality:**
    -   Presents a list or menu of available statistical models or functions (e.g., linear regression, clustering, hypothesis tests, data transformations).
    -   Allows the user to select a model/function.
    -   Likely renders a specific configuration interface for the selected model/function (potentially by mounting other dedicated components).
    -   Provides controls to execute the model/function.
    -   May display results (e.g., model coefficients, test statistics, new derived attributes) or trigger updates in other components ([`PlotView`](../dynplot/PlotView.md), [`CaseTableComponent`](./CaseTableComponent.md)) to visualize results.
-   **Extensibility:** May be designed to easily incorporate new models or functions.

## Key Props (Conceptual)

-   `availableModels`: A list of models/functions the user can choose from.
-   `attributes`: The list of available [`Attribute`](../dynDataset/Attribute.md) objects, needed for model configuration (e.g., selecting dependent/independent variables).
-   `onModelExecute`: A callback function to trigger the execution of the selected model with its configuration.

## Rendering

-   Initially displays a list or selection mechanism for available models/functions.
-   Once a model is selected, conditionally renders the specific configuration UI for that model.
-   Includes buttons to run the model and potentially view/manage results.

## Usage

-   Launched from [`CaseCardComponent`](./CaseCardComponent.md) or an analysis menu.
-   Provides access to advanced statistical analysis capabilities integrated within the data exploration environment.

## Dependencies

-   Often launched/controlled by **[`CaseCardComponent`](./CaseCardComponent.md)**.
-   Requires the list of available **[`Attribute`](../dynDataset/Attribute.md)** objects for configuration.
-   Interacts with underlying statistical libraries or calculation engines to execute models.
-   May create new attributes or update application state (`Dyn`) with results.
-   Results might be visualized in **[`PlotView`](../dynplot/PlotView.md)** or **[`CaseTableComponent`](./CaseTableComponent.md)**. 