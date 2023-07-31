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

`interface` TipConfig

* topLeftPoint: [`Point`](point.md);

  Defines where to put the tip by specifying its top left point.

* width: `number`
  
  Specifies how wide in pixels the tip message box is.

* duration: `number`
  
  Specifies in milliseconds how long the tip is shown before it disappears.

* coordinateBase: `"view" | "image"`
  
  Specifies the coordinate base which determines the actual behaviour of the properties `topLeftPoint` and `width`.
  
