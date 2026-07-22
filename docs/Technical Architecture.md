# Technical Architecture

The core platform, user-interface toolkit, theme requirement, installer technology, supported Windows versions, and application architecture have been selected. Other implementation details remain undecided and must be recorded in [[Decisions]] when chosen.

## Technology choices

Wallwright will be built as a Windows desktop application using the following technologies:

### Application platform

- .NET 8
- C#
- WPF
- Windows 10 and Windows 11

The application is intended specifically for Windows. Cross-platform support is not a goal.

Wallwright must support both Windows 10 and Windows 11. Features that depend on newer Windows APIs must either have a compatible fallback or be excluded from the supported behaviour on Windows 10.

The exact minimum supported Windows 10 version and build remain `TBD`.

### Supported processor architectures

Wallwright should support both:

- x64
- ARM64

The application must not assume that Windows runs only on Intel processors. AMD-based Windows systems are covered by the x64 build, while Windows on Arm devices require an ARM64 build.

The aim is to support Windows users whether their computer contains an Intel processor, an AMD processor, or an Arm processor quietly plotting to make itself indispensable.

Support for 32-bit x86 is not currently planned.

Packaging, native dependencies, and image-processing libraries must therefore be selected with both x64 and ARM64 support in mind. Any dependency that prevents ARM64 support requires a documented justification in [[Decisions]].

### Application architecture

Wallwright will use the Model-View-ViewModel pattern.

MVVM should provide a clear separation between:

- Views and visual presentation
- View models and user-interface state
- Product logic
- Image-processing behaviour
- Windows platform integration
- Configuration and persistence

The architecture should remain pragmatic. MVVM must not be used as justification for unnecessary abstraction, excessive service wrappers, or interfaces with only one trivial implementation.

Code-behind may be used where behaviour is purely visual or belongs naturally to the WPF view. Product behaviour and application state should remain outside the view.

The specific MVVM implementation approach and whether a supporting toolkit will be used remain `TBD`.

### User interface

The application will use [WPF UI by Lepo](https://wpfui.lepo.co/) for its visual components and Windows-style application shell.

WPF UI should be used to provide a modern Windows appearance without obscuring standard WPF behaviour or introducing unnecessary custom controls.

The project should follow the design language established by WPF UI rather than mixing unrelated component libraries or visual styles.

### Graphics and image processing

The graphics and image-processing technology has not yet been selected.

The chosen technology must support:

- Loading common wallpaper image formats
- High-quality image scaling
- Cropping without altering the source image
- Reliable preview-to-output fidelity
- Large images without unreasonable memory use
- Correct handling of display dimensions and DPI
- Export to formats compatible with Windows wallpaper APIs

Potential technologies must be evaluated before selection. No image-processing library should be added until the requirements and trade-offs have been documented in [[Decisions]].

### Installation

Wallwright will be distributed using an installer created with Inno Setup.

The installer should eventually support:

- Installation for normal Windows users
- Start menu shortcuts
- Optional desktop shortcut
- Clean uninstall
- Application version information
- Upgrade installation over an existing version
- Removal of application files without deleting user-created images or unrelated files

Detailed installer behaviour remains `TBD`.

### Theme support

Wallwright must support both light mode and dark mode.

The application should default to the theme selected by Windows.

Theme detection and application are technical responsibilities, while the expected user experience is documented in [[UX and Design]].

### Technical decisions still required

- Exact .NET 8 SDK version
- Minimum supported Windows 10 version
- Unit-test framework
- MVVM toolkit, if any
- Dependency-injection approach, if one is needed
- Graphics and image-processing technology
- Wallpaper-generation strategy
- Multi-monitor integration
- Settings storage format
- Logging approach
- Update mechanism
- Installer scope: per-user or per-machine
- Whether the application will be self-contained or framework-dependent

## Application boundaries

Wallwright will use MVVM to separate visual presentation from application state and behaviour.

The intended boundaries are:

- **Views** display application state and handle purely visual interaction.
- **View models** expose state and commands required by the views.
- **Product logic** models wallpaper placement, scaling, cropping, and output decisions.
- **Image processing** loads source images and produces wallpaper output.
- **Windows integration** discovers displays and applies wallpapers.
- **Persistence** stores application settings and recoverable user state.

The boundaries should remain practical rather than ceremonial. Additional layers should be introduced only when they provide a clear testing, maintenance, or platform-integration benefit.

## Image-processing responsibilities

The application will need to produce an applied result from non-destructive positioning, scaling, and cropping choices.

The original source image must never be modified.

The image-processing component will eventually be responsible for:

- Loading supported image formats
- Reading source image dimensions and metadata
- Producing preview images
- Applying scaling and crop calculations
- Rendering the final wallpaper image
- Preserving acceptable image quality
- Creating output with the correct dimensions for the selected display arrangement
- Managing temporary or generated wallpaper files

The processing library, colour-management behaviour, supported source formats, output formats, and generated-file lifecycle remain `TBD`.

## Windows wallpaper integration

`TBD` — the Windows APIs, output lifecycle, restoration behaviour, and differences between Windows 10 and Windows 11 require investigation and a documented decision.

## Multi-monitor support

Multi-monitor support is required for the first release and must shape the architecture from the beginning. The architecture must support assigning and positioning wallpaper images across multiple displays. The exact per-monitor, spanning, mixed-resolution, mixed-DPI, orientation, and display-change behaviours remain `TBD`.

## Configuration and persistence

`TBD` — settings, saved state, storage location, and migration policy have not been selected.

## Testing strategy

The MVVM separation should allow view-model and product behaviour to be tested independently of the WPF interface.

Wallwright must have unit tests for non-trivial product logic, view-model behaviour, image calculations, and bug fixes where unit testing is appropriate.

The specific unit-test framework remains `TBD`.

When a test double is needed, use Moq rather than adding handwritten fake implementations. Tests should still prefer simple real collaborators when they are deterministic, fast, and clearer than a mock.

Human release verification is defined in [[Release Integration Tests]]. The detailed strategy for automated integration, visual, image-comparison, and supported-Windows-version testing remains `TBD`.

## Packaging and distribution

Inno Setup will be used to create the installer.

Wallwright will support Windows 10 and Windows 11 on x64 and ARM64. Installer behaviour, installation scope, application deployment model, prerequisites, and update mechanism remain `TBD`.

## Open technical questions

- What is the minimum supported Windows 10 version and build?
- Should an MVVM toolkit be used, and which one?
- Which graphics technology provides the best balance of quality, performance, and maintainability?
- Which Windows APIs can reliably produce preview-to-application fidelity?
- How should display scaling and mixed-DPI monitor arrangements be modelled?
- Which output formats preserve quality while remaining compatible with Windows?
- Which parts of wallpaper application can be tested automatically?
