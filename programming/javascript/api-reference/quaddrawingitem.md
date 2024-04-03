---
layout: default-layout
title: QuadDrawingItem - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the QuadDrawingItem definitions of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: camera enhancer, quaddrawingitem, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: QuadDrawingItem
permalink: /programming/javascript/api-reference/quaddrawingitem.html
---

# Class QuadDrawingItem

The `QuadDrawingItem` class extends the functionality of the `DrawingItem` class and is specifically tailored to handle quadrilateral-related drawing operations.

| Name                                                | Description                                                 |
| --------------------------------------------------- | ----------------------------------------------------------- |
| `constructor` [QuadDrawingItem()](#quaddrawingitem) | Constructor for the class.                                  |
| [getQuad()](#getquad)                               | Retrieves the current quadrilateral being used for drawing. |
| [setQuad()](#setquad)                               | Sets the quadrilateral to be used for drawing.              |

## QuadDrawingItem

Constructor for the class.

```typescript
constructor(
    quad: Quadrilateral,
    drawingStyleId?: number
)
```

**Parameters**

`quad`: the quadrilateral to be drawn, of type `Quadrilateral`.

`drawingStyleId`: [Optional] the unique ID of the `DrawingStyle` to apply to this `DrawingItem`.

**Code Snippet**

```js
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.createDrawingLayer();
let quadItem = new Dynamsoft.DCE.DrawingItem.QuadDrawingItem(
    {
        points:[{
            x: 50, 
            y: 50
        },{
            x: 500, 
            y: 50
        },
        {
            x: 500, 
            y: 500
        },{
            x: 50, 
            y: 500
        }]
    }
);
drawingLayer.addDrawingItem(quadItem);
```

**See also**

[Quadrilateral](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/quadrilateral.html)

## getQuad

Retrieves the current quadrilateral being used for drawing.

```typescript
getQuad(): Quadrilateral;
```

**Parameters**

None.

**Return Value**

The current quadrilateral being used for drawing, of type `Quadrilateral`.

**Code Snippet**

```js
quadItem.getQuad();
```

## setQuad

Sets the quadrilateral to be used for drawing. This method allows changing the quadrilateral after the object has been instantiated.

```typescript
setQuad(quad: Quadrilateral): void;
```

**Parameters**

`quad`: the quadrilateral to be drawn, of type `Quadrilateral`.

**Return Value**

None.

**Code Snippet**

```js
quadItem.setQuad(/*A-New-Quadrilateral*/);
```

**See also**

[Quadrilateral](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/quadrilateral.html)
