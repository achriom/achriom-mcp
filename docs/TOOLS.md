# Achriom MCP Tools

Complete reference for all 43 tools available in the Achriom MCP server.

## Media Types

Most tools require a `media_type` parameter:
- `book`
- `movie`
- `album`
- `show`
- `anime`
- `podcast`
- `game`

A few tools are type-specific: `set_format` is books only, `set_progress` covers books, shows, and anime, and `get_show_progress` / `mark_tv_watched` are shows only.

---

## Search & Discovery

### `search`
Search your collection by title, creator, genre, or theme. Literal keyword match: the query must appear in the item's text, so use `search_library` for mood or concept questions.

```json
{
  "name": "search",
  "arguments": {
    "media_type": "book",
    "query": "science fiction"
  }
}
```

### `search_library`
Semantic search across your entire library by meaning, theme, or vibe. Searches every book, movie, album, show, anime, podcast, and game as one corpus. Use for cross-media questions like "things about grief".

```json
{
  "name": "search_library",
  "arguments": {
    "query": "noir mood",
    "limit": 10
  }
}
```

### `get_details`
Get full details for a specific item including AI analysis, themes, and your notes. Albums return a track list; box sets list every contained album.

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
Collection statistics: progress, rating distribution, genre and theme breakdown, timeline. Omit `media_type` for combined stats.

```json
{
  "name": "get_stats",
  "arguments": {
    "media_type": "book"
  }
}
```

### `lookup_item`
Search external databases before adding to your collection. Returns candidates with external IDs for disambiguation.

Sources: Books = Open Library, Movies = TMDB, Shows = TVDB (falls back to TMDB), Albums = Discogs, Anime = AniList, Games = IGDB.

```json
{
  "name": "lookup_item",
  "arguments": {
    "media_type": "movie",
    "title": "Dune",
    "year": 2021
  }
}
```

### `get_recently_added`
List items by when they were added to the library, newest first. Addition order, which differs from `get_timeline`.

```json
{
  "name": "get_recently_added",
  "arguments": {
    "media_type": "album",
    "limit": 8
  }
}
```

### `random_pick`
Pick random items for serendipitous discovery, optionally filtered.

```json
{
  "name": "random_pick",
  "arguments": {
    "media_type": "book",
    "filter": "unstarted",
    "count": 1
  }
}
```

---

## Collection Management

### `add_item`
Add a new item to your collection. Use `external_id` from `lookup_item` for precise matching. Games accept `platform` and `format` (physical or digital).

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

### `bulk_add_items`
Add up to 250 items in one call, mixed media types allowed. Use this instead of looping `add_item` for lists longer than three. Pass `year` and `external_id` where known, since bare titles are resolved by fuzzy text search. Returns counts for added, skipped duplicates, and failed, plus a per-item result list.

```json
{
  "name": "bulk_add_items",
  "arguments": {
    "items": [
      { "media_type": "game", "title": "Outer Wilds", "year": 2019 },
      { "media_type": "book", "title": "Dune", "year": 1965 }
    ]
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
Correct an item. `new_title` and `new_creator` save a personal override visible only to you. `new_external_id` relinks the item to a different catalog entry, which is the fix when the wrong film, show, or album was added.

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
Re-fetch metadata from external sources for an item whose data is incomplete. This repeats the same lookup, so use `edit_item` with `new_external_id` to fix a wrong match.

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

## Lists

Private, cross-media collections you curate. Items from any media type can share one list.

### `create_list`
Create a named list, with an optional one-line description.

```json
{
  "name": "create_list",
  "arguments": {
    "name": "Halloween marathon",
    "description": "Annual rewatch pile"
  }
}
```

### `add_to_list`
Add a library item to a list by title. Creates the list if it does not exist. The item must already be in the library.

```json
{
  "name": "add_to_list",
  "arguments": {
    "list_name": "Halloween marathon",
    "media_type": "movie",
    "title": "The Thing",
    "note": "Opens the night every year"
  }
}
```

### `remove_from_list`
Remove an item from a list. The item stays in the library.

```json
{
  "name": "remove_from_list",
  "arguments": {
    "list_name": "Halloween marathon",
    "title": "The Thing"
  }
}
```

### `get_list`
With a name, returns that list's items in order. Without a name, returns all lists with counts.

```json
{
  "name": "get_list",
  "arguments": {
    "name": "Halloween marathon"
  }
}
```

---

## Status, Ratings & Progress

### `update_status`
Change reading, watching, listening, or playing status.

**Status values by type:**
- Books: `unread`, `reading`, `finished`, `abandoned`
- Movies/Shows/Anime: `unwatched`, `watching`, `watched`, `abandoned`
- Albums: `unheard`, `listening`, `played`, `saved`
- Podcasts: `want_to_listen`, `listening`, `caught_up`, `dropped`
- Games: `unplayed`, `playing`, `played`, `saved`, `on_hold`, `abandoned`

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
Set a rating from 0.5 to 5 stars, in half-star increments.

```json
{
  "name": "update_rating",
  "arguments": {
    "media_type": "movie",
    "title": "Blade Runner",
    "rating": 4.5
  }
}
```

### `update_notes`
Add or update personal notes. Replaces existing notes.

```json
{
  "name": "update_notes",
  "arguments": {
    "media_type": "album",
    "title": "Kid A",
    "notes": "The turn after OK Computer, a completely different sound"
  }
}
```

### `set_priority`
Set an item's priority: `high` for what you want next, `normal` for standard backlog, `low` for speculative or distant.

```json
{
  "name": "set_priority",
  "arguments": {
    "media_type": "game",
    "title": "Disco Elysium",
    "priority": "high"
  }
}
```

### `set_format`
Set how a book was read: `print`, `ebook`, `audiobook`, or `ereader`.

```json
{
  "name": "set_format",
  "arguments": {
    "title": "Dune",
    "format": "audiobook"
  }
}
```

### `set_progress`
Update how far you are through an in-progress item. Books take `current_page`, shows take `current_season` and `current_episode`, anime takes `episodes_watched`.

```json
{
  "name": "set_progress",
  "arguments": {
    "media_type": "book",
    "title": "Dune",
    "current_page": 210
  }
}
```

### `mark_tv_watched`
Mark TV progress. Season plus episode marks that episode, `through: true` marks everything up to it, season alone marks the whole season, neither marks the whole show. Set `watched: false` to unmark.

```json
{
  "name": "mark_tv_watched",
  "arguments": {
    "title": "The Wire",
    "season": 2,
    "episode": 6,
    "through": true
  }
}
```

### `get_show_progress`
Read a show's season-by-season watch progress and the next unwatched episode.

```json
{
  "name": "get_show_progress",
  "arguments": {
    "title": "The Wire"
  }
}
```

### `log_event`
Log a completion or a repeat with a date. The first finish is tracked by status; this records rewatches, rereads, and relistens so they appear in history and stats.

```json
{
  "name": "log_event",
  "arguments": {
    "media_type": "movie",
    "title": "Heat",
    "event_type": "rewatched",
    "event_date": "2026-08-01"
  }
}
```

### `bulk_update_status`
Update status for multiple items at once, filtered by `all`, `rated`, or `unrated`.

```json
{
  "name": "bulk_update_status",
  "arguments": {
    "media_type": "book",
    "status": "finished",
    "filter": "rated"
  }
}
```

### `get_by_status`
Filter collection by status. Pass `all` to return items regardless of status.

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
Show items started and finished over time.

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
Sample any album from Apple Music without adding it to your library.

```json
{
  "name": "preview_album",
  "arguments": {
    "title": "In Rainbows",
    "artist": "Radiohead"
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
Semantic search within uploaded EPUB/PDF files, using AI embeddings to find relevant passages.

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
Read a specific section by line numbers, up to 200 lines.

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
Information about the current research scope (focused research mode).

### `expand_research_scope`
Add an item to the current research corpus.

### `get_context`
User context for adaptive conversation: lifecycle stage and behavioral signals.

### `get_signals`
Behavioral signals: theme repetition, consumption gaps, and recent activity.

### `search_conversations`
Semantic search across past conversations, finding conceptually related ones rather than keyword matches alone.

### `show_item`
Navigate to an item's detail page. Works on all clients: web app, iOS app, and Claude Desktop.

---

## Profile & Memory

### `get_user_profile`
Persistent profile built from past conversations: taste patterns, key facts, cross-media connections, and preferences.

### `save_insight`
Store a lasting insight about your patterns and preferences, categorized as `taste_pattern`, `key_fact`, `cross_media_connection`, or `preference`.

### `get_taste_portrait`
Your full Taste Portrait: generated archetype, essence, core tension, preoccupations, the recommendation you do not own yet, and your blind spot. Unlocks at 10 items.

---

## Data Sources

Books come from Open Library, movies from TMDB, shows from TVDB with a TMDB fallback, albums from Discogs, anime from AniList, and album previews from Apple Music. Game data is powered by IGDB.com.
