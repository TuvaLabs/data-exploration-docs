---
sidebar_position: 4 # Position after AttributeStats
title: AttributeFormula
---

# AttributeFormula Class

(*Path likely `src/lib/dynDataset/attributeFormula.js` or `src/lib/dynDataset/formulaManager.js`*)

This helper class is responsible for parsing, managing, and evaluating the formulas used to define **derived attributes** within a [`DataSet`](./DataSet.md).

## Overview

When a user creates a new attribute using a formula (via [`NewAttributeComponent`](../components/NewAttributeComponent.md)), an `AttributeFormula` instance is likely created and associated with the new [`Attribute`](./Attribute.md) object. It handles the complexities of interpreting and calculating the formula's result for each case.

-   **Functionality:**
    -   **Parsing:** Takes the formula string entered by the user and parses it into an executable representation (e.g., an abstract syntax tree or intermediate code).
    -   **Dependency Tracking:** Identifies which other attributes are referenced within the formula.
    -   **Evaluation:** Calculates the result of the formula for a given case, retrieving the necessary values from the dependent attributes for that case.
    -   **Error Handling:** Manages potential errors during parsing or evaluation (e.g., syntax errors, type mismatches, division by zero).
    -   **Re-evaluation:** Provides mechanisms to trigger re-calculation when the values of dependent attributes change.
-   **Formula Syntax:** Defines or relies on a specific syntax for formulas, including:
    -   Referencing other attributes (e.g., `attributeName` or `id`).
    -   Mathematical operators (`+`, `-`, `*`, `/`).
    -   Logical operators (`<`, `>`, `==`, `!=`, `&&`, `||`).
    -   Built-in functions (e.g., `log()`, `abs()`, `if()`, string functions, date functions).

## Key Properties (Conceptual)

-   `formulaString`: The original formula string.
-   `parsedRepresentation`: The internal parsed form of the formula.
-   `dependentAttributeIds`: An array of IDs for the attributes referenced in the formula.
-   `errorState`: Information about any parsing or evaluation errors.

## Key Methods (Conceptual)

-   `constructor(formulaString, allAttributes)`: Parses the string and identifies dependencies.
-   `parse()`: Internal method to convert the string to the executable form.
-   `evaluate(caseIndex, caseDataAccessor)`: Calculates the formula result for a specific case. Requires a way to access the values of dependent attributes for that case.
-   `getDependencies()`: Returns the list of dependent attribute IDs.
-   `isValid()`: Returns true if the formula parsed without errors.

## Usage

-   An instance is created and associated with a derived **[`Attribute`](./Attribute.md)** when defined using [`NewAttributeComponent`](../components/NewAttributeComponent.md).
-   The **[`DataSet`](./DataSet.md)** likely uses `AttributeFormula` instances during its `evaluateFormulas()` or data update cycles to compute the values for derived attributes.
-   The formula string might be displayed or edited via **[`AttributeEditComponent`](../components/AttributeEditComponent.md)**.

## Dependencies

-   Works closely with the **[`Attribute`](./Attribute.md)** class (specifically derived attributes).
-   Used by the **[`DataSet`](./DataSet.md)** for calculating derived values.
-   Requires access to the values of other attributes during evaluation.
-   May utilize an external **parsing library** (e.g., Math.js, JSEP) or implement its own parser. 