# Achriom

The media memory layer for AI agents and their humans. Books, movies, albums, TV shows, and anime — tracked, analyzed, and searchable from Claude, ChatGPT, or any MCP client.

**29 tools** · **15 skills** · **5 slash commands** · **5 media types** · **Free for all accounts**

---

## Claude / Cowork Plugin

The full librarian experience — skills, slash commands, and your collection — in one install.

### Install

In **Cowork** or **Claude Desktop**: go to Customize → Plugins → Browse, find Achriom, and click Install.

In **Claude Code**:
```bash
claude plugins add achriom/achriom-mcp
```

When prompted, enter your Achriom API key. Get it from [Settings → Connect to AI Tools](https://app.achriom.com/settings). The key is stored securely and wired up automatically — no manual config needed.

### What you get

**Skills** — activated automatically by the librarian based on context:

| Skill | When it activates |
|-------|-------------------|
| `librarian` | Every conversation about your collection |
| `book-analysis` | Literary analysis and author deep-dives |
| `movie-analysis` | Film craft, directors, cinematography |
| `music-analysis` | Albums, sound, production — always plays tracks |
| `show-analysis` | Series structure, seasonal arcs, ensemble dynamics |
| `anime-analysis` | Studios, sakuga, adaptation, cultural context |
| `recommendations` | "What should I read/watch next?" questions |
| `collection-insights` | Pattern recognition across your full library |
| `focused-research` | Deep study on a curated subset of items |
| `stop-slop` | Writing quality filter — always on |

**Slash commands:**

| Command | Description |
|---------|-------------|
| `/achriom:recommend` | Personalized recommendation by mood, theme, or similarity |
| `/achriom:deep-dive` | Full analysis of a specific book, film, album, show, or anime |
| `/achriom:discover` | Trace a theme or idea across your entire collection |
| `/achriom:research` | Focused deep-study mode on a curated subset |
| `/achriom:collection-review` | Full library audit — patterns, taste profile, gaps |

---

## Claude.ai Connector (Tools Only)

If you want just the MCP tools without the librarian skills and slash commands:

1. Go to **Settings → Connectors → Add custom connector**
2. Name: **Achriom**
3. URL: `https://mcp.achriom.com/mcp`
4. Auth: **OAuth** — sign in with your Achriom account

This gives you all 29 tools directly in Claude.ai conversations, without the plugin's skills and commands.

---

## ChatGPT

Requires Developer Mode (Plus or Pro).

1. **Settings → Apps** → Enable Developer mode
2. **Settings → Connectors** → Create
3. Name: **Achriom**, URL: `mcp.achriom.com/mcp`
4. Auth: **OAuth** → sign in with your Achriom account

---

## Other MCP Clients

For Cursor, Windsurf, and any HTTP MCP client:

```
https://mcp.achriom.com/mcp?api_key=YOUR_KEY
```

Get your key from [account settings](https://app.achriom.com/settings).

Ready-made config files: [examples/](examples/) (Claude Desktop, Cursor, VS Code).

---

## What the Tools Do

- **Search** — by title, creator, genre, theme, mood, or rating
- **Item details** — full metadata with AI analysis and your notes
- **Collection stats** — patterns across ratings, genres, themes, eras
- **Read and write** — update ratings, status, notes from any client
- **Apple Music previews** — 30-second samples inline
- **YouTube search** — trailers, interviews, video essays
- **Book search** — semantic search inside uploaded EPUBs and PDFs

Full reference: [docs/TOOLS.md](docs/TOOLS.md) · [docs/PROMPTS.md](docs/PROMPTS.md)

---

## Requirements

Free Achriom account required. MCP access included on all plans. Pro removes the 50-message cap.

[Sign up](https://app.achriom.com/signup) · [Settings](https://app.achriom.com/settings) · [Support](mailto:hello@achriom.com)

---

## Find Us

- [Smithery](https://smithery.ai/servers/achriom/achriom)
- [Glama](https://glama.ai/mcp/connectors/com.achriom.mcp/achriom)
- [MCP.so](https://mcp.so/server/achriom/achriom)
