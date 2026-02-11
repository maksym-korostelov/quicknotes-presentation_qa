---
agent: "agent"
description: "Generate a test plan for a release or feature based on feature specifications"
---

# Generate Test Plan

You are a QA Lead creating a comprehensive test plan.

## Context — Read These Files

1. `.github/copilot-instructions.md` — project overview, environments, devices
2. `.github/instructions/test-plans.instructions.md` — test plan format
3. `features/product-overview.md` — full feature inventory and global rules
4. **All relevant feature files** from `features/` — for the features in scope
5. Scan `test-cases/` — list existing test case files

## Input

The user will provide:
- **Release version** or **Feature name**
- **Scope** (which features/areas are included)
- **Timeline** (optional)
- **Special concerns** (optional)

## Generation Rules

### Scope Definition
- List all features in scope with references to their feature files
- For each feature, note the number of Acceptance Criteria and Validation Rules

### Test Coverage Mapping
For each feature in scope:

| Feature | Spec File | Acceptance Criteria | Validation Rules | Existing Test Cases | Gap |
|---------|-----------|--------------------|--------------------|--------------------|----- |
| {name} | `features/{file}` | {count} | {count} | {file or "None"} | {Yes/No} |

### Risk Assessment
- Use ⚠️ warnings from feature files as risk indicators
- Features with many validation rules = higher risk
- Features with cross-feature dependencies = higher risk
- New/changed features = higher risk than stable features

### Entry Criteria
- All feature specification files in `features/` are up to date
- Test cases exist for all in-scope features
- Test data is generated for all in-scope features

### Exit Criteria
- 100% of P0/P1 test cases passed
- 95% of P2 test cases passed
- No open Critical or Major bugs
- All Acceptance Criteria verified

## Output

Create at: `test-plans/{identifier}-test-plan.md`
