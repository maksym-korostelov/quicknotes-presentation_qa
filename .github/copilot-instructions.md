# QuickNotes - QA Instructions

## Project Overview

QuickNotes is an iOS/Android notes application allowing users to create, edit, organize, and delete personal notes.

- **Platforms:** iOS 17+, Android 14+
- **Key Features:** Note CRUD, Categories, Search, Sync
- **Backend:** REST API
- **Test Management:** Jira / TestRail

## Application Terminology

| Term | Definition |
|------|------------|
| Note | A single text entry with title, content, timestamps |
| Category | A grouping/folder for organizing notes |
| Quick Note | A note created without a title (auto-generated) |
| Sync | Cloud synchronization of notes across devices |

## User Roles

| Role | Description |
|------|-------------|
| Guest | Unauthenticated user, local storage only |
| Free User | Authenticated, limited to 50 notes |
| Premium User | Authenticated, unlimited notes, sync enabled |

## Key Screens

1. **Note List** - Main screen showing all notes
2. **Note Detail** - View/edit single note
3. **Categories** - Manage note categories
4. **Settings** - User preferences, account management
5. **Search** - Search notes by title/content

## Testing Environments

| Environment | URL / Build |
|-------------|-------------|
| DEV | dev.quicknotes.app |
| QA | qa.quicknotes.app |
| STAGING | staging.quicknotes.app |
| PROD | quicknotes.app |
