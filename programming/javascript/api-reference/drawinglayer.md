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

| API Name                                                   | Description                                                                                                      |
| ---------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| [getId()](drawinglayer.md#getid)                           | Returns the ID of the `DrawingLayer`.                                                                            |
| [addDrawingItems()](drawinglayer.md#adddrawingitems)       | Adds `DrawingItems` to the `DrawingLayer`.                                                                       |
| [getDrawingItems()](drawinglayer.md#getdrawingitems)       | Returns all `DrawingItems` or just some of them based on a filter function.                                      |
| [setDrawingItems()](drawinglayer.md#setdrawingitems)       | Replaces all `DrawingItems` of the DrawingLayer with new ones.                                                   |
| [hasDrawingItem()](drawinglayer.md#hasDrawingItem)         | Checks out if a `DrawingItem` belongs to the layer.                                                              |
| [removeDrawingItems()](drawinglayer.md#removedrawingitems) | Removes `DrawingItems` from the DrawingLayer.                                                                    |
| [clearDrawingItems()](drawinglayer.md#cleardrawingitems)   | Removes all `DrawingItems` from the DrawingLayer.                                                                |
| [renderAll()](drawinglayer.md#renderall)                   | Renders all `DrawingItems`, usually required when the style for one or more items is changed.                    |
| [setDefaultStyle()](drawinglayer.md#setdefaultstyle)       | Sets the style for `DrawingItems` on the layer.                                                                  |
| [setVisible()](drawinglayer.md#setvisible)                 | Shows or hides the `DrawingLayer`.                                                                               |
| [isVisible()](drawinglayer.md#isvisible)                   | Returns whether the `DrawingLayer` is visible.                                                                   |
| [onSelectionChanged()](drawinglayer.md#onselectionchanged) | An event handler that is triggered when different `DrawingItems` gets selected/deselected on the `DrawingLayer`. |

**Special Notice**

If you are using **Dynamsoft Camera Enhancer** with **Dynamsoft Barcode Reader**, **Dynamsoft Label Recognizer** or **Dynamsoft Document Normalizer**, note that there are dedicated DrawingLayers for them as shown below:

| SDK Name                      | DrawingLayer ID |
| ----------------------------- | --------------- |
| Dynamsoft Document Normalizer | 1               |
| Dynamsoft Barcode Reader      | 2               |
| Dynamsoft Label Recognizer    | 3               |

You can manipulate these DrawingLayers directly, for example, the following code applies a different DrawingStyle to the DrawingLayer used by **Dynamsoft Label Recognizer**:

> Alternatively, you can directly change the style already in use instead of replacing it with a new one. Learn more at [updateDrawingStyle](ui.md#updatedrawingstyle).

```javascript
// Gets the DrawingLayer used by the Dynamsoft Label Recognizer instance to which cameraEnhancer is bound.
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
dlrDrawingLayer.setDefaultStyle(newStyleId)
```

## getId

Returns the Id of the `DrawingLayer`.

```typescript
getId(): number;
```

**Code Snippet**

```javascript
let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
let drawingLayer = cameraEnhancer.createDrawingLayer();
let drawingLayerId = drawingLayer.getId();
```

## addDrawingItems

Adds `DrawingItems` to the `DrawingLayer`.

```typescript
addDrawingItems(drawingItems: Array<DrawingItem>): void;
```

**Code Snippet**

```javascript
let drawingItems = new Array(
    new RectDrawingItem({
        x: 10,
        y: 10,
        width: 100,
        height: 100,
        isMeasuredInPercentage: true
    }),
    new TextDrawingItem("label 1", {
        x: 10,
        y: 10,
        width: 100,
        height: 20,
        isMeasuredInPercentage: true
    }),
    new LineDrawingItem({
        startPoint:{
            x: 10,
            y: 50
        },
        endPoint: {
            x: 90,
            y: 50
        }
    }));
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.getDrawingLayer(100);
drawingLayer.addDrawingItems(drawingItems);
```

**See also**

* [DrawingItem](drawingitem.md)

## getDrawingItems

Returns all `DrawingItems` or just some of them based on a filter function.

```typescript
getDrawingItems(filter?: (item: DrawingItem) => boolean): Array<DrawingItem>;
```

**Parameters**

`filter` : specifies a function which checks each DrawingItem to determine whether it should be returned.

**Code Snippet**

```javascript
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.getDrawingLayer(100);
// Return only DrawingItems belong to the type DT_Rect.
let drawingItems = drawingLayer.getDrawingItems(item => item.mediaType === EnumDrawingItemMediaType.DIMT_RECTANGLE);
```

**See also**

* [DrawingItem](drawingitem.md)

## setDrawingItems

Replaces all `DrawingItems` of the DrawingLayer with new ones.

```typescript
setDrawingItems(drawingItems: Array<DrawingItem>): void;
```

**Code Snippet**

```javascript
let drawingItems = new Array(
    new RectDrawingItem({
        x: 10,
        y: 10,
        width: 100,
        height: 100,
        isMeasuredInPercentage: true
    }),
    new TextDrawingItem("label 1", {
        x: 10,
        y: 10,
        width: 100,
        height: 20,
        isMeasuredInPercentage: true
    }),
    new LineDrawingItem({
        startPoint:{
            x: 10,
            y: 50
        },
        endPoint: {
            x: 90,
            y: 50
        }
    }));
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.getDrawingLayer(100);
drawingLayer.setDrawingItems(newDrawingItems);
```

**See also**

* [DrawingItem](drawingitem.md)

## hasDrawingItem

Checks out if a `DrawingItem` belongs to the layer.

```typescript
hasDrawingItem(drawingItem: DrawingItem): Boolean;
```

**Code Snippet**

```javascript
let drawingItem = new RectDrawingItem({
        x: 10,
        y: 10,
        width: 100,
        height: 100,
        isMeasuredInPercentage: true
    });
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.getDrawingLayer(100);
let hasDrawingItem = drawingLayer.hasDrawingItem(drawingItem);
```

**See also**

* [DrawingItem](drawingitem.md)

## removeDrawingItems

Removes `DrawingItems` from the DrawingLayer.   

```typescript
removeDrawingItems(drawingItems: Array<DrawingItem>): void;
```

**Code Snippet**

```javascript
let drawingItems = new Array(
    new RectDrawingItem({
        x: 10,
        y: 10,
        width: 100,
        height: 100,
        isMeasuredInPercentage: true
    }),
    new TextDrawingItem("label 1", {
        x: 10,
        y: 10,
        width: 100,
        height: 20,
        isMeasuredInPercentage: true
    })
);
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.getDrawingLayer(100);
drawingLayer.removeDrawingItems(drawingItems);
```

**See also**

* [DrawingItem](drawingitem.md)

## clearDrawingItems

Removes all `DrawingItems` from the DrawingLayer.

```typescript
clearDrawingItems(): void;
```

**Code Snippet**

```javascript
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.getDrawingLayer(100);
drawingLayer.clearDrawingItems();
```

## renderAll

Renders all `DrawingItems` , usually required when

* One or multiple `DrawingItems` have altered their `DrawingStyle` IDs; 
* One or multiple `DrawingItems` have changed their properties such as the coordinates for the top-left corner of a `RectDrawingItem` item.

```typescript
renderAll(): boolean;
```

**Code Snippet**

```javascript
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.getDrawingLayer(100);
drawingLayer.getDrawingItems()[0].styleId = customId;
let isRenderedAll = drawingLayer.renderAll();
```

## setDefaultStyle

Sets the style for `DrawingItems` on the `DrawingLayer`

* If both "state" and "mediaType" are ignored, the style will apply to all `DrawingItems`;
* If only "state" is specified, all `DrawingItem` with the specified state will use this default style.;
* If "state" and "mediaType" are both specified, the style will only apply to `DrawingItems` of that "mediaType" in that "state".

```typescript
setDefaultStyle(drawingStyleId: number, state?: EnumDrawingItemState, mediaType?: EnumDrawingItemMediaType): void;
```

**Parameters**

`drawingStyleId`: specifies a style by its ID.  
`state`(Optional): specifies a state.  
`mediaType`(Optional): specifies a mediaType.

**Code Snippet**

```javascript
//set style 1 for all the DrawingItems on the `DrawingLayer`
drawingLayer.setDefaultStyle(1);
//set style 1 for all selected DrawingItems on the `DrawingLayer`
drawingLayer.setDefaultStyle(1, EnumDrawingItemState.DIS_SELECTED);
//set style 1 for all selected RectDrawingItems on the `DrawingLayer`
drawingLayer.setDefaultStyle(1, EnumDrawingItemState.DIS_SELECTED, EnumDrawingItemMediaType.DIMT_RECTANGLE);
```

**See also**

* [DrawingStyle](interface/drawingstyle.md)
* [EnumDrawingItemState](enum/enumdrawingitemstate.md)
* [EnumDrawingItemMediaType](enum/enumdrawingitemmediatype.md)

## setVisible

Shows or hides the `DrawingLayer` .

```typescript
setVisible(visibility: boolean): void;
```

**Parameters**

`visibility` : set true to show and false to hide the `DrawingLayer` .

**Code Snippet**

```javascript
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.getDrawingLayer(100);
drawingLayer.setVisible(false);
```

## isVisible

Returns whether the `DrawingLayer` is visible.

```typescript
isVisible(): boolean;
```

**Code Snippet**

```javascript
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.getDrawingLayer(100);
let isVisible = drawingLayer.isVisible();
```

## onSelectionChanged

An event handler that is triggered when different `DrawingItems` gets selected/deselected on the `DrawingLayer`.

```typescript
onSelectionChanged(selectedDrawingItems: Array<DrawingItem>, deselectedDrawingItems: Array<DrawingItem>): void;
```

**Parameters**

`selectedDrawingItems` : specifies the selected `DrawingItem` objects.  
`deselectedDrawingItems` : specifies the deselected `DrawingItem` objects.

**Code Snippet**

```javascript
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.getDrawingLayer(100);
drawingLayer.onSelectionChanged = (selected, deselected) => {
    //do ...
}
```