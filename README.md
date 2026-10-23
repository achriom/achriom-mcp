# Achriom MCP Server

The media memory layer for AI agents and their humans. Your AI client gets 55 tools to search your collection, add items, update ratings, preview music, curate lists, and find patterns across everything you've read, watched, listened to, and played.

Access your Achriom library from Claude, ChatGPT, or any MCP-compatible client.

**55 tools** · **15 prompts** · **8 media types** · **Free for all accounts**

## What You Get

Everything the in-app librarian uses, across books, movies, albums, TV shows, anime, podcasts, games, and manga:

- **Search**: by title, creator, genre, theme, or mood, with semantic search across the whole library
- **Item details**: full metadata with AI analysis and your notes
- **Collection stats**: patterns across ratings, genres, themes
- **Read and write**: update ratings, status, notes, and priority from any client
- **Lists**: cross-media lists you curate, private, shared by link, or public on your page
- **Dates and history**: started, finished and added dates (a year alone is fine), rewatches and rereads, with undo
- **Recommendations**: what people with overlapping taste also loved, across media, from other libraries in aggregate
- **Your public page**: favorites, reviews, and what stays hidden
- **Progress**: page counts, season and episode tracking, repeat plays and rereads
- **Games**: platforms, time to beat, screenshots, and franchises
- **Apple Music previews**: 30-second samples for albums
- **YouTube search**: trailers, interviews, video essays
- **Book search**: semantic search inside uploaded EPUBs

Plus 15 librarian prompts that shape how AI engages with your collection.

Game data is powered by IGDB.com.

## Connect

### Claude & Claude Desktop

The connector works on any Claude plan. The plugin needs a paid Claude plan (Pro, Max, Team, or Enterprise).

**Option 1: Plugin (recommended on paid plans)**

Includes MCP access plus Achriom-specific skills built for Claude.

1. Go to **Settings → Plugins**
2. Click **Add plugins**
3. Paste this URL and install:
   ```
   https://github.com/achriom/achriom-claude-plugin.git
   ```
4. Sign in with your Achriom account

**Option 2: Connector (MCP only, any plan)**

1. Go to **Settings → Connectors**
2. Click **Add** → **Add custom connector**
3. Enter the name **Achriom** and URL `https://mcp.achriom.com/mcp`
4. Click **Connect** and sign in with your Achriom account

### ChatGPT

No Developer Mode required.

1. Open the [Achriom ChatGPT app](https://chatgpt.com/apps/achriom/asdk_app_698a63a87aa081918a6532ccf4cbc1a1)
2. Sign in with your Achriom account

### Other MCP Clients

Use the MCP URL with OAuth:

```
https://mcp.achriom.com/mcp
```

Connection details at [www.achriom.com/connect](https://www.achriom.com/connect).

## In-App vs External

The in-app librarian knows things external clients don't: your conversation history, current research focus, how to present results visually. It's built for the experience.

External clients get the raw tools. Capable, but less context. Use the app when you want the full experience. Use MCP when you want your data somewhere else.

## Requirements

Free Achriom account required. MCP access is included on all plans.

## Technical Reference

For developers and agents: [docs/](docs/) contains detailed tool and prompt specifications.

## Find Us

- [Smithery](https://smithery.ai/servers/achriom/achriom): Remote MCP server
- [Glama](https://glama.ai/mcp/connectors/com.achriom.mcp/achriom): MCP directory
- [MCP.so](https://mcp.so/server/achriom/achriom): Community directory

## Links

- [Achriom](https://www.achriom.com)
- [MCP Documentation](https://www.achriom.com/mcp)
- [Support](mailto:hello@achriom.com)
