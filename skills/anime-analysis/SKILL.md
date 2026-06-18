---
name: anime-analysis
description: Anime analysis methodology. Use when exploring animation quality, studio style, adaptation fidelity, Japanese cultural context, or what makes an anime resonate. Triggers on questions about visual storytelling, sakuga moments, or genre conventions.
---

# Anime Analysis

## When to Activate

- Discussing animation quality or visual style
- Analyzing studio characteristics (Ghibli, Bones, MAPPA, etc.)
- Exploring adaptation from manga, light novel, or visual novel
- Discussing Japanese cultural context or themes
- Comparing anime across eras or genres
- Any deep-dive into what makes an anime work

## Analysis Approach

### 1. Gather Anime Details
```
get_details(media_type="anime", title="...")
```
Look at: studios, source material, themes, mood, era, genres, episodes, format, AniList score

### 2. Find Related Anime
```
search(media_type="anime", query="similar theme or studio")
```
Connect to others by same studio, director, or thematic similarity

### 3. Video Content
Opening/ending sequences, AMVs, analysis videos, sakuga compilations:
```
search_youtube(query="anime title opening analysis")
search_youtube(query="anime title sakuga")
```

### 4. Research Context
```
tavily-search(query="anime title production history interview")
```

## Discussion Patterns

**Animation quality:** What stands out visually? Sakuga moments? Distinctive style?

**Studio identity:** How does this fit the studio's body of work? Is it typical or a departure?

**Adaptation fidelity:** If from source material, what changed? What was gained or lost?

**Cultural context:** Japanese-specific elements that enrich understanding? Seasonal anime culture?

**Genre conventions:** How does it work within or subvert its genre? What tropes does it use?

**Character design:** How do the designs reflect personality? Memorable visual choices?

**Music and sound:** OST quality, voice acting (seiyuu), opening/ending themes?

## Era Classification

- **Classic (pre-1995):** Foundational works, hand-drawn era (Akira, Dragon Ball, Sailor Moon)
- **Golden Age (1995-2010):** Digital transition, mainstream breakthrough (Eva, Cowboy Bebop, Death Note)
- **Modern (2010-2020):** Streaming emergence, seasonal model (Attack on Titan, Your Name)
- **Current (2020+):** Peak production quality, global simultaneous release

## Proactive Features

- **Embed openings/endings** - often artistic highlights
- **Find sakuga breakdowns** - animation analysis videos
- **Connect to source material** - if manga/LN is in their collection
- **Note the studios** - production company strengths and history
- **Surface watch order** - for series with multiple seasons, movies, OVAs
- **Highlight voice cast** - notable seiyuu performances
- **Cultural notes** - explain Japanese-specific references when relevant
