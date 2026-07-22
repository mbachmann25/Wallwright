# Decisions

This is a lightweight log for significant product and architectural decisions. Add new entries without rewriting prior decisions; supersede an earlier entry explicitly when necessary.

## Decision template

### Title

- **Date:** YYYY-MM-DD
- **Decision:** `TBD`
- **Context:** `TBD`
- **Alternatives considered:** `TBD`
- **Reasoning:** `TBD`
- **Consequences:** `TBD`

## Descriptive documentation filenames

- **Date:** 2026-07-22
- **Decision:** Use descriptive documentation filenames instead of numbered filenames. Use [[Overview]] to control navigation and intended reading order.
- **Context:** The `docs` directory is an Obsidian vault intended to be browsed and maintained by humans.
- **Alternatives considered:** Prefix filenames with numbers to force filesystem sorting.
- **Reasoning:** Descriptive note names are easier to link, search, and understand outside a prescribed sequence. Navigation belongs in the vault's entry point rather than in filename prefixes.
- **Consequences:** Contributors must keep [[Overview]] current when the documentation structure or intended reading order changes.

## Initial application platform and architecture

- **Date:** 2026-07-22
- **Decision:** Build Wallwright as a Windows-specific .NET 8 C# application supporting Windows 10 and Windows 11 on x64 and ARM64, using WPF, pragmatic MVVM, WPF UI by Lepo, light and dark themes that follow Windows by default, and an installer created with Inno Setup. Support for 32-bit x86 is not currently planned.
- **Context:** The project requires a Windows desktop interface, reliable Windows integration across supported Windows versions and processor architectures, clear separation of presentation and product behaviour, a consistent modern Windows design language, and a conventional installation experience.
- **Alternatives considered:** `TBD`
- **Reasoning:** These technologies, supported platforms, and architectural boundaries were selected as the initial implementation direction. Detailed dependency choices, deployment model, and installer behaviour remain undecided.
- **Consequences:** Cross-platform support is not a goal. Newer Windows API features require a Windows 10-compatible fallback or exclusion from Windows 10 behaviour. Packaging and dependencies must support both x64 and ARM64; a dependency that prevents ARM64 support requires documented justification. Product behaviour and application state remain outside views, while purely visual behaviour may use code-behind. The application should preserve standard WPF behaviour, follow WPF UI's design language, support both themes consistently, and package releases through Inno Setup.

## Unit testing and test doubles

- **Date:** 2026-07-22
- **Decision:** Add unit tests for non-trivial testable behaviour and use Moq when test doubles are needed instead of creating handwritten fake implementations. The unit-test framework remains `TBD`.
- **Context:** The project needs automated verification of product logic and regressions without committing prematurely to a specific unit-test framework.
- **Alternatives considered:** Handwritten fake implementations; selecting a unit-test framework immediately.
- **Reasoning:** Moq provides a consistent approach to test doubles while allowing the unit-test framework to be evaluated separately.
- **Consequences:** Test projects will depend on Moq when mocking is required. Tests should use simple real collaborators when clearer, and should not introduce fake implementation classes solely for testing.

## Multi-monitor support in the first release

- **Date:** 2026-07-22
- **Decision:** Multi-monitor support is required for the first release and must influence the architecture and prototype from the beginning.
- **Context:** Wallwright is intended to position and assign wallpaper images on systems with one or more monitors. Building first around single-monitor assumptions could make correct multi-monitor behaviour difficult to add later.
- **Alternatives considered:** Ship the first release for single-monitor systems and add multi-monitor support later.
- **Reasoning:** Monitor discovery, coordinate systems, image assignment, preview, output generation, and Windows integration all depend on the display arrangement and should be validated as one coherent workflow.
- **Consequences:** The prototype, product model, image processing, Windows integration, automated testing, and human release testing must account for multiple displays. Exact per-monitor, spanning, mixed-resolution, mixed-DPI, orientation, and display-change behaviour must be specified before the corresponding implementation begins.
