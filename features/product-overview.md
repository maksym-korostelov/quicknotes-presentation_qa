# QuickNotes — Product Overview

**Version:** 1.0  
**Last Updated:** 2025-01-15  
**Status:** In Development

---

## 1. Product Description

QuickNotes is a cross-platform mobile application for creating, organizing, and managing personal notes. It targets iOS and Android platforms with native implementations sharing the same architecture and feature set.

### 1.1 Supported Platforms

| Platform | Minimum Version | Framework |
|----------|----------------|-----------|
| iOS | 17.0+ | SwiftUI |
| Android | 14+ (API 34) | Jetpack Compose |

### 1.2 App Version Info

| Field | Value |
|-------|-------|
| Current Version | 1.0.0 |
| Build | Incremented per release |
| Display Format | "Version X.Y.Z (Build N)" on About screen |

---

## 2. User Roles & Permissions

### 2.1 Guest User
- No authentication required
- Full access to all local features (notes, categories, search)
- Data stored locally on device only
- No sync capability
- No note limit
- **This is the default and current mode** — v1.0 does not implement authentication

### 2.2 Free User (Future — v2.0)
- Email-based authentication
- Maximum **50 notes** — enforcement at save time
- Basic sync across devices (manual)
- Standard support

### 2.3 Premium User (Future — v2.0)
- All Free features
- **Unlimited notes**
- Automatic real-time sync
- Priority support
- Advanced features (TBD)

> **⚠️ For v1.0 Testing:** All users are effectively Guest users. Free/Premium distinctions are documented for future reference but MUST NOT be tested as current functionality. The Profile screen shows hardcoded demo data.

---

## 3. Navigation Structure

### 3.1 Main Tab Bar

The app uses a tab-based navigation with 4 tabs:

| Tab | Icon | Screen | Description |
|-----|------|--------|-------------|
| Notes | `note.text` | NoteListView | Primary screen — list of all notes |
| Categories | `folder` | CategoryListView | Category management |
| Search | `magnifyingglass` | SearchNotesView | Full-text search across notes |
| Settings | `gearshape` | SettingsView | App preferences and navigation hub |

### 3.2 Navigation Flows

```
Notes Tab:
  NoteListView → NoteDetailView → NoteEditorView
  NoteListView → AddNoteView (via + button)

Categories Tab:
  CategoryListView → CategoryEditorView (new)
  CategoryListView → CategoryEditorView (edit existing)

Search Tab:
  SearchNotesView → NoteDetailView → NoteEditorView

Settings Tab:
  SettingsView → ProfileView
  SettingsView → AboutView
  SettingsView → HelpView
```

### 3.3 First Launch

On first app launch, the OnboardingView is displayed INSTEAD of the main tab bar. After completing or skipping onboarding, the user sees the main tab bar and onboarding is never shown again.

---

## 4. Data Model Summary

### 4.1 Note

| Field | Type | Required | Constraints |
|-------|------|----------|-------------|
| id | UUID | Auto-generated | Unique identifier |
| title | String | **YES** | 1–100 characters; MUST NOT be empty or whitespace-only |
| content | String | No | 0–5,000 characters; empty string is valid |
| createdAt | Date | Auto-generated | Set on creation, never changes |
| modifiedAt | Date | Auto-generated | Updated on every save |
| categoryId | UUID? | No | Reference to a Category; `nil` = uncategorized |
| isPinned | Bool | No | Default: `false` |
| color | String | No | Hex color code (e.g., "#FF5733"); default provided |

### 4.2 Category

| Field | Type | Required | Constraints |
|-------|------|----------|-------------|
| id | UUID | Auto-generated | Unique identifier |
| name | String | **YES** | 1–30 characters; MUST NOT be empty or whitespace-only |
| emoji | String | **YES** | Single emoji character; default: "📁" |
| color | String | **YES** | Hex color code; default provided |
| createdAt | Date | Auto-generated | Set on creation |

### 4.3 UserProfile

| Field | Type | Required | Notes |
|-------|------|----------|-------|
| id | UUID | Auto-generated | Unique identifier |
| displayName | String | YES | User's display name |
| email | String | YES | Email address |
| memberSince | Date | Auto-generated | Registration date |
| notesCount | Int | Computed | Total notes created |
| categoriesCount | Int | Computed | Total categories created |

> **⚠️ v1.0 Note:** UserProfile is populated with hardcoded demo data. There is no authentication or user management. The Profile screen is read-only.

---

## 5. Global Business Rules

### 5.1 Data Persistence
- All data is stored locally on device
- Data persists across app launches
- No cloud sync in v1.0
- No data export/import in v1.0

### 5.2 Sorting
- Notes list: **Pinned notes first**, then sorted by `modifiedAt` descending (newest first)
- Categories list: Sorted by `name` ascending (alphabetical)
- Search results: Sorted by relevance (matching in title ranks higher than content)

### 5.3 Deletion
- All deletions are **permanent** — there is no trash/recycle bin
- Delete actions MUST show a confirmation dialog before proceeding
- After deletion, user is navigated back to the list view

### 5.4 Timestamps
- All dates are stored in UTC
- Display format adapts to user's locale
- "Modified" date updates on every save, even if no content changed
- "Created" date never changes after initial creation

### 5.5 Error Handling
- Errors from data operations display as user-facing alerts
- Error alerts have a single "OK" dismiss button
- Error state does NOT navigate away from current screen

### 5.6 Empty States
- Every list screen (Notes, Categories, Search Results) MUST show an empty state view when there are no items
- Empty states include an icon, a title, and a descriptive subtitle
- Empty states do NOT include action buttons (e.g., no "Create your first note" button in v1.0)
