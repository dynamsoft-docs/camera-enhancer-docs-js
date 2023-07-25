---
layout: default-layout
title: CameraView APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the page for Dynamsoft Camera Enhancer JavaScript SDK CameraView APIs.
keywords: cameraView, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: CameraView
permalink: /programming/javascript/api-reference/cameraview.html
---

# CameraView

### Create and Destroy Instances

| API Name                                     | Description                                                                              |
| -------------------------------------------- | ---------------------------------------------------------------------------------------- |
| `static` [createInstance()](#createinstance) | Creates a `CameraView` instance.                                                         |
| [dispose()](#dispose)                        | Releases all resources used by the `CameraView` instance.                                |
| [disposed](#disposed)                        | A readonly boolean value indicating whether the `CameraView` instance has been disposed. |
| [getUIElement()](#getuielement)              | Returns the HTML element that is used by the `CameraView` instance.                      |
| [setUIElement()](#setuielement)              | Specifies an HTML element for the `CameraView` instance to use as its UI element.        |

### Drawing and UI

| API Name                                                          | Description                                                                                               |
| ----------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| [createDrawingLayer()](#createdrawinglayer)                       | Creates a DrawingLayer object and put it in an array of DrawingLayers.                                    |
| [getDrawingLayer()](#getdrawinglayer)                             | Gets the DrawingLayer specified by its ID.                                                                |
| [getAllDrawingLayers()](#getalldrawinglayers)                     | Returns an array of all DrawingLayer objects.                                                             |
| [deleteUserDefinedDrawingLayer()](#deleteuserdefineddrawinglayer) | Deletes a DrawingLayer object specified by its ID.                                                        |
| [clearUserDefinedDrawingLayers()](#clearuserdefineddrawinglayers) | Removes all user-defined DrawingLayers.                                                                   |
| [setTipConfig()](#settipconfig)                                   | Configures the tip feature.                                                                               |
| [getTipConfig()](#gettipconfig)                                   | Returns the configuration of the tip.                                                                     |
| [setTipVisible()](#settipvisible)                                 | Sets whether to show the tip.                                                                             |
| [isTipVisible()](#istipvisible)                                   | Returns whether the tip is visible.                                                                       |
| [updateTipMessage()](#updatetipmessage)                           | Updates the message shown in the tip.                                                                     |
| [getVisibleRegionOfVideo()](#getvisibleregionofvideo)             | Returns a `Region` object which specifies which part of the original video is shown in the video element. |
| [getVideoElement](#getvideoelement)                               | Returns the video element used by the `CameraView` instance.                                              |
| [setScanRegionMaskStyle()](#setscanregionmaskstyle)               | Sets the drawing style for the scan-region mask.                                                          |
| [getScanRegionMaskStyle()](#getscanregionmaskstyle)               | Returns the drawing style for the scan-region mask.                                                       |
| [setScanRegionMaskVisible()](#setscanregionmaskvisible)           | Sets whether to show the scan-region mask.                                                                |
| [isScanRegionMaskVisible()](#isscanregionmaskvisible)             | Returns whether the scan-region mask is visible.                                                          |
| [setScanLaserVisible()](#setscanlaservisible)                     | Sets whether to show the laser that indicates the scanning is going on.                                   |
| [isScanLaserVisible()](#isscanlaservisible)                       | Returns whether the laser is visible.                                                                     |

## createInstance

Creates a `ImageEditorView` instance.

```typescript
static createInstance: () => Promise<ImageEditorView>;
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
dispose: () => void;
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

A readonly boolean value indicating whether the `ImageEditorView` instance has been disposed.

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
getUIElement: () => HTMLElement; 
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
setUIElement: (element: HTMLDivElement) => Promise<void>;
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
createDrawingLayer: () => DrawingLayer;
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
getDrawingLayer: (id: number) => DrawingLayer;
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
getAllDrawingLayers: () => Array<DrawingLayer>;
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
deleteUserDefinedDrawingLayer: (id: number) => void;
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
clearUserDefinedDrawingLayers: () => void;
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
setTipConfig: (tipConfig: TipConfig) => void;
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
getTipConfig: () => TipConfig;
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
setTipVisible: (visible: boolean) => void;
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
isTipVisible: () => boolean;
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
updateTipMessage: (message: string) => void;
```

**Parameters**

`message`: A string used to update or change the content of the tip message displayed in the imageEditorView.

**Return value**

None.

**Code Snippet**

```javascript
imageEditorView.updateTipMessage('Hold the phone closer.');
```

## getVisibleRegionOfVideo

Returns a `Region` object which specifies which part of the original video is shown in the video element


## getVideoElement

Returns the video element used by the `CameraView` instance.


## setScanRegionMaskStyle

Sets the drawing style for the scan-region mask.

```typescript
setScanRegionMaskStyle: (newStyle: {
                lineWidth: number,
                strokeStyle: string,
                fillStyle: string
            }) => void;
```

**Parameters**

`lineWidth`: The width of the lines used to draw the mask border.
`strokeStyle`: The color or style of the mask border lines.
`fillStyle`: The color of the mask's interior fill.

**Return value**

None.

**Code Snippet**

```javascript
imageEditorView.setScanRegionMaskStyle({
  lineWidth: 3,
  strokeStyle: 'red',
  fillStyle: 'rgba(50, 50, 50, 0.3)'
});
```

## getScanRegionMaskStyle

Returns the drawing style for the scan-region mask.

```typescript
getScanRegionMaskStyle: () => DrawingStyle;
```

**Parameters**

None.

**Return value**

Returns the current style settings of the scan region mask, which include properties such as lineWidth, strokeStyle, and fillStyle.

**Code Snippet**

```javascript
const currentStyle = imageEditorView.getScanRegionMaskStyle();
console.log(currentStyle);
```

## setScanRegionMaskVisible

Sets whether to show the scan-region mask.

```typescript
setScanRegionMaskVisible: (visible: boolean) => void;
```

**Parameters**

`visible`: Sets whether to show the scan region mask.

**Return value**

None.

**Code Snippet**

```javascript
imageEditorView.setScanRegionMaskVisible(False);
//Set false to hide the region mask.
```

## isScanRegionMaskVisible

Returns whether the scan-region mask is visible.

```typescript
isScanRegionMaskVisible: () => boolean;
```

**Parameters**

None.

**Return value**

Returns whether the ScanRegionMask is visible.

**Code Snippet**

```javascript
const maskIsVisible = imageEditorView.isScanRegionMaskVisible();
console.log(maskIsVisible); 
```

## setScanLaserVisible

Sets whether to show the laser that indicates the scanning is going on.

```typescript
setScanLaserVisible: (visible: boolean) => void;
```

**Parameters**

`visible`: Sets whether to show the laser.

**Return value**

None.

**Code Snippet**

```javascript
imageEditorView.setScanLaserVisible(False);
//Set false to hide the laser.
```

## isScanLaserVisible

Returns whether the laser is visible.

```typescript
isScanLaserVisible: () => boolean;
```

**Parameters**

None.

**Return value**

Returns whether the laser is visible.

**Code Snippet**

```javascript
const laserIsVisible = imageEditorView.isScanLaserVisible();
console.log(laserIsVisible); 
```