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

The `DCEFrame` interface extends the [DSImageData](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/ds-image-data.html) interface and represents an image extracted from video streams (video frame).

```ts
interface DCEFrame extends DSImageData {
  isDCEFrame: boolean;
  toCanvas: () => HTMLCanvasElement;
  tag?: VideoFrameTag;
}
```

## isDCEFrame
  
Flag indicating whether the frame is a `DCEFrame`.

## toCanvas

Converts the image data into an HTMLCanvasElement for display or further manipulation in web applications.

**See Also** 

[HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement)

## tag: `VideoFrameTag`
  
Holds extra information about the image data which is extracted from video streams.
  
**See Also**
  
[VideoFrameTag](videoframetag.md)