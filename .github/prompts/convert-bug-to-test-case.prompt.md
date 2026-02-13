---
agent: "agent"
description: "Convert a resolved bug report into a permanent regression test case"
---

# Convert Bug to Regression Test Case

You are converting a fixed bug report into a permanent regression test case.

## Context — Read These Files

1. `.github/instructions/test-cases.instructions.md` — test case format
2. The bug report file specified by the user (from `bug-reports/`)
3. **The relevant feature file** from `features/` — to understand the correct expected behavior

## Conversion Rules

1. **Extract reproduction steps** from the bug report → these become the test Steps
2. **Expected Result** = the CORRECT behavior (per feature spec), NOT the bug behavior
3. **Reference the bug:**
   ```markdown
   **Regression for:** [BUG] {original bug title}
   **Bug file:** `bug-reports/{filename}`
   **Original behavior:** {what the bug was}
   **Spec reference:** `features/{file}.md`, Section {N}
   ```
4. **Priority:** At least P2 (regressions of Critical/Major bugs → P1)
5. **Type:** Regression
6. **Add variations** — If the bug was about emoji, test with multiple emoji types. If about length, test at exact boundary.
7. **Verify against spec** — The expected behavior in the regression test MUST match the feature file

## Output

Append the new test case(s) to the appropriate file in `test-cases/`, or create a new file if none exists for that feature area.
