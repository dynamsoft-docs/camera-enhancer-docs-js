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

# CameraEnhancer - Create and Destroy Instances

| Name                                         | Description                                                         |
| -------------------------------------------- | ------------------------------------------------------------------- |
| `static` [createInstance()](#createinstance) | Initializes a new instance of the `CameraEnhancer` class.           |
| [dispose()](#dispose)                        | Releases all resources used by the `CameraEnhancer` instance.       |
| [disposed](#disposed)                        | Returns whether the `CameraEnhancer` instance has been disposed of. |

## createInstance

Initializes a new instance of the `CameraEnhancer` class. 

```typescript
static createInstance(cameraView?: CameraView): Promise<CameraEnhancer>;
```

**Parameters**

`cameraView`: [Optional] specifies a `CameraView` instance to be used by the `CameraEnhancer` instance.

**Return value**

A promise that resolves with the initialized `CameraEnhancer` instance.

**Code Snippet**

```javascript
(async () => {
    let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
    let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(cameraView);
})();
```

**See also**

[dispose](#dispose)

[CameraView](cameraview.md)

## dispose

Releases all resources used by the `CameraEnhancer` instance. Subsequently, the instance retains only the `disposed` property, set to true.

```typescript
dispose(): void;
```

**Parameters**

None.

**Return value**

None.

**Code Snippet**

```javascript
let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
// Use the object to perform some tasks
//...
cameraEnhancer.dispose();
```

**See also**

[disposed](#disposed)

## disposed

Returns whether the `CameraEnhancer` instance has been disposed of.

```typescript
readonly disposed: boolean; 
```

**Return value**

Boolean indicating whether the `CameraEnhancer` instance has been disposed of.

**Code Snippet**

```javascript
let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
//...
let flag = cameraEnhancer.disposed;
```

**See also**

[dispose](#dispose)

## onWarning

Event triggered when the running environment is not ideal. 

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

[Warning](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/warning.html)