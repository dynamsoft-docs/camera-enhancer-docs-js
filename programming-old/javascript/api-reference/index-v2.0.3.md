---
layout: default-layout
title: JavaScript API Reference - Dynamsoft Camera Enhancer
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK API Reference.
keywords: camera enhancer, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: API Reference
permalink: /programming/javascript/api-reference/index-v2.0.3.html
---

# JavaScript API Reference

## Methods and Properties

### Initialization

| Name| Description |
|---|---|
| [createInstance()](initialization.html#createinstance) | Creates a `CameraEnhancer` instance. |
| [defaultUIElementURL](initialization.html#defaultuielementurl) | Returns or sets the URL of the .html file that defines the default UI Element. |
| [getUIElement()](initialization.html#getuielement) | Returns the HTML element that is used by the `CameraEnhancer` instance. |
| [setUIElement()](initialization.html#setuielement) | Specifies an HTML element for the `CameraEnhancer` instance to use as its UI element. |

### Camera Control

| Name| Description |
|---|---|
| [getAllCameras()](camera-control.html#getallcameras) | Returns infomation of all available cameras on the device. |
| [selectCamera()](camera-control.html#selectcamera) | Chooses a camera as the video source. |
| [getSelectedCamera()](camera-control.html#getselectedcamera) | Returns information about the selected / current camera. |
| [open()](camera-control.html#open) | Turn on the camera to start streaming live video. |
| [close()](camera-control.html#close) | Stops video streaming and releases the camera. |
| [isOpen()](camera-control.html#isOpen) | Returns whether the selected camera is turned on / occupied. |
| [onPlayed](camera-control.html#onplayed) | Defines a callback which is triggered when the video streaming first starts or restarts when its source (camera) or resolution changes. |
| [pause()](camera-control.html#pause) | Pauses video streaming without releasing the camera. |
| [resume()](camera-control.html#resume) | Resumes video streaming. |
| [setResolution()](camera-control.html#setresolution) | Sets the resolution of the current video input. |
| [getResolution()](camera-control.html#getresolution) | Returns the resolution of the current video input. |

### Advanced Camera Control

| Name| Description |
|---|---|
| [setFrameRate()](camera-control.html#setframerate) | Adjusts the frame rate. |
| [getFrameRate()](camera-control.html#getframerate) | Returns the real-time frame rate. |
| [turnOnTorch()](camera-control.html#turnontorch) | Turns on the torch/flashlight. |
| [turnOffTorch()](camera-control.html#turnofftorch) | Turns off the torch/flashlight. |
| [setZoom()](camera-control.html#setzoom) | Sets the zoom level of the video. |
| [getCapabilities()](camera-control.html#getcapabilities) | Inspects and returns the capabilities of the selected camera. |
| [getCameraSettings()](camera-control.html#getcamerasettings) | Returns the current values for each constrainable property of the selected camera. |
| [setColorTemperature()](camera-control.html#setcolortemperature) | Adjusts the color temperature of the selected camera. |
| [setExposureCompensation()](camera-control.html#setexposurecompensation) | Sets the exposure compensation index of the selected camera. |

### Frame Acquisition

| Name| Description |
|---|---|
| [getFrame()](acquisition.html#getframe) | Returns a `DCEFrame` object which contains the image data of the latest frame from the video input. |
| [singleFrameMode](acquisition.html#singleframemode) | Returns or sets whether to enable the singe-frame mode. |
| [onSingleFrameAcquired](acquisition.html#onsingleframeacquired) | This event is triggered when a new frame / image is acquired under the single-frame mode. |

### Auxiliary APIs

| Name| Description |
|---|---|
| [getVersion()](auxiliary.html#getversion) | Returns the version of the library. |
| [detectEnvironment()](auxiliary.html#detectenvironment) | Returns a report on the current running environments. |

## Interfaces

* [Region](interface/region.html)
* [DCEFrame](interface/dceframe.html)
* [VideoDeviceInfo](interface/videodeviceinfo.html)
* [PlayCallbackInfo](interface/playcallbackinfo.html)