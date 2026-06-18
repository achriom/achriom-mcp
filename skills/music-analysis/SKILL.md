---
name: music-analysis
description: Album and artist discussion methodology. Use when exploring musical style, artist evolution, production, lyrics, or cultural impact. Triggers when discussing what makes an album special or how it fits an artist's catalog.
---

# Music Analysis

## When to Activate

- Discussing an album's sound, production, or significance
- Exploring an artist's evolution or influences
- Analyzing lyrics, themes, or musical choices
- Comparing albums or finding sonic connections
- Any deep music conversation

## Analysis Approach

### 1. Gather Album Details
```
get_details(media_type="album", title="...")
```
Look at: artist, themes, mood, era, claude_summary, genres, tracks

### 2. Play the Music
Don't just describe - let them hear:
```
get_track_previews(album_title="...", max_tracks=5)
```
Include previews inline when discussing specific songs.

### 3. Artist's Other Work
```
search(media_type="album", query="artist name")
```
How does this album fit in their discography?

### 4. Find Performances
```
search_youtube(query="artist album live performance")
```
Live versions, music videos, studio sessions, interviews.

### 5. Research Context
```
tavily-search(query="album title recording history making of")
```

## Discussion Patterns

**Sonic evolution:** How does this album differ from earlier/later work? What changed?

**Production choices:** What makes this sound distinctive? Who produced it?

**Lyrical themes:** For lyric-focused artists, what are they saying? How does it connect?

**Cultural moment:** What was happening in music when this dropped? How did it influence what came after?

## Proactive Features

- **ALWAYS play tracks** when discussing albums - `get_track_previews` is your best tool
- **Embed live performances** - often more revealing than studio versions
- **Show music videos** for visual artists
- **Connect to films** - soundtracks, scores, or thematic parallels
- **Surface the mood** - "If you're in this headspace, you might also reach for [album]"
