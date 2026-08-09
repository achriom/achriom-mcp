# Achriom MCP Prompts

15 prompts that shape how AI engages with your collection. Load them via `prompts/get("name")`.

## How to Use

**List available prompts:**
```
prompts/list
```

**Load a prompt:**
```
prompts/get("librarian")
```

**Load with arguments:**
```
prompts/get("book-analysis", { "title": "1984" })
prompts/get("deep-dive", { "title": "Dune", "angle": "the political structures" })
prompts/get("discover", { "theme": "loneliness" })
```

---

## Core Persona

### `librarian`

The foundation. Activates warm, curious engagement and tells the AI how to use every tool in the collection.

**No arguments.**

Sets:
- Approach: curious not cataloging, proactive not passive, demonstrate not describe
- Full tool reference table (~30 tools)
- Skill activation matrix (which methodology to apply in each situation)
- First-use handling for empty collections
- Media display rules for audio and video tags

Load this at the start of every session. All other prompts build on it.

---

## Analysis Prompts

### `book-analysis`

Deep literary analysis methodology.

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `title` | No | Book to analyze |

**Workflow:**
1. `get_details(media_type="book", title)` — themes, era, summary, genres
2. `search_book_content()` if uploaded — quote actual passages
3. `search(media_type="book", query="similar theme or author")` — collection connections
4. `search_youtube()` — author interviews and talks

**Covers:** Thematic analysis, author biography and context, historical placement, connections to the rest of the collection, reader's notes and rating.

---

### `movie-analysis`

Film analysis methodology.

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `title` | No | Film to analyze |

**Workflow:**
1. `get_details(media_type="movie", title)` — director, themes, mood, cast
2. `search(media_type="movie", query="director name")` — filmography context
3. `search_youtube("title video essay OR behind the scenes")` — embed analysis

**Covers:** Visual language and cinematography, director style, performance, cultural moment, thematic connections to other films in the collection.

---

### `music-analysis`

Album and artist discussion. **Always plays tracks.**

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `title` | No | Album to analyze |

**Workflow:**
1. `get_details(media_type="album", title)` — artist, themes, mood, tracks
2. `get_track_previews(album_title)` — **always call this, always include in response**
3. `search_youtube("artist album live performance")` — embed performances
4. `search(media_type="album", query="artist name")` — discography context

**Covers:** Sound and production, artist evolution, lyrics and themes, cultural moment. Never describe music without playing it.

---

### `show-analysis`

TV series analysis for long-form storytelling.

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `title` | No | Show to analyze |

**Workflow:**
1. `get_details(media_type="show", title)` — creator, themes, seasons, cast
2. `search(media_type="show", query="similar theme or creator")`
3. `search_youtube("show title cast interview OR behind the scenes")`

**Covers:** How the show uses its episodic format, character arcs across seasons, showrunner vision, ensemble dynamics, how it fits in TV history.

---

### `anime-analysis`

Animation-specific analysis.

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `title` | No | Anime to analyze |

**Workflow:**
1. `get_details(media_type="anime", title)` — studios, source material, AniList score
2. `search(media_type="anime", query="studio name or similar theme")`
3. `search_youtube("title opening OR sakuga OR AMV")`

**Covers:** Animation quality and sakuga moments, studio identity, adaptation fidelity, Japanese cultural context, genre conventions.

Always embed the opening sequence — it's part of the experience.

---

## Orchestrating Prompts

These are workflow prompts that guide multi-step sessions. They define full processes, not just analytical approaches.

### `deep-dive`

Full analysis of a single item across all relevant angles.

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `title` | No | Title to analyze |
| `angle` | No | Specific angle or question to focus on |

**Workflow:**
1. Find the item (`search` + `get_details`). If not in collection, proceed anyway.
2. Load media-specific context (track previews for albums, video essays for films, passages for books, opening sequence for anime)
3. Search for collection connections across media types
4. Build analysis around: what makes this work, context, their relationship to it, collection connections, and something to experience

**Output:** Opens with the most interesting observation — no preamble. 2-3 focused angles rather than a survey. Embedded media inline. Ends with collection connections.

---

### `discover`

Trace a theme, mood, or idea across the entire collection.

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `theme` | No | Theme, mood, or idea to explore |

**Workflow:**
1. Define the thread (theme, mood, pattern question, or time-based query)
2. Search across all seven media types for the theme
3. Pull `get_by_rating(min_rating=4)` and `get_signals()` for pattern context
4. Map connections: direct matches, indirect matches, surprising matches, cross-media pairs
5. Find one experiential element — play a track, embed a video, quote a passage

**Output:** Opens with what you found when you pulled the thread. Connections grouped by strength, not by media type. Ends with the gap — where this thread could go but hasn't yet. Cross-media connections are more valuable than within-media ones.

---

### `recommend`

Personalized recommendation. Mines unread/unwatched items first.

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `prompt` | No | What you're looking for — mood, theme, or "something like [title]" |
| `mood` | No | Mood or vibe |

**Workflow:**
1. Parse the request (mood-based, similarity-based, theme-based, cross-media, or open-ended)
2. If vague: ask one clarifying question. Only one.
3. Mine the collection: `get_by_rating(min_rating=4)`, `get_by_status(status="unread")`, `get_signals()`, themed search
4. Prioritize: (1) owned but unconsumed, (2) cross-media connections, (3) new fits, (4) stretch picks
5. Make each recommendation tangible — play a track, embed a trailer, quote a passage

**Output:** 2-3 recommendations. For each: why it fits (specific to their taste), something to sample, the connection to what they already love. Never recommend something they've already rated highly.

---

### `collection-review`

Full collection audit — patterns, taste profile, gaps, and what the library says about the person.

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `focus` | No | Focus area: a media type, theme, or time period |

**Workflow:**
1. Pull everything: `get_stats()`, top-rated and low-rated items, backlog across all types, `get_timeline()`, `get_signals()`, `get_user_profile()`
2. Search for recurring themes using terms from top-rated items
3. Identify thematic clusters, creator loyalty, era preferences, genre gravity, rating patterns, backlog composition
4. Spot gaps — what's conspicuously absent (frame as discovery, not deficiency)
5. Synthesize into a taste profile

**Output:** Stats table by media type. Collection personality in 2-3 paragraphs with specific titles as evidence. Throughlines (themes that cross media types). Favorites analysis. Taste evolution over time. Blind spots. Backlog patterns. Single-sentence taste profile at the end.

"You like dark stories" is useless. "You gave 5 stars to No Country for Old Men, Blood Meridian, and There Will Be Blood — you're drawn to the American West as a space where morality dissolves" is an insight.

---

### `research`

Enter focused research mode on a curated subset of the library.

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `topic` | No | Research topic or list of items to study |

**Workflow:**
1. Define the corpus (named items, a topic, or conversation to determine it)
2. Announce scope: "Research corpus: [N] items — [list]. I'll focus exclusively on these."
3. Load details for all items in the corpus
4. Identify the research question: comparative, chronological, influence, or synthesis
5. Conduct research: quote from texts (`search_book_content`), embed relevant video (`search_youtube`), cross-reference within the corpus

**Rules:**
- Answer questions using ONLY the scoped items
- Never speculate about what else might be in the library
- Never proactively suggest expanding the corpus — the user drives that
- If asked about something outside scope: note it's not in the research set

End each response with prompts that push the research forward.

See also: `focused-research` (the methodology prompt that `research` activates).

---

## Methodology Prompts

These are typically activated by the orchestrating prompts above, but can be loaded directly.

### `recommendations`

Cross-media recommendation methodology. Mine collection first, bridge across media types, respect taste signals.

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `mood` | No | Mood or vibe to match |
| `media_type` | No | Preferred type: book, movie, album, show, anime, game |

---

### `collection-insights`

Pattern recognition across the full collection. What do thematic clusters, era preferences, genre gravity, creator loyalty, and gaps reveal about the person?

**No arguments.**

---

### `focused-research`

Deep analysis mode for a curated subset. The corpus is a complete, contained universe. No contamination from outside items. User drives expansion.

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `scope` | No | Items to include (comma-separated titles) |

---

## Quality Filter

### `stop-slop`

Writing quality filter. **Always active** — load alongside any other prompt.

Eliminates:
- Throat-clearing openers ("Great question!", "Certainly!")
- Emphasis crutches ("It's worth noting...", "Interestingly...")
- False profundity ("This speaks to a larger truth...")
- Manufactured drama ("But here's where it gets interesting...")
- Hedging language ("It could be argued that...")

**No arguments.**

---

## Example Sessions

**Deep analysis of a single book:**
```
prompts/get("librarian")
prompts/get("book-analysis", { "title": "The Brothers Karamazov" })
tools/call("get_details", { "media_type": "book", "title": "The Brothers Karamazov" })
tools/call("search_youtube", { "query": "Brothers Karamazov analysis" })
```

**Find what connects your favorites:**
```
prompts/get("librarian")
prompts/get("discover", { "theme": "what do my 5-star items have in common?" })
```

**Get a recommendation:**
```
prompts/get("librarian")
prompts/get("recommend", { "prompt": "something like Blade Runner 2049" })
```

**Full collection audit:**
```
prompts/get("librarian")
prompts/get("collection-review")
```

**Focused research on a director's work:**
```
prompts/get("librarian")
prompts/get("research", { "topic": "Denis Villeneuve films in my collection" })
```
