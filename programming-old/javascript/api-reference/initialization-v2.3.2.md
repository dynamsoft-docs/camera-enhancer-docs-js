---
layout: default-layout
title: Initialization - Dynamsoft Camera Enhancer JavaScript API
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK Initialization v 2.3.2.
keywords: camera enhancer, initialization, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: Initialization
permalink: /programming/javascript/api-reference/initialization-v2.3.2.html
---

# Initialization APIs

| API Name | Description |
|---|---|
| [createInstance()](#createinstance) | Creates a `CameraEnhancer` instance. |
| [defaultUIElementURL](#defaultuielementurl) | Returns or sets the URL of the .html file that defines the default UI Element. |
| [getUIElement()](#getuielement) | Returns the HTML element that is used by the `CameraEnhancer` instance. |
| [setUIElement()](#setuielement) | Specifies an HTML element for the `CameraEnhancer` instance to use as its UI element. |

## createInstance

Creates a `CameraEnhancer` instance.

```typescript
static createInstance(): Promise<CameraEnhancer>;
```

**Parameters**

None.

**Return value**

A promise resolving to the created `CameraEnhancer` object.

**Code Snippet**

```javascript
let pEnhancer = null;
(async () => {
    let cameraEnhancer = await (pEnhancer = pEnhancer || Dynamsoft.DCE.CameraEnhancer.createInstance());
})();
```

## defaultUIElementURL

Returns or sets the URL of the *.html* file that defines the default UI Element. The URL can only be set before the API [createInstance](#createinstance) is called.

```typescript
static defaultUIElementURL: string;
```

**Code Snippet**

```javascript
Dynamsoft.DCE.CameraEnhancer.defaultUIElementURL = "https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@2.3.2/dist/dce.ui.html";
let pEnhancer = null;
(async () => {
    let cameraEnhancer = await (pEnhancer = pEnhancer || Dynamsoft.DCE.CameraEnhancer.createInstance());
    await cameraEnhancer.open();
})();
```

## getUIElement

Returns the HTML element that is used by the [CameraEnhancer](#CameraEnhancer) instance.

```typescript
getUIElement(): HTMLElement;
```

**Parameters**

None.

**Return value**

The HTML element used as the UI by the [CameraEnhancer](#CameraEnhancer) instance.

**Code Snippet**

```html
<!-- Define an element to hold the UI element -->
<div id="enhancerUIContainer"></div>
<script>
    let pEnhancer = null;
    (async () => {
        let cameraEnhancer = await (pEnhancer = pEnhancer || Dynamsoft.DCE.CameraEnhancer.createInstance());
        await cameraEnhancer.open();
        document.getElementById("enhancerUIContainer").appendChild(cameraEnhancer.getUIElement());
    })();
</script>
```

## setUIElement

Specifies an HTML element for the [CameraEnhancer](#CameraEnhancer) instance to use as its UI. The structure inside the element determines the appearance of the UI.

```typescript
setUIElement(elementOrURL: HTMLElement | string): Promise<void>;
```

**Parameters**

`elementOrURL` : specifies an existing element on the page or the URL of an HTML file which contains an element.

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```html
<!-- Define an element to hold the video input -->
<div class="dce-video-container" style="position:absolute;left:0;top:0;width:100%;height:100%;"></div>
<script>
    let pEnhancer = null;
    (async () => {
        let cameraEnhancer = await (pEnhancer = pEnhancer || Dynamsoft.DCE.CameraEnhancer.createInstance());
        await cameraEnhancer.setUIElement(document.getElementsByClassName("dce-video-container")[0]);
        await cameraEnhancer.open();
    })();
</script>
```

```html
<!-- Use a UI element defined in a HTML file. -->
<script>
    let pEnhancer = null;
    (async () => {
        let cameraEnhancer = await (pEnhancer = pEnhancer || Dynamsoft.DCE.CameraEnhancer.createInstance());
        // The following line is not needed if you just want to use the official UI element.
        // Only use it when you want to specify a different HTML page that contains a different UI definition.
        await cameraEnhancer.setUIElement("https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@2.3.2/dist/dce.ui.html");
        // Note that because the element is not on the current page, you need to pass "true" when calling open() in order to show it.
        await cameraEnhancer.open(true);
    })();
</script>
```
