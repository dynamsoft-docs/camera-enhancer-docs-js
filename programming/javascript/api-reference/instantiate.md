---
layout: default-layout
title: Instantiation - Dynamsoft Camera Enhancer JavaScript API
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK Instantiation.
keywords: camera enhancer, Instantiation, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: Instantiation
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

## createInstance

Creates a `CameraEnhancer` instance.

```typescript
static createInstance(cameraView?: CameraView): Promise<CameraEnhancer>;
```

**Parameters**

* `cameraView`(optional): Specifies a `CameraView` instance to be used by the `CameraEnhancer` instance.

**Return value**

A promise resolving to the created `CameraEnhancer` object.

**Code Snippet**

```javascript
(async () => {
    let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
    let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(cameraView);
})();
```

**See also**

[Dispose](#dispose)  
[CameraView](cameraview.md)

## dispose

Releases all resources used by the `CameraEnhancer` instance. After that, the instance will be left with only the property `disposed` (the value is `true`).

```typescript
dispose(): void;
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

**See also**

[Disposed](#disposed)

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

**See also**

[Dispose](#dispose)

## onWarning

A callback which is triggered when the running environment is not ideal.

```typescript
static onWarning: (warning: Warning) => {};
```

In this version, it may get triggered in two scenarios:

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

**See also**

[Warning]([interface/warning.md](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/warning.html))