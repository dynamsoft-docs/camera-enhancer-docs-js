---
layout: default-layout
title: Interface DCEFrame - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the DCEFrame Interface of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: DCEFrame, CameraEnhancer, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: DCEFrame
permalink: /programming/javascript/api-reference/interface/dceframe.html
---

# DCEFrame

`interface` DCEFrame

The DCEFrame interface inherits from the `DSImageData` in the `Core.BasicStructures` namespace.

* isDCEFrame: `boolean`
  
  Returns whether this is a `DCEFrame`.

* toCanvas: `()=>HTMLCanvasElement`

  A `Function` which converts the image data to an `HTMLCanvasElement` object.

The following are extended from the basic interface [DSImgaeData](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/ds-image-data.html)

* bytes: `Uint8Array`

  The raw image data.

* format: `EnumImagePixelFormat`

  The pixel format of the image data. Read more about [EnumImagePixelFormat](https://www.dynamsoft.com/capture-vision/docs/core/enums/core/image-pixel-format.html?lang=js)

* stride: `number`

  The stride is the width of a single row of pixels (a scan line), rounded up to a four-byte boundary.

* width: `number`

  The width of the image data in pixels.

* height: `number`

  The height of the image data in pixels.

* tag: `VideoFrameTag`
  
  This property holds extra information about the image data. Note that [VideoFrameTag](videoframetag.md) is extended from [ImageTag](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/image-tag.html)