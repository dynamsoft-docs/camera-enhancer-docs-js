---
layout: default-layout
title: Interface DrawingLayer - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the DrawingLayer Interface of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: DrawingLayer, CameraEnhancer, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: DrawingLayer
permalink: /programming/javascript/api-reference/drawinglayer.html
---

# Class DrawingLayer

| Name                                        | Description                                                                                           |
| ------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| [getId()](#getid)                           | Retrieves the unique identifier of the layer.                                                         |
| [isVisible()](#isvisible)                   | Retrieves the visibility status of the layer.                                                         |
| [setVisible()](#setvisible)                 | Sets the visibility of the layer.                                                                     |
| [setDefaultStyle()](#setdefaultstyle)       | Establishes the baseline styling preferences for `DrawingItem` objects on the layer.                  |
| [addDrawingItems()](#adddrawingitems)       | Adds an array of `DrawingItem` objects to the layer.                                                  |
| [removeDrawingItems()](#removedrawingitems) | Removes specified `DrawingItem` objects from the layer.                                               |
| [setDrawingItems()](#setdrawingitems)       | Sets the layer's `DrawingItem` objects, replacing any existing items.                                 |
| [getDrawingItems()](#getdrawingitems)       | Retrieves `DrawingItem` objects from the layer, optionally filtered by a custom function.             |
| [hasDrawingItem()](#hasDrawingItem)         | Checks if a specific `DrawingItem` exists within the layer.                                           |
| [clearDrawingItems()](#cleardrawingitems)   | Clears all `DrawingItem` objects from the layer.                                                      |
| [onSelectionChanged()](#onselectionchanged) | Event triggered whenever there is a change in which `DrawingItem` objects are selected or deselected. |
| [renderAll()](#renderall)                   | Forces a re-render of all `DrawingItem` objects on the layer.                                         |

**Special Notice**

If you are using **Dynamsoft Camera Enhancer** with **Dynamsoft Barcode Reader**, **Dynamsoft Label Recognizer** or **Dynamsoft Document Normalizer**, note that there is a dedicated `DrawingLayer` for each of them:

| SDK Name                      | DrawingLayer ID |
| ----------------------------- | --------------- |
| Dynamsoft Document Normalizer | 1               |
| Dynamsoft Barcode Reader      | 2               |
| Dynamsoft Label Recognizer    | 3               |

You can manipulate these `DrawingLayer` objects directly, for example, the following code applies a different `DrawingStyle` to the `DrawingLayer` used by **Dynamsoft Label Recognizer**:

> Alternatively, you can directly change the style already in use instead of replacing it with a new one. Learn more at [updateDrawingStyle](./drawingstylemanager.md#updatedrawingstyle).

```javascript
// Gets the `DrawingLayer` used by Dynamsoft Label Recognizer.
let cameraView = cameraEnhancer.getCameraView();
let dlrDrawingLayer = cameraView.getDrawingLayer(3);
// Creates a new style to be used.
let newStyleId = Dynamsoft.DCE.DrawingStyleManager.createDrawingStyle({
    fillStyle: "rgba(100, 75, 245, 0.3)",
    lineWidth: 5,
    paintMode: "strokeAndFill",
    strokeStyle: "rgba(73, 173, 245, 1)"
});
// Replaces the old style with the new one.
dlrDrawingLayer.setDefaultStyle(newStyleId);
```

## getId

Retrieves the unique identifier of the layer.

```typescript
getId(): number;
```

**Parameters**

None.

**Return Value**

The unique identifier of the layer.

**Code Snippet**

```javascript
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.createDrawingLayer();
let drawingLayerId = drawingLayer.getId();
```

## isVisible

Retrieves the visibility status of the layer.

```typescript
isVisible(): boolean;
```

**Parameters**

None.

**Return Value**

Boolean indicating whether the layer is visible.

**Code Snippet**

```javascript
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.getDrawingLayer(1);
let isVisible = drawingLayer.isVisible();
```

## setVisible

Sets the visibility of the layer.

```typescript
setVisible(visibility: boolean): void;
```

**Parameters**

`visibility`: whether to show or hide the layer.

**Return Value**

None.

**Code Snippet**

```javascript
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.getDrawingLayer(1);
drawingLayer.setVisible(false);
```

## setDefaultStyle

Establishes the baseline styling preferences for `DrawingItem` objects on the layer. This method offers flexible styling options tailored to the diverse requirements of `DrawingItem` objects based on their state and type:

* Universal Application: By default, without specifying `state` or `mediaType`, the designated style is universally applied to all `DrawingItem` objects on the layer, ensuring a cohesive look and feel.
* State-Specific Styling: Specifying only the state parameter allows the method to target `DrawingItem` objects matching that particular state, enabling differentiated styling that reflects their current status or condition.
* Refined Targeting with State and MediaType: Providing both `state` and `mediaType` parameters focuses the style application even further, affecting only those `DrawingItem` objects that align with the specified type while in the given state. This precision is particularly useful for creating visually distinct interactions or highlighting specific elements based on their content and interaction state.

```typescript
setDefaultStyle(drawingStyleId: number, state?: EnumDrawingItemState, mediaType?: EnumDrawingItemMediaType): void;
```

**Parameters**

`drawingStyleId`: the unique ID of the `DrawingStyle` to be applied.

`state`: [Optional] allows the styling to be conditional based on the `DrawingItem`'s current state. 

`mediaType`: [Optional] further refines the application of the style based on the the `DrawingItem`'s type.

**Return Value**

None.

**Code Snippet**

```javascript
//Sets style 1 for all the DrawingItems on the `DrawingLayer`
drawingLayer.setDefaultStyle(1);
//Sets style 1 for all selected DrawingItems on the `DrawingLayer`
drawingLayer.setDefaultStyle(1, Dynamsoft.DCE.EnumDrawingItemState.DIS_SELECTED);
//Sets style 1 for all selected RectDrawingItems on the `DrawingLayer`
drawingLayer.setDefaultStyle(1, Dynamsoft.DCE.EnumDrawingItemState.DIS_SELECTED, Dynamsoft.DCE.EnumDrawingItemMediaType.DIMT_RECTANGLE);
```

**See also**

[DrawingStyle](./interface/drawingstyle.md)

[EnumDrawingItemState](./enum/enumdrawingitemstate.md)

[EnumDrawingItemMediaType](./enum/enumdrawingitemmediatype.md)

## addDrawingItems

Adds an array of `DrawingItem` objects to the layer.

```typescript
addDrawingItems(drawingItems: Array<DrawingItem>): void;
```

**Parameters**

`drawingItems`: an array of `DrawingItem` objects.

**Return Value**

None.

**Code Snippet**

```javascript
let drawingItems = new Array(
    new Dynamsoft.DCE.DrawingItem.RectDrawingItem({
        x: 200,
        y: 200,
        width: 100,
        height: 100,
        isMeasuredInPercentage: true
    }),
    new Dynamsoft.DCE.DrawingItem.TextDrawingItem("label 1", {
        x: 300,
        y: 300,
        width: 300,
        height: 20,
        isMeasuredInPercentage: true
    }),
    new Dynamsoft.DCE.DrawingItem.LineDrawingItem({
        startPoint:{
            x: 400,
            y: 50
        },
        endPoint: {
            x: 900,
            y: 500
        }
    }));
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.createDrawingLayer();
drawingLayer.addDrawingItems(drawingItems);
```

**See also**

[DrawingItem](./drawingitem.md)

## removeDrawingItems

Removes specified `DrawingItem` objects from the layer.

```typescript
removeDrawingItems(drawingItems: Array<DrawingItem>): void;
```

**Parameters**

`drawingItems`: an array of `DrawingItem` objects.

**Return Value**

None.

**Code Snippet**

```javascript
let drawingItems = new Array(
    new Dynamsoft.DCE.DrawingItem.RectDrawingItem({
        x: 200,
        y: 200,
        width: 100,
        height: 100,
        isMeasuredInPercentage: true
    }),
    new Dynamsoft.DCE.DrawingItem.TextDrawingItem("label 1", {
        x: 300,
        y: 300,
        width: 300,
        height: 20,
        isMeasuredInPercentage: true
    }));
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.createDrawingLayer();
drawingLayer.addDrawingItems(drawingItems);
setTimeout(function(){
    drawingLayer.removeDrawingItems(drawingItems);
}, 2000);
```

**See also**

[DrawingItem](./drawingitem.md)

## setDrawingItems

Sets the layer's `DrawingItem` objects, replacing any existing items.

```typescript
setDrawingItems(drawingItems: Array<DrawingItem>): void;
```

**Parameters**

`drawingItems`: an array of `DrawingItem` objects.

**Return Value**

None.

**Code Snippet**

```javascript
let drawingItems = new Array(
    new Dynamsoft.DCE.DrawingItem.RectDrawingItem({
        x: 200,
        y: 200,
        width: 100,
        height: 100,
        isMeasuredInPercentage: true
    }),
    new Dynamsoft.DCE.DrawingItem.TextDrawingItem("label 1", {
        x: 300,
        y: 300,
        width: 300,
        height: 20,
        isMeasuredInPercentage: true
    }),
    new Dynamsoft.DCE.DrawingItem.LineDrawingItem({
        startPoint:{
            x: 400,
            y: 50
        },
        endPoint: {
            x: 900,
            y: 500
        }
    }));
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.createDrawingLayer();
drawingLayer.setDrawingItems(drawingItems);
```

**See also**

[DrawingItem](./drawingitem.md)

## getDrawingItems

Retrieves `DrawingItem` objects from the layer, optionally filtered by a custom function.

```typescript
getDrawingItems(filter?: (drawingItem: DrawingItem) => boolean): Array<DrawingItem>;
```

**Parameters**

`filter`: [Optional] a predicate function used to select a subset of `DrawingItem` objects based on specific criteria. Only items for which this function returns `true` are included in the result.

**Return Value**

An array of `DrawingItem` objects.

**Code Snippet**

```javascript
let drawingItems = new Array(
    new Dynamsoft.DCE.DrawingItem.RectDrawingItem({
        x: 200,
        y: 200,
        width: 100,
        height: 100,
        isMeasuredInPercentage: true
    }),
    new Dynamsoft.DCE.DrawingItem.TextDrawingItem("label 1", {
        x: 300,
        y: 300,
        width: 300,
        height: 20,
        isMeasuredInPercentage: true
    }),
    new Dynamsoft.DCE.DrawingItem.LineDrawingItem({
        startPoint:{
            x: 400,
            y: 50
        },
        endPoint: {
            x: 900,
            y: 500
        }
    }));
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.createDrawingLayer();
drawingLayer.setDrawingItems(drawingItems);
// Return only DrawingItem objects of type DIMT_RECTANGLE.
let rectDrawingItems = drawingLayer.getDrawingItems(drawingItem => drawingItem.mediaType === Dynamsoft.DCE.EnumDrawingItemMediaType.DIMT_RECTANGLE);
```

**See also**

[DrawingItem](./drawingitem.md)

## hasDrawingItem

Checks if a specific `DrawingItem` exists within the layer.

```typescript
hasDrawingItem(drawingItem: DrawingItem): boolean;
```

**Parameters**

`drawingItem`: specifies the `DrawingItem`.

**Return Value**

Boolean indicating whether the specific `DrawingItem` exists.

**Code Snippet**

```javascript
let drawingItem = new Dynamsoft.DCE.DrawingItem.RectDrawingItem({
    x: 200,
    y: 200,
    width: 100,
    height: 100,
    isMeasuredInPercentage: true
});
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.createDrawingLayer();
let hasDrawingItem = drawingLayer.hasDrawingItem(drawingItem); //false
drawingLayer.addDrawingItems([drawingItem]);
drawingLayer.hasDrawingItem(drawingItem); //true
```

**See also**

[DrawingItem](./drawingitem.md)

## clearDrawingItems

Clears all `DrawingItem` objects from the layer.

```typescript
clearDrawingItems(): void;
```

**Parameters**

None.

**Return Value**

None.

**Code Snippet**

```javascript
let drawingItems = new Array(
    new Dynamsoft.DCE.DrawingItem.RectDrawingItem({
        x: 200,
        y: 200,
        width: 100,
        height: 100,
        isMeasuredInPercentage: true
    }),
    new Dynamsoft.DCE.DrawingItem.TextDrawingItem("label 1", {
        x: 300,
        y: 300,
        width: 300,
        height: 20,
        isMeasuredInPercentage: true
    }));
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.createDrawingLayer();
drawingLayer.addDrawingItems(drawingItems);
setTimeout(function(){
    drawingLayer.clearDrawingItems();
}, 2000);
```

## renderAll

Forces a re-render of all `DrawingItem` objects on the layer.

> Invoke this method to ensure any modifications made to existing `DrawingItem` objects are visually reflected on the layer.

```typescript
renderAll(): void;
```

**Parameters**

None.

**Return Value**

None.

**Code Snippet**

```javascript
let drawingItem = new Dynamsoft.DCE.DrawingItem.RectDrawingItem({
    x: 200,
    y: 200,
    width: 100,
    height: 100,
    isMeasuredInPercentage: true
});
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.createDrawingLayer();
drawingLayer.addDrawingItems([drawingItem]);
setTimeout(function(){
    drawingItem.drawingStyleId = 3;
    drawingItem.setRect({
        x: 200,
        y: 300,
        width: 100,
        height: 200,
        isMeasuredInPercentage: true
    });
    drawingLayer.renderAll();
}, 2000);
```

## onSelectionChanged

Event triggered whenever there is a change in which `DrawingItem` objects are selected or deselected.

NOTE: This event is only functional when the `DrawingLayer` in which it is defined belongs to an `ImageEditorView` instance.

```typescript
onSelectionChanged(selectedDrawingItems: Array<DrawingItem>, deselectedDrawingItems: Array<DrawingItem>): void;
```

**Parameters**

`selectedDrawingItems`: specifies the selected `DrawingItem` objects.  

`deselectedDrawingItems`: specifies the deselected `DrawingItem` objects.

**Code Snippet**

```javascript
let imageEditorView = await Dynamsoft.DCE.ImageEditorView.createInstance();
let drawingLayer = imageEditorView.createDrawingLayer();
drawingLayer.onSelectionChanged = (selected, deselected) => {
    //Do something based on the selection change.
}
```
