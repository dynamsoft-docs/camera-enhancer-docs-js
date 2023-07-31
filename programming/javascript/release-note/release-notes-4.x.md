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

### Changelog:

* Refactored the camera controlling APIs of the `CameraEnhancer` class.
* Refactored the layer, scan region and tip configuration APIs of the `CameraView` class.
* Added class `ImageEditorView`, allowing users to edit and manipulate drawable graphics. With this new class, users can easily enhance the visual appearance of captured results.
* Added several enhanced features to the  `CameraEnhancer`  class, including enhanced-focus, auto-zoom, and tap-to-focus functionalities. These features can be enabled using the `enableEnhancedFeatures()` method of the `CameraEnhancer` class. Please note that a valid license is required to enable and use these enhanced features.