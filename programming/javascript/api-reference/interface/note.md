---
layout: default-layout
title: Interface Note - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the Note Interface of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: Note, CameraEnhancer, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: Note
permalink: /programming/javascript/api-reference/interface/note.html
---

# Note

The `Note` interface defines a structure to store extra information in a [DrawingItem](../drawingitem.md). A `DrawingItem` can have one or multiple `Notes`.

```ts
interface Note {
  /** The name of the note. */
  name: string;
  /** The content of the note, can be of any type. */
  content: any;
}
```

## name

The name of the note.

## content

The content of the note, can be of any type.
