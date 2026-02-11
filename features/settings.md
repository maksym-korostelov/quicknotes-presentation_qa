# Settings

**Feature Owner:** Core Team  
**Last Updated:** 2025-01-15  
**Screens:** SettingsView

---

## 1. Settings Screen (SettingsView)

### 1.1 Access
- Fourth tab in the main tab bar
- Icon: `gearshape` (SF Symbol)
- Title: "Settings"

### 1.2 Layout

The Settings screen uses a **grouped list (Form)** layout with the following sections:

#### Section 1: Account
| Row | Action | Icon |
|-----|--------|------|
| Profile | Navigate to ProfileView | `person.circle` |

#### Section 2: Preferences
| Row | Control | Default | Description |
|-----|---------|---------|-------------|
| Dark Mode | Toggle (Switch) | OFF (system) | Toggles between light/dark appearance |
| Notifications | Toggle (Switch) | ON | Enables/disables notification preferences |

#### Section 3: Data
| Row | Action | Icon |
|-----|--------|------|
| Export Notes | Action (not functional in v1.0) | `square.and.arrow.up` |
| Delete All Data | Destructive action | `trash` |

#### Section 4: About
| Row | Action | Icon |
|-----|--------|------|
| About QuickNotes | Navigate to AboutView | `info.circle` |
| Help & Support | Navigate to HelpView | `questionmark.circle` |

#### Footer
- Displays app version: "QuickNotes v1.0.0"

---

## 2. Preferences Behavior

### 2.1 Dark Mode Toggle
- Toggles between light and dark color scheme
- Change is applied **immediately** (no "Save" button needed)
- Preference persists across app launches (stored in UserDefaults / SharedPreferences)
- Default value: OFF (follows system appearance)

> **⚠️ Platform difference:** On iOS, the toggle overrides the system appearance for the app only. On Android, it overrides the MaterialTheme. Neither affects other apps or system-wide settings.

### 2.2 Notifications Toggle
- Toggles notification preferences ON/OFF
- In v1.0, this is a **UI-only preference** — there is no actual notification system
- The toggle state persists across app launches
- Changing this toggle does NOT trigger any system permission dialogs in v1.0

> **⚠️ Bug Triage Note:** "Turning on notifications doesn't actually send notifications" is **Not a bug** in v1.0. The toggle is a placeholder for future functionality. Only report it as a bug if: (1) the toggle state doesn't persist, (2) the UI glitches, (3) it crashes.

---

## 3. Data Management

### 3.1 Export Notes
- In v1.0, this feature is **not functional**
- Tapping "Export Notes" MAY show a "Coming Soon" message or no response
- This is NOT a bug — it is a known v1.0 placeholder

### 3.2 Delete All Data
- **Destructive action** that permanently deletes ALL notes AND ALL categories
- Confirmation dialog:
  - Title: "Delete All Data"
  - Message: "This will permanently delete all your notes and categories. This action cannot be undone."
  - Buttons: "Cancel" (default), "Delete All" (destructive)
- On confirm:
  - All notes are deleted
  - All categories are deleted
  - User is returned to Settings screen
  - Navigating to Notes or Categories tab shows empty states
- This action does NOT reset preferences (Dark Mode, Notifications remain unchanged)
- This action does NOT delete the UserProfile demo data

> **⚠️ Critical test case:** After "Delete All Data", verify that: (1) Notes list is empty, (2) Categories list is empty, (3) Search returns no results, (4) Profile stats show 0 notes and 0 categories, (5) Settings preferences are unchanged.

---

## 4. Navigation Rows

### 4.1 Profile
- Navigates to ProfileView (see `user-profile.md`)
- Shows a right chevron disclosure indicator

### 4.2 About QuickNotes
- Navigates to AboutView (see `informational-screens.md`)
- Shows a right chevron disclosure indicator

### 4.3 Help & Support
- Navigates to HelpView (see `informational-screens.md`)
- Shows a right chevron disclosure indicator

---

## 5. Acceptance Criteria

- [ ] Settings screen is accessible from the fourth tab
- [ ] Profile row navigates to ProfileView
- [ ] Dark Mode toggle changes app appearance immediately
- [ ] Dark Mode preference persists across app launches
- [ ] Notifications toggle state persists across app launches
- [ ] "Delete All Data" shows confirmation dialog
- [ ] "Delete All Data" deletes all notes and categories when confirmed
- [ ] "Delete All Data" does NOT delete preferences or user profile
- [ ] About row navigates to AboutView
- [ ] Help row navigates to HelpView
- [ ] App version is displayed in footer
- [ ] Export Notes is not functional (no crash on tap)
