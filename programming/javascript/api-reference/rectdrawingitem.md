---
layout: default-layout
title: RectDrawingItem - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the RectDrawingItem definitions of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: camera enhancer, rectdrawingitem, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: RectDrawingItem
---

# Class RectDrawingItem

The `RectDrawingItem` class extends the functionality of the `DrawingItem` class and is specifically tailored to handle rectangle-related drawing operations.

| Name                                                | Description                                             |
| --------------------------------------------------- | ------------------------------------------------------- |
| `constructor` [RectDrawingItem()](#rectdrawingitem) | Constructor for the class.                              |
| [getRect()](#getrect)                               | Retrieves the current rectangle being used for drawing. |
| [setRect()](#setrect)                               | Sets the rectangle to be used for drawing.              |

## RectDrawingItem

Constructor for the class.

```typescript
constructor(
    rect: Rect,
    drawingStyleId?: number
)
```

**Parameters**

`rect`: the rectangle to be drawn, of type `Rect`.

`drawingStyleId`: [Optional] the unique ID of the `DrawingStyle` to apply to this `DrawingItem`.

**Code Snippet**

```js
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.createDrawingLayer();
let rectItem = new Dynamsoft.DCE.RectDrawingItem(
    {
        x: 50,
        y: 50,
        width: 500,
        height: 500
    }
);
drawingLayer.addDrawingItem(rectItem);
```

**See also**

[Rect](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/rect.html)

## getRect

Retrieves the current rectangle being used for drawing.

```typescript
getRect(): Rect;
```

**Parameters**

None.

**Return Value**

The current rectangle being used for drawing, of type `Rect`.

**Code Snippet**

```js
rectItem.getRect();
```

## setRect

Sets the rectangle to be used for drawing. This method allows changing the rectangle after the object has been instantiated.

```typescript
setRect(rect: Rect): void;
```

**Parameters**

`rect`: the rectangle to be drawn, of type `Rect`.

**Return Value**

None.

**Code Snippet**

```js
rectItem.setRect(/*A-New-Rectangle*/);
```

**See also**

[Rect](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/rect.html)
