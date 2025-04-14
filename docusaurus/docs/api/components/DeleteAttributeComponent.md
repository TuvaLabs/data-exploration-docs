---
sidebar_position: 6.31 # Position nested under AttributeEditComponent
title: DeleteAttributeComponent
---

# DeleteAttributeComponent

(*Path likely `src/components/deleteAttributeComponent.js` or similar*)

This is a sub-component rendered within [`AttributeEditComponent`](./AttributeEditComponent.md). It provides the button or control to **delete** the attribute currently being edited, typically only enabled for user-created custom attributes.

## Overview

While original dataset attributes are usually fixed, users might create custom attributes (e.g., via formulas using [`NewAttributeComponent`](./NewAttributeComponent.md)). This component offers the mechanism to remove those custom attributes.

-   **Functionality:**
    -   Displays a "Delete Attribute" button or similar control.
    -   The control is often **conditionally enabled** only if the attribute being edited is identified as a deletable (user-created) attribute.
    -   Clicking the button likely triggers a confirmation prompt before proceeding with the deletion.
-   **Data Binding/Action:** Interacts with the parent [`AttributeEditComponent`](./AttributeEditComponent.md) or directly with the application state (`Dyn`) to initiate the deletion process upon confirmation.

## Key Props (Conceptual)

-   `attribute`: The [`Attribute`](../dynDataset/Attribute.md) object being edited.
-   `isDeletable`: A boolean flag indicating if this attribute can be deleted.
-   `onDeleteAttribute`: A callback function (provided by `AttributeEditComponent`) to trigger the deletion process.

## Rendering

-   Renders a button labeled "Delete Attribute" or similar.
-   Sets the button's disabled state based on the `isDeletable` prop.
-   Attaches a click handler that likely shows a confirmation dialog and, if confirmed, calls `onDeleteAttribute`.

## Usage

-   Rendered within [`AttributeEditComponent`](./AttributeEditComponent.md), usually near the bottom or alongside Save/Cancel actions.
-   Provides the mechanism for users to remove custom attributes they no longer need.

## Dependencies

-   Contained within and controlled by **[`AttributeEditComponent`](./AttributeEditComponent.md)**.
-   Operates on an **[`Attribute`](../dynDataset/Attribute.md)** object.
-   Relies on logic to determine if an attribute is deletable.
-   Interacts with application state (`Dyn`) or data management functions to perform the actual deletion. 