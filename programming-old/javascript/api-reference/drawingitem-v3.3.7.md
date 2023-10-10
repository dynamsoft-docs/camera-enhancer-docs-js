---
layout: default-layout
title: DrawingItem - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the DrawingItem definitions of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: camera enhancer, drawingitem, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: DrawingItem
permalink: /programming/javascript/api-reference/drawingitem-v3.3.7.html
---

# DrawingItem

A DrawingItem can be one of seven types.

```typescript
type DrawingItem = DT_Rect | DT_Arc | DT_Line | DT_Polygon | DT_Text | DT_Image | DT_Group;
```

| Type Name | Description |
|---|---|
| [DT_Rect](#dt_rect) | Defines a DrawingItem the shape of a rectangle. |
| [DT_Arc](#dt_arc)   | Defines a DrawingItem the shape of a arc. |
| [DT_Line](#dt_line) | Defines a DrawingItem the shape of a line. |
| [DT_Polygon](#dt_polygon) | Defines a DrawingItem the shape of a polygon. |
| [DT_Text](#dt_text) | Defines a DrawingItem that draws text. |
| [DT_Image](#dt_image) | Defines a DrawingItem that draws an image. |
| [DT_Group](#dt_group) | Defines a DrawingItem which is a combination of more than one DrawingItem of the other six types.  |

## DT_Rect

Defines a DrawingItem the shape of a rectangle.

```typescript
class DT_Rect { 
  public constructor(x: number, y: number, width: number, height: number, styleId?: number) { };
  // The ID of a drawingLayer where the DrawingItem is drawn. Only assigned after it's added to the drawingLayer.
  readonly drawingLayerId: number;
  // The media type.
  readonly mediaType: "rect"; 
  // The style selector. If left blank, the drawingLayer will assume it's "default". Available values are "default" and "selected".
  styleSelector: string; 
  // The style ID expected to be used to paint this item. If left blank, the drawingLayer will decide which style to use.
  styleId?: number;
  // Sets the following properties of the DrawingItem:
  // 1. The coordinates of the upper-left corner of the rectangle, in pixels.
  //    x: number; y: number;
  // 2. The dimensions of the rectangle, in pixels.
  //    width: number; height: number;
  setAttribute: (property:string, value:any) => void;
  // Returns the values for the properties x, y, width & height.
  getAttribute: (property:string) => any;
  // Adds an event listener to the DrawingItem for the event specified by eventName. Allowed events are: mousedown, mouseup, dblclick, mouseover, mouseout (the last three don't work on mobile devices).
  on: (eventName: string, listener: (event: DrawingItemEvent) => void) => void;
  // Removes an event listener to the DrawingItem for the event specified by eventName.
  off: (eventName: string, listener: (event: DrawingItemEvent) => void) => void;
  // Adds a Note to this DrawingItem
  addNote: (note: Note, replace?: boolean) => void;
  // Returns a Note specified by its name.
  getNote: (name: string) => Note;
  // Returns whether a Note with the specified name exists on this DrawingItem.
  hasNote: (name: string) => boolean;
  // Updates the content of a Note specified by its name. If `mergeContent` is set to true, then the new content is added to the Note alongside the original content.
  updateNote: (name: string, content: any, mergeContent?: boolean) => void;
  // Deletes a Note specified by its name.
  deleteNote: (name: string) => void;
  // Returns all Notes on the DrawingItem.
  getNotes: () => Array<Note>;
  // Deletes all Notes on the DrawingItem.
  clearNotes: () => void;
} 
```

**See also**

* [Note](interface/note.html)
* [DrawingItemEvent](interface/drawingitemevent.html)

## DT_Arc

Defines a DrawingItem the shape of a arc.

```typescript
class DT_Arc { 
  constructor(x: number, y: number, radius: number, startAngle: number, endAngle: number, styleId?: number) { };
  // The ID of a drawingLayer where the DrawingItem is drawn. Only assigned after it's added to the drawingLayer.
  readonly drawingLayerId: number;
  // The media type.
  readonly mediaType: "rect"; 
  // The style selector. If left blank, the drawingLayer will assume it's "default". Available values are "default" and "selected".
  styleSelector: string; 
  // The style ID expected to be used to paint this item. If left blank, the drawingLayer will decide which style to use.
  styleId?: number;
  // Sets the following properties of the DrawingItem:
  // 1. The coordinates of the the center of the circle, in pixels.
  //    x: number; y: number;
  // 2. The radius of the circle, in pixels.
  //    radius: number; 
  // 3. The starting and ending angles (in degrees, not radians).
  //    startAngle: number, endAngle: number; 
  setAttribute: (property:string, value:any) => void;
  // Returns the values for the properties x, y, radius, startAngle & endAngle.
  getAttribute: (property:string) => any;
  // Adds an event listener to the DrawingItem for the event specified by eventName. Allowed events are: mousedown, mouseup, dblclick, mouseover, mouseout (the last three don't work on mobile devices).
  on: (eventName: string, listener: (event: DrawingItemEvent) => void) => void;
  // Removes an event listener to the DrawingItem for the event specified by eventName.
  off: (eventName: string, listener: (event: DrawingItemEvent) => void) => void;
  // Adds a Note to this DrawingItem
  addNote: (note: Note, replace?: boolean) => void;
  // Returns a Note specified by its name.
  getNote: (name: string) => Note;
  // Returns whether a Note with the specified name exists on this DrawingItem.
  hasNote: (name: string) => boolean;
  // Updates the content of a Note specified by its name. If `mergeContent` is set to true, then the new content is added to the Note alongside the original content.
  updateNote: (name: string, content: any, mergeContent?: boolean) => void;
  // Deletes a Note specified by its name.
  deleteNote: (name: string) => void;
  // Returns all Notes on the DrawingItem.
  getNotes: () => Array<Note>;
  // Deletes all Notes on the DrawingItem.
  clearNotes: () => void;
} 
```

**See also**

* [Note](interface/note.html)
* [DrawingItemEvent](interface/drawingitemevent.html)

## DT_Line

Defines a DrawingItem the shape of a line.

```typescript
class DT_Line {
  public constructor(startPoint: Point, endPoint: Point, styleId?: number) { };
  // The ID of a drawingLayer where the DrawingItem is drawn. Only assigned after it's added to the drawingLayer.
  readonly drawingLayerId: number;
  // The media type.
  readonly mediaType: "rect"; 
  // The style selector. If left blank, the drawingLayer will assume it's "default". Available values are "default" and "selected".
  styleSelector: string; 
  // The style ID expected to be used to paint this item. If left blank, the drawingLayer will decide which style to use.
  styleId?: number;
  // Sets the following properties of the DrawingItem:
  // 1. The coordinates of the staring point, in pixels.
  //    startPoint: Point; 
  // 2. The coordinates of the end point, in pixels.
  //    endPoint: Point; 
  setAttribute: (property:string, value:any) => void;
  // Returns the values for the properties startPoint and endPoint.
  getAttribute: (property:string) => any;
  // Adds an event listener to the DrawingItem for the event specified by eventName. Allowed events are: mousedown, mouseup, dblclick, mouseover, mouseout (the last three don't work on mobile devices).
  on: (eventName: string, listener: (event: DrawingItemEvent) => void) => void;
  // Removes an event listener to the DrawingItem for the event specified by eventName.
  off: (eventName: string, listener: (event: DrawingItemEvent) => void) => void;
  // Adds a Note to this DrawingItem
  addNote: (note: Note, replace?: boolean) => void;
  // Returns a Note specified by its name.
  getNote: (name: string) => Note;
  // Returns whether a Note with the specified name exists on this DrawingItem.
  hasNote: (name: string) => boolean;
  // Updates the content of a Note specified by its name. If `mergeContent` is set to true, then the new content is added to the Note alongside the original content.
  updateNote: (name: string, content: any, mergeContent?: boolean) => void;
  // Deletes a Note specified by its name.
  deleteNote: (name: string) => void;
  // Returns all Notes on the DrawingItem.
  getNotes: () => Array<Note>;
  // Deletes all Notes on the DrawingItem.
  clearNotes: () => void;
} 
```

**See also**

* [Point](interface/point.html)
* [Note](interface/note.html)
* [DrawingItemEvent](interface/drawingitemevent.html)

## DT_Polygon

Defines a DrawingItem the shape of a polygon.

```typescript
class DT_Polygon { 
  public constructor(vertices: Array<Point>, styleId?: number) { };
  // The ID of a drawingLayer where the DrawingItem is drawn. Only assigned after it's added to the drawingLayer.
  readonly drawingLayerId: number;
  // The media type.
  readonly mediaType: "rect"; 
  // The style selector. If left blank, the drawingLayer will assume it's "default". Available values are "default" and "selected".
  styleSelector: string; 
  // The style ID expected to be used to paint this item. If left blank, the drawingLayer will decide which style to use.
  styleId?: number;
  // Sets the property vertices: Array<Point>; 
  setAttribute: (property:string, value:any) => void;
  // Returns the value for the property vertices: Array<Point>; 
  getAttribute: (property:string) => any;
  // Adds an event listener to the DrawingItem for the event specified by eventName. Allowed events are: mousedown, mouseup, dblclick, mouseover, mouseout (the last three don't work on mobile devices).
  on: (eventName: string, listener: (event: DrawingItemEvent) => void) => void;
  // Removes an event listener to the DrawingItem for the event specified by eventName.
  off: (eventName: string, listener: (event: DrawingItemEvent) => void) => void;
  // Adds a Note to this DrawingItem
  addNote: (note: Note, replace?: boolean) => void;
  // Returns a Note specified by its name.
  getNote: (name: string) => Note;
  // Returns whether a Note with the specified name exists on this DrawingItem.
  hasNote: (name: string) => boolean;
  // Updates the content of a Note specified by its name. If `mergeContent` is set to true, then the new content is added to the Note alongside the original content.
  updateNote: (name: string, content: any, mergeContent?: boolean) => void;
  // Deletes a Note specified by its name.
  deleteNote: (name: string) => void;
  // Returns all Notes on the DrawingItem.
  getNotes: () => Array<Note>;
  // Deletes all Notes on the DrawingItem.
  clearNotes: () => void;
} 
```

**See also**

* [Point](interface/point.html)
* [Note](interface/note.html)
* [DrawingItemEvent](interface/drawingitemevent.html)

## DT_Text

Defines a DrawingItem that draws text within a text box with a fixed width. The text is wrapped to fit the width of the text box.

> Note
>
> The content of the text can include line breaks (`\n`) and tabs (`\t`).
>
> For example: "FistName:\tJohn\nLastName:\tDoe".

```typescript
class DT_Text { 
  public constructor(text: string, x: number, y: number, width: number, styleId?: number) { };
  // The ID of a drawingLayer where the DrawingItem is drawn. Only assigned after it's added to the drawingLayer.
  readonly drawingLayerId: number;
  // The media type.
  readonly mediaType: "rect"; 
  // The style selector. If left blank, the drawingLayer will assume it's "default". Available values are "default" and "selected".
  styleSelector: string; 
  // The style ID expected to be used to paint this item. If left blank, the drawingLayer will decide which style to use.
  styleId?: number;
  // Sets the following properties of the DrawingItem:
  // 1. The coordinates of the upper-left corner of the text box, in pixels.
  //    x: number; y: number;
  // 2. The width of the text box, in pixels.
  //    width: number,
  // 3. The text to be drawn.
  //    text: string; 
  setAttribute: (property:string, value:any) => void;
  // Returns the values for the properties x, y, width or text.
  getAttribute: (property:string) => any;
  // Adds an event listener to the DrawingItem for the event specified by eventName. Allowed events are: mousedown, mouseup, dblclick, mouseover, mouseout (the last three don't work on mobile devices).
  on: (eventName: string, listener: (event: DrawingItemEvent) => void) => void;
  // Removes an event listener to the DrawingItem for the event specified by eventName.
  off: (eventName: string, listener: (event: DrawingItemEvent) => void) => void;
  // Adds a Note to this DrawingItem
  addNote: (note: Note, replace?: boolean) => void;
  // Returns a Note specified by its name.
  getNote: (name: string) => Note;
  // Returns whether a Note with the specified name exists on this DrawingItem.
  hasNote: (name: string) => boolean;
  // Updates the content of a Note specified by its name. If `mergeContent` is set to true, then the new content is added to the Note alongside the original content.
  updateNote: (name: string, content: any, mergeContent?: boolean) => void;
  // Deletes a Note specified by its name.
  deleteNote: (name: string) => void;
  // Returns all Notes on the DrawingItem.
  getNotes: () => Array<Note>;
  // Deletes all Notes on the DrawingItem.
  clearNotes: () => void;
} 
```

**See also**

* [Note](interface/note.html)
* [DrawingItemEvent](interface/drawingitemevent.html)

## DT_Image

Defines a DrawingItem that draws an image.

```typescript
class DT_Image { 
  //NOTE: If an DT_Image instance has been constructed with an image, it can be replaced later with either an HTMLImageElement or an HTMLCanvasElement. However, an HTMLVideoElement can only be used during the constructing. 
  public constructor(image: HTMLImageElement | HTMLCanvasElement | HTMLVideoElement, x: number, y: number, styleId?: number) { };
  // The ID of a drawingLayer where the DrawingItem is drawn. Only assigned after it's added to the drawingLayer.
  readonly drawingLayerId: number;
  // The media type.
  readonly mediaType: "rect"; 
  // The style selector. If left blank, the drawingLayer will assume it's "default". Available values are "default" and "selected".
  styleSelector: string; 
  // The style ID expected to be used to paint this item. If left blank, the drawingLayer will decide which style to use.
  styleId?: number;
  // Sets the following properties of the DrawingItem:
  // 1. The coordinates of the upper-left corner of the image, in pixels.
  //    x: number; y: number;
  // 2. The image itself
  //    image: HTMLImageElement | HTMLCanvasElement | HTMLVideoElement
  setAttribute: (property:string, value:any) => void;
  // Returns the values for the properties x, y or image.
  getAttribute: (property:string) => any;
  // Adds an event listener to the DrawingItem for the event specified by eventName. Allowed events are: mousedown, mouseup, dblclick, mouseover, mouseout (the last three don't work on mobile devices).
  on: (eventName: string, listener: (event: DrawingItemEvent) => void) => void;
  // Removes an event listener to the DrawingItem for the event specified by eventName.
  off: (eventName: string, listener: (event: DrawingItemEvent) => void) => void;
  // Adds a Note to this DrawingItem
  addNote: (note: Note, replace?: boolean) => void;
  // Returns a Note specified by its name.
  getNote: (name: string) => Note;
  // Returns whether a Note with the specified name exists on this DrawingItem.
  hasNote: (name: string) => boolean;
  // Updates the content of a Note specified by its name. If `mergeContent` is set to true, then the new content is added to the Note alongside the original content.
  updateNote: (name: string, content: any, mergeContent?: boolean) => void;
  // Deletes a Note specified by its name.
  deleteNote: (name: string) => void;
  // Returns all Notes on the DrawingItem.
  getNotes: () => Array<Note>;
  // Deletes all Notes on the DrawingItem.
  clearNotes: () => void;
} 
```

**See also**

* [Note](interface/note.html)
* [DrawingItemEvent](interface/drawingitemevent.html)

## DT_Group

Defines a DrawingItem which is a combination of more than one DrawingItem of the other six types.

```typescript
class DT_Group { 
  public constructor(childItems: Array<DrawingItem>) { };
  // The ID of a drawingLayer where the DrawingItem is drawn. Only assigned after it's added to the drawingLayer.
  readonly drawingLayerId: number;
  // The media type.
  readonly mediaType: "rect"; 
  // The style selector. If left blank, the drawingLayer will assume it's "default". Available values are "default" and "selected".
  styleSelector: string; 
  // The style ID expected to be used to paint this item. If left blank, the drawingLayer will decide which style to use.
  styleId?: number;
  // Sets the coordinates of the upper-left corner of the DrawingItem:
  //    x: number; y: number;
  setAttribute: (property:string, value:any) => void;
  // Returns the values for the properties x or y.
  getAttribute: (property:string) => any;
  // Adds an event listener to the DrawingItem for the event specified by eventName. Allowed events are: mousedown, mouseup, dblclick, mouseover, mouseout (the last three don't work on mobile devices).
  on: (eventName: string, listener: (event: DrawingItemEvent) => void) => void;
  // Removes an event listener to the DrawingItem for the event specified by eventName.
  off: (eventName: string, listener: (event: DrawingItemEvent) => void) => void;
  // Adds a Note to this DrawingItem
  addNote: (note: Note, replace?: boolean) => void;
  // Returns a Note specified by its name.
  getNote: (name: string) => Note;
  // Returns whether a Note with the specified name exists on this DrawingItem.
  hasNote: (name: string) => boolean;
  // Updates the content of a Note specified by its name. If `mergeContent` is set to true, then the new content is added to the Note alongside the original content.
  updateNote: (name: string, content: any, mergeContent?: boolean) => void;
  // Deletes a Note specified by its name.
  deleteNote: (name: string) => void;
  // Returns all Notes on the DrawingItem.
  getNotes: () => Array<Note>;
  // Deletes all Notes on the DrawingItem.
  clearNotes: () => void;
} 
```

**See also**

* [Note](interface/note.html)
* [DrawingItemEvent](interface/drawingitemevent.html)
