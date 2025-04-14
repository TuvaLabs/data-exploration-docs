---
sidebar_position: 6.41 # Position nested under NewAttributeComponent
title: FormulaInputComponent
---

# FormulaInputComponent

(*Path likely `src/components/formulaInputComponent.js` or similar*)

This is a specialized sub-component rendered within [`NewAttributeComponent`](./NewAttributeComponent.md). Its primary purpose is to provide a dedicated input area for users to write the **formulas** or expressions that define new, calculated attributes.

## Overview

Creating derived attributes requires a way to input mathematical or logical expressions. `FormulaInputComponent` provides a potentially enhanced input field tailored for this task.

-   **Functionality:**
    -   Provides a text area or specialized editor for entering formula strings.
    -   May offer features to improve the user experience, such as:
        -   **Syntax Highlighting:** Color-coding operators, functions, attribute names, and numbers.
        -   **Autocompletion:** Suggesting available [`Attribute`](../dynDataset/Attribute.md) names or built-in function names as the user types.
        -   **Validation/Error Feedback:** Providing real-time feedback on syntax errors within the formula string before submission.
        -   **Function/Attribute List:** Potentially displaying a browsable list of available functions and attributes that can be inserted into the formula.
-   **Data Binding:** The entered formula string is bound to the state managed by the parent [`NewAttributeComponent`](./NewAttributeComponent.md).

## Key Props (Conceptual)

-   `currentFormula`: The formula string currently being edited.
-   `availableAttributes`: A list/map of existing [`Attribute`](../dynDataset/Attribute.md) objects (needed for validation and autocompletion).
-   `availableFunctions`: A list/map of built-in functions supported by the formula engine ([`AttributeFormula`](../dynDataset/AttributeFormula.md)).
-   `onFormulaChange`: A callback function (provided by `NewAttributeComponent`) to update the formula string in the parent's state.
-   `validationStatus`: Information about the validity of the current formula (e.g., error message, success state).

## Rendering

-   Renders a text input area, possibly using a code editor library (like CodeMirror, Monaco Editor) for advanced features.
-   Implements syntax highlighting, autocompletion, and error display logic.
-   May include helper UI elements like function/attribute browsers.

## Usage

-   Rendered as the primary input field for the expression within [`NewAttributeComponent`](./NewAttributeComponent.md).
-   Provides the user experience for defining the calculation logic of a new attribute.

## Dependencies

-   Contained within and controlled by **[`NewAttributeComponent`](./NewAttributeComponent.md)**.
-   Needs access to the list of existing **[`Attribute`](../dynDataset/Attribute.md)** objects.
-   Relies on the syntax rules and function definitions supported by the **[`AttributeFormula`](../dynDataset/AttributeFormula.md)** parsing and evaluation engine.
-   May utilize external **code editor or syntax highlighting libraries**. 