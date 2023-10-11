---
layout: default-layout
title: JavaScript 3.x Release Notes  - Dynamsoft Camera Enhancer
description: This is the Release Notes page for Dynamsoft Camera Enhancer JavaScript SDK v 2.x.
keywords:  camera enhancer, release notes, javascript
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: v3.x Release Notes
permalink: /programming/javascript/release-note/release-notes-3.x.html
---

# Release Notes - JavaScript 3.x

## 3.3.7 (10/11/2023)

### Fixed

* Fixed an issue where incorrect data was retrieved when fetching grayscale images or fetching images by 'context2d'.

## 3.3.6 (09/13/2023)

### Changed

* Updated the API singleFrameMode to allow direct camera access on mobile devices.

### Fixed

* Fixed a issue may causing an unnecessary input element to appear in Safari on iOS 16.

## 3.3.5 (08/02/2023)

### Fixed

* Fixed an issue where TypeScript 5 cannot locate the declaration file when importing package.

### New

* Added API `isPaused()` to check if the video stream is paused.

### Improved

* Optimized the logic of default camera selection on iOS.
* Modified `convertToPageCoordinates()` and `convertToClientCoordinates()` to return decimal results directly instead of rounded results.

## 3.3.4 (04/17/2023)

### Fixed

* Fixed a bug that the `ScanRegionMask` and `ScanRegionLaser` might disappear when the camera is re-opened.
* Fixed a bug that the `Resolution` might be changed when the method `getResolutions()` is triggered.

## 3.3.3 (04/11/2023)

### Fixed

* Fixed a bug that led to a wrong camera being selected as the default camera when used on a device running iOS 16.4.
* Fixed a bug that caused the scan region mask or the decorator to randomly appear and disappear when swiping the screen in Safari on iOS.

## 3.3.2 (04/04/2023)

### New

* Added method `convertToPageCoordinates()` to convert the coordinates on image frames to coordinates on the HTML page.
* Added method `convertToClientCoordinates()` to convert the coordinates on image frames to coordinates within the application's viewport (usually it means the browser window).

### Improved

* When `open()` is called, if there is no camera or the access is denied, an error is thrown right away (previously the error is thrown after a while).

## 3.3.1 (02/20/2023)

### Fixed

* Fixed a bug where tapping to focus the camera could go beyond the camera's supported range.

## 3.3.0 (02/09/2023)

### Changed

* The DrawingLayer is placed over the scan region mask.

### Fixed

* Fixed a bug where resuming a video is not "resuming" but "replaying".
* Fixed a bug where tip continues to show up after `hideTip()` is called.
* Fixed a bug in Safari where video may stop playing when the web page's [`visibilityState`](https://developer.mozilla.org/en-US/docs/Web/API/Document/visibilitychange_event) changes to "visible" from "hidden".

## 3.2.0 (12/13/2022)

### New

* Introduced the Tip feature with the new methods `showTip()`, `hideTip()`, `updateTipMessage()` and an event `onTipSuggested`.
* Added method `deleteDrawingLayer()` to delete an existing DrawingLayer.
* Added method `clearFrameBuffer()` to remove all buffered image frames.
* Added methods `getZoomSettings()`, `resetZoom()`, `getFocusSettings()`, `enableTapToFocus()`, `disableTapToFocus()` and `isTapToFocusEnabled()` for better camera control.
* Added method `testCameraAccess()` to help test the availability of cameras.

### Changed

* The method `setZoom()` now accepts an object as zoom settings.
* The method `setFocus()` now accepts an object as focus settings.

## 3.1.0 (10/20/2022)

### New

* Added methods `getZoom()`, `getColorTemperature()`, `getExposureCompensation()` for better camera control.
* Added the "Note" feature to DrawingItems to allow extra information to be added to them for timely interation. Related methods include `addNote()`, `getNote()`, `hasNote()`, `updateNote()`, `deleteNote()`, `getNotes()`, and `clearNotes()`.
* Added methods `setAttribute()` and `getAttribute()` to DrawingItems to allow the change and retrieval of their properties.
* Added methods `on()` and `off()` to DrawingItems to allow binding and unbinding of event listeners to the events **mousedown**, **mouseup**, **dblclick**, **mouseover**, **mouseout** (the last three don't work on mobile devices).

### Changed

* The method `setZoom()` now uses both the camera and WebGL, so it works on all browsers and devices.
* The method `getDrawingItems()` now accepts a filter function to allow the returning of only a selected few of all DrawingItems on the DrawingLayer.
* The property `isDisposed` has been deprecated in favor of `disposed`.
* The property `frameColorMode` has been deprecated in favor of `framePixelFormat`.
* The field name `colorMode` has been deprecated in favor of `pixelFormat` in the interface `DCEFrame`.
* The DrawingItem Type `DT_Text` now has a fixed width and the text within is wrapped.
* The DrawingItem Type `DT_Text` now allows line breaks (`\n`) and tabs (`\t`) in the content of the text.
* When playing a static video, the camera selection and resolution selection boxes are hidden.

## 3.0.1 (08/04/2022)

* Fixed a bug where the scan region mask and/or other shapes drawn on the UI were not updated when the view changed to landscape from portrait or vice versa on mobile devices.

## 3.0.0 (07/27/2022)

### Changelog

#### New

* Added callback [`onWarning`](../api-reference/initialization.html#onwarning) which is triggered when the running environment is not ideal.
* Added property [`isDisposed`](../api-reference/auxiliary.html#isdisposed) to indicate whether the **CameraEnhancer** instance has been disposed.
* Added method [`offAll()`](../api-reference/auxiliary.html#offall) to remove all event handlers from the specified event. If no event is specified, remove all event handlers.
* Added method [`removeScanRegionOverlayCanvas()`](../api-reference/ui.html#removescanregionoverlaycanvas) to remove the specified Canvas element which was added with **addScanRegionOverlayCanvas()**.

The following APIs are for the new feature of drawing shapes. Read more on [Draw Shapes with DCE JS](../user-guide/features/draw-shapes.html).

* Added type [`DrawingItem`](../api-reference/drawingitem.html) to define basic shapes to be drawn.
* Added class `DT_Rect`, `DT_Arc`, `DT_Text`, `DT_Line`, `DT_Polygon`, `DT_Image`, and `DT_Group` to define different shapes of **DrawingItem**.
* Added interface `Point` to describe the vertices when constructing objects of `DT_Line` and `DT_Polygon`.

* Added interface [`DrawingLayer`](../api-reference/drawinglayer.html) to organize items.
* Added method [`createDrawingLayer()`](../api-reference/ui.html#createdrawinglayer) to create a **DrawingLayer** object.
* Added method [`getDrawingLayer()`](../api-reference/ui.html#getdrawinglayer) to get the **DrawingLayer** specified by its ID.
* Added method [`clearDrawingLayers()`](../api-reference/ui.html#cleardrawinglayers) to remove all **DrawingLayer** objects.

* Added interface [`DrawingStyle`](../api-reference/interface/drawingstyle.html) to customize styles for drawing **DrawingItems**.
* Added method [`createDrawingStyle()`](../api-reference/ui.html#createdrawingstyle) to create a **DrawingStyle** object and return its ID.
* Added method [`getDrawingStyle()`](../api-reference/ui.html#getdrawingstyle) to get the **DrawingStyle** specified by its ID.
* Added method [`getDrawingStyles()`](../api-reference/ui.html#getdrawingstyles) to get all **DrawingStyle** objects.
* Added method [`updateDrawingStyle()`](../api-reference/ui.html#updatedrawingstyle) to update a **DrawingStyle** specified by its ID.

* Added method [`setOriginalImage()`](../api-reference/ui.html#setoriginalimage) to set an original image to be drawn on a built-in canvas above which shapes are drawn usually based on coordinates of certain objects found on this image by other SDKs such as barcode locations found by DBR.
* Added method [`getOriginalImage()`](../api-reference/ui.html#getoriginalimage) to return the original image.
* Added method [`showOriginalImage()`](../api-reference/ui.html#showoriginalimage) to show the built-in canvas on which the original image is drawn.
* Added method [`hideOriginalImage()`](../api-reference/ui.html#hideoriginalimage) to hide the built-in canvas on which the original image is drawn.
* Added method [`deleteOriginalImage()`](../api-reference/ui.html#deleteoriginalimage) to delete the original image and remove the built-in canvas that shows it.
* Added method [`getSelectedDrawingItems()`](../api-reference/ui.html#getselecteddrawingitems) to get the selected **DrawingItems** which will be helpful in further processing of the original image by another SDK. For example, the **DrawingItem** may refer to the boundaries of the region of interest that the user wishes to crop from the image.

On the **DrawingLayer** interface:

* Added method [`addDrawingItems()`](../api-reference/drawinglayer.html#adddrawingitems) to add one or multiple **DrawingItems**.
* Added method [`getDrawingItems()`](../api-reference/drawinglayer.html#getdrawingitems) to return all **DrawingItems**.
* Added method [`removeDrawingItems()`](../api-reference/drawinglayer.html#removedrawingitems) to remove one or multiple **DrawingItems**.
* Added method [`setDrawingItems()`](../api-reference/drawinglayer.html#setdrawingitems) to set new **DrawingItems** which means old  **DrawingItems** will be removed.
* Added method [`hasDrawingItem()`](../api-reference/drawinglayer.html#hasdrawingitem) to determine whether a **DrawingItem** exists on this **DrawingLayer**.
* Added method [`clearDrawingItems()`](../api-reference/drawinglayer.html#cleardrawingitems) to remove all **DrawingItems** from this **DrawingLayer**.
* Added method [`setMode()`](../api-reference/drawinglayer.html#setmode) to switch the **DrawingLayer** between editor and viewer mode.
* Added method [`getMode()`](../api-reference/drawinglayer.html#getmode) to get the current mode the **DrawingLayer** is in.
* Added method [`getId()`](../api-reference/drawinglayer.html#getid) to return the ID of the **DrawingLayer**.
* Added method [`setDrawingStyle()`](../api-reference/drawinglayer.html#setdrawingstyle) to use different **DrawingStyles** on the **DrawingLayer**.
* Added method [`setVisible()`](../api-reference/drawinglayer.html#setvisible) to show or hide the **DrawingLayer**.
* Added method [`isVisible()`](../api-reference/drawinglayer.html#isvisible) to return whether the **DrawingLayer** is visible.
* Added method [`renderAll()`](../api-reference/drawinglayer.html#renderall) to redraw all **DrawingItems**.
* Added event [`onSelectionChange()`](../api-reference/drawinglayer.html#onselectionchange) to listen on the selection or deselection of **DrawingItems** on the **DrawingLayer**.
