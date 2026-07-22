# Development Guidelines

This document is the single source of truth for AI coding-agent instructions. `AGENTS.md` and `CLAUDE.md` are generated from it by `scripts/sync-agent-instructions.ps1`.

## General behaviour

- Read the relevant documents in `/docs` before implementing a feature.
- Start with `docs/Overview.md` when unfamiliar with the project.
- Do not invent product requirements.
- Record significant architectural or product decisions in `docs/Decisions.md`.
- Keep changes focused on the requested task.
- Do not perform unrelated refactoring.
- Prefer readable, maintainable code over clever code.
- Explain assumptions when requirements are incomplete.
- Do not silently change established behaviour.
- Do not claim work is complete unless it builds and relevant tests pass.

## Vibe-coding safeguards

- Always consult the relevant documents in `/docs` when vibe-coding, and treat the documented requirements and decisions as authoritative.
- The user may describe desired behaviour informally. Translate that into explicit requirements before implementing substantial behaviour.
- Do not treat a mock-up as a complete specification.
- Do not add features merely because they seem useful.
- Do not replace working architecture with a fashionable alternative without a documented reason.
- Avoid unnecessary frameworks, abstractions, dependency-injection layers, service wrappers, and generic repositories.
- Build the smallest coherent implementation that satisfies the documented requirement.
- Preserve the project's design language once established.
- Prefer native Windows and .NET capabilities where they are sufficient.
- State assumptions clearly rather than concealing uncertainty in code.
- Do not confuse visual decoration with design.
- Never solve a UI issue by merely placing the existing UI inside another border, panel, card, or container.
- A visual redesign must address hierarchy, spacing, alignment, typography, interaction, responsiveness, and states, not just decoration.
- Do not introduce dark mode, animations, rounded cards, gradients, or similar styling merely because they are fashionable.
- Do not remove unusual behaviour until it has been confirmed that the behaviour is accidental rather than intentional.
- When something appears incorrect, first consider whether it may reflect an undocumented requirement, domain rule, compatibility constraint, or user misunderstanding.
- Prefer asking for a documented decision over confidently implementing a guess.

## Documentation

- Keep documentation current when behaviour changes.
- Use Obsidian-compatible Markdown.
- Prefer relative links or Obsidian links.
- Use descriptive filenames intended for humans.
- Do not add numbered filename prefixes merely to control sorting.
- Use `Overview.md` to establish navigation and reading order.
- Do not add generated build artefacts to the vault.
- Use Mermaid diagrams where they communicate architecture or flow more clearly.
- Mark speculation and undecided matters as `TBD`.
- Do not rewrite documentation into generic corporate language.
- Preserve the project's established voice where practical.

## Code quality

- Use CRLF line endings for repository text files.
- Follow ECMA-335 (the Common Language Infrastructure specification) for applicable .NET and CIL behaviour.
- Use nullable reference types.
- Prefer async APIs for genuinely asynchronous work.
- Pass cancellation tokens through asynchronous operations where appropriate.
- Avoid `async void` except for event handlers.
- Do not suppress warnings without documenting why.
- Add tests for non-trivial behaviour and bug fixes.
- Use Moq when test doubles are needed; do not add handwritten fake implementations.
- Keep Windows-specific code behind clear boundaries where practical.
- Dispose native and managed resources correctly.
- Avoid global mutable state.
- Log useful operational information without logging private user data or image contents.
- Do not add dependencies when the platform or standard library already provides a clear and maintainable solution.
- Keep methods and classes focused without splitting code into abstractions that provide no practical value.
- Prefer explicit domain names over generic names such as `Manager`, `Helper`, `Processor`, or `Service`.

## Git behaviour

- Do not commit unless explicitly requested.
- Do not push unless explicitly requested.
- Do not rewrite history.
- Do not modify unrelated files.
- Use small, descriptive commits when asked to commit.
- Never include generated binaries, local configuration, secrets, or user-specific paths.
- Review `git diff` before reporting completion.
- Do not discard existing user changes.
- Do not use destructive Git commands unless explicitly requested.
