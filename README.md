# Pixelnthings Skills

Free Claude skills from [pixelnthings.com](https://pixelnthings.com) — drop-in workflows for solo content operators, marketers, and builders who run their work through Claude Code or Claude Desktop.

Built and maintained by [Nick](https://x.com/heyiamnick_).

---

## What's a Claude skill?

A skill is a folder with a `SKILL.md` file that teaches Claude how to do one specific job really well. Drop it in `~/.claude/skills/`, restart Claude Code, and Claude loads it automatically on every conversation.

Skills are plain markdown. No code, no plugins, no API keys. You can read them, edit them, fork them, rewrite them.

---

## Available skills

| Skill | What it does | Install |
|---|---|---|
| [`content-research-lite`](./content-research-lite) | 6-prompt research workflow that turns Claude into a junior content researcher. Cuts research time from 4 hours to 30 minutes per post. | See below |

More skills dropping regularly — follow [@heyiamnick_ on Twitter](https://x.com/heyiamnick_) for updates.

---

## Quick install (recommended)

Uses [`degit`](https://github.com/Rich-Harris/degit) to grab a single skill folder without cloning the full repo. One command, any OS with Node installed:

```bash
# Install content-research-lite into your personal Claude skills folder
npx degit heyiamnick/pixelnthingsz/content-research-lite ~/.claude/skills/content-research-lite
```

Then restart Claude Code. Type `/skills` to verify it's loaded.

## Alternative install (git clone)

If you don't have Node, use git instead:

```bash
# Clone the whole skills library into a temp folder
git clone https://github.com/heyiamnick/pixelnthingsz.git /tmp/pixelnthingsz

# Copy just the skill you want
cp -r /tmp/pixelnthingsz/content-research-lite ~/.claude/skills/
```

## Windows (PowerShell)

```powershell
# Using degit
npx degit heyiamnick/pixelnthingsz/content-research-lite "$env:USERPROFILE\.claude\skills\content-research-lite"

# Or using git
git clone https://github.com/heyiamnick/pixelnthingsz.git $env:TEMP\pixelnthingsz
Copy-Item -Path "$env:TEMP\pixelnthingsz\content-research-lite" -Destination "$env:USERPROFILE\.claude\skills\" -Recurse
```

---

## Verify it worked

Open Claude Code and run:

```
/skills
```

You should see `content-research-lite` in the list. If not, make sure the folder is at `~/.claude/skills/content-research-lite/` with `SKILL.md` directly inside it (not nested deeper).

---

## Paid skills (coming soon)

The **AI Content OS pack** is dropping in the next few days. It includes:

- The full `content-research` MCP server (runs all 6 prompts as background jobs with GPT verification)
- `wordpress-publisher` skill (markdown → WP draft in one command)
- `pxcreative-designer` skill (generate cover images that don't look AI-generated)
- The Notion Content OS template the pipeline is wired into

Stay tuned at [pixelnthings.com](https://pixelnthings.com) or DM me on [Twitter](https://x.com/heyiamnick_) if you want early access.

---

## Questions or bugs?

DM me on Twitter: [x.com/heyiamnick_](https://x.com/heyiamnick_) — I read every message.

## License

MIT. Use, modify, fork, share. Just don't repackage and resell the free skills as your own.

— Nick / pixelnthings.com
