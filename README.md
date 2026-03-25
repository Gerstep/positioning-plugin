# Positioning Plugin for Claude Code

A structured positioning statement exercise for startups and teams. Combines deep competitive research with forced-choice strategic questions and team alignment to produce an honest, compressed positioning statement.

Built for accelerator portfolio companies, internal strategy sessions, or any team that can't answer "why us?" in one sentence.

## What it does

The plugin guides you through a 7-phase workflow:

1. **Context** — Collects basic company info (what you do, who you serve, stage)
2. **Research** — Runs parallel competitive analysis (direct competitors + adjacent/aspirational)
3. **Questions** — Asks 4 forced-choice strategic questions informed by the research
4. **Team exercise** — Generates a copy-paste questionnaire for your team
5. **Synthesis** — Analyzes team replies for alignment, contradictions, and surprises
6. **Output** — Produces a positioning statement under 30 words + supporting sections under 200 words total
7. **Iteration** — Optional refinement of specific sections

## Philosophy

Most positioning exercises produce corporate fluff. This one forces honesty:

- Competitors are researched **before** questions are asked — no hiding from reality
- Every question is a **forced choice** — no "all of the above"
- Team members write **independently**, then answers are collided
- Final output is **compressed to under 30 words**

The output is a strategic alignment tool, not marketing copy.

## Install

### From GitHub (recommended)

```
/plugin marketplace add Gerstep/positioning-plugin
/plugin install positioning@positioning-plugins
```

### Local testing

```bash
claude --plugin-dir /path/to/positioning-plugin
```

### Manual install

Clone to `~/.claude/plugins/positioning-plugin/`, then restart Claude Code.

```bash
git clone https://github.com/Gerstep/positioning-plugin ~/.claude/plugins/positioning-plugin
```

## Usage

```
/positioning:positioning
```

The skill will walk you through each phase interactively. You can also:

- Provide a website URL or file path in Phase 1 for automatic context extraction
- Skip to the synthesis phase if you already have team replies collected
- Iterate on specific sections after the first output

## Example output

```markdown
# Acme Corp — Positioning Statement

## The customer test
DevOps teams pick us over Datadog because we catch incidents
before they page. Our causal graph traces root cause in seconds,
not minutes of dashboard hunting.

## The honest gap
No mobile app. On-call engineers can't triage from their phone yet.

## The core bet
Building predictive alerting that fires before metrics breach thresholds.
Today: reactive with faster root cause. By Q3: predictive.

## Market scope
Cloud infrastructure observability for mid-market SaaS (50-500 engineers).
Not enterprise. Not edge/IoT.

## Positioning statement
We help DevOps teams resolve incidents before customers notice,
through causal root-cause analysis, unlike dashboard-first monitoring tools.
```

## Quality rules

The final output enforces:

- No sentence over 20 words
- No unverifiable adjectives ("innovative", "cutting-edge", "world-class")
- Every claim is either already true or explicitly marked as a bet
- Aspirational claims use "By [date], we plan to..." — never "We are..."
- Positioning statement under 30 words
- All sections combined under 200 words

## Requirements

- Claude Code CLI
- Web search tools (for competitive research phase) — works best with Perplexity or Exa MCP servers configured, but will use built-in web search as fallback

## License

MIT
