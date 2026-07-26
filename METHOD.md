# METHOD — how this base is built and improved

This file is for maintainers (humans and AI sessions doing base work). It is never loaded at
skill runtime and costs nothing in use.

**Definition:** An expert = a selection **envelope** (`name/field/when/when_not`) + a **payload**
that either *pins* knowledge the model already has (anchors/triggers) or *carries* it outright
(a written methodology/framework) — and it is built from the best existing source, never improvised.

## 1. Two kinds of payload

- **Anchors** — for experts the model knows deeply (famous thinkers, mainstream fields): signature
  vocabulary, named coinages, 1–3 Sample voice lines (labeled paraphrases), questions they ask,
  never-lets-slide. Purpose: keep the whole answer pinned to the real apparatus, prevent drift
  into generic advice. Budget: 15–30 lines.
- **Operational core (method)** — for process experts (diagnostician, discovery coach, incident
  commander...) and for thin-knowledge subjects: the methodology written out — steps, what to ask,
  what to listen for, decision points, escalation, handoffs. The file IS the knowledge.
  Budget: up to ~150 lines. Must read as a protocol with decision points ("if you hear X → probe Y
  / hand off to Z"), never as an encyclopedia — everything in a file pulls toward being used.
- Most strong files are hybrids: anchors + a compact operational core.

## 2. Source hierarchy (research before writing)

1. **Primary canon** — the expert's own books/papers/talks.
2. **Established standards and bodies** — e.g. OWASP, DORA, WCAG, published clinical protocols.
3. **Well-built existing packagings** (OSS skills/prompts/kits) — distill, check the license,
   attribute in the file or README. Others' tested work beats our one-shot generation.
4. Secondary commentary — last resort.

Before authoring any method payload: check `research/` notes first, then search the web for
existing well-tested packagings. Do not write from imagination what someone already wrote from
practice.

## 3. Research memory (`research/`)

Research is done **per topic, not per expert** — one topic (MI/OARS, DORA, thought records...)
feeds many experts. Each research effort ends in `research/<topic>.md`:
sources (with licenses), distilled frameworks and facts, which experts it feeds, and a
"leftovers" section for material not yet used. Future sessions read the note instead of
re-searching.

## 4. Quality bar (applies to every file)

- **Anti-fabrication:** every concrete claim, framework, tool, number must be genuinely
  attributable. Sample lines are labeled paraphrases, never invented verbatim quotes.
  Thin knowledge → generalize to the school, research first, or leave it out.
- **Selection over recitation:** no flat mega-lists; prefer signal→tool mappings
  ("fix works then fades → shifting the burden") so the model picks the apt tool, not the top-3.
  Order inside the payload only where the order IS the doctrine (Meadows' leverage ladder),
  never as an answer script.
- **Honest boundaries:** `when_not` with named redirect targets (other expert slugs or specialist
  types). On a misfit: flag it, name where it belongs, stop — no ghost-answering the specialist's
  numbers.
- **Pacing (narrative experts):** one story/parable and 2–3 vocabulary items per answer;
  keep an inventory of 4+ cases so sessions don't recycle the same two.
- **One voice:** a merged or enriched file must read as one coherent perspective.

## 5. Runtime philosophy (mirrored in SKILL.md)

The file is the expert's knowledge, not the answer's outline. Diagnose first; pull the 1–2 tools
this situation calls for; if underspecified, ask the expert's diagnostic question before
prescribing. One framework per response, never stacked (rule adopted from Satori,
github.com/MetcalfSolutions/Satori, Apache-2.0). Method experts run their protocol across turns —
ask, listen, decide — rather than lecturing it.

## 6. Maintenance

- `INDEX.md` is generated from envelopes only (payload size never affects selection cost).
- After any base change: lint (envelope keys, line budgets, slug=filename, INDEX↔files 1:1),
  regenerate INDEX, commit and push — the skill folder is a git clone of xtompie/expert.
- Provenance of the initial base: distilled 2026-07 from agency-agents, wshobson/agents,
  VoltAgent, contains-studio (roles axis) + model-knowledge passes (thinkers & life axes),
  reshaped to envelope+payload, evaluated with 25-test embodiment probes.
