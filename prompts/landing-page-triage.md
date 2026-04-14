# Prompt: Landing Page Triage

**When to use this:** You have a lot of landing pages (10, 50, 85, 500) and you need to decide which to keep, which to unpublish, which to rewrite. Most common scenarios: inheriting an old site, cleaning up after a programmatic page experiment, or auditing an indexing bloat problem.

**When NOT to use this:** If you have fewer than 5 landing pages. Audit them by hand in 20 minutes instead.

**The reality check:** A full "keep/kill/rewrite" verdict ideally needs two data sources — content quality (what's on the page) AND actual traffic performance (what Google and your users do with the page). This prompt covers Part 1 (content quality) in one session. Part 2 (GSC traffic overlay) is a follow-up once you've connected Google Search Console. Don't skip Part 2 — it catches the "thin but ranking" outliers that you'd otherwise kill by mistake.

---

## Part 1: Content-quality triage

**Input you need:** A list of landing page URLs. If you don't have one, ask Claude Code to pull them from your sitemap first:

> "Fetch [yourdomain.com/sitemap.xml] and give me a list of all URLs that match the pattern [/landing/*] or whatever directory your LPs live in."

Once you have the list, use this prompt:

```
I have [N] landing pages I need to triage. Here are the URLs:

[paste the list, or point to the sitemap and the pattern]

For each page, fetch it and score on this 5-point rubric (1-5 each, where
5 is best):

1. Title uniqueness — is the title unique and specific, or templated/duplicate?
2. Content depth — is there substantive content (500+ words of real information),
   or is it thin/skeleton content?
3. Unique content ratio — is this page meaningfully different from other pages
   on the site, or is it a find-and-replace of another page with a different
   city/industry/keyword swapped in?
4. Internal links — does this page link out to other pages on the site with
   meaningful anchor text, and is it linked TO from other pages on the site?
5. Schema and meta quality — does it have a proper meta description (not
   duplicated), canonical tag, appropriate schema markup?

For each page, output one row:

| URL | Title | Depth | Unique | Links | Schema | Total | Verdict |

Where Verdict is one of: KEEP, REWRITE, KILL.

Scoring guide:
- Total 20-25: KEEP — the page is solid, leave it alone
- Total 12-19: REWRITE — the page has intent but needs work
- Total below 12: KILL — unpublish, redirect to a better page

After the table, give me:

1. Total KEEP count
2. Total REWRITE count, prioritized by which to rewrite first (highest total
   score among REWRITEs goes first — closest to KEEP)
3. Total KILL count
4. Top 5 pages to rewrite, with the single most important fix for each
5. Patterns you noticed across the KILLs. For example: "all 15 city pages are
   thin templated content with only the city name swapped in", or "all 8 industry
   pages have the same meta description, which is bad for SEO". Be specific.
6. If you found programmatic pages that share a template, flag them as a group
   and recommend a batch action for the whole group.

Report the full table even if it's long. Follow with the summary sections above.
```

---

## Part 2: GSC traffic overlay (next session)

*The content-quality triage gives you a first verdict. The second layer is actual performance data from Google Search Console. Do this in a follow-up session once GSC data is available to Claude Code (either via an MCP, an export, or a copy-paste from the GSC UI).*

```
Overlay GSC data on the landing page triage from last session. GSC data:
[paste export or point to the connected MCP]

For each KILL and REWRITE verdict from Part 1:

- If the page has driven more than 50 clicks in the last 90 days, flag it for
  review — maybe it's thin but still ranking for something valuable.
- If the page has driven zero clicks and zero impressions in 90 days, confirm
  the KILL verdict and add it to the unpublish list.
- If the page ranks for any query in positions 10-30, upgrade it from KILL to
  REWRITE — it's striking-distance opportunity, not dead weight.
- If a REWRITE page has zero impressions, downgrade it to KILL — rewriting it
  won't help because Google isn't seeing it.

Produce a final action list with three sections:

1. Confirmed KILLs — URLs to unpublish, grouped by pattern where applicable
2. Confirmed REWRITEs — prioritized by existing traffic (highest traffic first)
3. KEEPs — leave alone, re-triage quarterly

For each confirmed KILL, recommend a redirect target (the closest relevant page
on the site). If no close match exists, flag it as "remove from sitemap, let it
404" instead of "redirect."
```

---

## Why this works

Triaging 85 landing pages by hand takes a week and you'll lose focus by page 20. Claude Code does Part 1 in 30-60 minutes and gives you a defensible first pass backed by an explicit rubric. The GSC overlay in Part 2 catches the "thin but ranking" outliers — the pages that look like dead weight but are quietly carrying traffic. Combined, you get a high-confidence plan in one or two sessions instead of a vague "we should probably clean up the landing pages someday" that never happens.

This is exactly the kind of work that used to require an SEO consultant and a month of project time. Now it's a prompt.

---

## What happens after the triage

- **KILL:** Unpublish the page in your CMS. If it was getting any traffic, set up a 301 redirect to the nearest relevant page. Remove from your sitemap. Request re-crawl in GSC. Track how long it takes Google to drop the page.
- **REWRITE:** Add each REWRITE page to your content backlog in NOW.md. The single most important fix from the triage is your starting point for each.
- **KEEP:** Leave alone for now. Re-triage quarterly — pages drift.

---

## Variations

**Programmatic pages specifically.** If the pages were generated from a template (city pages, industry pages, location pages), the rubric should weight "unique content ratio" heavily. Templated pages almost always fail this test, and the fix is usually either (a) add substantive unique content to each, or (b) consolidate into a single page with an interactive filter.

**Whole-site audit, not just a directory.** Skip the URL list and start with the full sitemap. Ask Claude Code to crawl it, group pages by URL pattern, and triage each group separately. More efficient for sites with 500+ pages where you don't even know what's live.

**Indexation bloat check.** Combine triage with `/seo technical` findings. If a page is KILL and also has indexation problems (duplicate content, thin content, canonical issues), that's a double-confirmation — unpublish with confidence.

**Conservative mode.** If you're nervous about killing pages, change the rubric thresholds: KEEP at 16+, REWRITE at 10-15, KILL below 10. Fewer kills, more rewrites. Then pair with Part 2 GSC data to confirm everything still.
