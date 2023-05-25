---
layout: default-layout
title: Auxiliary APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK Auxiliary.
keywords: camera enhancer, auxiliary, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: Auxiliary
permalink: /programming/javascript/api-reference/auxiliary-v2.0.3.html
---

# Auxiliary APIs

| API Name | Description |
|---|---|
| [getVersion()](auxiliary.md#getversion) | Returns the version of the library. |
| [detectEnvironment()](auxiliary.md#detectenvironment) | Returns a report on the current running environments. |

## getVersion

Returns the version of the library.

```typescript
static getVersion(): string
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
static detectEnvironment(): Promise<any>
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
