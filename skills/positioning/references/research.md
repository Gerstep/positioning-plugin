# Competitive research

Launched in the background during session setup. Hard timebox: about 4
minutes, best-effort. A late result is folded in at compile; never make the
founder wait for it.

## How to run it

- **Subagent tool available** (Claude Code / Cowork agents, Codex subagents):
  launch both briefs below as parallel background agents.
- **No subagents, but web search available:** run the queries yourself between
  session phases — cap at 5–6 searches total.
- **No web access:** skip. Write "research: not run (no web access)" in the
  pack. Do not invent competitors.

Use whatever web search or research tools the harness actually has; richer
research tools when present, built-in search as the floor. Do not probe for
specific tool names.

## Brief A — direct competitors

> Research the competitive landscape for: [company description].
> Find the 3–5 closest players (same buyer, same problem). For each: name,
> one-line positioning as THEY state it, the word or phrase they own, pricing
> if visible, one real weakness.
> Then answer: (1) What do ALL of them claim? That is table stakes. (2) What
> does NONE of them claim? That is white space. (3) Which single axis of
> comparison does the current leader own?
> Output: compact markdown table plus 3 bullets. Cite the source page for
> each positioning quote. Timebox: return your best within 4 minutes.

## Brief B — adjacent players and frames

> Research companies adjacent to: [company description].
> Find: 2–3 solving a related problem for the same buyer; 2–3 solving the
> same problem for a different buyer; any company this team would be
> flattered to be compared to.
> For each: one line on the frame they use — category words, axis, who they
> ignore.
> Suggest 1–2 axes of competition nobody in the direct set is extreme on.
> Output: short markdown list. Timebox: 4 minutes.

## What the session consumes

At Phase 4 the session needs, at most: the 3–5 direct players with the word
each owns, table stakes, white space, and the proposed axes. Compress to
that. Full findings go to `positioning/research.md` with source links and a
retrieval date.
