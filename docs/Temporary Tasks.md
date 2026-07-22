# Temporary Tasks

This is a temporary, repository-local snapshot of currently known Wallwright work for transfer to the project Kanban board. The Kanban board is the planning source of truth; this note should be updated or removed once its tasks have been captured there.

Tasks are grouped by development stage rather than priority or delivery date. An unchecked item is not necessarily ready to implement: consult its linked documentation and resolve relevant `TBD` decisions first.

## Specification

- [x] Define the complete first-release user workflow from launch through wallpaper application.
- [x] Define supported image formats and any image size limits.
- [x] Define how users select source images and assign them to monitors.
- [ ] Define positioning methods, coordinate model, units, bounds, and snapping behaviour.
- [ ] Define scaling controls, units, limits, and aspect-ratio behaviour.
- [ ] Define cropping controls, constraints, and interaction behaviour.
- [ ] Define measurable preview-to-applied-wallpaper fidelity criteria.
- [ ] Define wallpaper-application success, failure, restoration, and recovery behaviour.
- [ ] Define per-monitor image assignment behaviour.
- [ ] Decide whether one image may span multiple monitors.
- [ ] Define how monitor position, orientation, and Windows virtual desktop coordinates are represented.
- [ ] Define behaviour for mixed monitor resolutions and mixed DPI values.
- [ ] Define behaviour when monitors are connected, disconnected, reordered, or changed.
- [ ] Decide whether wallpaper configurations can be saved and restored.
- [ ] Define settings, persistence, migration, and reset behaviour.
- [ ] Define empty, loading, and error states.
- [ ] Select accessibility targets and the supported assistive-technology test matrix.
- [ ] Establish first-release acceptance criteria.

## Technical decisions

- [ ] Select the exact .NET 8 SDK version.
- [ ] Select the minimum supported Windows 10 version and build.
- [ ] Decide whether to use an MVVM toolkit and select one if needed.
- [ ] Select the unit-test framework; use Moq when test doubles are required.
- [ ] Decide whether dependency injection is needed and document the approach if it is.
- [ ] Evaluate and select graphics and image-processing technology for x64 and ARM64.
- [ ] Define the wallpaper-generation strategy and generated-file lifecycle.
- [ ] Select the Windows APIs used for monitor discovery and wallpaper application.
- [ ] Define the technical model for mixed-DPI and multi-monitor coordinates.
- [ ] Select the settings storage format and location.
- [ ] Define the logging approach without recording private image data.
- [ ] Decide whether deployment is self-contained or framework-dependent.
- [ ] Decide whether installation is per-user or per-machine.
- [ ] Decide whether x64 and ARM64 require separate installers.
- [ ] Decide the code-signing approach.
- [ ] Decide the release distribution location.
- [ ] Decide whether an update mechanism belongs in the first release.
- [ ] Record every selected product or technical decision in [[Decisions]].

## UX prototype

- [ ] Design a focused prototype for monitor discovery and selection.
- [ ] Prototype selecting images and assigning them to monitors.
- [ ] Prototype direct and precise positioning and scaling interactions.
- [ ] Prototype non-destructive cropping through the preview.
- [ ] Prototype reviewing the complete single-monitor and multi-monitor result.
- [ ] Prototype the wallpaper-application step and its success and failure feedback.
- [ ] Test whether the workflow is understandable with representative users.
- [ ] Record prototype findings in [[UX and Design]].
- [ ] Record product decisions resulting from prototype evaluation in [[Decisions]].

## Repository and application foundation

- [ ] Create the .NET 8 solution and initial project structure after the relevant decisions are documented.
- [ ] Configure WPF and WPF UI by Lepo.
- [ ] Configure x64 and ARM64 builds.
- [ ] Establish pragmatic MVVM boundaries without unnecessary abstraction.
- [ ] Create the unit-test project using the selected framework and Moq.
- [ ] Establish application versioning.
- [ ] Add continuous integration for build and automated tests on supported architectures where practical.

## Core implementation

- [ ] Discover connected monitors and represent their arrangement.
- [ ] Implement source-image selection and validation.
- [ ] Implement image-to-monitor assignment.
- [ ] Implement the documented positioning model.
- [ ] Implement the documented scaling model.
- [ ] Implement non-destructive cropping.
- [ ] Render a preview from the same calculations used for final output.
- [ ] Generate wallpaper output with correct display dimensions and acceptable image quality.
- [ ] Apply generated wallpaper through the selected Windows APIs.
- [ ] Preserve source images unchanged throughout the workflow.
- [ ] Implement documented errors and recovery paths.
- [ ] Implement light and dark themes that follow Windows by default.
- [ ] Respond appropriately when the Windows theme changes while Wallwright is running.
- [ ] Implement the documented accessibility and keyboard behaviour.
- [ ] Implement settings and recoverable state after persistence behaviour is specified.

## Multi-monitor implementation

- [ ] Support assigning and positioning wallpaper images across multiple displays.
- [ ] Support the documented mix of per-monitor and spanning behaviour.
- [ ] Handle mixed resolutions and DPI values according to the specification.
- [ ] Handle landscape and portrait monitor arrangements.
- [ ] Handle negative virtual desktop coordinates and reordered displays.
- [ ] Handle monitor connection, disconnection, and primary-display changes according to the specification.
- [ ] Verify that the preview represents the complete applied multi-monitor result.

## Automated testing

- [ ] Add unit tests for positioning calculations.
- [ ] Add unit tests for scaling calculations.
- [ ] Add unit tests for cropping calculations.
- [ ] Add unit tests for monitor-coordinate calculations.
- [ ] Add tests for representative multi-monitor arrangements.
- [ ] Add tests for mixed resolutions, DPI values, and Windows scaling.
- [ ] Add tests for wallpaper-output dimensions.
- [ ] Add image-based tests for preview-to-output fidelity where reliable.
- [ ] Add tests for settings persistence and migration once specified.
- [ ] Add tests for failure and recovery behaviour.
- [ ] Add regression tests for non-trivial bug fixes.
- [ ] Verify x64 and ARM64 builds.
- [ ] Define and implement the remaining automated integration test strategy.

## Packaging and release preparation

- [ ] Create the Inno Setup installer after packaging decisions are documented.
- [ ] Install the correct x64 or ARM64 build for the target architecture.
- [ ] Add the Start menu shortcut and optional desktop shortcut.
- [ ] Include accurate application version information.
- [ ] Support upgrade installation over an existing version.
- [ ] Support clean uninstall without deleting user-created images or unrelated files.
- [ ] Configure code signing if required by the documented decision.
- [ ] Document supported systems, installation, known limitations, and uninstall behaviour.
- [ ] Replace remaining placeholder cases in [[Release Integration Tests]] with concrete steps and expected results.
- [ ] Run automated tests against the release candidate.
- [ ] Complete the human [[Release Integration Tests]] matrix on Windows 10 and Windows 11, x64 and ARM64.
- [ ] Record release evidence and obtain human approval before publishing.

## Documentation maintenance

- [ ] Keep [[Functional Requirements]] current as behaviour is decided.
- [ ] Keep [[UX and Design]] current as the interface evolves.
- [ ] Keep [[Technical Architecture]] and [[Decisions]] current as technologies and boundaries are selected.
- [ ] Keep [[Release Integration Tests]] aligned with implemented behaviour.
- [ ] Review and update [[Roadmap]] when scope decisions change.
- [ ] Remove this temporary note after all tasks have been transferred to the Kanban board.
