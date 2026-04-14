# Ritual: Start of Session

*Memorize this. Every session starts the same way. The ritual is what turns Claude Code from a chatbot into an employee who remembers where you left off.*

---

## 1. Open your project folder

```bash
cd ~/path/to/your/project
code .
```

VS Code opens with your project in the sidebar. This matters — Claude Code reads files relative to the folder it's running in, so you have to be IN the project folder for CLAUDE.md to load.

## 2. Start a Claude Code session

In VS Code, open a terminal (View menu → Terminal, or press `` Cmd+` `` on Mac, `` Ctrl+` `` on Windows). Then type:

```bash
claude
```

Claude Code starts. You should see a prompt asking what you want to do.

## 3. Say the magic sentence

Type this:

> We're working on [project name]. Read NOW.md, STRATEGY.md, and CONTEXT.md and tell me what's next.

Claude Code will read all three files and summarize them. This is the most important step in the whole session. Here's why: if Claude's summary is wrong or incomplete, you catch it in 30 seconds — before any real work happens. If Claude's summary is right, you have confidence it actually understood the project and the work you're about to do will be informed.

Don't skip this. It's the difference between a session that feels like working with a senior marketer and a session that feels like talking to a stranger.

## 4. Confirm or redirect

After the summary, Claude will usually propose a next action based on what's in NOW.md. You have three options:

- **Confirm.** "Yes, let's work on that."
- **Redirect.** "Actually, I want to work on something different today. Let's do [Y] instead."
- **Explore before committing.** "Before we pick, tell me more about [Z]."

## 5. Work

This is where real work happens. Use slash commands (`/seo audit`, `/seo page`, `/ads google`, `/geo-optimization`) or describe what you want in natural language. Both work.

If you feel the session drifting from the plan — Claude is going down a rabbit hole, or making changes you didn't ask for — stop and redirect. You drive. Claude is a collaborator, not a manager.

---

## Common mistakes

**Skipping the summary step.** If you dive into work without making Claude read NOW.md, you're relying on it to guess your context. The output will be generic or subtly wrong. The summary step costs 30 seconds and saves an hour.

**Starting Claude Code outside the project folder.** Claude Code needs to be running IN the project directory to see CLAUDE.md. If you start it in your home folder, it won't load anything. Always `cd` into the project first.

**Treating it like ChatGPT.** ChatGPT is a chat. Claude Code is an employee inside your project. Give it tasks, not questions-in-a-vacuum. "Audit the landing pages in /industries" beats "What do you think of SEO?"

**Running multiple sessions on the same project at the same time.** They can't see each other's work. If you need parallel work, commit frequently so both sessions can pull the latest files.
