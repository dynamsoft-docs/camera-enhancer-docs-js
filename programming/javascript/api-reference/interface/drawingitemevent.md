---
layout: default-layout
title: Interface DrawingItemEvent - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the DrawingItemEvent Interface of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: DrawingItemEvent, CameraEnhancer, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: DrawingItemEvent
permalink: /programming/javascript/api-reference/interface/drawingitemevent.html
---

# DrawingItemEvent

The `DrawingItemEvent` interface extends the [Event](https://developer.mozilla.org/en-US/docs/Web/API/Event) interface and represents an event bound to a [DrawingItem](../drawingitem.md).

```ts
interface DrawingItemEvent extends Event {
  targetItem: DrawingItem,
  itemClientX: number;
  itemClientY: number;
  itemPageX: number;
  itemPageY: number;
}
```

## targetItem

The drawing item that is the target of the event.

**See Also**

[DrawingItem](../drawingitem.md)

## itemClientX

The X coordinate of the item relative to the viewpoint of the browser window..

## itemClientY

The Y coordinate of the item relative to the viewpoint of the browser window..

## itemPageX

The X coordinate of the item relative to the entire document (the webpage content).

## itemPageY

The Y coordinate of the item relative to the entire document (the webpage content).
