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

The `CameraTestResponse` interface is designed to encapsulate the response from a camera test operation by the method `Dynamsoft.DCE.CameraEnhancer.testCameraAccess()`, providing a standardized format for assessing the outcome. 

```ts
export interface CameraTestResponse {
    /**
     * 
     */
    ok: boolean;
    /**
     * Provides a descriptive message about the outcome of the camera test.
     * - For a successful test (`ok: true`), this message might confirm the operational status or provide additional success-related information.
     * - For a failed test (`ok: false`), it typically contains details about the error or issue encountered during the test, which could be useful for troubleshooting or informing the user about the failure reason.
     */
    message: string;
}
```

## ok

Indicates the success or failure of the camera test.

- `true` signifies that the test was successful, meaning the camera is operational and ready to use.
- `false` implies that the test failed, indicating an issue with accessing or using the camera.

## message

Provides a descriptive message about the outcome of the camera test.

- For a successful test (`ok: true`), this message might confirm the operational status or provide additional success-related information.
- For a failed test (`ok: false`), it typically contains details about the error or issue encountered during the test, which could be useful for troubleshooting or informing the user about the failure reason.
