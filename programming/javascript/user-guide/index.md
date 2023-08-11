---
layout: default-layout
title: User Guide - Dynamsoft Camera Enhancer for JavaScript
description: This is the user guide of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: user guide, javascript, js
breadcrumbText: User Guide
noTitleIndex: true
needGenerateH3Content: true
needAutoGenerateSidebar: true
permalink: /programming/javascript/user-guide/index.html
---

# Dynamsoft Camera Enhancer for Your Website

Dynamsoft Camera Enhancer allows your website to easily control the camera in the browser on desktop or mobile devices.

With the SDK integrated, your users can open your website in a browser, access their cameras to stream live video and acquire real-time frames for further processing. The SDK also supports simple shape drawing, allowing information to be presented directly on the video stream or over a static image for integrated user interaction.

In this guide, you will learn step by step on how to integrate the Dynamsoft Camera Enhancer SDK into your website.

- [Dynamsoft Camera Enhancer for Your Website](#dynamsoft-camera-enhancer-for-your-website)
  - [Getting Started](#getting-started)
    - [Include the SDK](#include-the-sdk)
      - [Use a CDN](#use-a-cdn)
      - [Host the SDK yourself](#host-the-sdk-yourself)
    - [Use the SDK](#use-the-sdk)
      - [Show live video stream on the page](#show-live-video-stream-on-the-page)
      - [Capture image frames from the video stream](#capture-image-frames-from-the-video-stream)
      - [Use ImageEditorView and the Drawing Logic](#use-imageeditorview-and-the-drawing-logic)
      - [Customize the UI](#customize-the-ui)
  - [Hosting the SDK](#hosting-the-sdk)
    - [Step One: Deploy the dist folder](#step-one-deploy-the-dist-folder)
    - [Step Two: Configure the Server](#step-two-configure-the-server)
    - [Step Three: Include the SDK from the server](#step-three-include-the-sdk-from-the-server)
  - [FAQ](#faq)
    - [Can I open the web page directly from the hard drive?](#can-i-open-the-web-page-directly-from-the-hard-drive)
    - [Why can't I use my camera?](#why-cant-i-use-my-camera)
  - [API Documentation](#api-documentation)
  - [Release Notes](#release-notes)
  - [Next Steps](#next-steps)

## Getting Started

### Include the SDK

#### Use a CDN

The simplest way to include the SDK is to use either the [jsDelivr](https://jsdelivr.com/) or [UNPKG](https://unpkg.com/) CDN.

- jsDelivr

  ```html
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@4.0.0/dist/dce.js"></script>
  ```

- UNPKG  

  ```html
  <script src="https://unpkg.com/dynamsoft-camera-enhancer@4.0.0/dist/dce.js"></script>
  ```

> In some rare cases, you might not be able to access the CDN. If this happens, you can use [https://download2.dynamsoft.com/dce/dynamsoft-camera-enhancer-js/dynamsoft-camera-enhancer-js-4.0.0/dist/dce.js](https://download2.dynamsoft.com/dce/dynamsoft-camera-enhancer-js/dynamsoft-camera-enhancer-js-4.0.0/dist/dce.js)

#### Host the SDK yourself

Besides using the CDN, you can also download the SDK and host it locally.

The following shows a few ways to download the SDK.

- From the website

  [Download the JavaScript Package](https://www.dynamsoft.com/camera-enhancer/downloads/1000021-confirmation/?utm_source=guide)

- yarn

  ```cmd
  yarn add dynamsoft-camera-enhancer
  ```

- npm

  ```cmd
  npm install dynamsoft-camera-enhancer --save
  ```

Depending on how you downloaded the SDK and where you put it. You can typically include it like this:

```html
<script src="/dynamsoft-camera-enhancer-js-4.0.0/dist/dce.js"></script>
```

or

```html
<script src="/node_modules/dynamsoft-camera-enhancer/dist/dce.js"></script>
```

or

```typescript
import { CameraEnhancer } from 'dynamsoft-camera-enhancer';
```

Read more on [how to host the SDK](#hosting-the-sdk).

### Use the SDK

#### Show live video stream on the page

We can create a `CameraEnhancer` instance to open and show the video stream on the page. The following code snippet demonstrates the complete process:

1. Create a `CameraView` instance, `view` in our case;
2. Pass `view` to the method `createInstance()` for creating a `CameraEnhancer` instance. This way, `view` is bound to the created object `enhancer`;
3. Show the UI element of `view` by appending it to an existing element in the DOM;
4. Open the video stream which will show up in the UI Element.

Step 3 can be done anywhere after step 1.

```html
<!-- Define an element to hold the UI element -->
<div id="enhancerUIContainer" style="width:1280px;height:720px;"></div>
<script>
  (async () => {
      let view = await Dynamsoft.DCE.CameraView.createInstance();
      let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(view);
      // use the default UI element
      enhancerUIContainer.append(view.getUIElement());
      await enhancer.open();
  })();
</script>
```

#### Capture image frames from the video stream

There are two ways to capture image frames with Dynamsoft Camera Enhancer

1. Capture a single latest frame

  This is done with the method [fetchImage()](../api-reference/acquisition.md#fetchimage). The following is a code snippet that shows this

  ```javascript
  let img = enhancer.fetchImage();
  document.body.appendChild(img.toCanvas());
  ```

2. Start a capture loop that captures multiple frames at a steady interval into a buffer and then read frames from the buffer

  The following code snippet shows how it works

  ```javascript
  // Start the built-in fetching loop.
  let img = enhancer.startFetching();
  setInterval(function(){
    // Check the buffer every 2 seconds and check the latest buffered image.
    if(!enhancer.isBufferEmpty()){
        let img = enhancer.getImage();
        console.log(img.toCanvas());
    }
  }, 2000);
  ```
  
#### Use ImageEditorView and the Drawing Logic

The other view class ImageEditorView is designed to show a single image. The following code snippet shows a single frame in an `ImageEditorView` instance and draws a rectangle on the image:

```html
<div id="imageEditorContainer" style="width:1280px;height:720px;"></div>
```

```javascript
let editorView = await Dynamsoft.DCE.ImageEditorView.createInstance(document.getElementById('imageEditorContainer'));
// When the video is already playing, capture an image and draw it on the ImageEditorView
let img = enhancer.fetchImage();
editorView.setOriginalImage(img.toCanvas());
// Draw a rectangle on the image
let drawingLayer = editorView.createDrawingLayer();
let rect = new Dynamsoft.DCE.DrawingItem.RectDrawingItem(
  {
    x: 100,
    y: 100,
    width: 1070,
    height: 520
  });
drawingLayer.addDrawingItems([rect]);
```

Once the rectangle appears on the image, you can click to select it and adjust its position, size, etc.

#### Customize the UI

The built-in UI of the `CameraView` instance is defined in the file `dist/dce.ui.html` . There are a few ways to customize it:

- Modify the file `dist/dce.ui.html` directly.

  This option is only possible when you host this file on your own web server instead of using a CDN.

- Copy the file `dist/dce.ui.html` to your project, modify it and pass its path in the API `createInstance` to set it as the default UI.

```javascript
// To make sure the following line takes effect, put it before the API `open()` is called.
Dynamsoft.DCE.CameraView.createInstance("THE-URL-TO-THE-FILE");
```

- Build the UI element into your own web page and specify it with the API `setUIElement(HTMLElement)`.

  - Embed only the video

  ```html
  <div id="enhancerUIContainer" style="width:1280px;height:720px" >
    <div style="position:relative;width:100%;height:100%;min-width:100px;min-height:100px;background:#ddd;">
      <div class="dce-video-container" style="position:absolute;left:0;top:0;width:100%;height:100%;"></div>
    </div>
  </div>
  <script>
      (async () => {
        let view = await Dynamsoft.DCE.CameraView.createInstance();
        let enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(view);
        await view.setUIElement(document.getElementById("enhancerUIContainer"));
        await enhancer.open();
      })();
  </script>
  ```

  > The video element will be created and appended to the DIV element with the class `dce-video-container`, make sure the class name is the same. Besides, the CSS property `position` of the DIV element must be either `relative`, `absolute`, `fixed`, or `sticky`.

  - Add the camera list and resolution list. If the class names for these lists match the default ones,  `dce-sel-camera` and `dce-sel-resolution` , the SDK will automatically populate the lists and handle the camera/resolution switching.

  ```html
  <div style="position: absolute;left: 0;top: 0;">
    <select class="dce-sel-camera" style="display: block;"></select>
  </div>
  ```

  ```html
  <div style="position: absolute;left: 0;top: 0;">
    <select class="dce-sel-resolution" style="display: block;margin-top: 5px;">
    </select>
  </div>
  ```

  > By default, only 3 hard-coded resolutions (1920 x 1080, 1280 x 720, 640 x 480), are populated as options. You can show a customized set of options by hardcoding them.

  ```html
  <select class="dce-sel-resolution">
      <option class="dce-opt-gotResolution" value="got"></option>
      <option data-width="1920" data-height="1080">1920x1080</option>
      <option data-width="1280" data-height="720">1280x720</option>
      <option data-width="640" data-height="480">640x480</option>
  </select>
  ```

  > Generally, you need to provide a resolution that the camera supports. However, in case a camera does not support the specified resolution, it usually uses the cloest supported resolution. As a result, the selected resolution may not be the actual resolution. In this case, add an option with the class name `dce-opt-gotResolution` (as shown above) and the SDK will then use it to show the **actual resolution**.

## Hosting the SDK

### Step One: Deploy the dist folder

Once you have downloaded the SDK, you can locate the "dist" directory and copy it to your project (usually as part of your website / web application). The following shows some of the files in this directory:

- `dce.js` // The main SDK file
- `dce.mjs` // For using the SDK as a module (`<script type="module">`)
- `dce.ui.html` // Defines the default enhancer UI

### Step Two: Configure the Server

- Enable HTTPS

  To use the SDK, you must access your website / web application via a secure HTTPS connection. This is due to browser security restrictions which only grant camera video streaming access to a [secure context](https://developer.mozilla.org/en-US/docs/Web/Security/Secure_Contexts).

  > For convenience, self-signed certificates are allowed during development and testing. Or use "http://localhost".

### Step Three: Include the SDK from the server

Now that the SDK is hosted on your server, you can include it accordingly.

```html
<script src="https://www.yourwebsite.com/PATH-TO-THE-SDK/dynamsoft-camera-enhancer/dist/dce.js"></script>
```

## FAQ

### Can I open the web page directly from the hard drive?

Yes, for simple testing purposes, it's ok to open the file directly from the hard drive (`file://`). However, you might encounter some issues in doing so (like unable to access the camera, etc.). The recommendation is to deploy this page to your web server and run it over **HTTPS** or use "http://localhost" during development.

If you don't have a ready-to-use web server but have a package manager like *npm* or *yarn*, you can set up a simple HTTP server in minutes. Check out [`http-server` on npm](https://www.npmjs.com/package/http-server) or [yarn](https://yarnpkg.com/package/http-server).

### Why can't I use my camera?

If you open the web page as `http://` , the camera may not work and you see the following error in the browser console:

> [Deprecation] getUserMedia() no longer works on insecure origins. To use this feature, you should consider switching your application to a secure origin, such as HTTPS. See [https://goo.gl/rStTGz](https://goo.gl/rStTGz) for more details.

- In Safari 12 the equivalent error is:

> Trying to call getUserMedia from an insecure document.

You get this error because the API [getUserMedia](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia) requires HTTPS to access the camera.

To make sure your web application can access the camera, please configure your web server to support HTTPS. The following links may help.

- NGINX: [Configuring HTTPS servers](https://nginx.org/en/docs/http/configuring_https_servers.html)
- IIS: [Create a Self Signed Certificate in IIS](https://aboutssl.org/how-to-create-a-self-signed-certificate-in-iis/)
- Tomcat: [Setting Up SSL on Tomcat in 5 minutes](https://dzone.com/articles/setting-ssl-tomcat-5-minutes)
- Node.js: [npm tls](https://nodejs.org/docs/v0.4.1/api/tls.html)

## API Documentation

You can check out the detailed documentation about the APIs of the SDK at
[https://www.dynamsoft.com/camera-enhancer/docs/programming/javascript/api-reference/index.html](https://www.dynamsoft.com/camera-enhancer/docs/programming/javascript/api-reference/index.html).

## Release Notes

Learn about what are included in each release at [https://www.dynamsoft.com/camera-enhancer/docs/programming/javascript/release-note/index.html](https://www.dynamsoft.com/camera-enhancer/docs/programming/javascript/release-note/index.html).

## Next Steps

Now that you have got the SDK integrated, you can choose to move forward in the following directions

1. Learn more about the [Shape Drawing Feature](https://www.dynamsoft.com/camera-enhancer/docs/programming/javascript/user-guide/features/draw-shapes.html).
2. Check out the [official samples on Github](https://github.com/Dynamsoft/camera-enhancer-javascript-samples).
3. Learn about the available [APIs](https://www.dynamsoft.com/camera-enhancer/docs/programming/javascript/api-reference/index.html).
