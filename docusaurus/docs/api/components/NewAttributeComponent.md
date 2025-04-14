---
sidebar_position: 6.4 # Position alongside AttributeEditComponent related items
title: NewAttributeComponent
---

# NewAttributeComponent

(*Path likely `src/components/newAttributeComponent.js` or similar*)

This component provides the user interface for creating **new, calculated attributes** based on formulas or expressions involving existing attributes.

## Overview

Often launched from the [`CaseCardComponent`](./CaseCardComponent.md) or a dedicated menu, `NewAttributeComponent` allows users to extend the dataset with derived variables.

-   **Functionality:**
    -   Provides input fields for the **new attribute's name** and **description**.
    -   Includes a dedicated area for inputting the **formula** or expression.
    -   Allows users to reference existing attributes within the formula (e.g., by name like `Attribute1` or potentially by a unique ID like `att123`).
    -   May include validation for the formula syntax.
    -   Provides actions to Save/Create the new attribute or Cancel.
-   **Formula Input:** Likely utilizes a specialized sub-component (e.g., **`FormulaInputComponent`**) to handle formula entry, potentially offering features like:
    -   Syntax highlighting.
    -   Autocompletion for attribute names or functions.
    -   Error checking.
-   **Data Source:** Needs access to the list of existing [`Attribute`](../dynDataset/Attribute.md) objects to validate references in the formula.

## Key Props (Conceptual)

-   `existingAttributes`: A list or map of current [`Attribute`](../dynDataset/Attribute.md) objects.
-   `onCreateAttribute`: A callback function to trigger the creation logic in the application state (`Dyn`), passing the new attribute definition (name, description, formula).
-   `onCancel`: A callback to close the component without creating an attribute.

## Rendering

-   Renders input fields for the new attribute name and description.
-   Renders the dedicated **`FormulaInputComponent`** (or similar) for the expression.
-   Displays Save and Cancel buttons.
-   May show status messages or validation errors related to the formula.

## Usage

-   Launched from [`CaseCardComponent`](./CaseCardComponent.md) or a main toolbar/menu.
-   Allows users to perform calculations across attributes (e.g., `Attribute1 + Attribute2`, `AttributeA / AttributeB`) and save the result as a new, usable attribute.

## Dependencies

-   Often launched/controlled by **[`CaseCardComponent`](./CaseCardComponent.md)**.
-   Requires the list of existing **[`Attribute`](../dynDataset/Attribute.md)** objects.
-   Likely contains a specialized **`FormulaInputComponent`** (needs separate documentation).
-   Interacts with application state (`Dyn`) or data management functions to register the newly created attribute. 