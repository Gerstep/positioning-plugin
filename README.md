# Positioning

A 15-minute session with your AI agent that produces a real positioning
statement — and the artifacts a startup needs to hold the position.

Position or be positioned. If you don't pick a category, you will be assigned
one. And since the market's default setting today is disbelief, claims don't
compete anymore — proof does. This skill forces the choices most teams avoid,
then turns every claim into something provable today or a dated bet.

## What you get

Fifteen minutes of forced-choice questions per founder, then a `positioning/`
folder in your project:

- **Positioning statement** under 30 words — ONLYness or FIRSTness, depending
  on your category path
- **Message architecture** — target market, category, position, value prop,
  three key messages, elevator story: the script everyone stays on
- **Mind virus** — the phrase the market should repeat without you in the room
- **Category decision** — compete, reframe, or create, with what you give up
- **Compass** — the axis the leader owns vs. the axis you introduce
- **Ignore list** — who you serve, who you deliberately don't
- **Worldview** — the irreversible moment and your irreversible question,
  timestamped
- **Archetype** — one of twelve, so the brand feels like one thing
- **90-day window of proof** — three dated proofs, sequenced to compound

## How it works

One command, three moments. The skill detects which one you're in:

1. **Session** — each co-founder runs it solo. 15 minutes, forced choices, gut
   answers. Competitive research runs in the background while you answer.
   Answers are saved to a file. (Solo founder? You get the full pack
   immediately.)
2. **Compile** — when every founder has run it, one of you runs it again: it
   maps agreements, surfaces contradictions, forces a decision on each, and
   writes the final pack — with each founder's draft shown against the final.
3. **Proof** — weeks later, run it again: did the proofs ship, is the market
   repeating your phrase, has anyone joined your category, is it time to drop
   "first".

Every claim in the final statement passes a skeptic check against public
evidence. What can't be verified isn't deleted — it's rewritten as "By
[date], ..." and booked into the 90-day plan.

## Install

**Claude Code / Claude Cowork**

```
/plugin marketplace add Gerstep/positioning-plugin
/plugin install positioning@positioning-plugins
```

Then run `/positioning`.

**Codex**

```
git clone https://github.com/Gerstep/positioning-plugin
cp -r positioning-plugin/skills/positioning ~/.agents/skills/
```

Then invoke `$positioning` (or browse `/skills`). Working inside a clone of
this repo also works — Codex discovers `.agents/skills/` automatically.

**Anything that speaks [Agent Skills](https://agentskills.io)** — the skill is
spec-compliant; point your agent at `skills/positioning/`.

## Example output

> We are the only incident-response platform that finds root cause before
> customers notice, unlike dashboard-first monitoring tools, which only show
> symptoms.

## Quality rules

- No sentence over 20 words; statement under 30
- No unverifiable adjectives — "innovative", "cutting-edge", "world-class"
  don't survive
- Every claim is true today or explicitly a bet with a proof date
- No "all of the above" — the pain of choosing is the exercise

## Credits

Built by [Stepan Gershuni](https://github.com/Gerstep) ·
[cyber.fund](https://cyber.fund). MIT license.
