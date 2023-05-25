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

| API Name | Description |
|---|---|
| [createInstance()](initialization.md#createinstance) | Creates a `CameraEnhancer` instance. |
| [defaultUIElementURL](initialization.md#defaultuielementurl) | Returns or sets the URL of the .html file that defines the default UI Element. |
| [getUIElement()](initialization.md#getuielement) | Returns the HTML element that is used by the `CameraEnhancer` instance. |
| [setUIElement()](initialization.md#setuielement) | Specifies an HTML element for the `CameraEnhancer` instance to use as its UI element. |

### Camera Control

| API Name | Description |
|---|---|
| [getAllCameras()](camera-control.md#getallcameras) | Returns infomation of all available cameras on the device. |
| [selectCamera()](camera-control.md#selectcamera) | Chooses a camera as the video source. |
| [getSelectedCamera()](camera-control.md#getselectedcamera) | Returns information about the selected / current camera. |
| [open()](camera-control.md#open) | Turn on the camera to start streaming live video. |
| [close()](camera-control.md#close) | Stops video streaming and releases the camera. |
| [isOpen()](camera-control.md#isOpen) | Returns whether the selected camera is turned on / occupied. |
| [onPlayed](camera-control.md#onplayed) | Defines a callback which is triggered when the video streaming first starts or restarts when its source (camera) or resolution changes. |
| [pause()](camera-control.md#pause) | Pauses video streaming without releasing the camera. |
| [resume()](camera-control.md#resume) | Resumes video streaming. |
| [setResolution()](camera-control.md#setresolution) | Sets the resolution of the current video input. |
| [getResolution()](camera-control.md#getresolution) | Returns the resolution of the current video input. |

### Advanced Camera Control

| API Name | Description |
|---|---|
| [setFrameRate()](camera-control.md#setframerate) | Adjusts the frame rate. |
| [getFrameRate()](camera-control.md#getframerate) | Returns the real-time frame rate. |
| [turnOnTorch()](camera-control.md#turnontorch) | Turns on the torch/flashlight. |
| [turnOffTorch()](camera-control.md#turnofftorch) | Turns off the torch/flashlight. |
| [setZoom()](camera-control.md#setzoom) | Sets the zoom level of the video. |
| [getCapabilities()](camera-control.md#getcapabilities) | Inspects and returns the capabilities of the selected camera. |
| [getCameraSettings()](camera-control.md#getcamerasettings) | Returns the current values for each constrainable property of the selected camera. |
| [setColorTemperature()](camera-control.md#setcolortemperature) | Adjusts the color temperature of the selected camera. |
| [setExposureCompensation()](camera-control.md#setexposurecompensation) | Sets the exposure compensation index of the selected camera. |

### Frame Acquisition

| API Name | Description |
|---|---|
| [getFrame()](acquisition.md#getframe) | Returns a `DCEFrame` object which contains the image data of the latest frame from the video input. |
| [singleFrameMode](acquisition.md#singleframemode) | Returns or sets whether to enable the singe-frame mode. |
| [onSingleFrameAcquired](acquisition.md#onsingleframeacquired) | This event is triggered when a new frame / image is acquired under the single-frame mode. |

### Auxiliary APIs

| API Name | Description |
|---|---|
| [getVersion()](auxiliary.md#getversion) | Returns the version of the library. |
| [detectEnvironment()](auxiliary.md#detectenvironment) | Returns a report on the current running environments. |

## Interfaces

* [Region](interface/region.md)
* [DCEFrame](interface/dceframe.md)
* [VideoDeviceInfo](interface/videodeviceinfo.md)
* [PlayCallbackInfo](interface/playcallbackinfo.md)