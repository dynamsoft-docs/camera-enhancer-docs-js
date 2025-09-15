---
layout: default-layout
title: EnumDrawingItemMediaType  - Dynamsoft Camera Enhancer JavaScript Edition API
description: Use this enum data type to set media type for drawing items when using Dynamsoft Camera Enhancer JavaScript Edition in your project.
keywords: EnumDrawingItemMediaType, CameraEnhancer, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: EnumDrawingItemMediaType
permalink: /programming/javascript/api-reference/enum/enumdrawingitemmediatype.html
---

# EnumDrawingItemMediaType

`EnumDrawingItemMediaType` categorizes different types of drawing items that can be created, manipulated, or displayed.

```typescript
enum EnumDrawingItemMediaType {
    /**
     * Represents a rectangle, a basic geometric shape with four sides where opposite sides are equal in length and it has four right angles.
     */
    DIMT_RECTANGLE = 1,
    /**
     * Represents any four-sided figure. This includes squares, rectangles, rhombuses, and more general forms that do not necessarily have right angles or equal sides.
     */
    DIMT_QUADRILATERAL = 2,
    /**
     * Represents a text element. This allows for the inclusion of textual content as a distinct drawing item within the graphic representation.
     */
    DIMT_TEXT = 4,
    /**
     * Represents an arc, which is a portion of the circumference of a circle or an ellipse. Arcs are used to create curved shapes and segments.
     */
    DIMT_ARC = 8,
    /**
     * Represents an image. This enables embedding bitmap images within the drawing context.
     */
    DIMT_IMAGE = 16,
    /**
     * Represents a polygon, which is a plane figure that is described by a finite number of straight line segments connected to form a closed polygonal chain or circuit.
     */
    DIMT_POLYGON = 32,
    /**
     * Represents a line segment. This is the simplest form of a drawing item, defined by two endpoints and the straight path connecting them.
     */
    DIMT_LINE = 64,
    /**
     * Represents a group of drawing items. This allows for the logical grouping of multiple items, treating them as a single entity for manipulation or transformation purposes.
     */
    DIMT_GROUP = 128
}
```