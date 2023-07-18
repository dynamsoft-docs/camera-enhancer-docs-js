---
layout: default-layout
title: Interface CameraTestResponse - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the CameraTestResponse Interface of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: CameraTestResponse, CameraEnhancer, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: CameraTestResponse
permalink: /programming/javascript/api-reference/interface/CameraTestResponse.html
---

# CameraTestResponse

`interface` CameraTestResponse

* ok: `boolean`

  Specifies whether there is an available camera.

* message: `string`
    
  The response string.

The possible responses are

```json
{
    ok: false,
    message: "Insecure context."
}
```

```json
{
    ok: false,
    message: "No camera detected."
}
```

```json
{
    ok: false,
    message: "No permission to access camera."
}
```

```json
{
    ok: false,
    message: "Some problem occurred which prevented the device from being used."
}
```

```json
{
    ok: false,
    message: "A hardware error occurred."
}
```

```json
{
    ok: false,
    message: "User media support is disabled."
}
```

```json
{
    ok: true,
    message: " Successfully accessed the camera."
}
```
