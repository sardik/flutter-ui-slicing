# Design Tokens

All styling MUST use design tokens. NEVER hardcode hex colors, pixel values, or TextStyles.

---

## Spacing (`Space.*`)

| Token        | Size | Use Case                     |
| ------------ | ---- | ---------------------------- |
| `Space.xs`   | 4px  | Micro spacing                |
| `Space.sm`   | 8px  | Small gaps                   |
| `Space.reg`  | 12px | Form field padding           |
| `Space.md`   | 16px | Medium spacing               |
| `Space.lg`   | 20px | Screen horizontal padding ⭐ |
| `Space.xl`   | 24px | Section spacing              |
| `Space.xxl`  | 28px | Extra large                  |
| `Space.xxxl` | 32px | Maximum spacing              |

## Border Radius (`Rounded.*`)

| Token          | Size   | Use Case                  |
| -------------- | ------ | ------------------------- |
| `Rounded.xs`   | 2px    | Micro radius              |
| `Rounded.sm`   | 4px    | Small radius              |
| `Rounded.reg`  | 6px    | Regular radius            |
| `Rounded.md`   | 8px    | Medium radius             |
| `Rounded.lg`   | 10px   | Interactive elements      |
| `Rounded.xl`   | 12px   | Cards, form containers ⭐ |
| `Rounded.full` | 9999px | Pills, chips, circles ⭐  |

## Colors (`context.color.*`)

### Content Colors

| Token                                  | Use Case            |
| -------------------------------------- | ------------------- |
| `context.color.contentPrimary1`        | Primary main        |
| `context.color.contentPrimary2`        | Primary secondary   |
| `context.color.contentPrimary3`        | Primary tertiary    |
| `context.color.contentAccent1`         | Accent main         |
| `context.color.contentAccent2`         | Accent secondary    |
| `context.color.contentAccent3`         | Accent tertiary     |
| `context.color.contentBlack`           | Black text          |
| `context.color.contentPrimaryInverted` | White/Inverted text |
| `context.color.contentSecondary`       | Secondary text      |
| `context.color.contentTertiary`        | Tertiary/Muted text |
| `context.color.contentAccent`          | Generic accent text |
| `context.color.contentSuccess`         | Success text        |
| `context.color.contentWarning`         | Warning text        |
| `context.color.contentError`           | Error text          |
| `context.color.contentDisabled`        | Disabled text       |
| `context.color.contentDarkPurple`      | Dark Purple text    |

### Background Colors

| Token                         | Use Case                |
| ----------------------------- | ----------------------- |
| `context.color.bgPrimary1`    | Primary default         |
| `context.color.bgPrimary2`    | Primary secondary       |
| `context.color.bgPrimary3`    | Primary tertiary        |
| `context.color.bgAccent1`     | Accent default          |
| `context.color.bgAccent2`     | Accent secondary        |
| `context.color.bgAccent3`     | Accent tertiary         |
| `context.color.bgPlain`       | Plain/White background  |
| `context.color.bgGrey`        | Grey background         |
| `context.color.bgGrey2`       | Lighter Grey            |
| `context.color.bgLightGrey`   | Light Grey (#222222)    |
| `context.color.bgDarkGrey`    | Dark Grey (#141313)     |
| `context.color.bgGreenSoft`   | Soft Green background   |
| `context.color.bgYellowSoft`  | Soft Yellow background  |
| `context.color.bgRedSoft`     | Soft Red background     |
| `context.color.bgGreenVivid`  | Vivid Green background  |
| `context.color.bgYellowVivid` | Vivid Yellow background |
| `context.color.bgRedVivid`    | Vivid Red background    |

### Border Colors

| Token                          | Use Case           |
| ------------------------------ | ------------------ |
| `context.color.borderPrimary1` | Primary border     |
| `context.color.borderPrimary2` | Primary border 2   |
| `context.color.borderPrimary3` | Primary border 3   |
| `context.color.borderDefault`  | Default border     |
| `context.color.borderDisabled` | Disabled border    |
| `context.color.borderError`    | Error border       |
| `context.color.borderPlain`    | Plain/White border |

## Typography (`context.font.*`)

| Token                                      | Use Case    |
| ------------------------------------------ | ----------- |
| `context.font.h1` — `h8`                   | Headings    |
| `context.font.body1` — `body3`             | Body text   |
| Override: `.copyWith(color:, fontWeight:)` | Adjustments |

## Animation Standards

### Standard Transitions

```dart
// Standard duration & curve
duration: Durations.short3
curve: context.currentCurve  // easeInOutCubic

// Property transitions
AnimatedContainer(duration: Durations.short3, curve: context.currentCurve, ...)

// Opacity transitions
AnimatedOpacity(duration: Durations.short3, opacity: isVisible ? 1.0 : 0.0, ...)
```

### Initial/Landing Animation (Conditional)

**RULE**: ONLY implement landing animations if the user prompt explicitly requests it (e.g., "implement animation", "with animation", "add fade in"). If not mentioned, skip landing animations.

When requested, use `FadeinSlide` to create a staggered entrance effect:

- Use `y: 10` for upward motion.
- Use `delayMs` in increments (e.g., 200, 300, 400) for staggered elements.

```dart
FadeinSlide(
  delayMs: 200,
  y: 10,
  child: _buildHeader(),
),
FadeinSlide(
  delayMs: 300,
  y: 10,
  child: _buildContent(),
),
```

## Layout Standards

```dart
// Screen padding
EdgeInsets.all(Space.lg)             // 20px standard

// Spacing between elements
SizedBox(height: Space.xl)           // 24px section spacing
SizedBox(height: Space.md)           // 16px element spacing
SizedBox(height: Space.sm)           // 8px micro spacing
```

## When Token Doesn't Exist

If a design value has no matching token:

1. MUST add it to `AdditionalColors` in `lib/core/theme/color_theme.dart`
2. MUST use the `AdditionalColors` entry in UI (no direct hex usage)
3. SHOULD keep naming specific to the design intent
