---
layout: default-layout
title: Features - Draw Shapes - Dynamsoft Camera Enhancer JavaSCript User Guide
description: This page talks about how to use DCE JS to draw shapes.
keywords: user guide, javascript, js, draw shapes.
noTitleIndex: true
needGenerateH3Content: true
needAutoGenerateSidebar: true
permalink: /programming/javascript/user-guide/features/draw-shapes-v3.3.5.html
---

# Draw Shapes with DCE JS

In version 3.0.0 of DCE-JS, we introduced multiple APIs for drawing basic shapes on the built-in UI. This article will dive into how it works.

We will start with the following code which defines a page that has a CameraEnhancer instance embeded:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>DCEJS - Draw Shapes</title>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer/dist/dce.js"></script>
</head>
<body style="width:80vw; height:600px; margin: 0 auto">
    <br />
    <button id="drawShapes">Click to Draw Shapes</button><br /><br />
    <div id="enhancerUIContainer" style="width:100%; height:100%;"></div>
    <script>
        let enhancer = null;
        document.getElementById('drawShapes').onclick = drawShapes;
        (async () => {
            enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
            await enhancer.setUIElement(Dynamsoft.DCE.CameraEnhancer.defaultUIElementURL);
            document.getElementById("enhancerUIContainer").appendChild(enhancer.getUIElement());
            await enhancer.open();
        })();
        function drawShapes(){}
    </script>
</body>
</html>
```

## Add a DrawingLayer

All shapes are drawn on specific [`DrawingLayer`](../../api-reference/drawinglayer.md)s. The first step in drawing a shape is to create a **DrawingLayer**.

```javascript
function drawShapes(){
  let drawingLayer = enhancer.createDrawingLayer();
}
```

## Define DrawingItems

An `DrawingItem` is the basic shape that can be drawn. The SDK classify **DrawingItems** in different types: [`DT_Rect`](../../api-reference/drawingitem.md#dtrect), [`DT_Arc`](../../api-reference/drawingitem.md#dtarc), [`DT_Line`](../../api-reference/drawingitem.md#dtline), [`DT_Polygon`](../../api-reference/drawingitem.md#dtpolygon), [`DT_Text`](../../api-reference/drawingitem.md#dttext), and [`DT_Image`](../../api-reference/drawingitem.md#dtimage). The SDK also allow multiple items to be joined together and form the type called [`DT_Group`](../../api-reference/drawingitem.md#dtgroup).

The following code shows how to define these types of **DrawingItems**:

```javascript
let rect = new Dynamsoft.DCE.DrawingItem.DT_Rect(50, 50, 300, 300);
let arc = new Dynamsoft.DCE.DrawingItem.DT_Arc(840, 150, 100, 0, 360);
let line = new Dynamsoft.DCE.DrawingItem.DT_Line({x: 600, y: 600}, {x: 1050, y: 400});
let text = new Dynamsoft.DCE.DrawingItem.DT_Text("TESTING...", 360, 360);
let image = new Dynamsoft.DCE.DrawingItem.DT_Image(document.getElementById('testIMG'), 150, 600);
let polygon = new Dynamsoft.DCE.DrawingItem.DT_Polygon([{x: 640, y: 100}, {x: 500, y: 300}, {x: 780, y: 300}, {x: 690, y: 100}]);
```

Alternatively, the code might be like this

```javascript
import { DrawingItem } from "dynamsoft-camera-enhancer";
let arc = new DrawingItem.DT_Arc(840, 150, 100, 0, 360);
let line = new DrawingItem.DT_Line({x: 600, y: 600}, {x: 1050, y: 400});
let text = new DrawingItem.DT_Text("TESTING...", 360, 360);
let image = new DrawingItem.DT_Image(document.getElementById('testIMG'), 150, 600);
let polygon = new DrawingItem.DT_Polygon([{x: 640, y: 100}, {x: 500, y: 300}, {x: 780, y: 300}, {x: 690, y: 100}]);
```

> NOTE:
>
> `document.getElementById('testIMG')` is an image on the page defined in an `HTMLImageElement`.

## Draw these DrawingItems

After **DrawingItems** have been defined, simply call `addDrawingItems()` to draw them on the **DrawingLayer** we created earlier:

```javascript
function drawShapes(){
  let drawingLayer = enhancer.createDrawingLayer();
  let rect = new Dynamsoft.DCE.DrawingItem.DT_Rect(50, 50, 300, 300);
  let arc = new Dynamsoft.DCE.DrawingItem.DT_Arc(840, 150, 100, 0, 360);
  let line = new Dynamsoft.DCE.DrawingItem.DT_Line({x: 600, y: 600}, {x: 1050, y: 400});
  let text = new Dynamsoft.DCE.DrawingItem.DT_Text("TESTING...", 360, 360);
  let image = new Dynamsoft.DCE.DrawingItem.DT_Image(document.getElementById('testIMG'), 150, 600);
  let polygon = new Dynamsoft.DCE.DrawingItem.DT_Polygon([{x: 640, y: 100}, {x: 500, y: 300}, {x: 780, y: 300}, {x: 690, y: 100}]);
  drawingLayer.addDrawingItems([rect, arc, line, text, image, polygon]);
}
```

## Define the DrawingStyle

All new **DrawingLayer** objects come with the same predefined style definition

```javascript
{
  fillStyle: "rgba(245, 236, 73, 0.3)",
  fontFamily: "sans-serif",
  fontSize: 10,
  id: 4,
  lineWidth: 2,
  paintMode: "stroke",
  strokeStyle: "rgba(245, 236, 73, 1)"
}
```

If the default style doesn't look good, you can create your own style to use:

```javascript
let newDrawingStyleID = enhancer.createDrawingStyle({
  lineWidth: 5,
  paintMode: "strokeAndFill",
  fontSize: 100,
  fillStyle: "rgba(65, 105, 225, 0.5)",
  strokeStyle: "rgba(65, 105, 225, 1)",
  fontFamily: "Consolas"
});
drawingLayer.setDrawingStyle(newDrawingStyleID);
```

### Set multiple DrawingStyles

For each **DrawingLayer**, `DrawingStyles` can be used in three ways

1. Use the same **DrawingStyle** for everything;
2. Use a specific **DrawingStyle** for a specific type of **DrawingItems**;
3. Use a specific **DrawingStyle** for a specific type of **DrawingItems** which are in a particular state.

> As of version 3.0.1, the only available states for a **DrawingStyle** are "default" and "selected".

The following shows how to do the different settings with the method [`setDrawingStyle`](../../api-reference/drawinglayer.md#setdrawingstyle):

```javascript
// The following code assumes we have defined 3 different DrawingStyles with IDs 100, 101 and 102.
// Use DrawingLayer 100 for everything
drawingLayer.setDrawingStyle(100);
// Use DrawingLayer 101 for all "rect"s
drawingLayer.setDrawingStyle(101, "rect");
// Use DrawingLayer 102 for selected "rect"s
drawingLayer.setDrawingStyle(102, "rect", "selected");
```

## Modify existing DrawingItems

The SDK allows **DrawingItems** to be modified after they are drawn on the UI. To do this, we first change the **DrawingLayer** to "editor" mode with the method [`setMode()`](../../api-reference/drawinglayer.md#setmode).

```javascript
drawingLayer.setMode("editor");
```

Next, click on the **DrawingItem** you want to modify and you will see its "corners" and a "rotate control point" which, when dragged, modify the original shape in different ways. At the same time, this **DrawingItem** will be marked "selected", which means it might [use a different **DrawingStyle**](#set-multiple-drawingstyles).

## Try it out

You can try the shape drawing feature on the following link:

[Draw Shapes with DCEJS](https://jsfiddle.net/DynamsoftTeam/mjnq07Lp/)
