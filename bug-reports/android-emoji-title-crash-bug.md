# Bug Reports

## [BUG] Note Editor - App crashes when saving note with emoji in title

**Severity:** Critical
**Priority:** P0
**Environment:** QA
**Platform:** Android 14
**Device:** Pixel 8
**App Version:** 1.2.3 (build TBD)

### Description
The application crashes immediately when attempting to save a note that contains an emoji character in the title field. The crash occurs on Android 14 devices.

### Steps to Reproduce
1. Open QuickNotes app on Pixel 8 (Android 14)
2. Tap "Create New Note" button
3. Enter a title with an emoji, e.g., "Shopping List 🛒"
4. Enter any content in the note body
5. Tap "Save" button

### Actual Result
- App crashes immediately upon tapping Save
- User is returned to device home screen
- Note is not saved
- No error message displayed

### Expected Result
- Note should save successfully with emoji in title
- User should remain in the app
- Note should appear in the note list with emoji displayed correctly

### Evidence
- Screenshot: [Pending - screenshot before crash]
- Video: [Pending - screen recording of crash]
- Logs: [Pending - logcat output]

### Additional Context
- Crash is reproducible 100% of the time
- Tested with multiple emoji types (🛒, 😀, ❤️) - all cause crash
- Saving notes WITHOUT emoji works normally
- Environment: Testing in QA environment
- Impact: Users cannot use emojis in note titles on Android
