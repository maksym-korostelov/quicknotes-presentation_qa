# Note Management

**Feature Owner:** Core Team  
**Last Updated:** 2025-01-15  
**Screens:** NoteListView, NoteDetailView, NoteEditorView, AddNoteView

---

## 1. Note List (NoteListView)

### 1.1 Display
- Shows ALL notes in a single scrollable list
- Each note row displays:
  - **Title** — truncated to 1 line if too long
  - **Content preview** — first ~2 lines of content, truncated with ellipsis
  - **Category badge** — emoji + name if the note has a category; hidden if uncategorized
  - **Date** — `modifiedAt` formatted relative to current date
  - **Pin indicator** — visual indicator if `isPinned` is true
  - **Color accent** — note's color displayed as a left border or subtle background tint

### 1.2 Sorting Rules
- **Pinned notes appear first** in a separate "Pinned" section
- Within each section, notes are sorted by `modifiedAt` **descending** (newest first)
- There is NO manual reordering

### 1.3 Empty State
- Displayed when there are zero notes in the system
- Icon: `note.text` (SF Symbol)
- Title: "No Notes Yet"
- Subtitle: "Tap + to create your first note"

### 1.4 Actions
- **Tap note row** → Navigate to NoteDetailView for that note
- **Swipe left on note row** → Reveals Delete action (red)
- **Delete swipe action** → Shows confirmation alert → deletes note permanently
- **"+" toolbar button** → Navigate to AddNoteView
- **Pull to refresh** → Reloads note list from data store

### 1.5 Business Rules
- Note list refreshes automatically when returning from NoteDetailView or AddNoteView
- Deleting a note from the list removes it immediately with animation
- If deletion fails, an error alert is shown and the note remains in the list

---

## 2. Note Detail (NoteDetailView)

### 2.1 Display
- Shows the full content of a single note:
  - **Title** — displayed prominently at the top
  - **Content** — full text, scrollable if longer than screen
  - **Category** — emoji + name badge (if assigned); "Uncategorized" label if no category
  - **Created date** — formatted with locale-appropriate date+time
  - **Modified date** — formatted with locale-appropriate date+time
  - **Color indicator** — note's color shown as header accent
  - **Pin status** — visual indicator (pin icon) if pinned

### 2.2 Actions
- **"Edit" toolbar button** → Navigate to NoteEditorView with this note's data pre-filled
- **"Delete" toolbar button** → Shows confirmation alert:
  - Title: "Delete Note"
  - Message: "Are you sure you want to delete this note? This action cannot be undone."
  - Buttons: "Cancel" (default), "Delete" (destructive)
  - On confirm → Delete note → Navigate back to NoteListView
- **"Pin/Unpin" button** → Toggles `isPinned` status immediately (no save confirmation needed)
- **Back navigation** → Returns to the previous list (NoteListView or SearchNotesView)

### 2.3 Business Rules
- Note content is **read-only** on this screen — editing requires navigating to NoteEditorView
- If the note is deleted by another process while viewing (edge case), navigating back shows the updated list
- Pin/Unpin toggle updates `modifiedAt` timestamp

---

## 3. Note Editor (NoteEditorView)

### 3.1 Purpose
- Edit an **existing** note's title, content, category, and color
- Pre-fills all fields with the note's current data

### 3.2 Form Fields

| Field | Type | Required | Validation |
|-------|------|----------|------------|
| Title | TextField | **YES** | 1–100 chars; trimmed; MUST NOT be empty/whitespace-only |
| Content | TextEditor (multiline) | No | 0–5,000 chars |
| Category | Picker | No | List of available categories + "None" option |
| Color | ColorPicker | No | Hex color; default preserved if unchanged |

### 3.3 Save Behavior
- **"Save" button** → Validates fields → Saves note → Navigates back to NoteDetailView
- On save, `modifiedAt` is updated to current timestamp
- On save, `createdAt` is **NOT** modified
- If title is empty/whitespace after trimming → Save button is **disabled** (not clickable)
- Save button is only enabled when there are unsaved changes AND title is valid

### 3.4 Cancel / Discard Behavior
- **"Cancel" button** → If there are unsaved changes:
  - Shows confirmation alert:
    - Title: "Discard Changes?"
    - Message: "You have unsaved changes. Are you sure you want to discard them?"
    - Buttons: "Keep Editing" (default), "Discard" (destructive)
  - On "Discard" → Navigate back without saving
- **"Cancel" button** → If NO unsaved changes → Navigate back immediately (no alert)

### 3.5 Business Rules
- Title is **trimmed** (leading/trailing whitespace removed) before validation and save
- Content is saved as-is (no trimming) to preserve intentional formatting
- Changing the category does NOT affect other notes in that category
- Changing the color is immediate in preview but only persists on Save
- If save fails → Error alert is shown → User stays on editor (data not lost)

### 3.6 Edge Cases
- Editing a note that was deleted externally → Save will fail with error
- Very long content (approaching 5,000 chars) → Character count is NOT displayed (no visual limit indicator in v1.0)
- Emoji in title → Allowed, counted as characters normally
- Special characters (quotes, backslash, HTML tags) → Allowed, stored as plain text, displayed as-is (no rendering)

---

## 4. Add Note (AddNoteView)

### 4.1 Purpose
- Create a **new** note from scratch
- Simpler interface than NoteEditorView — only title and content fields

### 4.2 Form Fields

| Field | Type | Required | Default Value |
|-------|------|----------|---------------|
| Title | TextField | **YES** | Empty string |
| Content | TextEditor (multiline) | No | Empty string |

> **Note:** AddNoteView does NOT include Category or Color pickers. New notes are created as Uncategorized with the default color. Category and color can be set later via NoteEditorView.

### 4.3 Save Behavior
- **"Save" button** → Validates title → Creates note → Navigates back to NoteListView
- New note gets:
  - Auto-generated UUID
  - `createdAt` = current timestamp
  - `modifiedAt` = current timestamp (same as createdAt on creation)
  - `categoryId` = nil (uncategorized)
  - `isPinned` = false
  - `color` = default color value
- Save button is **disabled** when title is empty/whitespace-only

### 4.4 Cancel Behavior
- Same discard confirmation logic as NoteEditorView (Section 3.4)
- If both title and content are empty → Navigate back immediately (no alert, nothing to lose)

### 4.5 Business Rules
- Title is trimmed before save
- Content is saved as-is
- After successful creation, the new note appears at the top of the Notes list (newest first)
- There is no "Quick Note" single-tap creation in v1.0 — all notes go through this form

---

## 5. Validation Rules Summary

| Rule ID | Field | Rule | Error Behavior |
|---------|-------|------|----------------|
| NV-001 | Title | MUST NOT be empty after trimming | Save button disabled |
| NV-002 | Title | MUST NOT exceed 100 characters | Not enforced in UI (no character counter) — behavior at 101+ chars is truncation at save |
| NV-003 | Content | MUST NOT exceed 5,000 characters | Not enforced in UI — behavior at 5,001+ chars is truncation at save |
| NV-004 | Title | MUST be trimmed (leading/trailing whitespace removed) before save | Automatic, not user-visible |
| NV-005 | CategoryId | If provided, MUST reference an existing category | Orphaned categoryId treated as nil (uncategorized) |

---

## 6. Acceptance Criteria

- [ ] User can view a list of all notes sorted by modification date
- [ ] Pinned notes appear in a separate section above unpinned notes
- [ ] User can tap a note to view its full content
- [ ] User can create a new note with title and content
- [ ] User cannot save a note with an empty title
- [ ] User can edit an existing note's title, content, category, and color
- [ ] User can delete a note with confirmation
- [ ] Deletion is permanent — no undo
- [ ] Note list refreshes after creation, editing, or deletion
- [ ] Empty state is shown when no notes exist
- [ ] User can pin/unpin notes from the detail view
- [ ] Cancel with unsaved changes shows a discard confirmation
