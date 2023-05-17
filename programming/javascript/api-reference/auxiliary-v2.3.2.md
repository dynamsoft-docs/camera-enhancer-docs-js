---
layout: default-layout
title: Auxiliary APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK Auxiliary.
keywords: camera enhancer, auxiliary, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: Auxiliary
permalink: /programming/javascript/api-reference/auxiliary-v2.3.2.html
---

# Auxiliary APIs

| API Name | Description |
|---|---|
| [on()](#on) | Attach an event handler function for a built-in event. |
| [off()](#off) | Remove an event handler. |
| [dispose()](#dispose) | Releases all resources used by the CameraEnhancer instance. |
| [getVersion()](#getversion) | Returns the version of the library. |
| [detectEnvironment()](#detectenvironment) | Returns a report on the current running environments. |

## on

Attach an event handler function for a built-in event.

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

Remove an event handler.

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

## dispose

Releases all resources used by the CameraEnhancer instance.

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
Dynamsoft.DCE.CameraEnhancer.getVersion(); // 'JS 1.0.0.20210628'
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
