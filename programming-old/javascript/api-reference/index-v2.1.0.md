---
layout: default-layout
title: JavaScript API Reference - Dynamsoft Camera Enhancer
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK API Reference.
keywords: camera enhancer, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: API Reference
permalink: /programming/javascript/api-reference/index-v2.1.0.html
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
| [ifSkipCameraInspection](camera-control.md#ifskipcamerainspection) | Returns or sets whether to skip camera inspection at initialization to save time. |
| [ifSaveLastUsedCamera](camera-control.md#ifsavelastusedcamera) | Returns or sets whether to save the last used camera and resolution. |
| [getAllCameras()](camera-control.md#getallcameras) | Returns infomation of all available cameras on the device. |
| [selectCamera()](camera-control.md#selectcamera) | Chooses a camera as the video source. |
| [getSelectedCamera()](camera-control.md#getselectedcamera) | Returns information about the selected / current camera. |
| [open()](camera-control.md#open) | Turn on the camera to start streaming live video. |
| [close()](camera-control.md#close) | Stops video streaming and releases the camera. |
| [isOpen()](camera-control.md#isopen) | Returns whether the selected camera is turned on / occupied. |
| [pause()](camera-control.md#pause) | Pauses video streaming without releasing the camera. |
| [resume()](camera-control.md#resume) | Resumes video streaming. |
| [setResolution()](camera-control.md#setresolution) | Sets the resolution of the current video input. |
| [getResolution()](camera-control.md#getresolution) | Returns the resolution of the current video input. |

### Advanced Camera Control

| API Name | Description |
|---|---|
| [setFrameRate()](camera-control.md#setframerate) | Adjusts the frame rate. |
| [getFrameRate()](camera-control.md#getframerate) | Returns the real-time frame rate. |
| [turnOnTorch()](camera-control.md#turnontorch) | Turns on the torch/flashlight if the current camera supports it. |
| [turnOffTorch()](camera-control.md#turnofftorch) | Turns off the torch/flashlight. |
| [setZoom()](camera-control.md#setzoom) | Sets the zoom level of the video. |
| [setFocus()](camera-control.md#setfocus) | Sets the focus mode and focus distance of the camera. |
| [getFocus()](camera-control.md#getfocus) | Gets the focus mode and focus distance of the camera. |
| [getCapabilities()](camera-control.md#getcapabilities) | Inspects and returns the capabilities of the selected camera. |
| [getCameraSettings()](camera-control.md#getcamerasettings) | Returns the current values for each constrainable property of the selected camera. |
| [setColorTemperature()](camera-control.md#setcolortemperature) | Adjusts the color temperature of the selected camera. |
| [setExposureCompensation()](camera-control.md#setexposurecompensation) | Sets the exposure compensation index of the selected camera. |

### Frame Acquisition

<!--
| [croppingRegions](acquisition.md#singleframemode) | Returns or sets a few regions that the DCE instance will enumerate when cropping consecutive frames. |
| [croppingRegionIndex](acquisition.md#singleframemode) | Returns or sets which of the cropping regions is to be used in cropping the next frame. |
| [refreshInterval](acquisition.md#singleframemode) | Returns or sets how often the buffer is refreshed when the buffer is full. |
-->
    
| API Name | Description |
|---|---|
| [setScanRegion()](acquisition.md#setscanregion) | Specifies which part of the original video is considered when processing frames. |
| [getScanRegion()](acquisition.md#getscanregion) | Returns the scan region. |
| [getFrame()](acquisition.md#getframe) | Returns a `DCEFrame` object which contains the image data of the latest frame from the video input. |
| [getFrameFromBuffer()](acquisition.md#getframefrombuffer) | Returns a `DCEFrame` object which contains the image data of the specified buffered frame. |
| [startFetchingLoop()](acquisition.md#startfetchingloop) | Starts a fetching loop that continuously put frames in a buffer. |
| [stopFetchingLoop()](acquisition.md#stopfetchingloop) | Stops the fetching loop. |
| [isFetchingLoopStarted()](acquisition.md#isfetchingloopstarted) | Returns the state of the fetching loop. |
| [maxNumberOfFramesInBuffer](acquisition.md#maxnumberofframesinbuffer) | Sets or returns how many frames can be buffered. |
| [numberOfFramesInBuffer](acquisition.md#numberofframesinbuffer) | Returns how many frames there are in the buffer. |
| [loopInterval](acquisition.md#loopinterval) | Returns or sets the start time of the next fetch operation. |
| [singleFrameMode](acquisition.md#singleframemode) | Returns or sets whether to enable the singe-frame mode. |

### UI

| API Name | Description |
|---|---|
| [getVisibleRegion()](ui.md#getvisibleregion) | Returns a `Region` object which specifies which part of the original video is shown in the video element. |
| [addScanRegionOverlayCanvas()](ui.md#addscanregionoverlaycanvas) | Add a canvas of the same size as the scan area directly above the scan area. |
| [ifShowScanRegionMask](ui.md#ifshowscanregionmask) | Returns or sets whether the scan region mask is shown. |
| [ifShowScanRegionLaser](ui.md#ifshowscanregionlaser) | Returns or sets whether the laser indicator is shown in the scan region. |
| [setScanRegionMaskStyle()](ui.md#setscanregionmaskstyle) | Sets the styles for the scan region mask. |
| [setVideoFit()](ui.md#setvideofit) | Sets the `object-fit` CSS property of the video element. |
| [getVideoFit()](ui.md#getvideofit) | Returns the value of the `object-fit` CSS property of the video element. |
| [setViewDecorator()](ui.md#setviewdecorator) | Sets and shows the view decorator. |
| [getViewDecorator()](ui.md#getviewdecorator) | Gets what view decorator is shown. |
| [setViewDecoratorLineWidth()](ui.md#setviewdecoratorlinewidth) | Sets the line width for drawing the view decorator. |
| [setViewDecoratorStrokeStyle()](ui.md#setviewdecoratorstrokestyle) | Sets the stroke style for drawing the view decorator. |
| [setViewDecoratorFillStyle()](ui.md#setviewdecoratorfillstyle) | Sets the fill style for drawing the view decorator. |
| [setViewDecoratorMaskFillStyle()](ui.md#setviewdecoratormaskfillstyle) | Sets the fill style for drawing the ask for the view decorator. |

### Auxiliary APIs

| API Name | Description |
|---|---|
| [on()](auxiliary.md#on) | Attach an event handler function for a built-in event. |
| [off()](auxiliary.md#off) | Remove an event handler. |
| [dispose()](auxiliary.md#dispose) | Releases all resources used by the CameraEnhancer instance. |
| [getVersion()](auxiliary.md#getversion) | Returns the version of the library. |
| [detectEnvironment()](auxiliary.md#detectenvironment) | Returns a report on the current running environments. |

## Interfaces

* [Area](interface/area.md)
* [Region](interface/region.md)
* [DCEFrame](interface/dceframe.md)
* [VideoDeviceInfo](interface/videodeviceinfo.md)
* [PlayCallbackInfo](interface/playcallbackinfo.md)