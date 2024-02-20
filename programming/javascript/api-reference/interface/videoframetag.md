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

The `VideoFrameTag` interface extends the `ImageTag` interface and introduces additional attributes tailored for characterizing images extracted from video streams, known as [DCEFrames](./dceframe.md).

```typescript
interface VideoFrameTag extends ImageTag {
    cropRegion: DSRect;
    currentHeight: number;
    currentWidth: number;
    isCropped: boolean;
    originalHeight: number;
    originalWidth: number;
    timeSpent: number;
    timeStamp: number;
}
```

## cropRegion

The region based on which the original frame was cropped. If `isCropped` is false, the region covers the entire original image.

**See Also**

[DSRect](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/ds-rect.html)

## currentWidth

The current width of the video frame after cropping.

## currentHeight

The current height of the video frame after cropping.

## isCropped

Indicates whether the video frame is cropped.

## originalWidth

The original width of the video frame before any cropping.

## originalHeight

The original height of the video frame before any cropping.

## timeSpent

The time spent acquiring the frame, in milliseconds.

## timeStamp

The timestamp marking the completion of the frame acquisition.
  