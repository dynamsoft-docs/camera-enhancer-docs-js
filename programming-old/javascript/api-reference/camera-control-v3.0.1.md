---
layout: default-layout
title: Camera Control - Dynamsoft Camera Enhancer JavaScript API
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK Camera Control.
keywords: camera enhancer, camera control, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: Camera Control
permalink: /programming/javascript/api-reference/camera-control-v3.0.1.html
---

# Camera Control

**Basic Control**

| Name| Description |
|---|---|
| [ifSkipCameraInspection](#ifskipcamerainspection) | Returns or sets whether to skip camera inspection at initialization to save time. |
| [ifSaveLastUsedCamera](#ifsavelastusedcamera) | Returns or sets whether to save the last used camera and resolution. |
| [getAllCameras()](#getallcameras) | Returns information of all available cameras on the device. |
| [selectCamera()](#selectcamera) | Chooses a camera as the video source. |
| [getSelectedCamera()](#getselectedcamera) | Returns information about the selected / current camera. |
| [open()](#open) | Turns on the camera to start streaming live video. |
| [close()](#close) | Stops video streaming and releases the camera. |
| [isOpen()](#isopen) | Returns whether the selected camera is turned on / occupied. |
| [pause()](#pause) | Pauses video streaming without releasing the camera. |
| [resume()](#resume) | Resumes video streaming. |
| [setResolution()](#setresolution) | Sets the resolution of the current video input. |
| [getResolution()](#getresolution) | Returns the resolution of the current video input. |
| [getResolutions()](#getresolutions) | Returns the resolutions supported by the current video input. |
| [videoSrc](#videosrc) | Sets or returns the source of the video. |

**Advanced Control**

| Name| Description |
|---|---|
| [setFrameRate()](#setframerate) | Adjusts the frame rate. |
| [getFrameRate()](#getframerate) | Returns the real-time frame rate. |
| [turnOnTorch()](#turnontorch) | Turns on the torch/flashlight if the current camera supports it. |
| [turnOffTorch()](#turnofftorch) | Turns off the torch/flashlight. |
| [setZoom()](#setzoom) | Sets the zoom level of the video. |
| [setFocus()](#setfocus) | Sets the focus mode and focus distance of the camera. |
| [getFocus()](#getfocus) | Gets the focus mode and focus distance of the camera. |
| [getCapabilities()](#getcapabilities) | Inspects and returns the capabilities of the selected camera. |
| [getCameraSettings()](#getcamerasettings) | Returns the current values for each constrainable property of the selected camera. |
| [setColorTemperature()](#setcolortemperature) | Adjusts the color temperature of the selected camera. |
| [setExposureCompensation()](#setexposurecompensation) | Sets the exposure compensation index of the selected camera. |

## ifSkipCameraInspection

Returns or sets whether to skip camera inspection at initialization to save time. Note that if a previously used camera is already available in the [localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage), the inspection is skipped automatically. Read more on [ifSaveLastUsedCamera](#ifsavelastusedcamera).

```typescript
ifSkipCameraInspection: boolean;
```

## ifSaveLastUsedCamera

Returns or sets whether to save the last used camera and resolution. This feature makes use of the [localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage) of the browser.

> NOTE
>
> This feature only works on mainstream browsers like Chrome, Firefox and Safari. Other browsers may change the device IDs dynamically thus making it impossible to track the camera.

```typescript
ifSaveLastUsedCamera: boolean;
```

## getAllCameras

Returns information of all available cameras on the device.

```typescript
getAllCameras(): Promise<VideoDeviceInfo[]>;
```

**Parameters**

None.

**Return value**

A promise resolving to an array of `VideoDeviceInfo` objects.

**Code Snippet**

```javascript
let cameras = await enhancer.getAllCameras();
if (cameras.length) {
    await enhancer.selectCamera(cameras[0]);
}
```

**See also**

[VideoDeviceInfo](interface/videodeviceinfo.html)

## selectCamera

Chooses a camera as the video source.

> If called before `open()` or `show()`, the selected camera will be used. Otherwise, the system will decide which one to use.

```typescript
selectCamera(cameraObjectOrDeviceID: VideoDeviceInfo | string): Promise<PlayCallbackInfo>;
```

**Parameters**

`cameraObjectOrDeviceID`: specifies the camera.

**Return value**

A promise resolving to a `PlayCallbackInfo` object.

**Code Snippet**

```javascript
let cameras = await enhancer.getAllCameras();
if (cameras.length) {
    await enhancer.selectCamera(cameras[0]);
}
```

**See also**

[PlayCallbackInfo](interface/playcallbackinfo.html)

## getSelectedCamera

Returns information about the selected / current camera.

```typescript
getSelectedCamera(): VideoDeviceInfo;
```

**Parameters**

None.

**Return value**

A `VideoDeviceInfo` object with details about the selected camera.

**Code Snippet**

```javascript
let camera = enhancer.getSelectedCamera();
console.log(camera.label);
```

**See also**

[VideoDeviceInfo](interface/videodeviceinfo.html)

## open

Turns on the camera to start streaming live video.

```typescript
open(appendOrShowUI?: boolean): Promise<PlayCallbackInfo>;
```

**Parameters**

`appendOrShowUI`: this parameter specifies how to handle the UI. When set to true, if the UI doesn't exist in the DOM tree, the CameraEnhancer instance will append it in the DOM and show it; if the UI already exists in the DOM tree but is hidden, it'll be displayed. When not set or set to false, it means not to change the original state of that UI: if it doesn't exist in the DOM tree, nothing shows up on the page; if it exists in the DOM tree, it may or may not show up depending on its original state.

> NOTE: if `setUIElement()` is not called before `open()`, the default UI Element will be used, which is equivalent to the following code:
>
> ```javascript
> await cameraEnhancer.setUIElement(Dynamsoft.DCE.CameraEnhancer.defaultUIElementURL);
> await cameraEnhancer.open(appendOrShowUI);
> ```
>
> If you want to use a different UI element, call API [`setUIElement()`](initialization.html#setuielement) beforehand.

**Return value**

A promise resolving to a `PlayCallbackInfo` object.

**See also**

[PlayCallbackInfo](interface/playcallbackinfo.html)

## close

Stops video streaming and releases the camera.

```typescript
close(hideUI?: boolean): void;
```

**Parameters**

`hideUI`: this parameter specifies how to handle the UI. When set to true, if the UI doesn't exist in the DOM tree or it exists but is hidden, nothing is done; if the UI already exists in the DOM tree and is shown, it'll be hidden. When not set or set to false, it means not to change the original state of that UI: if it doesn't exist in the DOM tree, nothing happens; if it exists in the DOM tree, it may or may not be hidden depending on its original state.

**Return value**

None.

## isOpen

Returns whether the selected camera is turned on / occupied.

```typescript
isOpen(): boolean;
```

**Parameters**

None.

**Return value**

`true` means the camera is turned on and `false` the opposite.

## pause

Pauses video streaming without releasing the camera.

```typescript
pause(): void;
```

**Parameters**

None.

**Return value**

None.

## resume

Resumes video streaming.

```typescript
resume(): void;
```

**Parameters**

None.

**Return value**

None.

## setResolution

Sets the resolution of the current video input. If the specified resolution is not exactly supported, the closest resolution will be applied.

> If called before `open()` or `show()`, the camera will use the set resolution when it opens. Otherwise, the default resolution is used, which is 1280 x 720.

```typescript
setResolution(widthOrResolution: number | number[], height: number): Promise<PlayCallbackInfo>;
```

**Parameters**

`width`: specifies the horizontal resolution.

`height`: specifies the vertical resolution.

**Return value**

A promise resolving to a `PlayCallbackInfo` object.

**Code Snippet**

```javascript
await enhancer.setResolution(width, height);
```

**See also**

[PlayCallbackInfo](interface/playcallbackinfo.html)

## getResolution

Returns the resolution of the current video input.

```typescript
getResolution(): [number, number];
```

**Parameters**

None.

**Return value**

An array of two numbers representing the resolution in the sequence of [width, height].

**Code Snippet**

```javascript
let resolution = enhancer.getResolution();
console.log(resolution[0] + " x " + resolution[1]);
```

## getResolutions

Returns the resolutions supported by the current video input.

> The returned resolutions are limited to these values "160 by 120", "320 by 240", "480 by 360", "640 by 480", "800 by 600", "960 by 720", "1280 by 720", "1920 by 1080", "2560 by 1440", "3840 by 2160".

```typescript
getResolutions(): Promise<Array<[number, number]>>;
```

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```javascript
const resolutions = await enhancer.getResolutions();
console.log(resolutions);
```

## setFrameRate

Adjusts the frame rate.

> At present, this method only works in Edge, Safari, Chrome and other Chromium-based browsers (Firefox is not supported). Also, it should be called when a camera is open.

```typescript
setFrameRate(rate: number): Promise<void>;
```

**Parameters**

`rate`: specifies the new frame rate.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```javascript
await enhancer.setFrameRate(10);
```

**See also**

[getCapabilities](#getcapabilities)

## getFrameRate

Returns the real-time frame rate.

```typescript
getFrameRate(): number;
```

**Parameters**

None.

**Return value**

The calculated real-time frame rate.

**Code Snippet**

```javascript
await enhancer.getFrameRate();
```

## turnOnTorch

Turns on the torch/flashlight if the current camera supports it.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
turnOnTorch(): Promise<void>;
```

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```javascript
await enhancer.turnOnTorch();
```

**See also**

[turnOffTorch](#turnofftorch)

[getCapabilities](#getcapabilities)

## turnOffTorch

Turns off the torch/flashlight.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
turnOffTorch(): Promise<void>;
```

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```javascript
await enhancer.turnOffTorch();
```

**See also**

[turnOnTorch](#turnontorch)

[getCapabilities](#getcapabilities)

## setZoom

Sets the zoom level of the video.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
setZoom(zoomValue: number): Promise<void>;
```

**Parameters**

`zoomValue`: specifies the zoom level.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```javascript
await enhancer.setZoom(2);
```

**See also**

[getCapabilities](#getcapabilities)

## setFocus

Sets the focus mode and focus distance of the camera.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
setFocus(mode: string, distance?: number): Promise<void>;
```

**Parameters**

`mode`: specifies the focus mode, the available values include `continuous` and `manual` .

`distance`: specifies the focus distance, only required when the `mode` is set to `manual` . Use [getCapabilities](#getcapabilities) to get the allowed value range.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```javascript
await enhancer.setFocus("manual", 400);
```

**See also**

[getCapabilities](#getcapabilities)

## getFocus

Gets the focus mode and the focus distance.

```typescript
getFocus(): {mode: string, distance?: number};
```

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```javascript
await enhancer.getFocus();
```

**See also**

[getCapabilities](#getcapabilities)

## getCapabilities

Inspects and returns the capabilities of the selected camera.

> At present, this method only works in Edge, Safari, Chrome and other Chromium-based browsers (Firefox is not supported). Also, it should be called when a camera is open.

```typescript
getCapabilities(): MediaTrackCapabilities;
```

**Parameters**

None.

**Return value**

A `MediaTrackCapabilities` object which specifies the values or range of values for each constrainable property of the current camera.

**Code Snippet**

```javascript
enhancer.getCapabilities();
/* Result sample
{
  aspectRatio: {max: 1280, min: 0.001388888888888889},
  brightness: {max: 64, min: -64, step: 1},
  colorTemperature: {max: 6500, min: 2800, step: 10},
  contrast: {max: 95, min: 0, step: 1},
  deviceId: "3a505c29a3312600ea0afd79f8e2b4ba4fba3e539257801ff1de8718c27f2bed",
  exposureMode: ["continuous", "manual"],
  exposureTime: {max: 10000, min: 39.0625, step: 39.0625},
  facingMode: [],
  focusDistance: {max: 1024, min: 0, step: 10},
  focusMode: ["continuous", "manual"],
  frameRate: {max: 30, min: 0},
  groupId: "35a82dcb7d5b0ef5bda550718d194f04a812c976175e926ccb81fb9d235d010f",
  height: {max: 720, min: 1},
  resizeMode: ["none", "crop-and-scale"],
  saturation: {max: 100, min: 0, step: 1},
  sharpness: {max: 7, min: 1, step: 1},
  whiteBalanceMode: ["continuous", "manual"],
  width: {max: 1280, min: 1}
}
*/
```

**See also**

[MediaTrackCapabilities](https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamTrack/getCapabilities)

## getCameraSettings

Returns the current values for each constrainable property of the selected camera.

```typescript
getCameraSettings(): MediaTrackSettings;
```

**Parameters**

None.

**Return value**

The current values for each constrainable property of the current camera in the form of a [MediaTrackSettings](https://developer.mozilla.org/en-US/docs/Web/API/MediaTrackSettings) object.

**Code Snippet**

```javascript
enhancer.getCameraSettings();
/* Result sample
{
  aspectRatio: 1.3333333333333333,
  brightness: 0,
  colorTemperature: 4600,
  contrast: 0,
  deviceId: "3a505c29a3312600ea0afd79f8e2b4ba4fba3e539257801ff1de8718c27f2bed",
  exposureMode: "continuous",
  exposureTime: 156.25,
  focusDistance: 120,
  focusMode: "continuous",
  frameRate: 30,
  groupId: "35a82dcb7d5b0ef5bda550718d194f04a812c976175e926ccb81fb9d235d010f",
  height: 480,
  resizeMode: "none",
  saturation: 73,
  sharpness: 2,
  whiteBalanceMode: "continuous",
  width: 640
}
*/
```

**See also**

[getCapabilities](#getcapabilities)

## setColorTemperature

Adjusts the color temperature of the selected camera.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
setColorTemperature(colorTemperatur: number): Promise<void>;
```

**Parameters**

`colorTemperatur`: specifies the new color temperature.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```javascript
await enhancer.setColorTemperature(5000);
```

**See also**

[getCapabilities](#getcapabilities)

## setExposureCompensation

Sets the exposure compensation index of the selected camera.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
setExposureCompensation(exposureCompensation: number): Promise<void>;
```

**Parameters**

`exposureCompensation`: specifies the new exposure compensation index.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```javascript
await enhancer.setExposureCompensation(-0.7);
```

**See also**

[getCapabilities](#getcapabilities)

## videoSrc

Sets or returns the source of the video.

> You can use this property to specify an existing video as the source to play which will be processed the same way as the video feed from a live camera.

```typescript
videoSrc: string | MediaStream | MediaSource | Blob;
```
