---
layout: default-layout
title: Auxiliary APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK Auxiliary.
keywords: camera enhancer, auxiliary, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: Auxiliary
permalink: /programming/javascript/api-reference/auxiliary.html
---

# Auxiliary

| API Name | Description |
|---|---|
| [on()](#on) | Attaches an event handler function for a built-in event. |
| [off()](#off) | Removes an event handler. |
| [offAll()](#offall) | Removes all event handlers from the specified event. If no event is specified, remove all event handlers. |
| [dispose()](#dispose) | Releases all resources used by the CameraEnhancer instance. |
| [disposed](#disposed) | A readonly boolean value indicating whether the CameraEnhancer instance has been disposed. |
| [getVersion()](#getversion) | Returns the version of the library. |
| [detectEnvironment()](#detectenvironment) | Returns a report on the current running environments. |

**Type definition used on this page**:

```typescript
type EventName = "cameraChange" | "cameraOpen" | "cameraClose" | "resolutionChange" | "played" | "singleFrameAcquired" | "frameAddedToBuffer";
```

**Built-in Event Reference Table**

| Event Name | Description |
| --| --|
| cameraChange | Triggered when a differnt camera is used. |
| cameraOpen | Triggered when the camera opens. |
| cameraClose | Triggered when the camera closes. |
| resolutionChange | Triggered when the resolution changes. |
| played | Triggered when the video starts playing/streaming. |
| singleFrameAcquired | Triggered when an image is acquired under the single-frame mode. |
| frameAddedToBuffer | Triggered each time a new frame is added to the buffer. |

## on

Attaches an event handler function for a built-in event.

```typescript
on(eventName: EventName, listener: Function): void;
```

**Parameters**

`eventName` : specifies the event.  
`listener` : specifies the handler function.

**Return value**

None.

**Code Snippet**

```javascript
let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
enhancer.on("cameraChange", playCallBackInfo => {
    console.log(playCallBackInfo.deviceId);
});
enhancer.on("cameraOpen", playCallBackInfo => {
    console.log(playCallBackInfo.deviceId);
});
enhancer.on("cameraClose", playCallBackInfo => {
    console.log(playCallBackInfo.deviceId);
});
enhancer.on("resolutionChange", playCallBackInfo => {
    console.log("width:" + playCallBackInfo.width);
    console.log("height:" + playCallBackInfo.height);
});
enhancer.on("played", playCallBackInfo => {
    console.log(playCallBackInfo.deviceId);
});
enhancer.on("singleFrameAcquired", dceFrame => {
    document.body.appendChild(dceFrame.toCanvas());
});
enhancer.on("frameAddedToBuffer", () => {
    let dceFrame = enhancer.getFrameFromBuffer();
    document.body.appendChild(dceFrame.toCanvas());
});
```

## off

Removes an event handler.

```typescript
off(eventName: EventName, listener: Function): void;
```

**Parameters**

`eventName` : specifies the event.  
`listener` : specifies the handler function.

**Return value**

None.

**Code Snippet**

```javascript
let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
let cameraChanged = playCallBackInfo => {
    console.log(playCallBackInfo.deviceId);
    enhancer.off("cameraChange", cameraChanged);
}
enhancer.on("cameraChange", cameraChanged);
```

## offAll

Removes all event handlers from the specified event. If no event is specified, remove all event handlers.

```typescript
offAll(eventName?: EventName): void;
```

**Parameters**

`eventName` : specifies the event.

**Return value**

None.

**Code Snippet**

```javascript
enhancer.offAll("cameraChange");
```

## dispose

Releases all resources used by the CameraEnhancer instance. After that, the instance will be left with only the property `disposed` (the value is `true`).

> The HTML elements used by the instance's UI element are only removed when `removeUIElement` is set to `true`. Otherwise, they are only hidden.

```typescript
dispose(removeUIElement?: boolean): void;
```

**Parameters**

`removeUIElement`: whether to hide or remove the HTML elements in the instance's UI element.

**Return value**

None.

**Code Snippet**

```javascript
let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
// Use the object to perform some tasks
enhancer.dispose();
```

## disposed

A readonly boolean value indicating whether the `CameraEnhancer` instance has been disposed.

> This property replaces the deprecated old property `isDisposed`.

```typescript
readonly disposed: boolean; 
```

**Code Snippet**

```javascript
let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
//...
let flag = enhancer.disposed;
```

## getVersion

Returns the version of the library.

```typescript
static getVersion(): string;
```

**Parameters**

None.

**Return value**

The version string of the library.

**Code Snippet**

```javascript
Dynamsoft.DCE.CameraEnhancer.getVersion();
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
