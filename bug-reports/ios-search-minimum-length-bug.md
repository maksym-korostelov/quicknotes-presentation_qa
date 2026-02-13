## [BUG] Search - Minimum query length enforced at 3+ characters instead of 1

**Severity:** Major  
**Priority:** P1  
**Environment:** DEV  
**Platform:** iOS 17+  
**Device:** iPhone 16 Pro  
**App Version:** 1.0.0

### Description
The search bar requires a minimum of 3 characters to trigger search results, but the specification requires search to accept single-character queries. Users cannot search for notes using 1 or 2 character terms, contradicting the documented behavior.

### Steps to Reproduce
1. Open QuickNotes app
2. Navigate to Search tab
3. Tap on the search field
4. Enter a single character (e.g., "a")
5. Observe the screen

### Actual Result
- No search results are displayed
- The search does not trigger with only 1 or 2 characters
- User must enter 3+ characters for results to appear

### Expected Result
- Per `features/search.md`, Section 2.2, Rule SV-002: Search results should update immediately with even a single character query
- Single character results matching title or content should appear in the results list
- Results are sorted by relevance (title matches rank higher than content-only matches)

### Evidence
- Screenshot: [Pending — to be attached]
- Video: [Pending — to be attached]

### Additional Context
**Spec Reference:** `features/search.md`, Section 2.2 - Matching Rules  
**Rule SV-002:** "No minimum length (1 char triggers search) | Results update immediately"

This behavior directly contradicts the documented requirement that minimum query length is 1 character and results should update in real-time as the user types.
