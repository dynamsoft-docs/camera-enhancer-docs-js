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

The `DrawingStyle` interface defines a customizable set of style properties that can be applied to a [DrawingItem](../drawingitem.md). 

```ts
interface DrawingStyle {
  fillStyle?: string;
  fontFamily?: string;
  fontSize?: number;
  readonly id?: number;
  lineWidth?: number;
  paintMode?: string;
  strokeStyle?: string;
}
```

## fillStyle

The fill color and opacity in rgba format. If not specified, the default is "rgba(245, 236, 73, 0.5)".

## fontFamily

The font family for text elements. If not specified, the default is "consolas".

## fontSize
 
The font size for text elements. If not specified, the default is 40.

## id

ID for the drawing style.

> NOTE: The `id` property is immutable and is exclusively assigned at the creation of a new drawing style.

## lineWidth

The width of lines. If not specified, the default is 2.

## paintMode

The mode of painting (e.g., "fill", "stroke" or "strokeAndFill"). If not specified, the default is "stroke".

## strokeStyle

The stroke color and opacity in rgba format. If not specified, the default is "rgba(245, 236, 73, 1)".

## Built-in DrawingStyles

The SDK comes with 8 default Drawing styles. Their style definitions are listed below

```javascript
// DrawingStyle 1 (STYLE_BLUE_STROKE)
// Used by Dynamsoft Document Normalizer for DrawingItems in "default" state.
{
  "id": 1,
  "lineWidth": 4,
  "fillStyle": "rgba(73, 173, 245, 0.3)",
  "strokeStyle": "rgba(73, 173, 245, 1)",
  "paintMode": "stroke",
  "fontFamily": "consolas",
  "fontSize": 40
}
// DrawingStyle 2 (STYLE_GREEN_STROKE_FILL)
// Used by Dynamsoft Label Recognizer for DrawingItems in "default" state.
{
  "id": 2,
  "lineWidth": 2,
  "fillStyle": "rgba(73, 245, 73, 0.3)",
  "strokeStyle": "rgba(73, 245, 73, 0.9)",
  "paintMode": "strokeAndFill",
  "fontFamily": "consolas",
  "fontSize": 40
}
// DrawingStyle 3 (STYLE_ORANGE_STROKE_FILL)
// Used by Dynamsoft Barcode Reader for DrawingItems in "default" state.
{
  "id": 3,
  "lineWidth": 2,
  "fillStyle": "rgba(254, 180, 32, 0.3)",
  "strokeStyle": "rgba(254, 180, 32, 0.9)",
  "paintMode": "strokeAndFill",
  "fontFamily": "consolas",
  "fontSize": 40
}
// DrawingStyle 4 (STYLE_YELLOW_STROKE)
// Used by custom DrawingLayers for DrawingItems in "default" state.
{
  "id": 4,
  "lineWidth": 2,
  "fillStyle": "rgba(245, 236, 73, 0.3)",
  "strokeStyle": "rgba(245, 236, 73, 1)",
  "paintMode": "stroke",
  "fontFamily": "consolas",
  "fontSize": 40
}
// DrawingStyle 5 (STYLE_BLUE_STROKE_FILL)
// Used by Dynamsoft Document Normalizer for DrawingItems in "selected" state.
{
  "id": 5,
  "lineWidth": 4,
  "fillStyle": "rgba(73, 173, 245, 0.3)",
  "strokeStyle": "rgba(73, 173, 245, 1)",
  "paintMode": "strokeAndFill",
  "fontFamily": "consolas",
  "fontSize": 40
}
// DrawingStyle 6 (STYLE_GREEN_STROKE_FILL)
{
  "id": 6,
  "lineWidth": 2,
  "fillStyle": "rgba(73, 245, 73, 0.3)",
  "strokeStyle": "rgba(73, 245, 73, 0.9)",
  "paintMode": "strokeAndFill",
  "fontFamily": "consolas",
  "fontSize": 40
}
// DrawingStyle 7
// Used by Dynamsoft Barcode Reader for DrawingItems in "selected" state.
{
  "id": 7,
  "lineWidth": 2,
  "fillStyle": "rgba(254, 180, 32, 0.3)",
  "strokeStyle": "rgba(254, 180, 32, 1)",
  "paintMode": "strokeAndFill",
  "fontFamily": "consolas",
  "fontSize": 40
}
// DrawingStyle 8 (STYLE_YELLOW_STROKE_FILL)
// Used by custom DrawingLayers for DrawingItems in "selected" state.
{
  "id": 8,
  "lineWidth": 2,
  "fillStyle": "rgba(245, 236, 73, 0.3)",
  "strokeStyle": "rgba(245, 236, 73, 1)",
  "paintMode": "strokeAndFill",
  "fontFamily": "consolas",
  "fontSize": 40
}
```