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

The `Feedback` class is designed to facilitate both audio and haptic feedback functionalities, enabling applications to provide users with auditory signals through beeps and tactile sensations through vibrations.

| Name                                         | Description                                          |
| -------------------------------------------- | ---------------------------------------------------- |
| `static` [beep()](#beep)                     | Initiates a beep sound upon invocation.              |
| `static` [beepSoundSource](#beepsoundsource) | Returns or sets the beep's sound source.             |
| `static` [vibrate()](#vibrate)               | Activates device vibration upon invocation.          |
| `static` [vibrateDuration](#vibrateduration) | Determines the vibration's duration in milliseconds. |

## beep

Initiates a beep sound upon invocation.

```typescript
static beep(): void;
```

**Parameter**

None.

**Return value**

None.

**Code Snippet**

```javascript
Dynamsoft.DCE.Feedback.beep();
```

## beepSoundSource

Returns or sets the beep's sound source. The value is either a base64 encoded string that represents the sound or a URL to the sound file.

```typescript
static beepSoundSource: string;
```

**Code Snippet**

```javascript
Dynamsoft.DCE.Feedback.beepSoundSource = "path/to/beepSound.mp3";
```

## vibrate

Activates device vibration upon invocation.

> This method requires [Sticky user activation](https://developer.mozilla.org/en-US/docs/Web/Security/User_activation) as a security measure. More details can be found on the [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/vibrate#security).

```typescript
static vibrate(): void;
```

**Parameter**

None.

**Return value**

None.

**Code Snippet**

```javascript
Dynamsoft.DCE.Feedback.vibrate();
```

## vibrateDuration

Determines the vibration's duration in milliseconds.

```typescript
static vibrateDuration: number;
```

**Code Snippet**

```javascript
Dynamsoft.DCE.Feedback.vibrateDuration = 1000;
```
