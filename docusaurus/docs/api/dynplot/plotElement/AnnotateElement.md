---
sidebar_position: 15 # Position after MapElement
title: AnnotateElement (Base)
---

# `AnnotateElement` (Base Class/Concept)

(*Path likely `src/lib/dynplot/plotElement/annotateElement.js` or similar*)

This `PlotElement` subclass is responsible for enabling users to draw and manage various **annotations** directly onto the plot area rendered by [`PlotView`](../PlotView.md).

## Overview

`AnnotateElement` acts as the controller for the annotation layer. When active (likely selected from the [`ToolbarComponent`](../../components/ToolbarComponent.md)), it allows users to select different annotation tools and draw corresponding shapes, lines, text, or images onto the plot.

-   **Functionality:**
    -   Provides tool selection (e.g., Pencil, Rectangle, Text) for different annotation types.
    -   Handles user input events (mouse down, drag, mouse up) on the plot canvas to draw the selected annotation type.
    -   Stores the data for each created annotation (position, size, text content, style properties, type).
    -   Manages the rendering of all created annotations.
    -   Handles selection and modification of existing annotations (moving, resizing, changing style, deleting).
    -   Manages layering (bring to front/back).
-   **Integration:** Works closely with [`PlotView`](../PlotView.md) to capture mouse events and render SVG/Canvas elements for the annotations.

## Supported Annotation Types

`AnnotateElement` manages various types of annotations, each potentially handled by specific internal logic or helper classes:

-   [`AnnotationLinePencil`](./AnnotationLinePencil.md): Freehand drawing.
-   [`AnnotationRectangle`](./AnnotationRectangle.md): Drawing rectangles.
-   [`AnnotationCircle`](./AnnotationCircle.md): Drawing circles/ellipses.
-   [`AnnotationArrow`](./AnnotationArrow.md): Drawing arrows.
-   [`AnnotationStraightLine`](./AnnotationStraightLine.md): Drawing straight line segments.
-   [`AnnotationText`](./AnnotationText.md): Adding text labels.
-   [`AnnotationImage`](./AnnotationImage.md): Embedding images.

## Key Properties & Methods (Conceptual)

-   `activeTool`: The currently selected annotation tool type.
-   `annotations`: An array or list storing the data for all created annotations.
-   `selectedAnnotation`: Reference to the currently selected annotation for modification.
-   `handleMouseDown/Drag/MouseUp()`: Methods processing user input to draw or modify annotations.
-   `addAnnotation(annotationData)`: Adds a new annotation to the list.
-   `removeAnnotation(annotationId)`: Removes an annotation.
-   `updateAnnotation(annotationId, changes)`: Updates properties of an annotation.
-   `renderAnnotations()`: Method called by `PlotView` to draw all annotations.
-   `setActiveTool(toolType)`: Sets the current drawing tool.

## Usage

-   Instantiated and managed by [`PlotShaper`](../PlotShaper.md) when the user selects an "Annotate" mode or tool from the [`ToolbarComponent`](../../components/ToolbarComponent.md).
-   Provides the tools for users to add explanatory drawings, text, or images to enrich the plot visualization.
-   User interactions with annotations (e.g., right-click) might trigger the [`AnnotationContextMenu`](../../components/common/AnnotationContextMenu.md).

## Dependencies

-   Extends **[`PlotElement`](./PlotElement.md)**.
-   Interacts heavily with **[`PlotView`](../PlotView.md)** for event handling and rendering (likely using RaphaelJS or similar).
-   Manages data related to specific annotation types (Text, Line, Shape, Image).
-   May interact with **[`ContextMenuUtil`](../utils/ContextMenuUtil.md)** and **[`AnnotationContextMenu`](../../components/common/AnnotationContextMenu.md)**. 