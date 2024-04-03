---
layout: default-layout
title: CameraEnhancerModule APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the page of the APIs for the class CameraEnhancerModule of Dynamsoft Camera Enhancer JavaScript SDK.
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
