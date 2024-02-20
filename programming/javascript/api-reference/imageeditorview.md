---
layout: default-layout
title: ImageEditorView APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the page for Dynamsoft Camera Enhancer JavaScript SDK ImageEditorView APIs.
keywords: ImageEditorView, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: ImageEditorView
permalink: /programming/javascript/api-reference/imageeditorview.html
---

# ImageEditorView

| Name                                                            | Description                                                                                      |
| --------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| `static` [createInstance](#createInstance)                      | Initializes a new instance of the `ImageEditorView` class.                                       |
| [dispose](#dispose)                                             | Releases all resources used by the `ImageEditorView` instance.                                   |
| [disposed](#disposed)                                           | Returns whether the `ImageEditorView` instance has been disposed of.                             |
| [getUIElement](#getUIElement)                                   | Returns the `HTMLDivElement`, where the `ImageEditorView` UI is loaded.                          |
| [setUIElement](#setUIElement)                                   | Sets a specific `HTMLDivElement`, where the UI element for the `ImageEditorView` will be loaded. |
| [setOriginalImage](#setOriginalImage)                           | Sets the image to be drawn on the `ImageEditorView`.                                             |
| [getOriginalImage](#getOriginalImage)                           | Returns the current image drawn on the `ImageEditorView`.                                        |
| [createDrawingLayer](#createDrawingLayer)                       | Creates a new `DrawingLayer` object and returns it.                                              |
| [getDrawingLayer](#getDrawingLayer)                             | Retrieves a `DrawingLayer` object by its unique identifier (ID).                                 |
| [getAllDrawingLayers](#getAllDrawingLayers)                     | Returns an array of all `DrawingLayer` objects managed by this `DrawingLayerManager`.            |
| [clearUserDefinedDrawingLayers](#clearUserDefinedDrawingLayers) | Clears all user-defined `DrawingLayer` objects.                                                  |
| [deleteUserDefinedDrawingLayer](#deleteUserDefinedDrawingLayer) | Deletes a user-defined `DrawingLayer` object specified by its unique identifier (ID).            |
| [getSelectedDrawingItems](#getSelectedDrawingItems)             | Asynchronously returns an array of all selected DrawingItem instances across different layers.   |

## createInstance

Initializes a new instance of the `ImageEditorView` class.

```typescript
static createInstance(defaultUIElement?: HTMLDivElement | string): Promise<ImageEditorView>;
```

**Parameters**

`defaultUIElement`: [Optional] specifies an empty `HTMLDivElement`, where the `ImageEditorView` UI will be dynamically loaded. If the parameter is omitted, the method will generate the UI without putting it on the page.

**Return value**

A promise that resolves with the initialized `ImageEditorView` instance.

**Code Snippet**

```javascript
let imageEditorView = await Dynamsoft.DCE.ImageEditorView.createInstance();
```

or

```html
<div id="enhancerUIContainer" style="width:1280px;height:720px;background:#ddd;" >
</div>
<script>
    // Create 'ImageEditorView' instance and pass an element as its UI.
    let imageEditorView = await Dynamsoft.DCE.ImageEditorView.createInstance(document.getElementById("enhancerUIContainer"));
</script>
```

## dispose

Releases all resources used by the `ImageEditorView` instance.

```typescript
dispose(): void;
```

**Parameters**

None.

**Return value**

None.

**Code Snippet**

```javascript
let editorView = await Dynamsoft.DCE.ImageEditorView.createInstance();
//...
editorView.dispose();
```

## disposed

Returns whether the `ImageEditorView` instance has been disposed of.

```typescript
readonly disposed: boolean; 
```

**Return value**

Boolean indicating whether the `ImageEditorView` instance has been disposed of.

**Code Snippet**

```javascript
let editorView = await Dynamsoft.DCE.ImageEditorView.createInstance();
//...
let flag = editorView.disposed;
```

## getUIElement

Returns the `HTMLDivElement`, where the `ImageEditorView` UI is loaded.

```typescript
getUIElement(): HTMLElement; 
```

**Parameters**

None.

**Return value**

The `HTMLDivElement`, where the `ImageEditorView` UI is loaded.

**Code Snippet**

```javascript
const uiElement = imageEditorView.getUIElement();
```

## setUIElement

Sets a specific `HTMLDivElement`, where the UI element for the `ImageEditorView` instance will be loaded.

```typescript
setUIElement(UIElement: HTMLDivElement | string): Promise<void>;
```

**Parameters**

`UIElement`: the `HTMLDivElement`, where the UI element for the `ImageEditorView` instance will be loaded.

**Return value**

A promise that resolves once the new UI has been successfully loaded. It does not provide any value upon resolution.

**Code Snippet**

```javascript
<div id="enhancerUIContainer" style="width: 100vw; height:70vh"></div>
<script>
    (async () => {
        await imageEditorView.setUIElement(document.getElementById("enhancerUIContainer"));
    })();
</script>
```

## setOriginalImage

Sets the image to be drawn on the `ImageEditorView`. 

```typescript
setOriginalImage(image: DSImageData | HTMLCanvasElement | HTMLImageElement): void;
```

**Parameters**

`image`: the image to be drawn on the `ImageEditorView`. 

**Return value**

None.

**Code Snippet**

```javascript
let currentFrame = cameraEnhancer.fetchImage();
imageEditorView.setOriginalImage(currentFrame);
```

## getOriginalImage

Returns the current image drawn on the `ImageEditorView`.

```typescript
getOriginalImage(): DSImageData | HTMLCanvasElement | HTMLImageElement
```

**Parameters**

None.  

**Return value**

The current image drawn on the `ImageEditorView`. The returned type will match the format of the image originally set via `setOriginalImage()`.

**Code Snippet**

```javascript
let image = imageEditorView.getOriginalImage();
```

## createDrawingLayer

Creates a new `DrawingLayer` object and returns it.

```typescript
createDrawingLayer(): DrawingLayer;
```

**Parameters**

None.

**Return value**

The created `DrawingLayer` object.

**Code Snippet**

```javascript
const newDrawingLayer = imageEditorView.createDrawingLayer();
```

## getDrawingLayer

Retrieves a `DrawingLayer` object by its unique identifier (ID).

```typescript
getDrawingLayer(id: number): DrawingLayer | null;
```

**Parameters**

`id`: the unique identifier (ID) of the `DrawingLayer` object.

**Return value**

The `DrawingLayer` object specified by its unique identifier (ID) or `null`.

**Code Snippet**

```javascript
retrievedDrawingLayer = imageEditorView.getDrawingLayer(layerId);
```

## getAllDrawingLayers

Returns an array of all `DrawingLayer` objects managed by this `DrawingLayerManager`.

```typescript
getAllDrawingLayers(): Array<DrawingLayer>;
```

**Parameters**

None.

**Return value**

An array of all `DrawingLayer` objects.

**Code Snippet**

```javascript
DrawingLayers = imageEditorView.getAllDrawingLayers();
```

## clearUserDefinedDrawingLayers

Clears all user-defined `DrawingLayer` objects.

```typescript
clearUserDefinedDrawingLayers(): void;
```

**Parameters**

None.

**Return value**

None.

**Code Snippet**

```javascript
imageEditorView.clearUserDefinedDrawingLayers();
```

## deleteUserDefinedDrawingLayer

 Deletes a user-defined `DrawingLayer` object specified by its unique identifier (ID).

```typescript
deleteUserDefinedDrawingLayer(id: number): void;
```

**Parameters**

`id`: the unique identifier (ID) of the `DrawingLayer` object.

**Return value**

None.

**Code Snippet**

```javascript
imageEditorView.deleteUserDefinedDrawingLayer(DrawingLayerId);
```

## getSelectedDrawingItems

Asynchronously returns an array of all selected DrawingItem instances across different layers, supporting complex selection scenarios.

```typescript
getSelectedDrawingItems(): Array<DrawingItem> | null;
```

**Parameters**

None.

**Return value**

An array of `DrawingItem` objects or `null`.

**Code Snippet**

```javascript
let drawingItems = imageEditorView.getSelectedDrawingItems();
```
