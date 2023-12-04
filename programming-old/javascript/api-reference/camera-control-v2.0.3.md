---
layout: default-layout
title: Camera Control - Dynamsoft Camera Enhancer JavaScript API
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK Camera Control.
keywords: camera enhancer, camera control, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: Camera Control
permalink: /programming/javascript/api-reference/camera-control-v2.0.3.html
---

# Camera Control

**Basic Control**

| API Name | Description |
|---|---|
| [getAllCameras()](#getallcameras) | Returns information of all available cameras on the device. |
| [selectCamera()](#selectcamera) | Chooses a camera as the video source. |
| [getSelectedCamera()](#getselectedcamera) | Returns information about the selected / current camera. |
| [open()](#open) | Turns on the camera to start streaming live video. |
| [close()](#close) | Stops video streaming and releases the camera. |
| [isOpen()](#isOpen) | Returns whether the selected camera is turned on / occupied. |
| [onPlayed](#onplayed) | Defines a callback which is triggered when the video streaming first starts or restarts when its source (camera) or resolution changes. |
| [pause()](#pause) | Pauses video streaming without releasing the camera. |
| [resume()](#resume) | Resumes video streaming. |
| [setResolution()](#setresolution) | Sets the resolution of the current video input. |
| [getResolution()](#getresolution) | Returns the resolution of the current video input. |

**Advanced Control**

| API Name | Description |
|---|---|
| [setFrameRate()](#setframerate) | Adjusts the frame rate. |
| [getFrameRate()](#getframerate) | Returns the real-time frame rate. |
| [turnOnTorch()](#turnontorch) | Turns on the torch/flashlight. |
| [turnOffTorch()](#turnofftorch) | Turns off the torch/flashlight. |
| [setZoom()](#setzoom) | Sets the zoom level of the video. |
| [getCapabilities()](#getcapabilities) | Inspects and returns the capabilities of the selected camera. |
| [setColorTemperature()](#setcolortemperature) | Adjusts the color temperature of the selected camera. |
| [setExposureCompensation()](#setexposurecompensation) | Sets the exposure compensation index of the selected camera. |

<!--| [getCameraSettings()](#getcamerasettings) | Returns the current values for each constrainable property of the selected camera. |-->

## getAllCameras

Returns information of all available cameras on the device.

```typescript
getAllCameras(): Promise<VideoDeviceInfo[]>
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

* [VideoDeviceInfo](interface/videodeviceinfo.html)

## selectCamera

Chooses a camera as the video source.

> If called before `open()` or `show()`, the selected camera will be used. Otherwise, the system will decide which one to use.

```typescript
selectCamera(cameraObjectOrDeviceID: VideoDeviceInfo | string): Promise<PlayCallbackInfo>
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

* [PlayCallbackInfo](interface/playcallbackinfo.html)

## getSelectedCamera

Returns information about the selected / current camera.

```typescript
getSelectedCamera(): Promise<VideoDeviceInfo | null>
```

**Parameters**

None.

**Return value**

A promise resolving to a `VideoDeviceInfo` object.

**Code Snippet**

```javascript
let camera = await enhancer.getSelectedCamera();
```

**See also**

* [VideoDeviceInfo](interface/videodeviceinfo.html)

## open

Turns on the camera to start streaming live video.

```typescript
open(): void
```

**Parameters**

None.

**Return value**

None.

## close

Stops video streaming and releases the camera.

```typescript
close(): void
```

**Parameters**

None.

**Return value**

None.

## isOpen

Returns whether the selected camera is turned on / occupied.

```typescript
isOpen(): boolean
```

**Parameters**

None.

**Return value**

`true` means the camera is turned on and `false` the opposite.

## onPlayed

Defines a callback which is triggered when the video streaming first starts or restarts when its source (camera) or resolution changes.

```typescript
onPlayed: (playCallBackInfo:PlayCallBackInfo) => {}
```

**Arguments**

`playCallBackInfo`: returns the resolution of the video input.

**Code Snippet**

```javascript
let pEnhancer = null;
(async () => {
    let enhancer = await (pEnhancer = pEnhancer || Dynamsoft.DCE.CameraEnhancer.createInstance());
    enhancer.onPlayed = playCallBackInfo => {
        console.log(playCallBackInfo.width);
    };
    await enhancer.open();
})();
```

**See also**

* [PlayCallbackInfo](interface/playcallbackinfo.html)

## pause

Pauses video streaming without releasing the camera.

```typescript
pause(): void
```

**Parameters**

None.

**Return value**

None.

## resume()

Resumes video streaming.

```typescript
resume(): void
```

**Parameters**

None.

**Return value**

None.

## setResolution

Sets the resolution of the current video input. If the specified resolution is not exactly supported, the closest resolution will be applied.

```typescript
setResolution(width: number, height: number): Promise<PlayCallbackInfo>
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

* [PlayCallbackInfo](interface/playcallbackinfo.html)

## getResolution

Returns the resolution of the current video input.

```typescript
getResolution(): [number, number]
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

## setFrameRate

Adjusts the frame rate.

> At present, this method only works in Edge, Safari, Chrome and other Chromium-based browsers (Firefox is not supported). Also, it should be called when a camera is open.

```typescript
setFrameRate(rate: number): Promise<void>
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

Turns on the torch/flashlight.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
turnOnTorch(): Promise<void>
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
turnOffTorch(): Promise<void>
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

## setZoom

Sets the zoom level of the video.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
setZoom(zoomValue: number): Promise<void>
```

**Parameters**

`zoomValue` : specifies the zoom level.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```javascript
await enhancer.setZoom(2);
```

**See also**

* [getCapabilities](#getcapabilities)

## getCapabilities

Inspects and returns the capabilities of the selected camera.

```typescript
getCapabilities(): MediaTrackCapabilities
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

<!--
## getCameraSettings

Returns the current values for each constrainable property of the selected camera.

```typescript
getCameraSettings(): any
```

**Parameters**

None.

**Return value**

The current values for each constrainable property of the current camera

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
-->
## setColorTemperature

Adjusts the color temperature of the selected camera.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
setColorTemperature(colorTemperatur: number): Promise<void>
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

## setExposureCompensation

Sets the exposure compensation index of the selected camera.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
setExposureCompensation(exposureCompensation: number): Promise<void>
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
