---
title: laser-controls
type: components
layout: docs
parent_section: components
image:
  src: https://user-images.githubusercontent.com/674727/26897482-91947a94-4b7d-11e7-9cb5-5c47f50938e4.gif
source_code: src/components/laser-controls.js
examples: []
---

The laser-controls component provides a tracked controller with a laser or ray
cursor shooting out to be used for input and interactions. All headsets ship with some form of 
tracked input controller that has at least a button to trigger actions. Using laser-controls we can
get a consistent form of interaction that works across all VR platforms with
a single line of HTML.

[meta-touch-controls]: ./meta-touch-controls.md
[vive-controls]: ./vive-controls.md
[windows-motion-controls]: ./windows-motion-controls.md

laser-controls is a **higher-order component**, meaning the component wraps and
configures other components, rather than implementing any logic itself. Under
the hood, laser-controls sets all of the tracked controller components:

- [vive-controls]
- [meta-touch-controls]
- [windows-motion-controls]

[cursor]: ./cursor.md
[raycaster]: ./raycaster.md

These controller components get activated if its respective controller is
connected and detected via the Gamepad API. Then the model of the actual
controller is used. laser-controls then configures the [cursor
component][cursor] for listen to the appropriate events and configures the
[raycaster component][raycaster] to draw the laser.

When the laser intersects with an entity, the length of the line gets truncated
to the distance to the intersection point.

## Example

```html
<a-entity laser-controls="hand: left"></a-entity>
```

## Properties

| Properties        | Description                                             |
|-------------------|---------------------------------------------------------|
| hand              | `left` or `right`.                                      |
| model             | Whether the default model for the controller is loaded. |
| defaultModelColor | Color for the default controller model.                 |

## Customizing the Raycaster

Configure the [raycaster properties][raycaster].

For example:

```html
<a-entity laser-controls raycaster="objects: .links; far: 5"></a-entity>
```

## Customizing the Line

[customize]: ./raycaster.md#customizing-the-line

See [*Raycaster: Customizing the Line*][customize].

For example:

```html
<a-entity laser-controls raycaster="lineColor: red; lineOpacity: 0.5"></a-entity>
```
