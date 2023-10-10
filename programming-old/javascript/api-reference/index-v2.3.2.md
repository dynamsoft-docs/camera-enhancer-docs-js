---
layout: default-layout
title: JavaScript API Reference - Dynamsoft Camera Enhancer
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK API Reference.
keywords: camera enhancer, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: API Reference
permalink: /programming/javascript/api-reference/index-v2.3.2.html
---

# JavaScript API Reference

## Methods and Properties

### Initialization

| API Name | Description |
|---|---|
| [createInstance()](initialization.html#createinstance) | Creates a `CameraEnhancer` instance. |
| [defaultUIElementURL](initialization.html#defaultuielementurl) | Returns or sets the URL of the .html file that defines the default UI Element. |
| [getUIElement()](initialization.html#getuielement) | Returns the HTML element that is used by the `CameraEnhancer` instance. |
| [setUIElement()](initialization.html#setuielement) | Specifies an HTML element for the `CameraEnhancer` instance to use as its UI element. |

### Camera Control

| API Name | Description |
|---|---|
| [ifSkipCameraInspection](camera-control.html#ifskipcamerainspection) | Returns or sets whether to skip camera inspection at initialization to save time. |
| [ifSaveLastUsedCamera](camera-control.html#ifsavelastusedcamera) | Returns or sets whether to save the last used camera and resolution. |
| [getAllCameras()](camera-control.html#getallcameras) | Returns infomation of all available cameras on the device. |
| [selectCamera()](camera-control.html#selectcamera) | Chooses a camera as the video source. |
| [getSelectedCamera()](camera-control.html#getselectedcamera) | Returns information about the selected / current camera. |
| [open()](camera-control.html#open) | Turn on the camera to start streaming live video. |
| [close()](camera-control.html#close) | Stops video streaming and releases the camera. |
| [isOpen()](camera-control.html#isopen) | Returns whether the selected camera is turned on / occupied. |
| [pause()](camera-control.html#pause) | Pauses video streaming without releasing the camera. |
| [resume()](camera-control.html#resume) | Resumes video streaming. |
| [setResolution()](camera-control.html#setresolution) | Sets the resolution of the current video input. |
| [getResolution()](camera-control.html#getresolution) | Returns the resolution of the current video input. |
| [getResolutions()](camera-control.html#getresolutions) | Returns the resolutions supported by the current video input. |

### Advanced Camera Control

| API Name | Description |
|---|---|
| [setFrameRate()](camera-control.html#setframerate) | Adjusts the frame rate. |
| [getFrameRate()](camera-control.html#getframerate) | Returns the real-time frame rate. |
| [turnOnTorch()](camera-control.html#turnontorch) | Turns on the torch/flashlight if the current camera supports it. |
| [turnOffTorch()](camera-control.html#turnofftorch) | Turns off the torch/flashlight. |
| [setZoom()](camera-control.html#setzoom) | Sets the zoom level of the video. |
| [setFocus()](camera-control.html#setfocus) | Sets the focus mode and focus distance of the camera. |
| [getFocus()](camera-control.html#getfocus) | Gets the focus mode and focus distance of the camera. |
| [getCapabilities()](camera-control.html#getcapabilities) | Inspects and returns the capabilities of the selected camera. |
| [getCameraSettings()](camera-control.html#getcamerasettings) | Returns the current values for each constrainable property of the selected camera. |
| [setColorTemperature()](camera-control.html#setcolortemperature) | Adjusts the color temperature of the selected camera. |
| [setExposureCompensation()](camera-control.html#setexposurecompensation) | Sets the exposure compensation index of the selected camera. |

### Frame Acquisition

<!--
| [croppingRegions](acquisition.html#singleframemode) | Returns or sets a few regions that the DCE instance will enumerate when cropping consecutive frames. |
| [croppingRegionIndex](acquisition.html#singleframemode) | Returns or sets which of the cropping regions is to be used in cropping the next frame. |
| [refreshInterval](acquisition.html#singleframemode) | Returns or sets how often the buffer is refreshed when the buffer is full. |
-->
    
| API Name | Description |
|---|---|
| [setScanRegion()](acquisition.html#setscanregion) | Specifies which part of the original video is considered when processing frames. |
| [getScanRegion()](acquisition.html#getscanregion) | Returns the scan region. |
| [getFrame()](acquisition.html#getframe) | Returns a `DCEFrame` object which contains the image data of the latest frame from the video input. |
| [getFrameFromBuffer()](acquisition.html#getframefrombuffer) | Returns a `DCEFrame` object which contains the image data of the specified buffered frame. |
| [startFetchingLoop()](acquisition.html#startfetchingloop) | Starts a fetching loop that continuously put frames in a buffer. |
| [stopFetchingLoop()](acquisition.html#stopfetchingloop) | Stops the fetching loop. |
| [isFetchingLoopStarted()](acquisition.html#isfetchingloopstarted) | Returns the state of the fetching loop. |
| [frameColorMode](acquisition.html#framecolormode) | Sets or returns the color mode of the images generated by getFrame(). |
| [maxNumberOfFramesInBuffer](acquisition.html#maxnumberofframesinbuffer) | Sets or returns how many frames can be buffered. |
| [numberOfFramesInBuffer](acquisition.html#numberofframesinbuffer) | Returns how many frames there are in the buffer. |
| [loopInterval](acquisition.html#loopinterval) | Returns or sets the start time of the next fetch operation. |
| [singleFrameMode](acquisition.html#singleframemode) | Returns or sets whether to enable the singe-frame mode. |

### UI

| API Name | Description |
|---|---|
| [getVisibleRegion()](ui.html#getvisibleregion) | Returns a `Region` object which specifies which part of the original video is shown in the video element. |
| [addScanRegionOverlayCanvas()](ui.html#addscanregionoverlaycanvas) | Add a canvas of the same size as the scan area directly above the scan area. |
| [ifShowScanRegionMask](ui.html#ifshowscanregionmask) | Returns or sets whether the scan region mask is shown. |
| [ifShowScanRegionLaser](ui.html#ifshowscanregionlaser) | Returns or sets whether the laser indicator is shown in the scan region. |
| [setScanRegionMaskStyle()](ui.html#setscanregionmaskstyle) | Sets the styles for the scan region mask. |
| [setVideoFit()](ui.html#setvideofit) | Sets the `object-fit` CSS property of the video element. |
| [getVideoFit()](ui.html#getvideofit) | Returns the value of the `object-fit` CSS property of the video element. |
| [setViewDecorator()](ui.html#setviewdecorator) | Sets and shows the view decorator. |
| [getViewDecorator()](ui.html#getviewdecorator) | Gets what view decorator is shown. |
| [setViewDecoratorLineWidth()](ui.html#setviewdecoratorlinewidth) | Sets the line width for drawing the view decorator. |
| [setViewDecoratorStrokeStyle()](ui.html#setviewdecoratorstrokestyle) | Sets the stroke style for drawing the view decorator. |
| [setViewDecoratorFillStyle()](ui.html#setviewdecoratorfillstyle) | Sets the fill style for drawing the view decorator. |
| [setViewDecoratorMaskFillStyle()](ui.html#setviewdecoratormaskfillstyle) | Sets the fill style for drawing the ask for the view decorator. |

### Auxiliary APIs

| API Name | Description |
|---|---|
| [on()](auxiliary.html#on) | Attach an event handler function for a built-in event. |
| [off()](auxiliary.html#off) | Remove an event handler. |
| [dispose()](auxiliary.html#dispose) | Releases all resources used by the CameraEnhancer instance. |
| [getVersion()](auxiliary.html#getversion) | Returns the version of the library. |
| [detectEnvironment()](auxiliary.html#detectenvironment) | Returns a report on the current running environments. |

## Interfaces

* [Area](interface/area.html)
* [Region](interface/region.html)
* [DCEFrame](interface/dceframe.html)
* [VideoDeviceInfo](interface/videodeviceinfo.html)
* [PlayCallbackInfo](interface/playcallbackinfo.html)