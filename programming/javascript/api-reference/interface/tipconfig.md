---
layout: default-layout
title: Interface TipConfig - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the TipConfig Interface of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: TipConfig, CameraEnhancer, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: TipConfig
permalink: /programming/javascript/api-reference/interface/tipconfig.html
---

# TipConfig

The `TipConfig` interface configures how the tip message box is displayed.

```ts
interface TipConfig {
  topLeftPoint: Point;
  width: number;
  duration: number;
  coordinateBase: "view" | "image";
}
```

## topLeftPoint

The top left point of the tip message box.

**See Also**

[Point](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/point.html)

## width

The width of the tip message box.

## duration

The display duration of the tip in milliseconds.

## coordinateBase

The base coordinate system used (e.g., "view" or "image").
