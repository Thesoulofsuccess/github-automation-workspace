# github-automation-workspace

Personal AI & automation workspace by **Vikash Rajan** — Head of Global Operations, Redpin Payments (Mumbai).
Home of the **GitHub Intelligence Station** plus the Claude Code config and ops tooling I build on top of it.

## Contents

| Path | Description |
|------|-------------|
| `github-intel-station/` | A multi-agent AI system that scouts all of GitHub weekly, scores repos, and emails a ranked executive brief. Added as a **submodule** → lives at [Thesoulofsuccess/github-intel-station](https://github.com/Thesoulofsuccess/github-intel-station). |
| `.claude/` | Claude Code configuration and skills for this workspace. |
| `package-lock.json` | Locked dependency manifest. |

## GitHub Intelligence Station — what it does

Five agents run every Monday and return one ranked brief before standup:

**Scout → Analyst → Connector → Briefer → Gap Scout**

Recently upgraded from a topic-tag-only scout into a genuinely open discovery engine:

- **Multi-lane discovery** — beyond `topic:` tags, it now runs full-text **keyword** search (catches *untagged* repos) and a **velocity / wildcard** lane that surfaces just-shipped, fast-rising projects regardless of category. Ranking is `overlap × star-velocity × log(stars)`, not raw star count.
- **Notability axis** — a repo survives into the brief if it's objectively impressive *even when it doesn't fit a domain*, so nothing great gets filtered out for being off-thesis.
- **Gap Scout** — holds the week's most notable repos up against my own stack and reports **capability gaps**: what these repos do that my systems don't, and how to close it.
- **One-click adoption** — every recommended repo and every gap ships copy-able install commands for **Claude Code**, **Codex**, and **any other tool** (`brief.json` + a generated `adoption.md`).

> Discovery config is a single source of truth in `github-intel-station/scripts/recipes.json`; the system manifest it measures gaps against is `scripts/systems_manifest.json`.

## Notes

- Secrets (`.env`, API keys) are **excluded** via `.gitignore` and are never committed.
- `node_modules/` and build output are ignored.
- `github-intel-station` is a submodule — clone with `git clone --recurse-submodules`, or run `git submodule update --init` after cloning.

---

*Maintained for personal automation, payments-ops, and trading-intelligence tooling.*
