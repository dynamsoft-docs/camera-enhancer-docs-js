---
layout: default-layout
title: Camera Control - Dynamsoft Camera Enhancer JavaScript API
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK Camera Control.
keywords: camera enhancer, camera control, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: Camera Control
---

# Camera Control

**Basic Control**

| API Name | Description |
|---|---|
| [ifSkipCameraInspection](#ifskipcamerainspection) | Returns or sets whether to skip camera inspection at initialization to save time. |
| [ifSaveLastUsedCamera](#ifsavelastusedcamera) | Returns or sets whether to save the last used camera and resolution. |
| [getAllCameras()](#getallcameras) | Returns infomation of all available cameras on the device. |
| [selectCamera()](#selectcamera) | Chooses a camera as the video source. |
| [getSelectedCamera()](#getselectedcamera) | Returns information about the selected / current camera. |
| [open()](#open) | Turns on the camera to start streaming live video. |
| [close()](#close) | Stops video streaming and releases the camera. |
| [isOpen()](#isopen) | Returns whether the selected camera is turned on / occupied. |
| [pause()](#pause) | Pauses video streaming without releasing the camera. |
| [isPaused()](#ispaused) | Returns whether the video streaming is paused. |
| [resume()](#resume) | Resumes video streaming. |
| [setResolution()](#setresolution) | Sets the resolution of the current video input. |
| [getResolution()](#getresolution) | Returns the resolution of the current video input. |
| [getResolutions()](#getresolutions) | Returns the resolutions supported by the current video input. |
| [videoSrc](#videosrc) | Sets or returns the source of the video. |

**Advanced Control**

| API Name | Description |
|---|---|
| [setFrameRate()](#setframerate) | Adjusts the frame rate. |
| [getFrameRate()](#getframerate) | Returns the real-time frame rate. |
| [turnOnTorch()](#turnontorch) | Turns on the torch/flashlight if the current camera supports it. |
| [turnOffTorch()](#turnofftorch) | Turns off the torch/flashlight. |
| [getZoomSettings()](#getzoomsettings) | Returns the zoom settings. |
| [setZoom()](#setzoom) | Zooms the video stream. |
| [resetZoom()](#resetzoom) | Resets the zoom level of the video. |
| [getFocusSettings()](#getfocussettings) | Returns the focus settings. |
| [setFocus()](#setfocus) | Sets how the camera focuses. |
| [enableTapToFocus()](#enabletaptofocus) | Enables manual camera focus when clicking/tapping on the video. |
| [disableTapToFocus()](#disabletaptofocus) | Disables manual camera focus when clicking/tapping on the video. |
| [isTapToFocusEnabled()](#istaptofocusenabled) | Returns whether clicking/tapping on the video invokes the camera to focus. |
| [getCapabilities()](#getcapabilities) | Inspects and returns the capabilities of the selected camera. |
| [getCameraSettings()](#getcamerasettings) | Returns the current values for each constrainable property of the selected camera. |
| [getColorTemperature()](#getcolortemperature) | Returns the color temperature of the selected camera. |
| [setColorTemperature()](#setcolortemperature) | Adjusts the color temperature of the selected camera. |
| [getExposureCompensation()](#getexposurecompensation) | Returns the exposure compensation index of the selected camera. |
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

Returns infomation of all available cameras on the device.

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

* [VideoDeviceInfo](interface/videodeviceinfo.md)

## selectCamera

Chooses a camera as the video source.

> If called before `open()` or `show()` , the selected camera will be used. Otherwise, the system will decide which one to use.

```typescript
selectCamera(cameraObjectOrDeviceID: VideoDeviceInfo | string): Promise<PlayCallbackInfo>;
```

**Parameters**

`cameraObjectOrDeviceID` : specifies the camera.

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

* [PlayCallbackInfo](interface/playcallbackinfo.md)

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

* [VideoDeviceInfo](interface/videodeviceinfo.md)

## open

Turns on the camera to start streaming live video.

```typescript
open(appendOrShowUI?: boolean): Promise<PlayCallbackInfo>;
```

**Parameters**

`appendOrShowUI` : this parameter specifies how to handle the UI. When set to true, if the UI doesn't exist in the DOM tree, the CameraEnhancer instance will append it in the DOM and show it; if the UI already exists in the DOM tree but is hidden, it'll be displayed. When not set or set to false, it means not to change the original state of that UI: if it doesn't exist in the DOM tree, nothing shows up on the page; if it exists in the DOM tree, it may or may not show up depending on its original state.

> NOTE: if `setUIElement()` is not called before `open()` , the default UI Element will be used, which is equivalent to the following code:
>
> ```javascript
> await cameraEnhancer.setUIElement(Dynamsoft.DCE.CameraEnhancer.defaultUIElementURL); 
> await cameraEnhancer.open(appendOrShowUI); 
> ```
>
> If you want to use a different UI element, call API [ `setUIElement()` ](initialization.md#setuielement) beforehand.

**Return value**

A promise resolving to a `PlayCallbackInfo` object.

**See also**

* [PlayCallbackInfo](interface/playcallbackinfo.md)

## close

Stops video streaming and releases the camera.

```typescript
close(hideUI?: boolean): void;
```

**Parameters**

`hideUI` : this parameter specifies how to handle the UI. When set to true, if the UI doesn't exist in the DOM tree or it exists but is hidden, nothing is done; if the UI already exists in the DOM tree and is shown, it'll be hidden. When not set or set to false, it means not to change the original state of that UI: if it doesn't exist in the DOM tree, nothing happens; if it exists in the DOM tree, it may or may not be hidden depending on its original state.

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

## isPaused

Returns whether the video streaming is paused.

```typescript
isPaused(): boolean;
```

**Parameters**

None.

**Return value**

A Boolean value indicating whether the video streaming is paused.

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

> If called before `open()` or `show()` , the camera will use the set resolution when it opens. Otherwise, the default resolution is used, which is 1280 x 720.

```typescript
setResolution(widthOrResolution: number | number[], height: number): Promise<PlayCallbackInfo>;
```

**Parameters**

`width` : specifies the horizontal resolution.  
`height` : specifies the vertical resolution.

**Return value**

A promise resolving to a `PlayCallbackInfo` object.

**Code Snippet**

```javascript
await enhancer.setResolution(width, height);
```

**See also**

* [PlayCallbackInfo](interface/playcallbackinfo.md)

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

> NOTE
> 
> 1. The returned resolutions are limited to these values "160 by 120", "320 by 240", "480 by 360", "640 by 480", "800 by 600", "960 by 720", "1280 by 720", "1920 by 1080", "2560 by 1440", "3840 by 2160".
> 2. The SDK tests all these resolutions to find out which ones are supported. As a result, the method may be time-consuming.

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

`rate` : specifies the new frame rate.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```javascript
await enhancer.setFrameRate(10);
```

**See also**

* [getCapabilities](#getcapabilities)

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

* [turnOffTorch](#turnofftorch)
* [getCapabilities](#getcapabilities)

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

* [turnOnTorch](#turnontorch)
* [getCapabilities](#getcapabilities)

## getZoomSettings

Returns the zoom settings.

```typescript
getZoomSettings(): { factor: number };;
```

**Parameters**

None.

**Return value**

An object that describes the zoom settings. As of version 3.2, it contains only the zoom factor.

**Code Snippet**

```javascript
console.log(enhancer.getZoomSettings().factor);
```

## setZoom

Zooms the video.

> How it works:
>
> 1. If the camera supports zooming and the zoom factor is within its supported range, zooming is done directly by the camera.
> 2. If the camera does not support zooming, WebGL is used instead.
> 3. If the camera supports zooming but the zoom factor is beyond what it supports, the camera's maximum zoom is used, and WebGL is used to do the rest. (In this case, you may see a brief video flicker between the two zooming processes).

```typescript
setZoom(settings:{factor: number}): Promise<void>;
```

**Parameters**

`settings` : specifies how to zoom the video. As of version 3.2, the setting only contains a zoom factor.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```javascript
await enhancer.setZoom({
    factor: 3
});
```

**See also**

* [getCapabilities](#getcapabilities)

## resetZoom

Resets the zoom level of the video.

```typescript
resetZoom(): Promise<void>;
```

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```javascript
await enhancer.resetZoom();
```

## getFocusSettings

Returns the focus settings.

```typescript
type FocusArea = {
    centerPoint: { x: string, y: string };
    width: string;
    height: string;
};
type FocusSettings = {
    mode: string;
    distance: number;
    area: FocusArea;
};
getFocusSettings(): FocusSettings;
```

**Parameters**

None.

**Return value**

The current focus settings.

**Code Snippet**

```javascript
enhancer.getFocusSettings();
```

**See also**

* [getCapabilities](#getcapabilities)

## setFocus

Sets how the camera focuses.

> NOTE:
>
> 1. This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.
> 2. Typically, `continuous` mode works best. `manual` mode based on a specific area helps the camera focus on that particular area which may seem blurry under `continuous` mode. `manual` mode with specified distances is for those rare cases where the camera distance must be fine-tuned to get the best results.

```typescript
setFocus(settings: { mode: string } | { mode: 'manual', distance: number } | {
    mode: 'manual', area: {
        centerPoint: { x: string, y: string };
        // If not specified, the width is 1/6 of the video width or height, whichever is narrower
        width?: string;
        // If not specified, the height is 1/6 of the video width or height, whichever is narrower
        height?: string;
    }
}) => Promise<void>;
```

**Parameters**

`settings` : specifies the focus settings. Available `mode` options are `continuous` and `manual` . `distance` and `area` are only effective when `mode` is set to `manual` and they should not coexist. The combinations are shown in the code snippet.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

> The "continuous" mode invokes the camera to focus automatically and continuously. Use [getCapabilities()](#getcapabilities) to inspect whether the camera supports "continuous" mode.

```javascript
if (enhancer.getCapabilities().focusMode.find(mode => mode.localeCompare('continuous') == 0)) {
    await enhancer.setFocus({
        mode: "continuous"
    });
}
```

> The "manual" mode means manually specifying the focus distance.
> Use [getCapabilities()](#getcapabilities) to inspect the distance range.
>
> ```javascript
> enhancer.getCapabilities().focusDistance; > //{max: 1024, min: 0, step: 10}
> ```
>
> NOTE: If the set distance is between two allowed values, it will be rounded to the nearest value.

```javascript
await enhancer.setFocus({
    mode: "manual",
    distance: 200
});
```

> The SDK also has a built-in algorithm that adjusts focus distance based on the blurriness of a particular area. Specify the area with the parameter `area` .
>
> NOTE: the area is a rectangle defined by its center point and its width and height. All coordinates can be in pixels or percentages, such as "500px" or "50%". Percentages are based on stream dimensions.

```javascript
await enhancer.setFocus({
    mode: "manual",
    area: {
        centerPoint: {
            x: "50%",
            y: "50%"
        },
        width: "50%",
        height: "50%"
    }
});
```

**See also**

* [getCapabilities](#getcapabilities)

## enableTapToFocus

Enables manual camera focus when clicking/tapping on the video.

```typescript
enableTapToFocus() : void;
```

**Parameters**

None.

**Return value**

None.

**Code Snippet**

```javascript
enhancer.enableTapToFocus();
```

## disableTapToFocus

Disables manual camera focus when clicking/tapping on the video.

```typescript
disableTapToFocus() : void;
```

**Parameters**

None.

**Return value**

None.

**Code Snippet**

```javascript
enhancer.disableTapToFocus();
```

## isTapToFocusEnabled

Returns whether clicking/tapping on the video invokes the camera to focus.

```typescript
isTapToFocusEnabled() : boolean;
```

**Parameters**

None.

**Return value**

`true` means clicking/tapping on the video will invoke the camera to focus. `false` means clicking/tapping on the video does nothing.

**Code Snippet**

```javascript
if (enhancer.isTapToFocusEnabled()) {
    console.log("You can tap or click on the video to focus!");
}
```

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

* [MediaTrackCapabilities](https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamTrack/getCapabilities)

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

* [getCapabilities](#getcapabilities)

## getColorTemperature

Returns the color temperature of the selected camera.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
getColorTemperature(): number;
```

## setColorTemperature

Adjusts the color temperature of the selected camera.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
setColorTemperature(colorTemperatur: number): Promise<void>;
```

**Parameters**

`colorTemperatur` : specifies the new color temperature.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```javascript
await enhancer.setColorTemperature(5000);
```

**See also**

* [getCapabilities](#getcapabilities)

## getExposureCompensation

Returns the exposure compensation index of the selected camera.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
getExposureCompensation(): number;
```

## setExposureCompensation

Sets the exposure compensation index of the selected camera.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
setExposureCompensation(exposureCompensation: number): Promise<void>;
```

**Parameters**

`exposureCompensation` : specifies the new exposure compensation index.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```javascript
await enhancer.setExposureCompensation(-0.7);
```

**See also**

* [getCapabilities](#getcapabilities)

## videoSrc

Sets or returns the source of the video.

> You can use this property to specify an existing video as the source to play which will be processed the same way as the video feed from a live camera.
>
> When playing an existing video, the camera selection and video selection boxes will be hidden.

```typescript
videoSrc: string | MediaStream | MediaSource | Blob;
```