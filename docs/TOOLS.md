# Achriom MCP Tools

Complete reference for all 29 tools available in the Achriom MCP server.

## Media Types

Most tools require a `media_type` parameter:
- `book`
- `movie`
- `album`
- `show`
- `anime`

---

## Search & Discovery

### `search`
Search your collection by title, creator, genre, or theme.

```json
{
  "name": "search",
  "arguments": {
    "media_type": "book",
    "query": "science fiction"
  }
}
```

### `get_details`
Get full details for a specific item including AI analysis, themes, and your notes.

```json
{
  "name": "get_details",
  "arguments": {
    "media_type": "movie",
    "title": "Blade Runner"
  }
}
```

### `get_stats`
Collection statistics: counts, ratings distribution, progress, timeline.

```json
{
  "name": "get_stats",
  "arguments": {
    "media_type": "book"
  }
}
```

### `lookup_item`
Search external databases (Open Library, TMDB, Discogs, AniList) before adding to your collection. Returns candidates with external IDs for disambiguation.

```json
{
  "name": "lookup_item",
  "arguments": {
    "media_type": "movie",
    "query": "Dune"
  }
}
```

### `random_pick`
Get a random item from your collection, optionally filtered.

```json
{
  "name": "random_pick",
  "arguments": {
    "media_type": "book",
    "status": "unread"
  }
}
```

---

## Collection Management

### `add_item`
Add a new item to your collection. Use `external_id` from `lookup_item` for precise matching.

```json
{
  "name": "add_item",
  "arguments": {
    "media_type": "movie",
    "title": "Dune",
    "external_id": "438631"
  }
}
```

### `delete_item`
Remove an item from your collection.

```json
{
  "name": "delete_item",
  "arguments": {
    "media_type": "book",
    "title": "The Great Gatsby"
  }
}
```

### `edit_item`
Update item metadata (title, creator, external_id).

```json
{
  "name": "edit_item",
  "arguments": {
    "media_type": "album",
    "title": "OK Computer",
    "new_title": "OK Computer OKNOTOK"
  }
}
```

### `re_enrich`
Re-fetch metadata from external sources.

```json
{
  "name": "re_enrich",
  "arguments": {
    "media_type": "book",
    "title": "1984"
  }
}
```

---

## Status & Ratings

### `update_status`
Change reading/watching/listening status.

**Status values by type:**
- Books: `unread`, `reading`, `finished`, `abandoned`
- Movies/Shows/Anime: `unwatched`, `watching`, `watched`, `abandoned`
- Albums: `unheard`, `listening`, `played`, `saved`

```json
{
  "name": "update_status",
  "arguments": {
    "media_type": "book",
    "title": "Dune",
    "status": "reading"
  }
}
```

### `update_rating`
Set a 1-5 star rating.

```json
{
  "name": "update_rating",
  "arguments": {
    "media_type": "movie",
    "title": "Blade Runner",
    "rating": 5
  }
}
```

### `update_notes`
Add or update personal notes.

```json
{
  "name": "update_notes",
  "arguments": {
    "media_type": "album",
    "title": "Kid A",
    "notes": "The transition from OK Computer - completely different sound"
  }
}
```

### `bulk_update_status`
Update status for multiple items at once.

```json
{
  "name": "bulk_update_status",
  "arguments": {
    "media_type": "book",
    "titles": ["Book 1", "Book 2"],
    "status": "finished"
  }
}
```

### `get_by_status`
Filter collection by status.

```json
{
  "name": "get_by_status",
  "arguments": {
    "media_type": "book",
    "status": "reading"
  }
}
```

### `get_by_rating`
Filter collection by rating range.

```json
{
  "name": "get_by_rating",
  "arguments": {
    "media_type": "movie",
    "min_rating": 4
  }
}
```

### `get_timeline`
Show items started/finished over time.

```json
{
  "name": "get_timeline",
  "arguments": {
    "media_type": "book"
  }
}
```

---

## Media Playback

### `get_track_previews`
Get 30-second audio previews for album tracks in your library.

```json
{
  "name": "get_track_previews",
  "arguments": {
    "album_title": "OK Computer",
    "max_tracks": 5
  }
}
```

Returns `[audio:URL|TITLE|ARTIST|ARTWORK]` tags for inline playback.

### `preview_album`
Sample any album from Apple Music without adding to your library.

```json
{
  "name": "preview_album",
  "arguments": {
    "query": "Radiohead In Rainbows"
  }
}
```

### `search_youtube`
Find related videos: trailers, interviews, analysis, performances.

```json
{
  "name": "search_youtube",
  "arguments": {
    "query": "Blade Runner analysis"
  }
}
```

Returns `[youtube:VIDEO_ID]` tags for inline display.

---

## Book Content

### `search_book_content`
Semantic search within uploaded EPUB/PDF files.

```json
{
  "name": "search_book_content",
  "arguments": {
    "book_title": "1984",
    "query": "doublethink"
  }
}
```

### `read_book_section`
Read a specific section by line numbers.

```json
{
  "name": "read_book_section",
  "arguments": {
    "book_title": "1984",
    "start_line": 100,
    "end_line": 150
  }
}
```

---

## Research & Context

### `get_scope_info`
Information about current research scope (focused research mode).

### `expand_research_scope`
Add an item to the current research corpus.

### `get_context`
User context for adaptive conversation: lifecycle stage, activity signals.

### `get_signals`
Behavioral signals: theme repetition, consumption gaps, activity patterns.

### `search_conversations`
Semantic search across past conversations.

### `show_item`
Navigate to an item's detail page (works on web, iOS, Claude Desktop).

---

## Profile & Memory

### `get_user_profile`
Persistent profile distilled from past conversations.

### `save_insight`
Store a lasting insight about user patterns and preferences.
