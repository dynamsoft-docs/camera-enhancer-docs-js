---
layout: default-layout
title: Auxiliary APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the page of the Auxiliary APIs of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: camera enhancer, auxiliary, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: Auxiliary
permalink: /programming/javascript/api-reference/auxiliary.html
---

# Class CameraEnhancer

## Auxiliary

| Name          | Description                                                           |
| ------------- | --------------------------------------------------------------------- |
| [on()](#on)   | Registers an event listener for specific camera-related events.       |
| [off()](#off) | Removes an event listener previously registered with the `on` method. |

**Type definition used on this page**:

```typescript
type EventName ="cameraOpen" | "cameraClose" | "cameraChange" | "resolutionChange" | "played" | "singleFrameAcquired" | "frameAddedToBuffer";
```

**Built-in Event Reference Table**

| Event Name          | Description                                                      |
| ------------------- | ---------------------------------------------------------------- |
| cameraOpen          | Triggered when the camera opens.                                 |
| cameraClose         | Triggered when the camera closes.                                |
| cameraChange        | Triggered when a different camera is used.                       |
| resolutionChange    | Triggered when the resolution changes.                           |
| played              | Triggered when the video starts playing/streaming.               |
| singleFrameAcquired | Triggered when an image is acquired under the single-frame mode. |
| frameAddedToBuffer  | Triggered each time a new frame is added to the buffer.          |

> NOTE:
>
> When the event "singleFrameAcquired" is triggered, the acquired image data will be returned as a reference, not a copy. Therefore, any changes to it will change the data source, and if another callback returns the same image data, the modifications will be synchronized.

## on

Registers an event listener for specific camera-related events. 

```typescript
on(eventName: EventName, listener: Function): void;
```

**Parameters**

`eventName`: the name of the event to listen for. Possible values include "cameraOpen", "cameraClose", "cameraChange", "resolutionChange", "played", "singleFrameAcquired", and "frameAddedToBuffer".

`listener`: the callback function to be invoked when the event occurs.

**Return value**

None.

**Code Snippet**

```javascript
let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
cameraEnhancer.on("cameraOpen", () => {
    console.log("Camera opened.");
});
cameraEnhancer.on("cameraClose", () => {
    console.log("Camera closed.");
});
cameraEnhancer.on("cameraChange", (deviceId, previousDeviceId) => {
    console.log("Camera changed.");
});
cameraEnhancer.on("resolutionChange", (resolution, previousResolution) => {
    console.log("Resolution changed.");
});
cameraEnhancer.on("played", () => {
    console.log("Video stream started.");
});
cameraEnhancer.on("singleFrameAcquired", dceFrame => {
    console.log("An image is acquired under the single-frame mode.");
});
cameraEnhancer.on("frameAddedToBuffer", () => {
    console.log("A new frame is added to the buffer.");
});
```

## off

Removes an event listener previously registered with the `on` method.

```typescript
off(eventName: EventName, listener: Function): void;
```

**Parameters**

`eventName`: the name of the event to listen for. Possible values include "cameraOpen", "cameraClose", "cameraChange", "resolutionChange", "played", "singleFrameAcquired", and "frameAddedToBuffer".

`listener`: the callback function to be invoked when the event occurs.

**Return value**

None.

**Code Snippet**

```javascript
let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
let cameraChanged = playCallBackInfo => {
    console.log(playCallBackInfo.deviceId);
    cameraEnhancer.off("cameraChange", cameraChanged);
}
cameraEnhancer.on("cameraChange", cameraChanged);
```

<!--
## offAll

Removes all event handlers from the specified event. If no event is specified, remove all event handlers.

```typescript
offAll(eventName?: EventName): void;
```

**Parameters**

`eventName`: specifies the event.

**Return value**

None.

**Code Snippet**

```javascript
cameraEnhancer.offAll("cameraChange");
```

## detectEnvironment

Returns a report (in JSON) on the current running environments.

```typescript
static detectEnvironment(): Promise<any>;
```

**Parameters**

None.

**Return value**

A JSON object about the running environment. For example

```json
{
    "wasm": true,
    "worker": true,
    "getUserMedia": true,
    "camera": true,
    "browser": "Chrome",
    "version": 90,
    "OS": "Windows"
}
```

**Code Snippet**

```javascript
await Dynamsoft.DCE.CameraEnhancer.detectEnvironment();
```

## setErrorListener

Sets the error listener to receive notifications should errors occur during image acquisition.

```typescript
setErrorListener(listener: ImageSourceErrorListener): void;
```

**Parameters**

`listener`: the callback function that is triggered when an error occurs during image acquisition.

**Code Snippet**

```javascript
cameraEnhancer.setErrorListener(
    {
        onErrorReceived: (errorCode, errorMessage) => {
            console.log(errorMessage);
        },
    }
);
```

-->