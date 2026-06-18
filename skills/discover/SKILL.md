---
name: discover
description: Explore a theme, mood, or idea across your entire collection
argument-hint: "<theme, mood, or question>"
allowed-tools:
  - mcp__plugin_achriom_achriom__get_stats
  - mcp__plugin_achriom_achriom__search
  - mcp__plugin_achriom_achriom__get_details
  - mcp__plugin_achriom_achriom__get_by_rating
  - mcp__plugin_achriom_achriom__get_timeline
  - mcp__plugin_achriom_achriom__get_signals
  - mcp__plugin_achriom_achriom__get_context
  - mcp__plugin_achriom_achriom__get_track_previews
  - mcp__plugin_achriom_achriom__search_youtube
  - mcp__plugin_achriom_achriom__search_book_content
---

# /discover — Follow a Thread Across Your Library

Take a theme, mood, or idea and trace it through everything you own. Books, films, albums, shows, anime — find where the thread appears across media.

## Invocation

```
/discover loneliness
/discover what keeps showing up in my highest-rated items?
/discover the relationship between power and isolation
/discover things I added in 2024 — what was I drawn to?
```

## Workflow

### Step 1: Define the Thread

Understand what the user wants to explore:

- **A theme**: loneliness, identity, rebellion, memory, home
- **A mood**: melancholy, restless, hopeful, unsettling
- **A pattern question**: "what do my 5-star items have in common?"
- **A time-based question**: "what was I into last year?"
- **An abstract idea**: "the relationship between art and commerce"

If the request is broad, start searching and let the collection shape the direction. Don't over-plan — discover alongside the user.

### Step 2: Search Across All Media Types

Using the **collection-insights** skill methodology, search systematically:

```
get_stats()                                          # Collection shape
search(media_type="book", query="theme")
search(media_type="movie", query="theme")
search(media_type="album", query="theme")
search(media_type="show", query="theme")
search(media_type="anime", query="theme")
get_by_rating(min_rating=4)                          # Top-rated for pattern matching
get_timeline()                                       # Temporal patterns
get_signals()                                        # Behavioral patterns
```

For pattern questions, lean on:
```
get_by_rating(min_rating=5)                          # What do their favorites share?
get_context()                                        # Broader behavioral signals
```

### Step 3: Map the Connections

Identify where the thread appears:

1. **Direct matches** — items explicitly about the theme
2. **Indirect matches** — items where the theme lives beneath the surface
3. **Surprising matches** — items you wouldn't expect to connect but do
4. **Cross-media pairs** — a book and a film circling the same idea from different angles

For each connection, get details:
```
get_details(media_type, title)    # For the most relevant items
```

### Step 4: Find the Story

The thread should tell a story. Using the **collection-insights** skill patterns:

- **The throughline**: Where does this theme keep appearing?
- **The evolution**: Has their relationship to this theme changed over time?
- **The constellation**: Which items from different media types orbit the same idea?
- **The absence**: Is there a notable gap — a direction this theme could go that they haven't explored?

### Step 5: Make It Experiential

For the strongest connections, bring them to life:
- Play a track that captures the mood: `get_track_previews()`
- Embed a scene or video essay: `search_youtube()`
- Quote a passage: `search_book_content()`

### Step 6: Present the Discovery

## Output Format

```
## [Theme/Mood] — Across Your Collection

[Opening observation — what you found when you pulled this thread.
One paragraph, no preamble.]

### The Thread

[Map of where this theme appears. Group by connection strength,
not by media type. The most compelling connections first.]

**[Title 1]** ([media type]) and **[Title 2]** ([media type])
[How these two items connect through the theme — be specific]

[Embedded media if available]

**[Title 3]** ([media type])
[How this item carries the theme in a different direction]

---

### The Surprise Connection

[The pairing or connection the user probably hasn't noticed.
This is the insight that makes discovery worthwhile.]

### The Gap

[Where this thread could go but hasn't yet in their collection.
Frame as invitation, not criticism.]

"You've explored [theme] through [angle], but there's a whole tradition
of [unexplored angle] you might find interesting — [1-2 specific suggestions]."

<!-- SUGGESTIONS: Go deeper on [strongest connection] | Find me something new in this vein | What other themes run through my collection? -->
```

## Notes

- Lead with the most interesting connection, not the most obvious one
- Cross-media connections are more valuable than within-media ones — finding that a book and an album share DNA is more interesting than two similar books
- If the search doesn't surface clear connections, say so. "This theme doesn't have deep roots in your collection yet" is a valid finding.
- For time-based questions, lean on `get_timeline()` and present chronologically
- Always include at least one experiential element (audio, video, or quote)
