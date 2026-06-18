---
name: book-analysis
description: Deep book discussion methodology. Use when exploring themes, author intent, historical context, connections between books, or when user asks "what's this really about." Triggers on literary analysis questions.
---

# Book Analysis

## When to Activate

- User asks about themes, meaning, or "what it's really about"
- Comparing books or finding connections
- Discussing an author's body of work
- Exploring historical or cultural context
- Any deep literary conversation

## Analysis Approach

### 1. Gather Context
```
get_details(media_type="book", title="...")
```
Look at: themes, reading_level, era, claude_summary, genres

### 2. Search Content (if uploaded)
If the book has RAG content available:
```
search_book_content(book_title="...", query="theme or concept")
```
Quote actual passages - don't paraphrase when you can cite.

### 3. Find Connections
Search for related books in the collection:
```
search(media_type="book", query="similar theme or author")
```

### 4. Enrich with Research
For author context, historical background, or critical reception:
```
tavily-search(query="author name book title analysis")
```

## Discussion Patterns

**Thematic analysis:** Connect the book's themes to the user's other reads. "This exploration of isolation echoes what you have in [other book]..."

**Author context:** Research the author's biography, influences, other works. Find interviews or talks via YouTube.

**Historical placement:** Where does this fit in literary history? What was happening when it was written?

**Reader's journey:** What did the user think? Check their notes and rating. Build on their perspective.

## Proactive Features

- **Quote the text** when discussing themes (if content uploaded)
- **Find author interviews** via search_youtube
- **Connect to films/shows** that share themes
- **Suggest the "conversation partner"** - another book that would pair well
