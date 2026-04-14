# Installing Claude Code (for non-engineers)

*This guide is for people who are not software engineers and just need to get Claude Code running so they can do marketing work. If you know your way around a terminal, the official docs at [code.claude.com/docs](https://code.claude.com/docs) are faster.*

**Time needed:** About 15 minutes if everything goes smoothly. Add 15 more minutes if you hit a snag.

---

## What you need before you start

- A Mac, Windows, or Linux computer
- A Claude.com account on a paid plan (Pro, Max, Team, or Enterprise)
- Admin rights on your computer (to install software)
- About 15 minutes

**You do NOT need to know how to code.** You will type a few commands, but you don't need to understand how they work. Copy, paste, press Enter.

---

## Step 1: Install Claude Code

### On a Mac

1. Open the **Terminal** app. Press `Cmd + Space` to open Spotlight, type "Terminal", press Enter.
2. Paste this command into the Terminal and press Enter:

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

3. Wait for it to finish. It'll download and install Claude Code. When it's done, you'll see a success message.
4. **Close the Terminal window and open a new one.** This matters — the new terminal picks up the updated PATH so the `claude` command works.

### On Windows

1. Open **PowerShell**. Press the Windows key, type "PowerShell", press Enter.
2. Paste this command and press Enter:

```powershell
irm https://claude.ai/install.ps1 | iex
```

3. Wait for it to finish. Close PowerShell. Open a new PowerShell window.

**Important for Windows users:** You also need **Git for Windows**. Download and install it from [git-scm.com/downloads/win](https://git-scm.com/downloads/win). Accept all default options during install.

### Alternative: VS Code extension

If you already use VS Code (the free code editor from Microsoft — you should install it if you haven't, it's where most people run Claude Code), you can install Claude Code as an extension:

1. Open VS Code
2. Press `Cmd + Shift + X` on Mac, or `Ctrl + Shift + X` on Windows
3. Search for "Claude Code"
4. Click **Install**
5. Restart VS Code

The VS Code extension gives you Claude Code in a side panel with inline diff viewing, which many people prefer to the terminal.

---

## Step 2: Verify the install worked

Open a terminal (or VS Code's terminal: **View** menu → **Terminal**). Type:

```bash
claude --version
```

You should see a version number like `claude-code 1.x.x`. If you see "command not found" or similar, the install didn't complete. Close the terminal, open a new one, and try again. If it still doesn't work, restart your computer and try once more.

---

## Step 3: Log in

Type:

```bash
claude
```

The first time you run it, Claude Code will open a browser window asking you to log in. Sign in with your Claude.com account. Once you approve the connection, Claude Code is authenticated. You'll see it return to the terminal with a session prompt.

**Tip:** You only need to log in once. After that, Claude Code remembers your login across sessions.

---

## Step 4: Check your plan tier

Inside a Claude Code session, type:

```
/status
```

Claude Code will show you which plan you're on. Here's what the plans mean for marketing work:

| Plan | Price | Good for |
|------|-------|----------|
| **Pro** | $17/mo annual | Testing the waters. You'll hit usage limits on heavy audits. |
| **Max** | From $100/mo | Recommended for individuals doing regular SEO/content work. |
| **Team** | $20-25/seat/mo (5+ seats) | Recommended for companies. Includes organization-wide skill deployment, SSO, central billing, admin controls. |
| **Enterprise** | Custom | Larger orgs needing audit logs, SCIM, compliance features. |

If you don't know what plan you have, go to [claude.com/settings/billing](https://claude.com/settings/billing) while logged in to the work account you use for Claude.

**For company IT / admins:** If your org is on Team or Enterprise, you can deploy custom skills (like the ones below) at the org level so every team member gets them automatically without installing individually. Check your admin settings page in Claude.com. This is a huge time saver.

---

## Step 5: Install the SEO and ads skill packs

These are the "slash commands" that unlock `/seo audit`, `/seo page`, `/ads google`, `/geo-optimization`, and dozens of other marketing workflows. Install once and they work forever across every project you start.

**If you are on a Team or Enterprise plan:** Ask your admin to deploy these org-wide. Skip to Step 6 once they're installed.

**If you're installing them yourself:** Open a terminal and run these commands:

```bash
# Create the skills directory if it doesn't exist
mkdir -p ~/.claude/skills

# Install the SEO skill pack
git clone https://github.com/AgriciDaniel/claude-seo.git ~/.claude/skills/claude-seo

# Install the ads skill pack
git clone https://github.com/AgriciDaniel/claude-ads.git ~/.claude/skills/claude-ads
```

On Windows, use the same commands in PowerShell or Git Bash.

---

## Step 6: Test everything

Make a new folder somewhere to use as a test project:

```bash
mkdir ~/test-claude-code
cd ~/test-claude-code
claude
```

In the Claude Code session, type:

```
/seo audit https://example.com
```

If Claude Code starts running an audit (you'll see it thinking, then producing output), congratulations — everything is installed correctly. You're ready to use the Aperture Marketing Kit.

If you see "unknown command" or nothing happens, the skill pack didn't install correctly. See the troubleshooting guide at `docs/troubleshooting.md` in the Kit.

---

## Next steps

1. Clone the Aperture Marketing Kit project starter into a real project folder — see the Kit README for the copy-paste commands
2. Fill out `CONTEXT.md` in your new project — this is the most important step
3. Read `rituals/START-OF-SESSION.md` and `rituals/END-OF-SESSION.md` — internalize the two rituals
4. Run your first real session

---

## If you get stuck

See `docs/troubleshooting.md` in this Kit for common issues.

If that doesn't help, Claude Code has a built-in help menu — type `/help` inside any session. The official troubleshooting guide lives at [code.claude.com/docs/en/troubleshooting](https://code.claude.com/docs/en/troubleshooting).
