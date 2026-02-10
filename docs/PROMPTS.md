# Achriom MCP Prompts

Prompts define the librarian's personality and analysis methodologies. Load them to shape how the AI engages with your collection.

## Usage

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
```

---

## Core Persona

### `librarian`
The core librarian personality. Activates warm, insightful engagement with media collections.

**Key behaviors:**
- Curious, not cataloging - notices patterns, makes connections
- Proactive - surfaces interesting observations without being asked
- Demonstrates rather than describes - plays music, shows videos, displays covers

**No arguments.**

---

## Analysis Skills

### `book-analysis`
Deep literary analysis methodology.

**Covers:**
- Themes and meaning
- Author intent and biography
- Historical and cultural context
- Connections to other books in your collection

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `title` | No | Book to analyze |

### `movie-analysis`
Film analysis methodology.

**Covers:**
- Cinematography and visual language
- Director style and filmography
- Performance analysis
- Cultural context and reception

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `title` | No | Film to analyze |

### `music-analysis`
Album and artist discussion. **Always plays tracks.**

**Covers:**
- Sound and production choices
- Artist evolution and discography
- Lyrics and themes
- Cultural moment and impact

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `title` | No | Album to analyze |

### `show-analysis`
TV series analysis for long-form storytelling.

**Covers:**
- Show structure (serialized vs procedural)
- Character arcs across seasons
- Showrunner vision
- Ensemble dynamics

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `title` | No | Show to analyze |

### `anime-analysis`
Animation-specific analysis.

**Covers:**
- Studio style and animation quality
- Sakuga moments
- Adaptation fidelity (manga, light novel, etc.)
- Japanese cultural context

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `title` | No | Anime to analyze |

---

## Cross-Collection Skills

### `recommendations`
Cross-media recommendation methodology.

**Philosophy:**
- Mines your collection first (unread/unwatched gems)
- Bridges across media types by mood and theme
- Respects your taste signals (ratings, notes)

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `mood` | No | Mood or vibe to match |
| `media_type` | No | Preferred type: book, movie, album, show, anime |

### `collection-insights`
Pattern recognition across your entire library.

**Identifies:**
- Thematic clusters across media types
- Era and genre preferences
- Creator loyalty patterns
- Gaps and blind spots

**No arguments.**

### `focused-research`
Deep analysis mode for a curated subset.

**Behavior:**
- Works only within defined scope
- No speculation outside the corpus
- User controls expansion

**Arguments:**
| Name | Required | Description |
|------|----------|-------------|
| `scope` | No | Comma-separated titles to include |

---

## Quality Filter

### `stop-slop`
Writing quality filter. **Always active.**

Eliminates AI writing patterns:
- No throat-clearing openers
- No false profundity
- No manufactured drama
- No hedging language

**No arguments.**

---

## Example Flow

1. Load the librarian persona:
   ```
   prompts/get("librarian")
   ```

2. Get collection overview:
   ```
   tools/call("get_stats", { "media_type": "book" })
   ```

3. Deep dive on a specific book:
   ```
   prompts/get("book-analysis", { "title": "The Brothers Karamazov" })
   tools/call("get_details", { "media_type": "book", "title": "The Brothers Karamazov" })
   tools/call("search_youtube", { "query": "Brothers Karamazov analysis" })
   ```

4. Get a recommendation:
   ```
   prompts/get("recommendations", { "mood": "contemplative" })
   tools/call("get_by_rating", { "media_type": "book", "min_rating": 4 })
   ```
