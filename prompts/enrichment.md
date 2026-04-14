# Prompt: Enrichment — Extract your positioning from your own site

**When to use this:** You have a rough idea of your ICP, voice, and positioning in your head or in a draft CONTEXT.md. Before you start writing content or running audits, you want Claude Code to read what your site ACTUALLY says and compare it to what you intend. This is the fastest way to find the gaps between what you mean to communicate and what a visitor actually reads.

**When NOT to use this:** If you haven't published any content on your site yet. There's nothing to extract.

---

## The prompt

Copy this into a Claude Code session. Replace `[YOUR URL]` with your homepage.

```
Fetch my homepage at [YOUR URL] and extract, based ONLY on what's actually on the page:

1. The one-sentence product pitch — how the site describes what you do. Quote it
   directly if there's a clear hero headline. If not, synthesize what the page is
   trying to say in one sentence.

2. The ICP — who is this site obviously written for? What's their role, company
   size, pain point, sophistication level? Be specific; don't hedge.

3. The core insight — what's the one understanding about the customer this site
   is trying to communicate? What problem does it say you solve that competitors
   don't?

4. The voice — what does the brand sound like? List 3-5 specific words or phrases
   that are distinctive. Note any filler words, corporate jargon, or signs of
   generic SaaS writing.

5. What's clearly missing — based on SEO and GEO best practices, what's noticeably
   absent from the page? Think: direct answer in the first 60 words, E-E-A-T
   signals, specific data points, schema hints, quotable claims.

6. The biggest inconsistency — if there's a gap between what the site claims to
   be and how it actually reads, name it.

Don't speculate. Pull everything from what's actually on the page.

Now compare your findings to what's in CONTEXT.md (or ask me if CONTEXT.md isn't
filled out). Produce a side-by-side:

| Aspect | What the site says | What I want it to say | Gap |

Finally, give me three specific, concrete changes I could make to the homepage
copy today that would close the biggest gap. Be prescriptive — "change headline
from X to Y" not "the headline could be clearer."
```

---

## Why this works

Most business owners can't see their own site clearly. They've been staring at it through the context of a hundred internal meetings and they can't read it the way a stranger does. Claude Code reads it fresh and tells you what the page actually communicates — which is almost never exactly what you meant.

This is the AI-first thinking move. Instead of spending a week in a positioning workshop, you get a 90-second audit of your current positioning plus three concrete fixes. You've just compressed a consulting engagement into a prompt.

---

## What to do with the output

1. **If the gaps are small:** Your CONTEXT.md is accurate and your site reflects it. Move on.
2. **If the gaps are medium:** The site needs a copy pass. Take the three concrete changes and ship them today.
3. **If the gaps are huge:** You have a positioning problem, not a copy problem. Go back to CONTEXT.md and figure out what you actually stand for before rewriting the homepage.

---

## Variations

**Full site version.** Instead of the homepage only, ask Claude Code to fetch your top 5 pages and run this extraction on each. Then ask: "Do all five pages speak to the same ICP in the same voice? Where's the drift?"

**ICP-first version.** If CONTEXT.md is already filled out, invert the prompt:

> "Here's my CONTEXT.md. Fetch my homepage and tell me: would the ICP I described feel spoken to, or would they bounce? What would I need to change on the homepage to make this ICP feel like I wrote the page for them personally?"

**Competitive version.** Point Claude Code at your homepage AND a competitor's homepage in the same prompt:

> "Fetch my homepage AND [competitor URL]. Compare one-sentence pitches, voice, and the ICP each speaks to. Where am I differentiated? Where am I invisible? Where do we sound identical?"

**The "build CONTEXT.md from scratch" shortcut.** If you haven't filled out CONTEXT.md yet, use this prompt to bootstrap a first draft:

> "Fetch my homepage at [URL] and produce a first draft of CONTEXT.md based on what's already there. I'll refine it from there."
