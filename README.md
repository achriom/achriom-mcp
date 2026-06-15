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

1. Go to **Settings → Connectors**
2. Click **Add custom connector**
3. Enter the name **Achriom** and your MCP URL from [Achriom settings](https://app.achriom.com/settings)
4. Follow the auth prompts to connect

### ChatGPT

Requires Developer Mode (Plus or Pro).

1. **Settings → Apps** → Enable Developer mode
2. **Settings → Connectors** → Create
3. Name: **Achriom**
4. URL: `mcp.achriom.com/mcp`
5. Auth: **OAuth** → sign in with your Achriom account

### Other MCP Clients

For Cursor, Windsurf, and any HTTP MCP client, use your personal API key:

```
https://mcp.achriom.com/mcp?api_key=YOUR_KEY
```

Get your API key from [account settings](https://app.achriom.com/settings).

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
