# Flutter UI Slicing Skill

An AI agent skill for slicing Figma designs into Flutter widgets with consistency and high quality.

## What It Does

This skill provides a comprehensive workflow for implementing UI from Figma designs into Flutter widgets. It covers:

- **Design Analysis** — Extract layout, spacing, typography, and colors from Figma
- **File Structure** — Organized screen/section layout with 500 LOC limit
- **Design Tokens** — Consistent use of `Space.*`, `Rounded.*`, `context.color.*`, `context.font.*`
- **Asset Management** — `AppImages` registry pattern
- **Localization** — ARB generation for EN/ID with auto-translation
- **Animation** — Conditional landing animations with `FadeinSlide`
- **State Handling** — Loading (shimmer), error, and empty states
- **Quality Assurance** — Pixel-perfect validation checklist

## Installation

```bash
npx skills add sardik/flutter-ui-slicing
```

## Skill Structure

```
flutter-ui-slicing/
├── SKILL.md              # Main skill definition
├── examples/
│   └── templates.md      # Code templates & patterns
├── resources/
│   ├── design-tokens.md  # Spacing, color, typography tokens
│   ├── assets.md         # Asset management rules
│   ├── file-structure.md # File organization rules
│   ├── localization.md   # ARB localization guide
│   ├── state-handling.md # Loading/error/empty patterns
│   ├── widget-selection.md # Widget choice guide
│   ├── quality-checklist.md # QA checklist
│   └── tokens.md         # Token reference
└── scripts/              # Helper scripts (reserved)
```

## Key Rules

- ✅ MUST use design tokens — never hardcode values
- ✅ MUST split sections into separate files (1 section = 1 file)
- ✅ MUST handle loading/empty/error states
- ✅ MUST keep files under 500 LOC
- ✅ MUST reuse existing core widgets before creating new ones

## License

[MIT](LICENSE)
