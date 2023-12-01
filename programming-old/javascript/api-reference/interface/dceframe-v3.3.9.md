---
layout: default-layout
title: Interface DCEFrame - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the DCEFrame Interface of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: DCEFrame, CameraEnhancer, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: DCEFrame
permalink: /programming/javascript/api-reference/interface/dceframe-v3.3.9.html
---

# DCEFrame

`interface` DCEFrame

* pixelFormat: `string`

  The pixel format of the image data. The value is limited to "rgba" (default), "rbga", "grba", "gbra", "brga", "bgra", "grey" or "grey32".

* stride: `number`

  The stride is the width of a single row of pixels (a scan line), rounded up to a four-byte boundary.

* data: `Uint8Array`

  The raw image data.

* region: `Region`

  The region based on which the original frame is cropped.

* isCropped: `boolean`

  Whether the image was cropped from the original frame.

* sx: `number`

  The horizontal coordinate of the upper left point of the `data` on the original frame. If the frame was not cropped, the coordinate is 0.

* sy: `number`

  The vertical coordinate of the upper left point of the `data` on the original frame. If the frame was not cropped, the coordinate is 0.

* width: `number`

  The width of the image data.

* height: `number`

  The height of the image data.

* timeSpent: `number`

  The time in miniseconds spent in acquiring the frame.

* timeStamp: `number`

  The timeStamp at which point the frame acquisition finished.

* toCanvas: `()=>HTMLCanvasElement`

  A `Function` which converts the image data to an `HTMLCanvasElement` object.
  
