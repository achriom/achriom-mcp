---
name: recommend
description: Get a personalized recommendation based on your collection, mood, or a specific theme
argument-hint: "<mood, theme, or 'something like [title]'>"
allowed-tools:
  - mcp__plugin_achriom_achriom__get_stats
  - mcp__plugin_achriom_achriom__get_by_rating
  - mcp__plugin_achriom_achriom__get_by_status
  - mcp__plugin_achriom_achriom__get_timeline
  - mcp__plugin_achriom_achriom__get_signals
  - mcp__plugin_achriom_achriom__get_context
  - mcp__plugin_achriom_achriom__search
  - mcp__plugin_achriom_achriom__get_details
  - mcp__plugin_achriom_achriom__get_track_previews
  - mcp__plugin_achriom_achriom__preview_album
  - mcp__plugin_achriom_achriom__search_youtube
  - mcp__plugin_achriom_achriom__search_book_content
  - mcp__plugin_achriom_achriom__add_item
  - mcp__plugin_achriom_achriom__lookup_item
---

# /recommend — What Should I Read / Watch / Listen To?

Surface the right thing at the right time — from what you already own or something new worth adding.

## Invocation

```
/recommend
/recommend something like Blade Runner
/recommend I'm in a melancholy mood
/recommend a book that pairs with OK Computer
```

## Workflow

### Step 1: Understand the Request

Determine what the user is after:

- **Mood-based**: "I'm restless," "something comforting," "I want to feel unsettled"
- **Similarity-based**: "something like [title]" — unpack what they loved about it
- **Theme-based**: "stories about memory," "music about place"
- **Cross-media**: "a book that pairs with [film]," "an album for reading [book]"
- **Open-ended**: "what should I read next?" — use collection signals to decide

If the request is vague, ask one clarifying question. Only one. Then recommend.

### Step 2: Mine the Collection

Always check what they already own before suggesting anything new. Using the **recommendations** skill methodology:

```
get_stats()                                    # Collection shape
get_by_rating(min_rating=4)                    # What they love
get_timeline()                                 # Recent activity
search(media_type, query="relevant theme")     # Themed search
get_by_status(media_type, status="unread")     # Unread/unwatched shelf
get_signals()                                  # Behavioral patterns
```

Look for:
- Unread/unwatched items that match the request
- Highly-rated items with thematic connections to the request
- Recent engagement patterns that suggest current taste

### Step 3: Build the Recommendation

Using the **recommendations** and **collection-insights** skills:

For each recommendation (aim for 2-3):
1. **Why this fits** — the specific connection to their request and taste
2. **Something to sample** — play a track, embed a video, quote a passage
3. **The thread** — how it connects to what they already love

Prioritize in this order:
1. Items they own but haven't explored yet
2. Cross-media connections within their collection
3. New items that fit their established taste
4. Stretch picks that expand their range

### Step 4: Make It Tangible

Don't just name titles. Demonstrate:
- For albums: `get_track_previews()` — play the music
- For films/shows: `search_youtube()` — embed a trailer or video essay
- For books: `search_book_content()` if available, or find an author interview
- For anime: `search_youtube()` — embed the opening sequence

### Step 5: Present the Recommendations

Use the output format below. End with follow-up prompts that let them go deeper or pivot.

## Output Format

```
## Here's What I'd Reach For

### [Title] — [Media Type]
[Cover/poster image]

[2-3 sentences on WHY this fits — specific to their request and taste.
Reference actual items in their collection as connection points.]

[Embedded media: track preview, video, or passage]

**The connection:** [One line linking this to something they love]

---

### [Title 2] — [Media Type]
[Same structure]

---

### The Stretch Pick: [Title 3]
[Same structure but frame as expanding their range]

<!-- SUGGESTIONS: Tell me more about [title] | Play more from [artist] | What else connects to this theme? -->
```

## Notes

- Never recommend something they've already rated highly — they know about it
- If recommending something they own but haven't consumed, acknowledge the unread/unwatched status directly
- For cross-media recommendations, make the connection explicit — don't assume they'll see it
- If nothing in the collection fits, say so honestly and research externally
- Always include at least one item from their existing collection
