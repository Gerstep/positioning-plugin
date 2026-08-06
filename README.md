# Positioning

A 15-minute session with your AI agent that produces a real positioning
statement — and the artifacts a startup needs to hold the position.

Position or be positioned. If you don't pick a category, you will be assigned
one. And since the market's default setting today is disbelief, claims don't
compete anymore — proof does. This skill forces the choices most teams avoid,
then turns every claim into something provable today or a dated bet.

## How it runs

### Step 1 — each founder does it alone (15 minutes)

Open your AI tool in your project and type `/positioning`. It asks who you are
and what the company does — and while you keep answering, it quietly
researches your competitors in the background.

Then it walks you through about ten questions, one at a time. Every question
is a forced choice, answered from the gut in 30 seconds. No "all of the
above" — having to pick is the whole point:

- Can your buyer name an obvious go-to product in your space? This decides
  whether you compete with a leader, change what "good" means, or create a
  new category.
- Who exactly are you selling to — and who are you *deliberately* not selling
  to? Including: which deal are you chasing right now that you just said you
  shouldn't be?
- What is it, why does it matter (it keeps asking "so what?" until you hit
  the real answer), why you, why now?
- Then it shows what it found about competitors: what they all say (so you
  can't say it) and what none of them say (your opening).
- You write your one-sentence positioning statement, under 30 words.
- You pick the word or phrase you want the market to repeat about you.
- You pick how the brand should feel — one of twelve personalities, two quick
  questions.
- You name three things you'll ship in the next 90 days that *prove* your
  claims, with dates.

At the end it fact-checks your statement like a suspicious customer would.
Anything it can't verify is rewritten as "By [date] we will…" instead of "We
are…". Your answers are saved to a file. Done.

### Step 2 — the founders' answers collide

Once each co-founder has done their own 15 minutes (without peeking at each
other's answers), any one of you types `/positioning` again. It reads
everyone's files and shows:

- where you **agree** — that's your real positioning;
- where you **contradict** each other — those are decisions nobody has
  actually made yet;
- anything one person said that's clearly right.

For each disagreement it makes you pick a side — or explicitly write "we'll
decide together by [date]". No blending two answers into mush. Every
founder's original draft is shown next to the final statement.

Solo founder? You get the final pack right after Step 1 — no Step 2 needed.

## What you get

A `positioning/` folder in your project with one main document:

- **Positioning statement** under 30 words
- **Message architecture** — target market, category, position, value prop,
  three key messages, elevator story: the script everyone stays on
- **Mind virus** — the phrase the market should repeat without you in the room
- **Category decision** — compete, reframe, or create, with what you give up
- **Compass** — the axis the leader owns vs. the axis you introduce
- **Ignore list** — who you serve, who you deliberately don't
- **Worldview** — what changed in the world and the question you exist to
  answer, timestamped
- **Archetype** — one of twelve, so the brand feels like one thing
- **90-day window of proof** — three dated proofs, sequenced to compound

## Install

**Claude Code / Claude Cowork**

```
/plugin marketplace add Gerstep/positioning-plugin
/plugin install positioning@positioning-plugins
```

Then run `/positioning`.

**Codex**

Settings → Plugins → **Add plugin marketplace** → paste
`Gerstep/positioning-plugin` as the source (leave Git ref on `main`) → **Add
marketplace** → install **positioning**.

Then invoke `$positioning` (or browse `/skills`).

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
