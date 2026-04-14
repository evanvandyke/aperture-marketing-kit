# Troubleshooting

*Common problems people hit when using Claude Code + the Aperture Marketing Kit. If your issue isn't here, type `/help` in any Claude Code session, or check the official docs at [code.claude.com/docs](https://code.claude.com/docs).*

---

## Install issues

### "command not found" when I type `claude`

- **Close the terminal and open a new one.** Install needs a fresh shell to pick up the updated PATH variable. This fixes it 90% of the time.
- If still broken, restart your computer.
- If still broken, the install script didn't finish. Re-run the install command from `docs/installing-claude-code.md`.

### "I installed Claude Code but nothing happens when I run `claude`"

- Check that you're in a folder you have read/write permissions for. Don't run it in `/System/` or similar protected folders.
- Try `claude --version` to confirm the binary is installed and working.
- If `--version` works but `claude` does nothing, delete `~/.claude` and run `claude` fresh to re-authenticate.

### Windows: "git is not recognized as an internal or external command"

- You need to install **Git for Windows** separately: https://git-scm.com/downloads/win
- Accept all default options during the Git install.
- Restart PowerShell after installing.

---

## Authentication issues

### "Claude says I'm not authenticated" even though I logged in

- Run `claude /logout` then `claude` again. This clears the old token and re-authenticates cleanly.
- If the browser window never opens on first login, the URL probably got copied to your clipboard. Paste it into a browser manually.

### "My authentication expired in the middle of a session"

- Just run `claude /login` to re-authenticate. It's a one-minute fix and you pick up where you left off.

### "I want to switch between a personal and work Claude account"

- Use `claude /logout` to sign out of the current account, then `claude /login` to sign in to the other. Claude Code only supports one active account at a time per machine.

---

## Skills not loading

### `/seo audit` (or another slash command) returns "unknown command"

- Verify the skill pack is installed:

  ```bash
  ls ~/.claude/skills/
  ```

  You should see `claude-seo` and/or `claude-ads` as subfolders.

- If missing, re-run the clone command:

  ```bash
  git clone https://github.com/AgriciDaniel/claude-seo.git ~/.claude/skills/claude-seo
  ```

- **Restart the Claude Code session** after installing. Skills are loaded at session start.

### "I'm on a Team plan, should I install skills myself?"

No. Ask your Claude admin to deploy the skill packs at the organization level from the admin dashboard. You'll get them automatically next time you start a session. This saves every team member from installing individually.

### "A slash command exists but behaves weirdly"

- Skills update independently. Pull the latest version:

  ```bash
  cd ~/.claude/skills/claude-seo
  git pull
  ```

- Restart your Claude Code session after updating.

---

## Project / file issues

### "Claude Code doesn't see my CLAUDE.md file"

- You're running Claude Code from the wrong directory. The file is in your project folder, but Claude Code is probably running in your home folder or somewhere else.
- **Always `cd` into the project folder BEFORE running `claude`.**
- Confirm you're in the right place: `ls CLAUDE.md` — if that errors, you're in the wrong folder.

### "Claude edited a file I didn't want it to"

- If you're using git (you should be): `git diff` to see the change, `git restore [filename]` to revert.
- If you're not using git: check for an editor backup (some IDEs keep one), or rewrite from memory. **Lesson: always `git init` and commit before starting real work.**

### "I have uncommitted work and Claude Code wants to do something destructive"

- **Say NO.** Commit your work first, then let Claude proceed.
- Rule of thumb: commit between every major task. Git is your undo button.

### "Claude keeps trying to run commands that need my approval"

- That's by design — destructive commands ask for confirmation. Read each prompt carefully.
- If you're tired of approving, you can adjust permission mode in Claude Code settings, but don't turn off approval for destructive operations (`rm`, `git reset --hard`, etc.). That's how you lose work.

---

## Git issues (for non-engineers)

### "How do I undo my last commit?"

- `git reset HEAD~1` — undoes the commit but keeps your changes as uncommitted edits
- `git reset --hard HEAD~1` — undoes the commit AND throws away the changes (**DANGEROUS** — don't use unless you're sure)

### "How do I push to GitHub for the first time?"

1. Create an empty repo on GitHub.com (don't add a README or .gitignore from GitHub — you already have them)
2. In your project terminal:

   ```bash
   git remote add origin https://github.com/your-username/your-repo.git
   git branch -M main
   git push -u origin main
   ```

3. After that first push, future pushes are just `git push`.

### "Claude keeps asking for my git username/password"

- Set up a GitHub personal access token: https://github.com/settings/tokens (scopes: `repo`, `workflow`)
- Or install the GitHub CLI and authenticate once:
  - Mac: `brew install gh && gh auth login`
  - Windows: `winget install GitHub.cli` then `gh auth login`

---

## Usage / cost issues

### "I hit a usage limit"

- Your plan has a rate limit. Wait an hour, or upgrade.
- Max plan has higher limits than Pro. Team plan has shared limits across seats.
- Running `/seo audit` on a very large site is expensive — consider auditing a subfolder instead of the whole site.

### "I'm worried Claude Code will cost me extra money"

- On Pro, Max, and Team plans, Claude Code usage is included in the subscription — no per-token billing.
- On Enterprise, there may be usage overage billing depending on your contract.
- Check your plan and billing at [claude.com/settings/billing](https://claude.com/settings/billing).

---

## Behavior problems

### "Claude Code is stuck in a loop or hung"

- Press `Esc` or `Ctrl+C` to interrupt.
- If it won't respond, type `/exit` to force-close the session.
- Start a fresh session with `claude`.

### "Claude is ignoring rules in CLAUDE.md"

- Read your CLAUDE.md yourself first — sometimes the rules are unclear or conflict with each other.
- Re-state the rule in plain language in your current message: "Stop doing X — that's against the rule in CLAUDE.md under 'hard rules'."
- Update CLAUDE.md to be more explicit if the rule is ambiguous. Rules should leave no wiggle room.

### "Claude made up a statistic / gave me a wrong number"

- LLMs hallucinate. Always verify data claims against source material.
- Add a rule to CLAUDE.md: *"Do not fabricate statistics, testimonials, or case studies. If you need a number, ask me for a source or say 'I don't have data for this.'"*
- If Claude cites a source, click through and verify.

### "Claude is being too agreeable and not pushing back"

- Add to CLAUDE.md: *"Push back when you disagree with me. Friction is the feature. I'd rather you argue than silently execute a bad plan."*
- Explicitly ask in your messages: "Before you do this, is there a reason this plan is bad? Push back if you see one."

---

## "I'm stuck and the above didn't help"

1. Type `/help` in any Claude Code session
2. Check the official troubleshooting guide: [code.claude.com/docs/en/troubleshooting](https://code.claude.com/docs/en/troubleshooting)
3. Ask Claude Code itself: "I'm stuck with [describe problem]. Walk me through diagnosing it."
4. Ask the Claude Code community on Discord (linked from [code.claude.com](https://code.claude.com))
