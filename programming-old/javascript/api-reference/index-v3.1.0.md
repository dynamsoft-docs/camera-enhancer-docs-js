---
layout: default-layout
title: JavaScript API Reference - Dynamsoft Camera Enhancer
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK API Reference.
keywords: camera enhancer, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: API Reference
permalink: /programming/javascript/api-reference/index-v3.1.0.html
---

# JavaScript API Reference

## CameraEnhancer

### Initialization

| Name| Description |
|---|---|
| [createInstance()](initialization.html#createinstance) | Creates a `CameraEnhancer` instance. |
| [defaultUIElementURL](initialization.html#defaultuielementurl) | Returns or sets the URL of the .html file that defines the default UI Element. |
| [getUIElement()](initialization.html#getuielement) | Returns the HTML element that is used by the `CameraEnhancer` instance. |
| [setUIElement()](initialization.html#setuielement) | Specifies an HTML element for the `CameraEnhancer` instance to use as its UI element. |
| [onWarning](initialization.html#onwarning) | A callback which is triggered when the running environment is not ideal. |

### Camera Control

| Name| Description |
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
| [videoSrc](camera-control.html#videosrc) | Sets or returns the source of the video. |

### Advanced Camera Control

| Name| Description |
|---|---|
| [setFrameRate()](camera-control.html#setframerate) | Adjusts the frame rate. |
| [getFrameRate()](camera-control.html#getframerate) | Returns the real-time frame rate. |
| [turnOnTorch()](camera-control.html#turnontorch) | Turns on the torch/flashlight if the current camera supports it. |
| [turnOffTorch()](camera-control.html#turnofftorch) | Turns off the torch/flashlight. |
| [getZoom()](camera-control.html#getzoom) | Returns the zoom level of the video. |
| [setZoom()](camera-control.html#setzoom) | Sets the zoom level of the video. |
| [setFocus()](camera-control.html#setfocus) | Sets the focus mode and focus distance of the camera. |
| [getFocus()](camera-control.html#getfocus) | Gets the focus mode and focus distance of the camera. |
| [getCapabilities()](camera-control.html#getcapabilities) | Inspects and returns the capabilities of the selected camera. |
| [getCameraSettings()](camera-control.html#getcamerasettings) | Returns the current values for each constrainable property of the selected camera. |
| [getColorTemperature()](camera-control.html#getcolortemperature) | Returns the color temperature of the selected camera. |
| [setColorTemperature()](camera-control.html#setcolortemperature) | Adjusts the color temperature of the selected camera. |
| [getExposureCompensation()](camera-control.html#getexposurecompensation) | Returns the exposure compensation index of the selected camera. |
| [setExposureCompensation()](camera-control.html#setexposurecompensation) | Sets the exposure compensation index of the selected camera. |

### Frame Acquisition

<!--
| [croppingRegions](acquisition.html#singleframemode) | Returns or sets a few regions that the DCE instance will enumerate when cropping consecutive frames. |
| [croppingRegionIndex](acquisition.html#singleframemode) | Returns or sets which of the cropping regions is to be used in cropping the next frame. |
| [refreshInterval](acquisition.html#singleframemode) | Returns or sets how often the buffer is refreshed when the buffer is full. |
-->

| Name| Description |
|---|---|
| [setScanRegion()](acquisition.html#setscanregion) | Specifies which part of the original video is considered when processing frames. |
| [getScanRegion()](acquisition.html#getscanregion) | Returns the scan region. |
| [getFrame()](acquisition.html#getframe) | Returns a `DCEFrame` object which contains the image data of the latest frame from the video input. |
| [getFrameFromBuffer()](acquisition.html#getframefrombuffer) | Returns a `DCEFrame` object which contains the image data of the specified buffered frame. |
| [startFetchingLoop()](acquisition.html#startfetchingloop) | Starts a fetching loop that continuously put frames in a buffer. |
| [stopFetchingLoop()](acquisition.html#stopfetchingloop) | Stops the fetching loop. |
| [isFetchingLoopStarted()](acquisition.html#isfetchingloopstarted) | Returns the state of the fetching loop. |
| [framePixelFormat](acquisition.html#framepixelformat) | Sets or returns the pixel format of the images generated by getFrame(). |
| [maxNumberOfFramesInBuffer](acquisition.html#maxnumberofframesinbuffer) | Sets or returns how many frames can be buffered. |
| [numberOfFramesInBuffer](acquisition.html#numberofframesinbuffer) | Returns how many frames there are in the buffer. |
| [loopInterval](acquisition.html#loopinterval) | Returns or sets the start time of the next fetch operation. |
| [singleFrameMode](acquisition.html#singleframemode) | Returns or sets whether to enable the singe-frame mode. |

### UI

| Name| Description |
|---|---|
| [getVisibleRegion()](ui.html#getvisibleregion) | Returns a `Region` object which specifies which part of the original video is shown in the video element. |
| [addScanRegionOverlayCanvas()](ui.html#addscanregionoverlaycanvas) | Adds a canvas of the same size as the scan area directly above the scan area. |
| [removeScanRegionOverlayCanvas()](ui.html#removescanregionoverlaycanvas) | Removes the specified Canvas element. |
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
| [createDrawingLayer()](ui.html#createdrawinglayer) | Creates a DrawingLayer object and put it in an array of DrawingLayers. |
| [getDrawingLayer()](ui.html#getdrawinglayer) | Gets the DrawingLayer specified by its ID. |
| [getDrawingLayers()](ui.html#getdrawinglayers) | Returns an array of all DrawingLayer objects. |
| [clearDrawingLayers()](ui.html#cleardrawinglayers) | Removes all DrawingLayers. |
| [createDrawingStyle()](ui.html#createdrawingstyle) | Creates a new DrawingStyle object and returns its ID. |
| [getDrawingStyle()](ui.html#getdrawingstyle) | Returns the DrawingStyle object specified by its Id. |
| [getDrawingStyles()](ui.html#getdrawingstyles) | Returns all DrawingStyle objects. |
| [updateDrawingStyle()](ui.html#updatedrawingstyle) | Updates an existing DrawingStyle specified by its ID. |
| [setOriginalImage()](ui.html#setoriginalimage) | Sets the original image to be drawn on the editor canvas.  |
| [getOriginalImage()](ui.html#getoriginalimage) | Returns the original image shown on the editor. |
| [showOriginalImage()](ui.html#showoriginalimage) | Shows the original image. |
| [hideOriginalImage()](ui.html#hideoriginalimage) | Hides the original image. |
| [deleteOriginalImage()](ui.html#deleteoriginalimage) | Deletes the original image and remove the canvas that shows it. |
| [getSelectedDrawingItems()](ui.html#getselecteddrawingitems) | Returns the selected DrawingItem object(s). |

### Auxiliary APIs

| Name| Description |
|---|---|
| [on()](auxiliary.html#on) | Attaches an event handler function for a built-in event. |
| [off()](auxiliary.html#off) | Removes an event handler. |
| [offAll()](auxiliary.html#offall) | Removes all event handlers from the specified event. If no event is specified, remove all event handlers. |
| [dispose()](auxiliary.html#dispose) | Releases all resources used by the CameraEnhancer instance. |
| [disposed](auxiliary.html#disposed) | A readonly boolean value indicating whether the CameraEnhancer instance has been disposed. |
| [getVersion()](auxiliary.html#getversion) | Returns the version of the library. |
| [detectEnvironment()](auxiliary.html#detectenvironment) | Returns a report on the current running environments. |

## DrawingLayer

| Name| Description |
|---|---|
| [getId()](drawinglayer.html#getid) | Returns the ID of the DrawingLayer. |
| [addDrawingItems()](drawinglayer.html#adddrawingitems) | Adds DrawingItem(s) to the DrawingLayer. |
| [getDrawingItems()](drawinglayer.html#getdrawingitems) | Returns all DrawingItem(s) or just some of them based on a filter function. |
| [setDrawingItems()](drawinglayer.html#setdrawingitems) | Replaces all DrawingItem(s) of the DrawingLayer with new ones. |
| [hasDrawingItem()](drawinglayer.html#hasDrawingItem) | Checks out if a DrawingItem belongs to the layer. |
| [removeDrawingItems()](drawinglayer.html#removedrawingitems) | Removes DrawingItem(s) from the DrawingLayer. |
| [clearDrawingItems()](drawinglayer.html#cleardrawingitems) | Removes all DrawingItem(s) from the DrawingLayer. |
| [setDrawingStyle()](drawinglayer.html#setdrawingstyle) | Sets the style for the DrawingLayer or for a particular mediaType or for a particular mediaType in a particular state. |
| [setVisible()](drawinglayer.html#setvisible) | Shows or hides the DrawingLayer. |
| [isVisible()](drawinglayer.html#isvisible) | Returns whether the DrawingLayer is visible. |
| [renderAll()](drawinglayer.html#renderall) | Renders all DrawingItems, usually required when the style for one or more items is changed. |
| [onSelectionChange()](drawinglayer.html#onselectionchange) | An event handler that is triggered when different DrawingItem(s) gets selected/deselected on the DrawingLayer. |
| [setMode()](drawinglayer.html#setmode) | Changes the mode of the layer. |
| [getMode()](drawinglayer.html#getmode) | Returns the current mode. |

## DrawingItem

| Type Name | Description |
|---|---|
| [DT_Rect](drawingitem.html#dtrect) | Defines a DrawingItem the shape of a rectangle. |
| [DT_Arc](drawingitem.html#dtarc)   | Defines a DrawingItem the shape of a arc. |
| [DT_Line](drawingitem.html#dtline) | Defines a DrawingItem the shape of a line. |
| [DT_Polygon](drawingitem.html#dtpolygon) | Defines a DrawingItem the shape of a polygon. |
| [DT_Text](drawingitem.html#dttext) | Defines a DrawingItem that draws text. |
| [DT_Image](drawingitem.html#dtimage) | Defines a DrawingItem that draws an image. |
| [DT_Group](drawingitem.html#dtgroup) | Defines a DrawingItem which is a combination of more than one DrawingItem of the other six types.  |

## Interfaces

* [Area](interface/area.html)
* [DCEFrame](interface/dceframe.html)
* [DrawingItemEvent](interface/drawingitemevent.html)
* [DrawingStyle](interface/drawingstyle.html)
* [Note](interface/note.html)
* [PlayCallbackInfo](interface/playcallbackinfo.html)
* [Point](interface/point.html)
* [Region](interface/region.html)
* [VideoDeviceInfo](interface/videodeviceinfo.html)
* [Warning](interface/warning.html)
