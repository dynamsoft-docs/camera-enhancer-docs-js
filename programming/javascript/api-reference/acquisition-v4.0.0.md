---
layout: default-layout
title: Acquisition - Dynamsoft Camera Enhancer JavaScript API
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK Acquisition.
keywords: camera enhancer, acquisition, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: Acquisition
permalink: /programming/javascript/api-reference/acquisition.html
---

# Class CameraEnhancer

## Frame Acquisition

| API Name                                                              | Description                                                                                         |
| --------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| [setScanRegion()](#setscanregion)                                     | Specifies which part of the original video is considered when processing frames.                    |
| [getScanRegion()](#getscanregion)                                     | Returns the scan region.                                                                            |
| [fetchImage()](#fetchimage)                                           | Returns a `DCEFrame` object which contains the image data of the latest frame from the video input. |
| [addImageToBuffer()](#addimagetobuffer)                               | Adds an `DSImageData` object to the buffer.                                                         |
| [setImageFetchInterval()](#setimagefetchinterval)                     | Sets the interval at which `startFetching()` is called when continued fetching has started.            |
| [getImageFetchInterval()](#getimagefetchinterval)                     | Returns the fetch interval.                                                                         |
| [startFetching()](#startfetching)                                     | Starts to continuously fetch images and put them into the buffer.                                   |
| [stopFetching()](#stopfetching)                                       | Stops fetching any more images.                                                                     |
| [setMaxImageCount()](#setmaximagecount)                               | Sets the size of the buffer as in how many images can be buffered.                                  |
| [getMaxImageCount()](#getmaximagecount)                               | Returns the size of the buffer.                                                                     |
| [getImageCount()](#getimagecount)                                     | Returns how many images are in buffer.                                                              |
| [hasImage()](#hasimage)                                               | Checks whether an image exists. The image is specified by its id.                                   |
| [getImage()](#getimage)                                               | Returns a `DCEFrame` object from the buffer.                                                        |
| [setNextImageToReturn()](#setnextimagetoreturn)                       | Specifies an image by its id to be returned when `getImage()` is called the next time.              |
| [setBufferOverflowProtectionMode()](#setbufferoverflowprotectionmode) | Sets a protection mode that determines what happens when the buffer overflows.                      |
| [getBufferOverflowProtectionMode()](#getbufferoverflowprotectionmode) | Returns the buffer protection mode.                                                                 |
| [isBufferEmpty()](#isbufferempty)                                     | Returns whether the buffer is empty.                                                                |
| [hasNextImageToFetch()](#hasnextimagetofetch)                         | Checks whether another image can be fetched. In other words, whether the video is still streaming.  |
| [setPixelFormat()](#setpixelformat)                                   | Sets the pixel format of the images returned by `getImage()`.                                       |
| [singleFrameMode()](#singleframemode)                                 | Returns or sets whether to enable the singe-frame mode.                                             |
| [takePhoto()](#takephoto)                                             | Invokes the system camera to take a frame with better image quality.                                |

## setScanRegion

Specifies which part of the original video is considered when processing frames.

```typescript
setScanRegion(region: Rect | DSRect): void;
```

**Parameters**

`region`: a `Rect` or `DSRect` object that specifies a part of the video.

**Return value**

None.

**Code Snippet**

```javascript
let scanRegion = {
    x: 25,
    y: 75,
    width: 25,
    height: 75
    isMeasuredInPercentage: true
};
cameraEnhancer.setScanRegion(scanRegion); 
```

**See also**

* [Rect](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/rect.html)
* [DSRect](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/ds-rect.html)

## getScanRegion

Returns the scan region.

```typescript
getScanRegion(): Rect | DSRect;
```

**Parameters**

None.

**Return value**

A `Rect` or `DSRect` object which specifies the scan region.

**Code Snippet**

```javascript
let region = cameraEnhancer.getScanRegion();
```

**See also**

* [DSRect](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/ds-rect.html)

## fetchImage

Returns a `DCEFrame` object which contains the image data of the latest frame from the video input.

```typescript
fetchImage(): DCEFrame;
```

**Parameters**

None.

**Return value**

A `DCEFrame` object which contains the image data of the frame and related information.

**Code Snippet**

```javascript
let image = cameraEnhancer.fetchImage();
document.body.appendChild(image.toCanvas());
```

**See also**

* [DCEFrame](interface/dceframe.md)

## addImageToBuffer

Adds an `DSImageData` object to the buffer.

```typescript
addImageToBuffer(image: DSImageData): void;
```

**Parameters**

* `image`: the image to be added to buffer.

**Return value**

None.

**Code Snippet**

```javascript
let image = cameraEnhancer.fetchImage();
cameraEnhancer.addImageToBuffer(image);
```

## setImageFetchInterval

Sets the interval at which `startFetching()` is called when continued fetching has started.

```typescript
setImageFetchInterval(interval: number): void;
```

**Parameters**

* `interval`: specifies the interval in milliseconds.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.setImageFetchInterval(200);
```

## getImageFetchInterval

Returns the fetch interval.

```typescript
getImageFetchInterval(): number;
```

**Parameters**

None.

**Return value**

The fetch interval.

**Code Snippet**

```javascript
let fetchInterval = cameraEnhancer.getImageFetchInterval();
```

## startFetching

Starts to continuously fetch images and put them into the buffer.

```typescript
startFetching(): void;
```

**Parameters**

None.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.startFetching();
```

## stopFetching

Stops fetching any more images.

```typescript
stopFetching(): void;
```

**Parameters**

None.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.stopFetching();
```

## setMaxImageCount

Sets the size of the buffer as in how many images can be buffered.

```typescript
setMaxImageCount: (count: number) void;
```

**Parameters**

* `count`: specifies how many images can be held in buffer.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.setMaxImageCount(10);
```

## getMaxImageCount

Returns the size of the buffer.

```typescript
getMaxImageCount(): number;
```

**Parameters**

None.

**Return value**

A number indicating how many images can be held in buffer.

**Code Snippet**

```javascript
let bufferSize = cameraEnhancer.getMaxImageCount();
```

## getImageCount

Returns how many images are in buffer.

```typescript
getImageCount(): number;
```

**Parameters**

None.

**Return value**

A number indicating how many images are held in buffer.

**Code Snippet**

```javascript
let imageCount = cameraEnhancer.getImageCount();
```

## hasImage

Checks whether an image exists. The image is specified by its id.

```typescript
hasImage(imageId: number): boolean;
```

**Parameters**

* `imageId`: specifies an image by its id.

**Return value**

True means the image exists in the buffer, false the opposite.

**Code Snippet**

```javascript
let imageCount = cameraEnhancer.hasImage(10);
```

## getImage

Returns a `DCEFrame` object from the buffer.
> This function retrieves the latest image added to the buffer, and removing it from the buffer in the process.

```typescript
getImage(): DCEFrame;
```

**Parameters**

None.

**Return value**

A `DCEFrame` object which contains the image data of the frame and related information.

**Code Snippet**

```javascript
let image = cameraEnhancer.getImage();
document.body.appendChild(image.toCanvas());
```

**See also**

* [DCEFrame](interface/dceframe.md)

## setNextImageToReturn

Specifies an image by its id to be returned when `getImage()` is called the next time.

```typescript
setNextImageToReturn(imageId: number, keepInBuffer?: boolean): void;
```

**Parameters**

* `imageId`: specifies the image by its id.  
* `keepInBuffer`(optional): specifies whether to keep the image in buffer after it is returned.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.setNextImageToReturn(10);
let image = cameraEnhancer.getImage();
document.body.appendChild(image.toCanvas());
```

## setBufferOverflowProtectionMode

Sets a protection mode that determines what happens when the buffer overflows.

```typescript
setBufferOverflowProtectionMode(mode:EnumBufferOverflowProtectionMode): void;
```

**Parameters**

* `mode`: specifies the protection mode.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.setBufferOverflowProtectionMode(EnumBufferOverflowProtectionMode.BOPM_Append);
```

**See also**

* [EnumBufferOverflowProtectionMode](https://www.dynamsoft.com/capture-vision/docs/core/enums/core/buffer-overflow-protection-mode.html?lang=js)

## getBufferOverflowProtectionMode

Returns the buffer protection mode.

```typescript
getBufferOverflowProtectionMode(): EnumBufferOverflowProtectionMode;
```

**Parameters**

* `mode`: specifies the protection mode.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.getBufferOverflowProtectionMode(EnumBufferOverflowProtectionMode.BOPM_Append);
```

**See also**

* [EnumBufferOverflowProtectionMode](https://www.dynamsoft.com/capture-vision/docs/core/enums/core/buffer-overflow-protection-mode.html?lang=js)

## isBufferEmpty

Returns whether the buffer is empty.

```typescript
isBufferEmpty(): boolean;
```

**Parameters**

None.

**Return value**

True means the buffer is empty, false the opposite.

**Code Snippet**

```javascript
if(cameraEnhancer.isBufferEmpty()) {
    console.log("There is no image in buffer!");
}
```

## hasNextImageToFetch

Checks whether another image can be fetched.

```typescript
hasNextImageToFetch(): boolean;
```

**Parameters**

None.

**Return value**

True means the input image source can supply more images, false means the input image source is closed or exhausted.

**Code Snippet**

```javascript
if(!cameraEnhancer.hasNextImageToFetch()) {
    console.log("The image source is exhausted!");
}
```

## setPixelFormat

Determines the format of the images added to the buffer when the `fetchImage()` or `startFetching()` method is called.

```typescript
setPixelFormat(pixelFormat: EnumImagePixelFormat.IPF_GRAYSCALED
                | EnumImagePixelFormat.IPF_ABGR_8888
                | EnumImagePixelFormat.IPF_ARGB_8888): void;
```

**Parameters**

* `pixelFormat`: specifies the format of the image to return.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.setPixelFormat(EnumImagePixelFormat.IPF_ARGB_8888);
let image = cameraEnhancer.getImage();
document.body.appendChild(image.toCanvas());
```

**See also**

* [EnumImagePixelFormat](https://www.dynamsoft.com/capture-vision/docs/core/enums/core/image-pixel-format.html?lang=js)

## singleFrameMode

Returns or sets whether to enable the singe-frame mode.

When the single-frame mode is enabled, the video will not stream in the built-in UI of the library. Instead, the user can click the UI to invoke the system camera interface to catch a frame or select an existing image from the device storage.

To get the actual data, add a event handler to the event 'singleFrameAcquired'.

```typescript
singleFrameMode: boolean;
```

**Code Snippet**

```javascript
(async () => {
    let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
    cameraEnhancer.on('singleFrameAcquired', frameData => {
        document.body.appendChild(frameData.toCanvas());
    });
    cameraEnhancer.singleFrameMode = true;
    await cameraEnhancer.open(true);
})();
```

> As shown in the code snippet above, `singleFrameMode` should be set before calling `open()`.

## takePhoto

Invokes the system camera to take a frame with better image quality or select an existing image from the device storage.

```typescript
takePhoto(listener: (dceFrame: DCEFrame) => void): void;
```

**Parameter**

`listener`: The listener callback function expects a single argument of type DCEFrame, representing the data related to the captured photo.

**Return Value**

None.

**Code Snippet**

```javascript
function handleCapturedPhoto(dceFrame) {
  console.log('Captured Photo Data:', dceFrame);
  // Process the captured photo data as needed.
}

// Capture a photo and invoke the listener with the captured data.
cameraEnhancer.takePhoto(handleCapturedPhoto);
```