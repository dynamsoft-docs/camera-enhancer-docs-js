---
layout: default-layout
title: EnumDrawingItemState  - Dynamsoft Camera Enhancer JavaScript Edition API
description: Use this enum data type to set item state when using Dynamsoft Camera Enhancer JavaScript Edition in your project.
keywords: EnumDrawingItemState, CameraEnhancer, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: EnumDrawingItemState
permalink: /programming/javascript/api-reference/enum/enumdrawingitemstate.html
---

# EnumDrawingItemState

`EnumDrawingItemState` defines the various states that a drawing item can be in, providing a mechanism for distinguishing between normal and selected states.

```typescript
enum EnumDrawingItemState {
    /**
     * DIS_DEFAULT: The default state of a drawing item. This state indicates that
     * the drawing item is in its normal, unselected state.
     */
    DIS_DEFAULT = 1,
    /**
     * DIS_SELECTED: Indicates that the drawing item is currently selected. This state
     * can trigger different behaviors or visual styles, such as highlighting the item
     * to show it is active or the focus of user interaction.
     */
    DIS_SELECTED = 2
}
```
