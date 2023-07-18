---
layout: default-layout
title: Interface VideoFrameTag - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the VideoFrameTag Interface of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: VideoFrameTag, CameraEnhancer, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: VideoFrameTag
permalink: /programming/javascript/api-reference/interface/videoframetag.html
---

# VideoFrameTag

`interface` VideoFrameTag

* isCropped: `boolean`

  Whether the image was cropped from the original frame.

* cropRegion: `Region`

  The region based on which the original frame was cropped.

* originalWidth: `number`
  
  The width of the original frame.

* originalHeight: `number`  

  The height of the original frame.

* currentWidth: `number`

  The width of the DCEFrame.

* currentHeight: `number`

  The height of the DCEFrame.

* timeSpent: `number`

  The time in miniseconds spent in acquiring the frame.

* timeStamp: `number`

  The timeStamp at which point the frame acquisition finished.