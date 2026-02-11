# Note Creation Test Data

## Test Users

```json
{
  "freeUser": {
    "userId": "550e8400-e29b-41d4-a716-446655440001",
    "email": "testuser+free@quicknotes.test",
    "password": "TestPass123!",
    "name": "John Smith",
    "plan": "free",
    "noteCount": 25
  },
  "premiumUser": {
    "userId": "550e8400-e29b-41d4-a716-446655440002",
    "email": "testuser+premium@quicknotes.test",
    "password": "TestPass123!",
    "name": "Maria Garcia",
    "plan": "premium",
    "noteCount": 150
  }
}
```

## Normal Notes (Valid Test Cases)

### Note 1: Simple Shopping List
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440001",
  "title": "Shopping List",
  "content": "Milk, Eggs, Bread, Butter",
  "categoryId": null,
  "createdAt": "2026-01-15T10:30:00Z",
  "modifiedAt": "2026-01-15T10:30:00Z"
}
```

### Note 2: Meeting Notes
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440002",
  "title": "Team Meeting - Q1 Planning",
  "content": "Agenda: Review Q4 results, discuss Q1 goals, assign action items. Attendees: John, Maria, Alex, Sarah. Key decisions: Launch new feature by March, increase marketing budget by 20%, hire 2 new developers.",
  "categoryId": "750e8400-e29b-41d4-a716-446655440001",
  "createdAt": "2026-01-20T14:00:00Z",
  "modifiedAt": "2026-01-20T15:45:00Z"
}
```

### Note 3: Recipe
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440003",
  "title": "Chocolate Chip Cookies",
  "content": "Ingredients: 2 cups flour, 1 cup butter, 1 cup sugar, 2 eggs, 2 tsp vanilla, 1 tsp baking soda, 2 cups chocolate chips. Instructions: Mix butter and sugar, add eggs and vanilla, combine dry ingredients, fold in chocolate chips, bake at 350°F for 12 minutes.",
  "categoryId": "750e8400-e29b-41d4-a716-446655440002",
  "createdAt": "2026-01-25T09:15:00Z",
  "modifiedAt": "2026-01-26T11:20:00Z"
}
```

### Note 4: Travel Itinerary
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440004",
  "title": "Paris Trip 2026",
  "content": "Day 1: Arrive at CDG, check into hotel, visit Eiffel Tower. Day 2: Louvre Museum, Seine river cruise. Day 3: Versailles day trip. Day 4: Montmartre, Sacré-Cœur. Day 5: Shopping on Champs-Élysées, departure. Hotel: Le Marais Boutique, Confirmation: #AB123456. Flight: AA1234, Seat 12A.",
  "categoryId": "750e8400-e29b-41d4-a716-446655440003",
  "createdAt": "2026-02-01T16:30:00Z",
  "modifiedAt": "2026-02-03T10:00:00Z"
}
```

### Note 5: Book Summary
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440005",
  "title": "Atomic Habits - Key Takeaways",
  "content": "Main idea: Small changes lead to remarkable results. Four Laws of Behavior Change: 1. Make it obvious, 2. Make it attractive, 3. Make it easy, 4. Make it satisfying. Focus on systems rather than goals. Identity-based habits are more powerful than outcome-based habits.",
  "categoryId": null,
  "createdAt": "2026-02-05T20:00:00Z",
  "modifiedAt": "2026-02-05T20:00:00Z"
}
```

## Edge Case Notes

### Edge Case 1: Special Characters & Unicode
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440101",
  "title": "Café Menu ☕🥐",
  "content": "Espresso: €3.50\nCappuccino: €4.00\nLatte: €4.50\n\n日本語メニュー:\n抹茶ラテ: ¥500\nコーヒー: ¥300\n\nСпециальное предложение: Круассан + кофе = 6€\n\nEmojis test: 🎉🚀💯✨🌟❤️🔥\n\nSymbols: @#$%^&*()_+-=[]{}|;:',.<>?/~`",
  "categoryId": "750e8400-e29b-41d4-a716-446655440004",
  "createdAt": "2026-01-10T08:00:00Z",
  "modifiedAt": "2026-01-10T08:00:00Z"
}
```

### Edge Case 2: Maximum Length Title
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440102",
  "title": "This is a very long title that tests the maximum character limit for note titles in the application",
  "content": "Testing maximum title length boundary. The title of this note is exactly 100 characters long, which should be the maximum allowed length according to the application specifications.",
  "categoryId": null,
  "createdAt": "2026-01-12T12:00:00Z",
  "modifiedAt": "2026-01-12T12:00:00Z"
}
```

### Edge Case 3: Empty Content
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440103",
  "title": "Note with Empty Content",
  "content": "",
  "categoryId": null,
  "createdAt": "2026-01-14T18:30:00Z",
  "modifiedAt": "2026-01-14T18:30:00Z"
}
```

## Additional Edge Cases for Boundary Testing

### Edge Case 4: Whitespace Only Content
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440104",
  "title": "Whitespace Test",
  "content": "     ",
  "categoryId": null,
  "createdAt": "2026-01-16T09:00:00Z",
  "modifiedAt": "2026-01-16T09:00:00Z"
}
```

### Edge Case 5: Single Character
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440105",
  "title": "a",
  "content": "x",
  "categoryId": null,
  "createdAt": "2026-01-17T13:00:00Z",
  "modifiedAt": "2026-01-17T13:00:00Z"
}
```

### Edge Case 6: Maximum Content Length
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440106",
  "title": "Maximum Length Content Test",
  "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum. Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas nulla pariatur. At vero eos et accusamus et iusto odio dignissimos ducimus qui blanditiis praesentium voluptatum deleniti atque corrupti quos dolores et quas molestias excepturi sint occaecati cupiditate non provident, similique sunt in culpa qui officia deserunt mollitia animi, id est laborum et dolorum fuga.",
  "categoryId": null,
  "createdAt": "2026-01-18T15:00:00Z",
  "modifiedAt": "2026-01-18T15:00:00Z"
}
```

## Invalid Notes (Negative Testing)

### Invalid Note 1: Exceeds Title Length Limit
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440201",
  "title": "This is an invalid title that exceeds the maximum character limit of 100 characters for testing boundary conditions error",
  "content": "This note should fail validation because the title is 101 characters long, which is one character over the limit.",
  "categoryId": null,
  "expectedError": "Title exceeds maximum length of 100 characters",
  "expectedStatusCode": 400
}
```

### Invalid Note 2: Missing Required Title
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440202",
  "title": null,
  "content": "This note should fail validation because the title field is required but is set to null.",
  "categoryId": null,
  "expectedError": "Title is required",
  "expectedStatusCode": 400
}
```

### Invalid Note 3: Empty Title
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440203",
  "title": "",
  "content": "This note should fail validation if empty titles are not allowed.",
  "categoryId": null,
  "expectedError": "Title cannot be empty",
  "expectedStatusCode": 400
}
```

### Invalid Note 4: XSS Attack Attempt
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440204",
  "title": "XSS Test",
  "content": "<script>alert('XSS Attack')</script><img src=x onerror=alert('XSS')>",
  "categoryId": null,
  "expectedBehavior": "Content should be sanitized or escaped, not executed",
  "expectedStatusCode": 201
}
```

### Invalid Note 5: SQL Injection Attempt
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440205",
  "title": "SQL Injection Test",
  "content": "'; DROP TABLE notes;--",
  "categoryId": null,
  "expectedBehavior": "Input should be properly escaped/parameterized, no SQL execution",
  "expectedStatusCode": 201
}
```

### Invalid Note 6: Invalid Category ID
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440206",
  "title": "Invalid Category Test",
  "content": "This note references a non-existent category ID.",
  "categoryId": "999e8400-e29b-41d4-a716-446655440999",
  "expectedError": "Category not found",
  "expectedStatusCode": 404
}
```

### Invalid Note 7: Malformed UUID
```json
{
  "noteId": "invalid-uuid-format",
  "title": "Malformed UUID Test",
  "content": "This note has an invalid UUID format.",
  "categoryId": null,
  "expectedError": "Invalid UUID format",
  "expectedStatusCode": 400
}
```

## Test Scenarios

### Scenario 1: Free User Note Limit
- **User:** freeUser (current count: 49 notes)
- **Action:** Create 2 notes
- **Expected Result:** First note succeeds, second note fails with "Free plan limit reached (50 notes maximum)"

### Scenario 2: Premium User Unlimited Notes
- **User:** premiumUser (current count: 150 notes)
- **Action:** Create multiple notes
- **Expected Result:** All notes created successfully

### Scenario 3: Quick Note Creation
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440301",
  "title": null,
  "content": "Quick note without title",
  "categoryId": null,
  "expectedBehavior": "System should auto-generate title from first line of content or use 'Quick Note' + timestamp",
  "expectedStatusCode": 201
}
```

### Scenario 4: Concurrent Creation
- **Action:** Create same note simultaneously from two devices
- **Expected Result:** Both should succeed with different noteIds, or second should fail with conflict error

## Special Date Cases

### Leap Year Date
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440401",
  "title": "Leap Year Test",
  "content": "Testing leap year date handling",
  "createdAt": "2024-02-29T23:59:59Z",
  "modifiedAt": "2024-02-29T23:59:59Z"
}
```

### DST Transition
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440402",
  "title": "DST Transition Test",
  "content": "Testing daylight saving time transition",
  "createdAt": "2026-03-08T02:30:00-05:00",
  "modifiedAt": "2026-03-08T03:30:00-04:00"
}
```

### Timezone Boundary
```json
{
  "noteId": "650e8400-e29b-41d4-a716-446655440403",
  "title": "Timezone Test",
  "content": "Testing timezone boundary at midnight",
  "createdAt": "2026-01-31T23:59:59Z",
  "modifiedAt": "2026-02-01T00:00:01Z"
}
```

## Categories for Testing

```json
{
  "categories": [
    {
      "categoryId": "750e8400-e29b-41d4-a716-446655440001",
      "name": "Work",
      "color": "#FF5733"
    },
    {
      "categoryId": "750e8400-e29b-41d4-a716-446655440002",
      "name": "Personal",
      "color": "#33FF57"
    },
    {
      "categoryId": "750e8400-e29b-41d4-a716-446655440003",
      "name": "Travel",
      "color": "#3357FF"
    },
    {
      "categoryId": "750e8400-e29b-41d4-a716-446655440004",
      "name": "Food",
      "color": "#FF33F5"
    }
  ]
}
```
