# Quality Checklist

Every UI slicing task MUST pass all items before it is considered done.

---

## Design Tokens

- [ ] All spacing uses `Space.*` tokens
- [ ] All colors use `context.color.*`
- [ ] All typography uses `context.font.*`
- [ ] All radius uses `Rounded.*`

## UI Standards

- [ ] Touch targets ≥ 44x44px
- [ ] File size < 500 LOC per file
- [ ] Zero linter errors
- [ ] Pixel-perfect match to Figma
- [ ] If landing animation requested, `FadeinSlide` used correctly with staggered delays and `y: 10`

## State Handling

- [ ] Loading state uses `ShimmerContainer`
- [ ] Error state handled inside content tree
- [ ] Empty state handled inside content tree

## Assets

- [ ] All assets used via `AppImages.*` constants
- [ ] No hardcoded asset path strings in widgets
- [ ] No assets exported via Figma MCP
- [ ] User was prompted for any missing design assets

## Localization

- [ ] All hardcoded strings moved to `app_en.arb` and `app_id.arb`
- [ ] English wording accurately translated to Indonesian in `app_id.arb`
- [ ] Indonesian wording accurately translated to English in `app_en.arb`
- [ ] ARB keys follow naming convention (e.g., `screenNameElementName`)

## File Organization

- [ ] Screen file only composes sections
- [ ] One section = one file
- [ ] Sections exported via `section/index.dart`
- [ ] No hardcoded dummy data (use `lib/core/model/mock/`)
- [ ] Reusable widgets in `lib/core/widget/` (not in screen folder)

## Code Quality

- [ ] `build()` method is LAST in the class
- [ ] No side effects inside `build()`
- [ ] `const` used wherever possible
- [ ] Comments minimal — no obvious restatements
- [ ] No commented-out code
