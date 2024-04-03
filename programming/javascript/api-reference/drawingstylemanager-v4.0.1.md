---
layout: default-layout
title: DrawingStyleManager APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the page for Dynamsoft Camera Enhancer JavaScript SDK DrawingStyleManager APIs.
keywords: cameraView, imageEditorView, DrawingStyleManager, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: DrawingStyleManager
---

# class DrawingStyleManager

The `DrawingStyleManager` class serves as a centralized repository and management system for `DrawingStyle` objects within an application. It is designed to streamline the process of creating, retrieving, updating, and maintaining a consistent set of drawing styles that can be applied to [DrawingItem](./drawingitem.md) objects. 

| Name                                                 | Description                                                     |
| ---------------------------------------------------- | --------------------------------------------------------------- |
| `static` [createDrawingStyle()](#createdrawingstyle) | Generates a new `DrawingStyle` object, providing its unique ID. |
| `static` [getDrawingStyle()](#getdrawingstyle)       | Retrieves a specific `DrawingStyle` object using its ID.        |
| `static` [getDrawingStyles()](#getdrawingstyles)     | Fetches a collection of all available `DrawingStyle` objects.   |
| `static` [updateDrawingStyle()](#updatedrawingstyle) | Modifies an identified `DrawingStyle` object by its ID.         |

## createDrawingStyle

Generates a new `DrawingStyle` object, providing its unique ID. The ID starts from 1024 and increases in a sequential order.

```typescript
static createDrawingStyle(styleDefinition: DrawingStyle): number; 
```

**Parameters**

`styleDefinition`: the properties and values defining the drawing style.

**Return value**

The unique ID of the newly created DrawingStyle object.

**Code Snippet**

```javascript
let styleID = Dynamsoft.DCE.DrawingStyleManager.createDrawingStyle({
    lineWidth: 4,
    fillStyle: " rgba(73, 173, 245, 0.8)",
    strokeStyle: " rgba(73, 173, 245, 1)",
    paintMode: "fill",
    fontSize: 50,
    fontFamily: "sans-serif"
});
```

**See also**

[DrawingStyle](interface/drawingstyle.md)

## getDrawingStyle

Retrieves a specific `DrawingStyle` object using its ID.

> A set of predefined `DrawingStyle` objects are included by default which are specifically designed for use with Dynamsoft products. Read more on [Predefined DrawingStyle object](#predefined-drawingstyle-object)

```typescript
static getDrawingStyle(drawingStyleId: number): DrawingStyle; 
```

**Parameters**

`drawingStyleId`: the unique ID of the `DrawingStyle` to update.

**Return value**

The `DrawingStyle` object associated with the given ID.

**Code Snippet**

```javascript
// Update `drawingStyleId` to a valid identifier available at runtime.
let drawingStyle = Dynamsoft.DCE.DrawingStyleManager.getDrawingStyle(Dynamsoft.DCE.DrawingStyleManager.STYLE_BLUE_STROKE);
```

**See also**

[DrawingStyle](interface/drawingstyle.md)

## getDrawingStyles

Fetches a collection of all available `DrawingStyle` objects.

```typescript
static getDrawingStyles(): Array<DrawingStyle>; 
```

**Return value**

An array of `DrawingStyle` objects.

**Code Snippet**

```javascript
let drawingStyles = Dynamsoft.DCE.DrawingStyleManager.getDrawingStyles();
```

**See also**

[DrawingStyle](interface/drawingstyle.md)

## updateDrawingStyle

Modifies an identified `DrawingStyle` object by its ID. You can update all properties of the `DrawingStyle` or you can update just a few of them. Check the code snippets for more information.

> Modifications are immediately effective for drawing items that are added to the layer moving forward. Additionally, existing items on the layer will be updated upon the addition of a new item. To apply updates to all existing items without the necessity of adding a new one, it's recommended to use the `renderAll()` method of the `DrawingLayer` object.

```typescript
static updateDrawingStyle(drawingStyleId: number, styleDefinition: DrawingStyle): void; 
```

**Parameters**

`drawingStyleId`: the unique ID of the `DrawingStyle` to update.

`styleDefinition`: the new properties and values to update the drawing style with.

**Code Snippet**

```javascript
// Change the whole style
Dynamsoft.DCE.DrawingStyleManager.updateDrawingStyle(Dynamsoft.DCE.DrawingStyleManager.STYLE_GREEN_STROKE, {
    fillStyle: "rgba(100, 75, 245, 0.3)",
    fontFamily: "sans-serif",
    fontSize: 25,
    lineWidth: 2,
    paintMode: "strokeAndFill",
    strokeStyle: "rgba(73, 173, 245, 1)"
});
// Only change the fontSize
Dynamsoft.DCE.DrawingStyleManager.updateDrawingStyle(Dynamsoft.DCE.DrawingStyleManager.STYLE_GREEN_STROKE, {
    fontSize: 30
});
```

**See also**

[DrawingStyle](interface/drawingstyle.md)

[renderAll()](drawinglayer.md#renderall)

**Special Notice**

If you are using **Dynamsoft Camera Enhancer** with **Dynamsoft Barcode Reader**, **Dynamsoft Label Recognizer** or **Dynamsoft Document Normalizer**, you can use `updateDrawingStyle()` to update their dedicated styles. These products use the styles of the following IDs:

| SDK Name                      | Style IDs                                        |
| ----------------------------- | ------------------------------------------------ |
| Dynamsoft Document Normalizer | 1 (*default*), 5 (*selected*), 9 (*unverified*)  |
| Dynamsoft Label Recognizer    | 2 (*default*), 6 (*selected*), 10 (*unverified*) |
| Dynamsoft Barcode Reader      | 3 (*default*), 7 (*selected*), 11 (*unverified*) |

You can update these styles to apply changes to the `DrawingLayers` used by these products. For example, the following code changes the style for highlighting found barcodes:

```javascript
Dynamsoft.DCE.DrawingStyleManager.updateDrawingStyle(Dynamsoft.DCE.DrawingStyleManager.STYLE_ORANGE_STROKE, {
    fillStyle: "rgba(100, 75, 245, 0.3)",
    lineWidth: 5,
    paintMode: "strokeAndFill",
    strokeStyle: "rgba(73, 173, 245, 1)"
});
```

## Predefined DrawingStyle object

Dynamsoft Camera Enhancer includes a set of predefined `DrawingStyle` objects specifically designed for use with Dynamsoft products.

For more details, check out [Built-in DrawingStyles](./interface/drawingstyle.md#built-in-drawingstyles)

> DDN: Dynamsoft Document Normalizer
> DBR: Dynamsoft Barcode Reader
> DLR: Dynamsoft Label Recognizer

| Style Name                      | Style ID | Description                                                                    |
| ------------------------------- | -------- | ------------------------------------------------------------------------------ |
| STYLE_BLUE_STROKE               | 1        | Used by DDN for drawing found document boundaries.                             |
| STYLE_GREEN_STROKE              | 2        | Used by DLR for highlighting found text lines.                                 |
| STYLE_ORANGE_STROKE             | 3        | Used by DBR for highlighting found barcode symbols.                            |
| STYLE_YELLOW_STROKE             | 4        | Used as the default style for user-defined drawing layers.                     |
| STYLE_BLUE_STROKE_FILL          | 5        | Used by DDN for drawing selected document boundaries.                          |
| STYLE_GREEN_STROKE_FILL         | 6        | Used by DLR for highlighting selected text lines.                              |
| STYLE_ORANGE_STROKE_FILL        | 7        | Used by DBR for highlighting selected barcode symbols.                         |
| STYLE_YELLOW_STROKE_FILL        | 8        | Used as the style for selected drawing items on user-defined drawing layers.   |
| STYLE_BLUE_STROKE_TRANSPARENT   | 9        | Used by DDN for drawing found document boundaries that haven't been verified.  |
| STYLE_GREEN_STROKE_TRANSPARENT  | 10       | Used by DLR for highlighting found text lines that haven't been verified.      |
| STYLE_ORANGE_STROKE_TRANSPARENT | 11       | Used by DBR for highlighting found barcode symbols that haven't been verified. |

**Code Snippet**

```javascript
let style = Dynamsoft.DCE.DrawingStyleManager.getDrawingStyle(Dynamsoft.DCE.DrawingStyleManager.STYLE_GREEN_STROKE);
style.lineWidth = 3;
// Update the style
Dynamsoft.DCE.DrawingStyleManager.updateDrawingStyle(Dynamsoft.DCE.DrawingStyleManager.STYLE_GREEN_STROKE, style);
```
