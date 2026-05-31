# Key Threads — High-Signal Bookmarks Worth Re-Reading In Full

Most bookmarks are short tweets. A few are long substantive threads or articles. These are the ones where it's worth opening the original.

## 1. @burkov — How LLMs actually attend to context (essential mental model)

**Why it matters**: changes how you write prompts.

> LLMs process text from left to right — each token can only look back at what came before it, never forward. This means that when you write a long prompt with context at the beginning and a question at the end, the model answers the question having "seen" the context, but the context tokens were generated without knowledge of the question.

The practical implication: **put the question first, then the context**. Or: ask the question, get a one-line answer, then ask "Now read this context and refine your answer."

This is one of those "obvious in retrospect" prompt-engineering insights that comes from understanding the architecture, not from heuristic experimentation.

## 2. @levie — Agents in the enterprise

@levie spent a week meeting with IT/AI leaders from banking, media, retail, healthcare, consulting, tech, sports. The thread is the most comprehensive take in the corpus on **what enterprise AI adoption actually looks like in mid-2026**.

Themes that recur:
- Move from chat era to agents that use tools
- Most enterprises are still in early experimentation
- The reality of integration: MCP is becoming the standard
- Org-design implications (who owns AI workflows?)

Worth opening the full thread when thinking about enterprise positioning.

## 3. @steipete — OpenClaw / "what if tokens don't matter"

@steipete's framing of OpenClaw is the deepest articulation in the corpus of **"AI as remote workforce, not autocomplete"**:

> "Part of what excites me so much about working on OpenClaw is that I'm trying to answer the question: How would we build software in the future if tokens don't matter? We constantly run ~100 codex in the cloud, reviewing every PR, every issue."

The mental shift from "I use AI as a tool" to "I run AI as a service" is the core idea.

## 4. @milan_milanovic — Spotify "Honk" reveal

Specific, concrete, real-company example of what AI-native development looks like:
- Best devs haven't written code since December 2025
- Internal Claude-Code-powered system called "Honk"
- 50+ features shipped in 2025
- Engineers fix bugs and deploy from Slack on their phones

Use this when explaining to skeptics what's actually possible.

## 5. @StartupArchive_ — Naval Ravikant on leverage in 2026

Naval's leverage framework, applied to AI:
- Original leverage hierarchy: labor → capital → code/media → AI
- "I've been saying this for a while, but the leverage in the system is insane"
- AI compounds with existing leverage, doesn't replace it

The implication: people with existing leverage (engineers, capital owners, content creators) get the biggest AI multipliers.

## 6. @anothercohen — Slack + MCP + AI agents inside a real company

> "It's pretty incredible how much of how I work has changed in just the last two weeks. We rolled out an AI chatbot inside Slack (OpenClaw), hooked up a bunch of tools via MCP and APIs, and now I basically just chat with AI to knock out entire projects."

Pairs with the Spotify "Honk" story — two examples of "AI agent inside Slack" as the dominant 2026 enterprise interface pattern.

## 7. The @levelsio dev setup

@levelsio's tmux-on-Hetzner-with-Termius setup is described in enough detail across multiple bookmarks to be a reproducible reference for "what does a working indie hacker dev environment look like in 2026." Already detailed in `02-coding-tools.md`.

## 8. Curated knowledge > encyclopedic accumulation

A cultural meta-thread from `@BBHerodotus` quoting Dumas's Abbé Faria character:

> "I had nearly five thousand volumes in my library at Rome; but after reading them over many times, I found out that with one hundred and fifty well-chosen books a man possesses... at least all that a man need really know."

The relevance to AI engineering: prefer **curated depth over complete breadth** when assembling context for an LLM. A small set of well-chosen documents almost always outperforms a kitchen-sink dump.

## Why these specifically

These threads:
1. Define a worldview or strategy in a way short tweets don't
2. Come from authoritative voices (named operators, not anonymous accounts)
3. Have specific, concrete content (not vague predictions)
4. Recur thematically across other bookmarks in the corpus

Reading these in full gives you most of the actionable AI/engineering insight from the corpus.
