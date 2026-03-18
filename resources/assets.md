# Asset Management Rules

During UI slicing, all image assets MUST be handled through the central project registry.

---

## Asset Registry Location

- **Registry File**: `lib/app/assets/images/index.dart`
- **Class Name**: `AppImages`

## Rules for Assets

1. **Mandatory Registry**: NEVER use hardcoded asset path strings in widgets.
2. **Auto-Mapping**: If a prompt mentions an asset by name (e.g., "use asset bgOnboarding"), automatically map it to the corresponding constant in `AppImages` (e.g., `AppImages.bgOnboarding`).
3. **Registry Awareness**: Always check `lib/app/assets/images/index.dart` to see if the asset already exists.

## Figma MCP Restrictions

> [!WARNING]
> **DO NOT** use the Figma MCP tool to export or download assets from Figma.

1. **Manual Import**: Asset exporting should be done manually by the developer.
2. **Feedback Requirement**: If a design requires a new asset that is not yet in `AppImages`:
   - Stop implementing the asset usage.
   - Give feedback to the USER stating that an asset is needed.
   - Request the asset file or the confirmed `AppImages` path from the USER.

## Implementation Pattern

```dart
// WRONG
Image.asset('lib/app/assets/images/onboarding/bg_onboarding.png')

// CORRECT
Image.asset(AppImages.bgOnboarding)
```

> [!IMPORTANT]
> If an asset is missing, wait for the USER to provide it before proceeding with that specific part of the UI.
