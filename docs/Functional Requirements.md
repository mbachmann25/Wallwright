# Functional Requirements

This document records agreed behaviour. Unless stated explicitly, details remain `TBD`.

## Core workflow

The intended high-level flow is to choose an image, arrange it for the target desktop, preview the result, and apply it. Detailed steps are `TBD`.

## Image import

- The user can select a source image without Wallwright modifying that source.
- Supported formats, size limits, and import methods: `TBD`.

## Positioning

- The user can control image placement more precisely than Windows' built-in modes allow.
- Coordinate model, snapping, and input methods: `TBD`.

## Scaling

- The user can adjust image scale.
- Constraints, units, and aspect-ratio behaviour: `TBD`.

## Cropping

- The applied result can use a selected portion of the source image.
- Crop controls and interaction details: `TBD`.

## Preview

- The user can preview the wallpaper before applying it.
- The preview must represent the final wallpaper accurately.
- Preview fidelity requirements and display context: `TBD`.

## Applying wallpaper

- The user can apply the prepared result through Windows wallpaper integration.
- Output handling, restoration, and failure recovery: `TBD`.

## Multi-monitor behaviour

Multi-monitor support is required for the first release. Wallwright must support assigning and positioning wallpaper images across multiple displays. Supported arrangements, per-monitor image assignment, spanning, mixed-resolution and mixed-DPI behaviour, orientation changes, and display reconnection behaviour remain `TBD`.

## Persistence and settings

`TBD` — no persistence or settings behaviour has been agreed.

## Error handling

- Failures should be explained in useful, user-facing language.
- Detailed recovery behaviour and diagnostics: `TBD`.

## Open questions

- What is the minimum complete first workflow?
- Which precision controls and units are required?
- Should arrangements be saved or reopened?
- What restoration guarantees should applying a wallpaper provide?
