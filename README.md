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

### 1. Clone the Kit and set up your project folder

```bash
# Clone this Kit
git clone https://github.com/evanvandyke/aperture-marketing-kit.git

# Create a new project folder for your business
mkdir ~/my-marketing-project
cp -r aperture-marketing-kit/project-starter/. ~/my-marketing-project/
cd ~/my-marketing-project
git init
```

### 2. Open in VS Code and start Claude Code

```bash
code .
```

Open the integrated terminal in VS Code (View → Terminal, or `` Cmd/Ctrl + ` ``) and run:

```bash
claude
```

### 3. Ask Claude to install the skill packs

This is where the Kit deviates from most install guides: you don't run the install commands yourself. You ask Claude to do it for you. Paste this exact message into the Claude Code session:

```
I want to install two open-source skill packs for this project. Install
them at the project level (inside .claude/skills/ in this folder) so they
only load for this project, not globally on my machine.

Source repos:
- https://github.com/AgriciDaniel/claude-seo
- https://github.com/AgriciDaniel/claude-ads

Each repo contains multiple skills under a skills/ directory and agents
under an agents/ directory. Clone the repos, copy the contents of their
skills/ folders into .claude/skills/ in this project, and copy their
agents/ folders into .claude/agents/ in this project. When you're done,
confirm by listing what /seo commands are now available.
```

Claude clones the repos, copies the files, and reports back with the full list of commands now available. If something goes wrong, Claude explains what and why — and you fix it by asking. This "use the machine to build the machine" pattern is the core move the Kit is built around.

**Why project-scoped and not global?** Skills at the project level only load inside this specific folder. That keeps marketing tools isolated from any other Claude Code work on your machine, and makes your project self-contained. You can always install globally later if you want the skills everywhere.

### 4. Start your first session

Tell Claude to read the project files:

> Read NOW.md, STRATEGY.md, and CONTEXT.md and tell me what's next.

Claude walks you through filling out `CONTEXT.md` for your business. That's the most important step — the quality of everything you produce depends on the quality of that file.

**First session shortcut.** If you don't know where to start with CONTEXT.md, say:

> Fetch my homepage at [URL] and produce a first draft of CONTEXT.md based on what's already on the site. I'll refine it from there.

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
