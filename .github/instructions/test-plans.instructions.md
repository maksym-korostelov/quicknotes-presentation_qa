---
applyTo: "**/*test-plan*.md"
---

# Test Plan Instructions

## Format

```markdown
# Test Plan: [Feature/Release Name]

## Overview
**Release:** [Version]
**Feature:** [Feature name]
**QA Owner:** [Name]
**Dev Contact:** [Name]
**Test Period:** [Start] - [End]

## Scope

### In Scope
- [Feature/Area 1]
- [Feature/Area 2]

### Out of Scope
- [Feature/Area explicitly not tested]

## Test Strategy

### Test Types
| Type | Coverage |
|------|----------|
| Functional | [X test cases] |
| Regression | [X test cases] |
| UI/UX | [X test cases] |
| Performance | [X test cases] |
| Security | [X test cases] |

### Environments
- [ ] DEV
- [ ] QA
- [ ] STAGING

### Devices/Browsers
- [ ] iPhone 15 Pro (iOS 17)
- [ ] iPhone SE (iOS 17)
- [ ] Pixel 8 (Android 14)
- [ ] Samsung S24 (Android 14)

## Test Cases

### [Area 1: e.g., Note Creation]
| TC ID | Title | Priority | Status |
|-------|-------|----------|--------|
| TC-101 | Create note with title and content | P1 | ⬜ |
| TC-102 | Create note with empty title | P2 | ⬜ |

### [Area 2: e.g., Note Editing]
| TC ID | Title | Priority | Status |
|-------|-------|----------|--------|

## Entry Criteria
- [ ] Feature code complete
- [ ] DEV testing passed
- [ ] Test environment available
- [ ] Test data prepared

## Exit Criteria
- [ ] All P0/P1 test cases passed
- [ ] No Critical/Major open bugs
- [ ] P2 test cases: 95% passed
- [ ] Performance benchmarks met

## Risks & Mitigations

| Risk | Impact | Mitigation |
|------|--------|------------|
| [Risk 1] | [High/Med/Low] | [Mitigation plan] |

## Sign-off

| Role | Name | Date | Signature |
|------|------|------|-----------|
| QA Lead | | | |
| Dev Lead | | | |
| PM | | | |
```