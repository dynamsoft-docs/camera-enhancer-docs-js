---
layout: default-layout
title: LineDrawingItem - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the LineDrawingItem definitions of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: camera enhancer, linedrawingitem, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: LineDrawingItem
permalink: /programming/javascript/api-reference/linedrawingitem.html
---

# Class LineDrawingItem

The `LineDrawingItem` class extends the functionality of the `DrawingItem` class and is specifically tailored to handle line-related drawing operations.

| Name                                                | Description                                        |
| --------------------------------------------------- | -------------------------------------------------- |
| `constructor` [LineDrawingItem()](#linedrawingitem) | Constructor for the class.                         |
| [getLine()](#getline)                               | Retrieves the current line being used for drawing. |
| [setLine()](#setline)                               | Sets the line to be used for drawing.              |

## LineDrawingItem

Constructor for the class.

```typescript
constructor(
    line: LineSegment,
    drawingStyleId?: number
)
```

**Parameters**

`line`: the line to be drawn, of type `LineSegment`.

`drawingStyleId`: [Optional] the unique ID of the `DrawingStyle` to apply to this `DrawingItem`.

**Code Snippet**

```js
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.createDrawingLayer();
let lineItem = new Dynamsoft.DCE.DrawingItem.LineDrawingItem(
    {
        startPoint:
        {
            x: 50, 
            y: 50
        }, 
        endPoint:
        {
            x: 500, 
            y: 500
        }
    }
);
drawingLayer.addDrawingItem(lineItem);
```

**See also**

[LineSegment](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/line-segment.html)

## getLine

Retrieves the current line being used for drawing.

```typescript
getLine(): LineSegment;
```

**Parameters**

None.

**Return Value**

The current line being used for drawing, of type `LineSegment`.

**Code Snippet**

```js
lineItem.getLine();
```

## setLine

Sets the line to be used for drawing. This method allows changing the line after the object has been instantiated.

```typescript
setLine(line: LineSegment): void;
```

**Parameters**

`line`: the line to be drawn, of type `LineSegment`.

**Return Value**

None.

**Code Snippet**

```js
lineItem.setLine(/*A-New-Line*/);
```

**See also**

[LineSegment](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/line-segment.html)
