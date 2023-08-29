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

`interface` DrawingItemEvent

The DrawingItemEvent interface extends the default `Event` interface of DOM with the following extra fields.

* targetItem: `DrawingItem`

  The DrawingItem onto which the event was dispatched.

* itemClientX, itemClientY: `number`

  The coordinates of the top-left vertex of the minimum bounding box of the DrawingItem, relative to the viewpoint of the browser window.

* itemPageX, itemPageY: `number`

  The coordinates of the top-left vertex of the minimum bounding box of the DrawingItem, relative to the entire document (the webpage content).
