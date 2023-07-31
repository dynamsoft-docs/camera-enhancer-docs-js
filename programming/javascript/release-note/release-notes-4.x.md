---
layout: default-layout
title: JavaScript 4.x Release Notes  - Dynamsoft Camera Enhancer
description: This is the Release Notes page for Dynamsoft Camera Enhancer JavaScript SDK.
keywords:  camera enhancer, release notes, javascript
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: v4.x Release Notes
permalink: /programming/javascript/release-note/release-notes-4.x.html
---

# Release Notes - JavaScript 4.x

## 4.0.0 (08/04/2023)

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
