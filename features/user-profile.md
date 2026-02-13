# User Profile

**Feature Owner:** Core Team  
**Last Updated:** 2025-01-15  
**Screens:** ProfileView

---

## 1. Profile Screen (ProfileView)

### 1.1 Access
- Accessed from **SettingsView** → "Profile" row
- There is no direct tab for Profile — it is nested under Settings

### 1.2 Display

The Profile screen shows the following information:

| Section | Field | Source | Editable |
|---------|-------|--------|----------|
| Header | Avatar/Initials circle | Computed from displayName | No |
| Header | Display Name | UserProfile.displayName | No |
| Header | Email | UserProfile.email | No |
| Stats | Notes Count | Computed from actual notes in database | No |
| Stats | Categories Count | Computed from actual categories in database | No |
| Info | Member Since | UserProfile.memberSince, formatted | No |

### 1.3 Stats Computation
- **Notes Count** is computed dynamically — it reflects the **current** number of notes at the time the profile screen is loaded
- **Categories Count** is computed dynamically — same behavior
- Stats are **NOT** cached — they are fetched fresh on every screen appearance
- If the user creates/deletes notes on another screen and returns to Profile, the counts MUST be updated

### 1.4 Display Name Initials
- The avatar circle shows initials computed from `displayName`
- Algorithm: Take the first letter of the first word and the first letter of the second word (if any)
- Examples:
  - "Alex Johnson" → "AJ"
  - "Alex" → "A"
  - "" (empty) → Default placeholder icon

---

## 2. v1.0 Constraints

### 2.1 Hardcoded Demo Data

> **⚠️ Critical for QA:** In v1.0, the UserProfile is populated with **hardcoded demo data**. There is no authentication, no registration, and no profile editing.

The demo profile data is:

| Field | Value |
|-------|-------|
| displayName | "Alex Johnson" |
| email | "alex.johnson@example.com" |
| memberSince | Fixed date (see SeedData) |

### 2.2 What Is NOT Functional in v1.0

| Feature | Status | Notes |
|---------|--------|-------|
| Edit profile | ❌ Not implemented | No edit button or screen |
| Change avatar/photo | ❌ Not implemented | Initials only |
| Change email | ❌ Not implemented | Read-only display |
| Change password | ❌ Not implemented | No authentication system |
| Log out | ❌ Not implemented | No authentication system |
| Delete account | ❌ Not implemented | No authentication system |

> **⚠️ Bug Triage Note:** Any report about "cannot edit profile" or "logout button missing" is **Not a bug** — these are known v1.0 limitations. Only report profile-related bugs if: (1) displayed data is incorrect/malformed, (2) stats counts are wrong, (3) screen crashes, (4) navigation issues.

---

## 3. Acceptance Criteria

- [ ] Profile screen is accessible from Settings
- [ ] Display name is shown correctly
- [ ] Email is shown correctly
- [ ] Notes count reflects actual number of notes in the system
- [ ] Categories count reflects actual number of categories in the system
- [ ] Member since date is displayed in locale-appropriate format
- [ ] Initials circle shows correct initials from display name
- [ ] Stats update when returning to Profile after creating/deleting notes or categories
- [ ] Screen does NOT crash with empty data
