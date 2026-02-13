# Category Management

**Feature Owner:** Core Team  
**Last Updated:** 2025-01-15  
**Screens:** CategoryListView, CategoryEditorView

---

## 1. Category List (CategoryListView)

### 1.1 Display
- Shows ALL categories in a scrollable list
- Each category row displays:
  - **Emoji** — large emoji icon (displayed using system font for icon sizing, NOT app typography)
  - **Name** — category name, single line
  - **Note count** — number of notes assigned to this category (e.g., "5 notes")
  - **Color accent** — category's color shown as background tint or indicator

### 1.2 Sorting Rules
- Categories are sorted **alphabetically by name** (ascending, case-insensitive)
- There is NO manual reordering
- There is NO pinning for categories

### 1.3 Empty State
- Displayed when there are zero categories
- Icon: `folder` (SF Symbol)
- Title: "No Categories"
- Subtitle: "Create categories to organize your notes"

### 1.4 Actions
- **Tap category row** → Navigate to CategoryEditorView in **edit** mode (pre-fills existing data)
- **Swipe left on category row** → Reveals Delete action (red)
- **Delete swipe action** → Shows confirmation alert → deletes category permanently
- **"+" toolbar button** → Navigate to CategoryEditorView in **create** mode (empty form)

### 1.5 Category Deletion Rules

**This is a critical business rule that distinguishes a bug from a feature:**

- Deleting a category does **NOT** delete notes associated with it
- Notes that belonged to the deleted category become **uncategorized** (their `categoryId` is set to `nil`)
- Confirmation dialog:
  - Title: "Delete Category"
  - Message: "Are you sure you want to delete '{category name}'? Notes in this category will not be deleted but will become uncategorized."
  - Buttons: "Cancel" (default), "Delete" (destructive)
- After deletion, the category is removed from the list with animation
- The note count shown in the confirmation reflects the current count at the time of deletion

> **⚠️ Common Bug vs Feature Confusion:** QA engineers sometimes report "notes lost category after category deletion" as a bug. This is **intentional behavior** per this spec. Only report it as a bug if the notes themselves are deleted or if the notes' categoryId is NOT set to nil.

---

## 2. Category Editor (CategoryEditorView)

### 2.1 Purpose
- Create a **new** category OR edit an **existing** category
- Same screen handles both modes, differentiated by whether an existing category is passed in

### 2.2 Form Fields

| Field | Type | Required | Default (Create) | Validation |
|-------|------|----------|-------------------|------------|
| Name | TextField | **YES** | Empty string | 1–30 chars; trimmed; MUST NOT be empty/whitespace-only |
| Emoji | EmojiPicker / TextField | **YES** | "📁" | Single emoji character |
| Color | ColorPicker | **YES** | System-provided default | Valid hex color code |

### 2.3 Create Mode
- All fields start at default values
- Navigation title: "New Category"
- Save creates a new category with auto-generated UUID and current timestamp

### 2.4 Edit Mode
- Fields pre-filled with existing category data
- Navigation title: "Edit Category"
- Save updates the existing category (same UUID preserved)

### 2.5 Save Behavior
- **"Save" button** → Validates fields → Saves/updates category → Navigates back to CategoryListView
- Save button is **disabled** when name is empty/whitespace-only
- Name is trimmed before save
- Duplicate category names ARE allowed (no uniqueness constraint)

### 2.6 Cancel Behavior
- Same discard confirmation pattern as Note Editor:
  - Unsaved changes → Confirmation alert → "Keep Editing" / "Discard"
  - No changes → Navigate back immediately

### 2.7 Emoji Selection
- The emoji field accepts a single emoji character
- On iOS: System emoji keyboard is used for input
- On Android: Emoji keyboard or manual emoji input
- If user enters non-emoji text → Only the first character is used
- If user clears the field → Default emoji "📁" is used on save

---

## 3. Category–Note Association Rules

### 3.1 Assignment
- A note can belong to **at most one** category (not multiple)
- A category can have **unlimited** notes
- Assignment is done from the **NoteEditorView** (note editing screen), NOT from CategoryEditorView
- The category picker in NoteEditorView shows all available categories + a "None" / "Uncategorized" option

### 3.2 Reassignment
- Changing a note's category simply updates the `categoryId` field
- The old category's note count decreases; the new category's count increases
- No confirmation is needed for category reassignment

### 3.3 Orphaned References
- If a category is deleted while notes reference it, those notes' `categoryId` becomes `nil`
- The app handles this gracefully — orphaned references do NOT cause crashes or errors
- In the Note Detail view, a note with an orphaned categoryId shows as "Uncategorized"

---

## 4. Validation Rules Summary

| Rule ID | Field | Rule | Error Behavior |
|---------|-------|------|----------------|
| CV-001 | Name | MUST NOT be empty after trimming | Save button disabled |
| CV-002 | Name | MUST NOT exceed 30 characters | Not enforced in UI — truncated at save |
| CV-003 | Emoji | MUST contain at least one character | Default "📁" used if empty |
| CV-004 | Emoji | SHOULD be a single emoji character | First character used if multiple entered |
| CV-005 | Color | MUST be a valid hex color code | Default color used if invalid |
| CV-006 | Name | Duplicate names ARE allowed | No error — this is intentional |

---

## 5. Acceptance Criteria

- [ ] User can view a list of all categories sorted alphabetically
- [ ] Each category row shows emoji, name, and note count
- [ ] User can create a new category with name, emoji, and color
- [ ] User cannot save a category with an empty name
- [ ] User can edit an existing category's name, emoji, and color
- [ ] User can delete a category with confirmation
- [ ] Deleting a category does NOT delete associated notes
- [ ] Associated notes become uncategorized after category deletion
- [ ] Category list refreshes after creation, editing, or deletion
- [ ] Empty state is shown when no categories exist
- [ ] Cancel with unsaved changes shows discard confirmation
- [ ] Duplicate category names are allowed without error
