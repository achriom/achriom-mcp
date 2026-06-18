---
name: collection-insights
description: Pattern recognition across the full collection. Use when analyzing taste, finding connections, identifying gaps, or reflecting what the collection reveals about the person. Triggers on "what does my collection say" or pattern questions.
---

# Collection Insights

## When to Activate

- User asks what their collection reveals about them
- Looking for patterns across media types
- Identifying gaps or blind spots
- Reflecting on taste evolution
- "What themes keep showing up?"

## Insight Methodology

Collections are autobiographical. The patterns reveal:
- What preoccupies them
- How their taste has evolved
- What they return to
- What they avoid

### 1. Map the Territory
```
get_stats()  # Size and composition
get_by_rating(min_rating=4)  # Across all types - what they love
get_timeline()  # Recent engagement
```

### 2. Find Recurring Themes
Search across all media types for common threads:
```
search(media_type="book", query="isolation")
search(media_type="movie", query="isolation")
search(media_type="album", query="isolation")
```

### 3. Identify Patterns

**Thematic clusters:** What ideas keep appearing?
- Isolation/connection
- Power/corruption
- Identity/transformation
- Loss/redemption

**Era preferences:** Do they gravitate to certain periods?
- Classic (pre-1970)
- Golden age (1970-1999)
- Modern (2000-2015)
- Contemporary (2015+)

**Genre gravity:** Where does the collection cluster?

**Creator loyalty:** Which authors/directors/artists appear multiple times?

### 4. Spot the Gaps

What's conspicuously absent?
- Entire genres they avoid
- Eras they skip
- Popular works they've passed on

Gaps are as revealing as presences.

## Insight Patterns

**The throughline:** "Across books, films, and music, you keep returning to stories about [theme]. It shows up in [examples]..."

**The evolution:** "Your earlier additions lean [direction], but recently you've moved toward [new direction]..."

**The constellation:** "These five items from different media types are all circling the same idea..."

**The blind spot:** "You have deep coverage of [area] but almost nothing in [related area]. Curious or intentional?"

**The signature:** "Your collection has a distinctive character - [description]. Not many people would have both [unlikely pairing]..."

## Delivering Insights

- Be specific with examples, not generic observations
- Show the evidence - reference actual titles
- Frame as discovery, not judgment
- Invite reflection: "Does this resonate?"
