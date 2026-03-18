# File Structure

Every screen MUST follow the standard folder layout with sections split into separate files.

---

## Screen Folder Structure

```
lib/screen/<screen_name>/
├── <screen_name>.dart          ← Main screen file (composer)
└── section/
    ├── index.dart              ← Export all sections
    ├── header_section.dart     ← Section 1
    ├── content_section.dart    ← Section 2
    └── action_section.dart     ← Section 3
```

## Rules

- Screen file is responsible only for **layout composition** and ordering
- One section = one file
- Sections are exported via `section/index.dart`
- Files MUST be under **500 LOC**
- MUST split files by responsibility when exceeded

## What Goes Where

| Use Case        | Location                                   |
| --------------- | ------------------------------------------ |
| Reusable widget | `lib/core/widget/`                         |
| Screen section  | `lib/screen/<screen>/section/`             |
| Core model/mock | `lib/core/model/` & `lib/core/model/mock/` |
| API service     | `lib/app/service/`                         |
| API model       | `lib/app/model/`                           |

## Forbidden

- Placing reusable widgets inside screen folders
- Placing sections outside the `section/` directory
- Mixing models and mock data
- Hardcoded dummy data inside UI
- Large files without proper splitting
