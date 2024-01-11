---
layout: default-layout
title: ImageEditorView APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the page for Dynamsoft Camera Enhancer JavaScript SDK ImageEditorView APIs.
keywords: ImageEditorView, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: ImageEditorView
permalink: /programming/javascript/api-reference/imageeditorview-v3.3.9.html
---

# ImageEditorView

### Create and Destroy Instances

| API Name                                     | Description                                                                                   |
| -------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `static` [createInstance()](#createinstance) | Creates an `ImageEditorView` instance.                                                         |
| [dispose()](#dispose)                        | Releases all resources used by the `ImageEditorView` instance.                                |
| [disposed](#disposed)                        | A readonly boolean value indicating whether the `ImageEditorView` instance has been disposed. |
| [getUIElement()](#getuielement)              | Returns the HTML element that is used by the `ImageEditorView` instance.                      |
| [setUIElement()](#setuielement)              | Specifies an HTML element for the `ImageEditorView` instance to use as its UI element.        |

### Drawing and UI

| API Name                                                                | Description                                                              |
| ----------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| [createDrawingLayer()](#createdrawinglayer)                             | Creates a DrawingLayer object and put it in an array of DrawingLayers.   |
| [getDrawingLayer()](#getdrawinglayer)                                   | Gets the DrawingLayer specified by its ID.                               |
| [getAllDrawingLayers()](#getalldrawinglayers)                           | Returns an array of all DrawingLayer objects.                            |
| [deleteUserDefinedDrawingLayer()](#deleteuserdefineddrawinglayer)       | Deletes a DrawingLayer object specified by its ID.                       |
| [clearUserDefinedDrawingLayers()](#clearuserdefineddrawinglayers)       | Removes all user-defined DrawingLayers.                                  |
| [setTipConfig()](#settipconfig)                                         | Configures the tip feature.                                              |
| [getTipConfig()](#gettipconfig)                                         | Returns the configuration of the tip.                                    |
| [setTipVisible()](#settipvisible)                                       | Sets whether to show the tip.                                            |
| [isTipVisible()](#istipvisible)                                         | Returns whether the tip is visible.                                      |
| [updateTipMessage()](#updatetipmessage)                                 | Updates the message shown in the tip.                                    |
| [getSelectedDrawingItems()](imageeditorview.html#getselecteddrawingitems) | Returns the selected DrawingItem object(s).                              |
| [setVideoFit()](imageeditorview.html#setvideofit)                         | Sets the `object-fit` CSS property of the video element.                 |
| [getVideoFit()](imageeditorview.html#getvideofit)                         | Returns the value of the `object-fit` CSS property of the video element. |
| [setOriginalImage()](imageeditorview.html#setoriginalimage)               | Sets the image to be drawn on the image editor view.          |
| [getOriginalImage()](imageeditorview.html#setoriginalimage)               | Returns the image drawn on the image editor.                             |

## createInstance

Creates an `ImageEditorView` instance.

## dispose

Releases all resources used by the `ImageEditorView` instance.

## disposed

A readonly boolean value indicating whether the `ImageEditorView` instance has been disposed.

## getUIElement

Returns the HTML element that is used by the `ImageEditorView` instance.

## setUIElement

Specifies an HTML element for the `ImageEditorView` instance to use as its UI element.

## createDrawingLayer

Creates a DrawingLayer object and put it in an array of DrawingLayers


## getDrawingLayer

Gets the DrawingLayer specified by its ID


## getAllDrawingLayers

Returns an array of all DrawingLayer objects


## deleteUserDefinedDrawingLayer

Deletes a DrawingLayer object specified by its ID


## clearUserDefinedDrawingLayers

Removes all user-defined DrawingLayers


## setTipConfig

Configures the tip feature


## getTipConfig

Returns the configuration of the tip


## setTipVisible

Sets whether to show the tip


## isTipVisible

Returns whether the tip is visible


## updateTipMessage

Updates the message shown in the tip


## getSelectedDrawingItems

Returns the selected DrawingItem object(s).

## setVideoFit

Sets the `object-fit` CSS property of the video element.


## getVideoFit

Returns the value of the `object-fit` CSS property of the video element.

## setOriginalImage

Sets the image to be drawn on the image editor view.

## getOriginalImage

Returns the image drawn on the image editor.
