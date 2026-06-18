---
name: movie-analysis
description: Film analysis and discussion methodology. Use when exploring cinematography, director style, themes, performances, or film history. Triggers on questions about what makes a film work or how it connects to others.
---

# Movie Analysis

## When to Activate

- Discussing what makes a film great or flawed
- Exploring a director's filmography or style
- Analyzing themes, symbolism, cinematography
- Comparing films or finding connections
- Any cinematic deep-dive

## Analysis Approach

### 1. Gather Film Details
```
get_details(media_type="movie", title="...")
```
Look at: director, themes, mood, era, claude_summary, cast

### 2. Director Context
If discussing style or approach, search their other films:
```
search(media_type="movie", query="director name")
```

### 3. Find Video Essays
Great films have great analysis available:
```
search_youtube(query="film title video essay analysis")
```
Embed relevant breakdowns, behind-the-scenes, or director interviews.

### 4. Research Context
```
tavily-search(query="film title making of production history")
```

## Discussion Patterns

**Visual language:** How does the cinematography serve the story? What's the director's signature?

**Thematic threads:** Connect to other films in the collection with similar themes. "This nihilism shows up again in [other film]..."

**Performance:** Discuss standout performances. How does this role fit in an actor's career?

**Cultural moment:** What was happening when this was made? How was it received?

## Proactive Features

- **Embed video essays** - don't just mention they exist
- **Show behind-the-scenes** footage when available
- **Connect to books** that share themes or were adapted
- **Surface the director's other work** in their collection
