---
layout: default-layout
title: ImageEditorView APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the page for Dynamsoft Camera Enhancer JavaScript SDK ImageEditorView APIs.
keywords: ImageEditorView, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: ImageEditorView
permalink: /programming/javascript/api-reference/imageeditorview-v4.0.0.html
---

# ImageEditorView

### Create and Destroy Instances

| API Name                                     | Description                                                                                   |
| -------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `static` [createInstance()](#createinstance) | Creates a `ImageEditorView` instance.                                                         |
| [dispose()](#dispose)                        | Releases all resources used by the `ImageEditorView` instance.                                |
| [disposed](#disposed)                        | A readonly boolean value indicating whether the `ImageEditorView` instance has been disposed. |
| [getUIElement()](#getuielement)              | Returns the HTML element that is used by the `ImageEditorView` instance.                      |
| [setUIElement()](#setuielement)              | Specifies an HTML element for the `ImageEditorView` instance to use as its UI element.        |

### Drawing and UI

| API Name                                                                | Description                                                              |
| ----------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| [createDrawingLayer()](#createdrawinglayer)                             | Creates a DrawingLayer object and put it in an array of DrawingLayers.   |
| [getDrawingLayer()](#getdrawinglayer)                                   | Gets the DrawingLayer specified by its ID.                               |
| [getAllDrawingLayers()](#getalldrawinglayers)                           | Returns an array of all DrawingLayer objects.                            |
| [deleteUserDefinedDrawingLayer()](#deleteuserdefineddrawinglayer)       | Deletes a DrawingLayer object specified by its ID.                       |
| [clearUserDefinedDrawingLayers()](#clearuserdefineddrawinglayers)       | Removes all user-defined DrawingLayers.                                  |
| [setTipConfig()](#settipconfig)                                         | Configures the tip feature.                                              |
| [getTipConfig()](#gettipconfig)                                         | Returns the configuration of the tip.                                    |
| [setTipVisible()](#settipvisible)                                       | Sets whether to show the tip.                                            |
| [isTipVisible()](#istipvisible)                                         | Returns whether the tip is visible.                                      |
| [updateTipMessage()](#updatetipmessage)                                 | Updates the message shown in the tip.                                    |
| [getSelectedDrawingItems()](imageeditorview.md#getselecteddrawingitems) | Returns the selected DrawingItem object(s).                              |
| [setVideoFit()](imageeditorview.md#setvideofit)                         | Sets the `object-fit` CSS property of the video element.                 |
| [getVideoFit()](imageeditorview.md#getvideofit)                         | Returns the value of the `object-fit` CSS property of the video element. |
| [setOriginalImage()](imageeditorview.md#setoriginalimage)               | Sets the image to be drawn on the image editor imageeditorview.          |
| [getOriginalImage()](imageeditorview.md#setoriginalimage)               | Returns the image drawn on the image editor.                             |

## createInstance

Creates a `ImageEditorView` instance.

```typescript
static createInstance(): Promise<ImageEditorView>;
```

**Parameters**

None.

**Return value**

A promise resolving to the created `ImageEditorView` object.

**Code Snippet**

```javascript
(async () => {
    let editorView = await Dynamsoft.DCE.ImageEditorView.createInstance();
})();
```

## dispose

Releases all resources used by the `ImageEditorView` instance.

```typescript
dispose(): void;
```

**Parameters**

None.

**Return value**

None.

**Code Snippet**

```javascript
let editorView = await Dynamsoft.DCE.ImageEditorView.createInstance();
//...
editorView.dispose();
```

## disposed

A read-only Boolean value indicating whether the `ImageEditorView` instance has been disposed.

```typescript
readonly disposed: boolean; 
```

**Code Snippet**

```javascript
let editorView = await Dynamsoft.DCE.ImageEditorView.createInstance();
//...
let flag = editorView.disposed;
```

## getUIElement

Returns the HTML element that is used by the `ImageEditorView` instance.

```typescript
getUIElement(): HTMLElement; 
```

**Parameters**

None.

**Return value**

Returns an HTMLElement.

**Code Snippet**

```javascript
const uiElement = imageEditorView.getUIElement();
```

## setUIElement

Specifies an HTML element for the `ImageEditorView` instance to use as its UI element.

```typescript
setUIElement(element: HTMLDivElement): Promise<void>;
```

**Parameters**

`element`: Takes an argument element of type HTMLDivElement, which represents the new UI element to be associated with the image editor view.

**Return value**

None.

**Code Snippet**

```javascript
const containerElement1 = document.getElementById('imageEditorContainer1');
await imageEditorView.setUIElement(containerElement1);
```

## createDrawingLayer

Creates a DrawingLayer object and put it in an array of DrawingLayers.

```typescript
createDrawingLayer(): DrawingLayer;
```

**Parameters**

None.

**Return value**

Returns a DrawingLayer object.

**Code Snippet**

```javascript
const containerElement = document.getElementById('imageEditorContainer');
const imageEditorView = new ImageEditorView(containerElement);
// Create a new drawing layer and get a reference to it.
const newDrawingLayer = imageEditorView.createDrawingLayer();
```

## getDrawingLayer

Gets the DrawingLayer specified by its ID.

```typescript
getDrawingLayer(id: number): DrawingLayer;
```

**Parameters**

`id`: The ID of the layer that you want to get.

**Return value**

Returns the object of the targeting layer.

**Code Snippet**

```javascript
const containerElement = document.getElementById('imageEditorContainer');
const imageEditorView = new ImageEditorView(containerElement);
retrievedDrawingLayer = imageEditorView.getDrawingLayer(layerId);
```

## getAllDrawingLayers

Returns an array of all DrawingLayer objects.

```typescript
getAllDrawingLayers(): Array<DrawingLayer>;
```

**Parameters**

None.

**Return value**

Returns an array of all DrawingLayer objects.

**Code Snippet**

```javascript
const containerElement = document.getElementById('imageEditorContainer');
const imageEditorView = new ImageEditorView(containerElement);
DrawingLayers = imageEditorView.getAllDrawingLayers();
```

## deleteUserDefinedDrawingLayer

Deletes a DrawingLayer object specified by its ID.

```typescript
deleteUserDefinedDrawingLayer(id: number): void;
```

**Parameters**

`id`: The ID of the layer that you want to delete.

**Return value**

None.

**Code Snippet**

```javascript
imageEditorView.deleteUserDefinedDrawingLayer(DrawingLayerId);
```

## clearUserDefinedDrawingLayers

Removes all user-defined DrawingLayers.

```typescript
clearUserDefinedDrawingLayers(): void;
```

**Parameters**

None.

**Return value**

None.

**Code Snippet**

```javascript
imageEditorView.clearUserDefinedDrawingLayers();
```

## setTipConfig

Configures the tip feature.

```typescript
setTipConfig(tipConfig: TipConfig): void;
```

**Parameters**

`tipConfig`: Takes a parameter of type TipConfig and is used to set the configuration for a tip in the image editor view.

**Return value**

None.

**Code Snippet**

```javascript
imageEditorView.setTipConfig(TipConfig);
```

## getTipConfig

Returns the configuration of the tip.

```typescript
getTipConfig(): TipConfig;
```

**Parameters**

None.

**Return value**

Returns the configuration of the tip.

**Code Snippet**

```javascript
const tipConfig = imageEditorView.getTipConfig();
```

## setTipVisible

Sets whether to show the tip.

```typescript
setTipVisible(visible: boolean): void;
```

**Parameters**

`visible`: Sets whether to show the tip.

**Return value**

None.

**Code Snippet**

```javascript
imageEditorView.setTipVisible(False);
//Set false to hide the tip.
```

## isTipVisible

Returns whether the tip is visible.

```typescript
isTipVisible(): boolean;
```

**Parameters**

None.

**Return value**

Returns whether the tip is visible.

**Code Snippet**

```javascript
const tipIsVisible = imageEditorView.isTipVisible();
console.log(tipIsVisible); 
```

## updateTipMessage

Updates the message shown in the tip.

```typescript
updateTipMessage(message: string): void;
```

**Parameters**

`message`: A string used to update or change the content of the tip message displayed in the imageEditorView.

**Return value**

None.

**Code Snippet**

```javascript
imageEditorView.updateTipMessage('Hold the phone closer.');
```

## getSelectedDrawingItems

Returns all selected DrawingItem object(s) from different drawing layers.

```typescript
getSelectedDrawingItems(): Promise<Array<DrawingItem>>;
```

**Parameters**

None.

**Return value**

Returns a Promise that resolves to an array of DrawingItem objects representing the currently selected drawing items in the image editor view.

**Code Snippet**

```javascript
let drawingItems = imageEditorView.getSelectedDrawingItems();
```

## setVideoFit

Sets the `object-fit` CSS property of the video element.

```typescript
setVideoFit(objectFit: string): void;
```

**Parameters**

`objectFit`: Specify the new fit type. At present, only "cover" and "contain" are allowed and the default is "contain". Check out more on [object-fit](https://developer.mozilla.org/en-US/docs/Web/CSS/object-fit).

**Return value**

None.

**Code Snippet**

```javascript
imageEditorView.setVideoFit("cover");
```

## getVideoFit

Returns the value of the `object-fit` CSS property of the video element.

```typescript
getVideoFit(): string;
```

**Parameters**

None.

**Return value**

The value of the `object-fit` CSS property.

**Code Snippet**

```javascript
let videofitType = imageEditorView.getVideoFit();
```

## setOriginalImage

Sets the image to be drawn on the image editor image editor view.

```typescript
setOriginalImage(img: Core.BasicStructures.DSImageData | HTMLImageElement | HTMLCanvasElement): Promise<void>;
```

**Parameters**

`img` : Specifies the image data in format of `DSImageData` , `HTMLImageElement` or `HTMLCanvasElement`.  

**Return value**

None.

**Code Snippet**

```javascript
let currentFrame = enhancer.getFrame();
let cvs = currentFrame.toCanvas();
imageEditorView.setOriginalImage(cvs);
```

## getOriginalImage

Returns the image drawn on the image editor.

```typescript
getOriginalImage(): Promise<Core.BasicStructures.DSImageData>;
```

**Parameters**

None.  

**Return value**

Returns a Promise that resolves to a Core.BasicStructures.DSImageData object representing the original image displayed in the image editor view.

**Code Snippet**

```javascript
let image = imageEditorView.getOriginalImage();
```