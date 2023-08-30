---
layout: default-layout
title: CameraView APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the page for Dynamsoft Camera Enhancer JavaScript SDK CameraView APIs.
keywords: CameraView, javascript, js
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

Creates a `CameraView` instance. The `CameraView` is used to display the camera preview and provides UI controlling APIs. You can add interactable UI elements on the view.

```typescript
static createInstance(defaultUIElement?: HTMLDivElement | string): Promise<CameraView>;
```

**Parameters**

`defaultUIElement`(optional): Either a DIV element in which to build the default UI, a URL to use an external UI definition, or omitted for no initial DOM element.

**Return value**

A promise resolving to the created `CameraView` object.

**Code Snippet**

```javascript
let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
```

or

```javascript
// Pass the path of the customized UI in the API `createInstance` to set it as the default UI.
let cameraView = await Dynamsoft.DCE.CameraView.createInstance("THE-URL-TO-THE-FILE");
```

or

```html
<div id="enhancerUIContainer" style="width:1280px;height:720px;background:#ddd;" >
  <div class="dce-video-container" style="width:100%;height:100%;"></div>
</div>
<script>
    // Create 'CameraView' instance and pass an element as its UI.
    let view = await Dynamsoft.DCE.CameraView.createInstance(document.getElementById("enhancerUIContainer"));
</script>
```

## dispose

Releases all resources used by the `CameraView` instance, so that the instance is left with only one property "disposed" as true.

```typescript
dispose(): void;
```

**Parameters**

None.

**Return value**

None.

**Code Snippet**

```javascript
let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
//...
cameraView.dispose();
```

## disposed

A read-only Boolean value indicating whether the `CameraView` instance has been disposed.

```typescript
readonly disposed: boolean; 
```

**Code Snippet**

```javascript
let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
//...
let flag = cameraView.disposed;
```

## getUIElement

Returns the HTML element that is used by the `CameraView` instance.

```typescript
getUIElement(): HTMLElement; 
```

**Parameters**

None.

**Return value**

Returns an HTMLElement.

**Code Snippet**

```javascript
const uiElement = cameraView.getUIElement();
```

## setUIElement

Specifies an HTML element for the `CameraView` instance to use as its UI element. The structure inside the element determines the appearance of the UI.

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
    <div class="dce-video-container" style="position:relative;width:100%;height:500px;"></div>
</div>
<script>
    (async () => {
        let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
        await enhancer.setUIElement(document.getElementById("enhancerUIContainer"));
        await enhancer.open();
    })();
</script>
```

or

```javascript
let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
enhancer.setUIElement("THE-URL-TO-THE-FILE");
```

> If the input HTMLDivElement is not complete, the default video element will be created and appended to the DIV element with the class "dce-video-container". For further customizing the UI please make sure the class name is the same.

## createDrawingLayer

Creates and returns a DrawingLayer object.

```typescript
createDrawingLayer(): DrawingLayer;
```

**Parameters**

None.

**Return value**

A `DrawingLayer` object.

**Code Snippet**

```javascript
const newDrawingLayer = cameraView.createDrawingLayer();
```

## getDrawingLayer

Gets the `DrawingLayer` specified by its ID.

```typescript
getDrawingLayer(id: number): DrawingLayer;
```

**Parameters**

`id`: The ID of the layer that you want to get.

**Return value**

Returns the object of the targeting layer.

**Code Snippet**

```javascript
retrievedDrawingLayer = cameraView.getDrawingLayer(layerId);
```

## getAllDrawingLayers

Returns an array of all `DrawingLayer` objects.

```typescript
getAllDrawingLayers(): Array<DrawingLayer>;
```

**Parameters**

None.

**Return value**

Returns an array of all `DrawingLayer` objects.

**Code Snippet**

```javascript
DrawingLayers = cameraView.getAllDrawingLayers();
```

## deleteUserDefinedDrawingLayer

Deletes a `DrawingLayer` object specified by its ID.

```typescript
deleteUserDefinedDrawingLayer(id: number): void;
```

**Parameters**

`id`: The ID of the layer that you want to delete.

**Return value**

None.

**Code Snippet**

```javascript
cameraView.deleteUserDefinedDrawingLayer(DrawingLayerId);
```

## clearUserDefinedDrawingLayers

Removes all user-defined `DrawingLayers`.

```typescript
clearUserDefinedDrawingLayers(): void;
```

**Parameters**

None.

**Return value**

None.

**Code Snippet**

```javascript
cameraView.clearUserDefinedDrawingLayers();
```

## setTipConfig

Configures the tip feature.

```typescript
setTipConfig(tipConfig: TipConfig): void;
```

**Parameters**

`tipConfig`: Takes a parameter of type TipConfig and is used to set the configuration for a tip in the `cameraView`.

**Return value**

None.

**Code Snippet**

```javascript
cameraView.setTipConfig(TipConfig);
```

**See also**

* [TipConfig](interface/tipconfig.md)

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
const tipConfig = cameraView.getTipConfig();
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
cameraView.setTipVisible(False);
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
const tipIsVisible = cameraView.isTipVisible();
console.log(tipIsVisible); 
```

## updateTipMessage

Updates the message shown in the tip.

```typescript
updateTipMessage(message: string): void;
```

**Parameters**

`message`: A string used to update or change the content of the tip message displayed in the `cameraView`.

**Return value**

None.

**Code Snippet**

```javascript
cameraView.updateTipMessage('Hold the phone closer.');
```

## getVisibleRegionOfVideo

Returns a `Region` object which specifies which part of the original video is shown in the video element.

```typescript
getVisibleRegionOfVideo(options: { inPixels?: boolean }): Core.BasicStructures.Rect;
```

**Parameters**

`options`: Have an inPixels property to specify whether the returned Rect should be in pixel or percentage.

**Return value**

Returns a Rect object that defines the visible region of the video.

**Code Snippet**

```javascript
let visibleRegion = cameraView.getVisibleRegionOfVideo();
```

## getVideoElement

Returns the video element used by the `CameraView` instance.

```typescript
getVideoElement(): HTMLVideoElement;
```

**Parameters**

None.

**Return value**

Returns a HTMLVideoElement.

**Code Snippet**

```javascript
let videoElement = cameraView.getVideoElement();
```

## setScanRegionMaskStyle

Sets the drawing style for the scan-region mask.

```typescript
setScanRegionMaskStyle(newStyle: {
                lineWidth: number,
                strokeStyle: string,
                fillStyle: string
            }): void;
```

**Parameters**

`lineWidth`: The width of the lines used to draw the mask border.  
`strokeStyle`: The color or style of the mask border lines.  
`fillStyle`: The color of the mask's interior fill.  

> The default value is
>
> ```javascript
> lineWidth = 2; 
> strokeStyle = "rgb(254,142,20)"; 
> fillStyle = "rgba(0,0,0,0.5)"; 
> ```
>
> Read more on [strokeStyle](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/strokeStyle) and [fillStyle](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/fillStyle).

**Return value**

None.

**Code Snippet**

```javascript
cameraView.setScanRegionMaskStyle({
  lineWidth: 3,
  strokeStyle: 'red',
  fillStyle: 'rgba(50, 50, 50, 0.3)'
});
```

## getScanRegionMaskStyle

Returns the drawing style for the scan-region mask.

```typescript
getScanRegionMaskStyle(): DrawingStyle;
```

**Parameters**

None.

**Return value**

Returns the current style settings of the scan region mask, which include properties such as lineWidth, strokeStyle, and fillStyle.

**Code Snippet**

```javascript
const currentStyle = cameraView.getScanRegionMaskStyle();
console.log(currentStyle);
```

## setScanRegionMaskVisible

Sets whether to show the scan-region mask.

```typescript
setScanRegionMaskVisible(visible: boolean): void;
```

**Parameters**

`visible`: Sets whether to show the scan region mask.

**Return value**

None.

**Code Snippet**

```javascript
cameraView.setScanRegionMaskVisible(False);
//Set false to hide the region mask.
```

## isScanRegionMaskVisible

Returns whether the scan-region mask is visible.

```typescript
isScanRegionMaskVisible(): boolean;
```

**Parameters**

None.

**Return value**

Returns whether the ScanRegionMask is visible.

**Code Snippet**

```javascript
const maskIsVisible = cameraView.isScanRegionMaskVisible();
console.log(maskIsVisible); 
```

## setScanLaserVisible

Sets whether to show the laser that indicates the scanning is going on.

```typescript
setScanLaserVisible(visible: boolean): void;
```

**Parameters**

`visible`: Sets whether to show the laser.

**Return value**

None.

**Code Snippet**

```javascript
cameraView.setScanLaserVisible(False);
//Set false to hide the laser.
```

## isScanLaserVisible

Returns whether the laser is visible.

```typescript
isScanLaserVisible(): boolean;
```

**Parameters**

None.

**Return value**

Returns whether the laser is visible.

**Code Snippet**

```javascript
const laserIsVisible = cameraView.isScanLaserVisible();
console.log(laserIsVisible); 
```