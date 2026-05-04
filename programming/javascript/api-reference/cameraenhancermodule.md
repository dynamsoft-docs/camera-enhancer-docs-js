---
layout: default-layout
title: CameraEnhancerModule APIs - Dynamsoft Camera Enhancer JavaScript API
description: "Learn what the does in Dynamsoft Camera Enhancer JavaScript API, including its purpose, key data, and how it supports capture workflows for modern web."
keywords: camera enhancer, camera-enhancer module, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: CameraEnhancerModule
permalink: /programming/javascript/api-reference/cameraenhancermodule.html
---

# Class CameraEnhancerModule

The `CameraEnhancerModule` class defines common functionality in the `CameraEnhancer` module.

| Name                            | Description                                       |
| ------------------------------------ | ------------------------------------------------- |
| `static` [getVersion()](#getversion) | Returns the version of the CameraEnhancer module. |

### getVersion

Returns the version of the CameraEnhancer module.

```typescript
static getVersion(): string;
```

**Parameters**

None.

**Code snippet**

```javascript
const version = Dynamsoft.DCE.CameraEnhancerModule.getVersion();
console.log(version);
```
