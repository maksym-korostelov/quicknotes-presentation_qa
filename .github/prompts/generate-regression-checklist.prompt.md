---
mode: "agent"
description: "Generate a regression checklist tailored to a specific change or release"
---

# Generate Regression Checklist

You are creating a quick regression checklist for the QuickNotes app.

## Context — Read These Files

1. `features/product-overview.md` — navigation structure, key screens
2. All feature files in `features/` — to understand full app scope
3. Existing test cases in `test-cases/` — to reference known coverage

## Input

The user will provide:
- **Trigger** — why is this regression needed? (e.g., "hotfix for emoji crash", "pre-release v1.3")
- **Platform** — iOS / Android / Both
- **Time budget** — how many minutes (e.g., "30 min", "1 hour")

## Generation Rules

### Prioritize by risk
1. **Critical Path** (always included) — Core user journeys that must never break:
   - App launches successfully
   - Create note → View → Edit → Delete lifecycle
   - Category CRUD lifecycle
   - Search finds notes by title and content
   - Settings accessible, preferences persist

2. **Affected Area** — Features most likely impacted by the trigger:
   - Use the feature files to understand feature boundaries
   - If trigger mentions "notes" → test note list, detail, editor, add note, AND search (it displays notes)
   - If trigger mentions "categories" → test categories AND note editor (category picker) AND note detail (category display) AND profile (category count)

3. **Smoke Checks** — Quick verification of unrelated features

### Scale to time budget
| Budget | Scope |
|--------|-------|
| 15 min | Critical Path only (5–8 items) |
| 30 min | Critical Path + Affected Area (12–18 items) |
| 1 hour | Full smoke across all features (25–35 items) |
| 2 hours | Full regression with edge cases (40+ items) |

### Checklist format
```markdown
## {Section Name}
- [ ] {Action} → {Expected result}
- [ ] {Action} → {Expected result}
```

### Cross-feature impact awareness
Use feature files to identify cross-feature dependencies:
- Deleting a category → check Notes list (uncategorized), Search results, Profile stats
- Delete All Data → check Notes, Categories, Search, Profile stats, Settings preferences
- Creating a note → check Notes list order, Search, Profile stats

## Output

Create at: `checklists/{trigger-slug}-regression-checklist.md`
