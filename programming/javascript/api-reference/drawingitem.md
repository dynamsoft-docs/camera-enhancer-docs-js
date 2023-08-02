---
layout: default-layout
title: DrawingItem - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the DrawingItem definitions of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: camera enhancer, drawingitem, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: DrawingItem
permalink: /programming/javascript/api-reference/drawingitem.html
---

# Class DrawingItem

| API Name                                        | Description                                                                                                |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| [drawingLayerId](drawingitem.md#drawinglayerid) | Returns the id of a `DrawingLayer` where the `DrawingItem` is drawn.                                       |
| [mediaType](drawingitem.md#mediatype)           | Returns the `mediaType` of the `DrawingItem`.                                                              |
| [coordinateBase](drawingitem.md#coordinatebase) | Sets or returns the `coordinateBase` which determines the meaning of the coordinates of the `DrawingItem`. |
| [drawingStyleId](drawingitem.md#drawingstyleid) | Sets or returns the id of the `DrawingStyle` that applies to the `DrawingItem`.                            |
| [setState()](drawingitem.md#setstate)           | Sets whether the `DrawingItem` is selected or not.                                                         |
| [getState()](drawingitem.md#getstate)           | Returns the state of the `DrawingItem`.                                                                    |
| [on()](drawingitem.md#on)                       | Adds an event listener to the `DrawingItem` for the event specified by `eventName`.                        |
| [off()](drawingitem.md#off)                     | Removes an event listener to the `DrawingItem` for the event specified by `eventName`.                     |
| [addNote()](drawingitem.md#addnote)             | Adds a `Note` to this `DrawingItem`.                                                                       |
| [getNote()](drawingitem.md#getnote)             | Returns a `Note` specified by its name.                                                                    |
| [hasNote()](drawingitem.md#hasnote)             | Returns whether a `Note` with the specified name exists on this `DrawingItem`.                             |
| [updateNote()](drawingitem.md#updatenote)       | Updates the content of a `Note` specified by its name.                                                     |
| [deleteNote()](drawingitem.md#deletenote)       | Deletes a `Note` specified by its name.                                                                    |
| [getAllNotes()](drawingitem.md#getallnotes)     | Returns all `Notes` on the `DrawingItem`.                                                                  |
| [clearNotes()](drawingitem.md#clearnotes)       | Deletes all `Notes` on the `DrawingItem`.                                                                  |

Child classes based on `DrawingItem`

## Class LineDrawingItem

| API Name                                            | Description                                                       |
| --------------------------------------------------- | ----------------------------------------------------------------- |
| [LineDrawingItem()](drawingitem.md#linedrawingitem) | Constructor of a `LineDrawingItem`.                               |
| [getLine()](drawingitem.md#getline)                 | Returns the `LineSegment` object the item is based on.            |
| [setLine()](drawingitem.md#setline)                 | Specifies a `LineSegment` object to be used for drawing the line. |

## Class RectDrawingItem

| API Name                                            | Description                                                |
| --------------------------------------------------- | ---------------------------------------------------------- |
| [RectDrawingItem()](drawingitem.md#rectdrawingitem) | Constructor of a `RectDrawingItem`.                        |
| [getRect()](drawingitem.md#getrect)                 | Returns the `Rect` object the item is based on.            |
| [setRect()](drawingitem.md#setrect)                 | Specifies a `Rect` object to be used for drawing the item. |

## Class QuadDrawingItem

| API Name                                            | Description                                                         |
| --------------------------------------------------- | ------------------------------------------------------------------- |
| [QuadDrawingItem()](drawingitem.md#quaddrawingitem) | Constructor of a `QuadDrawingItem`.                                 |
| [getQuad()](drawingitem.md#getquad)                 | Returns the `Quadrilateral` object the item is based on.            |
| [setQuad()](drawingitem.md#setquad)                 | Specifies a `Quadrilateral` object to be used for drawing the item. |

## Class TextDrawingItem

| API Name                                            | Description                                                         |
| --------------------------------------------------- | ------------------------------------------------------------------- |
| [TextDrawingItem()](drawingitem.md#textdrawingitem) | Constructor of a `TextDrawingItem`.                                 |
| [getText()](drawingitem.md#gettext)                 | Returns the text drawn.                                             |
| [setText()](drawingitem.md#settext)                 | Specifies the text to draw.                                         |
| [getTextRect()](drawingitem.md#gettextrect)         | Returns the `Rect` object which determines where the text is drawn. |
| [setTextRect()](drawingitem.md#settextrect)         | Specifies a `Rect` object in which the text is drawn.               |

## Class ImageDrawingItem

| API Name                                                  | Description                                                                       |
| --------------------------------------------------------- | --------------------------------------------------------------------------------- |
| [ImageDrawingItem()](drawingitem.md#imagedrawingitem)     | Constructor of a `ImageDrawingItem`.                                              |
| [maintainAspectRatio](drawingitem.md#maintainaspectratio) | Sets or returns whether aspect ratio of the image is maintained when it is drawn. |
| [getImage()](drawingitem.md#getimage)                     | Returns the image drawn.                                                          |
| [setImage()](drawingitem.md#setimage)                     | Specifies the image to draw.                                                      |
| [getImageRect()](drawingitem.md#gettextrect)              | Returns the `Rect` object which determines where the image is drawn.              |
| [setImageRect()](drawingitem.md#settextrect)              | Specifies a `Rect` object in which the image is drawn.                            |

## drawingLayerId

Returns the id of a `DrawingLayer` where the `DrawingItem` is drawn.

```typescript
readonly drawingLayerId: number;
```

## mediaType

Returns the `mediaType` of the `DrawingItem`.

```typescript
readonly mediaType: EnumDrawingItemMediaType;
```

## coordinateBase

Sets or returns the `coordinateBase` which determines the meaning of the coordinates of the `DrawingItem`.

```typescript
readonly coordinateBase: string;
```

## drawingStyleId

Sets or returns the id of the `DrawingStyle` that applies to the `DrawingItem`.

```typescript
drawingStyleId?: number;
```

## getState

Returns the state of the `DrawingItem`.

```typescript
getState(): EnumDrawingItemState;
```

**Return Value**

return a value of type `EnumDrawingItemState`.

## on

Adds an event listener to the `DrawingItem` for the event specified by `eventName`.

```typescript
on(eventName: string, listener(event: DrawingItemEvent): void): void;
```

**See Also**

* [DrawingItemEvent](interface/drawingitemevent.md)

## off

Removes an event listener to the `DrawingItem` for the event specified by `eventName`.

```typescript
off(eventName: string, listener(event: DrawingItemEvent): void): void;
```

**See Also**

* [DrawingItemEvent](interface/drawingitemevent.md)

## addNote

Adds a `Note` to this `DrawingItem`.

```typescript
addNote(note: Note, replace?: boolean): void;
```

**Parameters**

`note`: Expects an instance of the Note, including name and content properties to be passed when the method is called.
`replace`: Determines whether an existing note should be replaced when adding the new note.

## getNote

Returns a `Note` specified by its name.

```typescript
getNote(name: string): Note;
```

**Parameters**

`name`: The expects string representing the name of the note.

**Return Value**

Returns the corresponding Note object based on the provided name.

## hasNote

Returns whether a `Note` with the specified name exists on this `DrawingItem`.

```typescript
hasNote(name: string): boolean;
```

**Parameters**

`name`: The expects string representing the name of the note.

**Return Value**

Returns a value of boolean indicates whether a specific note exists with the given name.

## updateNote

Updates the content of a `Note` specified by its name.

```typescript
updateNote(name: string, content: any, mergeContent?: boolean): void;
```

**Parameters**

`name`: The string representing the name of the note.
`content`: The content of the note.
`mergeContent`: If this parameter is set to true, then the new content is added to the Note alongside the original content.

## deleteNote

Deletes a `Note` specified by its name.

```typescript
deleteNote(name: string): void;
```

**Parameters**

`name`: The string representing the name of the note.

## getAllNotes

Returns all `Notes` on the `DrawingItem`.

```typescript
getAllNotes(): Array<Note>;
```

**Return Value**

Returns an array of all Notes on the DrawingItem.

## clearNotes

Deletes all `Notes` on the `DrawingItem`.

```typescript
clearNotes(): void;
```

---

## LineDrawingItem

Constructor of a `LineDrawingItem`.

```typescript
constructor(line: Core.BasicStructures.LineSegment, drawingStyleId?: number) { super(Object) };
```

## getLine

Returns the `LineSegment` object the item is based on.

```typescript
getLine(): Core.BasicStructures.LineSegment;
```

**Return Value**

Returns the line of type `LineSegment`.

## setLine

Specifies a `LineSegment` object to be used for drawing the line.

```typescript
setLine(line: Core.BasicStructures.LineSegment): void;
```

**Parameters**

`line`: A line of type `Core.BasicStructures.LineSegment`.

---

## RectDrawingItem

Constructor of a `RectDrawingItem`.

```typescript
constructor(rect: Core.BasicStructures.Rect, drawingStyleId?: number) { super(Object) };
```

## getRect

Returns the `Rect` object the item is based on.

```typescript
getRect(): Core.BasicStructures.Rect;
```

**Return Value**

Returns the rectangle of type `Rect`.

## setRect

Specifies a `Rect` object to be used for drawing the item.

```typescript
setRect(rect: Core.BasicStructures.Rect): void;
```

**Parameters**

`rect`: A rectangle of type `Core.BasicStructures.Rect`.

---

## QuadDrawingItem

Constructor of a `QuadDrawingItem`.

```typescript
constructor(quad: Core.BasicStructures.Quadrilateral, drawingStyleId?: number) { super(Object) };
```

## getQuad

Returns the `Quadrilateral` object the item is based on.

```typescript
getQuad(): Core.BasicStructures.Quadrilateral;
```

**Return Value**

Returns the rectangle of type `Quadrilateral`.

## setQuad

Specifies a `Quadrilateral` object to be used for drawing the item.

```typescript
setQuad(quad: Core.BasicStructures.Quadrilateral): void;
```

**Parameters**

`quad`: A quadrilateral of type `Core.BasicStructures.Quadrilateral`.

---

## TextDrawingItem

Constructor of a `TextDrawingItem`.

```typescript
constructor(text: string, rect: Core.BasicStructures.Rect, drawingStyleId?: number) { super(Object) };
```

## getText

Returns the text drawn.

```typescript
getText(): string;
```

**Return Value**

Returns the rectangle of type `string`.

## setText

Specifies the text to draw.

```typescript
setText(text: string): void;
```

**Parameters**

`text`: A text string.

## getTextRect

Returns the `Rect` object which determines where the text is drawn.

```typescript
getTextRect(): Core.BasicStructures.Rect;
```

**Return Value**

Returns the rectangle of type `Rect`.

## setTextRect

Specifies a `Rect` object in which the text is drawn.

```typescript
setTextRect(rect: Core.BasicStructures.Rect): void;
```

**Parameters**

`rect`: A rectangle of type `Core.BasicStructures.Rect`.

---

## ImageDrawingItem()

Constructor of a `ImageDrawingItem`.

```typescript
constructor(
    image: Core.BasicStructures.DSImageData | HTMLImageElement | HTMLCanvasElement | HTMLVideoElement,
    rect: Core.BasicStructures.Rect,
    maintainAspectRatio: boolean,
    drawingStyleId?: number) { super(Object) };
```

## maintainAspectRatio

Sets or returns whether aspect ratio of the image is maintained when it is drawn.

```typescript
maintainAspectRatio: boolean;
```

## getImage

Returns the image drawn.

```typescript
getImage(): Core.BasicStructures.DSImageData | HTMLImageElement | HTMLCanvasElement | HTMLVideoElement;
```

## setImage

Specifies the image to draw.

```typescript
setImage(image: Core.BasicStructures.DSImageData | HTMLImageElement | HTMLCanvasElement | HTMLVideoElement): void;
```

## getImageRect

Returns the `Rect` object which determines where the image is drawn.

```typescript
getImageRect(): Core.BasicStructures.Rect;
```

**Return Value**

Returns the image located rectangle of type `Rect`.

## setImageRect

Specifies a `Rect` object in which the image is drawn.

```typescript
setImageRect(rect: Core.BasicStructures.Rect): void;
```

**Parameters**

`rect`: A rectangle of type `Core.BasicStructures.Rect`.