---
layout: default-layout
title: JavaScript 4.x Release Notes  - Dynamsoft Camera Enhancer
description: This is the Release Notes page for Dynamsoft Camera Enhancer JavaScript SDK v 4.x.
keywords:  camera enhancer, release notes, javascript
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: v4.x Release Notes
permalink: /programming/javascript/release-note/release-notes-4.x.html
---

# Release Notes - JavaScript 4.x

## 4.0.2 (03/28/2024)

### New

* Implemented a visual magnifier to facilitate adjustment of corner points.

### Improved

* Enhanced "beep" quality by allowing multiple soundtracks now.
* Renamed the method `getDrawingStyles()` to `getAllDrawingStyles()` under class `DrawingStyleManager` for clarity.

### Fixed

* Fixed a bug where changing `singleFrameMode` would get drawing layers removed.
* Fixed a bug where an unnecessary button to appear on iOS devices when invoking the `takePhoto()` method.
* Fixed a bug specific to iOS 17, where reopening the camera after leaving the browser could result in failure.

## 4.0.1 (01/11/2024)

### Added

* Added `beepSoundSource` & `vibrateDuration` to the class [`Feedback`](../api-reference/feedback.md).
* Added `maintainAspectRatio` to [`ImageDrawingItem`](../api-reference/drawingitem.md#imagedrawingitem).
* Added [`clearAllInnerDrawingItems()`](../api-reference/cameraview.md#clearallinnerdrawingitems) to clear internally added DrawingItems.
* Added [`setErrorListener()`](../api-reference/auxiliary.md#seterrorlistener) to receive errors occurred during image acquisition.
* Added [`cameraOpenTimeout`](../api-reference/camera-control.md#cameraopentimeout) to control the maximum time allowed for opening a selected camera.

### Improved

* Updated the behaviour of [`SingleFrameMode`](../api-reference/acquisition.md#singleframemode) to allow an Android or iOS device user to make use of the camera without having to select between the camera and image gallery as the image source. 
* Updated the method [`setScanRegion()`](../api-reference/acquisition.md#setscanregion) to allow passing `null` to clear the scan region.
* Updated the resolution selection drop-down box to make it more intuitive.
* Updated `setZoom()` to support Safari on iOS v17.x.

### Fixed

* Fixed issues with the methods `setZoom()` & `getZoomSettings()` so that they can now work with static videos.
* Fixed issues with the autozoom or enhanced-focus features to prevent them from throwing unnecessary error messages.
* Fixed an issue with unstable video streaming upon opening the camera on iOS 17.x.

## 4.0.0 (08/24/2023)

### Changelog

* Separated the user interaction functionality from the original `CameraEnhancer` class into two new dedicated classes: `CameraView` and `ImageEditorView`:
  * The `CameraView` class is responsible for streaming video with real-time interaction such as highlighting certain objects found in the video;
  * The `ImageEditorView` class is responsible for displaying a single image with real-time interaction such as editing the boundaries of an object found in the image.
* Refactored the `CameraEnhancer` class to be compliant with the [ImageSourceAdapter](https://www.dynamsoft.com/capture-vision/docs/core/architecture/input.html#image-source-adapter) interface.
* Improved the built-in drawing logic:
  * Added the `DrawingStyleManager` class to manage `DrawingStyles`;
  * Renamed basic `DrawingItem` types;
  * Expanded the drawing logic to include the ScanRegion indicators.
* Refactored the `Tip` feature with a `TipConfig` interface and methods like `setTipConfig()`, `getTipConfig()`, `setTipVisible()` and `isTipVisible()`.
* The following features are grouped together as enhanced features that require a license. They can be enabled or disabled with the methods `enableEnhancedFeatures()` or `disableEnhancedFeatures()`:
  * Enhanced-focus. This feature used to be called auto-focus. Now it is defined as `EnumEnhancedFeatures.EF_ENHANCED_FOCUS`.
  * Auto-zoom. This feature is defined as `EnumEnhancedFeatures.EF_AUTO_ZOOM`, and we allow the zoom range to be set or returned with the methods `setAutoZoomRange()` and `getAutoZoomRange()`.
  * Tap-to-focus. This feature used to be controlled by the method `enableTapToFocus()`. Now it is defined as `EnumEnhancedFeatures.EF_TAP_TO_FOCUS`.
* Added the method `takePhoto()` to the `CameraEnhancer` class to allow users to temporarily invoke the system camera to capture a video frame with higher quality
