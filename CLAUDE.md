# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Private content tooling for the **Remy Dova** persona — a lofi musician for introverts. Two standalone HTML tools:

- `newsletter-generator.html` — generates Substack "quiet notes" newsletter content (issue copy, Substack Notes posts, Pinterest pins)
- `video-generator.html` — generates short-form video scripts with CapCut production instructions, hook lines, text cards, and bilingual captions (EN/JP)

## Running the tools

No build step. Open either HTML file directly in a browser. No server, no npm, no dependencies to install.

## Architecture

Both tools are **self-contained single-file HTML apps** with embedded CSS and vanilla JS. They share:

- **Identical design system** via CSS custom properties: `--bg:#0c0c18`, `--surf:#13131f`, `--surf2:#1a1a2e`, `--amber:#d4956a`, `--teal:#7fb5a0`, `--lav:#9b8bb4`, `--text:#e8ddd0`
- **Fonts**: Playfair Display (serif headings), Lora (body), Caveat (cursive labels/UI) — loaded from Google Fonts
- **Claude API calls** routed through a Cloudflare Worker proxy at `https://remy-claude-proxy.gkstutler.workers.dev`, using model `claude-sonnet-4-20250514`. Both tools POST `{model, max_tokens, messages}` and parse the response as structured JSON.
- **Fallback content** (`getFallback()`) used when the API call fails — both tools handle errors gracefully and display static placeholder content instead.

## Remy Dova persona

The Claude prompts embed a detailed character definition. Key constraints that must be preserved across any prompt changes:

- Always lowercase (except proper nouns)
- Never political, never news, never social commentary
- Intimate letter voice — not a blog post
- Core world: Miso (tabby cat), Juni (illustrator friend), Theo (high school friend), MIDI keyboard music 9pm–midnight, French press coffee, crochet, ink/watercolor drawing
- Muses: Studio Ghibli, Japanese concept of "ma", SNES soundtracks, October light, rain, old bookshops
- Tagline: "it's okay to be you."

## Output format

Both tools instruct Claude to return **only valid JSON** (no markdown fences, no preamble). The response is parsed with `JSON.parse(raw.replace(/\`\`\`json|\`\`\`/g,'').trim())`.

- Newsletter output fields: `subject`, `title`, `opening`, `section1_heading`, `section1_body`, `quote`, `section2_heading`, `section2_body`, `prompt`, `closing`, `ps`, `note_wednesday`, `note_friday`, `pins[]`
- Video output fields: `hook`, `cards[]`, `caption_en`, `caption_jp`
