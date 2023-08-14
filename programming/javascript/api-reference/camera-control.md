---
layout: default-layout
title: Camera Control - Dynamsoft Camera Enhancer JavaScript API
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK Camera Control.
keywords: camera enhancer, camera control, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: Camera Control
permalink: /programming/javascript/api-reference/camera-control.html
---

# Class CameraEnhancer

## Basic Camera Control

| API Name                                              | Description                                                                           |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------- |
| [getAllCameras()](#getallcameras)                     | Returns information of all available cameras on the device.                            |
| [selectCamera()](#selectcamera)                       | Chooses a camera as the video source.                                                 |
| [getSelectedCamera()](#getselectedcamera)             | Returns information about the selected / current camera.                              |
| [getCameraState()](#getcamerastate)                   | Returns the state of the selected camera which could be "opening", "open" or "closed" |
| [open()](#open)                                       | Turns on the camera to start streaming live video.                                    |
| [close()](#close)                                     | Stops video streaming and releases the camera.                                        |
| [isOpen()](#isopen)                                   | Returns whether the selected camera is turned on / occupied.                          |
| [pause()](#pause)                                     | Pauses video streaming without releasing the camera.                                  |
| [isPaused()](#ispaused)                               | Returns whether the video streaming is paused.                                        |
| [resume()](#resume)                                   | Resumes video streaming.                                                              |
| [setResolution()](#setresolution)                     | Sets the resolution of the selected camera.                                           |
| [getResolution()](#getresolution)                     | Returns the resolution of the selected camera.                                        |
| [getAvailableResolutions()](#getavailableresolutions) | Returns the resolutions supported by the selected camera.                             |
| [testCameraAccess()](#testcameraaccess)               | Tests whether there is an available camera.                                           |
| [ifSaveLastUsedCamera](#ifsavelastusedcamera)         | Returns or sets whether to save the last used camera and resolution.                  |
| [videoSrc](#videosrc)                                 | Sets or returns the source of the video.                                              |

## Advanced Camera Control

| API Name                                              | Description                                                                        |
| ----------------------------------------------------- | ---------------------------------------------------------------------------------- |
| [setFrameRate()](#setframerate)                       | Adjusts the frame rate.                                                            |
| [getFrameRate()](#getframerate)                       | Returns the real-time frame rate.                                                  |
| [turnOnTorch()](#turnontorch)                         | Turns on the torch/flashlight if the current camera supports it.                   |
| [turnOffTorch()](#turnofftorch)                       | Turns off the torch/flashlight.                                                    |
| [getZoomSettings()](#getzoomsettings)                 | Returns the zoom settings.                                                         |
| [setZoom()](#setzoom)                                 | Zooms the video stream.                                                            |
| [resetZoom()](#resetzoom)                             | Resets the zoom level of the video.                                                |
| [getFocusSettings()](#getfocussettings)               | Returns the focus settings.                                                        |
| [setFocus()](#setfocus)                               | Sets how the camera focuses.                                                       |
| [getCapabilities()](#getcapabilities)                 | Inspects and returns the capabilities of the selected camera.                      |
| [getCameraSettings()](#getcamerasettings)             | Returns the current values for each constrainable property of the selected camera. |
| [getColorTemperature()](#getcolortemperature)         | Returns the color temperature of the selected camera.                              |
| [setColorTemperature()](#setcolortemperature)         | Adjusts the color temperature of the selected camera.                              |
| [getExposureCompensation()](#getexposurecompensation) | Returns the exposure compensation index of the selected camera.                    |
| [setExposureCompensation()](#setexposurecompensation) | Sets the exposure compensation index of the selected camera.                       |
| [setAutoZoomRange()](#setautozoomrange)               | Sets the range (minimum to maximum) for zoom when it is done automatically.        |
| [getAutoZoomRange()](#getautozoomrange)               | Returns the auto zoom range.                                                       |
| [enableEnhancedFeatures()](#enableenhancedfeatures)   | Enables the specified enhanced features.                                           |
| [disableEnhancedFeatures()](#disableenhancedfeatures) | Disables the specified enhanced features.                                          |

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

## getCameraState

Returns the state of the selected camera which could be "opening", "open" or "closed".

```typescript
getCameraState(): string;
```

**Parameters**

None.

**Return value**

A string indicating the camera state, it is either "opening", "open" or "closed".

**Code Snippet**

```javascript
let state = enhancer.getCameraState();
console.log("The camera is " + state);
```

## open

Turns on the camera to start streaming live video.

```typescript
open(): Promise<PlayCallbackInfo>;
```

**Parameters**

None.

**Return value**

A promise resolving to a `PlayCallbackInfo` object.

**Code Snippet**

```html
<div id="enhancerUIContainer" style="width:1280px;height:720px;">
```

```javascript
let view = await Dynamsoft.DCE.CameraView.createInstance();
document.getElementById("enhancerUIContainer").append(view.getUIElement());
let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(view);
await enhancer.open();
```

**See also**

* [PlayCallbackInfo](interface/playcallbackinfo.md)

## close

Stops video streaming and releases the camera.

```typescript
close(): void;
```

**Parameters**

None.

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
resume(): Promise<void>;
```

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

## setResolution

Sets the resolution of the selected camera. If the specified resolution is not exactly supported, the closest resolution will be applied.

> If called before `open()` or `show()` , the camera will use the set resolution when it opens. Otherwise, the default resolution is used, which is 1280 x 720.

```typescript
setResolution(resolution: Resolution): Promise<PlayCallbackInfo>;
```

**Parameters**

`resolution` : specifies the resolution. 

**Return value**

A promise resolving to a `PlayCallbackInfo` object.

**Code Snippet**

```javascript
await enhancer.setResolution({width:1280, height:720});
```

**See also**

* [Resolution](interface/resolution.md)

## getResolution

Returns the resolution of the selected camera.

```typescript
getResolution(): Resolution;
```

**Parameters**

None.

**Return value**

The resolution.

**Code Snippet**

```javascript
let resolution = enhancer.getResolution();
console.log(resolution.width + " x " + resolution.height);
```

**See also**

* [Resolution](interface/resolution.md)

## getAvailableResolutions

Returns the resolutions supported by the selected camera.

> NOTE
> 
> 1. The returned resolutions are limited to these values "160 by 120", "320 by 240", "480 by 360", "640 by 480", "800 by 600", "960 by 720", "1280 by 720", "1920 by 1080", "2560 by 1440", "3840 by 2160".
> 2. The SDK tests all these resolutions to find out which ones are supported. As a result, the method may be time-consuming.

```typescript
getAvailableResolutions(): Promise<Array<Resolution>>;
```

**Parameters**

None.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```javascript
const resolutions = await enhancer.getAvailableResolutions();
console.log(resolutions);
```

## testCameraAccess

Tests whether there is an available camera.

```typescript
static testCameraAccess(): Promise<{ ok: boolean, message: string }>;
```

**Parameters**

None.

**Return value**

A promise resolving to a object containing two `properties` ok and `message`.

**Code Snippet**

```javascript
const testResponse = await Dynamsoft.DCE.CameraEnhancer.testCameraAccess();
if (testResponse.ok) {
    console.log(testResponse.message);
}
```

## ifSaveLastUsedCamera

Returns or sets whether to save the last used camera and resolution. This feature makes use of the [localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage) of the browser.

> NOTE
>
> This feature only works on mainstream browsers like Chrome, Firefox and Safari. Other browsers may change the device IDs dynamically thus making it impossible to track the camera.

```typescript
ifSaveLastUsedCamera: boolean;
```

## videoSrc

Sets or returns the source of the video.

> 1. You can use this property to specify an existing video as the source to play which will be processed the same way as the video feed from a live camera.
>
> 2. When playing an existing video, the camera selection and video selection boxes will be hidden.

```typescript
videoSrc: string | MediaStream | MediaSource | Blob;
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
getZoomSettings(): { factor: number };
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
}): Promise<void>;
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

## setAutoZoomRange

Sets the range (minimum to maximum) for zoom when it is done automatically.

```typescript
setAutoZoomRange(range: { min: number, max: number }): void;
```

**Parameters**

* `range`: specifies the zoom range (from minimum value to maximum value).

**Return value**

None.

**Code Snippet**

```javascript
enhancer.setAutoZoomRange({min: 1, max: 5});
```

## getAutoZoomRange

Returns the auto zoom range.

```typescript
getAutoZoomRange(): { min: number, max: number };
```

**Parameters**

None.

**Return value**

The zoom range.

**Code Snippet**

```javascript
let zoomRange = enhancer.getAutoZoomRange();
```

## enableEnhancedFeatures

Enables the specified enhanced features.

```typescript
enableEnhancedFeatures(features: EnumEnhancedFeatures): void;
```

**Parameters**

* `features`: specifies the features to enable.

**Return value**

None.

**Code Snippet**

```javascript
await enhancer.enableEnhancedFeatures(EnumEnhancedFeatures.EF_AUTO_ZOOM);
```

**See also**

* [EnumEnhancedFeatures](enumerations/enumenhancedfeatures.md)

## disableEnhancedFeatures

Disables the specified enhanced features.

```typescript
disableEnhancedFeatures(features: EnumEnhancedFeatures): void;
```

**Parameters**

* `features`: specifies the features to disable.

**Return value**

None.

**Code Snippet**

```javascript
await enhancer.disableEnhancedFeatures(EnumEnhancedFeatures.EF_AUTO_ZOOM);
```

**See also**

* [EnumEnhancedFeatures](enumerations/enumenhancedfeatures.md)
