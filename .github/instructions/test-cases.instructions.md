---
applyTo: "**/*test-case*.md"
---

# Test Case Writing Instructions

## Format

Every test case must follow this structure:

```markdown
## TC-[ID]: [Brief Title]

**Priority:** P0 / P1 / P2 / P3
**Type:** Functional / UI / Performance / Security
**Preconditions:**
- [List all required setup]

**Steps:**
1. [Action verb] [specific action]
2. [Action verb] [specific action]
3. ...

**Expected Result:**
- [Specific, verifiable outcome]

**Test Data:**
- [Any specific data needed]
```

## Guidelines

### Titles
- Start with action verb: "Verify", "Validate", "Check", "Ensure"
- Be specific: "Verify note saves with 1000 characters" NOT "Test note saving"

### Steps
- One action per step
- Use specific values, not vague descriptions
- Include exact navigation path
- Number all steps sequentially

### Expected Results
- Must be objectively verifiable
- Include specific values/states where applicable
- Describe what user SEES, not internal behavior

### Priority Definitions

| Priority | Definition | Example |
|----------|------------|---------|
| P0 | Critical - Blocks release | App crash, data loss |
| P1 | High - Major feature broken | Cannot create notes |
| P2 | Medium - Feature degraded | Formatting issues |
| P3 | Low - Minor issues | Typos, minor UI glitches |

## Example Test Case

```markdown
## TC-101: Verify user can create a note with title and content

**Priority:** P1
**Type:** Functional
**Preconditions:**
- User is logged in
- User is on Note List screen
- No existing notes

**Steps:**
1. Tap the "+" button in the top right corner
2. Enter "Shopping List" in the Title field
3. Enter "Milk, Eggs, Bread" in the Content field
4. Tap "Save" button

**Expected Result:**
- Note List screen is displayed
- New note "Shopping List" appears at the top of the list
- Note shows preview text "Milk, Eggs, Bread"
- Note shows current date/time as creation time

**Test Data:**
- Title: "Shopping List"
- Content: "Milk, Eggs, Bread"
```