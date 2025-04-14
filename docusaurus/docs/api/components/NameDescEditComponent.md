---
sidebar_position: 6.21 # Position nested under AttributeEditComponent
title: NameDescEditComponent
---

# NameDescEditComponent

(*Path likely `src/components/nameDescEditComponent.js` or similar*)

This is a sub-component rendered within [`AttributeEditComponent`](./AttributeEditComponent.md) and is specifically responsible for allowing the user to edit the **name** and **description** of the selected attribute.

## Overview

`NameDescEditComponent` provides simple input fields tied to the name and description properties of the attribute being edited.

-   **Functionality:** Displays the current name and description of the attribute in text input fields and allows the user to modify them.
-   **Data Binding:** The input fields are bound to the temporary state managed by the parent [`AttributeEditComponent`](./AttributeEditComponent.md) during the editing session.
-   **Validation:** May include basic validation (e.g., ensuring the name is not empty).

## Key Props (Conceptual)

-   `attributeName`: The current name of the attribute being edited.
-   `attributeDescription`: The current description of the attribute being edited.
-   `onNameChange`: A callback function (provided by `AttributeEditComponent`) to update the name in the parent's state as the user types.
-   `onDescriptionChange`: A callback function (provided by `AttributeEditComponent`) to update the description in the parent's state.

## Rendering

-   Renders labeled text input fields (e.g., `<input type="text">` for name, `<textarea>` for description).
-   Populates the fields with the initial `attributeName` and `attributeDescription` props.
-   Attaches the `onNameChange` and `onDescriptionChange` handlers to the respective input fields.

## Usage

-   Rendered as part of the layout within [`AttributeEditComponent`](./AttributeEditComponent.md).
-   Provides the basic text editing controls for the attribute's core identifiers.

## Dependencies

-   Contained within and controlled by **[`AttributeEditComponent`](./AttributeEditComponent.md)**.
-   Receives and updates properties related to an **[`Attribute`](../dynDataset/Attribute.md)**. 