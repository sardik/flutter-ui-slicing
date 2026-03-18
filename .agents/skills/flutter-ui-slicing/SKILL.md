---
name: flutter-ui-slicing
description: Workflow for slicing Figma designs into Flutter widgets. Covers design analysis, section splitting, basic animation, arb localization design token application, and quality assurance.
---

# Flutter UI Slicing Skill

Comprehensive skill for implementing UI from Figma designs into Flutter widgets consistently and with high quality.

## When to Apply

- Slicing a new screen from Figma into Flutter
- Creating screen sections from a design
- Implementing pixel-perfect UI from design specs
- Building new Flutter screens with proper structure

## Rule Categories by Priority

| #   | Category          | Priority | Rules                                          |
| --- | ----------------- | -------- | ---------------------------------------------- |
| 1   | Design Tokens     | CRITICAL | Spacing, colors, typography, radius, animation |
| 2   | Asset Management  | CRITICAL | AppImages registry, no Figma MCP exports       |
| 3   | File Structure    | CRITICAL | Screen/section layout, 500 LOC limit, exports  |
| 3   | State Handling    | HIGH     | ShimmerContainer pattern, loading/error/empty  |
| 4   | Localization      | HIGH     | ARB EN/ID generation, auto-translation         |
| 5   | Widget Selection  | MEDIUM   | StatelessWidget vs ConsumerStatefulWidget      |
| 6   | Quality Checklist | MEDIUM   | Final validation before done                   |

## Quick Reference

### Workflow Steps

1. **Analyze Design** — Extract layout, spacing, typography, colors from Figma
2. **Setup Structure** — Create screen file + section files under `lib/screen/<name>/`
3. **Resolve Assets** — Check `AppImages` for existing assets; request from USER if missing.
4. **Implement** — Apply design tokens (`Space.*`, `Rounded.*`, `context.color.*`, `context.font.*`)
5. **Core Widgets** — Use existing widgets (`SimpleHeader`, `CoreButton`, `Pressable`, `ShimmerContainer`)
6. **Localization** — Extract text to `app_en.arb` and `app_id.arb` (auto-translate as needed)
7. **State Handling** — Loading via `ShimmerContainer`, error/empty inside content tree
8. **Quality Check** — Zero linter errors, pixel-perfect, file < 500 LOC

### Key Rules

- MUST use design tokens, NEVER hardcode values
- MUST split sections into separate files (1 section = 1 file)
- MUST handle loading/empty/error states
- MUST keep files under 500 LOC
- MUST reuse existing core widgets and app-specific components before creating new ones
- MUST extract repeating UI patterns into reusable components instead of building them locally per screen
- MUST extract all design values from Figma — never guess
- MUST conditionally implement landing animations (`FadeinSlide`) ONLY when explicitly requested (e.g., "implement animation", "with animation").

## How to Use

Read individual rule files for detailed explanations and code examples:

```
resources/design-tokens.md
resources/assets.md
resources/file-structure.md
resources/localization.md
resources/state-handling.md
resources/widget-selection.md
resources/quality-checklist.md
```

Read code templates for implementation patterns:

```
examples/templates.md
```
