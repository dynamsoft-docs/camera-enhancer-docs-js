---
layout: default-layout
title: JavaScript API Reference - Dynamsoft Camera Enhancer
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK API Reference.
keywords: camera enhancer, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: API Reference
permalink: /programming/javascript/api-reference/index-v3.1.html
---

# JavaScript API Reference

## CameraEnhancer

### Initialization

| API Name | Description |
|---|---|
| [createInstance()](initialization.md#createinstance) | Creates a `CameraEnhancer` instance. |
| [defaultUIElementURL](initialization.md#defaultuielementurl) | Returns or sets the URL of the .html file that defines the default UI Element. |
| [getUIElement()](initialization.md#getuielement) | Returns the HTML element that is used by the `CameraEnhancer` instance. |
| [setUIElement()](initialization.md#setuielement) | Specifies an HTML element for the `CameraEnhancer` instance to use as its UI element. |
| [onWarning](initialization.md#onwarning) | A callback which is triggered when the running environment is not ideal. |

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
| [getResolutions()](camera-control.md#getresolutions) | Returns the resolutions supported by the current video input. |
| [videoSrc](camera-control.md#videosrc) | Sets or returns the source of the video. |

### Advanced Camera Control

| API Name | Description |
|---|---|
| [setFrameRate()](camera-control.md#setframerate) | Adjusts the frame rate. |
| [getFrameRate()](camera-control.md#getframerate) | Returns the real-time frame rate. |
| [turnOnTorch()](camera-control.md#turnontorch) | Turns on the torch/flashlight if the current camera supports it. |
| [turnOffTorch()](camera-control.md#turnofftorch) | Turns off the torch/flashlight. |
| [getZoom()](camera-control.md#getzoom) | Returns the zoom level of the video. |
| [setZoom()](camera-control.md#setzoom) | Sets the zoom level of the video. |
| [setFocus()](camera-control.md#setfocus) | Sets the focus mode and focus distance of the camera. |
| [getFocus()](camera-control.md#getfocus) | Gets the focus mode and focus distance of the camera. |
| [getCapabilities()](camera-control.md#getcapabilities) | Inspects and returns the capabilities of the selected camera. |
| [getCameraSettings()](camera-control.md#getcamerasettings) | Returns the current values for each constrainable property of the selected camera. |
| [getColorTemperature()](camera-control.md#getcolortemperature) | Returns the color temperature of the selected camera. |
| [setColorTemperature()](camera-control.md#setcolortemperature) | Adjusts the color temperature of the selected camera. |
| [getExposureCompensation()](camera-control.md#getexposurecompensation) | Returns the exposure compensation index of the selected camera. |
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
| [framePixelFormat](acquisition.md#framepixelformat) | Sets or returns the pixel format of the images generated by getFrame(). |
| [maxNumberOfFramesInBuffer](acquisition.md#maxnumberofframesinbuffer) | Sets or returns how many frames can be buffered. |
| [numberOfFramesInBuffer](acquisition.md#numberofframesinbuffer) | Returns how many frames there are in the buffer. |
| [loopInterval](acquisition.md#loopinterval) | Returns or sets the start time of the next fetch operation. |
| [singleFrameMode](acquisition.md#singleframemode) | Returns or sets whether to enable the singe-frame mode. |

### UI

| API Name | Description |
|---|---|
| [getVisibleRegion()](ui.md#getvisibleregion) | Returns a `Region` object which specifies which part of the original video is shown in the video element. |
| [addScanRegionOverlayCanvas()](ui.md#addscanregionoverlaycanvas) | Adds a canvas of the same size as the scan area directly above the scan area. |
| [removeScanRegionOverlayCanvas()](ui.md#removescanregionoverlaycanvas) | Removes the specified Canvas element. |
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
| [createDrawingLayer()](ui.md#createdrawinglayer) | Creates a DrawingLayer object and put it in an array of DrawingLayers. |
| [getDrawingLayer()](ui.md#getdrawinglayer) | Gets the DrawingLayer specified by its ID. |
| [getDrawingLayers()](ui.md#getdrawinglayers) | Returns an array of all DrawingLayer objects. |
| [clearDrawingLayers()](ui.md#cleardrawinglayers) | Removes all DrawingLayers. |
| [createDrawingStyle()](ui.md#createdrawingstyle) | Creates a new DrawingStyle object and returns its ID. |
| [getDrawingStyle()](ui.md#getdrawingstyle) | Returns the DrawingStyle object specified by its Id. |
| [getDrawingStyles()](ui.md#getdrawingstyles) | Returns all DrawingStyle objects. |
| [updateDrawingStyle()](ui.md#updatedrawingstyle) | Updates an existing DrawingStyle specified by its ID. |
| [setOriginalImage()](ui.md#setoriginalimage) | Sets the original image to be drawn on the editor canvas.  |
| [getOriginalImage()](ui.md#getoriginalimage) | Returns the original image shown on the editor. |
| [showOriginalImage()](ui.md#showoriginalimage) | Shows the original image. |
| [hideOriginalImage()](ui.md#hideoriginalimage) | Hides the original image. |
| [deleteOriginalImage()](ui.md#deleteoriginalimage) | Deletes the original image and remove the canvas that shows it. |
| [getSelectedDrawingItems()](ui.md#getselecteddrawingitems) | Returns the selected DrawingItem object(s). |

### Auxiliary APIs

| API Name | Description |
|---|---|
| [on()](auxiliary.md#on) | Attaches an event handler function for a built-in event. |
| [off()](auxiliary.md#off) | Removes an event handler. |
| [offAll()](auxiliary.md#offall) | Removes all event handlers from the specified event. If no event is specified, remove all event handlers. |
| [dispose()](auxiliary.md#dispose) | Releases all resources used by the CameraEnhancer instance. |
| [disposed](auxiliary.md#disposed) | A readonly boolean value indicating whether the CameraEnhancer instance has been disposed. |
| [getVersion()](auxiliary.md#getversion) | Returns the version of the library. |
| [detectEnvironment()](auxiliary.md#detectenvironment) | Returns a report on the current running environments. |

## DrawingLayer

| API Name | Description |
|---|---|
| [getId()](drawinglayer.md#getid) | Returns the ID of the DrawingLayer. |
| [addDrawingItems()](drawinglayer.md#adddrawingitems) | Adds DrawingItem(s) to the DrawingLayer. |
| [getDrawingItems()](drawinglayer.md#getdrawingitems) | Returns all DrawingItem(s) or just some of them based on a filter function. |
| [setDrawingItems()](drawinglayer.md#setdrawingitems) | Replaces all DrawingItem(s) of the DrawingLayer with new ones. |
| [hasDrawingItem()](drawinglayer.md#hasDrawingItem) | Checks out if a DrawingItem belongs to the layer. |
| [removeDrawingItems()](drawinglayer.md#removedrawingitems) | Removes DrawingItem(s) from the DrawingLayer. |
| [clearDrawingItems()](drawinglayer.md#cleardrawingitems) | Removes all DrawingItem(s) from the DrawingLayer. |
| [setDrawingStyle()](drawinglayer.md#setdrawingstyle) | Sets the style for the DrawingLayer or for a particular mediaType or for a particular mediaType in a particular state. |
| [setVisible()](drawinglayer.md#setvisible) | Shows or hides the DrawingLayer. |
| [isVisible()](drawinglayer.md#isvisible) | Returns whether the DrawingLayer is visible. |
| [renderAll()](drawinglayer.md#renderall) | Renders all DrawingItems, usually required when the style for one or more items is changed. |
| [onSelectionChange()](drawinglayer.md#onselectionchange) | An event handler that is triggered when different DrawingItem(s) gets selected/deselected on the DrawingLayer. |
| [setMode()](drawinglayer.md#setmode) | Changes the mode of the layer. |
| [getMode()](drawinglayer.md#getmode) | Returns the current mode. |

## DrawingItem

| Type Name | Description |
|---|---|
| [DT_Rect](drawingitem.md#dtrect) | Defines a DrawingItem the shape of a rectangle. |
| [DT_Arc](drawingitem.md#dtarc)   | Defines a DrawingItem the shape of a arc. |
| [DT_Line](drawingitem.md#dtline) | Defines a DrawingItem the shape of a line. |
| [DT_Polygon](drawingitem.md#dtpolygon) | Defines a DrawingItem the shape of a polygon. |
| [DT_Text](drawingitem.md#dttext) | Defines a DrawingItem that draws text. |
| [DT_Image](drawingitem.md#dtimage) | Defines a DrawingItem that draws an image. |
| [DT_Group](drawingitem.md#dtgroup) | Defines a DrawingItem which is a combination of more than one DrawingItem of the other six types.  |

## Interfaces

* [Area](interface/area.md)
* [DCEFrame](interface/dceframe.md)
* [DrawingItemEvent](interface/drawingitemevent.md)
* [DrawingStyle](interface/drawingstyle.md)
* [Note](interface/note.md)
* [PlayCallbackInfo](interface/playcallbackinfo.md)
* [Point](interface/point.md)
* [Region](interface/region.md)
* [VideoDeviceInfo](interface/videodeviceinfo.md)
* [Warning](interface/warning.md)
