# Onboarding

**Feature Owner:** Core Team  
**Last Updated:** 2025-01-15  
**Screens:** OnboardingView

---

## 1. Onboarding Screen (OnboardingView)

### 1.1 Trigger Conditions
- Displayed on **first app launch only**
- After the user completes or skips onboarding, it is **never shown again** (even after app reinstall is a platform-specific behavior — see Section 3)
- The "has seen onboarding" flag is stored in local preferences (UserDefaults / SharedPreferences)

### 1.2 Layout
- Single-page scrollable view (NOT a paged carousel in v1.0)
- Contains:
  - **App title:** "QuickNotes" displayed prominently
  - **Subtitle:** "Your ideas, organized" (or similar tagline)
  - **Feature highlights:** List of 3–4 app capabilities with icon + title + description
  - **"Get Started" button:** Primary CTA at the bottom
  - **"Skip" button:** Secondary/text button below or near "Get Started"
  - **Page indicator:** Optional progress indicator

### 1.3 Feature Highlights

The following features are highlighted (exact content may vary by platform):

| Icon | Title | Description |
|------|-------|-------------|
| `note.text` | Create Notes | "Capture your thoughts and ideas quickly" |
| `folder` | Organize | "Keep notes organized with custom categories" |
| `magnifyingglass` | Search | "Find any note instantly with powerful search" |
| `paintpalette` | Customize | "Personalize notes with colors and styles" |

---

## 2. Actions

### 2.1 "Get Started" Button
- Marks onboarding as completed
- Navigates to the main tab bar interface
- The onboarding screen is dismissed and cannot be returned to

### 2.2 "Skip" Button
- Same behavior as "Get Started" — marks onboarding as completed and navigates to main app
- There is NO functional difference between "Get Started" and "Skip" in v1.0
- Both set the same "onboarding completed" preference flag

### 2.3 Back Navigation
- There is NO back button on the onboarding screen
- The system back gesture (Android) / swipe-to-go-back (iOS) should NOT dismiss onboarding to a blank screen — it should either be disabled or have no effect

---

## 3. Persistence & Edge Cases

### 3.1 Preference Flag
- The "has completed onboarding" flag is stored locally
- Flag name: platform-specific (e.g., `hasCompletedOnboarding` in UserDefaults)
- Once set to `true`, onboarding is never shown again

### 3.2 App Update
- Onboarding does NOT re-appear after app updates
- The preference flag persists across updates

### 3.3 App Reinstall
- **iOS:** UserDefaults are deleted on uninstall → Onboarding WILL appear again after reinstall
- **Android:** SharedPreferences may persist if the user doesn't clear data → Behavior varies
- This is platform-standard behavior and NOT a bug

### 3.4 "Delete All Data" (Settings)
- The "Delete All Data" action in Settings does **NOT** reset the onboarding flag
- Onboarding does NOT re-appear after deleting all data

---

## 4. Acceptance Criteria

- [ ] Onboarding appears on first app launch
- [ ] Onboarding does NOT appear on subsequent launches
- [ ] "Get Started" navigates to main tab bar
- [ ] "Skip" navigates to main tab bar
- [ ] Feature highlights are displayed with icons, titles, and descriptions
- [ ] Back navigation does not lead to blank/broken state
- [ ] Onboarding does NOT re-appear after "Delete All Data"
- [ ] Onboarding re-appears after full app uninstall + reinstall on iOS
