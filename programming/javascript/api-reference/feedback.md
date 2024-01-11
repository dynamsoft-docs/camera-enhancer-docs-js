---
layout: default-layout
title: Feedback APIs - Dynamsoft Camera Enhancer JavaScript API
description: This is the page of the Feedback APIs of Dynamsoft Camera Enhancer JavaScript SDK.
keywords: camera enhancer, Feedback, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: Feedback
permalink: /programming/javascript/api-reference/feedback.html
---

# Class Feedback

| API Name                            | Description                                                   |
| ----------------------------------- | ------------------------------------------------------------- |
| [beep()](#beep)                     | Trigger a beep when the method is called.                     |
| [vibrate()](#vibrate)               | Trigger a vibrate when the method is called.                  |
| [beepSoundSource](#beepsoundsource) | Returns or sets the sound source for the beep.                |
| [vibrateDuration](#vibrateduration) | Returns or sets how long the vibration lasts in milliseconds. |

## beep

Trigger a beep when the method is called.

```typescript
beep(): void;
```

**Code Snippet**

```javascript
enhancerFeedback.beep();
```

## vibrate

Trigger a vibrate when the method is called.

> [Sticky user activation](https://developer.mozilla.org/en-US/docs/Web/Security/User_activation){:target="_blank"} is required for triggering a "vibration", read more [here](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/vibrate#security){:target="_blank"}.

```typescript
vibrate(): void;
```

**Code Snippet**

```javascript
enhancerFeedback.vibrate();
```

## beepSoundSource

Returns or sets the sound source for the beep. The value is either a base64 encoded string that represents the sound or a URL to the sound file.

```typescript
beepSoundSource: string;
```

## vibrateDuration

Returns or sets how long the vibration lasts in milliseconds. The default value is 300 .

```typescript
vibrateDuration: number;
```
