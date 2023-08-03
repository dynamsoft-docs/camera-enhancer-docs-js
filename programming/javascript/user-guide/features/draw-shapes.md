---
layout: default-layout
title: Features - Draw Shapes - Dynamsoft Camera Enhancer JavaSCript User Guide
description: This page talks about how to use DCE JS to draw shapes.
keywords: user guide, javascript, js, draw shapes.
noTitleIndex: true
needGenerateH3Content: true
needAutoGenerateSidebar: true
permalink: /programming/javascript/user-guide/features/draw-shapes.html
---

# Draw Shapes with DCE JS

In version 4.0.0 of DCE-JS, we introduced multiple APIs for drawing basic shapes on the built-in UI. This article will dive into how it works.

We will start with the following code which defines a page that has a CameraEnhancer instance embedded:

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
      let view = null;
      document.getElementById('drawShapes').onclick = drawShapes;
      (async () => {
          view = await Dynamsoft.DCE.CameraView.createInstance();
          enhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(view);
          document.getElementById("enhancerUIContainer").appendChild(view.getUIElement());
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

An `DrawingItem` is the basic shape that can be drawn. The SDK classify **DrawingItems** in different types: [`LineDrawingItem`](../../api-reference/drawingitem.md#linedrawingItem), [`RectDrawingItem`](../../api-reference/drawingitem.md#rectdrawingitem), [`QuadDrawingItem`](../../api-reference/drawingitem.md#quaddrawingitem), [`TextDrawingItem`](../../api-reference/drawingitem.md#textdrawingitem), and [`ImageDrawingItem`](../../api-reference/drawingitem.md#imagedrawingitem). The SDK also allow multiple items to be joined together and form the type called [`GroupDrawingItem`](../../api-reference/drawingitem.md#groupdrawingitem).

The following code shows how to define these types of **DrawingItems**:

```javascript
let drawingLayer = view.createDrawingLayer();
let rect = new Dynamsoft.DCE.DrawingItem.RectDrawingItem({x: 100,y: 100,width: 300,height: 300});
let line = new Dynamsoft.DCE.DrawingItem.LineDrawingItem({startPoint:{x: 600, y: 600}, endPoint:{x: 1050, y: 400}});
let text = new Dynamsoft.DCE.DrawingItem.TextDrawingItem("TESTING...",{x: 20,y: 20,width: 100,height: 100});
let quad = new Dynamsoft.DCE.DrawingItem.QuadDrawingItem({points:[{x:600,y:100},{x:500,y:300},{x:700,y:300},{x:700,y:100}]});
//let img = new Dynamsoft.DCE.DrawingItem.ImageDrawingItem(document.getElementById('testIMG'),{x: 200,y: 200,width: 300,height: 300},true);
```

Alternatively, the code might be like this

```javascript
import { DrawingItem } from "dynamsoft-camera-enhancer";
let drawingLayer = view.createDrawingLayer();
let rect = new DrawingItem.RectDrawingItem({x: 100,y: 100,width: 300,height: 300});
let line = new DrawingItem.LineDrawingItem({startPoint:{x: 600, y: 600}, endPoint:{x: 1050, y: 400}});
let text = new DrawingItem.TextDrawingItem("TESTING...",{x: 20,y: 20,width: 100,height: 100});
let quad = new DrawingItem.QuadDrawingItem({points:[{x:600,y:100},{x:500,y:300},{x:700,y:300},{x:700,y:100}]});
//let img = new Dynamsoft.DCE.DrawingItem.ImageDrawingItem(document.getElementById('testIMG'),{x: 200,y: 200,width: 300,height: 300},true);
```

> NOTE:
>
> `document.getElementById('testIMG')` is an image on the page defined in an `HTMLImageElement`.

## Draw these DrawingItems

After **DrawingItems** have been defined, simply call `addDrawingItems()` to draw them on the **DrawingLayer** we created earlier:

```javascript
function drawShapes(){
  let drawingLayer = view.createDrawingLayer();
  let rect = new Dynamsoft.DCE.DrawingItem.RectDrawingItem({x: 100,y: 100,width: 300,height: 300});
  let line = new Dynamsoft.DCE.DrawingItem.LineDrawingItem({startPoint:{x: 600, y: 600}, endPoint:{x: 1050, y: 400}});
  let text = new Dynamsoft.DCE.DrawingItem.TextDrawingItem("TESTING...",{x: 20,y: 20,width: 100,height: 100});
  let quad = new Dynamsoft.DCE.DrawingItem.QuadDrawingItem({points:[{x:600,y:100},{x:500,y:300},{x:700,y:300},{x:700,y:100}]});
  //let img = new Dynamsoft.DCE.DrawingItem.ImageDrawingItem(document.getElementById('testIMG'),{x: 200,y: 200,width: 300,height: 300},true);
  drawingLayer.addDrawingItems([rect,line,text,quad]);
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
let newDrawingStyleID = Dynamsoft.DCE.DrawingStyleManager.createDrawingStyle({
  id: 1;
  lineWidth: 5,
  paintMode: "strokeAndFill",
  fontSize: 100,
  fillStyle: "rgba(65, 105, 225, 0.5)",
  strokeStyle: "rgba(65, 105, 225, 1)",
  fontFamily: "Consolas"
});
// take new drawing style ID as input parameter
drawingLayer.setDefaultStyle(1);
```

### Set multiple DrawingStyles

For each **DrawingLayer**, `DrawingStyles` can be used in three ways

1. Use the same **DrawingStyle** for everything;
2. Use a specific **DrawingStyle** for a specific type of **DrawingItems**;
3. Use a specific **DrawingStyle** for a specific type of **DrawingItems** which are in a particular state.

> As of version 4.0.0, the only available states for a **DrawingStyle** are "default" and "selected".

The following shows how to do the different settings with the method [`setDefaultStyle`](../../api-reference/drawinglayer.md#setdefaultstyle):

```javascript
// The following code assumes we have defined 3 different DrawingStyles with IDs 100, 101 and 102.
// Use DrawingLayer 100 for everything
drawingLayer.setDefaultStyle(100);
// Use DrawingLayer 101 for all "rect"s
drawingLayer.setDefaultStyle(101, "rect");
// Use DrawingLayer 102 for selected "rect"s
drawingLayer.setDefaultStyle(102, "rect", "selected");
```

## Try it out

You can try the shape drawing feature on the following link:

[Draw Shapes with DCEJS](https://jsfiddle.net/DynamsoftTeam/mjnq07Lp/)
