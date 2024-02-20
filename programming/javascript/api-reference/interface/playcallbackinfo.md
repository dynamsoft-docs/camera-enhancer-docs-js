---
layout: default-layout
title: Interface PlayCallbackInfo - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the PlayCallbackInfo Interface of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: PlayCallbackInfo, CameraEnhancer, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: PlayCallbackInfo
permalink: /programming/javascript/api-reference/interface/playcallbackinfo.html
---

# PlayCallbackInfo

The `PlayCallbackInfo` interface specifies the unique identifier of a camera along with its resolution following any modifications or operations applied to it.

```ts
interface PlayCallbackInfo {
  deviceId: string;
  height: number;
  width: number;
}
```

## deviceId

The unique identifier of the camera.

## height

The height of the video frame.

## width

The width of the video frame.
