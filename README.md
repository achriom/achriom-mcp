# Achriom MCP Server

The media memory layer for AI agents and their humans. Your AI client gets 29 tools to search your collection, add items, update ratings, preview music, and find patterns across everything you've read, watched, and listened to.

Access your Achriom library from Claude, ChatGPT, or any MCP-compatible client.

**29 tools** · **10 prompts** · **5 media types** · **Free for all accounts**

## What You Get

Everything the in-app librarian uses:

- **Search** — By title, creator, genre, theme, or mood
- **Item details** — Full metadata with AI analysis and your notes
- **Collection stats** — Patterns across ratings, genres, themes
- **Read and write** — Update ratings, status, notes from any client
- **Apple Music previews** — 30-second samples for albums
- **YouTube search** — Trailers, interviews, video essays
- **Book search** — Semantic search inside uploaded EPUBs

Plus 10 librarian prompts that shape how AI engages with your collection.

## Connect

### Claude & Claude Desktop

Requires a paid Claude plan (Pro, Max, Team, or Enterprise).

**Option 1: Plugin (recommended)**

Includes MCP access plus Achriom-specific skills built for Claude.

1. Go to **Settings → Plugins**
2. Click **Add plugins**
3. Paste this URL and install:
   ```
   https://github.com/achriom/achriom-claude-plugin.git
   ```
4. Sign in with your Achriom account

**Option 2: Connector (MCP only)**

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

Connection details at [app.achriom.com/mcp](https://app.achriom.com/mcp).

## In-App vs External

The in-app librarian knows things external clients don't — your conversation history, current research focus, how to present results visually. It's built for the experience.

External clients get the raw tools. Capable, but less context. Use the app when you want the full experience. Use MCP when you want your data somewhere else.

## Requirements

Free Achriom account required. MCP access is included on all plans.

## Technical Reference

For developers and agents: [docs/](docs/) contains detailed tool and prompt specifications.

## Find Us

- [Smithery](https://smithery.ai/servers/achriom/achriom) — Remote MCP server
- [Glama](https://glama.ai/mcp/connectors/com.achriom.mcp/achriom) — MCP directory
- [MCP.so](https://mcp.so/server/achriom/achriom) — Community directory

## Links

- [Achriom](https://www.achriom.com)
- [MCP Documentation](https://www.achriom.com/mcp)
- [Support](mailto:hello@achriom.com)
