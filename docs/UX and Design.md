# UX and Design

This note defines design intent, not a finished visual design.

## Design goals

- Make the relationship between the source image, crop, and desktop result clear.
- Keep common actions obvious while allowing precise control.
- Preserve user confidence through an accurate preview and reversible Windows integration.

## Main application layout

`TBD` — no window structure or finished layout has been selected.

## Primary workflow

The expected sequence is image selection, arrangement, preview, and application. Exact interactions are `TBD`.

## Controls

`TBD` — control types, keyboard interactions, precision entry, and reset behaviour require design decisions.

## Preview behaviour

The preview must match the applied wallpaper. How monitor bounds, scaling, and system UI are represented is `TBD`.

## Empty states

The application should explain how to begin when no image is loaded. Content and actions are `TBD`.

## Loading states

`TBD` — loading operations and progress presentation depend on the technical design.

## Error states

Errors should identify what failed and offer a meaningful next step where possible. Specific states are `TBD`.

## Accessibility

Keyboard access, screen-reader support, contrast, text scaling, and motion considerations must be addressed. Detailed targets are `TBD`.

## Windows design language

The application should follow the design language established by WPF UI and feel at home on Windows without allowing decoration to obscure hierarchy or interaction. Wallwright supports Windows 10 and Windows 11; the minimum supported Windows 10 version and build remain `TBD`.

## Theme behaviour

Wallwright must support both light mode and dark mode.

By default, the application should follow the current Windows theme. A user opening Wallwright should therefore see an interface consistent with the rest of their operating system without having to configure anything first.

The application should respond appropriately when the Windows theme changes.

A manual theme setting may be added later, with the following possible options:

- Follow Windows
- Light
- Dark

The default must remain `Follow Windows`.

Theme support must apply consistently across the entire application, including:

- Window chrome
- Navigation
- Controls
- Dialogs
- Image-preview surroundings
- Empty states
- Error states
- Tooltips
- Disabled controls
- Focus and selection states

Dark mode must not be treated as an inverted light theme. Contrast, readability, borders, disabled states, and image-preview backgrounds must be designed deliberately for both themes.

The wallpaper preview itself must not be colour-shifted or altered by the selected application theme.

## Open questions

- What information must remain visible during adjustment?
- How should precise numeric control coexist with direct manipulation?
- How should multiple monitors be represented?
- Which accessibility standard and test matrix will be adopted?
