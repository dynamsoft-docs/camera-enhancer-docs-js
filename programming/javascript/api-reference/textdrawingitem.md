---
layout: default-layout
title: TextDrawingItem - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the TextDrawingItem definitions of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: camera enhancer, textdrawingitem, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: TextDrawingItem
permalink: /programming/javascript/api-reference/textdrawingitem.html
---

# Class TextDrawingItem

The `TextDrawingItem` class extends the functionality of the `DrawingItem` class and is specifically tailored to handle text-related drawing operations.

| Name                                                | Description                                                    |
| --------------------------------------------------- | -------------------------------------------------------------- |
| `constructor` [TextDrawingItem()](#textdrawingitem) | Constructor for the class.                                     |
| [getText()](#gettext)                               | Retrieves the current text being used for drawing.             |
| [setText()](#settext)                               | Sets the text to be used for drawing.                          |
| [getTextRect()](#gettextrect)                       | Returns the rectangle area within which the text is drawn.     |
| [setTextRect()](#settextrect)                       | Sets the rectangle area within which the text should be drawn. |

## TextDrawingItem

Constructor for the class.

```typescript
constructor(
    text: string,
    rect: Rect,
    drawingStyleId?: number
)
```

**Parameters**

`text`: the text to be drawn.

`rect`: defines the rectangle area within which the text will be drawn.

`drawingStyleId`: [Optional] the unique ID of the `DrawingStyle` to apply to this `DrawingItem`.

**Code Snippet**

```js
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.createDrawingLayer();
let textItem = new Dynamsoft.DCE.DrawingItem.TextDrawingItem(
    "Hello World", 
    {
        x: 100, 
        y: 200, 
        width: 640, 
        height: 360, 
        isMeasuredInPercentage: false
    },
    3
);
drawingLayer.addDrawingItem(textItem);
```

**See also**

[Rect](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/rect.html)

## getText

Retrieves the current text being used for drawing.

```typescript
getText(): string;
```

**Parameters**

None.

**Return Value**

The current text being used for drawing.

**Code Snippet**

```js
textItem.getText();
```

## setText

Sets the text to be used for drawing. This method allows changing the text after the object has been instantiated.

> Invoke `renderAll()` for the change to take effect if the `DrawingItem` has already been added to a `DrawingLayer`. 

```typescript
setText(text: string): void;
```

**Parameters**

`text`: the text to be drawn.

**Return Value**

None.

**Code Snippet**

```js
textItem.setText(/*A-New-Text*/);
```

## getTextRect

Returns the rectangle area within which the text is drawn.

```typescript
getTextRect(): Rect;
```

**Parameters**

None.

**Return Value**

The rectangle area within which the text is drawn.

**Code Snippet**

```js
textItem.getTextRect();
```

## setTextRect

Sets the rectangle area within which the text should be drawn. This method allows for the adjustment of position and size of the text.

> The change takes effect right away.

```typescript
setTextRect(rect: Rect): void;
```

**Parameters**

`rect`: defines the rectangle area within which the text should be drawn.

**Return Value**

None.

**Code Snippet**

```js
textItem.setTextRect(
    {
        height: 100, 
        width:300,
        x: 200,
        y :200
    }
);
```

**See Also**

[Rect](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/rect.html)
