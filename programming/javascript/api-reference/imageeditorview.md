---
layout: default-layout
title: ImageEditorView APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the page for Dynamsoft Camera Enhancer JavaScript SDK ImageEditorView APIs.
keywords: ImageEditorView, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: ImageEditorView
permalink: /programming/javascript/api-reference/imageeditorview.html
---

# ImageEditorView

### Create and Destroy Instances

| API Name                                     | Description                                                                                   |
| -------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `static` [createInstance()](#createinstance) | Creates an `ImageEditorView` instance.                                                         |
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
| [getSelectedDrawingItems()](imageeditorview.md#getselecteddrawingitems) | Returns the selected DrawingItem object(s).                              |
| [setOriginalImage()](imageeditorview.md#setoriginalimage)               | Sets the image to be drawn on the image editor view.                     |
| [getOriginalImage()](imageeditorview.md#setoriginalimage)               | Returns the image drawn on the image editor.                             |

## createInstance

Creates an `ImageEditorView` instance. The `ImageEditorView` is responsible for displaying a single image with real-time interaction such as editing the boundaries of an object found in the image.

```typescript
static createInstance(defaultUIElement?: HTMLDivElement | string): Promise<ImageEditorView>;
```

**Parameters**

`defaultUIElement`(optional): Either a DIV element in which to build the default UI, a URL to use an external UI definition, or omitted for no initial DOM element.

**Return value**

A promise resolving to the created `ImageEditorView` object.

**Code Snippet**

```javascript
let cameraView = await Dynamsoft.DCE.ImageEditorView.createInstance();
```

or

```javascript
// Pass the path of the customized UI in the API `createInstance` to set it as the default UI.
let cameraView = await Dynamsoft.DCE.ImageEditorView.createInstance("THE-URL-TO-THE-FILE");
```

or

```html
<div id="enhancerUIContainer" style="width:1280px;height:720px;background:#ddd;" >
  <div class="dce-image-container" style="width:100%;height:100%;"></div>
</div>
<script>
    // Create 'ImageEditorView' instance and pass an element as its UI.
    let view = await Dynamsoft.DCE.ImageEditorView.createInstance(document.getElementById("enhancerUIContainer"));
</script>
```

## dispose

Releases all resources used by the `ImageEditorView` instance, so that the instance is left with only one property "disposed" as true.

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

Specifies an HTML element for the `ImageEditorView` instance to use as its UI element. The structure inside the element determines the appearance of the UI.

```typescript
setUIElement(element: HTMLDivElement | string): Promise<void>;
```

**Parameters**

`element`: A DIV element in which to build the default UI, or a URL to use an external UI definition.

**Return value**

None.

**Code Snippet**

```javascript
<div id="enhancerUIContainer" style="width:100%;height:100%;">
    <div class="dce-image-container" style="display:none; width: 100vw; height: 70vh"></div>
</div>
<script>
    (async () => {
        let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
        await enhancer.setUIElement(document.getElementById("enhancerUIContainer"));
        await enhancer.open();
    })();
</script>
```

> If the input HTMLDivElement is not complete, the default image element will be created and appended to the DIV element with the class "dce-image-container". For further customizing the UI please make sure the class name is the same.

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

<!--
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
-->
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

<!--
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
-->
## setOriginalImage

Sets the image to be drawn on the image editor view.

```typescript
setOriginalImage(img: Core.BasicStructures.DSImageData | HTMLImageElement | HTMLCanvasElement): void;
```

**Parameters**

`img` : Specifies the image data in format of `DSImageData` , `HTMLImageElement` or `HTMLCanvasElement`.  

**Return value**

None.

**Code Snippet**

```javascript
let currentFrame = enhancer.getFrame();
imageEditorView.setOriginalImage(currentFrame);
```

## getOriginalImage

Returns the image drawn on the image editor.

```typescript
getOriginalImage(): Core.BasicStructures.DSImageData | HTMLImageElement | HTMLCanvasElement;
```

**Parameters**

None.  

**Return value**

Either a `DSImageData` object, an HTMLImageElement, or an HTMLCanvasElement.

**Code Snippet**

```javascript
let image = imageEditorView.getOriginalImage();
```