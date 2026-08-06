---
name: positioning
description: Run a 15-minute forced-choice positioning session for a startup. Pick a category path (compete, reframe, or create), decide who you serve and who you ignore, write a positioning statement under 30 words, find the mind-virus phrase, choose a brand archetype, and plan a 90-day window of proof. Each co-founder runs it solo; the skill then compiles all answers, surfaces contradictions, and forces decisions. Use when a company needs positioning, messaging, category strategy, a value proposition, or founder alignment on "why us".
license: MIT
metadata:
  author: "Stepan Gershuni, cyber.fund"
  version: "2.0.0"
---

# Positioning

A 15-minute forced-choice session that produces a positioning statement and the
artifacts a startup needs to hold a position: message architecture, mind virus,
compass, ignore list, worldview, archetype, and a 90-day proof plan.

Position or be positioned. If you don't pick a category, you will be assigned
one. The market's default setting is disbelief, so competition has shifted from
making claims to surviving verification. This skill forces the choices, then
makes every claim either provable today or a dated bet.

## Operating rules (read first)

**Questions.** If an interactive question tool is available (for example
AskUserQuestion in Claude Code or Cowork), use it for every forced choice.
Otherwise ask in plain text: one question at a time, numbered options, wait for
the answer. Never stack questions in plain-text mode.

**Forced choice.** No "all of the above". Gut answers over polished answers —
tell the user 30 seconds per question is enough. The pain of choosing is the
exercise.

**Time.** The session targets 15 minutes total. Never block on research; never
loop. Phase budgets are in the session script. If research has not returned by
the statement phase, proceed without it and mark the pack "research pending".

**Research.** If a subagent tool is available, launch research in the
background during setup. If only web search is available, run a few quick
searches inline between phases. If there is no web access, skip research and
say so in the output. Never invent competitors.

**Files.** All artifacts live in `positioning/` under the current working
directory (create it if needed). Never overwrite another founder's answers
file.

## Which moment is this?

If the user asked for a specific mode in plain words ("compile", "proof check",
"start over", "new session"), obey that. Otherwise check `positioning/` in the
current directory and route:

| State | Moment | Script |
|---|---|---|
| No `positioning/` dir, or no `answers-*.md` files | First run — run the session | `references/session.md` |
| One or more `answers-*.md`, no `positioning.md` | Ask: run your own session, or compile the team's answers now? | `references/session.md` or `references/compile.md` |
| `positioning.md` exists | Offer: proof check-in, a new founder session, or recompile | `references/proof.md` |

A solo founder goes straight from session to the full pack — compile is only
for teams.

## The method in one breath

Category first (compete / reframe / create — the maturity of the category
decides which is honest). Then community (who you speak to, who you ignore).
Then the logical spine: what is it, why does it matter, why you, why now. Then
compress into an ONLYness or FIRSTness statement under 30 words, find the
phrase the market could repeat without you in the room, pick the archetype that
gives the position feel, and book three proofs for the next 90 days. Detail
lives in the reference scripts — load only the one you need.

## Quality rules (apply to every artifact)

- No sentence over 20 words. Statement under 30 words.
- No unverifiable adjectives: innovative, cutting-edge, world-class, unique,
  seamless, revolutionary.
- Every claim is either true today or explicitly a bet with a proof date.
- Aspirational is written "By [date] we will..." — never "We are...".
- If it reads like a SaaS landing page, rewrite it drier.

## Files in this skill

- `references/session.md` — the 15-minute founder session (phases, questions, timings)
- `references/research.md` — competitor research briefs and timebox
- `references/archetypes.md` — the 90-second archetype picker
- `references/compile.md` — merge co-founder answers, force tiebreaks, emit the pack
- `references/proof.md` — the 90-day proof check-in
- `assets/pack-template.md` — template for `positioning/positioning.md`
- `assets/answers-template.md` — template for per-founder answers files
