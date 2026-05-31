# AI Engineering Learnings

A distilled, AI-context-ready set of notes on **what people are actually building with LLMs in 2026** — derived from ~575 curated X (Twitter) bookmarks, clustered by topic and enriched with external research.

Designed to be loaded as a knowledge source for an AI assistant (Claude Project, Cursor `@docs`, ChatGPT custom GPT, etc.) so the assistant inherits the technical worldview without you having to re-explain what's going on in the ecosystem.

## What's here

| File | Purpose |
|---|---|
| `00-overview.md` | The corpus at a glance — topic distribution, cross-cutting themes |
| `01-ai-engineering.md` | The biggest file. Claude Code workflows, agentic loops, MCP, prompting, the "AI as remote workforce" thesis |
| `02-coding-tools.md` | Specific tools, libs, dev setups. The "levelsio Hetzner stack", Claude Code skills, PDF parsing, GPU rental, the boring-infra-wins philosophy |
| `03-people-to-follow.md` | Authors producing repeatedly signal-rich content in the AI/coding space |
| `04-key-threads.md` | The handful of threads worth opening in full — Burkov on attention, levie on enterprise AI, steipete on OpenClaw, the Spotify "Honk" story |

## How to use

**With Claude.ai**: Create a Project, drag the markdown files into the Project knowledge. Claude now reasons with this context.

**With Cursor**: `@docs` → add this folder. Cursor will reference it during coding sessions.

**With ChatGPT custom GPT**: Upload files as knowledge documents.

**Plain context-stuffing**: Concatenate all the files and paste at the top of your chat as background.

If you want the leanest possible context, just load `00-overview.md` + `01-ai-engineering.md` — that's about 60% of the actionable content at 1/3 the size.

## How this was built

1. **Sync**: Used the [fieldtheory CLI](https://github.com/afar1/fieldtheory-cli) to pull X bookmarks into local JSON
2. **Cluster**: Scripted topic clustering by keyword across all 575 bookmarks
3. **Distill**: Read every bookmark, summarized the signal portions by topic, enriched with external context where needed (e.g. classical references, tool documentation, scholarly context)
4. **Filter for public release**: Removed personal/political/local-civic content, kept the technical AI/coding material

This repo is the **technical subset only** — opinions, frameworks, and concrete tooling. The original bookmark stream is more personal and not included here.

## Worldview to know

The corpus reflects a particular slice of 2026 tech opinion:

- **Claude Code is the central productivity tool.** Not just "an AI" — *the* IDE-shaped agentic surface around which workflows orbit.
- **Agentic loops are mainstream.** Not experimental. Ralph Wiggum loops, multi-instance Claude Code orchestration, plan-mode → Codex pipelines are how people actually work now.
- **MCP is the integration glue.** Treating MCP servers as the default plumbing between LLMs and tools.
- **"Boring infrastructure wins."** Anti-Kubernetes-for-its-own-sake. Pro-ECS, pro-Hetzner-VPS, pro-one-Dockerfile.
- **Vibe-coding is real but localhost-syndrome is real too.** The bookmarks hold both takes simultaneously.
- **The leverage hierarchy is labor → capital → code/media → AI.** AI compounds existing leverage, doesn't replace it.

## Updating

This is a snapshot from late May 2026. AI tooling moves fast — re-sync your own bookmarks and rebuild periodically with the same approach. The clustering scripts and prompt templates that produced this are not in the repo (they're personal) but the methodology is:

1. Export your X bookmarks (fieldtheory, X API, or the official X data archive)
2. Cluster by topic keywords
3. Read each cluster, distill recurring signals
4. Enrich with external context where the bookmarks reference things by name only

## License

MIT — use any way you want. Attribution appreciated but not required.
