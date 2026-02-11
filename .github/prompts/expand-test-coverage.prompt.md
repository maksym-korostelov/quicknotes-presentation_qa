---
agent: "edit"
description: "Analyze existing test cases and add missing coverage based on feature specifications"
---

# Expand Test Coverage

You are reviewing an existing test case file and adding missing coverage based on the feature specification.

## Context — Read These Files

1. `.github/instructions/test-cases.instructions.md` — format and guidelines
2. The test case file provided by the user (current file in editor)
3. **The matching feature file** from `features/` — the authoritative source for what SHOULD be tested
4. `features/product-overview.md` — global business rules

## Analysis Process

### Step 1: Map existing test cases to Acceptance Criteria
Read the **Acceptance Criteria** section from the feature file. For each criterion, check if the existing test cases cover it.

### Step 2: Map existing test cases to Validation Rules
Read the **Validation Rules** table from the feature file. For each rule, check if there's a test case.

### Step 3: Map existing test cases to ⚠️ Warnings
Each ⚠️ "Bug vs Feature" warning represents a scenario QA might encounter. Check if there's a test case that explicitly verifies the correct (spec-defined) behavior.

### Step 4: Check coverage categories
- ✅/❌ Happy Path
- ✅/❌ Validation (from Validation Rules table)
- ✅/❌ Boundary Values (from Data Model constraints)
- ✅/❌ Negative Testing
- ✅/❌ State-Based (empty, full, after Delete All Data)
- ✅/❌ Interruption (backgrounding, navigation)
- ✅/❌ Cross-Platform (iOS/Android differences noted in spec)

### Step 5: Generate missing test cases

## Rules

- Continue the existing TC-ID numbering sequence
- Match the exact format and style of existing test cases
- Do NOT duplicate existing coverage
- Reference Rule IDs and spec sections in new test cases
- Add new cases at the END of the file with a section header:

```markdown
---

## Additional Coverage (Spec-Based Expansion)

**Source:** `features/{file}.md`
**Coverage gaps identified:** {list}

### {Category}: {Description}
```

- Include a Coverage Analysis summary at the top of the additions
