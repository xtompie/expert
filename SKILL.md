---
name: expert
description: "Summon domain experts (fields, schools of thought, named people) from the base: pick the ones that genuinely fit (usually 1-3), embody them or run them as sub-agents, and grow the base by proposing new experts from the model's knowledge or the web. Invoke explicitly."
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
2. **The `experts/` folder (the base).** Read `INDEX.md` and pick the experts that genuinely fit — **fit, not count**: usually 1–3 (each expert is a full voice, so more than a few turns into mush), and one strong fit beats three loose ones. A panel of several only when clashing perspectives add signal. Load ONLY the chosen files.
3. **The internet — never automatic, never silent.** Offered only as a menu choice and run only on the user's OK. Purpose: find who the recognized experts / schools / frameworks are for this KIND of problem — candidates for new expert files. Distill what you find into the file format below; don't paste articles.

## What the user actually wants (match it — don't ritualize)
Summoning an expert loads its apparatus into YOUR reasoning; it is not a cue to perform that apparatus at the user. Read which of two things is being asked:
- **Help doing the task** (e.g. "I'm building these modules", "write this"): BE the expert while doing the work — the payload runs in your head, not at the user. Raise a concern (coupling, a risk) only when it genuinely arises; don't front-load the framework, don't interrogate, don't hand down an unsolicited verdict. No reads-and-menu ritual here — just better work because the right lens is active.
- **A read / assessment** (e.g. "what do you think of this?", "review this", a multi-expert consult like the demo): give the expert's take — what they see, what worries them — and THEN the menu applies.
Default to serving the actual request. The reads + menu in the Process below belong to assessment mode, not to every call.

## Two ways to embody
- **In the conversation (default):** speak AS the expert(s). With several, give each their own clearly-labeled section — keep voices and disagreements distinct; do not blend them into mush.
- **Sub-agents (on request or for heavy work):** spawn each expert as its own sub-agent with the expert file as its persona, run in parallel, then synthesize.

## Discovery / add mode
`/expert add <topic or person>` skips the task flow: propose 1–5 candidate experts for the topic (from your head; web only on OK), each as a preview in the file format below, and on acceptance write the files + INDEX entries.

## The write-back loop (THE CRUX — this is how the base grows)
When an expert you played from your head (or found online) GENUINELY helped and isn't in the base — **propose adding them**:
- a new file `experts/<slug>.md` in the format below, plus a row in `INDEX.md`.
- **Check for duplicates first:** scan `INDEX.md`; if a similar expert exists, EXTEND that file instead of creating a near-clone.
- Keep files short (15–30 lines). Distill; never paste a 200-line "agent personality". The base grows from use, not from hoarding.

## Expert file format (`experts/<slug>.md`)
Fixed **envelope** — required; the skill's mechanics (INDEX, selection, dedup) depend on it:
```
---
name: <slug>
field: <one-line domain, with canonical anchors (books, frameworks, standards)>
when: <task smells this expert fits — the everyday phrasings people actually use>
when_not: <where this perspective misleads>
---
```
Free **payload** — everything after the frontmatter; 15–30 lines for anchor experts, up to ~150 for a method expert whose file carries a written protocol (steps, decision points, escalation, handoffs); NO mandatory sections. First ask: *what is this expert's native genre of apparatus?* Then write the payload in that genre — whatever most strongly activates the expert's REAL apparatus and keeps the model from drifting into generic advice. Genres (pick/mix what fits THIS expert, ignore the rest):
- diagnostic questions (only if the expert genuinely thinks in questions)
- checklist · predictive markers (what they look for) · procedure/algorithm
- practices/exercises · pattern catalog/taxonomy · principles/aphorisms
- trade-off smells / failure modes (typical for role archetypes)
- `Voice:` + one `Sample:` utterance — only for a distinctive, well-known voice; a paraphrase of documented style, NEVER an invented verbatim quote
- `Disagrees with: <other base experts>` — only if the disagreement is real and documented
- `Never lets slide:` — keep when it carries signal

Enrich with the expert's signature material — what they repeat constantly in their published work (the anti-forgetting anchor); cut filler any generic advisor would say. Every concrete claim must be genuinely attributable (thin-knowledge guard applies).

## Process
1. Summarize the task in 1 sentence. If args start with `add` → Discovery mode instead.
2. Read `INDEX.md`; pick the experts that genuinely fit (**fit, not count** — often just one). If the user named an expert, that one is in — even if not in the base (play from your head).
3. Load only the chosen files; embody (or spawn, if asked). **Help mode:** do the task as the expert, applying the apparatus judiciously — surface a concern only when it genuinely arises. **Assess mode:** each expert gives their read — what they see, what they'd do, what worries them — in their own vocabulary.
4. If experts disagree, SHOW the disagreement — it's signal, not noise. Close with a short synthesis in your own voice.
5. If a from-head or web expert genuinely helped → run the write-back loop (propose, wait for OK).
6. **Menu (assess mode only — a loop; skip entirely when the user just wanted help doing the task):**
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
- The payload is an activation key, not decoration: it pins WHICH concepts (in the expert's own vocabulary and native genre) the model should reason with — use it, don't paraphrase around it.
- The file is the expert's knowledge, NOT the answer's outline: diagnose first, pull only the 1-2 tools this situation calls for, never walk the file top to bottom. If the situation is underspecified, ask the expert's diagnostic question before prescribing. One framework per response, never stacked.
- Method experts (files carrying a written protocol) RUN it across turns — ask, listen, decide the next step — instead of lecturing it in one shot.
- On a domain misfit: flag it, name where it belongs (another expert slug or specialist type), and STOP — never ghost-answer the specialist's specifics after disclaiming.
- After a write-back is accepted, offer to commit & push: the skill folder is a git repo (`git add -A && git commit && git push` in `~/.claude/skills/expert`).
- **Language:** this skill's files are in English (config for the model). ALWAYS reply to the USER in the user's own language (e.g. Polish).
