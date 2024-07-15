---
layout: default-layout
title: ImageDrawingItem - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the ImageDrawingItem definitions of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: camera enhancer, imagedrawingitem, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: ImageDrawingItem
---

# Class ImageDrawingItem

The `ImageDrawingItem` class extends the functionality of the `DrawingItem` class and is specifically tailored to handle image-related drawing operations.

| Name                                                  | Description                                                                        |
| ----------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `constructor` [ImageDrawingItem()](#imagedrawingitem) | Constructor for the class.                                                         |
| [maintainAspectRatio](#maintainaspectratio)           | Determines whether the image's aspect ratio should be maintained when it is drawn. |
| [getImage()](#getimage)                               | Retrieves the current image being used for drawing.                                |
| [setImage()](#setimage)                               | Sets the image to be used for drawing.                                             |
| [getImageRect()](#getimagerect)                       | Returns the rectangle area within which the image is drawn.                        |
| [setImageRect()](#setimagerect)                       | Sets the rectangle area within which the image should be drawn.                    |

## ImageDrawingItem

Constructor for the class.

```typescript
constructor(
    image: DSImageData | HTMLImageElement | HTMLCanvasElement | HTMLVideoElement,
    rect: Rect,
    maintainAspectRatio: boolean,
    drawingStyleId?: number
)
```

**Parameters**

`image`: the image to be drawn, which can be one of several types, including `DSImageData` or standard HTML elements for images, canvas, or video.

`rect`: defines the rectangle area within which the image will be drawn.

`maintainAspectRatio`: determines whether the image's aspect ratio should be maintained when it is drawn. If true, the height in `rect` may be adjusted to preserve the image's aspect ratio.

`drawingStyleId`: [Optional] the unique ID of the `DrawingStyle` to apply to this `DrawingItem`.

**Code Snippet**

```html
<div style="display:none;">
  <img id="source" src="path-to-source-image.jpg" width="300" height="227" />
</div>
```

```js
let cameraView = cameraEnhancer.getCameraView();
let drawingLayer = cameraView.createDrawingLayer();
const image = document.getElementById("source");
let imgItem = new Dynamsoft.ImageDrawingItem(
    image, 
    {
        x: 50, 
        y: 50, 
        width: 640, 
        height: 360, 
        isMeasuredInPercentage: false
    }, 
    true,
    3
);
drawingLayer.addDrawingItem(imgItem);
```

**See also**

[DSImageData](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/ds-image-data.html)

[Rect](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/rect.html)

## maintainAspectRatio

Determines whether the image's aspect ratio should be maintained when it is drawn.

> Invoke `renderAll()` for the change to take effect if the `DrawingItem` has already been added to a `DrawingLayer`. 

```typescript
maintainAspectRatio: boolean;
```

**Code Snippet**

```js
imgItem.maintainAspectRatio = true;
drawingLayer.renderAll();
```

## getImage

Retrieves the current image being used for drawing. The return type can be any of the specified types, depending on what was set.

```typescript
getImage(): DSImageData | HTMLImageElement | HTMLCanvasElement | HTMLVideoElement;
```

**Parameters**

None.

**Return Value**

The current image being used for drawing.

**Code Snippet**

```js
imgItem.getImage();
```

## setImage

Sets the image to be used for drawing. This method allows changing the image after the object has been instantiated.

> Invoke `renderAll()` for the change to take effect if the `DrawingItem` has already been added to a `DrawingLayer`. 

```typescript
setImage(image: DSImageData | HTMLImageElement | HTMLCanvasElement | HTMLVideoElement): void;
```

**Parameters**

`image`: the image to be drawn, which can be one of several types, including `DSImageData` or standard HTML elements for images, canvas, or video.

**Return Value**

None.

**Code Snippet**

```js
imgItem.setImage(/*A-New-Image*/);
```

**See also**

[DSImageData](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/ds-image-data.html)

## getImageRect

Returns the rectangle area within which the image is drawn.

```typescript
getImageRect(): Rect;
```

**Parameters**

None.

**Return Value**

The rectangle area within which the image is drawn.

**Code Snippet**

```js
imgItem.getImageRect();
```

## setImageRect

Sets the rectangle area within which the image should be drawn. This method allows for the adjustment of position and size of the image.

> The change takes effect right away.

```typescript
setImageRect(rect: Rect): void;
```

**Parameters**

`rect`: defines the rectangle area within which the image should be drawn.

**Return Value**

None.

**Code Snippet**

```js
imgItem.setImageRect(
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
