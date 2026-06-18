---
name: collection-review
description: Full audit of your collection — patterns, taste profile, gaps, and what your library says about you
argument-hint: "<optional focus area>"
allowed-tools:
  - mcp__plugin_achriom_achriom__get_stats
  - mcp__plugin_achriom_achriom__get_by_rating
  - mcp__plugin_achriom_achriom__get_by_status
  - mcp__plugin_achriom_achriom__get_timeline
  - mcp__plugin_achriom_achriom__get_signals
  - mcp__plugin_achriom_achriom__get_context
  - mcp__plugin_achriom_achriom__get_user_profile
  - mcp__plugin_achriom_achriom__search
  - mcp__plugin_achriom_achriom__get_details
---

# /collection-review — What Does Your Library Say About You?

A comprehensive review of your entire collection. Patterns, taste evolution, thematic clusters, blind spots, and the personality of your library.

## Invocation

```
/collection-review
/collection-review just my books
/collection-review how has my taste changed?
/collection-review what am I avoiding?
```

## Workflow

### Step 1: Map the Full Territory

Pull everything:

```
get_stats()                                    # Size, composition, media breakdown
get_by_rating(min_rating=5)                    # The all-time favorites
get_by_rating(min_rating=4)                    # The broader "loved it" tier
get_by_rating(max_rating=2)                    # What didn't land
get_by_status(media_type, status="unread")     # The backlog (all types)
get_timeline()                                 # When things were added
get_signals()                                  # Behavioral patterns
get_context()                                  # Broader context
```

If the user asked about a specific media type or focus area, concentrate there. Otherwise, go wide.

### Step 2: Find the Patterns

Using the **collection-insights** skill, analyze systematically:

**Thematic clusters:**
Search for recurring themes across media types:
```
search(media_type="book", query="isolation")
search(media_type="movie", query="isolation")
# Repeat for themes that emerge from the top-rated items
```

**Creator loyalty:**
Which authors, directors, artists, and studios appear multiple times?

**Era preferences:**
When were the items in the collection made? Where does it cluster?

**Genre gravity:**
Where does the collection mass? What genres dominate, what's sparse?

**Rating patterns:**
What do the 5-star items share? What do the low-rated items have in common? Is there a generous or harsh rating tendency?

**The backlog:**
What's sitting unread/unwatched? Is there a pattern to what gets deferred?

### Step 3: Identify the Gaps

What's conspicuously absent:
- Entire genres they avoid
- Eras they skip
- Obvious works in genres they love that aren't present
- Media types that are thin relative to others

Frame gaps as curiosity, not criticism: "You have deep coverage of [area] but almost nothing in [related area]."

### Step 4: Build the Taste Profile

Synthesize everything into a profile — if this collection were a person, who would they be? What preoccupies them? What do they reach for when they need comfort vs. when they want to be challenged?

### Step 5: Present the Review

## Output Format

```
## Your Library

**[N] items** across [media types] — [one-line characterization of the collection's personality]

---

### The Numbers

| Media Type | Total | Completed | Backlog | Avg Rating |
|-----------|-------|-----------|---------|------------|
| Books | [n] | [n] | [n] | [n]/5 |
| Films | [n] | [n] | [n] | [n]/5 |
| Albums | [n] | [n] | [n] | [n]/5 |
| Shows | [n] | [n] | [n] | [n]/5 |
| Anime | [n] | [n] | [n] | [n]/5 |

### What Your Collection Says

[2-3 paragraphs characterizing the collection's personality. Be specific —
reference actual titles. This should feel like an observation about the person,
not a database summary.]

### The Throughlines

**[Theme 1]** — appears in [Title A] (book), [Title B] (film), [Title C] (album)
[1-2 sentences on how this theme manifests differently across media]

**[Theme 2]** — [same structure]

**[Theme 3]** — [same structure]

### Your Favorites Tell a Story

[Analysis of the highest-rated items. What do they share? What does the
"best of" shelf reveal about what moves this person?]

### The Evolution

[How taste has shifted over time, based on timeline data. Early additions
vs. recent additions. Any notable pivots or deepening interests.]

### The Blind Spots

[What's absent. Frame as discovery opportunities, not deficiencies.]

- **[Gap 1]**: [What's missing and why it's interesting given what IS present]
- **[Gap 2]**: [Same]

### The Backlog

[What's sitting unread/unwatched. Any patterns? Any items that deserve
to be bumped up the queue given recent taste?]

"Based on your recent ratings, **[unread title]** should probably move up your list."

---

### Taste Profile

> **In a sentence:** [One-line characterization — "You're drawn to stories about
> [theme] told through [style], with a blind spot for [gap] and a soft spot for [weakness]"]

<!-- SUGGESTIONS: Go deeper on [strongest theme] | What should I read/watch next based on this? | Compare my taste across decades -->
```

## Notes

- The collection review is the most data-intensive command. Pull everything before synthesizing.
- Specific titles make this feel real. "You like dark stories" is useless. "You gave 5 stars to No Country for Old Men, Blood Meridian, and There Will Be Blood — you're drawn to the American West as a space where morality dissolves" is an insight.
- The taste profile sentence at the end should feel like a revelation, not a summary
- If the collection is small (under 20 items), note that patterns will be provisional
- For very large collections, focus on the signal (high ratings, recent additions) rather than trying to characterize everything
