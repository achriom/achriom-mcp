---
name: show-analysis
description: TV series analysis methodology. Use when discussing show structure, character arcs, seasonal evolution, or the unique aspects of long-form storytelling. Triggers on questions about what makes a series work across seasons.
---

# TV Show Analysis

## When to Activate

- Discussing character development across seasons
- Analyzing what makes a series compelling
- Exploring showrunner vision or writing room choices
- Comparing series or finding connections
- Any long-form storytelling deep-dive

## Analysis Approach

### 1. Gather Show Details
```
get_details(media_type="show", title="...")
```
Look at: creator, themes, mood, seasons, era, claude_summary, cast

### 2. Find Related Series
```
search(media_type="show", query="similar theme or creator")
```

### 3. Video Content
Cast interviews, behind-the-scenes, analysis videos:
```
search_youtube(query="show title behind the scenes making of")
```

### 4. Research Context
```
tavily-search(query="show title oral history production")
```

## Discussion Patterns

**Long-form advantage:** What does this series do that a film couldn't? How does it use time?

**Character arcs:** How do characters evolve across seasons? What's the journey?

**Seasonal structure:** Does it have a planned arc or evolve organically? How does quality change?

**Cultural impact:** Did it change TV? Influence other shows? Become part of the conversation?

**The ensemble:** How does the cast work together? Standout performances?

## Proactive Features

- **Embed cast interviews** - actors discussing their characters
- **Find the creators' vision** - showrunner interviews about intent
- **Connect to source material** - if adapted from books in their collection
- **Note the vintage** - how it fits in TV history (golden age, prestige era, streaming)
- **Surface watch order** - if part of a connected universe
