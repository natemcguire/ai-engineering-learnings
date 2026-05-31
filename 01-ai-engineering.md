# AI Engineering & LLM Workflows

The dominant theme across the bookmarks: how people are actually building with LLMs in 2026, with a heavy lean toward **Claude Code** as the primary IDE/agentic surface.

## The agentic workflow shift (the big picture)

### From "AI as autocomplete" to "AI as remote employee"

The pattern recurring across many bookmarks:

> **"You're not supposed to watch Claude Code work. You're supposed to wake up and review what it shipped."** — Anthropic engineer (paraphrased from a Code w/ Claude talk)

> **"How would we build software in the future if tokens don't matter?"** — @steipete (Peter Steinberger), describing OpenClaw — running ~100 Codex instances in the cloud reviewing every PR and issue.

> **"Spotify's best developers haven't written a single line of code since December, thanks to an internal AI system called 'Honk' powered by Claude Code. The company shipped 50+ new features in 2025. Engineers fix bugs and deploy features directly from Slack."** — @milan_milanovic

The throughline: **best practice is no longer human-in-the-loop, it's human-as-reviewer**. You set up agentic loops, kick them off, sleep, and review the output.

### Specific patterns worth knowing

**The "plan-mode-then-codex" pipeline** (per @0xgaut):
1. Use Claude Code plan mode to think out loud and get thoughts on paper
2. Ask Claude to write a prompt for Codex
3. Send to Codex, let it run
4. Have Claude critique the Codex output

**Multi-instance orchestration** (per @0xgaut):
- 15 background agents + 10 Claude Code instances on screen simultaneously
- Operator-as-conductor model — don't need to know what each is doing, just route work

**The "Ralph Wiggum" / Ralph loop pattern** (per @arvidkahl, @intheworldofai, @alxfazio):
- Define a goal condition
- Let the agent loop until verifiably done
- "We learn from failure"-centric — failures feed back into the next iteration
- TUI tools exist for this (Ralph Loop TUI)
- Now extended to drive UIs (per @iannuttall — Ralph + droid + GitHub issues = auto-fix PRs)

### Skills (Anthropic's term for Claude expertise modules)

> "Skills are just folders. Folders that teach Claude your job. Your workflow. Your expertise. Your domain." — @kirillk_web3 (paraphrasing two Anthropic engineers)

Built-in/community Claude Code skills mentioned:
- **`/simplify`** — "cleans up >90% of slop from a working solution" (@iamsahaj_xyz)
- **`/prompt`** — turns unstructured brain dumps into coherent instructions (@cblatts)
- **`/review-plan`** — runs multiple agents to critique a plan and suggest a new one (@cblatts)
- **`/goal`** — combined with `react-doctor` for React app improvement (@ParthJadhav8)
- **Cartographer** — uses parallel Sonnet subagents to analyze entire codebases and generate an architecture doc (@KingBootoshi)
- **Autonomous Dogfooding** — agent-browser skill that uses your app the way users do (@ctatedev)

### Karpathy's framing (the meta-take)

> "The worst thing an expert can do right now is reject them [LLMs]. Most experts read it as a threat, but it's advice. The gap between 'AI tools are bad' and 'AI tools are useful when used right' is the gap between being net-negative or net-positive on adoption." — Karpathy, summarized via @Mnilax

## MCP — Model Context Protocol

The integration standard that's making LLM-tool composition tractable.

**MCP 2026-07-28 release candidate highlights** (per @dsp_):
- Protocol is now **stateless** — no handshake, no session id, any request can hit any server instance
- Extensions are first-class (MCP Apps, Tasks)
- Auth hardening
- Proper deprecation policy

**MCP servers worth knowing**:
- **Google's official CLI for Gmail/Drive/Calendar/Sheets** comes with an MCP server (per @wesbos) — relevant for any AI assistant doing email/calendar work
- Several bookmarks mention building MCP servers for proprietary tooling — this is the standard glue layer now

## Local-model and "small model" tooling

- **Qwen** small models that run locally on a $600 Mac Mini (per @TukiFromKL, @AlexFinn) — "frontier intelligence on a potato"
- @tolibear_: running a Sonnet 4.6-level LLM locally, private, no rate limits, free
- **Project N.O.M.A.D.** — fully offline AI/Wikipedia/maps survival computer; everything runs locally, zero telemetry (per @godofprompt)
- **vast.ai** for cheap GPU rental — same A100 that's $4/hr on AWS is $0.50/hr there (per @inboxfelon)

## Document / data ingestion

- **LiteParse v2.0** (per @jerryjliu0, LlamaIndex) — fastest open-source PDF parser, rewritten in Rust, 100x faster, packaged for Rust/JS/TS/Python with WASM for browser/edge
- **MarkItDown** (Microsoft, per @mdancho84) — converts any document to Markdown for LLM consumption, open source
- **LangExtract** (Google, per @techNmak) — "killed the document extraction industry," extracts structured data from unstructured text, maps every entity to source location, handles 100+ page documents

## Prompt engineering signal

**The left-to-right attention insight** (per @burkov):
> LLMs process text from left to right — each token can only look back at what came before it, never forward. When you write a long prompt with context at the beginning and a question at the end, the model answers the question having "seen" the context, but the context tokens were generated without knowledge of the question. **Put the question first, then the context.** Or: ask the question, get a one-line answer, then ask "Now read this context and refine your answer."

**MIT's "Recursive Meta-Cognition"** (per @godofprompt) — reportedly 110% better than standard prompts. (Vendor-y framing — verify before treating as canonical.)

**For email-style writing**: @SullyOmarr notes GPT-4/Sonnet still can't write emails in personal tone. Tone-matching + autocomplete is an unsolved-enough product opportunity that it shows up multiple times.

## Image / multimodal

- **Nano Banana** (Google's image edit model) — described as a "wow moment again like first time" for image manipulation, e.g. "show this woman wearing this outfit" works accurately from flat-lay photos (per @levelsio, @deedydas)
- "Going to kill 99% of Photoshop" framing — accurate description, given the use cases shown (passport pics, decorate-this-house, put-clothes-on-me)

## Image generation as marketing/branding tool

- **Google Pomelli** (per @JoshKale) — feed it your website to build "brand DNA", then prompt for any marketing material; replaces $1000s in photoshoot costs

## Specialized vertical AI examples

- **Mr. Chatterbox** (Victorian Gentleman Chatbot, @Nomads4Pritzker) — LLM trained from scratch on 1837-1899 Victorian literature; thinks it's *in* a Victorian novel and invents Victorian scenarios. Hugging Face Space.
- **Spotify "Honk"** — internal AI dev system (Claude Code-powered) — see Spotify reference above

## Vibe-coding / "non-technical shipping" tension

The bookmarks split between optimism and skepticism:

**Optimist take** (@iannuttall):
> "Ben built a UI for Ralph loops with droid, hooked into GitHub issues to automatically fix and create PRs for issues. Ben is 'non-technical' btw and figured this out by chatting, forking repos, and copying images from X. There's no such thing as non-technical anymore."

**Skeptic take** (@boneGPT):
> "I call this localhost syndrome. It's only when they finally try to ship that they realize it's not secure, the API key is leaking, their Stripe webhook won't work, all the data they thought is real is actually simulated. It's more dunning-kruger than psychosis."

**Pragmatist take** (@robustus):
> "Turns out with claude code, my decades long strategy of NOT deeply learning regexes, sql, nginx confs, elaborate shell commands, advanced shell scripting, any javascript framework, perf optimization, webpack, cdns, bundlers… was entirely correct."

Worth holding both at once.

## Education / learning content referenced

- **Stanford 2-hour lecture** on how Stanford trains engineers to build AI systems (per @RohOnChain) — described as "more practical than every Claude tutorial & prompting thread"
- **Linus Torvalds 70-minute Google lecture on Git** (per @slash1sol) — "99% of developers use it wrong"
- **Two Anthropic engineers explaining Claude Skills in 16 minutes** — Barry and Mahesh; canonical resource per @kirillk_web3

## One-liners worth quoting

- "Having coworkers is crazy, it's like Claude code but they prompt themselves." — @haydenbleasel
- "Claude: 'I estimate this will take 1-2 weeks to complete.' Me: [image of skepticism]" — @RhysSullivan
- "Add WarCraft 3 sounds to Claude hooks to get alerts when it finishes a task or needs permission. How to finally become the 10x engineer." — @JorgeCastilloPr
- "Double espresso + good playlist + claude code." — @0xgaut
- "Your Docker image is 2.3GB. You're shipping an entire operating system to run a Python script that sends emails. This is not engineering. This is hoarding with extra steps." — @brankopetric00
- "Boring works. Boring scales. Boring lets you sleep at night." (re: Docker setup at $30M ARR company — one Dockerfile, plain ECS, no Kubernetes, no service mesh) — @brankopetric00
