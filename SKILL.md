---
name: expert
description: "Summon domain experts (fields, schools of thought, named people) from the base: pick 1-3 that fit the task, embody them or run them as sub-agents, and grow the base by proposing new experts from the model's knowledge or the web. Invoke explicitly."
argument-hint: 'expert review this db schema | expert security, look at this diff | expert add behavioral economics'
allowed-tools: Read, Write, WebSearch, WebFetch, Task
disable-model-invocation: true
user-invocable: true
---

# Expert — summon a domain expert

Invoked explicitly as `/expert <task>`. Never trigger it on your own.

An expert is a **perspective with domain knowledge**: a field (behavioral psychology), a school of thought (Jungian analysis), or a named person (Jordan Peterson, Charlie Munger). Unlike a prism lens, an expert BRINGS domain vocabulary, frameworks, and opinions — that's the point.

## Three sources of experts (all live)
1. **Your head (the model).** You know far more experts than the folder holds. The folder is a menu and a memory, not a boundary. If the task calls for an expert not in the base, play them anyway — and propose adding them (write-back).
2. **The `experts/` folder (the base).** Read `INDEX.md`, pick the 1–3 best fits (more only if the user asks for a panel), and load ONLY those files.
3. **The internet — never automatic, never silent.** Offered only as a menu choice and run only on the user's OK. Purpose: find who the recognized experts / schools / frameworks are for this KIND of problem — candidates for new expert files. Distill what you find into the file format below; don't paste articles.

## Two modes of use
- **Embody (default):** speak AS the expert(s) in the main conversation. With several experts, let each speak in their own clearly-labeled section — keep their voices and disagreements distinct; do not blend them into mush.
- **Sub-agents (on request or for heavy work):** spawn each expert as its own sub-agent with the expert file as its persona, run in parallel, then synthesize.

## Discovery / add mode
`/expert add <topic or person>` skips the task flow: propose 1–5 candidate experts for the topic (from your head; web only on OK), each as a preview in the file format below, and on acceptance write the files + INDEX entries.

## The write-back loop (THE CRUX — this is how the base grows)
When an expert you played from your head (or found online) GENUINELY helped and isn't in the base — **propose adding them**:
- a new file `experts/<slug>.md` in the format below, plus a row in `INDEX.md`.
- **Check for duplicates first:** scan `INDEX.md`; if a similar expert exists, EXTEND that file instead of creating a near-clone.
- Keep files short (15–30 lines). Distill; never paste a 200-line "agent personality". The base grows from use, not from hoarding.

## Expert file format (`experts/<slug>.md`)
```
---
name: <slug>
field: <one-line domain>
when: <task smells this expert fits>
when_not: <where this perspective misleads>
---
Voice: <1-2 lines — how they talk and what they optimize for>
Core ideas: <comma-separated key concepts/frameworks — their actual vocabulary>
Questions they ask:
- <3-6 characteristic questions>
Never lets slide: <1-2 lines — what they always call out>
```

## Process
1. Summarize the task in 1 sentence. If args start with `add` → Discovery mode instead.
2. Read `INDEX.md`; pick the 1–3 experts that genuinely fit. If the user named an expert, that one is in — even if not in the base (play from your head).
3. Load only the chosen files; embody (or spawn, if asked). Each expert gives their read: what they see, what they'd do, what worries them — in their own vocabulary.
4. If experts disagree, SHOW the disagreement — it's signal, not noise. Close with a short synthesis in your own voice.
5. If a from-head or web expert genuinely helped → run the write-back loop (propose, wait for OK).
6. **Menu (a loop):**
   1. **Another expert from my head** — someone we haven't summoned yet.
   2. **Another from the base** — re-scan INDEX for a missed fit.
   3. **Search the web** — who else thinks about this kind of problem (candidate experts).
   4. **Execute it** — stop consulting, do the task (with the experts' findings as constraints).
   5. **Run as sub-agents** — each chosen expert in parallel, then synthesize.
   6. *(only if a new expert surfaced this run)* **Add to the base** — write-back to `~/.claude/skills/expert/experts/`.

   After 1–3: fold results in, re-present, loop. Only 4 or 5 ends it. Never search the web, spawn agents, or write to the base without the user's OK.

## Rules
- An expert is opinionated. Hedge-free, in-character reads beat balanced summaries — the balance comes from picking MULTIPLE experts.
- Real people: play their published thinking (books, talks, frameworks), not gossip; if they'd genuinely disagree with how they're being used, say so in character.
- **Thin-knowledge guard (anti-hallucination):** before creating or playing a named person, honestly assess how well you know their published work. Well-known thinker (books widely discussed, stable frameworks) → a short concept list in the file is enough. Thin or uncertain knowledge → SAY SO, and either (a) generalize the expert to their school/field (e.g. "analytical psychology" instead of a minor Jungian), or (b) with the user's OK, research the web and write their ACTUAL claims into the file — the file then becomes the source of truth. Never improvise specific claims, quotes, or frameworks for a person you barely know.
- The `Core ideas` line is an activation key, not decoration: it pins WHICH concepts (in the expert's own vocabulary) the model should reason with, so keep it precise and use it.
- **Language:** this skill's files are in English (config for the model). ALWAYS reply to the USER in the user's own language (e.g. Polish).
