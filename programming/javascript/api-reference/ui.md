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

# Class CameraEnhancer

## UI

| API Name                                                         | Description                                                                                                                                                      |
| ---------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [getCameraView()](ui.md#getcameraview)                             | Returns the `CameraView` instance used by the `CameraEnhancer` instance.                                                                                         |
| [setCameraView()](ui.md#setcameraview)                             | Sets a `CameraView` instance to be used by the `CameraEnhancer` instance.                                                                                        |
| [getVideoEl()](ui.md#getvideoel)                                   | Returns the video element used by the `CameraView` instance.                                                                                                     |
| [convertToPageCoordinates()](ui.md#converttopagecoordinates)     | Converts coordinates of a point to the coordinates relative to the top left point of the entire document.                                                        |
| [convertToClientCoordinates()](ui.md#converttoclientcoordinates) | Converts coordinates of a point to the coordinates within the application's viewport at which the event occurred (as opposed to the coordinate within the page). |

## getCameraView

Returns the `CameraView` instance used by the `CameraEnhancer` instance. The `CameraView` is responsible for streaming video with real-time interaction such as highlighting certain objects found in the video.

```typescript
getCameraView(): CameraView;
```

**Parameters**

None.

**Return value**

The `CameraView` instance used by the `CameraEnhancer` instance.

**Code Snippet**

```javascript
let cameraView = enhancer.getCameraView();
cameraView.getVisibleRegionOfVideo();
```

**See Also**

* [CameraView](cameraview.md)

## setCameraView

Sets a `CameraView` instance to be used by the `CameraEnhancer` instance.

```typescript
setCameraView(cameraView: CameraView): void;
```

**Parameters**

* `cameraView` : specifies the `CameraView` instance.

**Return value**

None.

**Code Snippet**

```javascript
let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
enhancer.setCameraView(cameraView);
```

## getVideoEl

Returns the video element used by the `CameraEnhancer` instance.

```typescript
getVideoEl(): HTMLVideoElement;
```

**Parameters**

None.

**Return value**

The video element.

**Code Snippet**

```javascript
let videoElement = enhancer.getVideoEl();
```
<!--
## setVideoEl

Sets a video element to be used by the `CameraView` instance.

```typescript
setVideoEl(videoElement: HTMLVideoElement): Promise<void>;
```

**Parameters**

* `videoElement` : specifies an `HTMLVideoElement` element.

**Return value**

A promise resolving to none.

**Code Snippet**

```javascript
let el = document.getElementById("videoElement");
enhancer.setVideoEl(el);
```
-->

## convertToPageCoordinates

Converts coordinates of a point to the coordinates relative to the top left point of the entire document.

```typescript
convertToPageCoordinates(point: Point): Point;
```

**Parameters**

* `point`: specifies the original points (refer to the image selected in the video or in `singleFrameMode`) to be converted.

**Return value**

The converted point.

**Code Snippet**

```javascript
enhancer.convertToPageCoordinates({x: 0, y: 0});
```

**See Also**

* [Point](https://www.dynamsoft.com/capture-vision/docs/core/enums/core/buffer-overflow-protection-mode.html?lang=js)

## convertToClientCoordinates

Converts coordinates of a point to the coordinates within the application's viewport (as opposed to the coordinate within the page).

```typescript
convertToClientCoordinates(point: Point): Point;
```

**Parameters**

* `point`: specifies the original point to be converted.

**Return value**

The converted point.

**Code Snippet**

```javascript
enhancer.convertToClientCoordinates({x: 0, y: 0});
```

**See Also**

* [Point](https://www.dynamsoft.com/capture-vision/docs/core/enums/core/buffer-overflow-protection-mode.html?lang=js)
