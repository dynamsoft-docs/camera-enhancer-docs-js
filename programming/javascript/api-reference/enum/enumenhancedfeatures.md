---
layout: default-layout
title: EnumEnhancedFeatures  - Dynamsoft Camera Enhancer JavaScript Edition API
description: Use this enum data type to set enhanced features when using Dynamsoft Camera Enhancer JavaScript Edition in your project.
keywords: EnumEnhancedFeatures, CameraEnhancer, api reference, javascript, js
needAutoGenerateSidebar: false
noTitleIndex: true
breadcrumbText: EnumEnhancedFeatures
permalink: /programming/javascript/api-reference/enum/enumenhancedfeatures.html
---

# EnumEnhancedFeatures

`EnumEnhancedFeatures` enumerates the advanced features that can be enabled to enhance user interaction.

```typescript
export enum EnumEnhancedFeatures {
    /**
     * Enables auto-focus on areas likely to contain barcodes, assisting in their identification and interpretation.
     */
    EF_ENHANCED_FOCUS = 4,
    /**
     * Facilitates automatic zooming in on areas likely to contain barcodes, aiding in their detection and decoding.
     */
    EF_AUTO_ZOOM = 16,
    /**
     * Allows users to tap on a specific item or area in the video feed to focus on,
     * simplifying the interaction for selecting or highlighting important elements.
     */
    EF_TAP_TO_FOCUS = 64,
}
```