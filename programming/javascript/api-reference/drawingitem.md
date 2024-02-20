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

The `DrawingItem` class specifies the foundational attributes and functionalities of a graphical element, including shapes, images, or textual sections, intended for rendering on a canvas. Functioning as an abstract class, it cannot be instantiated on its own. Instead, it serves as a blueprint for more specific subclasses, such as `QuadDrawingItem`, `TextDrawingItem`, and others, which inherit and tailor these properties and methods to suit diverse graphical requirements and contexts.

In this version, the subclasses include:

- [ImageDrawingItem](./imagedrawingitem.md)
- [LineDrawingItem](./linedrawingitem.md)
- [QuadDrawingItem](./quaddrawingitem.md)
- [RectDrawingItem](./rectdrawingitem.md)
- [TextDrawingItem](./textdrawingitem.md)

| Name                              | Description                                                                                            |
| --------------------------------- | ------------------------------------------------------------------------------------------------------ |
| [coordinateBase](#coordinatebase) | Returns or sets the coordinate system base.                                                            |
| [drawingLayerId](#drawinglayerid) | Returns the numeric ID for the `DrawingLayer` this `DrawingItem` belongs to.                           |
| [drawingStyleId](#drawingstyleid) | Returns or sets the numeric ID for the `DrawingStyle` that applies to this `DrawingItem`.              |
| [mediaType](#mediatype)           | Returns an enumeration value which indicates the type of this `DrawingItem` (e.g., image, line, text). |
| [getState()](#getstate)           | Returns the current state of the `DrawingItem`                                                         |
| [on()](#on)                       | Binds a listener for a specific event. `eventName`.                                                    |
| [off()](#off)                     | Unbinds a listener for a specific event.                                                               |
| [addNote()](#addnote)             | Adds a `Note` object to this `DrawingItem`.                                                            |
| [getNote()](#getnote)             | Returns a `Note` object specified by its name, if it exists.                                           |
| [getNotes()](#getnotes)           | Returns a collection of all existing `Note` objects on this `DrawingItem`.                             |
| [hasNote()](#hasnote)             | Checks if a `Note` object with the specified name exists.                                              |
| [updateNote()](#updatenote)       | Updates the content of a specified `Note` object.                                                      |
| [deleteNote()](#deletenote)       | Deletes a `Note` object specified by its name.                                                         |
| [clearNotes()](#clearnotes)       | Deletes all `Note` objects on this `DrawingItem`.                                                      |

## coordinateBase

Returns or sets the coordinate system base with a string:

- "view" for viewport-based coordinates or 
- "image" for image-based coordinates.

```typescript
coordinateBase: string;
```

## drawingLayerId

Returns the numeric ID for the `DrawingLayer` this `DrawingItem` belongs to. 

```typescript
readonly drawingLayerId: number;
```

## drawingStyleId

Returns or sets the numeric ID for the `DrawingStyle` that applies to this `DrawingItem`.

> Invoke [renderAll()](./drawinglayer.md#renderall) for the new `DrawingStyle` to take effect.

```typescript
drawingStyleId?: number;
```

## mediaType

Returns an enumeration value which indicates the type of this `DrawingItem` (e.g., image, line, text).

```typescript
readonly mediaType: EnumDrawingItemMediaType;
```

**See Also**

[EnumDrawingItemMediaType](./enum/enumdrawingitemmediatype.md)

## getState

Returns the current state of the `DrawingItem`.

```typescript
getState(): EnumDrawingItemState;
```

**Parameters**

None.

**Return Value**

The current state of the `DrawingItem`, of type `EnumDrawingItemState`.

**See Also**

[EnumDrawingItemState](./enum/enumdrawingitemstate.md)

## on

Binds a listener for a specific event.

```typescript
on(eventName: string, listener: (event: DrawingItemEvent) => void): void;
```

**Parameters**

`eventName`: specifies the event by its name. Allowed events are: `mousedown`, `mouseup`, `dblclick`, `mouseover` and `mouseout`.

`listener`: the event listener.

**Return Value**

None.

**See also**

[DrawingItemEvent](interface/drawingitemevent.md)

## off

Unbinds a listener for a specific event.

```typescript
off(eventName: string, listener(event: DrawingItemEvent): void): void;
```

**Parameters**

`eventName`: specifies the event by its name. Allowed events are: `mousedown`, `mouseup`, `dblclick`, `mouseover` and `mouseout`.

`listener`: the event listener.

**Return Value**

None.

**See also**

[DrawingItemEvent](interface/drawingitemevent.md)

## addNote

Adds a `Note` object to this `DrawingItem`.

```typescript
addNote(note: Note, replace?: boolean): void;
```

**Parameters**

`note`: specifies the `Note` object.

`replace`: [Optional] whether to replace an existing note if the notes share the same name.

**Return Value**

None.

**Code Snippet**

```js
let item = new Dynamsoft.DCE.DrawingItem.RectDrawingItem({
    x: 100,
    y: 200,
    width: 300,
    height: 300,
    isMeasuredInPercentage: false
});
item.addNote(
    {
        name: "Description", 
        content: {
            noteType: "Rectangle"
        }
    }, true
);
```

**See also**

[Note](interface/note.md)

## getNote

Returns a `Note` object specified by its name, if it exists.

```typescript
getNote(name: string): Note;
```

**Parameters**

`name`: specifies the name of the `Note` object.

**Return Value**

The corresponding `Note` object specified by its name, if it exists.

**Code Snippet**

```js
item.getNote("Description");
```

## getNotes

Returns a collection of all existing `Note` objects on this `DrawingItem`.

```typescript
getNotes(): Array<Note>;
```

**Code Snippet**

```js
item.getNotes();
```

**Parameters**

None.

**Return Value**

All existing `Note` objects on this `DrawingItem`.

**See Also**

[Note](./interface/note.md)

## hasNote

Checks if a `Note` object with the specified name exists.

```typescript
hasNote(name: string): boolean;
```

**Parameters**

`name`: specifies the name of the `Note` object.

**Return Value**

Boolean indicating whether the `Note` object exists.

**Code Snippet**

```js
item.hasNote("Description");
```

## updateNote

Updates the content of a specified `Note` object.

```typescript
updateNote(name: string, content: any, mergeContent?: boolean): void;
```

**Parameters**

`name`: specifies the name of the `Note` object.

`content`: specifies the new content, can be of any type.

`mergeContent`: [Optional] whether to merge the new content with the existing one.

**Return Value**

None.

**Code Snippet**

```js
item.updateNote(
    "Description", 
    {
        timeStamp: (new Date()).getTime()
    }, true
);
```

## deleteNote

Deletes a `Note` object specified by its name.

```typescript
deleteNote(name: string): void;
```

**Parameters**

`name`: specifies the name of the `Note` object.

**Return Value**

None.

**Code Snippet**

```js
item.deleteNote("Description");
```

## clearNotes

Deletes all `Note` objects on this `DrawingItem`.

```typescript
clearNotes(): void;
```

**Parameters**

None.

**Return Value**

None.

**Code Snippet**

```js
item.clearNotes();
```
