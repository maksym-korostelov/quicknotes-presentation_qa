# QuickNotes — Feature Descriptions

This directory serves as the **single source of truth** for QuickNotes feature requirements and business rules. It replaces Confluence for Copilot-assisted test case generation, bug triage, and coverage analysis.

## Why This Exists

In a real project, these specifications would live in Confluence, Notion, or Jira. However:
- Copilot cannot access Confluence (no MCP integration available)
- QA engineers need precise business rules to determine if something is a **bug or a feature**
- Test case generators need exact validation rules, boundary values, and expected behaviors
- Without this context, Copilot invents plausible-sounding rules that may be **wrong**

## Structure

| File | Scope |
|------|-------|
| `product-overview.md` | App-level context: user roles, platforms, navigation structure |
| `note-management.md` | Notes CRUD: creation, editing, viewing, deletion, listing |
| `category-management.md` | Categories CRUD: creation, editing, deletion, note association |
| `search.md` | Search functionality: query behavior, results display, filtering |
| `user-profile.md` | Profile screen: display, statistics, membership info |
| `settings.md` | App settings: theme, notifications, data management |
| `onboarding.md` | First-launch experience: feature highlights, skip/complete flow |
| `informational-screens.md` | About screen, Help screen: static content, navigation, links |

## How to Use These Files

### With Copilot Prompts
Prompt files in `.github/prompts/` reference these feature descriptions automatically. When you run a prompt like `generate-test-cases`, it reads the relevant feature file to understand exact business rules.

### For Bug Triage
Before filing a bug, check the relevant feature file:
- Is the behavior described as intentional? → **Not a bug**
- Does it contradict a stated rule? → **Bug — reference the rule in your report**
- Is the behavior not mentioned at all? → **Check with the team, may need a spec update**

### For Test Case Writing
Each feature file contains:
- **Acceptance criteria** — what "done" looks like
- **Business rules** — exact validation rules, limits, behaviors
- **Edge cases & known constraints** — things that are intentionally limited
- **UI behavior** — what the user sees, confirmation dialogs, empty states

## Keeping These Files Updated

| When | Action |
|------|--------|
| New feature starts development | PM/QA adds feature description BEFORE testing begins |
| Requirement changes during sprint | Update the relevant feature file + add `[Updated: date]` tag |
| Bug reveals undocumented behavior | Add the clarification to the feature file after team decision |
| Feature is deprecated/removed | Move to `features/archive/` with deprecation note |

## Document Conventions

- **MUST / MUST NOT** — Hard requirements, violation = bug
- **SHOULD / SHOULD NOT** — Strong recommendations, violation = minor issue
- **MAY** — Optional behavior, not a bug either way
- `[Platform: iOS]` / `[Platform: Android]` — Platform-specific behavior
- `[User: Free]` / `[User: Premium]` / `[User: Guest]` — User-role-specific behavior
- `→` — Indicates expected result or navigation outcome
