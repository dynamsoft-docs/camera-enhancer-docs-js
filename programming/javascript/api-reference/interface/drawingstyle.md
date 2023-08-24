---
layout: default-layout
title: Interface DrawingStyle - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the DrawingStyle Interface of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: DrawingStyle, CameraEnhancer, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: DrawingStyle
permalink: /programming/javascript/api-reference/interface/drawingstyle.html
---

# DrawingStyle

`interface` DrawingStyle

* id: `number`

  The ID of the current `DrawingStyle` .

* fillStyle: `string`

  The fill color of the current `DrawingStyle` . Default: `rgba(245, 236, 73, 0.3)`.

* fontFamily: `string`

  The fontFamily of the current `DrawingStyle` . Default: `sans-serif`.

* fontSize: `number`

  The fontSize of the current `DrawingStyle` . Default: `10`.

* lineWidth: `number`

  The line width (in pixels) of the current `DrawingStyle` . Default: `2`.

* paintMode: "fill" \| "stroke" \| "strokeAndFill"

  Three paint modes provided. Default: `stroke`.

* strokeStyle: `string`

  The stroke color of the current `DrawingStyle` . Default: `rgba(245, 236, 73, 1)`.

## Built-in DrawingStyles

  The SDK comes with 8 default Drawing styles. Their style definitions are listed below

  ```javascript
  // DrawingStyle 1
  // Used by Dynamsoft Document Normalizer for DrawingItems in "default" state.
  {
      id: 1,
      fillStyle: "rgba(73, 173, 245, 0.3)",
      fontFamily: "consolas",
      fontSize: 40,
      lineWidth: 4,
      paintMode: "stroke",
      strokeStyle: "rgba(73, 173, 245, 1)"
  }
  // DrawingStyle 2
  // Used by Dynamsoft Label Recognizer for DrawingItems in "default" state.
  {
      id: 2,
      fillStyle: "rgba(73, 245, 73, 0.3)",
      fontFamily: "consolas",
      fontSize: 40,      
      lineWidth: 2,
      paintMode: "strokeAndFill",
      strokeStyle: "rgba(73, 245, 73, 0.9)"
  }
  // DrawingStyle 3
  // Used by Dynamsoft Barcode Reader for DrawingItems in "default" state.
  {
      id: 3,
      fillStyle: "rgba(254, 180, 32, 0.3)",
      fontFamily: "consolas",
      fontSize: 40,
      lineWidth: 2,
      paintMode: "strokeAndFill",
      strokeStyle: "rgba(254, 180, 32, 0.9)"
  }
  // DrawingStyle 4
  // Used by all custom DrawingLayers for DrawingItems in "default" state.
  {
      id: 4,
      fillStyle: "rgba(245, 236, 73, 0.3)",
      fontFamily: "consolas",
      fontSize: 40,
      lineWidth: 2,
      paintMode: "stroke",
      strokeStyle: "rgba(245, 236, 73, 1)"
  }
  // DrawingStyle 5
  // Used by Dynamsoft Document Normalizer for DrawingItems in "selected" state.
  {
      id: 5,
      fillStyle: "rgba(73, 173, 245, 0.3)",
      fontFamily: "consolas",
      fontSize: 40,
      lineWidth: 4,
      paintMode: "strokeAndFill",
      strokeStyle: "rgba(73, 173, 245, 1)"
  }
  // DrawingStyle 6
  // Used by Dynamsoft Label Recognizer for DrawingItems in "selected" state.
  {
      id: 6,
      fillStyle: "rgba(73, 245, 73, 0.3)",
      fontFamily: "consolas",
      fontSize: 40,
      lineWidth: 2,
      paintMode: "strokeAndFill",
      strokeStyle: "rgba(73, 245, 73, 0.9)"
  }
  // DrawingStyle 7
  // Used by Dynamsoft Barcode Reader for DrawingItems in "selected" state.
  {
      id: 7,
      fillStyle: "rgba(254, 180, 32, 0.3)",
      fontFamily: "consolas",
      fontSize: 40,
      lineWidth: 2,
      paintMode: "strokeAndFill",
      strokeStyle: "rgba(254, 180, 32, 1)"
  }
  // DrawingStyle 8
  // Used by custom DrawingLayers for DrawingItems in "selected" state.
  {
      id: 8,
      fillStyle: "rgba(245, 236, 73, 0.3)",
      fontFamily: "consolas",
      fontSize: 40,
      lineWidth: 2,
      paintMode: "strokeAndFill",
      strokeStyle: "rgba(245, 236, 73, 1)"
  }
  ```
