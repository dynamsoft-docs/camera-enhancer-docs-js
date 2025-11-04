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

| Name                                                         | Description                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------------- |
| `static` [createInstance()](./instantiate.md#createinstance) | Initializes a new instance of the `CameraEnhancer` class.           |
| [dispose()](./instantiate.md#dispose)                        | Releases all resources used by the `CameraEnhancer` instance.       |
| [disposed](./instantiate.md#disposed)                        | Returns whether the `CameraEnhancer` instance has been disposed of. |
| `static` [onWarning](./instantiate.md#onwarning)             | Event triggered when the running environment is not ideal.          |

### Basic Camera Control

| Name                                                                   | Description                                                                                                                    |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| [cameraOpenTimeout](./camera-control.md#cameraOpenTimeout)             | Specifies the timeout in milliseconds for opening the camera.                                                                  |
| [close](./camera-control.md#close)                                     | Closes the currently active camera and stops the video stream.                                                                 |
| [getAllCameras](./camera-control.md#getAllCameras)                     | Retrieves a list of all available video input devices (cameras) on the current device.                                         |
| [getAvailableResolutions](./camera-control.md#getAvailableResolutions) | Retrieves a list of available resolutions supported by the currently selected camera.                                          |
| [getCameraState](./camera-control.md#getCameraState)                   | Retrieves the current state of the camera.                                                                                     |
| [getResolution](./camera-control.md#getResolution)                     | Gets the current resolution of the video stream.                                                                               |
| [getSelectedCamera](./camera-control.md#getSelectedCamera)             | Returns the currently selected camera device.                                                                                  |
| [getVideoSettings](./camera-control.md#getVideoSettings)               | Retrieves the current video settings applied to the camera stream.                                                             |
| [ifSaveLastUsedCamera](./camera-control.md#ifSaveLastUsedCamera)       | Determines whether the last used camera settings should be saved and reused the next time the `CameraEnhancer` is initialized. |
| [ifSkipCameraInspection](./camera-control.md#ifSkipCameraInspection)   | Determines whether to skip the initial camera inspection process.                                                              |
| [isOpen](./camera-control.md#isOpen)                                   | Checks if the camera is currently open and streaming video.                                                                    |
| [isPaused](./camera-control.md#isPaused)                               | Checks if the video stream is currently paused.                                                                                |
| [open](./camera-control.md#open)                                       | Opens the currently selected camera and starts the video stream.                                                               |
| [pause](./camera-control.md#pause)                                     | Pauses the video stream without closing the camera.                                                                            |
| [resume](./camera-control.md#resume)                                   | Resumes the video stream from a paused state.                                                                                  |
| [selectCamera](./camera-control.md#selectCamera)                       | Selects a specific camera for use by the `CameraEnhancer`.                                                                     |
| [setResolution](./camera-control.md#setResolution)                     | Sets the resolution of the video stream to a specified value.                                                                  |
| [testCameraAccess](./camera-control.md#testCameraAccess)               | Tests whether the application has access to the camera.                                                                        |
| [updateVideoSettings](./camera-control.md#updateVideoSettings)         | Updates the video settings for the camera stream with new constraints.                                                         |
| [videoSrc](./camera-control.md#videoSrc)                               | Sets or returns the source URL for the video stream to be used by the `CameraEnhancer`.                                        |

### Advanced Camera Control

| Name                                                                   | Description                                                                     |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| [disableEnhancedFeatures](./camera-control.md#disableEnhancedFeatures) | Disables one or more previously enabled enhanced features.                      |
| [enableEnhancedFeatures](./camera-control.md#enableEnhancedFeatures)   | Enables one or more enhanced features that require a license.                   |
| [getAutoZoomRange](./camera-control.md#getAutoZoomRange)               | Retrieves the current auto zoom range settings for the camera.                  |
| [getCameraSettings](./camera-control.md#getCameraSettings)             | Retrieves the current settings of the camera.                                   |
| [getCapabilities](./camera-control.md#getCapabilities)                 | Gets the capabilities of the current camera.                                    |
| [getColorTemperature](./camera-control.md#getColorTemperature)         | Retrieves the current color temperature setting of the camera's video feed.     |
| [getExposureCompensation](./camera-control.md#getExposureCompensation) | Retrieves the current exposure compensation setting of the camera's video feed. |
| [getFocusSettings](./camera-control.md#getFocusSettings)               | Retrieves the current focus settings of the camera.                             |
| [getFrameRate](./camera-control.md#getFrameRate)                       | Retrieves the current frame rate of the camera's video stream.                  |
| [getZoomSettings](./camera-control.md#getZoomSettings)                 | Retrieves the current zoom settings of the camera.                              |
| [resetZoom](./camera-control.md#resetZoom)                             | Resets the zoom level of the camera to its default value.                       |
| [setAutoZoomRange](./camera-control.md#setAutoZoomRange)               | Sets the auto zoom range for the camera.                                        |
| [setColorTemperature](./camera-control.md#setColorTemperature)         | Sets the color temperature of the camera's video feed.                          |
| [setExposureCompensation](./camera-control.md#setExposureCompensation) | Sets the exposure compensation of the camera's video feed.                      |
| [setFocus](./camera-control.md#setFocus)                               | Sets the focus mode of the camera.                                              |
| [setFrameRate](./camera-control.md#setFrameRate)                       | Sets the frame rate of the camera's video stream.                               |
| [setZoom](./camera-control.md#setZoom)                                 | Sets the zoom level of the camera.                                              |
| [turnOffTorch](./camera-control.md#turnOffTorch)                       | Turns off the camera's torch (flashlight) mode.                                 |
| [turnOnTorch](./camera-control.md#turnOnTorch)                         | Turns on the camera's torch (flashlight) mode, if supported.                    |

### Frame Acquisition

| Name                                                                                | Description                                                                                                            |
| ----------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| [addImageToBuffer](./acquisition.md#addImageToBuffer)                               | Adds an image to the internal buffer.                                                                                  |
| [clearBuffer](./acquisition.md#clearBuffer)                                         | Clears all images from the buffer, resetting the state for new image fetching.                                         |
| [fetchImage](./acquisition.md#fetchImage)                                           | Fetches the current frame from the camera's video feed.                                                                |
| [getBufferOverflowProtectionMode](./acquisition.md#getBufferOverflowProtectionMode) | Retrieves the current mode for handling buffer overflow.                                                               |
| [getColourChannelUsageType](./acquisition.md#getColourChannelUsageType)             | Retrieves the current usage type for color channels in images.                                                         |
| [getImage](./acquisition.md#getImage)                                               | Retrieves a buffered image, of type `DSImageData`.                                                                     |
| [getImageCount](./acquisition.md#getImageCount)                                     | Retrieves the current number of images in the buffer.                                                                  |
| [getImageFetchInterval](./acquisition.md#getImageFetchInterval)                     | Retrieves the current interval at which images are continuously fetched from the camera's video feed.                  |
| [getMaxImageCount](./acquisition.md#getMaxImageCount)                               | Retrieves the maximum number of images that can be buffered.                                                           |
| [getPixelFormat](./acquisition.md#getPixelFormat)                                   | Retrieves the current pixel format used for images fetched from the camera.                                            |
| [getScanRegion](./acquisition.md#getScanRegion)                                     | Retrieves the current scan region set within the camera's view.                                                        |
| [hasImage](./acquisition.md#hasImage)                                               | Checks if an image with the specified ID is present in the buffer.                                                     |
| [hasNextImageToFetch](./acquisition.md#hasNextImageToFetch)                         | Determines whether there are more images available to fetch.                                                           |
| [isBufferEmpty](./acquisition.md#isBufferEmpty)                                     | Determines whether the buffer is currently empty.                                                                      |
| [setBufferOverflowProtectionMode](./acquisition.md#setBufferOverflowProtectionMode) | Sets the behavior for handling new incoming images when the buffer is full.                                            |
| [setColourChannelUsageType](./acquisition.md#setColourChannelUsageType)             | Sets the usage type for color channels in images.                                                                      |
| [setErrorListener](./acquisition.md#setErrorListener)                               | Sets an error listener to receive notifications about errors that occur during image source operations.                |
| [setImageFetchInterval](./acquisition.md#setImageFetchInterval)                     | Sets the interval at which images are continuously fetched from the camera's video feed.                               |
| [setMaxImageCount](./acquisition.md#setMaxImageCount)                               | Sets the maximum number of images that can be buffered at any time.                                                    |
| [setNextImageToReturn](./acquisition.md#setNextImageToReturn)                       | Sets the processing priority of a specific image so that it is returned the next time `getImage()` is called.          |
| [setPixelFormat](./acquisition.md#setPixelFormat)                                   | Sets the pixel format for the images fetched from the camera.                                                          |
| [setScanRegion](./acquisition.md#setScanRegion)                                     | Sets the scan region within the camera's view which limits the frame acquisition to a specific area of the video feed. |
| [singleFrameMode](./acquisition.md#singleFrameMode)                                 | Controls the single-frame mode of the `CameraEnhancer`.                                                                |
| [startFetching](./acquisition.md#startFetching)                                     | Starts the process of fetching images.                                                                                 |
| [stopFetching](./acquisition.md#stopFetching)                                       | Stops the process of fetching images.                                                                                  |
| [takePhoto](./acquisition.md#takePhoto)                                             | Initiates a sequence to capture a single frame/image, halting the video stream temporarily.                            |

### UI

| Name                                                                         | Description                                                                                         |
| ---------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| [convertToPageCoordinates](./ui.md#convertToPageCoordinates)                 | Converts coordinates from the video's coordinate system to coordinates relative to the whole page.  |
| [convertToClientCoordinates](./ui.md#convertToClientCoordinates)             | Converts coordinates from the video's coordinate system to coordinates relative to the viewport.    |
| [convertToScanRegionCoordinates](./ui.md#convertToScanRegionCoordinates)     | Converts coordinates from the video's coordinate system to coordinates relative to the scan region. |
| [convertToContainCoordinates](./ui.md#convertToClientCoordinates)            | Converts coordinates from the `fit: cover` to `fit: contain` mode.                                  |
| [setCameraView](./ui.md#setCameraView)                                       | Sets the `CameraView` instance to be used with the `CameraEnhancer`.                                |
| [getCameraView](./ui.md#getCameraView)                                       | Retrieves the current `CameraView` instance associated with the `CameraEnhancer`.                   |
| [getVideoEl](./ui.md#getVideoEl)                                             | Retrieves the HTMLVideoElement used by the `CameraEnhancer` for displaying the camera feed.         |

### Auxiliary

| Name                        | Description                                                           |
| --------------------------- | --------------------------------------------------------------------- |
| [on()](./auxiliary.md#on)   | Registers an event listener for specific camera-related events.       |
| [off()](./auxiliary.md#off) | Removes an event listener previously registered with the `on` method. |

## View Classes

### Class CameraView

| Name                                                                           | Description                                                                                 |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------- |
| `static`  [createInstance](./cameraview.md#createInstance)                     | Initializes a new instance of the `CameraView` class with optional UI customization.        |
| [dispose](./cameraview.md#dispose)                                             | Releases all resources used by the `CameraView` instance.                                   |
| [disposed](./cameraview.md#disposed)                                           | Returns whether the `CameraView` instance has been disposed of.                             |
| `static` [defaultUIElementURL](./cameraview.md#defaultUIElementURL)            | Specifies the URL to a default UI definition file.                                          |
| [getUIElement](./cameraview.md#getUIElement)                                   | Retrieves the current UI element associated with the `CameraView` instance.                 |
| [setUIElement](./cameraview.md#setUIElement)                                   | Sets a specific `HTMLDivElement` as the UI element for the `CameraView` instance.           |
| [createDrawingLayer](./cameraview.md#createDrawingLayer)                       | Creates a new `DrawingLayer` object.                                                        |
| [getDrawingLayer](./cameraview.md#getDrawingLayer)                             | Retrieves a `DrawingLayer` object by its unique identifier (ID).                            |
| [getAllDrawingLayers](./cameraview.md#getAllDrawingLayers)                     | Returns an array of all `DrawingLayer` objects managed by this instance.                    |
| [clearUserDefinedDrawingLayers](./cameraview.md#clearUserDefinedDrawingLayers) | Clears all user-defined `DrawingLayer` objects.                                             |
| [deleteUserDefinedDrawingLayer](./cameraview.md#deleteUserDefinedDrawingLayer) | Deletes a user-defined `DrawingLayer` object by ID.                                         |
| [clearAllInnerDrawingItems](./cameraview.md#clearAllInnerDrawingItems)         | Clears all system-defined `DrawingItem` objects while keeping user-defined ones.            |
| [getVideoElement](./cameraview.md#getVideoElement)                             | Retrieves the `HTMLVideoElement` used for displaying video.                                 |
| [setVideoFit](./cameraview.md#setVideoFit)                                     | Sets the `object-fit` CSS property of the `HTMLVideoElement`.                               |
| [getVideoFit](./cameraview.md#getVideoFit)                                     | Retrieves the current value of the `object-fit` CSS property.                               |
| [getVisibleRegionOfVideo](./cameraview.md#getVisibleRegionOfVideo)             | Returns the region of the video that is currently visible to the user.                      |
| [setScanRegionMaskStyle](./cameraview.md#setScanRegionMaskStyle)               | Sets the style of the scan region mask, including line width, stroke color, and fill color. |
| [getScanRegionMaskStyle](./cameraview.md#getScanRegionMaskStyle)               | Retrieves the current style of the scan region mask.                                        |
| [setScanRegionMaskVisible](./cameraview.md#setScanRegionMaskVisible)           | Sets the visibility of the scan region mask.                                                |
| [isScanRegionMaskVisible](./cameraview.md#isScanRegionMaskVisible)             | Checks if the scan region mask is currently visible.                                        |
| [setScanLaserVisible](./cameraview.md#setScanLaserVisible)                     | Sets the visibility of the scan laser effect.                                               |
| [isScanLaserVisible](./cameraview.md#isScanLaserVisible)                       | Checks if the scan laser effect is currently visible.                                       |
| [getTipConfig](./cameraview.md#getTipConfig)                                   | Retrieves the current configuration of the tip message box.                                 |
| [setTipConfig](./cameraview.md#setTipConfig)                                   | Applies configuration settings to the tip message box.                                      |
| [setTipVisible](./cameraview.md#setTipVisible)                                 | Controls the visibility of the tip message box on the screen.                               |
| [isTipVisible](./cameraview.md#isTipVisible)                                   | Checks whether the tip message box is currently visible.                                    |
| [updateTipMessage](./cameraview.md#updateTipMessage)                           | Updates the message displayed in the tip message box.                                       |
             
### Class ImageEditorView

| Name                                                                                | Description                                                                                      |
| ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| `static` [createInstance](./imageeditorview.md#createInstance)                      | Initializes a new instance of the `ImageEditorView` class.                                       |
| [dispose](./imageeditorview.md#dispose)                                             | Releases all resources used by the `ImageEditorView` instance.                                   |
| [disposed](./imageeditorview.md#disposed)                                           | Returns whether the `ImageEditorView` instance has been disposed of.                             |
| [getUIElement](./imageeditorview.md#getUIElement)                                   | Returns the `HTMLDivElement`, where the `ImageEditorView` UI is loaded.                          |
| [setUIElement](./imageeditorview.md#setUIElement)                                   | Sets a specific `HTMLDivElement`, where the UI element for the `ImageEditorView` will be loaded. |
| [setOriginalImage](./imageeditorview.md#setOriginalImage)                           | Sets the image to be drawn on the `ImageEditorView`.                                             |
| [getOriginalImage](./imageeditorview.md#getOriginalImage)                           | Returns the current image drawn on the `ImageEditorView`.                                        |
| [createDrawingLayer](./imageeditorview.md#createDrawingLayer)                       | Creates a new `DrawingLayer` object and returns it.                                              |
| [getDrawingLayer](./imageeditorview.md#getDrawingLayer)                             | Retrieves a `DrawingLayer` object by its unique identifier (ID).                                 |
| [getAllDrawingLayers](./imageeditorview.md#getAllDrawingLayers)                     | Returns an array of all `DrawingLayer` objects managed by this `DrawingLayerManager`.            |
| [clearUserDefinedDrawingLayers](./imageeditorview.md#clearUserDefinedDrawingLayers) | Clears all user-defined `DrawingLayer` objects.                                                  |
| [deleteUserDefinedDrawingLayer](./imageeditorview.md#deleteUserDefinedDrawingLayer) | Deletes a user-defined `DrawingLayer` object specified by its unique identifier (ID).            |
| [getSelectedDrawingItems](./imageeditorview.md#getSelectedDrawingItems)             | Asynchronously returns an array of all selected DrawingItem instances across different layers.   |

## Auxiliary Classes

### CameraEnhancerModule

| Name                                               | Description                                         |
| -------------------------------------------------- | --------------------------------------------------- |
| `static` [getVersion()](./cameraenhancermodule.md) | Returns the version of the `CameraEnhancer` Module. |

### DrawingItem

| Name                                              | Description                                                                                            |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| [coordinateBase](./drawingitem.md#coordinatebase) | Returns or sets the coordinate system base.                                                            |
| [drawingLayerId](./drawingitem.md#drawinglayerid) | Returns the numeric ID for the `DrawingLayer` this `DrawingItem` belongs to.                           |
| [drawingStyleId](./drawingitem.md#drawingstyleid) | Returns or sets the numeric ID for the `DrawingStyle` that applies to this `DrawingItem`.              |
| [mediaType](./drawingitem.md#mediatype)           | Returns an enumeration value which indicates the type of this `DrawingItem` (e.g., image, line, text). |
| [getState()](./drawingitem.md#getstate)           | Returns the current state of the `DrawingItem`                                                         |
| [on()](./drawingitem.md#on)                       | Binds a listener for a specific event. `eventName`.                                                    |
| [off()](./drawingitem.md#off)                     | Unbinds a listener for a specific event.                                                               |
| [addNote()](./drawingitem.md#addnote)             | Adds a `Note` object to this `DrawingItem`.                                                            |
| [getNote()](./drawingitem.md#getnote)             | Returns a `Note` object specified by its name, if it exists.                                           |
| [getNotes()](./drawingitem.md#getnotes)           | Returns a collection of all existing `Note` objects on this `DrawingItem`.                             |
| [hasNote()](./drawingitem.md#hasnote)             | Checks if a `Note` object with the specified name exists.                                              |
| [updateNote()](./drawingitem.md#updatenote)       | Updates the content of a specified `Note` object.                                                      |
| [deleteNote()](./drawingitem.md#deletenote)       | Deletes a `Note` object specified by its name.                                                         |
| [clearNotes()](./drawingitem.md#clearnotes)       | Deletes all `Note` objects on this `DrawingItem`.                                                      |

Child classes based on `DrawingItem`

#### ImageDrawingItem

| Name                                                                  | Description                                                                        |
| --------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `constructor` [ImageDrawingItem()](./drawingitem.md#imagedrawingitem) | Constructor for the class.                                                         |
| [maintainAspectRatio](./drawingitem.md#maintainaspectratio)           | Determines whether the image's aspect ratio should be maintained when it is drawn. |
| [getImage()](./drawingitem.md#getimage)                               | Retrieves the current image being used for drawing.                                |
| [setImage()](./drawingitem.md#setimage)                               | Sets the image to be used for drawing.                                             |
| [getImageRect()](./drawingitem.md#getimagerect)                       | Returns the rectangle area within which the image is drawn.                        |
| [setImageRect()](./drawingitem.md#setimagerect)                       | Sets the rectangle area within which the image should be drawn.                    |

#### LineDrawingItem

| Name                                                                | Description                                        |
| ------------------------------------------------------------------- | -------------------------------------------------- |
| `constructor` [LineDrawingItem()](./drawingitem.md#linedrawingitem) | Constructor for the class.                         |
| [getLine()](./drawingitem.md#getline)                               | Retrieves the current line being used for drawing. |
| [setLine()](./drawingitem.md#setline)                               | Sets the line to be used for drawing.              |

#### QuadDrawingItem

| Name                                                                | Description                                                 |
| ------------------------------------------------------------------- | ----------------------------------------------------------- |
| `constructor` [QuadDrawingItem()](./drawingitem.md#quaddrawingitem) | Constructor for the class.                                  |
| [getQuad()](./drawingitem.md#getquad)                               | Retrieves the current quadrilateral being used for drawing. |
| [setQuad()](./drawingitem.md#setquad)                               | Sets the quadrilateral to be used for drawing.              |

#### RectDrawingItem

| Name                                                                | Description                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------- |
| `constructor` [RectDrawingItem()](./drawingitem.md#rectdrawingitem) | Constructor for the class.                              |
| [getRect()](./drawingitem.md#getrect)                               | Retrieves the current rectangle being used for drawing. |
| [setRect()](./drawingitem.md#setrect)                               | Sets the rectangle to be used for drawing.              |

#### TextDrawingItem

| Name                                                                | Description                                                    |
| ------------------------------------------------------------------- | -------------------------------------------------------------- |
| `constructor` [TextDrawingItem()](./drawingitem.md#textdrawingitem) | Constructor for the class.                                     |
| [getText()](./drawingitem.md#gettext)                               | Retrieves the current text being used for drawing.             |
| [setText()](./drawingitem.md#settext)                               | Sets the text to be used for drawing.                          |
| [getTextRect()](./drawingitem.md#gettextrect)                       | Returns the rectangle area within which the text is drawn.     |
| [setTextRect()](./drawingitem.md#settextrect)                       | Sets the rectangle area within which the text should be drawn. |

### DrawingLayer

| Name                                                         | Description                                                                               |
| ------------------------------------------------------------ | ----------------------------------------------------------------------------------------- |
| [getId()](./drawinglayer.md#getid)                           | Retrieves the unique identifier of the layer.                                             |
| [isVisible()](./drawinglayer.md#isvisible)                   | Retrieves the visibility status of the layer.                                             |
| [setVisible()](./drawinglayer.md#setvisible)                 | Sets the visibility of the layer.                                                         |
| [setDefaultStyle()](./drawinglayer.md#setdefaultstyle)       | Establishes the baseline styling preferences for `DrawingItem` objects on the layer.      |
| [addDrawingItems()](./drawinglayer.md#adddrawingitems)       | Adds an array of `DrawingItem` objects to the layer.                                      |
| [removeDrawingItems()](./drawinglayer.md#removedrawingitems) | Removes specified `DrawingItem` objects from the layer.                                   |
| [setDrawingItems()](./drawinglayer.md#setdrawingitems)       | Sets the layer's `DrawingItem` objects, replacing any existing items.                     |
| [getDrawingItems()](./drawinglayer.md#getdrawingitems)       | Retrieves `DrawingItem` objects from the layer, optionally filtered by a custom function. |
| [hasDrawingItem()](./drawinglayer.md#hasDrawingItem)         | Checks if a specific `DrawingItem` exists within the layer.                               |
| [clearDrawingItems()](./drawinglayer.md#cleardrawingitems)   | Clears all `DrawingItem` objects from the layer.                                          |
| [renderAll()](./drawinglayer.md#renderall)                   | Forces a re-render of all `DrawingItem` objects on the layer.                             |

### DrawingStyleManager

| Name                                                                       | Description                                                     |
| -------------------------------------------------------------------------- | --------------------------------------------------------------- |
| `static` [createDrawingStyle()](drawingstylemanager.md#createdrawingstyle) | Generates a new `DrawingStyle` object, providing its unique ID. |
| `static` [getDrawingStyle()](drawingstylemanager.md#getdrawingstyle)       | Retrieves a specific `DrawingStyle` object using its ID.        |
| `static` [getDrawingStyles()](drawingstylemanager.md#getdrawingstyles)     | Fetches a collection of all available `DrawingStyle` objects.   |
| `static` [updateDrawingStyle()](drawingstylemanager.md#updatedrawingstyle) | Modifies an identified `DrawingStyle` object by its ID.         |

### Feedback

| Name                                                    | Description                                          |
| ------------------------------------------------------- | ---------------------------------------------------- |
| `static` [beep()](feedback.md#beep)                     | Initiates a beep sound upon invocation.              |
| `static` [beepSoundSource](feedback.md#beepsoundsource) | Returns or sets the beep's sound source.             |
| `static` [vibrate()](feedback.md#vibrate)               | Activates device vibration upon invocation.          |
| `static` [vibrateDuration](feedback.md#vibrateduration) | Determines the vibration's duration in milliseconds. |

## Interfaces

* [CameraTestResponse](interface/cameratestresponse.md)
* [DCEFrame](interface/dceframe.md)
* [DrawingItemEvent](interface/drawingitemevent.md)
* [DrawingStyle](interface/drawingstyle.md)
* [Note](interface/note.md)
* [PlayCallbackInfo](interface/playcallbackinfo.md)
* [Resolution](interface/resolution.md)
* [TipConfig](interface/tipconfig.md)
* [VideoDevice](interface/videodevice.md)
* [VideoFrameTag](interface/videoframetag.md)

## Enumerations

* [EnumDrawingItemMediaType](enum/enumdrawingitemmediatype.md)
* [EnumDrawingItemState](enum/enumdrawingitemstate.md)
* [EnumEnhancedFeatures](enum/enumenhancedfeatures.md)
