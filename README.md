# Aperture Marketing Kit

**A project scaffold for running professional SEO and paid ads work with Claude Code.**

Clone this, fill in a few files, and you'll be running `/seo audit` on your own site within 15 minutes. Every session after that starts and ends the same way. It's an operating system for marketing work, built over real campaigns at [Aperture OS](https://aperture-os.com) and packaged so you can adopt it in one afternoon.

---

## Why this exists

Most people who try to use Claude Code for marketing work hit the same wall: they open a session, ask it to do something, get a decent answer, close the session, and three days later they've forgotten what they asked and Claude has forgotten too. Every session starts from scratch. Nothing compounds.

The fix is structural. Memory lives in files. Context lives in files. Strategy lives in files. Rituals turn a chat tool into an employee who remembers where you left off. That's what this Kit packages: the exact file structure, the exact session rituals, and the exact library of prompts I reach for when I'm doing real work.

It's not magic. It's just what happens when you stop treating Claude Code like ChatGPT and start treating it like a junior strategist who lives in your repo.

---

## Who this is for

- **Founders and operators** running their own SEO and content marketing without an in-house team
- **Agency owners** who want a repeatable delivery system to run across clients
- **Non-engineer marketers** inside technical companies who need a scaffold they can clone and run
- **Anyone** who has used Claude Code a few times, found it useful, and wants it to feel reliable instead of magical

It's not for complete beginners who have never opened a terminal. You'll need the basics: clone a repo, edit a file, run a command. If you've done any of those, you're fine.

---

## What's inside (two parts)

### Part 1: Skill packs (install once per machine)

Claude Code "skills" are specialized prompt packages that unlock slash commands like `/seo audit`, `/seo page`, `/ads google`, `/seo geo`. They install into your global `~/.claude/skills/` folder and work across every project on your machine.

The Kit is built to work alongside these two open-source skill packs:

- **[claude-seo](https://github.com/AgriciDaniel/claude-seo)** by [@AgriciDaniel](https://github.com/AgriciDaniel) — the SEO command library. Site audits, technical SEO, schema, content quality, GEO, sitemap analysis, competitor pages, and more. Twenty-plus commands.
- **[claude-ads](https://github.com/AgriciDaniel/claude-ads)** by [@AgriciDaniel](https://github.com/AgriciDaniel) — the paid advertising command library. Google, Meta, LinkedIn, TikTok, Microsoft. Full audits, creative review, budget allocation, tracking health checks.

Both packs install in about two minutes apiece. We did not fork them — they're actively maintained, they work, and forking would mean carrying our own versions forever. This Kit is the project layer we run on top of them.

> **Team or Enterprise plan users:** your admin can deploy these skill packs organization-wide, which saves every team member from installing manually. Worth checking before you clone anything.

### Part 2: Project starter (clone per project)

The files in `project-starter/` are what you copy into every new marketing project folder. Once in place, Claude Code reads them at session start and knows exactly how to work on the project — what it sells, who it sells to, what's already been done, what's next.

| File | What it does |
|---|---|
| `CLAUDE.md` | Tells Claude Code what to read at the start of every session, the hard rules it can't break, and the voice rules for the project |
| `NOW.md` | The single "what's next" file. First thing Claude Code reads. Updated at the end of every session. |
| `STRATEGY.md` | Priority backlog, phase roadmap, strategic context. The "why" behind NOW.md. |
| `CONTEXT.md` | Product, ICP, voice, positioning, competitors, founder story. The source of truth for everything Claude Code produces. |
| `CONTENT-INDEX.md` | Dedup tracker so you never accidentally write the same post twice |
| `.gitignore` | Sensible defaults that prevent you from committing secrets, OS junk, or editor files |

The other top-level folders in the Kit:

- **`rituals/`** — the start-of-session and end-of-session procedures, documented as muscle memory you can practice
- **`prompts/`** — copy-paste prompts for high-leverage moves: positioning extraction, competitor research, landing page triage, content optimization
- **`docs/`** — install guide and troubleshooting for people who aren't engineers

---

## Quick start

```bash
# 1. Install the skill packs (one-time, per machine)
mkdir -p ~/.claude/skills
git clone https://github.com/AgriciDaniel/claude-seo.git ~/.claude/skills/claude-seo
git clone https://github.com/AgriciDaniel/claude-ads.git ~/.claude/skills/claude-ads

# 2. Clone this Kit
git clone https://github.com/evanvandyke/aperture-marketing-kit.git

# 3. Copy the project starter into a new folder for your business
mkdir ~/my-seo-project
cp -r aperture-marketing-kit/project-starter/. ~/my-seo-project/

# 4. Initialize git in your new project
cd ~/my-seo-project
git init

# 5. Open in VS Code and start a Claude Code session
code .
# Then open a terminal in VS Code (View → Terminal) and run:
claude

# 6. In the Claude Code session, say:
# "Read NOW.md, STRATEGY.md, and CONTEXT.md and tell me what's next."
```

From there, Claude Code will walk you through filling out `CONTEXT.md` for your business. That's the most important step — the quality of everything you produce depends on the quality of that file.

**First session shortcut.** If you can't figure out where to start with CONTEXT.md, say this in your Claude Code session:

> "Fetch my homepage at [URL] and produce a first draft of CONTEXT.md based on what's already on the site. I'll refine it from there."

That alone is probably the fastest onboarding you'll get.

---

## The philosophy

Three ideas underneath everything in this Kit:

**1. Files are memory.** Claude Code forgets between sessions. Anything that needs to persist — strategy, context, voice, backlog, "what's next" — lives in a markdown file in the repo. The file is the memory. If it's not in a file, it doesn't exist.

**2. Session rituals make the tool feel reliable.** Opening a session without a ritual is chaotic. Every session starts by reading `NOW.md`. Every session ends by updating `NOW.md` and committing. Two rituals, practiced until they're automatic, and the tool starts feeling like an employee who remembers where you left off.

**3. AI-first thinking beats manual work.** The biggest wins come from asking Claude Code to do research, extraction, and analysis that would take you a week manually. The prompts in `prompts/` are the ones I reach for most often — the "show Claude the site and have it extract the positioning" kind of moves. Stop asking "how do I research this?" and start asking "how do I get Claude to research this for me?"

---

## Directory structure

```
aperture-marketing-kit/
├── README.md              ← you are here
├── LICENSE
├── project-starter/       ← copy these files into every new project
│   ├── CLAUDE.md
│   ├── NOW.md
│   ├── STRATEGY.md
│   ├── CONTEXT.md
│   ├── CONTENT-INDEX.md
│   └── .gitignore
├── rituals/
│   ├── START-OF-SESSION.md
│   └── END-OF-SESSION.md
├── prompts/
│   ├── enrichment.md           ← sharpen ICP + positioning from your site
│   ├── competitor-research.md  ← extract competitor positioning and whitespace
│   ├── landing-page-triage.md  ← keep/kill/rewrite verdict for LP cleanup
│   └── content-optimization.md ← GSC striking-distance query optimization
└── docs/
    ├── installing-claude-code.md   ← for non-engineers
    └── troubleshooting.md
```

---

## What this is NOT

- **Not a silver bullet.** This is methodology, not software. It works because you fill the files in thoughtfully. Empty files produce empty output.
- **Not a replacement for strategy.** The Kit enforces a structure for strategic thinking. It doesn't think for you.
- **Not a maintained software product.** It's a template. Clone it, fork it, modify it, make it yours. The structure is the gift.
- **Not specific to SEO.** Most of it applies to any kind of marketing work. The prompts are SEO-heavy because that's what Aperture OS runs most often, but the project structure works for ads, content, or anything else Claude Code can help with.

---

## Credits

- **Skill packs** by [Daniel Agrici](https://github.com/AgriciDaniel). Without `claude-seo` and `claude-ads`, none of this works. They're the foundation.
- **Kit** assembled by [Evan Van Dyke](https://aperture-os.com), founder of [Aperture OS](https://aperture-os.com). Built over hundreds of sessions on real SEO and ads campaigns for my own product and client projects.
- **Methodology** informed by painful lessons about what doesn't work, dozens of published blog posts, three automated content pipelines, and some expensive ad experiments that didn't pan out.

If you get value from this, the best thing you can do is star the two skill pack repos — claude-seo and claude-ads — and tell Daniel his work matters. He's the reason the rest of this exists.

---

## License

MIT. Use it, fork it, remix it, sell derivative work based on it. Attribution appreciated but not required. See `LICENSE` for the full text.

---

## Contact

Questions, suggestions, or stories about how you're using the Kit? Find me at [aperture-os.com](https://aperture-os.com) or [@evanvandyke on GitHub](https://github.com/evanvandyke).
