# Prompt: Content Optimization (GSC Striking-Distance)

**When to use:** You have content that's indexed and ranking somewhere on pages 2-5 of Google — positions 10-50. Instead of writing new content, you can push these pages up by weaving the actual queries Google is already surfacing into your existing copy. This is the single highest-leverage content move you can make on a mature site.

**When NOT to use:** If the content isn't indexed yet, or if it's already consistently on page 1. This prompt is for the "close but not quite" zone where small changes have outsized effects.

---

## Prerequisite

You need Google Search Console data for the page you're optimizing. You can get it three ways:

1. **GSC MCP server** connected to Claude Code — fastest, most powerful
2. **Manual CSV export** from GSC (Performance report → filter by page URL → Queries tab → Export)
3. **Screenshot or copy-paste** the GSC query list for a specific page

Any of the three works. The MCP is the cleanest if you can get it set up.

---

## The prompt

Copy this into Claude Code. Replace `[URL]` and paste your GSC data.

```
I want to do a striking-distance optimization pass on [URL]. GSC data for this
page:

[paste CSV contents, or point to the MCP/file]

Step 1: From the GSC queries, identify the 5 highest-opportunity queries.
Opportunity = high impressions + position 10-30 + relevance to the page's topic.
Report them as a table:

| Query | Position | Impressions | Clicks | CTR | Opportunity score |

Step 2: For each of the top 3 queries, quote the current page content and show
me:
a. Whether the exact query phrase appears anywhere on the page currently (yes/no)
b. The 2-3 best places in the existing content to weave it in naturally — not
   keyword stuffing, natural language that a human reader wouldn't notice
c. The specific edit you'd propose, quoted before/after

Step 3: Check the meta description. Does it include the primary target query?
If not, propose a rewrite that includes it and still reads well. Quote current
vs proposed.

Step 4: Does the page have a direct-answer block in the first 150 words that
answers the primary query? If not, draft one — 60-100 words, self-contained,
citable by an LLM, leading with the answer in the first sentence. This is the
GEO move — LLMs extract this kind of block as a citation.

Step 5: Internal linking audit. Look at the other content on the site (fetch
the sitemap if needed). Which other pages should link TO this page with exact-
match anchor text using the target query? Propose 3-5 specific inbound links:
(a) source page URL, (b) sentence to add the link to (quoted), (c) anchor text.

Step 6: Summary action list. A numbered list of exact edits to make, in order.
After each edit, note which query position it's expected to improve.
```

---

## Why this works

Content optimization beats new content creation on most mature sites. A page already indexed at position 20 has existing authority and trust signals. Moving it to position 5 compounds on work you already did. Writing a new page starts from zero every time.

The move that matters: you're not keyword-stuffing, you're matching the exact language Google already thinks your content is about. GSC is telling you which queries are knocking on your door. Your job is to open it — add the specific phrasing to the page so Google's confidence in the match goes up.

Second-order benefit: the direct-answer block in Step 4 isn't just SEO. It's GEO. LLMs extract 60-100 word answer blocks as citations. A page optimized for striking-distance queries with a clean answer block wins in both channels at the same time.

---

## What to do after the optimization

1. **Apply the edits** in your CMS. If your content lives in a file or database Claude Code can reach, have Claude apply them directly and commit.
2. **Request re-indexing in GSC** for the edited URL — Search Console → URL Inspection → Request Indexing. Without this step, Google may take weeks to re-crawl.
3. **Track the queries weekly** — position movement usually shows up within 2-4 weeks.
4. **If no movement after 4 weeks:** the page needs more than a copy tweak. Consider a full rewrite, more backlinks, or schema improvements. This prompt was the first punch, not the only punch.

---

## Variations

**Cluster optimization.** Instead of one URL, run this on a cluster of 3-5 related pages. Look for shared queries that could benefit from internal links between the cluster members. Pages in a cluster reinforcing each other with exact-match anchor text is one of the most underused moves in SEO.

**"Why isn't this ranking?" diagnostic.** If a page has high impressions but terrible CTR (under 1%), the content isn't the problem — the title and meta description are. Ask Claude Code to rewrite those specifically.

**Standalone answer block generator.** If Step 4 shows the page is missing a direct-answer block, you can run this as its own prompt in a follow-up session:

> "Draft a 60-100 word answer block that directly answers the query '[QUERY]' using only information from [URL]. Self-contained, citable, leads with the answer in the first sentence, includes one specific data point if the page has one."

**The 'page is dying' diagnostic.** If a page used to rank and now doesn't, run the prompt anyway but add: "Also tell me what likely changed. Did I lose backlinks? Is there a newer competitor page outranking mine? Is the content out of date?"
