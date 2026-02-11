---
applyTo: "**/*test-data*.md"
---

# Test Data Generation Instructions

## Guidelines

When generating test data:

### User Data
- Use realistic but fake names (John Smith, Maria Garcia)
- Use test email format: `testuser+[scenario]@quicknotes.test`
- Never use real personal data

### Note Content
- Vary content length: short (10 chars), medium (100 chars), long (1000+ chars)
- Include special characters: émojis 🎉, unicode: café, symbols: @#$%
- Include edge cases: empty strings, whitespace only, max length

### Dates
- Past dates for "created" timestamps
- Recent dates for "modified" timestamps
- Edge cases: leap years, timezone boundaries, DST transitions

### IDs
- Use valid UUID format: `550e8400-e29b-41d4-a716-446655440000`
- Ensure uniqueness within test set

## Test Data Templates

### Users
```json
{
  "freeUser": {
    "email": "testuser+free@quicknotes.test",
    "password": "TestPass123!",
    "name": "Free User",
    "plan": "free"
  },
  "premiumUser": {
    "email": "testuser+premium@quicknotes.test",
    "password": "TestPass123!",
    "name": "Premium User",
    "plan": "premium"
  }
}
```

### Notes
```json
{
  "simpleNote": {
    "title": "Shopping List",
    "content": "Milk, Eggs, Bread"
  },
  "longNote": {
    "title": "Meeting Notes - Q4 Planning",
    "content": "[500+ characters of realistic meeting notes]"
  },
  "specialCharsNote": {
    "title": "Café Menu ☕",
    "content": "Espresso: €3.50\nCappuccino: €4.00\n日本語テスト"
  },
  "emptyContent": {
    "title": "Empty Note",
    "content": ""
  },
  "maxLengthTitle": {
    "title": "[100 character title...]",
    "content": "Testing max title length"
  }
}
```

### Edge Cases Checklist
- [ ] Empty string
- [ ] Whitespace only: `"   "`
- [ ] Single character: `"a"`
- [ ] Max length
- [ ] Max length + 1 (boundary)
- [ ] Special characters: `<script>alert('xss')</script>`
- [ ] Unicode: `你好世界`
- [ ] Emoji: `🎉🚀💯`
- [ ] SQL injection: `'; DROP TABLE notes;--`