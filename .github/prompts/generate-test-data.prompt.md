---
mode: "agent"
description: "Generate test data for a feature based on its specification and validation rules"
---

# Generate Test Data for Feature

You are generating structured test data for manual and automated testing of QuickNotes.

## Context — ALWAYS Read These Files First

1. `features/product-overview.md` — Data Model tables with field types, constraints, defaults
2. `.github/instructions/test-data.instructions.md` — test data format guidelines
3. **The relevant feature file** from `features/` — Validation Rules tables with Rule IDs
4. `test-data/note-creation-test-data.md` — example of expected output format

## Input

The user will provide:
- **Feature name** (e.g., "Note Editing", "Categories", "Search")

## Data Generation Rules

### Derive ALL boundary values from the spec

Read the Data Model in `features/product-overview.md` and Validation Rules in the feature file. Generate data for:

| Category | Source | Count |
|----------|--------|-------|
| Valid data | Realistic entries within spec constraints | 4–6 |
| Boundary values | Exact min/max from Data Model (e.g., title: 1 char, 100 chars) | 4–6 |
| Invalid data (negative) | Values violating Validation Rules (reference Rule IDs) | 4–6 |
| Edge cases | Unicode, emoji, special chars, XSS, SQL injection | 4–6 |
| State scenarios | Empty DB, max items, after Delete All Data | 2–3 |

### For each test data entry, include:
```json
{
  "id": "valid-uuid-format",
  "description": "What this data tests",
  "validatesRule": "NV-001",
  "data": { ... },
  "expectedOutcome": "accepted" | "rejected",
  "expectedError": "Error message if rejected"
}
```

### Data Format
- Use JSON code blocks
- UUID format: `{8}-{4}-{4}-{4}-{12}`
- Dates: ISO 8601 `2026-01-15T10:30:00Z`
- Emails: `testuser+{scenario}@quicknotes.test`

## Output

Create at: `test-data/{feature-slug}-test-data.md`
