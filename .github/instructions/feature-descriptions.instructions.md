---
applyTo: "**"
---

# Feature Descriptions Reference

The `features/` directory contains the authoritative feature specifications for the QuickNotes application. These files serve as the **single source of truth** for expected app behavior, replacing Confluence documentation.

## Available Feature Files

| File | Coverage |
|------|----------|
| `features/product-overview.md` | User roles, platforms, navigation, data model, global rules |
| `features/note-management.md` | Note CRUD: list, detail, editor, add note |
| `features/category-management.md` | Category CRUD: list, editor, note association rules |
| `features/search.md` | Search behavior, matching rules, result display |
| `features/user-profile.md` | Profile display, stats computation, v1.0 constraints |
| `features/settings.md` | Preferences, data management, navigation |
| `features/onboarding.md` | First-launch experience, persistence rules |
| `features/informational-screens.md` | About screen, Help screen, FAQ content |

## How to Use Feature Files

### When generating test cases:
- ALWAYS read the relevant feature file(s) before generating test cases
- Use the **Acceptance Criteria** section as the minimum test coverage
- Use the **Business Rules** sections for edge case and validation test cases
- Use the **"Bug vs Feature" warnings** (⚠️) to avoid false bug reports

### When writing or triaging bug reports:
- Check if the reported behavior is documented as intentional in the feature file
- Reference specific rule IDs (e.g., NV-001, CV-003, SV-002) in bug reports
- If behavior contradicts a feature file → it's a bug
- If behavior is not mentioned in any feature file → escalate for spec clarification

### When creating test data:
- Use the **Data Model** tables in `product-overview.md` for field types, constraints, and defaults
- Use the **Validation Rules** tables in each feature file for boundary values
- Reference specific Rule IDs in test data comments

## Key Business Rules to Remember

- All deletions are permanent (no trash/undo)
- Delete actions always require confirmation dialogs
- Title fields are trimmed before validation (leading/trailing whitespace removed)
- Content fields are NOT trimmed (preserves formatting)
- Category deletion does NOT delete associated notes (they become uncategorized)
- Search matches title AND content, but NOT category names
- UserProfile is hardcoded demo data in v1.0 (not editable)
- Onboarding shows only on first launch, never again (even after "Delete All Data")
