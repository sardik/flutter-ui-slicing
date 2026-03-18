# Widget Selection

Choose the right widget type based on screen requirements. Prefer simplicity — start small, upgrade when needed.

---

## Decision Tree

```
IF screen has state    → ConsumerStatefulWidget
IF screen is static    → StatelessWidget (prefer const)
IF unsure              → start StatelessWidget, upgrade when needed
```

## Widget Order (StatefulWidget)

1. `initState`
2. handlers / helpers
3. `dispose`
4. widget builders (`_buildSectionName`)
5. `build` **(LAST)**

## Widget Order (StatelessWidget)

1. helpers
2. widget builders
3. `build` **(LAST)**

## Reusable Widget Criteria

- **Check First**: Before slicing a new UI element, check if the design can be provided by an existing reusable component in `lib/app/widget/` or `lib/core/widget/`. If so, use it.
- **Extract When Needed**: If a UI pattern (like a specific card or list tile) appears multiple times in the design but no component exists, extract it into a reusable component instead of building it locally for one screen.
- **Location**: Reusable widgets belong in `lib/core/widget/` (for generic UI) or `lib/app/widget/` (for app-specific domain UI) when they:
  - Are used by **2+ screens**
  - Contain no screen-specific logic
  - Are configured via parameters

## What is NOT Allowed

- Placing reusable widgets inside screen folders
- Placing sections outside the `section/` directory
- Hardcoded dummy data inside UI

## Core Widgets Available

Before creating new widgets, check if these existing ones can be used:

| Widget             | Purpose                        |
| ------------------ | ------------------------------ |
| `SimpleHeader`     | Screen headers                 |
| `CoreButton`       | Primary action buttons         |
| `Pressable`        | Touchable wrapper with effects |
| `TitleSection`     | Section headings               |
| `ShimmerContainer` | Loading state container        |
| `ShimmerWidget`    | Loading skeleton element       |
| `ShimmerCard`      | Loading skeleton card          |
