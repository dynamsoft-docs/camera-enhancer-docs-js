---
layout: default-layout
title: Interface DrawingLayer - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the DrawingLayer Interface of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: DrawingLayer, CameraEnhancer, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: DrawingLayer
permalink: /programming/javascript/api-reference/drawinglayer-v3.3.10.html
---

# DrawingLayer

| Name| Description |
|---|---|
| [getId()](#getid) | Returns the ID of the DrawingLayer. |
| [addDrawingItems()](#adddrawingitems) | Adds DrawingItem(s) to the DrawingLayer. |
| [getDrawingItems()](#getdrawingitems) | Returns all DrawingItem(s) of the DrawingLayer. |
| [setDrawingItems()](#setdrawingitems) | Replaces all DrawingItem(s) of the DrawingLayer with new ones. |
| [hasDrawingItem()](#hasdrawingitem) | Checks out if a DrawingItem belongs to the layer. |
| [removeDrawingItems()](#removedrawingitems) | Removes DrawingItem(s) from the DrawingLayer. |
| [clearDrawingItems()](#cleardrawingitems) | Removes all DrawingItem(s) from the DrawingLayer. |
| [setDrawingStyle()](#setdrawingstyle) | Sets the style for the DrawingLayer or for a particular mediaType or for a particular mediaType in a particular state. |
| [setVisible()](#setvisible) | Shows or hides the DrawingLayer. |
| [isVisible()](#isvisible) | Returns whether the DrawingLayer is visible. |
| [renderAll()](#renderall) | Renders all DrawingItems, usually required when the style for one or more items is changed. |
| [onSelectionChange()](#onselectionchange) | An event handler that is triggered when different DrawingItem(s) gets selected/deselected on the DrawingLayer. |
| [setMode()](#setmode) | Changes the mode of the layer. |
| [getMode()](#getmode) | Returns the current mode. |

**Special Notice**

If you are using **Dynamsoft Camera Enhancer** with **Dynamsoft Barcode Reader**, **Dynamsoft Label Recognizer** or **Dynamsoft Document Normalizer**, note that there are dedicated DrawingLayers for them as shown below:

| SDK Name | DrawingLayer ID |
|--|--|
|Dynamsoft Document Normalizer | 1 |
|Dynamsoft Label Recognizer | 2 |
|Dynamsoft Barcode Reader| 3 |

You can manipulate these DrawingLayers directly, for example, the following code applies a different DrawingStyle to the DrawingLayer used by **Dynamsoft Label Recognizer**:

> Alternatively, you can directly change the style already in use instead of replacing it with a new one. Learn more at [updateDrawingStyle](ui.html#updatedrawingstyle).

```javascript
// Gets the DrawingLayer used by the Dynamsoft Label Recognizer instance to which enhancer is bound.
let dlrDrawingLayer = enhancer.getDrawingLayer(2);
// Creates a new style to be used.
let newStyleId = enhancer.createDrawingStyle({
    fillStyle: "rgba(100, 75, 245, 0.3)",
    lineWidth: 5,
    paintMode: "strokeAndFill",
    strokeStyle: "rgba(73, 173, 245, 1)"
});
// Replaces the old style with the new one.
dlrDrawingLayer.setDrawingStyle(newStyleId)
```

## getId

Returns the Id of the `DrawingLayer` .

```typescript
getId(): number;
```

**Code Snippet**

```javascript
let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
let drawingLayer = enhancer.createDrawingLayer();
let drawingLayerId = drawingLayer.getId();
```

## addDrawingItems

Adds `DrawingItem` (s) to the `DrawingLayer` .

```typescript
addDrawingItems(drawingItems: Array<DrawingItem>): void;
```

**Code Snippet**

```javascript
let drawingItems = new Array(
    new DT_Rect(10, 10, 100, 100, 1),
    new DT_Text("label 1", 40, 40, 2),
    new DT_Line({
        x: 10,
        y: 50
    }, {
        x: 90,
        y: 50
    }, 3)
)
let drawingLayer = enhancer.getDrawingLayer(100);
drawingLayer.addDrawingItems(drawingItems);
```

**See also**

[DrawingItem](drawingitem.html)

## getDrawingItems

Returns all `DrawingItem` (s) of the `DrawingLayer` .

```typescript
getDrawingItems() :Array<DrawingItem>);
```

**Code Snippet**

```javascript
let drawingLayer = enhancer.getDrawingLayer(100);
let drawingItems = drawingLayer.getDrawingItems();
```

**See also**

[DrawingItem](drawingitem.html)

## setDrawingItems

Replaces all `DrawingItem` (s) of the `DrawingLayer` with new ones.

```typescript
setDrawingItems(drawingItems: Array<DrawingItem>): void;
```

**Code Snippet**

```javascript
let newDrawingItems = new Array(
    new DT_Rect(10, 10, 100, 100, 1),
    new DT_Text("label 1", 40, 40, 2),
    new DT_Line({
        x: 10,
        y: 50
    }, {
        x: 90,
        y: 50
    }, 3)
)
let drawingLayer = enhancer.getDrawingLayer(100);
drawingLayer.setDrawingItems(newDrawingItems);
```

**See also**

[DrawingItem](drawingitem.html)

## hasDrawingItem

Checks out if a `DrawingItem` belongs to the layer.

```typescript
hasDrawingItem(drawingItem: DrawingItem): Boolean;
```

**Code Snippet**

```javascript
let drawingItem = new DT_Rect(10, 10, 100, 100, 1);
let drawingLayer = enhancer.getDrawingLayer(100);
let hasDrawingItem = drawingLayer.hasDrawingItem(drawingItem);
```

**See also**

[DrawingItem](drawingitem.html)

## removeDrawingItems

Removes specific `DrawingItem` (s) from the `DrawingLayer` .

```typescript
removeDrawingItems(drawingItems: Array<DrawingItem>): void;
```

**Code Snippet**

```javascript
let drawingItems = new Array(
    new DT_Rect(10, 10, 100, 100, 1),
    new DT_Text("label 1", 40, 40, 2)
)
let drawingLayer = enhancer.getDrawingLayer(100);
drawingLayer.removeDrawingItems(drawingItems);
```

**See also**

[DrawingItem](drawingitem.html)

## clearDrawingItems

Removes all `DrawingItem` (s) from the `DrawingLayer` .

```typescript
clearDrawingItems(): void;
```

**Code Snippet**

```javascript
let drawingLayer = enhancer.getDrawingLayer(100);
drawingLayer.clearDrawingItems();
```

## setDrawingStyle

Sets the style for `DrawingItems` on the `DrawingLayer`

* If both "mediaType" and "styleSelector" are ignored, the style will apply to all `DrawingItems`; 
* If "mediaType" is specified, the style will only apply to `DrawingItems` of that "mediaType"; 
* If "mediaType" is "all" and "styleSelector" is specified, the style will apply to all types of `DrawingItems` which  have the specified "styleSelector"; 
* If both "mediaType" and "styleSelector" are specified, the style only applies to `DrawingItems` of the specified "mediaType" which have the specified "styleSelector".

```typescript
setDrawingStyle(styleId: number, mediaType?: string, styleSelector?: string): void;
```

**Parameters**

`styleId`: specifies a style by its ID.

`mediaType`: specifies a mediaType, allowed values are "rect", "arc", "line", "polygon", "text", "image" and "all".

`styleSelector`: specifies a selector, allowed values are "default", "selected" and "all".

**Code Snippet**

```javascript
//set style 1 for all the DrawingItems on the `DrawingLayer`
drawingLayer.setDrawingStyle(1);
//set style 1 for all Rect-shape DrawingItems on the `DrawingLayer`
drawingLayer.setDrawingStyle(1, "rect");
//set style 1 for all selected DrawingItems on the `DrawingLayer`
drawingLayer.setDrawingStyle(1, "all", "selected");
//set style 1 for all Rect-shape and selected DrawingItems on the `DrawingLayer`
drawingLayer.setDrawingStyle(1, "rect", "selected");
```

**See also**

[DrawingStyle](interface/drawingstyle.html)

## setVisible

Shows or hides the `DrawingLayer` .

```typescript
setVisible(visibility: boolean): void;
```

**Parameters**

`visibility`: Specifies true to show and false to hide the `DrawingLayer` .

**Code Snippet**

```javascript
let drawingLayer = enhancer.getDrawingLayer(100);
drawingLayer.setVisible(false);
```

## isVisible

Returns whether the `DrawingLayer` is visible.

```typescript
isVisible(): boolean;
```

**Code Snippet**

```javascript
let drawingLayer = enhancer.getDrawingLayer(100);
let isVisible = drawingLayer.isVisible();
```

## renderAll

Renders all `DrawingItems` , usually required when

* One or multiple `DrawingItems` have altered their `DrawingStyle` IDs; 
* One or multiple `DrawingItems` have changed their properties such as the coordinates for the top-left corner of a `DT_Rect` item.

```typescript
renderAll(): boolean;
```

**Code Snippet**

```javascript
let drawingLayer = enhancer.getDrawingLayer(100);
drawingLayer.getDrawingItems()[0].styleId = customId;
drawingLayer.getDrawingItems()[0].set("x", 100);
let isRenderedAll = drawingLayer.renderAll();
```

## onSelectionChange

An event handler that is triggered when different `DrawingItem` (s) gets selected/deselected on the `DrawingLayer` .

```typescript
onSelectionChange: (selectedDrawingItems: Array<DrawingItem>, deselectedDrawingItems: Array<DrawingItem>) => void;
```

**Parameters**

`selectedDrawingItems`: specifies the selected `DrawingItem` objects.

`deselectedDrawingItems`: specifies the deselected `DrawingItem` objects.

**Code Snippet**

```javascript
let drawingLayer = enhancer.getDrawingLayer(100);
drawingLayer.onSelectionChange = (selected, deselected) => {
    //do ...
}
```

## setMode

Changes the mode of the layer.

```typescript
setMode(newMode: string): void;
```

**Parameters**

`newMode`: specifies the new mode. At present, the allowed values are "editor" and "viewer" and the default is "viewer".

> Compared with the "viewer" mode, the "editor" mode shows the "corners" and a "rotate control point" for a selected DrawingItem, which, when dragged, modify the original shape in different ways.

**Code Snippet**

```javascript
let drawingLayer = enhancer.getDrawingLayer(100);
drawingLayer.setMode("editor");
```

## getMode

Returns the current mode.  

```typescript
getMode(): "editor" | "viewer"; 
```

**Return value**

The mode of current `DrawingLayer` .

**Code Snippet**

```javascript
let drawingLayer = enhancer.getDrawingLayer(100);
let mode = drawingLayer.getMode();
```
