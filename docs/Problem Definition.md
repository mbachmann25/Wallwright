# Problem Definition

## Current Windows behaviour

Windows provides a small set of wallpaper placement modes: Fill, Fit, Stretch, Tile, and Centre. These presets make broad choices about scaling and placement, but do not expose precise control over the visible crop or the image's position.

## User problem

A user may want a particular subject or region of an image to appear at an exact place on the desktop. The built-in modes can crop the wrong area, introduce unwanted empty space or distortion, or provide no way to adjust the result deliberately.

## Scope

Wallwright is concerned with positioning, scaling, cropping, previewing, and applying desktop wallpapers more precisely than the built-in modes allow. Exact supported workflows and monitor configurations are `TBD`.

## Out of scope

- Editing or overwriting the source image.
- General-purpose image editing.
- Features not explicitly accepted into the product specification.

Further exclusions are `TBD`.

## Open questions

- What is the minimum supported Windows 10 version and build?
- Which image formats will be supported?
- What multi-monitor behaviours are required?
- Which operations, if any, should be available after a wallpaper has been applied?
