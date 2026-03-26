---
name: positioning
description: Guide founders and teams through a structured positioning statement exercise. Combines competitive research, strategic questioning, and team alignment to produce a sharp, honest positioning statement. Use when a company needs to define who they are, what they offer, and why anyone should care.
---

# Positioning Skill

Structured positioning statement exercise for startups and teams. Combines deep competitive research with forced-choice strategic questions to produce an honest, compressed positioning statement.

Designed for accelerator portfolio companies, internal use, or any team that can't answer "why us?" in one sentence.

## Philosophy

Most positioning exercises produce corporate fluff because they skip the hard questions. This skill forces honesty by:
- Researching competitors BEFORE asking questions (so you can't hide from reality)
- Searching for structural analogs in other categories (not just direct competitors)
- Making every question a forced choice (no "all of the above")
- Requiring the team to write independently, then collide answers
- Testing defensibility with a cornerstone question
- Compressing the final output to under 30 words

The output is not marketing copy. It's a strategic alignment tool.

## Workflow

### PHASE 1: Context gathering

**Action:** Use `AskUserQuestion` to collect basic info.

```
Questions:
1. "What does the company do? (2-3 sentences, plain language)"
   - Free text
2. "Who is the target customer today?"
   - Free text
3. "What stage? What's the team size?"
   - Options: [Pre-seed solo/duo, Pre-seed with team (3-8), Seed, Series A+]
4. "Is there an existing website, pitch deck, or memo I should read?"
   - Free text (URLs or file paths)
```

**If the user provides a file path or URL:** Read it. Extract product description, claimed differentiators, current messaging, pricing, and team.

### PHASE 2: Competitive research

**Action:** Before launching research, detect available research tools by calling `ListMcpResourcesTool` or checking which MCP tools are available. Build a tool instruction block based on what's present.

**Tool detection priority (check in order, use all that are available):**

| MCP Tool Pattern | What it provides | How to use |
|---|---|---|
| `mcp__perplexity__perplexity_research` | Deep multi-source research | Use for the primary competitive landscape query |
| `mcp__perplexity__perplexity_search` | Fast web-grounded search | Use for quick competitor lookups |
| `mcp__exa__web_search_exa` | Semantic web search | Use for finding similar/adjacent companies |
| `mcp__parallel-search__web_search_preview` | Parallel web search | Use for batch competitor searches |
| `mcp__parallel-task__createDeepResearch` | Analyst-grade research reports | Use for deep competitor analysis |
| `mcp__firecrawl__firecrawl_search` | Web search + scraping | Use for competitor website analysis |
| `WebSearch` (built-in) | Basic web search | Always available as fallback |
| `WebFetch` (built-in) | Fetch URL content | Always available as fallback |

**Compose the research tool instructions dynamically.** For example:
- If Perplexity is available: "Use `mcp__perplexity__perplexity_research` for the main competitive landscape query, then `WebFetch` to verify specific competitor websites."
- If Exa is available: "Use `mcp__exa__web_search_exa` for semantic search to find companies similar to [description]."
- If nothing extra is available: "Use `WebSearch` for competitor queries and `WebFetch` on each competitor's website."

**Launch 2 parallel agents with the detected tools:**

**Agent 1: Direct competitors**
```
Launch an Agent (general-purpose) with this prompt:

Research the competitive landscape for: [company description from Phase 1].

[INSERT DETECTED TOOL INSTRUCTIONS — tell the agent exactly which tools to use]

Find:
1. The 3-5 closest competitors (same customer, same problem)
2. For each: one-liner positioning, pricing, key differentiator, weakness
3. What do ALL of them say? (common claims = table stakes, not differentiators)
4. What does NONE of them say? (potential white space)

Output as a markdown table + 3 bullet summary.
```

**Agent 2: Adjacent/aspirational competitors**
```
Launch an Agent (general-purpose) with this prompt:

Research companies adjacent to: [company description from Phase 1].

[INSERT DETECTED TOOL INSTRUCTIONS]

Find:
1. 2-3 companies solving a related problem for the same customer
2. 2-3 companies solving the same problem for a different customer
3. Any company that this team might secretly aspire to be (the "we're like X but for Y" reference)

For each: one-liner, why they matter as context.
```

**Agent 3: Structural analog competitors**
```
Launch an Agent (general-purpose) with this prompt:

Find companies in DIFFERENT categories that solved a structural analog of this problem:
[company description from Phase 1].

[INSERT DETECTED TOOL INSTRUCTIONS]

The goal is NOT to find competitors — it's to find companies that faced
the same STRUCTURAL challenge (accessibility vs. power, automation vs. control,
expert tool vs. mass market) in a completely different domain.

Find:
1. 2-3 companies that democratized an expert-only category
   (e.g., Figma for design, Square for payments, Canva for graphics)
2. For each: what was the structural barrier, how did they break it,
   what did incumbents dismiss that became the new company's cornerstone
3. What pattern emerges across these analogs that applies to [company]?

Output as a table + 1 paragraph on the structural pattern.
```

**Why this matters:** Direct competitors reveal table stakes. Adjacent competitors reveal alternative approaches. Structural analogs reveal the deeper pattern — what's structurally broken in the category that nobody inside it can see. The most defensible positioning often comes from structural analogs, not direct competition.

**Launch all three agents in parallel.** The skill works with just built-in WebSearch/WebFetch but produces richer research when Perplexity, Exa, or other research MCPs are configured.

**After agents return:** Present findings to user as a compact summary. Ask:

```
AskUserQuestion:
- "Anything missing or wrong in this competitive picture?"
  Options: [Looks right, Let me add/correct]
- "Which competitor do founders most often compare you to?"
  Free text
```

### PHASE 3: The four questions

**Action:** Present the four positioning questions using `AskUserQuestion`. Each question is informed by the competitive research.

**IMPORTANT:** Frame questions using SPECIFIC competitor names and findings from Phase 2. Do not use generic placeholders.

---

**Q1: The founder/customer test**

```
header: "The customer test"
question: |
  Your ideal customer is evaluating you against [TOP COMPETITOR 1] and [TOP COMPETITOR 2].
  They can only pick one. Why do they pick you?

  Rules:
  - Don't say "price" or "we're cheaper"
  - Don't say "better technology" without specifics
  - Don't say "customer service" (everyone says this)
options:
  - [Generate 3-4 options based on research findings, each representing a distinct strategic direction]
  - "Something else (write your own)"
```

**Q2: The honest gap**

```
header: "The honest gap"
question: |
  What is the single biggest reason your ideal customer says NO today?
  Be specific. Not "we're early stage" — that's a cop-out.
options:
  - [Generate 3-4 options based on competitive weaknesses found in research]
  - "Something else (write your own)"
```

**Q3: The core bet**

Before presenting options, first surface the shared assumption:

```
Think step by step:
1. Review all competitors from Phase 2 (direct, adjacent, AND structural analogs)
2. Identify what ALL of them assume to be true about this market
3. Ask: "Is there a direction that BREAKS this shared assumption?"
4. Include that assumption-breaking direction as one of the options below
```

```
header: "The core bet"
question: |
  You can only invest in ONE of these directions for the next 6 months.
  Which one?

  Note: Based on research, all your competitors seem to share this assumption:
  "[STATE THE SHARED ASSUMPTION]"
  One of the options below challenges this assumption directly.
options:
  - [Generate 2-3 options based on the white space found in research,
     each with a 1-sentence description of what it means concretely]
  - [Generate 1 option that BREAKS the shared assumption identified above —
     label it: "Break the assumption: [description]"]
  - "Something else (write your own)"
```

**Q4: Market scope**

```
header: "Market scope"
question: |
  Which market are you actually in? Pick the one that defines your roadmap.
options:
  - [Generate 3-4 market definitions from narrow to broad,
     based on the company's product and competitive research.
     Example: "Smart contract security for Solidity only" vs
     "AI code security for all languages" vs
     "Critical infrastructure verification"]
```

**Q5: Your first draft**

After the four questions, immediately ask:

```
AskUserQuestion:
- "Now write your positioning statement. Under 30 words. Don't overthink it — gut reaction based on what you just answered."
  Template: We help [WHO] achieve [WHAT] through [HOW], unlike [ALTERNATIVE].
  Free text
```

**Do not skip this.** Save the user's draft verbatim. In Phase 6, show it side-by-side with the final synthesized version and call out what changed and why.

### PHASE 4: Team collection

**Action:** After the user completes all five questions, generate the team exercise.

Output a clean markdown block that the user can copy-paste to their team:

```markdown
# Positioning Exercise — [Company Name]

Answer each question independently. Don't discuss with teammates first.
Spend max 10 minutes total. Gut reactions > polished answers.

## 1. The customer test
[Customized question with competitor names from research]

## 2. The honest gap
[Customized question]

## 3. The core bet
[Customized question with forced-choice options]

## 4. Market scope
[Customized question with scope options]

## 5. Positioning statement
Fill in, keep under 30 words:
We help [WHO] achieve [WHAT] through [HOW], unlike [ALTERNATIVE].

---
Return all answers to [user name] by [user specifies deadline].
```

Then ask:
```
AskUserQuestion:
- "Send this to your team and paste all their replies here when you have them.
   How many people will respond?"
  Free text
```

### PHASE 5: Synthesis

**Action:** When user pastes team replies, analyze them.

**Analysis structure:**

1. **Alignment map** — Where does everyone agree? (These are real. Use them.)
2. **Contradiction map** — Where do people disagree? (These are the strategic decisions that need to be made.)
3. **Surprise findings** — Anything one person said that nobody else did but is clearly right.
4. **Gap analysis** — Questions nobody answered well (signals the team hasn't thought this through).

Present this analysis, then ask:

```
AskUserQuestion:
- "For each contradiction, which direction do you want to go?"
  [Present each contradiction as a forced binary choice]
```

### PHASE 6: Final positioning statement

**Action:** Generate the combined positioning statement.

**Output format:**

```markdown
# [Company Name] — Positioning Statement

## The customer test
[2-3 sentences. Lead with the answer. No fluff.]

## The honest gap
[1-2 sentences. Brutally honest.]

## The core bet
[2-3 sentences. What you're building, what exists today vs. planned.]

## Market scope
[1 sentence. The market you chose and what it excludes.]

## Positioning statement
[Under 30 words. Fill in the template:]
We help [WHO] achieve [WHAT] through [HOW], unlike [ALTERNATIVE].

## Your first draft vs. final
> **Your draft:** [user's verbatim draft from Phase 3 Q5]
> **Final:** [synthesized version above]
> **What changed:** [1-2 sentences on what shifted and why — e.g. "You led with technology, the team led with outcome. The final version centers the customer problem."]

## The cornerstone test
[Answer this: "What did your competitors explicitly reject or ignore that you made central to your product?" If the answer is "nothing" — the positioning is incremental, not structural. If specific — this is the most defensible part of the positioning.]
```

**Quality rules for final output:**
- No sentence over 20 words
- No adjectives that can't be verified (remove "innovative", "cutting-edge", "world-class", "unique")
- Every claim must be either (a) already true or (b) explicitly marked as a bet
- If something is aspirational, say "By [date], we plan to..." — not "We are..."
- Total length: under 200 words for all sections combined

**Save to:** Ask the user where they'd like to save the output.

### PHASE 7: Iteration (optional)

If user wants to iterate, use `AskUserQuestion` to identify which section needs work. Re-run only that section's question with tighter constraints.

## Anti-patterns to avoid

- **Don't generate positioning without research.** The competitive context is what makes questions sharp.
- **Don't let the user skip the team exercise.** Solo positioning statements are echo chambers.
- **Don't use marketing language.** If it sounds like it belongs on a SaaS landing page, rewrite it.
- **Don't accept "all of the above" answers.** Force choices. The pain of choosing IS the exercise.
- **Don't make the final statement longer than 30 words.** Compression is clarity.
