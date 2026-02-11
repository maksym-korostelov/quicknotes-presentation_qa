# Informational Screens

**Feature Owner:** Core Team  
**Last Updated:** 2025-01-15  
**Screens:** AboutView, HelpView

---

## 1. About Screen (AboutView)

### 1.1 Access
- Accessed from **SettingsView** → "About QuickNotes" row

### 1.2 Display Content

| Section | Content | Dynamic? |
|---------|---------|----------|
| App Icon/Logo | QuickNotes logo or SF Symbol (`note.text`) | No |
| App Name | "QuickNotes" | No |
| Version | "Version 1.0.0" (reads from app bundle) | Yes — updates with releases |
| Description | Brief description of the app's purpose | No |
| Features List | Key capabilities of the app | No |
| Developer Info | "Developed by [Team/Company Name]" | No |
| Links Section | Privacy Policy, Terms of Service | No |
| Copyright | "© 2025 QuickNotes. All rights reserved." | No |

### 1.3 Features Listed

The About screen lists the following app capabilities:

| Icon | Feature |
|------|----------|
| `note.text` | Create and manage notes |
| `folder` | Organize with categories |
| `magnifyingglass` | Powerful search |
| `paintpalette` | Customize with colors |
| `lock.shield` | Your data stays on your device |

### 1.4 Links Behavior
- **Privacy Policy** and **Terms of Service** links open in the system browser (Safari / Chrome)
- In v1.0, these MAY point to placeholder URLs or show "Coming Soon"
- Links that fail to open should NOT crash the app

### 1.5 Actions
- **Back navigation** → Returns to SettingsView
- There are NO other interactive elements on this screen (no buttons, no forms)
- This is a **read-only informational screen**

---

## 2. Help Screen (HelpView)

### 2.1 Access
- Accessed from **SettingsView** → "Help & Support" row

### 2.2 Display Content

The Help screen uses an **expandable FAQ / accordion** layout:

| Section | Content |
|---------|----------|
| Title | "Help & Support" |
| FAQ Items | Expandable question-answer pairs |
| Contact Section | Support email or contact info |

### 2.3 FAQ Items

The following FAQ entries are displayed:

| # | Question | Answer Summary |
|---|----------|----------------|
| 1 | How do I create a note? | Tap + on Notes tab, enter title and content, tap Save |
| 2 | How do I organize notes? | Create categories in Categories tab, assign via note editor |
| 3 | How do I search notes? | Go to Search tab, type in search bar, results update in real-time |
| 4 | How do I delete a note? | Swipe left on note in list, or tap Delete in note detail |
| 5 | Can I recover deleted notes? | No — deletion is permanent. Always confirm before deleting. |
| 6 | How do I pin a note? | Open note detail, tap the pin button. Pinned notes appear at the top. |
| 7 | Is my data backed up? | In v1.0, data is stored locally only. Cloud backup coming in a future update. |

> **⚠️ QA Note:** The FAQ answers MUST be consistent with the actual app behavior. If an FAQ says "swipe left to delete" but the app uses a different gesture, that's a **documentation bug** — file it against the Help screen content.

### 2.4 FAQ Interaction
- Each FAQ item is **expandable/collapsible** (tap to toggle)
- By default, all items are **collapsed** (answer hidden)
- Multiple items can be expanded simultaneously (accordion is NOT exclusive)
- Expanding/collapsing is animated with a smooth transition

### 2.5 Contact Section
- Displays a support email address
- Tapping the email MAY open the system mail composer
- If no mail app is configured → Graceful handling (no crash; may show "Copy to clipboard" option or just display the address as text)

### 2.6 Actions
- **Back navigation** → Returns to SettingsView
- **Tap FAQ item** → Expand/collapse the answer
- **Tap email** → Open mail composer or copy to clipboard

---

## 3. Shared Rules for Informational Screens

### 3.1 Content is Static
- Both About and Help screens display **static content** that is bundled with the app
- Content does NOT come from a server or API
- Content changes require an app update

### 3.2 No Analytics in v1.0
- No tracking of which FAQ items are viewed
- No analytics on About screen visits

### 3.3 Accessibility
- All text content MUST be accessible to screen readers
- FAQ expand/collapse state SHOULD be announced by VoiceOver / TalkBack
- Link elements MUST be identified as links by accessibility services

---

## 4. Acceptance Criteria

### About Screen
- [ ] About screen is accessible from Settings
- [ ] App name "QuickNotes" is displayed
- [ ] Version number is displayed and matches actual app version
- [ ] App description is displayed
- [ ] Feature list is displayed with icons
- [ ] Developer/company information is displayed
- [ ] Copyright notice is displayed
- [ ] Privacy Policy link opens in browser (or shows placeholder gracefully)
- [ ] Terms of Service link opens in browser (or shows placeholder gracefully)
- [ ] Back navigation returns to Settings

### Help Screen
- [ ] Help screen is accessible from Settings
- [ ] All FAQ items are displayed
- [ ] FAQ items are collapsed by default
- [ ] Tapping a question expands/collapses the answer
- [ ] Multiple FAQ items can be expanded simultaneously
- [ ] FAQ content is accurate and matches actual app behavior
- [ ] Contact/support email is displayed
- [ ] Tapping email opens mail composer or handles gracefully
- [ ] Back navigation returns to Settings
