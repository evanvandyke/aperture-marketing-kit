# Strategy — {{PROJECT_NAME}}
*The "why" behind NOW.md. Revisit and refresh quarterly. The backlog below is the long-term plan; NOW.md is the immediate next actions.*

---

## The North Star

*One paragraph: what are you trying to achieve over the next 12 months, and how will you know if you're winning? Be specific. "Grow traffic" is not a North Star. "Get to 10,000 organic monthly visitors with a 3% conversion rate to free trial by Q4" is.*

> [Your North Star]

---

## Priority Order

*Which channel gets the most attention, and why? This forces tradeoffs.*

1. **[Channel]** — [why it's primary]
2. **[Channel]** — [why it's secondary]
3. **[Channel]** — [why it's tertiary or deferred]

---

## Phase 0: Foundation (do once, before anything else)

- [ ] Run full SEO audit: `/seo audit [your-url]`
- [ ] Fix all Critical items in `ACTION-PLAN.md` before moving forward
- [ ] Run technical audit: `/seo technical [your-url]`
- [ ] Run GEO baseline: `/seo geo [your-url]`
- [ ] Fill out `CONTEXT.md` completely
- [ ] Set up Google Search Console and Google Analytics 4
- [ ] Submit sitemap to GSC

*Nothing below matters if Phase 0 is incomplete. A broken technical foundation cannot be fixed with content.*

---

## Phase 1: Strategic Plan (do once, refresh quarterly)

- [ ] Run strategic plan for your industry: `/seo plan [saas|ecommerce|local-service|agency|publisher]`
- [ ] Review generated `SEO-STRATEGY.md`, `COMPETITOR-ANALYSIS.md`, `CONTENT-CALENDAR.md`, `SITE-STRUCTURE.md`
- [ ] Adapt generated plan to your actual situation (the plan is a starting point, not gospel)

---

## Phase 2: Site Architecture

- [ ] Audit current URL structure
- [ ] Identify page types you need: homepage, solution/use-case pages, comparison pages, resources, blog, about
- [ ] Prioritize which page types to build first based on intent (high-intent first)
- [ ] For each page type, define what "good" looks like (schema, content depth, internal links)

---

## Phase 3: Keyword Strategy

- [ ] Generate seed list (40-60 keywords) — ask Claude Code or use Google Autocomplete + Trends
- [ ] Map keywords to intent buckets: problem-aware, solution-aware, comparison, category, job-to-be-done
- [ ] Map keywords to page types
- [ ] Identify your "whitespace" — keywords your competitors aren't writing for

---

## Phase 4: Content Engine

- [ ] Establish 3-4 content pillars (topical authority clusters)
- [ ] Build content calendar (4-8 posts per month)
- [ ] Write cornerstone post for each pillar (long, definitive, canonical)
- [ ] Document a repeatable writing process (outline → draft → E-E-A-T pass → GEO pass → publish)
- [ ] Build content distribution checklist

**The video→blog pipeline:** record a screen share or talking-head video on something real you're learning/building, upload to YouTube, pull the transcript, feed to Claude Code with your keyword target, publish. Firsthand voice + video SEO + blog SEO in one pass.

---

## Phase 5: Distribution

Publishing isn't enough. Same content needs to live in multiple places.

| Platform | Post type | Why |
|---|---|---|
| Reddit | Full article or link post to relevant subs | Platform traffic + Google ranking for Reddit + community validation |
| LinkedIn | Article or long-form post | Ranks on Google; reaches B2B ICP |
| X (Twitter) | X Article or thread | Ranks on Google; reaches tech/operator audience |
| YouTube | Original video | YouTube SEO + Google video results |

- [ ] Set up distribution channel for each platform
- [ ] Build a repeatable post-publish checklist

---

## Phase 5.5: Backlinks (CRITICAL for domain authority)

*Most common bottleneck for sites with good content that won't rank. Without backlinks from trusted sites, Google won't promote you to pages 1-3 regardless of content quality.*

**Weekly routine (~70 min/week):**

| Day | Activity | Time |
|-----|----------|------|
| Mon | Qwoted + Featured: check for queries, respond to 2-3 | 20 min |
| Tue | MentionMatch / Help a B2B Writer: scan email, respond | 10 min |
| Wed | Buffer — catch up on unanswered queries | 10 min |
| Thu | Research 1 podcast to pitch (or follow up) | 15 min |
| Fri | One outreach email (guest post, broken link, resource page) | 15 min |

- [ ] Sign up: Qwoted, Featured, MentionMatch/Help a B2B Writer
- [ ] Write your expert source response template
- [ ] Identify 10 podcasts to pitch
- [ ] Identify 5 guest post targets
- [ ] Build a linkable asset (calculator, report, template)

Aim for 4-8 new backlinks per month. Quality over quantity — one Forbes mention beats 20 directory listings.

---

## Phase 6: Comparison Pages

*High-converting, decision-stage content. Build these once you have enough brand awareness that people are actively comparing you to alternatives (usually Month 3+).*

- [ ] Identify top 3-5 competitors worth a `/compare/[us]-vs-[them]` page
- [ ] Build first comparison page using `/seo competitor-pages`
- [ ] Keep competitive claims accurate and dated

---

## Phase 7: Schema & Structured Data

- [ ] Run `/seo schema [url]` across key pages
- [ ] Add Organization + WebSite + SoftwareApplication/Product to homepage
- [ ] Add Article + Person (author) to blog posts
- [ ] Add FAQPage schema where appropriate
- [ ] Validate with Google Rich Results Test

---

## Phase 8: Ongoing Optimization Loop

**Weekly:**
- Publish 1-2 pieces of content
- Run `/geo-optimization` on each new piece before distributing
- Distribute across all channels
- Check GSC for new ranking keywords

**Monthly:**
- Run `/seo audit` — catch regressions
- Review `ACTION-PLAN.md` for new issues
- Run `/seo content` — E-E-A-T check on recent content
- Test 3-5 queries in ChatGPT + Perplexity (AI Search Testing Template)

**Quarterly:**
- Refresh `/seo plan` as product evolves
- Run `/seo geo` — track AI visibility progress
- Update comparison pages with fresh competitor data
- Review and update CONTEXT.md

---

## Current Backlog

*The running list of things to do. Priority levels are loose — use your judgment. NOW.md pulls from the top of this list for immediate work.*

| Priority | What | Why |
|----------|------|-----|
| URGENT | [task] | [reason] |
| Next | [task] | [reason] |
| Next | [task] | [reason] |
| Month 2 | [task] | [reason] |
| Month 3+ | [task] | [reason] |
| Someday | [task] | [reason] |

---

## Prioritizing Fixes: ICE Scoring

When the backlog feels long, score each item with ICE:

- **Impact** (1-3): How much will this move the needle?
- **Confidence** (1-3): How sure are you it'll work?
- **Ease** (1-3): How easy is it to execute?

**Score = I + C + E.** Highest score wins. Fixes that help both SEO AND GEO get priority at equal scores (the channels compound).

| Fix | Impact | Confidence | Ease | Score |
|-----|--------|------------|------|-------|
|  |  |  |  |  |

---

## What's NOT on the roadmap (and why)

*Being explicit about what you're not doing is as valuable as the roadmap itself. Write down the shiny things you've consciously chosen to skip.*

- [Thing you're skipping]: [why]
- [Thing you're skipping]: [why]
