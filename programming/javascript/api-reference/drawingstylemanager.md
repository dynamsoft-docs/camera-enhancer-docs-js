---
layout: default-layout
title: DrawingStyleManager APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the page for Dynamsoft Camera Enhancer JavaScript SDK DrawingStyleManager APIs.
keywords: cameraView, imageEditorView, DrawingStyleManager, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: DrawingStyleManager
permalink: /programming/javascript/api-reference/drawingstylemanager.html
---

# class DrawingStyleManager

| API Name                                                                     | Description                                             |
| ---------------------------------------------------------------------------- | ------------------------------------------------------- |
| `static` [createDrawingStyle()](drawingstylemanager.md#createdrawingstyle)   | Creates a new `DrawingStyle` object and returns its ID. |
| `static` [getDrawingStyle()](drawingstylemanager.md#getdrawingstyle)         | Returns the `DrawingStyle` object specified by its Id.  |
| `static` [getAllDrawingStyles()](drawingstylemanager.md#getalldrawingstyles) | Returns all `DrawingStyle` objects.                     |
| `static` [updateDrawingStyle()](drawingstylemanager.md#updatedrawingstyle)   | Updates an existing `DrawingStyle` specified by its ID. |

## createDrawingStyle

Creates a new `DrawingStyle` object and returns its ID.

```typescript
static createDrawingStyle(styleDefinition: DrawingStyle): number; 
```

**Parameters**

`styleDefinition` : defines a `DrawingStyle` object. The following are all the allowed properties and their default values. All of them are optional, if a property is not included in the definition, it uses the default value.

The default values are:

* lineWidth: `1.0`
* fillStyle: `rgba(245, 236, 73, 0.3)`
* strokeStyle: `rgba(245, 236, 73, 1)`
* paintMode: `stroke`
* fontSize: `10`
* fontFamily: `sans-serif`

**Return value**

The id of the created `DrawingStyle` .

**Code Snippet**

```javascript
let styleID = Dynamsoft.DCE.DrawingStyleManager.createDrawingStyle({
    lineWidth: 1.0,
    fillStyle: " rgba(73, 173, 245, 0.8)",
    strokeStyle: " rgba(73, 173, 245, 1)",
    paintMode: "fill",
    fontSize: 100,
    fontFamily: "sans-serif"
});
```

**See also**

* [DrawingStyle](interface/drawingstyle.md)

## getDrawingStyle

Returns the `DrawingStyle` object specified by its Id.

> The SDK comes with 8 default styles with the IDs 1 ~ 8, check [DrawingStyle](interface/drawingstyle.md) for more information.

```typescript
static getDrawingStyle(styleId: number): DrawingStyle; 
```

**Parameters**

`styleId` : specifies a `DrawingStyle` .

**Return value**

The `DrawingStyle` specified by the input id.

**Code Snippet**

```javascript
// Change `styleId` to one that you know exists at runtime. 
let drawingStyle = Dynamsoft.DCE.DrawingStyleManager.getDrawingStyle(100);
```

**See also**

* [DrawingStyle](interface/drawingstyle.md)

## getAllDrawingStyles

Returns all `DrawingStyle` objects.

```typescript
static getAllDrawingStyles(): Array<DrawingStyle>; 
```

**Return value**

The array of all of the `DrawingStyle` objects of current `CameraEnhancer` .

**Code Snippet**

```javascript
let drawingStyles = Dynamsoft.DCE.DrawingStyleManager.getAllDrawingStyles();
```

**See also**

* [DrawingStyle](interface/drawingstyle.md)

## updateDrawingStyle

Updates an existing `DrawingStyle` specified by its ID. You can update all properties of the `DrawingStyle` or you can update just a few of them. Check the code snippet for more information.

> The update takes effect immediately.

```typescript
static updateDrawingStyle(styleId: number, styleDefinition: DrawingStyle): void; 
```

**Parameters**

`styleId` : specifies a `DrawingStyle` which needs to be updated.  
`styleDefinition` : Defines a new `DrawingStyle` object.

**Code Snippet**

```javascript
// Change the whole style
Dynamsoft.DCE.DrawingStyleManager.updateDrawingStyle(100, {
    fillStyle: "rgba(100, 75, 245, 0.3)",
    fontFamily: "sans-serif",
    fontSize: 25,
    lineWidth: 2,
    paintMode: "strokeAndFill",
    strokeStyle: "rgba(73, 173, 245, 1)"
});
// Only change the fontSize
Dynamsoft.DCE.DrawingStyleManager.updateDrawingStyle(100, {
    fontSize: 30
});
```

**See also**

* [DrawingStyle](interface/drawingstyle.md)

**Special Notice**

If you are using **Dynamsoft Camera Enhancer** with **Dynamsoft Barcode Reader**, **Dynamsoft Label Recognizer** or **Dynamsoft Document Normalizer**, you can use `updateDrawingStyle()` to update their dedicated styles. These SDKs use the styles of the following IDs:

| SDK Name                      | Style IDs                     |
| ----------------------------- | ----------------------------- |
| Dynamsoft Document Normalizer | 1 (*default*), 5 (*selected*) |
| Dynamsoft Label Recognizer    | 2 (*default*), 6 (*selected*) |
| Dynamsoft Barcode Reader      | 3 (*default*), 7 (*selected*) |

You can update these styles to apply changes to the DrawingLayers used by these products. For example, the following code changes the style for highlighting found barcodes:

```javascript
Dynamsoft.DCE.DrawingStyleManager.updateDrawingStyle(3, {
    fillStyle: "rgba(100, 75, 245, 0.3)",
    lineWidth: 5,
    paintMode: "strokeAndFill",
    strokeStyle: "rgba(73, 173, 245, 1)"
});
```
