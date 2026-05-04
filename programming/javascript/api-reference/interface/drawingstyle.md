---
layout: default-layout
title: Interface DrawingStyle - Dynamsoft Camera Enhancer JavaScript API
description: "Understand the DrawingStyle interface in Dynamsoft Camera Enhancer JavaScript API and learn how it supports capture, camera, or result workflows for modern web."
keywords: DrawingStyle, CameraEnhancer, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: DrawingStyle
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

## Predefined DrawingStyles

The SDK comes with 12 default Drawing styles. Please refer to [Predefined DrawingStyle](../drawingstylemanager.md#predefined-drawingstyle-object).