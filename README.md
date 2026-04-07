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

## ⚠️ Important — Which Claude environment should you run this in?

The `content-research-lite` skill depends on **live web search**. If Claude can't reach the internet in real time, the entire workflow collapses into the same training-data slop it's designed to prevent. Here's what actually works:

| Environment | Live search | Recommended? |
|---|---|---|
| **Claude Cowork** | ✅ Built in | **Yes — easiest path** |
| **Claude Desktop** (with search enabled in settings) | ✅ Built in | Yes |
| **Claude.ai** (web, Pro/Max plan) | ✅ Built in | Yes |
| **Claude Code** | ⚠️ WebSearch is a deferred tool — Claude has to fetch it before running any step | Works, but needs one extra step |
| **Claude API (raw)** | ❌ No search unless you wire it yourself | Not recommended for this skill |

**If you're on Claude Code:** the skill's Step 0 tells Claude to fetch WebSearch before running. If Claude skips that and starts searching anyway, stop it and say *"Fetch WebSearch first, then restart Step 0."* Once fetched, the workflow runs normally.

**If you're on Claude Cowork or Desktop:** just install the skill and run it. Search is already there.

### Don't have live search? Give Claude superpowers with a search MCP

If your environment doesn't ship with WebSearch, you can wire up a third-party search MCP and Claude will use it like a native tool. Any of these work with this skill:

| MCP | Best for | Link |
|---|---|---|
| **Firecrawl** | Full-page scraping + search, handles JS-rendered pages | [firecrawl.link/heyiamnick](https://firecrawl.link/heyiamnick) |
| **Brave Search** | Free tier, privacy-focused, good for general queries | [brave.com/search/api](https://brave.com/search/api/) |
| **Serper** | Google results via API, fastest for SERP-style research | [serper.dev](https://serper.dev) |
| **Tavily** | Purpose-built for AI agents, returns clean JSON | [tavily.com](https://tavily.com) |
| **Exa** | Neural search, great for finding niche/expert content | [exa.ai](https://exa.ai) |

Install any one of these as an MCP server, add it to your Claude config, restart, and the skill will pick it up automatically on the next run. Firecrawl is the heaviest lift but gives you the best data quality; Brave is the cheapest starting point.

> *The Firecrawl link above is my affiliate — if you sign up through it, I get a small commission at no cost to you. It's the one I actually use in my own pipeline.*

**Quick sanity test after install:** open Claude, load the skill, and ask:
> *Use content-research-lite. Confirm today's date with a live search, then run Step 1 for niche "AI tools for freelancers" and audience "freelance designers making $3k–$10k/mo".*

If Claude echoes back the correct real-world date in the first reply, search is working. If it hesitates or uses a training-cutoff date, search is not reachable and the skill will not work in that environment.

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
