# Note Creation - Test Cases

## TC-001: Verify user can create a note with title and content

**Priority:** P1
**Type:** Functional
**Preconditions:**
- User is logged in
- User is on Note List screen
- No existing notes with title "Meeting Notes"

**Steps:**
1. Tap the "+" button in the top right corner
2. Enter "Meeting Notes" in the Title field
3. Enter "Discuss Q1 budget and team planning" in the Content field
4. Tap "Save" button

**Expected Result:**
- Note List screen is displayed
- New note "Meeting Notes" appears in the list
- Note shows preview text "Discuss Q1 budget and team planning"
- Note displays current date/time as creation timestamp
- Success message confirms note was saved

**Test Data:**
- Title: "Meeting Notes"
- Content: "Discuss Q1 budget and team planning"

---

## TC-002: Verify user can create a note with title only (no content)

**Priority:** P1
**Type:** Functional
**Preconditions:**
- User is logged in
- User is on Note List screen

**Steps:**
1. Tap the "+" button
2. Enter "Quick Reminder" in the Title field
3. Leave the Content field empty
4. Tap "Save" button

**Expected Result:**
- Note List screen is displayed
- New note "Quick Reminder" appears in the list
- Note shows no preview text or displays placeholder text
- Note displays current date/time as creation timestamp
- Success message confirms note was saved

**Test Data:**
- Title: "Quick Reminder"
- Content: (empty)

---

## TC-003: Verify note title accepts maximum character limit (100 chars)

**Priority:** P2
**Type:** Functional
**Preconditions:**
- User is logged in
- User is on Note List screen

**Steps:**
1. Tap the "+" button
2. Enter exactly 100 characters in the Title field: "This is a very long title that contains exactly one hundred characters to test the maximum limit allowed"
3. Enter "Test content" in the Content field
4. Tap "Save" button

**Expected Result:**
- Note is saved successfully
- Full 100-character title is displayed in Note List
- Note displays current date/time as creation timestamp
- No error or warning messages appear

**Test Data:**
- Title: "This is a very long title that contains exactly one hundred characters to test the maximum limit allowed" (100 chars)
- Content: "Test content"

---

## TC-004: Verify note content accepts maximum character limit (5000 chars)

**Priority:** P2
**Type:** Functional
**Preconditions:**
- User is logged in
- User is on Note List screen

**Steps:**
1. Tap the "+" button
2. Enter "Long Content Test" in the Title field
3. Enter exactly 5000 characters in the Content field (use repeated text to reach limit)
4. Tap "Save" button

**Expected Result:**
- Note is saved successfully
- Note "Long Content Test" appears in the list
- Full 5000-character content is preserved
- Note displays current date/time as creation timestamp
- No error or warning messages appear

**Test Data:**
- Title: "Long Content Test"
- Content: [5000 characters of text]

---

## TC-005: Verify validation error when title is empty

**Priority:** P1
**Type:** Functional
**Preconditions:**
- User is logged in
- User is on Note List screen

**Steps:**
1. Tap the "+" button
2. Leave the Title field empty
3. Enter "Some content here" in the Content field
4. Tap "Save" button

**Expected Result:**
- Note is NOT saved
- User remains on Note Detail screen
- Error message displays: "Title is required"
- Title field is highlighted or marked with error indicator
- No new note appears in Note List

**Test Data:**
- Title: (empty)
- Content: "Some content here"

---

## TC-006: Verify title cannot exceed 100 characters

**Priority:** P2
**Type:** Functional
**Preconditions:**
- User is logged in
- User is on Note List screen

**Steps:**
1. Tap the "+" button
2. Attempt to enter 101 characters in the Title field: "This is a very long title that contains one hundred and one characters to test exceeding the maximum limit"
3. Enter "Test content" in the Content field
4. Tap "Save" button

**Expected Result:**
- Either: Title field prevents input after 100 characters (character counter shows 100/100)
- Or: Error message displays: "Title cannot exceed 100 characters"
- Note is NOT saved if validation occurs on save
- User remains on Note Detail screen if validation fails

**Test Data:**
- Title: "This is a very long title that contains one hundred and one characters to test exceeding the maximum limit" (101 chars)
- Content: "Test content"

---

## TC-007: Verify content cannot exceed 5000 characters

**Priority:** P2
**Type:** Functional
**Preconditions:**
- User is logged in
- User is on Note List screen

**Steps:**
1. Tap the "+" button
2. Enter "Content Limit Test" in the Title field
3. Attempt to enter 5001 characters in the Content field
4. Tap "Save" button

**Expected Result:**
- Either: Content field prevents input after 5000 characters (character counter shows 5000/5000)
- Or: Error message displays: "Content cannot exceed 5000 characters"
- Note is NOT saved if validation occurs on save
- User remains on Note Detail screen if validation fails

**Test Data:**
- Title: "Content Limit Test"
- Content: [5001 characters of text]

---

## TC-008: Verify creation timestamp is accurate when note is saved

**Priority:** P1
**Type:** Functional
**Preconditions:**
- User is logged in
- User is on Note List screen
- Device time is accurate and synchronized

**Steps:**
1. Note the current system time (e.g., 2:30 PM)
2. Tap the "+" button
3. Enter "Timestamp Test" in the Title field
4. Enter "Verifying timestamp accuracy" in the Content field
5. Tap "Save" button immediately
6. View the note in Note List and check the creation timestamp

**Expected Result:**
- Note is saved successfully
- Creation timestamp matches current system time (within 1-2 seconds)
- Timestamp format follows app standard (e.g., "Feb 6, 2026 at 2:30 PM")
- Timestamp does not change on subsequent views

**Test Data:**
- Title: "Timestamp Test"
- Content: "Verifying timestamp accuracy"

---

## TC-009: Verify title accepts special characters and unicode

**Priority:** P2
**Type:** Functional
**Preconditions:**
- User is logged in
- User is on Note List screen

**Steps:**
1. Tap the "+" button
2. Enter "Test @#$% & Émojis 🎉📝 中文" in the Title field
3. Enter "Special character test" in the Content field
4. Tap "Save" button

**Expected Result:**
- Note is saved successfully
- Title displays correctly with all special characters and emojis preserved
- Note appears in Note List with full title visible
- No encoding or display issues occur

**Test Data:**
- Title: "Test @#$% & Émojis 🎉📝 中文"
- Content: "Special character test"

---

## TC-010: Verify content accepts special characters and unicode

**Priority:** P2
**Type:** Functional
**Preconditions:**
- User is logged in
- User is on Note List screen

**Steps:**
1. Tap the "+" button
2. Enter "Special Content Test" in the Title field
3. Enter multi-line content with special characters: "Line 1: Hello @user!\nLine 2: Price: $99.99\nLine 3: Émojis: 🎉🎊\nLine 4: 中文测试\nLine 5: Code: <html>&nbsp;</html>"
4. Tap "Save" button

**Expected Result:**
- Note is saved successfully
- All content is preserved including line breaks, special characters, and unicode
- Content displays correctly when note is reopened
- No encoding or display issues occur

**Test Data:**
- Title: "Special Content Test"
- Content: "Line 1: Hello @user!\nLine 2: Price: $99.99\nLine 3: Émojis: 🎉🎊\nLine 4: 中文测试\nLine 5: Code: <html>&nbsp;</html>"

---

## TC-011: Verify cancel action does not save note

**Priority:** P1
**Type:** Functional
**Preconditions:**
- User is logged in
- User is on Note List screen

**Steps:**
1. Tap the "+" button
2. Enter "Cancelled Note" in the Title field
3. Enter "This should not be saved" in the Content field
4. Tap "Cancel" or "Back" button

**Expected Result:**
- Note Detail screen closes
- User returns to Note List screen
- No new note is created or saved
- Note List remains unchanged from before step 1

**Test Data:**
- Title: "Cancelled Note"
- Content: "This should not be saved"

---

## TC-012: Verify note creation with only whitespace in title fails validation

**Priority:** P2
**Type:** Functional
**Preconditions:**
- User is logged in
- User is on Note List screen

**Steps:**
1. Tap the "+" button
2. Enter only spaces/whitespace in the Title field (e.g., "     ")
3. Enter "Content text" in the Content field
4. Tap "Save" button

**Expected Result:**
- Note is NOT saved
- Error message displays: "Title is required" or "Title cannot be empty"
- Title field is highlighted or marked with error indicator
- User remains on Note Detail screen

**Test Data:**
- Title: "     " (whitespace only)
- Content: "Content text"

---

## TC-013: Verify multiple notes can be created in sequence

**Priority:** P1
**Type:** Functional
**Preconditions:**
- User is logged in
- User is on Note List screen

**Steps:**
1. Tap the "+" button
2. Create first note with title "Note 1" and content "First note"
3. Tap "Save" button
4. Tap the "+" button again
5. Create second note with title "Note 2" and content "Second note"
6. Tap "Save" button
7. Tap the "+" button again
8. Create third note with title "Note 3" and content "Third note"
9. Tap "Save" button

**Expected Result:**
- All three notes are saved successfully
- Note List displays all three notes
- Each note has unique creation timestamp
- Notes are ordered by creation time (newest first or as per app default)
- Each note preserves its unique title and content

**Test Data:**
- Note 1: Title: "Note 1", Content: "First note"
- Note 2: Title: "Note 2", Content: "Second note"
- Note 3: Title: "Note 3", Content: "Third note"
