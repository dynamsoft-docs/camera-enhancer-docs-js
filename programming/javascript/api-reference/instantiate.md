---
layout: default-layout
title: Initialization - Dynamsoft Camera Enhancer JavaScript API
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK Initialization.
keywords: camera enhancer, initialization, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: Initialization
permalink: /programming/javascript/api-reference/instantiate.html
---

# Class CameraEnhancer

## Create and Destroy Instances

| API Name                                                         | Description                                                                                  |
| ---------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `static` [createInstance()](#createinstance)                     | Creates a `CameraEnhancer` instance.                                                         |
| [dispose()](#dispose)                                            | Releases all resources used by the `CameraEnhancer` instance.                                |
| [disposed](#disposed)                                            | A readonly boolean value indicating whether the `CameraEnhancer` instance has been disposed. |
| `static` [onWarning](#onwarning)                                 | A callback which is triggered when the running environment is not ideal.                     |
| `static` [isCameraInspectionSkipped](#iscamerainspectionskipped) | Sets or returns whether to skip camera inspection when creating a `CameraEnhancer` instance. |

## createInstance

Creates a `CameraEnhancer` instance.

```typescript
static createInstance: (cameraView?: CameraView) => Promise<CameraEnhancer>;
```

**Parameters**

* cameraView: Specifies a `CameraView` instance to be used by the `CameraEnhancer` instance.

**Return value**

A promise resolving to the created `CameraEnhancer` object.

**Code Snippet**

```javascript
(async () => {
    let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
    let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(cameraView);
})();
```

## dispose

Releases all resources used by the `CameraEnhancer` instance. After that, the instance will be left with only the property `disposed` (the value is `true`).

```typescript
dispose: () => void;
```

**Parameters**

None.

**Return value**

None.

**Code Snippet**

```javascript
let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
// Use the object to perform some tasks
//...
enhancer.dispose();
```

## disposed

A readonly boolean value indicating whether the `CameraEnhancer` instance has been disposed.

```typescript
readonly disposed: boolean; 
```

**Code Snippet**

```javascript
let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
//...
let flag = enhancer.disposed;
```

## onWarning

A callback which is triggered when the running environment is not ideal. In this version, it may get triggered in two scenarios:

1. If the page is opened from the disk;
2. The page is hosted in a HTTP site without SSL;

The following two warnings are returned respectively:

```json
{
    id: 1,
    message: "The page is opened over file:// and Dynamsoft Camera Enhancer may not work properly. Please open the page via https://."
}
```

```json
{
    id: 2,
    message: "Dynamsoft Camera Enhancer may not work properly in a non-secure context. Please open the page via https://."
}
```

**Code Snippet**

```javascript
Dynamsoft.DCE.CameraEnhancer.onWarning = warning => console.log(warning);
```

**See Also**

[Warning](interface/warning.md)

## isCameraInspectionSkipped

Sets or returns whether to skip camera inspection when creating a `CameraEnhancer` instance. If skipped, the instantiation is done faster. Note that if a previously used camera is already available in the [localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage), the inspection is skipped automatically. Read more on [ifSaveLastUsedCamera](camera-control.md#ifsavelastusedcamera).

```typescript
ifSkipCameraInspection: boolean;
```