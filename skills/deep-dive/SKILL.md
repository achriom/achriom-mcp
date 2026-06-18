---
name: deep-dive
description: Deep analysis of a specific book, film, album, show, or anime in your collection
argument-hint: "<title or topic>"
allowed-tools:
  - mcp__plugin_achriom_achriom__search
  - mcp__plugin_achriom_achriom__get_details
  - mcp__plugin_achriom_achriom__get_track_previews
  - mcp__plugin_achriom_achriom__search_youtube
  - mcp__plugin_achriom_achriom__search_book_content
  - mcp__plugin_achriom_achriom__read_book_section
  - mcp__plugin_achriom_achriom__get_context
  - mcp__plugin_achriom_achriom__add_item
  - mcp__plugin_achriom_achriom__lookup_item
---

# /deep-dive — Go Deep on Something

Full analysis of a single item — themes, craft, context, connections. The kind of conversation you'd have with someone who's read, watched, or listened to the same thing and has something to say about it.

## Invocation

```
/deep-dive Dune
/deep-dive the cinematography in There Will Be Blood
/deep-dive why is Kid A so divisive?
/deep-dive what makes Cowboy Bebop hold up?
```

## Workflow

### Step 1: Identify the Item

Find the item in the collection:

```
search(media_type, query="title or topic")
get_details(media_type, title)
```

If the item isn't in the collection, note that and offer to add it. Proceed with analysis either way — the librarian knows things beyond the shelf.

If the user specified a particular angle ("the cinematography in..."), note that as the focus. Otherwise, let the analysis follow what's most interesting about the work.

### Step 2: Gather Context

Using the appropriate media-specific analysis skill (**book-analysis**, **movie-analysis**, **music-analysis**, **show-analysis**, or **anime-analysis**):

**For books:**
```
get_details(media_type="book", title="...")
search_book_content(book_title="...", query="key themes")   # if content available
search(media_type="book", query="author name")               # other works in collection
search_youtube(query="author name interview")
```

**For films:**
```
get_details(media_type="movie", title="...")
search(media_type="movie", query="director name")
search_youtube(query="film title video essay")
search_youtube(query="film title behind the scenes")
```

**For albums:**
```
get_details(media_type="album", title="...")
get_track_previews(album_title="...", max_tracks=5)          # ALWAYS play the music
search(media_type="album", query="artist name")
search_youtube(query="artist album live performance")
```

**For shows:**
```
get_details(media_type="show", title="...")
search_youtube(query="show title behind the scenes")
search(media_type="show", query="creator name")
```

**For anime:**
```
get_details(media_type="anime", title="...")
search_youtube(query="anime title opening")
search_youtube(query="anime title sakuga analysis")
search(media_type="anime", query="studio name")
```

### Step 3: Find Collection Connections

Look for how this item connects to the rest of their library:

```
search(media_type="book", query="shared theme")
search(media_type="movie", query="shared theme")
search(media_type="album", query="shared theme")
get_context()                                    # broader behavioral context
```

### Step 4: Build the Analysis

Draw from the appropriate analysis skill. Include:

1. **What makes this work** — the craft, the choices, what elevates it
2. **Context** — when it was made, what was happening, why it matters
3. **Their relationship to it** — their rating, notes, status, when they added it
4. **Collection connections** — other items that share DNA with this one
5. **Something to experience** — embedded media (don't just describe, show)

If the user asked about a specific angle, lead with that. Otherwise, lead with whatever is most interesting.

### Step 5: Present the Analysis

## Output Format

```
## [Title]
[Cover/poster image]

[Opening that immediately says something substantive — no preamble.
Lead with the most interesting observation about this work.]

### [Angle 1 — e.g., "The Sound," "The Visual Language," "What It's Really About"]

[2-3 paragraphs of actual analysis. Quote the work where possible.
Reference specific scenes, tracks, chapters, episodes.]

[Embedded media — video essay, live performance, interview clip]

### [Angle 2]

[Continue the analysis from a different angle]

### In Your Collection

[How this connects to other things they own. Specific titles, specific connections.
"The same tension shows up in [other title] — but approached from the opposite direction."]

### Your Notes
[If they have ratings or notes, reflect them back. "You rated this 5/5 — and given
your notes about [X], I think what grabbed you was..."]

<!-- SUGGESTIONS: Compare this to [related title] | What influenced [creator]? | Find me something with the same energy -->
```

## Notes

- For albums, ALWAYS play track previews. The analysis should be accompanied by the actual music.
- For anime, embed the opening — it's often a work of art in itself
- If the user has notes on the item, incorporate them. Their perspective is part of the analysis.
- Don't try to cover everything. Go deep on 2-3 angles rather than shallow on 8.
- If the item isn't in their collection, the "In Your Collection" section becomes "What This Connects To" — reference items they DO own
