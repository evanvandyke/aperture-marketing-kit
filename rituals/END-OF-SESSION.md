# Ritual: End of Session

*The close-out ritual matters as much as the start ritual. Skip it once and the next session will be confused. Skip it twice and you've lost the plot.*

---

## 1. Update NOW.md

Before you close the session, tell Claude Code:

> Update NOW.md to reflect what we did this session and what's next.

Claude will read the current NOW.md, propose an updated version, and show you a diff. Review it. Make sure:

- The "Session N" entry reflects what actually happened (not what you hoped would happen)
- Completed items are moved to the "Completed" section at the bottom
- New items that came up during the session are added to "Upcoming"
- The "Current Focus" line still reflects what you're working on this week

If the proposed update is wrong, say so. "No, we didn't finish X — it's still in progress. And add Y to the backlog because we talked about it but didn't start."

## 2. Commit and push

Still in the Claude Code session:

> Commit everything with the message "Session [N]: [one-line summary]" and push.

Or manually in the terminal:

```bash
git add -A
git commit -m "Session 12: Landing page triage on /industries directory"
git push
```

This is what makes the files feel like memory. Uncommitted work lives in RAM and dies when your laptop restarts. Committed work is durable and lives in your git history forever.

If you don't have a remote set up yet, just commit locally — you can connect a remote later without losing anything.

## 3. Note blockers (optional)

If you're blocked on something — waiting on a client, waiting on data, waiting on yourself to make a decision — add it to NOW.md under a "Blocked" section. Your future self will thank you.

## 4. Close the session

Type `/exit` or close the terminal window. The session ends. Claude Code has no memory of the conversation itself — but the files in your repo do.

---

## Why this matters

Every session starts by reading NOW.md. If you didn't update NOW.md at the end of last session, you start today with stale information. One missed update is recoverable. Three missed updates and you're running on vibes instead of a plan.

The rule: **no session ends without a NOW.md update and a git commit.** If you have 60 seconds left in your day, skip everything else and do these two things.

---

## When it's okay to skip

Rare but legitimate:

**The session did nothing.** You opened Claude Code, asked a question, got an answer, no state changed. No need to commit nothing. Don't update NOW.md just to say "asked a question."

**You ran out of time mid-work.** Your meeting is starting in 30 seconds. Skip the commit, but type one quick line at the top of NOW.md: "Session left mid-work on [task], pick up at [X]." That one line is your breadcrumb so the next session knows what was interrupted.

---

## A note on commit messages

Short, specific, past tense. The goal is that when you scroll through git history six months from now, each message tells you what that session accomplished.

**Good:**
- "Session 14: Landing page triage on /industries, 12 KILLs confirmed"
- "Session 22: Cornerstone post published, 7 internal links added"
- "Session 31: CONTEXT.md rewritten after competitor research findings"

**Bad:**
- "Updates" (what updates?)
- "Session 14" (what did you do?)
- "Various SEO improvements" (meaningless)
