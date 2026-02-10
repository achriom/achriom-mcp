# Achriom MCP Server

The media memory layer for AI agents and their humans. Track books, movies, music, TV, and anime.

Access your Achriom library from Claude, ChatGPT, or any MCP-compatible client.

**29 tools** · **10 prompts** · **5 media types**

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

### Claude

1. Click **Search and tools** (lower left of chat)
2. Select **Add connectors**
3. Click **Add custom connector**
4. Paste your MCP link from Achriom settings
5. Click **Connect**

### ChatGPT

Requires Developer Mode (Plus/Pro).

1. Settings → Apps → Advanced settings → Enable Developer mode
2. Settings → Connectors → Create
3. Name: **Achriom**
4. URL: `mcp.achriom.com/mcp`
5. Authentication: **OAuth**
6. Click Connect and sign in

### Other Clients

Add to your MCP config:

```json
{
  "mcpServers": {
    "achriom": {
      "type": "http",
      "url": "https://mcp.achriom.com/mcp?api_key=YOUR_API_KEY"
    }
  }
}
```

Get your API key in [account settings](https://app.achriom.com/settings).

## In-App vs External

The in-app librarian knows things external clients don't — your conversation history, current research focus, how to present results visually. It's built for the experience.

External clients get the raw tools. Capable, but less context. Use the app when you want the full experience. Use MCP when you want your data somewhere else.

## Requirements

MCP access requires an Achriom Pro subscription.

## Technical Reference

For developers and agents: [docs/](docs/) contains detailed tool and prompt specifications.

## Find Us

- [Smithery](https://smithery.ai) — Remote MCP server
- [Glama](https://glama.ai/mcp/servers) — MCP directory
- [MCP.so](https://mcp.so) — Community directory

## Links

- [Achriom](https://www.achriom.com)
- [MCP Documentation](https://www.achriom.com/mcp)
- [Support](mailto:hello@achriom.com)
