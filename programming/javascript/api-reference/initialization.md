---
layout: default-layout
title: Initialization - Dynamsoft Camera Enhancer JavaScript API
description: This page shows the Initialization of Dynamsoft Camera Enhancer JavaScript SDK Initialization.
keywords: camera enhancer, initialization, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: Initialization
permalink: /programming/javascript/api-reference/initialization.html
---

# Initialization APIs

| API Name | Description |
|---|---|
| [createInstance()](#createinstance) | Creates a `CameraEnhancer` instance. |
| [defaultUIElementURL](#defaultuielementurl) | Returns or sets the URL of the .html file that defines the default UI Element. |
| [getUIElement()](#getuielement) | Returns the HTML element that is used by the `CameraEnhancer` instance. |
| [setUIElement()](#setuielement) | Specifies an HTML element for the `CameraEnhancer` instance to use as its UI element. |
| [onWarning](#onwarning) | A callback which is triggered when the running environment is not ideal. |
| [testCameraAccess](#testcameraaccess) | Test whether there is an available camera. |

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
(async () => {
    let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
})();
```

## defaultUIElementURL

Returns or sets the URL of the *.html* file that defines the default UI Element.

```typescript
static defaultUIElementURL: string;
```

> NOTE: if `defaultUIElementURL` is not set before `open()` , it will not take effect and the preset one, which is "dce.ui.html" will be used. If you want to use a different UI element, set `defaultUIElementURL` beforehand like this:
>
> ```javascript
> Dynamsoft.DCE.CameraEnhancer.defaultUIElementURL = "URL-TO-NEW-UIELEMENT"; 
> await cameraEnhancer.open(true); 
> ```
>
> Also note that the SDK comes with 3 default UI definitions which takes effect automatically (no need to change `defaultUIElementURL` ):
>
> | Definition Name | Notes |
> | ---             | ----- |
> | dce.ui.html     | Used by default if the CameraEnhancer instance is used on its own. |
> | dbr.ui.html     | Used by default if the CameraEnhancer instance is used as an image source for Dynamsoft Barcode Reader. |
> | dlr.ui.html     | Used by default if the CameraEnhancer instance is used as an image source for Dynamsoft Label Recognizer. |

**Code Snippet**

```javascript
// The following line is redundant and is for demonstration purposes only.
Dynamsoft.DCE.CameraEnhancer.defaultUIElementURL = "https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer/dist/dce.ui.html";
(async () => {
    let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
    await enhancer.open(true);
})();
```

## getUIElement

Returns the HTML element that is used by the [CameraEnhancer](#CameraEnhancer) instance.

> In 2.3.2 or earlier, you could call getUIElement() right after creating an instance of CameraEnhancer and it would return the default HTML element. In 3.0.0 or later, you should call getUIElement() after calling setUIElement() or calling open(). Otherwise, it will return undefined.

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
    (async () => {
        let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
        await enhancer.open();
        document.getElementById("enhancerUIContainer").appendChild(enhancer.getUIElement());
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
<!-- The video element will be created and appended to the DIV element with the class 'dce-video-container' , make sure the class name is the same.
Besides, the CSS property 'position' of the DIV element must be either 'relative', 'absolute', 'fixed', or 'sticky'. -->
<div class="dce-video-container" style="position:relative;width:100%;height:500px;"></div>
<script>
    (async () => {
        let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
        await enhancer.setUIElement(document.getElementsByClassName("dce-video-container")[0]);
        await enhancer.open();
    })();
</script>
```

```html
<!-- Use a UI element defined in a HTML file. -->
<script>
    (async () => {
        let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
        // The following line is not needed if you just want to use the official UI element for CameraEnhancer.
        // Only use it when you want to specify a different HTML page that contains a different UI definition.
        await enhancer.setUIElement("https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer/dist/dce.ui.html");
        // Note that because the element is not on the current page, you need to pass "true" when calling open() in order to show it.
        await enhancer.open(true);
    })();
</script>
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

**See also**

[Warning](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/warning.html)

## testCameraAccess

Test whether there is an available camera.

```typescript
static testCameraAccess(): Promise<{ ok: boolean, message: string }>;
```

**Parameters**

None.

**Return value**

A promise resolving to an object with properties `ok` and `message`.

`ok`: Indicates whether the camera access test was successful (true) or not (false).
`message`: A string type message to provide additional information or details about the camera access test.

**Code Snippet**

```javascript
const testResponse = await Dynamsoft.DCE.CameraEnhancer.testCameraAccess();
if (testResponse.ok) {
    console.log(testResponse.message);
}
```