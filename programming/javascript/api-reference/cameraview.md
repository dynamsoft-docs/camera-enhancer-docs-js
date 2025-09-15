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

| Name                                                        | Description                                                                                 |
| --------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [createInstance](#createInstance)                               | Initializes a new instance of the `CameraView` class with optional UI customization.        |
| [dispose](#dispose)                                             | Releases all resources used by the `CameraView` instance.                                   |
| [disposed](#disposed)                                           | Returns whether the `CameraView` instance has been disposed of.                             |
| [defaultUIElementURL](#defaultUIElementURL)                     | Specifies the URL to a default UI definition file.                                          |
| [getUIElement](#getUIElement)                                   | Retrieves the current UI element associated with the `CameraView` instance.                 |
| [setUIElement](#setUIElement)                                   | Sets a specific `HTMLDivElement` as the UI element for the `CameraView` instance.           |
| [createDrawingLayer](#createDrawingLayer)                       | Creates a new `DrawingLayer` object.                                                        |
| [getDrawingLayer](#getDrawingLayer)                             | Retrieves a `DrawingLayer` object by its unique identifier (ID).                            |
| [getAllDrawingLayers](#getAllDrawingLayers)                     | Returns an array of all `DrawingLayer` objects managed by this instance.                    |
| [clearUserDefinedDrawingLayers](#clearUserDefinedDrawingLayers) | Clears all user-defined `DrawingLayer` objects.                                             |
| [deleteUserDefinedDrawingLayer](#deleteUserDefinedDrawingLayer) | Deletes a user-defined `DrawingLayer` object by ID.                                         |
| [clearAllInnerDrawingItems](#clearAllInnerDrawingItems)         | Clears all system-defined `DrawingItem` objects while keeping user-defined ones.            |
| [getVideoElement](#getVideoElement)                             | Retrieves the `HTMLVideoElement` used for displaying video.                                 |
| [setVideoFit](#setVideoFit)                                     | Sets the `object-fit` CSS property of the `HTMLVideoElement`.                               |
| [getVideoFit](#getVideoFit)                                     | Retrieves the current value of the `object-fit` CSS property.                               |
| [getVisibleRegionOfVideo](#getVisibleRegionOfVideo)             | Returns the region of the video that is currently visible to the user.                      |
| [setScanRegionMaskStyle](#setScanRegionMaskStyle)               | Sets the style of the scan region mask, including line width, stroke color, and fill color. |
| [getScanRegionMaskStyle](#getScanRegionMaskStyle)               | Retrieves the current style of the scan region mask.                                        |
| [setScanRegionMaskVisible](#setScanRegionMaskVisible)           | Sets the visibility of the scan region mask.                                                |
| [isScanRegionMaskVisible](#isScanRegionMaskVisible)             | Checks if the scan region mask is currently visible.                                        |
| [setScanLaserVisible](#setScanLaserVisible)                     | Sets the visibility of the scan laser effect.                                               |
| [isScanLaserVisible](#isScanLaserVisible)                       | Checks if the scan laser effect is currently visible.                                       |
| [getTipConfig](#getTipConfig)                                   | Retrieves the current configuration of the tip message box.                                 |
| [setTipConfig](#setTipConfig)                                   | Applies configuration settings to the tip message box.                                      |
| [setTipVisible](#setTipVisible)                                 | Controls the visibility of the tip message box on the screen.                               |
| [isTipVisible](#isTipVisible)                                   | Checks whether the tip message box is currently visible.                                    |
| [updateTipMessage](#updateTipMessage)                           | Updates the message displayed in the tip message box.                                       |

## createInstance

Initializes a new instance of the `CameraView` class. This method allows for optional customization of the user interface (UI) through a specified HTML element or an HTML file.

```typescript
static createInstance(defaultUIElement?: HTMLDivElement | string): Promise<CameraView>;
```

**Parameters**

`defaultUIElement`: [Optional] specifies the UI element or the path to an HTML file containing the UI definition for the `CameraView` instance.
- If an `HTMLDivElement` is provided, it should either be an empty element where the UI will be dynamically loaded, or contain the predefined UI structure for the camera view.
- If a string is provided, it should be the path to an HTML file that includes the UI definition. This HTML content will be loaded and used as the camera view's UI.
- If the parameter is omitted or an empty `HTMLDivElement` is provided without corresponding UI definition, the method will fallback to a default UI definition specified by `defaultUIElementURL` and append it to the provided or newly created `HTMLDivElement`.

**Return value**

A promise that resolves with the fully initialized `CameraView` instance once the UI has been successfully set up. This includes loading the UI from the provided `defaultUIElement`, the specified HTML file, or from the fallback `defaultUIElementURL`.

**Code Snippet**

```javascript
let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
```

or

```javascript
// Provide the predefined UI structure for the camera view in an HTML file.
let cameraView = await Dynamsoft.DCE.CameraView.createInstance("THE-URL-TO-THE-FILE");
```

or

```html
<div id="div-ui-container" style="width: 70vw; height: 40vh; margin-top: 3vh;position:relative;">
	<div class="dce-video-container" style="position:absolute;left:0;top:0;width:100%;height:100%;"></div>
</div>
<script>
    // Provide the predefined UI structure for the camera view in an `HTMLDivElement`.
    let view = await Dynamsoft.DCE.CameraView.createInstance(document.getElementById("div-ui-container"));
</script>
```

## dispose

Releases all resources used by the `CameraView` instance.

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

Returns whether the `CameraView` instance has been disposed of.

```typescript
readonly disposed: boolean; 
```

**Code Snippet**

```javascript
let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
//...
let flag = cameraView.disposed;
```

## defaultUIElementURL

Specifies the URL to a default UI definition file. 

```typescript
static defaultUIElementURL: string;
```

**Code Snippet**

```javascript
Dynamsoft.DCE.CameraView.defaultUIElementURL = 'https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@4.0.1/dist/dce.ui.html';
let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
```

## getUIElement

Retrieves the current UI element associated with the `CameraView` instance. 

```typescript
getUIElement(): HTMLElement; 
```

**Parameters**

None.

**Return value**

The `HTMLDivElement` that is currently being used as the UI for the `CameraView`. This could be the default UI loaded from `defaultUIElementURL`, a UI defined in an HTML file specified at instance creation, or a UI set through `setUIElement()`.

**Code Snippet**

```javascript
const uiElement = cameraView.getUIElement();
```

## setUIElement

Sets a specific `HTMLDivElement` to serve as the UI element for the `CameraView` instance. This method allows for dynamic customization of the camera view's appearance and functionality by providing a new HTML structure as its user interface.

```typescript
setUIElement(UIElement: HTMLDivElement | string): Promise<void>;
```

**Parameters**

`UIElement`: The `HTMLDivElement` to be used as the new UI for the `CameraView`. This div can be:
- An empty element, where the UI will be dynamically loaded either from a specified HTML file or the default UI definition.
- A pre-populated element containing a predefined UI structure for the camera view. This allows for extensive customization and immediate application of the custom UI.

**Return value**

A promise that resolves once the new UI has been successfully applied to the `CameraView` instance. It does not provide any value upon resolution.

**Code Snippet**

```html
<div id="div-ui-container" style="width: 70vw; height: 40vh; margin-top: 3vh;position:relative;">
	<div class="dce-video-container" style="position:absolute;left:0;top:0;width:100%;height:100%;"></div>
</div>
<script>
    (async () => {
        let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
        await cameraView.setUIElement(document.getElementById("div-ui-container"));
    })();
</script>
```

## createDrawingLayer

Creates a new `DrawingLayer` object and returns it.

```typescript
createDrawingLayer(): DrawingLayer;
```

**Parameters**

None.

**Return value**

The created `DrawingLayer` object.

**Code Snippet**

```javascript
const newDrawingLayer = cameraView.createDrawingLayer();
```

## getDrawingLayer

Retrieves a `DrawingLayer` object by its unique identifier (ID).

```typescript
getDrawingLayer(id: number): DrawingLayer | null;
```

**Parameters**

`id`: the unique identifier (ID) of the `DrawingLayer` object.

**Return value**

The `DrawingLayer` object specified by its unique identifier (ID) or `null`.

**Code Snippet**

```javascript
retrievedDrawingLayer = cameraView.getDrawingLayer(layerId);
```

## getAllDrawingLayers

Returns an array of all `DrawingLayer` objects managed by this `DrawingLayerManager`.

```typescript
getAllDrawingLayers(): Array<DrawingLayer>;
```

**Parameters**

None.

**Return value**

An array of all `DrawingLayer` objects.

**Code Snippet**

```javascript
DrawingLayers = cameraView.getAllDrawingLayers();
```

## clearUserDefinedDrawingLayers

Clears all user-defined `DrawingLayer` objects.

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

## deleteUserDefinedDrawingLayer

 Deletes a user-defined `DrawingLayer` object specified by its unique identifier (ID).

```typescript
deleteUserDefinedDrawingLayer(id: number): void;
```

**Parameters**

`id`: the unique identifier (ID) of the `DrawingLayer` object.

**Return value**

None.

**Code Snippet**

```javascript
cameraView.deleteUserDefinedDrawingLayer(DrawingLayerId);
```

## clearAllInnerDrawingItems

Clears all system-defined `DrawingItem` objects while keeping user-defined ones.

```typescript
clearAllInnerDrawingItems(): void;
```

**Parameters**

None.

**Return value**

None.

**Code Snippet**

```javascript
cameraView.clearAllInnerDrawingItems();
```

## getVideoElement

Retrieves the `HTMLVideoElement` that is currently being used for displaying the video in this `CameraView` instance. This method allows access to the underlying video element, enabling direct interaction or further customization.

```typescript
getVideoElement(): HTMLVideoElement;
```

**Parameters**

None.

**Return value**

The `HTMLVideoElement` currently used by this `CameraView` instance for video display.

**Code Snippet**

```javascript
let videoElement = cameraView.getVideoElement();
```

## setVideoFit

Sets the `object-fit` CSS property of the `HTMLVideoElement` used by this `CameraView` instance. The `object-fit` property specifies how the video content should be resized to fit the container in a way that maintains its aspect ratio.

```typescript
setVideoFit(objectFit: string): void;
```

**Parameters**

The value for the `object-fit` property. At present, only "cover" and "contain" are allowed and the default is "contain". Check out more on [object-fit](https://developer.mozilla.org/en-US/docs/Web/CSS/object-fit).

**Return value**

None.

**Code Snippet**

```javascript
cameraView.setVideoFit("cover");
```

## getVideoFit

Retrieves the current value of the `object-fit` CSS property from the `HTMLVideoElement` used by this `CameraView` instance.

```typescript
getVideoFit(): string;
```

**Parameters**

None.

**Return value**

The current value of the `object-fit` property applied to the video element. At present, the value is limited to "cover" and "contain". Check out more on [object-fit](https://developer.mozilla.org/en-US/docs/Web/CSS/object-fit).

**Code Snippet**

```javascript
cameraView.getVideoFit();
```

## getVisibleRegionOfVideo

Returns the region of the video that is currently visible to the user.

```typescript
getVisibleRegionOfVideo(options?: { inPixels?: boolean }): Rect;
```

**Parameters**

`options`: [Optional] specifies how the visible region should be returned.

`options.inPixels` [Optional] if `true`, the coordinates of the visible region are returned in pixels. If `false` or omitted, the coordinates are returned as a percentage of the video element's size.

**Return value**

An object representing the visible region of the video.

**Code Snippet**

```javascript
let visibleRegion = cameraView.getVisibleRegionOfVideo();
```

## setScanRegionMaskStyle

Sets the style of the scan region mask. This style includes the line width, stroke color, and fill color.

```typescript
setScanRegionMaskStyle: (newStyle: { lineWidth: number, strokeStyle: string, fillStyle: string }) => void;
```

**Parameters**

`newStyle` An object containing the new style settings for the scan region mask.

`newStyle.lineWidth` The width of the line used to draw the border of the scan region mask.

`newStyle.strokeStyle` The color of the stroke (border) of the scan region mask.

`newStyle.fillStyle` The fill color of the scan region mask.

> The default value is
>
> ```javascript
> lineWidth = 6; 
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

Retrieves the current style of the scan region mask. This includes the line width, stroke color, and fill color.

```typescript
getScanRegionMaskStyle(): DrawingStyle;
```

**Parameters**

None.

**Return value**

The current `DrawingStyle` of the scan region mask, which includes the line width, stroke color, and fill color.

**Code Snippet**

```javascript
const currentStyle = cameraView.getScanRegionMaskStyle();
console.log(currentStyle);
```

## setScanRegionMaskVisible

Sets the visibility of the scan region mask. This can be used to show or hide the mask.

```typescript
setScanRegionMaskVisible(visible: boolean): void;
```

**Parameters**

`visible`: boolean indicating whether the scan region mask should be visible (`true`) or not (`false`).

**Return value**

None.

**Code Snippet**

```javascript
//Hide the region mask.
cameraView.setScanRegionMaskVisible(false);
```

## isScanRegionMaskVisible

Checks if the scan region mask is currently visible.

```typescript
isScanRegionMaskVisible(): boolean;
```

**Parameters**

None.

**Return value**

Boolean indicating whether the scan region mask is visible (`true`) or not (`false`).

**Code Snippet**

```javascript
const maskIsVisible = cameraView.isScanRegionMaskVisible();
console.log(maskIsVisible); 
```

## setScanLaserVisible

Sets the visibility of the scan laser effect. This can be used to show or hide the scan laser.

```typescript
setScanLaserVisible(visible: boolean): void;
```

**Parameters**

`visible`: boolean indicating whether the scan laser should be visible (`true`) or not (`false`).

**Return value**

None.

**Code Snippet**

```javascript
cameraView.setScanLaserVisible(false);
//Set false to hide the laser.
```

## isScanLaserVisible

Checks if the scan laser effect is currently visible.

```typescript
isScanLaserVisible(): boolean;
```

**Parameters**

None.

**Return value**

Boolean indicating whether the scan laser is visible (`true`) or not (`false`).

**Code Snippet**

```javascript
const laserIsVisible = cameraView.isScanLaserVisible();
console.log(laserIsVisible); 
```

## getTipConfig

Retrieves the current configuration of the tip message box, reflecting its position, size, display duration, and the coordinate system basis.

```typescript
getTipConfig(): TipConfig;
```

**Parameters**

None.

**Return value**

The current configuration settings of the tip message box.

**Code Snippet**

```javascript
const tipConfig = cameraView.getTipConfig();
```

## setTipConfig

Applies configuration settings to the tip message box.

This includes its position, size, display duration, and the coordinate system basis.

```typescript
setTipConfig(tipConfig: TipConfig): void;
```

**Parameters**

`tipConfig`: Configuration object for the tip message box, including top-left position, width, display duration, and coordinate system basis.

**Return value**

None.

**Code Snippet**

```javascript
cameraView.setTipConfig({
  topLeftPoint: {x: 50, y:50},
  width: 200,
  duration: 1000
})
```

**See also**

[TipConfig](interface/tipconfig.md)

## setTipVisible

Controls the visibility of the tip message box on the screen.

This can be used to show or hide the tip based on user interaction or other criteria.

```typescript
setTipVisible(visible: boolean): void;
```

**Parameters**

`visible`: boolean flag indicating whether the tip message box should be visible (`true`) or hidden (`false`).

**Return value**

None.

**Code Snippet**

```javascript
//Hide the tip message box.
cameraView.setTipVisible(false);
```

## isTipVisible

Checks whether the tip message box is currently visible to the user.

```typescript
isTipVisible(): boolean;
```

**Parameters**

None.

**Return value**

Boolean indicating the visibility of the tip message box (`true` for visible, `false` for hidden).

**Code Snippet**

```javascript
const tipIsVisible = cameraView.isTipVisible();
console.log(tipIsVisible); 
```

## updateTipMessage

Updates the message displayed in the tip message box.

This can be used to provide dynamic feedback or information to the user.

```typescript
updateTipMessage(message: string): void;
```

**Parameters**

`message`: the new message to be displayed in the tip message box.

**Return value**

None.

**Code Snippet**

```javascript
cameraView.updateTipMessage('Hold the phone closer.');
```
