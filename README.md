# Cadboro Labs — Claude Skills Marketplace

A one-command marketplace for the [Cadboro Labs](https://cadborolabs.com) PM toolkit. Add it once in Claude Code and install any skill as a plugin.

## Add the marketplace

```bash
/plugin marketplace add brandonsgitstub/cadboro-marketplace
```

## Install a skill

```bash
/plugin install product-roadmap@cadboro-labs
```

Installed skills are namespaced by plugin, so you invoke them like:

```bash
/product-roadmap:roadmap-generator
```

…or just describe the task in natural language and Claude triggers the right skill automatically.

## Update

When new skills are added, refresh your local copy:

```bash
/plugin marketplace update cadboro-labs
```

---

## What's in the catalog

| Plugin | Skill | What it does | Status |
|--------|-------|--------------|--------|
| `product-roadmap` | `roadmap-generator` | Backlog / prioritization → structured roadmap with sequencing rationale | ✅ Live |
| `prd-generator` | `prd-generator` | Rough ideas → engineering-ready PRDs | ✅ Live |
| `user-story-generator` | `user-story-generator` | Features → dev-ready user stories with acceptance criteria | ✅ Live |
| `feature-prioritization` | `feature-prioritization` | Backlog → ranked RICE scorecard + brief | ✅ Live |
| `jtbd-research` | `jtbd-interview-guide` | Jobs-to-be-Done interview guides + synthesis | ✅ Live |
| `anti-ai-design` | `frontend-design` | Distinctive, non-generic frontend interfaces | ✅ Live |
| `saas-metrics` | `saas-metrics-analyzer` | SaaS metrics → scenario-modeled financial analysis | ✅ Live |
| `saas-pricing` | `saas-pricing-analyzer` | Subscription data → pricing tier analysis | ✅ Live |

---

## Repo structure

```
cadboro-marketplace/
├── .claude-plugin/
│   └── marketplace.json          # the catalog — one entry per plugin
└── plugins/
    └── product-roadmap/
        ├── .claude-plugin/
        │   └── plugin.json        # plugin manifest
        ├── README.md
        └── skills/
            └── roadmap-generator/ # the skill (dir name = SKILL.md `name:`)
                ├── SKILL.md
                └── references/
```

`metadata.pluginRoot` is set to `./plugins`, so each marketplace entry's `source` is `./<plugin-folder>` (resolved relative to `pluginRoot`).

Each skill is **vendored** from its standalone repo under [`github.com/brandonsgitstub`](https://github.com/brandonsgitstub) (this marketplace is the curated install path; the standalone repos stay for direct download). Note the plugin folder name and the skill folder name can differ — the skill folder must match the `name:` in that skill's `SKILL.md` frontmatter (e.g. the `anti-ai-design` plugin's skill is `frontend-design`).

---

## Adding a new skill

To vendor a new skill into the marketplace as a plugin:

**1. Create the plugin folders**

```
plugins/<plugin-name>/
├── .claude-plugin/plugin.json
├── README.md
└── skills/<skill-name>/
    ├── SKILL.md            # copied from the skill's repo
    └── references/         # copied from the skill's repo (if any)
```

`<skill-name>` must match the `name:` in that skill's `SKILL.md` frontmatter.

**2. Add `plugin.json`** (template — change the names/links):

```json
{
  "name": "prd-generator",
  "description": "Turn rough ideas into structured, engineering-ready PRDs.",
  "version": "1.0.0",
  "author": { "name": "Brandon Gains", "url": "https://cadborolabs.com" },
  "homepage": "https://cadborolabs.com",
  "repository": "https://github.com/brandonsgitstub/prd-skill",
  "license": "GPL-3.0-or-later"
}
```

**3. Add an entry to `.claude-plugin/marketplace.json`** in the `plugins` array:

```json
{
  "name": "prd-generator",
  "source": "./prd-generator",
  "description": "Turn rough ideas into structured, engineering-ready PRDs.",
  "version": "1.0.0",
  "author": { "name": "Brandon Gains", "url": "https://cadborolabs.com" },
  "homepage": "https://cadborolabs.com",
  "repository": "https://github.com/brandonsgitstub/prd-skill",
  "license": "GPL-3.0-or-later",
  "keywords": ["product-management", "prd", "spec"],
  "category": "product-management"
}
```

**4. Validate before pushing:**

```bash
claude plugin validate .
```

> **Alternative (no vendoring):** if you'd rather keep a single source of truth, restructure each standalone repo into plugin layout (`.claude-plugin/plugin.json` + `skills/<name>/SKILL.md`) and point each marketplace entry at it with a `github` source instead of a relative path:
> ```json
> { "name": "prd-generator", "source": { "source": "github", "repo": "brandonsgitstub/prd-skill" }, "description": "…" }
> ```
> This avoids duplicating skill content, at the cost of reshaping the existing repos.

---

## License

This marketplace and the vendored skills are licensed under [GPL-3.0-or-later](./LICENSE).

Built by [Brandon Gains](https://www.linkedin.com/in/brandon-gains/) · [Cadboro Labs](https://cadborolabs.com)
