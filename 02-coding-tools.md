# Coding Tools & Dev Workflow

A curated list of concrete tools, libraries, and setups mentioned across the bookmarks — with enough context to know what each is for and whether to try it.

## The @levelsio "indie hacker dev" stack

@levelsio is the most-bookmarked dev-tooling voice in the corpus. His canonical setup:

- **Hetzner $5/mo VPS** (or DigitalOcean) as the primary dev environment
- **Termius** as the SSH client — each site is a profile (e.g., `hoodmaps.com` is a profile)
- **tmux session per site**, auto-attached on login via a startup snippet in the Termius profile
- **Claude Code installed natively** on the VPS:
  ```
  curl -fsSL claude.ai/install.sh | bash
  ```
  Or via npm: `npm install -g @anthropic-ai/claude-code`
- The native install bypasses npm entirely (per @maxast, @nachoiacovino)

The thesis: **treat the VPS as a "fun hobby server", no infra worship**.

## Claude Code ecosystem

### Plugins / skills mentioned

| Tool | What it does | Author(s) |
|---|---|---|
| **Ralph Wiggum** | Autonomous agentic loop — goal condition + iteration | @arvidkahl, multiple |
| **Ralph Loop TUI** | TUI wrapper for Ralph loops | @intheworldofai |
| **Cartographer** | Parallel Sonnet subagents → entire codebase architecture doc | @KingBootoshi |
| **/simplify** | Removes >90% of slop from a working solution | @iamsahaj_xyz |
| **/prompt** | Brain dump → coherent instructions | @cblatts |
| **/review-plan** | Multi-agent plan critique | @cblatts |
| **/goal** | Combined with `react-doctor` for iterative React fixes | @ParthJadhav8 |
| **Autonomous Dogfooding** | Agent uses your app the way users do; outputs structured bug report | @ctatedev |
| **Figma → Claude Code** | Figma integration; "design has been freed" | @Av1dlive |

### CLAUDE.md tips

@mattpocockuk: "Here are my CLAUDE.md additions for making plan mode 10x better. Before: unreadably long plans. After: concise, useful plans with followup questions." (Specific additions in his linked content.)

### Hooks pattern

@JorgeCastilloPr: WarCraft 3 sounds on Claude hooks to alert task completion / permission needs. Hooks are powerful for ambient awareness without watching the terminal.

## Codex 5.5 use cases (per @cjzafir)

- Made internet faster
- Made local 6B SLM 3x faster
- Made MacBook Pro faster
- Made lightweight suite to write & test Metal kernels
- Made a skill to communicate with Claude Code in realtime
- Made pipeline to generate SFT dataset

Codex is positioned as the "second AI" in many workflows (plan in Claude Code → execute in Codex → critique in Claude Code).

## PDF / document processing

| Tool | What | Why use it |
|---|---|---|
| **LiteParse v2** | Rust-based PDF parser (LlamaIndex) | 100x faster than pymupdf/pypdf/markitdown/pdftotext; works in Rust/JS/TS/Python + WASM |
| **MarkItDown** | Document → Markdown (Microsoft) | Lightweight Python lib for prepping anything for LLM consumption |
| **LangExtract** | Structured extraction (Google) | Open source; maps every entity to source location; handles 100+ page docs |

## Cursor IDE notes

- **Cursor Rules repo** (per @deedydas) — precise rules/prompts for Tauri, React, Chrome extensions etc. Makes AI-generated code much better.
- **plan.mdc** file pattern (per @adxmsardo) — Cursor planning thoroughly based on requirements is "a game changer"
- **15 rules of vibe coding with Cursor** (per @rileybrown) — exists as a reference

## Infrastructure / DevOps

### Linux commands (per @livingdevops's 13-year-collection)
```
ps aux | grep {process}   # Find sneaky processes
lsof -i :{port}            # Who's hogging that port?
df -h                       # We're out of space
netstat -tulpn             # Network connection detective
kubectl get pods | grep    # K8s pod search
```

### Docker philosophy

@brankopetric00 is a recurring voice on "boring infra wins":
- $30M ARR company shipping with: **one Dockerfile, one docker-compose for local dev, plain ECS in production. No Kubernetes, no service mesh, no drama.**
- "Your Docker image is 2.3GB. You're shipping an entire OS to run a Python script that sends emails."

### Kubernetes primer (per @twtayaan)

A clean "33 Timeless Kubernetes Concepts" thread exists in the bookmarks if you need a refresher. Key terms:
- Pod (atomic unit, one+ containers sharing network/storage)
- Node (worker machine)
- Cluster (nodes + control plane)
- Namespace (virtual cluster within a cluster)
- ...and 28 more

## GPU rental

**vast.ai** as the canonical "cheap GPU" alternative (per @inboxfelon):
- A100 at $0.50/hr vs $4/hr on AWS
- For training your own models, running local Llama/Mistral, anything that doesn't need AWS's compliance bells

## Bun rewrite-in-Rust

@jarredsumner is rewriting Bun (960,000 LOC) into Rust with Claude help. **Not** "Claude rewrite Bun." It's a structured human+AI rewrite. Worth following if you're tracking the future of JS runtimes or AI-assisted large refactors.

## Browser automation / scraping

- **fieldtheory CLI** (afar1/fieldtheory-cli on GitHub) — syncs X bookmarks locally, the tool used to extract this corpus
- General lesson from scraping experiments: X returns HTTP 402 to unauthenticated tweet fetches now; logged-in browser automation works but requires the Chrome `Allow JavaScript from Apple Events` toggle on macOS, and multiple Chrome profiles complicate AppleScript targeting

## Stack signals worth noting

The implicit stack the bookmarks orbit around:
- **Language**: TypeScript / Python / Rust (more Rust than expected — Bun rewrite, LiteParse rewrite)
- **Runtime**: Node 20+, Bun, Deno mentioned but secondary
- **AI infra**: Claude Code primary, Codex secondary, Cursor as IDE alternative
- **Hosting**: Cloudflare Pages/Workers, Railway, Hetzner VPS, ECS (boring), vast.ai for GPU
- **Data layer**: SQLite/Postgres for app data; Egnyte/Panzura for file storage in AECO context
- **Integration**: MCP servers as the default plumbing for agent-to-tool

## Things explicitly disrecommended

- "Non-technical teams shipping production code" without review (@Goosewin: among the 3 phrases heard before disaster)
- 2.3GB Docker images for Python email scripts
- Kubernetes when ECS would do
- AWS GPU prices when vast.ai exists
- Manually opening merge conflicts when Linus Torvalds's git lecture exists
