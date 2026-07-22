# Roadmap

This roadmap describes development stages, not dates or feature commitments. Scope within each stage remains subject to documented requirements and decisions.

Testing and documentation are continuous activities and must be updated alongside implementation rather than postponed until the end.

## Specification

Define the behaviour required for Wallwright to set wallpaper images across supported Windows systems and monitor arrangements.

Specification work includes:

- Defining the complete user workflow
- Defining how images are selected and assigned
- Defining positioning, scaling, and cropping behaviour
- Defining the relationship between the preview and the applied wallpaper
- Defining multi-monitor behaviour
- Defining supported monitor arrangements
- Defining mixed-resolution and mixed-DPI behaviour
- Defining persistence and restoration behaviour
- Defining error states and recovery behaviour
- Establishing acceptance criteria for the first release

Relevant `TBD` items must be resolved before their corresponding implementation begins.

## Prototype

Create a focused prototype to validate the user-interface workflow.

The prototype should demonstrate the intended process for:

- Discovering connected monitors
- Selecting a monitor or monitor arrangement
- Choosing wallpaper images
- Assigning images to monitors
- Positioning and scaling images
- Cropping through the preview
- Reviewing the complete result
- Applying the wallpaper

The prototype does not need production-ready Windows integration or final image processing unless required to validate the interaction.

The purpose of the prototype is to determine whether the workflow is understandable, efficient, and suitable for both single-monitor and multi-monitor users.

The prototype should identify:

- Confusing steps
- Missing controls
- Unnecessary interactions
- Problems caused by limited screen space
- Whether monitor selection and image assignment are sufficiently clear
- Whether users can understand what Windows will display before applying it

The results must be recorded in [[UX and Design]] and any resulting product decisions must be recorded in [[Decisions]].

## Core implementation

Implement the agreed workflow for setting wallpaper images.

The core implementation should include:

- Detecting connected monitors
- Representing the current monitor arrangement
- Selecting one or more source images
- Assigning wallpaper images to monitors
- Positioning images
- Scaling images
- Cropping images non-destructively
- Previewing the expected result
- Generating the required wallpaper output
- Applying the wallpaper through supported Windows APIs
- Reporting failures clearly
- Preserving the original source images

The first implementation should remain focused on setting wallpapers correctly. Features unrelated to this workflow should not be added merely because they appear useful.

## Multi-monitor support

Multi-monitor support is required for the first release.

Wallwright must be designed for multiple monitors from the beginning rather than adding multi-monitor behaviour after a single-monitor implementation has already shaped the architecture.

The implementation must support assigning and positioning wallpaper images across multiple displays.

The following behaviour still requires specification:

- Whether each monitor may use a separate source image
- Whether one image may span multiple monitors
- How monitor position and orientation are represented
- Behaviour when monitors use different resolutions
- Behaviour when monitors use different scaling values
- Behaviour with portrait and landscape monitors
- Behaviour when a monitor is disconnected or rearranged
- Whether configurations can be saved and restored
- How Windows virtual desktop coordinates affect generated output

These decisions must be documented before the corresponding implementation work begins.

## Packaging

Package Wallwright for Windows using Inno Setup.

Packaging work includes:

- Producing x64 and ARM64 application builds
- Creating the Inno Setup installer
- Installing the correct build for the target architecture
- Adding a Start menu shortcut
- Supporting an optional desktop shortcut
- Including application version information
- Supporting upgrade installations
- Supporting clean uninstall
- Preserving user-created images and unrelated files during uninstall

The following packaging decisions remain `TBD`:

- Per-user or per-machine installation
- Self-contained or framework-dependent deployment
- Minimum supported Windows 10 build
- Whether x64 and ARM64 use separate installers
- Update mechanism
- Code signing
- Release distribution location

## Testing

Automated tests must be added alongside implementation.

The testing strategy should cover:

- Positioning calculations
- Scaling calculations
- Cropping calculations
- Monitor-coordinate calculations
- Multi-monitor arrangements
- Mixed resolutions
- Mixed DPI and Windows scaling
- Wallpaper-output dimensions
- Settings persistence
- Failure and recovery behaviour
- x64 and ARM64 builds

Image-based tests should be used where they can verify preview-to-output fidelity reliably.

Windows integration behaviour should be tested on both Windows 10 and Windows 11.

Keep [[Release Integration Tests]] current as behaviour is specified. A human must complete the applicable release integration test plan before a release is approved.

The full automated test matrix and release acceptance criteria remain `TBD`.

## First release

The first release must provide a complete workflow for setting wallpaper images on systems with one or more monitors.

The intended minimum scope includes:

- Windows 10 and Windows 11
- x64 and ARM64
- Single-monitor and multi-monitor systems
- Selecting wallpaper images
- Assigning images to monitors
- Positioning images
- Scaling images
- Cropping images
- Previewing the result
- Applying the wallpaper
- Light and dark application themes
- Following the current Windows theme by default
- Installation and uninstall through Inno Setup

The first release does not need to include every possible wallpaper-management feature. It must perform the agreed core workflow reliably and make the applied result match the preview.

Release acceptance criteria remain `TBD`.

## Possible later work

Potential work should be recorded here only after discussion. Inclusion does not constitute a commitment.

Possible later work may include:

- Saved wallpaper layouts
- Reusable monitor profiles
- Automatic wallpaper rotation
- Scheduled wallpaper changes
- Folder-based image collections
- Online image sources
- Editing tools beyond positioning, scaling, and cropping
- Automatic update support
- Additional application themes

These items are not part of the first release unless explicitly moved into its documented scope.
