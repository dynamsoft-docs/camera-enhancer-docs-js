---
layout: default-layout
title: JavaScript API Reference - Dynamsoft Camera Enhancer
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK API Reference.
keywords: camera enhancer, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: API Reference
---

# Dynamsoft Camera Enhancer JavaScript API Reference

## Class CameraEnhancer

### Create and Destroy Instances

| API Name                                                   | Description                                                                                  |
| ---------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `static` [createInstance()](instantiate.md#createinstance) | Creates a `CameraEnhancer` instance.                                                         |
| [dispose()](instantiate.md#dispose)                        | Releases all resources used by the `CameraEnhancer` instance.                                |
| [disposed](instantiate.md#disposed)                        | A readonly boolean value indicating whether the `CameraEnhancer` instance has been disposed. |
| `static` [onWarning](instantiate.md#onwarning)             | A callback which is triggered when the running environment is not ideal.                     |

### Basic Camera Control

| API Name                                                               | Description                                                                           |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `static` [testCameraAccess()](camera-control.md#testcameraaccess)      | Tests whether there is an available camera.                                           |
| [getAllCameras()](camera-control.md#getallcameras)                     | Returns information of all available cameras on the device.                           |
| [selectCamera()](camera-control.md#selectcamera)                       | Chooses a camera as the video source.                                                 |
| [getSelectedCamera()](camera-control.md#getselectedcamera)             | Returns information about the selected / current camera.                              |
| [getCameraState()](camera-control.md#getcamerastate)                   | Returns the state of the selected camera which could be "opening", "open" or "closed" |
| [open()](camera-control.md#open)                                       | Turn on the camera to start streaming live video.                                     |
| [close()](camera-control.md#close)                                     | Stops video streaming and releases the camera.                                        |
| [isOpen()](camera-control.md#isopen)                                   | Returns whether the selected camera is turned on / occupied.                          |
| [pause()](camera-control.md#pause)                                     | Pauses video streaming without releasing the camera.                                  |
| [isPaused()](camera-control.md#ispaused)                               | Returns whether the video streaming is paused.                                        |
| [resume()](camera-control.md#resume)                                   | Resumes video streaming.                                                              |
| [setResolution()](camera-control.md#setresolution)                     | Sets the resolution of the selected camera.                                           |
| [getResolution()](camera-control.md#getresolution)                     | Returns the resolution of the selected camera.                                        |
| [getAvailableResolutions()](camera-control.md#getavailableresolutions) | Returns the resolutions supported by the selected camera.                             |
| [ifSaveLastUsedCamera](camera-control.md#ifsavelastusedcamera)         | Returns or sets whether to save the last used camera and resolution.                  |
| [videoSrc](camera-control.md#videosrc)                                 | Sets or returns the source of the video.                                              |
| [ifSkipCameraInspection](camera-control.md#ifskipcamerainspection)     | Whether to opt for an optimal rear camera at the first `open()`.                      |

### Advanced Camera Control

| API Name                                                               | Description                                                                        |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| [setFrameRate()](camera-control.md#setframerate)                       | Adjusts the frame rate.                                                            |
| [getFrameRate()](camera-control.md#getframerate)                       | Returns the real-time frame rate.                                                  |
| [turnOnTorch()](camera-control.md#turnontorch)                         | Turns on the torch/flashlight if the current camera supports it.                   |
| [turnOffTorch()](camera-control.md#turnofftorch)                       | Turns off the torch/flashlight.                                                    |
| [getZoomSettings()](camera-control.md#getzoomsettings)                 | Returns the zoom settings.                                                         |
| [setZoom()](camera-control.md#setzoom)                                 | Zooms the video stream.                                                            |
| [resetZoom()](camera-control.md#resetzoom)                             | Resets the zoom level of the video.                                                |
| [getFocusSettings()](camera-control.md#getfocussettings)               | Returns the focus settings.                                                        |
| [setFocus()](camera-control.md#setfocus)                               | Sets how the camera focuses.                                                       |
| [getCapabilities()](camera-control.md#getcapabilities)                 | Inspects and returns the capabilities of the selected camera.                      |
| [getCameraSettings()](camera-control.md#getcamerasettings)             | Returns the current values for each constrainable property of the selected camera. |
| [getColorTemperature()](camera-control.md#getcolortemperature)         | Returns the color temperature of the selected camera.                              |
| [setColorTemperature()](camera-control.md#setcolortemperature)         | Adjusts the color temperature of the selected camera.                              |
| [getExposureCompensation()](camera-control.md#getexposurecompensation) | Returns the exposure compensation index of the selected camera.                    |
| [setExposureCompensation()](camera-control.md#setexposurecompensation) | Sets the exposure compensation index of the selected camera.                       |
| [setAutoZoomRange()](camera-control.md#setautozoomrange)               | Sets the range (minimum to maximum) for zoom when it is done automatically.        |
| [getAutoZoomRange()](camera-control.md#getautozoomrange)               | Returns the auto zoom range.                                                       |
| [enableEnhancedFeatures()](camera-control.md#enableenhancedfeatures)   | Enables the specified enhanced features.                                           |
| [disableEnhancedFeatures()](camera-control.md#disableenhancedfeatures) | Disables the specified enhanced features.                                          |

### Frame Acquisition

| API Name                                                                            | Description                                                                                         |
| ----------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| [setScanRegion()](acquisition.md#setscanregion)                                     | Specifies which part of the original video is considered when processing frames.                    |
| [getScanRegion()](acquisition.md#getscanregion)                                     | Returns the scan region.                                                                            |
| [fetchImage()](acquisition.md#fetchimage)                                           | Returns a `DCEFrame` object which contains the image data of the latest frame from the video input. |
| [addImageToBuffer()](acquisition.md#addimagetobuffer)                               | Adds an `DSImageData` object to the buffer.                                                         |
| [setImageFetchInterval()](acquisition.md#setimagefetchinterval)                     | Sets the interval at which `fetchImage()` is called when continued fetching has started.            |
| [getImageFetchInterval()](acquisition.md#getimagefetchinterval)                     | Returns the fetch interval.                                                                         |
| [startFetching()](acquisition.md#startfetching)                                     | Starts to continuously fetch images and put them into the buffer.                                   |
| [stopFetching()](acquisition.md#stopfetching)                                       | Stops fetching any more images.                                                                     |
| [setMaxImageCount()](acquisition.md#setmaximagecount)                               | Sets the size of the buffer as in how many images can be buffered.                                  |
| [getMaxImageCount()](acquisition.md#getmaximagecount)                               | Returns the size of the buffer.                                                                     |
| [getImageCount()](acquisition.md#getimagecount)                                     | Returns how many images are in buffer.                                                              |
| [hasImage()](acquisition.md#hasimage)                                               | Checks whether an image exists. The image is specified by its id.                                   |
| [getImage()](acquisition.md#getimage)                                               | Returns a `DCEFrame` object from the buffer.                                                        |
| [setNextImageToReturn()](acquisition.md#setnextimagetoreturn)                       | Specifies an image by its id to be returned when `getImage()` is called the next time.              |
| [setBufferOverflowProtectionMode()](acquisition.md#setbufferoverflowprotectionmode) | Sets a protection mode that determines what happens when the buffer overflows.                      |
| [getBufferOverflowProtectionMode()](acquisition.md#getbufferoverflowprotectionmode) | Returns the buffer protection mode.                                                                 |
| [isBufferEmpty()](acquisition.md#isbufferempty)                                     | Returns whether the buffer is empty.                                                                |
| [hasNextImageToFetch()](acquisition.md#hasnextimagetofetch)                         | Checks whether another image can be fetched. In other words, whether the video is still streaming.  |
| [setPixelFormat()](acquisition.md#setpixelformat)                                   | Sets the pixel format of the images returned by `getImage()`.                                       |
| [singleFrameMode](acquisition.md#singleframemode)                                   | Returns or sets whether to enable the singe-frame mode.                                             |
| [takePhoto()](acquisition.md#takephoto)                                             | Invokes the system camera to take a frame with better image quality.                                |

### UI

| API Name                                                         | Description                                                                                                                                                      |
| ---------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [getCameraView](ui.md#getcameraview)                             | Returns the `CameraView` instance used by the `CameraEnhancer` instance.                                                                                         |
| [setCameraView](ui.md#setcameraview)                             | Sets a `CameraView` instance to be used by the `CameraEnhancer` instance.                                                                                        |
| [getVideoEl](ui.md#getvideoel)                                   | Returns the video element used by the `CameraView` instance.                                                                                                     |
| [convertToPageCoordinates()](ui.md#converttopagecoordinates)     | Converts coordinates of a point to the coordinates relative to the top left point of the entire document.                                                        |
| [convertToClientCoordinates()](ui.md#converttoclientcoordinates) | Converts coordinates of a point to the coordinates within the application's viewport at which the event occurred (as opposed to the coordinate within the page). |

### Auxiliary

| API Name                                              | Description                                                                                               |
| ----------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| [on()](auxiliary.md#on)                               | Attaches an event handler function for a built-in event.                                                  |
| [off()](auxiliary.md#off)                             | Removes an event handler.                                                                                 |
| [offAll()](auxiliary.md#offall)                       | Removes all event handlers from the specified event. If no event is specified, remove all event handlers. |
| [detectEnvironment()](auxiliary.md#detectenvironment) | Returns a report on the current running environments.                                                     |

## Class CameraView

### Create and Destroy Instances

| API Name                                                  | Description                                                                              |
| --------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| `static` [createInstance()](cameraview.md#createinstance) | Creates a `CameraView` instance.                                                         |
| [dispose()](cameraview.md#dispose)                        | Releases all resources used by the `CameraView` instance.                                |
| [disposed](cameraview.md#disposed)                        | A readonly boolean value indicating whether the `CameraView` instance has been disposed. |
| [getUIElement()](cameraview.md#getuielement)              | Returns the HTML element that is used by the `CameraView` instance.                      |
| [setUIElement()](cameraview.md#setuielement)              | Specifies an HTML element for the `CameraView` instance to use as its UI element.        |

### Drawing and UI

| API Name                                                                       | Description                                                                                               |
| ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------- |
| [createDrawingLayer()](cameraview.md#createdrawinglayer)                       | Creates a DrawingLayer object and put it in an array of DrawingLayers.                                    |
| [getDrawingLayer()](cameraview.md#getdrawinglayer)                             | Gets the DrawingLayer specified by its ID.                                                                |
| [getAllDrawingLayers()](cameraview.md#getalldrawinglayers)                     | Returns an array of all DrawingLayer objects.                                                             |
| [deleteUserDefinedDrawingLayer()](cameraview.md#deleteuserdefineddrawinglayer) | Deletes a DrawingLayer object specified by its ID.                                                        |
| [clearUserDefinedDrawingLayers()](cameraview.md#clearuserdefineddrawinglayers) | Removes all user-defined DrawingLayers.                                                                   |
| [setTipConfig()](cameraview.md#settipconfig)                                   | Configures the tip feature.                                                                               |
| [getTipConfig()](cameraview.md#gettipconig)                                    | Returns the configuration of the tip.                                                                     |
| [setTipVisible()](cameraview.md#settipvisible)                                 | Sets whether to show the tip.                                                                             |
| [isTipVisible()](cameraview.md#istipvisible)                                   | Returns whether the tip is visible.                                                                       |
| [setVideoFit()](cameraview.md#setvideofit)                                     | Sets the `object-fit` CSS property of the video element.                                                  |
| [getVideoFit()](cameraview.md#getvideofit)                                     | Returns the value of the `object-fit` CSS property of the video element.                                  |
| [updateTipMessage()](cameraview.md#updatetipmessage)                           | Updates the message shown in the tip.                                                                     |
| [getVisibleRegionOfVideo()](cameraview.md#getvisibleregionofvideo)             | Returns a `Region` object which specifies which part of the original video is shown in the video element. |
| [getVideoElement()](cameraview.md#getvideoelement)                             | Returns the video element used by the `CameraView` instance.                                              |
| [setScanRegionMaskStyle()](cameraview.md#setscanregionmaskstyle)               | Sets the drawing style for the scan-region mask.                                                          |
| [getScanRegionMaskStyle()](cameraview.md#getscanregionmaskstyle)               | Returns the drawing style for the scan-region mask.                                                       |
| [setScanRegionMaskVisible()](cameraview.md#setscanregionmaskvisible)           | Sets whether to show the scan-region mask.                                                                |
| [isScanRegionMaskVisible()](cameraview.md#isscanregionmaskvisible)             | Returns whether the scan-region mask is visible.                                                          |
| [setScanLaserVisible()](cameraview.md#setscanlaservisible)                     | Sets whether to show the laser that indicates the scanning is going on.                                   |
| [isScanLaserVisible()](cameraview.md#isscanlaservisible)                       | Returns whether the laser is visible.                                                                     |
                  
## Class ImageEditorView

### Create and Destroy Instances

| API Name                                                       | Description                                                                                   |
| -------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `static` [createInstance()](imageeditorview.md#createinstance) | Creates an `ImageEditorView` instance.                                                        |
| [dispose()](imageeditorview.md#dispose)                        | Releases all resources used by the `ImageEditorView` instance.                                |
| [disposed](imageeditorview.md#disposed)                        | A readonly boolean value indicating whether the `ImageEditorView` instance has been disposed. |
| [getUIElement()](imageeditorview.md#getuielement)              | Returns the HTML element that is used by the `ImageEditorView` instance.                      |
| [setUIElement()](imageeditorview.md#setuielement)              | Specifies an HTML element for the `ImageEditorView` instance to use as its UI element.        |

### Drawing and UI

| API Name                                                                            | Description                                                            |
| ----------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| [createDrawingLayer()](imageeditorview.md#createdrawinglayer)                       | Creates a DrawingLayer object and put it in an array of DrawingLayers. |
| [getDrawingLayer()](imageeditorview.md#getdrawinglayer)                             | Gets the DrawingLayer specified by its ID.                             |
| [getAllDrawingLayers()](imageeditorview.md#getalldrawinglayers)                     | Returns an array of all DrawingLayer objects.                          |
| [deleteUserDefinedDrawingLayer()](imageeditorview.md#deleteuserdefineddrawinglayer) | Deletes a DrawingLayer object specified by its ID.                     |
| [clearUserDefinedDrawingLayers()](imageeditorview.md#clearuserdefineddrawinglayers) | Removes all user-defined DrawingLayers.                                |
| [getSelectedDrawingItems()](imageeditorview.md#getselecteddrawingitems)             | Returns the selected DrawingItem object(s).                            |
| [setOriginalImage()](imageeditorview.md#setoriginalimage)                           | Sets the image to be drawn on the image editor view.                   |
| [getOriginalImage()](imageeditorview.md#setoriginalimage)                           | Returns the image drawn on the image editor.                           |

## Class CameraEnhancerModule

| API Name     | Description                                         |
| ------------ | --------------------------------------------------- |
| getVersion() | Returns the version of the `CameraEnhancer` Module. |

## Subordinate Classes

### Feedback

| API Name                         | Description                                  |
| -------------------------------- | -------------------------------------------- |
| [beep()](feedback.md#beep)       | Trigger a beep when the method is called.    |
| [vibrate()](feedback.md#vibrate) | Trigger a vibrate when the method is called. |

### DrawingLayer

| API Name                                                   | Description                                                                                                      |
| ---------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| [getId()](drawinglayer.md#getid)                           | Returns the ID of the `DrawingLayer`.                                                                            |
| [addDrawingItems()](drawinglayer.md#adddrawingitems)       | Adds `DrawingItems` to the `DrawingLayer`.                                                                       |
| [getDrawingItems()](drawinglayer.md#getdrawingitems)       | Returns all `DrawingItems` or just some of them based on a filter function.                                      |
| [setDrawingItems()](drawinglayer.md#setdrawingitems)       | Replaces all `DrawingItems` of the DrawingLayer with new ones.                                                   |
| [hasDrawingItem()](drawinglayer.md#hasDrawingItem)         | Checks out if a `DrawingItem` belongs to the layer.                                                              |
| [removeDrawingItems()](drawinglayer.md#removedrawingitems) | Removes `DrawingItems` from the DrawingLayer.                                                                    |
| [clearDrawingItems()](drawinglayer.md#cleardrawingitems)   | Removes all `DrawingItems` from the DrawingLayer.                                                                |
| [renderAll()](drawinglayer.md#renderall)                   | Renders all `DrawingItems`, usually required when the style for one or more items is changed.                    |
| [setDefaultStyle()](drawinglayer.md#setdefaultstyle)       | Sets the style for `DrawingItems` on the layer.                                                                  |
| [setVisible()](drawinglayer.md#setvisible)                 | Shows or hides the `DrawingLayer`.                                                                               |
| [isVisible()](drawinglayer.md#isvisible)                   | Returns whether the `DrawingLayer` is visible.                                                                   |
| [onSelectionChanged()](drawinglayer.md#onselectionchanged) | An event handler that is triggered when different `DrawingItems` gets selected/deselected on the `DrawingLayer`. |

### DrawingStyleManager

| API Name                                                                     | Description                                             |
| ---------------------------------------------------------------------------- | ------------------------------------------------------- |
| `static` [createDrawingStyle()](drawingstylemanager.md#createdrawingstyle)   | Creates a new `DrawingStyle` object and returns its ID. |
| `static` [getDrawingStyle()](drawingstylemanager.md#getdrawingstyle)         | Returns the `DrawingStyle` object specified by its Id.  |
| `static` [getAllDrawingStyles()](drawingstylemanager.md#getalldrawingstyles) | Returns all `DrawingStyle` objects.                     |
| `static` [updateDrawingStyle()](drawingstylemanager.md#updatedrawingstyle)   | Updates an existing `DrawingStyle` specified by its ID. |

### DrawingItem

| API Name                                        | Description                                                                                                |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| [drawingLayerId](drawingitem.md#drawinglayerid) | Returns the id of a `DrawingLayer` where the `DrawingItem` is drawn.                                       |
| [mediaType](drawingitem.md#mediatype)           | Returns the `mediaType` of the `DrawingItem`.                                                              |
| [coordinateBase](drawingitem.md#coordinatebase) | Sets or returns the `coordinateBase` which determines the meaning of the coordinates of the `DrawingItem`. |
| [drawingStyleId](drawingitem.md#drawingstyleid) | Sets or returns the id of the `DrawingStyle` that applies to the `DrawingItem`.                            |
| [setState()](drawingitem.md#setstate)           | Sets whether the `DrawingItem` is selected or not.                                                         |
| [getState()](drawingitem.md#getstate)           | Returns the state of the `DrawingItem`.                                                                    |
| [on](drawingitem.md#on)                         | Adds an event listener to the `DrawingItem` for the event specified by `eventName`.                        |
| [off](drawingitem.md#off)                       | Removes an event listener to the `DrawingItem` for the event specified by `eventName`.                     |
| [addNote()](drawingitem.md#addnote)             | Adds a `Note` to this `DrawingItem`.                                                                       |
| [getNote()](drawingitem.md#getnote)             | Returns a `Note` specified by its name.                                                                    |
| [hasNote()](drawingitem.md#hasnote)             | Returns whether a `Note` with the specified name exists on this `DrawingItem`.                             |
| [updateNote()](drawingitem.md#updatenote)       | Updates the content of a `Note` specified by its name.                                                     |
| [deleteNote()](drawingitem.md#deletenote)       | Deletes a `Note` specified by its name.                                                                    |
| [getAllNotes()](drawingitem.md#getallnotes)     | Returns all `Notes` on the `DrawingItem`.                                                                  |
| [clearNotes()](drawingitem.md#clearnotes)       | Deletes all `Notes` on the `DrawingItem`.                                                                  |

Child classes based on `DrawingItem`

#### LineDrawingItem


| API Name                                            | Description                                                       |
| --------------------------------------------------- | ----------------------------------------------------------------- |
| [LineDrawingItem()](drawingitem.md#linedrawingitem) | Constructor of a `LineDrawingItem`.                               |
| [getLine](drawingitem.md#getline)                   | Returns the `LineSegment` object the item is based on.            |
| [setLine](drawingitem.md#setline)                   | Specifies a `LineSegment` object to be used for drawing the line. |

#### RectDrawingItem

| API Name                                            | Description                                                |
| --------------------------------------------------- | ---------------------------------------------------------- |
| [RectDrawingItem()](drawingitem.md#rectdrawingitem) | Constructor of a `RectDrawingItem`.                        |
| [getRect](drawingitem.md#getrect)                   | Returns the `Rect` object the item is based on.            |
| [setRect](drawingitem.md#setrect)                   | Specifies a `Rect` object to be used for drawing the item. |

#### QuadDrawingItem


| API Name                                            | Description                                                         |
| --------------------------------------------------- | ------------------------------------------------------------------- |
| [QuadDrawingItem()](drawingitem.md#quaddrawingitem) | Constructor of a `QuadDrawingItem`.                                 |
| [getQuad](drawingitem.md#getquad)                   | Returns the `Quadrilateral` object the item is based on.            |
| [setQuad](drawingitem.md#setquad)                   | Specifies a `Quadrilateral` object to be used for drawing the item. |

#### TextDrawingItem

| API Name                                            | Description                                                         |
| --------------------------------------------------- | ------------------------------------------------------------------- |
| [TextDrawingItem()](drawingitem.md#textdrawingitem) | Constructor of a `TextDrawingItem`.                                 |
| [getText](drawingitem.md#gettext)                   | Returns the text drawn.                                             |
| [setText](drawingitem.md#settext)                   | Specifies the text to draw.                                         |
| [getTextRect](drawingitem.md#gettextrect)           | Returns the `Rect` object which determines where the text is drawn. |
| [setTextRect](drawingitem.md#settextrect)           | Specifies a `Rect` object in which the text is drawn.               |

#### ImageDrawingItem

| API Name                                                  | Description                                                                       |
| --------------------------------------------------------- | --------------------------------------------------------------------------------- |
| [ImageDrawingItem()](drawingitem.md#imagedrawingitem)     | Constructor of an `ImageDrawingItem`.                                             |
| [maintainAspectRatio](drawingitem.md#maintainaspectratio) | Sets or returns whether aspect ratio of the image is maintained when it is drawn. |
| [getImage](drawingitem.md#getimage)                       | Returns the image drawn.                                                          |
| [setImage](drawingitem.md#setimage)                       | Specifies the image to draw.                                                      |
| [getImageRect](drawingitem.md#gettextrect)                | Returns the `Rect` object which determines where the image is drawn.              |
| [setImageRect](drawingitem.md#settextrect)                | Specifies a `Rect` object in which the image is drawn.                            |

## Interfaces

* [DCEFrame](interface/dceframe.md)
* [DrawingItemEvent](interface/drawingitemevent.md)
* [DrawingStyle](interface/drawingstyle.md)
* [Note](interface/note.md)
* [PlayCallbackInfo](interface/playcallbackinfo.md)
* [Resolution](interface/resolution.md)
* [Point](interface/point.md)
* [Region](interface/region.md)
* [TipConfig](interface/tipconfig.md)
* [VideoDevice](interface/videodevice.md)
* [VideoFrameTag](interface/videoframetag.md)
* [Warning](interface/warning.md)

## Enumerations

* [EnumEnhancedFeatures](enum/enumenhancedfeatures.md)
* [EnumDrawingItemState](enum/enumdrawingitemstate.md)
* [EnumDrawingItemMediaType](enum/enumdrawingitemmediatype.md)