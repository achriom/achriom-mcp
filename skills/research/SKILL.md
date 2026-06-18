---
name: research
description: Enter focused research mode on a curated set of items from your collection
argument-hint: "<topic or list of items>"
allowed-tools:
  - mcp__plugin_achriom_achriom__search
  - mcp__plugin_achriom_achriom__get_details
  - mcp__plugin_achriom_achriom__get_scope_info
  - mcp__plugin_achriom_achriom__expand_research_scope
  - mcp__plugin_achriom_achriom__search_book_content
  - mcp__plugin_achriom_achriom__read_book_section
  - mcp__plugin_achriom_achriom__get_track_previews
  - mcp__plugin_achriom_achriom__search_youtube
  - mcp__plugin_achriom_achriom__save_insight
---

# /research — Focused Research Mode

Deep, contained research on a curated subset of your library. Select a few items, close the door, and study them together without distraction from the rest of the collection.

## Invocation

```
/research
/research my three books about food and culture
/research comparing Miyazaki's films in my collection
/research the relationship between Radiohead and Murakami
```

## Workflow

### Step 1: Define the Corpus

Determine what items belong in the research session:

**If the user named specific items:**
- Search for each item and confirm it's in the collection
- Load details for each

**If the user named a topic:**
- Search across media types for relevant items
- Present the candidates and let the user confirm the corpus
- "I found these 6 items related to [topic]. Should I include all of them, or do you want to narrow it down?"

**If no items specified:**
- Ask what they want to research
- Help them define the corpus through conversation

### Step 2: Enter Research Mode

Using the **focused-research** skill, establish containment:

```
get_scope_info()                    # All items in research scope
get_details(media_type, title)      # For each item in corpus
```

For small corpora (under 10 items), load full details for everything. For larger sets, load details as needed during analysis.

Announce the scope clearly:

```
**Research corpus:** [N] items
- [Title 1] ([media type])
- [Title 2] ([media type])
- [Title 3] ([media type])

I'll focus exclusively on these items. Ask me to expand if you want to bring something else in.
```

### Step 3: Identify the Research Question

What are we studying here? The user may have stated it explicitly or it may emerge from the corpus:

- **Comparative**: How do these items approach [theme] differently?
- **Chronological**: How did this idea evolve across these works?
- **Influence**: How did one creator influence another?
- **Synthesis**: What do these items illuminate together that they can't alone?

### Step 4: Conduct the Research

Using **focused-research** skill methodology:

**Comparative analysis:**
- Shared themes, contrasting perspectives
- How each item contributes a different angle on the same idea

**Deep reading (for books with uploaded content):**
```
search_book_content(book_title="...", query="concept")
```
- Quote directly from texts
- Cross-reference passages across multiple books

**Visual/audio analysis:**
```
search_youtube(query="relevant video essay or performance")
get_track_previews(album_title="...")
```

**External context:**
- Research production history, author interviews, critical reception
- Use web search to fill gaps in context

### Step 5: Present Findings

Frame as scholarly but accessible. Quote the works. Make connections explicit. End with research-oriented follow-up prompts.

## Output Format

```
## Research: [Topic or Theme]

**Corpus:** [N] items — [brief list]
**Central question:** [What we're investigating]

---

### [Finding 1 — The Core Insight]

[2-3 paragraphs developing the main insight from studying these items together.
Quote from works where possible. Reference specific scenes, passages, tracks.]

[Embedded media if relevant]

### [Finding 2 — The Unexpected Connection]

[Something that only becomes visible when you study these items side by side]

### [Finding 3 — The Tension]

[Where these items disagree or approach the theme from opposing directions.
Tensions are often more interesting than agreements.]

---

### Synthesis

[1-2 paragraphs pulling it together. What do these items illuminate collectively?
What would be lost if you studied any one of them alone?]

### Open Questions

[What this research raises but doesn't resolve. Invitations for further exploration.]

<!-- SUGGESTIONS: Find passages about [concept] in [book] | Compare how [item A] and [item B] handle [theme] | Expand the corpus with [suggested addition] -->
```

## Notes

- Containment is sacred. Do not reference items outside the corpus unless the user asks to expand
- The user drives corpus expansion — never proactively suggest adding items
- If the corpus is just one item, this becomes a deep dive. Suggest `/deep-dive` instead, or proceed as a single-item study
- For book-heavy corpora, lean heavily on `search_book_content()` — direct quotes make research tangible
- End each response with prompts that push the research forward, not sideways
