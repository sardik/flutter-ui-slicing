# Localization Rules

During UI slicing, all text elements extracted from Figma MUST be localized immediately.

---

## ARB File Locations

- **English**: `lib/core/localization/app_en.arb`
- **Indonesian**: `lib/core/localization/app_id.arb`

## Rules for Translation

1. **Auto-Translation**: When you extract text from Figma, you must generate entries for BOTH files.
2. **English Source**: If the Figma design uses English, you MUST automatically translate the wording to Indonesian for `app_id.arb`.
3. **Indonesian Source**: If the Figma design uses Bahasa Indonesia, you MUST automatically translate the wording to English for `app_en.arb`.
4. **Consistency**: Ensure the tone and context are preserved during translation.

## Naming Conventions (Keys)

Use descriptive keys following a hierarchical pattern:

- `[screenName][ElementName][Property]`
- Examples:
  - `onboardingLoginButton`: "Login/Register"
  - `loginTitle`: "Welcome Back"
  - `formLabelEmail`: "Email Address"

## Implementation Pattern

In your Flutter code, NEVER hardcode strings:

```dart
// WRONG
Text("Login")
Text(AppLocalizations.of(context)!.onboardingLoginButton)

// CORRECT
Text(context.lang.onboardingLoginButton) // lang is an extension of AppLocalizations
```

> [!IMPORTANT]
> Always verify that the new keys are added to BOTH `.arb` files before completing the task.
