---
layout: default-layout
title: Acquisition - Dynamsoft Camera Enhancer JavaScript API
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK Acquisition.
keywords: camera enhancer, acquisition, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: Acquisition
permalink: /programming/javascript/api-reference/acquisition-v2.0.3.html
---

# Frame Acquisition

| API Name | Description |
|---|---|
| [getFrame()](#getframe) | Returns a `DCEFrame` object which contains the image data of the latest frame from the video input. |
| [singleFrameMode](#singleframemode) | Returns or sets whether to enable the single-frame mode. |
| [onSingleFrameAcquired](#onsingleframeacquired) | This event is triggered when a new frame / image is acquired under the single-frame mode. |

## getFrame

Returns a `DCEFrame` object which contains the image data of the latest frame from the video input.

```typescript
getFrame(region?:Region): DCEFrame
```

**Parameters**

`region` : optional parameter of the type `Region` . It specifies a rectangular area on the image. If passed, the method only returns the frame cropped by the region.

**Return value**

A `DCEFrame` object which contains the image data of the (cropped) frame and related information.

**Code Snippet**

```javascript
// Returns only the 25% center area of the frame
let frameData = enhancer.getFrame({
    regionBottom: 75,
    regionRight: 75,
    regionLeft: 25,
    regionTop: 25,
    regionMeasuredByPercentage: true
});
document.body.appendChild(frameData.canvas);
```

**See also**

* [DCEFrame](interface/dceframe.md)
* [Region](interface/region.md)

## singleFrameMode

Returns or sets whether to enable the singe-frame mode. When the single-frame mode is enabled, the video will not stream in the built-in UI of the library. Instead, the user can click the UI to invoke the system camera interface to catch a frame or select an existing image from the device storage.

```typescript
singleFrameMode: boolean
```

**Code Snippet**

```javascript
let pEnhancer = null;
(async () => {
    let enhancer = await (pEnhancer = pEnhancer || Dynamsoft.DCE.CameraEnhancer.createInstance());
    enhancer.singleFrameMode = true;
    await enhancer.open();
})();
```

## onSingleFrameAcquired

This event is triggered when a new frame / image is acquired under the single-frame mode.

```typescript
onSingleFrameAcquired: (file: File) => {}
```

**Arguments**

`file` : a `File` object representing the image the user chose or a frame from the video input.

**Code Snippet**

```javascript
let pEnhancer = null;
(async () => {
    let enhancer = await (pEnhancer = pEnhancer || Dynamsoft.DCE.CameraEnhancer.createInstance());
    enhancer.onSingleFrameAcquired = file => {
        console.log(file.size);
    };
    await enhancer.open();
})();
```

**See also**

* [DCEFrame](interface/dceframe.md)
