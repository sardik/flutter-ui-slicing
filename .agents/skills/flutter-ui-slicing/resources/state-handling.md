# State Handling

MUST NOT use conditional branching for loading states inside `build()`. Loading is a **container concern**, not a screen concern.

---

## Required Pattern

```
ShimmerContainer
├── Loading State → ShimmerWidget / ShimmerCard
└── Content
    ├── Data State → ListView / GridView
    ├── Error State → ErrorView
    └── Empty State → EmptyView
```

## Rules

- MUST use `ShimmerContainer` with `showContent` as the single loading switch
- Loading state uses `ShimmerWidget` or `ShimmerCard` (never custom spinners)
- Error and empty states are handled **inside the content tree**, not as separate branches
- No hardcoded dummy data — use `lib/core/model/mock/` for mock data

## Incorrect ❌

```dart
@override
Widget build(BuildContext context) {
  if (_isLoading) return CircularProgressIndicator();  // ❌ Don't do this
  if (_error != null) return Text(_error!);
  return _buildContent();
}
```

## Correct ✅

```dart
@override
Widget build(BuildContext context) {
  return ShimmerContainer(
    showContent: !_isLoading,
    shimmerChild: ShimmerCard(),  // Loading skeleton
    child: _buildContent(),       // Handles data/error/empty internally
  );
}
```

## When Asset is Missing

Use a placeholder with a `TODO` comment:

```dart
Container(
  width: 120,
  height: 80,
  decoration: BoxDecoration(
    color: context.color.backgroundGrey,
    borderRadius: BorderRadius.circular(Rounded.md),
  ),
  child: Icon(Icons.image_outlined, color: context.color.contentTertiary),
)
// TODO: Replace with actual-asset-name.png when available
```
