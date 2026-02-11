---
applyTo: "**/*bug*.md"
---

# Bug Report Instructions

## Format

Every bug report must follow this structure:

```markdown
## [BUG] [Brief Description]

**Severity:** Critical / Major / Minor / Trivial
**Priority:** P0 / P1 / P2 / P3
**Environment:** [DEV / QA / STAGING / PROD]
**Platform:** [iOS X.X / Android X.X]
**Device:** [Device model]
**App Version:** [X.X.X (build)]

### Description
[Clear, concise description of the issue]

### Steps to Reproduce
1. [Exact step]
2. [Exact step]
3. ...

### Actual Result
[What actually happened]

### Expected Result
[What should have happened]

### Evidence
- Screenshot: [link]
- Video: [link]
- Logs: [link or attached]

### Additional Context
[Any relevant information: frequency, workarounds, related issues]
```

## Guidelines

### Titles
- Be specific and searchable
- Include affected feature: "[BUG] Note Editor - Text formatting lost on save"
- Avoid vague titles: "App doesn't work" ❌

### Severity Definitions

| Severity | Definition | Example |
|----------|------------|---------|
| Critical | App unusable, data loss, security issue | Crash on launch, notes deleted |
| Major | Feature broken, no workaround | Cannot save notes |
| Minor | Feature degraded, workaround exists | Save requires double-tap |
| Trivial | Cosmetic, no functional impact | Button slightly misaligned |

### Steps to Reproduce
- Start from a known state (e.g., "Fresh install", "Logged in as free user")
- Include exact data entered
- One action per step
- Must be reproducible by others

### Evidence Requirements
- **Critical/Major:** Screenshot + Video required
- **Minor:** Screenshot required
- **Trivial:** Screenshot optional

## Example Bug Report

```markdown
## [BUG] Note Editor - Content lost when switching apps during edit

**Severity:** Major
**Priority:** P1
**Environment:** QA
**Platform:** iOS 17.4
**Device:** iPhone 15 Pro
**App Version:** 1.2.3 (456)

### Description
When editing a note and switching to another app, then returning, all unsaved changes are lost without warning.

### Steps to Reproduce
1. Open QuickNotes app
2. Tap on existing note "Shopping List"
3. Add text "Butter, Cheese" to the content
4. Press Home button to go to iOS home screen
5. Wait 30 seconds
6. Return to QuickNotes app

### Actual Result
- Note content reverts to previous saved state
- Added text "Butter, Cheese" is gone
- No warning or auto-save occurred

### Expected Result
- Either: Changes are auto-saved as draft
- Or: User is warned about unsaved changes
- Added text should be preserved

### Evidence
- Screenshot: [link to before/after images]
- Video: [link to screen recording]
- Logs: See attached crash_log_2024.txt

### Additional Context
- Reproducible 100% of the time
- Also occurs on iPad
- Workaround: Manually tap Save before switching apps
- May be related to: JIRA-1234 (background handling)
```