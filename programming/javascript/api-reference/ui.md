---
layout: default-layout
title: UI APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK UI.
keywords: camera enhancer, UI, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: UI
permalink: /programming/javascript/api-reference/ui.html
---

# CameraEnhancer - UI

| Name                                                                  | Description                                                                                         |
| --------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| [convertToScanRegionCoordinates](#convertToScanRegionCoordinates)     | Converts coordinates from the video's coordinate system to coordinates relative to the scan region. |
| [convertToPageCoordinates](#convertToPageCoordinates)                 | Converts coordinates from the video's coordinate system to coordinates relative to the whole page.  |
| [convertToClientCoordinates](#convertToClientCoordinates)             | Converts coordinates from the video's coordinate system to coordinates relative to the viewport.    |
| [setCameraView](#setCameraView)                                       | Sets the `CameraView` instance to be used with the `CameraEnhancer`.                                |
| [getCameraView](#getCameraView)                                       | Retrieves the current `CameraView` instance associated with the `CameraEnhancer`.                   |
| [getVideoEl](#getVideoEl)                                             | Retrieves the HTMLVideoElement used by the `CameraEnhancer` for displaying the camera feed.         |

## convertToScanRegionCoordinates

Converts coordinates from the video's coordinate system to coordinates relative to the scan region.

This is useful for overlaying HTML elements on top of specific points in the video, aligning with the page's layout.

```typescript
convertToScanRegionCoordinates(point: Point): Point;
```

**Parameters**

`point`: a `Point` object representing the x and y coordinates within the video's coordinate system.

**Return value**

A `Point` object representing the converted x and y coordinates relative to the scan region.

**Code Snippet**

```javascript
cameraEnhancer.convertToScanRegionCoordinates({x: 0, y: 0});
```

## convertToPageCoordinates

Converts coordinates from the video's coordinate system to coordinates relative to the whole page.

This is useful for overlaying HTML elements on top of specific points in the video, aligning with the page's layout.

```typescript
convertToPageCoordinates(point: Point): Point;
```

**Parameters**

`point`: a `Point` object representing the x and y coordinates within the video's coordinate system.

**Return value**

A `Point` object representing the converted x and y coordinates relative to the page.

**Code Snippet**

```javascript
cameraEnhancer.convertToPageCoordinates({x: 0, y: 0});
```

**See also**

[Point](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/point.html)

## convertToClientCoordinates

Converts coordinates from the video's coordinate system to coordinates relative to the viewport. 

This is useful for positioning HTML elements in relation to the video element on the screen, regardless of page scrolling.

```typescript
convertToClientCoordinates(point: Point): Point;
```

**Parameters**

`point`: a `Point` object representing the x and y coordinates within the video's coordinate system.

**Return value**

A `Point` object representing the converted x and y coordinates relative to the viewport.

**Code Snippet**

```javascript
cameraEnhancer.convertToClientCoordinates({x: 0, y: 0});
```

**See also**

[Point](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/point.html)

## setCameraView

Sets the `CameraView` instance to be used with the `CameraEnhancer`.

This method allows for specifying a custom camera view, which can be used to display the camera feed and interface elements.

```typescript
setCameraView(cameraView: CameraView): void;
```

**Parameters**

`cameraView`: a `CameraView` instance that will be used to display the camera's video feed and any associated UI components.

**Return value**

None.

**Code Snippet**

```javascript
let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
cameraEnhancer.setCameraView(cameraView);
```

**See also**

[CameraView](cameraview.md)

## getCameraView

Retrieves the current `CameraView` instance associated with the `CameraEnhancer`.

This method allows for accessing the camera view, which can be useful for manipulating the view or accessing its properties and methods.

```typescript
getCameraView(): CameraView;
```

**Parameters**

None.

**Return value**

The current `CameraView` instance used by the `CameraEnhancer`.

**Code Snippet**

```javascript
let cameraView = cameraEnhancer.getCameraView();
cameraView.getVisibleRegionOfVideo();
```

**See also**

[CameraView](cameraview.md)

## getVideoEl

Retrieves the HTMLVideoElement used by the `CameraEnhancer` for displaying the camera feed.

This method provides direct access to the video element, enabling further customization or interaction with the video stream.

```typescript
getVideoEl(): HTMLVideoElement;
```

**Parameters**

None.

**Return value**

The `HTMLVideoElement` that is being used to display the camera's video feed.

**Code Snippet**

```javascript
let videoElement = cameraEnhancer.getVideoEl();
```
