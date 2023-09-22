---
layout: default-layout
title: CameraView APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the page for Dynamsoft Camera Enhancer JavaScript SDK CameraView APIs.
keywords: cameraView, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: CameraView
permalink: /programming/javascript/api-reference/cameraview-v3.3.6.html
---

# CameraView

### Create and Destroy Instances

| API Name                                     | Description                                                                              |
| -------------------------------------------- | ---------------------------------------------------------------------------------------- |
| `static` [createInstance()](#createinstance) | Creates a `CameraView` instance.                                                         |
| [dispose()](#dispose)                        | Releases all resources used by the `CameraView` instance.                                |
| [disposed](#disposed)                        | A readonly boolean value indicating whether the `CameraView` instance has been disposed. |
| [getUIElement()](#getuielement)              | Returns the HTML element that is used by the `CameraView` instance.                      |
| [setUIElement()](#setuielement)              | Specifies an HTML element for the `CameraView` instance to use as its UI element.        |

### Drawing and UI

| API Name                                                          | Description                                                                                               |
| ----------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| [createDrawingLayer()](#createdrawinglayer)                       | Creates a DrawingLayer object and put it in an array of DrawingLayers.                                    |
| [getDrawingLayer()](#getdrawinglayer)                             | Gets the DrawingLayer specified by its ID.                                                                |
| [getAllDrawingLayers()](#getalldrawinglayers)                     | Returns an array of all DrawingLayer objects.                                                             |
| [deleteUserDefinedDrawingLayer()](#deleteuserdefineddrawinglayer) | Deletes a DrawingLayer object specified by its ID.                                                        |
| [clearUserDefinedDrawingLayers()](#clearuserdefineddrawinglayers) | Removes all user-defined DrawingLayers.                                                                   |
| [setTipConfig()](#settipconfig)                                   | Configures the tip feature.                                                                               |
| [getTipConfig()](#gettipconfig)                                   | Returns the configuration of the tip.                                                                     |
| [setTipVisible()](#settipvisible)                                 | Sets whether to show the tip.                                                                             |
| [isTipVisible()](#istipvisible)                                   | Returns whether the tip is visible.                                                                       |
| [updateTipMessage()](#updatetipmessage)                           | Updates the message shown in the tip.                                                                     |
| [getVisibleRegionOfVideo()](#getvisibleregionofvideo)             | Returns a `Region` object which specifies which part of the original video is shown in the video element. |
| [getVideoElement](#getvideoelement)                               | Returns the video element used by the `CameraView` instance.                                              |
| [setScanRegionMaskStyle()](#setscanregionmaskstyle)               | Sets the drawing style for the scan-region mask.                                                          |
| [getScanRegionMaskStyle()](#getscanregionmaskstyle)               | Returns the drawing style for the scan-region mask.                                                       |
| [setScanRegionMaskVisible()](#setscanregionmaskvisible)           | Sets whether to show the scan-region mask.                                                                |
| [isScanRegionMaskVisible()](#isscanregionmaskvisible)             | Returns whether the scan-region mask is visible.                                                          |
| [setScanLaserVisible()](#setscanlaservisible)                     | Sets whether to show the laser that indicates the scanning is going on.                                   |
| [isScanLaserVisible()](#isscanlaservisible)                       | Returns whether the laser is visible.                                                                     |

## createInstance

Creates a `CameraView` instance.

## dispose

Releases all resources used by the `CameraView` instance.

## disposed

A readonly boolean value indicating whether the `CameraView` instance has been disposed.

## getUIElement

Returns the HTML element that is used by the `CameraView` instance.

## setUIElement

Specifies an HTML element for the `CameraView` instance to use as its UI element.

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


## getVisibleRegionOfVideo

Returns a `Region` object which specifies which part of the original video is shown in the video element


## getVideoElement

Returns the video element used by the `CameraView` instance


## setScanRegionMaskStyle

Sets the drawing style for the scan-region mask


## getScanRegionMaskStyle

Returns the drawing style for the scan-region mask


## setScanRegionMaskVisible

Sets whether to show the scan-region mask


## isScanRegionMaskVisible

Returns whether the scan-region mask is visible


## setScanLaserVisible

Sets whether to show the laser that indicates the scanning is going on


## isScanLaserVisible

Returns whether the laser is visible

