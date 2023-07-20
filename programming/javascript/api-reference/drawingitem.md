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
| [on](drawingitem.md#on)                         | Adds an event listener to the `DrawingItem` for the event specified by `eventName`.                        |
| [off](drawingitem.md#off)                       | Removes an event listener to the `DrawingItem` for the event specified by `eventName`.                     |
| [addNote()](drawingitem.md#addnote)             | Adds a `Note` to this `DrawingItem`.                                                                       |
| [getNote()](drawingitem.md#getnote)             | Returns a `Note` specified by its name.                                                                    |
| [hasNote()](drawingitem.md#hasnote)             | Returns whether a `Note` with the specified name exists on this `DrawingItem`.                             |
| [updateNote()](drawingitem.md#updatenote)       | Updates the content of a `Note` specified by its name.                                                     |
| [deleteNote()](drawingitem.md#deletenote)       | Deletes a `Note` specified by its name.                                                                    |
| [getAllNotes()](drawingitem.md#getallnotes)     | Returns all `Notes` on the `DrawingItem`.                                                                  |
| [clearNotes()](drawingitem.md#clearnotes)       | Deletes all `Notes` on the `DrawingItem`.                                                                  |

Child classes based on `DrawingItem`

## LineDrawingItem


| API Name                                            | Description                                                       |
| --------------------------------------------------- | ----------------------------------------------------------------- |
| [LineDrawingItem()](drawingitem.md#linedrawingitem) | Constructor of a `LineDrawingItem`.                               |
| [getLine](drawingitem.md#getline)                   | Returns the `LineSegment` object the item is based on.            |
| [setLine](drawingitem.md#setline)                   | Specifies a `LineSegment` object to be used for drawing the line. |

## RectDrawingItem

| API Name                                            | Description                                                |
| --------------------------------------------------- | ---------------------------------------------------------- |
| [RectDrawingItem()](drawingitem.md#rectdrawingitem) | Constructor of a `RectDrawingItem`.                        |
| [getRect](drawingitem.md#getrect)                   | Returns the `Rect` object the item is based on.            |
| [setRect](drawingitem.md#setrect)                   | Specifies a `Rect` object to be used for drawing the item. |

## QuadDrawingItem


| API Name                                            | Description                                                         |
| --------------------------------------------------- | ------------------------------------------------------------------- |
| [QuadDrawingItem()](drawingitem.md#quaddrawingitem) | Constructor of a `QuadDrawingItem`.                                 |
| [getQuad](drawingitem.md#getquad)                   | Returns the `Quadrilateral` object the item is based on.            |
| [setQuad](drawingitem.md#setquad)                   | Specifies a `Quadrilateral` object to be used for drawing the item. |

## TextDrawingItem

| API Name                                            | Description                                                         |
| --------------------------------------------------- | ------------------------------------------------------------------- |
| [TextDrawingItem()](drawingitem.md#textdrawingitem) | Constructor of a `TextDrawingItem`.                                 |
| [getText](drawingitem.md#gettext)                   | Returns the text drawn.                                             |
| [setText](drawingitem.md#settext)                   | Specifies the text to draw.                                         |
| [getTextRect](drawingitem.md#gettextrect)           | Returns the `Rect` object which determines where the text is drawn. |
| [setTextRect](drawingitem.md#settextrect)           | Specifies a `Rect` object in which the text is drawn.               |

## ImageDrawingItem

| API Name                                                  | Description                                                                       |
| --------------------------------------------------------- | --------------------------------------------------------------------------------- |
| [ImageDrawingItem()](drawingitem.md#imagedrawingitem)     | Constructor of a `ImageDrawingItem`.                                              |
| [maintainAspectRatio](drawingitem.md#maintainaspectratio) | Sets or returns whether aspect ratio of the image is maintained when it is drawn. |
| [getImage](drawingitem.md#getimage)                       | Returns the image drawn.                                                          |
| [setImage](drawingitem.md#setimage)                       | Specifies the image to draw.                                                      |
| [getImageRect](drawingitem.md#gettextrect)                | Returns the `Rect` object which determines where the image is drawn.              |
| [setImageRect](drawingitem.md#settextrect)                | Specifies a `Rect` object in which the image is drawn.                            |


## drawingLayerId

Returns the id of a `DrawingLayer` where the `DrawingItem` is drawn


## mediaType

Returns the `mediaType` of the `DrawingItem`


## coordinateBase

Sets or returns the `coordinateBase` which determines the meaning of the coordinates of the `DrawingItem`


## drawingStyleId

Sets or returns the id of the `DrawingStyle` that applies to the `DrawingItem`


## setState()

Sets whether the `DrawingItem` is selected or not


## getState()

Returns the state of the `DrawingItem`


## on

Adds an event listener to the `DrawingItem` for the event specified by `eventName`


## off

Removes an event listener to the `DrawingItem` for the event specified by `eventName`


## addNote()

Adds a `Note` to this `DrawingItem`


## getNote()

Returns a `Note` specified by its name


## hasNote()

Returns whether a `Note` with the specified name exists on this `DrawingItem`


## updateNote()

Updates the content of a `Note` specified by its name


## deleteNote()

Deletes a `Note` specified by its name


## getAllNotes()

Returns all `Notes` on the `DrawingItem`


## clearNotes()

Deletes all `Notes` on the `DrawingItem`



Child classes based on `DrawingItem`

---

## LineDrawingItem()

Constructor of a `LineDrawingItem`


## getLine

Returns the `LineSegment` object the item is based on


## setLine

Specifies a `LineSegment` object to be used for drawing the line


---

## RectDrawingItem()

Constructor of a `RectDrawingItem`


## getRect

Returns the `Rect` object the item is based on


## setRect

Specifies a `Rect` object to be used for drawing the item


---

## QuadDrawingItem()

Constructor of a `QuadDrawingItem`


## getQuad

Returns the `Quadrilateral` object the item is based on


## setQuad

Specifies a `Quadrilateral` object to be used for drawing the item


---

## TextDrawingItem()

Constructor of a `TextDrawingItem`


## getText

Returns the text drawn


## setText

Specifies the text to draw


## getTextRect

Returns the `Rect` object which determines where the text is drawn


## setTextRect

Specifies a `Rect` object in which the text is drawn


---

## ImageDrawingItem()

Constructor of a `ImageDrawingItem`


## maintainAspectRatio

Sets or returns whether aspect ratio of the image is maintained when it is drawn


## getImage

Returns the image drawn


## setImage

Specifies the image to draw


## getImageRect

Returns the `Rect` object which determines where the image is drawn


## setImageRect

Specifies a `Rect` object in which the image is drawn


