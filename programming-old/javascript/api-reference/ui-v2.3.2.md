---
layout: default-layout
title: UI APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the main page of Dynamsoft Camera Enhancer JavaScript SDK UI.
keywords: camera enhancer, UI, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: UI
permalink: /programming/javascript/api-reference/ui-v2.3.2.html
---

# UI APIs

| Name| Description |
|---|---|
| [getVisibleRegion()](#getvisibleregion) | Returns a `Region` object which specifies which part of the original video is shown in the video element. |
| [addScanRegionOverlayCanvas()](#addscanregionoverlaycanvas) | Add a canvas of the same size as the scan area directly above the scan area. |
| [ifShowScanRegionMask](#ifshowscanregionmask) | Returns or sets whether the scan region mask is shown. |
| [ifShowScanRegionLaser](#ifshowscanregionlaser) | Returns or sets whether the laser indicator is shown in the scan region. |
| [setScanRegionMaskStyle()](#setscanregionmaskstyle) | Sets the styles for the scan region mask. |
| [setVideoFit()](#setvideofit) | Sets the `object-fit` CSS property of the video element. |
| [getVideoFit()](#getvideofit) | Returns the value of the `object-fit` CSS property of the video element. |
| [setViewDecorator()](#setviewdecorator) | Sets and shows the view decorator. |
| [getViewDecorator()](#getviewdecorator) | Gets what view decorator is shown. |
| [setViewDecoratorLineWidth()](#setviewdecoratorlinewidth) | Sets the line width for drawing the view decorator. |
| [setViewDecoratorStrokeStyle()](#setviewdecoratorstrokestyle) | Sets the stroke style for drawing the view decorator. |
| [setViewDecoratorFillStyle()](#setviewdecoratorfillstyle) | Sets the fill style for drawing the view decorator. |
| [setViewDecoratorMaskFillStyle()](#setviewdecoratormaskfillstyle) | Sets the fill style for drawing the ask for the view decorator. |

## getVisibleRegion

Returns a `Region` object which specifies which part of the original video is shown in the video element

```typescript
getVisibleRegion(inPixels?: boolean): Region;
```

**Parameters**

`inPixels`: [optional] The coordinate type. If omitted or set to `false`, the returned coordinates are represented by percentage, otherwise, by pixels.

**Return value**

The visible region represented by a `Region` object.

**Code Snippet**

```javascript
enhancer.getVisibleRegion();
```

**See also**

[Region](interface/region.html)

## addScanRegionOverlayCanvas

Add a canvas of the same size as the scan area directly above the scan area.

```typescript
addScanRegionOverlayCanvas(): Canvas;
```

**Parameters**

None.

**Return value**

The added `Canvas` object.

**Code Snippet**

```javascript
let cvs = enhancer.addScanRegionOverlayCanvas();
let ctx = cvs.getContext('2d');
ctx.fillStyle = "white";
ctx.font = '50px serif';
ctx.fillText('Dynamsoft Camera Enhancer', 50, 90);
```

## ifShowScanRegionMask

Returns or sets whether the scan region mask is shown. The default is `true`.

```typescript
ifShowScanRegionMask: boolean;
```

## ifShowScanRegionLaser

Returns or sets whether the laser indicator is shown in the scan region.  The default is `false`.

> This API only works when the viewer element contains the elements with the class names `dce-scanarea` and `dce-scanlight` (like the built-in viewer).

```typescript
ifShowScanRegionLaser: boolean;
```

## setScanRegionMaskStyle

Sets the styles for the scan region mask.

```typescript
setScanRegionMaskStyle(maskStyle: any): void;
```

**Parameters**

`maskStyle`: specify the new style. Read more on [strokeStyle](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/strokeStyle) and [fillStyle](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/fillStyle).

> The default value is
>
> ```javascript
> lineWidth = 2;
> strokeStyle = "rgb(254,142,20)";
> fillStyle = "rgba(0,0,0,0.5)";
> ```

**Return value**

None.

**Code Snippet**

```javascript
enhancer.setScanRegionMaskStyle({
    lineWidth: 5,
    strokeStyle: "white",
    fillStyle: "rgba(50,50,50,0.3)"
});
```

## setVideoFit

Sets the `object-fit` CSS property of the video element.

```typescript
setVideoFit(objectFit: string): void;
```

**Parameters**

`objectFit`: specify the new fit type. At present, only "cover" and "contain" are allowed and the default is "contain". Check out more on [object-fit](https://developer.mozilla.org/en-US/docs/Web/CSS/object-fit).

**Return value**

None.

**Code Snippet**

```javascript
enhancer.setVideoFit("cover");
```

## getVideoFit

Returns the value of the `object-fit` CSS property of the video element.

```typescript
getVideoFit(): string;
```

**Parameters**

None.

**Return value**

The value of the `object-fit` CSS property.

**Code Snippet**

```javascript
enhancer.getVideoFit();
```

## setViewDecorator

Sets and shows the view decorator.

```typescript
setViewDecorator(type: string | string[], area: Area): void;
```

**Parameters**

`type`: specify the decorator type. Allowed values are "rectangle" , "focus" , "crossline" , "crosshair" , ["rectangle", "crossline"], ["rectangle", "crosshair"], ["focus", "crossline"] and ["focus", "crosshair"]. If passed an empty string, the decorator is cleared.

`area`: specify where to place the decorator. It accepts 4 values:

* `x`,     `y`: top-left point of the decorator in percentage (0~100) of the width/height of the viewer.
* `width`,     `height`: size of the decorator in percentage (0~100) of the width/height of the viewer.

**Return value**

None.

**Code Snippet**

```javascript
let area = {
    x: 5,
    y: 10,
    width: 90,
    height: 80
};
enhancer.setViewDecorator(["rectangle", "crosshair"], area);
```

**See also**

[Area](interface/area.html)

## getViewDecorator

Gets what view decorator is shown.

```typescript
getViewDecorator(): {type: string[], area: Area, canvas: Canvas};
```

**See also**

[Area](interface/area.html)

## setViewDecoratorLineWidth

Sets the line width for drawing the view decorator.

```typescript
setViewDecoratorLineWidth(type: string, width: number): void;
```

**Parameters**

`type`: specify the decorator type. Allowed values are "rectangle" , "focus" , "crossline" and "crosshair".

`width`: specify the line width.

**Return value**

None.

**Code Snippet**

```javascript
let area = {
    x: 5,
    y: 10,
    width: 90,
    height: 80
};
enhancer.setViewDecoratorLineWidth("rectangle", 10);
enhancer.setViewDecorator(["rectangle", "crosshair"], area);
```

## setViewDecoratorStrokeStyle

Sets the stroke style for drawing the view decorator.

```typescript
setViewDecoratorStrokeStyle(type: string, strokeStyle: string): void;
```

**Parameters**

`type`: specify the decorator type. Allowed values are "rectangle" , "focus" , "crossline" and "crosshair".

`strokeStyle`: specify the stroke style. Read more on [strokeStyle](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/strokeStyle).

**Return value**

None.

**Code Snippet**

```javascript
let area = {
    x: 5,
    y: 10,
    width: 90,
    height: 80
};
enhancer.setViewDecoratorStrokeStyle("rectangle", "white");
enhancer.setViewDecorator(["rectangle", "crosshair"], area);
```

## setViewDecoratorFillStyle

Sets the fill style for drawing the view decorator.

```typescript
setViewDecoratorFillStyle(type: string, fillStyle: string): void;
```

**Parameters**

`type`: specify the decorator type. Allowed values are "rectangle" and "focus".

`fillStyle`: specify the fill style. Read more on [fillStyle](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/fillStyle).

**Return value**

None.

**Code Snippet**

```javascript
let area = {
    x: 5,
    y: 10,
    width: 90,
    height: 80
};
enhancer.setViewDecoratorFillStyle("rectangle", "rgba(50,50,50,0.3)");
enhancer.setViewDecorator(["rectangle", "crosshair"], area);
```

## setViewDecoratorMaskFillStyle

Sets the fill style for drawing the ask for the view decorator.

```typescript
setViewDecoratorMaskFillStyle(type: string, fillStyle: string): void;
```

**Parameters**

`type`: specify the decorator type. Allowed values are "rectangle" and "focus".

`fillStyle`: specify the fill style. Read more on [fillStyle](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/fillStyle).

**Return value**

None.

**Code Snippet**

```javascript
let area = {
    x: 5,
    y: 10,
    width: 90,
    height: 80
};
enhancer.setViewDecoratorMaskFillStyle("rectangle", "rgba(50,50,50,0.3)");
enhancer.setViewDecorator(["rectangle", "crosshair"], area);
```