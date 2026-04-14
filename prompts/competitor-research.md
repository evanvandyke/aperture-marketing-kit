# Prompt: Competitor Research

**When to use this:** You need to understand what your competitors are actually doing for SEO, content, and positioning before you make strategic bets. Run this before building a comparison page, before writing content that targets their keywords, and before claiming you're differentiated.

**When NOT to use this:** As the first thing you do on a new project. Understand your own positioning first (see `enrichment.md`) — otherwise the comparison is meaningless because you don't have a baseline to compare against.

---

## The prompt

```
Research these competitors and report back. Do not speculate — pull everything
from their actual sites. Quote directly wherever possible.

Competitors:
1. [COMPETITOR NAME] - [URL]
2. [COMPETITOR NAME] - [URL]
3. [COMPETITOR NAME] - [URL]

For each one, extract:

a. One-sentence pitch — their headline hero claim, quoted directly from the page
b. Who they target — from the language on the site, who is this written for?
   Be specific about role, company size, and sophistication level.
c. Category positioning — are they claiming to be a [X] or a [Y]? What category
   do they put themselves in? Use their own language.
d. Voice — 3-5 words that describe how they sound
e. Content strategy signals — do they have a blog? How often are they publishing?
   What topics dominate? (If they have a blog, look at the last 10-20 posts.)
f. Their obvious strengths — what are they doing well that I should either learn
   from or avoid competing with head-on?
g. Their obvious weaknesses — what's clearly missing, generic, or half-baked on
   their site?
h. Keyword hints — based on their page titles, meta descriptions, and H1s, what
   search queries are they targeting?

Then synthesize across all competitors:

1. Where do they all look the same? (This is table-stakes positioning — you
   can't differentiate here, just meet the bar.)
2. Where do they differ from each other? (This is their positioning game —
   worth studying for competitive awareness.)
3. Where is NO competitor playing? (This is your whitespace — where you have
   the strongest opportunity to own ground.)
4. Based on my CONTEXT.md, where am I uniquely positioned to win? (Use my ICP
   and core insight to filter the whitespace down to what I can actually own
   credibly.)

Report in under 1000 words. Include specific quotes from competitor sites for
anything that's a direct claim.
```

---

## Why this works

Manual competitor research is slow, subjective, and rarely makes it into your strategy doc. Claude Code reads six or nine pages in two minutes, quotes what's actually there, and asks the right strategic questions at the end. You go from "I should research competitors sometime" to "I have a specific whitespace bet I want to make" in under 15 minutes.

The critical step most teams skip is the synthesis at the end. Fetching competitors and listing what they do is useful but not strategic. The strategic move is finding the pattern across them — the table stakes, the battleground, and the whitespace. That's where the bet lives.

---

## What to do with the output

1. **Save the raw output to a file** — create `research/competitor-analysis.md` in your project folder. Date it. Revisit quarterly; positioning shifts.
2. **Pull the whitespace finding into STRATEGY.md** — if Claude Code identifies a real gap, that's now a strategic priority. Add it to your backlog.
3. **Pull the keyword hints into your keyword strategy** — the queries they're targeting are queries you probably also want to rank for (or consciously avoid).
4. **Update CONTEXT.md's competitor section** with the top-level findings.

---

## Variations

**Deep dive on one competitor.** Use `/seo audit [competitor URL]` for a full technical + content audit of a single competitor. Much longer, gives you a richer picture. Use when one competitor is clearly the one to beat.

**Content reverse-engineer.** Follow up the base prompt with:

> "Fetch [competitor]/blog and list the 10 most recent posts with titles and first-paragraph summaries. What content pillars are they betting on? What topics are they ignoring?"

**Ad intelligence.** If competitors are running paid ads, use the `/ads competitor [domain]` skill to see what creative and copy they're testing. Combines nicely with content analysis: the ads reveal the hooks they're validating in market.

**Backlink reverse-engineer.** If you have Ahrefs (or similar) access:

> "Here are [competitor]'s top 20 linking domains: [paste]. Which of these domains could I also realistically get a link from, and what would be my angle for each?"
