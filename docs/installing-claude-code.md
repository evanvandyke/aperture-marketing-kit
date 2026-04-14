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

The skill packs are two open-source repos maintained by [@AgriciDaniel](https://github.com/AgriciDaniel):

- **claude-seo** — unlocks `/seo audit`, `/seo page`, `/seo schema`, `/geo-optimization`, and many more
- **claude-ads** — unlocks `/ads google`, `/ads meta`, `/ads linkedin`, `/ads tiktok`, and more

The recommended install method is to **ask Claude Code to install them for you** at the project level. You don't need to learn any install commands or repo structures. You tell Claude what you want, and Claude figures out how. This is the core pattern of working with Claude Code, and it's worth practicing on step one.

### Step 5a: Create a project folder (if you don't have one yet)

```bash
mkdir ~/my-marketing-project
cd ~/my-marketing-project
git init
code .
```

VS Code opens on the new folder. Open the integrated terminal (View → Terminal) and run:

```bash
claude
```

### Step 5b: Paste the install prompt

Inside the Claude Code session, paste this exact message:

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

Claude clones the repos, copies the files into `.claude/skills/` and `.claude/agents/` in your project, and reports back with the full list of commands now available. If something goes wrong — permission issue, network failure, anything — Claude will tell you what happened, and you ask it to fix the issue. You don't troubleshoot git commands yourself.

### Why project-scoped and not global?

Skills at the project level only load when Claude Code is running inside that specific folder. Three benefits:

1. **Isolation** — marketing skills don't clutter other Claude Code sessions on your machine (engineering projects, side projects, etc.)
2. **Self-contained** — anyone who clones your project folder gets the skills automatically
3. **No admin conflicts** — if your IT admin deploys different skills globally, project-scoped skills still work

### Team or Enterprise admins

If your org is on a Team or Enterprise Claude plan, you can deploy skills organization-wide through managed settings. See [Anthropic's official skills docs](https://code.claude.com/docs/en/skills) for the admin workflow.

### If you prefer global install

Each AgriciDaniel repo also supports a global install via an `install.sh` script. See the individual repos at [github.com/AgriciDaniel/claude-seo](https://github.com/AgriciDaniel/claude-seo) and [github.com/AgriciDaniel/claude-ads](https://github.com/AgriciDaniel/claude-ads) for those instructions. Project-scoped is recommended for most users.

---

## Step 6: Verify the install

You should still be in your project folder with Claude Code running. Type:

```
/seo
```

If autocomplete shows a list of SEO commands, the install succeeded. Try running a quick test:

```
/seo audit https://example.com
```

If Claude Code starts running an audit, everything is working correctly. You're ready to use the Aperture Marketing Kit.

If you see "unknown command" or autocomplete shows nothing, the skills didn't install correctly. Ask Claude to investigate:

> The /seo commands aren't showing up. Can you check what's in .claude/skills/ in this project and tell me what went wrong?

Claude will look at the files and usually figure out the issue on its own. See `docs/troubleshooting.md` for other common issues.

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
