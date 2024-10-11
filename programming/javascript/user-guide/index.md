---
layout: default-layout
title: User Guide - Dynamsoft Camera Enhancer for JavaScript
description: This is the user guide of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: user guide, javascript, js
breadcrumbText: User Guide
noTitleIndex: true
needGenerateH3Content: true
needAutoGenerateSidebar: true
---

# Dynamsoft Camera Enhancer for Your Website

Dynamsoft Camera Enhancer allows your website to easily control the camera in the browser on desktop or mobile devices.

With the SDK integrated, your users can open your website in a browser, access their cameras to stream live video and acquire real-time frames for further processing. The SDK also supports simple shape drawing, allowing information to be presented directly on the video stream or over a static image for integrated user interaction.

In this guide, you will learn step by step on how to integrate the Dynamsoft Camera Enhancer SDK into your website.

- [Dynamsoft Camera Enhancer for Your Website](#dynamsoft-camera-enhancer-for-your-website)
  - [Adding the SDK](#adding-the-sdk)
    - [Use a CDN](#use-a-cdn)
    - [Host the SDK yourself](#host-the-sdk-yourself)
  - [Using the SDK](#using-the-sdk)
    - [Stream live video](#stream-live-video)
    - [Capture image frames](#capture-image-frames)
    - [Use ImageEditorView](#use-imageeditorview)
    - [Customize the UI](#customize-the-ui)
  - [Hosting the SDK](#hosting-the-sdk)
    - [Step One: Deploy the dist folder](#step-one-deploy-the-dist-folder)
    - [Step Two: Configure the Server](#step-two-configure-the-server)
    - [Step Three: Add the SDK from the server](#step-three-add-the-sdk-from-the-server)
  - [FAQ](#faq)
    - [Can I open the web page directly from the hard drive?](#can-i-open-the-web-page-directly-from-the-hard-drive)
    - [Why can't I use my camera?](#why-cant-i-use-my-camera)
  - [API Documentation](#api-documentation)
  - [System Requirements](#system-requirements)
  - [Release Notes](#release-notes)
  - [Next Steps](#next-steps)

## Adding the SDK

To use the SDK, we first add the following packages:

1. `dynamsoft-camera-enhancer`: Required, it provides the camera related functionalities used in this guide.
2. `dynamsoft-core`: Required, it includes basic classes, interfaces, and enumerations that are shared between all Dynamsoft SDKs.
3. `dynamsoft-license`: Optional, if you wish to utilize advanced features such as auto-zoom, enhanced focus, and tap-to-focus, you will need it.

### Use a CDN

The simplest way to add the SDK is to use a CDN such as [jsDelivr](https://jsdelivr.com/) or [UNPKG](https://unpkg.com/).

- jsDelivr

  ```html
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-core@3.4.20/dist/core.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-license@3.4.21/dist/license.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@4.1.0/dist/dce.js"></script>
  ```

- UNPKG  

  ```html
  <script src="https://unpkg.com/dynamsoft-core@3.4.20/dist/core.js"></script>
  <script src="https://unpkg.com/dynamsoft-license@3.4.21/dist/license.js"></script>
  <script src="https://unpkg.com/dynamsoft-camera-enhancer@4.1.0/dist/dce.js"></script>
  ```

<!-- > In some rare cases, you might not be able to access the CDN. If this happens, you can use
>- [https://download2.dynamsoft.com/packages/dynamsoft-core@3.4.20/dist/core.js](https://download2.dynamsoft.com/packages/dynamsoft-core@3.2.10/dist/core.js)
>- [https://download2.dynamsoft.com/packages/dynamsoft-license@3.4.21/dist/license.js](https://download2.dynamsoft.com/packages/dynamsoft-license@3.2.10/dist/license.js)
>- [https://download2.dynamsoft.com/packages/dynamsoft-camera-enhancer@4.1.0/dist/dce.js](https://download2.dynamsoft.com/packages/dynamsoft-camera-enhancer@4.0.2/dist/dce.js) -->

### Host the SDK yourself

Besides using the CDN, you can also download the SDK and host it locally.

The following shows a few ways to download the SDK.

- yarn

  ```cmd
  yarn add dynamsoft-camera-enhancer
  ```

- npm

  ```cmd
  npm install dynamsoft-camera-enhancer --save
  ```

> Note: Upon installation of `dynamsoft-camera-enhancer`, a compatible versions of `dynamsoft-core` will be automatically installed if not installed already.

Depending on how you downloaded the SDK and where you put it. You can typically add it like this:

```html
<script src="./node_modules/dynamsoft-core/dist/core.js"></script>
<script src="./node_modules/dynamsoft-camera-enhancer/dist/dce.js"></script>
```

Read more on [how to host the SDK](#hosting-the-sdk).

## Using the SDK

### Stream live video

We can create a `CameraEnhancer` instance to open and show the video stream on the page. The following code snippet demonstrates the complete process:

1. Create a `CameraView` instance. In our case, it's named `cameraView`;
2. Pass `cameraView` to the method `createInstance()` to create a `CameraEnhancer` instance. This way, `cameraView` is bound to the created object `cameraEnhancer`;
3. Show the UI element of `cameraView` by appending it to an existing element in the DOM;
4. Open the video stream which will show up in the UI Element.

```html
<!-- Define an element to hold the UI element -->
<div id="enhancerUIContainer" style="width:1280px;height:720px;"></div>
<script>
  (async () => {
      // Initializes the license for using the SDK in the application.
      Dynamsoft.License.LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");
      // A default UI will be used if no parameter is passed to 'CameraView.createInstance()'.
      let cameraView = await Dynamsoft.DCE.CameraView.createInstance();
       // Create 'CameraEnhancer' instance and pass 'cameraView' to it.
      let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(cameraView);
      // Get 'CameraView' instance's UI and append it to DOM.
      document.querySelector("#enhancerUIContainer").append(cameraView.getUIElement());
      // Open the camera and start streaming the video on the page.
      await cameraEnhancer.open();
  })();
</script>
```

### Capture image frames

There are two ways to capture image frames with Dynamsoft Camera Enhancer.

- Capture a single latest frame

  This is done with the method [fetchImage()](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/api-reference/acquisition.html#fetchimage) as shown in the following code snippet:

  ```javascript
  let img = cameraEnhancer.fetchImage();
  document.body.appendChild(img.toCanvas());
  ```

- Start a capture loop that captures multiple frames at a steady interval into a buffer and then read frames from the buffer. The following code snippet shows how it works:

  ```javascript
  // Capture an image frame every 2 seconds and subsequently append it to the buffer.
  cameraEnhancer.setImageFetchInterval(2000);
  // The event "frameAddedToBuffer" is triggered whenever a new frame is added to the buffer.
  cameraEnhancer.on("frameAddedToBuffer", () => {
    let img = cameraEnhancer.getImage();
    console.log(img);
  });
  // Start the built-in fetching loop.
  cameraEnhancer.startFetching();
  ```
  
### Use ImageEditorView

The other view class ImageEditorView is designed to show a single image. The following code snippet shows a single frame in an `ImageEditorView` instance and draws a rectangle on the image:

```html
<div id="imageEditorContainer" style="width:1280px;height:720px;"></div>
```

```javascript
// The default UI will be used if no parameter is provided to 'ImageEditorView.createInstance()'.
let editorView = await Dynamsoft.DCE.ImageEditorView.createInstance();
// Retrieve the UI of the 'editorView' instance and append it to the DOM.
document.querySelector("#imageEditorContainer").append(editorView.getUIElement());
// When the video is already playing, capture an image and draw it on the ImageEditorView.
let img = cameraEnhancer.fetchImage();
editorView.setOriginalImage(img);
// Draw a rectangle on the image.
let drawingLayer = editorView.createDrawingLayer();
let rect = new Dynamsoft.DCE.RectDrawingItem(
  {
    x: 100,
    y: 100,
    width: 1070,
    height: 520
  });
drawingLayer.addDrawingItems([rect]);
```

Once the rectangle appears on the image, you can click to select it and adjust its position, size, etc.

Read more about [How to draw shapes](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/user-guide/features/draw-shapes.html).

### Customize the UI

Dynamsoft Camera Enhancer (DCE) offers extensive customization options. If you only need to adjust the UI without delving into other features, this section is for you.

**Use the built-in UI**

DCE includes several pre-defined UIs in the `DCE-LIB-PACKAGE/dist/xxxx.ui.html` (or `node_modules/dynamsoft-camera-enhancer/dist/xxxx.ui.html`).

* `dce.ui.html`: The default UI used by CameraView.createInstance() for simple use cases.
* `dce.mobile-native.ui.html`: A mobile-inspired UI with auto flash, suitable for most websites. Activate it with `CameraView.createInstance('@engineResourcePath/dce.mobile-native.ui.html')`.

When `cameraEnhancer.open()` is called, the UI elements are dynamically bound to functions based on their class names, such as `dce-xxxx`.

**Modify the UI dynamically**

To customize the UI, call `view.getUIElement()` to access the HTMLElement containing all UI elements. Before `cameraEnhancer.open()`, you can modify the UI by editing CSS, adding/removing elements, or restructuring the HTML. This usually works without issues, though testing is recommended.

After `cameraEnhancer.open()`, UI adjustments are possible via JavaScript, but handle elements with `dce-` prefixed class names carefully, as they may be linked to specific logic.

**Define the UI in a separate HTML**

For less dynamic but more structured customization, create a copy of the desired `xxxx.ui.html`, modify it as needed, and store it in your project's `public` folder. Use this customized UI with `CameraView.createInstance('PATH-TO/xxxx.ui.html')`.

**Integrate HTML into Your Project**

Alternatively, `CameraView.createInstance()` accepts an `HTMLElement` directly. This allows you to build and manage the UI within your webpage. For example, set the UI using `CameraView.createInstance(document.getElementById('my-custom-ui'))`.

Let's see the following example.

**Practise: customize base on `dce.ui.html`**

Start by opening dce.ui.html in your editor to review its content. You can copy several elements from this file.

Next, create a new HTML page, beginning by embedding only the video:

```html
<div id="enhancerUIContainer" style="width:1280px;height:720px;background:#ddd;" >
  <div class="dce-video-container" style="width:100%;height:100%;"></div>
</div>
<script>
    (async () => {
      // Initializes the license for using the SDK in the application.
      Dynamsoft.License.LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");
      // Create 'CameraView' instance and pass the element "enhancerUIContainer" as its UI.
      let cameraView = await Dynamsoft.DCE.CameraView.createInstance(document.getElementById("enhancerUIContainer"));
      let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(cameraView);
      await cameraEnhancer.open();
    })();
</script>
```

> The video element will automatically be created and appended to the `dce-video-container` div.

Next, add the camera and resolution list. If the classes match the default ones (`dce-sel-camera` and `dce-sel-resolution`), the SDK will populate them and manage switching.

```html
<div id="enhancerUIContainer" style="position:relative;width:1280px;height:720px;background:#ddd;" >
  <div class="dce-video-container" style="width:100%;height:100%;"></div>
  <div style="position: absolute;left: 0;top: 0;">
    <select class="dce-sel-camera" style="display: block;"></select>
  </div>
</div>
```

```html
<div id="enhancerUIContainer" style="position:relative;width:1280px;height:720px;background:#ddd;" >
  <div class="dce-video-container" style="width:100%;height:100%;"></div>
  <div style="position:absolute;left:0;top:0;">
    <select class="dce-sel-camera" style="display:block;"></select>
    <select class="dce-sel-resolution" style="display:block;margin-top:5px;"></select>
  </div>
</div>
```

> By default, only 3 hard-coded resolutions (1920 x 1080, 1280 x 720, 640 x 480) are available. You can show a customized set of options by hardcoding them.

```html
<select class="dce-sel-resolution">
    <option class="dce-opt-gotResolution" value="got"></option>
    <option data-width="1920" data-height="1080">1920x1080</option>
    <option data-width="1280" data-height="720">1280x720</option>
    <option data-width="640" data-height="480">640x480</option>
</select>
```

> Ensure the selected resolution is supported by the camera. If not, the closest supported resolution will be used. The `dce-opt-gotResolution` class shows the **actual resolution**.

**End of the section: customize the UI**

This concludes the UI customization section. Whether using built-in UIs or custom HTML, the process is straightforward.

## Hosting the SDK

### Step One: Deploy the dist folder

Once you have downloaded the SDK, you can locate the "dist" directory and copy it to your project (usually as part of your website / web application). The following shows some of the files in this directory:

- `dce.js` // The main SDK file
- `dce.mjs` // For using the SDK as a module (`<script type="module">`)
- `dce.ui.html` // Defines the default cameraEnhancer UI

### Step Two: Configure the Server

- Enable HTTPS

  To use the SDK, you must access your website / web application via a secure HTTPS connection. This is due to browser security restrictions which only grant camera video streaming access to a [secure context](https://developer.mozilla.org/en-US/docs/Web/Security/Secure_Contexts).

  > For convenience, self-signed certificates can be used during development and testing. You can also use "http://localhost" which allows camera access without an SSL certificate.

### Step Three: Add the SDK from the server

Now that the SDK is hosted on your server, you can add it accordingly.

```html
<script src="https://www.yourwebsite.com/PATH-TO-THE-SDK/dynamsoft-camera-enhancer/dist/dce.js"></script>
```

## FAQ

### Can I open the web page directly from the hard drive?

Yes, for simple testing purposes, it's ok to open the file directly from the hard drive (`file://`). However, you might encounter some issues in doing so (cannot access camera, etc.). The recommendation is to deploy this page to your web server and run it over **HTTPS** or use "http://localhost" during development.

If you don't have a ready-to-use web server but have a package manager like *npm* or *yarn*, you can set up a simple HTTP server in minutes. Check out [`http-server` on npm](https://www.npmjs.com/package/http-server) or [`http-server` on yarn](https://yarnpkg.com/package/http-server).

### Why can't I use my camera?

If you open the web page as `http://` , the camera may not work and you see a warnings or an error in the browser console. This is usually because the API [getUserMedia](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia) requires HTTPS to access the camera.

To make sure your web application can access the camera, please configure your web server to support HTTPS. The following links may help.

- NGINX: [Configuring HTTPS servers](https://nginx.org/en/docs/http/configuring_https_servers.html)
- IIS: [Create a Self Signed Certificate in IIS](https://aboutssl.org/how-to-create-a-self-signed-certificate-in-iis/)
- Tomcat: [Setting Up SSL on Tomcat in 5 minutes](https://dzone.com/articles/setting-ssl-tomcat-5-minutes)
- Node.js: [npm tls](https://nodejs.org/docs/v0.4.1/api/tls.html)

## API Documentation

You can check out the detailed documentation about the APIs of the SDK at
[https://www.dynamsoft.com/camera-enhancer/docs/programming/javascript/api-reference/index.html](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/api-reference/index.html).

## System Requirements

DCE requires the following features to work:

* Secure context (HTTPS deployment)

  When deploying your application / website for production, make sure to serve it via a secure HTTPS connection. This is required for two reasons
  
  * Access to the camera video stream is only granted in a security context. Most browsers impose this restriction.
  > Some browsers like Chrome may grant the access for `http://127.0.0.1` and `http://localhost` or even for pages opened directly from the local disk (`file:///...`). This can be helpful for temporary development and test.
  
  * Dynamsoft License requires a secure context to work.

* `MediaDevices`/`getUserMedia`

  This API is only required for in-browser video streaming.

* `getSettings`

  This API inspects the video input which is a `MediaStreamTrack` object about its constrainable properties.

The following table is a list of supported browsers based on the above requirements:

  | Browser Name | Version |
  | :----------: | :-----: |
  |    Chrome    |  v59+   |
  |   Firefox    |  v68+   |
  |     Edge     |  v79+   |
  |    Safari    |  v11+   |

Apart from the browsers, the operating systems may impose some limitations of their own that could restrict the use of the SDK. Browser compatibility ultimately depends on whether the browser on that particular operating system supports the features listed above.

## Release Notes

Learn about what are included in each release at [https://www.dynamsoft.com/camera-enhancer/docs/programming/javascript/release-note/index.html](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/release-note/index.html).

## Next Steps

Now that you have got the SDK integrated, you can choose to move forward in the following directions

1. Check out the [official samples on Github](https://github.com/Dynamsoft/camera-enhancer-javascript-samples).
2. Learn about the available [APIs](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/api-reference/index.html).
3. Learn more about the [Shape Drawing Feature](https://www.dynamsoft.com/camera-enhancer/docs/web/programming/javascript/user-guide/features/draw-shapes.html).