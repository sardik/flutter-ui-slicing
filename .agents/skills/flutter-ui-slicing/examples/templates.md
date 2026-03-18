# UI Slicing Code Templates

## Screen Template

```dart
class NewScreen extends ConsumerStatefulWidget {
  const NewScreen({super.key});

  @override
  ConsumerState<NewScreen> createState() => _NewScreenState();
}

class _NewScreenState extends ConsumerState<NewScreen> {
  // State variables
  String _selectedValue = '';

  @override
  void initState() {
    super.initState();
    // Initialize complex state here
  }

  // Handlers
  void _onSelectValue(String value) {
    setState(() => _selectedValue = value);
  }

  // Widget builders
  Widget _buildHeader() {
    return Column(children: [
      // TODO: Implement header content
    ]);
  }

  Widget _buildContent() {
    return Column(children: [
      // TODO: Implement main content
    ]);
  }

  Widget _buildActions() {
    return Column(children: [
      // TODO: Implement actions
    ]);
  }

  // build() LAST
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
        child: SingleChildScrollView(
          padding: EdgeInsets.all(Space.lg),
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              _buildHeader(),
              SizedBox(height: Space.xl),
              _buildContent(),
              SizedBox(height: Space.xl),
              _buildActions(),
            ],
          ),
        ),
      ),
    );
  }
}
```

## Section Export (index.dart)

```dart
export 'header_section.dart';
export 'content_section.dart';
export 'action_section.dart';
```

## Private Widget Template

```dart
class _ComponentName extends StatelessWidget {
  const _ComponentName({
    required this.title,
    this.onTap,
    this.isSelected = false,
  });

  final String title;
  final VoidCallback? onTap;
  final bool isSelected;

  @override
  Widget build(BuildContext context) {
    return Pressable(
      onPressed: onTap,
      child: Container(
        // Use design tokens for all styling
        padding: EdgeInsets.all(Space.md),
        decoration: BoxDecoration(
          color: context.color.backgroundGrey,
          borderRadius: BorderRadius.circular(Rounded.xl),
        ),
        child: Text(title, style: context.font.body1),
      ),
    );
  }
}
```

## Form Field Template

```dart
Widget _buildFormField({
  required String label,
  required String value,
  required ValueChanged<String> onChanged,
  String? placeholder,
  bool isRequired = false,
}) {
  return Column(
    crossAxisAlignment: CrossAxisAlignment.start,
    children: [
      Text(
        label + (isRequired ? ' *' : ''),
        style: context.font.body2.copyWith(color: context.color.contentPrimary),
      ),
      SizedBox(height: Space.sm),
      Container(
        padding: EdgeInsets.all(Space.reg),
        decoration: ShapeDecoration(
          color: context.color.backgroundGrey,
          shape: RoundedRectangleBorder(
            borderRadius: BorderRadius.circular(Rounded.xl),
            side: BorderSide(color: context.color.borderDefault),
          ),
        ),
        child: TextFormField(
          initialValue: value,
          onChanged: onChanged,
          decoration: InputDecoration(
            hintText: placeholder,
            border: InputBorder.none,
            contentPadding: EdgeInsets.zero,
          ),
        ),
      ),
    ],
  );
}
```

## Selection Chip Template

```dart
Widget _buildChip({
  required String label,
  required bool isSelected,
  required VoidCallback onTap,
}) {
  return Pressable(
    onPressed: onTap,
    child: AnimatedContainer(
      duration: Durations.short3,
      curve: context.currentCurve,
      padding: EdgeInsets.symmetric(horizontal: Space.md, vertical: Space.sm),
      decoration: ShapeDecoration(
        color: isSelected ? context.color.contentPrimary2 : Colors.transparent,
        shape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(Rounded.full),
          side: BorderSide(
            color: isSelected ? context.color.borderPrimary2 : context.color.borderDefault,
          ),
        ),
      ),
      child: Text(
        label,
        style: context.font.body2.copyWith(
          color: isSelected ? Colors.white : context.color.contentPrimary,
        ),
      ),
    ),
  );
}
```

## Radio Button Template

```dart
Widget _buildRadioOption({
  required String title,
  required bool isSelected,
  required VoidCallback onTap,
  String? subtitle,
}) {
  return Pressable(
    onPressed: onTap,
    child: Container(
      padding: EdgeInsets.all(Space.md),
      decoration: ShapeDecoration(
        color: context.color.backgroundGrey,
        shape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(Rounded.xl),
          side: BorderSide(
            color: isSelected ? context.color.borderPrimary2 : context.color.borderDefault,
            width: isSelected ? 2 : 1,
          ),
        ),
      ),
      child: Row(
        children: [
          Container(
            width: 20,
            height: 20,
            decoration: BoxDecoration(
              shape: BoxShape.circle,
              border: Border.all(
                color: isSelected ? context.color.borderPrimary2 : context.color.borderDefault,
                width: 2,
              ),
            ),
            child: isSelected
                ? Center(
                    child: Container(
                      width: 10,
                      height: 10,
                      decoration: BoxDecoration(
                        shape: BoxShape.circle,
                        color: context.color.contentPrimary2,
                      ),
                    ),
                  )
                : null,
          ),
          SizedBox(width: Space.reg),
          Expanded(
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.start,
              children: [
                Text(title, style: context.font.body1.copyWith(color: context.color.contentPrimary)),
                if (subtitle != null) ...[
                  SizedBox(height: Space.xs),
                  Text(subtitle, style: context.font.body3.copyWith(color: context.color.contentTertiary)),
                ],
              ],
            ),
          ),
        ],
      ),
    ),
  );
}
```

## Loading State (ShimmerContainer Pattern)

```
ShimmerContainer
│
├── Loading State
│   └── ShimmerWidget / ShimmerCard
│
└── Content
    ├── Data State → ListView / GridView → ItemWidget
    ├── Error State → ErrorView
    └── Empty State → EmptyView
```

Rule: Loading is a **container concern**, not a screen concern.
MUST use `ShimmerContainer` with `showContent` as the single loading switch.

## Empty State Template

```dart
Widget _buildEmptyState({
  required String title,
  required String message,
  VoidCallback? onActionTap,
  String? actionLabel,
}) {
  return Center(
    child: Padding(
      padding: EdgeInsets.all(Space.xl),
      child: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: [
          Container(
            width: 80,
            height: 80,
            decoration: BoxDecoration(
              color: context.color.backgroundGrey,
              borderRadius: BorderRadius.circular(Rounded.xl),
            ),
            child: Icon(Icons.inbox_outlined, size: 40, color: context.color.contentTertiary),
          ),
          SizedBox(height: Space.lg),
          Text(title, style: context.font.h4.copyWith(color: context.color.contentPrimary), textAlign: TextAlign.center),
          SizedBox(height: Space.sm),
          Text(message, style: context.font.body2.copyWith(color: context.color.contentTertiary), textAlign: TextAlign.center),
          if (onActionTap != null && actionLabel != null) ...[
            SizedBox(height: Space.lg),
            CoreButton(label: actionLabel, onPressed: onActionTap),
          ],
        ],
      ),
    ),
  );
}
```
