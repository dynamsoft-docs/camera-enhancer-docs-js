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

# Frame Acquisition

| Name                                                                | Description                                                                                                            |
| ------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| [addImageToBuffer](#addImageToBuffer)                               | Adds an image to the internal buffer.                                                                                  |
| [clearBuffer](#clearBuffer)                                         | Clears all images from the buffer, resetting the state for new image fetching.                                         |
| [fetchImage](#fetchImage)                                           | Fetches the current frame from the camera's video feed.                                                                |
| [getBufferOverflowProtectionMode](#getBufferOverflowProtectionMode) | Retrieves the current mode for handling buffer overflow.                                                               |
| [getColourChannelUsageType](#getColourChannelUsageType)             | Retrieves the current usage type for color channels in images.                                                         |
| [getImage](#getImage)                                               | Retrieves a buffered image, of type `DSImageData`.                                                                     |
| [getImageCount](#getImageCount)                                     | Retrieves the current number of images in the buffer.                                                                  |
| [getImageFetchInterval](#getImageFetchInterval)                     | Retrieves the current interval at which images are continuously fetched from the camera's video feed.                  |
| [getMaxImageCount](#getMaxImageCount)                               | Retrieves the maximum number of images that can be buffered.                                                           |
| [getPixelFormat](#getPixelFormat)                                   | Retrieves the current pixel format used for images fetched from the camera.                                            |
| [getScanRegion](#getScanRegion)                                     | Retrieves the current scan region set within the camera's view.                                                        |
| [hasImage](#hasImage)                                               | Checks if an image with the specified ID is present in the buffer.                                                     |
| [hasNextImageToFetch](#hasNextImageToFetch)                         | Determines whether there are more images available to fetch.                                                           |
| [isBufferEmpty](#isBufferEmpty)                                     | Determines whether the buffer is currently empty.                                                                      |
| [setBufferOverflowProtectionMode](#setBufferOverflowProtectionMode) | Sets the behavior for handling new incoming images when the buffer is full.                                            |
| [setColourChannelUsageType](#setColourChannelUsageType)             | Sets the usage type for color channels in images.                                                                      |
| [setErrorListener](#setErrorListener)                               | Sets an error listener to receive notifications about errors that occur during image source operations.                |
| [setImageFetchInterval](#setImageFetchInterval)                     | Sets the interval at which images are continuously fetched from the camera's video feed.                               |
| [setMaxImageCount](#setMaxImageCount)                               | Sets the maximum number of images that can be buffered at any time.                                                    |
| [setNextImageToReturn](#setNextImageToReturn)                       | Sets the processing priority of a specific image so that it is returned the next time `getImage()` is called.          |
| [setPixelFormat](#setPixelFormat)                                   | Sets the pixel format for the images fetched from the camera.                                                          |
| [setScanRegion](#setScanRegion)                                     | Sets the scan region within the camera's view which limits the frame acquisition to a specific area of the video feed. |
| [singleFrameMode](#singleFrameMode)                                 | Controls the single-frame mode of the `CameraEnhancer`.                                                                |
| [startFetching](#startFetching)                                     | Starts the process of fetching images.                                                                                 |
| [stopFetching](#stopFetching)                                       | Stops the process of fetching images.                                                                                  |
| [takePhoto](#takePhoto)                                             | Initiates a sequence to capture a single frame/image, halting the video stream temporarily.                            |

## addImageToBuffer

Adds an image to the internal buffer.

```typescript
addImageToBuffer(image: DSImageData): void;
```

**Parameters**

`image`: an instance of `DSImageData` containing the image to buffer.

**Return value**

None.

**Code Snippet**

```javascript
let image = cameraEnhancer.fetchImage();
cameraEnhancer.addImageToBuffer(image);
```

## clearBuffer

Clears all images from the buffer, resetting the state for new image fetching.

```typescript
clearBuffer(): void;
```

**Parameters**

None.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.clearBuffer()
```

## fetchImage

Fetches the current frame from the camera's video feed. 

This method is used to obtain the latest image captured by the camera.

```typescript
fetchImage(): DCEFrame;
```

**Parameters**

None.

**Return value**

A `DCEFrame` object representing the current frame. The structure and content of this object will depend on the pixel format set by `setPixelFormat()` and other settings.

**Code Snippet**

```javascript
let image = cameraEnhancer.fetchImage();
document.body.appendChild(image.toCanvas());
```

**See also**

[DCEFrame](interface/dceframe.md)

## getBufferOverflowProtectionMode

Retrieves the current mode for handling buffer overflow.

```typescript
getBufferOverflowProtectionMode(): EnumBufferOverflowProtectionMode;
```

**Parameters**

None.

**Return value**

The current buffer overflow protection mode.

**Code Snippet**

```javascript
cameraEnhancer.getBufferOverflowProtectionMode();
```

**See also**

[EnumBufferOverflowProtectionMode](https://www.dynamsoft.com/capture-vision/docs/core/enums/core/buffer-overflow-protection-mode.html?lang=js)

## getColourChannelUsageType

Retrieves the current usage type for color channels in images.

```typescript
getColourChannelUsageType(): EnumColourChannelUsageType;
```
**Parameters**

None.

**Return value**

The current color channel usage type.

**Code Snippet**

```javascript
cameraEnhancer.getColourChannelUsageType();
```

**See also**

[EnumColourChannelUsageType](https://www.dynamsoft.com/capture-vision/docs/core/enums/core/colour-channel-usage-type.html?lang=js)

## getImage

Retrieves a buffered image, of type `DSImageData`.

> This function retrieves the latest image added to the buffer, and removes it from the buffer in the process.

```typescript
getImage(): DCEFrame;
```

**Parameters**

None.

**Return value**

A `DSImageData` object retrieved from the buffer which contains the image data of the frame and related information.

**Code Snippet**

```javascript
let image = cameraEnhancer.getImage();
document.body.appendChild(image.toCanvas());
```

**See also**

[DCEFrame](interface/dceframe.md)

## getImageCount

Retrieves the current number of images in the buffer.

```typescript
getImageCount(): number;
```

**Parameters**

None.

**Return value**

The current image count in the buffer.

**Code Snippet**

```javascript
let imageCount = cameraEnhancer.getImageCount();
```

## getImageFetchInterval

Retrieves the current interval at which images are continuously fetched from the camera's video feed.

```typescript
getImageFetchInterval(): number;
```

**Parameters**

None.

**Return value**

The current fetch interval, specified in milliseconds.

**Code Snippet**

```javascript
let fetchInterval = cameraEnhancer.getImageFetchInterval();
```
     
## getMaxImageCount

Retrieves the maximum number of images that can be buffered.

```typescript
getMaxImageCount(): number;
```

**Parameters**

None.

**Return value**

The maximum image count for the buffer.

**Code Snippet**

```javascript
let bufferSize = cameraEnhancer.getMaxImageCount();
```

## getPixelFormat

Retrieves the current pixel format used for images fetched from the camera.

```typescript
getPixelFormat(): EnumImagePixelFormat;
```
             
**Parameters**

None.

**Return value**

The current pixel format, which could be one of the following: `IPF_GRAYSCALED`, `IPF_ABGR_8888`, and `IPF_ARGB_8888`.

**Code Snippet**

```javascript
let pixelFormat = cameraEnhancer.getPixelFormat();
console.log(pixelFormat);
```

## getScanRegion

Retrieves the current scan region set within the camera's view.

Note: If no scan region has been explicitly set before calling this method, an error may be thrown, indicating the necessity to define a scan region beforehand.

```typescript
getScanRegion(): Rect | DSRect;
```

**Parameters**

None.

**Return value**
 
A `DSRect` or `Rect` object representing the current scan region.

**Code Snippet**

```javascript
let region = cameraEnhancer.getScanRegion();
```

**See also**

[Rect](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/rect.html)

[DSRect](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/ds-rect.html)

## hasImage

Checks if an image with the specified ID is present in the buffer.

```typescript
hasImage(imageId: number): boolean;
```

**Parameters**

`imageId`: the ID of the image to check.

**Return value**

Boolean indicating whether the image is present in the buffer.

**Code Snippet**

```javascript
console.log(cameraEnhancer.hasImage(10));
```

## hasNextImageToFetch

Determines whether there are more images available to fetch.

```typescript
hasNextImageToFetch(): boolean;
```

**Parameters**

None.

**Return value**

Boolean indicating whether more images can be fetched. `false` means the image source is closed or exhausted.

**Code Snippet**

```javascript
if(!cameraEnhancer.hasNextImageToFetch()) {
    console.log("The image source is exhausted!");
}
```

## isBufferEmpty

Determines whether the buffer is currently empty.

```typescript
isBufferEmpty(): boolean;
```

**Parameters**

None.

**Return value**

Boolean indicating whether the buffer is empty.

**Code Snippet**

```javascript
if(cameraEnhancer.isBufferEmpty()) {
    console.log("There is no image in buffer!");
}
```

## setBufferOverflowProtectionMode

Sets the behavior for handling new incoming images when the buffer is full.

```typescript
setBufferOverflowProtectionMode(mode:EnumBufferOverflowProtectionMode): void;
```

**Parameters**

`mode`: one of the modes defined in `EnumBufferOverflowProtectionMode`, specifying how to handle buffer overflow.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.setBufferOverflowProtectionMode(Dynamsoft.Core.EnumBufferOverflowProtectionMode.BOPM_UPDATE);
```

**See also**

[EnumBufferOverflowProtectionMode](https://www.dynamsoft.com/capture-vision/docs/core/enums/core/buffer-overflow-protection-mode.html?lang=js)

## setColourChannelUsageType

Sets the usage type for color channels in images.

```typescript
setColourChannelUsageType(type: EnumColourChannelUsageType): void;
```

**Parameters**

`type`: one of the types defined in `EnumColourChannelUsageType`, specifying how color channels should be used.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.setColourChannelUsageType(Dynamsoft.Core.EnumColourChannelUsageType.CCUT_FULL_CHANNEL);
```

**See also**

[EnumColourChannelUsageType](https://www.dynamsoft.com/capture-vision/docs/core/enums/core/colour-channel-usage-type.html?lang=js)

## setErrorListener

Sets an error listener to receive notifications about errors that occur during image source operations.

```typescript
setErrorListener(listener: ImageSourceErrorListener): void;
```

**Parameters**

`listener`: an instance of `ImageSourceErrorListener` or its derived class to handle error notifications.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.setErrorListener(Dynamsoft.Core.EnumColourChannelUsageType.CCUT_FULL_CHANNEL);
```

**See also**

[ImageSourceErrorListener](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/image-source-error-listener.html)

## setImageFetchInterval

Sets the interval at which images are continuously fetched from the camera's video feed. 

This method allows for controlling how frequently new frames are obtained when `startFetching()` is invoked, which can be useful for reducing computational load or for pacing the frame processing rate.

```typescript
setImageFetchInterval(interval: number): void;
```

**Parameters**

`interval`: the desired interval between fetches, specified in milliseconds.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.setImageFetchInterval(200);
```

## setMaxImageCount

Sets the maximum number of images that can be buffered at any time.

```typescript
setMaxImageCount: (count: number) void;
```

**Parameters**

`count`: the maximum number of images the buffer can hold.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.setMaxImageCount(10);
```

## setNextImageToReturn

Sets the processing priority of a specific image so that it is returned the next time `getImage()` is called.

```typescript
setNextImageToReturn(imageId: number, keepInBuffer?: boolean): void;
```

**Parameters**

`imageId`: the ID of the image to prioritize.

`keepInBuffer`: [Optional] boolean indicating whether to keep the image in the buffer after it has been returned.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.setNextImageToReturn(10);
let image = cameraEnhancer.getImage();
document.body.appendChild(image.toCanvas());
```

## startFetching

Starts the process of fetching images.

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

## setPixelFormat

Sets the pixel format for the images fetched from the camera, which determines the format of the images added to the buffer when the `fetchImage()` or `startFetching()` method is called.

```typescript
setPixelFormat(pixelFormat: EnumImagePixelFormat.IPF_GRAYSCALED
                | EnumImagePixelFormat.IPF_ABGR_8888
                | EnumImagePixelFormat.IPF_ARGB_8888): void;
```

**Parameters**

`pixelFormat`: the desired pixel format for the images. Supported formats include `IPF_GRAYSCALED`, `IPF_ABGR_8888`, and `IPF_ARGB_8888`.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.setPixelFormat(EnumImagePixelFormat.IPF_ARGB_8888);
let image = cameraEnhancer.getImage();
document.body.appendChild(image.toCanvas());
```

**See also**

[EnumImagePixelFormat](https://www.dynamsoft.com/capture-vision/docs/core/enums/core/image-pixel-format.html?lang=js)

## setScanRegion

Sets the scan region within the camera's view which limits the frame acquisition to a specific area of the video feed.

Note: The region is always specified relative to the original video size, regardless of any transformations or zoom applied to the video display.

```typescript
setScanRegion(region?: Rect | DSRect): void;
```

**Parameters**

`region`: specifies the scan region.

**Return value**

None.

**Code Snippet**

```javascript
let scanRegion = {
    x: 25,
    y: 25,
    width: 50,
    height: 50,
    isMeasuredInPercentage: true
};
cameraEnhancer.setScanRegion(scanRegion); 
//...
cameraEnhancer.setScanRegion(null); //Cancel the scan region.
```

**See also**

[Rect](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/rect.html)

[DSRect](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/ds-rect.html)

## singleFrameMode

Controls the single-frame mode of the `CameraEnhancer`.

This mode is designed for scenarios where live camera feed is either not required, not supported by the browser, or when processing static images is preferred. Depending on the setting, it can alter the behavior of how images are sourced for processing.

- "disabled": The `CameraEnhancer` operates in its default mode, attempting to stream live video from the camera. This is the standard behavior in environments where camera access is supported and permitted.
- "image": The user is prompted to select a local image file for processing. This mode is useful for applications that need to process a single image instead of a continuous video stream. It can be used in any environment, regardless of camera support.
- "camera": The behavior varies based on the device type:
  - On desktop platforms, it prompts the user to select a local image, similar to the "image" mode.
  - On mobile devices, it invokes the system camera application, allowing the user to capture a new photo for processing. This leverages the device's camera in environments where direct camera streaming through the browser might not be available or preferred.

This property provides flexibility in handling different operational contexts, making it easier to adapt to varying application requirements and user environments.

```typescript
singleFrameMode: "disabled" | "camera" | "image";
```

**Code Snippet**

```javascript
(async () => {
    let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
    cameraEnhancer.on('singleFrameAcquired', frameData => {
        document.body.appendChild(frameData.toCanvas());
    });
    cameraEnhancer.singleFrameMode = "image";
    await cameraEnhancer.open();
})();
```

> As shown in the code snippet above, `singleFrameMode` should be set before calling `open()`.

## stopFetching

Stops the process of fetching images.

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

## takePhoto

Initiates a sequence to capture a single frame/image, halting the video stream temporarily.

This method prompts the user to either select a local image or capture a new one using the system camera, similar to the behavior in `singleFrameMode` but without changing the mode.

Note: This method is intended for use cases where capturing a single, user-obtained image is necessary while the application is otherwise utilizing a live video stream.

Steps performed by `takePhoto`:

1. Stops the video stream and releases the camera, if it was in use.
2. Prompts the user to select an image from their gallery or disk, or to take a new image with the system camera. This behavior mirrors that of `singleFrameMode`.
3. Places the obtained image into the buffer, differing from `singleFrameMode` which would display the image in the view.
4. Attempts to resume the video stream after the image has been obtained.

```typescript
takePhoto(listener: (dceFrame: DCEFrame) => void): void;
```

**Parameter**

`listener`: A callback function that is invoked with a `DCEFrame` object containing the obtained image.

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
