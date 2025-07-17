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

# CameraEnhancer - Camera Control

**Basic Camera Control**

| Name                                                | Description                                                                                                                    |
| --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| [cameraOpenTimeout](#cameraOpenTimeout)             | Specifies the timeout in milliseconds for opening the camera.                                                                  |
| [close](#close)                                     | Closes the currently active camera and stops the video stream.                                                                 |
| [getAllCameras](#getAllCameras)                     | Retrieves a list of all available video input devices (cameras) on the current device.                                         |
| [getAvailableResolutions](#getAvailableResolutions) | Retrieves a list of available resolutions supported by the currently selected camera.                                          |
| [getCameraState](#getCameraState)                   | Retrieves the current state of the camera.                                                                                     |
| [getResolution](#getResolution)                     | Gets the current resolution of the video stream.                                                                               |
| [getSelectedCamera](#getSelectedCamera)             | Returns the currently selected camera device.                                                                                  |
| [getVideoSettings](#getVideoSettings)               | Retrieves the current video settings applied to the camera stream.                                                             |
| [ifSaveLastUsedCamera](#ifSaveLastUsedCamera)       | Determines whether the last used camera settings should be saved and reused the next time the `CameraEnhancer` is initialized. |
| [ifSkipCameraInspection](#ifSkipCameraInspection)   | Determines whether to skip the initial camera inspection process.                                                              |
| [isOpen](#isOpen)                                   | Checks if the camera is currently open and streaming video.                                                                    |
| [isPaused](#isPaused)                               | Checks if the video stream is currently paused.                                                                                |
| [open](#open)                                       | Opens the currently selected camera and starts the video stream.                                                               |
| [pause](#pause)                                     | Pauses the video stream without closing the camera.                                                                            |
| [resume](#resume)                                   | Resumes the video stream from a paused state.                                                                                  |
| [selectCamera](#selectCamera)                       | Selects a specific camera for use by the `CameraEnhancer`.                                                                     |
| [setResolution](#setResolution)                     | Sets the resolution of the video stream to a specified value.                                                                  |
| [testCameraAccess](#testCameraAccess)               | Tests whether the application has access to the camera.                                                                        |
| [updateVideoSettings](#updateVideoSettings)         | Updates the video settings for the camera stream with new constraints.                                                         |
| [videoSrc](#videoSrc)                               | Sets or returns the source URL for the video stream to be used by the `CameraEnhancer`.                                        |

**Advanced Camera Control**

| Name                                                | Description                                                                     |
| --------------------------------------------------- | ------------------------------------------------------------------------------- |
| [disableEnhancedFeatures](#disableEnhancedFeatures) | Disables one or more previously enabled enhanced features.                      |
| [enableEnhancedFeatures](#enableEnhancedFeatures)   | Enables one or more enhanced features that require a license.                   |
| [getAutoZoomRange](#getAutoZoomRange)               | Retrieves the current auto zoom range settings for the camera.                  |
| [getCameraSettings](#getCameraSettings)             | Retrieves the current settings of the camera.                                   |
| [getCapabilities](#getCapabilities)                 | Gets the capabilities of the current camera.                                    |
| [getColorTemperature](#getColorTemperature)         | Retrieves the current color temperature setting of the camera's video feed.     |
| [getExposureCompensation](#getExposureCompensation) | Retrieves the current exposure compensation setting of the camera's video feed. |
| [getFocusSettings](#getFocusSettings)               | Retrieves the current focus settings of the camera.                             |
| [getFrameRate](#getFrameRate)                       | Retrieves the current frame rate of the camera's video stream.                  |
| [getZoomSettings](#getZoomSettings)                 | Retrieves the current zoom settings of the camera.                              |
| [resetZoom](#resetZoom)                             | Resets the zoom level of the camera to its default value.                       |
| [setAutoZoomRange](#setAutoZoomRange)               | Sets the auto zoom range for the camera.                                        |
| [setColorTemperature](#setColorTemperature)         | Sets the color temperature of the camera's video feed.                          |
| [setExposureCompensation](#setExposureCompensation) | Sets the exposure compensation of the camera's video feed.                      |
| [setFocus](#setFocus)                               | Sets the focus mode of the camera.                                              |
| [setFrameRate](#setFrameRate)                       | Sets the frame rate of the camera's video stream.                               |
| [setZoom](#setZoom)                                 | Sets the zoom level of the camera.                                              |
| [turnOffTorch](#turnOffTorch)                       | Turns off the camera's torch (flashlight) mode.                                 |
| [turnOnTorch](#turnOnTorch)                         | Turns on the camera's torch (flashlight) mode, if supported.                    |

## cameraOpenTimeout

Specifies the timeout in milliseconds for opening the camera. 

This property sets a limit on how long the `CameraEnhancer` will attempt to open the camera before timing out. It can be adjusted to accommodate different devices and scenarios, ensuring that the application does not hang indefinitely while trying to access the camera.

> NOTE
> 
> - The default value is 4000 ms.
> - Setting 0 means canceling the timeout or waiting indefinitely.

```typescript
cameraOpenTimeout: number;
```

**Code Snippet**

```javascript
// Set the timeout to 10 seconds.
cameraEnhancer.cameraOpenTimeout = 10000;
```

## close

Closes the currently active camera and stops the video stream.

```typescript
close(): void;
```

**Parameters**

None.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.close();
```

## getAllCameras

Retrieves a list of all available video input devices (cameras) on the current device.

```typescript
getAllCameras(): Promise<Array<VideoDeviceInfo>>;
```

**Parameters**

None.

**Return value**

A promise that resolves with an array of `VideoDeviceInfo` objects representing each available camera.

**Code Snippet**

```javascript
let cameras = await cameraEnhancer.getAllCameras();
if (cameras.length) {
    await cameraEnhancer.selectCamera(cameras[0]);
}
```

**See also**

[VideoDeviceInfo](./interface/videodeviceinfo.md)

## getAvailableResolutions

Retrieves a list of available resolutions supported by the currently selected camera.

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

A promise that resolves with an array of `Resolution` objects representing each supported resolution.

**Code Snippet**

```javascript
const resolutions = await cameraEnhancer.getAvailableResolutions();
console.log(resolutions);
```

## getCameraState
 
Retrieves the current state of the camera.

```typescript
getCameraState(): string;
```

**Parameters**

None.

**Return value**

A string indicating the camera's current state, which can be "opening", "open", or "closed".

**Code Snippet**

```javascript
let state = cameraEnhancer.getCameraState();
console.log("The camera is " + state);
```

## getResolution

Gets the current resolution of the video stream.

```typescript
getResolution(): Resolution;
```

**Parameters**

None.

**Return value**

The current `Resolution` of the video stream.

**Code Snippet**

```javascript
let resolution = cameraEnhancer.getResolution();
console.log(resolution.width + " x " + resolution.height);
```

**See also**

[Resolution](./interface/resolution.md)

## getSelectedCamera

Returns the currently selected camera device.

```typescript
getSelectedCamera(): VideoDeviceInfo;
```

**Parameters**

None.

**Return value**

The `VideoDeviceInfo` object representing the currently active camera.

**Code Snippet**

```javascript
let camera = cameraEnhancer.getSelectedCamera();
console.log(camera.label);
```

**See also**

[VideoDeviceInfo](./interface/videodeviceinfo.md)

## getVideoSettings

Retrieves the current video settings applied to the camera stream.

```typescript
getVideoSettings(): MediaStreamConstraints
```

**Parameters**

None.

**Return value**

The current `MediaStreamConstraints` object representing the video stream's settings.

**Code Snippet**

```javascript
cameraEnhancer.getVideoSettings();
```

**See also**

[MediaStreamConstraints](https://developer.mozilla.org/en-US/docs/Web/API/Media_Streams_API/Constraints)

## ifSaveLastUsedCamera

Determines whether the last used camera settings should be saved and reused the next time the `CameraEnhancer` is initialized. 

The default is `false`.

When set to `true`, the enhancer attempts to restore the previously used camera settings, offering a more seamless user experience across sessions.

> NOTE
> - This feature makes use of the [localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage) of the browser.
> - This feature only works on mainstream browsers like Chrome, Firefox, and Safari. Other browsers may change the device IDs dynamically thus making it impossible to track the camera.

```typescript
ifSaveLastUsedCamera: boolean;
```

**Code Snippet**

```javascript
cameraEnhancer.ifSaveLastUsedCamera = true;
```

## ifSkipCameraInspection

Determines whether to skip the initial camera inspection process.

The default is `false`, which means to opt for an optimal rear camera at the first `open()`.

Setting this property to `true` bypasses the automatic inspection and configuration that typically occurs when a camera connection is established. This can be useful for scenarios where the default inspection process may not be desirable or necessary.

Note that if a previously used camera is already available in the [localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage), the inspection is skipped automatically. Read more on [ifSaveLastUsedCamera](camera-control.md#ifsavelastusedcamera).

```typescript
ifSkipCameraInspection: boolean;
```

**Code Snippet**

```javascript
cameraEnhancer.ifSkipCameraInspection = true;
```

## isOpen

Checks if the camera is currently open and streaming video.

```typescript
isOpen(): boolean;
```

**Parameters**

None.

**Return value**

Boolean indicating whether the camera is open (`true`) or not (`false`).

**Code Snippet**

```javascript
cameraEnhancer.isOpen();
```

## isPaused

Checks if the video stream is currently paused.

```typescript
isPaused(): boolean;
```

**Parameters**

None.

**Return value**

Boolean indicating whether the video stream is paused (`true`) or active (`false`).

**Code Snippet**

```javascript
cameraEnhancer.isPaused();
```

## open

Opens the currently selected camera and starts the video stream.

```typescript
open(): Promise<PlayCallbackInfo>;
```

**Parameters**

None.

**Return value**

A promise that resolves with a `PlayCallbackInfo` object with details about the operation's outcome.

**Code Snippet**

```javascript
await cameraEnhancer.open();
```

**See also**

[PlayCallbackInfo](./interface/playcallbackinfo.md)

## pause

Pauses the video stream without closing the camera.

```typescript
pause(): void;
```

**Parameters**

None.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.pause();
```

## resume

Resumes the video stream from a paused state.

```typescript
resume(): Promise<void>;
```

**Parameters**

None.

**Return value**

A promise that resolves when the video stream resumes. It does not provide any value upon resolution.

**Code Snippet**

```javascript
await cameraEnhancer.resume();
```

## selectCamera

Selects a specific camera for use by the `CameraEnhancer`. The camera can be specified by a `VideoDeviceInfo` object or by its device ID.

> If called before `open()` or `show()`, the selected camera will be used. Otherwise, the system will decide which one to use.

```typescript
selectCamera(cameraObjectOrDeviceID: VideoDeviceInfo | string): Promise<PlayCallbackInfo>;
```

**Parameters**

`cameraObjectOrDeviceID`: the `VideoDeviceInfo` object or device ID string of the camera to select.

**Return value**

A promise that resolves with a `PlayCallbackInfo` object indicating the outcome of the camera selection operation.

**Code Snippet**

```javascript
let cameras = await cameraEnhancer.getAllCameras();
if (cameras.length) {
    await cameraEnhancer.selectCamera(cameras[0]);
}
```

**See also**

[PlayCallbackInfo](./interface/playcallbackinfo.md)

## setResolution

Sets the resolution of the video stream to a specified value. If the specified resolution is not exactly supported, the closest resolution will be applied.

> If called before `open()` or `show()`, the camera will use the set resolution when it opens. Otherwise, the default resolution used is 1920x1080 on desktop and 1280x720 on mobile devices.

```typescript
setResolution(resolution: Resolution): Promise<PlayCallbackInfo>;
```

**Parameters**

`resolution`: the `Resolution` to which the video stream should be set.

**Return value**

A promise that resolves with a `PlayCallbackInfo` object with details about the operation's outcome.

**Code Snippet**

```javascript
await cameraEnhancer.setResolution({width:1280, height:720});
```

**See also**

[Resolution](./interface/resolution.md)

## testCameraAccess

Tests whether the application has access to the camera. This static method can be used before initializing a `CameraEnhancer` instance to ensure that the device's camera can be accessed, providing a way to handle permissions or other access issues preemptively.

> This method offers the additional advantage of accelerating the camera opening process for the first time.

```typescript
static testCameraAccess(): Promise<{ ok: boolean, message: string }>;
```

**Parameters**

None.

**Return value**

A promise that resolves with an object containing:
- `ok`: Boolean indicating whether camera access is available.
- `message`: A string providing additional information or the reason why camera access is not available, if applicable.

**Code Snippet**

```javascript
const testResponse = await Dynamsoft.DCE.CameraEnhancer.testCameraAccess();
if (testResponse.ok) {
    console.log(testResponse.message);
}
```

## updateVideoSettings

Updates the video settings for the camera stream with new constraints.

```typescript
updateVideoSettings(constraints: MediaStreamConstraints): Promise<void>;
```

**Parameters**

`constraints`: the new `MediaStreamConstraints` to apply to the video stream.

**Return value**

A promise that resolves when the new `MediaStreamConstraints` is applied. It does not provide any value upon resolution.

**Code Snippet**

```js
await cameraEnhancer.updateVideoSettings({
    video: {
        width: {
            ideal: 1280
        },
        height: {
            ideal: 720
        },
        facingMode: {
            ideal: 'environment'
        }
    }
});
```

**See also**

[MediaStreamConstraints](https://developer.mozilla.org/en-US/docs/Web/API/Media_Streams_API/Constraints)

[PlayCallbackInfo](./interface/playcallbackinfo.md)

## videoSrc

Sets or returns the source URL for the video stream to be used by the `CameraEnhancer`.

> 1. You can use this property to specify an existing video as the source to play which will be processed the same way as the video feed from a live camera.
>
> 2. When playing an existing video, the camera selection and video selection boxes will be hidden.

```typescript
videoSrc: string;
```

**Code Snippet**

```js
cameraEnhancer.videoSrc = "PATH-TO-A-MP4";
```

## disableEnhancedFeatures

Disables one or more previously enabled enhanced features.

```typescript
disableEnhancedFeatures(enhancedFeatures: EnumEnhancedFeatures): void;
```

**Parameters**

`enhancedFeatures`: an enum value or a bitwise combination of `EnumEnhancedFeatures` indicating the features to be disabled.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.disableEnhancedFeatures(Dynamsoft.DCE.EnumEnhancedFeatures.EF_AUTO_ZOOM);
```

**See also**

[EnumEnhancedFeatures](enum/enumenhancedfeatures.md)

## enableEnhancedFeatures

Enables one or more enhanced features. 

- The enhanced features require a license, and only take effect when used in conjunction with other functional products under the Dynamsoft Capture Vision（DCV）architecture.
- `EF_ENHANCED_FOCUS` and `EF_TAP_TO_FOCUS` only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
enableEnhancedFeatures(enhancedFeatures: EnumEnhancedFeatures): Promise<void>;
```

**Parameters**

`enhancedFeatures`: an enum value or a bitwise combination of `EnumEnhancedFeatures` indicating the features to be enabled.

**Return value**

None.

**Code Snippet**

```javascript
// License is required.
Dynamsoft.License.LicenseManager.initLicense("YOUR-LICENSE");
await cameraEnhancer.enableEnhancedFeatures(Dynamsoft.DCE.EnumEnhancedFeatures.EF_AUTO_ZOOM);
```

**See also**

[EnumEnhancedFeatures](enum/enumenhancedfeatures.md)

## getAutoZoomRange

Retrieves the current auto zoom range settings for the camera.

```typescript
getAutoZoomRange(): { min: number, max: number };
```

**Parameters**

None.

**Return value**

An object representing the current auto zoom range, including the minimum and maximum zoom levels.

**Code Snippet**

```javascript
let zoomRange = cameraEnhancer.getAutoZoomRange();
```

## getCameraSettings

Retrieves the current settings of the camera.

```typescript
getCameraSettings(): MediaTrackSettings;
```

**Parameters**

None.

**Return value**

The `MediaTrackSettings` object representing the current settings of the camera's video track.

**Code Snippet**

```javascript
cameraEnhancer.getCameraSettings();
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

[MediaTrackSettings](https://developer.mozilla.org/en-US/docs/Web/API/MediaTrackSettings)

## getCapabilities

Gets the capabilities of the current camera.

> At present, this method only works in Edge, Safari, Chrome and other Chromium-based browsers (Firefox is not supported). Also, it should be called when a camera is open.

```typescript
getCapabilities(): MediaTrackCapabilities;
```

**Parameters**

None.

**Return value**

A `MediaTrackCapabilities` object representing the capabilities of the camera's video track.

**Code Snippet**

```javascript
cameraEnhancer.getCapabilities();
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
  focusDistance: {max: 

1024, min: 0, step: 10},
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

## getColorTemperature

Retrieves the current color temperature setting of the camera's video feed.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
getColorTemperature(): number;
```

**Parameters**

None.

**Return value**

The current color temperature in Kelvin.

**Code Snippet**

```javascript
cameraEnhancer.getColorTemperature();
```

## getExposureCompensation

Retrieves the current exposure compensation setting of the camera's video feed.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
getExposureCompensation(): number;
```

**Parameters**

None.

**Return value**

The current exposure compensation value.

**Code Snippet**

```javascript
cameraEnhancer.getExposureCompensation();
```

## getFocusSettings

Retrieves the current focus settings of the camera.

```typescript
type FocusArea = {
    centerPoint: { x: string, y: string };
    width: string;
    height: string;
};
getFocusSettings(): {mode: string} | {mode: "manual", area: FocusArea} | {mode: "manual", distance: number} | null;
```

**Parameters**

None.

**Return value**

An object representing the current focus settings or null.

**Code Snippet**

```javascript
cameraEnhancer.getFocusSettings();
```

**See also**

[getCapabilities](#getcapabilities)

## getFrameRate

Retrieves the current frame rate of the camera's video stream.

```typescript
getFrameRate(): number;
```

**Parameters**

None.

**Return value**

The current frame rate in frames per second (fps).

**Code Snippet**

```javascript
cameraEnhancer.getFrameRate();
```

## getZoomSettings

Retrieves the current zoom settings of the camera.

```typescript
getZoomSettings(): { factor: number };
```

**Parameters**

None.

**Return value**

An object containing the current zoom settings. As present, it contains only the zoom factor.

**Code Snippet**

```javascript
console.log(cameraEnhancer.getZoomSettings().factor);
```

## resetZoom

Resets the zoom level of the camera to its default value.

```typescript
resetZoom(): Promise<void>;
```

**Parameters**

None.

**Return value**

A promise that resolves when the zoom level has been successfully reset. It does not provide any value upon resolution.

**Code Snippet**

```javascript
await cameraEnhancer.resetZoom();
```

## setAutoZoomRange

Sets the auto zoom range for the camera.

> `EF_AUTO_ZOOM` is one of the enhanced features that require a license, and is only effective when used in conjunction with other functional products of Dynamsoft.

```typescript
setAutoZoomRange(range: { min: number, max: number }): void;
```

**Parameters**

`range`: an object specifying the minimum and maximum zoom levels. Both `min` and `max` should be positive numbers, with `min` less than or equal to `max`.

The default is `{min: 1, max: 999}`.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.setAutoZoomRange({min: 1, max: 5});
```

## setColorTemperature

Sets the color temperature of the camera's video feed.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
setColorTemperature(colorTemperature: number): Promise<void>;
```

**Parameters**

`colorTemperature`: the desired color temperature in Kelvin.

**Return value**

A promise that resolves when the color temperature has been successfully set. It does not provide any value upon resolution.

**Code Snippet**

```javascript
await cameraEnhancer.setColorTemperature(5000);
```

**See also**

[getCapabilities](#getcapabilities)

## setExposureCompensation

Sets the exposure compensation of the camera's video feed.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
setExposureCompensation(exposureCompensation: number): Promise<void>;
```

**Parameters**

`exposureCompensation`: the desired exposure compensation value.

**Return value**

A promise that resolves when the exposure compensation has been successfully set. It does not provide any value upon resolution.

**Code Snippet**

```javascript
await cameraEnhancer.setExposureCompensation(-0.7);
```

**See also**

[getCapabilities](#getcapabilities)

## setFocus

Sets the focus mode of the camera. This method allows for both manual and continuous focus configurations, as well as specifying a focus area.

> NOTE:
>
> - This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.
> - Typically, `continuous` mode works best. `manual` mode based on a specific area helps the camera focus on that particular area which may seem blurry under `continuous` mode. `manual` mode with specified distances is for those rare cases where the camera distance must be fine-tuned to get the best results.

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

`settings`: an object describing the focus settings. The structure of this object varies depending on the mode specified (`continuous`, `manual` with fixed `distance`, or `manual` with specific `area`).

**Return value**

A promise that resolves when the focus settings have been successfully applied. It does not provide any value upon resolution.

**Code Snippet**

> The "continuous" mode invokes the camera to focus automatically and continuously. Use [getCapabilities()](#getcapabilities) to inspect whether the camera supports "continuous" mode.

```javascript
if (cameraEnhancer.getCapabilities().focusMode.find(mode => mode.localeCompare('continuous') == 0)) {
    await cameraEnhancer.setFocus({
        mode: "continuous"
    });
}
```

> The "manual" mode means manually specifying the focus distance.
> Use [getCapabilities()](#getcapabilities) to inspect the distance range.
>
> ```javascript
> cameraEnhancer.getCapabilities().focusDistance; > //{max: 1024, min: 0, step: 10}
> ```
>
> NOTE: If the set distance is between two allowed values, it will be rounded to the nearest value.

```javascript
await cameraEnhancer.setFocus({
    mode: "manual",
    distance: 200
});
```

> The SDK also has a built-in algorithm that adjusts focus distance based on the blurriness of a particular area. Specify the area with the parameter `area` .
>
> NOTE: the area is a rectangle defined by its center point and its width and height. All coordinates can be in pixels or percentages, such as "500px" or "50%". Percentages are based on stream dimensions.

```javascript
await cameraEnhancer.setFocus({
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

[getCapabilities](#getcapabilities)

## setFrameRate

Sets the frame rate of the camera's video stream.

> At present, this method only works in Edge, Safari, Chrome and other Chromium-based browsers (Firefox is not supported). Also, it should be called when a camera is open.
> If you provide a value that exceeds the camera's capabilities, we will automatically adjust it to the maximum value that can be applied.

```typescript
setFrameRate(rate: number): Promise<void>;
```

**Parameters**

`rate`: the desired frame rate in frames per second (fps).

**Return value**

A promise that resolves when the frame rate has been successfully set. It does not provide any value upon resolution.

**Code Snippet**

```javascript
await cameraEnhancer.setFrameRate(10);
```

**See also**

[getCapabilities](#getcapabilities)

## setZoom

Sets the zoom level of the camera.

> How it works:
>
> 1. If the camera supports zooming and the zoom factor is within its supported range, zooming is done directly by the camera.
> 2. If the camera does not support zooming, software-based magnification is used instead.
> 3. If the camera supports zooming but the zoom factor is beyond what it supports, the camera's maximum zoom is used, and software-based magnification is used to do the rest. (In this case, you may see a brief video flicker between the two zooming processes).

```typescript
setZoom(settings:{factor: number}): Promise<void>;
```

**Parameters**

`settings`: an object containing the zoom settings. 
`settings.factor`: A number specifying the zoom level. At present, it is the only available setting.

**Return value**

A promise that resolves when the zoom level has been successfully set. It does not provide any value upon resolution.

**Code Snippet**

```javascript
cameraEnhancer.setZoom({
    factor: 3
});
```

**See also**

[getCapabilities](#getcapabilities)

## turnOffTorch

Turns off the camera's torch (flashlight) mode.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported.

```typescript
turnOffTorch(): Promise<void>;
```

**Parameters**

None.

**Return value**

A promise that resolves when the torch has been successfully turned off. It does not provide any value upon resolution.

**Code Snippet**

```javascript
await cameraEnhancer.turnOffTorch();
```

**See also**

[turnOnTorch](#turnontorch)

[getCapabilities](#getcapabilities)

## turnOnTorch

Turns on the camera's torch (flashlight) mode, if supported.

> This method should be called when the camera is turned on. Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

```typescript
turnOnTorch(): Promise<void>;
```

**Parameters**

None.

**Return value**

A promise that resolves when the torch has been successfully turned on. It does not provide any value upon resolution.

**Code Snippet**

```javascript
await cameraEnhancer.turnOnTorch();
```

**See also**

[turnOffTorch](#turnofftorch)

[getCapabilities](#getcapabilities)
