# Search

**Feature Owner:** Core Team  
**Last Updated:** 2025-01-15  
**Screens:** SearchNotesView

---

## 1. Search Screen (SearchNotesView)

### 1.1 Layout
- Search bar at the top of the screen (always visible)
- Results list below the search bar
- Empty state / initial state below search bar when no results or no query

### 1.2 Initial State (No Query)
- When the search field is empty, the screen shows an initial state:
  - Icon: `magnifyingglass` (SF Symbol)
  - Title: "Search Notes"
  - Subtitle: "Search by title or content"
- No notes are displayed until the user types a query

### 1.3 No Results State
- When a query is entered but matches zero notes:
  - Icon: `magnifyingglass` (SF Symbol) or `doc.text.magnifyingglass`
  - Title: "No Results"
  - Subtitle: "No notes match '{query}'" (showing the actual query text)

---

## 2. Search Behavior

### 2.1 What Is Searched
- Search matches against **two fields**: note `title` AND note `content`
- Both fields are searched simultaneously for every query
- Category names are **NOT** searchable (searching "Work" does not find notes in the "Work" category unless "Work" appears in the note's title or content)

### 2.2 Matching Rules
- **Case-insensitive** — searching "hello" matches "Hello", "HELLO", "hElLo"
- **Substring matching** — searching "shop" matches "Shopping List", "workshop", "bookshop"
- **No word boundary requirement** — partial matches within words are valid
- **Single query string** — the entire search text is used as one query (no AND/OR operators)
- **Minimum query length:** 1 character — even a single character triggers search
- **Whitespace handling:** Leading/trailing whitespace in the query is trimmed; a whitespace-only query is treated as empty (shows initial state)

### 2.3 Real-Time Search
- Search results update **as the user types** (no "Search" button to press)
- There is a debounce delay to avoid excessive queries on rapid typing
- Debounce interval: ~300ms (platform default; not user-configurable)
- Clearing the search field returns to the initial state immediately

### 2.4 Result Display
- Results are displayed in the same format as the Notes list (NoteListView):
  - Note title
  - Content preview (first ~2 lines)
  - Category badge (if assigned)
  - Modified date
  - Pin indicator (if pinned)
- Results are sorted by relevance:
  - **Title matches rank higher** than content-only matches
  - Within the same relevance tier, sorted by `modifiedAt` descending

### 2.5 Result Actions
- **Tap a result** → Navigate to NoteDetailView for that note
- From NoteDetailView, the user can edit or delete the note
- After navigating back from NoteDetailView, the search results are **refreshed** with the current query (reflecting any changes made)
- There is NO swipe-to-delete on search results (deletion only from NoteDetailView)

---

## 3. Search Limitations & Known Constraints

| Constraint | Details |
|------------|----------|
| No advanced operators | No support for AND, OR, NOT, quoted phrases |
| No category filtering | Cannot filter search results by category |
| No date range filtering | Cannot limit search to a date range |
| No regex support | Special regex characters are treated as literal text |
| No search history | Previous searches are not saved or suggested |
| No highlighted matches | Search terms are not highlighted in results |
| Local only | Search is performed against local data only |

> **⚠️ Common Bug vs Feature Confusion:** 
> - "Search doesn't find notes by category name" → **Not a bug** — category names are not indexed for search.
> - "Search doesn't highlight matching text" → **Not a bug** — highlight is not a v1.0 feature.
> - "Search is slow with many notes" → **Expected** if < 2 seconds; report as performance issue if > 2 seconds for under 1,000 notes.

---

## 4. Validation Rules Summary

| Rule ID | Field | Rule | Behavior |
|---------|-------|------|----------|
| SV-001 | Query | Whitespace-only query treated as empty | Shows initial state |
| SV-002 | Query | No minimum length (1 char triggers search) | Results update immediately |
| SV-003 | Query | Special characters treated as literal text | No errors, no regex interpretation |
| SV-004 | Query | Maximum length: platform default (no app-imposed limit) | Very long queries are allowed |

---

## 5. Acceptance Criteria

- [ ] User can search notes by title
- [ ] User can search notes by content
- [ ] Search is case-insensitive
- [ ] Search supports substring matching (partial word matches)
- [ ] Results update in real-time as user types
- [ ] Empty query shows initial state with instructional message
- [ ] No-results state shows the query that was searched
- [ ] Tapping a result navigates to NoteDetailView
- [ ] Search results refresh after returning from note detail/edit
- [ ] Category names are NOT searchable
- [ ] Whitespace-only queries are treated as empty
