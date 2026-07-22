# Release Integration Tests

This document defines the human-executed integration tests that must pass before a Wallwright release can be approved. These tests verify the complete application as a user experiences it, including the interface, image processing, Windows integration, persistence, installer, and supported environments.

The application is not ready for release while a required test is failing, blocked without an accepted justification, or has not been run on the applicable supported configuration.

Exact control names and behaviours that have not yet been specified are marked `TBD`. Replace those placeholders when the interface and requirements are decided.

## Recording a test run

Record the following for every release candidate:

- Release candidate version and commit
- Tester
- Date
- Windows version and build
- Processor architecture: x64 or ARM64
- Display arrangement, resolutions, orientation, and scale factors
- Theme: light or dark
- Installer type and installation scope
- Result for every test: Pass, Fail, Not applicable, or Blocked
- Evidence or notes for failures and blocked tests

Retain the completed test record with the release evidence. Storage location and format are `TBD`.

## Test images

Use a small, reviewed set of non-private test images that makes position, scale, crop, orientation, and image quality easy to judge. The eventual set should include:

- A landscape image with distinctive content at every edge and corner
- A portrait image with distinctive content at every edge and corner
- An image smaller than the target display
- An image larger than the target display
- An image with fine detail or a reference grid for detecting scaling and crop errors
- Each supported source format

The supported formats and repository location for test images remain `TBD`. Do not use personal wallpaper images as release evidence.

## Supported-environment matrix

Run the complete applicable test set on every supported combination, or document an approved reduced matrix in [[Decisions]]. At minimum, release coverage must include:

- Windows 10 x64
- Windows 10 ARM64
- Windows 11 x64
- Windows 11 ARM64
- Windows light theme
- Windows dark theme
- A standard 100% display scale
- At least one supported high-DPI display scale

The minimum Windows 10 build and exact display-scale matrix remain `TBD`.

## Installation and launch

### Clean installation

1. Begin on a supported system without Wallwright installed.
2. Run the release-candidate installer.
3. Complete installation using the default choices.
4. Launch Wallwright from the Start menu shortcut.

Expected result:

- Installation completes without an unexpected warning or error.
- The installed application and version information are correct.
- The Start menu shortcut launches the application.
- Wallwright opens in a usable empty state and follows the current Windows theme.
- No unrelated files or settings are changed.

### Optional desktop shortcut

1. Install Wallwright with the desktop-shortcut option enabled.
2. Launch Wallwright from that shortcut.
3. Repeat installation with the option disabled where practical.

Expected result:

- The shortcut is created only when requested and launches the installed application.
- Declining the option does not create a desktop shortcut.

### Upgrade installation

1. Install the previous supported Wallwright release.
2. Create representative application settings or recoverable state when those features exist.
3. Install the release candidate over the existing version.
4. Launch the upgraded application.

Expected result:

- The upgrade completes without requiring an unnecessary uninstall.
- The release candidate launches and reports the correct version.
- Existing supported settings and recoverable state behave according to the documented migration policy.

Migration behaviour remains `TBD` until persistence is specified.

## Empty state and image loading

### Initial empty state

1. Launch Wallwright without a previously loaded image.
2. Inspect the window and available primary action.

Expected result:

- The application clearly explains how to begin.
- Controls that require an image are unavailable or clearly inactive.
- Keyboard focus is visible and begins in a useful location.
- No placeholder image is mistaken for a selected wallpaper.

### Load a supported image

1. Activate the image-selection control (`TBD` label).
2. Select a valid image in each supported format.

Expected result:

- The selected image loads without modifying the source file.
- The application displays the correct image, orientation, and dimensions.
- Positioning, scaling, cropping, preview, and application controls become available as designed.
- Loading and errors do not leave stale content from a previously selected image.

### Cancel image selection

1. Activate the image-selection control.
2. Cancel the file picker without choosing an image.

Expected result:

- The application returns to its prior state without an error or unintended change.

### Reject an unsupported or invalid file

1. Attempt to load an unsupported, damaged, inaccessible, or non-image file where the picker permits it.

Expected result:

- Wallwright does not crash or display invalid image content.
- The error explains what failed and provides a useful next step.
- The previous valid state remains usable where possible.

Supported formats and exact recovery behaviour remain `TBD`.

## Positioning, scaling, and cropping

### Reposition an image

1. Load a test image with identifiable edges and a central reference point.
2. Move the image using every supported positioning method.
3. Position it at representative extremes and at a precise intermediate location.

Expected result:

- The image follows the input predictably and remains aligned with any displayed values.
- The chosen position is represented accurately in the preview.
- Movement does not alter the source image.

Exact positioning methods, units, bounds, and snapping behaviour remain `TBD`.

### Scale an image

1. Load images both larger and smaller than the selected display.
2. Increase and decrease scale using every supported scaling method.
3. Exercise representative minimum, maximum, and intermediate values.

Expected result:

- Scale changes are predictable and reflected accurately in the preview.
- Aspect-ratio behaviour matches the documented requirement.
- The interface remains responsive with supported large images.
- The source image remains unchanged.

Scale bounds, units, and aspect-ratio controls remain `TBD`.

### Crop an image

1. Load an edge-marked test image.
2. Adjust the visible region using every supported crop method.
3. Exercise each edge, each corner, and a central crop.

Expected result:

- The preview shows exactly which source region will be visible.
- Crop controls behave consistently at boundaries.
- No crop operation modifies the source image.

Crop interaction and constraints remain `TBD`.

## Preview and wallpaper application

### Preview fidelity

1. Create an arrangement whose position, scale, and crop can be identified unambiguously.
2. Inspect the preview and record evidence.
3. Apply the wallpaper.
4. Compare the Windows desktop with the recorded preview.

Expected result:

- The applied wallpaper matches the preview in position, scale, crop, orientation, and visible content.
- The output has no unexplained stretching, borders, colour shift, or quality loss.
- Display scaling does not create an unexpected offset or size difference.

Acceptance tolerances and comparison method remain `TBD`.

### Apply wallpaper

1. Load and arrange a valid image.
2. Activate the apply control (`TBD` label).
3. Observe the result in Windows and relaunch Wallwright.

Expected result:

- Windows displays the prepared wallpaper without requiring an unrelated manual step.
- Wallwright reports success only after application succeeds.
- Generated or temporary files are handled according to the documented lifecycle.
- The source image remains byte-for-byte unchanged.

### Application failure

1. Reproduce a safe, controlled condition in which Windows cannot accept or access the generated wallpaper (`TBD` procedure).
2. Attempt to apply the wallpaper.

Expected result:

- Wallwright does not report success.
- The error identifies the failed operation and provides a useful next step.
- The previous wallpaper and application state are preserved or recoverable according to the documented policy.

## Theme behaviour

### Launch in each Windows theme

1. Set Windows to light theme and launch Wallwright.
2. Inspect every available screen, dialog, tooltip, control state, and preview surrounding.
3. Repeat in dark theme.

Expected result:

- Wallwright follows the selected Windows theme on launch.
- Window chrome, navigation, controls, dialogs, empty states, error states, tooltips, disabled controls, focus, and selection states are legible and consistent.
- Dark mode is deliberately styled rather than merely colour-inverted.
- The wallpaper preview itself is not colour-shifted or otherwise altered by the application theme.

### Change the Windows theme while running

1. Launch Wallwright.
2. Change Windows from light to dark theme, then from dark to light.

Expected result:

- Wallwright responds appropriately without requiring corrupted state or an application restart unless a restart requirement is explicitly documented.
- All visible application surfaces update consistently.
- The source image and wallpaper preview colours remain unchanged.

## Keyboard and accessibility checks

1. Complete the primary workflow using the keyboard wherever the supported interaction permits.
2. Move focus through all interactive controls in both directions.
3. Inspect labels, focus indicators, disabled states, scaling, and contrast in both themes.
4. Exercise the supported screen-reader workflow (`TBD`).

Expected result:

- Focus order is logical and focus remains visible.
- Controls have meaningful accessible names and states.
- Keyboard operation does not trap focus or require a pointer without a documented reason.
- Text and controls remain usable at supported Windows text and display scales.

The accessibility standard, assistive-technology matrix, and detailed acceptance criteria remain `TBD`.

## Multi-monitor checks

Multi-monitor product behaviour remains `TBD`, but multi-monitor support is required for the first release. Before that release can be approved, replace this section with concrete tests covering every supported arrangement, including where applicable:

- Monitors with different resolutions
- Monitors with different scale factors
- Landscape and portrait orientation
- Negative desktop coordinates and reordered displays
- Primary-display changes
- Per-monitor wallpapers
- Wallpapers spanning multiple monitors
- Connecting or disconnecting a monitor while Wallwright is running

No multi-monitor behaviour should be considered release-tested solely because it worked on a single-display system.

## Persistence and recovery

Persistence behaviour remains `TBD`. When settings or recoverable state are implemented, add tests for:

- Normal application restart
- Operating-system restart
- Missing, damaged, inaccessible, and older configuration data
- Upgrade migration
- Reset to defaults
- Removal of generated files without removal of source images

## Uninstall

1. Install and use Wallwright to create representative settings and generated wallpaper files.
2. Uninstall Wallwright through the supported Windows interface.
3. Inspect the installation location, shortcuts, settings, generated files, source images, and current wallpaper.

Expected result:

- Application files and shortcuts are removed cleanly.
- User-created source images and unrelated files are never deleted.
- Settings, generated wallpapers, and the currently applied wallpaper follow the documented uninstall policy.

The policy for retained settings, generated files, and the active wallpaper remains `TBD`.

## Release approval

A human release reviewer must confirm that:

- Every applicable required test has a recorded result.
- Failures are fixed and retested, or explicitly accepted through a documented decision.
- Blocked and not-applicable tests include an explanation.
- Preview-to-application fidelity has been verified on the supported release matrix.
- Source images remained unmodified during testing.
- Installation, upgrade, launch, and uninstall were tested using the release-candidate package.
- Known limitations and unresolved `TBD` items do not contradict release claims.

The reviewer records the final result as **Approved** or **Rejected**. A rejected candidate must not be released.
