# Design System Tokens Reference

Consolidated design tokens for the Flutter app design system.

---

## Spacing Tokens (`Space.*`)

```dart
Space.xs    = 4px    // Micro spacing
Space.sm    = 8px    // Small gaps
Space.reg   = 12px   // Regular spacing, form field padding
Space.md    = 16px   // Medium spacing
Space.lg    = 20px   // Standard screen horizontal padding ⭐
Space.xl    = 24px   // Section spacing
Space.xxl   = 28px   // Extra large
Space.xxxl  = 32px   // Maximum spacing
```

## Border Radius Tokens (`Rounded.*`)

```dart
Rounded.xs   = 2px     // Micro radius
Rounded.sm   = 4px     // Small radius
Rounded.reg  = 6px     // Regular radius
Rounded.md   = 8px     // Medium radius
Rounded.lg   = 10px    // Interactive elements
Rounded.xl   = 12px    // Form containers, cards ⭐
Rounded.full = 9999px  // Pills, chips, circular ⭐
```

## Color Context Extensions

```dart
// Content
context.color.contentPrimary      // Main text, icons
context.color.contentPrimary2     // Interactive elements ⭐
context.color.contentSecondary    // Secondary text
context.color.contentTertiary     // Muted text ⭐

// Backgrounds
context.color.backgroundPrimary    // Main backgrounds
context.color.backgroundSecondary  // Card backgrounds
context.color.backgroundGrey       // Input fields, placeholders ⭐

// Borders
context.color.borderDefault    // Standard borders ⭐
context.color.borderPrimary2   // Active/selected states ⭐
```

## Typography Context Extensions

```dart
// Headings
context.font.h1 — context.font.h8

// Body Text
context.font.body1   // Primary body text
context.font.body2   // Secondary body text
context.font.body3   // Small body text

// Usage
context.font.h1.copyWith(color: context.color.contentPrimary)
```

## Animation Standards

```dart
Duration: Durations.short3           // Quick UI feedback
Curve:    context.currentCurve       // easeInOutCubic
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
